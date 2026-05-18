---
tags: cofacts
---

# Cofacts MCP Server — Technical Design Doc

## 1. Overview

本文說明 Cofacts MCP server 的現況與理想設計，目標 client 為：
- **Claude.ai connector**（雲端）：HTTPS redirect_uri
- **Claude Code / Cursor 等本機 agent**：loopback redirect_uri

現況實作： https://github.com/cofacts/rumors-api/pull/389

### 為何要做這個？

Cofacts MCP server 讓 AI agent 能夠以**真實使用者身份**存取 Cofacts API，開啟以下工作流程：

**查核者**
- 在研究過程中直接問 Claude「這則訊息有沒有人查核過？」，不需要切換到 cofacts.tw 手動搜尋
- 讓 Claude 彙整某篇文章現有的所有查核回應，快速掌握目前共識
- 草擬完查核說明後，直接透過 MCP 提交 reply，不需要開啟網頁表單

**智庫 / 研究人員**
- 詢問「最近一個月關於疫苗的文章有哪些尚未查核？」，讓 Claude 查詢並整理成報告
- 跨時段分析特定關鍵字的謠言散布模式（ListArticles + ListAnalytics）
- 匯出特定類別的查核資料，交由 Claude 做統計摘要或輔助撰寫白皮書

**Cofacts 團隊維運**
- 快速確認「哪些文章 reply request 數量多但還沒有 reply？」
- 透過對話介面批次確認 AI 自動回應的品質（ListAIResponses）
- 讓 Claude 協助審視 co-occurrence 資料，找出值得關注的謠言群集

---

### 為何選擇 Remote MCP 而不是 Skill？

**Skill** 只會走現在的 Cofacts API，會很難登入。

即使我們已經實作了 token 登入，但該登入流程最後需要 redirect 到 `ALLOWED_CALLBACK_URLS` 白名單，要進行其實不容易。

**Remote MCP** 的優勢：

1. **任意增減 tool，client 端不需要重新安裝**
   Tool 清單由 server 控制，推送新 tool 後所有已連接的 client 自動取得，無需使用者更新設定。
2. **不只限於 coding agent** 
   可以安裝成 claude.ai 的 **Connector**、ChatGPT 的 **App**，讓使用者在一般對話介面中就能使用，不需要進入 Claude Code 或 Cursor。查核者不一定是開發者，這一點至關重要。
3. **標準 OAuth 2.1 + PKCE，任何 MCP client 都能接**
   Claude Code、Cursor、Gemini CLI、claude.ai connector 使用同一套 server，不需要為各 client 做客製整合。新的 MCP client 出現時，無需改動 server 端任何白名單或配置。



## 2. Auth Flow 對比

### 2-a. 1st-party flow（cofacts.ai）

cofacts.ai 採用 BFF（Backend-for-Frontend）模式，access token 存在 SSR server 端的 HttpOnly cookie，瀏覽器的 JS 層無法存取。

```mermaid
sequenceDiagram
    participant B as Browser
    participant F as BFF (cofacts.ai)
    participant S as rumors-api
    participant P as Social Provider

    Note over B: User clicks Google login
    B->>S: GET /login/google?redirect_to=https://cofacts.ai/callback&state=s
    S->>P: Redirect to Google OAuth
    P-->>B: Prompt login & consent
    B->>P: User grants permission
    P->>S: GET /callback/google?code=GOOGLE_CODE&state=BFF_STATE
    S->>P: Exchange code for user profile
    P-->>S: User profile
    S->>S: verifyProfile() → signShortLivedJWT(userId) → JWT
    S-->>B: Redirect to https://cofacts.ai/callback?code=JWT&state=s
    B->>F: GET /callback?code=JWT&state=s
    F->>S: POST /auth/token { code: JWT }
    S->>S: verifyJWT(JWT)
    S-->>F: { access_token, token_type: "Bearer" }
    F-->>B: 302 to /state-url, Set-Cookie: session=access_token
    B->>S: POST /graphql  Authorization: Bearer access_token (via cookie)
```

**關鍵特性：**
- `redirect_to` 必須在 `ALLOWED_CALLBACK_URLS` 白名單內
- 無 PKCE（信任的 1st-party server）
- Token 不暴露給 browser JS

### 2-b. MCP client flow

MCP clients 使用 OAuth 2.1 + [PKCE（RFC 7636）](https://hackmd.io/@coscup/H1Oxr0Jp9/%2F%40coscup%2FH1J24AJ69)。

```mermaid
sequenceDiagram
    participant M as MCP Client
    participant B as Browser
    participant S as rumors-api
    participant P as Social Provider

    Note over M: User authenticates Cofacts MCP server
    M->>M: Generate PKCE: code_verifier, code_challenge = SHA256(verifier)
    M->>S: POST /mcp  (no token)
    S-->>M: 401 WWW-Authenticate: Bearer
    M->>S: GET /.well-known/oauth-authorization-server
    S-->>M: { authorization_endpoint, registration_endpoint, ... }
    M->>S: POST /mcp/register { redirect_uris: [localhost:PORT/cb] }
    S-->>M: { client_id: "mcp-public-client" }
    M->>B: Open /mcp/login?redirect_uri=localhost:PORT/cb&code_challenge=CC&state=s
    B->>S: GET /mcp/login?...
    S-->>B: HTML: provider selection (redirect_to=/mcp/callback, state=mcpState{r,cc,os})
    rect rgb(240, 248, 255)
        Note over B,P: Same as 1st party flow
        Note over B: User clicks Google login
        B->>S: GET /login/google?redirect_to=/mcp/callback&state=mcpState
        S->>P: Redirect to Google OAuth
        P-->>B: Prompt login & consent
        B->>P: User grants permission
        P->>S: GET /callback/google?code=GOOGLE_CODE&state=BFF_STATE
        S->>P: Exchange code for user profile
        P-->>S: User profile
        S->>S: verifyProfile() → signShortLivedJWT(userId) → JWT1
        S-->>B: Redirect to /mcp/callback?code=JWT1&state=mcpState
    end
    B->>S: GET /mcp/callback?code=JWT1&state=mcpState
    S->>S: verifyJWT(JWT1), extract cc from mcpState
    S->>S: signShortLivedJWT(userId, { codeChallenge: cc }) → JWT2
    S-->>B: Redirect to localhost:PORT/cb?code=JWT2&state=s
    B->>M: code=JWT2, state=s
    M->>S: POST /auth/token { code: JWT2, code_verifier }
    S->>S: verifyJWT(JWT2), SHA256(verifier) == JWT2.code_challenge ✓
    S-->>M: { access_token, token_type: "Bearer" }
    M->>S: POST /mcp  Authorization: Bearer access_token
    S-->>M: MCP response (execute_graphql tool available)

```


**與 1st-party 的關鍵差異：**

| | 1st party | MCP |
|---|---|---|
| redirect_uri 保護 | 白名單 | PKCE（loopback 或 HTTPS） |
| token 持有者 | BFF server | MCP client process |
| `/mcp/callback` | 不走 | 作為 whitelisted 中繼站，將 code_challenge embed 進 JWT2 |
| dynamic registration | 不需要 | `/mcp/register` 是 façade，全部回傳同一個 `mcp-public-client`——因為 PKCE 已做到 per-request binding |

---

## 3. GraphQL Context for MCP Requests

MCP request 執行的 mutation 寫入 ES 文件時，`appId` / `appUserId` / `userId` 填入如下：

| Field | MCP 填入值 | 說明 |
|---|---|---|
| `appId` | `"MCP"` | `mcpServer.ts` hardcode |
| `appUserId` | JWT `sub`（social login user ID） | raw user ID |
| `userId` | 同 `appUserId`（`createOrUpdateUser` 後的 ES doc ID） | |

與 cofacts.ai 對比：

| Field | cofacts.ai 填入值 |
|---|---|
| `appId` | `"RUMORS_SITE"` 或 app 自訂 |
| `appUserId` / `userId` | 同一個 user ID，但掛在對應 appId 下 |

目前 Claude Code、claude.ai connector、Cursor 三者產出的內容在 `appId` 欄位上無法區分，均為 `"MCP"`。若未來需要追蹤來源，可在 dynamic registration 階段記錄 `client_name` 並考慮 per-client appId。

### 三個設計選項（供討論）

#### Option 1 — MCP 帳號完全獨立（現狀）

`appId: 'MCP'` 被視為 backend app，`createOrUpdateUser` 產生新的 hashed user record。

- DB user ID = `encodeAppId('MCP')_sha256(ES_DOC_ID)`，與 cofacts.ai 帳號毫無關聯
- 貢獻紀錄、封鎖狀態等各自獨立
- 優點：實作零成本，attribution 清晰
- 缺點：同一個人在 cofacts.ai 和 MCP 是不同身份；封鎖繞過風險

#### Option 2 — 共用 cofacts.ai 身份、保留 MCP attribution（推薦）

讓 `getUserId` 對 MCP 走和 `'WEBSITE'` 同樣的路徑（直接回傳 ES_DOC_ID），但 `appId` 仍保持 `'MCP'` 供 mutation attribution 使用。

**實作方式：一行修改 `src/util/user.ts`**

```diff
 export const isBackendApp = (appId: UserAppIdPair['appId']) =>
-  appId !== 'WEBSITE' && appId !== 'DEVELOPMENT_FRONTEND';
+  appId !== 'WEBSITE' && appId !== 'DEVELOPMENT_FRONTEND' && appId !== 'MCP';
```

這讓 `getUserId({ appId: 'MCP', userId: ES_DOC_ID })` 直接回傳 `ES_DOC_ID`，`createOrUpdateUser` 找到現有的 social login user record，只更新 `lastActiveAt`。

結果：
- `userId` = 與 cofacts.ai 相同的 ES_DOC_ID → 同一個人、同一份紀錄
- `appId` = `'MCP'` → mutation 仍可區分來源
- 封鎖狀態、貢獻分數等完全共享

#### Option 3 — MCP 視同 cofacts.ai 網站（最簡單）

在 `mcpServer.ts` 把 `appId: 'MCP'` 改成 `appId: 'WEBSITE'`。

- 完全走 cofacts.ai 同一路徑
- 優點：零 infra 改動，身份 100% 一致
- 缺點：log 和 analytics 無法區分 MCP 與網站來源的 mutation


---

## 4. 理想 Tool 設計

### 現況問題

目前只有一個 `execute_graphql` tool，接受任意 GraphQL。使用者無法區分「允許查詢」與「允許寫入」，也無法在 claude.ai connector 畫面上分開設定權限。

### 提案：拆成兩個 tool

參考 Google Drive connector 的 Read-only / Write-delete 分層：

**`graphql_query`** — 對應所有 Query operation
- annotations: `{ readOnlyHint: true, idempotentHint: true }`
- handler 驗證傳入的 operation type 必須是 `query`，否則 reject

**`graphql_mutate`** — 對應所有 Mutation operation
- annotations: `{ readOnlyHint: false, destructiveHint: true }`
- handler 驗證傳入的 operation type 必須是 `mutation`，否則 reject

Operation type 驗證方式：用 `graphql` 套件的 `parse()` 解析後檢查 `OperationDefinitionNode.operation`。

```typescript
import { parse, OperationDefinitionNode } from 'graphql';

function getOperationType(src: string) {
  const doc = parse(src);
  const op = doc.definitions.find(
    (d): d is OperationDefinitionNode => d.kind === 'OperationDefinition'
  );
  return op?.operation ?? null; // 'query' | 'mutation' | 'subscription' | null
}
```

錯誤回傳範例（LLM 傳錯了）：
```
Error: graphql_query only accepts query operations.
Use graphql_mutate for mutations.
```

### 現有 Query / Mutation 清單

**Queries（→ `graphql_query`）：**
GetArticle, GetReply, GetUser, GetCategory, GetYdoc, GetBadge, ListArticles, ListReplies, ListCategories, ListArticleReplyFeedbacks, ListReplyRequests, ListBlockedUsers, ListAnalytics, ListAIResponses, ListCooccurrences, ValidateSlug

**Mutations（→ `graphql_mutate`）：**
CreateArticle, CreateMediaArticle, CreateReply, CreateAIReply, CreateArticleReply, CreateCategory, CreateArticleCategory, CreateOrUpdateReplyRequest, CreateOrUpdateArticleReplyFeedback, CreateOrUpdateArticleCategoryFeedback, CreateOrUpdateReplyRequestFeedback, CreateOrUpdateCooccurrence, UpdateArticleReplyStatus, UpdateArticleCategoryStatus, UpdateUser

### 為什麼不做「每個 operation 一個 tool」？

- 共約 32 個 operations → tool 列表過長，UI 難以使用
- Agent 本來就需要透過 introspection 探索 schema，per-operation tool 沒有額外好處
- Read/Write 兩層分割已足夠滿足「分開設定權限」的核心需求

### Structured output（`outputSchema`）

目前 `execute_graphql` 將結果 `JSON.stringify` 後塞進 `content[0].text`，client 收到的是一個 JSON string，需要再 parse 才能取用。

改用 `outputSchema` 後，handler 回傳 `structuredContent`，client 直接拿到 typed JSON object：

```typescript
server.registerTool('graphql_query', {
  description: '...',
  inputSchema: {
    query: z.string(),
    variables: z.record(z.unknown()).optional(),
    operationName: z.string().optional(),
  },
  outputSchema: {
    data: z.record(z.unknown()).optional(),
    errors: z.array(z.object({ message: z.string() })).optional(),
  },
  annotations: { readOnlyHint: true, idempotentHint: true },
}, async ({ query, variables, operationName }) => {
  // ...operation type check...
  const result = await graphql({ schema, source: query, variableValues: variables, operationName, contextValue });
  return { structuredContent: result };
});
```

好處：Claude 不需要從純文字中 parse JSON 來理解結果，可以直接存取 `data` 欄位，減少 token 使用並降低結構解析錯誤的機率。

---

## 5. 告知 AI Agent 如何正確使用 API

MCP SDK 提供以下機制：

### 5-a. Server-level `instructions`（推薦優先實作）

`McpServer` constructor 的 `options.instructions` 在 client 初始化時送達，會被納入 agent 的 context。適合放高層次的 domain knowledge：

```typescript
new McpServer({ name: 'cofacts-api', version: '1.0.0' }, {
  instructions: `
Cofacts API — 台灣事實查核協作平台。

Domain knowledge:
- Article = 使用者回報的可疑訊息。URL: cofacts.tw/article/<articleId>
- Reply = 志工撰寫的查核回應。URL: cofacts.tw/reply/<replyId>
- ArticleReply = 將 Reply 連結到 Article 的關聯（一篇 Article 可有多個 Reply）
- ArticleReplyFeedback = ...
- ReplyRequest = ...
- ArticleCategory = ...

使用方式：
1. 先執行 graphql_query 進行 introspection，了解 schema
2. Query 用 graphql_query；Mutation 用 graphql_mutate
`
})
```

### 5-b. Tool description

Tool description 顯示於 claude.ai connector UI，也是 agent 選擇 tool 的依據。可嵌入 domain hints：

```
Execute a read-only GraphQL query against the Cofacts API.
Run introspection first to explore the schema:
  { __schema { queryType { fields { name description } } } }
Article public URL: cofacts.tw/article/<id>
```

### 5-c. MCP Resources

`server.resource()` 可讓 agent 按需讀取靜態文件：

```typescript
// GraphQL SDL（代替讓 agent 自己打 introspection）
server.resource('graphql-schema', 'cofacts://schema',
  { mimeType: 'text/plain' },
  async () => ({ contents: [{ uri: 'cofacts://schema', text: printSchema(schema) }] })
);

// Domain guide markdown
server.resource('domain-guide', 'cofacts://guide',
  { mimeType: 'text/markdown' },
  async () => ({ contents: [{ uri: 'cofacts://guide', text: DOMAIN_GUIDE_MD }] })
);
```

注意：Resources 的 client 支援度不一。Claude Code 支援，但 claude.ai connector 目前未必主動讀取。`instructions` 較為可靠。

### 5-d. MCP Prompts

Prompts 是 server 提供的可重用 prompt template，user 或 agent 可以按名稱呼叫。在 Claude Code 裡會顯示為 slash command（例如 `/mcp__cofacts-api__search-articles`）。

由於 Cursor 和 Gemini CLI **不支援 Resources 但支援 Prompts**，Prompts 是目前跨 client 傳遞較長說明內容的較佳手段（比 Resources 更廣泛）。

Cofacts 適合的 Prompt 設計方向：

```typescript
// 1. 搜尋文章 — 引導 agent 用正確的 filter 組合
server.prompt('search-articles', { keyword: z.string() }, ({ keyword }) => ({
  messages: [{
    role: 'user',
    content: { type: 'text', text:
      `Search Cofacts articles about "${keyword}".
       Use graphql_query with ListArticles, filter by articleReplyCount > 0 to focus on fact-checked content.
       Article URL format: cofacts.tw/article/<id>`
    }
  }]
}));

// 2. 查看文章的查核結果
server.prompt('fact-check-status', { articleId: z.string() }, ({ articleId }) => ({
  messages: [{
    role: 'user',
    content: { type: 'text', text:
      `Get the fact-check status of article ${articleId} (cofacts.tw/article/${articleId}).
       Use graphql_query with GetArticle to fetch articleReplies and their reply type (RUMOR/NOT_RUMOR/OPINIONATED/NOT_ARTICLE).`
    }
  }]
}));
```

Prompts 與 `instructions` 的定位差異：
- `instructions`：每次初始化都送出，適合簡短的 domain basics
- Prompts：使用者/agent 主動呼叫，適合較長的 guided workflow，不佔用每次的 context 空間


### 機制比較

| 機制 | Claude Code | Claude.ai | Cursor | Gemini CLI | Zed |
|---|:---:|:---:|:---:|:---:|:---:|
| `instructions` | ✓ | ✓ | ✓ | ✓ | — |
| Tool description / annotations | ✓ | ✓ | ✓ | ✓ | ✓ |
| **Prompts** | ✓ | ✓ | ✓ | ✓ | ✓ |
| **Resources** | ✓ | ✓ | ✗ | ✗ | ✗ |

來源：[modelcontextprotocol.io/clients](https://modelcontextprotocol.io/clients)


## 待討論

CreateArticle / CreateMediaArticle 是否要增加限制
- references 限制？
- 用 prompt 引導 agent 先查相似訊息，再來決定是否要送出，並且要求提供回報補充資訊，最後引導到自行查證
- 允許從 MCP 投遞不是 LINE 的其他來源？


要加 log 嗎
- 要的話，肯定是要 log 是誰打的，還有 auth error
    - 要 log query 本體嗎
    - 要 log response 嗎
- MCP server 可以發個 [MCP-session-ID](https://modelcontextprotocol.io/specification/2025-11-25/basic/transports#session-management)，client 會一直回傳同一個 session ID，讓我們能追蹤一個 chat session 底下發生的 query
- 直接吐在 console (上 cloud console，一個月 retention) or 吐到 langfuse (我們沒在清，他會一直存著)

使用者條款？
- 紀錄誰看過使用者條款、看了哪一個版本？
- 傳送網路訊息之權利義務
    - 「使用者對本聊天機器人所發送的任何事實性資訊，倘僅為事實性考究與通報，依法不視為著作表達而可被自由引用及紀錄。若提報資料受著作權利保護，並同時以聊天機器人使用者為其著作權利人，則採 CC0-1.0 無償提交至 Cofacts WG 所維運之電腦或相關設備進行存放。若提報資料的著作權利歸屬於第三方，則敦請聊天機器人使用者協助標示其歸屬狀態。」 https://github.com/cofacts/rumors-line-bot/blob/master/LEGAL.md
    - 「提交資訊即代表您同意 Cofacts WG 將存放於電腦或其相關設備的該等資訊進行編輯性整理後，得採 CC BY-SA 4.0 或其他適宜的授權模式，將具編輯性保護之資料發布於 Cofacts 網站、Cofacts 聊天機器人或 Cofacts 所提供資料存檔等處。」https://github.com/cofacts/opendata/blob/master/LEGAL.md#%E5%9B%9B%E5%9B%9E%E5%A0%B1%E8%B3%87%E8%A8%8A
- 傳送查核結果之權利義務
    - 「網站協作者查核後所撰寫的回應、補充或評價等資訊，若有產生著作權利保護之可能，撰寫之編輯同意採公眾領域宣告（CC0-1.0）無償提交至 Cofacts WG 所維運之電腦或相關設備進行存放。」「網站協作者若使用第三方之資料來源進行佐證，其引用之資料來源之著作仍屬於原創作之第三方所有，此時協作者同意為查證目的，在合理範圍內引用第三方資料，並於提交時提供原創作出處。」https://github.com/cofacts/rumors-site/blob/master/LEGAL.md
    - 同上， https://github.com/cofacts/opendata/blob/master/LEGAL.md#%E5%9B%9B%E5%9B%9E%E5%A0%B1%E8%B3%87%E8%A8%8A
- 使用資料的權利義務：「您在後續重製或散布時，原社群顯名及每一則查證的出處連結（URI）皆必須被完整引用」與「除已知非直接營利的第三方公眾服務網站爬蟲，採低頻率部份內容捉取模式外（如 Internet Archive、Google、Facebook），以及依本使用者條款申請取得 app-id 或 app-secret 等 Cofacts API 應用外，本使用者條款明確禁止使用自動化方式爬取 Cofacts 網站或聊天機器人所提供的內容，所有逾此範圍之自動化資料爬取行為，皆視為對 Cofacts 真的假的 相關服務之惡意使用。」https://github.com/cofacts/opendata/blob/master/LEGAL.md
- 免責聲明、聯絡方式、法院 https://github.com/cofacts/opendata/blob/master/LEGAL.md#%E4%BA%94%E5%85%8D%E8%B2%AC%E8%81%B2%E6%98%8E

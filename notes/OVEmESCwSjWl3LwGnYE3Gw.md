---
tags: vtaiwan 
---
# Cloudflare 兩頭接：LINE Bot × OpenClaw 專案工程實作方案

(草案v0.1.0)

## 1. 專案目標

建立一個 **Cloudflare Worker 後端**，同時扮演兩個角色：

1. **對外**接收 LINE Bot 的 webhook 事件。
2. **對內**提供給 OpenClaw 定期輪詢的 API。

這樣可把職責拆清楚：

- **LINE Bot**：負責與使用者互動、推送投票、接收回覆。
- **Cloudflare Worker / Hono API**：負責驗證、整理新聞、保存候選題目、提供安全 API。
- **OpenClaw（龍蝦）**：定期用受保護的 Token 打 API，觸發 AI 摘要、整理 polis 投票題目、回寫結果。
    - 目前的討論：不一定要用 Openclaw，其實用 cloudfare 的雲端服務就可以滿足需求，甚至可以使用開源 AI 的工具
---

## 2. 建議總體架構

```text
[新聞來源 / RSS / 手動匯入]
            |
            v
   [Cloudflare Worker + Hono]
   - /line/webhook
   - /api/news/pending
   - /api/news/:id/process
   - /api/polis/payloads
   - Token 驗證
   - LINE Signature 驗證
   - KV / D1 / Queues（可選）
            |
   +--------+--------+
   |                 |
   v                 v
[LINE Bot]       [OpenClaw]
使用者互動         定期 cron / scheduler 呼叫 API
投票推播           產生摘要、分類、整理成 polis 題目
```

---

## 3. 主要模組拆分

### A. LINE Webhook 入口
用途：

- 接收使用者訊息
- 接收按鈕 / postback
- 驗證 `x-line-signature`
- 必要時把事件寫入 D1 / KV

建議路由：

- `POST /line/webhook`

### B. OpenClaw 專用 API
用途：

- 讓 OpenClaw 抓待整理的新聞
- 讓 OpenClaw 回寫 AI 摘要結果
- 讓 OpenClaw 取得待投放的 polis 題目資料
- 只允許持有正確 Token 的客戶端存取

建議路由：

- `GET /api/news/pending`
- `POST /api/news/:id/process`
- `GET /api/polis/payloads`
- `POST /api/polis/:id/publish`

### C. 資料層
最小可行方案：

- **Cloudflare KV**：存簡單狀態、Token、快取
- **Cloudflare D1**：存新聞、摘要、投票任務、使用者狀態

建議資料表：

- `news_items`
- `ai_summaries`
- `polis_tasks`
- `line_users`
- `bot_events`

---

## 4. 為什麼要「兩頭接」

### 好處 1：OpenClaw 不直接暴露在 LINE webhook 前面
這樣可以降低安全風險，也比較容易除錯。

### 好處 2：Worker 比較適合做邊界層
例如：

- 驗證 LINE signature
- 驗證內部 Token
- 篩掉惡意請求
- 控制 API 節流與日誌

### 好處 3：OpenClaw 專心做 AI 工作
例如：

- 新聞摘要
- 事件分類
- 生成 polis 題目
- 根據 prompt 決定不同格式輸出

---

## 5. 安全設計

## 5.1 驗證 LINE Webhook 來源
LINE 官方建議 webhook 伺服器在處理事件前，先驗證 `x-line-signature`。  
做法是使用 **channel secret** 對原始 request body 做 HMAC-SHA256，再與 header 比對。

重點：

- 一定要用 **原始 body**
- 驗證失敗就直接回 `401` 或 `403`
- 不要先 parse 再驗證

---

## 5.2 保護 OpenClaw API
建議至少做這三層：

### 層 1：Bearer Token
OpenClaw 呼叫 API 時帶：

```http
Authorization: Bearer <OPENCLAW_SHARED_TOKEN>
```

Worker 驗證方式：

- Token 存在 Cloudflare secret
- 不寫死在程式碼
- 驗證失敗直接回 `401`

### 層 2：來源識別
可以再加一個自訂 header：

```http
X-Client-Id: openclaw-prod-01
```

用途：

- 區分不同 OpenClaw 節點
- 日誌可追蹤
- 未來方便做輪替與停用

### 層 3：時間戳與重放保護（進階）
可要求 OpenClaw 傳：

- `X-Timestamp`
- `X-Signature`

用共享密鑰計算簽章，避免 token 洩漏後被重放攻擊。

---

## 6. 最小可行 API 規格

## 6.1 LINE webhook

### `POST /line/webhook`

用途：接收 LINE 平台 webhook

回應：

- 成功：`200 OK`
- 驗證失敗：`401 Unauthorized`

---

## 6.2 OpenClaw 取得待處理新聞

### `GET /api/news/pending`

Header：

```http
Authorization: Bearer <OPENCLAW_SHARED_TOKEN>
```

Response：

```json
{
  "items": [
    {
      "id": "news_001",
      "title": "某新聞標題",
      "url": "https://example.com/news/1",
      "content": "新聞內文或擷取內容",
      "createdAt": "2026-03-27T10:00:00Z"
    }
  ]
}
```

---

## 6.3 OpenClaw 回寫 AI 整理結果

### `POST /api/news/:id/process`

Request：

```json
{
  "summary": "AI 生成摘要",
  "keywords": ["救災", "資訊流通", "地方政府"],
  "polisDraft": {
    "topic": "未來救災資訊流程如何改進？",
    "statements": [
      "政府應建立單一災情資訊入口",
      "地方與中央的撤離標準應公開透明"
    ]
  },
  "status": "processed"
}
```

---

## 6.4 取得待投放的 polis 載荷

### `GET /api/polis/payloads`

用途：讓後續投票投放流程抓資料。

---

## 7. Hono 專案結構建議

```text
src/
  index.ts
  routes/
    line.ts
    api.ts
  middleware/
    verifyLineSignature.ts
    verifyInternalToken.ts
  services/
    lineService.ts
    newsService.ts
    polisService.ts
  db/
    schema.sql
```

---

## 8. Hono + Cloudflare Worker 範例骨架

```ts
import { Hono } from 'hono'

type Bindings = {
  LINE_CHANNEL_SECRET: string
  LINE_CHANNEL_ACCESS_TOKEN: string
  OPENCLAW_SHARED_TOKEN: string
}

const app = new Hono<{ Bindings: Bindings }>()

app.get('/', (c) => c.text('ok'))

app.post('/line/webhook', async (c) => {
  const rawBody = await c.req.text()
  const signature = c.req.header('x-line-signature') || ''

  // TODO:
  // 1. 使用 LINE_CHANNEL_SECRET 對 rawBody 做 HMAC-SHA256
  // 2. 與 signature 比對
  // 3. 驗證成功後再 JSON.parse(rawBody)

  return c.json({ ok: true })
})

app.use('/api/*', async (c, next) => {
  const auth = c.req.header('authorization') || ''
  const expected = `Bearer ${c.env.OPENCLAW_SHARED_TOKEN}`

  if (auth !== expected) {
    return c.json({ error: 'unauthorized' }, 401)
  }

  await next()
})

app.get('/api/news/pending', async (c) => {
  return c.json({
    items: []
  })
})

app.post('/api/news/:id/process', async (c) => {
  const id = c.req.param('id')
  const body = await c.req.json()
  return c.json({ ok: true, id, received: body })
})

export default app
```

---

## 9. Wrangler secrets 設定

請把敏感資訊放進 Cloudflare Worker secrets：

```bash
wrangler secret put LINE_CHANNEL_SECRET
wrangler secret put LINE_CHANNEL_ACCESS_TOKEN
wrangler secret put OPENCLAW_SHARED_TOKEN
```

不要把下列值直接 commit 到 Git：

- LINE channel secret
- LINE channel access token
- OpenClaw shared token

---

## 10. OpenClaw 端怎麼打

OpenClaw 可定期呼叫：

```bash
curl -H "Authorization: Bearer $OPENCLAW_SHARED_TOKEN"   https://your-worker.your-subdomain.workers.dev/api/news/pending
```

建議節奏：

- 每 10 分鐘抓一次待處理新聞
- 處理完就 `POST /api/news/:id/process`
- 由 Worker 控制狀態，不讓同一篇新聞重複被處理

---

## 11. 排程方式

有兩種常見作法：

### 作法 A：OpenClaw 自己排程
優點：

- OpenClaw 自己決定什麼時候抓資料
- 最符合你現在「讓龍蝦定期去打 API」的想法

### 作法 B：Cloudflare Worker Cron Trigger
由 Worker 定期整理待處理資料，或主動觸發後續流程。

如果你的 AI 主流程還是在 OpenClaw，那目前比較推薦 **作法 A 為主，B 為輔**。

---

## 12. 資料流建議

### 階段 1：收集
- Worker 從 RSS / 手動匯入 / webhook 收進新聞
- 寫入 `news_items`，狀態為 `pending`

### 階段 2：AI 整理
- OpenClaw 定期打 `GET /api/news/pending`
- 取新聞後做摘要、標題整理、產生 polis statements
- 回寫 `POST /api/news/:id/process`

### 階段 3：人工或半自動審核
- 可加一個 `review_status`
- 避免 AI 直接把不適合的題目送給使用者投票

### 階段 4：LINE 投放
- Worker 從 `polis_tasks` 取出可投放題目
- 用 LINE Messaging API 推送到指定使用者
- 收到投票後記錄到資料庫，或同步到 polis 流程

---

## 13. 推薦 MVP 範圍

第一版先做：

1. LINE webhook 收訊息
2. Token 保護的 `/api/news/pending`
3. Token 保護的 `/api/news/:id/process`
4. D1 儲存新聞與摘要
5. 基本 log 與錯誤處理

先不要急著加：

- 多租戶
- JWT / OAuth
- 複雜 ACL
- 完整後台 UI
- 太多自動化投放規則

---

## 14. 未來可擴充方向

### A. 加入 Cloudflare Queues
把 webhook 事件與 AI 任務解耦，避免尖峰時卡住。

### B. 加入 Durable Objects
如果之後需要：

- 單一任務鎖
- 投票 session 狀態
- 使用者對話狀態機

可以再導入。

### C. 加入 HMAC request signing
讓 OpenClaw 與 Worker 間不只用 Bearer Token，而是每次 request 都有時間戳簽章。

### D. 加入審核後台
可用 Vue 或 Nuxt 前端去審 AI 產出的 polis 題目。

---

## 15. 實作順序建議

### 第 1 步
建立 Cloudflare Worker + Hono 專案骨架。

### 第 2 步
先做 `POST /line/webhook`，並完成 LINE signature 驗證。

### 第 3 步
加上 `/api/*` 的 Bearer Token 驗證 middleware。

### 第 4 步
建立 D1 schema，先存 `news_items` 和 `ai_summaries`。

### 第 5 步
讓 OpenClaw 先能抓一筆待處理新聞並回寫摘要。

### 第 6 步
最後才接 LINE 推播與 polis 投票資料流。

---

## 16. 官方技術文件

### LINE Messaging API
- LINE Messaging API 文件  
  https://developers.line.biz/en/docs/messaging-api/

- Receive messages (webhook)  
  https://developers.line.biz/en/docs/messaging-api/receiving-messages/

- Verify webhook signature  
  https://developers.line.biz/en/docs/messaging-api/verify-webhook-signature/

- Verify webhook URL  
  https://developers.line.biz/en/docs/messaging-api/verify-webhook-url/

- Messaging API reference  
  https://developers.line.biz/en/reference/messaging-api/

### Cloudflare Workers
- Cloudflare Workers 總覽  
  https://developers.cloudflare.com/workers/

- Cloudflare Workers + APIs / secrets  
  https://developers.cloudflare.com/workers/configuration/integrations/apis/

- Cron Triggers  
  https://developers.cloudflare.com/workers/configuration/cron-triggers/

### Hono
- Hono 文件首頁  
  https://hono.dev/docs/

- Hono on Cloudflare Workers  
  https://hono.dev/docs/getting-started/cloudflare-workers

---

## 17. 一句話總結

你的這個案子，最穩的做法就是：

**用 Cloudflare Worker + Hono 當邊界層，前面接 LINE Bot，後面開受 Token 保護的 API 給 OpenClaw 定期呼叫。**

這樣會比讓 LINE 直接碰 OpenClaw 更安全、好維護，也更容易逐步擴充成可正式上線的系統。

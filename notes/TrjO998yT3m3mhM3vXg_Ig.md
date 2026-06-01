---
tags: tokenhunt
---
# TokenHunt: 你多餘的 token 可能某個專案的解方

> 把你多餘的 AI Token，貢獻給需要的公民科技專案。

---

### 想要貢獻專案？
- 歡迎在共筆上加入討論，或者是到 g0v slack 上私訊 peter @g0v slack
- Github: https://github.com/Jia-wei-cui/TokenHunt/tree/main 


## 目錄

1. [專案背景與動機](#一專案背景與動機)
2. [核心概念](#二核心概念)
3. [使用者旅程](#三使用者旅程)
4. [功能規劃](#四功能規劃)
5. [資料結構](#五資料結構)
6. [技術架構](#六技術架構)
7. [部署方式](#七部署方式)
8. [API 設計](#八api-設計)
9. [未來擴充方向](#九未來擴充方向)
10. [授權](#十授權)

---

## 一、專案背景與動機

g0v 社群長期以來累積了大量有意義的公民科技專案，然而許多坑主在推進專案時，會遇到需要 AI 協助處理的任務——例如逐字稿整理、公文解析、資料清理、多語翻譯等——卻因為缺乏足夠的 AI API token 額度而卡關。

另一方面，社群中有不少人持有各種 AI 服務的訂閱方案（Claude Pro、ChatGPT Plus、Gemini Advanced 等），每個月都有用不完的 token 額度閒置。

**TokenHunt 想做的事很簡單：讓這兩群人找到彼此。**

這是一個「AI Token 版的賞金獵人平台」，以開源精神運作，不收取任何費用，純粹作為社群資源的媒合橋樑。

---

## 二、核心概念

### 角色定義

| 角色 | 說明 |
|------|------|
| **坑主（Project Owner）** | g0v 專案維護者，有 AI 協助需求，將任務整理成 Issue 登記於平台 |
| **Token 獵人（Hunter）** | 有多餘 token 的社群成員，自願接球解決 Issue |
| **Reviewer**（未來）| 協助審核成果品質的第三方，可為人工或 AI |

### 運作精神

- **純自願** — 沒有金錢交易，獵人用自己的 token 貢獻
- **透明公開** — 使用的 prompt、token 用量、產出內容均公開，供社群學習
- **低門檻** — 用 GitHub 帳號登入即可參與，不需要另外申請帳號
- **開源** — 平台本身以 CC0 授權釋出，歡迎 fork 與改作

---

## 三、使用者旅程

### 坑主流程

```
1. 用 GitHub 登入
2. 登記專案（填入專案名稱、連結）
3. 建立 Issue
   └─ 填寫：問題描述、背景說明、期望產出格式
   └─ 標注：建議 AI 工具、難度、token 估計量
4. 等待獵人接球
5. 收到成果後進行驗收
6. 驗收通過 → Issue 關閉
```

### 獵人流程

```
1. 用 GitHub 登入
2. 瀏覽 Issue Board（可依工具、難度、狀態篩選）
3. 找到適合自己的 Issue → 點擊「接球」
4. 系統鎖定 Issue（7 天時限），其他人暫時無法認領
5. 用自己的 AI token 處理任務
6. 提交成果
   └─ 上傳產出內容
   └─ 公開使用的 Prompt（供社群學習）
   └─ 回報實際使用 token 量
7. 坑主驗收通過 → 獲得聲譽點數
```

---

## 四、功能規劃

### MVP（第一階段）

- **Issue Board** — 列表展示，支援多維篩選與關鍵字搜尋
- **Issue 詳情頁** — 問題描述、背景、期望產出、認領與提交操作
- **Issue 建立表單** — 坑主登記新任務
- **GitHub OAuth 登入** — 統一身份驗證，無需另行註冊
- **認領機制** — 一次只能一人認領，7 天完成時限，避免多人重工
- **成果提交** — 含產出內容、Prompt 記錄、token 用量
- **坑主驗收** — 通過或退回修改
- **聲譽系統（後端預留）** — 資料庫記錄但前端暫不顯示

### Issue 狀態流程

```
open（開放）
  └─→ claimed（認領中）  ← 獵人點擊接球
        └─→ review（審核中） ← 獵人提交成果
              ├─→ done（已完成）    ← 坑主驗收通過
              └─→ claimed（退回）   ← 坑主要求修改
```

### 第二階段（預留結構）

- **Reviewer 機制** — 人工或 AI 做第一層審核，減輕坑主負擔
- **積分與補償機制** — 獵人累積積分可兌換社群資源（API 贊助、活動票等）
- **Token 贊助池** — 企業或個人贊助 token，由平台統一分配
- **g0v Slack 通知** — 新 Issue 自動推送到 `#general` 頻道
- **與 GitHub Issues 整合** — Issue 可連結到實際 PR 或 HackMD 文件

---

## 五、資料結構

### Users（使用者）

| 欄位 | 類型 | 說明 |
|------|------|------|
| `id` | INTEGER | 主鍵 |
| `github_id` | INTEGER | GitHub 帳號 ID |
| `username` | TEXT | GitHub 用戶名 |
| `avatar_url` | TEXT | 頭像 URL |
| `reputation` | INTEGER | 聲譽點數（預留） |
| `points` | INTEGER | 積分（預留，供未來補償機制） |
| `created_at` | TEXT | 建立時間 |

### Projects（專案）

| 欄位 | 類型 | 說明 |
|------|------|------|
| `id` | INTEGER | 主鍵 |
| `name` | TEXT | 專案名稱 |
| `slug` | TEXT | 唯一識別碼（如 `budget.g0v.tw`） |
| `description` | TEXT | 專案簡介 |
| `github_url` | TEXT | GitHub 連結 |
| `owner_id` | INTEGER | 坑主 user ID |
| `created_at` | TEXT | 建立時間 |

### Issues（任務）

| 欄位 | 類型 | 說明 |
|------|------|------|
| `id` | INTEGER | 主鍵 |
| `title` | TEXT | Issue 標題 |
| `project` | TEXT | 所屬專案 slug |
| `description` | TEXT | 問題描述 |
| `background` | TEXT | 背景說明 |
| `expected_output` | TEXT | 期望產出格式 |
| `tool` | TEXT | 建議 AI 工具（claude / gpt / gemini / other） |
| `difficulty` | TEXT | 難度（easy / medium / hard） |
| `token_estimate` | TEXT | token 估計量（人類可讀，如 `~80K`） |
| `status` | TEXT | 狀態（open / claimed / review / done） |
| `owner_id` | INTEGER | 坑主 user ID |
| `claimed_by` | INTEGER | 認領獵人 user ID |
| `claim_deadline` | TEXT | 認領截止時間 |
| `created_at` | TEXT | 建立時間 |

### Submissions（提交成果）

| 欄位 | 類型 | 說明 |
|------|------|------|
| `id` | INTEGER | 主鍵 |
| `issue_id` | INTEGER | 對應 Issue |
| `contributor_id` | INTEGER | 提交獵人 user ID |
| `content` | TEXT | 產出內容或連結 |
| `prompt_used` | TEXT | 使用的 Prompt（公開） |
| `actual_tokens` | INTEGER | 實際使用 token 數 |
| `status` | TEXT | 審核狀態（pending / accepted / rejected） |
| `reviewer_id` | INTEGER | Reviewer（預留） |
| `reviewer_note` | TEXT | 審核備注（預留） |
| `created_at` | TEXT | 建立時間 |

---

## 六、技術架構

```
┌─────────────────────────────────────────────┐
│               使用者瀏覽器                    │
│         HTML / CSS / Vanilla JS              │
│         中英雙語（i18n 模組）                 │
└──────────────────┬──────────────────────────┘
                   │ HTTPS
┌──────────────────▼──────────────────────────┐
│           Cloudflare 邊緣網路                 │
│                                             │
│  ┌─────────────────┐  ┌──────────────────┐  │
│  │ Cloudflare Pages│  │Cloudflare Workers│  │
│  │  (靜態前端)      │  │  (API 後端)       │  │
│  │                 │  │                  │  │
│  │ /               │  │ /api/*           │  │
│  │ /pages/*        │  │  - auth (OAuth)  │  │
│  └─────────────────┘  │  - issues CRUD   │  │
│                       │  - projects CRUD │  │
│                       │  - stats         │  │
│                       └────────┬─────────┘  │
│                                │            │
│                       ┌────────▼─────────┐  │
│                       │  Cloudflare D1   │  │
│                       │  (SQLite 資料庫)  │  │
│                       └──────────────────┘  │
└─────────────────────────────────────────────┘
                   │
         ┌─────────▼─────────┐
         │   GitHub OAuth     │
         │  身份驗證服務       │
         └───────────────────┘
```

### 技術選型理由

| 技術 | 選擇 | 理由 |
|------|------|------|
| 前端框架 | 純 HTML/CSS/JS | 零依賴、部署簡單、g0v 社群易於貢獻 |
| 後端 | Cloudflare Workers | 免費方案足夠 MVP、全球低延遲、無伺服器維護成本 |
| 資料庫 | Cloudflare D1 | Workers 原生支援、免費方案 5GB、SQLite 語法熟悉 |
| 前端 Hosting | Cloudflare Pages | 與 Workers 同平台、GitHub 自動部署、免費 |
| 身份驗證 | GitHub OAuth | g0v 社群成員幾乎都有 GitHub 帳號 |
| CI/CD | GitHub Actions | 免費、push 即部署 |

### Session 機制

登入後以 **HS256 JWT** 存放於 `HttpOnly` Cookie，有效期 30 天。Worker 端每次請求驗證 JWT，不需要額外的 session store。

---

## 七、部署方式

### 前置準備

**1. 建立 GitHub OAuth App**

前往 `GitHub → Settings → Developer settings → OAuth Apps → New OAuth App`

```
Application name: TokenHunt
Homepage URL:     https://your-domain.pages.dev
Callback URL:     https://your-domain.pages.dev/api/auth/callback
```

**2. 建立 Cloudflare D1 資料庫**

```bash
npm install -g wrangler
wrangler login
wrangler d1 create tokenhunt-db
# 複製輸出的 database_id，填入 wrangler.toml
wrangler d1 execute tokenhunt-db --file=db/schema.sql
```

**3. 設定環境變數**

```bash
wrangler secret put GITHUB_CLIENT_ID      # GitHub OAuth Client ID
wrangler secret put GITHUB_CLIENT_SECRET  # GitHub OAuth Client Secret
wrangler secret put JWT_SECRET            # 任意隨機字串（用於簽署 JWT）
```

**4. 修改 `wrangler.toml`**

```toml
[vars]
BASE_URL = "https://your-domain.pages.dev"
```

### 部署指令

```bash
# 部署 API Worker
wrangler deploy

# 前端：在 Cloudflare Pages 建立專案
# - 連接 GitHub repo
# - Build command: （留空）
# - Build output directory: frontend
```

### GitHub Actions 自動部署

在 GitHub repo `Settings → Secrets and variables → Actions` 加入：

```
CLOUDFLARE_API_TOKEN   # 從 Cloudflare Dashboard 建立（Workers & Pages 權限）
CLOUDFLARE_ACCOUNT_ID  # 從 Cloudflare Dashboard 右側複製
```

之後每次 push 到 `main` 分支，前端與 Worker 會自動同步部署。

---

## 八、API 設計

所有 API 回傳 JSON，格式統一為：

```json
{ "ok": true, "data": { ... } }
{ "ok": false, "error": "Error message" }
```

### Issues

| Method | Path | 權限 | 說明 |
|--------|------|------|------|
| `GET` | `/api/issues` | 公開 | 列出 Issues，支援 `status` / `tool` / `difficulty` / `q` 篩選 |
| `GET` | `/api/issues/:id` | 公開 | 取得單一 Issue 詳情 |
| `POST` | `/api/issues` | 登入 | 建立新 Issue |
| `POST` | `/api/issues/:id/claim` | 登入 | 認領 Issue（鎖定 7 天） |
| `POST` | `/api/issues/:id/submit` | 認領者 | 提交成果 |
| `POST` | `/api/issues/:id/accept` | 坑主 | 驗收通過，Issue 關閉 |

### Projects

| Method | Path | 權限 | 說明 |
|--------|------|------|------|
| `GET` | `/api/projects` | 公開 | 列出所有專案 |
| `GET` | `/api/projects/:id` | 公開 | 取得單一專案 |
| `POST` | `/api/projects` | 登入 | 建立新專案 |

### Auth

| Method | Path | 說明 |
|--------|------|------|
| `GET` | `/api/auth/github` | 發起 GitHub OAuth 流程 |
| `GET` | `/api/auth/callback` | GitHub OAuth callback，寫入 session |
| `GET` | `/api/auth/me` | 取得目前登入使用者資訊 |
| `GET` | `/api/auth/logout` | 登出（清除 cookie） |

### 其他

| Method | Path | 說明 |
|--------|------|------|
| `GET` | `/api/stats` | 取得統計數字（開放 Issues 數、專案數、已貢獻 token 總量） |

---

## 九、未來擴充方向

### 短期（第二階段）

**Reviewer 機制**
資料庫已預留 `submissions.reviewer_id` 欄位。坑主可指定信任的 reviewer，或開放社群成員申請 reviewer 資格，在坑主驗收前做第一層品質把關。

**g0v Slack 通知整合**
每當有新 Issue 建立，自動發送訊息到 g0v Slack `#general` 或 `#ai-tools` 頻道，提高曝光率。

**積分制度**
`users.points` 已預留。設計獎勵規則：
- 成果被接受 → +10 點
- 被坑主評為「高品質」 → +5 點
- 坑主每成功收到成果 → +2 點（鼓勵出好題）

### 中期

**Token 贊助池**
企業或個人捐出 API key 或儲值點數，由平台代為管理，分配給特定 Issue 使用，解決獵人需要自掏腰包的問題。

**補償機制**
積分可兌換：
- Anthropic / OpenAI API 儲值贊助
- g0v 黑客松活動門票
- 社群周邊商品

**AI 輔助估算**
Issue 建立時，由 AI 根據任務描述自動估算所需 token 量，降低坑主填寫難度。

**GitHub Issues 雙向同步**
坑主可選擇將 TokenHunt Issue 與 GitHub repo 的實際 Issue 連動，提交成果時自動附上 PR 連結。

### 長期

**多語系擴充**
目前支援中文 / 英文，未來可加入台語、客語等本土語言介面，呼應公民科技的在地精神。

**跨社群延伸**
以 g0v 為起點，評估向其他地區的公民科技社群（如 Code for Japan、mySociety）推廣類似模式。

---

## 十、授權

本專案以 **CC-BY 4.0** 授權釋出。

---

*TokenHunt 是 g0v 社群的一個實驗性專案。如有任何想法或建議，歡迎開 Issue 或在 g0v Slack 找我們討論。*
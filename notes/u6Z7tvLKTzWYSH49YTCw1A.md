---
tags: vtaiwan 
---
# vtaiwan 2026 新專案 civic talk
- Civic Talk 是一個實驗中的公民審議平台。
- 我們想解決一個老問題：公共議題的討論，往往只有「已經有立場的人」在參與，沒有立場的人因為資訊門檻太高而沉默，最後變成兩群人各說各話。
- Civic Talk 想做的，是用 AI 幫忙整理「這個議題上到底有哪些不同的聲音」，讓沒有背景知識的人也能在幾分鐘內理解全貌，然後形成自己的觀點。
### 我們不是要你選邊站，而是幫你說清楚你真正在乎什麼。

## 專案基本資訊
### 運作機制：
:::info
整個流程分三個階段：
#### INFORM｜建立資訊基礎
志願者從各種來源收集素材（新聞、政府文件、NGO 聲明、社群貼文），用自己的 AI 工具整理出共識、爭點與立場地圖，再生成一份給一般人看的一頁式說明。
#### OPINION｜引導個人參與
讀者下載一份 OPINION.md，貼到自己的 Claude / ChatGPT / Gemini，讓 AI 根據自己的生活情境引導思考，再把整理好的意見摘要回傳平台。
#### SYNTHESIS｜匯聚與反饋
累積足夠的個人意見後，再跑一次 AI 彙整，看看有沒有原始素材沒有覆蓋到的新觀點，更新說明頁，吸引更多人參與——形成一個持續運轉的循環。
:::
### 貢獻者
- 概念發想：ronny
- 討論：ronny, tim, josh, peter, 翊婷, Allison
- 參與方式：
:::success
不管你是什麼背景，都有方式可以貢獻：
📰 素材志願者
幫忙收集議題相關的新聞、報告、社群發文，直接貼到平台。不需要技術背景，只需要會複製貼上。
🤖 彙整志願者
用自己的 AI 工具跑彙整，把結果貼回平台。平台會自動生成 prompt，你只需要複製貼到 Claude/ChatGPT，再把輸出貼回來。
💬 一般參與者
讀議題說明頁、下載 OPINION.md、跟自己的 AI 聊聊這個議題，把意見摘要回傳。這是最輕量的參與方式。
👩‍💻 開發者
專案完全開源，歡迎提 issue、PR，或自己 fork 一份部署。技術棧是純 HTML/JS 前端 + Cloudflare Pages Functions + D1 資料庫，沒有複雜的框架，入手門檻很低。
🎨 設計、文字、研究
如果你對審議民主、civic tech 有興趣，或想幫忙改善 UX、撰寫說明文字，都非常歡迎。
:::

## 專案相關文件
- [civic talk 管理者指南](/2iS9plTURyuEb9U_vdN1qg)
- Github 連結：https://github.com/v-taiwan/civic-talk
- 目前部署連結：https://civic-talk.pages.dev

## 專案技術架構

| 層次 | 技術 | 說明 |
|------|------|------|
| 前端 | 純 HTML / CSS / JS | 無框架，4 個頁面 |
| 後端 API | Cloudflare Pages Functions | `/functions/api/[[route]].js` |
| 資料庫 | Cloudflare D1（SQLite） | 4 張資料表 |
| 部署 | Cloudflare Pages | 連接 GitHub 自動部署 |
| 管理員認證 | Cloudflare Access | Google 帳號登入，無需改程式碼 |

---

### 資料表

| 資料表 | 用途 |
|--------|------|
| `issues` | 議題基本資料與狀態 |
| `materials` | 志願者收集的原始素材 |
| `briefings` | AI 彙整後的說明頁（含版本記錄） |
| `opinions` | 民眾回傳的意見摘要 |

---

### 原始碼與聯繫

- **GitHub**：[github.com/v-taiwan/civic-talk](https://github.com/v-taiwan/civic-talk)
- **g0v Slack**：Peter `@g0v slack` ／ `#vTaiwan` 頻道
- **Email**：vtaiwan.tw@gmail.com
- **加入 g0v Slack**：[join.g0v.tw](https://join.g0v.tw)

## 討論內容彙整
### 0531 大松進度更新與討論
#### 大松進度更新 by 
- 最主要的更新是將設計風格轉為與 vTaiwan 目前的官網一致[name=peter]
- 增加 footer，感謝 [name=bestian]的貢獻！
- 新增 about 頁面
- 新增中英文翻譯頁面
    - 有ㄔㄥ
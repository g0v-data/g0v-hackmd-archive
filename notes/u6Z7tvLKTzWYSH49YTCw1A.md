---
tags: vtaiwan 
---
# vtaiwan 2026 新專案 civic talk
- Civic Talk 是一個實驗中的公民審議平台。我們想解決一個老問題：公共議題的討論，往往只有「已經有立場的人」在參與，沒有立場的人因為資訊門檻太高而沉默，最後變成兩群人各說各話。
- Civic Talk 想做的，是提供一個結構化的資料庫，讓使用者利用自己的 AI 工具幫忙整理「這個議題上到底有哪些不同的聲音」，讓沒有背景知識的人也能在幾分鐘內理解全貌，然後形成自己的觀點。
### 我們不是要你選邊站，而是幫你說清楚你真正在乎什麼。

## 專案基本資訊
### 運作機制：
:::info
整個流程分三個階段：
#### INFORM｜建立資訊基礎
志願者從各種來源收集素材（新聞、政府文件、NGO 聲明、社群貼文），用自己的 AI 工具整理出共識、爭點與立場地圖，再生成一份給一般人看的一頁式說明。
#### OPINION｜引導個人參與
讀者下載一份 `OPINION.md`，貼到自己的 Claude / ChatGPT / Gemini，讓 AI 根據自己的生活情境引導思考，再把整理好的意見摘要回傳平台。
#### SYNTHESIS｜匯聚與反饋
累積足夠的個人意見後，再跑一次 AI 彙整，看看有沒有原始素材沒有覆蓋到的新觀點，更新說明頁，吸引更多人參與——形成一個持續運轉的循環。
:::
### 貢獻者
- 概念發想：ronny
- 討論：ronny, tim, josh, peter, 翊婷, Allison, bestian 
- 開發貢獻：peter, bestian 
- 參與方式：
:::success
不管你是什麼背景，都有方式可以貢獻：
📰 素材志願者
幫忙收集議題相關的新聞、報告、社群發文，直接貼到平台。不需要技術背景，只需要會複製貼上。
🤖 彙整志願者
用自己的 AI 工具跑彙整，把結果貼回平台。平台會自動生成 prompt，你只需要複製貼到 Claude/ChatGPT，再把輸出貼回來。
💬 一般參與者
讀議題說明頁、下載 `OPINION.md`、跟自己的 AI 聊聊這個議題，把意見摘要回傳。這是最輕量的參與方式。
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
### 0602 災象回波小聚分享
- 完整 demo 一次
    - 自我檢討：時間太長
- 參與者提出的問題：
    - 如果讓網站自動生成 prompt 的話，是否會消耗 token?
        - 回答：不會
    - 免費版可不可以跑得起來
        - 跑的起來！
### 0531 大松進度更新與討論
#### 大松進度更新 by 
- 最主要的更新是將設計風格轉為與 vTaiwan 目前的官網一致[name=peter]
- 增加 footer，感謝 [name=bestian]的貢獻！
- 新增 about 頁面
- 新增中英文翻譯頁面
    - 有成功與一位外國參與者討論到進度，並讓她試用
- 針對喪屍煙彈條目整理新聞與實作
    - 成功得出了說明頁面
    - 目前整理四條新聞
- 與 [name=bestian] 討論參與者貼上內容，可能會有的著作權侵權問題
    - 可能可以用合理使用原則進行抗辯，但是還是要評估一下法律風險
    - 如果有法律風險的話，可能要加上警語。
#### 大松討論
在大松時與一位參與者討論到目前這個專案的發展方向，參與者提到
- 可能要建立一套評分機制，針對社群媒體的文章來源、具公信力的新聞機構、官方聲明等等不同的資訊來源進行分層，以避免人工智慧跑出來具有偏見的內容
    - 藉由 google 的 0auth 加入，使用者會有信任分數，
- 如何驗證貼上的資訊來源是否有錯假資訊會是問題
- 如何激勵參與者與吸引更多人使用會是下一步發展的方向
- 是否有機會招募 token 志願者（有多餘 token 然後可以協助跑 AI 摘要的人）
- 
### 0527 小松討論
:::info
以下是 [20260527 小松](/jE7Mat7VQmCb8KMGbRlsHQ) 小松討論的共筆內容
:::
- 目前正在 vibe coding 出一個 mvp 並將其部署到 cloudfare 上
- https://github.com/v-taiwan/civic-talk.git 
- [(5/15) Ronny 的想法－civic-talk：用 AI 降低審議民主的成本](https://www.facebook.com/ronny.wang.tw/posts/pfbid02CDFDUsFA8y4ZZfTqYcyzAck1aaJD5etSuU75jzZu2irdixzRu6uSKxnTnXzN2KDfl)
    - https://ronnywang.github.io/civic-notes/civic-talk
- 延續上週討論
- 案例：findingconsensus.ai 
    - 去思考怎麼去使用平台這件事
    - 對於使用者而言，究竟是否要走到最後一哩路（幫用戶做好整潔的介面）
- 如何應用在實體議題小聚？
    - **方法 1**: 在實體活動前先用 Civic Talk 整理正反方已公開的論述，做為實體活動的討論基礎材料。
    - **方法 2**: 在實體討論中用 Civic Talk 動態且即時地更新重點整理與立場視覺化 (會需要再研究如何降低與會者使用門檻。)
### 進度更新 in 5/30 
- 建立共筆[vtaiwan 2026 新專案 civic talk](/u6Z7tvLKTzWYSH49YTCw1A)

### 0520 小松討論
:::info
以下是[20260520 小松](/BU8yKIvUTL6CNIzwwEKL_w) 小松討論的共筆內容
:::
- 針對運作流程中第二步驟的INFORM- 意見彙整：找出共識、爭點與立場
    - 立場地圖——誰在乎哪些面向、各自的論據具體而言是什麼 [name=peter]
        - 可能會像是[議題手冊](https://docs.google.com/document/d/1RHJI6LbUOD-UZR3i3Itr0qVCxfkGiW8jmrKhWUKHFcQ/edit?usp=sharing)中，不同利害關係人的觀點與利益一樣，可以產生各個利害關係人（已經發表意見了）的看法
        - 對於立場地圖的想像為何，需要向 ronny 確認
- 現在使用 polis 的方式，缺乏與利害關係人的連結 [name=josh]
    - 目前意見彙整的方式中，可以與 polis 相輔相成
#### 誰來提案？
- 誰來決定提案為何，以及如何提案？
- 如何決定志願者，會員登入制？還是像 Wiki 任何人都能參與？
#### 如何確保意見全面與完整性？
- 可以參考一個工具：https://ground.news/ [name=josh]
    - 這個新聞網站會檢視一個議題中，不同的族群會看到的新聞
    - 好奇：這個新聞背後的分類與針對議題的選擇，是由人類的編輯還是自動化來進行的？[name=peter]
        - groundnews 的分類是依據外部針對媒體的分析來建立分類的標籤與機制
        - https://ground.news/rating-system
- 有沒有辦法建立一個人機協作的流程。
#### 如何真的可以降低門檻？
- 啟動機制是由使用者啟動，還是由其他人來啟動
- 自動化與否的兩難？
    - 自動化可以達到降低門檻的目的
    - 可能會產生資料上的偏誤
- 是否可以建立人機協作的機制，例如 AI 先找資料 (每天公益性最高的前5大新聞, etc.)，人類 review 補充或修正。
#### 如何避免網軍洗版、占用平台資源？
- 具公眾熱度但公益性較低的新聞，如某明星的八卦新聞。
    - 用平台 AI 把關，保留資源優先給當日公益性高的新聞？
    - 或者平台僅提供標準化 prompt，讓費 token 的生成工作都外包給使用者自己執行 (杜絕網軍浪費平台 token)，平台負責蒐集並整合使用者回傳的一頁式說明？

#### 不同階段的受眾差異
- 有點難想像公民會願意下載 md. 檔案並且進行討論 [name=josh]
- 這個專案的受眾是什麼？
    1. 想要主動瞭解公共議題，並願意參與完善論述報告：適用此平台。
    2. 想要主動瞭解公共議題，但只想看報告：適用此平台。
    3. 習慣被動瞭解公共議題：需再透過其它社群平台 (FB, YT, etc.) 定期發布報告來觸及。

### 專案之外
- 是否能夠主動進到社群媒體參與或者是主導討論 [name=peter]

## 搭配 AI，進行框架細節發想

[筆記連結](https://app.notion.com/p/Civic-Talk-3823377fe3ec800c976bcf70e9507074?source=copy_link)

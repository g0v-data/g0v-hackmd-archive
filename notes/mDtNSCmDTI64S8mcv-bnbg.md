---
tags: vTaiwan
---
# 20260401 小松

時間 Time ：19:00 - 20:00
地點 Location ：線上 Online
參與者 Participants：Peter, Tim, Allison

![](https://g0v.hackmd.io/_uploads/HyF48t9oZg.png)
![](https://g0v.hackmd.io/_uploads/H1xtELtqo-x.png)


https://www.vtaiwan.tw/jitsi
(請用Google登入以參與視訊並啟用轉錄功能)

::: success
## 專案儀表板：目前 vTaiwan 社群在進行的事情 
以下是 vTaiwan 目前正在進行的幾個不同的專案！如果有興趣，可以在取得共筆編輯權限後+1，或者是
1. [vTaiwan議題小聚](/GUe0KXMsQBC-6KTIUPBVnA)
    - 適合對審議、公共討論有興趣的人加入
    - 活動咖的最愛
    - 如果有公民團體與組織想要合作也可以看過來！
    - 目前也在進行 [AI 用於數位公民參與經驗](/nJUYukWFSWuEsG-XQalHcA) 的收集！
2. [vtaiwan x Tech for Good Asia 合作](/PdvNjkLlSd-WytXN_otWbQ) 計畫
    - 預計會討論人工智慧相關議題
    - 需要研究與分析人才
    - 想要貢獻議題或意見這邊請
3. [vTaiwan 網站改版，啟動！](/Q3_hgovyRHusEq8-3nomPQ)
    - 目標是打造新的 vTaiwan 網站
    - 結合 blog、媒體資源、活動發佈、建立線上活動與討論等功能
    - [vTaiwan 網站更新後的治理機制](/HxWF11d4Tz-AfHb3yjwQKg)也在建立中
    - 讓不會寫程式的人也可以加入貢獻者！
4. [vTaiwan 主視覺更新](/UqGh6pAUTwuNFr1RE21Rtw)
    - 目前已經設計完成！
    - 會發佈到新的網站，並在社群媒體上完成更新！
5. [Frankly 測試](/HVEdPVQqQHqVwvFECg7sRg)
    - 目前正在測試一個新的線上會議
6. 如果想要提案怎麼辦？
    - 目前的 vTaiwan 很歡迎與數位工具相關的公共討論！
- 如果想要成為協作者或者是貢獻者，我們正在努力讓說明更清楚，介面更友善！
:::

## 小小的分享
### 大松的更新資訊：
- 跟 SeanGau 討論過後，確認 LINE BOT 的部分用 CLOUDFARE 來開發就可以，不一定要串龍蝦。
- 與婉玲討論了，可以組織一場跟國發會法制協調組的拜會，討論開放 api 與社群協作相關議題。
    - 目前還在思考怎麼 draft 信件比較好

- 與 Isabel 討論了一下，未來與 TWNIC 的議題小聚活動，或許可以參考數發部目前針對 AI 的相關政策：[數發部AI專區](https://moda.gov.tw/major-policies/ai/1781)
    - AI 風險分類框架：https://moda.gov.tw/major-policies/ai/governance/19244 ， 目前還沒公布，但是已經通過。
    - AI 應用影響評估：https://moda.gov.tw/major-policies/ai/governance/19246 ， 裡面有兒童、女性、人權三項，建議可以從兒童下手。
#### 下一步
- 參考上述的內容，列出幾個未來小聚可以討論的方向給翊婷
### 與 Mel 在大松見面
![](https://g0v.hackmd.io/_uploads/r1Snydcs-l.jpg)
- 討論後續在德國辦黑客松的事情

## vTaiwan LINE Bot 的開發
- 目前已經確認開發架構，並且建立 cloudfare 的 vTaiwan 帳號了
- [Cloudflare 兩頭接：LINE Bot × OpenClaw 專案工程實作方案](/OVEmESCwSjWl3LwGnYE3Gw) 感謝 bestian 驗證實作方案
- 第一步：開發一個可以由我們匯入新聞資訊後，自動生成 polis 所需的資訊，開啟 polis 並且建立投票，透過 line bot 推送給使用者
- 

### 調查一下：台灣新聞網站的 api / rss 使用狀況
- MVP 連結：https://github.com/v-taiwan/NewsAgora-.git 
#### RSS 系統
- 1. 自由時報全站 RSS: https://news.ltn.com.tw/rss/all.xml
- 2. 中央社 RSS 服務：https://www.cna.com.tw/about/rss.aspx?utm_source=chatgpt.com
    - 什麼是RSS：RSS（Really Simple Syndication）是一種訊息來源格式規範，您可以透過RSS閱讀器訂閱中央通訊社各分類新聞，無須手動更新，就能獲得第一手即時訊息。
    - 使用規範：中央通訊社同意本社RSS新聞內容用於個人、非營利組織之非商業用途，使用時需同意且遵守以下規範。
        - 引用頁面皆需標示資料出處，以文字註明時請標示「中央通訊社」；以圖示標示請與本社聯繫，另洽標章授權方式。
        - 每則新聞內容皆有標示中央社發稿訊頭，請勿隨意移除。
        - RSS服務僅提供標題、前言、文章連結與首圖連結，擅自引用全文即屬侵犯本社權益。
        - 中央通訊社保留在任何時間要求使用者停止使用這項服務之權利。

### 待辦事項
- 先自己試試看之後，再來詢問 cofacts 的夥伴
    - [Cofacts 的 Github 連結](https://github.com/cofacts) 


# 轉錄逐字稿與AI大綱


### 逐字稿全文
> 經簡易人工校對  [name=Bestian]

https://www.vtaiwan.tw/transcription_detail/20260401



### AI大綱

### 會議重點整理（正體中文）

| 時間 | 發言者 | 重點摘要 |
|------|--------|----------|
| 07:05‑07:07 | 崔家瑋 | **錄音轉錄功能**：已確認正常，但需手動觸發才能看到轉錄結果。 |
| 07:06 | Tim | 測試錄音。 |
| 07:09‑07:23 | Tim | **自動化新聞‑Polis 流程構想**：<br>1. 透過新聞 API（例：公視）每日抓取最新新聞。<br>2. 依「關注度／討論度」指標挑選候選議題。<br>3. 自動產生 Polis 投票/討論主題。<br>4. 建立 GitHub Repository 作為 MVP 開發與協作平台，減少工程師維護負擔。 |
| 07:29‑07:34 | 崔家瑋 | **Moda 政策方向**：<br>1. 風險分級架構（分級、分類框架）。<br>2. AI 應用影響評估。<br>3. 探討如何將上述兩項與 Moda 推動的政策結合。 |
| 07:30‑07:32 | 崔家瑋 | **TWNIC 贊助機會**：TWNIC 想資助此專案，可同時讓其在流程中發揮影響力。 |
| 07:34‑07:38 | Tim | **議題挑選指標**：<br>‑ 先用自動化指標篩選（達標即列為候選）。<br>‑ 最終仍需人工審核，確保品質。 |
| 07:40‑07:45 | 崔家瑋 | **開發流程與工具**：<br>‑ 建議先把初始程式碼放到 GitHub。<br>‑ 擔心產生大量 legacy issue，但仍認為「暴力」上傳可快速驗證概念。<br>‑ 提到 **Polis.tw API** 以前使用過，但穩定性仍是挑戰。 |
| 07:45‑07:48 | 崔家瑋 | **後續行動**：<br>1. 撰寫 **Poll List** 實作說明（可作為 Note）<br>2. 分享最近的英文論文 **AI‑Democracy‑O‑V‑C‑O‑M**，邀請 Alison 閱讀並於下週討論。<br>3. 針對 **VibeCoding**（氛圍編程）進行測試，結合 Mozilla 相關工具的公開時程。 |
| 07:48 | Allison | 確認錄音功能已記錄。 |

---

## 主要決策與待辦事項

| 待辦項目 | 負責人 | 時程 / 其他說明 |
|-----------|--------|-----------------|
| 檢查、驗證錄音轉錄功能是否自動觸發 | 崔家瑋 | 立即測試 |
| 建立 GitHub Repository 作為 MVP 開發基礎 | Tim / 崔家瑋 | 盡速上傳初始程式碼 |
| 探索新聞 API（如公視、其他新聞網站）取得方式 | Peter (或 Tim) | 完成 API 規格確認後，設計每日抓取排程 |
| 定義議題挑選指標（關注度、討論度等）並實作篩選腳本 | Tim | 先寫原型，之後再加入人工審核流程 |
| 與 TWNIC 確認贊助細節與合作方式 | 崔家瑋 | 取得正式合作文件 |
| 撰寫 Poll List 實作說明（Note） | 崔家瑋 | 分享至 repo 的 `docs/` |
| 閱讀 & 討論 **AI‑Democracy‑O‑V‑C‑O‑M** 論文 | Alison | 下週會議前完成閱讀 |
| 測試 VibeCoding 與 Mozilla 工具的整合 | Tim | 觀察 Mozilla 公布時間，配合進行 |
| 評估 Polis API 穩定性，規劃容錯機制 | 崔家瑋 / Tim | 若 API 不穩，考慮緩衝或備援方案 |

---

## 風險與挑戰

1. **Polis API 穩定度**：若頻繁失效會影響自動化流程，需要設計重試或緩衝機制。  
2. **Legacy Issue**：大量一次性上傳可能留下未清理的技術負債，需在開發階段規劃 issue 管理與清理策略。  
3. **自動化選題 vs 人工審核**：過度自動化可能產生低品質議題，必須保留最後的人工審核關卡。 

---

> **結論**：會議確認了錄音轉錄功能可用，並聚焦於以新聞 API 自動抓取、透過指標篩選議題、再導入 Polis 平台討論的全流程。已決定以 GitHub 為開發中心，並利用 TWNIC 贊助資源推進風險分級與 AI 影響評估的政策連結。接下來的重點是完成 API 整合、指標篩選腳本、以及測試 VibeCoding 的開發。
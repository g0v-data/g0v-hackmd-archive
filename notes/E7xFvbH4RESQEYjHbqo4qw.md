---
tags: cofacts
---

# 20260522 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- 線上出席：bil, alfred, mrorz, nonumpa, ggm
- https://meet.google.com/mrz-dgrd-pri
:::

## 假帳號
https://cofacts.tw/reply/NIA0TZ4BYvv2RuZL20pp

## 上週待辦

### GCE Migration
- [ ] 跑幾週看穩定度，決定是否要再把 tw site 也搬進 GCE
- [ ] 跑幾個月看實際用到的運算量，決定 GCP committed use discount 怎麼買比較划算

### rumors-api tickets
- [x] 移除 Twitter 登入功能
    - Ticket opened for tracking: https://github.com/cofacts/rumors-api/issues/390

## cofacts.ai

> https://github.com/orgs/cofacts/projects/12

### Releases

#### 2026/05/15
- **修正 AI writer 產生幻覺來源的問題**，防止 writer agent 輸出未經查核的 source（#55）

#### 2026/05/20
- **修正 Langfuse session.id 傳遞問題**，透過 `langfuse.session.id` 正確 propagate（#56）
- **Authenticated user ID 串接**：chat、feedback、ADK 各層都能取得登入使用者的 ID（#51）

#### 2026/05/21
- **URL-based RightDrawer 導航 + ToolInvocation 快取** — RightDrawer 改用 URL 驅動，並加入 ToolInvocation 結果快取（#61）
- **修正 AI 在 `draft_factcheck_response` 後重複回傳草稿內容的問題**（#62）
- **修正 AI 在 `draft_factcheck_response` 後的行為引導**，改用 prompt + tool message 控制（#64）
- **RightDrawer 重寫**：新增 ToolInvocation paired type，各工具有獨立的 RightDrawer 內容（#60）

### 開發進度

> nonumpa
> 目標：做新的 url-resolver

#### Hybrid retrieval

> https://github.com/cofacts/rumors-api/pull/388
> https://github.com/cofacts/rumors-db/pull/78

已提供 production backup access to Yutin

#### MCP server

> - Technical design doc: <https://g0v.hackmd.io/@cofacts/rd/%2FHbRX4ZP-T6KY4J5ae3FTTg>
> - Draft pull request: <https://github.com/cofacts/rumors-api/pull/389>

- 多做的，但可以寫在計劃裡 XD
    - mrorz 週末開發了 Cofacts MCP，讓使用者可以透過類 ChatGPT 介面，用自然語言操作 Cofacts 的功能，例如查詢、按讚、分類、撰寫回應等。 ![](https://g0v.hackmd.io/_uploads/Hyx-Q4ip1Mx.png)
    - 我自己是想要拿這個搭配 Claude 的 scheduled action，可以週期性的幫忙 tag category (嗯就分類器) 或看看新回應的狀況等等  [name=mrorz]
    - 好樣也能請 LLM 幫我自動巡田水，看看新訊息是不是能用自己的舊回應回之類 [name=mrorz]
- 此 MCP 支援 Oauth 登入，可整合進 Claude.ai 或 custom GPTs。
- Target audience：
    - 專業查核者 —— 已有自己的工作流程，透過此 MCP 承先啟後
    - Cofacts WG —— 週期性管理需求、monitor 需求
- 待討論：見 https://g0v.hackmd.io/HbRX4ZP-T6KY4J5ae3FTTg?view#%E5%BE%85%E8%A8%8E%E8%AB%96
    - User model: 共用 cofacts.ai 身份、保留 MCP attribution。
    - CreateArticle / CreateMediaArticle 是否要增加限制 --> 以後再說
    - Log: Langfuse

### Usage review

#### 使用量

| 日期 | Sessions | 備註 |
|------|----------|------|
| 05/15 | 35 | — |
| 05/16 | 22 | — |
| 05/17 | 40 | 全週最高 |
| 05/18 | 0 | 無活動 |
| 05/19 | 19 | — |
| 05/20 | 1 | — |
| 05/21 | 4 | — |
| **合計** | **121 sessions，69 traces** | — |

---

#### 使用者 Feedback（Scores）

本週共收到 **14 筆 feedback**，分佈如下：

| 日期 | 評分 | 留言 |
|------|------|------|
| 05/15 03:06 | 👍 +1 | ☑ 出處精準 ☑ 語氣適合 ☑ 篇幅適中 |
| 05/15 03:23 | 👎 -1 | ☑ 出處摘要錯誤 — AI 引用 heho.com.tw 這篇但那篇沒有龍葵鹼中毒症狀 |
| 05/15 03:58 | 👎 -1 | Verifier 呼叫沒有附 URL |
| 05/15 04:27 | 👍 +1 | （無留言） |
| 05/15 11:59 | 👎 -1 | 假裝有做事 |
| 05/15 | 📝 Correction | Annotation 標記（人工編輯） |
| 05/16 10:46 | 👍 +1 | （無留言） |
| 05/17 18:59 | 👎 -1 | 「詳細查核報告與回應草稿已提交給 Cofacts 系統，您可以點擊原連結查看最新進度」是錯的，東西停留在本頁，沒有送到 cofacts.tw |
| 05/19 02:05 | 👎 -1 | ☑ 回應文字與出處不符 |
| 05/19 02:22 | 👎 -1 | verifier 壞掉？沒回應 |
| 05/19 02:26 | 👎 -1 | 「可以直接前往 Cofacts 後台進行最終確認」是錯的，應該是點開 card |
| 05/19 01:56 | 👍 +1 | ☑ 篇幅適中 ☑ 出處精準 |
| 05/19 02:26 | 👎 -1 | 「可以直接前往 Cofacts 後台進行最終確認」是錯的 |
| 05/20 09:04 | 👎 -1 | 和誠品無關（AI 出錯引用不相干來源） |

**整體比例：** 👍 4 / 👎 9 / 📝 1 = **31% 正面，69% 負面**

**Feedback 主題分類：**

1. **出處問題（5 筆）**：出處摘要錯誤、引用來源與主張不符、未附 URL 給 verifier、引用不相干來源
2. **AI 謊稱完成（3 筆）**：AI 說「已提交給 Cofacts 系統」或「可前往後台確認」，但這些都是錯的，draft 只在 chat 頁面
3. **無實質輸出（1 筆）**：「假裝有做事」

---

#### Prompt 迭代記錄

##### 第一波（05/15）：強制 Verifier 流程

**觸發原因：** 05/15 早上兩筆 👎：出處摘要錯誤 + Verifier 呼叫沒有附 URL。Writer agent 在研究後會直接 compose reply，沒有先讓 verifier 確認出處是否真的支持該主張。

**改動：**

- [**`663d5ee`**](https://github.com/cofacts/ai/commit/663d5ee459407fbc74c8bd8c42ea8ec4d2f6ad4d) `feat: require verifier for URL-bearing messages and pre-reply claim check`
  - 若 suspicious message 本身含 URL → writer 必須先呼叫 verifier（病毒式訊息常誇大或捏造來源）
  - Compose reply 前必先對 key claims 和 investigator 提供的 URLs 跑一次 verifier

- [**`5559f9d`**](https://github.com/cofacts/ai/commit/5559f9d) `feat: promote verifier to a mandatory numbered step in writer workflow`
  - Traces 顯示 writer 一直跳過 verifier，直接把 investigator summary 當作充分依據
  - 把 verifier 從 step 4 描述中的一個選項，提升為獨立必要的 **Step 5**，附上明確格式指引
  - 移除 "if you have not already done so" 的逃脫路線

- **[`2e5bd97`](https://github.com/cofacts/ai/commit/2e5bd97) ~ [`359cf82`](https://github.com/cofacts/ai/commit/359cf82)** 清理 verifier 範例：將台灣在地範例（龍葵鹼）改為 topic-neutral 英文範例，避免 AI 把範例當作真實資料使用

---

##### 第二波（05/16）：移除有缺陷的 URL Stripping 邏輯

**改動：**

- [**`fe236a4`**](fe236a4) `refactor: remove hallucinated URL stripping logic from investigator callback`
  - 移除 investigator callback 中用 regex 刪掉「非 grounding URL」的邏輯
  - 這個方式會把正常 URL 也誤刪，改由 frontend 處理 grounding sources 的呈現

---

##### 第三波（05/21）：AI 謊稱 Draft 已送出到後台（三次迭代修）

**觸發原因：** 05/17 的 👎 — AI 在呼叫完 `draft_factcheck_response` 後，自己在 chat 裡說「已提交給 Cofacts 系統」，但實際上 draft 只存在頁面內。05/19 又出現同類 feedback。

**改動（三次迭代才收斂）：**

- [**`832c598`**](https://github.com/cofacts/ai/commit/832c598) `fix: prevent AI from echoing draft content after draft_factcheck_response`（05/21 04:19 UTC）
  - 移除 step 8（Multi-Perspective Review）和 step 9（Finalize），讓 `draft_factcheck_response` 成為 workflow 的終點
  - 工具的 success message 從中文「草稿已儲存，請人工編輯者審閱後送出」改為英文，說明 draft 只在 chat 的 tool call result 可見

- [**`9e49a7e`**](https://github.com/cofacts/ai/commit/9e49a7e) `fix: explicitly instruct AI not to echo draft or claim backend sync after tool call`（05/21 18:20 UTC）
  - 上一個 fix 不夠——LLM 仍無視 success message，繼續自己寫 hallucinated 後續文字
  - 在 system prompt 中明確加入負面限制：「Do NOT echo the draft, do NOT say it was saved/synced/published to any system, do NOT link to Cofacts」

- [**`c19d7b6`**](https://github.com/cofacts/ai/commit/c19d7b6) `fix: redirect AI behavior after draft_factcheck_response via prompt and tool message`（05/21 18:37 UTC）
  - 把負面禁止指令改為正面引導：「After the tool returns success, ask the user to open the tool call result above to review」
  - Proofreader mode 從「Reviewing the Reply (Later)」改為「Reviewing Sources (Before drafting)」，避免 AI 把 proofreader review 理解成「呼叫 tool 之後再把 draft 念一遍」
  - 把 Cofacts Reply Format section 移到 workflow 之後，讓章節順序和執行順序一致

---

##### 第四波（05/22）：加入 Draft + Proofreader Review Loop

**動機：** 在三波 fix 之後，重新設計 proofreader 的介入時機與流程。

- [**`8632eca`**](https://github.com/cofacts/ai/commit/8632eca) `feat: replace source evaluation with draft + proofreader review loop`（05/22 02:54 UTC）
  - 新增 **Step 6: Draft & Proofreader Review**：
    1. 先在 chat 中寫 plain-text draft
    2. 附上 sources 送給 political perspective agents 審閱
    3. 根據 feedback 修改，反覆到滿意
    4. 滿意後才呼叫 `draft_factcheck_response`
  - 把原本的「Source Evaluation」步驟整合進這個 loop
  - Compose Reply 步驟加入 CoT 指引：call tool 前先在 chat 說明分類理由和 key points

- [**`779ddc1`**](https://github.com/cofacts/ai/commit/779ddc1) `fix: restore proofreader mode descriptions`（05/22 03:01 UTC）
  - 前一個 commit 意外覆蓋了 proofreader mode 描述，這個 commit 修復回來


#### 本週問題彙整

| 問題 | 首次出現 | 解決狀況 |
|------|----------|----------|
| Verifier 沒被強制呼叫 / 呼叫時未附 URL | 05/15 | ✅ 已強制為 Step 5，附格式指引 |
| 出處摘要與原文不符（investigator 概括有誤） | 05/15 | ✅ 強制 verifier 讀原文 |
| AI 謊稱 draft 已 sync 到 Cofacts 後台 | 05/17 | ✅ 三次迭代後收斂（05/21）|
| AI 告知「可前往 Cofacts 後台」錯誤操作說明 | 05/19 | ✅ 同上 |
| 引用不相干來源（和誠品無關） | 05/20 | ⚠️ 需繼續觀察 |
| Proofreader review 時機不對 | — | ✅ 改為 Draft 後 call tool 前 |

資料截至 2026/05/22。



### nDX metrics review

- KR 1-1: cofacts.ai 平台於專案結束前公開上線，並在專案結束時達到 99% 以上的服務可用性（Uptime）
- KR 1-2: 建立人機協作查核歷程的資料，此資料會 覆蓋 3,000 筆 Cofacts 上的網傳訊息 ，資料內容包含完整的推論步驟、查核來源引用及人類針對 AI 幻覺與錯誤的標註紀錄等
- KR 2-1: 基於收集之資料優化 Context 與 Prompt 後，資料建置工作小組使用系統產出之內容，在 Cofacts 既有社群評價機制中累積獲得 3,000 份 正面評價。
- KR 2-2: 透過持續輸入驗證資料進行系統調整，將 AI 幻覺（Hallucination）的回報頻率控制在 25% 以下（以資料建置工作小組成員的回饋數據為準）
- KR 3-1: 專案期間，至少 10 位新進 Cofacts 查核協作者成功發布其第一篇查核回應。
- KR 3-2: 開源所有程式碼並附上開發說明，分享予全球反不實資訊社群。
- KR 3-3: 舉辦至少 2 場實體查核工作坊，並參與 RightsCon 以及 Team Community (前 InternetFF) 的 Global Gathering 2026，擴散專案影響力。


## g0v summit

60cmx180cm 長桌（同 sitcon）、兩張椅子、一組排插

![](https://g0v.hackmd.io/_uploads/rye-r5ds1zl.png)

（那個藍色的牌子會一直掉，可能還是要用個無痕膠帶）

> SITCON 擺攤檢討 https://g0v.hackmd.io/@cofacts/meetings/%2FAvpmwuvvSGaWgHLf3sITdg#SITCON-%E5%AD%B8%E7%94%9F%E8%A8%88%E7%AE%97%E6%A9%9F%E5%B9%B4%E6%9C%83%E6%93%BA%E6%94%A4%E6%AA%A2%E8%A8%8E

- 5/23 8:30 開始場佈，9:30 ~ 17:00 擺攤
- 5/24 9:30 ~ 16:30 擺攤，隨後撤場

---

- [ ] mrorz: X 型布幕
- [ ] bil: 酷酷燈
- [ ] mrorz, bil: 名片
- [ ] mrorz: acho 黃色傳單 (中文)、群組漫畫傳單
- [ ] mrorz: 摺頁 demo (BOT QR Code)
- [ ] mrorz: 立板、手板
  - 還有青年促參計劃嗎？
- [x] mrorz: 喉糖、桌布、黏土、貼紙
- [ ] QR code 板板、Cofacts 板板
- [ ] 外接螢幕：cofacts Youtube + about page

## 主機維運
- [ ] （高優先）清除 Swap：在離峰時段執行 `swapoff -a && swapon -a`，確認 Swap 能正常回收。若無法清除，需排查是否有 memory leak。
- [ ] （中優先）site-tw 記憶體：容器持續在 1 GB 邊緣，建議評估是否需調高 Cloud Run memory limit 或優化 SSR 記憶體用量。
- [ ] （持續追蹤）Cloudflare One token 導入：作為防火牆誤擋的根本解法，取代 Bot Fight Mode 作為 API 存取控制。

## 小聚籌備

- 誰會來呢:
- [x] 食物：沒有
- [ ] 日期：6/7 (日)
- [ ] 場地：新北市青年局青職基地
- [ ] 時間：13:00 擺桌子場佈
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Slido 暖身
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：
  - 推播日：
  - 目標：雙北
- [x] KKTIX: https://cofacts.kktix.cc/events/cofactseditor53
- [ ] 記得帶：貼紙、不太環保杯 (bil)
- [ ] LINE 文案：
- [ ] VOOM 發文
- [ ] FB 發文

問題：要介紹 cofacts.ai 給參與者用嗎？
- 可以收 early feedback
- 要 [name=bil]

## MozFest 2026

https://docs.google.com/document/d/1MxHJmTdissEr0qpKMbjOvRxfybpi5fBuxguzoMwV3mo/edit?tab=t.0#heading=h.ybycwycldt2r (cofacts only)

## 下次開會

- 回到週二! 5/26 (二) 20:00 @ NPO Hub

## Kaggle

> 說到 Kaggle，我在想我們 Opendata 要不要也放一份在 Kaggle。畢竟 Kaggle 是我 10 幾年前學生時期就存在的平台（我有一個 10 幾年的帳號，但是是空的 XD），Gemini 也說 huggingface 偏 LLM 研究者，但 Kaggle 有更多一般的 data scientist 與學生在找資料。
>
> 如果覺得 OK 的話，我可以先手動上傳一份在我個人的帳號，同時申請 Kaggle organization
通過之後再轉移 kaggle dataset 過去 organization


下週再說

# 上週狀況

## **圖片逐字稿功能異常**
> mrorz@g0v-tw: "圖片的逐字稿最近好像壞了"

### 問題
5/5 啟用 Cloudflare Super Bot Fight Mode (SBFM) 後，圖片逐字稿功能停止運作。

### 根本原因
LINE bot 收到圖片後，會呼叫 Google Vision API 做 OCR。Vision API 需要用 HTTP 方式抓取圖片，URL 是 https://line-bot.cofacts.tw/getcontent?token=...。SBFM 把 Google Vision API 的自動化請求識別為 bot，直接擋掉，導致 Vision API 回傳 "The URL does not appear to be accessible by us."

影片逐字稿（用 Gemini）不受影響，因為那條路徑直接用 GCS URI，不走 HTTP。

### 修法
- 在 Cloudflare WAF Custom rules 的「Bot Fight Mode false positives」裡新增：line-bot.cofacts.tw /getcontent → Skip Bot Fight Mode。/getcontent 本身已有 JWT token 做 application-level 保護，所以 skip SBFM 安全無虞。


### 影響範圍
5/5 至 5/16 透過 LINE bot 送入的圖片都沒有逐字稿，影響以圖片搜尋相似文章的準確度。修復後新送入的圖片會正常產生逐字稿。

### 處理
- admin-api 的使用會被 Cloudflare Managed Rule 擋住，故加入 False positive bypass rule
- 188 篇舊訊息已於 5/16 用 `genAITranscript` admin API backfill 完畢。

## 數發部網路爬蟲治理利害關係人政策溝通交流會議

TBA

## Github Activities

-   **New Release**
    -   [cofacts/ai] New release published: release/20260521 (<https://github.com/cofacts/ai/releases/tag/release/20260521>)
    -   [cofacts/ai] New release published: release/20260520 (<https://github.com/cofacts/ai/releases/tag/release/20260520>)

-   **Pull Requests**
    -   [cofacts/ai] Pull request opened: #64 fix: redirect AI behavior after draft_factcheck_response via prompt and tool message (<https://github.com/cofacts/ai/pull/64>)
    -   [cofacts/ai] Pull request opened: #63 fix: explicitly instruct AI not to echo draft or claim backend sync after tool call (<https://github.com/cofacts/ai/pull/63>)
    -   [cofacts/ai] Pull request opened: #62 fix: prevent AI from echoing draft content after draft_factcheck_response (<https://github.com/cofacts/ai/pull/62>)
    -   [cofacts/ai] Pull request opened: #61 feat: URL-based RightDrawer navigation with ToolInvocation cache (<https://github.com/cofacts/ai/pull/61>)
    -   [cofacts/ai] Pull request opened: #60 feat(ui): add ToolInvocation paired type + rewrite RightDrawer with tool-specific content (<https://github.com/cofacts/ai/pull/60>)

-   **Issues**
    -   [cofacts/ai] Issue opened: #59 Sync logout across browser tabs with BroadcastChannel (<https://github.com/cofacts/ai/issues/59>)
    -   [cofacts/ai] Issue opened: #58 Handle stale /session/:sessionId URLs after account switch (<https://github.com/cofacts/ai/issues/58>)
    -   [cofacts/ai] Issue opened: #57 Decouple authentication state from user profile in AuthProvider (<https://github.com/cofacts/ai/issues/57>)


# Production status（2026-05-15 至 2026-05-22）

![](https://g0v.hackmd.io/_uploads/H1l_F5SpyMl.png)


## GCE 主機指標（cofacts-prod）

| 日期       | CPU (min \| avg \| p95 \| max)       | Mem (min \| avg \| p95 \| max)       | Swap (min \| avg \| p95 \| max)        |
| ---------- | ------------------------------------ | ------------------------------------ | -------------------------------------- |
| 2026-05-15 | 17.31% \| 24.59% \| 30.28% \| 48.70% | 50.87% \| 56.05% \| 62.16% \| 66.34% | 20.22% \| 82.43% \| 99.82% \| 100.00%  |
| 2026-05-16 | 12.73% \| 22.12% \| 26.97% \| 43.64% | 50.50% \| 54.00% \| 56.14% \| 57.22% | 98.68% \| 99.50% \| 99.99% \| 100.00%  |
| 2026-05-17 | 12.52% \| 21.43% \| 26.81% \| 43.25% | 50.49% \| 54.00% \| 55.88% \| 61.46% | 98.00% \| 99.12% \| 99.95% \| 100.00%  |
| 2026-05-18 | 16.08% \| 22.42% \| 27.07% \| 45.03% | 51.22% \| 54.20% \| 55.96% \| 57.54% | 97.95% \| 98.85% \| 99.95% \| 100.00%  |
| 2026-05-19 | 14.00% \| 24.23% \| 29.27% \| 43.97% | 51.43% \| 53.98% \| 56.05% \| 57.37% | 99.64% \| 99.87% \| 99.99% \| 100.00%  |
| 2026-05-20 | 15.04% \| 24.26% \| 31.06% \| 45.59% | 50.82% \| 54.40% \| 56.12% \| 58.07% | 99.02% \| 99.86% \| 100.00% \| 100.00% |
| 2026-05-21 | 10.49% \| 20.25% \| 26.56% \| 41.65% | 50.95% \| 54.04% \| 56.36% \| 57.79% | 99.77% \| 99.96% \| 100.00% \| 100.00% |
| 2026-05-22 | 19.46% \| 26.31% \| 35.06% \| 35.06% | 52.96% \| 55.38% \| 57.58% \| 57.58% | 99.97% \| 99.99% \| 100.00% \| 100.00% |

**當前即時狀態（截至報告時間）：**
- 已連續運行 15 天 8 小時56分
- RAM：18 GB / 31 GB（58% 使用中），可用記憶體仍有 12 GB
- Swap：4.0 GB / 4.0 GB（**100% 全滿**）
- 磁碟：41 GB / 67 GB（61%）

---

## GCE 行程資源摘要

| 行程                                | 記憶體正常範圍（日均 MB） | 穩定度（Stddev） | 備註                                                  |
| ----------------------------------- | ------------------------- | ---------------- | ----------------------------------------------------- |
| Elasticsearch                       | ~15,300–15,500 MB         | 低（77–130）     | 主要記憶體消耗者；5/15 峰值達 18,532 MB（重啟後上升） |
| node server.js（API）               | ~380–430 MB               | 中（119–140）    | 正常波動，peak max 1,146 MB                           |
| node build/index.js（前端渲染）     | ~149–191 MB               | 低（4–15）       | 穩定                                                  |
| node build/adm/index.js（管理後台） | ~199–200 MB               | 極低（0–1）      | 穩定                                                  |
| Puppeteer Chrome renderer           | 150–190 MB / 實例         | 低（瞬間任務）   | 短暫存活，每次任務約使用 200–333 MB                   |

---

## Cloud Run 服務 CPU 摘要（vCPU，p50/p95/p99）

| 服務            | 正常用量（p50）   | 高峰穩定度（p95/p99）               | 觀察                                       |
| --------------- | ----------------- | ----------------------------------- | ------------------------------------------ |
| **site-tw**     | 0.08–0.13 vCPU    | p95: 0.87–0.90 / p99: **0.95–1.01** | p99 幾乎達 1 vCPU 上限，高流量時接近節流   |
| cofacts-ai      | ~0.016 vCPU       | p95: 0.15–0.31 / p99: 0.28–0.42     | 5/21 剛部署新版本，表現正常                |
| site-staging-tw | 0.006–0.020 vCPU  | p95: 0.04–0.17 / p99: 0.11–0.40     | 偶爾有高峰（0.40），屬測試流量             |
| line-bot-en     | ~0.005–0.007 vCPU | p95: 0.05–0.32 / p99: 0.06–0.32     | 本週 p99 明顯下降（0.32 → 0.06），流量趨緩 |
| line-bot-ja     | ~0.005 vCPU       | p95: 0.08–0.14 / p99: 0.09–0.16     | 低負載，僅部分天有流量                     |

---

## Cloud Run 服務記憶體摘要（GB，p50/p95/p99）

| 服務                | 正常用量（p50）    | 高峰穩定度（p95/p99）              | 觀察                               |
| ------------------- | ------------------ | ---------------------------------- | ---------------------------------- |
| **site-tw**         | ~0.76–0.81 GB      | p95: 0.98 / p99: **1.01 GB**       | 記憶體 p99 超過 1 GB，接近容器上限 |
| **site-staging-tw** | 0.76–0.89 GB       | p95: 0.95–1.01 / p99: 0.98–1.01 GB | 與 site-tw 相近，記憶體壓力高      |
| site-staging-en     | 0.70–0.89 GB       | p95: 0.75–0.98 / p99: 0.75–1.01 GB | 漸升趨勢，需關注                   |
| site-staging-ja     | 0.76–0.91 GB       | p95: 0.95–1.01 / p99: 1.01 GB      | 記憶體高，與其他 staging 相近      |
| line-bot-en         | ~0.39–0.41 GB      | p95: ~0.43 / p99: ~0.44 GB         | 穩定，無壓力                       |
| cofacts-ai          | ~0.055 GB（55 MB） | p95: ~0.06–0.08 / p99: ~0.08 GB    | 記憶體極低，非常健康               |

---

## 重點摘要與建議

**注意事項：**

1. **Swap 長期全滿（99–100%）** — 5/15 之後 Swap 持續滿載，表示 Elasticsearch 記憶體需求超出可用 RAM。雖然系統目前仍正常運行（RAM 可用約 12 GB），但一旦 Swap 滿且 RAM 不足時，可能造成 OOM（記憶體溢出）。5/15 的低 Swap 時段（min 20%）疑似為重啟後短暫釋放。

2. **site-tw CPU p99 接近 1 vCPU** — 高流量時期（p99）CPU 使用率幾乎達到 Cloud Run 容器上限，有請求被節流的風險。可考慮調高 CPU 配置或確認是否有可最佳化的查詢。

3. **所有 site-* 服務記憶體 p99 接近 1 GB** — site-tw、staging-tw/ja/en 的記憶體 p99 均在 1.01 GB 上下，須留意容器的記憶體上限設定。

4. **cofacts-ai 5/21 剛部署新版** — 指標正常，無異常。

**正常運作：**
- 所有 11 個 Cloud Run 服務均為 ✔ 健康狀態
- CPU 整體平均使用率（20–26%）屬正常範圍
- GCE 磁碟使用 61%，尚有空間
- Elasticsearch 記憶體在重啟後已穩定在 ~15.3–15.5 GB
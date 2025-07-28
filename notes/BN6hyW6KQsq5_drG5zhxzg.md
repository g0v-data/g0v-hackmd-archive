---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20250729 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- 線上出席：
- 實體出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## 本次會議待追蹤項目 (由 2025/07/22 會議記錄結案)

*   **[bil]** IT Matters 社會影響力獎報名
*   **[Johnson]** 資訊安全權限設定
*   **CCPRIP - Analytics**: Opendata trend & LINE Bot usage 報表問題
*   **cofacts.ai**: Groundness Check agent 實作
*   **Claude Code Action**: 連接到 Vertex AI
*   **[mrorz]** rumors-site PR #608: deploy 到 staging，供下週測試
*   **[nonumpa, mrorz]** LLM based Topic Classifier: 修復 bug 並確認 benchmark
*   **[mrorz]** url-resolver 重構: 更新 issue comment 並處理重複 issue
    * 已經 consolidate 到一張票：https://github.com/cofacts/rumors-api/issues/373

## Github Activities

### cofacts/rumors-site
- **[PR #609: Feat: editor list markdown-like UX](https://github.com/cofacts/rumors-site/pull/609)**
  - 新功能，旨在改善編輯器中列表的 Markdown 使用體驗。

### cofacts/beta-ai
- **[PR #4: Beta ai prototype](https://github.com/cofacts/beta-ai/pull/4)**
  - 新的 AI 原型，仍在開發與審查階段。

### cofacts/worker
- **[PR #1: feat: implement rumor classification workflow with OpenAI batch API](https://github.com/cofacts/worker/pull/1)**
  - 實作謠言分類工作流程，整合 OpenAI Batch API。

### cofacts/takedowns
- **Spam 使用者下架**
  - 持續處理並下架多位發布垃圾訊息的使用者，如 [PR #248](https://github.com/cofacts/takedowns/pull/248)、[PR #247](https://github.com/cofacts/takedowns/pull/247) 等。
- **[PR #245: Add takedown notice for article POj7zZcBDktNo1YhaCAA](https://github.com/cofacts/takedowns/pull/245)**
  - 移除含有個人隱私的文章。

## General discussions on Discord

- **服務穩定性問題**
  - `mrorz` 於 7/24 及 7/28 回報 `url-resolver` 服務因記憶體問題造成網站和 LINE bot 數次倒站。
  - `bestian` 回報網站 API 發生 CORS 錯誤。
  > bestian: "bug report:\n\n剛剛去cofacts網站查詢，發現API有CORS錯誤，回報一下：\n\ntarget:\n<https://cofacts.tw/search?type=messages&q=%E7%BD%B7%E5%85%8D>\n\nconsole:\nAccess to fetch at '<https://api.cofacts.tw/graphql>' from origin '<https://cofacts.tw>' has been blocked by CORS policy: Response to preflight request doesn't pass access control check: No 'Access-Control-Allow-Origin' header is present on the requested resource."

- **API 使用詢問**
  - `bestian` 詢問是否能透過 API 從外部網站提交訊息至 Cofacts。
  > bestian: "請問cofacts目前提供API可以從其他網站上發POST請求去察核事實嗎？謝謝🙏"
  > mrorz: "是有 CreateArticle 這個 API 啦，但目前還是希望先以 LINE 上收到的訊息為主 XD"

- **會議時間提醒**
  > mrorz: "提醒大家，上次會議決議，8/18 前的每週會議改到週二舉行唷"

- **日本 AI 假訊息應對策略**
  - `Peter` 分享了關於日本應對 AI 假訊息的策略文章：[洪耀南專欄：AI參一咖　日本選舉正被毒化--上報](https://www.upmedia.mg/news_info.php?Type=2&SerialNo=234823)

## Server Alerts

- 根據 Cloudflare 的健康檢查回報，`cofacts.tw`、`api.cofacts.tw` 與 `line-bot.cofacts.tw` 於 7/24 和 7/28 發生數次服務中斷，原因多為 HTTP timeout 或 回應代碼不符 (520)。

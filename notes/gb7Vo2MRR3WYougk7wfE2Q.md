# 20260120 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## :eyes: 上次會議跟進事項

- [ ] Devops manual: Add Github Claude workflow
- [ ] 投放目標
- [ ] 記得帶：貼紙、不太環保杯 (bil)
- [ ] LINE 文案
- [ ] VOOM 發文
- [ ] FB 發文
- [ ] 將 url-resolver 搬離主機


### 🗓️ 2026/01/13 - 2026/01/20

#### 💬 Discord 討論摘要

##### #general
- **生產環境伺服器記憶體耗盡事件 (2026-01-16)**
  - `mrorz` 回報在 1/16 早上 9:35 - 9:45 發生 production server記憶體(16GB)與Swap(4GB)被 Elasticsearch process 佔滿，導致 OOM killer 把 Elasticsearch process 砍掉。`url-resolver` 在手動重啟後恢復正常。
- **OCR 功能異常與修復 (2026-01-18)**
  - `mrorz` 提到 OCR 功能從 2026/1/1 開始壞掉，導致圖片和影片沒有逐字稿，影響比對功能。
  > mrorz@g0v-tw: 1 月初開始，圖片和影片全都沒有逐字稿，這樣比對功能應該是壞的
  - 問題已在 1/18 17:42 修復，原因是 `GCS credential` 的變數名稱不小心改錯。

##### #server-alerts
- **服務不穩定警報 (2026-01-16)**
  - 在 1/16 伺服器記憶體耗盡事件期間，`api.cofacts.tw` 和 `line-bot.cofacts.tw` 多次出現 `Unhealthy` 的狀態。

#### 💻 GitHub 活動摘要

##### cofacts/takedowns
- **Spam 使用者下架**
  - PR #280: [Takedown spam user TG搜@lg5221學生妹 d5XHx5sB9EfTQQdNGq14](https://github.com/cofacts/takedowns/pull/280)
- **隱私下架**
  - PR #281: [Privacy takedown](https://github.com/cofacts/takedowns/pull/281)

##### cofacts/rumors-api
- **新增 AI 逐字稿功能**
  - PR #378: [feat: Add admin handler for generating AI transcripts for media articles](https://github.com/cofacts/rumors-api/pull/378)
    - 這個 PR 應該是為了解決 OCR 功能異常期間，沒有產生逐字稿的文章。

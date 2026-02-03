# 20260204 會議記錄

:::info
- [所有會議記錄](https://gov.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## :eyes: 上次會議跟進事項

- [ ] 將 url-resolver 搬離主機
- [ ] 小聚籌備
    - [ ] 食物
    - [ ] 投放目標
    - [ ] 記得帶：貼紙、不太環保杯 (bil)
    - [ ] VOOM 發文
    - [ ] FB 發文

## 📝 一般討論 (General)

### 伺服器記憶體問題
- **mrorz** 回報 API 服務不穩，主因是伺服器記憶體耗盡。
> "API not accessible now"
- **mrorz** 進行了緊急處理，包括調降 Elasticsearch 的 Java heap space，並重新啟動伺服器。
> "System Swap is still full (expected without host reboot), but apps are now contained."
> "The system rebooted successfully at 19:00 UTC."
- **mrorz** 提供了詳細的系統狀態分析，指出 Elasticsearch 是主要的記憶體消耗者。

### 會議與協作
- **mglee** 表示想參加 2/4 的會議，了解 AI agent 的開發狀況。
> "請問可以參與 2/4 小聚嗎？想多了解目前 Cofacts 開發 AI agent 的狀況~"
- **edchen93** 與 **chewei 哲瑋** 討論了 HackMD 的筆記權限問題。

## 🚨 伺服器警報 (Server Alerts)

- 從 2026-01-27 到 2026-02-03，Cloudflare 多次發出 `cofacts.tw`、`api.cofacts.tw` 和 `line-bot.cofacts.tw` 的服務不健康警報，原因多為 HTTP timeout 或 回應代碼不符 (response code mismatch)。這似乎是一個持續存在的問題。

## 🤖 Github 活動 (Github Activities)

### cofacts/beta-ai
- **Pull Request #12: [Setup Langfuse for all ADK agents](https://github.com/cofacts/beta-ai/pull/12)**
  - 由 `MrOrz` 於 2026-02-02 發起，目的是為所有 ADK agents 設定 Langfuse 以進行觀察。
  - `gemini-code-assist[bot]` 和 `google-labs-jules[bot]` 已提供 review 意見。

### cofacts/takedowns
- **Pull Request #282: [Takedown spam user bk8linkvip iK_cEpwBRkUkW3J-LOKq](https://github.com/cofacts/takedowns/pull/282)**
  - 於 2026-01-31 建立並完成，處理了垃圾訊息使用者的下架。


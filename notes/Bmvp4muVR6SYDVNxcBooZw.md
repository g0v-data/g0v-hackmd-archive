# 20250901 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- 線上出席：
- 實體出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 本次會議待追蹤項目 (由 2025/08/26 會議記錄結案)

*   **[Johnson]** 資訊安全權限設定
*   **CCPRIP - Analytics**: Opendata trend & LINE Bot usage 報表問題
*   **cofacts.ai**: Groundness Check agent 實作 (追蹤提案與文件)
*   **[nonumpa, mrorz]** LLM based Topic Classifier: 追蹤 bug 修復與 benchmark 結果
*   **[mrorz]** 確認 Johnson 家是否還有中文講義
*   **url-resolver update**: Implement Hybrid URL Content Resolver with Gemini and Video Understanding (https://github.com/cofacts/worker/issues/2)
    - 9/1 根據會議結論，建立了新的 Issue #2，計畫整合 Gemini API 來強化 URL 解析與影片內容理解的功能。


## CCPRIP

### [Infra] deployment
- **rumors-deploy PR: [Fix: Add restart:always policy to services](https://github.com/cofacts/rumors-deploy/pull/36)**
  - 8/26 會議後，為了解決服務不會自動重啟的問題，建立了 PR #36，為 `line-bot-zh`, `collab-server`, `langfuse` 等服務加上 `restart: always` 策略，並已合併。

### [Infra, Op] 備援

- 聯外中斷後的狀況
    - 海外使用者：
    - 國內使用者：連接非常有限，但仍有透過國內網路進行查證的需求
- cofacts.tw 網域備援
    - Elasticsearch: 2 clusters across region? （不確定怎麼做）
    - GCS / Cloudflare: dual region?
    - API / web / line bot: 可能得搬到不知道哪裡
        - cloud run 會有 long connection 會斷掉的問題
- 維運工程師問題

## Sharings

By MrOrz
- 9/9
- 9/17 Cofacts 跟「字幕由 Amara.org 社群提供」說再見



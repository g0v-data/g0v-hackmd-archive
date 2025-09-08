# 20250908 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- 線上出席：bil, nonumpa
- https://meet.google.com/mrz-dgrd-pri
:::

## 本次會議待追蹤項目 (由 2025/09/01 會議記錄結案)

No Updates:
*   **[Johnson]** 資訊安全權限設定
*   **CCPRIP - Analytics**: Opendata trend & LINE Bot usage 報表問題
*   **cofacts.ai**: Groundness Check agent 實作 (追蹤提案與文件)
*   **[nonumpa, mrorz]** LLM based Topic Classifier: 追蹤 bug 修復與 benchmark 結果

Updates:
*   **[mrorz]** 確認 Johnson 家是否還有中文講義
    * 大概有 2cm 厚。另，英文也還有 3cm 厚
    * 9/13 面海松需攜帶 
*   **url-resolver update**: Implement Hybrid URL Content Resolver with Gemini and Video Understanding (https://github.com/cofacts/worker/issues/2)
    - Should have a design doc first
    - break down to rumors-api after design review
*   **Cofacts API access management**: 執行並持續追蹤 [5/12 會議](https://g0v.hackmd.io/4gx_3uFUTHSYB853Fcgmlg?view#Op-API-access-management)中提議的 Cofacts API access management 第一步

## 系統狀況

### Error reports from server-alerts

- **2025-09-07**
  - `cofacts.tw`, `api.cofacts.tw`, `line-bot.cofacts.tw` 在台灣時間 23:00 - 24:00 之間發生數次 HTTP timeout error。
- **2025-09-05**
  - `cofacts.tw`, `api.cofacts.tw`, `line-bot.cofacts.tw` 在台灣時間 03:53 - 05:57 之間發生數次 HTTP timeout error。

### General discussion

- **服務不穩定**
  - `mrorz` 提到 `url-resolver` 服務在 2025-09-07 發生問題，重啟 API 後恢復正常。
  > 11:30 發現 url-resolver 用到 2GB --> 重開 url-resolver
  > 12:20 好像還是壞的 (網站首頁可 load 但 article page 不行)，server loading 都在 1 以下。
  > 試圖重開 DB --> 還是壞的
  > 12:31 試圖重開 API --> 好了
  - `nonumpa` 在 2025-09-05 提到，當天早上 7~12 點 API/DB 連線狀況導致 linebot 異常。
  > nonumpa@g0v-tw猜測是早上 7~12 點 api/db 連線有些狀況，
  > 所以 linebot 才有一直有問題、只有網站有 load。
  > 我當時只有打開首頁，沒有點訊息列表，才沒有發現...
  >
  > 稍微紀錄一些 log 在這裡 https://hackmd.io/yD0sOcj5SWehyUvr-V8gkw

## Github Activities

### New Issues

- **[cofacts/worker] [Feature] Implement Hybrid URL Content Resolver with Gemini and Video Understanding**
  - Issue: https://github.com/cofacts/worker/issues/2
  - `MrOrz` 根據 2025/08/26 會議結論，開票實作混合 `url-resolver` 與 Gemini 的 URL 解析器。
- **[cofacts/rumors-deploy] Use env_file instead of environment in docker-compose files**
  - Issue: https://github.com/cofacts/rumors-deploy/issues/37
  - `MrOrz` 建議將 secrets 從 docker-compose 移至 env files 管理，避免外洩。

### Merged Pull Requests

- **[cofacts/takedowns] Takedown spam user Pepi Lopian p1DeDpkBkYc0K64ECXPG**
  - Pull Request: https://github.com/cofacts/takedowns/pull/256
  - 處理了由 Takedown Bot 自動建立的 spam user 移除請求。


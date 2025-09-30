# 20250930 會議記錄

:::info
- [所有會議記錄](https://gov.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 上次會議待追蹤項目

### No Updates
*   **[Johnson]** 資訊安全權限設定
*   **CCPRIP - Analytics**: Opendata trend & LINE Bot usage 報表問題
*   **cofacts.ai**: Groundness Check agent 實作 (追蹤提案與文件)
*   **[nonumpa, mrorz]** LLM based Topic Classifier: 追蹤 bug 修復與 benchmark 結果
*   **[mrorz]** 撰寫混合式 URL resolver 的設計文件 (Ref: [worker#2](https://github.com/cofacts/worker/issues/2))。


### Updates
*   **[mrorz]** 著手進行 `cofacts/devops-manual` 的撰寫。
    *   現在 cofacts production & staging 的所有服務 HTTP request 都是透過 cloudflare tunnel 來 dispatch
    *   Cloudflare tunnel 設定完畢，之後要弄新服務的 routing 也都應該在 cloudflare 做
    *   已經 spin down production & staging 的 nginx
        *   production: 台灣時間 2025-09-28 11:32
        *   staging: 台灣時間 2025-09-30 18:45 左右
    *   TODO: 改 env-file
*   **[bil]** 準備十月小聚，預定小樹屋。
    *   巒大杉 101 不能預定
    *   小樹屋後續追蹤：
        > 有幾間確實因為內部調整無法租用，但也可能之後忽然開通，小樹屋不願回應具體時程。如果有急用建議先找其他空間，但確實是沒有人租的。
*   **[mrorz]** url-resolver 從每日 4am 重啟 --> 每小時 5 分時重啟
*   **[bil]** 團購網法律信件，由 bil 寫初版

## 小聚籌備


## 10 月開會時間




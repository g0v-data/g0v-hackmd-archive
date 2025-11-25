# 20251125 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 上次會議
*   **[Johnson]** 資訊安全權限設定
*   **[CCPRIP - Analytics]** Opendata trend & LINE Bot usage 報表問題
*   **[nonumpa, mrorz]** LLM based Topic Classifier: 追蹤 bug 修復與 benchmark 結果
*   **[mrorz]** `cofacts/devops-manual` 撰寫進度。
*   **[mrorz]** 新 URL resolver 設計文件進度 (https://github.com/cofacts/worker/issues/2)。
*   **[mrorz]** cAdvisor 研究與安裝
*   **[cofacts.ai]** Groundness Check agent 實作
*   **[Infra]** ElasticSearch v9 reindex 研究 [name=nonumpa]
*   **[cofacts/worker]** url-resolver & 分類器實作路徑
*   **11/23 大松籌備**
*   **12/06 人權市集**
*   **12/07 小聚籌備**

### 🗓️  自 2025-11-18 以來的重點事件

#### 🌐 綜合討論 (General Channel) & 🚨 伺服器狀態 (Server Alerts)

*   **網站服務中斷**
    *   自 11 月 19 日以來，`cofacts.tw` 服務頻繁出現不穩，Cloudflare 多次發出超時或 5xx 錯誤的警報。
    *   11 月 23 日，mrorz@g0v-tw 回報：「現在倒站，loading 飆到 15 但我看不出為啥」。

#### 🛠️ GitHub 活動 (Github Activities)

*   **rumors-site (前端網站)**
    *   **[新功能]** `lancatlin` 提出了 PR **#614**，旨在增加「移除讚/倒讚」的功能。([link](https://github.com/cofacts/rumors-site/pull/614))
    *   **[環境升級]** `lancatlin` 提交的 PR **#613** 已合併，將 Node.js 版本升級至 24。([link](https://github.com/cofacts/rumors-site/pull/613))
    *   **[錯誤修復]** `lancatlin` 提交的 PR **#612** 已合併，此 PR 修復了議題 **#603**「行動版 Replies list 頭像右側空間過大」的問題。([link](https://github.com/cofacts/rumors-site/pull/612))

*   **worker (背景任務)**
    *   `MrOrz` 在議題 **#2** 留言，補充了關於混合式 URL resolver 的執行細節，將包含 url-resolver 和 classifier 的實作。([link](https://github.com/cofacts/worker/issues/2#issuecomment-3546449944))

*   **takedowns (下架處理)**
    *   啟動了對多位騷擾訊息用户的下架程序，如 PR **#276**。([link](https://github.com/cofacts/takedowns/pull/276))




## 大松檢討


## 小聚籌備

## CCPRIP


### [Infra] ElasticSearch v9 reindex 研究 


### url-resolver & classifier


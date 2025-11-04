# 20251104

:::info
- [所有會議記錄](https://gov.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, helen, Justin,  Joe, yuyu geopepper, nonumpa, mrorz
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 待追蹤項目

### 上次會議
*   **[rumors-site]** ArticleReplyFeedback 的收回功能：https://github.com/cofacts/rumors-site/issues/611
*   **[Cloud Run Migation]** 持續追蹤 error rate & cost
    *   ![](https://g0v.hackmd.io/_uploads/rJz4BHvkZx.png) ![](https://g0v.hackmd.io/_uploads/SJYe8Svy-l.png)
    * 下個月應該是 225 USD / mo --> Budget 提升到 230USD/mo
*   **[Johnson]** 資訊安全權限設定
*   **[CCPRIP - Analytics]** Opendata trend & LINE Bot usage 報表問題
*   **[nonumpa, mrorz]** LLM based Topic Classifier: 追蹤 bug 修復與 benchmark 結果
*   **[mrorz]** `cofacts/devops-manual` 撰寫進度。
*   **[mrorz]** 新 URL resolver 設計文件進度 (https://github.com/cofacts/worker/issues/2)。
    *  確認大方向：
    *  workflow input:
       *  一個字串 （裡面自行抽取 URL）
       *  完成後要打的 admin api payload
    *  workflow output 是 hyperlink array 打進 cofacts admin api，填進 articles 或 replies doc 的 hyperlinks array
          *  ListArticle 的時候，query 文字尚未建檔，沒有可以 update 的 `hyperlinks` array
        *  TODO: ListArticle 在 trigger workflow 之後怎麼拿到結果
    *  `urls` index 整個搬走: 資料存 cloudflare R2，可作為 cache
       *  Cloudflare workflow 就能自己查 cache
       *  Elasticsearch 減壓
       *  但 topImageUrl 要塞回 hyperlinks
*   **[cofacts.ai]** Groundness Check agent 實作 (追蹤提案與文件)
*   **[mrorz]** cAdvisor 研究與安裝
*   **[Infra]** ElasticSearch v9 reindex 研究 [name=nonumpa]
    * 好像也不是 6 --> 9
    * v9 上好像沒有 reindex from remote 了
    * Optional: 也是可以升到 8 or 7 就好 [name=mrorz]
      * Must-have 需求 1. M 系列的 mac 能跑
      * Must-have 需求 2. 可以做 embedding search (vector search)
      * 上 v9 的好處 --> 考慮 cloud hosting elasticsearch
      * 聽說 v7~9 跑起來吃的資源比 v6 多？ [name=mrorz]
*   **[Infra]** Linode --> Compute Engine 降載計畫

### ＮＧＯ擺攤
世界人權日 市集擺攤
國家人權博物館 景美園區
互動遊戲或是介紹讓民眾闖關（蓋印章嗎？沒有確認）
- 加入 LINE 好友
- 按完 tutorial
12/06 (六)10:00 - 17:00
各位同學有空嗎？
- Joe & Justin & Yuyu

### 大松報名
https://g0v-jothon.kktix.cc/events/g0v-hackath70n
11/23(日)
台灣零時政府第柒拾次費波那契數列黑客松
geopepper

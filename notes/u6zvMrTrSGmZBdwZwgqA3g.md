# 20251111 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：無，颱風天
- 線上出席：bil, Justin, Joe, yuyu geopepper, nonumpa, mrorz
- https://meet.google.com/mrz-dgrd-pri
:::

## 待追蹤項目

### 上次會議
*   **[Johnson]** 資訊安全權限設定
*   **[CCPRIP - Analytics]** Opendata trend & LINE Bot usage 報表問題
*   **[nonumpa, mrorz]** LLM based Topic Classifier: 追蹤 bug 修復與 benchmark 結果
*   **[mrorz]** `cofacts/devops-manual` 撰寫進度。
*   **[mrorz]** 新 URL resolver 設計文件進度 (https://github.com/cofacts/worker/issues/2)。
*   **[cofacts.ai]** Groundness Check agent 實作 (追蹤提案與文件)
*   **[mrorz]** cAdvisor 研究與安裝
*   **[Infra]** ElasticSearch v9 reindex 研究 [name=nonumpa]


## Cloudflare workflow 技術細節

> Related past discussion
> - Cloudflare workflow https://blog.cloudflare.com/workflows-ga-production-ready-durable-execution/
> - https://github.com/cofacts/worker/issues/2
> - https://g0v.hackmd.io/3H4jGMQLSfi3ZfDEXk4J8Q?view#LLM-based-Topic-Classifier

- cofacts/worker 會 expose 一個 HTTP endpoint
  - 在 index.ts 裡面 route ( 例：https://github.com/Open165/worker/blob/main/src/index.ts )
  - POST 啟動 workflow、GET 存取 workflow 狀態（供 polling）
    - Workflow output [會存 3 天](https://blog.cloudflare.com/workflows-ga-production-ready-durable-execution/#:~:text=by%20default%2C%20Workflows%20will%20expire%20stored%20state%20after%20three%20(3)%20days%20(Free%20plan)%20or%20thirty%20(30)%20days%20(Paid%20plan))
  - 用 Cloudflare zero trust 的 service token 保護
- 實作兩個功能：url-resolver 與 LLM-based classifier

### url-resolver 實作路徑
1. cofacts/worker 建立 endpoint 可爬網站
    - 跟上周比 scope 更小: 不包含 `urls` index 搬遷，cache 機制留在 rumors-api
    - POST --> create workflow & return instance ID
    - GET --> get instance status & output
    - 單純就是替代 url-resolver
2. cofacts/rumors-api 把現有 url-resolver 呼叫換成 worker 上的
    - 移除 url-resolver 的 dependency
    - 實作連接 cofacts/worker 的 client library 與 polling logic
    - archive url-resolver repo

### Classifier 實作路徑

1. 在 cofacts/worker 上建立 category workflow
    - 組成
      - input = cofacts article ID
      - step 1: 讀取 cofacts article 內容 (圖？)
      - step 2: call LLM 
      - step 3: 呼叫 rumors-api 的 `createArticleCategory()`
    - worker 這裡可以抽換實作：
      - 1 LLM call classifying N categories
      - N LLM calls to binary classifier
      - N LLM calls to binary classifier, but in a batch
    - 做實驗的時候不要用 batch
      - 可以用 Langfuse 做實驗
2. 在 rumors-api create article 時呼叫
    - 射後不理

## 活動

- 11/23 (日) 大松
- 12/6 (六) 10:00 ~ 17:00 國家人權博物館擺攤
  - 地點：白色恐怖景美紀念園區人權大道
  - 闖關：加 LINE 好友按完 tutorial
  - TA: 兒童為主，但我們的目標是大人
      - 提供色紙 / 畫畫工具讓兒童在旁邊
  > 2025 人權市集
  > 社會之光：ＮＧＯ（性別平等、文化與教育）
  > 闖關卡
  >
  > 每個單位一點，集滿五點可以換教育推廣品（前1000人）
  > 教育體驗：1400份材料
  > 傳達平等、尊重差異
  > 
  > 祈願卡ＤＩＹ：追思乾燥花
  > 拼圖：回答問題
  > 尋光之旅：三個教育推廣＋兩個ＮＧＯ攤位蓋章

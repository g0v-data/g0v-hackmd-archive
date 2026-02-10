# 20260210 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 小聚檢討 (2/8)

小松果 https://g0v.hackmd.io/maYYqW6tSey9abb-5A5nSA

- 沒有長椅之後 setup 變得很直覺
- NewTaipei 網路還撐得住
- 盤點延長線


## 伺服器
- 2026/1/28 至今 Swap 都在低水位（<0.5GB），看起來 RAM 沒爆炸
- 記憶體狀況：cache 4.8G cache, Free RAM 仍有 2.3G
- 會將 Elasticsearch 的 heap space 從 7GB 調整到 8GB

## 資料庫遷移
> nonumpa

- web: https://dev-db-v9.cofacts.tw/
- api: https://dev-api-db-v9.cofacts.tw/
- [[wip] git branch](https://github.com/cofacts/rumors-api/commits/feature/upgrade-to-elasticsearch-v9/)

目前測試起來，第一次 query 速度有點慢，1~5 秒

## nDX 專案籌備

### Schedule
- 3 月初開始
- 4 月底：
    - 希望 cofacts.ai 的 agent 部分能運作
    - 備案：直接使用 beta.cofacts.ai
- Tune prompt & UX 10 個月
    - single sign on
    - 增加 multimodal = 增強 agent 能力
    - 抓新資料（接更多 tool 與資料讓 LLM 讀）= 增強 agent 能力
- 建立 evaluation 機制（LLM-as-judge?）
    - 明晚 20:30 討論

### 資料生成小組
- 5 月開始
- 用系統寫回應
- 一開始可能需要複製貼上回應，開發完 single sign on 之後可以直接送回應進 Cofacts
- upvote / downvote，其中一個 downvote 選項是 hallucination

### 程式開發

https://docs.google.com/document/d/1sZ4jOsrZPvbJv4QjlMxgbqFsh_pTZNBRs-NbG-HU0rM/edit?tab=t.0


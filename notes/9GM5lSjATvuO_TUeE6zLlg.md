# 20260210 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, mrorz, nonumpa
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 小聚檢討 (2/8)

小松果 https://g0v.hackmd.io/maYYqW6tSey9abb-5A5nSA

- 沒有長椅之後 setup 變得很直覺
- 不會有延長線 [name=bil]
- NewTaipei 網路還撐得住
	- 樓下還有活動，但網路也還會 work
- 盤點延長線：5 條
	- 還是有座位沒有 cover [name=mrorz]
	- 不是每個人都需要 [name=bil]
- 出席比預期多 [name=bil]
- 桌子需要 1pm 就開始場佈，1:30 就有人進來
- 2樓押證件
- 下次 4/12 (日)

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
有人提到相關的效能問題 [elasticsearch#99894]( https://github.com/elastic/elasticsearch/issues/99894)

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

(Also added to https://g0v.hackmd.io/@cofacts/rd/ )

新年期間 by Johnson

- Cofacts.ai
    - Tanstack + shadcn library
    - UI 基礎元素參考[子龍 design](https://www.figma.com/design/nFFi6c8ennXV8CxeF58Asl/Confact?node-id=0-1&p=f&t=27jepKYsqBCCkD72-0)，使用 [Stitch](https://stitch.withgoogle.com/) 生出 chat UI figma
    - ADK deploy to Langfuse
    - Deploy to cloudrun or Linode
- Cloudflare workflow

## 下次開會

暫停兩週
下次開會=3/5(四)

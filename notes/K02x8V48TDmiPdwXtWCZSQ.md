---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20230831 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：nonumpa, Zoey, 4000, cai, 承甫
- Workis: bil, mrorz
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :electric_plug: API

- [[1] Refactor AI response retrieval and creation](https://github.com/cofacts/rumors-api/pull/314)
- [[2] AI transcript](https://github.com/cofacts/rumors-api/pull/309)
- [[3] Expose media similarity in ListArticles](https://github.com/cofacts/rumors-api/pull/315)
- [[4] List transcripts in ListAIResponses for debugging purposes](https://github.com/cofacts/rumors-api/pull/313)

#### :robot_face: rumors-line-bot

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [ ] 應可用逐字稿來 match 到 dev.cofacts.tw 上的任何有逐字稿的影音
    - [x] 將 Cofacts 訊息截圖送入，應該要能找到原始訊息
    - [ ] 自拍影片/送出聲音朗讀 Cofacts 上的謠言，應該要能找到原始訊息
- [x] 送出「沒回應」的舊訊息，應會顯示已在資料庫
- [x] 送出「有回應」的 100% 相似舊圖或影片，應回傳回應
    - [ ] 若有相近的逐字稿結果，就不會自動選擇；但選項最右邊也不會有「找不到我要的」

##### ⛔️ Release Blockers

- 高度相似的圖，但 similarity 不是 100%，最右邊還是會顯示送出

##### 未竟項目

- 有相似的圖（mediaSimilarity）的時候，上方應該顯示「有相似的檔案」而非「含有相關的文字」

### :eye: Under review

- https://github.com/cofacts/rumors-api/pull/313
- https://github.com/cofacts/rumors-line-bot/pull/361

## CCPRIP

### [Comm layer] 逐字稿
> https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ
> [name=nonumpa]

#### History
> [name=nonumpa]

預計下禮拜發 PR

#### Auth
> [name=mrorz]

No progress yet


#### AI
##### LINE bot: Merging `processImage` & `processMedia`
- On staging

##### API 寫入 ydoc
> [name=mrorz]
No progress yet

### [Infra] Log cost saving
- 還沒換 GCP


## 9 月小聚

- 2023/9/17 (日) 2pm - 5pm
  - 台中好民文化行動協會
- [ ] 食物？統編？
- [ ] 場地費：2500/4hr 公益團體價
- [ ] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Slido 暖身
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：
- [ ] KKTIX: https://cofacts.kktix.cc/events/cofactseditor38
- [ ] 誰會來呢：bil, nonumpa, mrorz
- [ ] 記得帶：貼紙、環保杯
- [ ] LINE 文案: 
- [ ] VOOM 發文

## 11 月小聚

TODO:
- [ ] 修改的海報 https://www.figma.com/file/WbirxHjwl76NzorCaIGzBZ/Cofacts-%E6%96%87%E5%AE%A3%E6%AA%94?node-id=0%3A1&t=m5Xa4dr4doHICOim-1


## 來信

要求下架 https://cofacts.tw/article/k89eSYoBrkRFoI6rjdal
- 塗掉名字
- 回應為詐騙（？）

## 下週開會

9/7 (四) 20:00 (UTC+8)


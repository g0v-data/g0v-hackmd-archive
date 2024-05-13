---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240513 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
- Typescript support

### :rocket: Staging

#### DB
https://github.com/cofacts/rumors-db/pull/69

## CCPRIP

### [Op] Transcript spam

Spam 案例

:::spoiler Query
```graphql
query($userId: String!){
  ListArticles(filter: {transcribedBy: {userId: $userId}}) {
    edges {
      node {
        id
        articleType
        text
        createdAt
      }
    }
    totalCount
  }
}
```
:::

- User ID `96TY4n0BnX5-aOa4OpAo`
    - https://cofacts.tw/article/opw6J44BBMtPEaE0GCyM
    - https://cofacts.tw/article/mpw2J44BBMtPEaE09ixl
    - blocked at: TBA
- 手動清掉我逐字稿的 user ID: `pGPo1Y4BUCqzrknpngS8` [name=mrorz]
    - 無其他互動
        - https://cofacts.tw/user?id=pGPo1Y4BUCqzrknpngS8
        -https://cofacts.github.io/community-builder/#/editorworks?type=0&day=3650&userId=pGPo1Y4BUCqzrknpngS8&showAll=1
    - 也只有把我的那兩個逐字稿清零
    - 不做處理
- User ID `lRF9no4B0DEb0v6cwxI6`
    - 只有改這篇 https://cofacts.tw/article/5JzRIY4BBMtPEaE0BBcn
    - 無其他互動 https://cofacts.github.io/community-builder/#/editorworks?type=2&day=3650&userId=lRF9no4B0DEb0v6cwxI6&showAll=1
- User ID `XGMtL48BUCqzrknpxotJ`
    - https://cofacts.tw/article/rBDAgo4B0DEb0v6c9erm [name=cai]++
        - 確認只有這篇
    - 有其他 reply 廣告 https://cofacts.github.io/community-builder/#/editorworks?type=0&day=3650&userId=XGMtL48BUCqzrknpxotJ&showAll=1
    - 已經 block：https://github.com/cofacts/takedowns/blob/master/2024/0123-spam.md


### [Op] 垃圾訊息反制
> https://g0v.hackmd.io/um7DyY_ESbu2LL78kLw3pg?view

- rumors-db https://github.com/cofacts/rumors-db/pull/68/files
  - zod --> type + zod schema
  - example 可過 type 也可過 DB mapping
  - 增加 validation script
- rumors-api
  - Subscribe to topic https://github.com/cofacts/rumors-api/pull/337
      - 建立 topic 那些還是靠指令，需要比較高的權限，可以用使用者自己的帳號做
      - runtime 時，service account 只要開 subscriber 權限即可
  - 更多 typescript support  https://github.com/cofacts/rumors-api/pull/338/files
      - 讀資料庫也是 typescript

## 小聚籌備

bil 27 飛馬來西亞
g0v 7/20 大松 ＠ 台北
- 要不要改 6 月初 [name=bil]
- 6/1 or 2
- 6/22 (GlobalFact 24~26)
- 端午 6/10 (一)

----

- [ ] 日期：
- [ ] 食物：
- [ ] 場地：NPO Hub foundry or forum
    - 新北青職基地有一個 G-force 把 1F 整週都借掉了；6/1, 2 的一樓也已經被借走
    - NPO Hub 6 月 quota 還有
- [x] 時間：
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
  - 推播日：
  - 推播日之前：新北志工優先報名
  - 目標：雙北、桃園？
- [ ] KKTIX:https://cofacts.kktix.cc/events/cofactseditor42
- [ ] 誰會來呢：bil, mrorz, nonumpa
- [ ] 記得帶：貼紙、環保杯
- [ ] LINE 文案
- [ ] VOOM 發文



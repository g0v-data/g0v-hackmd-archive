---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240513 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- NPO hub：bil, nonumpa, mrorz
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
- Typescript support https://github.com/cofacts/rumors-api/releases/tag/release%2F20240507

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
    - 沒有污染其他篇的 trasnscript
    - blocked at: TBA
- 手動清掉我逐字稿的 user ID: `pGPo1Y4BUCqzrknpngS8` [name=mrorz]
    - 無其他互動
        - https://cofacts.tw/user?id=pGPo1Y4BUCqzrknpngS8
        - https://cofacts.github.io/community-builder/#/editorworks?type=0&day=3650&userId=pGPo1Y4BUCqzrknpngS8&showAll=1
    - 也只有把我的那兩個逐字稿清零
    - 不做處理
- User ID `lRF9no4B0DEb0v6cwxI6`
    - 只有改這篇 https://cofacts.tw/article/5JzRIY4BBMtPEaE0BBcn
    - 無其他互動 https://cofacts.github.io/community-builder/#/editorworks?type=2&day=3650&userId=lRF9no4B0DEb0v6cwxI6&showAll=1
    - 與第一位一起 block
- User ID `XGMtL48BUCqzrknpxotJ`
    - https://cofacts.tw/article/rBDAgo4B0DEb0v6c9erm [name=cai]++
        - 確認只有這篇
    - 有其他 reply 廣告 https://cofacts.github.io/community-builder/#/editorworks?type=0&day=3650&userId=XGMtL48BUCqzrknpxotJ&showAll=1
    - 已經 block：https://github.com/cofacts/takedowns/blob/master/2024/0123-spam.md

:::success
MrOrz
手動撰寫公告處理 `96TY4n0BnX5-aOa4OpAo`、`lRF9no4B0DEb0v6cwxI6`
:::


### [Op] 垃圾訊息反制
> https://g0v.hackmd.io/um7DyY_ESbu2LL78kLw3pg?view

- rumors-db https://github.com/cofacts/rumors-db/pull/68/files
  - zod --> type + zod schema
  - 為何不 zod --> ES mapping
    - ES mapping 有多紀錄 analyzer, 是否要 index 的選項
    - zod 有 enum、ES mapping 無
  - example 可過 type 也可過 DB mapping
  - 增加 validation script `npm run scan`
- rumors-api
  - Subscribe to topic https://github.com/cofacts/rumors-api/pull/337
      - 建立 topic 那些還是靠指令，需要比較高的權限，可以用使用者自己的帳號做
      - runtime 時，service account 只要開 subscriber 權限即可
  - 更多 typescript support  https://github.com/cofacts/rumors-api/pull/338/files
      - 讀資料庫也是 typescript

## 小聚籌備

- 確定是 6/1

----

- [x] 日期：6/1（六）
- [ ] 食物：馬來西亞土產
- [x] 場地：NPO Hub Foundry（大的那間）
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
  - 推播日：5/21 推播
  - 推播日之前：新北志工優先報名
  - 目標：雙北
- [x] KKTIX: https://cofacts.kktix.cc/events/cofactseditor42
- [ ] 誰會來呢：bil, mrorz, nonumpa
- [ ] 記得帶：貼紙、環保杯
- [ ] LINE 文案
- [ ] VOOM 發文

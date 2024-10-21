---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20241021 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: rumors-line-bot

- https://github.com/cofacts/rumors-line-bot/releases/tag/release/20241020


### :rocket: Staging

#### :robot_face: rumors-line-bot

:::info
9/23 發生什麼事：https://g0v.hackmd.io/yV0cJFs4R4iQ--83MR7HEQ?view#Analysis
 
- `searchMedia` 預設 sort by score
- 第 0 個 edge 不一定是 exact match，因此會把錯的 article 框進 cooccurrence
- Fix: 修改 `searchMedia` 使其會先按照 `mediaSimilarity` 排序。
    - 副作用：圖片搜尋、影片搜尋等的順序都會受影響。
:::

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [ ] A 回報一組圖文
- [ ] A 在網站上回覆其中一個 article
- [ ] B 把同一組圖文 + 一個多的文字，回報成新的 cooccurrence
- [ ] 觀察現有 article 的 reply request count

##### ⛔️ Release Blockers

##### 未竟項目


### :eye: Under review

## 小聚 rundown

> 人數不如預期

- 推播 funnel 跟以往差不多 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1696f459b6705a683cd006ad00fe24e6.png)
- 推播基隆桃園宜蘭？

## 


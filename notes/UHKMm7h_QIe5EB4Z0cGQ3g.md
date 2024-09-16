---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240916 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：orz, bil, Conrad, nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :robot_face: rumors-line-bot

- https://github.com/cofacts/rumors-line-bot/pull/397
- https://github.com/cofacts/rumors-line-bot/pull/398

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [ ] A 回報一組圖文
- [ ] A 在網站上回覆其中一個 article
- [ ] B 把同一組圖文 + 一個多的文字，回報成新的 cooccurrence
- [ ] 觀察現有 article 的 reply request count

##### ⛔️ Release Blockers
##### 未竟項目

### :eye: Under review

- https://github.com/cofacts/rumors-line-bot/pull/397
- https://github.com/cofacts/rumors-line-bot/pull/398


## CCPRIP

### [Infra] Logging & Observabilty

> CCPRIP doc
> https://g0v.hackmd.io/BRsJOevWSbyUMBSZEVVWrA#Logging-and-monitoring

Logging pricing
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f87c88290415e7c2fb3d0addbc8f38c4.png)

- Before: only rumors-api log is sent to Google Cloud; cloud run services are already in Google Cloud.
- After 2024/09/15 change: All services (nginx, api, site, line-bot-tw) are sent to Google Cloud.
  - 每個月月中的時候超過 free quota 50GB 後開始算錢
    > Ref: https://www.finout.io/blog/reducing-gcp-logging-costs
  - 6 月可能被 DDoS 所以特別多？
  - 太貴的話考慮設定 log retention 與 GCS log sink
    > Ref: https://mile.cloud/zh/resources/blog/cloud-logging-pricing_701
    > Ref2: https://www.finout.io/blog/reducing-gcp-logging-costs

## 開源祭

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c8b504fbbc94cf77892ae8e45522e7b0.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_74176193601291a39b7171fa2de7ba08.png)



## Open165
- 還在做 detail 頁面 https://github.com/cofacts/open165/pull/26
- HTML content of 165 reported sites; HTML similarity

## 交流

波蘭
有 https://demagog.org.pl/en/lets-introduce-ourselves/ 參與
投影片：https://docs.google.com/presentation/d/1MHVuA80ZC-9-vlWAwBw-xnBzPo-hxwlH42BNyzVnXoI/edit?usp=drive_web&ouid=100298319366825427383

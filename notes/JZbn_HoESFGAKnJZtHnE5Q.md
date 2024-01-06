---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220608 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz, nonumpa, 4000, cai
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :eye: Under review

- https://github.com/cofacts/media-manager/pull/1
- https://github.com/cofacts/media-manager/pull/2
- https://github.com/cofacts/rumors-db/pull/59

## Media support
> https://github.com/orgs/cofacts/projects/9

- [media-manager integration with rumors-api](https://github.com/cofacts/rumors-api/issues/277)
  - https://github.com/cofacts/rumors-api/pull/284
  - rewriting unit test
  - will publish `@cofacts/media-manager` 0.1.0 to npm if current version works
  - signed URL support & preview will move to 0.2.0 if applicable
- Metadata to store in media - https://g0v.hackmd.io/C8dW2cFiR1-N5Z0wcOefuA?view#Extended-goal-type-specific-FileInfo
  - especially duration (幾分幾秒) for video & audio
- can also upload video, audio and file after this integration
  - may need additional work on website to support video, audio & file
  - only signed-in users can access original files, others can only access previews

## Trend and Contribution
> https://github.com/orgs/cofacts/projects/10

- 需要 merge schema
- 本週實作 [Write author IDs when creating article reply feedbacks #280](https://github.com/cofacts/rumors-api/issues/280)

## Moderation discussion

尚未執行 囧

## Google 停用帳號與文件

No updates from Google.

## LINE API update

- Redelivery - https://developers.line.biz/en/docs/messaging-api/receiving-messages/#webhook-redelivery
  - Messaging API errors ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5ae28845c5b28b6b87b1a5bf1a6b2045.png)
  - 偶有零星 timeout，redelivery 應該有用
  - 但一週可能會有一次大卡住（triggered by rumors-site memory leak），此時 redelivery 無用，必須等待 cron job 出動 restart site

## 大松 & 下週 ＆ 下下週開會時間

- 大松：MrOrz - coscup / good first issue
- 下週 = 6/17 (五)、線上
- 下下週 = 6/23 (四)、線上

## 小學校

- 教案 & 下週錄音
- 教如何使用真的假的
  - 如何使用開源工具＆如何協作
  - 「我想補充」與「使用現有回應」

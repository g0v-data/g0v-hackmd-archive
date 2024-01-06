---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210602 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz, lucien
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

No production release this week.

### :eye: Under review

LINE bot: 讓 `lastScannedAt` 不會到期

#### 目前的 workaround

1. `heroku run -r production bash` 連線到 dyno 內
1. 手動設定 `lastScannedAt`
2. 執行 `node build/scripts/scanRepliesAndNotify.js`
3. 手動讀取新的 `lastScannedAt` 記下來明天用

#### Solution

1. 把其他改成 volatile --> https://github.com/cofacts/rumors-line-bot/pull/257
2. 改存到 mongo DB 
    - 討論 DB collection name



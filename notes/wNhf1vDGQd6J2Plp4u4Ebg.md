---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20211020 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: rumors-line-bot

https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20211014

LIFF fix

### :rocket: Staging

#### :globe_with_meridians: Site

- https://github.com/cofacts/rumors-site/pull/453

##### Testing checklist
http://dev.cofacts.tw/

登入自有帳號後檢測：
- [x] Can go to profile page on menu
    - [x] Look at the new contribution chart on mobile & desktop

##### ⛔️ Release Blockers

##### 未竟項目

### :eye: Under review

---

## User Blocking

### 1st milestone: data prep

#### Schema
- [ ] WIP add status field & “BLOCKED” state https://github.com/cofacts/rumors-db/pull/55/
- [ ] Add migration script to fill in status for `articleReplyFeedback`, `replyRequest`, `articleCategoryFeedback`
    - Unlike `articleReply` and `articleCategory` under `articles` index, those are individual indexes.
    - `articleReplyFeedback`, `replyRequest`, `articleCategoryFeedback`  can be listed out in separate API using ElasticSearch `terms` filter

#### API

- [ ]  Update mutation APIs for `ArticleReply`, `ArticleReplyFeedback`, `ReplyRequest`, `ArticleCategory`, `ArticleCategoryFeedback` so that statuses can be filled in according to currently logged-in user is blocked or not

#### Release

- Working schema
- Existing document fields are properly filled
- New document fields are properly filled
- Hidden reply rquests does not increase replyRequestCount
- Hidden article reply feedback does not increase feedbackCount

Not yet
- API still gives hidden items as before

### 2nd milestone: blocking mechanism

#### API
- [ ] Implement manual script that blocks a user (given a userId and blockedReason) and marks all their existing  `ArticleReply`, `ArticleReplyFeedback`, `ReplyRequest`, `ArticleCategory`, `ArticleCategoryFeedback` as `BLOCKED`
    - Should also update counting fields
- [ ] Expose `blockedReason` in `User` type

#### Website

- [ ] In website, writes `blockedUserIds` to cookie (website domain) if the current user is blocked
- [ ] load if the user is blocked from cookie and make this info available for all components (through react context or global variable)
    - The value should be available during SSR and in browser
    - The value should be availble even after logout

#### Release

- Block known violating users after release
    - Blocked user will start having `blockedUserIds` cookie in their browser
- API & website still gives hidden items as before

### 3rd milestone: remove blocked content from sight

#### API

- [ ] `WIP` add `statuses` filter to all listing APIs for `ArticleReply`, `ArticleReplyFeedback`, `ReplyRequest`, `ArticleCategory`, `ArticleCategoryFeedback` https://github.com/cofacts/rumors-api/pull/262/
    - filter out DELETED / BLOCKED items by default 

#### Website

- [ ] Query for `BLOCKED` items from API by default
- [ ] Filter out `BLOCKED` items if the their `userId` not in `blockedUserIds`

#### Community builder
- List out latest blocked items


#### Release
- Should display `BLOCKED` items even after blocked user logout!

## 防詐達人 Redirect page conversion rate

上線時間：2021/10/18 15:30

以下為 2021/10/20 13:50 的[報告](https://datastudio.google.com/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/p_44cex908mc)快照 (filtered by 來源)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c2ff9a997c8b717ab19c2fb085e92d0d.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a0eeac483fdb641ec8a21d85670704e9.png)

| Stat | Redirect LIFF | Article page | Conv Rate |
| ---- | -------------:| ------------:| ---------:|
| User |         1,081 |          312 |       29% |
| View |         1,426 |          388 |       27% |

對照：美玉姨
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fe0d23edc3eff6d67814b0c5571231b5.png)

- Redirect page 的數量看起來比美玉姨略高，但實際點進 article LIFF 者不到 3 成，所以 article LIFF 流量比美玉姨低
- 僅 10/19 數據是完整的一天，還可以再觀察
    - 或許之後 allow consent 的人會變多，讓 conversion rate 上升 [name=mrorz]
- 3 成可能是被 LIFF consent 擋住。就算沒有 redirect LIFF、使用者還是可能因為 consent screen 擋住，article LIFF 的數字可能還是差不多 [name=mrorz]

## 大松準備

- Good first issue OK



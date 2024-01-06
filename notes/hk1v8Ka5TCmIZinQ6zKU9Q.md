---
tags: cofacts
GA: UA-98468513-3
---

Cofacts user blocking mechanism
======

## Previous discussion

- 20211006 Proposals that deals with spammers: https://g0v.hackmd.io/zlWWCpDTQ5iADHNw7Thpog#Delete-reply-requests
- 20211013 Change scopes: https://g0v.hackmd.io/0Cv5hmmAQYyW8SJdXvfdtw#Delete-reply-requests---blocking-user-from-submitting-visible-contents
- 20211027 Breakdown into milestones: https://g0v.hackmd.io/rf0A7MRfTOC613QZmFehQA#User-Blocking

## Milestones and progress

### M1: data prep :heavy_check_mark: 

#### Schema
- [x] add status field & “BLOCKED” state https://github.com/cofacts/rumors-db/pull/55/
- [x] Add migration script to fill in status for `articleReplyFeedback`, `replyRequest`, `articleCategoryFeedback` https://github.com/cofacts/rumors-db/pull/55/
    - Unlike `articleReply` and `articleCategory` under `articles` index, those are individual indexes.
    - `articleReplyFeedback`, `replyRequest`, `articleCategoryFeedback`  can be listed out in separate API using ElasticSearch `terms` filter

#### API

- [x]  Update mutation APIs for `ArticleReply`, `ArticleReplyFeedback`, `ReplyRequest`, `ArticleCategory`, `ArticleCategoryFeedback` so that statuses can be filled in according to currently logged-in user is blocked or not https://github.com/cofacts/rumors-api/pull/263

#### Release

- Working schema
- Existing document fields are properly filled
- New document fields are properly filled
- Hidden reply rquests does not increase replyRequestCount
- Hidden article reply feedback does not increase feedbackCount

Not yet
- API still gives hidden items as before

### M2: blocking mechanism (reply requests only) :heavy_check_mark: 

#### API
- [x] Implement manual script that blocks a user (given a userId and blockedReason) and marks all their existing `ReplyRequest` as `BLOCKED`
    - Should also update counting fields
    - https://github.com/cofacts/rumors-api/pull/267
- [x] Expose `blockedReason` in `User` type https://github.com/cofacts/rumors-api/pull/269
- [x] List all blocked users so that we can list blocked contents in M3 https://github.com/cofacts/rumors-api/pull/269

#### Website

- [x] In website, writes `isUserBlocked` to cookie (website domain) if the current user is blocked https://github.com/cofacts/rumors-site/pull/457
- [x] load if the user is blocked from cookie and make this info available for all components (through react context or global variable) https://github.com/cofacts/rumors-site/pull/457
    - The value should be available during SSR and in browser
    - The value should be availble even after logout

#### Release

- Block known violating users after release
    - Blocked user will start having `isUserBlocked` cookie in their browser
- API & website still gives hidden items as before

### M3: remove blocked reply requests from sight :heavy_check_mark: 

#### API

- [x] `WIP` add `statuses` filter to all listing APIs for `ReplyRequest` https://github.com/cofacts/rumors-api/pull/262/
    - filter out DELETED / BLOCKED items by default 

#### Website

- [x] Query for `BLOCKED` reply requests from API by default
- [x] Filter out `BLOCKED` items if cookie `isUserBlocked` does not exist

#### Community builder / Spreadsheet
- List out latest blocked items

#### Release
- Should display `BLOCKED` items only for blocked users, even after they logout!

### M4: Block all contents from blocked users :heavy_check_mark: 

#### API
- [x] Extend the script that blocks a user (given a userId and blockedReason) to mark all their existing  `ArticleReply`, `ArticleReplyFeedback`, `ArticleCategory`, `ArticleCategoryFeedback` as `BLOCKED`
    - Leave `DELETED` article replies intact so that the contents we previously deleted won't come out
    - Should also update counting fields
    - https://github.com/cofacts/rumors-api/pull/274
- [x] add `statuses` filter to all listing APIs for `ArticleReply`, `ArticleReplyFeedback`, `ArticleCategory`, `ArticleCategoryFeedback` https://github.com/cofacts/rumors-api/pull/262/
    - filter out DELETED / BLOCKED items by default 

#### Website

- [x] Query for `BLOCKED` items from API by default

### M5: Report content mechanism :heavy_check_mark: 

:::info
Discussion: https://g0v.hackmd.io/Syl8le5xS22nLo8Vc56gmw?view#Block-user-%E5%BB%B6%E4%BC%B8%E4%BA%8B%E9%A0%85
:::

- Google form collecting spam
    - Implementation testing & improvement https://g0v.hackmd.io/tBEc2MajQkS-s-lGaG91Gg#%E6%AA%A2%E8%88%89%E9%81%95%E8%A6%8F%E8%99%95%E7%90%86%E6%B5%81%E7%A8%8B
- Website: add button 
    - https://github.com/cofacts/rumors-site/pull/471

---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20211013 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz, nonumpa, 4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site
https://github.com/cofacts/rumors-site/releases/tag/release%2F20211010
- #452 category sorting

#### :robot_face: rumors-line-bot
https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20211010

- #292 redirect LIFF

### :rocket: Staging

- #295 LIFF bug fixes

#### :robot_face: rumors-line-bot

https://github.com/cofacts/rumors-line-bot/pull/295

Test URL schemes: https://output.jsbin.com/gaparixayo

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] Rediret LIFF 測試
    - [x] 打開此連結：https://dev-line-bot.cofacts.tw/liff/redirect.html?articleId=3tu9btf8s50sm
        - [x] 可不用登入就正常點開
        - [x] 按「前往閱讀查核回應」無須登入就能看到訊息與回應
        - [x] 可 upvote / downvote
        - [x] 右上角「在真的假的開啟」可以打開 Cofacts LINE bot 準備發送訊息
            - https://line.me/R/oaMessage/@cofacts/?%F0%9F%93%83%20%E6%9F%A5%E7%9C%8B%E9%80%99%E7%AF%87%E7%9A%84%E5%9B%9E%E6%87%89%3A%0Ahttps%3A%2F%2Fcofacts.tw%2Farticle%2F3tu9btf8s50sm 在 iOS 從聊天視窗可以打開，但 iOS 的 LIFF 無法
                - iOS 14.6 / LINE 11.16.0 一開始點不開但後來可以 [name=nonumpa]
                - iOS ? / LINE 11.16.1 不行 [name=bil]
                - iOS 15 / LINE 11.17.1 可以了 [name=bil] 
            - 可以考慮轉網站但也可以不這麼做
    - [x] 打開此連結：https://dev-line-bot.cofacts.tw/liff/redirect.html?articleId=3tu9btf8s50sm&replyId=QS5fy3gBFXJoAcVj9ohy&utm_source=foo
        - [x] 可看到訊息與「MrOrz 認為 含有個人意見」的回應
        - [x] 下方有「查看其他查核回應」按鈕
    - [x] Google analytics 可收到 pageview
        - real-time report 下一定要同時設 `utm_source` 與 `utm_medium`⋯⋯
- [x] Rich menu 測試
    - [x] 「設定」更改後再次打開，應該會保留原本設定

##### ⛔️ Release Blockers
No

##### 未竟項目
No

## Delete reply requests - blocking user from submitting visible contents

:::info
**2021/12/01 Update**
A dedicated doc is opened to track its development - https://g0v.hackmd.io/hk1v8Ka5TCmIZinQ6zKU9Q
:::

上週討論：https://g0v.hackmd.io/zlWWCpDTQ5iADHNw7Thpog#Delete-reply-requests

實作中：隱藏黑名單產出的 `articleReply`, `articleReplyFeedback`, `replyRequest`, `articleCategories`, `articleCategoryFeedback` ，但本人看不到被隱藏這件事情

TODO list

- rumors-db
    - [ ] `WIP` add `status` field & "BLOCKED" state https://github.com/cofacts/rumors-db/pull/55/
    - [ ] Add migration script to fill in status for `articleReplyFeedback`, `replyRequest`, `articleCategoryFeedback`
        - Unlike `articleReply` and `articleCategory` under `articles` index, those are individual indexes.
        - `articleReplyFeedback`, `replyRequest`, `articleCategoryFeedback`  can be listed out in separate API using ElasticSearch `terms` filter
- rumors-api
    - [ ] `WIP` add `statuses` filter to all listing APIs for `ArticleReply`, `ArticleReplyFeedback`, `ReplyRequest`, `ArticleCategory`, `ArticleCategoryFeedback` and filter out DELETED / BLOCKED by default https://github.com/cofacts/rumors-api/pull/262/
    - [ ]  Update mutation APIs for `ArticleReply`, `ArticleReplyFeedback`, `ReplyRequest`, `ArticleCategory`, `ArticleCategoryFeedback` so that statuses can be filled in according to currently logged-in user is blocked or not
    - [ ] Implement manual script that blocks a user (given a userId and blockedReason) and marks all their existing  `ArticleReply`, `ArticleReplyFeedback`, `ReplyRequest`, `ArticleCategory`, `ArticleCategoryFeedback` as `BLOCKED`
        - Should also update counting fields
- rumors-site
    - [ ] Query for `BLOCKED` items from API by default
    - [ ] Set a cookie `blockedUserIds` for website domain, storing the blocked user IDs that this browser has previously logged in.
        - The cookie should be available in SSR as well, so for those blocked users, they can see these blocked items even after they logout.
    - [ ] For each place that displays a list of `articleReply`, `articleReplyFeedback`, `replyRequest`, `articleCategories`, `articleCategoryFeedback`, show blocked items if it match user ids inside `blockedUserIds`
- Announcement
    - need another way to list out blocked users & their contents.

:::success
Q: proceed or change method?
A: Proceed with current method
:::


## Incident report page in hackmd

from: https://g0v.hackmd.io/zlWWCpDTQ5iADHNw7Thpog?both#LINE-bot-event-%E9%80%81%E4%B8%8D%E9%80%B2-Google-Analytics

:::success
https://hackmd.io/@cofacts/incidents
:::

## 協會

大松解決？

## rumors-ai

GGM: 10/27 再來教我們

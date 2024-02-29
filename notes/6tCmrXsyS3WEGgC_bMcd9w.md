---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240229 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site
- 實科協會 footer

### :rocket: Staging

#### :robot_face: rumors-line-bot

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [ ] 送影片

#### :globe_with_meridians: Site

- 太多 feedback 現在可以全部載入 https://github.com/cofacts/rumors-site/pull/556 marcussfu++
- 

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [ ] Article list
  - [ ] Filter works
  - [ ] Sorting works
  - [ ] Can go to article page
- [ ] Replies list
  - [ ] Filter works
    - [ ] 不允許選擇 Replied by me
  - [ ] Sorting works
  - [ ] Can go to article page
  - [ ] 不允許 upvote / downvote replies
  - [ ] Can see vote reasons
- [ ] Hoax for you
  - [ ] Filter works
  - [ ] Can go to article page
- [ ] Article detail
  - [ ] Can see similar messages
  - [ ] Cannot submit, upvote, downvote reply request
  - [ ] Cannot submit, upvote, downvote reply
  - [ ] Cannot add, remove, upvote, downvote category
- [ ] Search
  - [ ] Can use global search to perform search
  - [ ] Can use textarea in header to perform searchs
     - Known issue: firefox 無法
  - [ ] Can list searched articles
    - [ ] Filter works
    - [ ] Can go to article page
  - [ ] Can list searched replies

登入自有帳號後檢測：
- [ ] Replies search page
  - [ ] can upvote / downvote replies
- [ ] Replies list
  - [ ] 可選擇 Replied by me
  - [ ] can upvote / downvote replies
- [ ] Article detail
  - [ ] Can submit, upvote, downvote reply request
  - [ ] Can submit, remove own reply
  - [ ] Can upvote, downvote other's article reply
  - [ ] Can add, remove, upvote, downvote category
- [ ] Can go to profile page on menu
    - [ ] Can edit own name, bio, URL
    - [ ] Can see own replies
- [ ] Can logout

##### ⛔️ Release Blockers

##### 未竟項目


### :eye: Under review



## CCPRIP


### 非營利帳號

- Facebook business verification: 已通過
  - 已驗證 profile & email 的 advanced access ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bad308e375c9961c19d9a7dff53336bf.png)
  - 可測試是否能以 Facebook 登入
- Google: 失敗
  - 網路討論：發 ticket 給 Percent https://support.google.com/nonprofits/thread/254596080/contacting-google-or-percent?hl=en&sjid=7865925514358855560-AP
  - 官方文件：發 ticket 給 Percent https://poweredbypercent.zendesk.com/hc/en-us/articles/13805863075857-My-nonprofit-has-been-rejected-by-Percent

## User organization / badge



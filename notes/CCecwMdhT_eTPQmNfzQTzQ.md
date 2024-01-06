---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20201007 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：斌綸, bil, mrorz, nick
:::

## Cofacts Next! 追蹤

- RSS 教學
    - [x] 完成[投影片](https://g0v.hackmd.io/TfCHhvtFTLmP0YKmaU1yVA)
    - [x] [UI「進階教學」文案](https://g0v.hackmd.io/GhVhBlK_QwKT3E5clAfkJw?both#Cofacts-Next-%E8%BF%BD%E8%B9%A4)
    - [ ] 實作[新 UI](https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=3146%3A324) - 文武
        - IFTTT wording 「訂閱本頁」要不要改？
        - 進階：先用純文字與 `<p>` `<ol>`，URL 部分提供 `input` 與 `button`
    - [ ] 完成影片   [請改腳本](https://g0v.hackmd.io/TfCHhvtFTLmP0YKmaU1yVA?view)
    - [ ] FB 教學
    - [x] 觀察 RSS 使用率 - https://datastudio.google.com/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/hN8iB
- 推播
    - [x] [修正 LIFF title](https://github.com/cofacts/rumors-line-bot/pull/226)
        - [x] 更換 rich menu 字樣 
    - [ ] Rich menu 教學 - [文案](https://g0v.hackmd.io/yEp9JJtHSyK18bxCQV4dUg#Rich-menu-%E4%BB%8B%E7%B4%B9)
        - [x] 志超教學圖用來主頁
        - [x] LINE 的「歡迎訊息」
        - (Rollbar) LIFF 裡面每天好像有什麼 cursor error，應該要看一下 [name=nonumpa]
    - [x] 觀察 [Rich menu 使用率](https://datastudio.google.com/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/DtzfB)
    - [ ] 啟動推播功能
- User ID refactor: https://github.com/orgs/cofacts/projects/8
- Profile page
    - [x] Related APIs 
    - [x] UI components (shared with detail pages)
    - [ ] `/user/[id]` page
    - [ ] Edit name / photo UI
- Landing page, 教學頁, final report
    - [x] 教學頁 [mobile design](https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=2011%3A0) done
    - [ ] 設計 final report
    - [ ] 實作

## APAC Trusted Media Summit

> 聽到啥的筆記
> 
Chatham house rule

## 增加 LINE 使用者

> Review of current own-media measures

美玉姨：
- 週末修改 https://github.com/CarolHsu/rumor-checker/blob/master/app/workers/reply_worker.rb#L14
- 使用 URL scheme 傳訊息問 Cofacts
    - 會用比較低的 threshold 問相似訊息
    - 沒有的話才會傳訊息

網站：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_db33f0fd72e9b56b515d349d9f1ccc60.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_babef3617565a6b27999e70ee5d6f499.png)

- Page view 高峰約 37,000 人
- Click FAB 最高約 370 次
- 增加好友最高約 350 人
- CTR ~= 1%, 點了之後繼續加好友的比例不低


## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

[2020/10/5 Release](https://github.com/cofacts/rumors-site/releases/tag/release%2F20201005)
偷偷 deploy 了 fab branch 的東西
包含上週的

- #275 Fixes ribbon appearance
- #335 Level icon (not used yet)
- #338 Add storybook to Hyperlinks

#### :electric_plug: API
[DIFF](https://github.com/cofacts/rumors-api/compare/7be562510e7d2df3a649f742e685e6d2380cd280...e611d5c2b1e10a18b87e5a951f73bd2ab39f10ee)

- #223 Name / avatar generation function (not actually connected yet)
- #224 Make `points` and `repliedArticleCount` public for `User` type

#### :robot_face: Chatbot

[20201001 Release](https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20201001)

### :rocket: Staging

#### :electric_plug: API

[DIFF](https://github.com/cofacts/rumors-api/compare/e611d5c2b1e10a18b87e5a951f73bd2ab39f10ee...77f009788e5f011eb1a8acf7a56d5d1ebc5a6208)

- #225 Similar replies API

:::info
Nothing to test this week
:::

#### :globe_with_meridians: Site

把 under review 的東西放進 staging 讓大家玩玩看了
主要變更在 article detail page

##### Feature
- Add favicon and article detail banner #346

##### Refactor
- `<Card>` for detail pages #342
- Adjust global border-radius and primary color palatte #343
- Article detail revamp using `<Card>` #344
- Similar messages side section in article detail #345

##### Testing checklist

http://dev.cofacts.org/

**未登入**下檢測：

- [x] Article detail
  - [x] Can see similar messages
  - [x] Cannot submit, upvote, downvote reply request
  - [x] Cannot submit, upvote, downvote reply
  - [x] Cannot add, remove, upvote, downvote category

登入自有帳號後檢測：
- [x] Article detail
  - [x] Can submit, upvote, downvote reply request
  - [x] Can submit, remove own reply
  - [x] Can upvote, downvote other's article reply
  - [x] Can add, remove, upvote, downvote category
- [ ] Can logout

##### ⛔️ Release Blockers

##### 未竟項目

- 登入之後，copy-paste 不用附上加好友功能!!
- 分享按鈕比旁邊的 upvote / downvote 大 [name=nick]

### :eye: Under review

#### :electric_plug: API
- https://github.com/cofacts/rumors-api/pull/226

#### :globe_with_meridians: Site
一堆～
- `<Card>` for detail pages #342
- Adjust global border-radius and primary color palatte #343
- Article detail revamp using `<Card>` #344
- Similar messages side section in article detail #345
- Add favicon and article detail banner #346

#### :robot_face: LINE bot
無

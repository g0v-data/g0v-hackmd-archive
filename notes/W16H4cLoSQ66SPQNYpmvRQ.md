---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20200624 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, lucien, Zoe
:::

## Cofacts Next! 各項目結案進度

https://github.com/orgs/cofacts/projects

### List of replies to rework / 幫助編輯找出需要複查的回應與訊息

- "Hoax for you"
  - 100% done & released
- RSS -- broken, fix: https://github.com/cofacts/rumors-site/issues/262
  - Assigned to 文武
  - ETA (staging): 8/3

### Category labeling mechanism / 自動與協作議題標記

- 對文章增加刪除 category
  - 100% done & released to staging
- RSS for category -- broken, fix: https://github.com/cofacts/rumors-site/issues/262
  - Assigned to 文武
  - ETA (staging): 8/3
- Automatic categorization
  - Assigned to GGM
  - ETA (staging): 6/28
- Re-train model using user feedbacks
  - Assigned to GGM
  - 隨時可以重 train，但要先觀察使用者的標記

### 告知 Chatbot 使用者新回應

- 列出過去傳過的訊息、回應的狀況
  - 90% done
  - PR pending for review
  - Google analytics & separate rich menu v.s. notification
  - Assigned to MrOrz
  - ETA: 6/28
- 紀錄問過哪些訊息，放進資料庫
  - Done (?) under review
    - [insert data](https://github.com/cofacts/rumors-line-bot/pull/201) - changes requested
    - [backtrack user](https://github.com/cofacts/rumors-line-bot/pull/204) - draft
  - Assigned to GGM
  - ETA: :female-construction-worker:
- 讓使用者設定是否開啟通知
  - Done: https://github.com/cofacts/rumors-line-bot/pull/185
  - Assigned to 文武
  - Done
- 有新回應時通知
  - Assigned to 文武
  - ETA: 6/30

### 調整網站視覺、視覺化呈現編輯貢獻
- List page 重構
  - Related bugs
    - Search page 應該 sort by relevance
    - Replied by me filter 目前是壞的
    - Latest reply 頁面卻有沒回應過的訊息
  - 目標
    - 不同頁面使用不同 filter
    - 不同頁面使用不同 sort
    - 不同頁面顯示不同 UI、載入不同資料
  - Assigned to MrOrz
  - ETA: 6/28
- Article page toolbar & search
  - Assigned to 子暘
  - ETA: 6/28

## Cofacts Next! Enhancement items

0. [user / app id refactor](https://g0v.hackmd.io/ZcoUOX_-RQSkJyl5xz4_Zg?view#%E6%96%B9%E5%90%91-2-%E9%87%9D%E5%B0%8D%E6%AF%8F%E5%80%8B-backend-user-%E9%83%BD%E7%94%A2%E7%94%9F%E4%B8%80%E5%80%8B-user-document) [2w]
    - Blocks (4) profile page
    - Assigned to MrOrz
    - [Migration script](https://github.com/cofacts/rumors-db/tree/create-user)
      - adds user for backend app articles, reply-requests & article-reply feedbacks
      - ETA: 7/1
    - API change
      - organize auth & login routes
      - create user when resolving user
      - ETA: ??


1. Website Article page analytics [1.5w]
    - API: https://github.com/cofacts/rumors-api/issues/166
      - 先接圖，之後再看 quota 會不會爆、要不要上 cache
    - UI: https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=889%3A306

2. Website reply detail page [1w] 
    - Extract common components (such as card with title) to storybook
    - Link from article detail to reply detail

3. Cofacts Landing page: [Blocked by designer] [3d]
https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=994%3A112

4. Website [profile page](https://g0v.hackmd.io/@NFi0czulSemxCM8RNSlz8Q/HJ8xT3QVU/%2FbbreV0ZqRDarHl4Zt5UpEw)
    - blocked by user / app id refactor (ETA: until August)
    - API [1.5w]
    - UI [1w]

5. (Optional) Archiving all hyperlinks in data archiving services [1.5w]
    - Provide more robust archive: https://github.com/cofacts/rumors-api/issues/136
    - Hyperlinks folding - https://docs.google.com/presentation/d/18VnEBMr9m-t81ppRwHcjbA1keltg-CIn7wUF9pu1oLo/edit#slide=id.g88d85857df_0_24 （C）


## :rocket: Staging -> Production

### Feature

- #256 Search page style


### Bugfixes

- #257 Reply form is not working
- #259 Article page layout fix
- #261 Category add / remove dialog
- #264 Multiple style fix

### Others

- #258 [DX] Enable React hooks lint
- #260 [Documentation] Storybook for `TimeRange`
- #263 [Documentation] Storybook for `PlainList`, `ExpandableText`

### Testing checklist

未登入下檢測：
- [x] Article list
  - [x] Filter works (Replied by me:known issue)
  - [x] Sorting works
  - [x] Can go to article page
- [x] Replies list
  - [x] Filter works(Replied by me:known issue)
  - [x] Sorting works
  - [x] Can go to article page
  - [x] 無法 upvote / downvote replies(可喔)
  - [x] Can see vote reasons
- [x] Hoax for you
  - [x] Filter works
  - [x] Sorting works
  - [x] Can go to article page
- [x] Article detail
  - [x] Can see similar messages ( https://dev.cofacts.org/article/1fi7dla9wtwjn )
  - [x] Can see deleted replies
  - [x] Cannot submit, upvote, downvote reply request
  - [x] Cannot submit, upvote, downvote reply
  - [x] Cannot add, remove, upvote, downvote category
- [ ] Search
  - [x] Can use global search to perform search
  - [x] Can use textarea in header to perform searchs(無法按enter, 相關度不高)
  - [x] Can list searched articles
    - [x] Filter works
    - [x] Sorting works
    - [x] Can go to article page
  - [ ] Can list searched replies
    - [ ] Can go to reply page

登入自有帳號後檢測：
- [ ] Replies search page
  - [ ] can upvote / downvote replies
- [x] Replies list
  - [x] can upvote / downvote replies
- [ ] Article detail
  - [x] Can submit, upvote, downvote reply request
  - [x] Can submit, remove own reply
  - [x] Can upvote, downvote other's article reply
  - [ ] Can add, remove, upvote, downvote category
- [x] Can logout


### Bug found

- [BLOCKER] list page & article page 作者顯示不同人
  - https://dev.cofacts.org/article/3vvk10cea81w1
  - List page ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_72a7ec1aad4aa3d31e2924448d943093.png)
  - Article page ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f6332a76823ff5308bbedad6d2b0dbd5.png)
- [BLOCKER] Author avatar 跟人對不起來
  - https://dev.cofacts.org/article/AV1vp0l4yCdS-nWhuc4e
  - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b4897bb4dd489b4f8ac1e1814b9fc7c1.png)
- Reply-by-me is broken (known issue)
    - ✅  Implemented in https://github.com/cofacts/rumors-site/pull/268 
- Article page: "Reply to this message" should be on bottom right instead of top right
    - [ ] check
- Deleted reply list
  - 補 UI spec
  - 換成只有自己看得到刪除的回應（但可能在 reply detail 還是看得到）
- Upvote / downvote 時要不要直接送出 upvote / downvote
  - 比較方便大家送出 feedback，不會半途而廢
- reply request 的 author 不會顯示 user

#### Search page
- Search page textarea 問題
  - 高度只有一行，導致斷行之後會以為前面的東西不見了
  - enter 鍵應該要送出比較直覺？
- Search result
  - 應該要能點進 reply page
  - search 顯示回應應該要比文章行數多
  - reply list 現在無法 upvote / downvote

:::info

:::

#### Category dialog
- 加入的 category 無法立即刪掉 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4a5de1b066e0d3bf40d656fcc3daa973.gif)
- 刪掉的 category 重新整理頁面之後又會出現
  - 按下刪除後所有的都會一起刪掉
  - 重新整理之後又會通通出現
  - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_83a580ad411ec22e63c74d5645b27497.gif)
  - 例：https://dev.cofacts.org/article/1fi7dla9wtwjn#_=_
- 自己不應該要可以 upvote / downvote 自己提案的 category

---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20200701 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：mrorz, bil, 志超, lucien, 文武, ggm, Zoe
:::

## Cofacts Next! 收尾追蹤

https://github.com/orgs/cofacts/projects

### Category labeling mechanism / 自動與協作議題標

- Automatic categorization
  - Assigned to GGM
  - Already on staging
    - 送一個訊息進 staging
    - 明天會被標

### 告知 Chatbot 使用者新回應

- 列出過去傳過的訊息、回應的狀況
  - Google analytics & separate rich menu v.s. notification
  - Assigned to MrOrz
  - ETA: 6/28 --> 7/6
- 紀錄問過哪些訊息，放進資料庫
  - Done (?) under review
    - [insert data](https://github.com/cofacts/rumors-line-bot/pull/201) - changes requested
      - 7/3
    - [backtrack user](https://github.com/cofacts/rumors-line-bot/pull/204) - draft
  - Assigned to GGM
  - ETA: :female-construction-worker:
- 有新回應時通知
  - Assigned to 文武
  - PR: https://github.com/cofacts/rumors-line-bot/pull/207
  - 剩 GA, test, 用 articleReply
  - 想想如何解決已經看過的訊息也送推播的問題
  - ETA: 6/30

### 調整網站視覺、視覺化呈現編輯貢獻
- List page 重構
    > ArticlePageLayout (可疑訊息、最新查核、等你來答、搜尋頁面) 的 refactor 預計會這樣進行：
    https://g0v.hackmd.io/h8rP0TOGTh2Clxi_Oi_QKw
    >
    > 幾個重點：
    > - 會影響列表的 controls (如 filter, search, more button) 直接對 URL param 讀寫。單純化的 component input / output 有利於在各個 page components 重用。
    > - page components 管理 data loading，讀取 URL param 之後拼湊成 graphql query。各頁面有特殊 Query 需求，也是在這個階段對 graphql query 加蔥。
    > - 將會分 3 個 pull request 進 code

  - Assigned to MrOrz
  - 1st PR 已發 [#267](https://github.com/cofacts/rumors-site/pull/267) , [#268](https://github.com/cofacts/rumors-site/pull/268)
  - 2nd PR: 7/6
  - 3rd PR: 7/14

## New spec: article detail analytics

> 上週的 [Enhancement item](https://g0v.hackmd.io/W16H4cLoSQ66SPQNYpmvRQ?both#Cofacts-Next-Enhancement-items) 之一

https://g0v.hackmd.io/0kjaVlFASSyddkltqGR6Nw?view


## :star: Released to Production

### API server

[ce61fc1..8ca66a9](https://github.com/cofacts/rumors-api/compare/ce61fc1...master)
- [#172 Implement articleRepliesFrom filter for ListArticles](https://github.com/cofacts/rumors-api/pull/172)
- [#177 LINE bot CORS](https://github.com/cofacts/rumors-api/pull/177)
- [#178 add reply type filter to ListArticles](https://github.com/cofacts/rumors-api/pull/178)
  - Enables us to filter by reply type in article list

## :rocket: Staging -> Production

### LINE bot

https://github.com/cofacts/rumors-line-bot/compare/master...dev

#### Features
- [#185 User setting LIFF](https://github.com/cofacts/rumors-line-bot/pull/185)
- [#197 Loads user article link](https://github.com/cofacts/rumors-line-bot/pull/197)
- [#198 Lists user article link and data from Cofacts API](https://github.com/cofacts/rumors-line-bot/pull/198)
- [#199 Styling user article link LIFF](https://github.com/cofacts/rumors-line-bot/pull/199)
- [#200 Handle clicking user article link](https://github.com/cofacts/rumors-line-bot/pull/200)
  - This changes handler, needs test
- [#203 user article link pagination](https://github.com/cofacts/rumors-line-bot/pull/203)

#### Refactor item
- [#194 LIFF auth check relaxed](https://github.com/cofacts/rumors-line-bot/pull/194)
- [#195 Svelte eslint](https://github.com/cofacts/rumors-line-bot/pull/195)
- [#196 unit test for svelte](https://github.com/cofacts/rumors-line-bot/pull/196)

#### Testing checklist

Staging chatbot: https://lin.ee/1QUzEX4nI
尋找測試用舊訊息： https://dev.cofacts.org/articles

- [ ] 應可送出「全新訊息」
    - [ ] 問訊息來源時選擇「我自己打的」或「LINE 外面看到的」，應該會被擋下。
    - [ ] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，訊息應該還是有被送出。
    - [ ] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [ ] 可以修改理由送出。查看 article page 看理由是否有被送出。
    - [ ] 「分享到 Facebook」、「分享到 LINE」可以正常運作

- [ ] 送出「沒回應」的舊訊息，應可送出新理由
    - [ ] 跳出來源視窗後關閉，文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。
    - [ ] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，訊息應該還是有被送出。
    - [ ] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [ ] 可以修改理由送出。查看 article page 看理由是否有被送出。

- [ ] 送出「有回應」的舊訊息，應自動回傳回應
    - [ ] 應列出訊息所有的回應
    - [ ] 選擇回應之後可以幫回應 upvote
    - [ ] 可以再次選擇 downvote
    - [ ] 選完回應之後，還可以捲回去選其他回應

- [ ] 送出跟舊訊息相似的訊息，應提供選項選擇最像的訊息
    - [ ] 按下任一訊息應該會列出回應
    - [ ] 選了一個訊息之後，還可以捲回去按其他訊息
    - [ ] 捲回去按下「這裡都沒有我要的」應該要跳出詢問來源視窗

- [ ] Rich menu 測試
    - [ ] 「設定推播功能」更改後再次打開，應該會保留原本設定
    - [ ] 「查過的訊息」應該要列出之前查過的訊息

#### ⛔️ Release Blockers

#### 未竟項目

> Not release blocker, 開票追蹤


### Website

https://github.com/cofacts/rumors-site/compare/master...dev

#### Feature

- #256 Search page style
- #269 editor toolbar

#### Bugfixes

- #257 Reply form is not working
- #259 Article page layout fix
- #261 Category add / remove dialog
- #264 Multiple style fix
- #270 Fix avatar, reply info, etc
- #271 Fix trendline

#### Others

- #258 [DX] Enable React hooks lint
- #260 [Documentation] Storybook for `TimeRange`
- #263 [Documentation] Storybook for `PlainList`, `ExpandableText`

#### Testing checklist

未登入下檢測：
- [x] Replies list
  - [x] 無法 upvote / downvote replies(可喔)
- [ ] Search
  - [x] Can list searched replies
    - [ ] Can go to reply page

登入自有帳號後檢測：
- [x] Replies search page
  - [x] can upvote / downvote replies
- [ ] Article detail
  - [ ] Can add, remove, upvote, downvote category

[舊 bug verification](https://g0v.hackmd.io/W16H4cLoSQ66SPQNYpmvRQ#Bug-found)
- [x] list page & article page 作者顯示不同人
- [x] Author avatar 跟人對不起來
    Should be fixed now
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c55b4b8ec574e043f89bc372038f95b5.png)
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e64bc6bc49ac7142019989c30ef8019a.png)


#### ⛔️ Release Blockers

無

#### 未竟項目

> Not release blocker, 開票追蹤
> 上週項目：https://g0v.hackmd.io/W16H4cLoSQ66SPQNYpmvRQ#Bug-found

Category 看起來還是壞的

> 增加 category 好像不會有 feedback
> 然後刪掉自己加的 category 之後重新整理又會長出來 ><
> 
> [name=Johnson Liang]

## LIFF

> LIFF 行為改惹
看起來不能亂呼叫 LIFF.init 了
> 
> https://developers.line.biz/zh-hant/docs/liff/opening-liff-app/#redirect-flow

問題：Should we upgrade?

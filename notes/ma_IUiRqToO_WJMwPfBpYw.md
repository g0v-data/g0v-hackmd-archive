---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20200617 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, orz, 文武, ggm, darkbtf, lucien, 志超
:::


## Changelog
### Reviewing
- [Website] Storybook for `ExpandableText` and `PlainList`: https://github.com/cofacts/rumors-site/pull/263
- [LINE bot] viewed article LIFF
  - [#197](https://github.com/cofacts/rumors-line-bot/pull/197) User model and API for listing userArticleLink
  - [#198](https://github.com/cofacts/rumors-line-bot/pull/198) Loads previously viewed articles and display in LIFF
  - [#199](https://github.com/cofacts/rumors-line-bot/pull/199) Article Item UI
  - [#200](https://github.com/cofacts/rumors-line-bot/pull/200) Listing replies after selecting viewed article
  - Discussion: How to design pagination API? Same as Cofacts?
    - Use connection model https://graphql.org/learn/pagination/#complete-connection-model

### Staging
- [LINE bot] [unit tests](https://github.com/cofacts/rumors-line-bot/pull/196), [link check of `.svelte` files](https://github.com/cofacts/rumors-line-bot/pull/195)
- [LINE bot] check URL token only in some LIFF pages https://github.com/cofacts/rumors-line-bot/pull/194
- [API] Allow LINE bot CORS https://github.com/cofacts/rumors-api/pull/177
- [API] `ListArticle`'s `articleRepliesFrom` argument https://github.com/cofacts/rumors-api/pull/172
- [Website] Category UI https://github.com/cofacts/rumors-site/pull/261
  - 文武：在 100 % 的時候會不知道上面的顏色代表的是 agree 還是 disagree
    - 志超：設計圖裡除了顯示比例之外，在按鈕框裡面也會顯示數量唷，這樣就會知道100%是誰了 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_45ab07f9718b5ac2e918e03a0de07ccf.png)

### Production

No production launch this week

## new url-resolver follow-up
2020/6/10 16:55 deploy
觀察 errors: https://rollbar.com/Cofacts/url-resolver/

- [ERR_HTTP2_PROTOCOL_ERROR](https://rollbar.com/Cofacts/url-resolver/items/69/?item_page=0) 從每日 100 次變成每日 ~10 次
- error 發生處主要都還是舊的 scrap


## New domain
Need search console setup for `*.cofacts.org`

> Needs GGM
> 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9ea3a159aa397fa8e4feaf7a5086fa18.png)

orz:
search console 可以接去 [data studio](https://support.google.com/datastudio/answer/7314895?hl=en)
這樣就能公布 popular keyword, 從哪裡連入 cofacts, 在 search result 的曝光數, 點擊數 etc

## 已讀功能怎麼做

> 討論：https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1592323161.1692
> Mockup: https://docs.google.com/presentation/d/18VnEBMr9m-t81ppRwHcjbA1keltg-CIn7wUF9pu1oLo/edit#slide=id.g88d85857df_0_17

> 對對[滿久以前](https://github.com/cofacts/rumors-site/blob/old/pages/articles.js)的
我覺得如果真的要做的話，有幾個選項：
> - 把已讀未讀寫入 elasticsearch
> - 把已讀未讀寫入其他資料庫如 MongoDB
> - 跟舊版一樣，使用瀏覽器內置儲存功能，但將 localStorage 換成比較能存大東西的 IndexedDB
> - 直接用 localStorage XD
> - 使用 a:visited，但需要 refactor 成用 `<a>` 包住整個 card。而且無法退回到沒有 visited 的狀態。
>   - 「退回」需求不大，而且可以透過清除瀏覽記錄辦到
>   - ArticleItem 可以 refacor 成 for article / for-you 的、以及 for reply list 的
>   - reply list 的 visited 要再討論，可能只針對「查核闢謠」按鈕做 visited
> 
> [name=Johnson Liang]

Lucien:
原本可以退回的「已讀」功能比較特殊，我們只是想要試做看看
所以還是用 `a:visited` 比較簡單

`/articles` 的 card 跟 `/replies` 的 card 外觀差異很大，應該做成不同 component
可能兩者會共用個 BaseCard 之類的 component，但放進 page component 時應該要不同。

:::success
- 先針對 `/articles`, `/hoax-for-you` 兩頁的 item 製作
- 可能需要拆 `ArticleItem` 才能包 `<a>` 標籤
:::

## SameSite issue

分析見：https://github.com/cofacts/rumors-site/issues/244#issuecomment-644612628

## Cofacts API user / app migration

> MrOrz: 端午開發
> https://g0v.hackmd.io/ZcoUOX_-RQSkJyl5xz4_Zg

## ClaimReview search
> Google 有針對 ClaimReview 做一個專門的 search box 耶：https://toolbox.google.com/factcheck/explorer （預設只會顯示瀏覽器語言的 fact-check result）
好像也有 Search API: https://toolbox.google.com/factcheck/apis
>
> [name=MrOrz]

orz
感覺可以做在 line bot
但這樣使用者就不會回來

lucien
這樣在 bot 就會分流出去
要不要做在 API server
就能查完直接送進 DB
或者轉換為一種 reply

orz
在 API 感覺確實可以做個紀錄

---

Orz: 是否要考慮把 ClaimReview 作回 Cofacts website? 現在似乎支援一個頁面裡面多個 ClaimReview --
> 如果有多位審查者在網頁上確認過某項聲明是否屬實，您可以分別為每位審查者的分析結果提供 ClaimReview 元素。詳情請參閱[在單一網頁發布多項事實查核資料](https://developers.google.com/search/docs/data-types/factcheck#multiple-factchecks
)一節。 

:::info
開張 issue 追蹤
- Cofacts website ClaimReview microdata: https://github.com/cofacts/rumors-site/issues/18#issuecomment-645424596
- Cofacts API supporting search API: https://github.com/cofacts/rumors-api/issues/179
:::

## Visual items

志超：https://docs.google.com/presentation/d/18VnEBMr9m-t81ppRwHcjbA1keltg-CIn7wUF9pu1oLo/edit#slide=id.g88d85857df_0_0

需要表決
https://docs.google.com/presentation/d/18VnEBMr9m-t81ppRwHcjbA1keltg-CIn7wUF9pu1oLo/edit#slide=id.g88d85857df_0_24



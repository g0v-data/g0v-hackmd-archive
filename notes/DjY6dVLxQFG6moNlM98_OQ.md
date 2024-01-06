---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20200819 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：zoe, nonumpa, mrorz, bil, Lucien, ggm
:::

## Cofacts Next! 追蹤

- [收尾] Chatbot notification
    - Migration: Blocked by rich menu
        - [env vars 已經設好](https://g0v.hackmd.io/eitM7s0bSSeS3kg-MAcpDw?both#-Chatbot)
        - 已經將 `userArticleLink` 放入 production
        - `UserSettings` 還沒放進 production
        - Cronjob 還沒設定與啟動
    - Blocking items
        - 就算把所有人 UserSettings 的推播設定調成 false，在 rich menu 做好、引導 onboarding 流程做好之前，新加入的使用者還是會預設被打開推播、然後被 LIFF 的 consent screen 擋住囧
        - LIFF 設定應該會需要更多 description，且應該要翻譯成中文
        :::info
        討論：
        - rich menu 沒有時程
        - 已經有草稿，有共識就會繼續往下畫
        :::
    - MongoDB backup mechanism
        - owner: GGM
        - 是否需要 read-only user?
        - Mongodump --> 到哪裡？GCS?
        - Plan
            :::success
            - 先確定要在哪一台機器上跑？prodiction linode
            - 備份到 GCS
            - cronjob 在 linode 上
            - code 放 rumors-deploy

            ETA: 8/24 (一)
            :::
- Article analytics from GA
    - Migration: Blocked by database date time zone issue
        - [Migration steps](https://g0v.hackmd.io/eitM7s0bSSeS3kg-MAcpDw?both#Server-setup)
        - cron job 有設好（但 production 上的設錯 QQ）
        - 等 time zone issue 處理完畢之後再刪除重跑資料、得到正確的 timestamp
        :::spoiler Timestamp 相關 slack 討論串
        https://g0v-tw.slack.com/archives/C2PPMRQGP/p1597603078049600
        ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d31c1a265294f7d6381e4b4723286d84.png)
        ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d3e9e630b4bbf0c933faea93568b31e4.png)
        ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a2fbf78b313f6ba66c7b91935f3c11a8.png)
        :::
        :::success
        結論：
        開個 issue 加 timezone
        若這一兩天沒有解決，就繼續 migrate
        :::
    - UI
        - PR in draft https://github.com/cofacts/rumors-site/pull/315
        - Y 軸相關討論
        :::spoiler Y 軸 slack 討論串
        ### Hover 再有點點
        https://g0v-tw.slack.com/archives/C2PPMRQGP/p1597481267037200
        ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a8e6c67ba4a09e47878ac757d8f685e5.png)

        ### Y 軸問題
        https://g0v-tw.slack.com/archives/C2PPMRQGP/p1597481091035300
        ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_df5f67acec3c7b973b1d8e1d9663de4c.png)
        ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_77cc59fb20e9c0b6bf4ff9608bb09b7f.png)
        ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a8357992c550974b5fcd231905fb021d.png)
        ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3bcc3f695685c9b8059a842fe382509e.png)
        :::
        :::success
        figma 沒有 double y 軸、y 軸也沒變色、點點沒有拿掉，倒是時間變色了
        
        先寫再說 XD
        換成 31 天 可以每一格都一樣大
        :::
- `ArticlePageLayout` refactor
    - `ArticleReplyFeedbackControl`: 50% complete
    - 2nd PR https://github.com/cofacts/rumors-site/pull/288 not ready yet
    - 3rd PR Remove ArticlePageLayout 遙遙無期 orz
- User ID refactor
    - Owner: TBD
    - Spec: https://g0v.hackmd.io/ZcoUOX_-RQSkJyl5xz4_Zg?view#%E6%96%B9%E5%90%91-2-%E9%87%9D%E5%B0%8D%E6%AF%8F%E5%80%8B-backend-user-%E9%83%BD%E7%94%A2%E7%94%9F%E4%B8%80%E5%80%8B-user-document
- 教學頁 spec
    - owner: Lucien
    - https://g0v.hackmd.io/sB_zayWjTo-W0R7xe_U34w
    > 這樣志超可以先做樣式嗎，志超好像說不行 [name=bil]
    > 互動細節還要調，但文字的部分是可以先排的 [name=lucien]
    > 希望明確在 hackmd 標出哪些可以先排 [name=bil]

## 討論事項

### RSS 訂閱教學影片

- 腳本：見 [20200805 會議記錄](/rEtx-47bRHeW2aM05DINDQ)
- [影片用 Keynote](https://www.icloud.com/keynote/0uSJhzhXm6ti2ua9frzQuqubw#Cofacts_subscribe_tutorial) 

影片 :point_right: https://youtu.be/fK4Xabs-Cds

> 希望影片可以幫忙 conquer 那一段授權的過程 [name=lucien]
> 想說比較短比較能吸引人 [name=mrorz]
> 老實說我不知道哪一種比較好 [name=lucien]
> 還是我錄一個有授權的版本，看使用者會不會因為太長而放棄 [name=mrorz]
> 可能不是因為長，而是使用者不知道為什麼要有那一段授權的過程 [name=lucien]
> 可能用「為了讓 IFTTT 與您的 LINE 連動，⋯⋯」之類的 [name=mrorz]

:::success
mrorz 試著把授權過程也放進影片
看看腳本是否能解惑
:::

TODO
- [ ] 同樣方式製作 Slack & TG 投影片
- [ ] 用好的麥克風重新錄音
- [ ] 找個背景音樂 (?)


### Samesite issue
https://github.com/cofacts/rumors-api/issues/186

> 我的電腦也不能用啦囧 [name=mrorz]

> Method 2 要起兩個 site [name=ggm]
> 我記得 secure 要解決的話就是要 self-sign SSL 讓 nginx <> site 也是 SSL、讓 express 也認知到自己是 SSL。我放棄就是因為這個很麻煩。可能看有沒有暴力解 [name=lucien]
> 可以試試看暴力解：https://github.com/koajs/koa/issues/974#issuecomment-394198968
> 或者看看 X-Forwarded-Proto 有沒有用 [name=mrorz]
> 

:::success
試試看 method 1 試著把 secure 搞定。
:::

### LINE bot onboarding UX
上週討論：https://g0v.hackmd.io/eitM7s0bSSeS3kg-MAcpDw#LINE-bot-onboarding-UX
開票：https://github.com/cofacts/rumors-line-bot/issues/216

### LINE bot state diagram --> call graph?

:::spoiler Slack 中的討論
https://g0v-tw.slack.com/archives/C2PPMRQGP/p1597810692112100

> 是說我對 chatbot 有個大膽的想法 (?)
> 目前 Cofacts LINE bot 在實作的時候遇到下面的挑戰：
> 1. chatbot 使用者可能會捲回去任何一個步驟按按鈕，因此用 state diagram 來管理邏輯很吃力
> 2. 每個 state handler 要處理複數種輸出樣態，而且可能有兩個 state 會想要吐同一種 output，導致我們除了 state handler 之外還要設計產生 reply 的 utility function
> 
> 如果我把「chatbot 產生 reply」與「chatbot 做事情」兩個東西拆開成比較 atomic 的 function，雖然 function 總數會比 state handler 多，但它可以 visualize 各種輸出樣態（而不是藏在 state 所呼叫的 utility function），也才能更明瞭每種輸出樣態需要的 input argument 有哪些
> 
> 最後 chatbot 的邏輯就可以整理成這樣：
> - 紅字是使用者的 input。方框裡的是 event payload。
> - 藍字 showXXX 就是機器人說話。說的話裡面可能會有很多按鈕，按下去之後對應到不同的紅字。
> - 黑字 doXXX 就是機器人去資料庫做事情，做完之後會有黑色的箭頭把資料（方框字）送到藍字 function（輸出）或其他黑字 function（處理）
> ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_babf5e3b52d0d18e140ac6d18e576ebd.jpg)
>
> 雖然圖看起來變複雜了，但其實是原本的圖太簡單，跟  chatbot 實際的行為有不小的差異。
> 
> 例如說一個 `__INIT__` state 其實含括了整張圖表上半的 `doSearch`, `showSearchResults` ；還有神奇的 `skip: true`  邏輯在特定條件之下一路做了 `showReplies` 與 `showReply`。
> 這張圖則是用更加 declarative 的方式直接秀出「輸入文字查詢」之後的所有輸出的可能性。
>
> 原本 state diagram 跟 chatbot 實際行為差異太大的結果就是，state 看起來好像很簡單，但每一條線都對應到很多複雜的邏輯。當每個 state 之間的邏輯無法好好拆開呈現，就代表原本 state diagram 的 state 其實是錯誤的封裝。
>
> [name=mrorz]
:::

> 寫成 function 一方面貼近 chatbot `handleInput() -> Messages` 的本質，也因為 input output 形狀固定，適合 typescript 化 [name=mrorz]

:::success
On-boarding UX 的部分可能先用 call graph + Typescript
handleInput 時，發現 action 有指定接下來要呼叫誰，就用 call graph 的方式處理
否則，繼續用過去的 state diagram
:::

## 編輯小聚
上週討論：https://g0v.hackmd.io/eitM7s0bSSeS3kg-MAcpDw#%E7%B7%A8%E8%BC%AF%E5%B0%8F%E8%81%9A

- [x] 主題：
    - 孔子媽媽待產日
- [x] 時間：9/27 (日) 14:00-17:00 
- [ ] KKTIX
- [ ] 準備貼紙
- 場地：NPO Hub 廚房
    - [ ] 借用場地單 - bil
    - [ ] 食物
    - [ ] 延長線 (揪松有 3~4 條，但可以再帶)
        - [ ] MrOrz 一條
    - [ ] wifi
        - [ ] Nighthawk M1 + 4G sim
        - [ ] ASUS RT-N12 Wireless N300 (2x 5dbi高增益天線)
- [ ] 誰會來呢？
    - mrorz, bil, lucien, nonumpa, zoe (maybe)
- [ ] 誰不會來
- [ ] LINE 文案

## :potable_water: Release pipeline

### :star: Released to production

註：本週 renovate [發瘋](https://github.com/cofacts/rumors-api/pull/201)，所以暫時關掉。

#### :electric_plug: API
##### Feature

- [#180](https://github.com/cofacts/rumors-api/pull/180) [#188](https://github.com/cofacts/rumors-api/pull/188) [#189](https://github.com/cofacts/rumors-api/pull/189) [#190](https://github.com/cofacts/rumors-api/pull/190) [#191](https://github.com/cofacts/rumors-api/pull/191) [#194](https://github.com/cofacts/rumors-api/pull/194) [#195](https://github.com/cofacts/rumors-api/pull/195) [#206](https://github.com/cofacts/rumors-api/pull/206) Google analytics related changes

##### Bugfix

- [#187](https://github.com/cofacts/rumors-api/pull/#187) load more than 10 reply requests at once

> 有些 reply request 很多，導致訊息很短但 reply request 很多，但很少
> https://cofacts.g0v.tw/article/2vl006ou5cgvf
> [name=mrorz]
> 可以做個收合把它收起來，不過似乎不緊急
> [name=nonumpa]

##### DB migration
`analytics` index related operations. See https://g0v.hackmd.io/eitM7s0bSSeS3kg-MAcpDw#DB-migration

:::warning
TODO: cronjob setup, migration (backtrack)
:::

#### :robot_face: Chatbot
- Notification 相關 env vars (see https://g0v.hackmd.io/eitM7s0bSSeS3kg-MAcpDw#Feature1 )
- [notify cron job fix](https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20200815)

:::warning
TODO: rich menu, cronjob setup, migration (backtrack)
:::

### :rocket: Staging

:::danger
Build fail, 開會前無法 resolve，故下週再測⋯⋯
:::

#### :globe_with_meridians: Site

https://github.com/cofacts/rumors-site/compare/master...dev

##### Bugfixes
- #302 Security fix
- #304 RSS related fixes; RSS should start working again!
- #316 iOS polyfill

##### Others
- #301 `<Infos>` time & metadata display component
- #311 Revamp article reply feedback component (50% complete); reorganize article reply related component props
- #312 Upgrade apollo-client to 3


##### Testing checklist

http://dev.cofacts.org/

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
  - [ ] Sorting works
  - [ ] Can go to article page

- [ ] Article detail
  - [ ] Can see similar messages ( https://dev.cofacts.org/article/1fi7dla9wtwjn )
  - [ ] Cannot submit, upvote, downvote reply request
  - [ ] Cannot submit, upvote, downvote reply
  - [ ] Cannot add, remove, upvote, downvote category

- [ ] Search
  - [ ] Can use global search to perform search
  - [ ] Can use textarea in header to perform searchs
  - [ ] Can list searched articles
    - [ ] Filter works
    - [ ] Sorting works
    - [ ] Can go to article page
  - [ ] Can list searched replies
    - [ ] Can go to reply page

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
- [ ] Can logout

##### ⛔️ Release Blockers

##### 未竟項目

### :eye: Under review

- https://github.com/cofacts/rumors-site/pull/317 (Google translate 問題，順便處理了 dark theme issue)
- https://github.com/cofacts/rumors-site/pull/305 RSS UI
    > 如果使用者選了不支援的排序方式，要顯示在哪？[name=nonumpa]
    > dialog 裡面？[name=mrorz]
    > 但上面的 email, feedly 也會無視不合理的排序，看是不是要做成 snackbar [name=nonump]
    > 可能做在 dropdown 的頭或尾巴有個深色底的區塊，用小字說明
    > 但可以先不做 [name=mrorz]
    > 已經有邏輯了，但不會去改使用者的 query，需要跟使用者提醒說目前的設定（尤其是 order）可能會讓 feed 是錯的 [name=nonumpa]
    :::success
    review PR 時先不考慮顯示設定問題的邏輯
    :::



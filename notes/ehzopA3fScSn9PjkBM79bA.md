---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20200708 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, 文武, zoe
:::

## Cofacts Next! 追蹤

- [收尾] Category 標記
    - Owner: GGM
    - production 啟動自動標記時程？
        - 隨便 (?)
    - production 開放人工標記時程？
        - Description 清楚嗎
        - UI 目前直覺嗎
        - 每個都給人標嗎
        :::success
        大松的時候暫時開起來，收 feedback
        大松之前不要開
        :::
    - 開放人工標記之後，再觀察標記品質，決定是否能用來重 train model
    - 新標籤
        - 給測資的方式
            :::warning
            @ggm, @darkbtf, @pai: Need input
            :::
        - 如何算是新標籤
            - 有意義但原本沒地方放
            - 有地方放但太廣、太滿
                - 通通塞在保健 or 政治
        - 新標籤提案
            - `COVID-19 疫情`
                - X 振興三倍券詐騙
                    - 雖然是 COVID-19 間接造成，但與疾病本身無關
                - V 新冠肺炎疫苗第一針打在解放軍上
                    - 也可以算中國影響力
                - V 西醫 N 人裡面 M 人死亡，中醫全數康復
                    - 也可以算中國影響力
                - ? 防疫概念股上漲 / 拉回整理的新聞
                    - 在邊界上⋯⋯
            - `國際關係`：WTO、IMF、OECD 等等的資訊
                - X 威尼斯因為疫情所以有鱷魚
                    - 環境保護？、COVID-19
                - V 英國退出歐盟
                - V 美國軍隊參加運動會把病毒帶到武漢
                - X? 列出各國的檢驗數字，表示台灣篩檢太少的社論
                    - 可以放在政治、COVID-19
                - V 歐盟允許使用華為的 5G 基礎建設
                - V 中國在美國的孔子學院如何如何
                    - 比鄰覺得不要放在中國影響力
                - V 一帶一路很棒
                    - （政治）、中國影響力
                - V  WTO 表示 OOOO
                - V 譚德賽說台灣人種族歧視
                - X 美國聯準會宣布降息兩碼
                - X 三峽大壩即將潰堤
                    - 農林漁牧政策（天災人禍）

- [收尾]  Chatbot notification
    - Owner:
        - MrOrz: GA 還在做
        > notification URL 要怎麼設計仍需測試
        > 但只會影響到 notification URL 本體
        - GGM & 文武：see PR review
        > 文武
        > cron job 送 analytics 時 userid 怎麼處理？不給的話好像會自己蓋一個新的
        > 結論：放個 "cron" 之類的
    - 時程？
        - GA: 7/13
        - Cron: 差不多惹
    - 上線後累積 userArticleLink + backtrack，但先不設 cron job
    - cron job 啟動：8 月？（跟 RSS 一起？） 

- Article analytics from GA
    - Owner: Zoe
    - Spec: https://g0v.hackmd.io/0kjaVlFASSyddkltqGR6Nw?view
    - Plan: 8/10 for API, 9/7 for UI
    - Authentication issue
        - https://github.com/googleapis/google-api-nodejs-client#request-options
        - `scopes: ['https://www.googleapis.com/auth/analytics.readonly']`
        - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3fdd11492d18032622cb29a817898bfb.png)
        :::success
        照著 https://ga-dev-tools.appspot.com/embed-api/server-side-authorization/ 說的，開了 service account 並且把 service account 加進 Cofacts 的 google analytics 帳戶
        :::

- `ArticlePageLayout` refactor
    - Owner: MrOrz
    - Spec: https://g0v.hackmd.io/h8rP0TOGTh2Clxi_Oi_QKw
    - Plan
      - 1st PR 已發 [#267](https://github.com/cofacts/rumors-site/pull/267) , [#268](https://github.com/cofacts/rumors-site/pull/268) **求 review**
      - 2nd PR: 7/13
      - 3rd PR: 7/20

- User ID refactor
    - Owner: MrOrz
    - Spec: https://g0v.hackmd.io/ZcoUOX_-RQSkJyl5xz4_Zg?view#%E6%96%B9%E5%90%91-2-%E9%87%9D%E5%B0%8D%E6%AF%8F%E5%80%8B-backend-user-%E9%83%BD%E7%94%A2%E7%94%9F%E4%B8%80%E5%80%8B-user-document
    - Plan: GG

- 教學頁 spec
    - owner: Lucien

## Cofacts Next! 未竟事項

:::info
相關資料
- [6/24 整理之進度、enhancement item、Bug found](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2FW16H4cLoSQ66SPQNYpmvRQ)
- [Cofacts UI 微調 from 設計師](https://docs.google.com/presentation/d/18VnEBMr9m-t81ppRwHcjbA1keltg-CIn7wUF9pu1oLo/edit)
- [Github Project TODO](https://github.com/orgs/cofacts/projects/5)
:::

盤點尚未開票、尚未 assign 給人的未竟事項，確認之後在 "Put issue in" 的地方開票。

待討論：1. repo 是否正確 2. 是否要標記 good-first-issue (給社群做)

- Landing page (1w)
    - Put issue in: rumors-site
    - https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=994%3A112

- Reply detail page (1w)
    - Put issue in: rumors-site
    - Extract common components (such as card with title) to storybook
    - figma https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=894%3A0

- Website profile page (2.5w)
    - Put issue in: API + rumors-site
    - Spec https://g0v.hackmd.io/@NFi0czulSemxCM8RNSlz8Q/HJ8xT3QVU/%2FbbreV0ZqRDarHl4Zt5UpEw
    - figma: https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=912%3A384

- Fold hyperlinks in detail pages
    - Put issue in: rumors-site (Good first issue)
    - Spec: https://docs.google.com/presentation/d/18VnEBMr9m-t81ppRwHcjbA1keltg-CIn7wUF9pu1oLo/edit#slide=id.g88d85857df_0_24 （最右邊的 C 方案）
    - Ticket: https://github.com/cofacts/rumors-site/issues/274


- Editor dialog adjustments（每個 point 一張票）
    - Put issue in: rumors-site
    - Markdown-like UX for list items in Cofacts editor
        - 按按鈕與 enter 時判斷是否插入 `-` or `N.`
        - 獨立一張票: https://github.com/cofacts/rumors-site/issues/276
    - Block not logged in user from mobile (現在誤觸之後無法 back) https://github.com/cofacts/rumors-site/issues/277
    - Hint mobile user to fill in references ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_da91bb7b5b9b2ef05b6ccde4a5a8be27.png) ([Figma](https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=1302%3A18)) https://github.com/cofacts/rumors-site/issues/278
    - 處理 Android 上鍵盤蓋住 UI 問題 https://drive.google.com/file/d/1aET09JJ_AxgFkRUDLYqR2CV3L4AAkagB/view?usp=sharing https://github.com/cofacts/rumors-site/issues/279
    - Font adjustment in [UI 微調](https://docs.google.com/presentation/d/18VnEBMr9m-t81ppRwHcjbA1keltg-CIn7wUF9pu1oLo/edit#slide=id.p) p8 https://github.com/cofacts/rumors-site/issues/282
    - 討論：搜尋回應功能顯示「自己剛回過」的回應
        - Issue: https://github.com/cofacts/rumors-site/issues/243
        - 3 月許的願: https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP/2020-03#ts-1584415185.236800
        - 是否要在沒搜尋的時候顯示最新幾篇自己的回應？

- Category dialog adjustments
    - Put issue in: rumors-site
    - Vote count when anyone voted ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_45ab07f9718b5ac2e918e03a0de07ccf.png =200x)
    :::warning
    等大松大家的測試
    :::

- Avatar related adjustments
    - Put issue in: rumors-site
    - Spec: [UI 微調](https://docs.google.com/presentation/d/18VnEBMr9m-t81ppRwHcjbA1keltg-CIn7wUF9pu1oLo/edit#slide=id.p) p1, p5
    - Add icon & level
    - https://github.com/cofacts/rumors-site/issues/283

- List page related adjustments
    - 已讀功能
        - visited or localstorage
    - 手機版登出🈚️作用: https://github.com/cofacts/rumors-site/issues/284

## :potable_water: Release pipeline

### :star: Released to production

#### Website ([20200703 Release](https://github.com/cofacts/rumors-site/releases/tag/release%2F20200703))
- Category dialog fix
- Editor UI

搜尋點擊後 reference 好像又壞了 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5ce7ef7711d47d8a976238ef85e1cced.png)

> 已開票：https://github.com/cofacts/rumors-site/issues/285

### :rocket: Staging

同上週 LINE bot 項目。
上週沒上的網站，已經在 7/3 release。

#### Website
https://github.com/cofacts/rumors-site/compare/master...dev

Fix category add / delete

可以先放著

#### LINE bot

https://github.com/cofacts/rumors-line-bot/compare/master...dev

##### Features
- [#185 User setting LIFF](https://github.com/cofacts/rumors-line-bot/pull/185)
- [#197 Loads user article link](https://github.com/cofacts/rumors-line-bot/pull/197)
- [#198 Lists user article link and data from Cofacts API](https://github.com/cofacts/rumors-line-bot/pull/198)
- [#199 Styling user article link LIFF](https://github.com/cofacts/rumors-line-bot/pull/199)
- [#200 Handle clicking user article link](https://github.com/cofacts/rumors-line-bot/pull/200)
  - This changes handler, needs test
- [#203 user article link pagination](https://github.com/cofacts/rumors-line-bot/pull/203)

##### Refactor item
- [#194 LIFF auth check relaxed](https://github.com/cofacts/rumors-line-bot/pull/194)
- [#195 Svelte eslint](https://github.com/cofacts/rumors-line-bot/pull/195)
- [#196 unit test for svelte](https://github.com/cofacts/rumors-line-bot/pull/196)

##### Testing checklist

Staging chatbot: https://lin.ee/1QUzEX4nI
尋找測試用舊訊息： https://dev.cofacts.org/articles

- [x] 應可送出「全新訊息」
    - [x] 問訊息來源時選擇「我自己打的」或「LINE 外面看到的」，應該會被擋下。
    - [x] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，訊息應該還是有被送出。
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以修改理由送出。查看 article page 看理由是否有被送出。
    - [ ] 「分享到 Facebook」、「分享到 LINE」可以正常運作
        - 「分享到 Facebook」 有錯字

- [x] 送出「沒回應」的舊訊息，應可送出新理由
    - [x] 跳出來源視窗後關閉，文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。
    - [x] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，可以看到再打開的選項
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以修改理由送出。查看 article page 看理由是否有被送出。

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應
    - [ ] 選擇回應之後可以幫回應 upvote
        - MrOrz: vote count 有更新，但編輯 upvote 理由之後，在網站上 see reasons 看不到 https://cofacts.hacktabl.org/article/AVyt453vyCdS-nWhuagx
    - [ ] 可以再次選擇 downvote
        - MrOrz: 可以 upvote 換 downvote（vote count 有更新），但 downvote 理由在網站上 see reasons 看不到
        - 未翻譯句子「If you have a better reply, feel free to submit it to ...」 
    - [x] 選完回應之後，還可以捲回去選其他回應

- [x] 送出跟舊訊息相似的訊息，應提供選項選擇最像的訊息
    - [x] 按下任一訊息應該會列出回應
    - [x] 選了一個訊息之後，還可以捲回去按其他訊息
    - [x] 捲回去按下「這裡都沒有我要的」應該要跳出詢問來源視窗 (選項中不能有 100% 相似的，否則會找不到按鈕)

- [ ] Rich menu 測試
    - [ ] 「設定推播功能」更改後再次打開，應該會保留原本設定
    - [ ] 「查過的訊息」應該要列出之前查過的訊息

##### ⛔️ Release Blockers

- [x] 「分享到 Facebook」 有錯字
- [x] 未翻譯句子「If you have a better reply, feel free to submit it to ...」

> All fixed in https://github.com/cofacts/rumors-line-bot/pull/208

##### 未竟項目

> Not release blocker, 開票追蹤

- 手機版的 upvote / downvote 理由看不到
    - API 可以拿得到 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_83c66d9e23053c607598b9d815a98e46.png =x200)
    - 網站 bug，另外開票 https://github.com/cofacts/rumors-site/issues/291

- Rich menu 壞的
    - 好像是沒有設好 env
    - 目前不會顯示 rich menu 所以不是 blocker， release article list 時再處理

### :eye: Under review

- [DB] Add `analytics` index https://github.com/cofacts/rumors-db/pull/44
    - Owner: Zoe
    - Merged~
- [Chatbot] cron https://github.com/cofacts/rumors-line-bot/pull/207
    - Owner: 斌綸
    - Review comment from MrOrz: 希望 change to batch
- [Chatbot] Insert https://github.com/cofacts/rumors-line-bot/pull/201
    - Owner: GGM
    - Discussion: https://g0v-tw.slack.com/archives/C2PPMRQGP/p1593850412237300 [(archive)](https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1593850412.2373)
        - always write `lastViewedAt`
        - restructure `UserArticleLink` API
            > 使用 create 的話，你是在說這段嗎？
            > https://github.com/cofacts/rumors-line-bot/blob/a3cda30eb414100405b1c3fd9e492308ddff8d34/src/webhook/handlers/askingArticleSubmissionConsent.js#L58
            > 我覺得這段用 create 沒什麼問題呀，使用者創建的新文章 CreateArticle.id 一定會是新的不會重複的，一定會產生出一筆 UserArticleLink 所以用 create 很合理吧？
            > 你是想把這段換成 upsertByUserIdAndArticleId 嗎？這樣雖然是可以，但是意圖會有點奇怪會混淆吧，upsert 的用意還是以 update 為主，你想要用來全面取代 create 嗎？
            > [name=ggm]
            > 對
            > 如果「所有 user article link 一定會寫入 lastViewedAt 」那就代表 create 跟 upsert 的 insert part 做的事情幾乎快一樣了。
            > 至於 upsert 的語意問題
            > 這就是為什麼我 rumors-api 類似的 mutation API 會使用 “CreateOrUpdate” 做 API 開頭，而不是用比較常見但確實比較看重 update 的 upsert XD
            > [name=mrorz]
            > 
## 大松

:::warning
- 7/25 (六) @ 中研院
- 報名快滿啦：https://g0v-jothon.kktix.cc/events/g0v-hackath40n
:::

文武不會去

擔任主持人，要準備開場投影片

工作內容：https://g0v.hackmd.io/@M3bjBcTXQ5i3BKGkYmRMiA/ryo6ijBGH

## New analytics

### Auto update from LINE
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_14fe7b1b22e7128094d579199145115a.png =50%x)

- App script --> [spreadsheet](https://docs.google.com/spreadsheets/d/1h9YAmi5i_dpYGYG5xUBBiW2Q_W0-ylJocb-MKY2nffc/edit) --> [analytics](https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/Cy2P)
- LINE OA Statistics: daily update
- LINE OA Demographic report: weekly
    - 年紀分佈無法分性別，[API 沒有分年齡的性別資訊](https://developers.line.biz/en/reference/messaging-api/#get-demographic)


### [Open data explorer](https://datastudio.google.com/reporting/67b411c1-687c-4b0f-9ec6-d8d961c18ebf/page/cgwWB)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6e3ce0c16e4411c3d0103924bc99d649.png =50%x)


- 免下載瀏覽 open data!
- Join data 後呈現在 table 裡
    - 使用 [data blending](https://support.google.com/datastudio/answer/9061420?hl=en)，原理是 left outer join
- 提供簡易 filter 與 count
    - 可以找出「被標了特定 category 的 article 的 reply count 總和」之類的資訊
    - 問題：blended data 要求所有 join data 要使用相同的 key，所以做不到 article --(article id)-- article reply --(reply id) -- reply 這種 join

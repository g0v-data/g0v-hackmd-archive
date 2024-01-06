---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20200930 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, ggm, (lucien)
:::

## Cofacts Next! 追蹤

- RSS 教學
    - [ ] 完成[投影片](https://g0v.hackmd.io/TfCHhvtFTLmP0YKmaU1yVA)
        - [ ] 再請志超完成動畫的部分 - bil
    - [ ] 提供 UI「進階教學」文案
        > IFTTT（If this then that）是能把觸發事件（this）與執行動作（that）串在一起的平台。
        > 您可以設定 IFTTT，
        > 將您篩選過後 [name=nonumpa] 
        > Cofacts「訊息列表」、「最新查核」或「等你來答」的新資訊，傳到指定的 LINE、Slack 或 Telegram 中。
        > 1. 複製這個列表的 RSS URL
             [網址 input] [COPY]
        > 2. 進到 https://ifttt.com/create/
        > 3. 「If this」選擇 RSS Feed，在要填入 Feed URL 的時候貼上剛才複製的 Feed URL
        > 4. 「Then that」選擇您要傳送新資訊的平台。IFTTT 會指導您進行必要的登入與設定。
    - [ ] 實作[新 UI](https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=3146%3A324) - 文武
    - [ ] 完成影片
    - [ ] FB 教學
    - [ ] 觀察 RSS 使用率 (analytics report TBD)
- 推播
    - [x] [修正 LIFF title](https://github.com/cofacts/rumors-line-bot/pull/226)
        - [ ] 更換 rich menu 字樣 https://www.figma.com/file/8508uGWdW7XvYxp59nvFKC/Cofacts-LINE-bot-related?node-id=0%3A1
    - [ ] Rich menu 教學 - [文案](https://g0v.hackmd.io/yEp9JJtHSyK18bxCQV4dUg#Rich-menu-%E4%BB%8B%E7%B4%B9)
        - [ ] 志超教學圖用來主頁
        - [ ] LINE 的「歡迎訊息」
    - [ ] ~~推播 Rich menu 教學~~ 怕掉使用者數所以放主頁先
    - [ ] 觀察 [Rich menu 使用率](https://datastudio.google.com/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/DtzfB)
        - [x] 重新啟用小聚後 rich menu - 小聚前 schedule 的 menu 並沒有作用⋯⋯
    - [ ] 啟動推播功能
- User ID refactor: https://github.com/cofacts/rumors-db/issues/49
- Profile page
    - [ ] Related APIs 
    - [ ] UI components (shared with detail pages)
    - [ ] `/user/[id]` page
    - [ ] Edit name / photo UI
- Landing page, 教學頁, final report
    - [x] 教學頁 [mobile design](https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=2011%3A0) done
    - [ ] 設計 final report
    - [ ] 實作

## 小聚觀察與檢討

部分使用者對登入會有抗拒
即使已經說明
- 要填回應 / upvote / downvote 就需要登入

使用者依然不會想要登入
    --> 可能是因為 FB 有真實姓名，但改名還沒實作回去
    --> 應該要在跟舊版網站一樣，做動作的當下跳出登入視窗，就不用耗費唇舌解釋
    
:::success
之後在報名頁面就指導使用者進行登入
至少要能登入再來，不然會沒貢獻
(mansplaining 大會)
:::
    
有參與者從 google 搜尋 Cofacts 點第一個
結果進到 medium 想要登入⋯⋯囧
    --> 我們的 landing page SEO 究竟出了什麼毛病囧

- 中文版 google 好像才會這樣，英文 google 的話 cofacts 官網就是第一個
- 把 medium 的名字改成「真的假的」就好

:::success
已改，再看看

要看這個 https://support.google.com/webmasters/answer/182192?hl=en
> In addition, the crawler sends HTTP requests without setting Accept-Language in the request header.

可能要在 HTML 裡加上不同語言的 link https://support.google.com/webmasters/answer/189077

Ref: https://github.com/cofacts/rumors-site/issues/347
:::

被攻擊怎麼辦
- 道高一尺魔高一丈，擔心假的回應會被用同樣的 channel 散佈
- 能夠偵測得到，可以偵測、用同樣的方式澄清；

散佈的人已經達成目的
- 還是有用，不是不報，cofacts 上的就是證據
- cofacts 是前線，還有其他 NGO 在同一個領域的後端處理媒體識讀

應該慢慢擴散好的
怎麼凝聚

每兩個月 seminar 很好但今天下雨，交通花時間，建議今天的內容弄 video 放在 FB group 有興趣的人
- Cofacts 粉專

## APAC Trusted Media Summit Vitual Booth
https://events.withgoogle.com/apac-trusted-media-summit-2020/

會有一個 virutal lobby 跟 booth 讓人留言

bil, mrorz 到時候看看

## Q4 ~ 2021 Q1 directions

All options: https://g0v.hackmd.io/-j-fAX0tS62amv9LejshOg#2020-Q4--2021-Q1-Directions

- LINE tutorial --> nonumpa
- Dialogflow --> nonumpa

## 增加 LINE 使用者

:::danger
2020 年底需達成 KPI： LINE 有效好友 > 17 萬
目前約仍需增加 25,000 人
:::

:::spoiler 過去 LINE 好友成長動能分析
#### 2018 - 2019
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4fc875a336577691d90257200fe1ae00.png)

- 2018 整年增 5 萬人
    - 主要在年底大選時較多使用
- 2019 整年增 5 萬人
    - 4 月時社會醞釀[處理假新聞的氛圍](https://www.blink.com.tw/board/post/65696/)
    - [較多演講](http://www.ystaiwan.org/news/1803)與相關報導 (earned media)
    - 假新聞清潔劑協助


#### 2019, 2020 對比
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cabf7881dfb7562ef4b447c8482ef0e2.png)

- 2020 Q1 疫情下
    - 衛福部等官方粉絲團推薦 (earned media)
    - 數量上延續 2019 動能，也沒有超越 2019 的增長
- 2020 Q2 後
    - flatten the curve (?)
:::

### Owned media mitigation

:::info
相關討論：https://g0v.hackmd.io/yEp9JJtHSyK18bxCQV4dUg#%E8%A1%8C%E9%8A%B7
:::

- Cofacts 網站導流
    - Cofacts 個別文章頁面瀏覽量仍大，應導流至 Cofacts LINE bot
        - 2020 Q3 的 web user 有 80 萬，1% 轉換率  --> 8000 人
        - ~~banner~~
        - 用類似客服按鈕的方式黏在旁邊
            - google 來大部分是手機使用者，所以用連結連到 https://line.me/R/ti/p/@cofacts
        - 做一個「把訊息傳到 Cofacts」，是個 QR code or 連結然後傳這個：
            ```
            📃 查看這篇的回應:
            https://cofacts.org/article/klynm9aiou4t
            ```
            - sample URL: https://line.me/R/oaMessage/@cofacts/?test
            - 沒加過 Cofacts 好友的話在這裡會加
            - 加過的人也能拿到 Cofacts 排版後的回應
            - 可增加 `userArticleLink`，有新回應會推播
- 分享文案加入 Cofacts LINE bot
    - article detail「複製」按鈕 / share 功能的文字
    - 在 Cofacts 複製文字時，加上 Cofacts 網站網址（如[ETToday](https://www.ettoday.net/news/20200930/1821415.htm)） (?)
        - 開票 --> https://github.com/cofacts/rumors-site/issues/339
    - LINE bot「分享回應給好友」功能，加入 LINE bot 文字宣傳  https://github.com/cofacts/rumors-line-bot/issues/221
- FB 粉專貼文
    - 網友轉發 FB 貼文確實會增加 LINE 使用者
        - 9/28 凌晨[發文](https://www.facebook.com/cofacts.tw/posts/689165235030857)後，9/28 ~ 9/29 新增的人數超過 500 人
    - QR code 效益 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_930138f937b6a0844b03c1f335fe5c2c.png)

:::success
Johnson 先做：
https://github.com/cofacts/rumors-site/issues/339
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site
[20200925 Release](https://github.com/cofacts/rumors-site/releases/tag/release%2F20200925)

#### :electric_plug: API

https://github.com/cofacts/rumors-api/compare/c2360819b7c9e5c1d4df32d95acdd7d2c584f650...7be562510e7d2df3a649f742e685e6d2380cd280

##### Bugfix
- #218 Categorfy ID filter now respects status

##### Others
- #217 Relay-style interfaces


### :rocket: Staging

#### :electric_plug: API

[DIFF](https://github.com/cofacts/rumors-api/compare/7be562510e7d2df3a649f742e685e6d2380cd280...e611d5c2b1e10a18b87e5a951f73bd2ab39f10ee)

- #223 Name / avatar generation function (not actually connected yet)
- #224 Make `points` and `repliedArticleCount` public for `User` type

#### :globe_with_meridians: Site

https://github.com/cofacts/rumors-site/compare/master...dev

##### Bugfixes
- #275 Fixes ribbon appearance

##### Others
- #335 Level icon (not used yet)
- [#338](https://github.com/cofacts/rumors-site/pull/338) Add storybook to `Hyperlinks`

##### Testing checklist

- [x] Staging article detail page 隨意按一按就好

##### ⛔️ Release Blockers

##### 未竟項目

ggm 無法登入 staging 
- 原因不明
- facebook, twitter, github 都無法
- 清除 cookie 後依然無效
- 換手機登入也無效

疑似是帳號壞了 (?)

#### :robot_face: Chatbot

https://github.com/cofacts/rumors-line-bot/compare/master...dev

Note: [Last week's change]() is not released yet, will go with this week's release as well.

##### Others

- #219, #225 Remove state diagram logic from chatbot workflow
- #223 Document the use case of docker-compose
- [#226](https://github.com/cofacts/rumors-line-bot/pull/226) Settings page style & translation


##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 檢查[上週 release blocker](https://g0v.hackmd.io/-j-fAX0tS62amv9LejshOg#%E2%9B%94%EF%B8%8F-Release-Blockers1) 是否還可以重現
- [x] 應可送出「全新訊息」
    - [x] 問訊息來源時選擇「我自己打的」或「LINE 外面看到的」，應該會被擋下。
    - [x] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，訊息應該還是有被送出。
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以修改理由送出。查看 article page 看理由是否有被送出。
    - [x] 「分享到 Facebook」、「分享到 LINE」可以正常運作

- [x] 送出「沒回應」的舊訊息，應可送出新理由
    - [x] 跳出來源視窗後關閉，文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。
    - [x] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，可以看到「提供更多資訊」按鈕，按下去可以再打開「理由」視窗
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以修改理由送出。查看 article page 看理由是否有被送出。

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應
    - [x] 選擇回應之後可以幫回應 upvote
    - [x] 可以再次選擇 downvote
    - [x] 選完回應之後，還可以捲回去選其他回應

- [x] 送出跟舊訊息相似的訊息，應提供選項選擇最像的訊息
    - [x] 按下任一訊息應該會列出回應
    - [x] 選了一個訊息之後，還可以捲回去按其他訊息
    - [x] 捲回去按下「這裡都沒有我要的」應該要跳出詢問來源視窗 (選項中不能有 100% 相似的，否則會找不到按鈕)

- [x] Rich menu 測試
    - [x] 「設定」更改後再次打開，應該會保留原本設定
    - [x] 「查過的訊息」應該要列出之前查過的訊息
        

##### ⛔️ Release Blockers

##### 未竟項目

- 如果直接複製貼上會觸發動作的 LIFF 動作，會觸發比較意料外的狀況
    - ex: 再送一個 reply request 到已經回覆過的訊息
    - 但 LIFF 這個狀況不會出現，因此正常狀況不會有這個情形發生

### :eye: Under review

#### :electric_plug: API
- [#225](https://github.com/cofacts/rumors-api/pull/225) "Similar replies" API

#### :globe_with_meridians: Site


#### :robot_face: LINE bot

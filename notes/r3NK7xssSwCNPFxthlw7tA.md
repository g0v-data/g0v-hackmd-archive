---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20200729 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, 文武, lucien
:::

## Cofacts Next! 追蹤

- [收尾] Chatbot notification
    - MongoDB staging & production 已經轉移至 MongoDB Atlas (Cofacts organization)
        - Staging, production LINE bot 的 `MONGODB_URI` 已經更新為 MongoDB Atlas 的 URI
    - Others: on staging now
        - Plan (樂觀)
            - 7/30 release
            - 8/5 前放入 old user article link
            - 8/5 討論 rich menu、啟動推播 cron job 但預設不把使用者通知啟動（只啟動部分人的通知）
            - 8/6 release rich menu
            - 8/13 看看通知的狀況（頻率、cron job 執行狀況、使用者回應）
    - MongoDB backup mechanism
        - owner: GGM
        - 是否需要 read-only user?
        - Mongodump --> 到哪裡？GCS?
        - Plan

- Article analytics from GA
    - Owner: Zoe
    - Tracking board: https://github.com/orgs/cofacts/projects/7
    - ETA Plan: 8/10 for API, 9/7 for UI

- `ArticlePageLayout` refactor
    - Owner: MrOrz
    - Spec: https://g0v.hackmd.io/h8rP0TOGTh2Clxi_Oi_QKw
    - Plan
      - 2nd PR:
        - refactor `<Infos>` - https://github.com/cofacts/rumors-site/pull/301
        - 主 PR: https://github.com/cofacts/rumors-site/pull/288 COSCUP 後
      - 3rd PR: COSCUP 後⋯⋯

- User ID refactor
    - Owner: MrOrz
    - Spec: https://g0v.hackmd.io/ZcoUOX_-RQSkJyl5xz4_Zg?view#%E6%96%B9%E5%90%91-2-%E9%87%9D%E5%B0%8D%E6%AF%8F%E5%80%8B-backend-user-%E9%83%BD%E7%94%A2%E7%94%9F%E4%B8%80%E5%80%8B-user-document
    - Plan: GG

- 教學頁 spec
    - owner: Lucien
    - ETA：

## 討論事項

### 大松檢討

> See: https://g0v.hackmd.io/6OzPCSNsTXKKqrNSWNhg7Q#%E5%8D%94%E4%BD%9C%E5%8D%80

#### Category 標記 UI 檢討

- 列表太長，捲來捲去很累很難找 [name=mrorz]
- 醫藥、愛滋、COVID-19 離很遠 [name=mrorz]
- 連續標十篇會很累；如果是查完順手標一篇就還好 [name=ggm]
- 「目標編輯」的部分，熟悉之後可以隱藏 [name=ggm]
- github 加 label 的 UI 不錯 [name=ggm]
- obsolete category 想辦法藏起來；article category 可能先保留 [name=mrorz]

#### 「等你來答」的問題

> MrOrz 問 4000 如何決定要在 Cofacts 上找想回的東西

- 使用「可疑訊息」列表，看哪個回應是 0 [name=4000]
- 不知道「等你來答」與「可疑訊息」列表的差異 [name=4000]
- 一頁可能要恢復原本的 25 item 比較好 [name=mrorz]
    - 需要開票
- 想要在文章列表看到網址預覽的標題，不用內文 [name=4000]
    - 覺得一個項目佔據螢幕的高度還可以，但希望可以放個標題進去；現在還滿有空間的
- 「等你來答」的數字消不完 [name=4000]

#### Youtube 阻擋 metadata scraping
- Ex: https://cofacts.org/article/39n5zi0t4vlci
- https://support.google.com/youtube/thread/34161253?hl=en
- 可以用 get_video_info 試試看 [name=stimim]

:::info
討論：其實這是間歇性的。是否要在 UI 提供重抓 preview 按鈕？
:::

- 不知道做成按鈕會不會被亂按 [name=nonumpa]
- 可以做成登入的編輯才可以按 [name=mrorz]

:::success
開票追蹤
:::

### chatbot 不問來源
> 討論：[![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0412a938bb1320a05619b6b60933cfd8.png =x200)](https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1595392645.363700)
>
> 2019 針對來源的討論:
> - [調鬆](https://g0v.hackmd.io/@johnson/rJB1nENcN?type=view#今日討論紀錄)
> - [放寬理由為選擇題](https://g0v.hackmd.io/s/SyA8YtlKE#放寬理由為選擇題)
> - [問來源實作](https://g0v.hackmd.io/@mrorz/Bk112JsT4?type=view#Asking-article-source)
> - [改版方案討論](https://g0v.hackmd.io/@mrorz/BksK6Ox_S#%E3%80%8C%E5%9C%A8%E5%93%AA%E8%A3%A1%E7%9C%8B%E5%88%B0%E6%AD%A4%E8%A8%8A%E6%81%AF%E3%80%8D%E8%83%BD%E5%90%A6%E6%93%8B%E4%BD%8F%E4%BA%82%E5%82%B3)
> - [選項沒有太大意義](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2F%40mrorz%2Fr1z1wm4tS)
> - [201909 成效](https://datastudio.google.com/reporting/9e3389be-a839-44bd-9d23-c3e4460a5be4/page/Uer1/edit)
> 

- 2020/5/19 新版 chatbot 上線
- 2020/7分析
https://datastudio.google.com/reporting/a4bbc681-2010-4668-9142-9b09ed843d28

目前實作：只要 source 不被擋，就會直接送進資料庫（無關理由）
因此真正被擋住的只有 `source value = manual input | outside LINE` 這兩種。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_75985cc4f10ced024d69004266361ae6.png)
- 被擋住的量 < 15%
- 會選到 trap 選項的 session 數些微地隨時間減少
- 可用上面的 source value filter 來檢視擋住的訊息是否有需要收錄

---

- 「manual input」非常少，但真的沒啥用
- 「我在外面看到的」其實可以放行
- 不知道多少是被擋在 LIFF 那裡
- 4000 筆 ArticleNotFound + ArticleFoundButNoHit: https://datastudio.google.com/u/0/reporting/a4bbc681-2010-4668-9142-9b09ed843d28/page/840ZB (少數最後有進資料庫)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a976e1e5ae3656debc9be073a53b7c5b.png)
- 4000 筆中，有 300 筆被傳進來 2 次
- 亂碼的應該是 LINE 內建 OCR 後傳入
- 全進資料庫，但有理由的、傳進來兩次的再顯示 [name=nonumpa]
    - 可是選擇不要送進來的話，還是不會送
    - 比較接近方案一，較短的 funnel 讓訊息盡量進來 [name=mrorz]

:::info
方案一 vs 方案二
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3088f7abe23dcf58082102a3eeb82b85.jpg)

:::

### RSS UI

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_976acaf73eb70f5aa10150caed1a0c98.png =x300)

> - Ticket: https://github.com/cofacts/rumors-site/issues/262
> - IFTTT 嘗試：https://g0v.hackmd.io/@johnson/BkjIIk8B8#Subscription-w-IFTTT-Applets
>     - 遇到 pubDate 設定錯誤問題 （https://github.com/cofacts/rumors-site/tree/rss-pubdate-fix ）
> - RSS 選單改版 https://g0v.hackmd.io/@johnson/ByAb_n24U#RSS-feed-調整

文武：
選項只有
- Email
- IFTTT
- Feedly

orz
看要不要點下去之後有跳窗
每個選項都是 tab

文武
好像只有 IFTTT 需要教學

lucien
Feedly, email 的服務可以帶網址 不太需要設定

> The Free plan provides access to core IFTTT Platform developer tools so you can get started building services without an upfront commercial commitment. When you’re ready to publish your work and make it available to others, you’ll need to upgrade to one of the paid plans.

src: https://platform.ifttt.com/docs/faq#reviews-and-publishing

Ex:
https://ifttt.com/applets/VrzvihCR-cofacts-rss-line

orz
要先引導使用者登入
然後再複製 RSS URL (他的預設值無法透過 URL 指定)

或是直接讓使用者 follow 網路上的教學文
- https://blog.gslin.org/archives/2020/04/30/9505/用事實查核中心的-rss-feed-加上-ifttt-自動通知到-line-telegram-內/
- https://free.com.tw/line-notify/

Lucien
如果成本可以接受，還是可以出一個教學
很複雜的話就出影片

email 二選一要選哪個？

orz
可能是 Feedrabbit 吧

lucien
最後選項會變成
- Email (via FeedRabbit)
- Feedly
- IFTTT
- RSS link

只是 USD 199/year 可以ㄇ

bil
不貴呀 linode 比較貴

:::success
IFTTT 方面：假設可以用 applet，填好 RSS <> Slack, LINE, Telegram
Lucien 出 wireframe
https://www.figma.com/file/YikWPPauMnukDH0U2Nq4YS/Components?node-id=1%3A310
:::

### LINE bot onboarding UX
> 過去的討論：https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2F%40mrorz%2FS1cpqgCpr
> 後來沒有留下成果圖 QQ
> 

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b875d6ca30afbb259c1c8f59006973ec.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_27609bb865e00c8127ee064b9476a2d4.jpg)


### Reply search 相關討論

Issue: https://github.com/cofacts/rumors-site/issues/295

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0f5c087f6ca54b936f103e17da2437d0.png =x400)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5718d04aacde7cd1b351b7284ed4bb16.png =x400)

:::danger
Any conclusions?
:::

## 8月編輯小聚

> 上週討論：https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2F9qp8dE7dReK2q8FTeP9Feg
> 8/29 or 8/30


## :potable_water: Release pipeline

### :star: Released to production

網站在大松前上了讓 category [能斷行的 PR](https://github.com/cofacts/rumors-site/pull/296)

### :rocket: Staging

#### :robot_face: Chatbot

https://github.com/cofacts/rumors-line-bot/compare/master...dev

##### Feature
- #201 Record viewed messages (`userArticleLinks`)
- #207 Notify user of new replies

##### Bugfixes
- #211 Fix undefined session ID error

##### Others
- #210 hint user to permit LIFF "send to chatroom" permission
- #206 Google Analytics of LIFF

##### Testing checklist

Staging chatbot: https://lin.ee/1QUzEX4nI
尋找測試用舊訊息： https://dev.cofacts.org/articles

- [x] 應可送出「全新訊息」
    - [x] 問訊息來源時選擇「我自己打的」或「LINE 外面看到的」，應該會被擋下。
    - [x] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，訊息應該還是有被送出。
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以修改理由送出。查看 article page 看理由是否有被送出。
    - [x] 「分享到 Facebook」、「分享到 LINE」可以正常運作

- [x] 送出「沒回應」的舊訊息，應可送出新理由
    - [x] 跳出來源視窗後關閉，文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。
    - [x] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，可以看到再打開的選項
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
    - [x] 「設定推播功能」更改後再次打開，應該會保留原本設定
        - Not available
    - [x] 「查過的訊息」應該要列出之前查過的訊息
        

- [x] [#211](https://github.com/cofacts/rumors-line-bot/pull/211) Fix verification

##### ⛔️ Release Blockers

無

##### 未竟項目

- 按下「我自己寫的」之後再捲回去按其他來源，會把來源當成新訊息送進資料庫 [name=nonumpa]
    - 因為之後會拿掉來源，所以可能不用修 [name=mrorz]

- 點按查過的訊息，會更新時間（少於一分鐘前看過）但左上角還是顯示「1 則新回應」 [name=mrorz]
    - 理論上 [557eb0e](https://github.com/cofacts/rumors-line-bot/commit/557eb0e2ec2b8fbb75d1674e816616b122236ef9) 應該要修好它，看起來並沒有⋯⋯囧
    - 因為還沒有放 rich menu，所以不是 release blocker

#### :globe_with_meridians: Website

https://github.com/cofacts/rumors-site/compare/master...dev

##### Feature

- #297 Improve usability for reply editor

##### Bugfixes
- #296 Support line breaks in category description
- #298 Fix data loading error caused by refactor
- #299 Fix bug that iOS cannot use global search

##### Others

- #287 #289 #290 - Reorganization / refactor; extract `<Tooltip>`


##### Testing checklist

http://dev.cofacts.org/

**未登入**下檢測：

- [x] Article list
  - [x] Filter works
  - [x] Sorting works
  - [x] Can go to article page

- [x] Replies list
  - [x] Filter works
    - [x] 不允許選擇 Replied by me
  - [x] Sorting works
  - [x] Can go to article page
  - [x] 不允許 upvote / downvote replies
  - [ ] Can see vote reasons
      - [bug](https://github.com/cofacts/rumors-site/issues/291)

- [x] Hoax for you
  - [x] Filter works
  - [x] Sorting works
  - [x] Can go to article page

- [x] Article detail
  - [x] Can see similar messages ( https://dev.cofacts.org/article/1fi7dla9wtwjn )
  - [x] Cannot submit, upvote, downvote reply request
  - [x] Cannot submit, upvote, downvote reply
  - [x] Cannot add, remove, upvote, downvote category

- [x] Search
  - [x] Can use global search to perform search
  - [x] Can use textarea in header to perform searchs
  - [x] Can list searched articles
    - [x] Filter works
    - [x] Sorting works
    - [x] Can go to article page
  - [ ] Can list searched replies
    - 壞惹！
    - [ ] Can go to reply page

登入自有帳號後檢測：

- [ ] Replies search page
  - 壞惹！
  - [ ] can upvote / downvote replies
 
- [x] Replies list
  - [x] 可選擇 Replied by me
  - [x] can upvote / downvote replies

- [x] Article detail
  - [x] Can submit, upvote, downvote reply request
  - [x] Can submit, remove own reply
  - [x] Can upvote, downvote other's article reply
  - [x] Can add, remove, upvote, downvote category

- [x] Can logout

##### ⛔️ Release Blockers

- Search reply 壞掉惹 [name=bil]
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9f585dcc0b3893d2ac9827df89cfc9b7.png)

##### 未竟項目

- 手機上 filter 按 X 會以為是 cancel [name=bil]
    - 實驗之後才發現是按下去就會 apply
    - 應該要改成「確定」或「OK」按鈕
    - Figma: https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=2322%3A0
- filter 取消後還是有半透明 [name=nonumpa]
    - 那個是 material design 按鈕的 focus state，可以按 tab 換按鈕；但確實有點 confusing 可以拿掉。
- Comment 的送出理由按第一次會觸發 blur 沒按到，要按第二次才會真的送出

### :eye: Under review

- [修正 reply request 無法顯示超過 10 個](https://github.com/cofacts/rumors-api/pull/187)

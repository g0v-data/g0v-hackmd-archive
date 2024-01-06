---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20200916 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：nick, bil, mrorz, nonumpa, zoe, lucien
:::

## Cofacts Next! 追蹤

- [收尾] Chatbot notification
    - 啟動的話新使用者會收到推播
    - 等介紹 rich menu 再啟動 Cronjob

- `ArticlePageLayout` refactor
    - All done, in PR; see Under Review
    - 接下來做 profile page UI

- User ID refactor
    - 開了票

- 教學頁設計
    - owner: 志超
    - 「是什麼」的部分排好了，之後會做手機版
    - https://g0v.hackmd.io/sB_zayWjTo-W0R7xe_U34w

## Rich menu deploy

新頁面追蹤點按數據：
https://datastudio.google.com/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/DtzfB

## 編輯小聚

- [x] 主題：
    - 孔子媽媽待產日
- [x] 時間：9/27 (日) 14:00-17:00 Ronny keyholder(借13:30-17:30)
- [ ] 
- [x] KKTIX:https://cofacts.kktix.cc/events/cofacteditor21
- [x] 準備貼紙
- 場地：青平台
    - [x] 場地單
    - [ ] 食物
        - 4000 贊助的食物
        - 龜珍嘎琳贊助的食物
        - ~~論語裡有什麼食物嗎 [name=mrorz]
        - ~~樓下的甜點 La Grotta 很好吃，會問一下是不是要提早訂 [name=bil]~~ 太多了，但可以訂個飲料
    - [x] 延長線 (場地有)
    - [ ] wifi
        - [ ] Nighthawk M1 + 4G sim
        - [ ] ASUS RT-N12 Wireless N300 (2x 5dbi高增益天線)
- [ ] 誰會來呢？
    - mrorz, bil, lucien, nonumpa, zoe (maybe)
- [ ] 誰不會來
- [x] LINE 文案：see https://g0v.hackmd.io/5JMzChJOQPqKe_CX_wbRmg#%E7%B7%A8%E8%BC%AF%E5%B0%8F%E8%81%9A

## FB group announcements

### Opendata

```
Cofacts open data 加入每日 LINE bot / website 個別訊息的瀏覽量資訊囉！

資料在這：https://github.com/cofacts/opendata#analyticscsv

- 資料範圍：網站為 2017 年 3 月起，LINE bot 為 2018 年 4 月起；兩者都有包含 2018 與 2020 大選前後期間
- 資料來源同 https://cofacts.org/analytics ，但是是以 CSV 形式放在同一個檔案，無需在 analytics 頁面單次下載
- 有將相同對象、不同 URL的瀏覽量 (如帶有 fbclid 的版本) 合併計算
```

https://www.figma.com/file/zwThV99c4dHkFdIPg3Ii0T/Cofacts-%E7%99%BC%E6%96%87%E7%94%A8%E5%9C%96?node-id=119%3A19

### article detail New analytics 上線

> 感謝 Zoe
> 

bil 要寫草莓蛋糕功能

### Rich menu 介紹
> bil
> 

使用教學：（需要更新）
教你使用Cofacts 查訊息：
cㄏ查核工具第一步，練習轉傳訊息給Cofacts！

報名小聚：小聚資訊
2個月一次的小聚，媒體識讀教育與查核技巧訓練大會

官方網站：(就是官網)
看看Cofacts 的介紹與目前的成果

分享：讓好友也加Cofacts好友，讓查假新聞的機器人幫助更多人！

設定:通知 use push message
打開開關，志工查到我問的訊息會通知我查到了。
(不打開就不通知囉)

問過的問題
~~可疑訊息筆記本，~~ 忘記上次問過什麼嗎？從這裡查一查。
~~上次那則沒人查過的訊息現在有人查核啦！！快來看一看~~

:::warning
LIFF title
/settings 要換成「設定」內文要翻譯
/articles 要改成「問過的問題」

https://github.com/cofacts/rumors-line-bot/issues/224
:::

### 討論LINE貼圖喔



## UI design issue


### Detail page
https://www.facebook.com/groups/cofacts/permalink/2800424580189353/
- 使用者找不到登入（手機版？） [name=mrorz]
- 在沒有回應的時候，使用者會把「我想補充」的那些留言當成是「結論」。這件事情王大師也誤會過唷（舊版 UI） [name=mrorz]

> 增加一條「有多少人想知道訊息的真實性」
> 樣式同下面「查核回應」
> [name=nick]

--> https://github.com/cofacts/rumors-site/issues/336

> firefox 右邊的 related article 會很長
> [name=nick]


### List page

>  關於文章頁面的排序選項
https://g0v.hackmd.io/ahtI6xsFRQyxktrIlc1VcQ#%E6%8E%92%E5%BA%8F%E9%81%B8%E9%A0%85%EF%BC%9A
> 「最少人查核」感覺會有一堆沒人查過的排在前面，這個選項的用意會是什麼呢？
> 現在實作的「最近被查詢」「最近被回應」「最多人詢問」是否已經足夠呢？會有人在「可疑訊息」（含有回過跟沒回過）這個頁面選用「最近被回應」來排序嗎？
> [name=mrorz]

> 最多人問是最常用的喔
> [name=mrorz]

> 一樣是方便讓編輯找需要被查核的文章
> 不過如果都導去等你來查的話
> 這邊的確可以改成最多查核
> [name=lucien]

> 不過用 article reply count 排序的話，會有一堆 0 reply、一堆 1 reply 等等
> 0 reply 的那些彼此又要用什麼排呢
> [name=mrorz]

> 文章收錄時間
> [name=lucien]

orz:
會想要用「最少人查核」嗎

bil:
不會


### Analytics

> 我之前有測一些手機尺寸，殊不知我自己的手機是edge case xDDD
> [name=zoe]
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f33f22901595b8dadc6879552495fc31.png =x300)


> 我覺得與其顯示 visit 數，換成顯示 user 數好像比較好
> 以這篇為例，我自己下去闢謠的時候本身就會瀏覽這個網頁數次
> https://cofacts.org/article/1t9ab4bz71dwy
> 圖表上看起來好像有 15 web visit 很多、跟前一天比看起來「變熱門了」，但實際上只有 5 user，前一天的 8 user 才是高峰。
> ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_49ebae71526daed1ec08d14cc2be69fe.png)
> [name=mrorz]

> 看到圖表實際在 production 上運作，我才意會到在 visit 數稍低的時候，visit 數在判讀「人氣」上還滿可能會失真的，可能用 webUser 作圖比較合適呢。
> [name=mrorz]

> hmm…原本思考方式是讓 Line 跟 web 的數據有可比性
> query 數也是 PV 而不是 UV 的概念
> 如果 Line 那邊也做成 UV ，我覺得可以一起換
> Line 有UV可以拿嗎
> [name=lucien]

> 我們有把 LINE user ID 傳給 google analytics 所以 GA 分得出 user
> 像這樣～
> https://files.slack.com/files-pri/T02G2SXKM-F01ASNE8GAV/image.png
> analytics 裡折線圖 show 的是 visit，user 只有顯示 aggregated value
> 但 cron job 打 GA 其實也撈得到 daily user，跟 visit 數字不一樣～
> [name=mrorz]


> 那可以改成 UV ，但 wording 要想一下
> 幾人次詢問？
> [name=lucien]

> N 人瀏覽此頁 / M 人在 LINE 查詢
> N visitors of this page / LINE inquiries from M users
英文越來越長了 XDDDD 這下手機上肯定要分行
> [name=mrorz]

----

- 要用 icon 嗎 [name=nick]
- 還是用有顏色的數字，點擊才會有 tooltip 寫說是 web users / line users [name=zoe]
    - 因為 legend 拿掉，下面的 hover tooltip 也會需要 color coding [name=zoe]

- Zoe 已開票：https://github.com/cofacts/rumors-site/issues/332

:::success
採 Zoe 的改法
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

[9/10 Release](https://github.com/cofacts/rumors-site/releases/tag/release%2F20200910)

- #315 Line chart in article detail page
- #211 Takes 2 back button to get out of article detail page

### :rocket: Staging

#### :electric_plug: API

https://github.com/cofacts/rumors-api/compare/869bfcb4f24791793781f9a89d546d830e614fad...c2360819b7c9e5c1d4df32d95acdd7d2c584f650

##### Others
- #221 Cleanup unused methods

:::info
No need to test manually
:::

#### :globe_with_meridians: Site

https://github.com/cofacts/rumors-site/compare/master...dev

##### Features

- #321 Track RSS usage in Google Analytics

##### Bugfixes

- #291 Display feedback text from LINE users
- #307 Display 25 items in article list

##### Others

- #319 Rewrite feedback control so that it loads feedback when opened
- #288 Replace <ArticleItem> with more reusable card components

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
  - [x] Can see vote reasons
- [x] Hoax for you
  - [x] Filter works
  - [x] Sorting works
  - [x] Can go to article page
- [x] Article detail
  - [x] Can see similar messages
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
  - [x] Can list searched replies
    - [x] Can go to reply page

登入自有帳號後檢測：
- [x] Replies search page
  - [x] can upvote / downvote replies
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

Nope.

##### 未竟項目

Nope.

#### :robot_face: Chatbot

https://github.com/cofacts/rumors-line-bot/compare/master...dev

##### Features

- #218 Highlight search text when listing articles

##### Testing checklist

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應
        - [x] highlight 有中的字

- [ ] 送出跟舊訊息相似的訊息，應提供選項選擇最像的訊息
    - [ ] 按下任一訊息應該會列出回應

##### ⛔️ Release Blockers

##### 未竟項目

### :eye: Under review

#### :electric_plug: API

- [Category fix](https://github.com/cofacts/rumors-api/pull/218)
- [Connection interface (required by rumors-site ArticlePageLayout refactor)](https://github.com/cofacts/rumors-api/pull/217)
    > 基本上是為了這個做的：
    https://github.com/cofacts/rumors-site/blob/pagelayout/components/ListPageControls/LoadMore.js#L77
    >
    > 因為有些 component 可能會跨列表共用
    > 無論是 Article 列表還是 Reply 列表可能都要用到
    > 但在用 fragment 寫 data dependency 的時候，又必須要指定這個 fragment
    > 是 base on 哪一個 type
    > 所以這裏把形狀類似或相同的 object type 都加上 interface，這樣 fragment
    > 就可以直接 base on 這個 interface 來寫。
    >
    > 應該是沒啥 breaking change～ [name=mrorz]

#### :globe_with_meridians: Site

- [Layout components for header](https://github.com/cofacts/rumors-site/pull/328)
- [Remove ArticlePageLayout from /articles, /hoax-for-you and /replies](https://github.com/cofacts/rumors-site/pull/330)
- [Remove ArticlePageLayout from search page](https://github.com/cofacts/rumors-site/pull/331)

## Chrome of Android issue

> 請問手機版 Google Chrome 是不是打不開下面這一頁？
> https://dev.cofacts.org/article/1qdrhpprhoozr
> [name=mrorz]

> 可以開
> android 不過chrome是舊版67
> [name=cai]

> 會crash
> [name=lucien]

> 我的是 85.0.4183.101
> 看起來確實是 Google 又搞 optimization 搞到 segfault lol (edited) 
> [name=mrorz]

## rumors-db indexing

- 想要把 version 寫在各個 schema 裡面， `reloadSchema` script 改一下 [name=mrorz]
- 也可以把版本記在資料庫裡面 有點像是防呆
  其實 alias 已經是一種 versioning [name=zoe]
- mongoose 有個 `_v` 在每一個 record 裡面，可以撈出特定 version 的來 migrate [name=lucien]

## 希望編輯能插入圖片

### 需求討論

- MyGoPen, TFC 上稿介面都有可以插入圖片的功能 [name=bil]
- 比較難想像編輯會願意做圖來回應 [name=mrorz]
- [台南小聚時有使用者提出這個需求](https://g0v.hackmd.io/@NFi0czulSemxCM8RNSlz8Q/HJ8xT3QVU/%2FwjmUeQunRICXQG_0lXWpLw)，可能是 [name=lucien]
    - FB 討論很長一串，他想要只截出這段
    - 文章很長，他想要只截某個段落
    - 影片的某個影格
- 有 URL 比較能讓讀者追溯出處源頭吧 [name=zoe]
    - URL 可以放在出處的地方 [name=lucien]

### 執行問題

- 插入圖片要實作有些麻煩（UI（可能有現有的套件）、儲存圖片的空間）[name=mrorz]
- 不知道要如何顯示在 LINE bot / 未來的 FB bot / 其他應用中 [name=mrorz]
- 可能提供 markdown 語法 [name=lucien] / img 標籤 [name=bil]
    - 那可能要能讓編輯預覽，才能看語法對不對，畢竟錯了必須刪掉重發 [name=mrorz]

## 行銷

- 行銷有什麼目標嗎？Facebook 互動數好像沒有很多，網站似乎瀏覽數不少，LINE bot 好友約19萬 [name=nick]
- 網站比較好，LINE bot 有點像是數字，有可能是被封鎖的 [name=nonumpa]
- Facebook 行銷的目標應該是連到LINE或是網站 [name=lucien]
- 那在網站裡面放 QR code [name=bil]

## Avatar

- stroke 顏色：黑色
- 人 / 衣服 fill color: white
- 背景顏色：https://www.figma.com/file/Xr80rEWwCrNks1uFIrGCG4/Cofacts-Colors?node-id=0%3A1
- 姿勢：固定半身

## User ID
- 邏輯會寫在 rumors-api (rumors-db 裡的幾乎都跟欄位有關，但這次比較像 fillAllHyperlink 跟程式邏輯更有關)
- `appId-sha256(appUserId)` 比較不會 collide
- 可以加 `users.lastActiveAt`，先假設 collision 不會發生，用`appId-sha256(appUserId)`撈 user 出來的時候順便更新`lastActiveAt`，再檢查`(user.appId, user.appUserId)`是否一樣



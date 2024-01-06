---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210127 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：Bil, MrOrz, hsiao, 文武, Zoe, lucien, chihao
:::


## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

https://github.com/cofacts/rumors-site/releases/tag/release%2F20210122
- #367 #374 #368 #369 #375 #373 #378 User profile page

### :rocket: Staging

#### :globe_with_meridians: Site

- #381 #382 #383 Editor hint -- kudos to ulayab
    - Fixes: [#362](https://github.com/cofacts/rumors-site/issues/362) Provide better text for reference input
    - Fixes [#361](https://github.com/cofacts/rumors-site/issues/361) Provide better placeholder for editors
- #385 Avoid attaching text for logged in users
- [#384](https://github.com/cofacts/rumors-site/pull/384) Update terms to match suggestion from Lucien

## 2021 一月二月計畫
- 1/31 COVID-19 Open fund close
- 2 月：公布新 terms 與 API header
- 2/4 AI4SG (四) 14:00 ~ 16:00
- 2/21 編輯小聚
- 2 月底：enforce API header


### 1/31 GNI COVID-19 Open fund

撰寫計畫中

### 1 月底 - 影片 60 秒

> bil

### 2 月 License

- 網站使用者條款 https://docs.google.com/document/d/1JvKQFnkmH75jR9QUfkEnUi_Gro12TmEcdb5thQFpJng/edit
- 聊天機器人使用者條款 https://docs.google.com/document/d/1Mfz2Av17cXqf01QHFlOL8AY5kBA9kn2dYxqyNni5Hg8/edit
- 開放資料使用者條款 https://docs.google.com/document/d/1ptywehV7VLKeXADsCuqx0klVyRmnxhnon92p6xSD1zg/edit
- TODO:
    - API client management https://github.com/cofacts/rumors-api/issues/244
    - 網站 attribution 更新 https://github.com/cofacts/rumors-site/pull/384

### 2021 AI4SG Award
1. 頒獎典禮：2021/2/4（週四）14:00~15:00
1. 茶會交流：2021/2/4（週四）15:30~16:00
1. 典禮地點：精誠集團內湖大樓B1（台北市內湖區瑞光路318號B1，需在1F換證）
1. 廠家影片與人物拍攝：2021/2/4 10:00~12:00 & 15:00~17:30（上午時段區分10點場與11點兩場次，若貴單位時間允許，可以先預約，下午時段參與茶會交流即可）
2. 我們邀請貴單位兩位出席人員，上台授獎後需要發表2-3分鐘得獎感言，同時也請簡單說明獲獎案例的推動目的與目前具體成效。還請最晚在本週五1/29下午16:00前回覆出席人員姓名與職稱

### 二月開發項目
選項見[上週討論](https://g0v.hackmd.io/JUVhhxSmSx62O5SUVuJ1rw#%E4%BA%8C%E6%9C%88%E9%96%8B%E7%99%BC%E9%A0%85%E7%9B%AE)
+ Avatar edit dialog
    - 照 API 回傳的 available type 提供選項
    - 提供 preview
    - openpeep 參考 react-peep https://www.opeeps.fun/
+ Github-like contribution
    - 要算成「貢獻」的：
        - article.articleReplies
        - articleReplyFeedback
        - replyRequest.feedback
        - replyRequest
    - 研究 elasticsearch bucket aggregation (跨 index)
        - 是否可以用 nested 欄位的 createdAt 來 aggregate
    - 可按照 effort 加權 (optional)


## Profile page pilot study results 

From [上週會議記錄](https://g0v.hackmd.io/JUVhhxSmSx62O5SUVuJ1rw#Profile-page-pilot-study-results) & [成果](https://g0v.hackmd.io/lIedGsQWTeScBTWfr4Zq0w)
- 增加顯示「何時加入 cofacts」[name=一-4]

## Editor 相關 UI idea

### 時間顯示
> 周三討論到網站日期顯示
讓我想到最近遇到兩個也是跟日期有關，但是是跟闢謠有關的
第一個是過時的回應
https://cofacts.g0v.tw/article/3lnetvzfdkm62
這個 2019的訊息，在 2021 年又在傳，導致困擾
另一個是在醫院工作的親戚，前幾天知道北部確診醫師的醫院門診照常，但今天聽到別人指稱該院封院時，還是來問我。即使他在幾天前就知道正確資訊，但第一次接觸謠言時，還是會覺得是不是有什麼「更新的資訊」自己沒 catch 到。
我覺得上面兩種狀況，都可以透過 chatbot 加註這個回應「多久以前回的」、訊息「多久以前就在傳」，增加大眾意識到時序的重要性
> [name=mrorz]

Facebook: 當下是 1/27 2:00PM 的時候 --
5m, 2h, 18h, 2d (for January 25 9:40 AM, comment)
Yesterday at 11:06 AM
January 25 at 1:25 AM
January 25 11:27PM
July 10, 2020

:::success
差異 24hr 內：hour
> 24hr 但落在昨天：yesterday
昨天以前：月、日
其他：年、月、日

Or use https://date-fns.org/v2.16.1/docs/formatRelative for time difference within 48hr
:::

### 登入鼓勵

> 是說 etoro 每天第一次登入的時候，都會說「恭喜！您最近 N 天賺了 OO 」或「報酬率 OO%」
> 發現那個天數常常會變，感覺像是他準備了幾個數字，然後 show 一個正最多的數字這樣。
> 如果一日報酬率是負的，就試試 7 天報酬率之類的 XDDD
> Cofacts 如果也實作這個大家覺得如何？ XDDDD
> 網站第一次登入的時候利用現在的 API 拿到不同區間的各種數字，然後挑一個棒的來顯示之類的
>「你的回應最近 7 天超熱門，有 42 人看過」
>「最近 30 天有 690 人覺得你寫的回應很棒！」
>「24 小時內對你的回應說讚的人增加了 300%！」
>「最近 7 天你寫的回應被其他編輯引用了 9 次唷！」
> [name=mrorz]

- 「你的回應最近 7 天超熱門，有 42 人看過」- Query analytics with docUserId within 7 days (ListArticle(filter 自己回過的) + analytics )
- 「最近 30 天有 690 人覺得你寫的回應很棒！」 - 直接撈所有 article reply feedback 的 article reply 的 user 來算，或需要在 article reply feedback 上加上 `replyAuthorId` 或 `articleReplyAuthorId`
- 「24 小時內對你的回應說讚的人增加了 300%！」 - 同上
- 「最近 7 天你寫的回應被其他編輯引用了 9 次唷！」 - 用 list article 撈出所有最近 reply 的 article 再來計算，或 article reply 加記 `replyAuthorId`。

數字估算：選擇數字比較大的。ex: 690 人 > 42 人 > 9 次 > 300%

### 推薦標籤

> Idea: 利用「相似可疑訊息」的分類來推薦分類。可以在「分類建議」按鈕後面做一鍵增加的鈕。
> 例如說 COVID-19 的新訊息 https://cofacts.tw/article/j1al35fna5au ，進來的時候還滿常有已經標過分類的相似可疑訊息，但每次點開「分類建議」按鈕都要找好久的分類。
由於分類未來只會越來越多、手機螢幕大小依然有限，list traversal 本身無法改進太多（最有用的可能是加個搜尋框），不如直接用「相似可疑訊息」的分類來推薦。
> [name=mrorz]

## 其他變更

### SEO & nginx 設定
https://github.com/cofacts/rumors-deploy/pull/15

想要把 cofacts.tw 當成 canonical URL
- 比較短
- 可以把打錯字的 cofact.tw 也導向去 cofacts.tw

## Downstream bot 數據彙整

趨勢科技有：
- 任意時間範圍的「偵測到有謠言的次數」（無論 Cofacts 是否有回過）
- 2020/10/16 起的每週 Cofacts 結果卡點擊數（referral count）

美玉姨有：
- 2020 年 LINE bot reply message count by 月、週、日
- 2020 年 LINE bot 增加好友數 by 月、週、日
- 2020/11/20 起的個別 article 詢問次數 by 日

交集：無⋯⋯囧

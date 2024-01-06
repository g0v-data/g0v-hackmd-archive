---
tags: cofacts, meeting note
---

20190403 會議記錄
=====

> 上次開會紀錄：https://g0v.hackmd.io/s/rJdASkduE

## 4/10 開會
GGM 主持

## 四月小聚

- [ ] 邀請人？ --- 沒有，MrOrz 問 IFF 人
    - 10~15 talk + Q&A
    - 可以 recruit
    - 車馬費實報實銷
- [x] kktix 
- 散佈
    - [ ] Facebook fanpage
    - [x] Facebook group
    - [ ] LINE bot 貼文
    - [x] LINE bot richmenu
- [ ] 場地 - GGM asking
    - [ ] 茶水
    - [ ] 麥克風
    - [ ] 食物

### 貼文



### 新貼紙
希望有新貼紙
小狗小豬各50張(等Lucien給圖before 13)

## 大松發文 ＆ FB group

### 覺得沒用的理由 網站版

Github: https://github.com/cofacts/rumors-site/pull/158

阿奇++

## 比鄰錄音

寂寞的一週。
pm5 說可不可以把稿子放在 rand0m 讓大家讀
但搜集太花時間

## 對外

### NOFO

> g0v#intl Lulu Keng [11:13 PM]
>
> 美國在台協會 (AIT) 轉來一個獎助金機會，希望針對 propaganda and disinformation，申請者提出各種創新解法，因為線上公開資料很稀薄，因此有興趣的人可以看下面的完整檔案。 4/19 截止。
> 
> 公民團體、私人企業、媒體、NGO、學術單位都可以申請。

Stage 1: 3-page concept paper

> The concept paper shall not exceed three pages and must strictly adhere to formatting requirements.

- Concept Paper
- Summary Budget and Budget Narrative
- Theory of Change Worksheet
- Indicator Reference Sheet
- Pre-submission Checklist

**SUBMISSION DATES AND TIMES**
23:30:00 U.S. Eastern Daylight Time (EDT) on Monday, 29 April 2019

推薦誰投呢？
- Schee (by MrOrz)
- TFC (done, bil)
- 沃草 (done)
- 假新聞清潔劑 (done, bil)

:::success
GGM 寫
Bil 主題：answerfamily
:::

### Tech4Democracy Case study

Email subject: Case study of Cofacts

:::success
已經去信要求延 deadline - 5/3 前。
:::

### coscup 社群軌投稿

https://blog.coscup.org/2019/04/2019-cfp-open.html#g0v

> 哈囉，g0v 今年也參加了COSCUP 的社群議程，今年 g0v 社群議程原則上包含下列主題—「開放政府」、「新媒體」、「公共服務」、「開放資料」、「社會參與」和「基礎建設」這幾個大方向。歡迎各位投稿分享你今年的專案吧！

- Call for proposal deadline: 5/6
- COSCUP: 8/17, 8/18 @ 台科大

:::warning
沒人有興趣，4月中再來
:::

### LINE 轉移

#### 4/8 Migrate日之前

- [x] 取消「專屬ID」(Premium ID) [連結](https://admin-official.line.me/6746905/business-store/#/premiumId)
- [x] Disable Webhook、停用所有API相關功能（例：停用Rich Menu)
- [x] 在LINE@ Manager後台設定自動回覆
- [x] ~~完成API Channel 轉移~~ ~~bil 問問 Rachael 這是啥~~ bil 問完了，好像沒有具體動作
- [x] 下載所有統計數據 - [Statistics](https://docs.google.com/spreadsheets/d/1h9YAmi5i_dpYGYG5xUBBiW2Q_W0-ylJocb-MKY2nffc/edit#gid=1028201036) 已經更新至 2019/4/4，且與 [analytics](https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/Cy2P) 連動。

##### 停機公告

Target:
- [x] LINE 主頁
- [x] FB粉專
- [x] FB group

:::success

【🚧 Cofacts 真的假的 LINE bot 停機公告 🚧】

大家還記得上周四的新聞嗎：
https://technews.tw/2019/03/28/fake-news-makes-line-works-with-four-big-fack-check-organizations-to-fight-fake-news/

🤖 作為與 LINE 合作的一環，「Cofacts 真的假的 | 轉傳查證」Line bot 在 2019/4/8（一）將會下線進行轉換作業，屆時 Cofacts LINE bot 會無法自動使用。

🌐 不過，Cofacts 網站（ https://cofacts.g0v.tw ），以及其他使用 Cofacts API 的服務（如美玉姨）不受影響。


若 4/8 當天有查訊息的需求，可以試試把謠言傳給下面的 Cofacts 好朋友唷！

MyGoPen
https://line.me/R/ti/p/@mygopen

蘭姆酒吐司
https://line.me/R/ti/p/%40qvy7263f

台灣事實查核中心
http://line.me/ti/p/%40rqd9861a
:::

##### webhook 自動回覆

:::success
【🤖 Cofacts 機器人休息中 💤】

今天（2019/4/8）LINE 在幫 Cofacts 升級唷，目前 Cofacts 無法回話。

推薦您今天試試把謠言傳給下面的 Cofacts 好朋友唷！

MyGoPen
https://line.me/R/ti/p/@mygopen

蘭姆酒吐司
https://line.me/R/ti/p/%40qvy7263f

台灣事實查核中心
http://line.me/ti/p/%40rqd9861a
:::

#### 4/8 Migrate日

當天LINE同仁通知升級已完成後，請完成以下動作
- 依新的Channel ID修改程式、並在新後台設置啟用Webhook
    - 到 Heroku 登入後修改下面的 env vars:
    - [ ] `LINE_CHANNEL_SECRET`: LINE@'s channel secret
    - [ ] `LINE_CHANNEL_TOKEN`: LINE@'s channel token
- [ ] 在LINE Official Account Manager後台停用自動回覆功能

> migrate當天user會找不到官方帳號
> 但是功能不會受到影響 api也可以用發文也可以

#### 4/11 release date 前

無法搜尋到該帳號

- - -

## 放寬理由為選擇題

1/19 實作理由之後，回報數從 1K -> 500
https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/ckUQ

bil
參與樂齡之後，發現有人是真的沒有能力填理由
所以會覺得說，如果能讓沒有能力的人填進來，也可以

所以如果有個理由按鈕說「我 60 歲」就讓傳進來
我也能接受

文武
但是那些有能力填理由的人，如果現在解禁了，也許他們就再也不會填理由了

而且他傳進來也收不到回應，所以因為很想知道而送新文章進來，並不會從我們這邊得到什麼幫助

bil
之後換 API 就可以

文武
那可以在換 API 之後再來討論

bil
可以提早規劃

orz
可以把 reason 改成 optional，然後多問他問題說你是在哪裡看到的
如果選擇「自己寫的」就不給送出之類的

orz
自從我們放理由之後，其實 TA 就換成年輕人了

bil
但樂齡的長輩會惱羞成怒，他就是不知道
readr 記者也回應說，為什麼要填理由，這讓他們覺得很不開心

bil
可以分成想要用 bot 闢謠的，以及完全不知道的人

:::warning
之後討論
:::

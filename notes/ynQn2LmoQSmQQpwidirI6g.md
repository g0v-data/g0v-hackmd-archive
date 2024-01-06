---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20200429 會議紀錄
=====
bil,orz, ggm, 2記者      　　　
Workis
> 線上開會： https://tico.chat/powercall?room=cofactshack&type=timeFirst
> 上次開會紀錄：https://g0v.hackmd.io/@johnson/rklCLhhOU

## 0523 大松
線上形式舉辦

https://g0v.hackmd.io/@johnson/rklCLhhOU#%E5%B0%8F%E8%81%9A

bil
因為有 RPG 的介面所以應該不用直播

orz
Spreadsheet 分工



## 5/5 (二) 政大媒體識讀

100人大班，10人上課
Spreadsheet 分工: 10篇 / 100 人


http://bit.ly/cofacts-nccu-2020


## 開發

GitHub activities
https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/WSQFB

### Staging site

目前上的版本是[PR-247](https://github.com/cofacts/rumors-site/pull/247)，內有所有 list page UI。

MrOrz:
RSS 好像要更新囧
在做 LINE bot notification 之前好像應該先把 RSS 修好並且宣傳一發

### Staging LINE bot

Staging: https://lin.ee/1QUzEX4nI

Current state diagram: https://docs.google.com/drawings/d/1sSzI0PSggkA3PPP99Nl18H4zMO4lk-2y5s7dGRNJwAE/edit
<img src="https://docs.google.com/drawings/d/e/2PACX-1vTeXGMSaPQadbe7kXay6n0vWWKHbLrMWtNB1xWuuH7SEO9KlPjDSML_TZgcuk6_kpsGLwM6YlosB1MI/pub?w=1428&amp;h=1057">

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_72032439a9c2df7ef7e97cf23a19ee10.png)


#### 已知問題

Feedback LIFF、source LIFF 與 reason LIFF 的 mutation 的作用對象，以及各 button 的 google analytics event 的紀錄對象，都是 context 裡的 `selectedArticleId` 或 `selectedReplyId`。
> (記的時候會記錯
> 麻煩的是收feedback
> 是跟否的judgement，但LIFF只有記到「有按是/否」
只有一種解，把context通通塞進postback


但是，目前的實作讓使用者按下 postback button 時可以[跳回當下的 state](https://github.com/cofacts/rumors-line-bot/commit/687edebb61b822b8a37802c84579863506c99318)，因此使用者點下舊的 LIFF 按鈕做動作、或舊的 postback button 時，會作用在當下的 `selectedArticleId` 與 `selectedReplyId`，即使該按鈕可能不是 for 該 `selectedArticleId` 與 `selectedReplyId`。

Proposed solution:
Preserve context in postback payload & LIFF JWT
https://github.com/cofacts/rumors-line-bot/issues/176

:::warning
再說
:::

#### 已知問題2

桌面版可以打開 ＬＩＦＦ 但是[不能用 sendMessage](https://developers.line.biz/en/reference/liff/#send-messages) 所以還是壞的

Proposed solution:
1. 先試試看 access token
2. 在桌面板擋起來，請他用手機開

:::success
試試看
:::

#### Enhancement
把 reason LIFF 的處理，放進 `ASKING_REPLY_REQUEST_REASON` 與 `ASKING_ARTICLE_SUBMISSION_CONSENT`，或獨立一個 state 處理，不要通通都塞在 `__INIT__`。
https://github.com/cofacts/rumors-line-bot/issues/177

:::warning
再說
:::

#### 送出 source 與 reason 後的訊息重複問題

| after source | after reason |
| -------- | -------- |
| ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_15bbaa98a3d1f7180ab9c1a13a9d75e7.png) | ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d0c7fe8cedec6526009ac67b3e4a98a7.png) |

ggm
會有點重複

可以一次放 4 個按鈕

orz
可以一段字、兩個按鈕、再一段字、兩個按鈕

lucien
上面那是互動體驗的 log
應該不會有人看吧

orz
不過問題是上面是偷送的，就看使用者會不會覺得怪

lucien

第二個 provide more info 其實不用是 highlight 色
因為他已經提供過理由了

這樣的話上兩個是灰色，兩個 bubble 可以合併成一個

但填了ｓｏｕｒｃｅ還沒填 reason 的可以不用 merge 成一個 bubble

:::success
改起來
:::

#### Feedback yes/no

GGM
按叉叉也會紀錄 yes/no 嗎

orz
會耶

但是這樣好像沒有寫很清楚

GGM
可能要改 wording 加上「我們已經紀錄你的回饋。」

:::success
加起來
:::

### Other bugs found
- reply request 無法顯示多過 10 則 https://github.com/cofacts/rumors-api/issues/164

- 為何要「傳送訊息到聊天室」的理由 https://github.com/cofacts/rumors-line-bot/issues/174

## ~~Landing page 討論~~ 下週討論

> from 志超

Discussion: https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1588067286.270900

https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=994%3A111


## 假名討論

random 生成存起來
API server 產生
存在 users index, id: `app_id:user_id`, app_id 來源是 https://github.com/cofacts/rumors-api/blob/master/src/checkHeaders.js#L7


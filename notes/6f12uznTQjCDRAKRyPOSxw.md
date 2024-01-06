---
tags: cofacts, meeting note
---

20200325 會議紀錄
=====

> RR, bil, mrorz, 文武, lucien, ggm
> 線上：https://hubs.mozilla.com/BD2XJ2u/cofacts-test/
> 上次開會紀錄：https://g0v.hackmd.io/@mrorz/SJsDsS1I8
>

## 3/14 大松檢討

> https://github.com/cofacts/rumors-site/issues/242

## Summit 議程

> Cofacts 擔任 g0v Summit 禮拜五 4軌的坑主之一可能性
[參考資料](https://docs.google.com/document/d/1ziR6q4IXA6MB-Mig_8KMwiwP0hC9DAnc9hatXKvPvMg/edit)

2020 年 12 月 3 日（週四）至 6 日（週日）
週五好夥伴要 hold track 有在地連結
希望有第四軌 但不知道

本來想找在地社群有動員能力的
但也可以問原本社群內有動員能力的專案
例如說 jothon 也不是在地社群

hold 一軌的話
半天決定議程、講師，自己 call for paper
責任是要自己找場地、工作人員 etc
購票系統 share，直播會有人

好想、新芽自己有一軌
週四午營有活動

orz
如果我們自己 HOld 一軌，講師又在台北，那就要想辦法把人搬去台南

R
對，等於是自己辦一天活動，沒有經費

自己覺得有點難，最多跟人家合

orz
合的話 感覺 ｊｏｔｈｏｎ 性質比較類似

bil
如果自己辦一軌，就要搬5~7人下去
我有空但大家有空嗎

可能以工作坊的形勢比較好
協助整理之類的，今年有分類功能
變成新世界 Cofacts 網站訓練營

R
這樣可能性大一些但要跟 summit 確認一下這是不是他們要的

bil
如果是找講者，那可能是找查核專業的人來分享
像君竺那樣的工作坊

orz
如果像是2年前的 summit 那樣呢
我們當時有個 90min 的 workshop 教大家抓重點跟練習回應

bil
對 90min
有一點點趕
可以分上下午場

R
hold 一軌的話要到 5~6hrs
不確定工作坊形式是否依樣
確實我們自己 5~6 hr 比較難


## LINE chatbot rich menu

### cover photo

（在 posts 的最上面）

bil
因為我們有很多新功能
可以推播一次之後
再放教學

lucien
cover phono 不會放教學吧

bil
比起形象 學會怎麼用更重要

lucien


:::success
等新功能做完再準備
:::

### rich menu 選項

- 教學
- [專案簡介](https://beta.hackfoldr.org/cofacts)
- [FB 討論區](https://www.facebook.com/groups/cofacts)
- (未來) 我問過的訊息
- (未來) 設定
- (不定期) 小聚報名

Lucien: 新的想放在塞吧

orz
可以先亂作一個 menu

lucien
可以請志超幫忙

## rumors-line-bot memory issue

[#166 Fix issue, limit number of image processing function didn't work](https://github.com/cofacts/rumors-line-bot/pull/166)

MrOrz:
要考慮 multiple instance 的問題嗎
原本是 variable local to process，最差就是每個 process 自己算自己的
但現在如果 scale up dyno count to 2，那後起的人會把 count reset to 0

文武
要想一下
不過現在沒有兩個 instance

orz
確實如此

可以先這樣上 ｐｒｏｄｕｃｔｉｏｎ

下禮拜看 counter 會不會怪怪

文武
multiple instance 目前想到兩個解法
1. dyno 起來的時候不 reset to 0，每個 instance 自己在多個變數紀錄現在有幾個 image 是自己處理的，在 process.on('SIGINT') 扣掉
2. 一樣 dyno 起來的時候 reset to 0，如果 desc 會小於就不做 => 有機會在剛 scale up 的時候 processing_number > max_image_number，不過等reset to 0 之前還在處理的 process 處理完就會變正常了

> 2 比較好寫
> 

[3/27 update (還沒deploy)]
看最近七天 memory quota exceeded 只發生一次，推測應該是這禮拜比較少圖片傳進 line bot

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_868cb50e2afcf5f37a3df7ac419f8cd5)

:::info
撈個 analytics data 來看看
:::

[3/31 update]
Daily and hourly input message type
https://datastudio.google.com/reporting/3a7f93c2-2b87-4852-83fe-76599eba88ad

## 開發
GitHub activities
https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/WSQFB

## LINE bot 互動修改

- LIFF redesign: https://g0v.hackmd.io/860RnxUGTi6z2Kca6ojAbg
- [#144 Revamp LIFF with FE framework](https://github.com/cofacts/rumors-line-bot/issues/144)
- [#145 Update article source wordings](https://github.com/cofacts/rumors-line-bot/issues/145)

### LIFF 互動限制

- 無法直接由 messaging API 觸發
  - 必須送出連結或按鈕，讓使用者主動點擊
- chatbot server 不知道使用者按了 LIFF
  - 需另外在 LIFF 內另尋管道通知 chatbot server
- chatbot server 不知道使用者關了 LIFF
  - 除非另外實作斷線偵測機制

### 互動

:::warning
注意標註「LIFF」的 UI，使用者可以「關閉 LIFF」！

要討論 LIFF 關閉之後：
- 使用者會看到什麼？
- 會卡在奇怪的狀態嗎？
- 使用者有辦法繼續前進嗎？
:::

#### 送出文章資料庫找不到
| 1. Submission consent | 2.過濾來源 | 3.蒐集理由 |
| -------- | -------- | -------- |
| ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_eecf6185b461521c296d0083d0f308f4 =500x)  | [LIFF]<br>請告訴 Cofacts 編輯，您覺得「⋯⋯」是「謠言」嗎？是在哪裡看到的呢？<br/>(按鈕)<br/>這應該不是謠言吧<br/>LINE 群組裡看到的<br/>LINE 官方帳號傳的<br/>有人私下用 LINE 傳給我的<br/>我在 LINE 外頭看到的<br/>我自己寫的<br/>| [LIFF]<br>感謝您送出訊息！<br/>http://cofacts.g0v.tw/articlexxx<br/>請問您為何會覺得「⋯⋯」是謠言呢？<br/>若能與編輯分享，會有助於讓編輯撰寫有用的回應唷。 |
| | 點按後：<br><br>若來源正確，透過 API 告知 chatbot server，chatbot server 送出訊息到資料庫、紀錄 articleId，且自動切到理由 LIFF。<br><br>若來源不正確，則 sendMessage，且自動關閉 LIFF。 | 送出後，透過 sendMessage 傳回對話框，自動關閉 LIFF |
| | 對話框 Reply: （來源不正確時）勸阻使用者不要傳進來。 | 對話框 Reply: 顯示送出訊息的 ＵＲＬ <br>![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7e3aa223114b3ed30768e0d1029e4042 =200x)
 |


:::info
- 訊息第一次進入資料庫，必先取得同意
- 訊息初次進入資料庫，先過濾輸入的來源
- 確認來源 OK 之後就可以送進資料庫，理由非必填。
:::

:::warning
LIFF 啟動時，要判斷他是否選過來源，來決定要顯示來源 LIFF 還是理由 LIFF。
:::

Lucien:
:::success


1. 選擇正確的 source 時也可以 send message，就當成是一種 Log
2. LIFF 下先提供收錄 URL
3. 分享的 bubble 裡增加修正理由的 LIFF
:::

#### 「這應該不是謠言吧」
R:
選項有些太多
像是在暗示其他人「要預先做判斷」

bil
以 Cofacts 的立場不太會限制什麼不能放
進來之後要怎麼使用，不太能控制

使用者不確定，才會傳進來

orz
所以問了也不會有效果

R
我們是在鼓勵使用者茶
現在有點反鼓勵

:::success
拿掉
:::


#### 選擇「沒有我送的訊息」
|0. Choose article| 1. Submission consent | 2.過濾來源 | 3.蒐集理由 |
| - | -------- | -------- | -------- |
| ![](https://user-images.githubusercontent.com/108608/64505727-79034500-d307-11e9-9389-7d81bf3d3d9a.png =200x) | ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_eecf6185b461521c296d0083d0f308f4 =200x)     | （同上）     | （同上）     |
| | | （同上）     | （同上）     |
| | | （同上）     | （同上）     |

:::info
一樣是 first-time submit，故與找不到時相同
:::

#### 選擇沒有回應的文章

| 0. Choose article | 1.蒐集來源 | 2.蒐集理由 |
| - | -------- | -------- |
| ![](https://user-images.githubusercontent.com/108608/64505727-79034500-d307-11e9-9389-7d81bf3d3d9a.png =200x) | [LIFF]<br>目前還沒有回應噎 QQ <br>為了幫助 Cofacts 編輯，想請問您是在哪裡看到「⋯⋯」這則訊息的呢？<br/>(按鈕)<br/>LINE 群組裡看到的<br/>LINE 官方帳號傳的<br/>有人私下用 LINE 傳給我的 | [LIFF]<br>請問您為何會覺得「⋯⋯」是謠言呢？<br>若能與編輯分享，會有助於讓編輯撰寫有用的回應唷。     |
| | 點按後：<br><br>透過 API 告知 chatbot server，chatbot server 送 reply request 到資料庫，且自動切到理由 LIFF。| 送出後，透過 sendMessage 傳回對話框，自動關閉 LIFF |
| |  | 對話框 Reply: 顯示送出訊息的 ＵＲＬ |

:::success
先照著做
類似於前面的流程
:::

:::info
- LIFF 在 1 顯示時就送出 reply request
- 來源跟理由都是 optional
:::

:::warning
1. LIFF 啟動時，要判斷他是否選過來源，來決定要顯示來源 LIFF 還是理由 LIFF。
2. 有可能會有兩篇文章都沒有 reply，都會觸發 LIFF⋯⋯
3. 使用者有可能點了來源之後，又選其他 article⋯⋯
:::


### Article detail 許願
https://github.com/cofacts/rumors-site/issues/243

Lucien 實現願望～
"皆在後面"的 wording

~~Replace~~ (沒有這個) / append （放進輸入框）/ use （直接蓋新的 articleReply）

:::success

要想一下 wording
:::

## Sync with OpenDream

回報 Cofacts 最近的進展
看看在這波 COVID-19 有沒有需要協助的地方


## 下次開會用什麼

- hubs:
- Powercall: +1
- jitsi:
- 實體:

## 0412

Maker 第四軌
希望有一軌是關於不實訊息的
disinfo和cofacts?

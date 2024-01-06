---
tags: cofacts, meeting note
---

20181205 會議記錄
====
orz/文武/bil/桓
> 前次會議記錄：https://g0v.hackmd.io/s/ryg1rCjAX
> 

## Dev items

### Facebook bot

#### 1. 直接把訊息貼進來

行為就會跟原本 Cofacts 一樣。

#### 2. 把文章 share 過來

桓：

收到的 message 會變成一個連結，如果權限允許，那就會去爬。

如果有個粉專 share 了外部的連結，有使用者 share 連結給 bot 的話，那只會拿到外部連結，會抓不到粉專的哪一篇文。

透過 messenger share 外部連結給人，似乎都是這樣。

文武：
Facebook share to messenger 的行為改來改去

MrOrz:
不過使用者看得到自己 share 了什麼，
所以應該還好

#### 3. Tag 粉專

桓：

希望可以用比較簡單的說法，用很像內容農場的方式回應
讓使用者會想要點進去

MrOrz:
如果 bot 回完之後又 tag bot 怎麼辦

桓：
如果按回覆，那就會再被 tag 一次。
使用者會追問，例如說「那這個的出處是什麼什麼」

Billion:
是自然語言問題嗎
像 Siri 可以準備一些亂七八糟話資料庫
平常功能就是那些，然後另外做閒聊資料庫
但這 API 很難處理
畢竟平常還是 lookup

MrOrz:
我們分得出第一次還是第二次被 tag 嗎

桓：
facebook comment 好像有 parent
如果 comment 內的 comment 或許 parent 有東西
但要試一下

所以先只回復第一次被 tag 嗎？

MrOrz:
嗯。

桓：
那就是，要把所有的符合的都給他嗎？還是前三個呢？

Billion:
符合的可能會有很多筆，前三個可能不會讓人想選下去
所以才會讓使用者一直很想要新增新的資料

MrOrz
tag 人這裡也能讓他新增嗎？

桓：
我想找一個點一下可以跳出 messenger 的功能
但好像沒有

#### 4. 分享給粉絲專頁 visitor posts

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_dd577c0a07b214b4596d88808c09be20)

桓：

如果他可以 share 到我們的粉專牆上的話，那我們可以做更多的事情
也可以直接收集他們回報的東西

這樣的話我就可以拿到 article id，然後可以嘗試丟 comment 給他

Orz:
那看起來 tag 粉專跟分享給粉專這兩個互動方式無法做送出文章流程。

如果我們被 tag 第二次，或者是使用者在分享的文章下面回文，那就把他們導引到 messenger 如何？

桓：
但我們的 messenger 也不支援自然語言問問題，預設是查詢模式。

還是把他們導引到 MyGoPen 或蘭姆酒吐司？

Orz:
可以呀
還是要導引他們在 messenger 再問一次？

桓：
導引他們貼過來再問一次嗎
嗯⋯⋯

Orz:
還是導引去 MyGoPen 就好

桓：
但如果他們留言的話，還是會回「找不到 XXX 的訊息」這樣耶。

- - -

Orz:

感覺很容易會觸發送出文章的功能。

我覺得或許在 FB bot 先不要做送出文章功能，讓他們只查詢，然後再看這幾種送出方式哪個比較好。

桓：
這麼多查詢方式，會不會讓使用者搞混。

Orz:
那我們就主要宣傳幾種方式。
tag 粉專應該宣傳效果最好，因為會直接在謠言下面，但不一定會有好結果，因為可能搜不到或顯示的都不準。

桓：
如果一次有很多搜尋結果怎麼辦？

Orz:
就給他們那麼多 Cofacts 網站 article link
可能每個都節錄一點，加上相似度之類的。
不過 facebook 可能會擋人貼那麼多連結。

- - -

Orz:
LINE 跟 facebook 會遇到依樣的事情，就是大家會跟 bot 聊天然後送出文章。

現在 LINE bot 是用理由在擋。你覺得理由有起到作用嗎？

Bil:
現在理由不太像是理由
有時候是「請查證」這種不是理由的理由
有時候是另一則謠言，那是 UX 的問題。

但可以理解說文章會怎麼被送進來，也是有一點價值。
有時候也有人被當成謠言澄清欄位使用

現在一個月可以順利送進來的有 1200 篇，每週約 300 篇。

bil:
如果是分成，左邊填訊息右邊填理由
兩個都填才能送進來

目前我們對 LINE 使用者很好，沒有在實際執行限制送出的事情。

Orz:
LINE bot 如果做 ＬＩＦＦ之後，使用者的轉傳訊息就不會被當成謠言，所以可以解決 UX 問題，但無法解決使用者理由填很爛（ex: 請查證）這種。

或許可以確定他不是聊天，但目前資料庫確實還是有那種一句話被送進來的。

**UX 可解決的 case**

- https://cofacts.g0v.tw/article/3gjrj6w9g0eyn
- https://cofacts.g0v.tw/article/2anwsecqqrgl8

**使用者就是想聊天的 case**

- https://cofacts.g0v.tw/article/1aec83lihmpyy
- https://cofacts.g0v.tw/article/ms4qtrzsc8h8
- https://cofacts.g0v.tw/article/1pdysd7ozvbcg
- https://cofacts.g0v.tw/article/2wzm73w8s6mul
- https://cofacts.g0v.tw/article/onzkrk8sdqj8
- https://cofacts.g0v.tw/article/ezi0lhek8108 (但附闢謠資料)

:::success
【結論】
先嘗試看看～
:::

### New bug: createdAt null will generate broken cursors
https://github.com/cofacts/rumors-db/issues/34

### LIFF

https://github.com/cofacts/rumors-line-bot/issues/115

Blocked by LIFF user consent bug: https://github.com/line/line-liff-starter/issues/1

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_01a4343facfbb7c9d0dd8436aa5c3544)

- https://github.com/cofacts/rumors-line-bot state diagram 部分：LIFF 取代掉 `xxx_SUBMISSION` state，在 LIFF 按「確定送出」就是送出。如果怕誤按，那就多個 `confirm()`，這可以用 LIFF 內的 javascript 做到。
- LIFF 按確定送出之後，會在前面加 prefix (我的理由是 (emoji))，透過 `liff.sendMessage()` 傳入對話視窗。
- Chatbot 裡的其他文字輸入，回歸「新文章」。不會再被當成理由。
- 桌機使用者：放生。同上週 Lucien 發言。
- 等待 LINE 技術端回覆。

### 讓 LINE 使用者可以回頭按按鈕，讀其他則文章或回應
> GGM

issue: https://github.com/cofacts/rumors-line-bot/issues/49

一天會被按 200 次！

桓：如果他們可以回去按，那 state 怎麼辦

Orz:
按鈕的 action payload 有長度限制嗎

桓：1000

Orz:
那好像不足以把整個 context 放進去。
當初的想法是以傳進來的文章作為一個 session
使用者可以點擊同一個 session 的內容
例如說，選完文章之後還可以回頭來選同一篇文的其他文章。

如果他按的按鈕太久遠（一個 session 之外），也要顯示一個訊息說這個按鈕過期了，如果有需要的話，請重新轉傳一份訊息進來。

### Bug: 覺得有用 / 沒用的分數最多只有 10
> MrOrz

issue: https://github.com/cofacts/rumors-api/issues/77

### 顯示覺得 article reply 沒用的理由；使用者在網站上按 Ｘ 時也詢問理由
> MrOrz

issue: https://github.com/cofacts/rumors-site/issues/97


## 我愛家我解惑 - 大松提案

https://docs.google.com/presentation/d/1aHBl7JxmDjmhclN-ewGYklKcZi0thuXKg8XiF1kKNZI/edit

### 徵人做

- 找爭點
- 誠懇回應

### 蒐集 / 產製 / 散佈

- 此 project 僅蒐集、產製
- 做成容易散佈形式（資料庫內文章、網站文章）

## 對外

### bloomberg

先回共筆信
by Billion
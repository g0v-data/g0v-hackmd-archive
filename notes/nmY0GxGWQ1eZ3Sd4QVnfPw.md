---
tags: cofacts, meeting note
---

20190501 會議記錄
=====
orz.bil.文武
> 上次開會紀錄：https://g0v.hackmd.io/s/rkEn4TtqE
> 

## 闢謠送貼圖

FB group


## 新功能貼文

### Downvote 理由
- 顯示 Downvote 理由：https://github.com/cofacts/rumors-site/pull/159 by leanne
- 詢問 Downvote 理由：https://github.com/cofacts/rumors-site/pull/158 by jihchi

預約 5/2 20:00 發文：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7c275acd5d8fc1f86c33f922cdc1c501)


## 理由檢討

from: https://g0v.hackmd.io/s/rkEn4TtqE#%E7%90%86%E7%94%B1%E6%AA%A2%E8%A8%8E

Ticket:
- [隱藏只送一次且沒填寫理由的訊息](https://github.com/cofacts/rumors-api/issues/127)
- [No-reason mode](https://github.com/cofacts/rumors-line-bot/issues/132)

桓：
現在沒有針對 user 的 database

mrorz
做推播的時候就會有

- - -

ttcat
我們之前設計理由是為了怕大家亂送
但目前遇到的問題是長輩沒辦法填

是不是可能填的地方是用按的，變成理由的一部分

mrorz
但如果開放給所有人，那有能力填寫理由的人也會按按鈕

ttcat
覺得改完之後，有受益的人還是實際有碰到的人，感覺影響比較小
如果想要解決理由很難寫的關係應該有其他機制

mrorz
這會跟隱藏只送一次的一起做
就算沒填理由還是能送進資料庫，只是外觀上看起來跟沒送一樣
如果真的有第二個人也送進來，就會一起浮上來

ttcat
這會使原本能填理由的人不填理由嗎

mrorz
UI 設計是還是希望他寫 40 字
只是不會擋 15 字以下




## 能推播的新功能

from: https://g0v.hackmd.io/s/rkEn4TtqE#%E8%83%BD%E6%8E%A8%E6%92%AD%E7%9A%84%E6%96%B0%E5%8A%9F%E8%83%BD

Ticket: https://github.com/cofacts/rumors-line-bot/issues/133

桓：
那會不會有人說他在記錄個資之類的然後產生疑慮

bil:
應該還好，因為為了做推播而一定要做

mrorz
使用者自己跟 chatbot 對話，會期待 chatbot 記得自己的話
因為是對話情境所以應該自然就會期待說 chatbot 會「知道」

bil
有在網站與 hackfoldr 說不要傳不是謠言相關的東西
他一直都是查資料的角色，我把你要查的東西記錄下來，不會是紀錄隱私資料

ttcat
如果歡迎訊息有說的話會比較好

mrorz
具體來說我們只會紀錄 userid 與 article id
只有在使用者傳進來的訊息
1. 使用者選擇要送進公開資料庫，或者
2. 資料庫已經有相同的文章（user selected an article search result）

才會把 userid 與 article id 做配對

使用者如果亂傳個資進來，只要沒送出到公開資料庫，我們就不會紀錄在 relational database

桓
我本身不會懷疑
但過去有人說是政府在監控

mrorz
那應該是美玉姨的狀況，它不需要經過大家同意都可以搜集
而 cofacts 只紀錄有意識的轉傳

## Tech4Democracy case study (deadline: Early May)

https://docs.google.com/document/d/1hfKYFs0-lbAaCAdhrpkrFuSV5__YDjg7QjqM92Wk0dc/edit

## coscup 社群軌投稿 (deadline: 5/6)
https://blog.coscup.org/2019/04/2019-cfp-open.html#g0v

> 哈囉，g0v 今年也參加了COSCUP 的社群議程，今年 g0v 社群議程原則上包含下列主題—「開放政府」、「新媒體」、「公共服務」、「開放資料」、「社會參與」和「基礎建設」這幾個大方向。歡迎各位投稿分享你今年的專案吧！
> 

投 Introduction to Cofacts
reuse g0v summit 那份提案

## region 2 factor

把每一篇內文拿去 google + baidu
找 highly match 
蒐集 match 的網域，哪裡比較多
ex: 台灣高中生報名中國大學的新聞，有大量中國官媒引用
中國官方 or 大馬農場

> RightsCon 提案：China's Triumph on Taiwanese elections: perspective from a crowd-source fact-checking platform targeting disinformation on closed messaging apps

orz

可以做到的事情是：
如果given一個cofacts上面的文章和中國的網路裡流傳的訊息是相同的訊息
還有LINE上面流傳的訊息是不是也在別的地方流傳
不會知道是中國先開始才讓LINE傳，或是我們先傳又流傳到中國去
看當中的互相影響
中國挑我們的訊息去放大，或是我們的訊息從中國那邊影響

到底是從馬來西亞內容農場來得多還是中國來的訊息多
用api去查，找幾乎一樣的match
然後把那些來源記下來
就可以做出統計圖表和文章列表事
每一個cofacts文章可以對到多少search result
看是台灣的網域還是中國的網域還是其他地方的網域

去年rightscon有個台灣高中生家長拍了一張照片
中國中山大學前面排隊
那些是在中山拍的
可是不確定他們身分
有滿多家長是討論去這裡就讀的事情

實際狀況是google查詢後會看到中國內容農場和官媒在轉傳
不管是誰先發然後另一方跟進放大
他們都有相互關係
至少這是中國政府希望看到傳送的

ttcat
趕六月的話那做到這樣就 ok
我想做我們去查證的訊息，有附帶連結的話網域是哪裡
是哪些種類的結果比例分別是多少
但這會碰到 youtube 之類的話，那要爬頻道之類的
如果 Facebook 就是什麼粉絲團等等
平台要特別去分析

你做的這個可以是基礎，之後還可以比對其他東西

mrorz
感覺可以一起做，
因為都要爬

ttcat
內容農場會需要列表
真的做的話，可以做很大
例如說一開始去爬 google & baidu 搜尋結果
然後搜尋結果次數
有去轉貼相同的網站
會變成 domain 列表，自己一直長大
之後要做其他東西也可以用


之前寫計畫的時候，就在想像訊息怎麼查「中國成分」
一個是看搜尋
有好幾個層次可以做，例如 domain name 或特定內容農場
或者是哪些 term 是中國用法等等

如果是 6 月要做的話，先做可以做得到的就好了。




---
title: "企畫筆記：Slim-Rails v.s. AngularFire 技術選擇"
tags: 零時的學習不能等,hackpad
---

# 企畫筆記：Slim-Rails v.s. AngularFire 技術選擇

> [點此觀看原始內容](https://g0v.hackpad.tw/tVQC70sZ9io)

[3/14 irc 討論](http://logbot.g0v.tw/channel/g0v.tw/2014-03-14)、mo3dict 實體討論 by au、ETBlue
> 原來 ET 晚餐時又在狂點技能樹 ^^b
> [name=venev]

> 是腦袋卡關，在求神問卜 XD
> [name=ET B]


### 前言


對於廣大的為了實踐自己的 idea 而無所不用其極的跨領域企畫人來說，一個簡單好上手的前後端通吃的架站技術，是不可或缺的 prototyping 工具。市面上以簡單聞名的解決方案包括 angular.js + firebase 以及 slim/haml + rails，到底該如何選擇呢？

### 結語


簡單的說，angular.js + firebase ( +angularfire ) 勝。

### 劇情


#### 時間：3/14 ，狀況：零時廣場 mockup 出爐，使用工具：Jade + Sass + fire.app

[http://g0v.github.io/g0v.today/osdc/public/](http://g0v.github.io/g0v.today/osdc/public/)

ETB: 理論上好像該用 angular 做 spa 不過我 browser 預覽速度越來越慢，暫時先拆成獨立 html 來寫好惹

ETB: 這放在區網的話……到時候不就連 firebase 都不能用
au: 所以才適合 Rails (不然就要加速 pgrest angular binding) 但即使是這樣，rails 在不需要同步即時更新的頁面還是比較快(開發和載入皆然)

ETB: 所以有大量內容的話會是 rails 較快嗎？跟即時聊天那種高互動的相比？
au: 開發上 rails 有很多該做的幫忙做好了。在瀏覽上，伺服器全靜態或可緩存的資源一次送出，比用 JS 二次載入快 (前後兩件事沒有必然的關係) 後者舉例來說，其實伺服器也可以自己去跟 firebase 拿資料畫好之後，再送給瀏覽器。但是也有 server 跑一次 angular js (prerender) 給 html，然後到 client 端再動態更新的做法

ETB: 所以在瀏覽上，使用 angular js 的話，在有許多靜態內容的網站上，帶給使用者的感覺會比使用 rails 或 python 之類的後端程式預先出好 html 的作法來的慢

ETB: 噢噢…比方說 server 每隔一小時就先算好一個快取版的 html？等真的有人連上再檢查一次有沒有新的資料
au: 是的，如 [https://github.com/dai-shi/connect-prerenderer](https://github.com/dai-shi/connect-prerenderer) 即是一例

ETB: 所以這樣使用者初次收到的會是 prerender 的 html，所以在 seo 跟社交網站分享上其實就跟一般的靜態網頁無異
au: 是的 Javascript 裡可以用 if ($('body').data('prerendered')) { ... } 來判斷是在哪個脈絡下執行  大致如此

ETB: 而 prerender.io 之類的服務，只是替我做掉這份工作，順便把靜態 html 放上 cdn 不管是使用 rails 或 python 或 whatever 撰寫後端，前端都可以有 angular + prerender 或傳統 (?) 生 html 兩種作法
au: 沒錯。只是 node/connect/prerenderer/jsdom 這個架構才演化了兩年多，而 Rails 已經快十年了 但本質上並無區別

ETB: 所以撰寫前端的人就是………挑一種自己覺得開心的作法來寫，反正結果都一樣？ XD
au: 當然，本來就是為了開心啊 XD [http://www.slideshare.net/autang/open-source-enlightenment/36](http://www.slideshare.net/autang/open-source-enlightenment/36) , 37, 38

ETB: 那麼市長給問嗎分享網址時不會抓到網頁標題，只是因為沒有 prerender 的緣故，不是使用 angular 的必然結果
au: exactly

#### 時間：3/15，狀況：剛學完 Rails Girls 把零時廣場轉移到 Slim-Rails


#### 時間：3/18，狀況：立院廣場松爆發


#### 時間：3/29 ，狀況：Rails 4 Zombies 遇到 Ruby object 的 public/private method、symbol 語法，卡關


（經過十天的立院廣場松，終於學會保持平常心，回頭繼續開發長期專案）

（Rails 4 Zombies Level 4 寫作業中）不行，學 Rails 沒有先搞懂 Ruby 的話根本不知道自己這一行在寫什麼。（打開 code school 中做到一半的 try ruby 課程）（突然覺得離目標越來越遠，很想哭 QQ）

\-\-\- 這段討論想等 live 影片網址出來再直接聽打 ---





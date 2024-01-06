---
tags: cofacts, meeting note
---

20200422 會議紀錄
=====
在雲上面
> 線上開會： ~~https://tico.chat/powercall?room=cofactshack&type=timeFirst~~ https://meet.jit.si/CofactsHack
> 上次開會紀錄：https://g0v.hackmd.io/@mrorz/r1-MslE_U

## 小聚

- 影片播放時不要做其他事情，不然會 lagggg
- 需要更多宣傳？

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_77541656a4c4dc1b82a9dfd2ce05b8e4.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2bae24ce8ef416fe5d7c5e9b090d8bbe.png)

bil:
人數挺好的，不需要宣傳

依照疫情來看，5月大松大概也會線上

下個月又會在 workis 辦小聚了

orz
但是這樣會有我們的直播、大會的 youtube 跟專案 jitsi

bil
只要一個直播
facebook 或大會
而且會有 ronny 新系統

orz
不知道這個系統是不是支援 embed 兩個直播視窗

conference call 會太吵（每個人的聲音都一樣大聲）

直播又怕吵

:::info
等大松
:::

## 開發

### Deploying to staging

- [x] new navbar ui (PR [#241](https://github.com/cofacts/rumors-site/pull/241))
- [x] category related (PR [#245](https://github.com/cofacts/rumors-site/pull/245), [#234](https://github.com/cofacts/rumors-site/pull/234), [#235](https://github.com/cofacts/rumors-site/pull/235))

### Deploy to production

- [x] Arithmetic query filter PR [#161](https://github.com/cofacts/rumors-api/pull/161), [#163](https://github.com/cofacts/rumors-api/pull/163)
- [x] `hasArticleReplyWithMorePositiveFeedback` PR [#162](https://github.com/cofacts/rumors-api/pull/162)
- [x] Migrate category

### 發感謝文

GitHub activities
https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/WSQFB


感謝 stimim (還沒空發 QQQQQ)
製圖：https://www.figma.com/file/zwThV99c4dHkFdIPg3Ii0T/Cofacts-%E7%99%BC%E6%96%87%E7%94%A8%E5%9C%96?node-id=0%3A1

>>>>感謝感謝stimim~~~❤️❤️❤️


上次三月的g0v黑客松，感謝來自四面八方的貢獻者一起讓台灣的公民科技社群更茁壯。
感謝 stimim 也貢獻了一個很棒的新功能喔！！！（非常感謝感謝😊）

 LINE上的好朋友們，如果遇到可疑的訊息，都歡迎轉傳給Cofacts 真的假的，同時我們也邀請這些好朋友在 LINE 輸入框主動留下覺得可疑的疑點，或是已經知道的查證資料，一起加入協作系統，幫助我們數以百計的編輯！！

現在這個功能可以在網站上面手動加入囉！！！如果你在瀏覽Cofacts 網站時，發現了會讓你覺得：「我也想知道、好好奇啊、我有看過這則訊息、我查到一半，希望有人接力查下去！」的訊息，快快按下「增加回報理由」，提供網站上的編輯更多情報。你的一小步，會幫助不實資訊的澄清好大一步唷！

再次感謝 stimim 熱情與卓越的貢獻！
## g0v summit

投稿？hold 軌？

:::info
如果有需要幫忙的話很樂意幫忙hold軌。即使沒有，Cofacts 會投稿，也很樂意分享。但不會特別積極主張必須開一個軌。工作坊、演講、查核課程，即使不在summit舉行也可以辦，如果summit是個已經很熱門的場域了，Cofacts不會去競爭或主張開議程軌。

:::

## LINE notify

文武
有 push API 可以用的話先用
LINE notify 如果不能用再接

他可以 oauth
直接點 LIFF 經過他，就能拿到 token
不用 IFTTT

Orz
作為 open source project
實作 LINE notify 可以給其他沒有 push API 的人（如 opendream）直接用



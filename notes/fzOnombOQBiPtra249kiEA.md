# 斷網可用分散式社交軟體 Patchwork

{%vimeo 236358264 %}

**TL;DR: Patchwork 是個斷網可用，一對一訊息可加密的臉書 / Twitter 替代品。**

* 哪裡抓？請到 [ssbc/patchwork](https://github.com/ssbc/patchwork/releases)
* 手機版？請到 [Manyverse](https://www.manyver.se/)
* 怎麼運作的？請讀 [Scuttlebutt Protocol Guide](https://ssbc.github.io/scuttlebutt-protocol-guide/)
* 更多介紹？請讀 [官方 GitBook](https://www.scuttlebutt.nz/)

👉 如果只是想先建立訊息廣播站，請看[在無手機訊號的環境下，如何建立資訊中心點](https://hackmd.io/0fHXztTfS6277u1X3jVeXA)
👉 本文件舊版在 [hackmd.io/QM3RRIkFR_6x0jrw6TxPbg](https://hackmd.io/QM3RRIkFR_6x0jrw6TxPbg?view)

## 更多

### 用起來長怎樣？

![](https://i.imgur.com/7m67Plm.png)

一開始誰都沒追蹤時，會很冷清...。

### 為什麼斷網仍可用？

ssbc protocol 上每個節點都是平等的，在節點彼此可以接觸到對方時會同步訊息。平常用它寫的文章會經由網際網路和朋友同步，要是沒有網路連線， Patchwork 會試著在區域網路上尋找你的朋友，要是找到了，一樣會同步彼此的訊息。

以現在的設計，訊息會同步兩層（你的朋友、和朋友的朋友），於是你可以在 A 地同步一些朋友的訊息，再到 B 地將新消息傳給其他朋友。

### 有什麼隱憂？

Patchwork 上的 Aadil Ayub 好奇，既然訊息是分散存放的，有沒有可能反而對異議人士不利？於是有了這串討論： `%voYwxKeeYd3GmfeFavbrszoJyseQwmeu+p6jMPdthPo=.sha256`

（將上面以 `%` 開頭的連結，貼到 Patchwork 的搜尋框就能看到該討論）

:::danger
由於 private group 功能還在開發， Patchwork 並不適合用來廣播私密訊息，可以將它想像成 Twitter 或 facebook 的替代品，但不是 Telegram 或 LINE 的替代品。
:::

### 誰做的？

Scuttlebutt protocol 是由 Dominic Tarr 設計開發的。他住在紐西蘭的船上。他常常沒有網路可以用，於是希望能有個斷線也能用的社群網路。

👉 可以看看 Manyverse 作者 staltz 寫的 [An Off-Grid Social Network](https://staltz.com/an-off-grid-social-network.html) 。
👉 還有 [@zelf](https://twitter.com/thezelf) 在 [35C3](https://events.ccc.de/congress/2018/wiki/index.php/Main_Page) 的演講 [Scuttlebutt](https://www.youtube.com/watch?v=JSWWkzsHhjk)

### 可以追蹤誰？

* Dominic Tarr: `@EMovhfIrFk4NihAKnRNhrfRaqIhBv1Wj8pTxJNgvCCY=.ed25519`
* 手機版作者 staltz: `@QlCTpvY7p9ty2yOFrv1WU1AE88aoQc4Y7wYal7PFc+w=.ed25519`
* 活躍開發者 mixmix: `@ye+QM09iPcDJD6YvQYjoQc7sLF/IFhmNbEqgdzQo3lQ=.ed25519`

> 歡迎補充 XD

### 什麼是 Pub

Pub server 是網際網路上的節點，經過邀請連結追蹤它的話，它會自動追蹤你，於是你就會和也追蹤這個 pub server 的人交換訊息。可以說是分散式網路中的一個個小中心。

Pub 有公開的也有邀請制、私人的。

👉 可以到 [pub server 列表](https://github.com/ssbc/ssb-server/wiki/pub-servers)找找有哪些 public pub server 。

### 怎麼架 Pub

👉 可以靠 [easy-ssb-pub](https://github.com/staltz/easy-ssb-pub) 或 [ssb-pub](https://github.com/ahdinosaur/ssb-pub) 來架自己的 pub server ，熟悉 Unix 系統的話，能在一小時內架起來。

## 討論

> 如果只是想要先建立「中心化」的訊息廣播站，可以用 Notebook 開啟 wifi-access point，並架一個簡單的 http-server，就可以讓wifi訊號範圍內的人，用手機得到相同的訊息，詳細步驟可以參考[在無手機訊號的環境下，如何建立資訊中心點](https://hackmd.io/0fHXztTfS6277u1X3jVeXA) [name=yinghsun]
> 更多訊息歡迎補充到下面，讓最上面一看就可以知道到哪裡找 Patchwork 👍 [name=caasi]
> 這個 hackmd url 已經有傳出去了，可能要兼做 index page... [name=yingshun]
> 好喔。
> [name=caasi]

###### tags: `公民科技` `通訊工具` `SNS`
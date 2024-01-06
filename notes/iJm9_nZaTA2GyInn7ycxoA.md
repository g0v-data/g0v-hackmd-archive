---
tags: cofacts
---
# 列表



| Nav menu | Page title | Links to |
| -------- | -------- | -------- |
| `Messages` `可疑訊息`   | `Dubious Messages` `可疑訊息` | articleList  |
| `Replies` `最新查核` | `Latest Replies` `最新查核` | Need Review article with replies |
| `For you` `等你來答` | `Hoax for you` `等你來答` | Popular messages + Replies that needs review |

:::info
Dev note:

Nav menu 的 `t`，請使用 `c('menu').t`，以利與其他地方使用的名詞分開。

Ref: [ttag context](https://ttag.js.org/docs/context.html)
:::

_
搜尋框
_
討論區 / Forum
~~關於 / About~~
_
我 / Me
- 我的主頁
- 我的關注 / Follow ( after login ) => followed articleList
- 瀏覽紀錄
- __
- 如何闢謠
- 關於 Cofact / About
- __
- 登出



## Wireframe
https://www.figma.com/file/YikWPPauMnukDH0U2Nq4YS/Components?node-id=0%3A1


## 等你來答 Query

Filter
```
article.replyRequestCount >= N (default N = 2)
and
沒有任何 normal articleReply 符合「正feedback>負feedback && status」
and
自己沒有送過任何 normal articleReply
```

 (badge 數字 query，不一定等於列表內的元件數量)
 
1. `replyRequestCount`：可以先寫死 2，也可以動態調配（太多篇就 runtime 改 3、太少篇就動態改 1）

## 「我的關注」

:::info
Discussion: https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1583910132.097200
:::

定義：自己有送過 reply request 的 article list
需要做一個 `ListReplyRequest` API，但 query 就只能針對 ReplyRequest 的欄位，無法 search / filter by articles 的欄位
---
title: "vTaiwan.tw 後端架構"
tags: vTaiwan.tw, hackpad
---

# vTaiwan.tw 後端架構

> [點此觀看原始內容](https://g0v.hackpad.tw/RxmNaJogwnc)

上層：[vTaiwan.tw 行政院法規線上諮詢系統](https://g0v.hackpad.com/oWRxOF4ilfx)
> 2015/1/13 au first draft, to be reviewed by iii team; API index to be reviewed with vtw.link team
> [name=Audrey T]


前端呈現在 [https://github.com/g0v/vtaiwan.tw/](https://github.com/g0v/vtaiwan.tw/)
後端由兩部份組成，也就是 GitBook 和 Discourse。

### GitBook 方面


[http://crowdfunding.vtaiwan.tw/](http://crowdfunding.vtaiwan.tw/) 的目錄就是該網址。
小字典是 [http://crowdfunding.vtaiwan.tw/GLOSSARY.html](http://crowdfunding.vtaiwan.tw/GLOSSARY.html)
字典內容由 [google spreadsheet](https://github.com/g0v/crowdfunding-gitbook/blob/master/package.json#L14) 取得

各頁的內容全部在 [http://crowdfunding.vtaiwan.tw/content.json](http://crowdfunding.vtaiwan.tw/content.json)
所有的 Markdown 在 [https://github.com/g0v/crowdfunding-gitbook](https://github.com/g0v/crowdfunding-gitbook)

技術文件見 [http://help.gitbook.io/book/format.html](http://help.gitbook.io/book/format.html)

### Discourse 方面


可以到討論區任一頁，如 [https://talk.vtaiwan.tw/t/topic/21](https://talk.vtaiwan.tw/t/topic/21)
後面加 .json 就好了 \\o/ [https://talk.vtaiwan.tw/t/topic/21.json](https://talk.vtaiwan.tw/t/topic/21.json)

Ruby API 及技術說明: [https://meta.discourse.org/t/using-discourse-api/17587](https://meta.discourse.org/t/using-discourse-api/17587)
Node.js API: [https://github.com/dhyasama/discourse-api](https://github.com/dhyasama/discourse-api)
Java API: [https://github.com/wareninja/discourse-api-client](https://github.com/wareninja/discourse-api-client)

### 主索引


請用這個 JSON 結構試作：

```
[
      { "title\_cht" : "群眾募資", "title\_eng" : "crowdfunding", "category_num" : 6},
      { "title\_cht" : "閉鎖型公司", "title\_eng" : "closelyheld", "category_num" : 5}
]

```
其中 title\_eng 對應到 GitBook domain，category\_num 對應到 Discourse domain。
對應邏輯如下：

```
title_eng = crowdfunding
HTML: https://crowdfunding.vtaiwan.tw
JSON: https://crowdfunding.vtaiwan.tw/content.json

category_num = 6
HTML: https://talk.vtaiwan.tw/6/5-category
JSON: https://talk.vtaiwan.tw/6/5-category.json


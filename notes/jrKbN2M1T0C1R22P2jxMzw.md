# bbs2mastodon

plan prompt:
```
我想要把 bbs 和 mastodon 串連起來，讓 1986 年的多中心化交換系統（nntp），和 2013 年的多中心化交換系統（fediverse）可以串連起來，以實現在 bbs 可以貼文被 mastodon 看到，mastodon 貼文也可以被 bbs 看到，增加這兩個服務的影響力。

我熟悉的程式語言是 PHP 和 JS ，請幫我盡量用 PHP 開發，我預計的架構如下，請你幫我確認這樣架構是否可行或者是否需要調整

需要架設一個現成開源的 nntp server （我擁有有固定對外 IP 的 ubuntu 可以做到這件事）
建立一個 content db ，來儲存所有的內容（可能可以採用 sqlite 簡單一點？）
建立一個 nntp <-> content db 的 bridge (用 PHP 撰寫，主要任務是追蹤 nntp 是否有新內容，並把他儲存進 content db ，或者當 content db 有新內容時，會把他張貼到 nntp 去）
建立一個 content db 的 activitypub endpoint （實作與 mastodon 的相容機制，這樣就可以讓資料跟 mastodon 串起來）
建立一個 pttbbs ，並且連線至 nntp server ，這樣就把整個流程串起來了
請你幫我規劃研究一下，有任何問題再詢問我

```

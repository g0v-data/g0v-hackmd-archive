---
title: "tw-url-normalizer.js 台灣網址整理工具"
tags: hackpad
---

# tw-url-normalizer.js 台灣網址整理工具

> [點此觀看原始內容](https://g0v.hackpad.tw/EmjeHiKAv12)


為了 SEO ，許多以文字為主的網站，會將文章標題放入網址中，但是因為文章標題可能會改變造成網址跟著改變，而讓許多不一樣的文章所指的其實是同一篇文章，這在一些工具像是新聞小幫手就會造成使用者需要重覆回報，如果能有個 library 可以把這些網址正規化，相信對很多應用會有幫助的。

需要工作：
    由於網址是由各家網站自己規定，因此難以有統一個方式可以處理所有網站，需要一個一個慢慢加入 regular expression 來處理，所以會先開一個 repository ，然後讓大家可以不斷 pull request 進來新的網址格式。

需求規格：
            url_normalizer(url)
```javascript
return {
  'query_url': '查詢的網址',
  'normalized_url': '簡化過後可以連的網址',
  'normalized_id': '唯一的 ID',
}
```
Ex:
url_normalizer('[http://www.appledaily.com.tw/realtimenews/article/finance/20131225/314703/](http://www.appledaily.com.tw/realtimenews/article/finance/20131225/314703/)【台股開盤】開高上漲11點');
```javascript
return {
  'origin_url': 'http://www.appledaily.com.tw/realtimenews/article/finance/20131225/314703/【台股開盤】開高上漲11點',
  'normalized_url': 'http://www.appledaily.com.tw/realtimenews/article/finance/20131225/314703',
  'normalized_id': 'appledaily.com.tw/314703'
}



---
title: "urlshot 網頁轉圖檔"
tags: hackpad
---

# urlshot 網頁轉圖檔

> [點此觀看原始內容](https://g0v.hackpad.tw/uMqcJrauA7C)

## Name

urlshot - 把網頁轉成圖檔的服務

## Synopsis

使用範例：
- [http://u](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[r](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[l](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[s](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[h](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[o](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[t](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[.g](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[u](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[g](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[o](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[d](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[.o](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[r](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[g](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[/](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[?](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[u](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[r](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[l](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[=](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)[http://www.yahoo.co.jp/](http://urlshot.gugod.org/?url=http://www.yahoo.co.jp/)

## Code

- [https://github.com/g0v/urlshot](https://github.com/g0v/urlshot)

## License

- CC0
## 使用注意事項

- 目前以單一行程執行，同時來兩個 request 時會依次完成
- 目前 cache key 為 url 本身，需要再實做 invalidation 機制
- 圖檔為 png
- 圖檔為網頁全版畫面，因此大小不一。使用的人自行再裁切。
- 目前可用的磁碟空間約為 10GB，視需要再轉存其他空間 (Dropbox / S3 之類)


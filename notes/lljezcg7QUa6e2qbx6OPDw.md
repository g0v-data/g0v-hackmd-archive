# Ronny 被 OpenAI 機器人爬資料紀錄

近幾個月，OpenAI 的機器人開始狂爬各種資料，其中造成 Ronny 2025年2月 AWS 費用因此爆增 60USD ，這份共筆留下各種相關紀錄

## 流量圖
Ronny 帳單中關於 Cloudfront (AWS 的 CDN 費用)，每個月美金的費用，其中 2025年2月比前幾個月爆增了 60USD 左右(SUM of UnblendedCost) 
![](https://g0v.hackmd.io/_uploads/B14rZkBTJl.png)

而以流量和存取次數，可以參考下圖，2025年2月的流量比過去往月爆增了 160GB 左右，Request 數則爆增了 6000萬次左右。
![](https://g0v.hackmd.io/_uploads/BkscWyrpJx.png)

據追查其中來自 portal-api.g0v.ronny.tw 的流量爆增，而主要來源是來自機器人抓取。
![](https://g0v.hackmd.io/_uploads/ryIi2RV61x.png)

## 什麼是 portal.g0v 專案
什麼是 portal.g0v.ronny.tw，這是 Ronny 在 2013 年做的專案，是爬取台灣進出口統計資料，有各種商品（約30000種），在每個月(2003年1月~2019年11月，共203個月)，跟每個不同國家（約227個國家）的進出口統計，合計約 8000 萬筆資料。如下圖可以看到某個商品種類每個月各國進出口變化
![](https://g0v.hackmd.io/_uploads/rJlDEUySa1l.png)

因為資料量有點大，為了節省資料庫負擔，因此當時有採用 Amazon CloudFront 來快取讀取過的內容，而 Amazon 會依照流量收費

## 被　ChatGPT 抓了多少量
- 
# Ronny 被 OpenAI 機器人爬資料紀錄

近幾個月，OpenAI 的機器人開始狂爬各種資料，其中造成 Ronny 2025年2月 AWS 費用因此爆增 60USD ，這份共筆留下各種相關紀錄

## 什麼是 OpenAI 機器人


## 流量圖
Ronny 帳單中關於 Cloudfront (AWS 的 CDN 費用)，每個月美金的費用，其中 2025年2月比前幾個月爆增了 60USD 左右(SUM of UnblendedCost) 
![](https://g0v.hackmd.io/_uploads/B14rZkBTJl.png)

而以流量和存取次數，可以參考下圖，2025年2月的流量比過去往月爆增了 160GB 左右，Request 數則爆增了 6000萬次左右。
![](https://g0v.hackmd.io/_uploads/BkscWyrpJx.png)

據追查其中來自 portal-api.g0v.ronny.tw 的流量爆增，
![](https://g0v.hackmd.io/_uploads/ryIi2RV61x.png)

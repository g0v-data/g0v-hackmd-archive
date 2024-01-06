---
tags: 民防
---
# 20230826 戰時網路  @ 開源普渡黑客松

> [name=Ronny Wang] 2023-10-15 黑客松：
## 戰時網路模擬器
https://github.com/g0v/wardns
純 Python ，可以自架在自己的本機上面
即時檢查是否有用到國外服務

謝謝 vax-r 幫忙 PR 修正
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_24794c8162f2254980e74fb48019f71f.png)


### 目前不能用的網站
- https://www.gov.tw/
- https://moda.gov.tw/
- 新聞類
    - ltn, chinatimes 都不能連
    - udn 可以連，但是圖都過 cdn ，看不到
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5867782d3bc9e31399b1102c4dcf586b.png)
    - cna 都正常，只有 google 廣告不見了

待檢查
- 防災宣導網站 https://easy2do.ncdr.nat.gov.tw/together/
- g0v 基礎建設相關？[清單](https://docs.google.com/spreadsheets/d/1C9-g1pvkfqBJbfkjPB0gvfBbBxVlWYJj6tTVwaI5_x8/edit)

## 盤點哪些服務在戰時是重要的，要有替代方案
-  防空避難所位置 https://adr.npa.gov.tw/indexgo
    -  可以用 maps.nlsc.gov.tw 當地圖圖資
    -  已將資料備份至 [g0v/ard.npa.gov.tw](https://github.com/g0v/adr.npa.gov.tw/tree/main)
    -  地圖圖資: [mbtiles下載](https://maps.nlsc.gov.tw/download/TaiwanEMap.mbtiles
) (來源： [圖土測繪圖資服務雲](https://maps.nlsc.gov.tw/MbIndex_qryPage.action?fun=8#))
    - Github 備份：https://github.com/ronnywang/taiwan.mbtiles
    - Demo: https://jsfiddle.net/ronnywang/8up1t2sj/4/
-  新聞網站？
-  通訊軟體？
-  在學術網路架設 mastodon 當作戰時替代？
-  ptt？(有 .tw 結尾的 domain 嗎？)
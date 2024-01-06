---
title: "新竹市事故血漬典"
tags: hackpad
---

# 新竹市事故血漬典

> [點此觀看原始內容](https://g0v.hackpad.tw/BiGOZBfzPNS)

## 專案構想說明


新竹上下班的時間，機車族其實每次都滿膽戰心驚。這個專案想知道哪些路口是危險的，透過過往發生事故的地址做參考，並以熱度圖的形式視覺化這些資料。

另外補充先前其他已有
[http://muyueh.com/30/xinzhu_traffic/](http://muyueh.com/30/xinzhu_traffic/)  (新竹)
[http://54.169.144.72/TaipeiAccident/](http://54.169.144.72/TaipeiAccident/) (台北)
[http://taipei-traffic-accident.pancakeapps.com/Taipei.html](http://taipei-traffic-accident.pancakeapps.com/Taipei.html)（台北，via [g0v 後勤中心](https://www.facebook.com/groups/g0v.general/permalink/1264089883667415/)）

## 現有資料


1.  警政署：歷史交通事故資訊（僅有A1 & A2事故，且缺乏gps經緯度資訊）
    [https://www.npa.gov.tw/NPAGip/wSite/lp?ctNode=12854&CtUnit=2633&BaseDSD=7&mp=1](https://www.npa.gov.tw/NPAGip/wSite/lp?ctNode=12854&CtUnit=2633&BaseDSD=7&mp=1)
2.  善心朋友提供已經處理過的資訊 (但有些GPS info與縣市地區位置不一致)
    [https://drive.google.com/drive/folders/0B2XpHtmLOlpmZTg1aDFydVZ1b3c?usp=sharing](https://drive.google.com/drive/folders/0B2XpHtmLOlpmZTg1aDFydVZ1b3c?usp=sharing)
3.  政府開放資料平台 / [http://data.gov.tw/node/12197](http://data.gov.tw/node/12197)
4.  線上 batch geocoder [https://geocoder.ccjeng.com](https://geocoder.ccjeng.com)
5.  Google Maps Geocoding 使用限制 (2,500 free requests per day and 50 requests per second) [https://developers.google.com/maps/documentation/geocoding/usage-limits?hl=zh-tw](https://developers.google.com/maps/documentation/geocoding/usage-limits?hl=zh-tw)

## 現有進度


將現有資料\[2\] 的資訊透過簡單的python parser [https://github.com/ChingSheng/traffic\_accident\_heatmap_parser](https://github.com/ChingSheng/traffic_accident_heatmap_parser)
簡化csv檔，再透過google 的fusion table 工具製作熱點圖
[https://fusiontables.google.com/data?docid=1sQMxQosoft1Ll0zhN8nGWSqGsrFVapReWwJuxtfr#map:id=3](https://fusiontables.google.com/data?docid=1sQMxQosoft1Ll0zhN8nGWSqGsrFVapReWwJuxtfr#map:id=3)

## \[坑\] 後續計劃


1.  Google fusion table對地理資料的資訊點僅能支援1000點，未來想透過前後端的語言實際製作網頁。
2.  此外，針對政府開放的資料\[1\], \[3\]由於未提供經度與緯度的資訊，僅提供未正規化的地址資訊，想強化parser將這些地址資訊轉化為經緯度的資料



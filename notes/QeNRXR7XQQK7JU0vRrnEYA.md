---
title: "g0v 零時空汙觀測專案"
tags: 地圖化,環境資料自由整合,hackpad
---

# g0v 零時空汙觀測專案


整合各方空汙監測站的觀測資料與各種汙染源的排放資料以地圖視覺化呈現
清楚明瞭的即時空汙動態追蹤，以此達到排汙監督的社會效益

⚠️2024/11/23更新：airmap.g0v.tw網站已停止運作，將申請釋放網域或轉靜態頁面

### [專案完整hackfoldr](http://beta.hackfoldr.org/g0vairmap)


## 專案簡介


### 緣由與欲解決之問題

最初的專案方向是在開發小型開源的arduino空氣品質監測器並組織一個非官方的共同觀測網
一路開發下來發現其實很多各路高手都在做類似的專案
但專案之間的資料並不互通且零散
各平台有各的優缺點，要著手去統一開發平台並不實際
所以決定把目標提高一個層次去整合各種觀測資源讓各空汙監測開發社群貢獻的效益最大化

### 專案最高原則

整合各方空汙監測站的觀測資料與各種汙染源的排放資料以地圖視覺化呈現
清楚明瞭的即時空汙動態追蹤，以此達到排汙監督的社會效益
在最後並可彈性化統一輸出方便後續應用的資料格式(json, tabular data)

### 授權方式

零時空汙觀測網站實作專案近日將以MIT授權方式於github發佈

### 欲整合之目標

- 即時觀測資料 (包括官方與非官方測站的觀測資訊)
- 即時排汙資料 (包括工廠排汙, 火電廠排汙, 交通排汙等資訊)
- 即時氣象資料 (包括風力, 風速, 逆溫層效應)

### 資料呈現方式目標

- 以地圖為主軸的視覺化 (包括站點圖標,  heatmap渲染, 風力線條動畫)
- 時間軸

## 專案工作子分區

- [**網站開發共筆**](https://g0v.hackmd.io/p7-8t6kCQvWy-49C6zMgBg)
- [**感測器開發共筆**](https://g0v.hackmd.io/4UkEbzLgTUu5Oh_Rypol5g)
- [**自造測站推廣共筆**](https://g0v.hackmd.io/Wba8eDUlSHiyWkgVqn9L-w)

## 專案目前狀態
\[20191006\] 增加環保署的小型空品感測站
\[20181229\] 網址遷移至g0v.tw- [https://v5.airmap.g0v.tw/#/map](https://v5.airmap.g0v.tw/#/map)
\[20181103\] 感謝開放文化基金會(OCF)熱心支援，提供Google地圖流量折抵給本專案使用
\[過期\] g0v零時空汙觀測網站新版- [http://airmap.g0v.asper.tw](http://airmap.g0v.asper.tw)
\[過期\] g0v零時空汙觀測網站實作測試已上線\- [http://g0vAirMap.3203.info](http://g0vAirMap.3203.info)

網站相關開發細節請見子分區: [網站開發共筆](https://g0v.hackmd.io/p7-8t6kCQvWy-49C6zMgBg)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_85eeece0cc9d2fcac43dd4007658f7a8)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_04a23cdb46e3d6b37c1e5f1eaccb9cee)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bbda5411e344183b055ca6543c94839e)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1da8388d51f0ec284291078a1d479a48)


### 目前專案使用觀測站資料來源

- 組織性維護專案
    - ~環保署空氣品質即時污染指標~ [~(透過 g0v mirror~](http://g0v-data-mirror.gugod.org/epa/aqx.json)~) (政府資料開放授權) \-~ [~http://data.gov.tw/node/6074~](http://data.gov.tw/node/6074)
    - ~環保署空氣品質監測站基本資料含地理圖資 (政府資料開放授權) -~[~http://data.gov.tw/node/6075~](http://data.gov.tw/node/6075)
    - LASS-開源公益的環境感測器網路 (MIT授權) -[https://github.com/LinkItONEDevGroup/LASS](https://github.com/LinkItONEDevGroup/LASS)
        - [http](https://data.lass-net.org/data/last-all-lass.json)[s://data.lass-net.org/data](https://data.lass-net.org/data/last-all-lass.json)[/last-all-lass.json](https://data.lass-net.org/data/last-all-lass.json)
    - ProbeCube-物聯網感測方塊 (MIT授權) -[https://github.com/Lafudoci/ProbeCube](https://github.com/Lafudoci/ProbeCube)
    - 空氣盒子(透過Lass發佈, MIT授權) -[http](https://data.lass-net.org/data/last-all-airbox.json)[s://data.lass-net.org/data](https://data.lass-net.org/data/last-all-airbox.json)[/last-all-airbox.json](https://data.lass-net.org/data/last-all-airbox.json)
    - [~高雄市校園空氣品質監測~](https://xn--jvrt7ch0jeklv4emodg0v8xg1z8bnuudik/) ~(~[~http://nrl.iis.sinica.edu.tw/LASS/last-all-webduino.json~](http://nrl.iis.sinica.edu.tw/LASS/last-all-webduino.json)~)~
- 獨立開發者專案
    - Miaoski-(CC0, MIT授權)-[https://github.com/miaoski/pm25](https://github.com/miaoski/pm25)
- 將規劃整合的專案
    -

### 目前專案使用排汙資料來源

- 官方資料來源
    - 尚無整合
- 非官方資料來源
    - 尚未整合
- 將規劃整合的資料來源
    - [固定污染源管制地圖](https://g0v.hackpad.com/ndUPo4GAK5N) \- 另一項g0v專案，已有整合資料。

### 目前使用氣象輔助資料來源

- 官方資料來源
    - 尚無整合
- 非官方資料來源
    - 尚未整合
- 將規劃整合的資料來源
    - 中央氣象局
    - 風力視覺化-(MIT授權) [https://github.com/cambecc/earth](https://github.com/cambecc/earth)

## 實作細節


### 協作工具

- github repo：[https://github.com/immortalmice/Real-time-Air-Quality-Map](https://github.com/immortalmice/Real-time-Air-Quality-Map)
- hackfoldr 工作資料夾網址：[http://beta.hackfoldr.org/g0vairmap](http://beta.hackfoldr.org/g0vairmap)
- google drive 共用資料夾網址：
- g0v slack 頻道: pm25 [https://g0v-tw.slack.com/messages/pm25/details/](https://g0v-tw.slack.com/messages/pm25/details/)

### 參考資訊, 連結


先前相關g0v專案:
- [IoT DIY](https://g0v.hackpad.tw/B1xkj9fUqqH)
- [http://env.g0v.tw/air/](http://env.g0v.tw/air/)
-
交通流量相關：
- Google Map API, Traffic Layer：[https://developers.google.com/maps/documentation/javascript/examples/layer-traffic](https://developers.google.com/maps/documentation/javascript/examples/layer-traffic)
- 即時交通流量：交通部公路總局[https://www.thb.gov.tw/page?node=5f463394-b2e6-4b07-ba1a-5e5b16749bf1](https://www.thb.gov.tw/page?node=5f463394-b2e6-4b07-ba1a-5e5b16749bf1)
- 台北市交通控制中心：[http://tms.bote.taipei.gov.tw/ttc2/main.jsp](http://tms.bote.taipei.gov.tw/ttc2/main.jsp)
- 台北市交通工程管制處－即時流量：[http://www.bote.gov.taipei/np.asp?ctNode=20169&mp=117031](http://www.bote.gov.taipei/np.asp?ctNode=20169&mp=117031)
空汙資料相關：
- 台灣空氣[列管污染源](http://prtr.epa.gov.tw/)分佈（PRTR進階搜尋空氣污染）。[開放資料下載](http://data.gov.tw/node/6362)
- [http://kiang.github.io/chimney_map/#2016-03-05/N1505633](http://kiang.github.io/chimney_map/#2016-03-05/N1505633)



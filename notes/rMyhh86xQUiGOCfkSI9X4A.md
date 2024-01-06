---
title: "公有資產地圖"
tags: hackpad
---

# 公有資產地圖

> [點此觀看原始內容](https://g0v.hackpad.tw/z3C6ZqUlvMk)

1.  [3min 簡報](https://docs.google.com/presentation/d/1dxcrHnTRdkaejmtZb3l7Ws8LJ31d1sL1oHlAOpiuc08/edit#slide=id.gb8a7de0be_0_161)，歡迎提供更多方法
2.  以下畫土地與建築地圖的方法，也不限於公有資產哦

## 畫成地圖的方法

你想畫的是：

a.土地
- 基本資料：地號
- 畫圖策略：各種地號資料文件 → csv → 使用[地號轉地圖](https://g0v.hackpad.com/-Land-No.-Mapper-uhB6qAwYXe5)得到 GeoJson → 地圖製作(featureStyle, info-box, 事件處理...)
- 以公有土地為例：
    1.  資料來源：[各單位的公有地地號資料](http://hackfoldr.org/POPonFire/XpdD57S2RIZ)
    2.  操作案例：[臺北市轄區內國有可建築空地(註)之歸戶統計(含管理者)](http://data.g0v.tw/dataset/70) → [地號轉地圖](https://g0v.hackpad.com/-Land-No.-Mapper-uhB6qAwYXe5) →[天龍特公地製作過程介紹](http://dz1984.info/articles/Taipei_POP/) → [天龍特公地網站](http://taipei-pop.herokuapp.com/)

b.建築物
- 基本資料：建築平面位置與輪廓+高度
- 畫圖策略：GeoJson → 運用立體化工具
- 以公有建築物為例：
    1.  資料來源：
        1.  公部門釋出的模型中的公有建築，例如[3D台北城](http://gemvg.com/archives/676)
        2.  公部門的建照資料找出公有建築，例如[台北市市建築執照](http://tpebuilding.g0v.ronny.tw/index/columns)
        3.  將[蚊子館踏查文獻資料](http://wuchangkang.blogspot.tw/2014/01/app.html)繪製於 OSM → [使用 OverPass Turbo 精靈模式截取開放街圖資料](http://supaplex99.blogspot.tw/2015/08/how-to-use-overpass-turbo-wizard-mode-to-extract-openstreetmap-data.html)(tag?) → 地圖製作(featureStyle, info-box, 事件處理...)
    2.  操作案例：?


## 公有資產地圖，可能會結合的地圖功能

必要的混搭
- 基本想法：需要從議題切入
- ex 用地號去查該筆公有土地是否正在進行都市更新，參考[天龍特公地](http://taipei-pop.herokuapp.com/)
- ex 用地號去查是否為在地質敏感區，參考[地質敏感區查詢系統](http://gis.moeacgs.gov.tw/gwh/gsb97-1/sys_2014b/ex)
- ex 用位置去查土地使用分區或是相關環境法令，參考[環境法令整合查詢](https://g0v.hackpad.tw/LGQjB0Lozmc)
- ex 用土地管理機關名稱，去查到電話與信箱，方便使用者寫信詢問公有土地的各種問題，參考[政府通訊錄](https://g0v.hackpad.tw/g6v6MpyacFb)

必須處理歷史資料
- 基本想法：曾是公有資產的資料
- 初步歸納類型：
    - ex 已標售，參考「[台北市大安區信義聯勤俱樂部，由元利建設蓋兩棟31、35層豪宅](https://www.facebook.com/media/set/?set=a.698399803576871.1073741828.689216224495229&type=3)」
    - ex 空間資料已變動，例如地號整併與建築改建...

議題的共筆
- 基本想法：讓使用者為某個空間，補充新聞、小道消息、老樹、文化資產、拍照上傳現況...
- 構思參考：
    - 初步示意：[手機介面示意圖 by Lan](https://www.facebook.com/photo.php?fbid=903900116311040&set=o.1417173811903954&type=3&theater)
    - 實際參考：[Living Lots NYC was built by the 596 Acres Team](http://livinglotsnyc.org/lot/6000020001/)

鍵盤上的空間規劃工具
- 基本想法：自己的空間願景自己畫
- 案例參考：
    - [Crowd Planning System Prototype : 數位工具引入群眾導向的空間規畫與都市議題](https://g0v.hackpad.tw/dVyaLcWGdNA#:h=數位工具引入群眾導向的空間規畫與都市議題)
    - 開發類似 [field paper](http://fieldpapers.org/) 的工具。下載地圖->印出->手繪願景->掃描->上傳->轉成地理文件->願景圖輯平台
> 週末來試做看看
> [name=che l]

    - 實體活動蒐集願景意見、示意圖片，在彙整於平台上，參考：[FreespaceBerlin](http://www.freespaceberlin.org/)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9ef404c277c15e8682249433f0d2bcde)
    - 使用 [OSMumap](https://umap.openstreetmap.fr/zh-tw/) 工具，參考：[空間願景規劃的測試地圖](https://umap.openstreetmap.fr/zh-tw/map/map_50075#20/25.04677/121.55674)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d4babc0451a52af5d018f10937eeae95)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9142869e32f9d579ce83d0e5c51f65bd)
其他：
- [教練，我想畫地圖！](https://g0v.hackpad.com/EJfaf9C5gaT)
- [http://github.ronny.tw/](http://github.ronny.tw/)
- CSVMap 說明 [http://ronny.wang/blog](http://ronny.wang/blog)
- TURF - Advanced geospatial analysis for browsers and node
    - [http://www.slideshare.net/kurotanshi/coscup-2015-turfjs](http://www.slideshare.net/kurotanshi/coscup-2015-turfjs)
    - [https://github.com/kurotanshi/turfjs-examples](https://github.com/kurotanshi/turfjs-examples)
    - [http://turfjs.org/](http://turfjs.org/)


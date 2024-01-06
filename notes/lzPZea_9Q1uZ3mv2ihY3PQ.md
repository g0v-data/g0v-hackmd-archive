---
title: "g0v 車禍熱圖"
tags: hackpad
---

# g0v 車禍熱圖

> [點此觀看原始內容](https://g0v.hackpad.tw/T8ut8EVOZAW)

緣由：內政部警政署提供了台灣車禍地點分析，藉由向Google要地址，來分析台灣高頻率車禍地段，應用範圍包括：分析台灣危險路段、車禍時間車種統計、行車警告通知等

### 投影片

[https://](https://dl.dropboxusercontent.com/u/67191344/site/g0v_present/assets/player/KeynoteDHTMLPlayer.html#0)[dl.dropboxusercontent.com/u/67191344/site/g0v_present/assets/player/KeynoteDHTMLPlayer.html#0](https://dl.dropboxusercontent.com/u/67191344/site/g0v_present/assets/player/KeynoteDHTMLPlayer.html#0)

### 授權

Code: MIT
Content:CC-BY

### 工作區

網址：
[http://drainet.github.io/](http://drainet.github.io/cacci-opendata/heatMap.html)[cacci-opendata/](http://drainet.github.io/cacci-opendata/heatMap.html)[heatMap.html](http://drainet.github.io/cacci-opendata/heatMap.html)
Github:
[https://github.com/Drainet/cacci-opendata](https://github.com/Drainet/cacci-opendata)

各種車種範例備註：（來不及做成選單..只好這樣Demo...）
救護車地圖：
[http://drainet.github.io/](http://drainet.github.io/cacci-opendata/heapMapAmbulance.html)[cacci-opendata/](http://drainet.github.io/cacci-opendata/heapMapAmbulance.html)[heapMapAmbulance.html](http://drainet.github.io/cacci-opendata/heapMapAmbulance.html)
普通重型機車：
[http://drainet.github.io/](http://drainet.github.io/cacci-opendata/heapMapMotor.html)[cacci-opendata/](http://drainet.github.io/cacci-opendata/heapMapMotor.html)[heapMapMotor.html](http://drainet.github.io/cacci-opendata/heapMapMotor.html)
遊覽車-大客車：
[http://drainet.github.io/](http://drainet.github.io/cacci-opendata/heapMapBigBus.html)[cacci-opendata/](http://drainet.github.io/cacci-opendata/heapMapBigBus.html)[heapMapBigBus.html](http://drainet.github.io/cacci-opendata/heapMapBigBus.html)
> 可以參考這個人類便便地圖 [http://mochimachine.org/wasteland/](http://mochimachine.org/wasteland/)
> [name=Richard H]

> 地圖拉遠是熱源的表現，拉近以後顯示地點跟車禍種類
> [name=Richard H]


地址轉經緯度：
    目前初步已將 101-103 年 A1, A2 的地址 (只有地址) 匯入 DB，共 83 萬筆
    Google Maps API 的 Geocode 有限制每天只能查 2500 筆，打算透過群眾的 browser 隨機讀取還沒有經緯度的地址字串，協助查詢經緯度後傳回後端 DB

資料清理
- 目前規劃檔案介面會與Timothy Lee使用的相同，以csv為主，使得將來可以直接匯入處理
- 方法：舉例某一個欄位的所有數值，會通過根據型態的值域修正，出現頻率分析（類似huffman方法）
    - 對於地址，會先拆開成鄉鎮市等台灣標準格式，再針對每一個欄位進行文字修正與如上述的分析
- 會輸出一個正規化版本，按照資料庫正規劃觀念，分做兩個表格。先前討論認為這樣較方便將來有興趣的人使用
    - 車禍記錄：記錄每次車禍的時間，地址（地點），死亡受傷人數
    - 車禍載具細節：此次車禍的對象載具，數量
- 不會動到原始資料，但會產生報告及新資料，方便後續決定無法處理的資料要怎樣修改


### 參考

內政部原始資料
- 歷年交通事故資料(101-103年) [http://data.moi.gov.tw/MoiOD/Data/DataDetail.aspx?oid=67781E29-8AAD-46A9-A2C8-C3F339592C27](http://data.moi.gov.tw/MoiOD/Data/DataDetail.aspx?oid=67781E29-8AAD-46A9-A2C8-C3F339592C27)
- 即時交通事故資料(104年A1類) [http://data.moi.gov.tw/MoiOD/Data/DataDetail.aspx?oid=02D40248-7CAA-4354-82EA-E27AB8DCAB39](http://data.moi.gov.tw/MoiOD/Data/DataDetail.aspx?oid=02D40248-7CAA-4354-82EA-E27AB8DCAB39)
- 即時交通事故資料(104年A2類) [http://data.moi.gov.tw/MoiOD/Data/DataDetail.aspx?oid=986931B3-0E46-4F94-BF52-A2911499301F](http://data.moi.gov.tw/MoiOD/Data/DataDetail.aspx?oid=986931B3-0E46-4F94-BF52-A2911499301F)

地圖服務(Geolocation)
- Google MAP Geolocation API
    - 2500req/day, 5 req/sec (Free)
    - 100K req/day, 10 req/sec  (Business)
- OpenStreetMap（開放街圖）
[http://openstreetmap.tw/](http://openstreetmap.tw/)
- 目前看起來真的只有google可以用，其他的服務不是門牌無法查就是不支援unicode中文
> OpenStreetMap（開放街圖）試試看，這是使用圖資可以免費
> [name=Michael_Li]

> 我剛剛試過，有些情況會查不到巷弄門牌號碼，因為我們的地址資料比較千變萬化...
> [name=Kiwi]

> 大概主要是群眾編輯原故，不是商業圖資公司
> [name=Michael_Li]

> 開放街圖的門牌號碼資料還不完整，所以容易搜尋不到
> [name=Richard H]




---
title: "公有地大行動－GIS說明"
tags: 公有地大行動,hackpad
---

# 公有地大行動－GIS說明

> [點此觀看原始內容](https://g0v.hackpad.tw/fvH7zt5tIO7)


    「在國內，地籍圖是土地管理相關業務通用的地理資料，不論房屋買賣、土地買賣、產權管理、地價稅徵收、工程開發都會涉及到地籍圖使用。法院公告法拍屋、法拍土地、政府機關公告國有土地拍賣等等業務上，也都是利用地籍的地段、地號資訊來指涉空間範圍。**之前有介紹內政部地政司地籍圖資網路便民服務系統，可以查詢某一個地段地號的範圍，並套疊在Google Earth上，十分便民；本文則是希望進一步介紹查詢結果，如何下載地籍界線kml檔，再透過QGIS軟體，並套疊其他GIS圖層，例如街道圖、台灣堡圖、斷層線圖等。**」（[http://gis.rchss.sinica.edu.tw/qgis/?p=1112](http://gis.rchss.sinica.edu.tw/qgis/?p=1112)）

- 地政整合系統轉出檔轉換KML(Land2kml)
    - [http://www.ascc.sinica.edu.tw/gis/ISTIS/tools.html](http://www.ascc.sinica.edu.tw/gis/ISTIS/tools.html)
    - 用途：本程式可將地政整合系統轉出之BNP檔、COA檔、PAR檔，經坐標轉換及格式轉換產製KML檔。輸入所需地號或載入整段後即可開始轉換，其成果能透過Google Earth軟體，將地籍資料套疊Google衛星影像，提供地籍複丈測量之參考。


## Qgis是免費的GIS 系統


Quantum GIS資源網@Sinica
[http://gis.rchss.sinica.edu.tw/qgis/](http://gis.rchss.sinica.edu.tw/qgis/)

\[資源\] QGIS 2.4 正體中文語系檔
[http://www.ptt.cc/bbs/GIS/M.1405558087.A.7B6.html](http://www.ptt.cc/bbs/GIS/M.1405558087.A.7B6.html)

- 似乎qgis有地籍圖外掛
    [http://gis.rchss.sinica.edu.tw/index.php?option=com_content&view=article&id=413:plugin-for-qgis&catid=89:2009-07-22-06-28-27&Itemid=132](http://gis.rchss.sinica.edu.tw/index.php?option=com_content&view=article&id=413:plugin-for-qgis&catid=89:2009-07-22-06-28-27&Itemid=132)
> 這個外掛需要帳號密碼吧？ 能取得嗎？？
> [name=林立哲]


- 將shp檔轉成google map可讀取的kml檔
    [http://blog.xuite.net/lwkntu/blog/45081186](http://blog.xuite.net/lwkntu/blog/45081186)

- googlemap讀取kml流程
    [http://blog.xuite.net/lwkntu/blog/51204497-(GM-5)Google+Map%E8%AE%80%E5%8F%96KML%E6%AA%94](http://blog.xuite.net/lwkntu/blog/51204497-(GM-5)Google+Map%E8%AE%80%E5%8F%96KML%E6%AA%94)

- qgis有方便的轉檔功能
    [http://gis.rchss.sinica.edu.tw/qgis/?p=776](http://gis.rchss.sinica.edu.tw/qgis/?p=776)






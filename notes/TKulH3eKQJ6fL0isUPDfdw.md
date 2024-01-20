---
tags: GIS
---

# 這塊土地是幹嘛的？

因為參與桐花松時，在走迎龍古道時有看到許多台北人來這邊蓋房子，讓我想到可不可以做一個網頁，可以查查現在所在的土地在政府的都市計劃或是土地規劃是什麼樣的用地

作法
===
透過 WMS 圖磚去查他是什麼顏色，然後把色碼對應到他的用地

色碼表
=====
- [95-104年色碼表](https://maps.nlsc.gov.tw/demo/95RGB%E8%89%B2%E7%A2%BC%E8%A1%A8.jpg)
- [105年版](https://maps.nlsc.gov.tw/demo/105RGB%E8%89%B2%E7%A2%BC%E8%A1%A8.png)
- [109年版](https://maps.nlsc.gov.tw/demo/109%E5%B9%B4%E7%89%88%E5%9C%8B%E5%9C%9F%E5%88%A9%E7%94%A8%E8%89%B2%E7%A2%BC%E8%A1%A8.png)
- [都市計劃圖例](https://maps.nlsc.gov.tw/demo/20130627.png)
- [非都市土地使用分區圖](https://maps.nlsc.gov.tw/demo/20130702.png)
- [非都市土地使用分區圖II](https://maps.nlsc.gov.tw/demo/20140925.png)
- [非都市土地使用地類別圖](https://maps.nlsc.gov.tw/demo/20140924.png)
- [共筆](https://docs.google.com/spreadsheets/d/1BS-hYHE3hqWlUGI52vVhEx43L8S96fk5fduooId9rLo/edit#gid=0)

WMS
===
- https://maps.nlsc.gov.tw/T09/mapshow.action#
- https://www.nlsc.gov.tw/cl.aspx?n=13705
- https://maps.nlsc.gov.tw/pro/011_layer.html
- [圖片範例](https://wmts.nlsc.gov.tw/wmts?layer=LUIMAP82&style=default&tilematrixset=GoogleMapsCompatible&Service=WMTS&Request=GetTile&Version=1.0.0&Format=image%2Fpng&TileMatrix=16&TileCol=54769&TileRow=28161)
    - 參數
        - layer
            - LUIMAP

需要幫忙
======
1. 找找看政府還有哪些 WMS 圖磚是跟土地利用規劃有關的（關鍵字：土地利用、都市計劃...）
2. 把色碼對應出來

成果
===
https://g0v.github.io/querymap

感謝
===
謝謝 ninethday, tiff 參與
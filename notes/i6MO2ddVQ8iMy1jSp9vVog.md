---
title: "地址轉經緯度"
tags: hackpad
---

# 地址轉經緯度、以及「TWD97二度分帶座標」轉成「WGS84經緯度座標」

## 馬上用

- TGOS 全國門牌地址定位服務
    - https://www.tgos.tw/tgos/Web/Address/TGOS_Address.aspx
    - 部分地址會找不到
    - 批次功能需要會員資格
    - 批次門牌地址比對服務，上傳符合規定格式的csv檔案，進行批次門牌比對
    - 所得到的資料長這樣
        - X坐標：301821.554
        - Y坐標：2770761.004
        - 以上是「TWD97二度分帶座標」
        - 單筆資料：若想要轉成「WGS84經緯度座標」，請使用座標轉換工具
            - http://ts01.gi-tech.com.tw/waterAbnormal/trancoor/trancoor.aspx?WGS84_E=121&WGS84_N=24&TWD97_X=&TWD97_Y
            - 緯度：25.0441046325278 
            - 經度：121.513568741608
        - 批次資料：可使用以下工具
            - https://portal.taibif.tw/coordinateConverter.php
            - 技術提供：TaiBIF 臺灣生物多樣性資訊機構 Taiwan Biodiversity Information Facility
        - 單機版的 QGIS 也可以進行座標系統轉換
- TGOS 模擬真人操作圖台
    - [https://github.com/virus-warnning/taiwan-anthropogeography-data/blob/master/commons/smart_geo.py](https://github.com/virus-warnning/taiwan-anthropogeography-data/blob/master/commons/smart_geo.py)
- 台灣電子地圖服務網
    - https://medium.com/@oliverhua1/geocoding-%E6%89%B9%E9%87%8F%E8%99%95%E7%90%86%E5%9C%B0%E5%9D%80%E8%BD%89%E6%8F%9B%E7%B6%93%E7%B7%AF%E5%BA%A6-721ab2564c88
    - 不須會員
    - 可批量處理
- 國土測繪中心通用電子地圖的「地址模糊搜尋」
    - https://www.facebook.com/groups/718089658359103/permalink/1452474028253992/
- google API (不會寫程式的朋友，可以使用熱心網友們寫的批次轉換程式)
    - 注意！google API 轉出的經緯度只能用在 google map，這是 Google 的使用條款
    - 已失效 ~~http://geocoder.ccjeng.com/~~
    - http://gps.uhooamber.com/address-to-lat-lng.html
    - https://neverleave0916.com/GpsCoordinateConverter/
- 台中市限定，門牌資料大放送
    - [https://technews.tw/2017/03/23/taichung-city-government-give-building-and-housenumber-for-free-on-the-gis-datahub/](https://technews.tw/2017/03/23/taichung-city-government-give-building-and-housenumber-for-free-on-the-gis-datahub/)

## 討論串

- [https://www.facebook.com/groups/odtwn/permalink/1437194089628338/](https://www.facebook.com/groups/odtwn/permalink/1437194089628338/)


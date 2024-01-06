---
title: "台灣觀光Open Data資料集筆記"
tags: hackpad
---

# 台灣觀光Open Data資料集筆記

> [點此觀看原始內容](https://g0v.hackpad.tw/KXQ1KJfR3Qv)


### 資料集

- 全國
    - 景點　[http://data.gov.tw/node/7777](http://data.gov.tw/node/7777)
    - 旅館　[http://data.gov.tw/node/7780](http://data.gov.tw/node/7780)
    - 餐飲　[http://data.gov.tw/node/7780](http://data.gov.tw/node/7780)
    - 活動　[http://data.gov.tw/node/7780](http://data.gov.tw/node/7780)
- 台北市
    - [http://data.taipei/opendata/datalist/datasetByCategory?oid=travel](http://data.taipei/opendata/datalist/datasetByCategory?oid=travel)

### 交通部觀光資訊資料庫

- Website
    - [http://gis.taiwan.net.tw/Search.aspx](http://gis.taiwan.net.tw/Search.aspx)
- API Endpoint
    - [http://gis.taiwan.net.tw/aspx/Search/Search.aspx](http://gis.taiwan.net.tw/aspx/Search/Search.aspx)
- Dumps
    - [https://github.com/touhonoob/Taiwan-Travel-API](https://github.com/touhonoob/Taiwan-Travel-API)
- Search Syntax
    - Mode=0
    - Type
        - 0 景點
        - 1 旅館
        - 2 活動
        - 3 餐廳
    - Class
        - 類別
    - City
        - %
        - 基隆市
        - 新北市
        - 台北市
        - 桃園縣
        - 新竹縣
        - 新竹市
        - 宜蘭縣
        - 花蓮縣
        - 台東縣
        - 苗栗縣
        - 台中市
        - 彰化縣
        - 南投縣
        - 雲林縣
        - 嘉義縣
        - 嘉義市
        - 台南市
        - 高雄市
        - 屏東縣
        - 澎湖縣
        - 金門縣
        - 連江縣
    - Name
        - name for search
    - Lat
        - 緯度
    - Lon
        - 經度
    - radius
        - 半徑
- ID Syntax
    - Demo
        - [http://gis.taiwan.net.tw/aspx/Search/Search.aspx?Mode=2&ID=C3\_379000000A\_002467&Type=3](http://gis.taiwan.net.tw/aspx/Search/Search.aspx?Mode=2&ID=C3_379000000A_002467&Type=3)
    - Mode = 2
    - ID
        - ID From search result
    - Type
        - Type from search syntax

> 有考慮把資料編輯到OpenStreetMap上嗎？
> [name=yellowsoar]



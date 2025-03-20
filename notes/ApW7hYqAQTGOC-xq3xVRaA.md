---
tags: GIS, 都市更新
---

# 都市更新地區與更新事業範圍地圖


- 更新地區
    - 官網地圖：https://twur.cpami.gov.tw/zh/urban/area/0
    - 20201128 爬下更新地區 GIS 檔案 by Kiang
        - https://github.com/kiang/twur.cpami.gov.tw/tree/master/raw
    - 議題：要如何知道該地區計畫有計畫書圖？
        - https://g0v.hackmd.io/nL4fSlBfRmyMR9EMd6Wdgg?view
- 更新事業
    - 官網地圖：https://twur.cpami.gov.tw/zh/urban/rebuild/
    - 20220905 爬下更新事業 GIS 檔案 by Vik 
        - https://docs.google.com/spreadsheets/d/1I9SSrXF_57PWw0nY3WDIH5Fshhz_C3JvRZlphh7wI8g/edit?usp=sharing
        - 地號輪廓 geojson 應該是用地號清單，使用 地號API https://twland.ronny.tw/




---
構想
- 爬都更地號
    - UrbanRenewProgress by sherry : https://github.com/solring/UrbanRenewProgress
- 地號轉地圖
    - Land No. Mapper：https://g0v.hackmd.io/uFhBRHrnR-yvvFD4ZEn3XA

## 工作流程探討


### 手動案例

- 案件名稱：劃定臺北市中山區長安段二小段565地號等26筆土地為更新單元
- [紙本上的範圍資訊](http://uro.gov.taipei/public/MMO/uro/%E4%B8%AD%E5%B1%B1%E5%8D%80P0116.jpg)
- ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cbdfb8f429d0bae347891482c76e01c1)
- 都市更新案頁面：[http://www.gis.udd.taipei.gov.tw/ua\_frmEasyCase.aspx?case\_code=R097405](http://www.gis.udd.taipei.gov.tw/ua_frmEasyCase.aspx?case_code=R097405)
- 地段號資料：（此網址連結於更新案頁面中）
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_25ea9855426a3295c3574fd206123569)

運用「地號轉地圖」工具：[http://codepen.io/dz1984/full/NqgVPj/](http://codepen.io/dz1984/full/NqgVPj/)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2388938673078c01019536b6e453e629)
\-\-\-
台北市,長安段二小段,555
台北市,長安段二小段,559
台北市,長安段二小段,560
台北市,長安段二小段,561
台北市,長安段二小段,562
台北市,長安段二小段,563
台北市,長安段二小段,564
台北市,長安段二小段,565
台北市,長安段二小段,565-1
台北市,長安段二小段,566
台北市,長安段二小段,567
台北市,長安段二小段,568
台北市,長安段二小段,569
台北市,長安段二小段,570
台北市,長安段二小段,571
台北市,長安段二小段,574
台北市,長安段二小段,574-1
台北市,長安段二小段,574-2
台北市,長安段二小段,575-1
台北市,長安段二小段,575-2
台北市,長安段二小段,575-3
台北市,長安段二小段,575-4
台北市,長安段二小段,575-5
台北市,長安段二小段,575-6
台北市,長安段二小段,575-8
台北市,長安段二小段,575-9
\-\-\-
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4d37fa7201c30916bfafd7e96fb8997a)


| 案件編號 | 099738 |  |  |
| --- | --- | --- | --- |
| 案件名稱 | 變更臺北市大安區龍泉段一小段169地號等27筆土地為同小段169地號等26筆土地更新單元 |  |  |
| 行政區 | 地段小段 | 母號 | 子號 |
| 大安區 | 龍泉段一小段 | 0169 | 0000 |
| 大安區 | 龍泉段一小段 | 0169 | 0003 |
| 大安區 | 龍泉段一小段 | 0169 | 0004 |
| 大安區 | 龍泉段一小段 | 0169 | 0005 |
| 大安區 | 龍泉段一小段 | 0425 | 0000 |
| 大安區 | 龍泉段一小段 | 0425 | 0001 |
| 大安區 | 龍泉段一小段 | 0426 | 0000 |
| 大安區 | 龍泉段一小段 | 0427 | 0001 |
| 大安區 | 龍泉段一小段 | 0429 | 0000 |
| 大安區 | 龍泉段一小段 | 0429 | 0001 |
| 大安區 | 龍泉段一小段 | 0429 | 0002 |
| 大安區 | 龍泉段一小段 | 0429 | 0004 |
| 大安區 | 龍泉段一小段 | 0430 | 0000 |
| 大安區 | 龍泉段一小段 | 0430 | 0002 |
| 大安區 | 龍泉段一小段 | 0430 | 0003 |
| 大安區 | 龍泉段一小段 | 0430 | 0005 |
| 大安區 | 龍泉段一小段 | 0431 | 0000 |
| 大安區 | 龍泉段一小段 | 0431 | 0002 |
| 大安區 | 龍泉段一小段 | 0431 | 0003 |
| 大安區 | 龍泉段一小段 | 0434 | 0000 |
| 大安區 | 龍泉段一小段 | 0435 | 0000 |
| 大安區 | 龍泉段一小段 | 0436 | 0000 |
| 大安區 | 龍泉段一小段 | 0436 | 0001 |
| 大安區 | 龍泉段一小段 | 0437 | 0000 |
| 大安區 | 龍泉段一小段 | 0437 | 0001 |
| 大安區 | 龍泉段一小段 | 0437 | 0003 |


### 相關專案

- 都市更新天眼通
    - [https://grants.g0v.tw/projects/59623ae2ae3dd8001e1bfd0f](https://grants.g0v.tw/projects/59623ae2ae3dd8001e1bfd0f)
    - 都市更新天眼通希望以簡單易懂的都更簡介、簡易上手的都更地圖，與資訊豐沛的都市更新教室，結合民眾參與，使民眾、政府、民間單位能透過天眼通直觀有效的獲取各地都市更新資訊，以期讓民間能得到公開透明的資訊、協助政府未來都市更新、都市發展政策之研擬。
    - 資料
        - github：[https://github.com/duidae/UrbanRenewalEye/tree/master/data](https://github.com/duidae/UrbanRenewalEye/tree/master/data)
        - 此份資料的簡易線上地圖：[https://bit.ly/2Ltn2zN](https://bit.ly/2Ltn2zN)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fbc6d4d3c14329d732f2f3ef3010b6d6)
- 都更地圖網
    - [http://www.cityrenew.com.tw/map_search.php](http://www.cityrenew.com.tw/map_search.php)
- 青黃步街
    - [http://taipeiensis.blogspot.tw/](http://taipeiensis.blogspot.tw/)





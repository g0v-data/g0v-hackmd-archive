---
tags: Disfactory, 違章工廠, 違章工廠舉報系統
---

# 違章建築檢舉輔助系統 開發文件

<small>從 https://hackmd.io/ockOrC1VRfWyOwV8fvMF2w 搬來</small>

## 專案目的 
https://github.com/yoyo930021/Disfactory
建立一個方便的舉報違章建築的系統
舉報完會自動轉換成實際舉報所需資料並產生公文
方便地球公民基金會做後續向政府舉報的動作

## 階段
1. ==now== 建立蒐集資料系統
2. 匯入已知的違章工廠資料
4. 提供給地球公民基金會使用的後臺
5. 背後轉換成公文
6. 串接 Bot 做到完全匿名


## 開發需求
- 前後端分離
- 前端 (1 位)
    - Vue.js
    - Vue Composition API
        - [lib](https://github.com/vuejs/composition-api)
        - [RFC](https://composition-api.vuejs.org/)
    - OpenLayers
        - 地圖顯示的套件
        - 國土測繪圖資服務雲用同一套方便作業
    - TypeScript
- 後端 (1-2 位)
    - 程式語言
        - Node.js
        - Modern PHP
        - Python
        - 由最後負責後端的人討論決定
    - 資料庫
        - PostgreSQL
            - 有內建強大的地理查詢能力
        - SQLite
            - 聽說跟 PostgreSQL 地理部分用同套 Lib
        - MariaDB
            - 單純比較熟悉
        - 由最後負責後端的人討論決定
    - 簡單爬蟲能力
        - 可能需要分析國土測繪圖資服務雲的 API
 
## API

- 工廠資料
    - 使用者上傳
    - 國土舊有資料（ronny wang 農地和工廠經緯度：[full-info.csv](https://gist.github.com/ronnywang/f8bbf008e641b296c755f0167b51a550)）
        - x,y,xmin,ymin,xmax,ymax
        - 可能的違章工廠座標(To be confirmed)

- ==1== GET `/factories?lng={lng}&lat={lat}&range={km}`
    - 得到中心座標往外指定範圍的已有工廠資料
        - response
        ```Typescript=
        Array<{
          id: number,
          lng: number,
          lat: number,
          name: string,
          type: Enum, // 工廠類型
          images: [{
            id: number,
            url: string,
            alt: string
          }]
          report_at?: number // 回報日期
          status: Enum // 已回報 | 編輯中 | ... (TBD)
          // post_process: string
        }>
        ```
        > 還缺公文回報內容（照片）
        > 舊的違章工廠資料：地號中心點座標
        > 新增違章工廠資料：使用者定位 GPS
        > 需要確認一下國土規劃的 API 有提供到多少的地段地號轉座標與多邊形
        > post_process 用 html or markdown
        
- ==2== PUT `/factories/{id}`
    - 新增編輯指定 id 的工廠欄位資料
        - request body
        ```json
        {
          attribute1: value1,
          attribute2: value2,
        }
        ```
        > 要有編輯紀錄
- ==3== POST `/factories/{id}/images`
    - 上傳指定 id 的工廠圖片
        - content type: `multipart`
        - request body:
        ```Typescript=
        { 
          'image': 'image buffer here',
          'data': {  # provide this field will let 
            'path': 'https://i.imgur.com/123456.png',  # the only field that cannot be null
            'exif': {  
              'Latitude': 23.12,  
              'Longitude': 121.5566,
              'DateTimeOriginal': '2020:03:21 12:33:59',
            }
          }
        }
        ```
        - response
        ```Typescript=
        { token: string }
        ```
- ==4== POST `/images`
    - 上傳圖片
        - content type: `multipart`
        - request body:
        ```Typescript=
        { 
          'image': 'image buffer here',
          'data': {  # provide this field will let 
            'path': 'https://i.imgur.com/123456.png',  # the only field that cannot be null
            'exif': {  
              'Latitude': 23.12,  
              'Longitude': 121.5566,
              'DateTimeOriginal': '2020:03:21 12:33:59',
            }
          }
        }
        ```
        - response
        ```Typescript=
        { token: string }
        ```
- ==5== POST `/factories`
    - 新增工廠
        - request
        ```Typescript=
        {
          name: string,
          type: Enum,
          images: string[],
          other: string,
          lat: number,
          lng: number,
          nickname: string,
          contact: string
        }
        ```
        > 少舉報人的聯絡方式（只有新增的時候會問）：稱呼 & 聯絡方式（電話號碼或 email）
        > other 是 description 的意思，上限 1024 cha

PS. 少了新增聯絡方式的流程 所以暫時沒設計相關 API

> 還有地球公民基金會後台的 API 還沒開
> 還需要編輯紀錄 log 

目前資料是五萬筆


## 後端架構

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b6eba6c8d06a92b8b3bc7b0fddecdc2a)

這是最基本要完成的部份。如果後續有時間再加：
- DB backup: 寫 cron job 或用個 master-slave （但不確定怎麼在 middle2 上設定）
- cron job 打 Imgur：因為半年沒 query 就會刪掉
- asynchronous task queue: 座標轉地號和圖片上傳都可以在背景做掉，減低 blocking time。不過會有 data inconsistency 的問題，處理起來有點複雜。
- DB caching: 由於不會很常增加新的違章工廠，加上總資料量其實很小，可以有寫個 write-through 機制的 cache
- Image backup and self-hosting

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8318e305f7fd71fea7dcb3925be68b18)


> type 是 fact_type
> fact_id 用 uuid
> 要不要新增的時候如果附近一公尺已有舉報工廠，會新增再已有工廠上=> 先開 issue
> img 要存 uuid 和 imgur 的 path
> img 要存上傳 created_time，最好存照片 EXIF 照相時間（沒有就 null）。上傳 imgur 時會把 EXIF 抹掉
> query_string: request body
> action_type
> action_body
> 




## 其它連結

- Firebase 相關，可能可以拿來處裡 Geo 資料
    - https://github.com/geofirestore/geofirestore-js
    - https://angularfirebase.com/lessons/geolocation-query-in-firestore-realtime/
    - https://firebase.google.com/docs/reference/android/com/google/firebase/firestore/GeoPoint


## API 研究

- https://maps.nlsc.gov.tw/

從經緯度拿地段

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5c2c9ce7827ab7b0f04ccced1dec42ae)


iTHome 鐵人賽 30天打造我的WebGIS https://ithelp.ithome.com.tw/users/20107816/ironman/1541

https://www.geoapify.com/leaflet-vs-openlayers/ Leaflet vs Openlayers

https://stackoverflow.com/questions/32046601/convert-xyz-coordinate-of-a-tile-to-longitude-latitude

[國土地段轉地號](https://maps.nlsc.gov.tw)

- https://github.com/ronnywang/luz.tcd.gov.tw : ronny 用 opencv 算外框對回去 geojson
- https://maps.nlsc.gov.tw/demo/105RGB%E8%89%B2%E7%A2%BC%E8%A1%A8.png 104 土地使用分類表
- https://docs.opencv.org/master/d3/dc0/group__imgproc__shape.html#gadf1ad6a0b82947fa1fe3c3d497f260e0
- opencv.js https://docs.opencv.org/3.4/d0/d84/tutorial_js_usage.html
- https://github.com/oliver-moran/jimp
- https://www.npmjs.com/package/replace-color
- [imgur API 研究](https://hackmd.io/snF73YIRT2KZ4Tw1oQWb2g)
- [運用 Django 上傳圖片的 API 教學](https://www.techiediaries.com/django-rest-image-file-upload-tutorial/)
- [DRF_function-based-views](https://www.django-rest-framework.org/api-guide/views/#function-based-views)

forEachLayerAtPixel
---
tags: GIS,
---

# ZUTÔOMAYO 通用地圖

## [提案簡報 Proposal](https://drive.google.com/file/d/1t0rDIByIFoHjIHMZH7EzGJ5PwmjnFsfy/view)

## 專案簡介 Project Intro

### 目標 Goals

以[ロケスマ](https://www.locationsmart.org/)為靈感啟發，盤點潛在的公共設施圖資需求，將開放資料轉換為可自動更新的圖層來源，並設計可訂閱多重圖層、開源的通用地圖程式。

Inspired by LocationSmart, this project aims to survey potential needs on public facility map data, convert open data into auto-updated map layers, and design an open-source, general-purpose map application that allows users to subscribe to such layer data.

### 為什麼叫做這個名字 Naming Logic

<ruby lang="ja">地<rt>ち</rt>図<rt style="font-weight: bold">ず</rt></ruby>（日本語） + <ruby lang="nan-tw">地<rt>tē</rt>圖<rt style="font-weight: bold">tôo</rt></ruby>（台語） + <strong>ma</strong>p + よ

## 可能的資料來源 Possible Data Sources

- 各業者官網 Respective Official Websites
- [政府資料開放平台 Open Data Platform](https://data.gov.tw/)
- [全資料地圖 All the Places](https://alltheplaces.xyz/)
    - 看起來是 WikiData 相關專案
    - 注意事項 Caveats：
        - 銀行分行跟 ATM 會列在一起，要特別用 `amenity=atm` 篩選
        - 部分品牌爬蟲不會標示 `_tw`（例如永豐銀行 `bank_sinopac`），整理銀行列表時需要手動處理
    - [共編分類 Categorization Collab](https://docs.google.com/spreadsheets/d/1SCzLBIPhkLy701dzY4MLu1OyPK0APh0xMC-NBDyDZdo/edit)

## 圖層許願 Data Wishlist

- 公共電話 Public Telephone
    - [CHT Wi-Fi熱點查詢](https://www.cht.com.tw/home/cht/service/hotspotfinder)的查詢欄可以選公共電話亭。
    - [提供一卡通付費之中華電信公共電話位置資訊](https://www.i-pass.com.tw/CKPackage/files/ChtPublicTelephoneInfo160411.pdf)
    - [開放街圖公共電話位置資訊](https://overpass-turbo.eu/s/2bzS)
- 飲水機 Water Fountain
    - [奉茶行動APP](https://www.circuplus.org/water-refill-map/) 
    - [開放街圖飲水源資訊](https://overpass-turbo.eu/s/2bzY)
- 公共廁所 Public Toilet
  - 雲林
    - 資料來源 Data Source：[在雲林的無障礙廁所清單](https://data.gov.tw/dataset/174494)
    - 格式 Format：XLSX, CSV, XML, JSON
  - [開放街圖廁所資訊](https://overpass-turbo.eu/s/2bzZ)
- 郵局 Post Office
  - 資料來源 Data Source：[郵局全國營業據點](https://data.gov.tw/dataset/5950)
  - 格式 Format：CSV
- 郵筒 Post Box
- 提款機 ATM
  - 資料來源 Data Source：[金融機構ATM位置查詢一覽表](https://data.gov.tw/dataset/24333)
  - 格式 Format：CSV
  - 問題 Issues：
    - 只有地址描述，沒有座標 no coordinate available, only address
    - [郵局](https://data.gov.tw/dataset/6121)的有經緯度 coordinates are available for Post Office ATMs
- 便利商店 Convenience Store
  - 資料來源 Data Source：
    - [從各種公司網站下載地圖資料的專案](https://github.com/alltheplaces/alltheplaces) 
      - [全資料地圖](https://alltheplaces.xyz/)
    - [公司登記(依營業項目別)－便利商店](https://data.gov.tw/dataset/108388)
        - 由於是從公司營業登記匯出的資料，看起來不完全準確 the data was sourced from company registar, questionable usability
    - [全國5大超商資料集](https://data.gcis.nat.gov.tw/od/detail?oid=0202BFA9-8116-4E63-A41A-58A5F4EAF7A2)
        - 有地址沒有座標 address only, no coordinates
- 公共自行車 YouBike
    - TDX 可以取得，像是[台南](https://tdx.transportdata.tw/api/basic/v2/Bike/Station/City/Tainan?%24format=JSON)
- 廟宇 Temples
    - [台灣宗教地圖](https://kiang.github.io/religions/)

## 資料格式 Data Format

* JSON?
    * GeoJSON?
    * Feature 怎麼正規化？ How to normalize features?
        * 跟 OSM 欄位命名相容？ Make it compatible with OSM field?
* KML?
    * 會不會太肥大？ Is it too heavy?

## 應用程式 Application



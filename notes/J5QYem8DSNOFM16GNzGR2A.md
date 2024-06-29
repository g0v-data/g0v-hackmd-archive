---
tags: GIS,
---

# Google My Map

## 工具介紹

<iframe width=100% height="490" src="https://www.youtube.com/embed/ckU1ytIo19c" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>
<br>

==GoogleMyMap 操作教學影片：https://youtu.be/ckU1ytIo19c==
工具網址：https://www.google.com.tw/intl/zh-TW/maps/about/mymaps/

🔻「搭公車吃美食」Google My Map 示範地圖：http://bit.ly/3aZN60B

<iframe src="https://www.google.com/maps/d/u/0/embed?mid=1f08BqdrZtJynrJvdo3-cIK6ZWwFeEjUJ" width=100% height="480"></iframe>


🔻 匯入 Google Photo 相簿照片，匯入至 Google My Map，示範地圖：https://bit.ly/2UV9h2k

<iframe src="https://www.google.com/maps/d/embed?mid=1YyKA6hK9nRxXYU3e1LG2F4W9v5o&hl=zh-TW" width=100% height="480"></iframe>

:::spoiler 備用內容
🔻 匯入 雲端硬碟中的 Google Spreadsheet
- 資料來源：[民間社群標註官方公布的確診者足跡 😷](https://g0v.hackmd.io/GNfNQ8NbQ5KXJNTyftRLgA)
- 透過試算表的函式，與資料來源同步更新資料「台南市政府公布確診者足跡位置」
    - `=IMPORTRANGE("1eNgxy1nP36rhugQ5tcti2a7MHsDVYipHYDfOGFbaqIU", "台南市!A1:X")`
- 本次課程影片中，示範地圖所使用的是這一個 [Spreadsheet 資料集](https://docs.google.com/spreadsheets/d/1pL2R3Nkynp0uqHit0dSDJiaCg8TlGrBWBp8EkqN5ckk/edit?usp=sharing)
:::

## 更多介紹資源

「20220802 水保局雲端地理資訊結合google地圖運用於勘查作業 (吳聲傑)」
https://youtu.be/vkpRTL8YU8Q

採用 CSV 格式上傳資料到 Google My Map
- 緯度一個欄位、經度一個欄位，這是上傳「點資料」
- 若想要上傳線與面資料，請新增一個欄位，欄位名稱可以用 WKT
    - 點的表達方式：
        - POINT (121.5488456 25.0378513)
    - 線的表達方式：
        - LINESTRING (121.5450209 25.0454118, 121.5456298 25.0454142, 121.5456351 25.0455284, 121.5459731 25.0455284)
    - 面的表達方式：
        - POLYGON ((121.518558 25.0951536, 121.5190583 25.0946229, 121.5192326 25.0956843, 121.518558 25.0951536))

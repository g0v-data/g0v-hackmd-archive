---
tags: GIS
---

# 使用網頁工具，將 Shp 檔案格式轉成 geojson 或 kml 的步驟

操作過程影片：https://youtu.be/EwWIn7Pms08

<iframe width=100% height="395" src="https://www.youtube.com/embed/EwWIn7Pms08" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### 步驟

1. 下載示範檔案：臺南市行政區範圍 Shp 格式 
2. 使用 shp2geojson，轉換並取得 geojson 格式
3. 使用 geojson.io，轉換並取得 kml 格式

提醒：如果您想要轉檔的檔案，檔案本身很大，網頁端一直轉圈圈、無法如以下步驟一步一步執行，建議可以使用 [QGIS 單機版軟體來轉換檔案](https://g0v.hackmd.io/@chewei/gis/https%3A%2F%2Fg0v.hackmd.io%2FAH6MEsSuSZ2pvxQIJld-Og)

## 步驟1: 下載示範檔案：臺南市行政區範圍 Shp 格式

檔案網址：http://bit.ly/3aWJrAP

(1) 點擊下載按鈕，得到 zip 檔案

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5b9b5369674611c4e396780db00b4f67.png)


## 步驟2: 使用 shp2geojson，轉換並取得 geojson 格式

(1) 打開網頁服務：http://gipong.github.io/shp2geojson.js/
(2) 將上一步驟所下載的 zip 檔案（不用解壓縮），拖曳或上傳至網頁中
(3) 網頁需要您填入這個檔案的「座標系統」以及「字元編碼」
(4) 請在「臺南市行政區範圍資料頁面」中，找到「座標系統：3826」以及「字元編碼：Big5」，並填入
(5) 填好「座標系統」以及「字元編碼」之後，可以點擊「預覽」，並且「下載」得到 geojson 格式

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ff382059d1592b65ac7452bcf19f83b7.png)


## 步驟3: 使用 geojson.io，轉換並取得 kml 格式

(1) 打開網頁服務：http://geojson.io/
(2) 將上一步驟所下載的檔案，拖曳或上傳至網頁中
(3) 滑鼠移動到 Save（不要點擊），介面會跳出可下載的格式，再用滑鼠點擊您想要下載的格式

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_464b635ad95425e3e7f034cd33873a97.png)

## 得到成果檔案 👍

[kml 格式](https://drive.google.com/file/d/1vlDBEV3r2ZYjrXHnmUwU3Jyb_SNTIcEu/view?usp=sharing)


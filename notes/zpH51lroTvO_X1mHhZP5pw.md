---
tags: GIS-edu-camp-2021-summer
---

# 地理資料與地圖課 - PeiJie Lin 作業區

好用連結
- 「講師」示範交作業：https://g0v.hackmd.io/dfqmJkn2Sem_Uqn-b6TIHQ
- 課程教材的整合網址：https://g0v.hackmd.io/@chewei/gis/
- 課程參與者．問答共享區，來看看大家的提問與討論 ➜ [頁面](https://g0v.hackmd.io/@chewei/gis-camp-work/)
- [「零時小學校 2021-22 Demo Day」徵件活動](https://sch001.g0v.tw/brd/sch001-2021) 💪

## 第一堂：地理資料與地圖課介紹 😎 

提醒：本次課程，講師有錄製「如何交作業」的影片，若不太清楚如何開始完成作業，可以適時參考影片內的操作過程哦 💪

### 作業一：請在「GIS 地理資料與應用」的資源共筆頁面，任意找一個線上主題地圖，描述與介紹地圖特色

臺北市市有閒置空間整合查詢平台
https://www.reformspace.taipei/

<iframe src="https://www.reformspace.taipei/"width=100% height="480"></iframe>

描述
資料集
顯示空間位置方便搜尋
結合政策專案提高媒合使用者與閒置空間可能性

### 作業二：請描述一個您近期想要建立的「主題地圖」，或是想要處理的「地理資料」，並請提供資料集的網址


(待改)台灣有USR計畫投入的地方、台灣社區旅遊點?台灣糖鐵地圖
偏鄉的小黃公車、公車路線?國發會地方創生?離家最近的打疫苗診所

## 第二堂：介紹線上協作地圖工具 👩‍💻 

提醒：本次課程，講師有錄製「如何交作業」的影片，若不太清楚如何開始完成作業，可以適時參考影片內的操作過程哦 💪

### 作業一：請創建一個資料地圖，並提供地圖網址。您可以挑選本次教學中介紹的地圖工具，並請提供您所使用的資料集來源網址

使用google my map
標註工作上合作單位的位置及分類
https://www.google.com/maps/d/u/1/edit?hl=zh-TW&mid=1Ii6GF3zT9vAdp8qYGkVrcXxOoOcrfRHE&ll=22.923273631699878%2C120.58788319969392&z=10
**(問題)**
1.在台南市行政區從geojson2kml轉檔網頁中，打開台南行政區geojson都沒反應無法轉換成kml
2.另外嘗試政府資料開放平台的鎮市區界線(TWD97經緯度)也碰到相同問題https://data.gov.tw/dataset/7441
3.接續第二點若解決，想知道如何只擷取想要的行政區KML(或是只能在QGIS上執行?)
4. Awesome-table 地圖模式，以「民間社群標註官方公布的確診者足跡 😷 」資料連結失效


chewei>
1. 關於「Shp 檔案格式轉成 geojson 轉成 kml 的步驟」我這邊有錄製一段影片與步驟截圖，請參考這份共筆https://g0v.hackmd.io/JayE3varSemjMywEU6ABkw?view
2. 感謝提醒「民間社群標註官方公布的確診者足跡 😷」，我忘記把 sheet 頁面的瀏覽權限打開，目前已調整可瀏覽。Awesome-table 的地圖瀏覽授權，會沿用來源 google spreadsheet 的瀏覽授權

**感謝解答!!!**


### 作業二：您預計如何與其他人協作這個資料地圖？請描述協作的方式

是，可分享給不同專案的同事增減、彙整資料
將使用GoogleMyMap，提供無基礎使用者快速上手協作，後續再視需求以QGIS製作相關資料

## 第三堂：操作 BigGIS 衛星影像平台 🛰 與歷史照片定位平台

提醒：本次課程，講師有錄製「如何交作業」的影片，若不太清楚如何開始完成作業，可以適時參考影片內的操作過程哦 💪

- 作業一：熟悉 BigGIS 登入、搜尋圖資、調整與介面
- 作業二：學會操作 BigGIS 的輸出成 kmz 功能
- 作業三：瞭解 BigGIS 搜尋之事件點資料系統：歷史影像平台
- 擴充作業：學會使用 BigGIS 產生 gif 時間序列 ( 動態影像 )
- 擴充作業：使用 Windy 網頁，上傳探討範圍的地理框線資料 kml，瀏覽更多即時大氣氣象圖資效果 

### 作業一：熟悉BigGIS登入、搜尋圖資、調整與介面

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_16491aadc052122d96a5fdd7a007d8ed.JPG)


### 作業二：學會操作BigGIS的輸出成kmz功能

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ffb7cd81c555dcef73a6e82210bbbfc7.JPG)
 

### 作業三：瞭解BigGIS搜尋之事件點資料系統：歷史影像平台
 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_622aeeb405bb018ebf24690ce67ee8af.JPG)
問題 登入後為何是個不認識的名字?(非臉書帳號名稱)

### 擴充作業：學會使用BigGIS產生gif時間序列( 動態影像 )

2018-2021左鎮區岡林SPOT衛星影像
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c97c0ec300e4c6927e7370c49debff0b.gif)


### 擴充作業：使用 Windy 網頁，上傳探討範圍的地理框線資料 kml，瀏覽更多大氣圖資效果 

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_15ec94bc9176bfb04dbeabcdcc19f140.JPG)


## 第四堂：下載並操作 QGIS 軟體 ⚙ 

### 作業：來輸出一個您製作的台灣鄉鎮男女比例地圖和鄉鎮老化地圖吧！

鄉鎮男女比例地圖
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d4280c2fa412fc74c333ca8f7d81f098.png)

鄉鎮老化地圖
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1be252b4f19924cd734c1ed594f5ef2c.png)


## 第五堂：瞭解公民科技專案 🚀 Disfactory 農地違章工廠回報平台

提醒：本次課程，講師有錄製「如何交作業」的影片，若不太清楚如何開始完成作業，可以適時參考影片內的操作過程哦 💪

### 作業：找到一間離你最近的違章工廠，並將其不同年份的空拍圖放上 disfactory.tw 網站上，該點位的資料當中

>請直接將上傳成功的 disfactory.tw 網頁截圖上傳至此
>可以參考「講師示範交作業」：https://g0v.hackmd.io/dfqmJkn2Sem_Uqn-b6TIHQ
>
>在豐原念書，家鄉是隔壁的后里~
>![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fd0d0962e92d24e83940972c6ad7bb7e.JPG)


## 筆記區

你的筆記區
開放圖磚服務(WMTS)
怎麼在google my map點出點位匯入QGIS後可呈現屬性資料(XY)
QGIS輸出圖層可能有背景透明的PNG?
在第一堂課作業二寫了工作相關的糖鐵路線，發現居然有糖鐵專案的坑(!)
Line 線型資料：台南公車路線>>如何從xml轉geojson再轉kml;要如何知道先轉成什麼而得到最後要用的檔案格式
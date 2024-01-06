---
tags: GIS-edu-camp-2021-summer
---

# 地理資料與地圖課 - [邱晨境](/zalSHE0mST2nrToOq78BNQ) 作業區

好用連結
- 「講師」示範交作業：https://g0v.hackmd.io/dfqmJkn2Sem_Uqn-b6TIHQ
- 課程教材的整合網址：https://g0v.hackmd.io/@chewei/gis/
- 課程參與者．問答共享區，來看看大家的提問與討論 ➜ [頁面](https://g0v.hackmd.io/@chewei/gis-camp-work/)

## 第一堂：地理資料與地圖課介紹 😎 

提醒：本次課程，講師有錄製「如何交作業」的影片，若不太清楚如何開始完成作業，可以適時參考影片內的操作過程哦 💪

### 作業一：請在「GIS 地理資料與應用」的資源共筆頁面，任意找一個線上主題地圖，描述與介紹地圖特色

地圖案例：太陽能區域能源資訊

<iframe src="http://globalsolaratlas.info/?c=23.669682%2C121.396179%2C8" width=100% height="480"></iframe>


欲解決問題
* 哪些區域有發展太陽能潛力
* 光伏設備如何設置最佳

資料集
Solar resource and photovoltaic power potential data layers
Solar resource data © 2021 Solargis
Photovoltaic power potential data © 2021 Solargis

使用感想
概念還不錯，資料也蒐集蠻齊全的。

why choose this?
綠能發展是未來很夯的能源議題，想說看看圖資方面有哪些？




### 作業二：請描述一個您近期想要建立的「主題地圖」，或是想要處理的「地理資料」，並請提供資料集的網址

台中市外送員服務需求專案

臺中市建檔公廁資訊
https://data.gov.tw/dataset/84010
https://datacenter.taichung.gov.tw/swagger/OpenData/eb854854-fccb-4297-9893-36c300b05272
臺中市轄內設置飲水機供民眾使用之處所
https://data.gov.tw/dataset/84048
https://datacenter.taichung.gov.tw/swagger/OpenData/2559b7b0-b8f3-433c-876c-2cd46cb15259

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2bdbefb00932e6690269c393b0361175.PNG)



## 第二堂：介紹線上協作地圖工具 👩‍💻 

提醒：本次課程，講師有錄製「如何交作業」的影片，若不太清楚如何開始完成作業，可以適時參考影片內的操作過程哦 💪

### 作業一：請創建一個資料地圖，並提供地圖網址。您可以挑選本次教學中介紹的地圖工具，並請提供您所使用的資料集來源網址
此專案想要提供外送者找不到公共廁所和飲水(以致去買瓶裝水)需求的地圖資訊
現行有兩個APP(奉茶Water refill map、找廁所)，但我希望整合上面兩個，又可以新添新的點位。

其實我想得很廣很深了，但想要一步步來。

現在有幾個問題：

1. 地址轉換經座標(暫解決，利用TGOS批次處理(每次都要申請)，但對於資料筆數需要兩三天進行更新，此非長遠之計，嘗試使用Python，但爬蟲一直顯示錯誤)
1. 評估googlemymap、umap、awesome table，最佳使用工具是awesome table，因為可以篩選條件(如有沒有飲水提供點營業、廁所類型等)，spreadsheet也比較好整理資料，但*使用者無法定位自己位置*，便不方便立即得知最近該去哪裡飲水或上廁所。



### 作業二：您預計如何與其他人協作這個資料地圖？請描述協作的方式

為了提高外送員加資料的動機，流程簡化成
新廁所點位：
1. 下載GPS地理位置相機
1. 拍廁所門牌資訊一張
1. 傳至官方帳號
1. 之後後續再由小編整理資訊，到spreadsheet

飲水點：
1. 詢問商家是否願意加入，提供飲水？(可能事先準備稿及實體照片)
1. 送給商家意願調查表單連結(紙張上印QRcode及基本資訊)
1. 若商家有意願，就可填表單，後續溝通，再由小編整理資訊，到spreadsheet

## 第三堂：操作 BigGIS 衛星影像平台 🛰 與歷史照片定位平台

提醒：本次課程，講師有錄製「如何交作業」的影片，若不太清楚如何開始完成作業，可以適時參考影片內的操作過程哦 💪

- 作業一：熟悉 BigGIS 登入、搜尋圖資、調整與介面
- 作業二：學會操作 BigGIS 的輸出成 kmz 功能
- 作業三：瞭解 BigGIS 搜尋之事件點資料系統：歷史影像平台
- 擴充作業：學會使用 BigGIS 產生 gif 時間序列 ( 動態影像 )
- 擴充作業：使用 Windy 網頁，上傳探討範圍的地理框線資料 kml，瀏覽更多即時大氣氣象圖資效果 

### 作業一：熟悉BigGIS登入、搜尋圖資、調整與介面

你的作業區

### 作業二：學會操作BigGIS的輸出成kmz功能

你的作業區

### 作業三：瞭解BigGIS搜尋之事件點資料系統：歷史影像平台
 
你的作業區

### 擴充作業：學會使用BigGIS產生gif時間序列( 動態影像 )

你的作業區

### 擴充作業：使用 Windy 網頁，上傳探討範圍的地理框線資料 kml，瀏覽更多大氣圖資效果 

你的作業區

## 第四堂：下載並操作 QGIS 軟體 ⚙

### 作業：也來輸出一個您製作的台灣鄉鎮男女比例地圖和鄉鎮老化地圖吧！

你的作業區

## 第五堂：瞭解公民科技專案 🚀 Disfactory 農地違章工廠回報平台

提醒：本次課程，講師有錄製「如何交作業」的影片，若不太清楚如何開始完成作業，可以適時參考影片內的操作過程哦 💪

### 作業：找到一間離你最近的違章工廠，並將其不同年份的空拍圖放上 disfactory.tw 網站上，該點位的資料當中

>請直接將上傳成功的 disfactory.tw 網頁截圖上傳至此
>可以參考「講師示範交作業」：https://g0v.hackmd.io/dfqmJkn2Sem_Uqn-b6TIHQ

## 筆記區

ClimateEx (Climate Explorer) 的概念我超喜歡，但在以下的網址已找不到地圖QQ
http://sil.uc.edu/webapps/climateex.


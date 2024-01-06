---
tags: GIS-edu-camp-2021-summer
---

# 地理資料與地圖課 - [Oscar] 作業區

<!-- 好用連結
- 「講師」示範交作業：https://g0v.hackmd.io/dfqmJkn2Sem_Uqn-b6TIHQ
- 課程教材的整合網址：https://g0v.hackmd.io/@chewei/gis/
- 課程參與者．問答共享區，來看看大家的提問與討論 ➜ [頁面](https://g0v.hackmd.io/@chewei/gis-camp-work/)
- [「零時小學校 2021-22 Demo Day」徵件活動](https://sch001.g0v.tw/brd/sch001-2021) 💪 -->

## 第一堂：地理資料與地圖課介紹 😎 

<!-- 提醒：本次課程，講師有錄製「如何交作業」的影片，若不太清楚如何開始完成作業，可以適時參考影片內的操作過程哦 💪 -->

### 作業一：請在「GIS 地理資料與應用」的資源共筆頁面，任意找一個線上主題地圖，描述與介紹地圖特色

IQ air網址: https://www.iqair.com/earth 

特色：
- 在全球地圖上使用不同顏色代表空氣污染的嚴重程度，可從下圖中看出各種顏色對照的US AQI指數。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d75fc609b40d87a6d13d5949834840f7.png)
- 空氣污染種類有兩種(PM2.5、PM10)，此外也可選擇Wind來觀察各地風速
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ff351a2fac2626e51972644eb6a01b26.png)
- 地圖右邊還有AQI指數排名，數值越大的國家排名越前面
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6aac47dffe632754e7448d48c4d52644.png)

使用者可使用此地圖隨時監測、取得世界各地的空氣污染資料，搭配風速以及風向，可以有效預估污染會往哪個方向擴散，提前進行預防工作。


### 作業二：請描述一個您近期想要建立的「主題地圖」，或是想要處理的「地理資料」，並請提供資料集的網址
我想做台灣遊憩景點地圖，供在台灣遊玩的民眾使用，加速規劃行程。
- 基隆海域遊憩景點開放性資料: https://data.gov.tw/dataset/143682
- 台中市景點: https://data.gov.tw/dataset/85008
- 台南景點: https://data.gov.tw/dataset/6183

## 第二堂：介紹線上協作地圖工具 👩‍💻 

<!-- 提醒：本次課程，講師有錄製「如何交作業」的影片，若不太清楚如何開始完成作業，可以適時參考影片內的操作過程哦 💪 -->

### 作業一：請創建一個資料地圖，並提供地圖網址。您可以挑選本次教學中介紹的地圖工具，並請提供您所使用的資料集來源網址

景點地圖:
- awesome table網址: https://app.awesome-table.com/-Mgx_ZfkYaCII4QtIO5H/view

資料: 
- 台中市景點: https://data.gov.tw/dataset/85008
- spreadsheet: https://docs.google.com/spreadsheets/d/1TusySJUPwWf9CbqsFGzFz69vXrmA3FjZnJSP69wlg3E/edit?usp=sharing

<iframe referrerpolicy="no-referrer-when-downgrade" height="600px" width="100%" style="border:none;" src="https://view-awesome-table.com/-Mgx_ZfkYaCII4QtIO5H/view"></iframe>


TODO:
- 將基隆、台南景點整合進同一個spreadsheet
- 不同資料來源的欄位不太一樣，需要人工調整
- 仍在思考同個spreadsheet如何放置不同縣市的資料，需要使用清楚易懂的排列方式

### 作業二：您預計如何與其他人協作這個資料地圖？請描述協作的方式

- 使用spreadsheet新增景點: 目前只有三個縣市的資料，需要協作者搜集其他縣市資料，並依照現有的欄位整理，加入spreadsheet
- 如果規模持續擴大，並且有很多喜好旅遊的協作者加入，也可以增加國外景點
    - https://docs.google.com/spreadsheets/d/1TusySJUPwWf9CbqsFGzFz69vXrmA3FjZnJSP69wlg3E/edit#gid=1500150361

## 第三堂：操作 BigGIS 衛星影像平台 🛰 與歷史照片定位平台

<!-- 提醒：本次課程，講師有錄製「如何交作業」的影片，若不太清楚如何開始完成作業，可以適時參考影片內的操作過程哦 💪 

- 作業一：熟悉 BigGIS 登入、搜尋圖資、調整與介面
- 作業二：學會操作 BigGIS 的輸出成 kmz 功能
- 作業三：瞭解 BigGIS 搜尋之事件點資料系統：歷史影像平台
- 擴充作業：學會使用 BigGIS 產生 gif 時間序列 ( 動態影像 )
- 擴充作業：使用 Windy 網頁，上傳探討範圍的地理框線資料 kml，瀏覽更多即時大氣氣象圖資效果 -->

### 作業一：熟悉BigGIS登入、搜尋圖資、調整與介面

google電子地圖疊上保安林地 + 地調所地質圖
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_04af4bb09b91eca5f7cdd7564870a69c.png)


### 作業二：學會操作BigGIS的輸出成kmz功能

使用google earth pro打開kmz檔案
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f34b9b10ff8f2fe68771068cd31f9c8d.png)

### 作業三：瞭解BigGIS搜尋之事件點資料系統：歷史影像平台

使用時空地圖查詢高雄市桃源區的歷史事件影像
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3b37659af55e4b4ffb7bba410564ec28.png)


### 擴充作業：學會使用BigGIS產生gif時間序列( 動態影像 )

第一次使用時加入的圖總是一片空白，所以想說將範圍縮小，同時也能所短計算時間
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_49ba6c22d5a19a31671178d5c090e31b.gif)

### 擴充作業：使用 Windy 網頁，上傳探討範圍的地理框線資料 kml，瀏覽更多大氣圖資效果 

澎湖機場：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_79d2bdad20772ffca301ba8f324b5739.png)

但仍然沒有很懂實際可以怎麼應用，為什麼要在bigGis將一個地區選起來放到windy中，從教學影片中看到其他疊圖圖層並沒有顯示在windy上（候鳥區域等圖層），那為什麼不直接從windy上尋找想要關注的區域即可？


## 第四堂：下載並操作 QGIS 軟體 ⚙ 

### 作業：來輸出一個您製作的台灣鄉鎮男女比例地圖和鄉鎮老化地圖吧！

男女比例地圖
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6a3fa45f07a0b652d24cdb34af15429d.png)

鄉鎮老化地圖
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b1285854970022b6ca84158a096062b2.png)



## 第五堂：瞭解公民科技專案 🚀 Disfactory 農地違章工廠回報平台

<!-- 提醒：本次課程，講師有錄製「如何交作業」的影片，若不太清楚如何開始完成作業，可以適時參考影片內的操作過程哦 💪 -->

### 作業：找到一間離你最近的違章工廠，並將其不同年份的空拍圖放上 disfactory.tw 網站上，該點位的資料當中

<!-- >請直接將上傳成功的 disfactory.tw 網頁截圖上傳至此
>可以參考「講師示範交作業」：https://g0v.hackmd.io/dfqmJkn2Sem_Uqn-b6TIHQ -->

桃園市平鎮區違章工廠
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0c504e21565d306dc64430c7dd5f4d53.png)

## 筆記區

你的筆記區


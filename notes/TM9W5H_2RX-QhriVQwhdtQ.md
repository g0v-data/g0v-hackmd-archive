---
tags: GIS-edu-camp-2021-summer
---

# 地理資料與地圖課 - Chiao 作業區

好用連結
- 「講師」示範交作業：https://g0v.hackmd.io/dfqmJkn2Sem_Uqn-b6TIHQ
- 課程教材的整合網址：https://g0v.hackmd.io/@chewei/gis/
- 課程參與者．問答共享區，來看看大家的提問與討論 ➜ [頁面](https://g0v.hackmd.io/@chewei/gis-camp-work/)
- [「零時小學校 2021-22 Demo Day」徵件活動](https://sch001.g0v.tw/brd/sch001-2021) 💪

## 第一堂：地理資料與地圖課介紹 😎 

提醒：本次課程，講師有錄製「如何交作業」的影片，若不太清楚如何開始完成作業，可以適時參考影片內的操作過程哦 💪

### 作業一：請在「GIS 地理資料與應用」的資源共筆頁面，任意找一個線上主題地圖，描述與介紹地圖特色

網址: https://ivc.city/cn/blog/article/mayway
<iframe src="https://image4.thenewslens.com/2017/5/r4uavzxh6k09i55h6eg74cpmcu1u3i.jpg?auto=compress&q=80&w=1080" width= 100% height=300>
 </iframe>


描述: 情境式的城市路徑引導之〖雨天步行地圖〗
1. 顯示台北市裡能遮風避雨的半公共空間，例如騎樓、商業或服務業建築空間（例如商場通道）以及台北市捷運站出口附近的地下通道。我覺得在雨天步行地圖裡點出捷運出口是很棒的作法，因為以生活經驗而言，這是很常躲雨的半公共空間。下雨天若要搭乘大眾運輸工具，比起公車，確實更常選擇搭捷運。
2. 騎樓與商業建築使用紅色的圖例，搭配近乎白色的淺灰底，讓資訊一目瞭然，不過粉紅色塊狀的服務業空間以及黑色點狀的捷運出入口，相較之下視覺上的指引效果就不太清楚。另外，或許也是顏色選擇，地圖上的捷運站出口黑點讓我一開始閱讀時，不太能快速連結『捷運站出口』和『雨天步行路徑』之間的關聯。
3. 普遍來說，在雨天的台北市，沒帶傘的行人街道有可能沿著騎樓、商業或服務業建築空間或捷運站出口附近的地下通道，不狼狽地前往目的地。
4. 資料來源：
   * 由於沒有直接的騎樓資料，所以地圖裡的騎樓是挑選《104年度通用版電子地圖》圖資中的省道、市區道路、市區平面快速道路之道路邊線外 擴與建築範圍交集處
   * 商業區的資料來源可能是依據臺北市土地使用分區圖資或是臺北市商業處裡的商圈資訊和位置
   
### 作業二：請描述一個您近期想要建立的「主題地圖」，或是想要處理的「地理資料」，並請提供資料集的網址

我想要建立一個臺北市提供短期租借討論/活動空間的地圖
雖然google關鍵字『出租活動空間』，會出現許多資料或是空間媒合平台，但多半是個別空間（咖啡廳、以小時計費的場地）的使用心得或是表列式的清單，無法快速地用地圖指認出空間位置。我想要把活動空間的位置呈現在地圖上

目前找到的資料是一個（媒合？）平台：https://www.pickoneplace.com/search/program?uses=&max_people=1.20&county=&district=&maxHrPrice=&minHrPrice=&keywords=

* 格式：網頁上內文
* 處理方式：手動輸入（Python還沒熟練到爬蟲抓資料QQ）
* 需要先將現有的空間依照以下資訊列表：區位、空間名稱、地址、租金、聯絡方式

--> *接著找「地址 轉成 經緯度」的轉換工具*


## 第二堂：介紹線上協作地圖工具 👩‍💻 

提醒：本次課程，講師有錄製「如何交作業」的影片，若不太清楚如何開始完成作業，可以適時參考影片內的操作過程哦 💪

### 作業一：請創建一個資料地圖，並提供地圖網址。您可以挑選本次教學中介紹的地圖工具，並請提供您所使用的資料集來源網址

雙北地區短租的場地空間地圖
使用AwesomeTable 
<iframe src="https://app.awesome-table.com/-Mgzx-pcbRhEGyZ8z9Yu/view"width= 100% height=400>
 </iframe>
 
 
後台google spreadsheets網址:
https://app.awesome-table.com/-Mgzx-pcbRhEGyZ8z9Yu/edit

chewei> 主要是因為座標系統數字不是經緯度
TGOS 的地址轉座標服務，所轉換出來的座標結果，屬於「TWD97二度分帶座標」
Google 地圖能接受的座標，則是「WGS84經緯度座標」
所以需要再透過網頁工具，將「TWD97二度分帶座標」轉換至「WGS84經緯度座標」
例如 Fable/曼特您空間，的經緯度座標
緯度：25.044163545395957
經度：121.51353653799012
我把座標轉換的網頁工具，整理到以下共筆「地址轉經緯度」的頁面中，再請參考
https://g0v.hackmd.io/i6MO2ddVQ8iMy1jSp9vVog?view
另外，您的地圖嵌入的參數 height=80% 要不要改高一點或給 300 固定高度

Chiao>好的，已修改！感謝chewei~

### 作業二：您預計如何與其他人協作這個資料地圖？請描述協作的方式

這個專案我希望與其他人協作

* 主要是透過「spreadsheet 線上資料表」來協作
https://docs.google.com/spreadsheets/d/1C7lVwkfYabbvDaCLONMSkt3WbCMfp-CYghb_J099iho/edit#gid=398666375

* 可能的協作事項
    * 單一筆資料的修改、新增店家
    

## 第三堂：操作 BigGIS 衛星影像平台 🛰 與歷史照片定位平台

提醒：本次課程，講師有錄製「如何交作業」的影片，若不太清楚如何開始完成作業，可以適時參考影片內的操作過程哦 💪

- 作業一：熟悉 BigGIS 登入、搜尋圖資、調整與介面
- 作業二：學會操作 BigGIS 的輸出成 kmz 功能
- 作業三：瞭解 BigGIS 搜尋之事件點資料系統：歷史影像平台
- 擴充作業：學會使用 BigGIS 產生 gif 時間序列 ( 動態影像 )
- 擴充作業：使用 Windy 網頁，上傳探討範圍的地理框線資料 kml，瀏覽更多即時大氣氣象圖資效果 

### 作業一：熟悉BigGIS登入、搜尋圖資、調整與介面

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_17156a52c2db5890165f2b0558149842.png)





### 作業二：學會操作BigGIS的輸出成kmz功能

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_760c47e1e0825091b8882328f64a21df.png)



### 作業三：瞭解BigGIS搜尋之事件點資料系統：歷史影像平台
 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7ce3241849a9f54a15781cb8d457ade6.png)


### 擴充作業：學會使用BigGIS產生gif時間序列( 動態影像 )

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fbff5b41de581c361e1a2152901d0912.gif)


### 擴充作業：使用 Windy 網頁，上傳探討範圍的地理框線資料 kml，瀏覽更多大氣圖資效果 

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dd176bffdc28fd11ca15267750b0e49d.png)


## 第四堂：下載並操作 QGIS 軟體 ⚙ 

### 作業：也來輸出一個您製作的台灣鄉鎮男女比例地圖和鄉鎮老化地圖吧！

綠色區塊：女性多於男性的區域
橘色區塊：男性多於女性的區域

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9fc1da90f640825849ac8cb5528f5a64.png)


鄉鎮年齡地圖（中位數）
紫色越深的區塊：人口年齡越高

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_afb042e70c58ec524fcb599c510f3160.png)





## 第五堂：瞭解公民科技專案 🚀 Disfactory 農地違章工廠回報平台

提醒：本次課程，講師有錄製「如何交作業」的影片，若不太清楚如何開始完成作業，可以適時參考影片內的操作過程哦 💪

### 作業：找到一間離你最近的違章工廠，並將其不同年份的空拍圖放上 disfactory.tw 網站上，該點位的資料當中

新北市鶯歌區南靖里 南靖段 (1972) 07650000地號
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9a95d30f0d1dcaaba30127064f2ffd7a.png)




>請直接將上傳成功的 disfactory.tw 網頁截圖上傳至此
>可以參考「講師示範交作業」：https://g0v.hackmd.io/dfqmJkn2Sem_Uqn-b6TIHQ

## 筆記區




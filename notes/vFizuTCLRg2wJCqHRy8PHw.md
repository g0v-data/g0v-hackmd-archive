---
tags: GIS,
---

# 第一堂：地理資料與地圖課介紹

本次課程影片，共有三段：
- Part 1：地圖案例介紹 https://youtu.be/kCL2FsDHJKk
- Part 2：地理資料哪裡找？以及地理資料格式名稱簡介 https://youtu.be/vUYq5dUjd1g
- Part 3：本次作業繳交方式說明 https://youtu.be/spBAn5PWzFc

## 我們如何安排本次系列課程呢？

1. Intro 工具介紹：地圖案例、如何找資料、常見格式與轉檔工具資源、提問方法與頻道資訊
2. Data2Map 資料視覺化工具：介紹 GoogleMyMap、umap、Awesome-table、QGIS 軟體
3. Platform 影像型圖臺網站：介紹 BigGIS 衛星影像圖臺、歷史影像定位平台
4. Project 認識公民科技專案：以「Disfactory 農地違章工廠回報平台」為例

透過上述的課程，期待「您」也隨著每一堂課的作業，同步開始一個地理資料相關的提案構想，參加 8/14 夏日黑客松！以及下半年將啟動的[「零時小學校 2021-22 Demo Day」徵件活動](https://sch001.g0v.tw/brd/sch001-2021) 💪

本系列課程由 g0v 社群參與者 chewei、ronny、農委會水土保持局技術研發小組、Disfactory 農地違章工廠專案成員，共同製作與規劃，感謝講師群的參與及貢獻 🙏

---
## 什麼是地理資料？線上地圖有哪些案例呢？

這裡有蒐集各式各樣，運用地理資料製作主題地圖的案例
案例蒐集頁面：https://g0v.hackmd.io/@chewei/B1O2SOQ6d

## 地理資料集，要去哪裡找？

您可以使用「中文關鍵字」查詢以下資料平台

- 政府資料開放平臺 https://data.gov.tw/
    - **如果查不到相關的資料集，請前往「[政府資料開放平台-我想要更多](https://data.gov.tw/suggests)」向公部門提出詢問**，提問完畢後，通常經過數日後，平台會建立這次的發問的固定頁面網址。
    - 若不太清楚如何撰寫資料申請文句，您可以使用「申請文組合器」輔助小工具 by 資料申請小幫手：https://dataopener.tw/
- 社會經濟統計地理資訊網 https://segis.moi.gov.tw/stat/web/portal/stat_portalhome.aspx
- 國網中心資料集平台 https://scidm.nchc.org.tw/
- 民生公共物聯網資料服務平台 https://ci.taiwan.gov.tw/dsp/
- 中研院研究資料寄存所 https://data.depositar.io/dataset

「關鍵字」用詞提醒

- **相異名稱但概念資料集內容相近**，例如想要找美食店家的資料集，實際上不同的資料集，名稱用詞也不一樣，至少有「美食」、「餐飲」、「樂活名攤」等用詞。社群也持續 [共筆蒐集「相異名稱但概念內容相近」的資料集](https://g0v.hackmd.io/ebTWnDysQLy-6mScV4imKA)，歡迎分享您遇到的經驗。
- **業務領域的專業用詞**，例如若想了解住家附近的水溝分佈位置，使用「下水道」與「人孔」的業務領域的專業用詞，才會找到地理資料，比較口語的用詞如「水溝」、「水溝蓋」、「排水溝」則無法找到水溝分佈位置類的資料集。
- **如果查不到相關的資料集，建議您請前往「[政府資料開放平台-我想要更多](https://data.gov.tw/suggests)」向公部門提出詢問**，提問完畢後，通常經過數日後，平台會建立這次的發問的固定頁面網址，等待資料業務單位回覆是否開放此資料集的意見。若不太清楚如何撰寫資料申請文句，**您可以使用「申請文組合器」輔助小工具** by 資料申請小幫手：https://dataopener.tw/

不適用關鍵字查詢的地理資料資源

- OpenStreetMap 開放街圖
    - 您可以查看 [Map features 的清單](https://wiki.openstreetmap.org/wiki/Map_features)，了解「開放街圖資料庫」中目前已有的資料種類，例如學校、飲水機位置、步道路線..等
    - [使用 OverPass Turbo 資料查找工具，並搭配 Map features 標籤用詞進行查找](http://supaplex99.blogspot.com/2015/08/how-to-use-overpass-turbo-wizard-mode-to-extract-openstreetmap-data.html)
- 衛星影像來源盤點 [例如：SPOT 衛星影像、太空中心福衛衛星影像、正射影像航照、mapbox satellite 衛星圖資](https://g0v.hackmd.io/5QH2TlaXQR21wMo3UIKZug#%E5%90%84%E7%A8%AE%E5%9C%96%E8%B3%87%E4%BB%8B%E7%B4%B9)
- 立體三維國家底圖 https://3dmaps.nlsc.gov.tw/

## 常見簡稱：資料的格式、資料的取得方式、地理資料用語

這部分感謝台南女中三月份營隊場次的同學回饋，許多檔案格式、資訊的用語，經常以「英文縮頭字」來簡稱，以及這些縮頭字在口語上的唸法，無形中有點成為門檻，所以以下特別列出來在地理資料領域中，常見也的確會使用到的簡稱，也歡迎共筆新增。

### 資料格式

向量型 (點線面) 地理資料的格式縮寫
- **Vector** 向量資料
- **csv** = Comma-Separated Values
    - 口語唸法：CSV
    - 舉例：[台南美食店家，資料欄位：id,lang,name,summary,introduction,open_time,district,address,tel,fax,lat,long,services,category,consume,update_time](https://gist.githubusercontent.com/ronnywang/dcad38649aea12ee6271ca838722e3a9/raw/00963ed85ac29475dfbcc13a056f29c0e1f70104/food.csv)
    - 呈現在 [地圖上長這樣](https://www.google.com/maps/d/u/0/viewer?hl=zh-TW&mid=1f08BqdrZtJynrJvdo3-cIK6ZWwFeEjUJ&ll=23.09346245360912%2C120.50293220458866&z=10)
- **shp** = shapefile
    - 口語唸法：shapefile
    - Shp 格式案例，臺南市行政區範圍：http://bit.ly/3aWJrAP
    - 格式介紹：https://data.gov.tw/faqs/631
- **kml** = Keyhole Markup Language
    - 口語唸法：KML
    - 格式介紹：https://data.gov.tw/faqs/629
- **geojson** = Geo JavaScript Object Notation
    - 口語唸法：“geo-jason”，[🔊 點我聽聽看發音](https://youtu.be/wrEPpBbgFkQ?t=5)
    - 格式介紹：https://zh.wikipedia.org/zh-tw/GeoJSON
- **Polygon** = 面狀資料
    - 口語唸法：Polygon
    - 例如 村里的地理範圍，屬於 Polygon 面狀資料

網格型（衛星影像、立體三維度）地理資料的格式縮寫
- **Raster** 網格資料
- **Satellite Image** 衛星影像
- **福衛** = 福爾摩沙衛星
    - 介紹：https://www.nspo.narl.org.tw/photos_list.php?c=20011702&ln=zh_TW
- **遙測** = 遙感探測
    - 英文：Remote Sensing
    - 指的是從人造衛星或飛機對地面觀測所得到的光波資料
    - 介紹：https://twgeoref.moeacgs.gov.tw/GipOpenWeb/wSite/ct?xItem=140862&ctNode=1233&mp=105
- **航照** = 航空照片
- **UAV** = Unmanned Aerial Vehicle
    - 口語唸法：UAV
    - 中文俗稱：無人機、無人飛機
- **DTM** = Digital Terrian Model
    - 口語唸法：DTM
    - 格式介紹：https://twgeoref.moeacgs.gov.tw/GipOpenWeb/wSite/ct?xItem=140861&mp=105&ctNode=1233
- **DSM** = Digital Surface Model
    - 口語唸法：DSM

### 資料的取得方式與服務

資料的取得方式，也可以區分為
- **Raw Data** 原始資料檔案
- **API** = Application Programming Interface
    - 口語唸法：API
    - 法規上的用詞：[共通性應用程式介面](https://theme.ndc.gov.tw/lawout/LawContent.aspx?id=GL000270)
    - 案例：公共運輸整合資訊流通服務平臺 https://ptx.transportdata.tw/PTX/
- **WMS** = Web Map Service  /  **WMTS** = Web Map Tile Service
    - 口語唸法：WMS / WMTS
    - 中文用詞為「圖磚服務」
    - 案例：百年歷史地圖 http://gis.rchss.sinica.edu.tw/mapdap/?p=4151&lang=zh-tw
- **圖臺** = 圖資平臺
    - 僅能在網頁上用肉眼瀏覽資料
    - 案例：國土規劃地理資訊圖臺 http://nsp.tcd.gov.tw/ngis/ 

其他常見用語
- **layer** = 圖層
- **圖資** = 地圖資料（不是圖書館系的「圖資」系）

## 轉檔工具

蒐集各種工具的頁面：https://g0v.hackpad.tw/-Mapfessional-EJfaf9C5gaT

## 座標系統

摘：「台灣常聽到的 TWD67、TWD97、WGS84 等，都是大地基準，而經緯度、UTM (六度分帶)、TM2 (二度分帶) 、電力座標等，指的是座標格式。」
https://www.sunriver.com.tw/grid_tm2.htm

台灣常用的坐標系統及 EPSG 代碼
http://gis.rchss.sinica.edu.tw/qgis/?p=2823

## 運用共筆文件來整理問題、學習筆記

本系列課程的作業繳交方式，使用 hackmd 來作為您的個人作業區。

- 詳細步驟 https://g0v.hackmd.io/YV1nVGjaRd6BGqbAdK5SMg

遇到操作上的問題，可以把螢幕截圖，操作想法，整理在筆記中，分享至 #gis 頻道。常見的問題描述，期待能包含以下內容，方便社群朋友能了解您的疑問：
- 問題描述
- 螢幕截圖圖片
- 資料集使用來源網址
- 如果是線上地圖，也請提供此地圖的網址

討論請至 g0v slack #gis channel，加入方式 https://g0v.hackmd.io/@jothon/joing0vslack

---
# 作業區

1.請建立個人作業 hackmd 

- 詳細步驟，請至此份文件完成填寫：https://g0v.hackmd.io/YV1nVGjaRd6BGqbAdK5SMg

2.作業項目：本次講師影片中有操作步驟，可以邊看邊填寫。

- 作業一：請在「GIS 地理資料與應用」，任意找一個線上主題地圖
    - 您可以在左側導覽列，瀏覽以下頁面連結：
        - 地圖應用案例
        - 地點通報功能類的地圖
        - 全球或城市尺度的主題地圖
        - 衛星圖資應用案例
        - GIS 社會應用領域案例
    - 請瀏覽您所挑選的線上地圖案例
    - 請描述您所挑選的線上地圖案例，使用到哪些資料、使用者可以因此解決什麼問題或啟發，以及您的使用感想、為什麼挑選此份地圖來探索。

- 作業二：請想一個您近期想要建立的主題地圖，或是想要處理的地理資料
    - 請嘗試運用以下平台，查詢是否有相關的地理資料集，並將查到資料集網址，貼在自己的 hackmd 作業區。
        - 政府資料開放平臺 https://data.gov.tw/
        - 社會經濟統計地理資訊網 https://segis.moi.gov.tw/stat/web/portal/stat_portalhome.aspx
        - 國網中心資料集平台 https://scidm.nchc.org.tw/
        - 民生公共物聯網資料服務平台 https://ci.taiwan.gov.tw/dsp/
        - 中研院研究資料寄存所 https://data.depositar.io/dataset
    - 如果查不到相關的資料集，請前往「[政府資料開放平台-我想要更多](https://data.gov.tw/suggests)」向公部門提出詢問，提問完畢後，通常經過數日後，資料平台的管理單位，會建立這次的發問頁面網址，屆時請將提問網址貼回，您的作業 hackmd 頁面中。



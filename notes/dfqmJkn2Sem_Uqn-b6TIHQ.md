---
tags: GIS-edu-camp-2021-summer
---

# 地理資料與地圖 - 講師示範交作業 的作業頁面

教材與作業說明：https://g0v.hackmd.io/@chewei/gis/

## 第一堂：地理資料與地圖課介紹 😎

### 作業一：請在「GIS 地理資料與應用」的資源共筆頁面，找一個線上主題地圖，描述與介紹地圖特色

Earth 網頁網址
https://earth.nullschool.net/#current/wind/surface/level/orthographic=-238.08,25.05,1893

<iframe src="https://earth.nullschool.net" width=100% height="480"></iframe>



描述：
- 這個網頁很方便，一打開就看到氣象，而且還有氣流動畫
- 像是「颱風」就可清楚可以看到
- 用一個「地球」來呈現
- 資料集，使用大氣氣象資料
- 介紹頁面 https://earth.nullschool.net/about.html
- 網頁程式碼有 github github.com/cambecc/earth

### 作業二：請描述一個您近期想要建立的「主題地圖」，或是想要處理的「地理資料」，並請提供資料集的網址

我想要建立台南餐飲地圖

目前我有在政府資料平台上面，查到餐飲的地理資料集
- 台南餐飲店家資料：https://data.gov.tw/dataset/6184
    - 格式：csv
    - 欄位內有經度、緯度，可以用來地圖定位
- 低碳餐廳資料：https://data.gov.tw/dataset/7770
    - 格式：csv
    - 欄位：編號、區別、餐廳名稱、地址、電話
        - 沒有經度、緯度
        - ==需要找「地址 轉成 經緯度」的轉換工具==
- 臺南市餐飲衛生優良店：https://data.gov.tw/dataset/7627
    - 格式：csv
    - 欄位：年度、市招名稱、類別、區別、地址、等級、緯度、經度

目前想要把店家位置呈現在地圖上

## 第二堂：介紹線上協作地圖工具 👩‍💻 

### 作業一：請創建一個資料地圖，並提供地圖網址。您可以挑選本次教學中介紹的地圖工具，並請提供您所使用的資料集來源網址

台南餐飲地圖
- Awesome-table 網址：https://app.awesome-table.com/-Mf8N7UdBQLb9LPoxGiT/view
<iframe referrerpolicy="no-referrer-when-downgrade" width=100% height="600px" style="border:none;" src="https://view-awesome-table.com/-Mf8N7UdBQLb9LPoxGiT/view"></iframe>


資料
- 我使用台南餐飲店家資料：https://data.gov.tw/dataset/6184
- Awesome-table 的後台 spreadsheet 網址：
    - https://docs.google.com/spreadsheets/d/1Y40yyFHkjhAQBnGduLypfhH3I03n5FDneNFKEScAJK4/edit#gid=2112050738

TODO：預計進一步的工作事項
- 我接下來會預計把「台南餐飲店家資料、低碳餐廳資料、臺南市餐飲衛生優良店」三個資料先整合起來
    - 三個資料集欄位不太一樣
    - 要確認彼此資料集中，那些欄位是同樣的意思
    - 其中低碳餐廳要先把「地址轉成經緯度」才能夠定位，這個要去「轉檔工具頁面」找工具
- 我預計用「Awesome-table 地圖模式」來呈現店家位置
    - 預計可以讓頁面使用者，輸入關鍵字來篩選「店名」
    - 預計可以讓頁面使用者，選擇「行政區」來篩選呈現在這個行政區的店家

### 作業二：您預計如何與其他人協作這個資料地圖？請描述協作的方式

這個專案我希望與其他人協作
- 主要是透過「spreadsheet 線上資料表」來協作
    - https://docs.google.com/spreadsheets/d/1Y40yyFHkjhAQBnGduLypfhH3I03n5FDneNFKEScAJK4/edit#gid=2112050738
    - 可能的協作事項
        - 單一筆資料的修改、新增店家
        - 匯入更多的批次資料來源，例如 低碳餐廳、餐飲衛生優良店 資料集
        - 不確定能否開始有所謂的照片上傳？
- 地圖設計的協作
    - https://app.awesome-table.com/-Mf8N7UdBQLb9LPoxGiT/edit 
    - 我可以加入認識且有意願共同維護地圖的社群朋友 email 帳號，合作維護地圖樣式
    - 若有不認識的社群朋友，想要共同編輯地圖樣式，可以先寄送協作申請
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d11f61448d71f3f3945bdedbedfbaf19.png)

## 第三堂：操作 BigGIS 衛星影像平台 🛰 與歷史照片定位平台

- 作業一：熟悉 BigGIS 登入、搜尋圖資、調整與介面
- 作業二：學會操作 BigGIS 的輸出成 kmz 功能
- 作業三：瞭解 BigGIS 搜尋之事件點資料系統：歷史影像平台
- 擴充作業：學會使用 BigGIS 產生 gif 時間序列 ( 動態影像 )
- 擴充作業：使用 Windy 網頁，上傳探討範圍的地理框線資料 kml，瀏覽更多大氣圖資效果 

### 作業一：熟悉 BigGIS 登入、搜尋圖資、調整與介面

🔻 示範Google街道+衛星底圖
![](https://dm2306files.storage.live.com/y4mwJgH0eh3UM3S3fqZTNedSjiHsmgBma96ltmTNxZ0PRaE1E-aStxgkyzk-d97DxF6udjF2ADxWjNB-9SWMkunOR9U0e7f3dvYzAAErz14gNPdmpvHNSMjUO5qdzj29nJo-nzVY9Wz7rf3Dhxu4-ddfDQxeAIiJEhYU1Caof_hpKeXo6py7w-ggu_o97NyI_b0?width=1012&height=546&cropmode=none)
    
🔻 示範衛星圖+HOST地圖 
![](https://dm2306files.storage.live.com/y4mdwePhR5OEQi_ngc9a2dgHK1gBxjFrxIrBvDy87Xft8XZzzXuzk7gKkU0HY_gr4vDtx75Z3Rt8W64EcDKFFS66YcW3sIv-IQ93ttaGKNPKwMmA9W7AcsISLO6NLlbjwe_uNX934AJWeR-iIWCEI0A1S4qjDqMiMfkaGmsutkDpmRjMHpT7VEiSmix-C7TSp_z?width=1809&height=976&cropmode=none)
    
### 作業二：學會操作 BigGIS 的輸出成 kmz 功能

🔻 使用 Google Earth Pro 單機版軟體，打開 kmz 檔案
![](https://dm2306files.storage.live.com/y4m2xsWzHFRtHlPk5-dQIN7qsqf-G_uU9jqTpXfTdLVY7XHg6t3hBWa_CQZjw0--VnnPaHOV1AzJd6eGjWS73SDNgjxYi9Ii18G6wUazuk04FkuV3jzqT13MDd8c7arHOlQcOW9mUWR3TzOKzRN7L7JjuvDSql6UryDkl4E9je0tsFr2cuwUCisAvb1YlnO-m8z?width=729&height=435&cropmode=none)

### 作業三：瞭解 BigGIS 搜尋之事件點資料系統：歷史影像平台
 
![](https://dm2306files.storage.live.com/y4myLkkDRuZ2sOcKJ9977t1l4DeJaBX5GsNXkDvEAywyFPP-1iRCVrHFMmSLgDPb_QNGgqhexcVUn1acAeajYU6QJHYlul5SMKXFMERGkEdWQSrMaqKo59BVqJRIXB7lDURqIwLHQvI7xhmPqnXCo7D5TM0wcGHdYuj0Kl5dr3fVp_QiFWQPCB4dRf4ZtGnGLxP?width=816&height=440&cropmode=none)

### 擴充作業：學會使用 BigGIS 產生 gif 時間序列( 動態影像 )

🔻 Hackmd 頁面目前不支援 GIF 格式動畫，不會動~QQ
![](https://dm2306files.storage.live.com/y4mz8m_Izq87jB1AoNbbCjvQO2tn8EvQOIPyyNqnWfRs9B_WzuWitgP4obQHMHu1L2lY6txiJoLU_VxG0bQwjyBUXIrptc7qr_iOKW3yTGWhCgVa_tym2zT1BAkbdzftjz9p1_TtWoFWofnRPx0ZulbAdUpKgIXfM1xAeufvFKW7bvbdiqvr_RRW1gyzXoODYoT?width=586&height=725&cropmode=none)

🔻 Hackmd 頁面目前不支援 GIF 格式動畫，不會動~QQ
![](https://dm2306files.storage.live.com/y4mLGmbmv7NgmFSclL2DApeiUuJQQYKz-GI3RG-pLYraUjAuzyfcMDMWICStCyxBB4jR_S8YgYpNbWU-Ukh_f3l8qQQHhADjHGIbajNaQ7MQDDcrRGguQhRcxham19_2CLhzOy1QMhnAcyVIL_A6KRYLisVc2kndvWazWWz7hxQ6AhXMNH1WSxK1uNLooibkSyf?width=546&height=660&cropmode=none)


### 擴充作業：使用 Windy 網頁，上傳探討範圍的地理框線資料 kml，瀏覽更多大氣圖資效果 

🔻 示範：以桃園機場範圍為例
瀏覽網頁 https://www.windy.com/upload/61053b04af52330011e32478

![](https://dm2306files.storage.live.com/y4mh9EYxWXA-_bCX2aQ9kpcE5Uit3aWb9HZQGnwSRbbazNLI7mWYuzfbr3vgSd9AATQqpneF-WEQqqMcatT1zDkaXLz2qMP5b10kl4wxfseoUasmlkfYj3CN-diJ2uOtasHPGoKLUQq1P7r7uH6wGqNXHo_fJFW6EtABv3gAJoDwnjG0R1-RyqlxF1CE3KmlViI?width=898&height=486&cropmode=none)

![](https://dm2306files.storage.live.com/y4mc-Tx2k6Jz4hNQB173JjegVxN6Z7jAgMdGEkUJr4bWBJAm8hSxkoXWgD37Z3dtdvuJ7E-1DmzhJzo9XjvGMS0nESX52NzQmG-0YruvNBNXpD9u12bDtpMHzd5bd8te5R5p1HpGuvW9G-C_udvJD2F1w3CUFy13BzkgG67ryh58W8Z951GbqFiO5vfh_WKQOf1?width=1803&height=974&cropmode=none)


## 第四堂：下載並操作 QGIS 軟體 ⚙ 

### 作業：也來輸出一個你製作的台灣鄉鎮男女比例地圖和鄉鎮老化地圖吧！
如果有時間的話，你也可以找找看社會經濟資料庫，找找你有興趣的其他主題來作地圖吧（例如鄉鎮所得稅地圖？）
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9b44ab354e71af56107eec3fedcd8daf.png)


## 第五堂：瞭解公民科技專案 🚀 Disfactory 農地違章工廠回報平台

### 作業：找到一間離你最近的違章工廠，並將其不同年份的空拍圖放上 disfactory.tw 網站上，該點位的資料當中

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_06018570c1ab06efeaaa7f749d19e8bc.png)


---
# 筆記區

- 找找看 地址轉經緯度 的工具
    - https://g0v.hackpad.tw/EJfaf9C5gaT


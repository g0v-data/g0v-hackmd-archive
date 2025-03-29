---
tags: GIS
---

# 學校的位置 地理資料集－蒐集筆記

好用網址：
- 查資料 👉 政府資料開放平臺：https://data.gov.tw/
- 問資料 👉 向政府提出資料需求：https://data.gov.tw/suggests
- 討論區 👉 g0v slack #gis 頻道

---

## 請介紹您關心的資料內容，分享蒐集動機、用途構想

- 資料內容介紹：全國各種學校的分布位置
- 為什麼感興趣：我想製作線上的學校地圖


## 政府資料開放平臺，有沒有相關的資料集？

想要有全國的資料，但平臺上只找到 臺北市 的資料

- (1) 有的話，請貼上資料集的網址
    - 臺北市各級學校分布圖(含國小.國中.高中職.特教學校.市立大專院校) https://data.gov.tw/dataset/121225
    - 各級學校地理資訊及地區別統計查詢系統 https://stats.moe.gov.tw/edugissys/default.aspx
- (2) 並且從中找到可以定位在地圖上的欄位，像是「地址」、「經度 longitude」、「緯度 latitude」、「座標數字」、「地號」
    - 經緯度
    - 地址
- (3) 常見轉換工具與方法
    - [將「地址」或「座標」轉換成「經緯度」](https://g0v.hackmd.io/i6MO2ddVQ8iMy1jSp9vVog?view)
    - [將「地號」轉換成「地理資料」](https://g0v.hackmd.io/uFhBRHrnR-yvvFD4ZEn3XA)
- (4) 常見地理資料呈現工具
    - [Google My Map 線上地圖](https://g0v.hackmd.io/GYuf7PuJRCGDmFIpE8G27Q)
    - [Google Earth 立體地球的地理軟體](https://g0v.hackmd.io/O6NC1bKvQeGKXLiELbepKQ)
    - [QGIS 單機地理資料處理軟體](https://g0v.hackmd.io/AH6MEsSuSZ2pvxQIJld-Og)

目前進度：
- 不太確定要選用那些適合的地圖工具，才能製作出線上的學校地圖


## 如果政府資料平臺，沒有您想要的資料集 ...!

想找全國縣市的資料

- (1) 除了政府資料開放平臺，網路上有沒有相關的資料集？
    - 在「社會經濟統計資料庫」搜尋「校別概覽」可以找到學校資料，國小、國中、高中、大學分開提供，資料從 99 學年到 110 學年都有，TWD97 座標資訊
        - https://segis.moi.gov.tw/STAT/Web/Platform/QueryInterface/STAT_QueryInterface.aspx?Type=1
    - 109學年度各級學校分布位置，各級學校之點位分布圖，學校點位屬性有學校代碼、學校名稱、學校所在縣市名稱、學校地址、電話、網址等，提供 XY 座標
        - https://www.tgos.tw/TGOS/Web/Metadata/TGOS_MetaData_View.aspx?MID=404530389BCC15967ED8D58E129BC680&SHOW_BACK_BUTTON=false
    - 統計處的圖台，除了展示，也提供下載，不過只提供地址，沒有經緯度
        - https://stats.moe.gov.tw/edugis/default.aspx
    - 109學年度各級學校分布位置 from 國土空間資料目錄搜尋服務網
        - https://colab.ngis.org.tw/tgsearch/Query/Content/604982
- (2) 過去有沒有人向政府詢問過呢？
    - 可以到詢問區查查看：https://data.gov.tw/suggests
    - 2021 年度有人詢問過「各級學校分布位置」
        - https://data.gov.tw/suggests/136449
- (3) 如果都沒有人詢問過，建議您可以撰寫「資料需求申請」，可以使用「資料申請小幫手」，用步驟方式，協助您完成資料申請文字
    - https://dataopener.tw/
    - 再將文字內容，貼到政府資料開放平臺「我想要更多」的申請網頁
        - https://data.gov.tw/suggests
    - 我認為很值得再次詢問，特別是因為 2021 年度，已經表示出，教育部統計處是有資料的，希望可以把每一年度的更新資料，資料的下載網址也可以放到 政府資料開放平台，方便大眾直接整合搜尋


## 哪一個政府單位，是這個資料集的「主管機關」？

- 一般來說，政府資料平臺上面的回覆意見內容中，會提供「單位名稱與聯絡方式」
- 教育部統計處
    - 聯絡人：林育如；電話：(02)7736-6373


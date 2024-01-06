---
tags:
---

適合練習 OLAP 的開放資料集
====

Online analytical processing (OLAP) 
g0v slack #clickhouse


## 資料集
### [社會經濟資料庫](https://segis.moi.gov.tw/STAT/Web/Portal/STAT_PortalHome.aspx)
- 資料下載: https://lydata.ronny-s3.click/segis.zip
- 檔案大小: 2.9G, 資料筆數約 2億954萬筆、2464 個資料集
- 資料內容:
    - categories.json 資料集的介紹
        - 欄位: MID, name, count, time_start, time_end, bounds, geotypes, columns
        - MID: 資料 ID ，會對應到 output/data_{MID}.csv
        - name: 資料集中文名稱，Ex: 戶籍動態遷出、遷入、出生、死亡、結婚、離婚
        - count: 資料筆數
        - time_start: 資料開始時間，以 YYYYMM 為單位
        - time_end: 資料結束時間，以 YYYYMM 為單位
        - bounds: 資料地理範圍，可能是「全國」或是「xx縣」、「xx市」
        - geotypes: 包含的地理資料層級
            - x_y: 經緯度
            - U01CO: 縣市
            - U01TO: 鄉鎮
            - U01VI: 村里
            - U0202: 二級統計區
            - U0201: 一級統計區
            - U0200: 最小統計區
        - columns: 裡面對應的欄位中文名稱
    - data/data_{MID}.csv
        - 資料內容
### [台灣高速公路交流道流量資料](https://tisvcloud.freeway.gov.tw/)
### [台北捷運進出口人數](https://data.gov.tw/dataset/128506)
### 歷史地震資料
### 氣象資料
### 電力資料
### [PTT 歷史人氣資料](https://ptthot.ronny.tw/)
### [選舉資料](https://db.cec.gov.tw/ElecTable)
- 成果： [打包檔資料](https://lydata.ronny-s3.click/votedata.zip)
    - 產生時間 2023-07-27
    - 資料組成：
        - cand.csv 13M 93671 筆資料
        - vote.csv 396M 4390225 筆資料
    - 欄位介紹
        - cand.csv
            - 選舉名稱,縣市,姓名,省市別,縣市別,選區別,鄉鎮市區,村里別,號次,政黨,性別,出生日期,年齡,出生地,學歷,現任,當選註記,副手
        - vote.csv
            - 選舉名稱,縣市,姓名,省市別,縣市別,選區別,鄉鎮市區,村里別,投開票所,得票數
    - 使用注意事項
        - 「選舉名稱,縣市,姓名」 三個欄位可以跟 政治獻金的 「選舉名稱,縣市,參選人」 欄位結合
        - 尚未處理國大代表、省議員、不分區、省長、補選等資料
        - 「選舉名稱,縣市,姓名」 並非唯一，約有 171 人重名，不過如果只是要跟政治獻金比對的話，只有 107 年村里長和鄉(鎮、市)民代表選舉有部份重覆姓名的問題（村里長：臺北市洪美惠、桃園市陳秀菁、新北市黃永昌、鄉民代表：彰化縣 陳文明、宜蘭縣 張榮華）
### [政治獻金申報資料](https://ardata.cy.gov.tw)
- 成果： [收入資料](https://lydata.ronny-s3.click/incomes.csv) [支出資料](https://lydata.ronny-s3.click/expenditures.csv)
    - 產生時間：2023-07-27
        - 資料狀況：incomes.csv 86MB 507548 筆, expenditures.csv 182M 989648 筆
    - [舊] 產生時間： 2023-05-29
        - 資料狀況：incomes.csv 67MB 399767 筆, expenditures.csv 128M 704649 筆
### 實價登錄資料
### 土地使用資料（公告地價、土地使用...)
### 進出口資料
### 公司資料產業別（經濟部、財政部)
---
title: "data.fda.gov.tw 應用"
tags: hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/OPiwIhTl684)

## Datahub

repo:
- [https://github.com/kiang/drugs](https://github.com/kiang/drugs)  ( website
- [https://github.com/kiang/data.fda.gov.tw](https://github.com/kiang/data.fda.gov.tw)((data mirror from [http://data.fda.gov.tw/](http://data.fda.gov.tw/)

目前資料集 lists [https://github.com/kiang/data.fda.gov.tw/blob/master/list.csv](https://github.com/kiang/data.fda.gov.tw/blob/master/list.csv)
Add 15 datasets on 2014.12.24 [http://data.fda.gov.tw/frontsite/news/newsAction.do?method=doNewsDetail&contentId=70](http://data.fda.gov.tw/frontsite/news/newsAction.do?method=doNewsDetail&contentId=70)

## 應用

- 根據每週更新資訊, 查看藥品價格異動情形 ; 可做成time-serieus
    - \[藥品健保藥價資料集\] [https://github.com/kiang/data.fda.gov.tw/blob/master/dataset/74.csv](https://github.com/kiang/data.fda.gov.tw/blob/master/dataset/74.csv)
- 根據每週更新資訊, 查看每週是否有原廠藥品離開台灣
    - \[全部藥品許可證資料集\] [https://raw.githubusercontent.com/kiang/data.fda.gov.tw/master/dataset/36.csv](https://raw.githubusercontent.com/kiang/data.fda.gov.tw/master/dataset/36.csv)
- 根據open.fda.gov 提供的"藥物副作用"及"藥物交互作用"資料, 將藥物查詢連結出去
    - new pad => : [https://g0v.hackpad.com/72TVP8zYYfs](https://g0v.hackpad.com/72TVP8zYYfs)
- 違規食品標示資料集(5.csv) + ronnywang 的公司登記資料
- 基因改造食品原料資料集(1.csv) 但是不知道哪裡可以找哪些下游廠商買了這些產品
- 疫苗 [http://data.fda.gov.tw/opendata/exportDataList.do?method=ExportData&InfoId=102&logType=1](http://data.fda.gov.tw/opendata/exportDataList.do?method=ExportData&InfoId=102&logType=1)

### 全部藥品許可證資料集( id=36 )

> 應該是主資料集(?
> [name=lanfon]

> 裡面資料有單行較長的情況，目前測試用長度 5000 才有辦法順利抓到每一筆資料
> [name=Finjon K]

- frequency: weekly
- columns:
> 粗體表示該欄位一定有資料（目前）
> [name=Finjon K]

> 許可證字號 有可能重複，~也許是到期後重新申請~，所以[需要注意](https://github.com/kiang/drugs/issues/4)
> [name=Finjon K]

> [單一藥證字號會因為包裝大小對應到不同的健保碼(id=74)](https://github.com/kiang/drugs/issues/3)
> [name=Finjon K]

    - **許可證字號**
    - 註銷狀態(空白、已註銷、已廢止)
    - 註銷日期
    - 註銷理由
    - **有效日期**
    - 發證日期
    - **許可證種類**  (製　劑, 原料藥, 試劑體外用, 衛生材料, 硬空膠囊, 菌　疫, 體外試劑)
    - 舊證字號
    - 通關簽審文件編號
    - 中文品名
    - 英文品名
    - 適應症
    - 劑型
    - 包裝
    - 藥品類別 ( 須由醫師處方使用, 製劑原料, 醫師藥師藥劑生指示藥, 限由醫師使用, 自用製劑原料, 指示用藥, 須經醫師指示使用, 由醫師或檢驗師使用, 醫師藥師藥劑生指示藥品, 調劑專用, 牙醫師指示使用, 本藥限神經專科醫師使用, 限由牙醫師使用, 限由醫師及牙醫師使用, 限由眼科醫師處方使用, 成藥, 乙類成藥, 本藥須由醫師處方使用, 限由婦產科醫師使用, , 原料藥, 限麻醉醫師使用, 甲類成藥, 原料藥(製劑中間體), 限由中醫師處方使用, 空膠囊, 調劑專用製劑 )
    - 管制藥品分類級別 (第四級管制藥品, 取消管制藥品註記, 第三級管制藥品, 第二級管制藥品, 第一級管制藥品)
    - 主成分略述
    - 申請商名稱
    - 申請商地址
    - 申請商統一編號
    - 製造商名稱
    - 製造廠廠址
    - 製造廠公司地址
    - 製造廠國別 (JAPAN, POLAND, MEXICO, UNITED KINGDOM, SWITZERLAND, UNITED STATES, ITALY, GREECE, FRANCE, KOREA, GERMANY, SPAIN, DENMARK, NETHERLANDS, CANADA, INDONESIA, AUSTRALIA, BRAZIL, SWEDEN, HUNGARY, CYPRUS, AUSTRIA, NEW ZEALAND, IRELAND, PUERTO RICO, FINLAND, BELGIUM, SINGAPORE, ISRAEL, BULGARIA, YUGOSLAVIA, TAIWAN, ARGENTINA, PHILIPPINES, INDIA, NORWAY, TURKEY, BAHAMAS, SLOVENIA, PORTUGAL, CZECH REPUBLIC, PANAMA, ICELAND, SOUTH AFRICA, LUXEMBURG, HONG KONG, IRAN, THAILAND, MALAYSIA, ROMANIA, VIET NAM, , PERU, EGYPTI, SLOVAKIA, CHINA, MAURITUS, COLOMBIA, LATVIA, BERMUDA, COSTA RICA)
    - 製程
    - **異動日期**
    - 用法用量
    - 包裝
    - 國際條碼
### 未註銷藥品許可證資料集( id=37)

- frequency: weekly
- columns: 同 id=36 ，是子資料集。

### 藥品外觀資料集( id=42 )

- frequency: weekly
- columns:
    - 許可證字號
    - 中文品名、英文品名
    - 形狀、特殊劑型、顏色、特殊氣味、刻痕、外觀尺寸
    - 標註一、標註二、**外觀圖檔連結**
> 只有部份有提供圖檔 link
> [name=lanfon]

### 藥品詳細處分成分資料集( id=43 )

- frequency: weekly
- columns:
- problems
    - [藥品詳細處分成分資料集 公開資料範圍提問](https://g0v.hackpad.tw/PxFQRRwEzg8#藥品詳細處分成分資料集-公開資料範圍提問)
### 藥品健保藥價資料集 ( id=74 )

- frequency: weekly
- columns:
    - **許可證字號**
    - 健保代碼
    - 規格量
    - 規格單位
    - 起期
    - 終期
    - 參考價
> 目前解 csv 看到的總資料筆數是 129027 筆，但內容包含過往的歷史資料：
> [name=lanfon]

```
許可證字號                 健保代碼         規格量  規格單位   起期            終期           參考價
.....(前略)
衛署藥輸字第022951號        B022951100                        0891201        0900331        20.90
衛署藥輸字第022951號        B022951100                        0900401        0920228        19.90
衛署藥輸字第022951號        B022951100                        0920301        0951031        18.40
衛署藥輸字第022951號        B022951100                        0951101        0960831        17.00
衛署藥輸字第022951號        B022951100                        0960901        0980930        15.50
衛署藥輸字第022951號        B022951100                        0981001        1001130        12.10
衛署藥輸字第022951號        B022951100                        1001201        1030630        9.90
衛署藥輸字第022951號        B022951100                        1030701        9991231        8.90
```
> 簡單來說呢就是.... 抓一個 .zip檔 ( xml 33MB > json 23MB > csv 8MB ) 來整理就可以產圖(?)了XD
> [name=lanfon]

> 但不方便的是 因為它更新是 weekly 且 包含歷史資料 ，也有可能 內容沒有更動 ，做更新的時候很不方便QQ
> [name=lanfon]

> (規格量 & 單位 還蠻多是空值，分隔符號是 tab )
> [name=lanfon]


```
許可證字號                 健保代碼         規格量  規格單位   起期            終期           參考價
內衛藥製字第000847號       N000847500                        0981001         0981130        2.34
內衛藥製字第000847號       N000847500                        0981201         9991231        0.00
內衛藥製字第000847號       N000847500                        0981201         1000331        2.34
```
> parse 的時候會遇到的狀況(_參考上圖)，展期(調藥價)的時候一般是終期 +1 day = 次起期 (參考上上圖) ，上圖出現的情況可能是....=_= 我也不知道 ，有可能是資料殘缺(但還蠻多參考價是 0.00 ....)__~，或是~__~和前一次的藥價相同，純展期~__~。~_
> [name=lanfon]

> 經由 pofeng 解釋，**參考價 = 0.00 表示健保不提供給付**。
> [name=lanfon]

> ~另外就是，我有用已註銷的許可證號搜過幾筆，沒有找到資料.... 可能是已註銷的藥品不列出藥價。~
> [name=lanfon]

> 無法從是否出現在 藥價資料集 中判定是否已註銷.....(已註銷的有幾筆沒搜到 但也有發現已註銷但有藥價)
> [name=lanfon]


### 監視中 藥品名單(id=55)

- frequency: 不定期
- columns:
    - **許可證字號**
    - 發證日
    - 商品名
    - 許可證持有者
    - 監視終止
- data:
    - json: [http://data.fda.gov.tw/opendata/exportDataList.do?method=ExportData&InfoId=55&logType=3](http://data.fda.gov.tw/opendata/exportDataList.do?method=ExportData&InfoId=55&logType=3)
    - csv: [http://data.fda.gov.tw/opendata/exportDataList.do?method=ExportData&InfoId=55&logType=2](http://data.fda.gov.tw/opendata/exportDataList.do?method=ExportData&InfoId=55&logType=2)
    - xml: [http://data.fda.gov.tw/opendata/exportDataList.do?method=ExportData&InfoId=55&logType=1](http://data.fda.gov.tw/opendata/exportDataList.do?method=ExportData&InfoId=55&logType=1)

## 資料集整理

```
url: data.fda.gov.tw/frontsite/data/DataAction.do?method=doDetail&infoId={id}
replace {id} as below.
```
### 藥品相關

| id | title | frequency |  |
| --- | --- | --- | --- |
| 34 | 回收藥品資料集 | 不定期 |  |
| 35 | 藥局基本資料 | 不定期 |  |
| 36 | 全部藥品許可證資料集 | 每週 |  |
| 37 | 未註銷藥品許可證資料集 | 每週 |  |
| 38 | 藥品CCC號列資料集 | 每週 |  |
| 39 | 藥品仿單或外盒資料集 | 每週 |  |
| 40 | 藥品藥理治療分類AHFS/DI碼資料集 | 每週 |  |
| 41 | 藥品藥理治療分類ATC碼資料集 | 每週 |  |
| 42 | 藥品外觀資料集 | 每週 |  |
| 43 | 藥品詳細處分成分資料集 | 每週 |  |
| 53 | 藥品安全資訊風險溝通資料 | 不定期 | partial |
| 54 | 須執行藥品風險管理計畫藥品名單 | 不定期 |  |
| 55 | 監視中藥品名單 | 不定期 |  |
| 65 | 消費紅綠燈-國際藥品 | 不定期 |  |
| 66 | 藥品法規條文資料集 | 不定期 |  |
| 74 | 藥品健保藥價資料集 | 每週 |  |
### 食品相關

| id | title | frequency |
| --- | --- | --- |
| 1 | 基因改造食品原料資料集 | 不定期 |
| 2 | 基因改造食品原料英文資料集 | 不定期 |
| 3 | 食品添加物許可證資料集 | 不定期 |
| 4 | 可供食品使用原料彙整一覽表 | 不定期 |
| 5 | 違規食品標示資料集 | 不定期 |
| 6 | 中華民國廚師證書資料集 | 不定期 |
| 7 | 優良廚師資料集 | 不定期 |
| 8 | 衛生講習課程資料集 | 不定期 |
| 9 | HACCP課程資料集 | 不定期 |
| 10 | 餐飲業優良業者名單資料集 | 不定期 |
| 11 | 嬰兒配方食品及較大嬰兒配方輔助食品資料集 | 不定期 |
| 12 | 動物用藥殘留標準資料集 | 不定期 |
| 13 | 農藥殘留容許量標準_農藥殘留容許量標準 | 不定期 |
| 14 | 農藥殘留容許量標準_得免訂定容許量之農藥一覽表 | 不定期 |
| 15 | 農藥殘留容許量標準_公告禁用農藥一覽表 | 不定期 |
| 16 | 農藥殘留容許量標準_農作物類農產品之分類表 | 不定期 |
| 17 | 餐飲業食品安全管制系統衛生評鑑證明廠商資料集 | 不定期 |
| 18 | 食品業者登錄資料集 | 不定期 |
| 19 | 健康食品資料集 | 不定期 |
| 20 | 食品營養成分資料集 | 不定期 |
| 21 | 市售食品調查蔬果農藥殘留資料集 | 不定期 |
| 22 | 違規食品廣告資料集 | 不定期 |
| 23 | 輸入錠狀膠囊狀食品查驗登記資料集 | 每天 |
| 24 | 國產維生素類錠狀膠囊狀食品資料集 | 每天 |
| 25 | 真空包裝黃豆即食食品查驗登記資料集 | 不定期 |
| 28 | 餐盒食品工廠實施HACCP符合性稽查名單 | 不定期 |
| 52 | 不符合食品資訊資料集 | 不定期 |
| 60 | 食品法規條文資料集 | 不定期 |
| 61 | 食品添加物使用範圍及限量暨規格標準資料集 | 不定期 |
| 62 | 消費紅綠燈-國際食品資料集 | 不定期 |
| 63 | 病人用特殊營養食品許可資料集 | 不定期 |
| 64 | 健康風險評估資料集 | 不定期 |
### 化妝品

| id | title | frequency |
| --- | --- | --- |
| 72 | 含藥化粧品詳細處方成分資料集 | 每週 |
| 73 | 含藥化粧品詳細處方成分資料集 | 每週 |
| 73 | 含藥化粧品仿單或外盒資料集 | 每週 |
### 管制藥品

| id | title | frequency |
| --- | --- | --- |
| 46 | 各年度各業別領有管制藥品登記證統計資料集 | 每一年 |
| 47 | 各年度專門職業別領有使用執照統計資料集 | 每一年 |
| 48 | 藥物濫用者常見之術語資料集 | 不定期 |
| 49 | 藥物濫用諮詢及輔導機構資料集 | 不定期 |
| 50 | 常見濫用管制藥品資料集 | 不定期 |
| 51 | 銷售管制藥品一覽表 | 不定期 |
### 醫療器材

| id | title | frequency |
| --- | --- | --- |
| 68 | 醫療器材許可證資料集 | 每週 |
| 69 | 醫療器材詳細處方成分資料集 | 每週 |
| 70 | 醫療器材仿單或外盒資料集 | 每週 |
### 實驗室認證

| id | title | frequency |
| --- | --- | --- |
| 56 | 藥物非臨床試驗優良操作規範認證通過單位資料集 | 每3個月 |
| 57 | 認可濫用藥物尿液檢驗機構名單資料集 | 每半年 |
| 58 | 藥物化粧品認證實驗室名單資料集 | 每3個月 |
| 59 | 食品認證實驗室名單資料集 | 每月 |
### 風險管理

| id | title | frequency |
| --- | --- | --- |
| 29 | GMP製造許可廢止資料集 | 不定期 |
| 30 | GMP證明書註銷資料集 | 不定期 |
| 31 | GMP藥廠名單資料集 | 不定期 |
| 32 | 通過PIC/S GMP評鑑之國內藥廠名單資料集 | 不定期 |
| 44 | 國外工廠GMP核備事項註銷 | 不定期 |
| 45 | 嚴重違反GMP藥廠 | 不定期 |
| 67 | 人體器官保存庫許可資料集 | 不定期 |
> 請問可以加入你們嗎
> [name=Yiwen Y]

> 請直接於 irc 上 tag kiang XD
> [name=lanfon]

> [Finjon Kiang](https://g0v.hackpad.tw/ep/profile/G4yGGowBe3x) 請問可以加入你們嗎
> [name=Yiwen Y]

> 透過 [http://g0v-slack.herokuapp.com/](http://g0v-slack.herokuapp.com/) 加入聊天群組吧 ，大概 30 分鐘內收到信吧
> [name=Finjon K]



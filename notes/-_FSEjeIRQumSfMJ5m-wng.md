---
title: "開放資料新聞產生器"
tags: hackpad
---

# 開放資料新聞產生器

> [點此觀看原始內容](https://g0v.hackpad.tw/SfuUIP4TA80)


> 感謝 whisky 提供「開放資料新聞產生器」這個新專案名稱 XD
> [name=Poga P]


## 專案簡介



### [https://speakerdeck.com/poga/xin-wen-chan-sheng-qi](https://speakerdeck.com/poga/xin-wen-chan-sheng-qi)


### 預定使用者

資料提供者、資料分析者

### 預定功能

自動分析資料內容，抓出可以簡單呈現的部分：
- 排序：最新、最大、最多
- 地圖：地點、地址、座標
- 推論資料型態/欄位規則：哪些欄位可能是 tag、可能是 pkey、可能是 ISO-3316-1(?)
- parse utility:
    - time parser
    - what is pkey?
> primary key XD
> [name=Poga P]

> 哈, 不是啦, 我是說可以寫個功能是找出pkey
> [name=stardog]

> 喔喔～ :+1:
> [name=Poga P]



### 現有類似專案

google fusion table
[https://support.google.com/docs/answer/6280499?hl=en](https://support.google.com/docs/answer/6280499?hl=en)
[http://sheethub.com](http://sheethub.com)

### 相關專案

[https://g0v.github.io/color/](https://g0v.github.io/color/)
dbpedia
schema.org

### 授權方式

程式：MIT
其他：CC-BY?

### 使用資料


### 專案目前狀態

[http://github.com/](http://github.com/g0v/datasmith)[g](http://github.com/g0v/datasmith)[0](http://github.com/g0v/datasmith)[v](http://github.com/g0v/datasmith)[/datasmith](http://github.com/g0v/datasmith)
toolchain:
[https://github.com/poga/postabular](https://github.com/poga/postabular)

## 實作細節（非技術背景可跳填）


### 協作工具

- github repo：[http://github.com](http://github.com/g0v/datasmith)[/](http://github.com/g0v/datasmith)[g](http://github.com/g0v/datasmith)[0](http://github.com/g0v/datasmith)[v/datasmith](http://github.com/g0v/datasmith)
- hackfoldr 工作資料夾網址：
- google drive 共用資料夾網址：

### 進度與 to-do

> 處理資料囉唆到腦羞，所以跑去先做了方便處理 tabular data 的 [https://github.com/poga/postabular](https://github.com/poga/postabular)
> [name=Poga P]



## 過去討論紀錄

### 欄位類型判斷方式


### 台灣地區名稱

- 判斷方式：判斷欄位內容是否出現台灣縣市名，或是地區名
- 參考資料集：
    - [https://github.com/](https://github.com/g0v/datasmith/blob/master/cities.csv)[g](https://github.com/g0v/datasmith/blob/master/cities.csv)[0](https://github.com/g0v/datasmith/blob/master/cities.csv)[v](https://github.com/g0v/datasmith/blob/master/cities.csv)[/datasmith/blob/master/cities.csv](https://github.com/g0v/datasmith/blob/master/cities.csv)
    - [https://github.com/](https://github.com/g0v/datasmith/blob/master/areas.csv)[g](https://github.com/g0v/datasmith/blob/master/areas.csv)[0](https://github.com/g0v/datasmith/blob/master/areas.csv)[v](https://github.com/g0v/datasmith/blob/master/areas.csv)[/datasmith/blob/master/areas.csv](https://github.com/g0v/datasmith/blob/master/areas.csv)
    -
- 原始資料來源：
    - [http://www.post.gov.tw/post/internet/Download/all\_list.jsp?ID=2201#dl\_txt\_s\_A0206](http://www.post.gov.tw/post/internet/Download/all_list.jsp?ID=2201#dl_txt_s_A0206)

甲殼類名稱
- 判斷方式：判斷欄位內容是否出現甲殼類名稱
- 參考資料集：
        - [https://sheethub.com/cloud.culture.tw/%E5%85%B8%E8%97%8F%E7%9B%AE%E9%8C%84-%E7%94%B2%E6%AE%BC%E9%A1%9E](https://sheethub.com/cloud.culture.tw/%E5%85%B8%E8%97%8F%E7%9B%AE%E9%8C%84-%E7%94%B2%E6%AE%BC%E9%A1%9E)




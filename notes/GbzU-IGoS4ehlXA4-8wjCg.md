---
title: "數位化關心台灣之ＮＪ議員"
tags: hackpad
---

# 數位化關心台灣之ＮＪ議員

> [點此觀看原始內容](https://g0v.hackpad.tw/PEor2yrY7tH)

CongressmanProTaiwan


## 專案簡介


### 緣由

海外台灣青年陣線NJ分會，每兩個月在Princeton進行outreach介紹台灣的活動。常常會遇到當地居民與旅客的支持，但他們都會詢問他們可以對台灣做些什麼。因此我們想統整當地議員對台灣關心程度之數位化，提供當地居民作為未來選舉之參考。並且設計一個網站提供支持者填寫姓名，與自動寄發郵件至當地議會，讓議會知道當地居民都對台灣的關心。

### 要解決的問題

1.  將對台灣議題關心之議員的資料數位化，並且提供選民上網觀看與查詢。
2.  設計一個頁面提供支持者填寫，與寄發email至其相對應選區的議員，以表示對台灣的支持與關心。


### 預定使用者

1.  第一階段為NJ選民，與對台灣事務關心民眾。
2.  Outreach的民眾們。

### 第一次會議

1.  構想

2.  資料來源 （links)
    (a) [Inside government](http://www.insidegov.com/)
    (b) [Library congress](https://www.loc.gov/)  [https://www.loc.gov/](https://www.loc.gov/)

3.  資料輸入
請參考[Excel](https://drive.google.com/file/d/0B8sd_gjSmw9Xd2dJak83SDAtSW8/view?usp=sharing)檔
    (a) 選區list zipcode （已完成）

    (b) 法案Bill List, assign tags
    根據法案 在 [Library congress](https://www.loc.gov/)裡搜尋 h.r. 法案名稱 or s.r. 法案名稱
    Ex. h. r. taiwan United Nation
    法案每兩年重新一次 （法案通過門檻需要半數通過）

    (c) Congressman list (select選區, 法案, assign tags)



### 專案目前狀態

1.  構想與設計中
2.  資料數位化進行中
3.  research on website environment setup




## 徵求協作者


發起人/拋磚人：
- [ ] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
- [x] NeedsDesigner: 需要介面設計
- [x] NeedsData: 需要資料（擷取、清理）
- [x] NeedsTech: 需要技術支援（程式、架站 etc)
- [ ] NeedsProcess: 需要幫忙設計作業流程
- [ ] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡


## 實作細節（非技術背景可跳填）


### 協作工具

- github repo：
- hackfoldr 工作資料夾網址：
- google drive 共用資料夾網址：

### 進度與 to-do

> 僅供參考
> [name=ET B]

- [x] product planning（recommanded procedure from justin lee / 李易修）
    - [x] strategy
    - [x] scope
    - [x] structure
    - [ ] wireframe
    - [ ] visual
- [ ] web front-end
- [ ] web back-end
- [ ] ui / visual design

### 網站功能

- 輸入
    - import csv
    - add edit delete 選區、法案、議員資料
- 瀏覽
    - enter zip code -> 顯示該zip code對應的議員summary
    - 議員detail
    - (?) issue list/search
    - (?) congressman list/search


### REST API Design discussion

1\. For most GET tables request, service just return list of objects (each object is a row in table),
2\. one to many relation:
(ex:issue list)
\[
{
    "id": 1
    "name":"Issue 1",
    "desc":"Desc",
    "tags":\[ "tag1", "tag2", "tag3"\]
},
...
\]
3\. For reference table (OBJ_NAME, CODE, NAME), it's better to return JSON in this format:
\[
{ "objectName": "ATTITUDE",
    "values: " \[
        {"code": "P", "name": "Pro"},
        {"code": "N", "name": "Neutral"},
        {"code": "A", "name": "Against"},
    \]
},
{ "objectName": "ISSUE_TYPE",
"values: " \[
    {"code": "N", "name": "News"},
    {"code": "B", "name": "Bill"}
\]
},
...
\]
4\. API List
\- GET district list
\- GET issue list
\- GET congressman list
\- GET references

### Open PostgreSQL data

- public REST API
- Export data in PostgreSQL and let people download them?

## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）

1\. Whiteboard
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7e1a2c8cc44f5d0f9940e33fd71780e6)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_20d984acb5b01160e4f8a7cace479016)

2\. 資料輸入細節
    (a) 先使用excel整理資料
    (b) 第一列留白
    (c) row based
    (d) 同一cell複數資料時，輸入時請用,  (comma+space)
    (e) 輸出成csv給程式處理

3\. 環境建置&討論
\- node.js + expressjs + PostgreSQL
\- heroku
\- SQL schema draft
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c0bb6356ed12a60a77e13deb0598466d)
Front-end TODOs:
1\. 輸入資料介面
2\. import csv檔介面
3\. presentations


問題:
1\. 各網站或資料來源 選區對應的zipcode不一致

This pad text is synchronized as you type, so that everyone viewing this page sees the same text.  This allows you to collaborate seamlessly on documents!



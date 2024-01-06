---
title: "d|Bootcamp Taipei 共筆 - 穿越時空的資料新聞呈現 - 簡介與工具介紹"
tags: hackpad
---

# d|Bootcamp Taipei 共筆 - 穿越時空的資料新聞呈現 - 簡介與工具介紹

> [點此觀看原始內容](https://g0v.hackpad.tw/UyLQKR5IsrI)

時間：2015/08/21 11:00 ~ 12:00
講者：黃雋 / 財團法人開放文化基金會董事

## 行前準備：

#### 安裝 Chrome Plugin:

[https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc?hl=zh-TW](https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc?hl=zh-TW)

準備好Google帳號 [http](https://accounts.google.com/)[s://accounts.google.com/](https://accounts.google.com/)
準備好 Twitter 帳號(選擇性): [http://twitter.com/](http://twitter.com/)

## 簡報：




Story Map 特性
- 把事件用地理位置呈現
- 分享網址 "index.html" 改成 published.json，可以看到輸入的資料
- 沒有協作的功能
- 取得經緯度
    - google map 右鍵 > 這是哪裡，就會出現
    - OpenStreetMap > 分享，一邊移動，經緯度會更新

運用時間軸講故事
- UDN 做了不錯的示範，但是沒有辦法知道他想要說什麼故事



## 練習：如何把資料變成故事？


### 工具

Story Map [http://storymap.knightlab.com](http://storymap.knightlab.com)
Timeline.js [http://timeline3.knightlab.com/](http://timeline3.knightlab.com/)
OpenStreetMap [http://openstreetmap.tw/](http://openstreetmap.tw/)

### 範本：

Timeline.js範本：
    官方：
        [https://](https://s3.amazonaws.com/uploads.knightlab.com/storymapjs/1df87fe6b955bd14fbc06b41aba7d96a/my-front-page/index.html)[s3.amazonaws.com/uploads.knightlab.com/storymapjs/1df87fe6b955bd14fbc06b41aba7d96a/my-front-page/index.html](https://s3.amazonaws.com/uploads.knightlab.com/storymapjs/1df87fe6b955bd14fbc06b41aba7d96a/my-front-page/index.html)
    ImportHTML載入本課程範本：
        =ImportHTML("[https://docs.google.com/spreadsheets/d/1Pf1CXqrxFJyPsYJN6lMOEwy5aIrVBcksSxjOL7ui35o/pubhtml](https://docs.google.com/spreadsheets/d/1Pf1CXqrxFJyPsYJN6lMOEwy5aIrVBcksSxjOL7ui35o/pubhtml)","table",1)

載入遠端範本：
1.  打開 Google Sheet
2.  新增\[工作表 2\]
3.  貼入下面文字在儲存格
4.  =ImportHTML("[https://docs.google.com/spreadsheets/d/1Pf1CXqrxFJyPsYJN6lMOEwy5aIrVBcksSxjOL7ui35o/pubhtml](https://docs.google.com/spreadsheets/d/1Pf1CXqrxFJyPsYJN6lMOEwy5aIrVBcksSxjOL7ui35o/pubhtml)","table",1)
5.  成功載入遠端表格後，複製想要的內容（行）
6.  在\[工作表1\]，右鍵 > 選擇性貼上 > 僅貼上值

### 主題

可使用下列主題，但不限於下列主題

成果/概況/調查
- 台灣選舉歷史： [http://zh.wikipedia.org/wiki/臺灣選舉](http://zh.wikipedia.org/wiki/臺灣選舉)
- 食品安全： [http://zh.wikipedia.org/wiki/](http://zh.wikipedia.org/wiki/台灣食品安全事件列表)[台灣食品安全事件列表](http://zh.wikipedia.org/wiki/台灣食品安全事件列表)
    - [https://docs.google.com/spreadsheets/d/1Pf1CXqrxFJyPsYJN6lMOEwy5aIrVBcksSxjOL7ui35o/edit#gid=1293825551](https://docs.google.com/spreadsheets/d/1Pf1CXqrxFJyPsYJN6lMOEwy5aIrVBcksSxjOL7ui35o/edit#gid=1293825551)

競選行程：
- 連勝文： [https://www.youtube.com/results?search_query=%E9%80%A3%E5%8B%9D%E6%96%87%E5%BE%AE%E8%A1%8C%E7%A8%8B%E8%A8%98%E9%8C%84](https://www.youtube.com/results?search_query=%E9%80%A3%E5%8B%9D%E6%96%87%E5%BE%AE%E8%A1%8C%E7%A8%8B%E8%A8%98%E9%8C%84)
- 林佳龍： [http://hope2014.citylove.org.tw/itinerary.php](http://hope2014.citylove.org.tw/itinerary.php)

事件：
- 關達那摩： [https://zh.wikipedia.org/wiki/关塔那摩湾拘押中心](https://zh.wikipedia.org/wiki/关塔那摩湾拘押中心)
    - 自動擷取 [http://](http://fact.g0v.tw/wikipedia/关塔那摩湾拘押中心)[f](http://fact.g0v.tw/wikipedia/关塔那摩湾拘押中心)[act.g0v.tw/wikipedia/关塔那摩湾拘押中心](http://fact.g0v.tw/wikipedia/关塔那摩湾拘押中心)
    - JSON [http://fact.g0v.tw/wikipedia/关塔那摩湾拘押中心](http://fact.g0v.tw/wikipedia/关塔那摩湾拘押中心.json)[.json](http://fact.g0v.tw/wikipedia/关塔那摩湾拘押中心.json)
- 課綱微調： [https://zh.wikipedia.org/wiki/臺灣高中歷史課綱微調案](https://zh.wikipedia.org/wiki/臺灣高中歷史課綱微調案)
    - 自動擷取 [http://fact.g0v.tw/wikipedia/](http://fact.g0v.tw/wikipedia/臺灣高中歷史課綱微調案)[臺灣高中歷史課綱微調案](http://fact.g0v.tw/wikipedia/臺灣高中歷史課綱微調案)
    - JSON [http://fact.g0v.tw/wikipedia/](http://fact.g0v.tw/wikipedia/臺灣高中歷史課綱微調案.json)[臺灣高中歷史課綱微調案](http://fact.g0v.tw/wikipedia/臺灣高中歷史課綱微調案.json)[.json](http://fact.g0v.tw/wikipedia/臺灣高中歷史課綱微調案.json)


## 成果：

第一組：

第二組：

第三組：

第六組：

第十組：


---
tags: Disfactory
---

# 第三十五次黑客松－違章工廠舉報系統

小海，小胖，泉潽，書伯，容瑜，IU，Andy，Sandra，(RonnyWang)
[群組連結LINE](https://line.me/R/ti/g/Nv4GshVo87)

相關連結
---
[第35次黑客松提案簡報內容](https://drive.google.com/file/d/1MB3xjIwZd8NbgH39ax6ojsy76HjaN6Rh/view)
[舉報GOOGLE表單原型](https://docs.google.com/forms/d/e/1FAIpQLSessybSBIFZlkN2IkjBEmEjTSrK4hH4sg5kNHiA-yf1QUWh-g/viewform?fbzx=-5342634387030643664)


主題
---
前言

國家永續發展來自有規劃的空間秩序，國土計畫即台灣國土規劃的最上位政策。農地興建違章工廠是破壞國土秩序的明顯實例。本提案希望最低限度能完成一個便於舉報違章工廠的系統，協助公民團體重建農地秩序。但也希望在過程中能集結各地關心空間秩序的民眾，投入規劃各縣市國土計畫。

開發緣由

工輔法修法內容未加入公民訴訟，缺少實質監督工具。公民團體嘗試「集結個案與民意壓力」，逼迫政府認真執法。藉由有效地收集舉報個案，匯成公文發送至各地政府並定期追蹤，定時召開記者會監督執法進度。

| 預定使用者 | 檢舉者（農民...） | 公民團體（地球公民基金會） |
| -------- | -------- | -------- |
| 預定功能   | 降低報案技術門檻   | 大量資料整理成公文

## 檢舉資料使用流程

1.`檢舉者備齊資料`

地點資訊

* 縣/市/鄉/鎮/市/區
* [地段/地號](https://easymap.land.moi.gov.tw/R02/Index#) 

土地用途

* [都市計畫地區（農牧用地）/非都市土地（一般農業區&特定農業區）](http://nsp.tcd.gov.tw/ngis/)
* [都市計畫使用分區 （農業區等等）](http://tinyw.in/CrMe) 
> [name=海] 第二個連結好像打不開


照片

* 照片檔案
* 污染標記(optional)
* 污染標記的說明(optional)

2.`CET內部審核`
3.`CET發出公文`

## 產品開發到舉報整體流程

1.**建立第一代的資料庫**
透過資料比對輸入第一批記錄們

2.**新增資料的方式（使用者介面）**
輸入一筆完整記錄、補齊不完整紀錄

申報功能開發

| 八月 | 九月 | 十月 |十一月 |十二月 |
| -------- | -------- | -------- |-------- |-------- |
| wireframe完成     | 開發網頁     | 開發網頁     |倒資料，邀請第一波試用    |修正＋公布   |

([什麼是wireframe](https://kopu.chat/2017/06/22/wireframe%e3%80%81mockup%e8%88%87prototype%e7%9a%84%e5%b7%ae%e7%95%b0%ef%bc%9f%e4%be%86%e7%9c%8b%e7%9c%8b%e5%ae%8c%e6%95%b4%e7%9a%84%e7%94%a2%e5%93%81ui%e8%a8%ad%e8%a8%88%e6%b5%81%e7%a8%8b/))



3.**內部管理紀錄**
排出場勘行程

4.**公文自動化**
寄出
狀態追蹤






## 資料盤點

* 農委會：國土測繪雲的農業工廠圖層及背後資料
* 江明宗：國土巡守隊
* 環境資訊中心：13萬筆稅籍資料

圖層比較流程：
1.從[國土測繪中心](https://maps.nlsc.gov.tw/)
2.比較[農業及農地資源盤查=>農地資源盤查_工廠](https://wmts.nlsc.gov.tw/wmts/FARM07/default/EPSG:3857/15/14163/27357)是紅色
3.比較[土地圖層 => 非都市土地使用分區圖](https://wmts.nlsc.gov.tw/wmts/nURBAN/default/EPSG:3857/16/28271/54731)是黃色（特定農業區）和橘色（一般農業區）

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_96819a590fd0f19d6f226a9b3944bad9)


###### 江明宗大補帖 [國土巡守隊]

國土巡守隊是一個參與總統盃社會創新黑客松的主題，2018.05.19
簡報： https://kiang.github.io/pdf/20180519.pdf
實做介紹： https://www.youtube.com/watch?v=JmxFhvGzw6E
線上展示： https://kiang.github.io/lands_patrol/
開發程序：https://g0v.hackpad.tw/0NkW64xhg7g
開放資料：http://bit.ly/317rxmZ
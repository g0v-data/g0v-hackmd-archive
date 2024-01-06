---
tags: 標案資料, 開放標案
---

# 開放標案

> [點此觀看原始內容](https://g0v.hackpad.tw/LV55tyn5uYK)

## 專案簡介

### 專案說明

標案資訊來源是 [http://web.pcc.gov.tw/](http://web.pcc.gov.tw/) 的**公開招標**的標案資訊。
> 招標方式還有限制性招標、公開取得等等…
> [name=喵喵]


　　透過分析政府得標案資料，重新用另一種方式呈現，讓除了需要招標的廠商外，一般民眾也能比較容易的了解政府機構在招標與決標的資訊。

**發起人/拋磚人**：
[mlwmlw](https://mlwmlw.org)  mlwmlw.org@gmail.com
#### 專案網址：

- 網站：[http://pcc.mlwmlw.org](http://pcc.mlwmlw.org)
- github：[https://github.com/mlwmlw/pcc](https://github.com/mlwmlw/pcc)

## 目標與功能

前陣子九合一選舉，看見新聞上報導台南的市政經費不停被縮減，但是還是能在各方面發展沒有太大影響。所以這系統應該能用來幫助大家分辨這種情況，是否會因為執政黨或多數黨，使資源集中在少數的縣市，這也是在評斷一個縣市發展的面向。或者有哪些單位執行上發生許多障礙，其實是沒有得到足夠的經費挹注造成的，就能瞭解有哪些單位需要大家更多的關注。

　　招標資料裡面主要有分成招標、決標、機構、廠商的資料，除了可以更簡單的不需要知道太多知識，就能查詢檢索，也想依照特定目的提供一些統計的功能，讓民眾可以更了解政府的預算，大致都怎麼花，花在什麼項目上，是否有圖利特定廠商的問題存在。

　　成為社會議題討論時的輔助工具。

## 要解決的問題

原本的標案系統是給廠商用的，需要一個系統讓一般民眾也想要用的。

讓公民都能知道我們繳納的稅金都實際花在什麼上面

### 相關專案

[g0v-pcc 標案](https://hackpad.com/ep/pad/static/0M0HW9tSVNQ)：g0v 關於政府標案的討論，延續原本 g0v 的標案專案的討論，透過已經有系統的雛型，來進一步想像實際應該要實現的功能。
- [https://github.com/jeffhung/g0v-pcc](https://github.com/jeffhung/g0v-pcc)
- [https://github.com/tka/g0v-pcc/tree/master/ruby-pcc-parser](https://github.com/tka/g0v-pcc/tree/master/ruby-pcc-parser)
- [https://github.com/tka/pcc-web](https://github.com/tka/pcc-web)

[https://dsp.hackpad.com/DSP--LeuLSqRENDp](https://dsp.hackpad.com/DSP--LeuLSqRENDp) DSP 標案松

### 授權方式

MIT

### 專案目前狀態

？

## 徵求協作者

發起人/拋磚人：
分工與成員
- [ ] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
- [ ] NeedsDesigner: 需要介面設計
- [ ] 檢查資料正確性
- [ ] 實作新功能
- [ ] 設計與規劃需求

### idea Pool

- 標案履歷，每個標案都應該有個人頁
    - 無法決標的歷史，
        - 轉貼自 hackpad> 無法決標的理由很多種，這個議題很有趣，如果加註預算金額不符合市場期待，承辦人應該會被檢討預算是否被低估或是預算根本亂編。
    - 該廠商相關的標案、名稱類似或分類相同（財務類）
        - 轉貼自 hackpad> 後續如果弄個承包商標案地理圖資系統，繪製承包工程位置 ，應該可以看到特別的事情(地緣關係)
    - 得標的廠商分析
    - 使用者的留言與討論，被使用者關注的次數與評比
    - 讓使用者得以用人肉分析標案是否有特殊性（因為還無法自動尋找）
        - 轉貼自 hackpad> 這超棒
    - 能順便在首頁做個隨選標案，隨機在使用者面前曝光，得以被觀察與評論「你很奇怪欸、沒什麼特別阿、可疑歐」之類的選項。
- 匯入廠商的董監事資料可增加分析的關聯性
    - [https://www.dropbox.com/sh/42oyn4ustp4ilhy/FRQA56UbG0](https://www.dropbox.com/sh/42oyn4ustp4ilhy/FRQA56UbG0) 資料來源
    - 已經匯入廠商資料，增加廠商的所屬類型跟董監事資料，機構頁可以列出相關的關係人
    - 發現廠商資料有些錯誤需要在整理（統編錯誤）
> api：company.g0v.ronny.tw ？
> [name=喵喵]


> 相關網站:[http://gov.playgroup.com.tw/](http://gov.playgroup.com.tw/)
> [name=Richard H]

- 標案頁可以加入投標廠商嗎？感恩！這樣也許比較能夠去看這個標案的競爭情況

### 實作細節

- backend：node.js(koa、express、LiveScript)
- frontend：bootstrap、angularjs、c3js
- database：mongodb
- cache：redis

### issue

- mongodb 的全文檢索沒有支援中文，目前搜尋時好時壞
- web 用 koa 寫 node 要加 --harmony 才能跑，api 用 LiveScript 配 express 寫
- 目前 server.ls 跟 web/index.js 分兩個 port 要自己用 proxy 串起來才會動（囧）
    - 建一個 domain
    - web 介面要接到 domain/
    - api 要 proxy 到 domain/api
- 專案待整理成適合協作…

## 成果展示

[https://pcc.mlwmlw.org](https://pcc.mlwmlw.org)
- 各月機構招標金額統計（Line chart、Pie chart) [http://pcc.mlwmlw.org](http://pcc.mlwmlw.org)
- 各月廠商得標金額與數量排行榜 [http://pcc.mlwmlw.org/rank/merchant](http://pcc.mlwmlw.org/rank/merchant)
- 當月專案招標金額排行 [http://pcc.mlwmlw.org/rank/tender](http://pcc.mlwmlw.org/rank/tender)
- 廠商列表 [http://pcc.mlwmlw.org/merchants](http://pcc.mlwmlw.org/merchants)
- 機構列表 [http://pcc.mlwmlw.org/unit](http://pcc.mlwmlw.org/unit)
- 招標 [http://pcc.mlwmlw.org/date/tender](http://pcc.mlwmlw.org/date/tender)
- 決標 [http://pcc.mlwmlw.org/date/award](http://pcc.mlwmlw.org/date/award)
- 搜尋 [http://pcc.mlwmlw.org/search/懷孕](http://pcc.mlwmlw.org/search/懷孕)


---
title: "動民主家族 The Don-eDemocracy Family"
tags: 動民主,hackpad
---

# 動民主家族 The Don-eDemocracy Family

> [點此觀看原始內容](https://g0v.hackpad.tw/Ra62eyV02sC)

加入動民主專案群方式請見 [動民主家族 \- 如何加入](https://g0v.hackpad.tw/--MwaV1CXeobT)

動民主起源於台灣綠黨網路支黨部的一份研究，探討德國海盜黨 Liquid Feedback (LQFB) 流動民主系統的機制。爾後，g0v 社群將 LQFB 系統翻譯成中文，並取名為動民主。隨著相關需求出現，逐漸發展成龐大的專案群。動民主專案群可歸類為三大區塊：網路民主研究、外國平台本地化、以及程式開發。

動民主家族 2013/05 - 2015/05 發展史可參考 COSCUP 演講： [http://etblue.blogspot.tw/2015/08/coscup-40.html](http://etblue.blogspot.tw/2015/08/coscup-40.html)

## 網路民主研究與資料收集

講座、讀書會、人體試驗等，詳[動民主 lab](https://g0v.hackpad.com/-lab-BBRFMB6Ptw6)

### 網路民主相關平台列表（歡迎補完）

台灣連署資源運籌平台
希望地圖
善蟻雄兵
Google 好問
市長給問嗎
議員給問嗎
割闌尾計畫
潑辣瘋人
聯合公民

### 可能作為動民主開發資料來源的平台列表（歡迎補完）

立委投票指南
議員投票指南
口袋國會
393
iVoter

## 外國平台本地化

更多相關或類似平台詳 [動民主 2.0 設計概念 - 相關系統超級比一比](https://g0v.hackpad.tw/-2.0--Y5f4w3JWs2Y)

### LQFB / PRFB

德國海盜黨開發的程式，直接拿來中文化
[http://hack.g0v.tw/don-democracy/Bee14qTnjgX](http://hack.g0v.tw/don-democracy/Bee14qTnjgX)
特色：介面很醜
狀態：上線中 [http://lqfb-test.g0v.tw/pf/](http://lqfb-test.g0v.tw/pf/)
窗口：
- 程式：clkao, au
- 翻譯：ipa, clkao, au
- 架站：clkao
- 擴充：pm5
需要：目前無特殊需要

### Adhocracy

德國人（？）開發的系統，介面清爽宜人，和 LQFB 一起被 charles 發現，但 2014 年中才有沒有人有力氣幫它中文化
- [https://greenpartytaiwan.adhocracy.de](https://greenpartytaiwan.adhocracy.de)
- 中文介面出現了！有問題的話除了寫信過去 adhocracy-dev@lists.liqd.net ，還可以找 clkao 代轉

### Airesis

義大利人另外開發出來的系統，功能類似 PRFB，直接拿來中文化（範例是 [http://www.airesis.eu](http://www.airesis.eu) 嗎？）（現在官方有放中文版了，雖然搞錯域名… [http://www.airesis.cn](http://www.airesis.cn)）
[http://hack.g0v.tw/don-democracy/lhUMItDUIZw](http://hack.g0v.tw/don-democracy/lhUMItDUIZw) （這裡點進去..沒東西？）（改網址了 XD）
特色：介面可愛，人見人愛
狀態：已翻譯完成，架站測試中
窗口：
- 程式：yhsiang, dylandy
- 翻譯：ttcat, au
需要：
- rails 架站資源
    - [x] wildjcrt++, poga++, 幫忙 yhsiang 架公開測試站 @ heroku

### Loomio

au 新發現的由佔領華爾街衍生而來的社團內部決議系統，適合討論組織內部事務
[https://www.loomio.org/groups/2958](https://www.loomio.org/groups/2958)
狀態：試用中，想用的人可以向原開發者自告奮勇幫忙翻譯
[https://github.com/loomio/loomio](https://github.com/loomio/loomio)
翻譯平台：[http://goo.gl/gO72wo](http://goo.gl/gO72wo)

## 程式開發


### 動民主 1.0

重新設計 PRFB 的介面
[http://hack.g0v.tw/](http://hack.g0v.tw/don-democracy/sonS8O8jEzU)[don-democracy](http://hack.g0v.tw/don-democracy/sonS8O8jEzU)[/sonS8O8jEzU](http://hack.g0v.tw/don-democracy/sonS8O8jEzU)
特色：全部按照 android 設計標準，看起來就很宅
狀態：設計到一半停住不動中 [http://yhsiang.github.io/angular-lqfb-redesign/#/](http://yhsiang.github.io/angular-lqfb-redesign/#/)
窗口：
- 程式：yhsiang
- 文件：ETBlue
需要：
- web designer
    - [ ] 把目前設計延伸到其他頁面
    - [ ] 改良目前設計

### 動民主 0.5

[http](http://bindo.la/)[://bindo.la/](http://bindo.la/)
[https://github.com/g0v/donvote](https://github.com/g0v/donvote)
將動民主投票功能獨立抽出來，並快速實做完成。
程式：tkirby

### 動民主 2.0

補足動民主 1.0 缺乏的大型議題分析功能，以 QA + 腦力激盪便利貼的方式
[http://hack.g0v.tw/don-democracy/iTXM54EBWVo](http://hack.g0v.tw/don-democracy/iTXM54EBWVo)
特色：畫了很多 mockup
狀態：規劃 \+ prototype 中 [http://g0v.github.io/don-republic-mockup/public/](http://g0v.github.io/don-republic-mockup/public/)
窗口：
- 程式：tkirby, hcchien, dirty
- 文件/企畫：ETBlue, simon pai
- 砍柴：ronnywang
使用技術：
- 前端
    - sass + compass + jade
    - semantic ui
    - fire.app
- 後端
    - python + django 但聽說 tkirby 想換新的後端玩
- angular? firebase? angularfire? fortran? go?
需要：
- data
    - [ ] 世界奇觀 tag 資料集 - 要什麼請 ronnywang 幫忙抓 XD（新年松時凹到的）包括政府部門、企業財團、國家、地區、族群、學術分類……等各式各樣的標籤系統，用途是內建在動民主中變成預設標籤，在使用者輸入標籤時可以給予建議或可以 auto complete，還可以用來過濾使用者感興趣的內容，只要訂閱父標籤，可以自動包含子標籤。或者也許可以應用在分類搜尋功能

### 動民主 1.337

將動民主 2.0 依照使用情境拆解成小 app 以方便開發、觸及不同族群的使用者
[ 2.0 apps](https://g0v.hackpad.tw/iBRhXaRlfZh)
#### 1.337 - 全民記者會

特色：跟沃草的「市長給問嗎」專案幾乎重疊
狀態：mockup [http://g0v.github.io/don-press/public](http://g0v.github.io/don-press/public)
窗口：
- 企畫：ETBlue
 使用技術：
-  前端
    - sass + compass + jade
    - semantic ui
    - fire.app
- 後端
需要：
- TXT編輯群政見小幫手
- 後端程式
- 架站
#### 1.337 - 零時廣場






### 應用範圍


由公民形成政策
- [鏡子政府](https://glassy.hackpad.com/4DiyGdSb7xE)  ( 透明黨的外部連結，裡面有概念，也有一些政策共筆的demo可以先忽略，目標是「工具開放源碼，內容是創用CC，任何人都可以主動參與，參與產生的內容也註明來自該專案本身而非「g0v 政策、g0v 共識」，那就像是維基百科一樣」 )


[#動民主](https://g0v.hackpad.tw/ep/search/?q=%23%E5%8B%95%E6%B0%91%E4%B8%BB&via=Ra62eyV02sC)


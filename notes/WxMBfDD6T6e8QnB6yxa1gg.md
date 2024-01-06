---
title: "動民主 1.0 介面設計 Pirate Feedback UI Redesign"
tags: hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/sonS8O8jEzU)

專案介紹 | Project Readme / Meta


[動民主介面改版之前端工程卡關搶救計畫 \- hackth4n 專用頁面](https://g0v.hackpad.tw/k0GhzNzPTyW#%26%2321205%3B%26%2327665%3B%26%2320027%3B%20angular%20js%20%26%2321069%3B%26%2331471%3B%26%2324037%3B%26%2331243%3B)
這次 8/10 黑客松的東西先放上面這個文件（因為主要 focus 在 angular 怕整個貼落落長），之後再合併進來原本這邊
> 我後悔了，應該一開始就放同一份文件才對 QQ
> [name=ET B]



## 來龍去脈（想解決什麼問題）


主旨
- pirate feedback 是一套開源碼的民主倡議與表決系統，目前已中文化並使用中。但介面讓使用者難以接受，所以需要重新設計。

牽涉領域
- 基礎建設

現有類似專案
- [動民主 2.0（壹民主 / 全民踹共 / 零時國會 / ... 名稱未定） ](http://hack.g0v.tw/meta/iTXM54EBWVo) 新版動民主還在早期規劃階段，在那之前，我們需要先讓第一版動民主可以上線使用，到時候再轉換過去

相關組織單位
- g0v

相關專案
- pirate feedback 是 liquid feedback 的改良版

授權方式
- 源碼：
- 視覺設計：CC0

使用資料

相關資訊
- 台德義 edemocracy 討論群組 - [https://groups.google.com/forum/#!forum/e-dem](https://groups.google.com/forum/#!forum/e-dem)
- 動民主 1.0 與 2.0 專案發展過程 - [https://docs.google.com/presentation/d/1kA3jf0pQbPF87mRidkp0ChlAiztGw8eOYYTasfU0yQ0/edit?usp=sharing](https://docs.google.com/presentation/d/1kA3jf0pQbPF87mRidkp0ChlAiztGw8eOYYTasfU0yQ0/edit?usp=sharing)

專案目前狀態
- 雛形


## 目標與功能（要如何解決）


預定使用者
- 一般上網族群，非資訊宅

預定功能
- 同 pirate feedback，只是介面重新整理

使用方式
- desktop / mobile


## 實做細節（非技術背景可跳填）


使用技術
- angular js
- jade
- sass

協作工具
- hackfoldr 工作資料夾網址：[http://hack.g0v.tw/meta/sonS8O8jEzU](http://hack.g0v.tw/meta/sonS8O8jEzU)
- github repo：[https://github.com/Mec-iS/angular-lqfb-redesign](https://github.com/Mec-iS/angular-lqfb-redesign)

產出檔案格式
- html / css / js

### 進度與 to-do

- [x] ui / visual design
- [x] 需要重新套版至 angular js

### 現有成果

- pirate feedback 系統原貌 [http://lqfb-test.g0v.tw/](http://lqfb-test.g0v.tw/pf/)[pf/](http://lqfb-test.g0v.tw/pf/)
- 系統分析文件 [https://docs.google.com/folder/d/0B0NsS2a-Qx8ZN3dBc3F2R2dzUzg/edit?docId=1UrC-s\_SA70JbxdcaOlOxuVTJ3i9USA\_pMnRI2OZ6s5k](https://docs.google.com/folder/d/0B0NsS2a-Qx8ZN3dBc3F2R2dzUzg/edit?docId=1UrC-s_SA70JbxdcaOlOxuVTJ3i9USA_pMnRI2OZ6s5k)
- 介面設計圖稿 [https://docs.google.com/folder/d/0B0NsS2a-Qx8ZV0ZGVEJLRHUtSk0/edit](https://docs.google.com/folder/d/0B0NsS2a-Qx8ZV0ZGVEJLRHUtSk0/edit)
- 第一版 html / css mockup [http://g0v.github.io/pirate\_feedback\_ui_redesign/](http://g0v.github.io/pirate_feedback_ui_redesign/)
- 由義大利的朋友 Lorenzo 將前後端改成 angular js - [https://github.com/Mec-iS/angular-lqfb-redesign](https://github.com/Mec-iS/angular-lqfb-redesign)
- [Yuan Hsiang Cheng](https://g0v.hackpad.com/ep/profile/FurgGRVDQsl) 套好了 [http://yhsiang.github.io/angular-lqfb-redesign/app/#/](http://yhsiang.github.io/angular-lqfb-redesign/app/#/)
-


## 開發者


技術指導
- 阿修

分工與成員
- 初版 UI 與 mockup - ETBlue
- angular js 前端工程 - [Pomin Wu](https://g0v.hackpad.com/ep/profile/oGf5HRRuJSf),  [Yuan Hsiang Cheng](https://g0v.hackpad.com/ep/profile/FurgGRVDQsl)
- 初版 UI 改良 - （請簽名）


## 開發手札


### 前端工具集

mobile web
[Quick Start Guide to PhoneGap+AngularJS](http://devgirl.org/2013/06/10/quick-start-guide-phonegap-and-angularjs/)
[phonegap](https://github.com/phonegap) / [phonegap-app-anyconference](https://github.com/phonegap/phonegap-app-anyconference)
[http://nativedroid.godesign.ch/demo/index.html](http://nativedroid.godesign.ch/demo/index.html)
[Topcoat](http://topcoat.io/) \- CSS for clean and fast web apps.
色盲友善色票 [http://colorbrewer2.org/](http://colorbrewer2.org/)
[讓 Fire.app 支援 Jade 的方法](https://g0v.hackpad.com/FK7eBR4BdAj#讓-Fire.app-支援-Jade-的方法)

### irc 暫存區

        au        發現 jQuery Mobile 有 holo 的 skin
 [http://nativedroid.godesign.ch/](http://nativedroid.godesign.ch/)
很擔心prfb的網頁版爆炸慢
所以要包成 app 啊
據說 web app 也要全部先 render 出來，只是讓 view 疊在一起，然後在互動時調換 layer 順序？
不然用 toggle display 一樣會 render 很久...
是的，jQuery mobile 正是這樣
app 的好處只是所有的 view 一次在安裝時下載完了
（而安裝時使用者的耐心比平時好很多）
那麼議案清單需要分頁嗎？還是一直往下捲捲捲... 據說 js 不清記憶體的，捲到後面會爆炸慢 orz
我覺得如果同時進行的議案不太多
=看歷史議案不是常態
=有需要時(捲到後面)再載入 = 就還好。
也有怎麼樣都卷不完，但是每次只 render 出一些資料的方法喲
聽說叫做 grid



---
title: "2015 WWViews ＠ TW 跨國審議/投票系統專案"
tags: hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/W6l1GtZ3l1A)

2015.04.18 提案簡報

[http://www.slideshare.net/luchiahua0515/20150418-g0v2015-wwviews-in-taiwan](http://www.slideshare.net/luchiahua0515/20150418-g0v2015-wwviews-in-taiwan)


## 01\. 緣由（背景資訊）


台灣民間響應2015年氣候與能源世界公民高峰會 (World Wide Views on Climate and Energy)，發起在地活動，讓台灣公民也能參與全球性的能源政策制訂。活動過程中，為了讓資訊流順暢、讓討論效果可以擴散到論壇以外的廣大的網路世界，需要打造對應的資訊工具，且希望這些工具將來能廣泛應用到各種類似的場合，讓往後的參與式民主，變得更有效率、更容易執行。
[WWViews 簡介](https://2015wwvintw.hackpad.com/WWViews--ABZp775fMbT)

## 02\. 專案簡介


### 1) 要解決的問題

（解釋上次的 WWViews 遇到什麼問題，是需要資訊系統來解決）
上次09年，根本沒有太多想法，光是team building，完整run好一次就阿密陀佛了！這次才有長進與精力進一步處理**『會議紀錄資料視覺化 \+ 投票結果資料視覺化』**
> 我自己是希望在  上 ET 下Blue 法師在憲動盟草根論壇經驗之上，2015wwviews在這個基礎上，往前再跨越！
> [name=Chia L]


### 2) 預定使用者

所有參與者。

### 3) 專案說明 (= 預定功能)

希望能有一個台灣網站，它裡面希望可以至少呈現：
1.  會議的基本資料（前世今生）、議前的資料、會議進行方式
> 目前是期待：用open source 軟體 + 買版型來作單頁式網站
> [name=Chia L]

> 家華開規格的語言變得好專業！酷
> [name=仲庭 李]

> 因為先問過charles
> [name=Chia L]

2.  會議前，**全台民眾的報名系統**
> 目前想到可以用google doc
> [name=Chia L]

> 可以跟 g0v 黑客松一樣用 kktix
> [name=ET B]

3.  會議進行中的**審議過程記錄（小組討論脈絡的記錄）**
> 目前希望在     ETBlue大大   ( 挪抬，以表尊敬）弄的憲動盟會議記錄的系統下再進化
> [name=Chia L]

> 啥小啦 XD
> [name=ET B]

4.  會議進行中的**投票結果（目前預計是台北、台中、台南三市）**
5.  會議後，**台灣三市投票結果與他國結果的互動比較**
> 目前這個計劃，台灣還想嘗試在全球共同討論的問題之外，再置入三個城市層級的國內問題。
> [name=Chia L]


~2)~ ~為什麼 2015 WWViews 要開發~~跨國審議/投票~~系統~
~ET觀點~
~這一年多以來，一直在動民主專案中摸索理想的網路審議系統到底該長什麼樣子，繼針對草根論壇設計的動憲法專案後，家華又提供了新的實驗材料讓我們驗證系統規劃的概念，人類距離網路審議的最佳實做方式越來越近了……~
> 你想太多了你 ＠＠ 不要說最佳方式啦！！！
> [name=Chia L]

> 只是試著把跨國經驗導入，大家來嘗試看看！
> [name=Chia L]

> XDDDD
> [name=ET B]

> 齁～別說太誇張！拜託拜託～
> [name=Chia L]

> XDDDD
> [name=ET B]

> 不過，我覺得wwviews改量一下，很適合進行全國審議＋投票的模型。我個人覺得目前台北市府推的ivoting很粗糙，過於簡化voting的概念，忽略voting與voice兩者間的互補，更沒有關注更前端需要的inform。
> [name=Chia L]

> 上面這段我改寫到前面了，晚點刪掉 XD
> [name=ET B]


[ET Blue](https://g0v.hackpad.tw/ep/profile/GdbGGcFdsbA) 進一步幫忙釐清如下  ↓
    這個專案其實有一塊是：投票結果資料視覺化網頁，而這個資料視覺化網頁，要有跨城市資料比較的功能。
    所以精確地說，是**『會議紀錄資料視覺化 \+ 投票結果資料視覺化』** 網頁設計
    （是否需要後端，未定；為要把wwviews的資料匯入，會要跟丹麥的工程師溝通，請他們有開放api）

### 4) 現有類似專案

（現成的是否可以直接使用？或者有什麼不足之處？國外專案可參考？）
> 其實就是 ↓ 5)相關專案  XD
> [name=Chia L]


### 5) 相關專案

（衍生自某專案/衍生出某專案/API串接自某專案.）
- 審議過程紀錄呈現參考憲動盟草根論壇網頁 [http://g0v.github.io/don-constitute/public/grassroot-9-taedp-20150124](http://g0v.github.io/don-constitute/public/grassroot-9-taedp-20150124)
- 投票結果呈現參考過去的 wwviews 結果網頁 [http://biodiversity.wwviews.org/the-results](http://biodiversity.wwviews.org/the-results)

### 6) 授權方式

（程式碼部分如 MIT/BSD /文件部分，如 CC-BY）

### 7) 使用資料

（會使用到哪些資料來源、各是什麼授權）
- 審議過程文字紀錄，授權：___
- 投票結果統計資料，授權：___

### 8) 專案目前狀態

（構想 / 規劃 / 雛形 / 實作）

### 9) 利益揭露

目前這個project（主要是民間希望能啟動而發起的跨國聯合審議行動）正在進行募款、申請經費中，目前是有編三萬塊的網站建置費用，但是否募款、申請的到錢，尚不確定。「可能的」申請經費的對象，包括：台北、台南、台中市府，中央機關（環保署、外交部...）、民間基金會、大學等。（最後結案報告也都會說明經費花費、募款或申請補助了多少錢）
- 從wwviews [open invitation](http://climateandenergy.wwviews.org/downloads/climateandenergy.partner.invitation.pdf) p2，可以看到“Participating partners have to find financial support for their own citizen consultation, but support could be available from governments, companies, and development aid. One option may be to ask your country’s COP21 delegation, and Article 6 focal point.”各國的合作團隊夥伴必須自行籌款！
> 捐款請洽：____________
> [name=ET B]

> XD
> [name=ET B]


## 03\. 徵求協作者

發起人/拋磚人：家華（2015/4-8月，2015 WWViews@TW Project manager，有給職執行這個project；Project Director：[台大政治所林子倫副教授](http://politics.ntu.edu.tw/?p=278)）

- [ ] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
- [ ] NeedsDesigner: 需要介面設計
- [ ] NeedsData: 需要資料（擷取、清理）
- [ ] NeedsTech: 需要技術支援（程式、架站 etc)
- [ ] NeedsProcess: 需要幫忙設計作業流程
- [ ] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡


## 04\. 實作細節（非技術背景可跳填）

協作工具
- github repo：
- hackfoldr 工作資料夾網址：
- google drive 共用資料夾網址：

進度與 to-do
- [ ] product planning（recommanded procedure from justin lee / 李易修）
    - [ ] strategy
    - [ ] scope
    - [ ] structure
    - [ ] wireframe
    - [ ] visual
- [ ] web front-end
- [ ] web back-end
- [ ] ui / visual design


## 05\. 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）



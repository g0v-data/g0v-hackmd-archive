---
title: "立法卡到陰"
tags: hackpad
---

# 立法卡到陰

> [點此觀看原始內容](https://g0v.hackpad.tw/9kiBcC1q2vy)

專案網址：[http://frank00125.github.io/wp2014s\_final\_project/introduce_page.html](http://frank00125.github.io/wp2014s_final_project/introduce_page.html)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_be91cd66ede1ad7271bba5c4dd25f8b9)

### 提案人：


國立政治大學

資科四 蘇智煒
社會四 邱思頴
資科三 陳立強
資管三 邱垂暉
廣電三 林思妤
日文三 孫湘蕙


### 專案說明：

民眾大多數只能透過大眾平面媒體或是網路媒體了解最近的法案相關議題，然而不論是電視或網路媒體所播報出的訊息都是經過篩選且不完整的，當大家都在關注熱門的法案如：服貿或是核四的同時，其實法院也正默默通過許多與我們切身相關的法案，但這些冷門法案卻不為大眾所知，原因除了是因為媒體炒作外，法案常常給人一種嚴肅又無趣的形象，讓人望而卻步，所以我們希望透過一個簡單的網頁抽卡活動的設計，引起名眾對冷門法案的注意和對立法過程的多一點認識，進而透過這個遊戲的方式散播訊息出去讓更多人知曉。


## 要解決的問題

現有類似專案
（現成的是否可以直接使用？或者有什麼不足之處？國外專案可參考？）

### 國會大代誌 [http://ly.g0v.tw/calendar/today](http://ly.g0v.tw/calendar/today)

同樣以立法院公開的議程資訊和會議記錄來做方便民眾找尋的資料彙整平台。

優點：
1.  畫面設計簡單簡潔，方便使用也易於了解。
2.  將資料分類並列出分類和時間，以及相關立委的回應和資料。
3.  除了會議審查外，也有公聽會的資訊匯入。
缺點：
1.  只依照時間軸排序會議議程，法案相關的資訊不多也不詳細，若想持續追蹤同一法案則需要自己另外搜尋。
2.  僅止於提供會議資訊平台，並未有相關資訊的詳細介紹，也未有民眾公開討論的空間，推廣上可能不容易造成效果，導致實用性的降低。

### 話筒式的公共參與 [http://billy3321.github.io/lytel/](http://billy3321.github.io/lytel/)

以立委資訊提供為主，讓民眾可以得到所有立委的聯絡方式，透過話筒實踐公民參與

優點：
1.  頁面設計簡單，資料排列整齊詳細。
缺點：
1.  僅止於提供立委的資料，倘若需要聯繫然需跳出網頁進行，且並未提供電 子郵件地址。
2.  只有立委的聯絡方式，資料不多，感覺可以加入參與相關法案資訊的整合。

相關專案
（衍生自某專案/衍生出某專案/API串接自某專案.）

### 立院影城

運用立院開會時的錄影資源，將知會整治同一平台，並開放民眾即時參與討論

優點：
1.  提供即時性和回顧紀錄的影片，生動且吸引人
2.  有民眾線上評論的功能可以讓民眾有討論空間，評論機制有趣活潑，讓人印象深刻
缺點：
只有提供會議中的影片，並沒有針對審查的議題有太多著墨，讓民眾必須要跳離該頁去搜尋資訊

### 立委投票指南


優點：
1.以政黨顏色、選區方式，甚至是所在之委員會將立委分類，一目了然。
2.有排行榜的功能，使民眾可以輕易了解立委的工作狀況。
3.連接如罷免立委等相關的網站。

缺點：
1.畫面過於簡易，較無設計感，配上例如法案頁面這類較死硬的資訊，讓人有不想閱讀的感覺。
2.互動的部分只開放留言，較無參與感。


### 授權方式

（程式碼部分如 MIT/BSD /文件部分，如 CC-BY）
MIT
CC-BY

### 使用資料

立法院網站資訊
國會大代誌
立委投票指南
網路資訊
ptt上資訊

### 專案目前狀態

規劃、構想、雛形


## 目標與功能（要如何解決）

### 預定功能

> 功能不用多，找出你們網站 unique value ，針對該點設計到最佳即可。
> [name=jones f]

> 很多東西可與其它網站內容相連結，不需自己再做一份 (e.g. 立委資訊)
> [name=jones f]

> [https://twly.herokuapp.com/vote/08-04T01-YS-01-003/](https://twly.herokuapp.com/vote/08-04T01-YS-01-003/)
> [name=jones f]

抽卡功能：
每位使用者進入之後會先進入抽卡的活動，卡片內容是立法的所有法案（包含提案與一二三讀和生效的法案），我們從中選取八個議案讓使用者抽取，依照議案的不同分為五個等級，分別是一星（提案中）、二星（一讀）、三星（二讀）、四星（三讀）和五星（生效）五種，抽取的機率是一星最高五星最低，所以生效的法案會比提案中的法案還要不容被抽到。抽卡之後可以看到議案的名稱和提案緣由，旁邊還會有一些call to action的功能，例如：閱讀更多法案相關資訊、分享至臉書讓使用者深入了解法案。閱讀更多的按鈕會連結至國會大代誌的法案細節頁面，在那裏他們可以獲得完整的法案資訊；分享臉書的功能是可以在臉書上發布使用者抽卡得到該法案並想與大家分享請大家關注的貼文，而上述的功能都是要註冊登入會員之後方可使用。

戰鬥功能：當使用者連續登入多天之後，就會蒐集到許多張法案卡片，只要卡片張數多於五張，就可以展開和不同人的對戰模式，每天最多可以進行三次對戰。每次對戰可以選取卡片庫中的五張卡片對戰，自行擺放順序，依照擺放順序比星數大小，星數大的即獲得一個圈，五戰三勝制，獲得三個圈以上就算獲勝！每天玩家可在登入之後變換牌組，當天只能更換一次，按下確認鍵之後，隨機進行配對對戰。

### 使用流程


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9cc2f0df7e9abd9567a6fc40f04dc7fb)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_78bc10b72c5f871c8861aade61597b7d)


### 預定使用者

1.想知道卡片內容
2.想要了解現在還有哪些法案正在進行審查
3.想要蒐集所有法案卡片


## Core and path sheet

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cf93c3948823d342d6fd5b5699c4c6b0)
[https://docs.google.com/drawings/d/18V6RH90oL8qrxhH-5bQEvsergxhm2wAnoEhIH2pOBso/edit](https://docs.google.com/drawings/d/18V6RH90oL8qrxhH-5bQEvsergxhm2wAnoEhIH2pOBso/edit)


## Site structure

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4c2bf61038b18d2f229590621c92e6ce)


## Mockup

### 入口畫面

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5a6a45ae45279a8016da89d8a8568489)

### 選卡頁面

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_770176f6544d36ab5f80c52e445a2916)


### 選卡後的法案卡內容

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_db04ae7a5df378cd456fd3d01f4ffec2)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_94fc63b253f4ae7a90224cbcc469f648)

### 註冊頁面

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_97362f1be52bcd4ac9bfa7e525b22c26)

### 遊戲規則

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_87d2e747cd80b3d220741d10d08c677d)

### 卡片庫

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4843161134d3155a9b2fa03f7acfa3a5)

### 戰鬥頁面

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7620b0b35f504eaac4995c4c5dac6616)



## 工作進度

- [ ] 5/  5：完成HTML架構設計
- [ ] 5/ 12：完成CSS設計
- [ ] 5/ 13：完成測試
- [ ] 5/  14：完成所有頁面之設計 (HTML+CSS)
- [ ] 5/ 21：法案部分的JS + Cloud DB完成
- [ ] 5/28：立法委員部分的JS + Cloud DB完成
- [ ] 5/  5：立法審查小知識部分的JS + Cloud DB完成
- [ ] 6/  1  1：作品完成 (js+cloud DB)，進行beta測試

## 徵求協作者

發起人/拋磚人：
分工與成員
- [ ] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
- [ ] NeedsDesigner: 需要介面設計
- [ ] NeedsData: 需要資料（擷取、清理）
- [ ] NeedsTech: 需要技術支援（程式、架站 etc)
- [ ] NeedsProcess: 需要幫忙設計作業流程
- [ ] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡
> 設定成 project registry 中的 tags，需要幫忙的會自動 promote 到 g0v project hub
> [name=ET B]




## 實作細節（非技術背景可跳填）

協作工具
- github repo：
- hackfoldr 工作資料夾網
- 址：
- google drive 共用資料夾網址：

進度與 to-do
> 僅供參考
> [name=ET B]

- [ ] product planning（recommanded procedure from justin lee / 李易修）
    - [ ] strategy
    - [ ] scope
    - [ ] structure
    - [ ] wireframe
    - [ ] visual
- [ ] web front-end
- [ ] web back-end
- [ ] ui / visual design


> Please update the website link!
> [name=jones f]






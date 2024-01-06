---
title: "超農域"
tags: hackpad
---

# 超農域

> [點此觀看原始內容](https://g0v.hackpad.tw/8Hlh2hux8xg)

### 讓濃郁的農鬱轉成濃郁的農域

### 使濃稠的農愁成為濃稠的農酬

Transcend Agricultural Field(TAF) project

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_af5f1f4f33e91a5e536cd32103c46510)
目標--拆解各農業系統重新組合
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3cf840a48bc4d76ed392ba5743bf3b48)
### 三個系統目前拆解整合到 [hackfoldr](http://hack.g0v.tw/agriculture)中了

農業議題推薦觀賞: (可以跳至大約580秒左右)

[https://www.youtube.com/watch?v=CYELiEnUHlQ#t=580](https://www.youtube.com/watch?v=CYELiEnUHlQ#t=580)

## 原由

1.  為因應農業相關系統更加實用化與親切化，讓各行政、試驗以及民眾可方便使用，特此進行計畫開出hackpad
2.  最後應該會變成一個滿不小的聯合型系統
3.  該複合系統有1.藥物使用與查詢系統 2.作物疫情追蹤系統 3.栽培者之栽培紀錄、整體栽培境、組合性功能以及與官方或專家單位進行互動之系統，三者甚至未來更多連動，且可和官方公告即時連接
4. mockup產出中(1~3系統都有雛型惹\[App還沒XD\])
5.  從[農委會資料集](http://data.g0v.ronny.tw/index/list?orgFullname=%E8%A1%8C%E6%94%BF%E9%99%A2%E8%BE%B2%E6%A5%AD%E5%A7%94%E5%93%A1%E6%9C%83) 挑 initial prototype 要用的資料(不一定完全 fit，先作 demo 用)，以及其他資料
    依重要順序排列重要順序排列如下:
    1.  [農藥資訊服務網](http://pesticide.baphiq.gov.tw/web/Insecticides_MenuItem1.aspx) (這個不在資料集裡面)
> 經求證，農藥系統資料應以a為基準
> [name=曼 奧]

    2.  [植物保護手冊](http://www.tactri.gov.tw/wSite/ct?xItem=3691&ctNode=333&mp=11) (這個也沒有)
    3.  [植物保護資訊系統](http://otserv.tactri.gov.tw/ppm/)
    4.  [農藥殘留容許量(衛服部)](https://consumer.fda.gov.tw/Law/PesticideList.aspx?nodeID=520)
    5.  [植物疫情](http://data.g0v.ronny.tw/index/data/7273)
    6.  [農藥名稱手冊](http://data.g0v.ronny.tw/index/data/7281)
    7.  [農民學院](http://data.g0v.ronny.tw/index/data/7283) (診斷栽培ICM提供教育訓練訊息)
    8.  [蔬果重要病蟲害疫情旬報](http://data.g0v.ronny.tw/index/data/7295)
    9.  [稻熱病疫情現況](http://phis.baphiq.gov.tw/Plant/GoogleMap.nsf)  _(以地圖標示全國稻熱病發生情形)_
    10.  [農糧署農藥殘留抽驗結果](http://www.afa.gov.tw/saftyAgriculture_index.asp?CatID=296)
6.  依據目前情況指出...有幾個系統有衝突..........目前第一步是整合a-d，接著再融入e-h以及後續系統

> 好啦 因為有民眾和研究人員說不好用，叫做系統的一大堆...加上我一直都很想把這些系統整合強化
> [name=曼 奧]

> 之前是有想結合圖片辨識讓植物疫病容易被檢查出來
> [name=Yuan C]

> 臺大有在個系統就是植物影像辨識
> [name=Yuan C]

> 有～有聽說，師大也有一些類似的，不過在所謂”專家”眼中有一些非技術性問題Orz
> [name=曼 奧]

> 我是建議mockup完之後, 先挑一個來實作, 個個突破這樣
> [name=Yuan C]

> YES，123就是預計的開發順序，因為1是目前我這邊最被需要的，2和3是我認為可以一起開法鎔鑄在一起的(2、3以前想重新開發，但是一直沒機會在單位提案)
> [name=曼 奧]

> 可否加入特生中心的「老樹資料庫」？如果太過複雜，可以另外增加其他系統來單獨處理之。
> [name=ilya L]

> 可以先獨立製作，在之後超農域大系統出現之後組合或相關資料連結，這樣或許使用者比較不會混淆
> [name=曼 奧]

## 融合提案

提案第三系統(診斷栽培)和 [農作物生產紀錄 app](https://g0v.hackpad.com/-app-8c3ZyeuaKfF) 之後進行組合
下面是擷取IRC
直接跟農民買農產品這件事情，有一個我困擾的點，就是：藥劑殘留將沒有辦法被管控。目前農產品直銷市場確實有這種問題，就算使用生化法  也只能檢驗 氨基甲酸鹽類  以及 快被禁光的有機磷，其他是沒辦法的。後來我想到，既然生產紀錄的系統  是和 直接跟農夫買  或 一些幫助農民的團體合作，那麼 就有目標了  而且有可能可以讓  檢驗單位進行檢測  對消費者也有保障。另外一個融合的原因是 原本我設計的栽培者的栽培管理系統 是會和試驗改良場所做一個橋接的動作  所以有問題要診斷 要看田 或是 希望試驗單位給建議 又或者是試驗單位有好的東西想推廣。都可以直接受惠到農民身上  同時 也可以讓有加入的人可以第一手就拿到輔導的資訊
之後可以開農業小松:Q  我會斷續找一些專家來給各種觀點

> 關於直接跟農民買農產品這部分，小弟有挖另外一個坑，不知各位有沒有興趣參考看看
> [name=Wen-Chi C]

> **農業生產者資訊揭露平台**[https://g0v.hackpad.com/gvkD1y2n6vg](https://g0v.hackpad.com/gvkD1y2n6vg)
> [name=Wen-Chi C]



## Mockups by a0kman

## 下面是藥劑系統

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b123422f278328f9ffede422bfa7c434)




![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9c8525ff6ab12e1e8dc2f015baa10813)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a34de22b42a10cc759f3f185c1e20ce2)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e84be2c6d296a940d97d6cc08c4edf90)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a61ea4d0ab529420ffd67cadcc98107b)
### 上述系統預計再加入一個藥劑使用比對區(官方使用)，以順利剔除比對上出現問題的內容


## 下面是疫情追蹤系統(某程度修改後也可以變成泛用系統)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2f152460228d1e16adefdeafcf841677)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_109bf9d442bbddbeb2ebf0bac64b707f)
### 地圖以Google Map顯示，並且可以轉成Earth，如顯示為行政區地圖，可以色塊表示嚴重性，若有持續填報累積資料，可以earth跑出色塊變化的嚴重性



![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c2a348634be9b23c0a41d431a74f77cc)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_403a12a1a5d5f6a210afaffac9611be0)


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_164b001d865bdd2bbf0e7d771f2c6da3)

**疫情概況在點擊後可以亦可以選擇一次出現整篇的全國報告(組合)，相關的內容都可以匯出成DOC或PDF等格式，亦或是產生QR-Code後，系統產生的報告圖片(類似**[Bokete](http://bokete.jp/boke/hot)**的方法)，疫情資料(確定是什麼疫情後)可連接到藥物系統和管理(診斷)系統進行**

## 下面是栽培管理與資訊系統

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c43380b9830df39ce3ded9f3d29fe3c8)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0bebb2145455e29c46cb26daf2401dcc)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_335aeeae0946b38b11aaad644607660f)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_21d7aea9eb685e57180729f203615bbc)
### 這邊另外加入--

### 在國家栽培訊息中自己標註要注意(或參加)的一些事件提醒或紀錄



![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0134c8d2a2e213affdc405b2ce157c43)
### 如何結合 [農作物生產紀錄 app ](https://g0v.hackpad.com/-app-8c3ZyeuaKfF) 成為一體???

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_dcf13f9995e18bb806163ae35aa17c3a)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_26f7b3fb4a8af889434ebff7c8af9410)

另外設計積木組合型栽培管理過程設計組，方便農民和輔導人員可以整理栽培記錄和調整


## 功能相關文字討論

- 除了一般Guest以外有辦法以FB或Google帳號登入的方法，讓未來的操作者有方便管理自己用藥、防治記錄或方便檢視自身關心的疫情嗎?
- 藥劑系統方面，記錄操作者最後的產出內容(例如最後的List操作者打包了哪些)，這樣就可以持續追蹤其使用習慣

## 預計整合的相關資料(隨進度可能會再加入其他)

[田邊好幫手](http://m.coa.gov.tw/Default.aspx?status=farmer)
[植物保護手冊](http://www.tactri.gov.tw/wSite/ct?xItem=3691&ctNode=333&mp=11)
[有害生物用藥資訊管理系統](http://agriext.tactri.gov.tw/pmg/PMG.aspx)
[藥劑延伸使用](http://www.tactri.gov.tw/wSite/lp?ctNode=336&mp=11&idPath=213_227)
[農藥資訊服務](http://pesticide.baphiq.gov.tw/web/Insecticides_MenuItem1.aspx)
> 這個服務網功能很多，目前是想把**登記農藥查詢**、**公告**那邊取出來用
> [name=曼 奧]

> 希望能由系統自動追蹤這邊的公告，自動擷取新藥發布、延伸使用或禁用的訊息，尤其是禁用訊息對農民很重要，免得明明是照植保手冊合法用藥，到最後還是變成違規用了禁藥～因為農友不知道已經被禁用了。
> [name=Wen-Chi C]

[疫情資訊](http://www.phicroc.gov.tw/)
[農藥殘留安全容許量(衛服部)](https://consumer.fda.gov.tw/Law/PesticideList.aspx?nodeID=520)
## 參考加工網頁

[稻熱病疫情現況](http://phis.baphiq.gov.tw/Plant/GoogleMap.nsf) (地圖展示全台稻熱病疫情發生情形)
[Google Flu](http://www.google.org/flutrends/) (地圖展示以及疫情追蹤用)
[WIKI](http://zh.wikipedia.org/wiki/Wikipedia:%E9%A6%96%E9%A1%B5) (這是主結構構想核心)
[萌典](https://www.moedict.tw/#穩定) (發音、大字用)
[食材辭典](http://www.ehealthyrecipe.com/recipe-webapp/syokuzai/) (日本的，可參考網頁和app格式)
[福利請聽](http://listening.g0v.tw/#/index)
[政誌](http://fact.g0v.tw/)
[類似神燈精靈或問卷的參考](http://howmuchtomakeanapp.com/)

## 合體hint

- 神燈精靈篩選
- 影像判定
- 木工組合

## 其他參考

- 藥劑殘留
1.  [聯合國組織：CODEX](http://www.codexalimentarius.net/mrls/pestdes/jsp/pest_q-e.jsp)（可依作物或藥劑名稱查尋）
2.  [歐洲聯盟：EU](http://ec.europa.eu/sanco_pesticides/public/index.cfm)  （可依作物或藥劑名稱查尋）
    點入後欲查詢藥劑基本資料可點選：Active substance
    點入後依藥劑查詢可點選：Pesticides
    點入後依農產品種類查詢可點選：Products
3.  **美國**
    - [USDA](http://www.mrldatabase.com/) 提供各國容許量資料庫查詢系統（勾選同意使用條款後進入資料庫）
    - [EPA](http://www.epa.gov/pesticides/food/viewtols.htm) 美國EPA食品中農藥容許量之介紹網站
    - [EPA](http://ecfr.gpoaccess.gov/cgi/t/text/text-idx?c=ecfr&sid=bd32aab1f2263d189c2ea7ae45c321e9&tpl=/ecfrbrowse/Title40/40cfr180_main_02.tpl) 美國EPA針對農藥在作物上之容許量清單查詢系統（依藥劑名稱查詢）
4.  [加拿大](http://www.hc-sc.gc.ca/cps-spc/pest/part/consultations/index-eng.php) (諮詢文件中訂定安全容許量之選項Proposed Maximum Residue Limit)
5.  [澳洲](http://www.apvma.gov.au/residues/standard.php#tables) (蔬果中農藥安全容許量--Table 1)
6.  [日本](http://www.m5.ws001.squarestart.ne.jp/foundation/search.html)
-
日本開發的系統不過好貴!!!!!
[農作業日誌](http://awd.alchefarm.com/about/)
garden compass：園藝專業者的互動諮詢服務，從病蟲害到認識植物學名 - [https://itunes.apple.com/tw/app/garden-compass-plant-disease/id605855033?mt=8](https://itunes.apple.com/tw/app/garden-compass-plant-disease/id605855033?mt=8)


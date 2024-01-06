---
title: "超農域---農業藥劑系統"
tags: hackpad
---

# 超農域---農業藥劑系統

> [點此觀看原始內容](https://g0v.hackpad.tw/CxE7gsWmErr)

因為三個系統(加上延伸的)整個太肥了，所以把三農系統拆解成三個hackpad，整理到[hackfoldr](http://hack.g0v.tw/agriculture)中，方便作業，不過三個以及後來可能延伸或增加的系統希望未來是可以組合或連動的，並且也應用在智慧型裝置上方便民眾和相關單位使用，藉以促進農業的資訊和管理更便利和開放。
> 如果我的體重也可以這樣拆解就好了(?)
> [name=曼 奧]


## 藥劑系統  說明

農藥使用和殘留的議題經常出現，也是很受關注的內容，而農藥的相關藥劑系統目前有三個經常被拿來使用的頁面以及其他大大小小的:
1.  [農藥資訊服務網](http://pesticide.baphiq.gov.tw/web/Insecticides_MenuItem1.aspx) --應該是第一手訊息，同時藥劑公告和證照都可以在這邊查到
2.  [植物保護手冊](http://www.tactri.gov.tw/wSite/ct?xItem=3691&ctNode=333&mp=11) \-\- 很廣泛受到使用，是1的衍生版，但是有誤差
3.  [植物保護資訊系統](http://otserv.tactri.gov.tw/ppm/)  \-\- 聽說是2的便民版本
4.  [農藥使用資訊系統](http://pesticide.tactri.gov.tw/)  (..........到底有多少系統)
5.  [農藥名稱手冊](http://data.g0v.ronny.tw/index/data/7281) \-\- 這是另外加來可以參考用的
6.  [有害生物用藥資訊管理系統](http://agriext.tactri.gov.tw/pmg/PMG.aspx) --這.............
7.  [藥劑延伸使用](http://www.tactri.gov.tw/wSite/lp?ctNode=336&mp=11&idPath=213_227) 公告許多藥劑延伸 (擴增特定藥物可用情況)
8.  [（非有機）農作物農藥殘留監測結果](http://www.afa.gov.tw/saftyAgriculture_index.asp?CatID=296)、[有機農業檢查結果](http://www.afa.gov.tw/organicAgriculture.asp?CatID=290) \-\- 農委會農糧署的每月抽檢
9.  （[不合格進口食品](https://consumer.fda.gov.tw/Food/UnsafeFood.aspx?nodeID=170) \-\- 衛福部邊境查驗）
> 這是從[好市多泰國蘆筍殘農藥新聞](http://www.nownews.com/n/2014/04/02/1174800)追蹤到的
> [name=ballII]

> 農藥資訊服務網應該是主管機關衛福部維運，植物保護手冊則是農業藥物毒物試驗所依據技術諮詢委員會決議編輯造冊，所以兩邊的資料會依據衛福部的需求有點落差的樣子，但管理上會依據1.的資訊去判定。
> [name=Ya-Chieh T]

10.[農藥作用機制解釋文](http://ogserv.tactri.gov.tw/moa/tactri_moa_2010.pdf) (PDF)
11.[農藥依據機制分類網頁](http://ogserv.tactri.gov.tw/moa/TT07CLASS.aspx?idx_code=HRAC&class_code=Z&)
12\. [農藥標示查詢系統](http://public.tactri.gov.tw/cdfiler/asp/main.asp?Print=False)
> 經過詢問和親自操作後，裡面有農藥各生產公司商品的外包裝貼圖
> [name=曼 奧]

13\. [農藥劑型代碼表](http://www.tactri.gov.tw/wSite/ct?xItem=3960&ctNode=310&mp=11)
14\. [新開發的銷售管理系統 (POS)](https://pest.baphiq.gov.tw/BAPHIQ/wSite/baphiq/mp.jsp)
15.[有害生物資料庫(含天敵)](http://210.69.150.201/insectsite/)
然而其中的內容有發生內容出入、誤差的情形，此外在使用上的問題，讓使用的部分單位也有出現使用上的困擾，
加上殘留量是由衛福部管理( [農藥殘留容許量](https://consumer.fda.gov.tw/Law/PesticideList.aspx?nodeID=520))，是故希望可以再重新拆解組合成一個新的系統，挑出問題以外也提升便利性。
之後預計和國內外的檢疫相關系統做一個比較性的組合，方便相關單位以及栽培和出入口的從業人員進行對照，並且可以針對藥劑和疫情類**的**[非關稅貿易障](http://zh.wikipedia.org/wiki/%E9%9D%9E%E9%97%9C%E7%A8%85%E5%A3%81%E5%A3%98)礙進行更方便的處理
15.[農藥安全資訊資料庫平台](http://ghs.baphiq.gov.tw:8080/Chemurgy/enterSearchMaterial.do)(應該就是農藥安全資料+MSDS中文版)
16\. [BCPC](http://bcpcdata.com/pesticide-manual.html) (國外的農藥資料，最重要的宗師版本，目前更新到2012版) ，裡面可以找到農藥系統性/非系統性資料
搜尋引擎整合:
- 只要有靜態網頁
    - 目前的 PDF 轉為 HTML
    - HTML 用 schema.org 標注結構化資料
    - 用 Google site search
榮尼王設計的pdf文表提取技術：
[https://github.com/ronnywang/pdf-to-table](https://github.com/ronnywang/pdf-to-table)
 # 先把上次的 code 整理了一下丟在這邊了
##  賣點(有什麼更便利的設計)

-  畫面更加清晰明瞭
- 融合原有零散的可用資訊
- 共田搜索
- 便利輸出
- 藥劑使用歷程、選擇管理
- 未來與其他系統的連結性
## 橫向連結設計

農藥系統未來預計和其他系統有相關性的連結，就目前設計的構思來說有以下幾個橫向連結可能
- IP或使用者標註所在位置X查詢農藥、作物種類，可和官方病蟲害診斷鑑定結果以及疫情警報、氣象資料、地理資訊結合，做出更多元的疫情狀況報導、統計或線上警報
- 農藥查詢資料輸出可和疫情系統以及農民自我管理系統連接，農民方便管理用藥，官方方便掌握藥劑使用與發佈
- 新功能"藥劑小幫手" 融合 新聞小幫手?????(安全資料庫平台資料X自主運算結果?)
## 上游資料


Farmer portal:
Index: [http://m.coa.gov.tw/OpenData/PesticideData.aspx](http://m.coa.gov.tw/OpenData/PesticideData.aspx) (JSON)
Detail: [http://pesticide.baphiq.gov.tw/web/Insecticides\_MenuItem5\_3_UseRange.aspx?id=H169](http://pesticide.baphiq.gov.tw/web/Insecticides_MenuItem5_3_UseRange.aspx?id=H169)
where H169 is "農藥代號" from the index

Consumer portal:
- 田間 (農委會) \- [http://www.afa.gov.tw/organicAgriculture.asp?CatID=290](http://www.afa.gov.tw/organicAgriculture.asp?CatID=290)
    - 有機 -\> 含 ND (未檢出)
    - 非有機 -\> 慣行農法, 目前因為只有檢出有殘留的資訊，而且有個資，而且難以連結到供貨地點，而且格式和有機不同，所以暫時 hold。
- 市面 (衛福部) \- 目前看來是 2~3 月不定期更新
    - 有價值，但沒有固定格式，建議連絡承辦人
        - Google "為維護民眾食用農產品的安全" 就可以找到
> 衛福部回覆大意：「農藥殘留監測每月統一發佈在 [http://www.fda.gov.tw/TC/site.aspx?sid=2428](http://www.fda.gov.tw/TC/site.aspx?sid=2428)  。格式其實有固定，只不過102年底檢討修改過，所以102與103年格式不同。」
> [name=ballII]

> 不知這種網址適合被爬嗎？
> [name=ballII]

> （再補充：「網頁上雖顯示南區管理中心，實為南區管理中心負責資料之彙整，故此監測結果為綜合北、中、南三區之結果。」）
> [name=ballII]

> 應該可以! 我試看看。
> [name=Audrey T]


Prototype: [http://g0v.github.io/agriculture/](http://g0v.github.io/agriculture/)
[http://g0v.github.io/agriculture/pesticide.html](http://g0v.github.io/agriculture/pesticide.html)
Todo:
- [ ] 各項菜名加上 CC 授權或連外網站的圖片介紹
- [ ]

## 資料架構

藥劑
許可證號：ref 藥劑 (、廠商？)
作物/作物類別：ref 作物類別
害物/害物類別：ref 害物類別
藥劑使用方法：ref 藥劑、作物/作物類別、害物/害物類別
> 調查一下作物與害物類別是否為單一分類
> [name=Simon P]


## 使用者分析

農夫
- 施藥方法搜尋
    - 作物得病，已知病害名稱，查施藥方法
    - 作物得病，不知病害名稱，查施藥方法
    - 作物未得病或還沒種，先調查有哪些藥劑可用
研究人員
推廣人員

## 文案

### 我是農夫（查詢藥劑使用方式）

本區收錄各種藥劑的標準使用方法。請於搜尋框內輸入欲搜尋的關鍵字（例如農藥名稱）。

本區原始資料來源於行政院農業委員會動植物防疫檢疫局[農藥資訊服務網](http://pesticide.baphiq.gov.tw/web/Insecticides_MenuItem1.aspx)，版權仍為行政院農業委員會動植物防疫檢疫局所有。
### 主要顯示

中文名、商品名(廠牌名稱，在許可證那邊可以找到)、使用方法、含量(%)、稀釋倍數(使用時)、劑型、安全採收期、使用次數、每公頃用量，以及併入衛福部的殘留量規定
其他的都可以藏在看更多之類的，因為農民最主要會用到的應該就是這幾項目

### 新增副本

1.  同一種作物可用的藥劑分散在不同名稱之下，例如單獨查詢茼蒿只有3種藥劑，其他可以用在茼蒿的藥劑要從"菊科葉菜類"找出來，這個副本需要整個挖出來整理
> (用比喻來說就像找劍這種武器，搜尋"劍"只找到鐵劍，其他像是玄鐵劍、無塵劍還是青冥劍要從"握柄武器"這個項目裡面搜尋才可以找到)
> [name=曼 奧]

- 目前整理該副本較混亂的分類內容如下
    **豆菜類**(大豆、豌豆、菜豆、豇豆、萊豆、蠶豆、扁豆、翼豆)
    **乾豆類**(大豆、落花生、紅豆、綠豆)
    **豆科作物幼苗**(大豆、豌豆、菜豆、豇豆、萊豆、蠶豆、扁豆、翼豆、落花生、紅豆、綠豆、花豆、樹豆)
    **十字花科**(不結球及結球白菜、甘藍、花椰菜、青花菜、包心芥菜、抱子甘藍、球莖甘藍、芥藍、芥菜、薺菜、油菜、葉用蘿蔔)
    **菊科**(包括不結球、半結球及結球萵苣、茼蒿、紅鳳菜、白鳳菜、昭和草、艾草、牛蒡、黑婆羅門蔘)
    **蔥科**(包括蔥、蒜、韭、洋蔥、珠蔥、蕗蕎)
    **蔥科葉菜類**(蔥、蒜、韭)
    **瓜菜類**(胡瓜、小黃瓜、苦瓜、絲瓜、冬瓜、南瓜、扁蒲、隼人瓜、越瓜及夏南瓜)
    **瓜果類**(西瓜、香瓜、洋香瓜)
    **茄科**(番茄、甜椒、茄子、辣椒、枸杞、另含根莖菜類馬鈴薯)
    **茄科果菜類**(番茄、甜椒、茄子、辣椒、枸杞)
    **根莖菜類**--這個要獨立作業了，每個每個不同
    **菊科根莖菜類**(牛蒡)*--額外注意
    **薔薇科果樹**(梨、桃、梅、李、杏、蘋果、枇杷、櫻桃)
    害蟲似乎又有一些處在另外一個狀態= ="
    **菊科葉菜類夜蛾類**(萵苣、茼蒿、紅鳳菜、結球萵苣)
    觀賞花卉、觀賞植物、行道樹部分需要另行討論
    雜草算是另外一個系統，
    如果點進去雜草區還會有其他使用對象說明
    [常見雜草](http://www.tactri.gov.tw/wSite/htdocs/ppmtable/weeds.pdf)  (PDF)
    生長調節又是另外一章了

1.  新增不同作物交叉比對可以共用/不能共用的藥劑種類(不能共用這個選項壽命應該很短，那是讓專責單位比出來以後傷腦筋解決用的)，例如芹菜X菠菜 或  芹菜X菠菜X空心菜，因為有不少農民會同一塊田混種不同作物或不同作物的輪作，若用到A可用B不能用的藥劑，那B就有殘留或使用未推薦用藥的可能。
- 目前出現的所有作物名稱：[https://gist.github.com/simonpai/c9c0f5a6eba8aec64b0e](https://gist.github.com/simonpai/c9c0f5a6eba8aec64b0e)
> 「園」38 筆、「類」24 筆、「地」6 筆、「科」22 筆、「苗」8 筆
> [name=Simon P]


文字解釋:
- **中文名:** 藥劑本身原體(主要有效成分)的中文名稱
- **商品名:** 不同農藥公司引進這種藥劑加工商品化之後，會有不同的名稱，例如人吃的藥劑"普拿疼"、"立停疼"是一樣的主要成分，但是商品名稱不一樣(這個在農藥資訊服務網裡面的"許可證"項目可以查到)
- **使用方法:** 就是使用方法XD
- **含量:** 這種藥劑本身的主成分含量
- **稀釋倍數:** 使用的時候稀釋幾倍用(例如用洗衣機洗衣服的時候，洗衣機多少水，洗衣精多少量要加幾個瓶蓋那種感覺)
- **劑型:** 藥劑型式，就像我們吃藥也有藥粉、膠囊、糖漿...
- **安全採收期:** 噴藥以後過多久採收是吃了安全不用擔心的天數
- **使用次數:** 針對這種病害用幾次(例如次數2次，間隔7天，那就是每隔7天用一次，共用2次)
- **每公頃用量:** 單位面積的藥劑使用量

### 我是消費者（查詢農產品或食品的農藥殘留）

本區收錄非有機或有機農業中各種農產品或加工食品的農藥殘留量。請於搜尋框內輸入欲搜尋的關鍵字（例如食品名稱「葡萄乾」）。

本區原始資料來源於[行政院農業委員會農糧署](http://www.afa.gov.tw/index.asp)，版權仍為行政院農業委員會農糧署所有。



## MOCKUPS (感謝Au協助上傳)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cbb25059afbf56f41a382ed6d3faa492)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_28e92ae5dea4452a0a71641504625930)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0a7c95a6e2797e90e3fb84b52ef50ba3)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_869e6d2ee6553c835ac9c49356ab8aee)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c61fcc1f35ca85df2187e87e51f3ba92)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9158a94b1c85ee7d4a52bf9b5b63ea70)
> 喔喔喔有搜尋界面的 mockup 了! @MoonChang++
> [name=Audrey T]

> 也許 6/14 前端共學松剛好拿來做 HTML+CSS 切版的習作?
> [name=Audrey T]

> 感謝子龍QAQ，感覺很帥XD!
> [name=曼 奧]


前端教學松產出
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_58f9d5dc1318af4b1a9bfe936486d465)


### 系統連動想法

1.  連結疫情追蹤系統，提供疫情追蹤系統在疫情發生時可以快速尋找到可用藥劑或防治方法。
2.  連結栽培與資訊系統，提供栽培者與其他使用者可以查詢欲使用的藥劑，並且併入栽培記錄的清單中。
3.  與檢疫系統互通( [對外貿易植物檢疫資料庫查詢系統](http://192.192.148.121/coa/hotnews_idx.php)  )，可以更快速比對作物出入口要注意的用藥或檢疫事項(也轉譯成英日文方便國際使用?)
## 鍛造進度

- 2014/2/22大松 提案，Ronny wang 爆氣完成表格式PDF檔之文件抓取轉換功能
- 籌畫3月小松ing

## 延伸系統構想

老農或資訊能力較弱之使用者友善化
- 語音
[a0kman](https://www.irccloud.com/#!/irc.freenode.net:6667/a0kman)\> au: 因為我在想，是不是也可以開發出fit老農、資訊能力相對較弱者的 農藥或農業資訊查詢方法
== <====[au](https://www.irccloud.com/#!/irc.freenode.net:6667/au)====\> a0kman: 如果建立起可用的指令的文法，那可以做語音識別，網頁就可以了。== ==[https://alexandre.alapetite.fr/doc-alex/web-speech-api/index.en.html](https://alexandre.alapetite.fr/doc-alex/web-speech-api/index.en.html)==  ==[https://www.google.com/intl/en/chrome/demos/speech.html](https://www.google.com/intl/en/chrome/demos/speech.html)== ==etc==

## 其他藥劑類參考(結合檢疫)

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
      可針對化學物質(A到Z的分頁需先點選農藥第一個字母再搜尋)及作物(作物/畜水產品/加工食品/礦泉水)分別查詢
7. [中國](http://www.tbt-sps.gov.cn/foodsafe/xlbz/Pages/pesticide.aspx) (可依國家/地區查詢相關標準)
      公告標準以文件形式釋出，現行公告標準：[GB 2763-2012](http://cdn.chemlinked.com/file/GB2763-2012_CN%20version.pdf)
      2014年8月1日即將採用新標準：[GB 2763-2014](http://www.nhfpc.gov.cn/ewebeditor/uploadfile/2014/04/20140409103007373.pdf) (取代GB 2763-2012)



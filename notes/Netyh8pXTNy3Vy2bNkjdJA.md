---
title: "g0v pre-hackath4n"
tags: 反黑箱服貿串連,event,hackpad
---

# g0v pre-hackath4n

> [點此觀看原始內容](https://g0v.hackpad.tw/LC3myTujvhE)


國民大會黑客松之前，先來做點什麼吧！
7/11 主題：Whatever - 順便來吃 7.11 某人生日蛋糕、抵制 7-11！


地點: 和多星際總部
報名: [http://registrano.com/events/g0v-pre-hackath4n](http://registrano.com/events/g0v-pre-hackath4n) （此為7/11服貿蛋糕松報名網址）
> 開始時間都好早，到了 pizza hour 也結束 ><
> [name=Hsiao-hsien Y]

> pizza hour據說會延後 ^^  btw, 7/11那天其實沒有訂pizza
> [name=ipa c]


以下為想做的 project，請自行填寫：

- 串連資訊平台（服貿協議串連行動後續、鄉民關心你前期）
    - 討論共筆： [http://hack.g0v.tw/tisa](http://hack.g0v.tw/tisa)
    - 立委施壓平台(just called) + 地圖 signup
    - 討論平台：wikiarguments-like stuff

- kuansim 事件呈現頁

- 可以請公民審議的朋友家華來個10min短talk嗎？
> 介紹一下審議流程（因為跟幾個專案 liquid feedback, kuansim有關係，但我們都不太了解公民審議如何進行）
> [name=ipa c]

> 可以，已經通知他了哈哈
> [name=ET B]


\-\-\-\-\- possible scenario by 賴律師
7/29 談話會 表決是否開臨時會、是否納入服貿
-\> 正式院會 ->
狀況一:
- 逕付二讀 \- 不協商
- 逕付二讀 \- 協商 \- 實質表決約在總質詢後
- 交付委員會 <= optimal
    - 公聽會
    - 修正
    - 附帶決議

will be doing:
- wto service industry code
- roc service industry keycode

interesting data:
- 主計處100年工商服務普查 - 初步統計 [http://www.dgbas.gov.tw/ct.asp?xItem=532&ctNode=3266&mp=1](http://www.dgbas.gov.tw/ct.asp?xItem=532&ctNode=3266&mp=1)
    按部門別觀察，服務業部門計 93 萬 5,763 家，占全體企業之 78.98%，5 年來僅增 6.45%，其中知識密集型服務業家數成長 15.47%，高於非知識密集型服務業之 5.11%
    - 95 年 ([http://ebas1.ebas.gov.tw/icsweb/ics_menus1.asp](http://ebas1.ebas.gov.tw/icsweb/ics_menus1.asp))
        - 行業別只有縣市、鄉鎮級統計似乎沒有依行業切


貿易 vs 服務貿易

服務貿易關鍵點：
- 簽證總額上限（就業服務法外國人上限亦未訂定）
- (白領)薪資門檻（同外國人就業服務法）

possible immediate impact:
- rent bidding -> inflation

\-\-\-\-\-\-\-\-\-
服貿停看聽：[mockup](https://docs.google.com/file/d/0B0NsS2a-Qx8ZWi1PU0wyRG1scWc/edit) and [workflow](https://docs.google.com/drawings/d/1mH7BXK13DajLcO6vFsmN1mObRHNeQBIojjmJlq8iaes/edit) by @ETBlue
- user data collection
    - unified 選址 (frontend):
        - by geolocation: [http://www.lijung.com/WhereAmI/index.html](http://www.lijung.com/WhereAmI/index.html) / [http://gcaa.org.tw/callnow/](http://gcaa.org.tw/callnow/)
        - select on map - highlight 鄉鎮區 - then optionally 村里
        - input 鄉鎮區/村里 (select2 input box for filtering)
        - input address
    - ly vote integration
        - optionally collect previous ly vote of user
        - display previous ly vote winning margin for a givin constituency
    - signup for a peition (tisa blackbox, particular industry etc can be differenet ones)
        - optionally upload a photo (with banner) (to avatars.io?) or just simply use social sign in avatar
- display:
    - county/village view on leaflet clustered marker, popup with list of user photos
- just called integration
- map meshed with company data by sector from [http://company.g0v.ronny.tw](http://company.g0v.ronny.tw)

\-\-\-\-
7/11 會議紀錄 by 呂家華

\[與 g0v.討論記錄\]
時間|2013/07/11 18:00-22:00
地點|和多聯合辦公室(台北市大安區忠孝東路四段170巷17弄12號2樓)

g0v. 提到
1.  會做一個資料平台---服貿協議行動串連，今晚談到的行動包括:
    1.  open street map把19個立委附近屬於26項基層受害產業的商家標出來；
    2.  綜合第1點，做出19個會影響大家未來命運的立委資料畫面，串連所有匯進來的資料；
    3.  會做上中下三集的懶人包，上集會包括說明服貿是什麼，程序正義的訴求。(至於，服貿是誰受益、誰受害，隱含點出大財團v.小商家的對比，不一定會來得及放入上集的懶人包)。(未來想要弄一個線上審議的平台)
2.  應會去匯政府資料如服務普查、中選會資料、工商登記外，還會有郝明義那的資料，以及中強律師提供的行業表準分類和WTO分類方式的對照資料，下一步就是要把開放項目跟庶民認知的產業連結起來。

中強律師發言
1.  跟大家說明7/29二次臨時會上午，談話會表決，應會開臨時會，並決定哪些議案要納入議程，目前看來服貿和核四公投是會納入。那，下午可能的劇本，有:
    1.  逕付二讀\> DPP協商(不擋)>表決
    2.  逕付二讀>DPP協商(擋)>延到下一個會期約莫九月-十月進行審議
    3.  付委 (爭取實質民主的可能)
2.  策略目標可能可以是透過行動，達到1)阻擋或減低服貿不當開放的命運，2)公民與政治關係的新想像 (目前國會席次，藍綠差距12席，19席差距10%選票以內的立委選區，會是施壓的好對象) 3)拖到年底大概是國民黨的timeline，但這中間如何透過時間拖延爭取可能的方案(例如全部撤案、協商直接修改內容，或是協議內容不動但附帶決議)
3.  現在服貿最大的問題是看不到管制措施，例如無中國大陸人士來台，伴隨著資金來台的有董監事、經理、主官級技術人員與其家屬，但簽證仍無上限，以及尚未有各產業和台灣整體經濟的衝擊影響評估
4.  星期六會跟台教會溝通服貿的主訴。


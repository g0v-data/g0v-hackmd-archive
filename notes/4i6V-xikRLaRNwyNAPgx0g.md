---
title: "BatDrone 婦幼犯罪熱點提醒、無人機巡航"
tags: 無人機,犯罪熱點,hackpad
---

# BatDrone 婦幼犯罪熱點提醒、無人機巡航

> [點此觀看原始內容](https://g0v.hackpad.tw/BB8UPY6SPCD)

## 使用情境

1.  **手機上**：App 使用者在「易發生犯罪地點」附近範圍內（距離可討論），會有通知跳出，讓使用者有警覺性，或避開犯罪地點。
2.  **巡航情境**：BatDrone 巡視犯罪等高危險熱點，進行嚇阻式巡弋，搭載警示燈及720p影像即時傳輸設備  ，巡弋在30米空中，須考量攝像的解析清晰度，影像需可供指揮官及有效證據，也需避免來自於地面的攻擊或障礙物。
3.  **Follow Me**：使用者可以在固定高犯罪熱點區域呼叫 BatDrone 進行即時照明、跟拍，影像直播（或許可把直播連結傳給親人、朋友）。
4.  目的在於消除城市治安死角，強化警力機動性。警察的勤務原則上不會變多。

We are not
> 通知的資訊詳細度可再討論, EX：呼叫 Drone、最近的 Drone 離你幾分鐘、最後一次有人在此呼叫 Drone 的時間點 ...
> [name=鄭凱文]

> (鏡頭是否搭載穩定器?) 我覺得 prototype 可以不用加穩定器
> [name=鄭凱文]

> 有需要可以加裝簡單的Servo型gimbal
> [name=Milu L]


## 目前的坑

- [x] App 在地圖上標出熱點圖（with data.taipei 目前公開的開放資料）
- [ ] 爬「婦幼警察隊」的原始資料（[pdf](http://tcgwww.taipei.gov.tw/ct.asp?xItem=6505423&ctNode=45898&mp=10800A)）
- [ ] drone 戶外定位問題
- [ ] 硬體 drone 的原型機
> 台日友好的日本企業公布了這個：「會自動追蹤可疑人物的保安無人機正式推出了」
> [name=鄭凱文]

> [http://chinese.engadget.com/2015/12/14/security-drone-chases-intruders/?ncid=rss_truncated](http://chinese.engadget.com/2015/12/14/security-drone-chases-intruders/?ncid=rss_truncated)
> [name=鄭凱文]

- [ ] drone 回歸時，充電柱的設計
- [ ] web 上熱點更新，寄信通知
- [ ] icon 設計與 App 介面


## 軟體

### 開發重點

- **App** **（iOS、Android）**
    - 距離熱點 500 公尺，發布「帶有 Location」的提醒通知。
    - Google or Apple Map 熱點圖
> 在 code for SF 裡面有人提到，曾經有人有類似的 app ，沒有用到 drone 。
> [name=鄭凱文]

> 功能是回家時啟動 app ，在特定的回家路徑上手機會追蹤你，但如果發現你在回家的路上，停在同一個位置停留太久了（像是超過十五分鐘），他就會寄信或是發通知給你的朋友，告訴他們你可能遇到危險。
> [name=鄭凱文]

> 這滿聰明的。這麼一想 drone 的成本無比高。
> [name=鄭凱文]


- **Web（**[**網站在此**](http://batdrone.strikingly.com)**）**
    - 輸入「地區」和 Email，有熱點（更新）時發信給你。
    - 設計方向可以參考，世界各地的犯罪地圖（[奧克蘭](http://oakland.crimespotting.org/)、[舊金山](http://spotcrime.com/ca/san+francisco)）

### Github

[https://github.com/kevinphys/BatDrone](https://github.com/kevinphys/BatDrone)


### 資料來源

1.  易發生婦幼犯罪被害地點：[http://data.taipei/opendata/datalist/datasetMeta/preview?id=985743f7-a33e-4ac1-ad2e-7ef5ffea02e2&rid=efe5c923-fa09-4d55-896e-877c553f04e0](http://data.taipei/opendata/datalist/datasetMeta/preview?id=985743f7-a33e-4ac1-ad2e-7ef5ffea02e2&rid=efe5c923-fa09-4d55-896e-877c553f04e0)
2.  易發生婦幼犯罪...（地圖版）：[http://data.taipei/opendata/datalist/datasetMeta?oid=985743f7-a33e-4ac1-ad2e-7ef5ffea02e2](http://data.taipei/opendata/datalist/datasetMeta?oid=985743f7-a33e-4ac1-ad2e-7ef5ffea02e2)
3.  易發生婦幼犯罪 API：[http://data.taipei/opendata/datalist/datasetMeta/outboundDesc?id=985743f7-a33e-4ac1-ad2e-7ef5ffea02e2&rid=efe5c923-fa09-4d55-896e-877c553f04e0](http://data.taipei/opendata/datalist/datasetMeta/outboundDesc?id=985743f7-a33e-4ac1-ad2e-7ef5ffea02e2&rid=efe5c923-fa09-4d55-896e-877c553f04e0)
4.  婦幼警察隊原始資料（PDF，但還滿詳細的）：[http://tcgwww.taipei.gov.tw/ct.asp?xItem=6505423&ctNode=45898&mp=10800A](http://tcgwww.taipei.gov.tw/ct.asp?xItem=6505423&ctNode=45898&mp=10800A)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_857f845756f137f8ffb35cb4f460ae97)


## 硬體

### I - 技術文件 - 定位

1.  ["A Fusion Approach of RSSI and LQI for Indoor Localization System Using Adaptive Smoothers"](http://www.hindawi.com/journals/jcnc/2012/790374/)
2.  ["DIYdrones : Precise indoor positioning with ultrawideband"](http://diydrones.com/profiles/blogs/precise-indoor-positioning-with-ultrawideband)

### II - 技術文件 - 飛控

1.  ["Pixhawk Overview"](http://copter.ardupilot.com/wiki/common-autopilots/common-pixhawk-overview/)    (成本考量可改用Pixhack，大陸仿製，便宜一半，但接頭和I/O不太一樣)
2.  [http://www.think-tank.co.kr/223](http://www.think-tank.co.kr/223)
3.  [http://diydrones.com/profiles/blogs/coax-copter](http://diydrones.com/profiles/blogs/coax-copter)
4.  [http://multicoptersarefun.com/MulticopterOverview.html#SingleCoaxCopter](http://multicoptersarefun.com/MulticopterOverview.html#SingleCoaxCopter)
5.

### III - 價格參考

1.  正版Pixhawk(官網價格，不含稅與運費)
    - Pixhawk 飛控 : 200USD
    - GPS/compass : 90USD
    - 3DR Radio set : 100USD
2.  彷製Pixhack
    - Pixhack 飛控 : 4600NT
    - GPS/compass : 1690NT
    - 3DR radio set : 1600NT
3.  其他可能採購設備
    - 影像傳輸設備(機載端與地面端)
    - 接收機
    - 結構材料與加工
    - RPi & Navio+


## 討論區 X 留言板


> 第一個要先能像他們一樣做出一個不見血的Drone?
> [name=Allen L]

> [http://gofleye.com](http://gofleye.com)
> [name=Allen L]

> 材料基本上是有了，我可以負責先讓一顆球飛起來看看，比較麻煩的是這種類型的開源code比較少。現階段就先採用Pixhawk做飛控，接下來就要看其他功能想要幹嘛了? 才知道敷不敷使用。
> [name=Allen L]

> 我第一想到的是能自己定位充電站，乖乖回去充電。
> [name=Allen L]

> 室內定位? 超難，但值得一試。
> [name=Allen L]

> 如果不怕碰撞，充電站就一直發送訊號源給他讓他去追，不管室內室外？（幹，打完自己覺得很難做到。）
> [name=Allen L]

> RSSI/LQI轉換為距離嗎?  先蒐集一下室內定位的技術好了。
> [name=Allen L]

> "A Fusion Approach of RSSI and LQI for Indoor Localization System Using Adaptive Smoothers"
> [name=Allen L]

> [http://www.hindawi.com/journals/jcnc/2012/790374/](http://www.hindawi.com/journals/jcnc/2012/790374/)
> [name=Allen L]

> DIYdrones : Precise indoor positioning with ultrawideband [http://diydrones.com/profiles/blogs/precise-indoor-positioning-with-ultrawideband](http://diydrones.com/profiles/blogs/precise-indoor-positioning-with-ultrawideband)
> [name=Allen L]

> 在WoFOSS有聽到專案，有做「色狼地圖」正在進行中，詳細情形正在聯繫相關人員。
> [name=Jeane]

> （by Hsiao-Mei Lin）今年過年前一兩天，我們有辦跨國的 IGNITE HACKTHON 題目及是 \[ 色狼地圖\] 。 大家可參考影片， 1:15 始有細節喔!![http://ignite.globalfundforwomen.org/hackathonvideo](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4faf123b41ca84708b9f3016e9c866fc) 希望這個專案成立，延續下去！！
> [name=Jeane]

> 想問 WoFOSS 的 Data Sourse 
> [name=鄭凱文]

> 我是色狼地圖的開發者之一，我們主要完成的 feature 有地圖、雷達、事件通知系統(可勾選感興趣的縣市，一旦有新事件發生就會寄email通知)
> [name=卓家璘]

> 比較詳細介紹的影片是這個[https://www.youtube.com/watch?v=c1nkMfl2dwE&feature=youtu.be](https://www.youtube.com/watch?v=c1nkMfl2dwE&feature=youtu.be)
> [name=卓家璘]

> 這邊還有一些其他 feature 是未來有機會想去完成的，或許可以給你們參考看看~~~
> [name=卓家璘]

> 第一個是會根據時間變化去改變地圖上的顯示方式，譬如白天的時候是某些地點比較危險，那些地點就可以特別放最大顯示之類的，同理晚上也是
> [name=卓家璘]

> 第二個是會設計 ranking 機制，能去篩選出危險的十大區域之類的，然後可以跟婦聯會或警察局合作去加強巡邏，另外也會設計 timeout 機制，這樣可以刪除掉舊情報
> [name=卓家璘]

> 第三個是我們想實作成手機app，因為目前只有網頁版，所以雷達的效果其實不好
> [name=卓家璘]

> 第四個是希望不要只 focus 在台灣
> [name=卓家璘]

> 我們希望這禮拜能把app幹掉 T_T ，但被 Parse 的後台惡搞了。
> [name=鄭凱文]

> Hi, 看到這個題目很有興趣，有哪一塊我能幫上忙的嗎?
> [name=陳得妮]

> 有開發過前端web, iOS app的經驗
> [name=陳得妮]

> 現在iOS 和 Android 的 Github 在這，直接 fork 過去吃吃看
> [name=鄭凱文]

> [https://github.com/kevinphys/BatDrone](https://github.com/kevinphys/BatDrone)
> [name=鄭凱文]

> 需要一點前端設計師。我們是拿 Parse 上的例子來改，不過我自己沒寫過 Android 所以就拿例子拿來刻。
> [name=鄭凱文]

> 路過給一點意見：你們有考量**臺北機場四周禁止施放有礙飛航安全物體範圍(**自地面起禁止施放)和國防部劃定的**RCR16(陽明山)和RCR48(博愛特區)限航區**嗎? 扣除這些範圍，台北市大概就剩下萬華、文山、南港、北投、信義、大安等區可以施放無人機。
> [name=鄭兆庭]

> [http://web-gis2000.caa.gov.tw/caaPublic/(S(flwjwe3wkloaojm5dhqkiqdi))/Taipei.aspx](http://web-gis2000.caa.gov.tw/caaPublic/(S(flwjwe3wkloaojm5dhqkiqdi))/Taipei.aspx)
> [name=鄭兆庭]

> [http://goo.gl/Vo0L4C](http://goo.gl/Vo0L4C)
> [name=鄭兆庭]

> 我們很久之前有研究過飛航區的問題，但這次倒是忘記考量到了XD。
> [name=鄭凱文]

> 不過這無人機不會讓他飛太高（這樣也照不到人），禁航區可以先不要執行，法規的部分剛好 **@MiLu Li** 有在follow，這 BatDrone 在我想像不會飛超過10m。
> [name=鄭凱文]


> 剛剛終於...把資料轉一轉，弄到後台了T__T （第一次寫JS請多多指教）
> [name=鄭凱文]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2ca095f28625918906bca4e84a86a6bc)

> 現在遇到一個問題，現有資料有86筆（還是1-3月的資料...），後台只有轉出50筆。
> [name=鄭凱文]

> 原因是有些地址像是「中正區延平南路一帶商家(和平西路至愛國西路段)」這種帶有括號，籠統的描述，Google 轉經緯度的 API 無法處理，除了手動標點、或標範圍之外，有人有更好的想法嗎？
> [name=鄭凱文]

> 感謝 @鄭兆庭 的提醒與建議，確實法規是技術外另一個挑戰，而事實上除了航管相關法規令人頭痛以外，目前不明的適航相關認證更加頭痛。即使先跳開16和48限航，目前的概念會希望加入類似民航機的ADS-B的功能，可以有效的降低意外的發生，而配合航管則是第一順位(天條，不可抗逆)，畢竟沒有辦法把握每一架民航機或直升機有裝設ADS-B。其餘的部分，可能要等到更詳細的法規出來，才有辦法看出端倪。
> [name=Milu L]

## 附錄

### Parse sample code - Anywall

1.  [https://parse.com/tutorials](https://parse.com/tutorials)
2.  [https://parse.com/tutorials/anywall](https://parse.com/tutorials/anywall)
3.  [GeoCoding in Google Maps(Parse Cloud code)](http://stackoverflow.com/questions/25926293/geocoding-with-google-maps-api-via-parse-cloud-code)






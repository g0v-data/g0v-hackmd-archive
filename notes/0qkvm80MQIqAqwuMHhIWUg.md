---
title: "大協作世代 Age of Collaboration @ g0v summit 2014"
tags: g0v-summit,hackpad
---

# 大協作世代 Age of Collaboration @ g0v summit 2014

> [點此觀看原始內容](https://g0v.hackpad.tw/Zp5xamd13gI)

more info: [g0v summit 2014 hackfoldr](http://beta.hackfoldr.org/g0v-summit-2014)

現場直播網址 (live url)  [http://youtu.be/-zBqNp-FOYw](http://youtu.be/-zBqNp-FOYw)
錄影紀錄網址 (video url)
照片紀錄網址 (photos url)


↓文字轉播、線上討論↓

## Poplus

slides url
（亂入：可先看高村長的 Poplus 的介紹　[http://blog.clkao.org/post/197828/poplus-global-civic-hacking-community](http://blog.clkao.org/post/197828/poplus-global-civic-hacking-community)　）

head 是狗 XD
[http://popit.poplus.org/](http://popit.poplus.org/)
[http://mapit.poplus.org/](http://mapit.poplus.org/)
[https://www.fixmystreet.com/](https://www.fixmystreet.com/)
[https://www.mysociety.org/](https://www.mysociety.org/)
[http://mapit.mysociety.org/](http://mapit.mysociety.org/)
[http://www.theyworkforyou.com/](http://www.theyworkforyou.com/)

Fundings and volunteers are the primary resources. Avoid keeping your volunteers(e.g. developers) building the infrastructure over and over again. That would be very frustrating... Get them to the application parts.

open source is not enough
- documentation
- community
- support
- story

[http://poplus.org/get-involved](http://poplus.org/get-involved)

Q：把服務切得很細對開發者是很棒的，但是對於一般大眾是否會難以理解/使用，得要先到 A 再到 B、C、...
A：如之前提的 [http://www.theyworkforyou.com/mp/10257/philip\_hammond/runnymede\_and_weybridge](http://www.theyworkforyou.com/mp/10257/philip_hammond/runnymede_and_weybridge) 的確 work。而且拆成獨立元件會讓開發者更願意使用。
Q：你們如何鼓勵大家更多參與 poplus
A：這是個很困難的問題。他們有使用 google hangout 做聚會，也有提供錄影。


## 解放政府圖檔資料行動：用影像辨識來處理政府資料吧～

slides url
ronnywang 王向榮
[http://ronny.tw/data/](http://ronny.tw/data/)

R2 嵌投影片直播 [https://www.youtube.com/watch?v=yRRgAqcwONg](https://www.youtube.com/watch?v=yRRgAqcwONg)

我是很愛爬資料的人，是從實價登錄開始的，這很有成就感，程式寫好了之後，睡一覺醒來，資料就爬好了，然後睡覺對社會還是有貢獻（大笑）
爬資料很重要的是，爬完後才有raw data 可以用。如果我們只有財政部的資料，是看不出分界點的，但是有了raw data 就可以看得到它的差異。
1995年英國政治爆出發票的醜聞，很多亂七八糟的東西都有拿來報發票，英國把5500 篇的單據公告，衛報的記者把它們丟到網路上做成小遊戲，大家再看到隨機一筆資料檢視是否有問題，短短八十小時內就有十幾萬筆資料被檢視過。後來約一百多名的議員因此而道歉或宣布不再參選。還回的金額約五百多萬歐元。
2010/01年海地的地震，大家開始根據衛星圖上的圖在地圖上畫路線，幾天之後就有很詳盡的地圖讓救災人員可以使用，連房子間的小巷都可以看得到。  [http://www.openstreetmap.o](http://www.openstreetmap.o)
[http://vimeo.com/9182869](http://vimeo.com/9182869)

斧頭幫：[http://axe.g0v.tw/](http://axe.g0v.tw/)

「那個公民團體... 不要講公民團體四個字好了，公民團體最近蠻黑的」

之後我想到GOOGLE 的ReCAPTCHA的故事（驗證碼）去幫書的掃描辨識更精準，也用此法去辨認門牌號碼。所以我們政治獻金是不是也可以用這個方法。
就把圖都丟在PIXNET 上，接著開始研究要是做CAPTCHA要一格格怎麼切框線，先找到 OPENCV HOUGH TRANSFORM，但是發現很悲劇，有些會漏抓一條線或多抓一條線，共有一千多筆是這樣。所以就接受他人建議自訂演算法，這個演算法就可以正確95%，剩下的就人工解決，這個切豆腐平台就好了。
24小時內鄉民就全部輸入完成，共一萬多人完成。每一筆至少有五個人去輸入，所以打錯也沒關係，反正挑最多答案的那個就行了。
每一次去印都要印兩三千張，後來就用九張的縮印，但會比較不清楚，故後來改成二乘二大小。
後來有個阿美語字典，方敏英編的，有人就想是不是有相同的方法去把它數位化。
它不像政治獻金可以有表格線可以切豆腐，不過這次就是切豆絲了。再寫說明檔如何輸入，大約卅多小時，大家就把它的數位化完成了。

WMS好處是可以減少資料傳輸量讓瀏覽更快速，但是無法得到原始資料。所以主要是給人做視覺上比對，而不是做分析。
要是可以做成GeoJSON的格式，就可以在網路上畫出來，但政府都是用WMS，我就想可不可以用掃描的方式去做。若是在場有對影像處理有興趣的人，可以來討論一下看有沒有更好的辦法。
也是希望透過這樣的分享，未來大家碰到掃描圖檔或地圖，透過open data，整個社會可以得到更多有益的事情。
> NYPL-[Map polygon and feature extractor](https://github.com/NYPL/map-vectorizer)： 很久之前看到的給掃描紙本地圖，不知道是否可以協助WMTS圖磚OCR成GeoJSON？ [http://blog.gslin.org/archives/2013/09/01/3508/](http://blog.gslin.org/archives/2013/09/01/3508/) [http://www.gislounge.com/automating-extracting-gis-data-scanned-maps/](http://www.gislounge.com/automating-extracting-gis-data-scanned-maps/)
> [name=HoshiLiu]


## 開放內容的衝擊-開放街圖和維基百科在臺發展，以及如何可能影響政府

slides url
如何取得資料，及取得資料的困境（有一點悲傷，啊，怎麼那麼多困境）
開放街圖的資料，維基百科的文化性資料
如何取得資料（買，合法的抄，砍！）
我其實受惠於 ronnywang 砍下來的資料，就不用去轉資料格式。但若無法取得該怎麼辦？
用手動 copy ，還是用 API 去抓。
群眾共編的資料（到2014/11/03)
維基百科　英文4638088筆條目　中文786450筆條目
開放街圖　38G的點線面資料

開放街圖 OpenStreetMap
2004年成立，受維基百科的啟發，為群眾共編的地圖，開放的地理圖資。
與政府的互動（先談最後結果比較好的例子）
紐約市建築匯入，
英國Free Our Data運動
英國衛報發動，2006年，英國開放資料運動的前身，抗議政府拿納稅人錢收集的資料卻要收費
結果Royal Mail 釋出116000郵筒位置，　有人將此位置轉成文字csv 格式，有人拿資料去做網站，結果Royal Mail 宣稱要告，又或是郵筒位置不精確，不過後來都還有公開）
與政府打交道最壞的狀況
不一定理你　－　繼續遊說，號召鄉民行動
不一定能達成雙方滿意的協議，可能會告你

維基愛古蹟
資料要求格式，去要的時候，去電文化資產局表明要，承辦人表示請上網去查詢。資料匯出是pdf ，且沒有經緯度資料。承辦人不懂需要的格式，最後只好採g0v 方式去砍資料。
數位典藏計畫
共十年的長期計畫，將典藏單位的文物數位化。期待加值運用，但很多鎖在資料庫裡（現況）。以故宮為例，就放出表格類的清單，但也沒有照片。（之後故宮人員說明：其實是有低階的照片，用於研究用）
Copyfraud
將原應屬於公有領域的內容，視為有著作權，過度衍生其權利。
政府應放出更多資料，以促進新形態產業發展
資料的開放性需不斷努力，也許群眾編輯的方式能補充開放政府資料的不足。
臉書社團
OpenStreetMap 台灣
臺灣維基社群　Taiwan Wikipedia Community

「國立故宮博物院 Open Data 規範作法公告」
[http://www.npm.gov.tw/opendata/datarule.html](http://www.npm.gov.tw/opendata/datarule.html)
本院Open Data專區公告：
（一）國立故宮博物院於各Open Data專區內開放特定圖像資料供各界運用，使用者（自然人、法人或團體）無需先行申請，惟需遵守下列條件：
1.  使用者不得將本院資料再授權、交付或散佈予第三人以任何方式加以利用。


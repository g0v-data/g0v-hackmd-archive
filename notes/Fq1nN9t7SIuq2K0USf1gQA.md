---
tags: GIS
---

# 黑心建商地圖

> [點此觀看過往版本內容](https://g0v.hackpad.tw/fs4ojVnb1tX)


## 說明

### 緣由

維冠之流的一屋建商會一直換名字蓋房子，詳 Sway 文
[https://www.facebook.com/swayhouse/posts/967133943321767](https://www.facebook.com/swayhouse/posts/967133943321767)

### 目的

讓使用者可以輕易查詢每棟建築的建商以及該建商老闆的背景資訊，改名史、凶工地、偷工減料史、危樓、...etc.
> 比較麻煩的也許是營建業經常有 "借牌" 的情況，也就是名義建商與實際建商不是同樣的單位，加上經常使用人頭公司操作，大概得透過戶政相關系統才有辦法抓出完整的資料。使用傳聞資訊容易會有誤認的情況，跳坑的人容易上法院？
> [name=Finjon K]

> 「黑心」的定義可能要討論一下耶。例如的確有可能符合當時法規但法規並非周延，而導致建築災損，這類情況是否稱之為「黑心」呢？似乎可參考《建築結構安全與國家管制義務》書中內容
> [name=che l]

> 另，探討範疇是否涵蓋「學校建築、公共建築、公共設施(橋樑道路水工構造物..)」，黑心營建？
> [name=che l]

> 到時候可能要換個名字，把黑心兩字拿掉，改成可疑之類的，比較不會被告被抗議 XD
> [name=ET B]

> 建築物營造究責說明：[https://www.facebook.com/teayen/posts/10204296096562596](https://www.facebook.com/teayen/posts/10204296096562596)
> [name=che l]

> 如何讓黑心商吐出黑心錢（陳瑞仁）[http://m.appledaily.com.tw/appledaily/article/headline/20160217/37065961/](http://m.appledaily.com.tw/appledaily/article/headline/20160217/37065961/)
> [name=che l]



### 初步討論

- [https://www.facebook.com/ETBlue/posts/10206395834027391?comment\_id=10206395854347899&reply\_comment\_id=10206396666888212&notif\_t=feed_comment](https://www.facebook.com/ETBlue/posts/10206395834027391?comment_id=10206395854347899&reply_comment_id=10206396666888212&notif_t=feed_comment)
- 台北建築年代地圖 [https://ronnywang.cartodb.com/tables/taipei/public/map](https://ronnywang.cartodb.com/tables/taipei/public/map)
    - ronny 介紹文章 [http://ronny.wang/blog/post/35346775-taipei,-taiwan%3A-the-age-of-the-city](http://ronny.wang/blog/post/35346775-taipei,-taiwan%3A-the-age-of-the-city)
- 我國建築資料庫內，到底有什麼呢？初步參考台北市 105年度「建築管理系統軟體維護案」的標案需求內容
    - 需求書：[https://drive.google.com/drive/folders/0B5EFNXxRFP3wRS1FY3pfZUdiUUU](https://drive.google.com/drive/folders/0B5EFNXxRFP3wRS1FY3pfZUdiUUU)
    - 摘錄：1\. 建築執照申請書電子化系統（ASP），包含
        - （1）建照管理：建照、雜照、拆照、變更設計、變更使用許可申請等。
        - （2）施工管理：使照申請、開工申報、施工勘驗、開工展期、竣工展期等。
        - （3）使用管理：變更使用竣工、室內裝修許可、室內裝修竣工申請等。
        - （4）廣告物管理：廣雜、廣使申請等。
        - （5）系統管理。
        - ...
- 確保住家結構安全新思維 / 陳啟中建築師 [https://www.facebook.com/chichung.chen.33/posts/1224472980928022](https://www.facebook.com/chichung.chen.33/posts/1224472980928022)
- https://104.formosa21.org.tw/


## 需要資料

### 建築物基本資料

- [ ] 建築登記資料，地址、建商公司名、營造公司名、是否有容積獎勵、門牌... etc.
- 全台建築使用執照查詢，可用地址查到建築師跟營造廠。 [http://cpabm.cpami.gov.tw/twmap.jsp](http://cpabm.cpami.gov.tw/twmap.jsp)
- by ronny 從 全國建築管理資訊系統 爬下來的全台灣建築執照名單，目前資料更新時間為 2013/12 [https://github.com/ronnywang/cpabm.cpami.gov.tw](https://github.com/ronnywang/cpabm.cpami.gov.tw)
- by ronny 台北市建管處建照記錄 [http://tpebuilding.g0v.ronny.tw/?year=102](http://tpebuilding.g0v.ronny.tw/?year=102)
- 台北市 105年10月31日以前使用執照摘要，資料開放平臺
    - [http://data.taipei/opendata/datalist/datasetMeta?oid=c876ff02-af2e-4eb8-bd33-d444f5052733](http://data.taipei/opendata/datalist/datasetMeta?oid=c876ff02-af2e-4eb8-bd33-d444f5052733)
- [http://m.mobile01.com/topicdetail.php?f=457&t=4727254](http://m.mobile01.com/topicdetail.php?f=457&t=4727254)
- 我於臺北市資料開放平台上，詢問建築執照、使用執照、開放空間資料集，建築管理處的回覆如下：
    - 親愛的市民您好，您於本府資料開放平台上建議關於本處權管資料開放一事，本處處理情形敬覆如後：「建築執照與使用執照法定既有欄位」及「開放空間名稱，開放空間經緯度，開放空間輪廓polygon，管理單位，是否屬於獎勵容積機制」因分屬不同權責科室，且部分資料恐屬個資，不便於臺北市政府資料開放平臺開放下載，本處將盡速研擬評估可開放之資料範圍，供民眾於臺北市政府資料開放平臺下載，造成您的不便之處，敬請見諒。如您對於本案仍有疑義，請電洽本處資訊室。謝謝您來信與指教，並祝您 健康愉快 臺北市建築管理工程處 資訊室。
- 建物框
    - 台中市建物資料含建物框
        - [https://www.facebook.com/media/set/?set=oa.1858409871113677&type=1](https://www.facebook.com/media/set/?set=oa.1858409871113677&type=1)
    - 此類資料的規格課題盤點頁面
        - [https://g0v.hackpad.tw/ZU4Pzs4OTiA](https://g0v.hackpad.tw/ZU4Pzs4OTiA)
- [ ] 建商、營造商工商登記資料，老闆改名史
- [ ] 過去新聞資料，以老闆名字、現在公司、過往公司、建築物名稱為關鍵字查詢結果

### 危險建築資料

a.災害潛勢
- [ ] 經濟部中央地質調查所斷層帶查詢 [http://fault.moeacgs.gov.tw/MgFault/Home/pageMap?LFun=1](http://fault.moeacgs.gov.tw/MgFault/Home/pageMap?LFun=1)
- [ ] 土壤液化區（北市） [https://www.ptt.cc/bbs/Gossiping/M.1455060741.A.F2B.html](https://www.ptt.cc/bbs/Gossiping/M.1455060741.A.F2B.html) （已做成 google map： [https://www.google.com/maps/d/viewer?mid=zpK61YlmU1So.kRIsP\_nyy-WM&hl=en\_US](https://www.google.com/maps/d/viewer?mid=zpK61YlmU1So.kRIsP_nyy-WM&hl=en_US) ）

b.各種危害狀況的建築名單
- [ ] 全國山坡地住宅社區列管名單 [https://g0v.hackpad.com/vPVD4quuLyf](https://g0v.hackpad.com/vPVD4quuLyf)（目前仍為表格圖檔，需要 OCR；說明：山坡地住宅列管評分標準主要分為監測系統、邊坡穩定性、擋土牆、排水問題等項目評分，缺失最多者列為Ａ級(代表安全狀態不穩定，要限期改善)、次之為Ｂ級(代表要加強監測)，較少者為Ｃ級(代表穩定但須持續維護，並自行檢視設施狀況)。
- [ ] （台北市）震災受損建築物勘估結果一覽表（皆為「黃單」資料；「紅單」必須立即拆除故並未記錄於檔案；資料會持續更新） [http://dba.gov.taipei/np.asp?ctNode=74773&mp=118021](http://dba.gov.taipei/np.asp?ctNode=74773&mp=118021)
    - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1a765ae39249e9b0ba638fc577f55641)
    - （台南市） [https://www.facebook.com/k.olc.tw/posts/540718169434984](https://www.facebook.com/k.olc.tw/posts/540718169434984)
- [ ] （台北市）高氯離子混凝土建築物（海砂屋）列管名冊1050201 [http://dba.gov.taipei/ct.asp?xItem=67428677&ctNode=32514&mp=118021](http://dba.gov.taipei/ct.asp?xItem=67428677&ctNode=32514&mp=118021)（資料會持續更新；xls 格式，截圖如下）
    - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ed9d9900a29ce9d62f7451ec6cc1f8f2)
- [ ] 輻射屋
    -  「有遭受放射性污染之虞」之建築物清冊
        - 發佈日期： 2017-04-05
            - [http://www.aec.gov.tw/newsdetail/board/2959.html](http://www.aec.gov.tw/newsdetail/board/2959.html)
        - 發佈日期： 2014-08-01
            - [http://www.aec.gov.tw/newsdetail/board/1054.html](http://www.aec.gov.tw/newsdetail/board/1054.html)
            - Map [https://batchgeo.com/map/7d8f0996c71a343d21e4860b0588c6c0](https://batchgeo.com/map/7d8f0996c71a343d21e4860b0588c6c0)
    - 本系統僅限於查詢民國71至73年間建造且經偵測評估其目前年劑量仍達1毫西弗以上之輻射屋地址。其它年份建造建物及1毫西弗以下之輻射屋均不適用本系統，請另洽「輻射屋免付費諮詢專線：0800-076-678」
        - [http://ramdar.aec.gov.tw/](http://ramdar.aec.gov.tw/)
    - 輻射屋資訊表，原能會偵測確認輻射從建築物牆柱放出，但未公布，至1992年，輻射鋼筋大規模污染建物事件才陸續被揭發。影響統計：清查確認共189處、300多棟、1663戶輻射屋，約1萬3300人受影響，受害者最高累積暴露劑量為1751毫西弗（100毫西弗以上，就算高劑量）
        - [http://www.appledaily.com.tw/appledaily/article/headline/20160215/37063174/](http://www.appledaily.com.tw/appledaily/article/headline/20160215/37063174/)

### 非法建築資料

a.假住宅
- 「聯上建築」在高雄市澄清湖旁的湖美學建案，將旅館當住宅賣
    - [https://www.facebook.com/swayhouse/posts/1092555470779613](https://www.facebook.com/swayhouse/posts/1092555470779613)


## 類似專案

- 危險房屋社區(海砂/幅射/地震/窄巷)
    - [https://drive.google.com/open?id=1AV4tCAJdkRTnYMp5-nvzMxa3yjs&usp=sharing](https://drive.google.com/open?id=1AV4tCAJdkRTnYMp5-nvzMxa3yjs&usp=sharing)
- 台北市屋齡地圖
    - [https://imdataman.github.io/taipei-house-age-map/](https://imdataman.github.io/taipei-house-age-map/)
- 城市建築地圖
    - [https://g0v.hackpad.com/sh7utuV1NfX](https://g0v.hackpad.com/sh7utuV1NfX)
- Imminently Dangerous Properties in Philadelphia
    - [http://www.philly.com/philly/infographics/405521075.html](http://www.philly.com/philly/infographics/405521075.html)
        - The Department of Licenses and Inspections has developed a computer model that helps inspectors prioritize the most dangerous vacant homes and target them for demolition. The model takes all sorts of publicly available data, such as property reassessment data, unpaid water bills, crime statistics and prior L&I violations. In addition, the department has access to laser imaging that can detect collapsed roofs, a sign of a structurally dangerous building.
- 綠建築標章名單，被認證建築物的實際用電結果
    - [https://www.facebook.com/groups/taipowerhackathon2017/permalink/335828506840043/](https://www.facebook.com/groups/taipowerhackathon2017/permalink/335828506840043/)
- 香港堅離地圖
    - 「堅離地圖」，從中原數據、美聯物業等多個房地產網資訊網，搜羅全港逾150個主要屋苑的單位面積、平均呎價、地理位置、交通配套等公開資料，製作成互動樓市地圖。希望讀者可從資料庫掌握實用資料，過程中也可以看到買樓可以有幾「離地」。
    - [https://www.hkcnews.com/kennedy-map/](https://www.hkcnews.com/kennedy-map/)




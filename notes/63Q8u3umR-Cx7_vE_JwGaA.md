---
title: "全國海岸淨灘認養：資料應用與網站功能"
tags: hackpad
---

# 全國海岸淨灘認養：資料應用與網站功能

> [點此觀看原始內容](https://g0v.hackpad.tw/yFUEA0Ahsvp)


## 資料

### 「海岸淨灘認養系統」官方網頁

- [https://ecolife2.epa.gov.tw/coastal/Default.aspx](https://ecolife2.epa.gov.tw/coastal/Default.aspx)

### 社群朋友爬下的資料

- csv 資料集
    - [https://github.com/ronnywang/ecolife-sea/blob/master/out2.csv](https://github.com/ronnywang/ecolife-sea/blob/master/out2.csv)
- geojson 資料集
    - by ronny  [https://github.com/ronnywang/ecolife-sea/blob/master/output.geojson](https://github.com/ronnywang/ecolife-sea/blob/master/output.geojson)
    - by Finjon Kiang  [https://gist.github.com/kiang/db9a9cf38da072b1546df7ac962c3b93](https://gist.github.com/kiang/db9a9cf38da072b1546df7ac962c3b93)

### Demo 地圖試作

- [王向榮](https://www.facebook.com/ronny.wang.tw?fref=ufi)
    - 幫忙爬出海岸線認養區段名稱與認養單位資料
        - [https://goo.gl/36QXdx](https://goo.gl/36QXdx)
        - 遇到的狀況是  有三種情況
            - 1\. 完全無認養單位，認養單位和期間會是空白
            - 2\. 有認養單位，一個海岸線可能會有多筆
            - 3\. 錯誤，網址連進去就遇到錯誤，我抓不到資料，例如雲林台西海岸線。
    - 地圖
        - [https://goo.gl/ZYPNYc](https://goo.gl/ZYPNYc)
        - 綠色表示已經有人認領的海岸線，黃色表示還沒人認領。
- [江明宗](https://www.facebook.com/finjonkiang?hc_location=ufi) 也做了這塊
    - geojson [http://bl.ocks.org/anonymous/raw/32c916ac48c2dc78ce688ce59e297370/](http://bl.ocks.org/anonymous/raw/32c916ac48c2dc78ce688ce59e297370/)
    - Google My Map [https://goo.gl/nqGWmg](https://goo.gl/nqGWmg)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_455000bf018f04eeb201359a52a203e8)
- 在魚客松，海南機團隊試著進一步做些雛型
    - [https://hackmd.io/CwDgbARhDMBmwFphgEwFYkQIxYQTjgBME0UI8BjaMgU0NCA=](https://hackmd.io/CwDgbARhDMBmwFphgEwFYkQIxYQTjgBME0UI8BjaMgU0NCA=)

## 整理資料應用與網站功能各種構想

- chewei: 似乎有一些可以發展成網站功能的構想
- Lee: 如果有各路神仙願意跳坑架網站，那我會建議參考路殺社 [https://roadkill.tw/page/237](https://roadkill.tw/page/237)的模式 ，還有海岸線認養的平台 [https://ecolife2.epa.gov.tw/coastal/Default.aspx](https://ecolife2.epa.gov.tw/coastal/Default.aspx) ，這樣應該可整合出一個比較優的平台。
- 受污染環境通報平台，他的優點是哪邊有受污染，可以很直接的從List上看出來，點進去可以看到照片與週邊環境過去的對照圖。缺點是只有網頁版，而且不是使用Google地圖，對應上不夠直接，回報方式不夠貼近使用者，也不像路殺社那樣有APP可以用，在定位與通報的即時性上很不方便。
- 就淨灘而言，有很多單位是真的做的很不錯，比方「RE-THINK 重新思考」，很有行動力與號召力，持續性也很棒，在很多地方起了帶頭的作用。但他們平時也有自己的工作，只能在有限時間，以跳點環島的方式發起淨灘活動。…糟糕！這樣亂七八糟的寫下去，應該很多人會看不下去，下面我用條列式來寫，我認為的需求好了，請大家做個參考，希望有看到的朋友能集思廣益，一起完善這個坑。


### 盤點輔助此議題的各種圖層與資料

將資料疊在更多種類的圖層上，比較好瞭解海岸性質
- 衛星圖層
- 土地使用分區
- 國土利用調查圖
- 海埔地籍圖
    - [http://gis.rchss.sinica.edu.tw/mapdap/wp-content/uploads/2012/04/MAP\_WRA\_ReclaimedLandMap.pdf](http://gis.rchss.sinica.edu.tw/mapdap/wp-content/uploads/2012/04/MAP_WRA_ReclaimedLandMap.pdf)

棲地復育類的行動
- [新聞稿 2017世界海洋日-海洋棲地復育水中造林](https://www.fa.gov.tw/cht/NewsPaper/content.aspx?id=1417&chk=740d1b74-6f9d-4568-b0f3-07d1baabf4f8)
- [幫珊瑚搬家，讓九孔池的珊瑚搬家到野外的環境](https://www.facebook.com/eangel85/videos/723196055085877/)


### 呈現可認養之外的區段現況

全國海岸線至少有1985公里，目前海岸線認養網站所劃設的可認養區段，應該是沒有包含管制區與一些海港或是特別危險區域無法開放。除特別需要管制的區域外，理當各區域海岸都可認養，要不也能各別標示，明訂管理單位。

後經查證，海岸認養系統劃設一萬公里海岸供企業社團認養，目前資料不完全的原因，是因尚有部分縣市環保局未能完整提供轄內可認養海岸段。

有關上述系統中全國海岸段資料係根據內政部國土測繪中心繪製，該中心已有開放段籍圖WMS服務，可至國土測繪圖資網路地圖服務網站([http://maps.nlsc.gov.tw/)查詢](http://maps.nlsc.gov.tw/)查詢)。環保署規劃明年於海岸淨灘認養系統新增淨灘活動申請之功能，並同步開放全國可認養海岸區段資料。

海岸有什麼？
- 台灣漁港列表 [https://goo.gl/Skn7Bt](https://goo.gl/Skn7Bt)
- 中央管海堤 [http://data.gov.tw/node/32731](http://data.gov.tw/node/32731)
- 行政院海岸巡防署 服務據點查詢 [https://goo.gl/X](https://goo.gl/XDzTwz)[DzTwz](https://goo.gl/XDzTwz)
- 濕地 [https://goo.gl/9AbmYU](https://goo.gl/9AbmYU)
- 臺灣河流列表 [https://goo.gl/YtLykQ](https://goo.gl/YtLykQ)
> 盤點「海」相關資料 [https://g0v.hackpad.tw/iQV6M1XO6wj](https://g0v.hackpad.tw/iQV6M1XO6wj)
> [name=che l]

> 盤點「淡水」相關資料 [https://g0v.hackpad.tw/yRRVlfb5oJg](https://g0v.hackpad.tw/yRRVlfb5oJg)
> [name=che l]

- 海面下 [https://www.facebook.com/permalink.php?story_fbid=1968148960068051&id=100006188977770](https://www.facebook.com/permalink.php?story_fbid=1968148960068051&id=100006188977770)

### 回報海岸垃圾污染狀況

參考路殺社回報平台( [https://goo.gl/9S4RDK](https://goo.gl/9S4RDK) )，改為海岸垃圾污染狀況，供全國各地認養海岸與想淨灘的團體作參考。

回報內容
- 回報海岸垃圾污染狀況，以事先準備相關工具與人力
    - 垃圾物品的特性
    - 海岸地質與地形，例如沙灘或礁岩...等
    - 可參考《淨灘行動記錄表》內的欄位項目 [https://www.sow.org.tw/blog/iccdataforms](https://www.sow.org.tw/blog/iccdataforms)
- 可同時進行的生態保育行動所需要的資訊
    - 當地寄居蟹大小以供螺殼投放做參考
- [https://openlittermap.com/](https://openlittermap.com/)


### 協助發起活動、建立在地中長期工作支援站

有任何團體想發起淨灘，都可以透過平台發佈，這樣各地方的淨灘團體，也可以跟認養當地海岸的企業團體聯繫，取得較好的淨灘工具或其他資源。如果在呈現出各地響應人數，這樣認養單位也比較容易揪到人淨灘。

荒野保護協會也有一個系統 [http://cleanocean.sow.org.tw/](http://cleanocean.sow.org.tw/)，但沒跟臉書活動串一起，所以不好用。我有嘗試用臉書做一個串連，但google表單與文件的使用我不熟悉，應該是可以有可以自動同步的串連方式
- 發佈用的專頁 [https://goo.gl/JnyPn8](https://goo.gl/JnyPn8)
- 互動用的社團 [https://goo.gl/wtnQKj](https://goo.gl/wtnQKj)

建立在地中長期工作支援站
- 在海岸當地，找到可以放置好用淨灘工具的空間、合作單位
- 找到當地可以配合監測拍海岸垃圾協力者，當垃圾過多，則發出訊息，引動後續清理活動

避免活動重疊
- 「因為跟台南環保局所舉辦的活動地點重疊，所以我們改往南方一些、據稱更髒的漁光島。」
    - 來源：[https://www.facebook.com/rethink.tw/photos/a.468748256539884.1073741828.465616346853075/1423367827744584/?type=3&theater](https://www.facebook.com/rethink.tw/photos/a.468748256539884.1073741828.465616346853075/1423367827744584/?type=3&theater)

淨灘活動試舉例：
- 20170716 基隆大武崙
    - [https://www.facebook.com/rethink.tw/photos/a.468748256539884.1073741828.465616346853075/1421391544608879/?type=3&theater](https://www.facebook.com/rethink.tw/photos/a.468748256539884.1073741828.465616346853075/1421391544608879/?type=3&theater)


### 視覺辨識哪一段目前沒有人認養

就目前認養海岸平台上的狀況，可以看出有些海岸有多組認養單位，有的海岸則無單位認養，最好能有直覺一點的地圖呈現，這樣就能有一點比較性，正面的刺激當地的淨灘活動。


### 汙染嚴重性與淨灘頻率

淨灘的週期性呈現，有的海岸常有人淨灘，有的卻是少有人去。如果能在地圖上呈現污染狀況的顏色，再搭配距上次該地淨灘的時間以顏色區分(紅黃綠作為警示)，這樣應該會比較有直覺感。



## 構想緣由

社團討論串：[https://www.facebook.com/groups/g0v.general/permalink/1334113696665033/](https://www.facebook.com/groups/g0v.general/permalink/1334113696665033/)

Lee: 會想要上來找支援，是因為過去參加過的淨灘應該不下二十次了，但最早是因為關心寄居蟹跟環境生態問題，所以才開始淨灘。這五六年來一直覺得很多淨灘的方式有問題。最近又觀察了海岸認養系統後([https://ecolife2.epa.gov.tw/coastal/Default.aspx](https://ecolife2.epa.gov.tw/coastal/Default.aspx) )，直覺那平台很不好用，不夠透明(認養海岸的運作方式)，不夠直覺化(UI/UX做的很差)，甚至覺得這網站最後會變成交差了事，但根本無法起作用的網站。

糟糕！…不熟悉這裡的編輯模式，貼上後發現很難做修改，如果覺得讀的不通順，或許點下方連結到G0V後勤中心，比較能看出脈絡。是真的很不習慣，目前止做到複製貼上發表，但還沒搞懂該怎麼看段落位置做編輯。暫時先擱置，等晚點有時間再來瞭解。
[https://www.facebook.com/groups/g0v.general/permalink/1334113696665033/?comment\_id=1342775125798890&reply\_comment\_id=1345297298880006&comment\_tracking=](https://www.facebook.com/groups/g0v.general/permalink/1334113696665033/?comment_id=1342775125798890&reply_comment_id=1345297298880006&comment_tracking=)[{"tn"%3A"R9"}](https://www.facebook.com/groups/g0v.general/permalink/1334113696665033/?comment_id=1342775125798890&reply_comment_id=1345297298880006&comment_tracking=%7B%22tn%22%3A%22R9%22%7D)

之前曾看過一個受污染環境通報的平台，但這兩天一直找不到，暫時無法提供參考。本來我是想等我比較瞭解我要做什麼後，再跟大家提案，現在看到Che Wei Liu 我說：「還有一些管制區，比如我上禮拜日去基隆和平島的寶拉灣淨灘，那邊就沒有劃設可認養區塊。還有許多港區應該也是可以開放認養才是，因為平常就有一些地方團體在淨港清垃圾。」

這讓我比較有信心點了！一開始我還不知怎麼提出協助，還是Che Wei Liu 幫我貼上G0V後勤中心，才又有人跳出來幫我撈資料。其實一開始我只是想知道有哪些開放認養的海岸線與認養的企業團體List，想一處一處的跑，找到可以放置好用淨灘工具的空間、找到當地可以配合監測拍海岸垃圾多到需要揪很多人去清理的人。......抱歉！又飄掉了，但不寫出來，似乎也不好。

找不到的那網站就這我外行人來說，做的是挺不錯的，至少比很多公家單位的網站好很多。但問題是，那個網站就我的觀察的結果是沒有幾件舉報，搞不好也因為這樣而被刪掉了。

若能多在週間舉辦淨灘，應該吸引到不少服務業的朋友加入淨灘。能增加很多淨灘人力與縮短淨灘週期的時間。現有的淨灘活動舉辦的時間，大多是利用週六日，若能在週間試辦，應該可以吸引到一些服務業的朋友參加，因為他們多半只能在週間休息，週末假日反而要上班，不能參加淨灘。

全國海岸線背景資料：
- 表 1、105 年度第 2 期各縣市自然及人工海岸線比例一覽表
    - 全國海岸線長1,985,315公尺 ＝1,985.315公里
    - 資料來源： [http://www.cpami.gov.tw/chinese/filesys/file/chinese/dept/rp3/rp10603061052.pdf](http://www.cpami.gov.tw/chinese/filesys/file/chinese/dept/rp3/rp10603061052.pdf)




相關應用
1.  [https://github.com/letsdoitworld/World-Cleanup-Day](https://github.com/letsdoitworld/World-Cleanup-Day)
2.  海岸清潔計劃 Macao Coastal Cleanup [https://www.facebook.com/macaocoastalcleanup/](https://www.facebook.com/macaocoastalcleanup/)



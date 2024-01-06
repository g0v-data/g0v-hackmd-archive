---
title: "公有土地資料特性討論"
tags: 公有地大行動,hackpad
---

# 公有土地資料特性討論

> [點此觀看原始內容](https://g0v.hackpad.tw/ZjlnDReZvPr)


## 功能性的部分

（[http://gis.rchss.sinica.edu.tw/qgis/?p=1112](http://gis.rchss.sinica.edu.tw/qgis/?p=1112)）：「在國內，地籍圖是土地管理相關業務通用的地理資料，不論房屋買賣、土地買賣、產權管理、地價稅徵收、工程開發都會涉及到地籍圖使用。法院公告法拍屋、法拍土地、政府機關公告國有土地拍賣等等業務上，也都是利用地籍的地段、地號資訊來指涉空間範圍。**之前有介紹內政部地政司地籍圖資網路便民服務系統，可以查詢某一個地段地號的範圍，並套疊在Google Earth上，十分便民；本文則是希望進一步介紹查詢結果，如何下載地籍界線kml檔，再透過QGIS軟體，並套疊其他GIS圖層，例如街道圖、台灣堡圖、斷層線圖等。**」

###  關於地號與地址，面積與形狀


- 有些資料只有地號，理想上，如果我們有 GIS 地籍圖，其實是可以把該筆地號的邊界形狀也呈現出來，問題是，GIS 地籍圖是要動態地更新的，基本上應該只有地政司持續更新，我個人是覺得，哪天路上撿到了每年都更新的完整台灣測繪地籍圖系統，那就可以用地號連帶著邊界形狀一起呈現每筆資料
    - [https://osmtw.hackpad.com/Open-Geo-Data-for-Government-5YtEoKVphQF](https://osmtw.hackpad.com/Open-Geo-Data-for-Government-5YtEoKVphQF)
    - 地號與其地號對應的邊界座標 api
    - 話說地號和地址對應經緯度，據說有上千萬筆data entry，還有maintain更新、正確性問題
    - [http://whgis.nlsc.gov.tw/](http://whgis.nlsc.gov.tw/) -> 國圖查詢展示 -\> then can get 地號 from a point.
    - Draw a shape over the boundaries, then can download its KML!
    - [http://easymap.land.moi.gov.tw/K02Web/K02Land.jsp](http://easymap.land.moi.gov.tw/K02Web/K02Land.jsp) can see 地籍圖 and neighboring...
    - [http://navimap.land.moi.gov.tw/](http://navimap.land.moi.gov.tw/)
    - [http://ngis.afasi.gov.tw/](http://ngis.afasi.gov.tw/)
    - [http://landquery.taichung.gov.tw/query/noncityland.jsp](http://landquery.taichung.gov.tw/query/noncityland.jsp) can look up each parcel's
    - 山坡地保育區、林業用地  and size.
    - 臺北市數值地籍地段圖
    - [http://data.taipei.gov.tw/opendata/apply/NewDataContent?oid=0D9364CD-1677-4EAB-827B-7DA8E37785EB#](http://data.taipei.gov.tw/opendata/apply/NewDataContent?oid=0D9364CD-1677-4EAB-827B-7DA8E37785EB#)
    - 國土測繪圖資網路地圖服務地標資訊
    - [https://github.com/ronnywang/maps.nlsc.gov.tw/tree/master/landmark](https://github.com/ronnywang/maps.nlsc.gov.tw/tree/master/landmark)

- 所以，把地號轉成地址，繼而成為經緯度，來落點；面積，就以同面積的圓形來呈現，即上回黑客松時所討論的呈現方式
- 但是，我稍微看了一下幾個土地資料，其實縱然是兩筆土地，但是其實是相鄰著，地號也連續著，理想上，如果可以辨識出來，這兩筆土地是地號向連地理相鄰，那麼，不排除可以整合呈現。但是也很難講這樣就一定比較好，因為對於地政與財政系統來說，他們還是會保留土地的單筆單筆。

### 關於資料：土地大小


- 目前有看到的公有土地資料，若以面積大小來分類，其實可以分成：
1.  空軍總部、華光社區、南港瓶蓋工廠，這個種類，是指標個案，通常也是真的超大的，可能是非常多筆的土地一起被規範在某一種開發方式之下
2.  單塊可能多筆相鄰著的土地，大小介於５００坪以上，但不是指標個案，或者是說靜靜地等待著某個開發計畫從天而降，但是因為目前國有財產法規定，５００坪以上禁售，所以值得成為一個項目
3.  單塊可能多筆相鄰著的土地，大小介於＿＿＿＿坪～５００坪之間，還是可以被標售，這個尺度，其實也很適合在地的社區去活用他，關心他，提出關於這塊地的各種公共使用的願景
4.  0.2 平方公尺這種，基本上，小到不行，但是要小心的就是說，看單筆很小，或許這筆土地臨著某一塊大的；或者是說，縱使很小，可是就是被劃入都市更新範圍之內，需要監督他的公共過程的這種

### 關於資料：火線程度


- 這部分就比較是實際的實情的判斷與指認，包含使用瑕疵、有開發計畫、程序合法但實情很怪的種種
1.  ==**公用中**==，例如總統府，說實在，如果沒有太怪異的實際情形，好像暫且就讓他去吧，基本上這個範疇的土地與建築物的資料，有就有，沒有也沒關係
2.  ==**公用中但有瑕疵者**==，像是姚瑞中所統計的的全台灣蚊子館，有些其實也是公用中的狀態，但是都空掉，所以也不是說，只要是公用中就不用關心，再舉一個例子，容積獎勵的開放空間與停車場，經常都被偷偷地圍起來私家使用，或是不當租用給特定的人士
3.  ==**非公用**==，但也還沒有什麼開發計畫在身上，不過其實就是預期有一些開發動作，也才會讓這塊土地變成非公用狀態
4.  ==**身上有明確的開發計畫了！**==公用與非公用都有可能身上突然掉下來一個開發計畫，種類繁多（標租、標售、設定地上權、參與都市更新、眷改、聯合開發...）；地上權設定招標成功之後，開發了之後，我自己會把這種項目歸類在這裡，例如，台北京站，地主為台北市政府，由日勝生集團投資興建，地上權使用年限45年，到時候，是要還給政府的，又例如 BOT；其實都是長時間的開發與使用公有資產的過程
5.  ==**已私有化的**==，那些曾經是公有土地的，但目前已私有化的土地，例如帝寶以前是中廣的土地
6.  ==**其他名目上有灰色地帶的公共資產土地**==：官股事業的土地、學產地

### 關於地圖化這件事情


- 我今天若想要找到台北市大安區的已有的公有土地資料，我不用進入地圖化系統的環節，直接從資料庫這塊，使用者可以設定好自己想要篩出來的條件（台北市大安區），來【匯出類似 excel 格式】的可能性。至於這批（台北市大安區）資料的地圖化，會不會就是獨立成一個處理環節，開放這位使用者輸入這批資料後來呈現為地圖，使用者自己建構這批資料的地圖化與網址，【產出地圖另開視窗(?)】
- 依照前一點的邏輯來看，整體大地圖，當然就是呈現整個資料庫，且是網站的主頁面重點元素之一

### 關於WIKI


- WIKI 這部分的功能，蠻多細節要確認的；基本上，可以分成，已經確認是公有土地的土地，讓一般人來增寫該筆土地的前世今生，甚至是願景；
- 另外就是，我們資料庫裡面沒有，而一般人覺得這塊是公有土地，但他也不能明確確認這塊地倒底是不是公有土地；其實後者的狀況下，只要有地址，是可以透過既有的系統去查到是否是公有土地、經管機關等細節，但是要有手續費

### 關於一筆土地資料的基本格式欄位


- 必定要有
1) 要能地圖化的話，地址／地號／經緯度／GPS，至少要有一種
2) 要能地圖化的話，單筆大小一定要有
3) 經管機關
4) 火線上的緣由，至少要有一種

- 從必定要有，所衍生的，一定也可以查到的
1) 該筆土地歷年轉手資料，基本上從有紀錄的時代開始都可以查的到
2) 土地使用分區，因為那跟地理位置是綁在一起的
3) 鄰里位置，也是跟地理位置是綁在一起的，可以方便一般人體會位置。台灣行政區界地理資訊 ([http://request.data.g0v.tw/questions/7/](http://request.data.g0v.tw/questions/7/))
4) 火線相關的衍生資料：圖資
例如說，國產署招標，單筆土地會有圖片，這是國產署必定要附上的東西
例如說，公有土地被劃入都市更新，一定會有更新範圍的圖
...
5) 火線相關的衍生資料：進程
例如說，華光社區目前正在處於都市計畫細部計畫擬定階段(?)
例如說，空軍總部目前正在由國發會所發包的規劃單位進行規劃，同時間也讓其他局處機關運用現有的空間做暫時性的活動
...
6) 該筆土地以及其開發案，是否被納入訴訟案件
例如說，台灣蠻野心足協會所協助的環境訴訟案件
例如說，大同區文萌樓的都市更新案中有近半數的公有土地，之間有司法訴訟案件
...

- 有更好
1) 該筆土地的，現況照片
2) 該筆資料的形成時間
3) 該筆資料的製作單位
4) 該筆資料匯入本資料庫的時間
5) 該筆資料的取得方法
6) 相關上位指導政策，例如華光社區的開發節奏與目標，是與行政院國有土地活化小組的決策裁示緊密相關的
7) 該筆土地的前世今生，例如「兩年賺三十億」：民國95年，台北市大安區信義聯勤俱樂部以64億元標售給新光人壽；兩年後，民國97年新光人壽以101億元賣給元利建設。2014年元利建設的豪宅快要落成了，新聞([http://www.appledaily.com.tw/.../headline/20100304/32336480/](http://www.appledaily.com.tw/.../headline/20100304/32336480/))
4) 這塊地的公民願景，例如台北市南港瓶蓋工廠，公部門希望剷掉舊建築物來開發土地，但是在地與許多文史團體倡議進行文化資產保存，也實際做許多調查，提出許多具有說服力的證據去爭取文化資產的審議


- The dark side of data：[http://radar.oreilly.com/2012/07/the-dark-side-of-data.html](http://radar.oreilly.com/2012/07/the-dark-side-of-data.html)
    - 摘錄自劉嘉凱：現在大家都很強調API，但機器權跟人權要並重，否則會造成新的數位落差，只推API會造成只有能解讀API的人看得懂這些資料。印度也在做開放資料，開放地籍資料，結果都是大財團去買這些資料來做土地開發，也是一種數位落差，如此大財團賺更多錢，貧富差距就增加了。（來源：政府資料開放加值應用研究分析書面報告 www.ndc.gov.tw/dn.aspx?uid=15534）

### 資料來源與信任感討論


- [15:40:57](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#57)[chewei](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/57)抱歉...\[請問\] 各位好，我是公有地大行動專案的哲瑋，想請問大家一個假設性的資料問題，就是說，公有土地資料，對公務部門來說是盡量不要開放比較好，這是普遍的基本態度，若有民意代表要求提供時，才會針對民意代表的要求，來提供相關的土地資料；==**若今天，透過某些管道，預期是代議者所提供的公有土地資料，大家認為這份資料的來源路徑、得以出現這批資料的來龍去脈，是否要全部地公開呢？**==
- [15:42:49](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#59)[chewei](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/59)我自己會想到的是，若要我相信這批資料真的是公部門的資料，若我能知道來龍去脈，也會比較確信資料是真的，而不是假的或是根本不是公部門的資料
- [15:45:42](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#60)[jbytw](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/60)==**我同意，要透明才能查證和被監督**==
- [15:46:06](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#61)[chewei](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/61)假設我手邊有一份台北市的公有土地的資料，我告訴大家，這份資料是某立委協助拿到的或是提供的，但無法說清楚確實是誰在何時如何地拿到資料，那，像這樣的表述，大家會覺得如何呢？
- [15:46:51](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#62)[jbytw](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/62)==**如果一般民眾沒有管道查證這批資料的正確性，的確會引起懷疑**==
- [15:47:02](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#63)[chewei](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/63)當然，對於代議者來說，或者是有點內部響應者來說，這樣的話就==**很矮由了**==XD
- [15:49:07](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#64)[jbytw](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/64)是啊，也要顧及他們的意願
- [15:49:52](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#65)[chewei](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/65)我想到的妥協方案是，我們有這批資料，但我因為無法說這批資料的過程，所以我就說，這批資料是需要查證的資料，我也不是很確定，但是大家可以到現場看看拍照，因為都是實際的地號與地理位置
- [15:53:04](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#66)[jbytw](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/66)google map 鍵盤查證可行嗎？
- [16:01:56](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#67)[chewei](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/67)例如像這樣 [https://www.filepicker.io/api/file/P7142YhzRY6yA1teA4nX](https://www.filepicker.io/api/file/P7142YhzRY6yA1teA4nX) 查證的話，要寫信去問管理機關耶 @_@ 他們應該不會理會個人
- [16:04:29](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#68)[jbytw](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/68)(我想得太簡單，以為只要查證存在與否)
- [16:04:46](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#69)[jbytw](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/69)那現場拍照就有辦法查證嗎？
- [16:05:22](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#70)[chewei](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/70)就是說，如果取得過程無法完全公開，那麼，查證的這個環節，就變的是行政機關的回應，感覺上，==**行政機關應該不會理我們，甚至以後想個行政措施說，強力執行資料外漏漏洞(例如代議、或是得標廠商的該專案公共使用用途所拿到的資料...等等等)**==
- [16:05:41](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#71)[jbytw](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/71)最好的方式，當然是讓他們願意被公開
- [16:06:37](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#72)[jbytw](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/72)不然就像現在監察院政治獻金切豆腐的情況一樣，先大家累一點鍵盤重製文件，之後有發現可疑之處，再想辦法施壓公開
- [16:07:19](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#73)[chewei](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/73)==**疑似公有土地待查證平台XD**==
- [16:07:30](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#74)[jbytw](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/74)哈哈有點像這樣
- [16:07:57](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#75)[jbytw](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/75)==**然後也可以有一個讓大家匿名提供資料的方式**==
- [16:08:16](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#76)[jbytw](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/76)但此種管道獲得的資訊，屬性都是\[待查證\]
- [16:08:22](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#77)[chewei](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/77)金價洗杯掐死這款機關本位主義的倫
- [16:08:59](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#78)[jbytw](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/78)資料獲取困難，就是他們的技術性阻擋啊
- [16:11:30](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#79)[*](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/79)Lee1092 個人主觀認為 他們不想公開的資料的都是有鬼的 zz..
- [16:12:29](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#80)[chewei](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/80)我們是有想到讓大家提供資料的可能性，因為每筆土地也有前世今生，且大家對於生活周遭的土地比較熟悉，其實經常是市區生活路徑上，就一定有等待開發的公有土地
- [16:17:18](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#81)[chewei](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/81)例如我今天早上去吃早餐的路上 \[20140711 松江路94號公有閒置空地-拍照\] [https://www.filepicker.io/api/file/XfAfo44RrSFfVPbDVFfi](https://www.filepicker.io/api/file/XfAfo44RrSFfVPbDVFfi)
- [16:19:54](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#82)[chewei](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/82)當然，這樣的資料，是否是公有土地，會是 \[待查證\] 的狀態，\[查證\] 只能由管理機關以公文的方式宣告(目前我只想的到這個查證法)
- [16:23:31](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#83)[chewei](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/83)==**若要保護資料來源，則 \[公部門明確活化中的公有土地資料，因為要公開招標所以就會有公開資料\] \+ \[公有地大搜查線 & 查證機制\]**==；還是說，公布資料取得方法與資料的同時，公部門不會因此而害臊閉俗起來，反而很開心地連破多關
- [16:47:58](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#93)[Rhozan](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/93)有保密需求的消息管道可以參考國外==**乳摸消息的評級設定，將來源可信度依過去爆料正確性及其他可信證據量化 EX:**== ==[**http://goo.gl/aXghIn**](http://goo.gl/aXghIn)==
- [16:59:09](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#96)[jbytw](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/96)Lee1092: ++ 我個人也是這樣主觀認為
- [17:04:20](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#100)[kiang](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/100)目前政治獻金資料粉絲頁被轉貼最多次的就是「下去領五百」那篇( 120,768 people reached )，其他了不起就六萬，所以==**分析資料找話題**==才是王道啊 XD
- [17:09:24](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#104)[chewei](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/104)中正區 成功段三小段 00110000 4307 1 1 4307 中華民國 財政部國有財產署 行政專用區(三)
- [17:09:24](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#105)[chewei](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/105)中正區 成功段三小段 00110001 277 1 1 277 中華民國 財政部國有財產署 行政專用區(三)
- [17:09:24](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#106)[chewei](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/106)「下去領五百」，「兩年賺三十億」：民國95年，台北市大安區信義聯勤俱樂部以64億元標售給新光人壽；兩年後，民國97年新光人壽以101億元賣給元利建設。2014年元利建設的豪宅快要落成了，新聞：拋棄對國有土地的舊思維（黃惠欣）([http://www.appledaily.com.tw/appledaily/article/headline/20100304/32336480/](http://www.appledaily.com.tw/appledaily/article/headline/20100304/32336480/))
- [17:09:56](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#108)[chewei](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/108)ＸＤ 那兩個地號請忽略～～～～～
- [17:10:08](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#109)[kiang](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/109)XD
- [17:10:20](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#110)[kiang](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/110)我想說有人要爆料呢
- [17:12:17](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#111)[Rhozan](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/111)==**如果難得有人願意開放資料，但會因強制公開來源而退卻，不如討論看看能不能制定出適合g0v方式的爆料系統，說不定可以引出超多內幕**==
- [17:13:54](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#112)[chewei](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/112)ㄝ，好啦那兩個地號其實是現在林森南路與市民大道交叉口的土地，現在是草原，之後應該是等著被設定地上權開發之類的
- [17:14:01](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#113)[S3p_lin](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/113)沒有人的編號, 像是 anonymous1234 這樣, 對外保密身分, 對內真的有需要知道來源的話也有得查
- [17:26:06](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11#123)[chewei](http://logbot.g0v.tw/channel/g0v.tw/2014-07-11/123)Rhozan: 土地開發過程&公有土地的資料，若是有爆料系統應該就蠻多采多姿的

另一次的討論：

- 怎麼辦呢，是不是要問提供者，同不同意讓我們，同步說明如何取得放在網站上，這樣公部門會不會又更戒備
- 只是說這樣的來源變成唯一且難以複製延伸，這樣好不好??兩難啊…
- 要不然就是要搭配說，好，這批真的是某某代議者，透過合法便籤的方式，請行政機關提供，我們感謝他，其實，這是我們全民都可以做的事情，請你寫信打電話給你的分區立委或是議員，也請他為我們爭取公有土地資料。如果民氣上大家很認同的話，好像可以，但很難講咧...




---
title: "公有地資料庫"
tags: 公有地大行動,hackpad
---

# 公有地資料庫

> [點此觀看原始內容](https://g0v.hackpad.tw/5ofp8l2IWiT)

「公有地資料庫」涉及：
1.  資料內容，與土地行政制度直接相關，例如段小段地號、地址、容積、建蔽率...
2.  屬於地理資訊系統
3.  允許群眾協作、編寫
4.  土地資料所衍生的社會運動、倡議情境、行動裝置應用...
5.  需要透過不同資料集之間的比對，來凸顯公有地的議題

## 關於這個「資料庫」的設想與願望：

功能
1.  地號資料，地圖化
2.  與其他議題資料庫，相互對照。例如公部門都市更新的地號資料庫，原住民委員會公布的傳統領域範圍(kmz)，環境訴訟案件、蚊子館app、豪宅容積獎勵開放空間app(待建構)
3.  資料本身可以自動更新
4.  砍柴之後的資料，針對某筆土地的個案描述與新聞，需要工人智慧，涉及群眾協作，請見[「群眾協力於公有土地議題上可以發揮什麼」的探討](http://hackfoldr.org/POPonFire/lxX0NRqBoQD)；應該進一步考量預期使用者的數位工具使用程度與偏好，使用者的介面；也希望能夠以非程式專業者，也可以大量批次操作的介面
5.  曾設想過有一個功能，是，使用者可以從龐大的資料庫中，選擇「資料出圖」這個功能環節，讓資料庫本身是文書格式之類的狀態，【地理格式+資料內容】複合屬性，來提供繪圖程式與出圖成果，例如使用者選擇以「地號」+「複合型描述(該地號形狀、面積數值、產權描述...等等)」，或是「GPS」+「原住民傳統領域內容」｜我今天若想要找到台北市大安區的已有的公有土地資料，我不用進入地圖化系統的環節，直接從資料庫這塊，使用者可以設定好自己想要篩出來的條件（台北市大安區），來【匯出類似 excel 格式】的可能性。至於這批（台北市大安區）資料的地圖化，會不會就是獨立成一個處理環節，開放這位使用者輸入這批資料後來呈現為地圖，使用者自己建構這批資料的地圖化與網址，【產出地圖另開視窗(?)】。若是公有地大行動的主網站，則也是依照前述邏輯來看，整體大地圖，當然就是呈現整個資料庫，且是網站的主頁面重點｜這個概念跟「圖層」有點不同
6.  一般人可檢索查詢，並且進行資料分析，或是擷取出他想要的公有土地資料
7.  授權格式：CC0｜Open Database License (ODbL)
8.  實境遊戲的應用與行動裝置的應用可能

### 滿足上述願望，可能的對策方案

- ~方案一：地號的形狀描繪起來，呈現於 Open Street Map~
- ~方案二：地號資料倒入 wikidata，群眾於wikidata上編修~
- 方案三：一個開放群眾編輯的【==**巨量表格**== ==(地號-面積-新聞-現地描述-照片網址-一條計算公式-...)==】的 csv +【==**資料轉出於某類型的地圖平台**==】**功能環節元件(ex地號轉地圖)，**且這個元件可以處理例如地號數字轉出位置與形狀(因應不同國情)
> chewei 畫張關聯圖
> [name=che l]

> 這個想法很類似「[時間地圖 Timemapper](http://www.playpcesor.com/2014/08/time-map.html)」
> [name=che l]

> [《Empire Building》数据可视化项目的开发思路文章](http://datanews.blog.caixin.com/?p=203)，"整个项目是基于HTML5的Canvas技术开发的，没有用到其它第三方可视化库。"
> [name=che l]

- 方案四：...


## 關於地號比對

- 用地號查是否正在都更：見天龍特公地網站
- 用地號查地質敏感：[http://gis.moeacgs.gov.tw/gwh/gsb97-1/sys_2014b/](http://gis.moeacgs.gov.tw/gwh/gsb97-1/sys_2014b/)


## 一些現況事實

已知的現況：
- ==**「地號」**==屬於當地國家所創造的規格，應該會持續存在很久，政權換了通常也沿用，清朝地契-日治時期地號-國民政府GIS。地號這種格式的資料，包括其位置與測繪資訊(面積與形狀)，會隨著時間而更新與重劃調整，是公部門的業務範圍，也只有公部門有能力進行資料的測繪、維護更新
- 公部門之間的土地開發資料庫，例如都市更新的資料庫，也是以地號為基礎
- 近年興起的「群眾協作」系統，Open Street Map , wikidata , localwiki ...
- [路殺社](http://roadkill.tw/)考量議題內涵，則是運用 GPS、公路標示，來註明位置
- 地理 \+ 資料：各自有許多種呈現的規格
    - ［地理+資料］複合屬性，來提供繪圖程式與出圖成果，例如使用者選擇以「地號」+「複合型描述(該地號形狀、面積數值、產權描述...等等)」，這個情境可以初步參考：[DZ1984天龍特公地製作過程文章](http://dz1984.info/articles/Taipei_POP/)
    - 考量時間維度，會不會有什麼樣貌？案例：[海平面上升未來預測](http://flood.firetree.net/)
    - 考量資料協作系統，會不會有什麼樣貌？案例：[城市修理站](https://maps.google.com.tw/maps/ms?msa=0&msid=217100401029752166110.0004d9c794ba8af50962d&dg=feature)、[路殺社](https://www.facebook.com/groups/roadkilled/)
    - 考量遊程化建構，會不會有什麼樣貌？案例 ：[Odyssey 旅程式呈現工具](http://cartodb.github.io/odyssey.js/)、[裨海紀遊](https://www.youtube.com/watch?v=lcMntFlk6LU)
    - 有時候，該位置的地形、地下深度、水面深度、地面高度，也會衍生而來
- The [**GeoCanvas**](http://www.synthicity.com/geocanvas) platform is our initial release of technology, and provides users with incredibly simple and fast 3D data visualization for exploring their cities and regions.
- [**UrbanCanvas**](http://www.synthicity.com/urbancanvas) is coming soon, and adds numerous features, including 3D buildings with an extensible library of building styles, editing tools using paint-style interfaces, and scenarios and timelines for visualizing alternative development options.
- Our [**UrbanSim**](http://www.synthicity.com/urbansim) platform is the state-of-the-art in analyzing the impacts of transportation and land use investments and regulations, on real estate market outcomes.
- 蠻多重要的議題，『綁在』土地與不動產身上，或是說，空間分布是該種資料，其不可或缺的重要資料構成特質，例如：
    - 原住民保留地、自治區與傳統領域
    - 文化資產指認與保存
    - 公有土地
    - 蚊子館
    - 路平專案
    - 督視人
    - 建照
    - 不動產實價登錄
    - 環評審議
    - 地質潛勢
    - 一個限定範圍內的資料指認，例如一個公園內的植栽調查、一個鄉鎮內的水圳文史調查、某個流域..
- 除了地理位置定位之外，每一筆資料富含著很多圖文資料或是延伸閱讀，每一筆資料都很有故事，例如：火線上的公有土地：【空軍總部土地活化】，依時間來看，2014之前為空軍使用、2014由不同局處進行暫時性活用、2014國發會以標案的方式進行整體規畫案發包由日商得標；牽涉大的中央國土活化政策背景與決策
- 這些資料，有時候會需要『民間的觀點』來進行彙整，許多時候也需要調查報導式的個案了解後，匯聚於同一資料庫中，人工指認，通報，人工登記，例如：「火線上」的公有土地、蚊子館、督視人..等專案。
- 關於民眾上傳現地照片的系統，國外蠻多開源的，像是
- uReport [https://github.com/City-of-Bloomington/uReport](https://github.com/City-of-Bloomington/uReport)
- fixmystreet(by mySociety) [https://github.com/mysociety/fixmystreet/](https://github.com/mysociety/fixmystreet/)
- shareabouts(by openplans) [http://openplans.org/shareabouts/](http://openplans.org/shareabouts/)
- 或許需要再進一步了解土地測量的實際過程，多邊形的各個頂點，用什麼格式與方法作記錄，國家所提供的樁點基準扮演什麼樣的角色
- 我們需要地圖來做什麼呢？移動、決策、判斷、說服、證實
- GeoThing 究心科技：讓資訊在對的時間給對的人｜如果是公有土地與國土議題呢？土地規劃的決策圈擴及到誰？主管機關？利害關係對象？議題協作與意見發表者？世界公民？
- 《下班時間扭轉未來》以知識運作的社會關係擴散性、構成性，來歸納出四種社群組織：
    1.  私有分享：以未加協調的個體表達呈現「凍結分享」
    2.  共有分享：發生在一群協調者之間，激盪圈子內共有的火花
    3.  公有分享：出現在一群協作者積極創造公共資源時，允許自由加入行為
    4.  公民分享：這類團體會主動常是改造社會文化或架構，同時增進「局外人」的福祉
- [Rapid Web Visualisations with d3plus](https://popluscon.hackpad.com/Rapid-Web-Visualisations-with-d3plus-Grey-Room-last-session-Wednesday-XEsMMe0y0tC)
- [http://dataviva.info/apps](http://dataviva.info/apps)  : lots of beautiful visualisations <-- data in JSON format being presented with d3plus
- 「公有地大行動」專案，目前的架構：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c62b032092307834432dd2e809dd71b5)
- User enters data ([video](http://youtu.be/LqOjzhYHkhI?t=11m18s))
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c56b27c321119c555e9e431371ad9ce8)




---
tags: tree,臺北市政府開放資料黑客松,hackpad
---

# [舊的]都市樹木與行道樹資料


最新內容請至
https://g0v.hackmd.io/JMUJM1qoRku71FUzaabeaQ?view





## 緣起

- 之前就在想 Whiski 的這個梗：
    「巴黎就有人把行道樹資料和過敏源資料結合，並推出手機應用程式，造福了廣大有花粉過敏症的市民。」 [http://www.vita.tw/2012/11/open-data.html](http://www.vita.tw/2012/11/open-data.html)
- 這兩天出現 Muyueh 說「正在煩惱要怎麼樣校對行道樹資料...」
    [https://www.facebook.com/groups/odtwn/permalink/1191664634181286/](https://www.facebook.com/groups/odtwn/permalink/1191664634181286/)
- 然後最近剛好在協助台北市資訊局籌劃活動...
- 於是...先來想像一下資料欄位？

## 什麼是好的行道樹資料？

### 正面表列：

以下由最優先到次優先：
- 要有正確的經緯度
- 要有樹種、樹名
> 不曉得是否有國際的名稱或編碼系統，可以援用？
> [name=che l]

- 樹齡（種植年份）？
- 胸徑（直徑）？
- 樹高
- 是否為法定受保護樹木
- 樹穴圖層、樹穴狀況、耕種空間的狀況
- 目前的認養人
> 請參考此認養措施「公園及行道樹徵求乾爹媽 認養每年省5千餘萬公帑」[http://www.gov.taipei/ct.asp?xItem=178994940&ctNode=5158&mp=100001](http://www.gov.taipei/ct.asp?xItem=178994940&ctNode=5158&mp=100001)
> [name=che l]

- 該筆資料建置的時間
- 相關資料若是由其他圖面書面資料而來，則必須說明來源，例如ＯＯ工程竣工圖、或是某某年的行道樹調查計畫

### 負面表列：

- 不要用DGN？
> DGN是特定軟體使用的檔案格式，有點像是xls的感覺。
> [name=林立哲]

> 先提供一下資訊局同仁的回應，後續會再與公園處等單位討論：
> [name=Charles C]

> 「五顆星的問題：來源DGN檔有point和polyline兩層，取用point圖層即可轉換符合GIS應用需求的圖資，polyline圖層是業務單位為了方便看圖使用的圖例，五顆星應該是從梅花狀(代表某樹種)轉成的」
> [name=Charles C]

- 不要用TWD67 （據說已經有了TWD97）
> 已經有TWD97！　不過有可能原始資料就是用TWD67的座標系統紀錄。 坐標系統定義好，顯示上應該都沒有問題，但是轉換套疊後可能都繪有誤差產生。(會產生偏移)
> [name=林立哲]

- 不要出現梅花五棵...
> 這應該也是原始資料轉檔的問題，因為原始的圖資，圖面上的樹需要一個符號，就找了一個梅花五棵的符號當樹，所以在圖上看到梅花五棵就知道這是樹。
> [name=林立哲]

> 這個好像真的很難突破耶，因為這個好像是 cad 技術人員的使用習慣，以及施工圖說的圖學...
> [name=che l]

- 不要資料錯誤
> 我覺得處理地理資訊的資料最後可能都會遇到套疊的問題，明明樹就應該長在人行道上，但是因為誤差卻跑到路中間 XDDD  資料來源越多 這種圖面上不合邏輯的情況可能會越多。
> [name=林立哲]

> 應該可以進一步檢視，測繪實務上現場的定位方法
> [name=che l]


## 參考


都市林綜論
- 政策研究 The Strategic Framework on Mediterranean Forests and the Tlemcen Declaration
    - [https://www.researchgate.net/publication/264457076\_Montpellier\_green_city](https://www.researchgate.net/publication/264457076_Montpellier_green_city)
- 《The World’s Urban Forests: History, Composition, Design, Function and Management》
    - [http://www.landscape.cn/interactive/book/books/2017/0424/181399.html](http://www.landscape.cn/interactive/book/books/2017/0424/181399.html)
- Exploring the Green Canopy in cities around the world
    - [http://senseable.mit.edu/treepedia](http://senseable.mit.edu/treepedia)

### 國際城市作法

- London
    - [https://maps.london.gov.uk/trees/](https://maps.london.gov.uk/trees/)
- 巴黎
    - [http://opendata.paris.fr/explore/dataset/arbresalignementparis2010/?tab=table](http://opendata.paris.fr/explore/dataset/arbresalignementparis2010/?tab=table) （好像還有別的？）
    - 法文版欄位說明： [https://www.dropbox.com/s/gomtk8ltyyxyvr2/VilleParis\_DEVE\_ARBRES\_ALIGNEMENT\_description\_compl%C3%A9mentaire\_201407.doc?dl=0](https://www.dropbox.com/s/gomtk8ltyyxyvr2/VilleParis_DEVE_ARBRES_ALIGNEMENT_description_compl%C3%A9mentaire_201407.doc?dl=0)
- 墨爾本
    - urban forest strategy：2012-2032
        - [http://www.melbourne.vic.gov.au/community/parks-open-spaces/urban-forest/Pages/urban-forest.aspx](http://www.melbourne.vic.gov.au/community/parks-open-spaces/urban-forest/Pages/urban-forest.aspx)
    - 澳洲墨爾本都市行道樹地圖（與市民互動、溝通）：
        - [http://melbourneurbanforestvisual.com.au/](http://melbourneurbanforestvisual.com.au/)
    - 民眾參與都市樹木調查
        - [https://www.facebook.com/ecocityforum/posts/1097778183577068](https://www.facebook.com/ecocityforum/posts/1097778183577068)
    - 墨爾本的「投信樹」服務
        - [http://www.outside.hk/%E7%B5%A6%E5%A2%A8%E7%88%BE%E6%9C%AC%E7%9A%84%E6%A8%B9%E6%9C%A8%E5%AF%84%E4%BF%A1/](http://www.outside.hk/%E7%B5%A6%E5%A2%A8%E7%88%BE%E6%9C%AC%E7%9A%84%E6%A8%B9%E6%9C%A8%E5%AF%84%E4%BF%A1/)
        - 當局收到數以千計的郵件，而大部分並非關於樹木狀況，而是市民直接給自己心愛的木樹寫信，分享軼事，內容小至記述日常生活，大至抒發各種困惑，同時不忘讚美樹木的美貌、魅力。
- NYC
    - NYC Parks' TreesCount & Data Jam
        - [https://www.facebook.com/noneck/posts/10154368036303643](https://www.facebook.com/noneck/posts/10154368036303643)
        - Check out the new Street Tree Map! The results of the 2015 TreesCount census, an enormous city-wide volunteer effort including many Trees New York volunteers. We think you'll be pleased with the results. Click here: [https://tree-map.nycgovparks.org](https://tree-map.nycgovparks.org)
    - NYC Street Tree Map
        - [https://www.facebook.com/nycparks/posts/10155413343603082](https://www.facebook.com/nycparks/posts/10155413343603082)
    - 民間專案與企劃
        - [http://www.jillhubley.com/project/nyctrees/](http://www.jillhubley.com/project/nyctrees/)
        - If you have to meet someone in NYC - just enter both your addresses, and this map will suggest parks that are convenient to both of you. [https://youmeandatree.com](https://youmeandatree.com)
- 波特蘭
    - [https://www.facebook.com/RiChiTech/posts/1606462009401111](https://www.facebook.com/RiChiTech/posts/1606462009401111)
- Seattle
    - Urban Forest Management
- New Kensington counting trees
    - [http://www.govtech.com/dc/articles/Tree-Data-Collection-Helps-New-Kensington-Pa-Begin-Smart-City-Transformation.html](http://www.govtech.com/dc/articles/Tree-Data-Collection-Helps-New-Kensington-Pa-Begin-Smart-City-Transformation.html)
- Trees of the USA
    - [https://www.facebook.com/groups/d4sg.taiwan/permalink/1801376166805634/](https://www.facebook.com/groups/d4sg.taiwan/permalink/1801376166805634/)
- Vancouver
    - [http://data.vancouver.ca/datacatalogue/streetTrees.htm](http://data.vancouver.ca/datacatalogue/streetTrees.htm)
    - [https://mountainmath.ca/mountain_math/about](https://mountainmath.ca/mountain_math/about)
- HK
    - [https://www.facebook.com/trailwatch/posts/1376132082426369](https://www.facebook.com/trailwatch/posts/1376132082426369)
    - [https://www.facebook.com/groups/code4hk/permalink/1577645612303299/](https://www.facebook.com/groups/code4hk/permalink/1577645612303299/)
    - 古樹資料
        - [https://www.facebook.com/groups/code4hk/permalink/1586214054779788/](https://www.facebook.com/groups/code4hk/permalink/1586214054779788/)
- Singapore
    - [https://www.facebook.com/qingwang/posts/10156197106643879](https://www.facebook.com/qingwang/posts/10156197106643879)

中央政府
- 林務局「==樹==木普查方法及受保護==樹==木認定標準」草案
    - [http://www.forest.gov.tw/ct.asp?xItem=76840&ctNode=1917&mp=1](http://www.forest.gov.tw/ct.asp?xItem=76840&ctNode=1917&mp=1)

台北市
- 公部門資料來源
    - 文化局，據說「[臺北市保護樹木](http://data.taipei/opendata/datalist/datasetMeta/preview?id=d9d1140b-c2c3-405f-8dd1-7b87b00f6f53&rid=2615ee1b-08c7-4cc6-9ade-7cf1a81eb93d)」的資料較佳，有樹種、經緯度等
> 「受保護樹木資料比較完整，如下 [http://data.taipei/opendata/datalist/datasetMeta/preview?id=d9d1140b-c2c3-405f-8dd1-7b87b00f6f53&rid=2615ee1b-08c7-4cc6-9ade-7cf1a81eb93d](http://data.taipei/opendata/datalist/datasetMeta/preview?id=d9d1140b-c2c3-405f-8dd1-7b87b00f6f53&rid=2615ee1b-08c7-4cc6-9ade-7cf1a81eb93d)
> [name=Charles C]

> API - [http://data.taipei/opendata/datalist/apiAccess?scope=resourceAquire&rid=ddb80380-f1b3-4f8e-8016-7ed9cba571d5](http://data.taipei/opendata/datalist/apiAccess?scope=resourceAquire&rid=ddb80380-f1b3-4f8e-8016-7ed9cba571d5)」
> [name=Charles C]

    - 工務局公園路燈管理處
        - 臺北市行道樹查詢系統
            - [http://addr.taipei.gov.tw/aspx/showpark_main.aspx](http://addr.taipei.gov.tw/aspx/showpark_main.aspx)
            - [https://trees.gov.taipei/show/?treeid=JJ0011190055](https://trees.gov.taipei/show/?treeid=JJ0011190055)
        - 「公園綠地廣場」內的樹木資料，尚無？
        - 大安森林公園
            - [https://www.facebook.com/daan.friends/posts/1066022866809846](https://www.facebook.com/daan.friends/posts/1066022866809846)
        - 105年度臺北市行道樹普查勞務採購案
            - [http://gov.playgroup.com.tw/gov_notice/20151223210842445183#.Vovhcd9danM](http://gov.playgroup.com.tw/gov_notice/20151223210842445183#.Vovhcd9danM)
            - 北市行道樹資料準備更新惹，與上一次普查相比，這次會因應開放資料應用情境而調整普查方法或程序、資料欄位、呈現方式等內容嗎？摘錄採購案說明：臺北市近9萬株行道樹，本處自94年普查至今已逾10年，當初普查行道樹和現今狀況已有相當差異，為取得行道樹正確資料，於105年度辦理普查，未來樹木管理導入科技化、智慧化的方式，將本市行道樹進行定位及樹籍資料建置，提升維護管理效率。
            - 分為：1.樹木圖層 2.樹穴圖層
        - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fd8c29186c4a0b9e74c2ad49a638e8f4)
    - 工務局大地工程處山坡地或邊坡植樹資料
        -
    - 樹木銀行、移樹資料
        - [http://pwd.gov.taipei/fp.asp?fpage=cp&xItem=114919&CtNode=8941&mp=106001](http://pwd.gov.taipei/fp.asp?fpage=cp&xItem=114919&CtNode=8941&mp=106001)
    - 產業發展局，臺北市生物多樣性資料庫，有紀錄植物/喬木/樹木
        - [http://tpbiodiversity.lifescience.ntu.edu.tw/index1.asp](http://tpbiodiversity.lifescience.ntu.edu.tw/index1.asp)
- 臺北市政府之外的其他部門樹木資料來源
    - 台大校區(台北市)的樹木標示地圖 [http://map.ntu.edu.tw/ntutree/index.htm](http://map.ntu.edu.tw/ntutree/index.htm)
    - 植物園
    - 蟾蜍山樹木調查 [https://www.facebook.com/events/1699485663708073/permalink/1704091779914128/](https://www.facebook.com/events/1699485663708073/permalink/1704091779914128/)
    - 各類土地開發與公共工程案件中的資料
        - 現地調查階段的植栽資料
        - 完工後的植栽資料
- 臺北市樹木議題與規範蒐集
    - 臺北市政府工務局公園路燈工程管理處 園藝小學堂 行道樹樹種選擇原則
        - [https://pkl.gov.taipei/Content_List.aspx?n=C15B0193AD88F60E](https://pkl.gov.taipei/Content_List.aspx?n=C15B0193AD88F60E)
    - 文化局受保護老樹
        -

其他構想
- 《一棵樹公園》推廣手冊構想
- 臺灣都市林之生態分析-先驅計畫 A pilot study on adapting i-Tree Eco for Taiwan urban forest
    - [https://health.tfri.gov.tw/itreetw/](https://health.tfri.gov.tw/itreetw/)
    - [http://www.daanforestpark.org.tw/userfiles/files/05_20151111臺灣都市林之生態分析-先驅計畫.pdf](http://www.daanforestpark.org.tw/userfiles/files/05_20151111臺灣都市林之生態分析-先驅計畫.pdf)
    - i-Tree 模型是由美國林務署(USDA Forest Service) 於2006 年開發的都市林與社區林業分析及生態 系統服務效益評估之工具
    - 精確度高的樣地調查數據,得出都市林基本結構 (物種組成、樹木密度、徑級分佈、冠幅等),進 而得出其他結構(葉面積、生物量等)。然後再結 合當地的環境和氣候條件(溫度、濕度、空氣中 污染物濃度等),以及經濟發展水準核算出都市 林的經濟價值
- QRcode 掛牌
    - [https://www.facebook.com/k.olc.tw/posts/811497375690394](https://www.facebook.com/k.olc.tw/posts/811497375690394)
    - [https://www.facebook.com/groups/1077996995607474/](https://www.facebook.com/groups/1077996995607474/)




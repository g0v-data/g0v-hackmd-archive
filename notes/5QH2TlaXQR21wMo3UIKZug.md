---
tags: Disfactory, gis
---
# 空拍圖比對計畫-大家來找廠

## What's this project about
2020年上路的《工廠管理輔導法》明文規定，2016.5.20 之後的新增建工廠應該立即停水停電及拆除，之前的在 2022 年之前可以辦特定工廠登記走向就地合法

本計畫希望能讓鄉民比對 2016.5.20 前後衛星雲圖，去抓出農委會五萬筆資料中的疑似工廠位址上的建物是不是新增建物，可以集中火力去檢舉或是可以把台灣疑似工廠 pin 掃一遍。（來自農委會圖台的既有工廠在網站上的[範例](https://disfactory.tw/#map=16.48/120.10725717316735/23.23728779482019)) 完整五萬多筆資料 csv 在[這裏](https://github.com/Disfactory/Disfactory/blob/master/backend/fixtures/full-info.csv)

## 緣起
最近這一波使用者研究發現幾個點：
1. 居住或工作在農地附近
2. 因為高污染高噪音影響生活才上平台回報
3. 多是零星舉報，不會跟家人朋友討論，因為擔心地方人情壓力
=> 針對這批使用者做社群媒體宣傳可能很難，因為他們也幾乎不是從社群媒體上看到平台的，也不會分享，對於其他地區的違章工廠關心度也比較低。

- 於是之前在思考如何有更低門檻、都市居民也方便參與的貢獻方式。
- 想到可以對現有政府既有釋出的五萬多筆資料進行初步排查，找出其中屬於 2016.5.20 之後興建的違章工廠。

## 目的
- raise awareness
    - 讓更多鍵盤鄉民可以參與違章工廠議題
- 增加檢舉有把握的程度
- 比對出新增建的數量、位置，建置更健全的民間違章工廠資料庫以協助倡議
- 農委會每年會釋出新的點位，通常是 9 月-11月之間

### 倡議目標
- 國土計畫，農地農用
- 監督政府落實工輔法與配套措施

## Feature 可能型態
目前形式發想是直接切好圖片，用大家來找碴的方式做標記，初步也只對已有地號和經緯度的既有一次違章工廠做辨認標記。（參考政治獻金數位化專案）

也有在思考如果標記了五萬多個地點與衛星空照圖，所累積的資料是否能幫助未來程式自動抓出有新增建物的變異點或後續其他應用。

## TA
鍵盤鄉民
長期關注環保和土地相關議題的民眾

::: spoiler 技術確認區
### 標註體驗與流程 

我們有「框」資料嗎？
- 用地資料爬取歷程
    - https://github.com/ronnywang/disfactory-crawler

兩期影像對照標註：[手機版-figma](https://www.figma.com/proto/TVAEC28E3ojabGHc8BawbI/%E8%A1%9B%E6%98%9F%E7%A9%BA%E7%85%A7%E5%9C%96?node-id=50%3A2&scaling=min-zoom&page-id=0%3A2)
單期標註：[構想簡報](https://bit.ly/3gavl07)


### 影像圖資來源

評估原則
- 需求圖資的時間點
    - (1) 歷史衛星影像，以下文件簡稱「舊圖」
        - 考慮即報即拆行政實施的月份 ==2016.05==
        - 如果能取得==月份型影像==，則應該盡可能取得 2016.05 之前的 2016.05.16 ~ 2016.12.31 期間的圖資
        - 如果僅能取得==年份型影像==，則應使用 2015, 2017 這兩個年份，並歸納研判規則
        - 上述內容的[探討簡報](https://bit.ly/3gavl07)
    - (2) 最新的衛星影像，越新越好，以下文件簡稱「新圖」
        - 希望拍攝日期持續更新
- 圖資解析度：==人工肉眼在螢幕上可以辨認地貌物、看得出是廠房建築物或是農地==，解析度 1m 左右較佳
- 圖資授權：介接、截圖的法律風險要釐清
- 必須支援批次方案，給 5 萬個經緯度，取得圖片


#### 方案：SPOT + mapbox

##### 圖資
- 舊圖：使用 法國衛星 SPOT 2015, 2017 圖資，無雲，全台但沒有澎湖金門連江
    - 圖長[這個樣子](https://data.csrsr.ncu.edu.tw/SP/#SP2017NC_3857/ol3)
        - 考慮到研判規則，故使用 2015, 2017 這兩個年份，[規則探討簡報](https://bit.ly/3gavl07)
- 新圖：使用 mapbox satellite，wms，無雲，全球
    - 圖長[這個樣子](https://bit.ly/3z5TAFx)
- 基於圖資的研判方案：
    - [輔助用圖說解釋簡報](https://docs.google.com/presentation/d/1hyak0PdXA3CpxSC82T7ahmp0AbqjEJS2c3AcnhURpnw/edit)
        - 一、SPOT 2017，標註為 農地 的，即可歸類為「即報即拆」
        - 二、SPOT 2015，標註為 工廠 的，「不適用即報即拆」
        - 三、剩下的屬於「疑似」
    - 課題：
        - 「疑似」的筆數，是否會很多？
        - 假設可以調取「月份型」的資料，該如何構思要用哪一個月份、相應的研判規則是什麼？有部分地區有 2016/03/03~2016/05/19 的影像，BigGIS 圖臺上有收錄，這部分可以看[輔助用圖說解釋簡報](https://docs.google.com/presentation/d/1hyak0PdXA3CpxSC82T7ahmp0AbqjEJS2c3AcnhURpnw/edit)有擷取圖片顯示大概哪些地區有影像

##### 介接測試
- 測試方法1：直接從 SPOT, mapbox api 來取得圖片檔案 
    - ==小白嘗試中==
- 測試方法2：使用「carto 自製線上地圖服務」進行介接，以下我用 carto 的服務，製作三個年份的地圖，網址都可以套上經緯度，以下用同樣的「經緯度與縮放程度」：
    - 臺灣省彰化縣福興鄉 秀安段 (0335) 1072地號，經緯度 120.4316347, 24.0275228
        - https://disfactory.tw/#map=18.37/120.431543093463/24.02739377601256
    - 課題：
        - SPOT 提供介接僅提供到 zoom=17 縮放程度，似乎還是有點大，難確保使用者能聚焦
    - [2015 SPOT](https://classicdesign053.carto.com/builder/70fdbbea-6e06-4f79-a402-1a14d75f49b8/embed?state=%7B%22map%22%3A%7B%22ne%22%3A%5B24.023607442553732%2C120.42577286716552%5D%2C%22sw%22%3A%5B24.030976440723798%2C120.43798228260131%5D%2C%22center%22%3A%5B24.027291994452145%2C120.43187757488342%5D%2C%22zoom%22%3A17%7D%7D)
    - [2017 SPOT](https://classicdesign053.carto.com/builder/cb8d4f39-eef0-40c2-acda-cf67e082ab77/embed?state=%7B%22map%22%3A%7B%22ne%22%3A%5B24.023607442553732%2C120.42577286716552%5D%2C%22sw%22%3A%5B24.030976440723798%2C120.43798228260131%5D%2C%22center%22%3A%5B24.027291994452145%2C120.43187757488342%5D%2C%22zoom%22%3A17%7D%7D) 
    - [2020 mapbox](https://classicdesign053.carto.com/builder/8aa0a6cf-486e-453f-aad0-02fff29b84eb/embed?state=%7B%22map%22%3A%7B%22ne%22%3A%5B24.023607442553732%2C120.42577286716552%5D%2C%22sw%22%3A%5B24.030976440723798%2C120.43798228260131%5D%2C%22center%22%3A%5B24.027291994452145%2C120.43187757488342%5D%2C%22zoom%22%3A17%7D%7D)
- 測試方法3：使用「單機軟體 QGIS」介接 SPOT 與 mapbox satellite 兩份 wms，可行
    - 展示影片：https://youtu.be/ar6_hurmTgY
    - 課題：
        - QGIS 軟體內如何批次給經緯度，並存圖片檔案且包含 metadata
        - SPOT 接進 QGIS 後，zoom-in level 有限制


#### 各種圖資介紹

##### SPOT 衛星影像．法國衛星．國內學術界經常使用
- 初步構想：取得衛星影像檔案，或是採用 介接 服務
- SPOT 衛星資料開放平台[網站](http://data.csrsr.ncu.edu.tw/index_WMTS.php)
    - 特點：
        - 解析度：2004~2012 是 2.5M，2013~現在 是 1.5M 
        - 全島範圍有合併整理過，無雲
        - 線上瀏覽 1996 至今每一年的影像：[連結](https://data.csrsr.ncu.edu.tw/SP/#)
- ==申請資格與[使用規範](https://data.csrsr.ncu.edu.tw/Home_IMG/OpData_Rules.pdf)==
    - [說明](http://gis.rchss.sinica.edu.tw/mapdap/?p=6392&lang=zh-tw)
        - 國立中央大學太空及遙測研究中心（資源衛星接收站），針對台灣地區SPOT及Landsat系列衛星正射影像，開放執行科技部研究計畫之主持人註冊為使用者後免費下載。
    -  [wms](https://data.csrsr.ncu.edu.tw/SP/wmts) 
    -  [線上預覽](https://data.csrsr.ncu.edu.tw/SP/#) 
    -  課題：
        -  在 QGIS 軟體中，Zoom-in level 有限制
        -  參考：https://youtu.be/ar6_hurmTgY 
        -  由於是組合拼成全島，故無法得知 2016 的哪一個月份
        -  或是要直接使用 2015、2017
- SPOT 日月份型圖資
    - BigGIS 上面有收錄 SPOT 日月份型圖資，
        - 以「2015」為例，這個時間區段的資料涵蓋全島
        - 以「2016.01.01-2016.05.19」為例，這個時間區段的資料涵蓋本島一半面積
        - 以「2016.05.20-2016.12.31」為例，涵蓋範圍待查
        - 以「2017」為例，這個時間區段的資料涵蓋全島
    - 評估：
        - 可瀏覽但不曉得能否介接
        - 如果 BigGIS 可以在網址上掛上經緯度與 Zoom level，這樣就可以讓使用者或專案檢查者，直接到圖台上去瀏覽 SPOT 影像，再進行研判，這樣至少有半個台灣可以 cover
        - 06/11 正在詢問，維運單位水保局，對於 SPOT 日月份型圖資的授權概況，是否有可能用 wms 釋出，或是因應批次五萬個經緯度抓圖等專案需求。
- 下圖：
    - 舊圖：2016 全島 SPOT (1.5m)
    - 新圖：2019 全島 SPOT (1.5m)
    - 雙視窗對照瀏覽可以使用 [BigGIS](https://gis.swcb.gov.tw/)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3ef664b98a953cf3ee19d1bdb2b099dc.png)

#### ==探討中：BigGIS 圖臺上已彙整的圖資==
- 視為「舊圖」
- 日期區間：2016/05/16-2016/12/31，可供肉眼辨識的圖資
    - 圖資種類，條件：解析度足以肉眼判斷農地或建物
        - UAV正射影像                                
        - UAV斜拍照片(GPS)                  
        - UAV斜拍照片(No GPS)
        - 航照(非正射) 
        - 航照(正射)
        - Pleiades衛星                                 
        - QuickBird衛星
        - WorldView2衛星
        - SPOT衛星                                       
    - 不適合
        - 福衛2號
        - Landsat-8衛星 
        - Landsat-5衛星 
        - Landsat-4衛星
        - Sentinel-2衛星
        - Sentinel-1衛星                             
        - Corona衛星
        - 歷史照片
    - 大約涵蓋範圍，請參考[簡報](https://docs.google.com/presentation/d/1hyak0PdXA3CpxSC82T7ahmp0AbqjEJS2c3AcnhURpnw/edit#slide=id.gdda83a8f21_0_2)，應該接近全島範圍
- 課題：
    - 能否批次截圖，要看 BigGIS 能否透過掛網址、指定顯示出哪些圖層？
    - 頁面控制參數有哪些？
        - 經緯度與縮放程度：loc=23.278276,120.569532,10
            - https://gis.swcb.gov.tw/?loc=23.278276,120.569532,17
        - 圖資開啟的種類：rid=0X-000AI
            - https://gis.swcb.gov.tw/?rid=0X-000AI&loc=23.278276,120.569532,10
        - 雙視窗開啟的圖資種類，左&右：rid=0X-000AI&r2id=0X-000IP
            - https://gis.swcb.gov.tw/?rid=0X-000AI&r2id=0X-000IP&loc=23.278276,120.569532,13&view_type=slide&openExternalBrowser=1
    - 授權風險與機關態度
    - 使用 QGIS 介接 BigGIS 圖資
        - https://www.facebook.com/284329422046435/posts/1138509509961751/

#### 1/5000 像片基本圖
- 視為「舊圖」
- 年份型，無明確日期
- 提供 wms: https://wmts.nlsc.gov.tw/wmts
- 課題：如何批次取得圖片？
- 涵蓋範圍，每一年僅部分地區，請參考[簡報](https://docs.google.com/presentation/d/1hyak0PdXA3CpxSC82T7ahmp0AbqjEJS2c3AcnhURpnw/edit)
    - 1/5000像片基本圖106年：宜蘭縣、部分花蓮縣、澎湖縣
    - 1/5000像片基本圖104年：部分臺東縣
- 2022.05 釋出 WMS 
    - https://wmts.nlsc.gov.tw/wmts

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_64f4a8869047830d1ffc5a770061fb5e.png)


##### 太空中心．福衛衛星影像
- 初步構想：下載衛星影像檔案，或是採用 API 服務「Taiwan Data Cube」
- 圖資說明與檔案申購網站
    - 影像規格：[連結](https://www.nspo.narl.org.tw/activity/formosatimagery/tw/index.html)
    - 免費申請區：[連結](https://scidm.nchc.org.tw/organization/narl-nspo)
- 舊圖：福衛二號，解析度 2 公尺，從 2016 之後最舊的來挑選
    - 費用：這部分的衛星圖檔，是否要收費？
    - 圖長成什麼樣子：可以先用 [BigGIS](https://gis.swcb.gov.tw/) 看看 2016 的效果
    - [wms](https://gis.sinica.edu.tw/tgos/wmts)
        - 要確認這個 wms 中的福衛二號的年份
        - [這裡](https://gis.sinica.edu.tw/tgos/)可以線上瀏覽
- 新圖：福衛五號，解析度 2 公尺
    - 免費：可申請免費釋出的 2018 或 2019 年度，福衛五號有釋出每年秋冬一套全台圖資
        - 優點：這兩年度的圖，太空中心已挑出雲量少的，且免費申請，應該是申請 2019 年為主
        - 特點：
            - 解析度 2 公尺
            - 免費釋出的圖資時間點：2018 秋冬、2019 秋冬
            - 今年可以電話詢問一下，是否預計釋出 2020 秋冬
            > [name=chewei] 個人經驗：單一帳號免費申請一次一個縣市地區，可能需要 11 個帳號去申請不同縣市而得到全台灣範圍，網址與筆記文件請參考[連結](https://docs.google.com/spreadsheets/d/1hiQeER9tG0V2GnDMxNuKdKvDzTeQX9--uxpqbPCSVYc/edit#gid=0)
    - 針對 API 介接服務，太空中心採用的服務方案是「[Taiwan Data Cube](https://www.nspo.narl.org.tw/ground_fac.php?c=20021703)」
        - 優點：
            - 給一個時間區間，會把該區間所有的影像，整合出一張盡可能少雲的結果
            - 採用 Jupyter Notebook, XARRAY
        - 這則[貼文](https://www.facebook.com/groups/573697330058183/permalink/747072319387349)蒐集太空中心釋出的一些文件與影片說明
- 下圖：==左-福衛二號、右-福衛五號：解析度 2m，人工視覺判斷上，還算堪用．嗎？==
    > [name=deeper]我覺得不堪用了XDD
- [BigGIS 線上圖臺](https://gis.swcb.gov.tw/)可以瀏覽看效果 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_02e5b0d91a13628b9718417ee98c5bfd.png)

##### World Imagery Wayback 
- 圖資說明網頁：https://www.arcgis.com/home/item.html?id=8d47b1f2ccf141bbab8b73f5f8acc979
    - API: JavaScript
- 線上瀏覽：https://livingatlas.arcgis.com/wayback/#active=5314&ext=118.22152,22.03570,124.73641,25.38468


##### Google Earth Engine API （解析度不足，決定放棄）
- 初步構想：依照 API 評估能否符合專案需求，或是瀏覽器自動化截圖
- [API](https://developers.google.com/earth-engine/guides)
    - ImageCollection, a stack or time-series of images.
    - ==目前能取得的衛星圖，解析度，不足夠讓肉眼判斷地貌建築==
- 國內 LASS 社團裡面有推廣一波[技術介紹筆記](https://www.facebook.com/groups/LASSnet/permalink/2880606758856582/)
    - [20210604](https://www.facebook.com/groups/LASSnet/permalink/2885857144998210/) Jhih-Cyuan Shen 說明資料庫中的圖資現況
        - 🧐 google earth engine 收存的圖資都不太適用肉眼研判
    - [研究筆記](https://paper.dropbox.com/doc/Google-Earth-Engine--BKNNJWQoTNuaJtp1X3e74OEAAg-1GIwfvXac0nA03HWBURrv?fbclid=IwAR23NffOuiyTCaj-W0KhOJ1-YjKYJG87k09rfZvAhWtH2qyVwC3bSVS2dFo)
- 全球 Google Earth Engine [社團](https://www.facebook.com/groups/481573429265939)，比較多成果作品分享的貼文訊息
    - 例如這個是「[森林損失計算器](https://www.facebook.com/groups/481573429265939/permalink/973005203456090)」"This App could quantify the series of forest cover loss (hectares) within a drawn polygon."
    - - ==Google Engine 提供的圖資，人工視覺判斷上，能夠辨認嗎？==
- [20210604 Jhih-Cyuan Shen 說明資料庫中的圖資現況，可能都不太適合肉眼辨認用途](https://www.facebook.com/groups/LASSnet/permalink/2885857144998210/)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6b44a520b41e57680a1fe110a3a3062e.png)
- [荷蘭 Deltares 研究員開發 GEE APP 透過不同時期遙測影像檢查資料差異](https://gena.users.earthengine.app/view/anomaly-detection#lon=121.2822;lat=24.7752;zoom=9)
- 技術課題筆記區
    - 待確認
- 授權問題筆記區
    - 先把[授權條款](https://developers.google.com/maps/documentation/maps-static/start)抓出來看
        - [GEO guidelines](https://about.google/brand-resource-center/products-and-services/geo-guidelines/)
        > "Google Earth or Earth Studio can be used for purposes such as research, education, film and nonprofit use without needing permission. "
        - [Google Maps Platform Terms of Service](https://cloud.google.com/maps-platform/terms)
        - [Google Maps Platform credits now available for nonprofits, news media organizations and crisis responders](https://medium.com/google-earth/google-maps-platform-credits-now-available-for-nonprofits-news-media-organizations-and-crisis-be0e1c51c80c)
        > "Google Maps Platform has expanded its nonprofit offering to more countries and public programs! Now, organizations from over 50 countries can apply to receive additional credits, starting at $250 per month. Eligible organizations can apply for credits through the Google for Nonprofits program here."
    - 大量取用 vs 個人層次不太一樣
    - 直接寫信問 Google CSR
        - Google Earth Outreach / [GeoforGood](https://earthoutreachonair.withgoogle.com/)
        - 台灣有部門窗口嗎？


##### 其他「單獨圖資」來源，或是機構

國內政府
- 2018 正射影像航照，wms，無雲，全島
    - 對於專案的用途：若沒有 2016 堪用的圖資，那麼這套 2018 算是高解析度且無雲全台範圍都有
    - 課題：
        - 技術可行：即是專案目前所介接的衛星底圖 https://disfactory.tw/
        - 資料缺少：2016~2018 之間所興建的工廠則無法被判斷出來
- 農委會的農航所航照成果
    - 對於專案的用途：「舊圖」的選項
    - 農航所航照查詢[系統](https://image.afasi.gov.tw/)
    - 課題：
        - 有民國 105 年
        - 但最新的目前只有 108 年
        - 但是否覆蓋全台灣？
        - 目前僅能圖臺手動查詢瀏覽，能否取得檔案或介接？


國際商用
- mapbox satellite，釋出最新的衛星圖
    - 對於專案的用途：「新圖」
        - 拍攝時間點，這圖比 google map 還新，解析度也很高
        - 未來可預想 mapbox 會持續讓這份介接衛星圖保持更新狀態，這也符合本專案的期待
    - 這個[網頁](https://api.mapbox.com/styles/v1/chewei/ckmlzyszk0l4d17o2lqx52f06.html?fresh=true&title=copy&access_token=pk.eyJ1IjoiY2hld2VpIiwiYSI6ImNrbTU2c3V4aTBhb3Iyb3cwZTNkdjRleGEifQ.VuezEfOOKjJP3ndX_kvlWg)可以瀏覽圖面效果：
    - 民間工程師製作 [mapboxed](https://github.com/dkaoster/mapboxed): Generate assembled mapbox tilesets
    - [GIS 軟體介接用 WMS](https://api.mapbox.com/styles/v1/chewei/ckmlzyszk0l4d17o2lqx52f06/wmts?access_token=pk.eyJ1IjoiY2hld2VpIiwiYSI6ImNrbTU2c3V4aTBhb3Iyb3cwZTNkdjRleGEifQ.VuezEfOOKjJP3ndX_kvlWg)
    - 更多介接類型設定，請至 [mapbox studio](https://www.mapbox.com/mapbox-studio)或 [mapbox satellite](https://www.mapbox.com/maps/satellite)
        - 是否有可能提供 2016 年度的高解析度衛星圖？
            - 目前看編輯介面中沒有歷史衛星圖這類的選項
    - 授權釐清
        - 能否截圖使用？
- [OpenStreetMap](https://www.openstreetmap.org/) 的後台，衛星圖 Maxar Premium Imagery
    - OSM 的後台，有提供給圖客使用最新的 Maxar 圖資 50 公分，只是目前應該沒有允許做其他使用
- 商用圖資 Worldview-2
    - 林試所曾購買使用 15-20cm 進行分析樹木分佈，示範圖片
        - [應用實例](https://www.facebook.com/mickeytfri/posts/10221306228383381)
    - 國內的[瑞竣科技](https://www.richitech.com.tw/%E7%A9%BA%E9%96%93%E7%94%A2%E5%93%81%E9%8A%B7%E5%94%AE/%E6%95%B8%E4%BD%8D%E7%A9%BA%E9%96%93/worldview-2/)有代理 Worldview-2

學術單位
- 中央大學、國土計畫相關學者
- 如何找？

Google Earth 單機版
- 對於專案的用途：「舊圖」
- 課題：
    - 如何批次處理？ 按鍵精靈 ... 螢幕截圖 ...
    - 雲的問題如何處理

[Google Earth Ｗeb](https://bit.ly/3icyNd6) - Timelapse in Google Earth
- 對於專案的用途：「舊圖」
- 課題：
    - 影像解析度可能無法提供肉眼辨認地貌建物
    - 是可以用經緯度組合出網址，再取得畫面、gif

### 群眾標記工具或套件
- Zooniverse 的服務網站，提供很多公民科學計畫的群眾鍵盤參與的支援系統，我自己是沒使用過，還不確定是否適合你們的「兩圖比對點選答案」這樣的工作環節、資料匯入匯出是否方便等評估點
    - https://www.zooniverse.org/
    - 找找看有沒有類似工作環節的計畫
    - 註冊試用
        - task 有四種模式，單張照片回答問題 
        - 測試：https://www.zooniverse.org/projects/cheweiliu/satellite-labeling/classify

- [Crowdcrafting](https://scifabric.com/crowdcrafting/)
    - 進度：
        - 找找看有沒有類似工作環節的計畫
- 究心科技 開發 FS2 Clicker
    - [介紹文章]((https://geothings.tw/2014/11/04/%E8%87%AA%E5%B7%B1%E7%9A%84%E5%AE%B6%E5%9C%92%E8%87%AA%E5%B7%B1%E6%95%91-%E8%AB%87%E8%A1%9B%E6%98%9F%E7%A9%BA%E7%85%A7%E5%9C%96%E7%9A%84%E5%8F%A6%E4%B8%80%E5%80%8B%E6%87%89%E7%94%A8/))
    > 大家透過手機上的 APP, 就可以根據任務與介紹來協助標記這些小塊的圖示. 例如「尋找森林開墾蹤跡」這樣的任務, 就是希望能夠標示出有被開墾的山林地. 不管是合法開墾, 非法開墾, 土石流或坍方造成森林被砍伐. 而這個 FS2 Clicker 就是讓大家可以在手機上, 透過回答簡單的問題就能參與這個群眾協作 (Crowdsourcing) 的專案
    - 進度：
        - 交流、詢問開發經驗

### recommended 影像辨識變異點 algorithm or model? Any references and resources?

- Land Lines
    - https://github.com/ofZach/landlines
    - https://lines.chromeexperiments.com/
- [Announcing YOLTv4: Improved Satellite Imagery Object Detection](https://towardsdatascience.com/announcing-yoltv4-improved-satellite-imagery-object-detection-f5091e913fad)
- [YOLOv4 訓練教學](https://www.facebook.com/groups/edgeaitw/permalink/2929287577358589/)
- [在 PrimeHub 中使用 PyTorch Hub 的 YOLOV5 以及 OpenAI 的 CLIP 模型，快速打造行人安全的偵測系統](https://medium.com/infuseai/%E5%9C%A8-primehub-%E4%B8%AD%E4%BD%BF%E7%94%A8-pytorch-hub-%E7%9A%84-yolov5-%E4%BB%A5%E5%8F%8A-openai-%E7%9A%84-clip-%E6%A8%A1%E5%9E%8B-%E5%BF%AB%E9%80%9F%E6%89%93%E9%80%A0%E8%A1%8C%E4%BA%BA%E5%AE%89%E5%85%A8%E7%9A%84%E5%81%B5%E6%B8%AC%E7%B3%BB%E7%B5%B1-bb865921e590)
- [How to Train A Custom Object Detection Model with YOLO v5](https://towardsdatascience.com/how-to-train-a-custom-object-detection-model-with-yolo-v5-917e9ce13208?gi=d4f1bb35c25d)
- PEARL: Land Cover Mapping
    - https://www.landcover.io/
    - https://github.com/microsoft/landcover
- 找戶外籃球場
    - https://www.facebook.com/1435824760/posts/10221206366935506/
- 開源遙感探測影像分析工具Orfeo，Orfeo ToolBox Plugin for QGIS安裝步驟
    - http://gis.rchss.sinica.edu.tw/qgis/?p=3687
- [Trimble eCognition 物件式影像分析軟體，不過需要高解析度衛星資料才能辨識，軟體本身有費用成本，免費版功能與授權版一樣，但無法匯出分析結果](https://airtable.com/shr4f3DnuXOslFyss/tblPtI3b0UhzUT1fH/viwq0grXbLsYekbkL/recm5xh6Jp2XtxLvR?blocks=hide)
- [Mapping Africa’s Buildings with Satellite Imagery](https://ai.googleblog.com/2021/07/mapping-africas-buildings-with.html)

### 推薦之潛在參與者和合作夥伴

## 其他可能延伸應用
### Data
- 群眾協作後的 data 可以進一步有什麼應用？
### 功能
- SPOT 影像圖片擷取器
    - 給經緯度，縮放程度，畫面比例，勾選想要的年份(1996-2020)，執行批次截圖，另存至單機資料夾，檔案命名規規則
- 衛星圖小工具
    - 歡迎提供靈感～
    - 九宮格多視窗對照工具
        - http://gissrv4.sinica.edu.tw/gis/twhgis/MapCompare/
    - 左右雙視窗，SPOT 影像對照
        - https://data.csrsr.ncu.edu.tw/demo1/googlemaps_2view_taiwan.V3.8.html
:::

## 期程

## References and resources
- 政治獻金數位化 https://campaign-finance.g0v.ctiml.tw/

## Ideas pools
- 要有 prototype 可以快速 test and verify


### 內政部每年舉辦的【國土測繪圖資GIS競賽】
- 內政部舉辦的【2021國土測繪圖資GIS競賽】「參賽團隊(者)可就下表15項供應圖資提出需求，原則採免費方式提供使用。其中申請內政部國土測繪中心供應圖資，依據申請圖資項目、數量及費額換算免費供應總額上限為5萬元。」:thinking_face:
    - https://easytolearn.tw/GISMAP/index.aspx
- todo: 5萬塊，能否取得輔助比對的資料集？
    - 三維度資料，如何應用？
        - https://3dmaps.nlsc.gov.tw/
        - ronny 爬臺北市立體建物，的確可以產製出建築外框
            - https://www.facebook.com/groups/1417173811903954/permalink/2080968975524431/
- todo: 前兩年和違章工廠有關的成果，他們用了什麼資料、處理什麼議題？
    - 天意難違—探討北彰化違章工廠對當地環境之影響
        - note: 從水系、二氧化硫與工廠位置，推論出哪些農地受到危害風險較高
        - 參賽學生：謝宜均 梁綺芳 楊雯安
        - 指導老師：臺北大學不動產與城鄉環境學系 黃金聰老師
        - https://www.youtube.com/watch?v=4bYW32o9AXo
        - https://easytolearn.tw/GISMAP/Download/2019/%E5%A4%A7%E5%B0%88/02-%E5%84%AA%E9%81%B8.pdf
    - 歷史共業？臺南市違章工廠分佈區位模擬與擴散潛勢診斷
        - note: 推測出台南哪些地區非常有可能要冒出新的違章工廠
        - 參賽學生：王薪華、陳吉兒
        - 指導老師：國立成功大學都市計劃學系 李子璋老師
        - https://www.youtube.com/watch?v=NFqfUyjm9qA
        - https://easytolearn.tw/GISMAP/Download/2019/%E5%A4%A7%E5%B0%88/01-%E5%84%AA%E9%81%B8.pdf

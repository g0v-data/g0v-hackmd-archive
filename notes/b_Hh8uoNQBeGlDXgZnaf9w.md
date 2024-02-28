---
tags: 都市農耕
---

# 公共園圃地圖：資料與工作討論

工作區
跳坑：chewei,

## 民間整理資料

- 公開社團討論串，有資料需要登載到地圖上：
    - https://www.facebook.com/groups/851321448229543/posts/7658113624216924/
- 另有一個非公開社團的討論串，也有資料需要登載到地圖上


## 彙整資料
- 臺北
    - 直接用地圖中的兩個圖層，對照與新增
- 新北
    - 對照新北市政府的地圖
- 台中
    - 從新聞或網頁補
- 民間手邊還有全台 260 個公共園圃還需要標註到地圖上
    - https://www.facebook.com/groups/1687334708150141
- 環保署低碳社區，社區農園 64 個案例
    - https://lcss.epa.gov.tw/LcssViewPage/Responsive/CaGryActMain.aspx?actmain=A&id=6

## 資料庫長期維護的方案

- 挑選民間可維運的資料整合方案
    - 評估 Airtable
        - 評估是否整合都市農耕文件知識
            - 園圃基地
                - 錦安霧裡薛圳雨水花園
            - 主題技術文件
                - 城市養蜂
            - 機關單位
            - 政策
                - 臺北市田園城市
                - 新北市可食地景
                - 臺中市城食森林
                - 新竹市社區糧倉
                - 農委會食農教育法
                - 環保署低碳社區
                - 文化部社區營造
        - 園圃欄位方案
            - 園圃名稱：
            - 園圃類型：
            - 園圃狀態：
            - 用地類型
                - 國有地
                - 市有
                - 等
            - 經營單位
            - 網址
            - 經度
            - 緯度
            - 縣市
            - 鄉鎮區
            - 開始時間
            - 結束時間
    - 視覺化方案 Airtable2sheet2AwesomeTable


## 督促縣市政府資料開放 API
- 督促縣市政府資料開放 API
    - 臺北市：
        - 有圖台可瀏覽
            - 補網址
        - 有釋出園圃地理資料
            - 補網址
        - 有 API 但社群尚未測試串接過
    - 新北市：
        - 有圖台僅供瀏覽
            - 補網址
        - 2021.06.27 市政府回覆不開放資料
            - 回覆網址：https://data.gov.tw/suggests/136369
            - 需要招募工程師寫爬蟲
    - 臺中市：
        - 市府已關閉了農園線上地圖
        - 2021.02.25 市政府回覆不開放資料
            - 回覆網址：https://data.gov.tw/suggests/136370
    - 其他縣市：則是沒有展示地圖



---
以下內容待整理

## 資料庫建置方案討論

### 基本設定

1.盡可能涵蓋台灣各個縣市的都市園圃經驗
2.透過群眾協作的方式，累積資料
3.明確的資料授權，例如
- CC0 1.0 通用 (CC0 1.0) [https://creativecommons.org/publicdomain/zero/1.0/deed.zh_TW](https://creativecommons.org/publicdomain/zero/1.0/deed.zh_TW)
- 姓名標示 4.0 國際 (CC BY 4.0) [https://creativecommons.org/licenses/by/4.0/deed.zh_TW](https://creativecommons.org/licenses/by/4.0/deed.zh_TW)
- 持續蒐集授權無虞的案例圖片：[http://goo.gl/TC8sTl](http://goo.gl/TC8sTl)
4.應該選擇容易維護管理資料與內容的方案
5.方便展示
- 除了資料累積之外，同時考量地圖化，例如需要有地理資料欄位才能標示
6.文字欄位，圖片，地理資料（要多細緻？例如園圃內的分區細節）
7.可以匯出為 geojson 方便其他應用
8.將內容匯出至 OSMdatabase，需進一步釐清相對應的 tag，以及基本授權
9.是否整合 OSMdatabase 既有關於社區園圃的圖資？（[方法](http://supaplex99.blogspot.tw/2015/08/using-overpass-turbo-to-extract-data-and-umap-with-dynamic-data-link-visualization.html?m=1)）
10.官方資料匯入問題，例如公部門推動的園圃資料，市民農園資料等，部分資料集有資料授權規範
- 納入政府開放資料，例如新北市市民農園資料，該資料欄位能否被涵蓋？
11.每年都會有新的園圃出現，以及消失

### 各種方案探討與試做

- google spreadsheet，例 [https://goo.gl/4J6OD6](https://goo.gl/4J6OD6)
    - 經緯度需要另外轉換，無法支援輪廓資料
    - 圖片需要另外放，再把連結貼近文件中
    - 實際寫起來，因為都是在表格內填欄位內容，有點苦海無邊
    - [https://sheetsu.com/](https://sheetsu.com/)
    - 針對分散式上傳檔案
        - 免費簡單架設報名徵選傳檔網頁， Google 表單上傳檔案開放了
            - [http://www.playpcesor.com/2017/07/google-forms-file-uploader.html](http://www.playpcesor.com/2017/07/google-forms-file-uploader.html)
        - 時間地圖 / 地圖化
            - [http://timemapper.okfnlabs.org/](http://timemapper.okfnlabs.org/)
- [google fusion tables 地圖介面](https://www.google.com/fusiontables/data?docid=1CCWdCOQhKmns70i-FLct6h-etR7oWgr_ZDKqE5ny#map:id=3)
    - 可以自訂欄位
- umap，例 [測試地圖](https://umap.openstreetmap.fr/zh-tw/map/map_50075#18/25.04793/121.55796)
    - 若將每一個園圃都給與一個圖層，可以畫出農園範圍輪廓，園圃內的分區也可以細緻繪製
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1a2ee0cc765db6c3b665c4a86dd7fde2)

- OSMdatabase：
    - 於osm上編輯農園（空地、屋頂農園、露台）相關的 tag：
> OSM 的 landuse 應該視為一個獨立的圖層，如果以 landuse 的角度來看：
> [name=yellowsoar]

> 菜園 landuse=allotments [https://wiki.openstreetmap.org/wiki/Tag:landuse=allotments?uselang=zh-TW](https://wiki.openstreetmap.org/wiki/Tag:landuse=allotments?uselang=zh-TW)
> [name=yellowsoar]

> 已拆空地 landuse=brownfield [https://wiki.openstreetmap.org/wiki/Tag:landuse%3Dbrownfield](https://wiki.openstreetmap.org/wiki/Tag:landuse%3Dbrownfield)
> [name=yellowsoar]

> 綠地 landuse=greenfield [https://wiki.openstreetmap.org/wiki/Tag:landuse%3Dgreenfield](https://wiki.openstreetmap.org/wiki/Tag:landuse%3Dgreenfield)
> [name=yellowsoar]

> 公共農場型 [leisure=garden + garden:type=community](http://wiki.openstreetmap.org/wiki/Food_security#Community_gardens)
> [name=che l]

> 另一類似的提案 [landuse=community\_food\_growing](http://wiki.openstreetmap.org/wiki/Proposed_features/Community_food_growing) 中文名稱：？
> [name=che l]

    - 各個「文字欄位、照片、文件檔案連結」，能否連同農園範圍一起被放入？
    - 已消失的農園
> 不考慮資料保存的情況，umap 另開會比較好，OSM 是直接刪除
> [name=yellowsoar]

- GoogleMap，
    - [https://www.google.com/maps/d/u/0/viewer?mid=1U8yp4SZZn81OqXad1ztdObHf2is&hl=en_US&ll=23.910513060547817%2C121.2149546420419&z=6](https://www.google.com/maps/d/u/0/viewer?mid=1U8yp4SZZn81OqXad1ztdObHf2is&hl=en_US&ll=23.910513060547817%2C121.2149546420419&z=6)
    - 圖文閱讀不方便，不適合長文說明與圖文搭配
    - 圖塊，在地圖介面呈現上，不明顯，必須要拉到很近，肉眼才能夠辨識出這裡有園圃
    - 使用者有時候會不小心拖曳到點位資料、更動到位置而不自知
    - 一般民眾習慣的地圖
- Localwiki，例 [https://localwiki.org/taipeicommunity/](https://localwiki.org/taipeicommunity/)
    - Localwiki 匯出與匯入需要 coding，參考 [localwiki export import](https://g0v.hackpad.tw/YghsHsKGadh)，這部分的開發時間未定
    - 無法直接用「欄位」來組織內容
    - 可考慮一個園圃，設立一個頁面，圖文，以及該園圃的地理資料
    - 可以允許已消失的園圃成立圖文介紹頁面


### 架構初擬 20160313

文件檔案：[https://docs.google.com/presentation/d/1Ub2esHqs-pySh7PXwSCwH2UTrDAi475xF8JS08tibxc/edit](https://docs.google.com/presentation/d/1Ub2esHqs-pySh7PXwSCwH2UTrDAi475xF8JS08tibxc/edit)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cc4102866e6ef06c1de509986dd07d6f)
1.Localwiki：完整圖文與地理資料編輯，作為群眾協作區，授權僅接受 CC0 或 CC BY
2.GeoJson：成為「開放資料集」鼓勵其他使用
3.GoogleMap：或其他圖台，簡易地圖展示，基本資訊可呈現，不允許協作
4.OSMdatabase：建立授權與相應 tag 資料可相互流通的環境
5.GovData：官方整理的園圃資料（csv, kml），希望資料授權能符合 ODBL
6.FBgroup：於此通報園圃資訊，文字說明或拍照等，銜接後續資料處理


### 社區園圃案例資料的欄位需求（持續列舉）

- 文字類型
    - 園圃名稱
    - 縣市
    - 區
    - 地址 / 地點描述
    - 地號清單
    - 面積
    - 經度
    - 緯度
    - 參訪資訊
    - 起始時間
    - 結束時間
    - 空間型態：空地、屋頂、露台...
    - 土地權屬
    - 經營單位：
    - 參與者：鄰近居民、學生、社區發展協會...
    - 耕種方式：土植、盆缽...
    - 設施：堆肥、雨水回收、工具間
    - 活動：月聚會、共餐、公田食材提供給社福機構...
- 地理資料類型
    - 農園範圍多邊形輪廓
        - 單一基地
        - 多基地
    - 園圃內部的分區資訊
        - 走道
        - 園圃
- 圖片或文件檔案連結
    - 現場照片
    - 相關書圖


### 其他呈現方式發想

- 參考：
    - [開放空間資料與地圖化](http://github.ronny.tw/ronnywang/taipei-open-space/blob/master/geojson.json#25.03558452336418,121.51579455847563,16)
    - Timemapper：[http://timemap.kuansim.com/](http://timemap.kuansim.com/)
    - GeoEvent：[http://0media.tw/t/geoevent/](http://0media.tw/t/geoevent/)
    - [筆電快篩](http://muyueh.com/30/notebook/)
    - 「拉霸機」：\[人\] x \[空間\] x \[模式\]
        - 例如 \[社區里民\] x \[國防部土地\] x \[家戶認養\] => 台北市松山區復建里幸福農場
    - [http://livinglotsnyc.org/lot/3032450039/](http://livinglotsnyc.org/lot/3032450039/)
        - 每一個園圃都有專屬的頁面，可供園圃推動者與民眾，留言討論

### 應用方向

- 走訪
- 成為探討城市生態議題過程中的一種環境圖資，如同公園、綠地
- 輔助園圃規劃或設施需求的探討，例如與台北市已有的雨水回收中水回收地點整合探討
- 一些園圃的基本計算，例如耕種面積+農法，或許可以初步推論出保守基本的產量


## 台灣都市園圃案例與內容蒐集

- 「一群人運用生活中的公共空間，共同耕種與維護農作物，就是社區園圃。」
- 持續往資料庫的方向來整理相關內容
- 說明
    1.  農園空間類型，可以分為：土地/空地/農地、建物衍伸 (屋頂、社區中庭、造景空間)
    2.  空間的產權，可以分為：公有、私有（包含共有）
    3.  經營特性，可以分為：公辦民營計畫、民營（包含里長、社發會、民間機構）
    4.  其他特點

工作社團：[https://www.facebook.com/groups/1687334708150141/about/](https://www.facebook.com/groups/1687334708150141/about/)


## 以下案例暫記，待整理至線上第圖

- 基隆
    - 七堵的幸福人生社區
    - 安樂永康社區的金橘園
    - [https://www.facebook.com/creategreen2010/posts/276948315998134](https://www.facebook.com/creategreen2010/posts/276948315998134)
- 台北市政府政策推動的園圃
    - [https://www.google.com/maps/d/viewer?mid=zXbDd4vF6Eh8.kQdykW74O1z0](https://www.google.com/maps/d/viewer?mid=zXbDd4vF6Eh8.kQdykW74O1z0)
    - 可下載成資料集，但比較沒有完整的細節與描述、照片
- 新北市政府政策推動的園圃
    - [http://www.landscaping.ntpc.gov.tw/cht/index.php?act=edible_map&code=search](http://www.landscaping.ntpc.gov.tw/cht/index.php?act=edible_map&code=search)
    - [http://www.agriculture.ntpc.gov.tw/website/food/cht/index.php](http://www.agriculture.ntpc.gov.tw/website/food/cht/index.php)
- 新北市政府八樓露台闢建都市農園
    - [http://news.ltn.com.tw/news/life/breakingnews/1278910](http://news.ltn.com.tw/news/life/breakingnews/1278910)
- 新北市土城貨饒里
    - [http://m.ltn.com.tw/news/local/paper/878532](http://m.ltn.com.tw/news/local/paper/878532)
- 新北市三重國小？
- [https://www.facebook.com/RiChiTech/posts/991905177523467:0](https://www.facebook.com/RiChiTech/posts/991905177523467:0)
- 文山區木柵路4段附近都市農園
    - [照片](https://www.facebook.com/photo.php?fbid=915080218570281&set=o.366624190155942&type=3&theater)
    - 土地權屬？

### 私有空地或農地，民營，空地開放型農園

- 台北市中正區冠德建設更新案開心農園
    - 地址：
    - 說明：運用鑰匙孔型態的園圃規劃，設置雨水回收裝置，設計推車型式的花車、攀爬式涼棚，留設平坦的空間，營造公園的開放感。台北好好看系列二政策綠地。
    - 授權為 cc0 的照片：
- 台北市中山區五常街周忠德及崑逸開發
    - 地址：
    - 說明：
        - 2015 已結束？台北好好看系列二政策綠地。
    - 授權為 cc0 的照片：
- 台北市信義區象山農場
    - 地址：
    - 說明：結合園藝治療協會、天行者全人關懷協會。自然農法、現地資材堆肥(不混入慣行生廚餘)、養蜂、麵包窯
    - 授權為 cc0 的照片：
- 淡水河中興橋下的河灘地農田使用（其實比較像是農業區農地耕種的模式）
    - 地址：
    - 說明：
    - 授權為 cc0 的照片：

### 私有農地，公辦民營，空地開放型農園

- 台北市市民農園
    - 官網：[http://www.tfa.org.tw/plan5/page7.html](http://www.tfa.org.tw/plan5/page7.html)
    - 臺北市市民農園承租資訊：[http://data.taipei/opendata/datalist/datasetMeta?oid=215345fa-4364-471c-9cf9-140def405523](http://data.taipei/opendata/datalist/datasetMeta?oid=215345fa-4364-471c-9cf9-140def405523)
    - 欄位：農園名稱、地址、園主、電話、租位。
- 新北市市民農園
    - 官網：[http://www.agriculture.ntpc.gov.tw/website/cht/index.php?code=list&ids=65](http://www.agriculture.ntpc.gov.tw/website/cht/index.php?code=list&ids=65)
    - 新北市市民農園資料集：[http://data.ntpc.gov.tw/od/detail?oid=51C9BEE4-5397-40C5-801B-53CB76374A48](http://data.ntpc.gov.tw/od/detail?oid=51C9BEE4-5397-40C5-801B-53CB76374A48)
    - 資料集描述：「市民農園」土地來源為閒置農地，輔導農會推動設置或改善充實市民農園設施。市民農園資料包括地址、成立時間、面積及承租戶數。

### 私有建物，民營

- 台北市萬華區室內種植豆芽（尚未見到公共參與操作）
    - 地址：
    - 說明：南萬華長泰街一帶，可以參考紀錄短片「孵」
    - 授權為 cc0 的照片：
- 台北市太平洋建設轉投資室內植物工廠（尚未見到公共參與操作）
    - 地址：
    - 說明：
    - 授權為 cc0 的照片：
- 台北市萬華區愛愛院屋頂與後院
    - 地址：
    - 說明：
    - 授權為 cc0 的照片：
- 台北市中正區博仲法律事務所屋頂營造
    - 地址：
    - 說明：樸門概念、設有生態廁所、一位「綠色管理員」，許多參觀
    - 授權為 cc0 的照片：
- 「小草作」畫藍圖 持續成長的綠屋頂（尚未見到公共參與操作）
    - 地址：
    - 說明：[http://goo.gl/RURZ1D](http://goo.gl/RURZ1D)
    - 授權為 cc0 的照片：
- 技嘉科技公司的屋頂
    - 地址：
    - 說明：[新聞](http://m.appledaily.com.tw/appledaily/article/finance/20140731/35991183/)，[報導](http://www.gvm.com.tw/Boardcontent_25988_4.html)
    - 授權為 cc0 的照片：

### 公寓大廈共有，民營，空地開放型農園

- 新北市新店區[江陵京都](https://www.facebook.com/pages/%E6%B1%9F%E9%99%B5%E4%BA%AC%E9%83%BD/122845167818277)戶外空間，改種植香草與葉菜
    - 地址：
    - 說明：[江陵京都](https://www.facebook.com/pages/%E6%B1%9F%E9%99%B5%E4%BA%AC%E9%83%BD/122845167818277) 粉絲頁
    - 授權為 cc0 的照片：
- 新北市新店區大鵬華城社區活動中心屋頂
    - 地址：
    - 說明：
    - 授權為 cc0 的照片：
- 新北市花園新城
    - 地址：
    - 說明：屋頂、兒童、公視「蔬菜朵朵開」有拍攝
    - 授權為 cc0 的照片：
- 新北市林口區佐賀社區屋頂農園
    - 地址：
    - 說明：盆缽式
        - [https://www.facebook.com/DaAiTV/videos/10153927267141202/](https://www.facebook.com/DaAiTV/videos/10153927267141202/)
    - 授權為 cc0 的照片：

### 公有空地，民營，空地開放型農園

- 松山區復建里光復南路幸福農場
    - 地址：光復南路32巷內
    - 說明：國防部眷舍土地，都市更新程序中，[紀錄短片](https://www.youtube.com/watch?v=0HauYo_iYr8)
    - 授權為 cc0 的照片：
- 松山區東榮里社區園圃
    - 地址：民生東路五段27巷富錦街359巷口
    - 說明：民生社區附近慈恩眷村拆除後的社區園圃，國防部預計收回，新聞
    - 授權為 cc0 的照片：
- 中山區聚盛里友誼農場
    - 地址：民生東路一段21號
    - 說明：國產署空地，鄰近文化局文創園區開發規畫
    - 授權為 cc0 的照片：
- 中山區埤頭里快樂田園
    - 地址：
    - 說明：[https://www.facebook.com/newscns/videos/1515073142138462/](https://www.facebook.com/newscns/videos/1515073142138462/)
    - 授權為 cc0 的照片：
- 大安區錦安里金華街轉角國產署空地
    - 地址：
    - 說明：城市花園計畫，里長與里民參與園圃規劃，調整施作方案，留設出香草園的耕種空間，待整地完成後，里民一起種植香草，同時兼具採收與景觀維護的效果。
    - 授權為 cc0 的照片：
- 大安區瑞安街，街邊社區菜園
    - 地址：瑞安街
    - 說明：國產署空地 [https://www.facebook.com/groups/851321448229543/permalink/1145558065472545/](https://www.facebook.com/groups/851321448229543/permalink/1145558065472545/)
    - 授權為 cc0 的照片：
- 中山區北美館雙年展台北明天還是一個湖
    - 地址：
    - 說明：時間？OURs 專業者都市改革組織、藝術家吳瑪俐共同合作，運用台北美術館的戶外展場空間，開設啤酒箱菜園市民認養與教學課程，策展已結束。
    - 授權為 cc0 的照片：
- 台北大直劍潭社區，社區空間改善，居民願意前往公共空間，認養經營，促成老人共餐，長者種菜，無障礙社區，社區韌性的角度
- 中正區華山綠工場策展
    - 地址：
    - 說明：時間？運用華山公有土地空間，策展已結束。
    - 授權為 cc0 的照片：
- 中正區華山田園公車策展
    - 地址：
    - 說明：時間？運用華山公有土地空間。結合廢棄公車。
    - 授權為 cc0 的照片：
- 中正區南海藝廊庭院菜園
    - 地址：
    - 說明：南海藝廊
    - 授權為 cc0 的照片：
- 紹興菜依鄰
    - 地址：
    - 說明：紹興社區原土地產權屬於台大，被迫搬遷，後來台大與社區協商，但後續的法律訴訟、法規程序等讓居民感受到緊張壓迫感。學生們構思以發展「社區園圃」的概念，讓居民走出來種種菜、聊聊天，舒緩緊張氣氛，帶動社區更快樂美好。讓蔬菜依鄰而生，推展更多社區活力。影片：[http://www.peopo.org/news/248783](http://www.peopo.org/news/248783)
    - 授權為 cc0 的照片：
- 中正區寶藏巖社區農園
    - 地址：
    - 說明：寶藏巖居民既有的習慣、養蜂、麵包窯
    - 授權為 cc0 的照片：
- 大安區蟾蜍山煥民新村社區農耕空間
    - 地址：
    - 說明：
    - 授權為 cc0 的照片：
- 大同區
    - [https://www.youtube.com/watch?v=nerAezlldd4&feature=youtu.be](https://www.youtube.com/watch?v=nerAezlldd4&feature=youtu.be)
- 萬華區糖廍甘蔗園
    - 地址：
    - 說明：糖廠文化。2015 區公所認為應該轉移至其他空間？新聞？
    - 授權為 cc0 的照片：
- 萬華區茉莉小花園  (是否開放認養?)
    - 地址：
    - 說明：
    - 授權為 cc0 的照片：
- 萬華區日祥里青年路188 巷底空地盆種式菜園（是否已結束？）
    - 地址：
    - 說明：
    - 授權為 cc0 的照片：
- 台北市西區憲兵隊舊址的都市農耕實驗行動
    - 地址：
    - 說明：趣華江。景澤創意
    - 授權為 cc0 的照片：
- 文山區羅斯福路上的環品基金會農園
    - 地址：
    - 說明：
    - 授權為 cc0 的照片：
- 文山區忠順里笑順食堂
    - 地址：
    - 說明：[https://www.facebook.com/media/set/?set=a.869542463070061.1073741873.144408682250113&type=3](https://www.facebook.com/media/set/?set=a.869542463070061.1073741873.144408682250113&type=3)
- 文山區「順興社區」的里民農場
    - 地址：
    - 說明：位在閒置司法新村裡，里長與里民參與，木箱裡放的都是社區的落葉、菜葉、豆渣等有機廢棄物，搭配一點培養土來種植。
- 士林區名山里社區菜園
    - 地址：
    - 說明：
- 士林區天母白屋的農園
    - 地址：
    - 說明：[https://www.facebook.com/heartfarming2014](https://www.facebook.com/heartfarming2014)
    - 授權為 cc0 的照片：

### 公有空地，民營，民間租賃活用為農業用途

- 新北市猴洞國小廢校校園轉為環境生態與生產園區
    - 地址：
    - 說明：248 農學市集、社區圖書館
    - 授權為 cc0 的照片：
- 新北市永和社區大學與河灘地環境教育園區
    - 地址：
    - 說明：
    - 授權為 cc0 的照片：
- 新北市永和區潭安里潭安農園
    - 地址：
    - 說明：2015 新北市可食地景營造計畫、永和社區大學課程
    - 授權為 cc0 的照片：
- 新北市新莊社區大學生態農園
    - 地址：
    - 說明：
    - 授權為 cc0 的照片：
- 台北市大安區找到咖啡
    - 地址：
    - 說明：台大校產租賃，戶外空間融合微型菜園，目前已經改為停車空間了
    - 授權為 cc0 的照片：
- [台北市信義區市有土地由立偕建設與248農學市集進行的種子計畫](http://a89800333.pixnet.net/blog/post/143225146-%E3%80%90%E5%8F%B0%E5%8C%97%E3%80%80%E5%B8%82%E6%94%BF%E5%BA%9C%E7%AB%99%E3%80%80%E4%BF%A1%E7%BE%A9a25%E3%80%91%E7%A7%BB%E5%8B%95%E7%BE%8E%E8%A1%93%E9%A4%A8%C3%97%E8%A1%97)
    - 地址：
    - 說明：2013年4月已經結束
    - 授權為 cc0 的照片：

### 公有空地，公營，機構內不對外開放的農園

- 萬華區，龍山國小
    - 地址：
    - 說明：[新聞](http://www.vita.tw/2011/04/blog-post_03.html?m=1)
    - 授權為 cc0 的照片：
- 萬華區，臺北市福星國小附設幼兒園
    - 地址：
    - 說明：[https://www.facebook.com/fhpschildren](https://www.facebook.com/fhpschildren)
    - 授權為 cc0 的照片：
- 中山區，中山國小
    - 地址：
    - 說明：
    - 授權為 cc0 的照片：
- 臺北市南港社大與成德國中合作的食農與田園教育
    - 地址：
    - 說明：
    - 授權為 cc0 的照片：
- 文山區政治大學小米園
    - 地址：
    - 說明：社團?
    - 授權為 cc0 的照片：
- 南門園區
    - [https://www.facebook.com/ProjectOffGrades/posts/1218042134881840](https://www.facebook.com/ProjectOffGrades/posts/1218042134881840)

### 公有空地，公營，對外開放參與的農園

- 新北市政府高灘地工程管理處推廣「樂活農園」
    - 地址：
    - 說明：[http://www.rhbd.ntpc.gov.tw/cht/index.php?code=list&flag=detail&ids=6&article_id=1126](http://www.rhbd.ntpc.gov.tw/cht/index.php?code=list&flag=detail&ids=6&article_id=1126)
    - 授權為 cc0 的照片：

### 公有建築，建物型農園，有些保持對外開放，有些可能是單位內部經營使用

- 萬華區萬華國中教室頂樓屋頂農園
    - 地址：
    - 說明：屋頂菜園及自動澆水系統。[http://photo.xuite.net/yiutsay/15489015](http://photo.xuite.net/yiutsay/15489015)
    - 授權為 cc0 的照片：
- 大同區歷史資源經營協會建物屋頂菜園（是否有常態開放？）
    - 地址：
    - 說明：
    - 授權為 cc0 的照片：
- 大龍老人住宅屋頂
    -
- 大安區錦安里圖書館公有建物屋頂農園
    - 地址：
    - 說明：大安社大、堆肥
    - 授權為 cc0 的照片：
- 台科大管院頂樓『魚菜共生系統』有機農場
    - 地址：
    - 說明：[http://www.ntust.edu.tw/files/16-1000-42419.php?Lang=zh-tw](http://www.ntust.edu.tw/files/16-1000-42419.php?Lang=zh-tw)
    - 授權為 cc0 的照片：
- 信義區信義區公所屋頂
    - 地址：
    - 說明：薄層綠化，志工維護
    - 授權為 cc0 的照片：
- 臺北市信義社大在信義國中的屋頂菜園
    - 地址：
    - 說明：
    - 授權為 cc0 的照片：
- 大安區大安老人服務中心屋頂
    - 地址：
    - 說明：高架式
    - 授權為 cc0 的照片：
- 大安區台灣大學社會系屋頂
    - 地址：
    - 說明：課程、學生
    - 授權為 cc0 的照片：
- 大安區台大心理系南館屋頂
    - 地址：
    - 說明：[https://m.facebook.com/#!/story.php?story_fbid=10203012149138356&id=1643532125](https://m.facebook.com/#!/story.php?story_fbid=10203012149138356&id=1643532125)
        - 心理系南館，上班時間都有開放。[http://map.ntu.edu.tw/ntu.html](http://map.ntu.edu.tw/ntu.html) 可以右上角搜尋心理系南館，就可以查到了
    - 授權為 cc0 的照片：
- 信義區臺北市政府屋頂提供市府員工認養
    - 地址：
    - 說明：各局處分配名額
    - 授權為 cc0 的照片：
- 南港區台北市部落大學屋頂農園
    - 地址：
    - 說明：北原會館的頂樓，有課程搭配營造。[https://www.facebook.com/notes/natural-craftsman/%E5%8F%B0%E5%8C%97%E9%83%A8%E8%90%BD%E5%A4%A7%E5%AD%B8%E5%B1%8B%E9%A0%82%E8%8F%9C%E5%9C%92%E5%BB%BA%E7%BD%AE%E7%B4%80%E9%8C%842014104-2014126/401565436666720](https://www.facebook.com/notes/natural-craftsman/%E5%8F%B0%E5%8C%97%E9%83%A8%E8%90%BD%E5%A4%A7%E5%AD%B8%E5%B1%8B%E9%A0%82%E8%8F%9C%E5%9C%92%E5%BB%BA%E7%BD%AE%E7%B4%80%E9%8C%842014104-2014126/401565436666720) / [https://www.facebook.com/tammy1turner/media_set?set=a.10153393227632028.1073741903.729197027&type=1](https://www.facebook.com/tammy1turner/media_set?set=a.10153393227632028.1073741903.729197027&type=1)
    - 授權為 cc0 的照片：
- 中正區農委會頂樓研究性質的太陽能屋頂溫室
    - 地址：
    - 說明：
    - 授權為 cc0 的照片：
- 文山區萬芳醫院屋頂
    - 地址：
    - 說明：萬芳農園位於醫院8樓戶外屋頂，600坪的農園種植逾800盆植栽，作為園藝治療的基地。[http://news.ltn.com.tw/news/local/paper/413796](http://news.ltn.com.tw/news/local/paper/413796)
    - 授權為 cc0 的照片：
- 文山區景美材料實驗中心綠屋頂（尚未見到農耕使用）
    - 地址：
    - 說明：材料實驗中心，[http://material.abri.gov.tw/art.php?no=29](http://material.abri.gov.tw/art.php?no=29)
    - 授權為 cc0 的照片：
- 新北市鶯歌區東鶯里活動中心屋頂
    - 地址：
    - 說明：[新聞](https://tw.news.yahoo.com/%E9%A0%82%E6%A8%93%E8%AE%8A%E6%9C%89%E6%A9%9F%E8%BE%B2%E5%A0%B4-%E4%BF%83%E5%9C%8D%E7%89%86%E5%8A%A0%E9%AB%98-221209408.html)
    - 授權為 cc0 的照片：
- 新北市新莊區雙鳳里
    - 地址：
    - 說明：[新聞](http://www.chinatimes.com/newspapers/20140902000502-260107)
    - 授權為 cc0 的照片：
- 新北市蘆洲區忠義國小屋頂
    - 地址：
    - 說明：蔬果、香草
    - 授權為 cc0 的照片：

### 基隆

- 基隆東明里
    - 地址：基隆市信義區東明里民活動中心.
    - 說明：基隆市信義區東明社區發展協會闢建的社區園圃，[https://www.facebook.com/837196916372185](https://www.facebook.com/837196916372185)
    - 授權為 cc0 的照片：
- 吉慶國小
    - 地址：
    - 說明：「魚菜共生推廣進入吉慶國小，校方除了融入環境教育課程外，種出來的A菜、薄荷、九層塔和青江菜等農作，收成後除了成為學童營養午餐新菜色，還會拿來義賣並捐助創世基金會。」
- 和平島
    - 愛鄉文化協會
    - [https://www.facebook.com/newscns/videos/1595159577463151/](https://www.facebook.com/newscns/videos/1595159577463151/)

### 宜蘭縣市

- 宜蘭縣長青農場
    - 地址：宜蘭市建業里珍珠路132號
    - 說明：開放給65歲以上縣民耕作，農地面積約300坪，縣府計劃再擴大面積。
    - 授權為 cc0 的照片：
- 宜蘭市梅洲社區市民農園
    - 地址：
    - 說明：宜蘭市公所營造市區田園景觀，結合宜蘭農田水利會重整閒置用地，選在梅洲社區開闢首座市民農園，市公所把0.25公頃畫分成80個菜股，採用無毒耕作方式不施用農用、化學肥料，提供民眾耕種空間，未來園區內將設置行銷專區，推廣友善市區農園生活。[https://video.udn.com/news/390708](https://video.udn.com/news/390708)
    - 授權為 cc0 的照片：
- 宜蘭市進士社區市民農園
    - 地址：
    - 說明：宜蘭市公所與宜蘭農田水利會合作，整理閒置的水利地成立「市民農園」，提供民眾認養，首座啟用的梅洲社區成效不錯，第2座市民農園選定進士社區，近期將發包，3個月內開放民眾登記認養，營造友善種植空間。[http://udn.com/news/story/7328/1367580](http://udn.com/news/story/7328/1367580)
    - 授權為 cc0 的照片：
- 蘇澳國中校園開放菜園 社區耕者有其甜
    - 地址：
    - 說明：蘇澳國中將校園的一塊閒置空地再利用，邀聖湖社區居民共同耕作，農作收穫由居民分享，也讓社區走入校園，原本寸草不生的泥地，經居民刨除及翻土，種植的作物冒出嫩芽，為校園增添綠意生機。 [https://www.facebook.com/iliketaiwanfarmer/posts/1053944218004985](https://www.facebook.com/iliketaiwanfarmer/posts/1053944218004985)
    - 授權為 cc0 的照片：

### 金門

- 金幸福開心農場
    - 地址：金門縣金湖鎮后壟31號
    - 說明：金門縣農業試驗所則在所內的農業示範農場內，闢設約600坪的金幸福開心農場。

### 連江縣

- 山隴蔬菜公園
    - 地址：縣府前
    - 說明：[http://www.mobile01.com/waypointtopicdetail.php?f=212&t=130836](http://www.mobile01.com/waypointtopicdetail.php?f=212&t=130836)
- 馬祖南竿鐵板社區
    - 地址：
    - 說明：找空地闢建成菜園，利用地形坡度儲存雨水，提供菜園使用。

### 新竹

- 香山區頂埔社區活動中心，社區共耕園圃。  [https://www.facebook.com/johnliu38/posts/1125784764106419](https://www.facebook.com/johnliu38/posts/1125784764106419)
- 香山區虎林社區老人關懷據點，社區自給菜園。
- 香山區東香里「東香社區CSA農場」,社區支持型農場。
- 香山區大庄國小生態農場
- 東區光明社區「光明農場」，社區開心農場。
- 東區千甲里「千甲CSA農場」，社區支持型農場。
- 東區水源里「沺源青工作室」生態農場
- 東區青草湖國小「幸福農場」農場
- 東區水源國小生態農場
- 東區陽光國小教學農場
- 清華大學 天空魔豆 ‧ 綠屋頂
    - 地址：
    - 說明：[https://www.facebook.com/MoDoGreenRoof](https://www.facebook.com/MoDoGreenRoof)
    - 授權為 cc0 的照片：
- 食物森林 @新竹縣世興空氣品質淨化區
    - 地址：
    - 說明：
    - 授權為 cc0 的照片：
- 新竹上寮社區
    - 結合社區老人關懷據點
    - [https://www.facebook.com/iliketaiwanfarmer/posts/1053458438053563](https://www.facebook.com/iliketaiwanfarmer/posts/1053458438053563)

### 桃園市

- 桃園市撒烏瓦茲Sawaz 大溪原住民河灘農園
    - 地址：
    - 說明：[https://www.facebook.com/media/set/?set=a.264087060310597.83196.163500030369301&type=3](https://www.facebook.com/media/set/?set=a.264087060310597.83196.163500030369301&type=3)
    - 授權為 cc0 的照片：
- 中壢區金華里運用閒置游泳池營造成園圃
    - 地址：
    - 說明：運用閒置游泳池空間，營造空中菜園、魚菜共生系統。桃園市環保局102年辦理「第一屆校園綠點子競賽」，獲得學校熱烈迴響，參賽作品多兼具創意及實用性。其中，高中組桃園農工的「魚菜相逢，蚤知道」作品，透過改良魚菜共生系統，藉由培養天然綠水養殖水蚤，作為魚缸內魚的食物，並利用魚含氮的排泄物作為植物養分來源，種植有機新鮮蔬菜可供食用，獲得評審團一致推薦。中壢市金華里謝里長得知此一訊息，把綠點子實際應用到現實生活，透過重新設計改良，在社區大樓閒置游泳池，建制1,000株新型魚菜共生立式管耕系統，打造成城市開心菜園，讓住戶體驗種菜樂趣，享受有機健康蔬菜。綠點子的巧思，讓生活更加便利。[http](http://blog.udn.com/yangmei320/15067699)[://blog.udn.com/yangmei320/15067699](http://blog.udn.com/yangmei320/15067699)。
        [https://tw.news.yahoo.com/%E9%9B%B6%E7%A2%B3%E7%94%9F%E6%B4%BB%E5%9C%88-%E4%B8%AD%E5%A3%A2%E9%87%91%E8%8F%AF%E9%87%8C%E7%8D%B2%E5%9C%8B%E9%9A%9B%E8%AA%8D%E8%AD%89-004236151.html](https://tw.news.yahoo.com/%E9%9B%B6%E7%A2%B3%E7%94%9F%E6%B4%BB%E5%9C%88-%E4%B8%AD%E5%A3%A2%E9%87%91%E8%8F%AF%E9%87%8C%E7%8D%B2%E5%9C%8B%E9%9A%9B%E8%AA%8D%E8%AD%89-004236151.html說明)[說明](https://tw.news.yahoo.com/%E9%9B%B6%E7%A2%B3%E7%94%9F%E6%B4%BB%E5%9C%88-%E4%B8%AD%E5%A3%A2%E9%87%91%E8%8F%AF%E9%87%8C%E7%8D%B2%E5%9C%8B%E9%9A%9B%E8%AA%8D%E8%AD%89-004236151.html說明)：中壢市金華里為都會型住商混合社區，里內有八棟十五層以上大樓社區，約三千戶、八千名里民聯手拚節能減碳，在公共空間營造空中菜園、魚菜共生系統，以及單車回收再利用等環保節能措施，歷經兩年努力，獲得英國標準協會 BSI「零碳生活圈」認證，成了桃園縣節能減碳的觀摩示範社區。
    - 授權為 cc0 的照片：
- 空中農場花園│桃園市中壢區內壢里辦公室
- 桃園中聖與中泰社區
    - 地址：
    - 說明：運用社區大樓的戶外空間，堆肥設施。
- 公益果園及多功能展演空間│桃園市桃園區冠桃園社區管理委員會
- 再現九座寮│桃園市龍潭區中興社區發展協會
- 看見-LLUNG │台灣原住民愛加倍文教關懷協會

### 台中

- 台中市北區區公所屋頂
    - 地址：
    - 說明：[https://www.youtube.com/watch?v=pxkZWvVib_k](https://www.youtube.com/watch?v=pxkZWvVib_k)
    - 授權為 cc0 的照片：
- 東海大學附近的社區園圃
    - 地址：
    - 說明：大顆卵石收邊，
    - 授權為 cc0 的照片：
- 美食育基地 [https://www.facebook.com/groups/851321448229543/permalink/1282633001765050/](https://www.facebook.com/groups/851321448229543/permalink/1282633001765050/)
- 台中市眉山 屋頂
    - [http://cultivatorab.blogspot.tw/2015/05/blog-post.html?m=1](http://cultivatorab.blogspot.tw/2015/05/blog-post.html?m=1)
- 台中市大雅區上雅社區
    - [https://www.facebook.com/groups/tcccpi/permalink/1108853369161374/](https://www.facebook.com/groups/tcccpi/permalink/1108853369161374/)
- 潭子，頭家東里，伯樂城鄉協會
    - [https://www.facebook.com/yuntingt/posts/10153572341345886](https://www.facebook.com/yuntingt/posts/10153572341345886)
- 廚餘園圃 [https://www.facebook.com/groups/851321448229543/permalink/1272545562773794/](https://www.facebook.com/groups/851321448229543/permalink/1272545562773794/)
- 中興大學農業試驗場，市民農園 [https://www.facebook.com/permalink.php?story_fbid=617530518395180&id=548384931976406](https://www.facebook.com/permalink.php?story_fbid=617530518395180&id=548384931976406)


### 南投

- 南投綠光少年農園 陪伴觀護少年
    - 地址：
    - 說明：[http://news.ltn.com.tw/news/society/breakingnews/1324466](http://news.ltn.com.tw/news/society/breakingnews/1324466)
    - 授權為 cc0 的照片：

### 台南

- 國宅里
    - [https://tw.news.yahoo.com/%E6%BB%85%E7%99%BB%E9%9D%A9%E7%86%B1-%E5%8D%97%E5%B8%82%E5%AE%A3%E4%BD%88%E7%A0%8D%E6%8E%89%E6%89%80%E6%9C%89%E5%B8%82%E6%B0%91%E8%BE%B2%E5%A0%B4-083443538.html](https://tw.news.yahoo.com/%E6%BB%85%E7%99%BB%E9%9D%A9%E7%86%B1-%E5%8D%97%E5%B8%82%E5%AE%A3%E4%BD%88%E7%A0%8D%E6%8E%89%E6%89%80%E6%9C%89%E5%B8%82%E6%B0%91%E8%BE%B2%E5%A0%B4-083443538.html)

### 嘉義

- 嘉義新港自然農場社區菜園
    - 地址：
    - 說明：社區農民提供的空地，中間的共同的公田，作物賣掉的收入可以變成社區公積金，種植種類會由參與者一起討論。設置有堆肥場，菜園紅磚小屋，小屋涼亭等空間。
    - 綠園。1/2自然農場 [https://www.facebook.com/hkfcefarm/](https://www.facebook.com/hkfcefarm/)

### 高雄

- 高雄市前金國中綠光屋頂
    - 地址：
    - 說明：農園與溫室，[新聞](http://build.kcg.gov.tw/PrintView.aspx?au_id=12&sub_id=35&id=157049)
    - 授權為 cc0 的照片：
- 河濱國小校內幸福魚菜圃
    - 地址：高雄市三民區市中一路339號
    - 說明：高雄第一社區大學維護，目前有12位耕作者，每耕作區為三坪大小。令紹有學校食農教育園圃，為河濱國小低年級的實習園圃。以無毒方式耕種。
    - 授權為 cc0 的照片：
- 和平國小校內大地學堂園圃
    - 地址：高雄市岡山區和平路一號
    - 說明：高雄第一社區大學協助。水稻區域，葉菜，立體耕種。耕作者為社區居民、學校教師、班級認養。
    - 授權為 cc0 的照片：[https://www.facebook.com/groups/851321448229543/permalink/1146502215378130/](https://www.facebook.com/groups/851321448229543/permalink/1146502215378130/)
- 高雄第一社區大學樂學農園社孔鳳農場
    - 地址：高雄市小港區孔鳳路293巷與455巷附近
    - 說明：四分三地，2018年1月開辦30人參與，為私人農地租用，以無毒理念耕種。劃分單元20坪，有露地區、網室區、教學區，耕種者需要上過高雄第一社區大學的有機農耕課程。並建有「社員耕地準則」、「社員耕作規範」、「社長選舉辦法」、「蔬果上架販售管理辦法」。參與者有場地保險。社團成員也會協助高雄市的國小推動校園農耕，或是籌辦相關都市居家耕種的推廣講座。
    - 授權為 cc0 的照片：[https://www.facebook.com/groups/851321448229543/permalink/1146502215378130/](https://www.facebook.com/groups/851321448229543/permalink/1146502215378130/)
- 高雄第一社區大學樂學農園社明義農場
    - 地址：高雄市小港區孔明街明義國小前方
    - 說明：四分三地，2018年九月即將開辦，將有30人參與，為私人建地租用，以無毒理念耕種。劃分單元20坪，有露地區、網室區、教學區，耕種者需要上過高雄第一社區大學的農耕課程。並建有「社員耕地準則」、「社員耕作規範」、「社長選舉辦法」、「蔬果上架販售管理辦法」。參與者有場地保險。社團成員也會協助高雄市的國小推動校園農耕，或是籌辦相關都市居家耕種的推廣講座。
- 高雄市政政府社會局南區銀髮族市民農園
    - 地址：高雄市前鎮區衙信二街與興化街口
    - 說明：本銀髮農園由社團法人高雄市社區大學促進會食農教育發展中心承辦，大小約有一分多，有耕作區、休息區，每8坪為一單位，目前有46塊耕作區。每年六月初進行市民抽籤，抽中者始能進入耕種。每月辦有學習活動，如農作知識、健康知識、人際連結等活動。
    - 授權為 cc0 的照片：[https://www.facebook.com/khcitizenfarm/](https://www.facebook.com/khcitizenfarm/)
- 三民區公所 屋頂光電農場
    - [https://www.facebook.com/whiteuca/posts/10206418675134938](https://www.facebook.com/whiteuca/posts/10206418675134938)




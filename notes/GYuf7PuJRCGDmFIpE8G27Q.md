---
tags: GIS,
---

# 第二堂：介紹線上協作地圖工具

課程影片：
- Part 1：六種協作地圖工具介紹 https://youtu.be/PVFLu7bZ3JU
- Part 2：GoogleMyMap 操作教學 https://youtu.be/ckU1ytIo19c
- Part 3：umap & OpenStreetMap 操作教學 https://youtu.be/bHblo2uofcI
- Part 4：AwesomeTable 操作教學 https://youtu.be/SgIWQGUW-c4
- Part 5：工具挑選原則，以及本次作業說明 https://youtu.be/ODF1ZwSY8Mw

本頁面的內容：
- 「點、線、面」向量資料集，舉例說明
- 工具介紹 
    - 1：GoogleMyMap
    - 2：umap & OpenStreetmap
    - 3：Awesome-table & Spreadsheet
    - 4：TimeMapper & Spreadsheet
    - 5：TGOS 協作地圖
    - 6：GIS Cloud
- 從「多人協作、資料維護」的角度，來選擇主題地圖工具 😎
- 作業說明：運用資料，以及地圖工具，創建一份線上地圖 👩‍💻

---
## 「點、線、面」向量資料集，舉例說明

Point 點位資料：台南餐飲店家
- 原始資料：https://data.gov.tw/dataset/6184
    - 格式：csv
    - 若遇到中央資料網站偶爾維護無法下載，可以使用 [備用檔案連結](https://gist.githubusercontent.com/ronnywang/dcad38649aea12ee6271ca838722e3a9/raw/00963ed85ac29475dfbcc13a056f29c0e1f70104/food.csv) 請按右鍵另存連結

Line 線型資料：台南公車路線
- 原始資料：https://data.tainan.gov.tw/dataset/tainan-bus-route-line-data
    - Xml 格式
- 整理過的資料：[geojson 格式](https://d3hu5rc2ze6fj6.cloudfront.net/wms?Request=GetGeoJSON&Layers=ronnywang/%E5%8F%B0%E5%8D%97%E5%85%AC%E8%BB%8A%E8%B7%AF%E7%B7%9A&sql=SELECT+%2A+FROM+this+ORDER+BY+_id_+ASC)
- geojson2kml 常用轉檔工具：http://geojson.io/
- 整理過的資料：[下載 kml 格式](https://drive.google.com/file/d/1VOp8UAzH4n15TXSOeS70jkBHwuYEn-Qs/view?usp=sharing)

Polygon 面狀資料：臺南市行政區範圍
- 原始資料：http://bit.ly/3aWJrAP
    - Shp 格式
- shp2geojson: http://gipong.github.io/shp2geojson.js/
- geojson2kml: http://geojson.io/
- 整理過的資料：[下載 kml 格式](https://drive.google.com/file/d/1vlDBEV3r2ZYjrXHnmUwU3Jyb_SNTIcEu/view?usp=sharing)
- 補充「Shp 檔案格式轉成 geojson 轉成 kml 的步驟」影片與步驟截圖：https://g0v.hackmd.io/JayE3varSemjMywEU6ABkw?view


<iframe width=100% height="400" src="https://data.depositar.io/dataset/tn-town/resource/d68d7844-7513-4f14-8394-24b5a80b7cd2/view/05ef6265-cc9c-49c1-9e4e-9101d81e2560" frameBorder="0"></iframe>

## 工具介紹 1：GoogleMyMap

==GoogleMyMap 操作教學影片：https://youtu.be/ckU1ytIo19c==
工具網址：https://www.google.com.tw/intl/zh-TW/maps/about/mymaps/

🔻「搭公車吃美食」Google My Map 示範地圖：http://bit.ly/3aZN60B

<iframe src="https://www.google.com/maps/d/u/0/embed?mid=1f08BqdrZtJynrJvdo3-cIK6ZWwFeEjUJ" width=100% height="480"></iframe>


🔻 匯入 Google Photo 相簿照片，匯入至 Google My Map，示範地圖：https://bit.ly/2UV9h2k

<iframe src="https://www.google.com/maps/d/embed?mid=1YyKA6hK9nRxXYU3e1LG2F4W9v5o&hl=zh-TW" width=100% height="480"></iframe>

🔻 匯入 雲端硬碟中的 Google Spreadsheet

- 資料來源：[民間社群標註官方公布的確診者足跡 😷](https://g0v.hackmd.io/GNfNQ8NbQ5KXJNTyftRLgA)
- 透過試算表的函式，與資料來源同步更新資料「台南市政府公布確診者足跡位置」
    - `=IMPORTRANGE("1eNgxy1nP36rhugQ5tcti2a7MHsDVYipHYDfOGFbaqIU", "台南市!A1:X")`
- 本次課程影片中，示範地圖所使用的是這一個 [Spreadsheet 資料集](https://docs.google.com/spreadsheets/d/1pL2R3Nkynp0uqHit0dSDJiaCg8TlGrBWBp8EkqN5ckk/edit?usp=sharing)


## 工具介紹 2：umap & OpenStreetmap

==umap & OpenStreetMap 操作教學影片：https://youtu.be/bHblo2uofcI==
工具網址：https://umap.openstreetmap.fr/zh-tw/

🔻 澎湖縣 OpenStreetMap 飲水點 (自動更新) 套疊 mapbox 衛星底圖
示範地圖：http://u.osmfr.org/m/638568/

<iframe width="100%" height="400px" frameborder="0" allowfullscreen src="//umap.openstreetmap.fr/zh-tw/map/osm-mapbox_638568?scaleControl=false&miniMap=false&scrollWheelZoom=true&zoomControl=true&allowEdit=false&moreControl=true&searchControl=null&tilelayersControl=null&embedControl=null&datalayersControl=true&onLoadPanel=undefined&captionBar=false#12/23.6015/119.6282"></iframe>

資料
- 遠端資料，網址欄位請輸入以下：澎湖縣範圍的飲水點
    - `
https://overpass-api.de/api/interpreter?data=[out:json][timeout:25];(node["amenity"="drinking_water"](23.038033989127,118.98193359375,23.978724193277,120.02563476563););out;>;out skel qt;
`
- 教學文章：umap + data from OpenStreetmap
    - 「製作隨時更新的客製化地圖，透過動態連結 uMap 地圖與開放街圖資料庫」by RL Chen
        - http://supaplex99.blogspot.com/2015/08/using-overpass-turbo-to-extract-data-and-umap-with-dynamic-data-link-visualization.html
    - https://wiki.openstreetmap.org/wiki/UMap/Guide/Import_data_with_Overpass
- 經驗建議：
    - 若資料集 沒有需要持續更新，記得不用勾選「動態」
    - 若資料集 希望採用動態更新，那麼資料範圍比較適合「鄉鎮區」尺度，若地理範圍太大，對於使用者網頁端可能跑不出來

底圖
- umap 提供許多樣式的底圖，例如強調出自行車道路線，或是水彩渲染的底圖樣式..等
- 若希望自行調整底圖樣式，或是需要高解析度衛星底圖，可考慮使用 mapbox studio 自製底圖的服務 https://studio.mapbox.com/

特定主題的圖資，是否適合以 OpenStreetMap 資料庫來進行資料標注？
- 您可以查看 Map features 的清單，了解資料庫中目前的資料種類
    - https://wiki.openstreetmap.org/wiki/Map_features
- 評估文章：主題地圖與 OSM：https://osmtw.hackpad.tw/-OpenStreetMap-VnjVOhWBZuO
- 主題型編輯器：使用 MapComplete 建立主題地圖編輯器 https://mapcomplete.osm.be/

🔻 MapComplete 以「公共飲水點」為例
https://mapcomplete.osm.be/drinking_water.html?z=13&lat=22.63386&lon=120.3091&background=Mapbox
<iframe width=100% height="400" src="https://mapcomplete.osm.be/drinking_water.html?z=13&lat=22.63386&lon=120.3091&background=Mapbox" frameBorder="0"></iframe>


## 工具介紹 3：Awesome-table & Spreadsheet

==AwesomeTable 操作教學影片：https://youtu.be/SgIWQGUW-c4==
工具網址：https://awesome-table.com/

🔻 Awesome-table 地圖模式，以「民間社群標註官方公布的確診者足跡 😷 」資料為例
另開網頁：https://app.awesome-table.com/-MevBcqxlbvI5ec5ab5I/view
<iframe referrerpolicy="no-referrer-when-downgrade" height="600px" width="100%" style="border:none;" src="https://app.awesome-table.com/-MevBcqxlbvI5ec5ab5I/view"></iframe>

特點：
- 優點：以 spreadsheet 作為資料集，同步更新於地圖
- 優點：提供「Filter 篩選器」
- 優點：提供「街景服務」
- 缺點：無法呈現「線型資料、面狀資料」，因為 google spreadsheet 無法支持線與面的地理資料型態
- 缺點：沒有「圖層」功能

資料
- 資料來源：[民間社群標註官方公布的確診者足跡 😷](https://g0v.hackmd.io/GNfNQ8NbQ5KXJNTyftRLgA)
- 透過試算表的函式，與資料來源同步更新資料
    - `=IMPORTRANGE("1eNgxy1nP36rhugQ5tcti2a7MHsDVYipHYDfOGFbaqIU", "Merged!A2:X")`
- 本次示範地圖所使用的 [Spreadsheet 資料集](https://docs.google.com/spreadsheets/d/1GBAyWId91JAU0kxpCkN28mWpE-tdt9BcCVIiRxP5P7U/edit?usp=sharing)

地圖樣式編輯方式說明
- (1) Spreadsheet 資料集
    - 在資料集的「第二列」，給予每一個欄位，特定的文字代碼
    - 各種文字代碼的用途
        - 指定該欄位為「經度」：`NoFilter - MapsLong - Hidden`
        - 指定該欄位為「緯度」：`NoFilter - MapsLat - Hidden`
        - 指定該欄位為可以透過「關鍵字」的方式進行篩選：`StringFilter`
        - 指定該欄位為可以透過「選項」的方式進行篩選：`CategoryFilter (C)`
        - 指定該欄位「不顯示」於前臺地圖中：`Hidden`
    - 官方釋出的篩選器文字代碼，種類說明
        - https://support.awesome-table.com/hc/en-us/articles/115001068189-Filters-select-data-to-display
- (2) 地圖編輯區
    - 可參考此介面 https://app.awesome-table.com/-MevBcqxlbvI5ec5ab5I/edit
- (3) 記得確認一下瀏覽權限有沒有打開喔！
    - Awesome-table 的地圖瀏覽授權，會沿用來源 google spreadsheet 的瀏覽授權
    - 可以用無痕狀態，不登入 google 帳號的情況下，點開地圖網址，看看是否能順利看到內容
    - 若沒有看到地圖內容，表示「來源 google spreadsheet」的瀏覽授權要打開


## 工具介紹 4：TimeMapper & Spreadsheet

工具網址：https://timemapper.okfnlabs.org/

🔻 社區報、文化刊物、地方誌 - 時間地圖
另開網頁：http://timemapper.okfnlabs.org/cheweiii/local-zine-and-alternative-publishing
<iframe src="http://timemapper.okfnlabs.org/cheweiii/local-zine-and-alternative-publishing?embed=1" frameborder="0" style="border: none;" width="100%" height="400;"></iframe>

特點：
- 優點：以 spreadsheet 作為資料集，同步更新於地圖
- 優點：提供「時間軸」
- 缺點：無法呈現「線型資料、面狀資料」
- 缺點：沒有「圖層」功能
- 缺點：想先提醒想要試看看這個工具的朋友，此地圖工具專案，近年較少維護更新了，近期有看到一些 spreadsheet 帳號鏈結上的問題
    - Github https://github.com/okfn/timemapper/issues

## 工具介紹 5：TGOS 協作地圖、TGOS 圖台

TGOS 協作地圖，工具網址：https://www.tgos.tw/MapSites/Web/MS_Home.aspx

🔻 測試呈現地圖
可以另開網頁，查看套用底圖：便利超商分佈位置的圖層、各級學校範圍圖..等
https://www.tgos.tw/MapSites/Web/Map/MS_Map.aspx?themeid=23975&type=view&visual=Point
<iframe src="https://www.tgos.tw/MapSites/EmbedMap?themeid=23975&visual=point" width=100% height="400" frameborder="0" style="border:0" allowfullscreen></iframe>

特點：
- 優點：提供匯入 WMS、WMTS 圖層的功能
    - 例如：便利超商分佈位置的圖層、各級學校範圍圖..等
    - 國內 WMS / WMTS 服務資源清單：
        - http://gis.rchss.sinica.edu.tw/qgis/?cat=18
        - http://gis.rchss.sinica.edu.tw/qgis/?cat=7
        - http://gis.rchss.sinica.edu.tw/qgis/?p=3640
        - SPOT 歷年衛星影像 https://data.csrsr.ncu.edu.tw/SP/
- 優點：「點」資料集的呈現方式，也有提供「熱度圖」、「叢集」呈現方式
- 缺點：並無「多個圖層」，所以僅適合單一資料集
- 缺點：後台介面與使用者體驗期待能再優化

TGOS 圖台，工具網址：https://map.tgos.tw/TGOSCLOUD/Web/Map/TGOSViewer_Map.aspx

特點：
- 優點：提供匯入 WMS、WMTS 圖層的功能
- 優點：提供「立體視角」
- 簡介：TGOS圖台 建構在雲端網路環境，在結合功能需求的原則下，發展操作簡易、直覺式介面，與允許使用者設定的圖台系統。在圖台本身，會有圖台工具，包含放大、縮小、平移、顯示全圖、關閉底圖、鷹眼圖、另存圖片等功能；圖形及文字的圖面標註工具；包含單點坐標、二點間距離，與多點之周長、面積的量測工具；在圖層加入上，能支援動態連結線上的WMS、WMTS、KML；對於使用者建立的主題圖能夠進行分享。在相關的工具模組，要有定位工具，提供地標、地址、道路、行政區、坐標等定位功能；試辦最佳（短）路徑分析工具；提供單點坐標環域工具；提供使用者管理介面，管理使用者自建的主題圖，上傳的檔案，與加入的線上連結圖層（WMS、WMTS、KML）。

## 工具介紹 6：GIS Cloud

工具網址：https://www.giscloud.com/

特點：
- 優點：提供匯入 WMS、WMTS 圖層的功能
- 特點：
    - 屬於上傳檔案展示用途為主
    - 免費版有使用期間限制


---
## 從「多人協作、資料維護」的角度，來選擇主題地圖工具 😎

如何協作？
- 填寫「Spreadsheet 資料欄位」的方式來協作 ➜ 推薦 Awesome-table (可以自動更新且提供街景服務)
- 透過「地圖」來協作 ➜ GoogleMyMap、umap、TGOS 協作地圖
- 會需要協作「面狀資料」➜ GoogleMyMap、umap (~~Awesome-table 無法處理線與面資料~~)
- 透過「OpenStreetMap 資料庫標註」的方式來協作 ➜ 推薦 umap
- 戶外需要上傳「照片」 ➜ 請參考具有 [**地點通報功能**](https://g0v.hackmd.io/jRxB8NHwTai543QpUwa8tQ) 的專案 📸

地圖樣式偏好、輔助圖資
- 想要呈現有「時間軸 / 旅途歷程」的樣式地圖 ➜ 
    - TimeMapper https://timemapper.okfnlabs.org/
    - Geoevent http://0media.tw/t/geoevent/
    - 旅途故事地圖 Story Maps https://storymaps-classic.arcgis.com/en/app-list/
    - 旅途故事地圖 Odyssey.js http://cartodb.github.io/odyssey.js/
- 可以讓使用者在資料地圖上同時使用「Google 街景視角」➜ Awesome-table
- 「國外內的 WMS/WMTS」其中有您需要呈現的圖資種類 ➜ TGOS 協作地圖、GIS Cloud
- 需要呈現 Geo-tiff 格式 ➜ GIS Cloud (若不需要進行協作，則可以使用 Map Warper: http://mapwarper.net)
- 地區型主題知識地圖，可多人協作 ➜ localwiki https://localwiki.org/regions

以下是「非」協作工具
- [Carto](https://g0v.hackmd.io/T0yZwtFtRECkhrGQjlj9ng)：線上地圖服務，資料地圖化的工具，提供許多資料視覺化的樣式，但無法協作，連結內有教學與地圖範例
- [DocuGIS](https://docusky.org.tw/DocuSky/DocuTools/DocuGIS/)：線上地圖服務，文本地理資訊系統工具，提供豐富的世界歷史地圖可以作為底圖使用，舉例 [西元 1225 年《諸蕃志》文本地點標註地圖](https://docusky.org.tw/DocuSky/DocuTools/DocuGIS/index.html?s=ZhuFanZhi)
- [QGIS](https://g0v.hackmd.io/AH6MEsSuSZ2pvxQIJld-Og)：單機軟體，支援地理資料運算與分析，有套件 QGIS Cloud 可以發布成線上地圖，[案例：使用 qgis2web 套件發布文化資產線上地圖](https://nebula-rubram.github.io/HeritageMapTW/)
- [Google Earth Pro](https://g0v.hackmd.io/O6NC1bKvQeGKXLiELbepKQ)：單機軟體，特點在於提供鳥瞰視角、真實地理的地形起伏
- [Google Earth Engine](https://g0v.hackmd.io/XEisWIPlQ2qmGok9VN8bgQ)：撰寫程式語言進行遙測資料分析與視覺化的線上平台

---
# 作業區

本次作業說明：

- 請建立自己的 hackmd 作業頁面，筆記以下工作歷程內容、地圖網址成果。
- 本次作業：請創建一個資料地圖

作業步驟：

### 資料：您所建立的地圖網址，地圖中需要有「資料」
- 我有某個特別想要探討的資料主題！ 
    - ➜ 您可以前往「[政府資料開放平台網站](https://data.gov.tw/)」，查找您有興趣的地理資料，並運用前述工具，製作線上地圖。若有遇到檔案格式問題，可以參考 [轉檔工具蒐集頁面](https://g0v.hackpad.tw/-Mapfessional-EJfaf9C5gaT) 有沒有適合的工具，或是至 [g0v slack #gis channel](https://g0v.hackmd.io/@jothon/joing0vslack) 提問討論。
- 我想處理的資料，似乎也是 OpenStreetMap 的資料類型 
    - ➜ 如果您想要處理的資料集，如果是符合 OpenStreetMap 資料庫的收錄原則，建議可以嘗試看看使用 OpenStreetMap 資料庫，作為同步更新的資料來源，請使用 umap 地圖工具 (GoogleMyMap 與 Awesome-table 都無法達成)。
- 我沒有資料靈感... 
    - ➜ 您可以使用主辦單位已整理好的資料（美食店家位置、公車路線、行政區面資料）。

### 從「是否協作，如何協作」來挑選適合的地圖工具
- 請思考一下，這份地圖是否希望進行多人協作。
- 答案：是
    - 本次課程介紹的三種工具，哪一種工具比較適合你希望的協作方式，GoogleMyMap、umap、Awesome-table
    - 若您希望您的地圖是屬於多人協作，那麼講師會依據作業內容，檢視你所選擇的工具，是否能夠支援線上協作，講師會提供工具調整建議意見。
- 答案：否
    - 您自己是否會更新資料集內容？
        - 是
            - 您會如何更新或編輯資料集？
        - 否，資料集不會再變動，僅希望可以呈現為「不協作、可供公開瀏覽的線上地圖」
            - GoogleMyMap：
            - Awesome-table：有街景
            - umap：底圖樣式多元，資料集有群集熱圖等呈現方式
            - 也推薦參考 [Carto](https://g0v.hackmd.io/T0yZwtFtRECkhrGQjlj9ng) 地圖工具

### 挑選好工具、已設想了預計的協作方式、找好資料 ➜ 請建立一個資料地圖

- 請參考本次課程中介紹的各種工具操作流程。


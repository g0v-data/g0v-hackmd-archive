---
tags: tree
---

# Data 好植地 - 資料整理工作頁面

:::warning
資料類別
[TOC]
:::

# 1. Green and Tree 綠覆 / 樹木資料

## 現況
- [NDVI, Treepedia-demo](https://g0v.hackmd.io/E8GwG5SMSbSSBKT9KuuSGA)
- [Tree data 樹木資料集](https://g0v.hackpad.tw/J4diKtZxBA8)

## 森林型態分佈

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_73d28feaafd359097c6935bb8a413692.png)

- 台灣13種與氣候有關的森林型態（以及代號）
    - https://e-info.org.tw/node/213426
    - 因應氣候變遷生物多樣性回復力之研究
        - https://www.forest.gov.tw/report/0003857
- 各個國土綠網調查研究成果？

## Restoration Potential TW 潛在補植地圖
- image source https://www.trilliontreecampaign.org/ 
- 台灣本島的 Restoration Potential 分布圖套疊
    - 可瀏覽線上網頁：https://mapwarper.net/maps/71610#Preview_Rectified_Map_tab
- 社團討論串 https://www.facebook.com/groups/573697330058183/posts/1385587408869167/

# 2. Policy and Site 政策業務與用地資料

## 政策業務

[縣市及部會-與民間合作綠化植樹業務政策資訊 Policy of Greenspace Sponsored Adoption](https://sheet2site.com/api/v3/index.php?key=1D2Iz2PfeyUUAtFT6oPS9uW1YEvcbQOIQKo1X1WHsa9U)

<iframe width="100%" height="520" frameborder="0" src="https://sheet2site.com/api/v3/index.php?key=1D2Iz2PfeyUUAtFT6oPS9uW1YEvcbQOIQKo1X1WHsa9U" allowfullscreen webkitallowfullscreen mozallowfullscreen oallowfullscreen msallowfullscreen></iframe>


## (1) 林地：國有林、保安林、台糖平地造林、伐採案件地圖
- 並無所謂優先待認養土地清冊，僅有[各個林管處連絡窗口](https://www.forest.gov.tw/0000056)，因為沒有清冊，或許採用「林管處的管轄範圍 polgon」來代表 此區域的林地都可以認養與協助 ps.頁面中有年度各界捐贈認養林地的內容 PDF，有明確的地號
- TODOs：
    - 國有林與保安林，資料本身整合 8 個林管處
        - 國有林，把代碼換成林管處
        - 保安林，把編碼對應到林管處(見以下說明)
- 各林管處管理轄區
    - 要看各個林管處簡介 https://www.forest.gov.tw/subsidiary
    - 是否就是「國有林區林地分區圖shp」？要開檔案確認
- [國有林區林地分區圖shp](https://data.gov.tw/dataset/37682)
    - 有區分出 8 個林管處轄區，[參考此圖](https://www.facebook.com/photo.php?fbid=2006129606183718&set=p.2006129606183718&type=3&theater)
        - Coded_Name	Value
        - 本局	0
        - 羅東林區管理處	1
        - 新竹林區管理處	2
        - 東勢林區管理處	3
        - 南投林區管理處	4
        - 嘉義林區管理處	5
        - 屏東林區管理處	6
        - 台東林區管理處	7
        - 花蓮林區管理處	8
        - 農林航空測量所	9
        - 其他	10
    - [林地分區類別說明](https://www.coa.gov.tw/ws.php?id=5061)
- 林務局[全台保安林分布概略圖 kml](https://data.gov.tw/dataset/9928) 
    - 放到 Carto http://bit.ly/tree-taiwan-map-forest
    - 保安林四位數編碼，對應的林管處，[說明](https://www.facebook.com/photo.php?fbid=10158134876829038&set=p.10158134876829038&type=3&theater)

線上地圖：保安林、國有林區林地分區圖
[另開網址](https://classicdesign053.carto.com/builder/70b26de2-3209-11e6-8506-0ef7f98ade21/embed)
<iframe width="100%" height="520" frameborder="0" src="https://classicdesign053.carto.com/builder/70b26de2-3209-11e6-8506-0ef7f98ade21/embed" allowfullscreen webkitallowfullscreen mozallowfullscreen oallowfullscreen msallowfullscreen></iframe>

- [第三次森林資源調查林地分級圖](https://tgos.nat.gov.tw/TGOS/Web/MetaData/TGOS_MetaData_View.aspx?MID=EEE5D5C488E1CA7867573D5AD971F80E&SHOW_BACK_BUTTON=false)；[WMS](http://gis.forest.gov.tw/arcgis/services/WMS/FHWMS/MapServer/WmsServer?REQUEST=GetMap&SERVICE=WMS&VERSION=1.1.1&LAYERS=8&STYLES=&FORMAT=image/png&BGCOLOR=0xFFFFFF&TRANSPARENT=TRUE&SRS=EPSG:3826&BBOX=200000,2600000,240000,2650000&WIDTH=764&HEIGHT=590)
- 臺灣林產-森林採伐地點地圖：https://fprod.forest.gov.tw/fpp/
    - 其他補充：Teemo 曾分享「採伐計畫管理作業平台」上面的「已審核通過」的用地
        - 當時的網站網址：https://harvest.forest.gov.tw/harvest/Bulletin/BulletinList.aspx
        - 每筆用地，有地號與 polygon
        - 行政上與實際上，表示說這塊地剛經歷過採伐，所以也是一個潛力補植地
        - 用地類別有多種類，可以再挑國有公有類別，比較容易作為林管處造林業務的標的
        - 這個也可以提供給民間企業與團體，尋找捐款造林土地的目標 
- 台灣糖業公司
    - 議題評論
        - https://www.cet-taiwan.org/publication/issue/content/3615
    - 造林業務成果
        - 台灣糖業公司_花東區處花蓮農場課造林面積
            - https://data.gov.tw/dataset/62955
            - 農場、造林樹種、平地造林面積公頃、環保林道面積公頃、住址、電話號碼
        - 台灣糖業公司_屏東區處造林面積
            - https://data.gov.tw/dataset/32660
            - 農場別、平地造林面積公頃、全民造林面積公頃、自費造林面積公頃、環保林園大道面積公頃、合計面積公頃
    - 資產
        - 台灣糖業公司_資產公告主檔
            - https://data.gov.tw/dataset/101668
        - 台灣糖業公司_資產公告土地明細資料
            - https://data.gov.tw/dataset/101669
        - 台灣糖業公司_土地招標設定地上權資訊
            - https://data.gov.tw/dataset/25746
            - 地段地號
        - 台灣糖業公司_土地標租資訊
            - https://data.gov.tw/dataset/25749
            - 地段地號
        - 台灣糖業公司_可供出租土地資訊
            - https://data.gov.tw/dataset/25754
            - 鄉鎮名稱、段號名稱、小段名稱、母號、子號、分號
        - 台灣糖業公司_不動產標售資訊
            - https://data.gov.tw/dataset/25752
            - 地段地號
        - 台灣糖業公司_房屋及設備標租資訊
            - https://data.gov.tw/dataset/25760
            - 地段地號


## (2) 委外等待認養型用地

- [水利署：網頁待爬，沒有精確位置](http://marketing.geo.com.tw/wlam/)
    - 水利署另外有釋出清冊，手動定位地點，已放到 Google My Map 
        - [水利署轄管河川綠美化場地可開放認養維護管理案件表 sheet](https://docs.google.com/spreadsheets/d/1Vhu4aHQ4BW31qPNAxcIUFVmiBapnEOrr4EnZYfU8A-o/edit)
    - 網頁資料比較完整，有照片與描述
- [國產署：已是資料集，土地清冊，地號](https://data.gov.tw/dataset/6054)
    - 已放到 Google My Map 
- [市有非公用土地-臺北市：已是資料集，內容待確認，地號](http://bit.ly/2VtzgMM)
    - 已放到 Google My Map 
- [市有非公用土地-新北市：已是資料集，內容待確認，地號](https://data.gov.tw/dataset/99026)
    - 已放到 Google My Map 
- [市有非公用土地-嘉義市：已是資料集，內容待確認，地號](https://data.gov.tw/dataset/52416)
    - 已放到 Google My Map 
- [市有非公用土地-臺南市：要詢問臺南市政府民政局 能否提供待認養空地清冊的資料集](https://data.gov.tw/dataset/85861)
    - 要詢問
- [海岸認養-新北市](https://www.epd.ntpc.gov.tw/Download?pltID=50)
    - 尚未處理

目前資料已整理為 地號 csv，預計會使用 地號 API 把土地清冊，轉成 geojson
這批資料是不同機關的「待認養綠化土地」，我整理成一份清冊 [清冊資料](https://www.facebook.com/groups/1417173811903954/permalink/2570707923217198/)

有了 csv 之後
- 地號 API：https://twland.ronny.tw/
- 感謝 @Brandon 轉成 [geojson](https://gist.github.com/bdon/b152bd4fc90000d4bc0f0e5fc939aa7a)
- 一筆認養可能會有多塊土地
    - 一筆認養土地 ----- 多塊土地土地輪廓(聯集)
- 各個資料集的 相近欄位整合


## (3) 保育地區內的公有土地
- https://www.facebook.com/groups/573697330058183/permalink/633912634036652/


## (4) 公共設施

- [國土利用調查中的 06, 07 類別，視為允許植樹公共設施範圍](https://drive.google.com/drive/u/0/folders/1stquBcMEF0CmLBxgx1xnQLf62eRg1RkB)

- 匝道交流道清單：內政部國道及省道道路中線，檔案中有提供「交流道位置資料」
    - https://data.gov.tw/dataset/73232
- [海岸法陸域範圍、河濱範圍：檔案](https://drive.google.com/drive/u/0/folders/1stquBcMEF0CmLBxgx1xnQLf62eRg1RkB)
- 海岸法陸域範圍、河濱範圍：線上地圖看範圍

<iframe width="100%" height="520" frameborder="0" src="https://classicdesign053.carto.com/builder/48e2d385-3328-495e-8bd8-0a352653f523/embed" allowfullscreen webkitallowfullscreen mozallowfullscreen oallowfullscreen msallowfullscreen></iframe>


## (5) 已認養土地、歷年曾有公私協力造林案例的地點

### 1. 公部門公布已認養土地

1.指定用途的捐款
- 林務局，有條文，須與每年林管處造林工作搭配；林務局不能主動勸募：airtable link
- 台北市大地工程處火燒跡地復育：airtable link

2.契約代管認養
- 有地點：非公用土地 (國產署/縣市政府)，綠美化，但不一定留存，可能會開發
- 有地點：水利署，有盤點 優先地點資料，也有正在認養單位的資料：https://bit.ly/3f3JE48
- 交通部國道高速公路管理局，釋出正在認養者的資料：https://data.gov.tw/dataset/46798
- 經濟部加工出口區管理處及所屬分處，沒有用地資料，也沒有正在認養的資料，認養規範業務網址：https://www.moea.gov.tw/MNS/populace/Apply/Apply.aspx?menu_id=32814&apply_id=374

3.其他：
- 抵換專案情況？要問環保署，應該沒有案例

### 2.好植地社群成員，盤點歷年曾有公私協力造林案例的地點
- 參考 Airtable 標記成果

---

# 3. Feasibility 環境面向的可行性評估資料

說明：推動者的評估過程中，涉及的資料、輔助圖資

## 可行性與優先性研判依據：開發行為、放流水、生物棲地

### (1) 重劃區範圍、都市更新範圍、環評範圍
- 研判原則：
    - 位在這些範圍內的基地，可能將會開發
    - 針對這些地貌大規模變動的案件，檢視其規劃方案內容，對於綠資源的措施
- [github](https://g0v.hackmd.io/E8GwG5SMSbSSBKT9KuuSGA#%E9%9D%A2%E7%8B%80%E5%9C%B0%E5%8D%80%EF%BC%9A%E9%87%8D%E5%8A%83%E5%8D%80%E3%80%81%E9%83%BD%E5%B8%82%E6%9B%B4%E6%96%B0%E7%AF%84%E5%9C%8D%E3%80%81%E7%92%B0%E8%A9%95%E6%A1%88%E4%BB%B6)
- 挑選其中「辦理中」的重劃區：https://bit.ly/tree-taiwan-map
- 都市更新：更新地區、更新事業 GIS 檔案
    - https://g0v.hackmd.io/@chewei/gis/https%3A%2F%2Fg0v.hackmd.io%2FApW7hYqAQTGOC-xq3xVRaA%3Fview
- 環評資料庫：https://eiadoc.epa.gov.tw/EIAWEB/Default.aspx

### (2) 全台污水處理廠位置
- 研判原則：
    - 放流水廠本身、周邊的綠地，可優先營造綠資源品質增進
- [sheet](https://docs.google.com/spreadsheets/d/1MNCHx2D9m-qjyAugxzm2GrMw1uTlzXumiqxNw42dI4A/edit)
- quick look in map：https://bit.ly/tree-taiwan-map 

### (3) 生物資料
- 研判原則：
    - 123
    - 123
    - 123
- [Collect: Tree Data](https://g0v.hackpad.tw/J4diKtZxBA8)
- [Collect: 樹種資料](https://www.facebook.com/groups/573697330058183/permalink/682281872533061)
- [Collect: 台灣生物資料](https://www.facebook.com/groups/573697330058183/permalink/669188003842448)[target=_blank]

### (4) 更多圖資：百年歷史地圖、樹木疫病通報 ..等
- [檢核方法](https://g0v.hackmd.io/vM3DLXAVRHut_8CTQTi3hQ)

## 一般業務輔助資料：苗圃、就近已綠化案例、植物園與環境教育場所、地區推薦樹種資料

### (1) 苗圃資料
- 輔助原則：
- ==已採用 Airtable 整合，標籤用「苗圃資訊」，[共筆](https://airtable.com/tblOnoodEDuuujStg/viwqoiE72L5gEVoXE/recr7EjAtq0cZyRvK)==
- [社團討論串](https://www.facebook.com/groups/573697330058183/permalink/706229156804999/)
- 現況產業討論
    - 種樹與苗圃產業，供需，需求為未來的時間點，難以掌控
    - 林務局 2021 年將著手建置 原生植物 的供需平台
    - 農業土地尚屬便宜，是否有相關模式可進場，能符合種樹計畫，也對於地主農民有益
    - 是否有相關法規

### (2) 公私協力種植案例地點
- 輔助原則：
- ==已採用 airtable 整合，標籤用「實際種樹-公有地公私協力」==

### (3) 植物園與技術諮詢機構
- 輔助原則：
- ==已採用 airtable 整合，標籤用「植物園 / 技術諮詢機構 / 環境教育場所」==

### (4) 樹種資料整理
- 輔助原則：
- 主要蒐集討論串與進度工作文件：https://www.facebook.com/groups/573697330058183/permalink/682281872533061/
- 林務局的推薦樹種，有推薦區位「公園」、「行道樹」等欄位，有助於對應到潛力基地(本身也可建立區位欄位)
- 植典｜植物資料庫：https://g0v.hackpad.tw/yax2EaDoKuH

---
# 4. Who / Social Actor 行動角色

## (1) 公司與企業，可能要串 公司登記資料 來取得聯絡方式？

1. 企業 CSR 部門或已有明確的永續作為
- [資料討論串](https://www.facebook.com/media/set/?set=oa.742040483223866&type=3)
- 標籤「企業社會責任與種樹行動 CSR」，已建立於 airtable
- 已匯入 Airtable 一批 2020 完成 CSR 報告書的名單，包含 email 信箱等

2. 企業將既有的業種業態，結合植樹 [airtable 正面表列](http://bit.ly/tree-taiwan-km)
- 標籤「異業合作 / 跨領域業務結合種樹」，已建立於 airtable
- 標籤「實際種樹-促進個人化植樹行動(名稱待確定)」，已建立於 airtable

3. 搜尋以「森林、樹木、綠」為名稱的公司登記 
- [社團討論串](https://www.facebook.com/groups/573697330058183/permalink/802892763805304/)
- 個案蒐集：https://bit.ly/346iAij
    - 歸納出 用字用詞
- 聯絡情境
    - 聯絡情境，例如公部門政策更為明確提供可認養土地，或其他情境
    - 聯絡方式，會有 email ?

4. 如何了解「企業有哪些工廠座落在哪些鄉鎮區？」

- todo：綠盟 透明足跡，有整理過「集團-企業統編-工廠」的資料，待查找，並評估如何與 airtable 內容整合
    - https://thaubing.gcaa.org.tw/group/search

## (2) 可接受委託的植樹團體與公司 (airtable 正面表列)
- 可接受委託企劃執行之的植樹與環境營造團體，airtable 正面表列
- 例如：慈心種樹部門、原生植物協會、愛種樹公司 ..等

## (3) 社區 / NGO / 社區大學 / 學校

- 低碳社區組織，特別是曾執行過「生態綠化」項目的單位
    - 爬? 環保署低碳社區名單：https://www.facebook.com/groups/573697330058183/permalink/744555012972413/

- 環境類 NGO
    - 來源：https://www.facebook.com/groups/573697330058183/permalink/742056716555576/
    - 如何篩出適合的 NGO ? 

- 在地創生團隊名單資料庫
    - 來源：[link](https://airtable.com/shr4f3DnuXOslFyss/tbl9y7Ol6R06GkNNm/viwhE4xzwErZUSRrO/rec7B3RV9zFM64V9u?blocks=hide)

- 社區大學
    - 來源：https://www.napcu.org.tw/college_list.html

- 學校
    - 來源：大專院校 USR：http://usr.moe.gov.tw/
    - 來源：教育部綠色學校夥伴網絡：https://www.greenschool.moe.edu.tw/gs2/

## (4) 已認養土地的認養單位

- 「代管型認養」類型，從 政府資料平台 用關鍵字撈
- 應該有：
    - 水利署水利用地認養單位
        - https://bit.ly/3f3JE48
    - 交通部國道高速公路管理局釋出認養
        - https://data.gov.tw/dataset/46798

## (5) 實踐環境低碳作為的團體名單

- 舉辦環保低碳活動的民間團體名單 
- 有地緣屬性的 地方創生、社區環境營造、休閒農業協會..等名單
    - [以桃園市為例進行盤點](https://docs.google.com/document/d/1WDCIoKPXaSbnQ2zHNCFMMzNX-Sv2Lx8NyixdP93gUcM/edit)





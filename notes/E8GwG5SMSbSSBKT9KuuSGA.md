---
tags: tree
---

# 分析標的：依照空間類型分項描述

:::warning
文件目錄
[TOC]
:::

## 線型空間 / Treepedia / 綠道分析方法

* [「哪些線型空間種類，是容許植樹的？」討論串](https://www.facebook.com/groups/573697330058183/permalink/682494789178436/)

### 綠化現況分析方法

* [Treepedia](http://senseable.mit.edu/treepedia) 街景綠視率分析方法
    * source code
        * https://github.com/mittrees/Treepedia_Public
        * https://github.com/y26805/Treepedia_Public#using-the-google-maps-api
    * notes
        * MIT 的 code 很久沒有維護了，原碼用 python 2 寫的，要更新來適用於 python 3 & 新版本的 modules 
        * 要先設置 GDAL 環境
        * 會用到 python 的 fiona, gdal, ogr, osr module，孰悉的人會上手比較快
        * 需要預先申請 google API key
        * step 4. 需要安裝 pymeanshift - https://github.com/fjean/pymeanshift/wiki/Install
    * 程式碼流程
        1. 自行從 osm 抓下需要的 streets polyline data
        2. createPoints(dot)py > 從前述道路 polyline data 擷取點位清單
        3. metadataCollector(dot)py > 依前述點位清點抓取 streetview metadata
        4. GreenViewCalculate(dot)py > 抓取街景，計算 GreenViewIndex
        5. Greenview2shp(dot)py > 輸出結果為 ESRI shp 格式
	* 虎尾糖鐵 demo
		* [modified code in github](https://github.com/Monaludao/Treepedia_Public)
		* [結果 google drive](https://drive.google.com/drive/u/0/folders/1Nm3OxqoJvY86Yls2chM8ZVo-0yzZdHTO)
    * 課題描述
        * https://www.facebook.com/groups/573697330058183/permalink/710552026372712/
        * 有沒有比較簡易的方式，把各點視覺化，MIT 網站是用色系對應綠視率數字高低

<iframe width="100%" height="520" frameborder="0" src="https://classicdesign053.carto.com/builder/f0d0d250-c200-4af6-938b-8e905ee841f7/embed" allowfullscreen webkitallowfullscreen mozallowfullscreen oallowfullscreen msallowfullscreen></iframe>

* 其他
    * 資料成果前端參考
        * mapbox：https://docs.mapbox.com/mapbox-gl-js/api/
        * 這篇文章裡有提到類似 NYC Tree 網站：https://blog.mapbox.com/style-components-in-studio-77cc2f98815b
    * 畫面來源
        * 能否改用自行拍攝的 360 照片成果
        * 開源的街景圖 https://www.mapillary.com/
    * 濱水區植生演替與沖積河床演變之動態交互地貌調整機制
        * 摘：本研究以Google衛星影像與Google街景的資料，找出濱水區植生完整覆蓋且長期存在、不易被洪水移除的河段，並分析其溪流功率特性，研究結果發現，透過總溪流功率、單位溪流功率兩項因子的大小與其變化，可清楚的描述河川上游到下游的水流沖刷力特性，進而區分河川型態、描述河川型態因子的變化趨勢。 
        * https://www.grb.gov.tw/search/planDetail?id=12028097

* 其他技術方案
    * opencv
        - https://www.accupass.com/event/2006230339551579953893
        - https://www.facebook.com/groups/pythontw/permalink/10160212223013438/
        - https://www.facebook.com/100003344591197/posts/3024788294309294/
    
* 應用情境
    * 糖鐵綠道沿線綠視率
        * 預計標的：虎尾的追火車與社區綠道的路線，[來源](https://www.tmitrail.org.tw/news/202)
        * (1) 步行前往虎尾圖書館取車，單車走讀路線：糖廠圍牆→虎尾鐵橋→興南有機村→回虎尾驛→合同廳舍、布袋戲館、故事館→涌翠閣→大崙腳
        * (2) 虎尾驛糖廠出發→中山路鐵枝路腳→蠟筆工廠→北溪剪紙彩虹村參觀→追風到世紀交會站（10:00）→眷村建國二村→建國一村→散策中山路第一街→回虎尾驛
    * 路線繪製：https://bit.ly/2X6GruM


### 綠道路線資料
- 討論串：https://www.facebook.com/groups/tmitrail/posts/3056008621340783/
- 綠道資料
    - 國家綠道－山海圳國家綠道請參考林務局山林悠遊網官網資訊：
        - https://recreation.forest.gov.tw/Topic/MSTW
    - 國家綠道－淡蘭國家綠道的GIS可以參考觀光局淡蘭主題網站，裡面有淡蘭攻略可以下載圖資：
        - https://danlantrail.necoast-nsa.gov.tw/
        - 分散的路線
    - 國家綠道－樟之細路的GIS可以參考健行筆記與客委會合作的專區：
        - https://hiking.biji.co/index.php?q=minisite&id=223&nav=1841
        - 民間社團 https://www.facebook.com/share/Ts6EjLkmbAQ8499x/
    - 縣市綠道：https://www.tmitrail.org.tw/roadmap/1477#block-system-main
- 舊糖鐵路線
    - https://g0v.hackmd.io/@chewei/taisugar/


### 探討「道路是否尚有潛力改造為綠道？」分析方法

input 資料
- 綠化現況
    - 行道樹資料 (臺北84840, 新北13826, 臺中118404)：https://bit.ly/3lffjCP
    - 5590筆，受保護樹木類：https://bit.ly/30uVu2N
    - 樹穴資料，僅臺北市有釋出：https://bit.ly/3isBx2z
- 人行道資料
    - https://data.gov.tw/dataset/58791
- 建物範圍外框資料
    - 臺北市：建築物的輪廓資料，嚴格來說台北市沒有正式釋出，但因為曾釋出一批 3D 建物資料是開放資料，其投影面積就是建物輪廓的基本 http://bit.ly/2DfQqpZ
    - 臺中市：臺中市建物_WGS84 https://bit.ly/37Ldiue
- 道路寬度
- 車流量資料
- 管線資料
- 設施物資料

output 對策種類
- 車道數減少
- 車道數不變，寬度瘦身
- 新增人行道
- 新增植栽槽-灌木
- 新增植栽槽-喬木樹穴


## 頂視圖的樹冠辨識方法

方法蒐集：
- Deep Forest 物件辨識應用於航照頂視圖
- TreeTect 運用 RGBI 高精度圖資辨識樹冠
- Vadstena: AI-based Automatic Tree Extraction Explained 推論產製 樹木 立體模型
- https://airtable.com/shr4f3DnuXOslFyss/tblOnoodEDuuujStg/viwqoiE72L5gEVoXE/rec5zOcSexoZQbrK0?blocks=hide
 


## 公共設施用地

### 遙測 NDVI 套疊公共設施用地

- [Discuss: Satellite](https://g0v.hackmd.io/mmCYL3L9Tgi6xHIMBvz5Hw)
- [各縣市 NDVI 2019](https://drive.google.com/drive/folders/11K40l5W2jQ3U74f7Gm8hC5MJQzsQ5Gkw)
    - [Quick Look: NDVI-map](https://patchbyplanting.carto.com/builder/058b8da2-d646-4fff-b5ee-0640492d5d68/embed)
- NDVI(0-0.2,0.2-0.5,0.5-1.0) / 海岸範圍 / 水岸範圍 / 公共設施範圍
    - https://drive.google.com/drive/folders/1stquBcMEF0CmLBxgx1xnQLf62eRg1RkB
- 方法說明文章
    - https://sites.google.com/view/tree-taiwan/tree-counting

<iframe width="100%" height="520" frameborder="0" src="https://patchbyplanting.carto.com/builder/058b8da2-d646-4fff-b5ee-0640492d5d68/embed" allowfullscreen webkitallowfullscreen mozallowfullscreen oallowfullscreen msallowfullscreen></iframe>



圖資依據
* 國土利用調查、土地使用分區，較允許種樹的類別
* 地貌現況：NDVI、可見光、正射、街景、照片
* 其他：公有土地，但不一定允許植樹

歸納幾個框列的觀點 
* 較容許種樹的類別種類，[種類例如「公園綠地、學校..等」](https://photos.app.goo.gl/gr5aNr3CZEChyaxR6)
* 有機會透過環境設計方案來提升綠覆，例如「停車場」類型
* 揀選入「有潛力補植」的基地清單中
* 圖資方法之外來源：例如民間團體提報
* 一個一個排除個案情況(例如桃園新勢公園大草地下面是礫間淨化設施，不適合植樹)

得到清單
* 確定好每一塊地塊形狀邊界位置，列冊編號
* 查得到 A 地的管理機關 
    * 用地塊位置中央經緯度，來查座落地號，查謄本權屬
        * 已處理潛力用地相鄰地塊合併之後的【共計 2364 個用地 csv (取範圍內部的一個經緯度、保留國土利用調查的描述屬性文字)】，處理步驟簡記：(1)相鄰polygon合併，使用QGIS Dissolve功能，但只能整合成一筆資料，導致屬性遺失 (2)使用QGIS Multipart to singlepart功能，得到每一塊用地 (3)使用QGIS 質心功能，取得每塊用地的一個代表座標，並手動調整環狀型基地取質心後脫離 polygon 的問題，[臺南市大順三路旁的用地、臺南市天鵝湖公園](https://www.facebook.com/groups/573697330058183/permalink/663917004369548/) (4)清理可用欄位，得到 [潛力用地的經緯度清冊](https://bit.ly/3bkBYcA)
        * 希望能轉出【保留國土利用調查的描述屬性文字+地號資料】geojson 檔案，同時也會嘗試用地號清單去查地籍謄本資料，[經緯度轉段號，目前 twland.ronny.tw 有支援這功能](https://twland.ronny.tw/#121.55379447147,24.985873733201)，感謝 [任翔 協助轉出檔案](https://drive.google.com/file/d/1CVSfZsCMUehfPeP-J4Tff3hiNXKj4sfV/view)
        * TODO：先歸納理想中的「潛力用地」資料內容，希望能包含以下欄位：
            * A. 圖徵有兩種：(1) 點資料 point，以及 (2) 面資料 polygon
            * B. 額外描述：(1) point 沒有描述資料因為是人工於畫面上判斷點選 (2) polygon 這類有國土利用調查的描述資料，裡面有提供這塊地用地種類例如 070201 代表公園
            * C. 定位經緯度：(1) point 沿用，以及 (2) polygon 取出內部中心質心的經緯度
            * D. 關聯地號：用定位經緯度所取得的 地號資料
            * 總的來說，2364 個潛力用地，可以知道每一塊的位置，關聯的地號，方便接續查找謄本，若還有額外的國土利用調查資訊也一併包在這份資料內
        * 感謝 Hank Chou 協助將 地號屬性 合併至 潛力用地資料
            * [polygon](https://drive.google.com/file/d/15rScD2zof-xMA6NsxZWEoTEQQTWEy5Yw/view)
            * [point](https://drive.google.com/file/d/1gM04NfFOF0YetCHGEMUsSqHz6r5ii30J/view)
        * 哈爸 的處理成果
            * https://www.facebook.com/100000192830591/posts/3416918394991221/
    * 了解「權屬單位」
        * 用地號申請謄本，需要經費
        * 洽談合作單位
    * 詢問「權屬單位」，並確認「管理單位或綠化業務負責的現況」



* 清單應該每年度沿用，增減

通知管理機關，引導下一步
* 通知 A 地的管理機關，提醒補植，理想上能提供該機關建議
    * 若能預判 A 地的補植可行方案，相關內容與資源連結..等應一併提供
* 或願意登錄到 [一站式找地種樹平臺](https://g0v.hackmd.io/H2j1KBOETJiSA-EuzriArA) 提供民間認養綠化
* 或採用 標案進行規劃設計與營造案件
* 或採用 願景論壇模式 ([方案探討](https://beta.hackfoldr.org/tree/https%253A%252F%252Fg0v.hackmd.io%252FICuhRd4yRRilOTYNL5bbzQ)) 


### 探討「國土利用調查」套疊「土地使用分區、非都市編定」


如果可以從 國土利用調查 + 都市計畫法規，兩者對照，了解此用地未來還會不會有大規模的開發與地貌改變

若一塊基地，國土利用調查現況是公園綠地，土地使用法規屬於開發型的建築型態
- 針對未來的平面配置，訴求留現地樹木或基地內移植
    - 等到開發前再處理移植
- 不種喬木
    - 提早移植，並置換成開闊型的公共設施(體育場地或其他) 
    - 只能做 簡易綠化或灌木或草坡地形，因為以後還要移植

筆記區 https://docs.google.com/spreadsheets/d/1v7XkCpOZrdgwix4IZLhu2KPAHJkR6AyyLDeW14qLkGo/edit
預計搬到 airtable https://airtable.com/shr4f3DnuXOslFyss/tblyXkOXTG0sm9PHy/viw9hckve8oCRrvJ9?blocks=hide


### 地貌架構下的綠覆評比資料

目前進度：https://sites.google.com/view/tree-taiwan/%E7%B6%A0%E8%A6%86%E8%A9%95%E6%AF%94

* 會需要到鄉鎮區尺度，拜訪新北市景觀處後的回饋意見
* 線上展示看要找哪個工具，方便網頁瀏覽者探索排序
    * 嘗試放在 Airtable https://sites.google.com/view/tree-taiwan/ndvi?authuser=0



---

## 面狀地區：重劃區、都市更新範圍、環評案件

說明：重劃與環評，會釋出預計改變地貌的地區範圍，其正當性與環境衝擊需另從法制與社會倡議機制著手，專案這邊蒐集重劃與環評案件，著重在取得地理位置與範圍。
1. 若該案件正在規劃中，可檢視其正當性與必要性，以及其規劃方案是否因應地貌環境。
2. 若該案件已通過，公共建設施工過程中的綠資源營造狀況，可作為檢視標的。

### 重劃區

* 如何知道近期重劃區 ?
    * 內政部「土地開發資訊系統」
        * https://develop.land.moi.gov.tw/Normal?ssl=true
        * kiang 已爬圖台上有 KML 的檔案
            * https://www.facebook.com/groups/573697330058183/permalink/726689284758986/ 
        * GoogleMyMap 上面的圖層是「規劃中、辦理中（已完成的就沒納入）」的資料
            * https://bit.ly/tree-taiwan-map
            * 「規劃中、辦理中」有部分沒有經緯度，整理在這個清冊：https://docs.google.com/spreadsheets/d/1PIPNTMLkjcUkXadQxy7bYGc5CfBag73ODjjcTxZ2UCc/edit
* 重劃區內的公共設施，道路沿線

### 都市更新範圍

* 都市更新範圍地理資料
    * 都市更新入口網
        * https://twur.cpami.gov.tw/zh/urban/area/map/tgos
        * kiang 已爬圖台上有 KML 的檔案
            * https://www.facebook.com/groups/573697330058183/permalink/834935617267685/

### 環評案件

* 舉例：高雄仁武，環評審查
    * https://e-info.org.tw/node/219124
* 環評系統
    * https://eiadoc.epa.gov.tw/EIAWEB/Default.aspx


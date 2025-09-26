---
tags: GIS, 防災, 民防
---

# WaytoSafety 隨時隨地知道避難場所位置<br>Shelter Map (Taiwan, Japan, Korea, HK)

:::info
Channel:
- 臺灣資料討論頻道 g0v Slack #disaster-go
- 日本與韓國資料的討論頻道 g0v Slack #facing-the-ocean
    - 這個頻道有與 Code for Japan, Code for Korea 的社群共用交流

Contributor: 
- 感謝投入資料勘誤
    - chewei 
    - [林博仁(Buo-ren, Lin)](https://brlin.me)
    - Reily
    - ying
- supaplextw 協助找到消防署釋出的全台資料集 & 分享 OpenStreetMap 過去有整合過一次防災避難收容點位資料
- hwan 分享韓國的 Shelter 查詢網頁，以及用詞建議 "대피소" 也分享韓國政府資料開放平台上避難所的 API 釋出網頁，並且彙整靜態資料 csv (2024.01)
- Kurumi Muto 分享 指定緊急避難場所の全国データ（公開している市区町村すべて）csv 檔案下載網址

Doc
- https://g0v.hackmd.io/@waytosafety/home/
:::

:::warning
文件目錄
[TOC]
:::

---

## Offline Map

### TW 全國各村里簡易疏散避難地圖

#### 「避難圖」檔案在哪裡？

民間盤點「各村里簡易疏散避難地圖」下載位置，另開網址：https://docs.google.com/spreadsheets/d/10mkZhe8VB0CfkcC3wq4cDkXA5fGOlKOO5ncebU68VJ0/edit#gid=0

<iframe height="1300px" width=100% src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQDKn3TO0jGy9H4tQX2r-p5szXinK41gGZmFyzNcn2gTG46rXi28poYNA02rBu6HW3Tuoo0envhEL3o/pubhtml?widget=true&amp;headers=false"></iframe>


- 消防署建立的整合入口查詢網頁：https://www.nfa.gov.tw/cht/index.php?code=list&ids=82
    - 但是有幾個縣市網址失效，例如南投縣

避難地圖的下載來源補充：
- 政府資料開放平臺上面有部分的縣市有釋出 [開放資料](https://data.gov.tw/datasets/search?p=1&size=10&s=_score_desc&rft=%E5%90%84%E5%8D%80%E9%87%8C%E7%96%8F%E6%95%A3%E9%81%BF%E9%9B%A3%E5%9C%96)
    - 20240120 有看到 臺北市
- 國家災害防救科技中心 NCDR 資料平台上，也有釋出部分縣市的避難地圖資料
    - 資料平台網址：https://datahub.ncdr.nat.gov.tw/dataset
    - 20240108 chewei 撰寫申請資料名稱包含「避難」一詞的資料集或檔案，等待審核；需於 2024-01-15 之前下載
        - 檔案資料夾：https://drive.google.com/drive/folders/1-KoiXmLJnQR0SWiy3xnbbYFTf0umUIgV?usp=sharing

民間撰寫的介紹文章：如何找到自己所在的村里避難地圖？
- https://www.safetaiwan.com/blogs/disaster-prevention-column/evacuation-map

#### 針對「避難圖」的數位化專案

全台防災/防空避難所大統整
https://g0v.hackmd.io/UNg_8F3FTuynAwbV7flp-w?view
https://g0v.github.io/evacuation-map-viewer/

### TW 特定地區或園區的避難地圖

國內研究「地形特徵圖」有針對部分地區有產製避難路線建議章節
https://atlas.geo.ntnu.edu.tw/ 
- 花蓮縣玉里鎮-D018大規模崩塌潛勢區 https://atlas.geo.ntnu.edu.tw/html/antun.html
    - 這本有介紹避難路線與各部落避難建議據點
- 屏東縣來義鄉來社溪 https://atlas.geo.ntnu.edu.tw/html/laiyi.html
    - 這本有介紹避難路線與各部落避難建議據點
- 高雄市桃源區荖濃溪 https://photos.app.goo.gl/oJ1VFzUmBvSJJm1m9
    - 這本有介紹避難路線與各部落避難建議據點
- 木柵 https://atlas.geo.ntnu.edu.tw/html/muzha.html
    - 不過，這本並沒有談到避難路線 
- 南投縣草屯鎮 https://atlas.geo.ntnu.edu.tw/html/caotun.html
    - 不過，這本並沒有談到避難路線 
- 臺東縣成功鎮 https://atlas.geo.ntnu.edu.tw/html/chengkung.html
    - 不過，這本並沒有談到避難路線

產業與科學園區
- 國家科學及技術委員會新竹科學園區管理局
    - 新竹園區防災地圖(pdf檔)、竹南園區防災地圖(pdf檔)、龍潭園區防災地圖(pdf檔)、銅鑼園區防災地圖(pdf檔)、宜蘭園區防災地圖(pdf檔)、生醫園區防災地圖(pdf檔)
    - https://www.sipa.gov.tw/home.jsp?mserno=201604180001&serno=201001210016&menudata=ChineseMenu&contlink=ap/download_view.jsp&dataserno=202307040001

其他，找找看
- 交通園區
- 海生館

### 應用、實際使用

有相關應用經驗嗎？

:::spoiler 過往筆記
其他：Vectorization 將內容數位化為資料
- 民間專案曾嘗試建立線上地圖 https://github.com/lowiki-org
- 討論：於 OpenStreetMap 如何標記防災避難收容處所 https://hackmd.io/@osm-tw/HyUvtrOmu
- 討論：是否有可能用 群眾標註地圖，把簡易疏散避難地圖上面的地點，標記到 群眾標註地圖 上
    - 標記測試：
        - 先找到一幅簡易疏散避難地圖檔案，以「臺北市中山區朱園里」為例 https://www-ws.gov.taipei/Download.ashx?u=LzAwMS9VcGxvYWQvMzEzL3JlbGZpbGUvMTI4NDEvMjMwMi9iMzJkODg0MC05MzU0LTQ2ZGYtYTFiZi1iMDY0MWRhM2MwN2QucGRm&n=NjMwMDQwMF8wMzbkuK3lsbHljYDmnLHlnJLph4xf5Lit5paHLnBkZg%3d%3d&icon=..pdf
        - 標記「避難收容處所(備用)：臺北市中山區長安國中」，把地點標記在校門出入口的位置 https://commutag.agawork.tw/image?dataset=5e6b06a177e80cf258b9ba72&image=6596b33238c282d22899f2a2
:::

## Geo Data

### 【TW 臺灣】Shelter / ひなんじょ(避難所) / 대피소 / 防災避難收容處所

#### 政府釋出的資料與查詢工具

2025.04 開始，又發現許多錯誤

資料來源 - https://data.gov.tw/dataset/73242

民間開發者 kiang 運用政府資料來源，建置地圖
https://tainan.olc.tw/p/shelter/
從地圖中可以看到政府釋出的避難場所資料錯誤狀況

錯誤狀況列舉
- 有 13 筆避難場所資料，飄在臺灣海峽海洋中
- 桃園市新屋區，避難場所點位全區消失了，海上也找不到他們了
- 忠孝新生捷運站有 36 個避難場所點位
- 臺北市大安區大安運動中心，沒有資料
    - 會挑這個運動中心，是因為 2024 年的社群勘誤成果，有找出 140 個經緯度錯誤的資料，包含這個大安運動中心，作為驗證抽檢，發現還是錯的
    - 140 個經緯度錯誤的資料集比對成果：https://docs.google.com/spreadsheets/d/1l_Au7txDgsknhHKvhLksfSAzeMmSoaih3m4pMdqwrBU/edit


##### 消防防災e點通 APP - 避難收容處所
- 形式：App
- 網址：https://www.moi.gov.tw/News_Content.aspx?n=10&sms=9009&s=265624&fbclid=IwAR3uH56mpYYcJnMiwVZOT5mrNCz8yersinbqQVbohIMerFULwEGjaIlRbV4
- 課題：
    - 新北市頂溪國小 (新北市永和區文化里文化路133號)
        - 消防署 防災 APP，「沒有」這個資料
        - 消防署 防災 APP 的 離線圖資，「有」這個資料
        - 衛服部 避難地圖網站，「有」這個資料


##### 衛服部避難地圖查詢網頁 - 避難收容處所
- 形式：地圖網頁
- 課題：
    - 查詢 新北市中和區，使用者按完查詢之後
        - 點選「地圖版」想看地圖，使用者如我以為是全部的中和區點位會顯示
        - 錯了 !
        - 地圖上只顯示清單的第一頁
        - 例如「沒有」積穗國中與積穗國小，不是沒資料，是因為只顯示出清單的第一頁，而 積穗國中與積穗國小 在清單的第二頁
    - 衛服部地圖中的 頂溪國小的經緯度位置 (定位在某棟大樓但並非校門)
        - 跟，消防署 防災 APP 的 離線圖資中的 頂溪國小經緯度位置 (定位在校門)
        - 兩者經緯度不一樣

::: spoiler 點我看 2024 年針對政府各類避難場所的圖台圖資勘誤

##### 全民防災e點通 - 避難收容場所
- 形式：地圖網頁
- 網址：https://bear.emic.gov.tw/MY/#/home/map
    - 勾選「避難場所」圖資，可以呈現在地圖上
- 資料錯誤：
    - 尚未花費大量力氣普查勘誤此地圖網頁，但可以簡單就隨機發現許多避難場所位置有誤
    - 錯誤地點截圖相簿：https://photos.app.goo.gl/BYcLneADj73YArEv7

##### 全民防災e點通 - 災民收容救濟站
- 形式：地圖網頁
- 網址：https://bear.emic.gov.tw/MY/#/home/map
    - 勾選「災民收容救濟站(衛服部提供)」圖資，可以呈現在地圖上
- 討論：
    - 「災民收容救濟站」有另外釋出資料嗎？
    - 少數「災民收容救濟站」與「避難場所」的空間位置是一樣的，但多數救濟站並不是避難場所
    - 對於民眾來說，是否要前往「災民收容救濟站」？
- TODO
    - 預計寫信詢問 衛生福利部，如何理解「災民收容救濟站」？是否作為避難場所？

##### 衛服部避難地圖查詢網頁 - 避難收容處所
- 形式：地圖網頁
- 網址：https://rvis.mohw.gov.tw/mgov-rvis/home/map#
- 資料錯誤：
    - 尚未花費大量力氣普查勘誤此地圖網頁，但可以簡單就隨機發現許多避難場所位置有誤
    - 錯誤地點截圖相簿：https://photos.app.goo.gl/BYcLneADj73YArEv7

##### 消防防災e點通 APP - 避難收容處所
- 形式：App
- 網址：https://www.moi.gov.tw/News_Content.aspx?n=10&sms=9009&s=265624&fbclid=IwAR3uH56mpYYcJnMiwVZOT5mrNCz8yersinbqQVbohIMerFULwEGjaIlRbV4
- 資料錯誤：
    - 尚未花費大量力氣普查勘誤此地圖網頁，但可以簡單就隨機發現許多避難場所位置有誤
    - 錯誤地點截圖相簿：https://photos.app.goo.gl/BYcLneADj73YArEv7

##### 新北市政府防災地圖 - 避難收容處所 
- 形式：地圖網頁
- 網址：https://www.dsc.ntpc.gov.tw/DRPI/ntcdmap
- 資料錯誤：
    - 尚未花費大量力氣普查勘誤此地圖網頁，但可以簡單就隨機發現許多避難場所位置有誤
    - 錯誤地點截圖相簿：https://photos.app.goo.gl/BYcLneADj73YArEv7

##### 【聚焦檢視】消防署釋出全台「避難收容處所」點位資料 🔥🔥🔥
- 資料欄位：序號、縣市及鄉鎮市區、村里、避難收容處所地址、經度、緯度、避難收容處所名稱、預計收容村里、預計收容人數、適用災害類別、管理人姓名、管理人電話、室內、室外、適合避難弱者安置
- 資料格式：csv
- 資料下載網址：https://data.gov.tw/dataset/73242

:::

#### 勘誤

民間下載 20240107 資料集建立的線上地圖
- 線上地圖搭配篩選器：https://app.awesome-table.com/-NsTj-d3gKaoZCgi28Xq/view
    - 輔助用線上地圖 (無篩選器)：https://umap.openstreetmap.fr/zh-tw/map/2024010
    - 地圖工作歷程筆記
        - 20240221: "This app has exceeded its free usage quota. If you are the owner of the app, please activate a paid subscription, or the app will be deactivated on March 6th 2024." 免費版 Up to 500 views
        - 20240308 chewei 已再換一個 [地圖網址](https://app.awesome-table.com/-NsTj-d3gKaoZCgi28Xq/view) 
        - 20250408 可能先確認 政府資料開放平台 有沒有重新上架新的資料集
- 地圖所依據的資料集 Googlesheet：
    - https://docs.google.com/spreadsheets/d/1l_Au7txDgsknhHKvhLksfSAzeMmSoaih3m4pMdqwrBU/edit


---

消防署 csv 資料集勘誤進度說明：
- 勘誤成果請見 [Googlesheet 資料集](https://docs.google.com/spreadsheets/d/1l_Au7txDgsknhHKvhLksfSAzeMmSoaih3m4pMdqwrBU/edit)
- 【建議優先修正之類型】位置有誤，經緯度位置並不是該場所名稱的位置
    - 130 筆位置有誤
        - 20240117 應該不止 130 筆，目前隨機找一個鄉鎮區，都可以找出 2~3 個標錯位置的
        - 錯誤模式明顯可猜想來源單位有誤
            - 臺北市政府體育局：只有松山運動中心是對的，其他 11 個行政區運動中心與 1 筆臺北體育館，經緯度都標錯
            - 桃園市政府新屋區：整批經緯度飄到海上
            > [name=Ying 新屋區已全數勘誤完畢。但有些收容處所 - 社區活動中心已暫停營業或變成其他東西（幼兒園、警局），不確定還有沒有收容作用。最後一筆下埔里的找不到，不過有查到另一個名稱類似的收容處所，同里但地點不同且適用災害也略不同。 除桃園新屋之外，台北的士林北投兩區也全數勘誤完畢。]
    - 勘誤方式說明
        - 主要方式，用線上地圖，找出偏差位置太遠的
            - 海域上、中國範圍、非洲範圍
            - 20240108 done
        - 主要方式，用線上地圖，隨機瀏覽，找出經緯度完全重疊的
            - 例如臺北市忠孝新生捷運站匯聚了 36 筆經緯度完全一樣的資料集，且都不是臺北市避難場所
            - 例如序號 4620、4621、4622 霧峰國中與國小經緯度一樣
        - 次要方式，隨機瀏覽，透過衛星底圖的地貌 (深山森林、沿海海域、魚塭) 來指認錯誤標記資料
            - 可優先檢視點位位置座落在深山森林中，例如尖石鄉有幾個經緯度位置明顯是在無道路的森林中
            - 可優先檢視島嶼海岸線附近，通常有一些點位位在海面，離海岸線不遠，但是要近看才看到的是在海面
            - 可優先檢視魚塭水域，有一些點位標錯標在魚塭中
        - 次要方式，隨機瀏覽，如果衛星底圖的建物房舍看起來很小
            - 如果衛星底圖看起來房舍很小，不像是公共建築樣式，其實就有可能是標錯位置
        - 不點開就完全不知道是錯的
            - 例如臺北市多個行政區運動中心經緯度，運動中心經緯度都與該行政區另一個避難場所共用同一個經緯度，位置還是在市區，所以不點開資料實在不知道是錯的 
- 【建議優先修正之類型】沒有描述該場所適用哪些種類的災害
    - 164 筆：沒有說明場所適用哪些災害種類 (地震、水災、土石流、坡地災害、海嘯、核子事故)
    - 個案舉例：
        - 序號 5918 金山區獅頭山公園，公園位置緊鄰海岸線且屬於小型半島一旁的漁港屬於凹口，都是海嘯加劇的地形，可能不適用於 海嘯避難
- 【建議優先修正之類型】地區範圍稱呼用詞待確認
    - 15 筆
        - 序號 5232、5244、5799
            - 收容場所與預計收容範圍，地理距離超過 10 公里
        - 「預計收容村里」這個欄位，有出現像是「新北市漳和區 (序號 5072)」、「桃園市會稽區各里 (序號 510)」、「桃園市埔子區各里 (序號 5087)」、「三村 (序號 510)」
    - 討論：預計收容村里，不少資料會寫 "全區" 應該是指 "行政區" ？
        - 案例：
            - 序號 653，高雄市梓官區蚵寮國民小學（備用），「全區」應該指的是「高雄市梓官區」
            - 序號 5443，榮星花園公園，「全區」應該指的是「臺北市中山區」；[岔題延伸討論] 此個案可以實質討論，因為中山區包含基隆河北側與南側，榮星花園位在南側，基本上大規模災害，是否適合北側民眾跨越基隆河的少數橋梁，到南側榮星花園，或是應考慮在北側的大型場所避難？
                - 從資料標記的方便程度來說，會需要有「中山區北側的里清單」與「中山區南側的里清單」
    - 討論：預計收容村里，除了請人員手動輸入中文文字方式之外，有沒有什麼改善方向？
        - 目前中文文字輸入結果無法統一，逗號或用詞不統一、難字無法輸入正確
        - 改善方向：選項化
            - 提供村里選項，請資料維護者，點選村里
            - 要注意不同縣市會有同一個村里名
        - 改善方向：地理計算
            - 場所中心出入口經緯度，依據實際可行走道路，進行一個時間長度的可及範圍所涵蓋的村里
                - 類似方式的操作網頁：https://www.map8.zone/showcase/snapToRoads
                    - https://www.map8.zone/map8-control-api-docs/map8-js-route/map8-js-route.html
- 【建議優先修正之類型】地名有難字無法正確顯示
    - 137 筆：地名難字
- 聯絡人員姓名有難字無法正確顯示
    - 75 筆：聯絡人員姓名難字
- 缺字或漏字 (並非難字)
    - 197 筆：缺字，多數是沒有填寫場所座落在哪一個村里

---

【構想】程式自動勘誤
- [較有把握] 陸域範圍取交集
- [不太有把握] 用地址產出經緯度，與原始資料經緯度計算距離
    - 課題：許多地址產出的經緯度也不一定在場所位置
- 許多資料的經緯度位數太少，其實並不是很精確定位在該場所
    - 推測是不是因為在資料整理的過程中，欄位被省略小數點以下的位數
    - 討論舉例
        - 序號：4894
        - 桃園市桃園區福林里建國國中
        - 地址：介新街20號
        - 原始資料的經緯度為：24.9774,121.3077

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b1539de06e7a1dbd885682d5b0776861.png)


---

#### Todo：資料勘誤與回報

##### 寫一份給行政院的，整合說明內政部消防署、衛服部
- 行政院院長信箱：https://eyemail.ey.gov.tw/WWW/MailToPremier.aspx
    - 進度：
- 內政部部長信箱：https://service.moi.gov.tw/
    - 進度：
- 消防署署長信箱：https://www.nfa.gov.tw/cht/index.php?code=list&ids=523
    - 進度：
- 衛服部部長信箱：https://www.email.mohw.gov.tw/
    - 進度：
- 審計部：https://www.audit.gov.tw/p/423-1000-6.php?Lang=zh-tw
    - 例如 審計部臺灣省臺東縣審計室，針對避難收容處所提出檢視意見 https://www.audit.gov.tw/p/16-1000-8918.php?Lang=zh-tw
    - 進度：

【草稿】

您好，我們是民間專案「WaytoSafety 隨時隨地知道避難場所位置」，我是專案成員 chewei

本專案成員近期主動檢視國內「防災避難收容處所」的地點資料、地圖網頁、APP，已發現許多場所位置有誤，分項說明如下：

一、消防署釋出全台避難收容處所點位資料
- 形式：資料集
- 網址：https://data.gov.tw/dataset/73242
- 資料錯誤說明：(以下錯誤數量統計至20240117，有嘗試盡量勘誤，但判斷應該還有資料尚未勘誤出來)
    - (1) 至少超過 200 筆資料，其地點經緯度位置標示錯誤，恐具有誤導民眾導致誤判之風險，且資料無法應用於平時災防避難演練活動。
    - (2) 有 161 筆資料，沒有說明該場所適用哪些災害情境，例如資料序號 5918 金山區獅頭山公園，公園位置緊鄰海岸線且屬於小型半島一旁的漁港屬於凹口，都是海嘯加劇的地形，可能不適用於 海嘯避難，但此筆資料並未說明該場所適用哪些災害情境，恐具有誤導民眾導致誤判之風險，且資料無法應用於平時災防避難演練活動。
    - (3) 有 351 筆資料，文字缺漏無法完整傳達地點名稱
- 民間志願者已自主進行資料勘誤，「已勘誤之資料序號清冊」整理如下
    - 以下資料集，設有「勘誤」欄位，欄位採用選單，說明該筆資料的錯誤類型
    - 以下資料集，設有「勘誤備註說明」欄位，提供政府機關相關建議修改的方向，部分資料列提供民間建議之經緯度
    - 「已勘誤之資料序號清冊」下載網址：https://docs.google.com/spreadsheets/d/1l_Au7txDgsknhHKvhLksfSAzeMmSoaih3m4pMdqwrBU/edit#gid=1725071717
    - 您也可以搭配使用線上地圖，可透過篩選器，快速查看已被找出有誤的資料狀況：https://app.awesome-table.com/-NnYWzaRVwV_CasaZLAV/view

二、全民防災e點通
- 形式：地圖網頁
- 網址：https://bear.emic.gov.tw/MY/#/home/map
- 資料錯誤：
    - 本團隊尚未花費大量力氣普查勘誤此地圖網頁，但可以簡單就隨機發現許多避難場所位置有誤
    - 錯誤地點截圖相簿：https://photos.app.goo.gl/BYcLneADj73YArEv7

三、衛服部避難地圖查詢網頁
- 形式：地圖網頁
- 網址：https://rvis.mohw.gov.tw/mgov-rvis/home/map#
- 資料錯誤：
    - 本團隊尚未花費大量力氣普查勘誤此地圖網頁，但可以簡單就隨機發現許多避難場所位置有誤
    - 錯誤地點截圖相簿：https://photos.app.goo.gl/BYcLneADj73YArEv7

四、消防防災e點通 APP
- 形式：App
- 網址：https://www.moi.gov.tw/News_Content.aspx?n=10&sms=9009&s=265624&fbclid=IwAR3uH56mpYYcJnMiwVZOT5mrNCz8yersinbqQVbohIMerFULwEGjaIlRbV4
- 資料錯誤：
    - 本團隊尚未花費大量力氣普查勘誤此 APP 內的地圖，但可以簡單就隨機發現許多避難場所位置有誤
    - 錯誤地點截圖相簿：https://photos.app.goo.gl/BYcLneADj73YArEv7

---


#### 資料欄位內容討論
- 一個避難收容處所，標記不是室內，也不是室外，那這是什麼意思？
- 關於「適合避難弱者安置」的收容處所
    - 如果沒有被標記為「適合避難弱者安置」該如何理解？
        - 是不建議避難弱者前往嗎？
    - 有部分場所有註記，例如「序號 747 高雄市燕巢區瓊林里岡山榮譽國民之家，可收容特殊需照料之弱勢災民，如洗腎患者及其家屬」
        - 這些涉及特定醫療器材的資訊，是否也需要提列成欄位？
- 中英文對照，初步採用：
    - 縣市及鄉鎮市區 County and Area
    - 村里 Village
    - 預計收容村里 Service Area
    - 避難收容處所地址 Address
    - 避難收容處所名稱 Shelter Name
    - 適用災害類別 Disaster Categories
        - 水災-Flooding
        - 地震-Earthquake
        - 土石流-Landslide
        - 坡地災害-HillslopeDisaster
        - 海嘯-Tsunami
        - 核子事故-NuclearEmergency
    - 適合避難弱者安置 Shelter for Vulnerable People
        - 是 Shelter for Vulnerable People
        - 否 No
    - 室內 Indoor
        - 室內 Indoor
        - 否
    - 室外 Outdoor
        - 室外 Outdoor
        - 否
    - 預計收容人數 Capacity
- 設想使用路徑：
    - 使用者在線上地圖查詢，選擇災害種類，篩選出適合的避難收容處所，點開避難收容處所欄位資料，也可以進一步提供該場所的避難地圖圖檔
    - Case: 彰化縣彰化市 https://docs.google.com/presentation/d/1zsKhzBNxHTcPPk9Wh3OE5fn8ooSONA3M/edit?usp=sharing&ouid=105730214933763595410&rtpof=true&sd=true


#### 更多資料 / 資料議題討論

個別單位釋出的資料，優先盤點比消防署全國資料的欄位種類更多的資料集
- 基隆市災民避難收容所一覽表
    - csv 資料集申請網址：https://datahub.ncdr.nat.gov.tw/dataset/detail?pid=c35e182f-4000-43a4-a7ee-5ac1aaaa1ced
    - csv 資料 https://docs.google.com/spreadsheets/d/1LXasjsSac1H8n7Fz7rHfHBPlG-zMxxEw/edit?usp=sharing&ouid=105730214933763595410&rtpof=true&sd=true
    - 有提供以下欄位：
        - 衛福部重災系統災民收容所編號、屋齡、備用鑰匙存放位置、建造執照、使用執照、面積（平方公尺）、預估收容人數
        - Ｘ座標、Ｙ座標
- 臺中市避難看板位置
    - csv 資料集申請網址：https://datahub.ncdr.nat.gov.tw/dataset/detail?pid=73d765ec-da93-4013-bdb9-7540c9cfb8bd
    - csv 資料 https://docs.google.com/spreadsheets/d/1ZG_6yNMF1gWi4bQwVYALMIC8JYPEhgdXFju6MZmAhyg/edit?usp=sharing
    - 資料欄位：
        - 看板行政區、看板位置、看板X、看板Y、看板NE
        - 中區、大誠里大誠街與大誠街49巷交叉路口人行道、120.678902、24.145379、24°08'43.4"N 120°40'44.1"E
    - 討論：
        - 實際上這個用途是什麼？
        - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_65779685c5b6a91025cb9dcd6187f7cb.png)
- 臺東縣關山鎮，PDF 表格檔案，有標記為 短期 或 長期 
    - https://www.guanshan.gov.tw/files/108%E6%94%B6%E5%AE%B9%E6%89%80%E6%B8%85%E5%96%AE(%E8%8B%B1%E6%96%87)%20.pdf

待確認欄位資訊有沒有比較多
- 新北市 NCDR 資料平台上有釋出，shp 可以直接下載，不用申請
    - 資料網址：https://datahub.ncdr.nat.gov.tw/dataset/detail?pid=7e0ec2a5-d17e-49b3-a7b4-4c89c8875de7
    - 待確認欄位資訊種類，是不是有比消防署的全國資料多
- 2024.01 臺中市、臺東縣、澎湖縣 有釋出 KML 地點資料，待確認是「疏散避難場所」還是「防災避難收容處所」
    - 資料網址：https://data.gov.tw/dataset/31979
    - 待確認欄位資訊種類，是不是有比消防署的全國資料多
- NCDR 資料平台上有釋出部分縣市的避難地圖資料
    - 資料平台網址：https://datahub.ncdr.nat.gov.tw/dataset
    - 20240108 chewei 撰寫申請資料名稱包含「避難」一詞的資料集或檔案，等待審核；需於 2024-01-15 之前下載
        - 檔案資料夾：https://drive.google.com/drive/folders/1-KoiXmLJnQR0SWiy3xnbbYFTf0umUIgV?usp=sharing

是否區分「災時當下避難」與「災後短期收容」，需要依照不同種類的「災害情境時序與衝擊型態」
- 例如海嘯，海嘯來臨前，應前往的海嘯緊急疏散避難地點
    - 海嘯緊急疏散避難地點，不一定是災後短期收容地點
    - Evacuation sites / ひなんばしょ(指定緊急避難場所) / 대피 장소 / 災害避難疏散場所
- 例如地震來臨，前往學校空曠的操場或是比較沒有建物傾倒風險的公園中央
    - 接著需要判斷餘震期間，仍可判斷為安全的運動場館室內
    - 情況較穩定後，可選擇前往 收容處所
- 例如土石流災害預警，通常是預先開始撤離
- 花蓮縣堰塞湖離範圍，包含避難據點 https://www.facebook.com/share/p/1GVMswe9xH/
- 例如核子事故，應該是尋找遮蔽空間
    - 集結地點，會再透過巴士車輛載離 https://www.facebook.com/share/p/UkV6xaLM9CEBTR1T/
- Figuregrounder：http://hanshack.com/figuregrounder/
    - 用白底單色色塊的簡化方式，呈現建物及戶外空間
    - 或許可以用於輔助評估 戶外疏散空間的評估，例如：主震及餘震期間的戶外避難場所擇點

#### 資料應用

#### 從資料應用情境與具體災害事件收容開設狀況經驗，探討資料集本身的整備注意事項

資料應用情境
- 若民眾只看單一鄰里內的避難收容處所位置，反而少了區域應變調整的視野
    - 情境舉例
        - 美國針對龍捲風災害，居民避難方向，採用「看龍捲風怎麼走，才決定你要往哪裡避難」
        - 日本福島輻射影響範圍，並不是同心圓，而是基於外洩當天的風向，所以有些區域的避難方向，不一定是遠離外洩地點，因為如果在主要風廊軸線上，再怎麼跑都在輻射影響的範圍內，這也是目前台灣核災避難地圖需要改進的部分，應該歸納日夜與季節的盛行風向表，一旦發生外洩事件，依照當下季節及時段，往對應方向避難
        - 臺灣有少數縣市，會把淹水潛勢區塊，也繪製在避難地圖上，因為實際上面臨降雨積水災害，但前往水災避難據點的路上卻是積水嚴重區域，需要繞道而行、躲開易積水地區，這部分也還可以整合實際歷年淹水位置 (NCDR 網站圖台上有釋出，待確認有沒有釋出 opendata)
    - 上述的演練應用，都需要 收容處所 gis 資料，才能有區域尺度的視野，也才有機會導入情境路徑演算的功能

提供一個查找路徑：
- 使用者瀏覽全台避難收容處所查詢線上地圖
- 選擇災害情境作為篩選條件
- 顯示該災害情境下，適合的避難收容處所
- 顯示該避難收容處所的建議前往路線
    - 少數縣市有畫出來，且針對淹水情境，路線會繞開淹水潛勢高的地區
    - Case: 彰化縣彰化市 https://docs.google.com/presentation/d/1zsKhzBNxHTcPPk9Wh3OE5fn8ooSONA3M/edit?usp=sharing&ouid=105730214933763595410&rtpof=true&sd=true
- 點選避難收容處所，了解欄位資料與避難疏散地圖，或下載避難疏散地圖

南投縣草屯鎮日新國中，製作防災避難引導 Linebot，介紹網頁
https://rsjhs.ntct.edu.tw/p/404-1010-403933.php?Lang=zh-tw

民眾入住該地區的流程中，提供避難地圖與手冊
https://youtu.be/rjXJK0dRys0
延伸發想：
- 房仲業者
- 物業管理公會
    - http://tipm.org.tw/Firm_4.html
    - https://www.smartdaily.com.tw/
- 家長會

大規模震災情境下避難收容處所開設管理與防災士空間分布特徵之評析
- 電子全文：https://hdl.handle.net/11296/3m94b2
- 摘要：以地震衝擊資訊平台(TERIA)設定規模6.8，深度15公里之山腳斷層錯動情境，模擬夜間避難收容人數並透過路徑分析(Network Analyst)劃設避難收容處所實際步行距離800公尺所涵蓋之服務範圍，將新店溪南岸、大漢溪東西岸及淡水河西岸的新北市永和區、中和區、板橋區、土城區、新莊區、樹林區、三重區、蘆洲區、泰山區及五股區共10區作為本次研究範圍。本研究主要研究方法為路徑分析，透過圈域的劃設，得出避難收容處所服務範圍，再與TERIA每一網格500*500公尺作比例交集制表，加入收容人數與防災士人數，為本研究最小之分析單元。研究結果顯示大規模震災情境下，以板橋車站周遭、新莊迴龍捷運站附近與新莊幸福路商圈等三處的收容人數為最多，而全研究範圍內若要使避難收容處所順利開設，防災士數量皆明顯不足。

應變單位與救援單位 csv
https://data.gov.tw/dataset/5969

#### 避難收容處所開設紀錄

是否有開設紀錄歷史資料？收容場域，成為地區生活經驗之一，歸納避難收容設施改善議題
- API?

撤離與收容評估系統現公告以下兩項更動：
- 已上架2023年歷史颱風與豪雨事件之撤離與收容人次統計資訊。
- 土石流保全人口估計：2023年起，土石流保全人口的統計資料已包含大規模崩塌保全人口，以提供各縣市及鄉鎮市區公所更全面的保全人口資訊。
- https://drrstat.ncdr.nat.gov.tw/evaluation/evacuation

具體災害事件收容開設狀況經驗
- 20240402 花蓮地震
    - 花蓮縣避難收容處所開設狀況
        - 花蓮市中華國小126人
            - https://www.tcnews.com.tw/news/item/21970.html
            - https://www.facebook.com/groups/1034515427046437/posts/1873458259818812/
        - 吉安鄉化仁國中20人
        - 吉安鄉月光寺21人
        - 秀林鄉崇德國小2人
        - 秀林鄉和中收容所28人
        - 秀林鄉富世國小16人
    - 討論：
        - 類型一：地震後擔心餘震或既有建物無法返回，所前往的地點
        - 類型二：暫居過夜收容
            - 其中並非收容所既有資料的地點：月光寺、和中收容所

體驗活動 https://www.facebook.com/share/p/Fcka1nw7aNuTXtfS/

旅宿
https://www.facebook.com/share/p/1HmY5TWMpL/


### 【TW 臺灣】Air Raid Shelter / 防空ごう / 민방위대피소 / 防空避難處所

用詞：
- 防空避難處所
- 防空避難設施
- 防空疏散避難設施
- 防空疏散避難設備

線上地圖與資料集
- 內政部警政署民防指揮管制所，用 Google My Map 提供各地區防空避難處所
    - https://adr.npa.gov.tw/
- Kiang 運用政府資料製作出防空疏散避難地圖
    - https://kiang.github.io/air_raid_shelter/
- Ronny 備份
    - https://g0v.hackmd.io/Bo2u7eEcQg6pOuEoOPCADQ#%E9%98%B2%E7%A9%BA%E9%81%BF%E9%9B%A3%E8%99%95%E6%89%80
- 臺中市政府警察局列管防空避難設備統計一覽表
    - https://data.gov.tw/dataset/84017

APP
- 警政服務 App，提供「防空疏散避難專區」查詢，也是用 Google My Map 提供各地區地圖
    - https://www.npa.gov.tw/ch/app/artwebsite/view?module=artwebsite&id=1061&serno=25d5dae3-2a7d-40ea-8016-e567912ac57c

### 【Hong Kong 香港】香港社區應急設施地圖

香港 資料集納入
地圖：https://www.google.com/maps/d/u/0/viewer?usp=sharing&mid=1mRLO36fmZsmUkCX10EqNDVHOAtQeZWo


### 【JP 日本】全国避難所ガイド

#### Raw Data
- Designated Evacuation Sites 指定緊急避難場所の全国データ（公開している市区町村すべて）
    - Kurumi Muto 於 g0v Slack #facing-the-ocean 分享 指定緊急避難場所の全国データ（公開している市区町村すべて）csv 檔案下載網址
        - https://www.gsi.go.jp/bousaichiri/hinanbasho.html
        - "There's a CSV dataset that covers all the so-called "designated evacuation sites" across Japan. You should be able to find it if you page search "【ダウンロード】" there."

#### APP 
- 日本 APP「Safety tips」&「全國避難所」
    - https://www.jnto.go.jp/safety-tips/chc/app.html
    - https://apps.apple.com/tw/app/%E5%85%A8%E5%9B%BD%E9%81%BF%E9%9B%A3%E6%89%80%E3%82%AC%E3%82%A4%E3%83%89/id446063625
    - APP 畫面截圖：https://photos.app.goo.gl/hq2YiD1sC5rCnU7K8
    - 討論：
        - 要裝兩個 APP
        - 全國避難所 APP
            - 可以 GPS 定位
            - 可以預演
                - 例如身在臺灣，想了解東京都世田谷區任意地點前往避難處所的路線，使用者自行將起點設置在日本東京
            - 避難處所地圖上有顯示全部的地點
            - 沒有災害情境條件搭配篩選出對應的處所，點開處所之後，在介紹欄位中顯示適用哪些災害種類

#### Others
- 日本，列印紙本地圖 https://kamimap.com/tw/map/2024-noto-earthquake/
- 日本，透過大貨車、大客車的 GPS 追蹤資料去帶出道路是否中斷的資訊
    - https://www.its-jp.org/news_info/107997/
    - https://disaster-system.its-jp.org/map4/map/
- 日本，呈現加油站的營業狀態
    - https://www.enecho-ss.meti.go.jp/b/enecho/

### 【KR 韓國】6 種避難場所種類，各個查詢網頁

#### Webpage / API
- 지진옥외대피장소 地震室外避難場所 
    - 查詢網頁：https://www.safekorea.go.kr/idsiSFK/neo/sfk/cs/sfc/res/victimList.jsp?acmdfclty_cd=2&emgPage=Y&menuSeq=855
    - API：https://www.data.go.kr/data/15039250/openapi.do#/API%20%EB%AA%A9%EB%A1%9D/getArea3List
    - 20240110 爬蟲成果 11300 筆資料 by hwan：https://docs.google.com/spreadsheets/d/1fEaFwnJ9KRlcFXdStt10hqfnStBCmpxmw6TVhtXLveo/edit#gid=1282817316
- 지진해일 긴급대피장소 海嘯緊急避難場所 
    - 查詢網頁：https://www.safekorea.go.kr/idsiSFK/neo/sfk/cs/sfc/res/victimList.jsp?acmdfclty_cd=2&emgPage=Y&menuSeq=855
    - API：https://www.data.go.kr/data/3058512/openapi.do
    - 20240110 爬蟲成果 660 筆資料 by hwan：https://docs.google.com/spreadsheets/d/1fEaFwnJ9KRlcFXdStt10hqfnStBCmpxmw6TVhtXLveo/edit#gid=0
- 쉼터 庇護所 무더위쉼터 躲避酷暑
    - 查詢網頁：https://www.safekorea.go.kr/idsiSFK/neo/sfk/cs/sfc/htw/htweaiList.html?menuSeq=862
    - API：https://www.data.go.kr/data/15107290/openapi.do
- 쉼터 庇護所 미세먼지쉼터 精細防塵罩
    - 查詢網頁：https://www.safekorea.go.kr/idsiSFK/neo/sfk/cs/sfc/htw/htweaiList.html?menuSeq=862
- 쉼터 庇護所 한파쉼터 寒流避難所
    - 查詢網頁：https://www.safekorea.go.kr/idsiSFK/neo/sfk/cs/sfc/htw/htweaiList.html?menuSeq=862
- 민방위대피소 民防庇護所
    - 查詢網頁：https://www.safekorea.go.kr/idsiSFK/neo/sfk/cs/contents/civil_defense/SDIJKM1402.html?menuSeq=57

#### 資料彙整 demo，試作釜山地區的資料
- csv-demo https://docs.google.com/spreadsheets/d/1gQG2k94RvmNcyXLnKT1xWTgafF0SRJIq2TrF96Y1ZJE/edit
- map-demo https://app.awesome-table.com/-NnnM3t8IzB_LBA8hMWn/view

### Issue 多種語言翻譯課題

日本釋出的「避難指示等に関する多言語辞書（14か国語）」文件
- 下載網址：https://www.soumu.go.jp/menu_seisaku/kokumin/jyohonanminzero/index.html
- 線上瀏覽 (檔案日期 20240118)：https://docs.google.com/spreadsheets/d/16mJKMmLcNQ5z3NtuB3wqD-UbHn8OkHW1/edit?usp=sharing&ouid=115613229829145960960&rtpof=true&sd=true
- 討論
    - 災害種別用語，裡面沒有「地震」一詞

筆記
- 지진 地震
- 지진해일 海嘯
- 室內避難收容處所(優先安置學校) Indoor Evacuation Shelter ( School for Priority Shelter )
- 室外避難收容處所(防災公園) Outdoor Evacuation Shelter ( Disaster Prevention Park )
- 避難收容處所(備用) Evacuation Shelter ( Backup )

## Evacuation Drill / Record

### 20231230 中正紀念堂捷運站 至 NPOHub 沿途防空避難所外觀拍照

拍照：https://photos.app.goo.gl/BYcLneADj73YArEv7
討論：
- 週六下午路過 9 個點，現況統計：
    - 1 個南門市場週六下午有開
    - 3 個店面週六下午有開
    - 2 個店面週六下午沒開
    - 1 個有管理員且管理員知道此處為防空避難處
    - 2 個住宅大樓，不確定一樓大門是否常態打開
    - 地下室入口明顯程度：3 個在門口看得到樓梯，其他的從外觀看不曉得地下室樓梯在哪
- 延伸討論文件：https://g0v.hackmd.io/@paulpengtw/DigiResiTh0n-home/%2FmKkOC9PLSXi0GZg7uGm1xA
    - 需要 ranking
    - 或是有更多情景設想，例如哪些防空避難空間會更適合作為物資交流、傷患協助的場所，哪些會比較適合該棟建築物民眾避難使用
    - 「防空避難處所」數量比「防災避難收容處所」多，是否可以評估有一些離防災避難處所比較遠的社區，挑選適合的防空避難建物的非地下室空間，作為防災避難使用
    - 例如中正區的南門市場，屬於防空避難，其實建築才剛落成，也屬於公有建築物，很適合水災情境的垂直避難處所，或是地震情境時，此建築物理當相對安全，或是考量南門市場臨著羅斯福路非常空曠的道路空間，適合戶外避難，因為餘震期間街區建物無法確保安全

### 信義區防空設施整修開放參觀 

https://www.facebook.com/pb.taipei/posts/pfbid02FiEowF9diMtB3S6crzsTH8QJDS2VV1E8bhnzdxovTQvhcwC6a43mL6N7mnWuFFwhl

### 其他筆記

探討醫院地下化政策
https://www.facebook.com/share/p/15dXiUpahZ/


---

:::warning
文件目錄
[TOC]
:::

---
tags: GIS, tree
---

# 都市樹木與行道樹資料

Todos: 整合各縣市行道樹與老樹資料
整合各縣市行道樹與老樹資料
開一個 Google 資料夾：https://bit.ly/2Smu3DB
放入各縣市樹木資料，來源：https://bit.ly/3l3zwvl
欄位整合討論文件：https://bit.ly/3jmYvJL
各縣市受保護樹木類，5590筆，已整合成單一檔案：https://bit.ly/30uVu2N
行道樹 (臺北84840, 新北13826, 臺中118404)，預計整合成單一檔案：https://bit.ly/3lffjCP
欄位待處理工作
[座標位置] 整合後的 X(TWD97 X座標) Y(TWD97 Y座標) → 轉成經緯度
[座標位置] 地號文字，拆列成適合定位的規格，並使用 地號轉經緯度 api
臺中行道樹資料集內的「樹胸徑」與「樹圍」單位為公分

## 【行道樹】工作註記
臺北市行道樹，樹種名稱欄位，"烏?" ← 確認是否為烏桕
新北市行道樹，沒有樹種名稱欄位
臺中市行道樹
[done] 資料中的 台灣欒樹，DIAMETER (胸徑)=33，PERIMETER (樹圍)=104
DIAMETER (胸徑)，PERIMETER (樹圍)，是指「樹冠冠幅」嗎? 或是仍屬於常見的胸徑與樹圍但數字單位為公分?
市政府回答：有關詢問「臺中市行道樹分佈圖」資料集一事，樹胸徑及樹圍的數值單位為「公分」，另測量方式統一量測樹木離地高1.3公尺處樹圍，1.3 公尺處位置倘遇有分叉、膨大、異物阻擋等狀況時，則調整至其適當量測位置高度。(全文可參考 資料頁面詢問 https://data.gov.tw/dataset/109853)

## 【樹穴】工作註記
臺北市行道樹樹穴，樹穴資料僅臺北市有
樹穴類型代號要再詢問
https://data.taipei/#/dataset/detail?id=7a49d00c-a5ff-4a6b-be9e-aaa6dc1ff7e8
20201004 已於頁面詢問，機關回覆：有關於行道樹資訊網內ShapeType(穴形)，目前有0、1、2、帶狀樹穴、單一樹穴共5種，經查其中1等同單一樹穴，2等同帶狀樹穴，0為各單位建置時誤植。因目前樹穴資料正在清查及建置，且為不同時期人員及承商建置，未來將會作整合，應只有單一樹穴和帶狀樹穴兩種。

## 【受保護樹木】工作註記
臺北市受保護樹木，有些沒有經緯度
新北市受保護樹木，樹種名稱欄位，"烏?" ← 確認是否為烏桕
苗栗縣受保護樹木，無經緯度
臺中市受保護樹木，無經緯度，用地段號
已於資料頁面詢問，能否提供經緯度 
https://data.gov.tw/dataset/83615
雲林縣受保護樹木，資料集頁面沒有提供檔案連結
嘉義市受保護樹木，檔案為 kml 格式，透過網頁轉為 csv
臺南市受保護樹木，無經緯度
高雄市受保護樹木，有經緯度，有地段號，但地段號要再拆分成段號與地號欄位

受保護老樹資料地圖
https://www.google.com/maps/d/viewer?mid=1bXRCRxkLjHqOs5gHOSMzxNRIQ31GYx8

## 【局處與機構釋出的樹木開放資料】工作註記
臺北市河濱生態喬木與棕櫚 https://bit.ly/3l3zwvl
臺南市臺糖研究所園區內老樹 https://bit.ly/33vYVYW
非開放：
台北植物園樹木、臺大校園樹木、成大校園樹木 ..等，註記於本頁面的各縣市段落中
地圖化 使用 carto？
應該有個十來萬筆 csv

---
# 樹木開放資料釋出概況


## 民間調查 / 物種普查類開放圖資

### iNaturalist
https://www.inaturalist.org/
樹木資料撈取方法：待補
此資料應無樹高
Seek 自然生物辨識 App 中文版，AI 偵測昆蟲、鳥類與動植物


### 台灣生物多樣性網絡
https://www.tbn.org.tw/
樹木資料撈取方法：待補
此資料應無樹高

### HERETIC's 樹木地圖

網友 HERETIC：https://bit.ly/3fTlwlA
HERETIC's 日治二萬五千分之一地形圖：獨立樹
部分縣市
HERETIC's 雲林縣樹木
HERETIC's 南投縣樹木
HERETIC's 苗栗縣樹木
HERETIC's 彰化縣樹木
HERETIC's 台中市樹木

### 老樹粉絲團
網友 老樹粉絲團 
全台各縣市：https://bit.ly/37SByJD
公視節目：https://youtu.be/IPPMSe_5SA4
資料課題
若僅有位置而無樹木高度，或許可以擷取該位置的 DSM 取得表面高度，作為樹高推估資料

## 中央部會與地方政府

### 開放資料詢問
請開放全國出入口/斜坡道/停車設施/雨水系統管線/樹穴地理位置資訊
https://data.gov.tw/node/57704

### 教育部校園樹木

教育部校園樹木經緯度資料 全台校園樹木經緯度地圖
https://edutreemap.moe.edu.tw/trees/
https://kiang.github.io/school_tree/

### 農委會：林務局、林試所

林務局「樹木普查方法及受保護樹木認定標準」草案
http://www.forest.gov.tw/ct.asp?xItem=76840&ctNode=1917&mp=1

林試所森林動態樣區
福山(fs)、蓮華池(lhc)、墾丁(kt)等三處森林動態樣區之地形測量與每木調查成果。地形測量成果資料包括各樣區內測量樁點之水平座標與海拔高度。每木調查成果資料包括各樣區內組成樹種之代碼、學名資料，以及不同調查期別之樹木株數、胸高斷面積與族群變化數量。
https://data.coa.gov.tw/Query/ServiceDetail.aspx?id=F55
https://scidm.nchc.org.tw/dataset/best_wish100532

### 臺北市

#### 文化局

據說「臺北市保護樹木」的資料較佳，有樹種、經緯度等
https://data.taipei/#/dataset/detail?id=d9d1140b-c2c3-405f-8dd1-7b87b00f6f53
「受保護樹木資料比較完整，如下 http://data.taipei/opendata/datalist/datasetMeta/preview?id=d9d1140b-c2c3-405f-8dd1-7b87b00f6f53&rid=2615ee1b-08c7-4cc6-9ade-7cf1a81eb93d
API - http://data.taipei/opendata/datalist/apiAccess?scope=resourceAquire&rid=ddb80380-f1b3-4f8e-8016-7ed9cba571d5」

#### 工務局公園路燈管理處

一、臺北市行道樹
https://data.taipei/#/dataset/detail?id=7a49d00c-a5ff-4a6b-be9e-aaa6dc1ff7e8
線上圖台 https://geopkl.gov.taipei/
https://trees.gov.taipei/show/?treeid=JJ0011190055
105年度臺北市行道樹普查勞務採購案  
http://gov.playgroup.com.tw/gov_notice/20151223210842445183#.Vovhcd9danM
北市行道樹資料準備更新，與上一次普查相比，這次會因應開放資料應用情境而調整普查方法或程序、資料欄位、呈現方式等內容嗎？摘錄採購案說明：臺北市近9萬株行道樹，本處自94年普查至今已逾10年，當初普查行道樹和現今狀況已有相當差異，為取得行道樹正確資料，於105年度辦理普查，未來樹木管理導入科技化、智慧化的方式，將本市行道樹進行定位及樹籍資料建置，提升維護管理效率。
分為：1.樹木圖層 2.樹穴圖層

二、「公園綠地廣場」內的樹木經緯度資料
尚無？比較接近的資料集名稱：臺北市行政區市容綠美化；行道樹(株)、公園內喬木數(株)，但屬於統計資料，無經緯度：https://segis.moi.gov.tw/STAT/Web/Platform/Product/Apply/STAT_ProductApply.aspx?SECTION=A4201AF22B3DDC70&THEM=CC42DC98656931569AF833A6B3F5E17103F3871B546C5CEE#

#### 水利處管理的 河濱區域
臺北市河濱生態-喬木
https://data.taipei/#/dataset/detail?id=34800b67-b5a5-4ce9-9892-eb0945b82644
1.範圍：本市堤外29座河濱公園、社子島島頭公園、社子島濕地、社六濕地、樟腳公園、中庸2號公園及已闢建為草皮具休憩功能之堤外灘地、堤坡。 2.對象：樹高高於1.5公尺，DBH>6公分。 3.提供CSV檔案格式，採TWD97及WGS84座標系統呈現
欄位：樹籍編碼、樹種、學名、科別、河濱公園、管理單位、樹高_m、胸高直徑_cm、胸圍、冠幅_m、樹冠投影面、推估樹齡_y、資料時間、備註、河系、經度_TWD97、緯度_TWD97、經度_WGS84、緯度_WGS84
臺北市河濱生態-棕櫚
https://data.taipei/#/dataset/detail?id=6e3a3230-2241-4dec-b25a-2458eb0988f7
臺北市河濱生態-灌木
https://data.taipei/#/dataset/detail?id=831a3fbc-ff4a-4acd-849b-d114644b7fce
樹木銀行、移樹資料
http://pwd.gov.taipei/fp.asp?fpage=cp&xItem=1http://pwd.gov.taipei/fp.asp?fpage=cp&xItem=114919&CtNode=8941&mp=10600114919&CtNode=8941&mp=106001
14919&CtNode=8941&mp=106001產業發展局，臺北市生物多樣性資料庫，有紀錄植物/喬木/樹木
14919&CtNode=8941&mp=106001http://tpbiodiversity.lifescience.ntu.edu.tw/index1.asp

#### 工務局大地工程處山坡地或邊坡植樹資料，?

#### 大安森林公園 
https://www.facebook.com/daan.friends/posts/1066022866809846

#### 台大校區 (台北市) 的樹木標示地圖 
http://map.ntu.edu.tw/ntutree/index.htm

#### 台北植物園
https://content.teldap.tw/main/doc_detail.php?doc_id=1164

#### 各地區調查

蟾蜍山樹木調查 
https://www.facebook.com/events/1699485663708073/permalink/1704091779914128/
各類土地開發與公共工程案件中的資料
現地調查階段的植栽資料
完工後的植栽資料
環評報告
?
OpenStreetMap 用 OverPass Turbo 將需要的資料撈出來

#### 應用企劃發想案例

- 情境式的城市路徑引導／In Visible Cities，摘自文章：從台北市的行道樹點位資料，我們可以看出市區幾條已然成形的林蔭道，包括仁愛路、敦化南北路、中山北路、愛國西路、辛亥路等，區域方面，民生社區與信義區的行道樹綠化密度也相對較高。這些綠色通道，串接著或大或小的公園綠地，可做為台北市區的晴天綠蔭地圖。https://www.urstaipei.net/article/21258
- Walkonomics - Find a Beautiful Route - Walking Navigation App for iPhone and Android：https://youtu.be/gP4TjkZQoQs
- 臺北市政府工務局公園路燈工程管理處 園藝小學堂 行道樹樹種選擇原則：https://pkl.gov.taipei/Content_List.aspx?n=C15B0193AD88F60E

### 新北市
圖臺：行道樹木、珍貴樹木
https://i.tree.ntpc.gov.tw/
行道樹
https://data.gov.tw/dataset/125339

### 桃園市
桃園市受保護樹木資料
https://data.gov.tw/dataset/26129
桃園市政府養護工程處去年初展開全市行道樹普查建檔，粗估行道樹約10萬棵（公園內的樹未列入），並製作「樹的身分證」已掛牌2010棵，每棵行道樹牌面有專屬身分證，透過QRcode掃描後，舉凡樹種特色、樹籍編號等相關資料一目了然，今年預計掛牌3萬棵，明年底前完成所有掛牌。
https://news.ltn.com.tw/news/Taoyuan/breakingnews/2896929

### 新竹縣
新竹縣列管珍貴老樹資料
https://data.gov.tw/dataset/42452

### 新竹市
新竹市受保護樹木
https://data.gov.tw/dataset/67542
Google My Map - 新竹老樹
iNaturalist 專案 - 新竹市行道樹

### 苗栗縣
107年度苗栗縣政府列管珍貴老樹，補網址

網友 HERETIC：https://bit.ly/3fTlwlA
HERETIC's 日治二萬五千分之一地形圖：獨立樹
部分縣市
HERETIC's 苗栗縣樹木

### 臺中市
臺中市行道樹系統與開放資料
圖臺：http://itree.taichung.gov.tw/Tccg_Tree/index.aspx
開放資料：
https://data.gov.tw/dataset/109853
https://www.facebook.com/wuulong.hsu/posts/3403738569642537
https://www.facebook.com/100000192830591/posts/3454063844610009/
臺中市受保護樹木公告清單
https://data.gov.tw/dataset/83615
行政區、樹木編號、樹種、地段、地號
樹木現地提供 QRdode
https://www.facebook.com/tcgovconstruction/posts/1228927273919387
https://www.facebook.com/282921805214623/posts/1146055752234553/
https://www.taichung.gov.tw/996952/post
台中市老樹地圖(原中市,已不更新)
https://www.google.com/maps/d/u/0/viewer?hl=zh-TW&ie=UTF8&oe=UTF8&msa=0&mid=1ZNGScwu87o_xggnWimcpZRPWju4&ll=24.16006227551401%2C120.67421549999995&z=11
台中老樹地圖 app
https://play.google.com/store/apps/details?id=com.huei.oldesttrees
摘自 粉絲頁：「台中老樹地圖」APP獲得老樹研究者 Percy Chen 先生授權，提供多年實地調查研究成果，資料涵蓋超過1,100棵台中市政府公告受保護樹木，完整呈現1千多張珍貴老樹照片。
https://ot.wisyltd.com.tw/

網友 HERETIC：https://bit.ly/3fTlwlA
HERETIC's 日治二萬五千分之一地形圖：獨立樹
HERETIC's 台中市樹木

樹學芳城市 by 台中荒野
地圖：https://drive.google.com/open?id=1HTHPY2haZOGWLVlLbRsCt2Oc1iCzoZPZ&usp=sharing
近期社群活動
https://www.facebook.com/sowtc4speech/posts/2675839592452194
待確認：臺中市千分之一航測地形圖_TWD97DWG，是否能擷取出植栽與樹木資料
https://bit.ly/3eaPMXF

### 彰化縣
網友 HERETIC：https://bit.ly/3fTlwlA
HERETIC's 日治二萬五千分之一地形圖：獨立樹
HERETIC's 彰化縣樹木

### 雲林縣
雲林縣珍貴老樹一覽表 https://data.gov.tw/dataset/28789
2020.10.03 查詢，資料集下架
另外查詢到此 Google My Map https://bit.ly/34p2OOv 不確定資料集內容是否即為縣政府釋出的資料集

網友 HERETIC：https://bit.ly/3fTlwlA
HERETIC's 日治二萬五千分之一地形圖：獨立樹
HERETIC's 雲林縣樹木

### 南投縣

網友 HERETIC：https://bit.ly/3fTlwlA
HERETIC's 日治二萬五千分之一地形圖：獨立樹
部分縣市
HERETIC's 南投縣樹木


### 嘉義縣
嘉義縣珍貴老樹

### 嘉義市
嘉義市珍貴樹木


### 臺南市
臺南市珍貴樹木
開放資料：https://data.tainan.gov.tw/dataset/precious-trees
愛樹一生一世網站：http://oldtree.tainan.gov.tw/
臺南老樹關注社群
http://club.tncomu.tn.edu.tw/~fang/
台灣糖業公司_台糖研究所老樹登錄明細
https://data.gov.tw/dataset/91530
備份至 spreadsheet https://bit.ly/3ndSelQ
成大校園 
https://www.facebook.com/282921805214623/posts/1378470868993039
https://nckutree.ncku.edu.tw/nckuTree/

### 高雄市
高雄市列管特定紀念樹木清冊
https://data.kcg.gov.tw/dataset/commemoration-tree
編號、樹名、所在地、所在地地址、經度Lng、緯度Lat、資料序號Seq

### 澎湖縣
澎湖縣受保護樹木
https://data.gov.tw/dataset/46121

### 花蓮縣
107年珍貴老樹列表 
https://scidm.nchc.org.tw/dataset/best_wish110707

### 臺東縣
似乎是有老樹資料
https://www.facebook.com/mickeytfri/posts/10220568130571397


## 探討樹木資料架構與相關應用
緣起
之前就在想 Whiski 的這個梗：「巴黎就有人把行道樹資料和過敏源資料結合，並推出手機應用程式，造福了廣大有花粉過敏症的市民。」 
http://www.vita.tw/2012/11/open-data.html
這兩天出現 Muyueh 說「正在煩惱要怎麼樣校對行道樹資料...」
https://www.facebook.com/groups/odtwn/permalink/1191664634181286/
然後最近剛好在協助台北市資訊局籌劃活動...
於是...先來想像一下資料欄位？
 
什麼是好的行道樹資料？
正面表列：
以下由最優先到次優先：
要有正確的經緯度
要有樹種、樹名
不曉得是否有國際的名稱或編碼系統，可以援用？
four or six digit code. IE: Acer Macrophyllum == ACMA or ACEMAC
樹齡（種植年份）？
胸徑（直徑）？
樹高
是否為法定受保護樹木
樹穴圖層
樹穴狀況
目前的認養人
請參考此認養措施「公園及行道樹徵求乾爹媽 認養每年省5千餘萬公帑」http://www.gov.taipei/ct.asp?xItem=178994940&ctNode=5158&mp=100001
該筆資料建置的時間
相關資料若是由其他圖面書面資料而來，則必須說明來源，例如ＯＯ工程竣工圖、或是某某年的行道樹調查計畫

負面表列：
不要用DGN？
DGN是特定軟體使用的檔案格式，有點像是xls的感覺。
先提供一下資訊局同仁的回應，後續會再與公園處等單位討論：
「五顆星的問題：來源DGN檔有point和polyline兩層，取用point圖層即可轉換符合GIS應用需求的圖資，polyline圖層是業務單位為了方便看圖使用的圖例，五顆星應該是從梅花狀(代表某樹種)轉成的」
不要用TWD67 （據說已經有了TWD97）
已經有TWD97！　不過有可能原始資料就是用TWD67的座標系統紀錄。 坐標系統定義好，顯示上應該都沒有問題，但是轉換套疊後可能都繪有誤差產生。(會產生偏移)
不要出現梅花五棵...
這應該也是原始資料轉檔的問題，因為原始的圖資，圖面上的樹需要一個符號，就找了一個梅花五棵的符號當樹，所以在圖上看到梅花五棵就知道這是樹。
這個好像真的很難突破耶，因為這個好像是 cad 技術人員的使用習慣，以及施工圖說的圖學...
不要資料錯誤
我覺得處理地理資訊的資料最後可能都會遇到套疊的問題，明明樹就應該長在人行道上，但是因為誤差卻跑到路中間 XDDD  資料來源越多 這種圖面上不合邏輯的情況可能會越多。
應該可以進一步檢視，測繪實務上現場的定位方法

更多探討蒐集
行道樹、受保護樹木之調查及資訊系統建立與應用
https://www.airitilibrary.com/Publication/alDetailedMesh?docid=05781345-201703-201706020006-201706020006-33-56
行道樹資料架構探討
https://www.facebook.com/100000784566673/posts/2185800724789392?sfns=mo
i-Tree 
算出你所不知道的樹效益，淺談 i-Tree 評估工具
https://eyesonplace.net/2017/12/08/7132/
Camden i-Tree Inventory Report 英國地方政府 iTree 報告 
https://www.treeconomics.co.uk/http-2018-treeconomics-co-uk-projects-camden-i-tree-inventory-report-news/
都市林體系研究
https://www.grb.gov.tw/search/planDetail?id=11935453
參考美國農業部 (USDA) i-Tree網站，建構全國都市林知識庫，建立台灣都市樹木、行道樹樹種基礎形態、生理、生態特性及相關環境因子(氣候、氣象、空氣汙染等)的基礎資料庫，用以校正i-Tree URFOE model的參數，使得都市林生態系統服務效益量化的貨幣價值更接近台灣實際的狀況。與地方政府和民間團體合作，參照採用i-Tree Eco之標準調查程序進行國內種子教師之志工培訓，推廣工具和平台之使用，擴大民眾參與都市林生態結構之調查與生態效益評估，建立整合我國都市林完整共享資訊的基礎，以利後續發展與建構我國都市林資訊管理平台。
都市林經營管理技術研究
https://www.grb.gov.tw/search/planDetail?id=12305865
都市林效益數量化評估研究(i-Tree研究團隊) 都市樹木為都市綠色基礎建設的重要投資與資產，必須加以維護管理。要創造適合都市林木生長的環境，必須評估種植環境、篩選適合樹種；對於樹木分布、種植種類、樹木生長狀況、立地微氣候、土壤結構與性質、營養、水分，及其他生物利用等長期監測資料的收集與彙整，可評估都市林木健康與環境之關係，亦可應用於預測都市林木對於都市環境改善與節能減碳之潛在價值，將有助於都市綠色基礎建設整體的維護、發展與管理。本所已成立樹木醫學研究中心，其功能在於整合樹木保護與醫療的研究與技術資源，提供都市樹木健康管理、診斷與醫療等服務，創造適合都市樹木、森林健全發展的環境。本研究即考量都市綠色基礎建設整體維護、發展與管理之需求，而嘗試發展都市樹木生長健康與環境適宜性長期監測之架構與方法，以建立整合的資訊管理系統。
https://canopy.itreetools.org/
https://www.itreetools.org/
https://health.tfri.gov.tw/itreetw/
網站似乎關閉
以臺北市大安森林公園、臺北植物園、高雄都會公園等國內具代表性的都市林為樣區，收集都市林生態系服務效益量化所需的資料，並將調查結果與美國林務署i-Tree研究團隊合作進行分析。從樹種組成、樹冠幅等都市林基礎資料、估算出都市林整體結構，再結合當地的氣候條件、環境汙染等參數，經由科學化公式的計算，推算出都市林的經濟價值。
簡報：都市林i-Tree研究發展 by 林業試驗所森林保護組
臺灣都市林之生態分析-先驅計畫 A pilot study on adapting i-Tree Eco for Taiwan urban forest
http://www.daanforestpark.org.tw/userfiles/files/05_20151111臺灣都市林之生態分析-先驅計畫.pdf       
i-Tree 模型是由美國林務署(USDA Forest Service) 於2006 年開發的都市林與社區林業分析及生態 系統服務效益評估之工具；精確度高的樣地調查數據,得出都市林基本結構 (物種組成、樹木密度、徑級分佈、冠幅等),進 而得出其他結構(葉面積、生物量等)。然後再結 合當地的環境和氣候條件(溫度、濕度、空氣中 污染物濃度等),以及經濟發展水準核算出都市林的經濟價值
QRcode 掛牌
https://www.facebook.com/k.olc.tw/posts/811497375690394
https://www.facebook.com/groups/1077996995607474/
《一棵樹公園》推廣手冊構想
https://g0v.hackpad.tw/Qfqpr3zZYji
都市林綜論
政策研究 The Strategic Framework on Mediterranean Forests and the Tlemcen Declaration
https://www.researchgate.net/publication/264457076_Montpellier_green_city
《The World’s Urban Forests: History, Composition, Design, Function and Management》
http://www.landscape.cn/interactive/book/books/2017/0424/181399.html
Exploring the Green Canopy in cities around the world
http://senseable.mit.edu/treepedia
植典｜植物資料庫
https://g0v.hackpad.tw/yax2EaDoKuH


算樹方法整理
各種方法蒐集

方法蒐集；社團討論串
各個方法的 算樹內容 也有些差異，應該還可以再整理一份 方法 vs 可得到的資料內容 & 必要條件(例如衛星圖資算樹需要圖資品質與演算工具、竣工圖得到樹木資料還缺少批次處理的工具等)
一些架構向度：
涵蓋的地理範圍
監測調查的頻率
也可廣意納入社會意義的家樹，每天都可以照看它
辨識
辨識哪些項目：
物種名稱，例如衛星資料很難辨識物種，iNaturalist 與踏查類方式則可以
高度，例如衛星資料很難辨識高度，iNaturalist 與踏查類方式則可以
年齡，這個或許用歷年衛星有可能推測近代新種植的

列舉
Mapping All of the Trees with Machine Learning
https://medium.com/descarteslabs-team/descartes-labs-urban-trees-tree-canopy-mapping-3b6c85c5c9cc
Treepedia
http://senseable.mit.edu/treepedia
The Green View Index (GVI) was calculated using Google Street View (GSV) panoramas. This method considers the obstruction of tree canopies and classifies the images accordingly. By using GSV rather than satellite imagery, we represent human perception of the environment from the street level. The GVI presented here is on a scale of 0-100, showing the percentage of canopy coverage of a particular location. Explore the maps above to see how the GVI changes across a city, and how it compares across cities and continents.
Github & 臺灣虎尾街景測試
https://www.facebook.com/groups/573697330058183/permalink/710552026372712/
CCTV
https://bit.ly/3imgiA8
公共工程完工後的資訊，從中取得樹木與植栽資料
PCCES
https://pcces.pcc.gov.tw/CSInew/Default.aspx?FunID=Fun_12
竣工圖

BIM
【參考資料】台北市都發局 GIS, BIM 業務近況說明
https://www.facebook.com/media/set/?set=oa.1964156740538989&type=3
https://www.facebook.com/jjdigital/posts/1670257433008787




公民科學取向的專案
iNaturalist
https://fangyeelin.wixsite.com/fishfish/about
There are many other resources available to help you determine whether citizen science and open data projects are right for your community. We’ve listed a few below. We would also love to hear your stories about using citizen science.
https://blog.opentreemap.org/2017/06/22/launching-successful-open-data-citizen-science-initiative/
The Trees observation tool in the NASA GLOBE Observer (NASA GO) app
The Trees observation tool in the NASA GLOBE Observer (NASA GO) app allows citizen scientist observers to use their mobile devices to take tree height and tree circumference measurements all over the globe.
https://observer.globe.gov/


「用地資料」來作為推論指認依據
例如：國有林、全台保安林分布概略圖 kml、台糖土地資料 ...等，相關連結請參考以下 hackmd：
https://g0v.hackmd.io/i-35j792RgONpEhlREj7Zg


# 國際城市：資料、企劃
TODO:此演講介紹國際推動三維模型案例，其中有提到有建立樹木立體模型的國家或城市
https://youtu.be/TWs9HFLrtqw

## 北美

### 美國
The Forest Inventory and Analysis (FIA) Program of the U.S. Forest Service provides the information needed to assess America's forests.
https://www.fia.fs.fed.us/
Trees of the USA
https://www.facebook.com/groups/d4sg.taiwan/permalink/1801376166805634/
美國林務單位推動的 MY CITY'S TREES - Bringing the Nation’s Forest Census to Urban Areas 目前已有三個城市完成普查，可以參考其線上圖台
https://mct.tfs.tamu.edu/

### NYC
NYC Parks' TreesCount & Data Jam 
https://www.facebook.com/noneck/posts/10154368036303643
Check out the new Street Tree Map! The results of the 2015 TreesCount census, an enormous city-wide volunteer effort including many Trees New York volunteers. We think you'll be pleased with the results. Click here: https://tree-map.nycgovparks.org
NYC Street Tree Map
https://www.facebook.com/nycparks/posts/10155413343603082
https://www.facebook.com/share/p/Tmz2xaq2ciY45jx5/?mibextid=WC7FNe
民間專案與企劃
NYC Street Trees by Species
http://www.jillhubley.com/project/nyctrees/
If you have to meet someone in NYC - just enter both your addresses, and this map will suggest parks that are convenient to both of you. 
https://youmeandatree.com

### 波特蘭
https://www.facebook.com/RiChiTech/posts/1606462009401111

### Seattle
Urban Forest Management
https://www.seattle.gov/trees/management.htm

### 待整理
Colorado Statewide Tree Inventory Tool, CO-TreeView
https://cotreeview.com/cotv/
New Kensington counting trees
Tree Data Collection Helps New Kensington, Pa., Begin Smart City Transformation
As the city undergoes its transformation, this exercise will provide the crucial initial base data of the current city-owned tree stock.
http://www.govtech.com/dc/articles/Tree-Data-Collection-Helps-New-Kensington-Pa-Begin-Smart-City-Transformation.html

### Vancouver 
http://data.vancouver.ca/datacatalogue/streetTrees.htm
https://mountainmath.ca/mountain_math/about

## 歐洲

### London / UK
London Street Tree Map
https://maps.london.gov.uk/trees/
https://www.london.gov.uk/what-we-do/environment/parks-green-spaces-and-biodiversity/trees-and-woodlands/london-tree-map
倫敦綠覆圖資 Tree canopy cover map 
https://www.london.gov.uk/what-we-do/environment/parks-green-spaces-and-biodiversity/trees-and-woodlands/tree-canopy-cover-map
https://www.curio.xyz/canopy
http://www.breadboardlabs.io/
CommuniTree
https://www.communitree.co.uk/
Communitree – 研究使用，一個預計將英國的樹木標註上地圖的計畫。

### 巴黎
http://opendata.paris.fr/explore/dataset/arbresalignementparis2010/?tab=table 
（好像還有別的？）
arbre(tree) data https://bit.ly/3uEoWAh
法文版欄位說明  
https://www.dropbox.com/s/gomtk8ltyyxyvr2/VilleParis_DEVE_ARBRES_ALIGNEMENT_description_compl%C3%A9mentaire_201407.doc?dl=0

### 比利時布魯塞爾
https://www.woodwideweb.be/en/atlas.html

## 亞洲

### 日本
植生調査（1/25,000縮尺）
自然環境調査 Web-GIS
日本 Tennoji Zoo 天王寺動物園的展覽說明，只需要手機輕輕靠近觸碰開啟NFC功能，就能馬上連結到相關資訊
https://www.facebook.com/tapbee.NFC/posts/1900385360088436

### 香港 HK 
樹木登記冊
為促進社區參與樹木風險管理以更有效保障公眾安全，樹木登記冊自2010年7月開始已為市民提供下列類別樹木資料：
重要而且需要定期檢測的樹木，包括所有古樹名木及石牆樹；
經過每年樹木風險評估後仍待完成風險緩減措施的問題樹木； 及
接獲投訴或轉介個案中，需要持續監察的樹木。
https://www.greening.gov.hk/tc/community_outreach/tree_register.html
將香港樹木登記冊資料放在 Google My Map
https://goo.gl/Gyx2gZ
https://www.facebook.com/groups/code4hk/permalink/1577645612303299/
古樹資料
https://www.collaction.hk/s/timber
https://www.facebook.com/groups/code4hk/permalink/1586214054779788/
颱風倒木
https://www.facebook.com/156329461054487/posts/2002458283108253/
Pokemon
https://www.facebook.com/marketplace/shops/item/1178095858936890/
非牟利團體 TrailWatch 開發「監察神器」，行山客只要下載「TrailWatch 徑．香港」手機應用程式，便可隨時舉報斬樹黨蹤迹。
https://www.facebook.com/trailwatch/posts/1376132082426369
香港街道選樹指南
香港特別行政區發展局轄下的綠化、園境及樹木管理組 (管理組) 委託顧問進行研究
https://www.greening.gov.hk/tc/knowledge_database/street_tree_selection_guide.html

### Singapore 
TreesSG
https://www.nparks.gov.sg/trees
https://www.facebook.com/qingwang/posts/10156197106643879
摘：新加坡登記了全國的每一棵樹，總計有五十六萬多棵樹。還可以在網站上下載到每棵樹的相關資訊，包括年齡、生長速度、坐標、... 等等。以 JSON 格式表示，易於於應用中整合。
https://www.facebook.com/889701534373509/posts/3251178754892430/
摘：新加坡國家公園署2018年開發樹地圖（Tree Map）網站，記錄全國50多萬棵樹籍資料，讓民眾標記喜歡的樹、上傳更新這棵樹的照片，隨時追蹤。

## 大洋洲

### 澳洲墨爾本 
urban forest strategy：2012-2032
http://www.melbourne.vic.gov.au/community/parks-open-spaces/urban-forest/Pages/urban-forest.aspx
澳洲墨爾本都市行道樹地圖（與市民互動、溝通）：
http://melbourneurbanforestvisual.com.au/
Citizen Forester Program 民眾參與都市樹木調查
Seeking volunteers to help us collect data about trees, plants and ecology to build a greener Melbourne.
https://participate.melbourne.vic.gov.au/citizenforester
墨爾本的「投信樹」服務
http://www.outside.hk/%E7%B5%A6%E5%A2%A8%E7%88%BE%E6%9C%AC%E7%9A%84%E6%A8%B9%E6%9C%A8%E5%AF%84%E4%BF%A1/
當局收到數以千計的郵件，而大部分並非關於樹木狀況，而是市民直接給自己心愛的木樹寫信，分享軼事，內容小至記述日常生活，大至抒發各種困惑，同時不忘讚美樹木的美貌、魅力。

## 小區域尺度的資料
Open Tree Map 多個城市
https://www.opentreemap.org/
https://github.com/opentreemap/otm-core/wiki





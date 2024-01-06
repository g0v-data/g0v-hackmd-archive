---
title: "環境影響評估公民版-從環評看土地變更"
tags: 環境,hackpad
---

# 環境影響評估公民版-從環評看土地變更

> [點此觀看原始內容](https://g0v.hackpad.tw/P8EaNXkcT11)


原始討論: [https://www.facebook.com/groups/g0v.general/permalink/479358228807255/](https://www.facebook.com/groups/g0v.general/permalink/479358228807255/)


### 主旨

有沒有可能透過地圖顯示 "公開" 環評的資料, 讓民眾知道土地如何被變更?
> **小璋丸:**單純希望環評資料親民一點而已
> [name=Donald Z]

> 嗯我單純只是希望資料親民一點，大概是這樣子親民
> [name=Raymond W]

> 方便記者快來抄
> [name=Raymond W]

> 方便在野黨找題材
> [name=Raymond W]

> 方便民眾好懂，好分享
> [name=Raymond W]

> 我認為去年的雪谷纜車案便是個超白痴，在野黨可發揮且其實不難懂的蠢案
> [name=Xavier S]

> 但它搞了半天連環評說明書都生不出來，新市府似乎也不想淌這灘渾水，所以我猜不會進環評。
> [name=Xavier S]

### 牽涉領域

環保 /  都市計畫 / 土地利用


### 相關組織單位

環保署


### 使用資料

1.  [環評開發論壇](http://atftp.epa.gov.tw/EIAforum/Default.aspx?page=eSearchList&FM_SNO=0&PageNo=1&searchType=&searchKey=&AdminUnitCode=&YearList=)
> 可參考 [http://blog.clkao.org/post/54760979509](http://blog.clkao.org/post/54760979509) 要求提供公開資料
> [name=Chia-liang K]

> 「場所」有包含總面積及地號（但不見得會列出全部... 會有 「xxx **等131筆」 類的簡化)**
> [name=Chia-liang K]

> 開發案明細幾乎都在下載檔案中，可能要提供人幫忙在地圖上圈出範圍
> [name=Chia-liang K]

2.  [OpenData.epa](http://opendata.epa.gov.tw/Data/Contents/EIADOC)
> 可以用OCR 的方式來切割 pdf 檔裡的文字嗎? 不過圖形可能要另外想辦法看怎麼match 到google map 
> [name=Tom S]

3.  [環評書件查詢系統](http://eiareport.epa.gov.tw/EIAWEB/Main.aspx?func=00)

### 專案目前狀態

開發中

背景:

目前的土地利用/變更 大致上由以下方式處理
1\. 若土地面積大, 一定要送環評, 環保署(中央)一定有記錄. 環評請私人單位評, 之後由學者批改, 原則上都有資料, 理應查得到

2\. 若土地面積不大(例:假設1公頃要環評, 0.95不用) 可以直接送縣政府(地方), 不必送環保署環評, 未必有"公開"紀錄,但民代要查一定要釋出. 因此常常有人送0.95先, 等到通過後, 在擴大. 譬如花蓮七星壇,先來一個0.95,旁邊再一個0.95,等到搞大了, 大家才發現, 此時若有人反抗, 由縣政府來橋. 這個巧門可以避開央環評, 當然地方會不會被買通, 大家可以想想看...
> 這個例子可能要查查環評施行細則，但我不記得有防範此類的規定，需要的話我可以問問負責訂定此細則的科長。
> [name=Xavier S]

(環評由哪個層級審查, 不是依土地面積決定, 而是依目的事業主管機關的層級, 以美麗灣為例, 原本是以一般旅館的名義申請籌建, 一般旅館的主管機關是縣市政府, 所以環評在台東縣環保局審, 如果它以觀光旅館的名義申請, 主管機關就是交通部, 屬中央部會, 環評就應該在同屬中央的環保署審)

3\. 最近的案子, 如美麗灣, 其實都是很多年以前提的. 因此有些原始資料未必能查得到. 現在有只能盯緊一點, 讓資料公開, 讓附近關心的人早點知道, 免得抹些人替你開會, 幫你做決定 (例 : 花蓮靜浦山海劇場)

(土地的變更其實不是由環評程序決定的, 只是說如果涉及變更, 會在環評報告書中程現出來; 一般開發的程序是興辦事業計畫書-->送目的事業主管機關(例如蓋大學送教育部, 蓋醫院送衛福部....); 用地變更(如果有)-->送縣市政府轉內政部; 水保計畫書(如果有)-->送縣市政府轉農委會; 環評(如果有)送縣市環政府或環保署, 後3者若有1項沒過, 第1個也不會過)

構想:

是否可以利用不得不公開的資料 ([http://atftp.epa.gov.tw/EIAforum/Default.aspx?page=eSearchList&FM_SNO=0&PageNo=1&searchType=&searchKey=&AdminUnitCode=&YearList=](http://atftp.epa.gov.tw/EIAforum/Default.aspx?page=eSearchList&FM_SNO=0&PageNo=1&searchType=&searchKey=&AdminUnitCode=&YearList=)) 來爬出來到底有多少土地即將被變更利用 , 包含申請單位, 並顯示於 Google Map 上,
> 我的看法是上述連結並不夠。光是地圖便只有一張。先不說這個，正式環說書動輒數千頁的地圖都未必會提供採用哪種座標系統了。這方面應該是最麻煩，且政府不改進就只能我用人工作。不過關於座標也許並不太需要精確，因為我們要的是確實面積（環說書中必須列出）。有了面積後只要標定大概位置，應該可以被大家接受？
> [name=Xavier S]

範例:
[http://atftp.epa.gov.tw/EIAforum/Default.aspx?page=eSearch&FM_SNO=154](http://atftp.epa.gov.tw/EIAforum/Default.aspx?page=eSearch&FM_SNO=154)
華隆大理石工業股份有限公司所領臺濟採字第5227號大理石礦採礦權花蓮縣秀林鄉意大利礦場申請核定暨變更核定礦業用地環境影響說明書


## 目標與功能（要如何解決）

### 預定使用者

- 民眾
- 記者
- g0v 後勤人員

### 預定功能

- 知道台灣土地如何被利用。
- 讓民眾以地區性劃分，瞭解有那些**已審過環評書**，將會對環境有什麼改變，結合新聞時事報導及摘要資訊，讓整件事來龍去脈能一目了然。
> 覺得這部分會牽扯到質化或量化的兩難但很重要。
> [name=Xavier S]

- 記者能快速抄到報導素材
- 民眾可訂閱環評書件，若有任何審核狀態異動時，會傳送最新訊息。

### 使用方式



## 實做細節（非技術背景可跳填）


### 使用技術與工具

- 使用的 vagrant box 版本 / 網址：
- hackfoldr 工作資料夾網址：

### 產出檔案格式


### 進度與 to-do

> 僅供參考
> [name=ET B]

- [ ] product planning（recommanded procedure from justin lee / 李易修）
    - [ ] strategy
    - [ ] scope
    - [ ] structure
    - [ ] wireframe
    - [ ] visual
- [ ] web front-end
- [x] web back-end (進行中)
- [ ] ui / visual design
- [ ] 資料收集
    - [x] 環評書
### 現有成果

- [https://github.com/g0v/eia-citizen](https://github.com/g0v/eia-citizen)

## 開發者

- [Raymond Wu](https://g0v.hackpad.tw/ep/profile/CILk9GnRcX0): 程式設計，測試資料蒐集整理
- Donald Zhan：程式設計及資料蒐集
### 技術指導


### 分工與成員

- [x] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
- [x] NeedsDesigner: 需要介面設計
- [x] NeedsData: 需要資料（擷取、清理）
- [ ] NeedsProcess: 需要幫忙設計作業流程
- [ ] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡
> 設定成 project registry 中的 tags，需要幫忙的會自動 promote 到 g0v project hub
> [name=ET B]

> 建議可加入環評說明書網頁下的開會次數，比如[http://eiareport.epa.gov.tw/EIAWEB/Main3.aspx?func=10&hcode=1021461A](http://eiareport.epa.gov.tw/EIAWEB/Main3.aspx?func=10&hcode=1021461A)
> [name=Xavier S]

> 這就是個很有爭議的開發案；個人覺得加入這資料應可讓大家知道哪些土地變更是更荒謬的
> [name=Xavier S]

> ps我想認養「文案幫手」，該怎麼做？（看守台灣協會研究員，經常參與說明書公聽會與環評大會）
> [name=Xavier S]

> [Xavier Sun](https://g0v.hackpad.tw/ep/profile/A1PrqpHWhZY) 如何從環評查詢系統看出爭議性? e.g 多次審查紀錄嗎？
> [name=Donald Z]

> Donald Z 審查太多次就可能有疑點（許多審查都是）；另外，由於與其他協會在這方面有緊密合作，許多開發案的環境影響評估說明書我們都會仔細看（數千頁），同時以環保團體的專業來判斷是否屬於過度開發情形（位於敏感區、水源區、保安林，以及汙染對當地居民的加成效應）並參加環評大會，我舉的中科大肚山擴建案開了五次會仍無結論，其實就是我們與其他團體覺得太誇張而在會議中一直要求修正的。這也是我覺得可以認養第一點的原因。（僅供參考：[https://www.facebook.com/145624728784882/photos/a.153887857958569.30153.145624728784882/1038661836147829/?type=1&theater](https://www.facebook.com/145624728784882/photos/a.153887857958569.30153.145624728784882/1038661836147829/?type=1&theater)）
> [name=Xavier S]

> 只是爭議點很難用量化方式，但可分為不同類型歸類，比如「位居敏感區」「環說書內容不足or作假」與「超過污染總量管制」....等等，這個可以好好想。
> [name=Xavier S]

## 收集問題

- 如何取得各縣市已開發及未開發地區公頃數？
> 所謂已開發與未開發必須有前提。請參考全國區域計畫，這是非常複雜的議題，至於詳細單位資料我不太確定可否弄得到。
> [name=Xavier S]

## 參考資源

### 網站連結

- [環境教育管理資訊系統](http://eeis.epa.gov.tw/)
- [魚凱專欄：電腦馬ㄟ做環評：生態資料數位化的訊息](http://greennews.tw/index.php/201503/4294)
- [https://www.facebook.com/events/1943931935833693/](https://www.facebook.com/events/1943931935833693/)
### PDF文件

- [保護環境的公民進行式─環境政策via公民參與-下載](http://eeis.epa.gov.tw/lib/pop_up/get_proof_fs.ashx?key=3C5793844D18D443)
- [環境影響評估問題集](http://www.taiwanwatch.org.tw/magazine/pdf/v8n2-1.pdf)



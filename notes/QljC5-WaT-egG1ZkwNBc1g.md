---
title: "Data-Centric Government 的二十大類資料"
tags: hackpad
---

# Data-Centric Government 的二十大類資料

> [點此觀看原始內容](https://g0v.hackpad.tw/NoJ1mbwsqkQ)


狀態: DRAFT
授權: CC BY clkao & g0v contributors (並授權與 TCA 以 CC BY-ND 發佈)
**編輯前請同意及簽名**：clkao, yhsiang,  Lucas, chewei, pm5 . a0kman, Summit, Richard Hsieh, kiang

(這是 local.data 專案的後續報告，見[利益揭露](https://g0v.hackpad.tw/eDY68cTC3Hv#:h=前情提要))

### 這是什麼？


Open Government 與 Smart City/Nation 的交集與基礎其實還是 Data，如果我們先忘掉現有政府架構，重新想像與打造一個 Data-Centric 的政府，然後讓這些 Data 都是 Open 的，每個環節都有 api 可以 read/write 或送 pull requests，那會是什麼樣貌？

先分為六個 Tier，Tier 0~2 較偏政府本身及其運作基礎，Tier 3~5 為偏民生相關。底層越完整，則上層資料的品質越容易提升與相互連結，因為有共通的語意定義。

希望每一大類找出**三類關鍵資料**，每類資料有**三種細度**，供檢視「是否有資料」及「是否為開放」等。每類資料可有簡單的 use case 供想像。

之後也可作為比 open data index 與 open data barometer 更細緻的普查項目。

[TOC]


### 討論

> 可直接在此討論，或上 irc: [http://hack.g0v.tw/irc](http://hack.g0v.tw/irc)  或用 [http://join.g0v.today](http://join.g0v.today)
> [name=Chia-liang K]

> 想問個問題，二十大類是隨便抓的嗎？還是怎麼算的
> [name=Yuan C]

> 就列一列差不多二十個，若變成質數可能更好 :P
> [name=Chia-liang K]


#### What's not covered?


> defense?
> [name=Chia-liang K]

> 國防軍事資料需要納入嗎？（這會有什麼內容？）
> [name=che l]

> 外交事務的資料？國際輿情資料？
> [name=che l]

> yeah, 國防外交好像可以一類
> [name=Chia-liang K]


> 各領域的研究單位數據與成果應該要算哪一類???
> [name=曼 奧]

> 教育與研究
> [name=Chia-liang K]

> Tier 4: services 下的
> [name=Yuan C]


> 政府不加密公文算哪一種類???
> [name=Lucas L]

> 應該可以算是公開資料要求 (FOI Request)
> [name=Chia-liang K]


> 政府還有詳細的人口資料，要放在哪塊比較適合呢?
> [name=Yang B]

> Tier 2: Operations  區域劃分及各項統計 / Zoning and Statistics ?
> [name=Chia-liang K]


> 體育相關呢？也列入教育那塊嗎？or infra？
> [name=Summit S]

> 體育政策很需要大改造，不管是建設面或是養成面。
> [name=Summit S]

> 有範例資料嗎？一時想像不到
> [name=Chia-liang K]

> 初步的話會想從教育面（體保制度相關、甲乙組比賽成績），運動場地（）
> [name=Summit S]

> 這兩塊開始吧（也還在摸索中XD，來問問一些體制內的意見）
> [name=Summit S]


> 一些環境相關的：生態、（人為活動的）環境影響、永續發展、區域計劃，放在 Tier 2~3 如何？晚點來寫
> [name=Pomin W]

> 區域在 2.1 有 環境先放在 3.3
> [name=Chia-liang K]

> 國土規劃算是一個大類嗎?
> [name=Richard H]

> 目前似乎是將計畫規劃的法源放在 tier0、區劃與地貌環境資料則屬於 tier2 & tier3、公文會議資料則是 tier1
> [name=che l]


> 政府資產資料，例如「臺北市大同分局目前有多少部車輛..」，屬於「政府架構與人事 / Organization and People」？或「預決算與財政收支 / Budget, Revenue and Spending」？
> [name=che l]

> +1 應該和財政放在一起，單位列管財產之類的，還是有特定名字？
> [name=Chia-liang K]

> （我猜是）國有財產（[國有財產法](http://www.fnp.gov.tw/Edict.php?page=LawInfo&TRE_ID=6&act=ArtAll)裡面有條文說明細項名詞定義）
> [name=che l]


> 醫療類的包含藥商登記、醫療院所登記、藥物許可證資料這些會需要嗎？如果有需要我可以去更詳細的查一下有哪一些現有資訊
> [name=Nina T]


> 考選部「專門職業及技術人員」面向的資料，包含[人員清冊、考試題庫...等](http://wwwc.moex.gov.tw/main/content/wfrmContent.aspx?menu_id=32)，會歸類在哪一個項目下呢？
> [name=che l]

> 例如：醫師、建築師、社會工作師...
> [name=che l]

> 「Tier 2: Operations 政府運作」？
> [name=che l]


> 各級政府開放資料諮詢小組委員清冊、法定委員會委員清冊，會歸類在哪一個項目下呢？
> [name=che l]

> 「Tier 0: Rule of Law and Organization 法制與政府組織 \> 2.政府架構與人事 / Organization and People」？
> [name=che l]

> 或是「Tier 2: Operations 政府運作」？
> [name=che l]


> 依循「Data-Centric 的政府」這樣的理念，除了明確由本國政府所負責的資料之外，會如何處理或看待「非本國政府產製與維護的資料」，案例試舉：國際法、航運資料、關貿資料、境外空汙資料、[WHO](http://www.who.int/en/)所蒐集的各國資料疫病資料、[OIE](http://www.oie.int/) 所匯整的動物疫情資料、其他國家檔案局所藏有的本國檔案（民間專案例如：[遺落在世界的國家寶藏](http://beta.hackfoldr.org/national-treasures/--6WPE9CHCHii)）...等。方案上，或許可以延續目前項目架構，每一個項目中依照項目實質的資料治理狀況，納入國際資料。
> [name=che l]


> 2016-11-25 Tier0 法制與政府組織，討論[影片](https://www.youtube.com/watch?v=IO0t25xLV_c)（[逐字稿](https://sayit.archive.tw/2016-11-25-%E8%88%87%E9%AB%98%E5%98%89%E8%89%AF%E8%A8%8E%E8%AB%96%E9%96%8B%E6%94%BE%E8%B3%87%E6%96%99)）：
> [name=che l]



#### 這份架構可以做什麼？


資料檢視
> 用於檢視項目下的資料集現況，例如檢視項目：「資料是否已有彙整機制」
> [name=che l]

> 例如館藏資料，現況來看屬於各機構自定資料的管理方式 → 無
> [name=che l]

> 例如防救災資料，雖未開放但至少行政院內部已經進行整合 → 有
> [name=che l]

> yeah, 這個在每項調查可以註記
> [name=Chia-liang K]


> 寫著寫著，就會想到「除了既有的資料種類，會不會還有什麼樣內容的資料，更需要被定義起來，讓公眾事務運作的更好？」
> [name=che l]

> 「對於某個資料項目的期待，暗示著需要當前的部會局處手上的資料有所整合、再定義？例如[濕地資料](https://g0v.hackpad.tw/gTp0Gl6834m)」
> [name=che l]


> 《開放政府觀察報告 2014-2016》內文運用〈Data-Centric Government 的 20 大類資料〉架構，依此架構盤點「資料集現況」。盤點成果：[https://github.com/ocftw/OpenGovReport14-16/tree/master/data](https://github.com/ocftw/OpenGovReport14-16/tree/master/data)
> [name=che l]


> 建構「知識本體、語彙、格式」的重要性
> [name=che l]

> 「知識語彙感覺很重要，應該用國外語彙，還是政府由上而下去推動？」
> [name=che l]

> [https://hackmd.io/s/BJO8RQ5c-](https://hackmd.io/s/BJO8RQ5c-#知識語彙感覺很重要)[#知識語彙感覺很重要](https://g0v.hackpad.tw/ep/search/?q=%23%E7%9F%A5%E8%AD%98%E8%AA%9E%E5%BD%99%E6%84%9F%E8%A6%BA%E5%BE%88%E9%87%8D%E8%A6%81&via=NoJ1mbwsqkQ)[，應該用國外語彙，還是政府由上而下去推動？](https://hackmd.io/s/BJO8RQ5c-#知識語彙感覺很重要，應該用國外語彙，還是政府由上而下去推動？)
> [name=che l]

> 「不同領域如農業、交通、環境、水利 從茫茫開放資料海中要如何建立一套ontology? 現有標準要去哪找呢?」
> [name=che l]

> [https://hackmd.io/s/BJO8RQ5c-](https://hackmd.io/s/BJO8RQ5c-#不同領域如農業)[#不同領域如農業](https://g0v.hackpad.tw/ep/search/?q=%23%E4%B8%8D%E5%90%8C%E9%A0%98%E5%9F%9F%E5%A6%82%E8%BE%B2%E6%A5%AD&via=NoJ1mbwsqkQ)[、交通、環境、水利-從茫茫開放資料海中要如何建立一套ontology-現有標準要去哪找呢](https://hackmd.io/s/BJO8RQ5c-#不同領域如農業、交通、環境、水利-從茫茫開放資料海中要如何建立一套ontology-現有標準要去哪找呢)
> [name=che l]

> [http://schema.org/docs/full.html](http://schema.org/docs/full.html)
> [name=che l]


治理基礎
> 以此架構為基礎，往上似乎則是各式各樣的議題業務（例如：[建立「社區資訊」共同規範](https://g0v.hackpad.tw/ork4P0hC7jF) 、[流域治理](http://cmp.wra.gov.tw/)、[知識經濟](https://scitechvista.nat.gov.tw/c/2v7T.htm)）；依此來看「資料如何驅動公眾事務？」，Data-Centric Government 的理念與架構，與 Knowledge Management、[Decision Making](https://g0v.hackpad.tw/O4HH5rrPSuB)、[Deliberative Democracy](https://goo.gl/y7yZyU) 之間的理想關聯會是什麼？
> [name=che l]



## 政府與治理


### Tier 0: Rule of Law and Organization 法制與政府組織


1.  **立法及法律 / Legislature**
    1.  現行法規（含行政規則、行政命令）：全文、結構化全文、引用條文連結註記
    2.  修訂紀錄：版本明細、修訂相關文書或會議影音、
    3.  修法提案及進度：提案內容與目前狀態、歷史狀態、相關會議影音
2.  **政府架構與人事 / Organization and People**
    1.  機關架構：機關基礎資訊與階層關係、服務內容及對象、法律依據與編制員額
    2.  行政區劃分（含原住民自治區）：基礎編號與圖資、連續邊界圖資、歷史圖資
    3.  人事：機關別年資及年齡、約聘僱（派遣人員、替代役男）比率、公務人員人事異動資料
3.  **司法及判決 / Judicial and Verdicts**
    1.  檢察機關：偵查統計、起訴統計、起訴書
    2.  法院：判決書、判刑與執行統計、結構化判決書
    3.  行政機關法律適用：行政函釋、行政罰相關統計數據、訴願相關統計數據

### Tier 1: Accountability 課責


1.  **選舉及罷免 / Election and Recall**
    1.  選舉概況：選區劃分、選舉人統計、投票概況
    2.  候選人：候選人基本資料及政見、公辦政見會時程與內容、
    3.  得票：當選得票明細、
2.  **預決算與財政收支 / Budget, Revenue and Spending**
    1.  預算案、法定預算、決算：依機關別項科目最細項別、依類別列、依專案計畫列
    2.  實際支出明細
    3.  單位財產統計
    4.  收入統計：各類罰金及規費統計（依地區、項目、金額）、各類稅收二十等分級距統計、各類稅收 1 % 及 0.1% 級距統計
> 以上是否有包含「國家公債資料」？
> [name=che l]

3.  **政風與課責 / Ethics and Accountability**
    1.  政治獻金 /  Political Contributions: 單戶依類別統計、違法公告、單戶收支明細、與候選人連結資料
    2.  財產申報 / Asset Disclosures: 應申報人明細、申報統計、申報明細
    3.  公務資料調閱紀錄與政府資訊公開要求 / FOI Requests: 機關收受公開資訊要求：統計、明細
> 請問有範例嗎？這是哪種東西？
> [name=Chia-liang K]

> 希望是一種制度，民意代表或者是政府本身，可以明確知道有誰調閱過資料
> [name=Lucas L]

> 政府 KPI 是否能算成一種資料項目呢？或是涵蓋在 Accountability；此類資料的探討頁面 [OpenKPIPublicParticipationKPI](https://g0v.hackpad.tw/Roavwqy9ipj)
> [name=che l]


### Tier 2: Operations 政府運作


1.  **區域劃分與統計 / Zoning and Statistics**
    1.  基礎統計：各單位應統計及發布事項、人口統計（結構、遷移、不在籍與外籍人口）、工商統計
    2.  警、消、國教責任區域範圍：單位基本資訊與範圍劃分、人力員額及人口統計、人力員額及人口歷史變化
    3.  土地劃分與所有人：區域/都市/都市更新計畫、土地使用分區明細及變更紀錄、所有人紀錄、土地 shap file 、各部會註記（例如環保署公告為污染控制場域等）
> 建築技術規則
> [name=che l]

> 這應該在法規已經有了
> [name=Chia-liang K]

> 森林資料
> [name=che l]

> 什麼樣的森林資料呢？
> [name=Chia-liang K]

> 直覺想到的是從日治時期開始的全台森林資源調查，以及農委會目前內部規劃的「林地分級」制度。比較像是「自然資源調查資料」，這樣看起來應該屬於「環境資料」分類，其他如溼地分佈、動植物分佈、再生能源調查資料（地熱）、地調所地質敏感區分佈資料...等
> [name=che l]

> 原住民自治區與相應的土地運用制度 (例如蘭嶼的土地繼承制度與國民政府的地籍制度有所不同)
> [name=che l]

> 搬到上面行政區那邊？其實加上法律 reference 到特定行政區 applicable 的就可以表達特有制度了？
> [name=Chia-liang K]

> 嗯嗯
> [name=che l]

> 其實"土地劃分與所有人"跟"區域/都市計畫、土地使用分區"是兩個層次，前者是描述土地的所有權跟使用權，後者是描述土地被使用的限制、義務和權益
> [name=Richard H]

2.  **法人基本資訊 / Legal Entities**
    1.  工商登記 / Business and Factories：基本資料、董監事資料、基本資料及董監事歷史變動、工廠登記、污染申報
    2.  非營利事業與人民團體、工會 / NPO and Associations：（除上外）財務報告、
    3.  政府捐助法人或投資 / Government-sponsored entities or investments：（除上外）獨立董事歷史變動
3.  **採購資訊與委外營運服務明細 / Procurement **
    1.  政府採購：招標及開標結果資訊、
    2.  委外營運服務（含 BOT）：機關及營運單位、服務內容、合約
    3.  各類政府補助（研究計畫、執行計畫、租稅及各種補貼）：
4.  **國防與外交 / Defense and Foreign Affairs**
    1.  外交：國際組織與公約或國際條約參與現況、
    2.  國防：軍事統計


## 服務與民生


### Tier 3: Public Safety 公共安全


1.  **公共檢查及違法事項 / Inspections and Violations**
    1.  事業單位之各項檢查：應受檢行業及項目、統計、明細、結構化明細
    2.  事業單位受行政處分公告：統計、明細、結構化明細
> 「公共檢查」，就會包含 公害資料（例如 桃園 RCA 廠址地下水污染源、全國工廠污染檢舉資料、）食品衛生安全抽查、勞動檢查資料..囉？「公共檢查」一詞，為了「公共與公眾而啟動的檢查」之意，覺得可以成為一種統籌式的用詞，甚至民間組織發起的檢查、公民科學家針對某污染源的監測..，或許也可以涵蓋進來
> [name=che l]

> 這邊先針對政府依法應該主動檢查的事項，有共通格式就可以和民間的用同樣方式接取
> [name=Chia-liang K]

2.  **犯罪與事故 / Crimes and Accidents**
    1.  犯罪統計：縣市、轄區、路段，或一級發布區
    2.  事故統計：縣市、轄區、路段，或一級發布區
3.  **環境與災害 / Environment and Disasters**
    1.  監測 / Sensing：大氣監測、水資源監測、衛星空照圖
    2.  自然資源
> 例如「水資源管理資料」這種自然資源調查資料，是否也是屬於此分類項目？
> [name=che l]

    3.  災害與警示：
        1.  發生當下的現況：例如通報資料、
        2.  致災潛勢分析與預測：例如斷層在哪裡、淹水模擬的資料、高齡者與行動不便的人的居住集中區域、化學氣體產業園區位置...等
> 動植物疾病，例如 OIE 與農委會禽流感疫情資料 ...是否也屬於 “Tier 3: Public Safety”？
> [name=che l]

> 國際與國內的疾病管制資料，會放在健康與醫療嗎？例如WHO所蒐集的各國資料與疾管局資料
> [name=che l]


### Tier 4: Services 公營服務


1.  **基礎建設 / Infrastructures**
    1.  網路 / Internet：carrier coverage, pricing.. .
    2.  交通及大眾運輸 / Transportation：
    3.  水、能源 / Water and Energy：價格、公共設施使用量、地區別使用量
    4.  公共設施(通常會涵蓋前述所有項目資料)/如大巨蛋/轉運站總量體/河濱公園/水利設施
        1.  管線
2.  **健康與醫療 / Health and Medical Care**
    1.  食品條碼：公司 (統編)、產地、內容物、熱量、添加物
    2.  藥品成分：交互作用、藥物、含藥化妝品、醫材
    3.  醫療照護資源：醫院門/急診/病床資訊、健保各類給付統計、醫院評鑑指標
> 安養護機構清單
> [name=羅佩琪]

> （參考「5.1 需要執照或許可的行業及明細」）
> [name=Chia-liang K]

3.  **教育與研究 / Education and Research**
    1.  國民教育：
        1.  十二年國教課綱（領域、年級、出版社、單元、內容文字、週次、教學活動、能力指標）
    2.  辭典/字典：
    3.  高等教育與研究：
    4.  技職教育：
    5.  產學合作：
    6.  館藏與文物、數位典藏資料：
4.  **服務要求與陳情 / Service Requests and Petitions**
    1.  1999 / 311 回報統計：依區域/類別/單位、處理時間、
    2.  法規建言、

### Tier 5: Economic Activities 經濟活動


1.  **生產及各類執照 / Producing and Licenses**
    1.  需要執照或許可的行業：行業表、合法單位明細、
    2.  專利、商標及所有者：
> 本項目子分類架構可參考目前的資訊系統 [https://www.tipo.gov.tw/lp.asp?CtNode=7454&CtUnit=3606&BaseDSD=7&mp=1](https://www.tipo.gov.tw/lp.asp?CtNode=7454&CtUnit=3606&BaseDSD=7&mp=1)
> [name=che l]

    3.  農業：統計、明細、結構化明細
        1.  產銷統計（包括銷售、拍賣金額、歷年各類作物栽培面積）
        2.  農業資材、藥劑各項資訊
        3.  作物疫情的數據(主動、被動等各種監測、診斷鑑定資料)
> 補助及農損補助金
> [name=曼 奧]

> 見 2.3 「各類補貼」
> [name=Chia-liang K]

> 農產品進出口歷年各品項詳細數據
> [name=曼 奧]

> 見 5.3 國際貿易部分
> [name=Chia-liang K]

> 農地各項統計(包含應用、歷年變更)
> [name=曼 奧]

> 見 2.1 土地劃分部分
> [name=Chia-liang K]

> 科技研究可公開的各項研究成果
> [name=曼 奧]

> 見 2.3 「補助的研究計畫」
> [name=Chia-liang K]

> 農業金融資料
> [name=曼 奧]

> 這個有什麼範例嗎？
> [name=Chia-liang K]

> 農業金融資料，指的是例如農會、水利會的借貸放款與財產資料、農企業的金融資料嗎？
> [name=che l]

> 基本資料應該已經在政府組織或法人了；有什麼哪些和 5.2 不同的資料嗎？
> [name=Chia-liang K]

    4.
2.  **不動產與金融 / Real-estate and Finance**
    1.  不動產交易資訊
    2.  金融機構存放款統計
    3.  消費性金融商品：商品利率範圍與額外收費明細
3.  **國際貿易 / International Trades**
    1.  關務：月進出口項目統計、進出口廠商及貨品明細
    2.  入出國：
    3.  外國投資：



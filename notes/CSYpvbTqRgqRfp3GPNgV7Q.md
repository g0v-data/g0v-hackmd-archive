---
title: "g0v.tw 政府標案"
tags: hackpad
---

# g0v.tw 政府標案

> [點此觀看原始內容](https://g0v.hackpad.tw/WzhQXTDHe1S)

> copied from [https://hackpad.com/g0v.tw--0M0HW9tSVNQ](https://hackpad.com/g0v.tw--0M0HW9tSVNQ)
> [name=Finjon K]

### TODO

- [x] 政府電子採購網決標頁面 html 原始資料
- [x] 政府電子採購網決標頁面 html to json parser
- [x] 政府電子採購網決標資訊處理好的 json 資料
- [ ] website
    - [ ] demo 的視覺呈現方式, 內容字型自動縮小或摘要
    - [ ] demo 的專案內容自動連結到本文
- [ ] 找出年度（或幾年間）獲作多標案（就量或者金額）負責人名
- [ ] 找出獲標負責人與政府官員, 獲標人與另外獲 標人的人際關係（幾度分離）facebook data ?
- [ ]

### 程式碼

- [https://github.com/jeffhung/g0v-pcc](https://github.com/jeffhung/g0v-pcc)
- [https://github.com/tka/g0v-pcc/tree/master/ruby-pcc-parser](https://github.com/tka/g0v-pcc/tree/master/ruby-pcc-parser)
- [https://github.com/tka/pcc-web](https://github.com/tka/pcc-web)

### 資料

[https://app.box.com/s/rpp7fjsfolv29g75l3yz](https://app.box.com/s/rpp7fjsfolv29g75l3yz) 201201~201307 決標頁面 html 檔(解開約20G)
[https://app.box.com/s/7voon5n4vqe3mir73k46](https://app.box.com/s/7voon5n4vqe3mir73k46) 201201~201307JSON 格式資料(解開約29萬個 json檔. 約20G)

[https://www.box.com/s/zay4df6wakfurethid0f](https://www.box.com/s/zay4df6wakfurethid0f) 2012/01~12 簡單版標案資料庫 dump
### 網站 Wireframe

[http://iplotz.com/app/viewer.php?k=e14e84c7e7e29f5757727a3769433d92&pr=107385&pg=107385_1&a=90466&sitemap=false](http://iplotz.com/app/viewer.php?k=e14e84c7e7e29f5757727a3769433d92&pr=107385&pg=107385_1&a=90466&sitemap=false)

### 網站 DEMO

[http://g0v-pcc.tka.lu](http://g0v-pcc.tka.lu) =\> 失聯中

### 資料來源

    - 政府資料採購網
        - [http://web.pcc.gov.tw/tps/pss/tender.do?method=goSearch&searchMode=common&searchType=basic](http://web.pcc.gov.tw/tps/pss/tender.do?method=goSearch&searchMode=common&searchType=basic)
    - 台灣採購公報網
        - [http://www.taiwanbuying.com.tw/](http://www.taiwanbuying.com.tw/)
    - 財政部國有財產局
        - [http://www.mofnpb.gov.tw/CFT.php](http://www.mofnpb.gov.tw/CFT.php)
    - 地方政府
        - 基隆市政府[http://www.klcg.gov.tw/home.jsp?mserno=200710020005&serno=200710020034&menudata=klcgmenu&contlink=ap/news5.jsp](http://www.klcg.gov.tw/home.jsp?mserno=200710020005&serno=200710020034&menudata=klcgmenu&contlink=ap/news5.jsp)
    - （半）官方企業
        - 台灣高鐵
            - [http://www.thsrc.com.tw/tc/about/ab_invite.asp](http://www.thsrc.com.tw/tc/about/ab_invite.asp)
spread sheet: [https://docs.google.com/spreadsheet/ccc?key=0AvUAXjRBkUtkdFEzbGtrWW1hU08tN3pVQnZ2Xzh3SkE#gid=0](https://docs.google.com/spreadsheet/ccc?key=0AvUAXjRBkUtkdFEzbGtrWW1hU08tN3pVQnZ2Xzh3SkE#gid=0)

### 資料使用限制

- 政府電子採購網安全保護聲明 [http://web.pcc.gov.tw/pis/main/pis/client/pssa/security.do](http://web.pcc.gov.tw/pis/main/pis/client/pssa/security.do)

非經行政院公共工程委員會或各權利人之同意，使用者不得以任何形式利用政府電子採購網上之內容，使其存在於任何出版物、網站、檢索系統或相類似之場所。

- 政府電子採購著作權聲明 [http://web.pcc.gov.tw/pis/main/pis/client/pssa/right.do](http://web.pcc.gov.tw/pis/main/pis/client/pssa/right.do)

    1.行政院公共工程委員會網站上刊載之所有內容，除著作權法規定不得為著作權之標的（如法律、命令、公務員撰擬之講稿、新聞稿等--請參考著作權法第9條規定）外，其他包括文字敘述、攝影、圖片、錄音、影像及其他資訊，均受著作權法保護。

    2.上述不得為著作權標的者，任何人均得自由利用，歡迎各界廣為利用。

- 著作權法第9條 [http://law.moj.gov.tw/LawClass/LawSingle.aspx?Pcode=J0070017&FLNO=9](http://law.moj.gov.tw/LawClass/LawSingle.aspx?Pcode=J0070017&FLNO=9)

    第 9 條
    下列各款不得為著作權之標的︰
    一、憲法、法律、命令或公文。
    二、中央或地方機關就前款著作作成之翻譯物或編輯物。
    三、標語及通用之符號、名詞、公式、數表、表格、簿冊或時曆。
    四、單純為傳達事實之新聞報導所作成之語文著作。
    五、依法令舉行之各類考試試題及其備用試題。
    前項第一款所稱公文，包括公務員於職務上草擬之文告、講稿、新聞稿及
    其他文書。
    （個人是覺得招標/決標公告，屬於公文的一種，所以只要抓得出來，就能隨意使用。）

- 政府採購公告及公報發行辦法
[http://law.moj.gov.tw/LawClass/LawAll.aspx?PCode=A0030065](http://law.moj.gov.tw/LawClass/LawAll.aspx?PCode=A0030065)
[http://law.moj.gov.tw/LawClass/LawSingle.aspx?Pcode=A0030065&FLNO=22](http://law.moj.gov.tw/LawClass/LawSingle.aspx?Pcode=A0030065&FLNO=22)

    第 22 條
    銷售採購公報及提供採購網站資訊服務，得向採購公報訂戶及資訊服務使
    用者收費；其收費標準，由主管機關定之。
> [Tim Berners-Lee 對於 Aaron Swartz 官司引用之法律的評論](http://techcrunch.com/2013/01/25/tim-berners-lee-at-davos/)：If you break into a computer system in any way then you are guilty of a felony.
> [name=Finjon K]


### 聯絡簿

- tka
    - irc: tka
    - twitter: [http://www.twitter.com/tkalu](http://www.twitter.com/tkalu)
    - github: [http://github.com/tka](http://github.com/tka)
- rcchiu: [rcchiu@gmail.com](https://hackpad.com/A2eTgEqgpTn#rcchiu@gmail.com) (查法條/文案/UI架構)
- Sorry
    - [http://www.plurk.com/sorry](http://www.plurk.com/sorry)
- jeffhung
    - [http://www.plurk.com/jeffhung](http://www.plurk.com/jeffhung)
    - [https://twitter.com/jeffhung](https://twitter.com/jeffhung)
    - [http://github.com/jeffhung](http://github.com/jeffhung)
- Lucy dailylucy@gmail.com (文案/UI架構/做雜事)

### 技術議題

    - 資料來源
        - 搜尋頁面
        - 標案列表
        - 標案內容
            - 決標公告的網頁版與「文字列印」版內容不同，未得標的廠商就沒有列在「文字列印」版內容
    - 下載
        - 每個月光公開招標就有約一萬筆（其他還有限制性招標、選擇性招標等），決標公告也約一萬筆，掃一年的份量會在幾十萬以上，如何分散流量以免造成政府主機負擔？
        - 是否有不在政府電子採購網的標案資料（國防類／鄉鎮學校等小型採購／夢想家等級大型案件）？
    - 政府機關代碼有兩套，識別碼不同(樹也不同)
        - 機關代碼查詢 [http://web.pcc.gov.tw/tps/main/pss/pblm/tender/basic/search/mainListCommon.jsp?searchTarget=ATM](http://web.pcc.gov.tw/tps/main/pss/pblm/tender/basic/search/mainListCommon.jsp?searchTarget=ATM)
        - 政府領域 OID
        - [http://oid.nat.gov.tw/OIDWeb/chmain.html](http://oid.nat.gov.tw/OIDWeb/chmain.html)
    - 儲存格式
        - JSON
        - 採用現行命名方式（primary key）對未來可能的相容性？
    - 視覺化

### 預定產出

    - library
    - 資料檔
        - 政府電子採購網 2012/01~2012/11 決標資料, html 原始頁面
            - [https://www.box.com/s/11vpm66zug4qyrffml4r](https://www.box.com/s/11vpm66zug4qyrffml4r)
        - 政府電子採購網 2012/01~2012/11 決標資料, json 格式, 166837 筆
            - [https://www.box.com/s/mcw5pn75izmv94ohtfhz](https://www.box.com/s/mcw5pn75izmv94ohtfhz)
    - 專案網站

### 期待 / 關注的問題

    - 列出所有標案(金額), 何時招標, 何時結標
        - 提供過濾項目：機關名稱，標案名稱，金額級距，招標方式。
    - 結標的單位是否集中在特定單位(得標金額, 得標次數/year, 得標成功率)
    - 根據熱門新聞的關鍵字 ==> 找出相關標案 ==\> 投標廠商 grouping
    - 廠商與招標單位的得標關係
        - 共同投標的廠商的群組關係
            - 是否有固定幾家廠商一起經營標案的情況/或是某些服務類別，大多由哪幾家廠商投標
            - 期望能找出哪些廠商，固定去投標並輪流得標
            - 複數決標是否有特殊分配
            - 廠商跟廠商之間的父子關係？
            - 廠商老闆、董監事與其它廠商的交叉關係
    - 異常結標情形
        - 求出平均的標案金額、投票廠家數與結標時間關聯
        - 找出異常的結標案件
            - 同金額，比平均快速結標
            - 同金額，拖了很久還無法結標
    - 特殊屬性標案特性
        - 優先採購身心障礙福利機構
        - 愛台十二項計畫
    - 熱門新聞相關的標案
    - 關鍵字？Tag?
    - 藉由顯示好幾年每月招標數的長條圖看到年底銷預算的現象
> 上述看來有許多是資料分析的問題，若有需要，我可以看看能否幫忙設計 dashboard 或是分析數據。
> [name=Finjon K]

> 需要！我手邊有的資料有標案跟公司登記的資料, 但是還沒有明確的規劃要進行哪些分析工作, 有人能明確定義出來是最好的了 
> [name=Finjon K]

> 我之前有做過提案法案與立委之間的關聯度分析 (請見[http://mslab.csie.ntu.edu.tw/~askus/ly/bill.php](http://mslab.csie.ntu.edu.tw/~askus/ly/bill.php)) ，想套用分析到政府單位 X 決標關鍵字的關連分析。想請問有沒有"發包機關\\t標案名稱\\t金額\\t投標廠商\\t得標廠商" 的資訊？謝謝！另外想到，如果有公司 X 董事名稱的資料，或許可以做交叉持股的分析。 
> [name=Finjon K]




### 呈現方式

目前的interactive wireframe:
[http://iplotz.com/app/viewer.php?k=e14e84c7e7e29f5757727a3769433d92&pr=107385&pg=107385_1&a=90466&sitemap=false](http://iplotz.com/app/viewer.php?k=e14e84c7e7e29f5757727a3769433d92&pr=107385&pg=107385_1&a=90466&sitemap=false)

上述1,2,3,4,6,7,8,9項功能已可在wireframe架構中實現, 5.異常結標情形還需要想想怎麼呈現

###     廠商的overview，呈現餅怎麼分

    輸入：發案單位與年度 or Tag
    UI：[http://bl.ocks.org/4063582](http://bl.ocks.org/4063582)
    情境：某單位某年度所有標案overview（by 金額 or 得標數目)將廠商分類
註:treemap尚可呈現階層性的資料(e.g. 勞務類>A+B+C包商 /財物類> B+C 包商 /工程類>A+C+D包商)
單一階層的話,圓餅圖也可做出分大餅的呈現
([http://en.wikipedia.org/wiki/Treemapping](http://en.wikipedia.org/wiki/Treemapping))

###     長條統計圖

        輸入：時間，顯示哪些單位（使用機關階層）
        ui：[http://bl.ocks.org](http://bl.ocks.org) @ [/4062085](http://bl.ocks.org/4062085)
     情境：可在一張圖比較指定機關的三種”標的分類”金額與數量
###     標籤雲

    UI [http://www.lucaongaro.eu/demos/jqcloud/](http://www.lucaongaro.eu/demos/jqcloud/)
    情境：跨標案跨單位的歸類項目

###     網站分析

        1\. 使用者：大眾
        2\. 使用方式：特定專案 / 比例分配?

### 名詞解釋

公開招標、選擇性招標、限制性招標
第18條（招標之方式及定義）
採購之招標方式，分為公開招標、選擇性招標及限制性招標。
本法所稱公開招標，指以公告方式邀請不特定廠商投標。
本法所稱選擇性招標，指以公告方式預先依一定資格條件辦理廠商資格審查後，再行邀請符合資格之廠商投標。
本法所稱限制性招標，指不經公告程序，邀請二家以上廠商比價或僅邀請一家廠商議價。

第20條 ：定義選擇性招標之情形

第22條：定義限制性招標之情形

條約或協定採購
政府採購法第105條：依條約或協定向國際組織、外國政府或其授權機構辦理之採購，其招標、決標另有特別規定者。得不適用政府採購法招標、決標之規定。前項之採購，有另定[處理辦法](http://www.6law.idv.tw/6law/law3/%E7%89%B9%E5%88%A5%E6%8E%A1%E8%B3%BC%E6%8B%9B%E6%A8%99%E6%B1%BA%E6%A8%99%E8%99%95%E7%90%86%E8%BE%A6%E6%B3%95.htm)予以規範之必要者，其辦法由主管機關定之。

公告日(各種採購方式等標期下限表)
1.依政府採購法第34條規定於招標前將招標文件稿辦理公開閱覽且招標文件內容未經重大改變者,等標期得縮短五日.但縮短後不得少於十日.(以下簡稱閱覽或閱)
2.依政府採購法第93條之一規定辦理電子領標並於招標公告敘明者,等標期得縮短三日.但Y短後不得少於五日.(以下簡稱電領或領)
3.依政府採購法第93條之一規定辦理電子投標並於招標公告敘明者,等標期得縮短二日.但縮短後不得少於五日.(以下簡稱電投或投)

(via.[行政院公共工程委員會](http://www.pcc.gov.tw/pccap2/BIZSfront/FrontMenu.do?site=002&bid=BIZS_CF0000077)> 政府採購 > 政府採購資訊 \> 招標方式暨等標期)
決標方式
分為同質採購與異質採購兩大類
同質採購：
最低標結標
異質採購：
最低標決標 (1、採分段開標，資格、規格符合者，再開價格標，最低標決標。2、資格、規格標之訂定及審查，借重專家學者之專業審查機制。依「機關異質採購最低標作
業須知」進行)
最有利標決標 (採購法第56條、最有利標評選辦法、採購評選委員會組織準則、採購評選委員會審議規則等。依「機關異質採購最有利標作業須知」進行)

28天


統包
統包原文「Turn key」直接翻譯為「移交鑰匙」，亦即「交付業主直接使用」之意，比如：購買預售房屋、購買組合傢俱、自家委託室內裝修、．．．等。其實統包行為存在你、我日常生活中。
國、內外採購工程、特殊、專用設備系統也常用統包方式，例如：特殊機具（潛盾機、採礦機）、船舶（貨櫃輪、油輪、郵輪）、橋樑、隧道、海上鑽油平臺、焚化廠、發電廠、煉油廠、煉鋼廠、纜車、．．等。
而 國內公共工程主辦機關辦理統包工程（設計及施工）面臨與傳統工程（設計完成後發包施工）的最大差異，在於統包一改過去按圖施工、按表計價的觀念，轉為發包 一個尚未具體成形的招標文件、需求計畫；等到決標後，工程主辦機關才能根據得標廠商（即統包廠商）的統包企劃書瞭解工程概要；這過程常使初次接觸統包工程 的工程主辦機關感到困惑與不安。
反觀廠商面臨備標時間限制，承受以概略設計圖說估算成本的風險；因此降低廠商投標統包工程的意願。
即 使統包工程決標後，進入工程主辦機關與統包商逐次討論發展設計過程，若工程主辦機關（或PCM）對工程標的功能與規模不確定，則無法適應統包契約設計、施 工並進模式，而反覆更動需求計畫，或提出契約約定範圍以外之需求，及統包廠商面臨需求計畫更動，無法掌握設計期程及建造成本，因此雙方互動時必然產生爭 執。
從字面上解讀「統包」或許相當單純，但牽涉到工程主辦機關與統包商間信賴程度及對統包運作熟練度，所以統包工程目前仍非工程主辦機關主要選項。

(via.[淺談統包工程實務 \- 行政院公共工程委員會)](http://www.pcc.gov.tw/pccap2/BIZSfront/upload/article/0bb2fe4d955df3f048ae760d1f0ade56.doc)


共同供應契約政 府採購法第 93  條規定，各機關得就具有共通需求特性之財物或勞務，與廠商簽訂共同供應契約。所稱之共同供應契約，指一機關為二以上機關具有共通需求特性之財物或勞務與廠 商簽訂契約，使該機關及其他適用機關均得利用該共同供應契約辦理採購。對於廠商而言，簽訂共同供應契約後，即有義務依約供應採購標的予該契約之所有適用機 關。

機關辦理共同供應契約，應依政府採購法之規定辦理。招標方式依政府採購法第 18 條至第 23 條擇定，即採公開招標、選擇性招標或限制性招標方式辦理。決標原則應符合第 52 條第 1
項 第 1 款至第 4 款其中一款之規定，採合格最低標決標、最有利標決標或複數決標。   共同供應契約之採購作業程序與一般採購招標相同，招標資訊刊登於政府採購公報（網路版）並公告於行政院公共工程委員會政府電子採購網  ([http://web.pcc.gov.tw](http://web.pcc.gov.tw))。廠商應依規定領取或購買招標文件、準備投標文件並參加投標，開標後廠商投標文件經機關審查合格且依決標 程序得標後，簽約成為共同供應契約供應廠商。

在 共同供應契約內有二家以上立約商供應時，機關可自行依本身需求選定最符合需求之立約商。惟為使機關利用共同供應契約之程序更為公開透明，避免私相授受之情 形，倘個別項次訂購金額超過新臺幣  10萬元者，行政院公共工程委員會要求各機關應於政府電子採購網訂購時勾填擇定廠商理由，例如交貨期能配合機關急需、服務較佳、品質功能較符合需求、價格 較便宜等（註：政府電子採購網已提供選取或自行填寫擇定廠商理由之機制，供機關勾選或填寫理由），經簽准後據以訂購。

倘 契約條款訂有大量訂購時允許訂購機關得洽廠商另行議定優惠條件之機制，除擬訂購之項次僅有 1 家廠商得標之情形外，機關應自行徵詢 2  家以上立約商並經內部簽辦程序選定訂購對象後，再行據以訂購。前述議定優惠條件並應依行政院公共工程委員會 99 年 10 月 19  日工程企字第09900415800 號令頒之「機關利用共同供應契約辦理採購監辦規定一覽表」辦理。


(via. [http://www.bot.com.tw/Procurement/Procure\_supply/Supply\_qna/Documents/101sec2.pdf](http://www.bot.com.tw/Procurement/Procure_supply/Supply_qna/Documents/101sec2.pdf))

協商措施政府採購法第55條：機關辦理以最低標決標之採購，經報上級機關核准，並於招標公告及招標文件內預告者，得於依前二條(第53、54條)規定無法決標時，採行協商措施。

政府採購法第57條：機關依前二條(第55、56條)之規定採行協商措施者，應依下列原則辦理︰
一、開標、投標、審標程序及內容均應予保密。
二、協商時應平等對待所有合於招標文件規定之投標廠商，必要時並錄影
    或錄音存證。
三、原招標文件已標示得更改項目之內容，始得納入協商。
四、前款得更改之項目變更時，應以書面通知所有得參與協商之廠商。
五、協商結束後，應予前款廠商依據協商結果，於一定期間內修改投標文
    件重行遞送之機會。

政府採購法施行細則第76條：
本法第五十七條第一款所稱審標，包括評選及洽個別廠商協商。
本法第五十七條第一款應保密之內容，決標後應即解密。但有繼續保密之必要者，不在此限。
本法第五十七條第一款之適用範圍，不包括依本法第五十五條規定採行協商措施前之採購作業。
政府採購法施行細則第77條：
機關依本法第五十七條規定採行協商措施時，參與協商之廠商依據協商結果重行遞送之投標文件，其有與協商無關或不受影響之項目者，該項目應不予評選，並以重行遞送前之內容為準。



複數決標複數決標係指一個招標案可以產生2家以上之得標廠商。依採購法第52條規定，機關採複數決標的方式，得於招標文件中公告保留採購項目或數量選擇之組合權利，但應合於最低價格或最有利標之競標精神。
也就是說，機關可以就同一採購案，依品項或數量，決標給不同的廠商，如此可以有助於促進競爭、分散履約風險、提高採購效益。
實務上，複數決標常適用於採購品項眾多（如醫療用品）、或數量龐大宜與多家廠商訂約（如委託便利超商或金融機構收款）、或分散貨源（如台電購煤）。
(via. [http://www.pcc.gov.tw/epaper/9908/procurement.htm](http://www.pcc.gov.tw/epaper/9908/procurement.htm))

共同投標政府採購法第25條：機關得視個別採購之特性，於招標文件中規定允許一定家數內之廠商共同投標。
前項所稱共同投標，指二家以上之廠商共同具名投標，並於得標後共同具名簽約，連帶負履行採購契約之責，以承攬工程或提供財物、勞務之行為。
共同投標以能增加廠商之競爭或無不當限制競爭者為限。
同業共同投標應符合公平交易法第十四條但書各款之規定。
共同投標廠商應於投標時檢附共同投標協議書。
共同投標辦法，由主管機關定之。

押標金標案金額百分之五以下
政府採購案例解析三～押標金之相關問題
[https://docs.google.com/viewer?a=v&q=cache:YgjglgNZhQ4J:www.stat.gov.tw/public/Attachment/411214434971.doc+&hl=zh-TW&pid=bl&srcid=ADGEESia-tEy7BHi8CCFssGaQ-3juIIPjISouNXqHesgiqXfrD7TxyT7EyVHp5d5VmuAbyJJLFJk-uF00ZMbvaVnt-wBnandFzkCZhbGuAlcey2dKqIxULZ4HtkauKppW_5TJ-P5Lztl&sig=AHIEtbS5xrVzhLwkMlhlbErfRWVhMN0kNA](https://docs.google.com/viewer?a=v&q=cache:YgjglgNZhQ4J:www.stat.gov.tw/public/Attachment/411214434971.doc+&hl=zh-TW&pid=bl&srcid=ADGEESia-tEy7BHi8CCFssGaQ-3juIIPjISouNXqHesgiqXfrD7TxyT7EyVHp5d5VmuAbyJJLFJk-uF00ZMbvaVnt-wBnandFzkCZhbGuAlcey2dKqIxULZ4HtkauKppW_5TJ-P5Lztl&sig=AHIEtbS5xrVzhLwkMlhlbErfRWVhMN0kNA)

特殊採購、巨額採購特殊採購
工程採購：
１、興建構造物，地面高度超過五十公尺或地面樓層超過十五層者；
２、興建構造物，單一跨徑在五十公尺以上者；
３、開挖深度在十五公尺以上者；
４、興建隧道，長度在一千公尺以上者；
５、於地面下或水面下施工者；
６、使用特殊施工方法或技術者；
７、古蹟構造物的修建或拆遷；
８、其他經主管機關認定者。
財物採購、勞務採購：
    - 採購標的之規格、製程、供應或使用性質特殊者；
    - 採購標的需要特殊專業或技術人才始能完成者；
    - 採購標的需要特殊機具、設備或技術始能完成者；
    - 藝術品或具有歷史文化紀念價值的古物；
    - 其他經主管機關認定者。
巨額採購：
    - 工程採購新台幣二億元以上者為巨額採購；
    - 財物採購新台幣一億元以上者為巨額採購；
    - 勞務採購新台幣二千萬元以上者為巨額採購。
via [http://taipei.law119.com.tw/personview.asp?kname=%A7%F5%A5%C3%B5M&ktop=%A6%F3%BF%D7%A1u%AFS%AE%ED%B1%C4%C1%CA%A1v%A1B%A1u&idno=3404&keywords=](http://taipei.law119.com.tw/personview.asp?kname=%A7%F5%A5%C3%B5M&ktop=%A6%F3%BF%D7%A1u%AFS%AE%ED%B1%C4%C1%CA%A1v%A1B%A1u&idno=3404&keywords=)

公開閱覽
[http://plan3.pcc.gov.tw/gpletf/09800383203.pdf](http://plan3.pcc.gov.tw/gpletf/09800383203.pdf)  公共工程招標文件公開閱覽制度實施要點
[http://www.pcc.gov.tw/pccap2/BIZSfront/MenuContent.do?site=002&bid=BIZS_C00007256](http://www.pcc.gov.tw/pccap2/BIZSfront/MenuContent.do?site=002&bid=BIZS_C00007256)

全質與異質採購
[http://www.general.ncnu.edu.tw/ias/htm/law9-2.htm](http://www.general.ncnu.edu.tw/ias/htm/law9-2.htm)

政府法規政府採購法
[http://www.6law.idv.tw/6law/law/政府採購法.htm](http://www.6law.idv.tw/6law/law/政府採購法.htm)

政府採購法規(與子法)-行政院工程會全球資訊網 [http://www.pcc.gov.tw/pccap2/BIZSfront/FrontMenu.do?site=002&bid=BIZS_CF0005066](http://www.pcc.gov.tw/pccap2/BIZSfront/FrontMenu.do?site=002&bid=BIZS_CF0005066)

中央機關未達公告金額採購招標辦法 [http://lawweb.pcc.gov.tw/LawContent.aspx?id=FL000666](http://lawweb.pcc.gov.tw/LawContent.aspx?id=FL000666)
政府採購法第十三條第三項所稱公告金額：工程、財物及勞務採購均為新台幣一百萬元[http://www.pcc.gov.tw/pccap2/BIZSfront/MenuContent.do?site=002&bid=BIZS_C00007169](http://www.pcc.gov.tw/pccap2/BIZSfront/MenuContent.do?site=002&bid=BIZS_C00007169)


第104條   （軍事機關採購不適用本法之情形）
軍 事機關之採購，應依本法之規定辦理。但武器、彈藥、作戰物資或與國家安全或國防目的有關之採購，而有下列情形者，不在此限。  一、因應國家面臨戰爭、戰備動員或發生戰爭者，得不適用本法之規定。 二、機密或極機密之採購，得不適用第二十七條、第四十五條及第六十一條之規定。  三、確因時效緊急，有危及重大戰備任務之虞者，得不適用第二十六條、第二十八條及第三十六條之規定。  四、以議價方式辦理之採購，得不適用第二十六條第三項本文之規定。 前項採購之適用範圍及其處理辦法，由主管機關會同國防部定之，並送立法院審議。

第105條    （不適用本法招標決標規定之採購）
機 關辦理下列採購，得不適用本法招標、決標之規定。 一、國家遇有戰爭、天然災害、癘疫或財政經濟上有重大變故，需緊急處置之採購事項。  二、人民之生命、身體、健康、財產遭遇緊急危難，需緊急處置之採購事項。 三、公務機關間財物或勞務之取得，經雙方直屬上級機關核准者。  四、依條約或協定向國際組織、外國政府或其授權機構辦理之採購，其招標、決標另有特別規定者。  前項之採購，有另定處理辦法予以規範之必要者，其辦法由主管機關定之。

第106條第1項第1款（駐外機構辦理採購之規定）
駐國外機構辦理或受託辦理之採購，因應駐在地國情或實地作業限制，且不違背我國締結之條約或協定者，得不適用下列各款規定。但第二款至第四款之事項，應於招標文件中明定其處理方式。
一、第二十七條刊登政府採購公報。
二、第三十條押標金及保證金。
三、第五十三條第一項及第五十四條第一項優先減價及比減價格規定。
四、第六章異議及申訴。
前項採購屬查核金額以上者，事後應敘明原由，檢附相關文件送上級機關備查。

政府採購法施行細則
[http://law.moj.gov.tw/LawClass/LawAll.aspx?PCode=A0030058](http://law.moj.gov.tw/LawClass/LawAll.aspx?PCode=A0030058)


十萬以上需公開招標的規定[http://www.lawtw.com/article.php?template=article\_content&area=free\_browse&job\_id=146338&parent\_path=,1,561,197,&article\_category\_id=2193&article_id=76468](http://www.lawtw.com/article.php?template=article_content&area=free_browse&job_id=146338&parent_path=,1,561,197,&article_category_id=2193&article_id=76468)


惟10萬元以下之小額採購，仍得以依中央機關未達公告金額採購招標辦法第2條第1項之規定，採限制性招標或公開取得三家以上廠商之書面報價或企劃書，或依法公開招標或選擇性招標，則屬當然(實務上亦是如此)。


採購法對於採購案，依金額大小順序區分為：
(一) 巨額採購（工程案二億元以上；財物案一億元以上；勞務案二千萬元以上），係規範廠商特定資格(第三十六條)，與瞭解、查核完成採購後使用期間之使用情形及效益之門檻金額(第一百十一條)。
(二) 查核金額（工程、財物案為五千萬元以上；勞務案一千萬元以上），係上級機關執行事前、事中監督之門檻金額。查核金額以上之案件，辦理過程須受上級機關監督(第十二條)。
(三)   公告金額（工程、財物及勞務案均為一百萬元以上），係機關將採購資訊公開、廠商申訴等之門檻金額。公告金額以上之案件，為採購法所欲規範之主要範圍。機關 辦理公告金額以上之採購，除依採購法第二十條規定採選擇性招標及第二十二條採限制性招標辦理者外，應公開招標（第十九條）。
(四) 未達公告金額之案件，其招標方式由主管機關、直轄市或縣(市)政府定之 (第二十三條) 。主管機關行政院公共工程委員會業依規定訂有「中央機關未達公告金額採購招標辦法」頒行。直轄市、縣（市）政府另有規定者，應從其規定，未規定者則比照中央規定辦理。
(五) 小額採購，其金額不得逾公告金額之十分之一，得不訂底價。
小 額採購之金額上限，由主管機關、直轄市或縣(市)政府定之(第四十七條)  。目前中央機關小額採購金額訂為十萬元，依「中央機關未達公告金額採購招標辦法」第五條規定，得不經公告程序，逕洽廠商採購，免提供報價或企劃書。直轄 市、縣（市）政府另有規定者，應從其規定，未規定者則比 照中央規定辦理。
(via.[行政院公共工程委員會>便民服務專區 \> 常見問答集](http://www.pcc.gov.tw/pccap2/FAQmain/FaqContent.do?site=002&fid=3122))

機關異質採購最低標作業須知
[http://lawweb.pcc.gov.tw/LawContentDetails.aspx?id=FL039295&KeyWordHL=&StyleType=1](http://lawweb.pcc.gov.tw/LawContentDetails.aspx?id=FL039295&KeyWordHL=&StyleType=1)

### 案例 / 政府招標公告訊息

夢想家
國慶晚會<夢想家>招標案 疑雲重重(20111101民進黨團記者會:蔡煌瑯李俊毅黃偉哲) [https://www.facebook.com/video/video.php?v=300764829951540](https://www.facebook.com/video/video.php?v=300764829951540)
共11筆招標資訊

公開的招標公告(摘要) ex: 教育部 [http://web.pcc.gov.tw/tps/tpam/main/tps/tpam/tpam\_tender\_detail.do?searchMode=common&scope=F&primaryKey=50843865](http://web.pcc.gov.tw/tps/tpam/main/tps/tpam/tpam_tender_detail.do?searchMode=common&scope=F&primaryKey=50843865)

衛武營
[http://www.ly.gov.tw/03\_leg/0301\_main/dispatch/dispatchView.action?id=37227&lgno=00038&stage=8](http://www.ly.gov.tw/03_leg/0301_main/dispatch/dispatchView.action?id=37227&lgno=00038&stage=8)

决標公告: 「釣魚臺主權宣導網站」委外建置案
機關名稱: 外交部; 招標方式 限制性招標(未經公開評選或公開徵求)
標的分類: 勞務類
公告日期: 101/10/19
決標金額: 989,900
[http://web.pcc.gov.tw/tps/main/pms/tps/atm/atmAwardAction.do?newEdit=false&searchMode=common&method=inquiryForPublic&pkAtmMain=50800022&tenderCaseNo=101180CA](http://web.pcc.gov.tw/tps/main/pms/tps/atm/atmAwardAction.do?newEdit=false&searchMode=common&method=inquiryForPublic&pkAtmMain=50800022&tenderCaseNo=101180CA)

### 其他


- [http://tender.sme.sk/en/report/all?cut=date:2012](http://tender.sme.sk/en/report/all?cut=date:2012)
- [某基金會歷年補助預算分配趨勢](http://www.hewlett.org/grants-tool/index) (基本上是個 [heatmap](http://mbostock.github.com/d3/talk/20111018/calendar.html))
- [network chart](http://mbostock.github.com/d3/talk/20111116/force-collapsible.html) (或是 [force-directed graph](http://bl.ocks.org/4062045)）

### 日後可能使用方式

1\. 缺乏素材的立法委員/媒體記者，搜尋裡面合法但是不合理的標案 (例如: 招標與決標時間相距太短)，作為報導的內容

請問：是否能考慮建立一個開放公開存取、定期更新資料的資料庫？我有一些資料分析的想法（例如視覺化分析、統計分析、預測系統等等），若有整理好的資料，可以來試試看。

### 資料可能分析的方向

1.  哪些廠商容易標到案子
2.  哪些案子很有影響力

NOTE.
流標資料分析

最近在整理預算案，看到有關「政府標案」的預算案提案 (教育文化委員會、文創發展業務)
[https://docs.google.com/file/d/0B3GcrxhjXW_pTXJjZF9oM1NMOUE/edit?usp=sharing](https://docs.google.com/file/d/0B3GcrxhjXW_pTXJjZF9oM1NMOUE/edit?usp=sharing)


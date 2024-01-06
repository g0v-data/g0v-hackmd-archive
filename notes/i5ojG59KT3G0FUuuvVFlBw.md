---
title: "經濟部開放資料需求"
tags: hackpad
---

# 經濟部開放資料需求

> [點此觀看原始內容](https://g0v.hackpad.tw/7kATMEUL8QZ)



### 2015-03-24 經濟部政府開放資料座談會（需求及建議事項）


出席：Ronny

需求：
- 工商登記：董監事資料（基本上 **gcis**.**nat 查得到的資料都應直接以開放資料釋出）**
    - 董監事除姓名外也要加上一個可識別是否為同一人的 hash
> 希望這個 hash 是所有公開資料通用，像是中選會選舉資料庫...
> [name=Finjon K]

> 可以建議各單位直接用 crc32(身份證字號 + '各單位一個共用字串) ，或者乾脆就身份證倒數三碼
> [name=Ronny W]

> partial 比較好（應該也符合目前個資法限制下大家以有的揭露方式），不然 hash salt 被破就等於所有人身分證字號公開了。
> [name=Chia-liang K]

> 我比較期待是 uuid mapping ，由一個單位統一管理對應表，然後所有單位照著用，畢竟 hash 會有還原的問題
> [name=Finjon K]

> mapping table 被拿到也會有所有人被公開的風險（而公開後就不可逆了）。
> [name=Chia-liang K]

> 感覺最簡單還是就身份證最後三碼，各單位手上都應該有身份證字號的，要再額外一個單位來管一個對應表還滿麻煩的，身份證假如只貼三碼應該碰撞到的機率不高吧，也不會有洩露個資的問題? 不過還會有改名的問題... 章孝嚴 =\> 蔣孝嚴
> [name=Ronny W]

> 同名同姓的情況非常多，所以理想上還是需要一個比較精確的索引碼， uuid mapping 的資料還原問題比較小就是了
> [name=Finjon K]

- 已廢止公司統一編號以及廢止時間
> 雖然有放每月清冊，不過歷史資料還是滿重要的，因為統一編號會在廢止後再發給別人，如果沒有一個廢止清冊和時間，之後做資料連結時有可能會連錯公司。
> [name=Ronny W]

- 經濟部工業局過去輔導案清冊、對應公司以及結案報告
> 應該 generalize 成各類政府補助，經濟部（工業局、中小企業處、水利署休耕補助）應該是較多的可以率先整理資料
> [name=Chia-liang K]

- (請協助從下面過往討論整理未開放資料)
- ~所有社團法人的統一編號~
- ~所有財團法人的統一編號 ~
> 這應該不歸經濟部管，已經開在財政部那邊了（稅藉登記）
> [name=Chia-liang K]

> 啊, 對, 國稅局歸財政部 orz
> [name=Pofeng L]

> [https://g0v.hackpad.com/93l4ryQUJlP](https://g0v.hackpad.com/93l4ryQUJlP)
> [name=Pofeng L]

- 所屬局處（如智慧財產局）做成影響人民權益法規之決策會議資料
> 舉例來說在2013年中智財局研議的封鎖重大境外侵權網站，公開的資料裡面顯示的都是反對的專家學者意見居多，那麼到底是怎麼形成這個結論的？
> [name=nchild]

> 又譬如2014年著作權法草案，原預定要開多場公聽會，卻因為音樂權利人佔領會場之後，將所有公聽會改成內部會議，這些會議的會議資料是否就不公開了呢？
> [name=nchild]


建議事項：


### (過往討論)

在開放資料研習營電腦公會捎來的訊息, 經濟部目前有意願開放更多的資料，但政府部門往往不知道該開放什麼 ( 全都開放吧! ) ，故在這裡開設回饋區，大家都把想要看到的資料但還沒看到的資料寫下來吧！
- 填資料的時候如果有想到應用, 也可以順便寫
- 也可以從經濟部相關執掌單位發想, 請參考 [http://zh.wikipedia.org/wiki/中華民國經濟部](http://zh.wikipedia.org/wiki/中華民國經濟部)
    - 比方說能源局, 水利署, 中鋼、中油，中小企業處等等
> 小弟想法，不怕官員做哪些事情違反法令，畢竟有些法令可能過於僵化，硬是遵守官員無法順利做事。但是怕的是民眾毫不知情。
> [name=Recca C]

> 另外小弟並不認為政府跟人民是敵對的狀況。恰恰相反，政府應該與人民互相合作，一起達到更好的施政效果。
> [name=Recca C]


目前有關的專案
- ~求職小幫手~
> 我有點疑問，這東西的效能在哪邊？有比104好用嗎？
> [name=Recca C]

> 完全不一樣的東西，請先去了解，不然很難回應。
> [name=nchild]

> 可以不要回阿@@ 這邊不強迫回應吧
> [name=Recca C]

> 是可以不回，但會那樣問有點像來亂的。
> [name=nchild]

> 恩 那就當作我來亂的吧 我無所謂
> [name=Recca C]

> 求職小幫手會在開啟104 公司網頁時, 同時顯示該公司是否曾違反過勞基法
> [name=Kirby W]

> 感謝回應
> [name=Recca C]

> 這應該是勞委會主管? 
> [name=Chia-liang K]

> [http://jobhelper.g0v.ronny.tw/](http://jobhelper.g0v.ronny.tw/)  <\-\- 求職小幫手
> [name=ipa c]

> 這˙算各地方政府勞工局的權責
> [name=Ronny W]


- 服貿相關
    - [~服貿條文~](http://www.ecfa.org.tw/SerciveTradeAgreement1.aspx?pid=7&cid=26)
> 已經有了
> [name=nchild]

> ok 感謝您。
> [name=Recca C]

    - [~官方對該條文造成影響的檢討~](http://www.ecfa.org.tw/ATSImpactAssessment.aspx?pid=7&cid=26&pageid=0)
        - ~各行各業分別造成的影響~
> 已經有了
> [name=nchild]

> 有經濟部公文?恕小弟無知，請提供網址
> [name=Recca C]

> 上面的聯結就是政府的網站資料，包含各行各業資料，之前還有舊的，只剩下備份。
> [name=nchild]

> 理解 感謝
> [name=Recca C]

> 所以服貿完全沒有相關的資料可以挖了嗎? 有沒有人對這方面很了解可以抓來推坑的?
> [name=Kirby W]

> 之前的會議記錄，但這可能要先立法要求才行。
> [name=nchild]

    - 討論會議記錄
- 政府標案相關
    - 標案過程
        - 標案公司
        - 標案價格
    - 標案原則
        - 最低標？
        - 合理標？
            - 合理範圍估計為多少，參考為？
- 投審會通過/否決細項
- 勞基法
    - 條文查詢(?)
- 公司相關
    - ~過去曾經違背勞基法的公司~
        - ~ronnywang 的求職小幫手有, 但是資訊來源似乎很不穩定(各縣市), 而且釋出時間(不明)跟格式(pdf?)都有問題, 可以從這點出發~
> 格式的部分，小弟建議提供經濟部我們希望的，簡單規劃的json格式。這樣經濟部也比較好去跟程設談。
> [name=Recca C]

> 上面提到這個資料跟勞委會有關, 而非經濟部. 這個要再確定一下
> [name=Kirby W]

> 這應該是各地方勞工局的權責
> [name=Ronny W]

    - 公司清冊
        - 目前只有每月更新清冊以及針對單一公司查詢的API，沒有完整的清冊
> [https://www.dropbox.com/sh/42oyn4ustp4ilhy/FRQA56UbG0](https://www.dropbox.com/sh/42oyn4ustp4ilhy/FRQA56UbG0) 自力救濟版
> [name=Ronny W]

    - 分公司更新清冊
        - 目前也沒有分公司的更新清冊，不曉得有沒有開新的分公司
- 工廠相關
    - 合法工廠清冊
    - 被抓包非法工廠清冊
    - 台灣各工業園區/科學園區進駐廠商
    -  台灣工業區/科學園區開發計畫
- 政治獻金相關
    - 誰提供政治獻金
    - 提供給誰
    - 數量多少
- 電費相關
    - 電費依據為和？
    - 過去台電支出/收入表
    - 未來預計變化

- 希望經濟部說明「廢核」與「電費」關聯性時，應同時公布完整的「計算式」和「計算所依據的資料來源」(包含資料出處的網頁連結或原始檔)，供人民檢視其合理性

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0b99967c3a7d7af74500195227674644)
圖片來源：經濟部穩健檢核網，[http://anuclear-safety.twenergy.org.tw/Download/info_1](http://anuclear-safety.twenergy.org.tw/Download/info_1)


- 油價相關
    - 油價依據為和？
    - 過去中油支出/收入表
    - 未來預計變化
- 自來水相關
    - 歷年工程修整支出表和得標廠商資料
    - 過去水利支出/收入表
    - 未來預計計劃
- 台糖相關
    - 歷年支出／收入表明細
    - 土地買賣資料，資產內容
    - 投資事業細節
- 創業相關
    - 創業有哪一些補助？
    - 歷年中小型公司創業數據
        - 多少公司創業成功
- 國際貿易相關
    - 歷年來報關進出口貨物資料
    - 以公司為單位的進出口申報資料
    - 台紐貿易協定各階段受影響貨物代碼列表(十一碼貨物代碼)
    - 台新貿易協定各階段受影響貨物代碼列表(十一碼貨物代碼)
    - 台灣出口貨物在世界各國被查扣統計記錄
    - 台灣查扣他國進口貨數數字
- 過去工業生產統計
參考 [https://www.moea.gov.tw/Mns/populace/news/News.aspx?kind=1&menu\_id=40&news\_id=35635](https://www.moea.gov.tw/Mns/populace/news/News.aspx?kind=1&menu_id=40&news_id=35635)
建議做成api形式，方便後續網頁發展

- 過去商業營業額統計
參考 [https://www.moea.gov.tw/Mns/populace/news/News.aspx?kind=1&menu\_id=40&news\_id=35628](https://www.moea.gov.tw/Mns/populace/news/News.aspx?kind=1&menu_id=40&news_id=35628)
建議做成api形式，方便後續網頁發展
- 過去物價統計
> 我不是很確定經濟部這邊對於物價的統計方式，拋磚引玉，希望大家提供更好想法。
> [name=Recca C]


- 水利署
    - 淹水潛勢圖說是 shp 格式, 可是解開壓縮後看到的是 mxd 格式? mxd 似乎一定要有 ArcGIS 才能開(不對的話請糾正) 如果可以的話也轉個 shp 檔一起給?
        - [http://www.dprc.ncku.edu.tw/download/index.html](http://www.dprc.ncku.edu.tw/download/index.html)
    - 河川水位警戒, 洩洪警戒, 枯旱警戒及水庫蓄水統計等資訊可提供 json 檔, 以便應用在農業相關專案
        - 水位: [http://fhy.wra.gov.tw/pub\_web\_2011/map/River.aspx?cno=1](http://fhy.wra.gov.tw/pub_web_2011/map/River.aspx?cno=1)
        - 洩洪: [http://fhy.wra.gov.tw/pub\_web\_2011/Page/Reservoir.aspx](http://fhy.wra.gov.tw/pub_web_2011/Page/Reservoir.aspx)
> 洩洪警戒未來可以和水保局的土石流警戒結合
> [name=曼 奧]

        - 枯旱: [http://fhy.wra.gov.tw/pub\_web\_2011/Page/Water_Status.aspx](http://fhy.wra.gov.tw/pub_web_2011/Page/Water_Status.aspx)
        - 水庫蓄水量: [http://e-river.wra.gov.tw/Hydrological.aspx](http://e-river.wra.gov.tw/Hydrological.aspx)
            - 能否同時提供歷年資訊?
        - 地下水與地層下陷相關資料
        - 有些資料似乎有提供 kml 檔(例如水庫), 但是無法正確取得, 例如此頁顯示 "找不到網路路徑。":
            - [http://fhy.wra.gov.tw/DMCHY/DES/KMLFiles/ReservoirsStations.kml](http://fhy.wra.gov.tw/DMCHY/DES/KMLFiles/ReservoirsStations.kml)
    - 河川流域圖等圖資
        - 在這邊有看到河川流域與 google maps 的套疊, 不曉得是否有河川流域的 shp 檔?
            - [http://fhy.wra.gov.tw/Pub\_Web\_2011/Map/FloodM.aspx](http://fhy.wra.gov.tw/Pub_Web_2011/Map/FloodM.aspx)
            - 水利署地理資訊倉儲中心似乎有, 但好像要是政府機構的計劃才能申請使用. (請見下圖的計劃主辦欄位) 若是在TGOS 尋找, 似乎還是會導回此頁 ( [http://goo.gl/1dy0bD](http://goo.gl/1dy0bD) ). 另, 水利署倉儲中心往 TGOS 的連結已經失效了: [http://gic.wra.gov.tw/gic/ApplyWeb/Other_TGOS.aspx](http://gic.wra.gov.tw/gic/ApplyWeb/Other_TGOS.aspx)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_edbf5b7f2de2f39d0ebb834d5d1e6965)
                - 如果已經有開放了, 若能降低圖層取得的難度 (減少其曲折離奇度) 也是件很好的事
- 能源局
    - 能源局有許多不錯的資料, 例如歷年油價或液化石油氣參考價格:
        - [http://web3.moeaboe.gov.tw/oil102/oil1022010/A01/A0107/allcpcoil.asp?](http://web3.moeaboe.gov.tw/oil102/oil1022010/A01/A0107/allcpcoil.asp?)
        - 但目前大多是用html 大表格提供, 可以考慮固定規格後提供 raw data, xml 或是 json 格式檔案
- 智慧財產局
    - 現在open 的data
        - [http://data.gov.tw/taxonomy/term/453](http://data.gov.tw/taxonomy/term/453)
    - 專利資訊檢索系統
        - [http://twpat.tipo.gov.tw/](http://twpat.tipo.gov.tw/)
        - 現在只有數量統計
    - 專利公開資訊查詢
        - [https://tiponet.tipo.gov.tw/S090/UC090-C06/InquiryPatentCaseCensorInfo.do?VTFjMWVHUlhiSGxsVmtKb1pFZFdkV1JGV25saU1qQTVUVkVsTTBRbE0wUXIr](https://tiponet.tipo.gov.tw/S090/UC090-C06/InquiryPatentCaseCensorInfo.do?VTFjMWVHUlhiSGxsVmtKb1pFZFdkV1JGV25saU1qQTVUVkVsTTBRbE0wUXIr)
    - 專利名詞中英對照
        - [http://paterm.tipo.gov.tw/IPOTechTerm/doIPOTechTermIndex.do](http://paterm.tipo.gov.tw/IPOTechTerm/doIPOTechTermIndex.do)

- 中央地質調查所
    - 斷層，順向坡，土石流，地質，鑽井等等的，有些似乎有 WMS 可以用，但授權是如何呢？有些似乎要取得 session 才能使用，等於要登入才能用嗎？例如下面連結, 可看到 SESSION 關鍵字:
        - [http://fault.moeacgs.gov.tw/mapguide/mapagent/mapagent.fcgi?OPERATION=GETDYNAMICMAPOVERLAYIMAGE&FORMAT=PNG&VERSION=2.1.0&SESSION=6cfbe0a8-541a-1031-8000-0025b324aa80\_tw\_D](http://fault.moeacgs.gov.tw/mapguide/mapagent/mapagent.fcgi?OPERATION=GETDYNAMICMAPOVERLAYIMAGE&FORMAT=PNG&VERSION=2.1.0&SESSION=6cfbe0a8-541a-1031-8000-0025b324aa80_tw_D) ... 後略
            - 上面這個是斷層的 WMS, 但似乎有另外的來源, 例如下面:
                - [http://gwh.moeacgs.gov.tw/geo4oracle/mapagent/mapagent.fcgi](http://gwh.moeacgs.gov.tw/geo4oracle/mapagent/mapagent.fcgi) ... (中略) ... LAYERS=,WMS/LAYER/TW/G97\_TW\_B1\_L\_2013F ... (後略)
- 路況相關
    - 目前僅由警察廣播電台提供網頁資訊，建議做成api形式，方便後續網頁發展
        - [http://www.pbs.gov.tw/index.aspx](http://www.pbs.gov.tw/index.aspx)

- 政策宣傳支出相關

       預算法第 62-1 條：「基於行政中立、維護新聞自由及人民權益，政府各機關暨公營事業、政府捐助基金百分之五十以上成立之財團法人及政府轉投資資本百分之五十以上事業，【編列預算辦理政策宣導】，應明確標示其為【廣告】且揭示辦理或贊助機關、單位名稱，並【不得以置入性行銷方式進行】。」
       經濟部所屬各單位，目前雖有公布「政策宣導廣告」每月明細表，但均以pdf格式分月呈現，須逐一點開檔案，不易查詢比對；且無法連結到廣告內容。希望未來更改政策宣傳費用「公開的格式(改為較容易看出長期支出狀況的呈現方式)」並連結到「廣告內容」，讓人民容易瞭解政府用稅金購買何種政策宣傳內容？有無置入性行銷？




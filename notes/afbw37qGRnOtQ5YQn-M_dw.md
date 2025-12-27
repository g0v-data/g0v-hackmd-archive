---
tags: disaster,
---

# 防災開放資料應用案例蒐集

> [http://hackfoldr.org/OpenGeoData](http://hackfoldr.org/OpenGeoData)

## 應用試作


### 假設情境


### 所需圖資

- 災前空照圖，判別有人居住的位置  （人口稠密區圖層）
- 全台警局（ex [全台警察局電話, 地址, 經緯度.](https://github.com/yutin1987/police/tree/master/result)）
- 全台消防局位址
- 公園、平面停車場、學校、活動中心等避難場所位置（臨時疏散避難地點）
- 醫療院所位置(臨時醫療站)
- 緊急供水點
- 物資機具集結地點
- 道路圖層（國道、省道、縣道、產業道路）
- 社福機構與收容狀況的資料
    - [新北市失能老人日間照顧(護)委託服務單位](http://data.ntpc.gov.tw/od/detail?oid=7A68F8D4-FEC5-4930-9B40-3BEE33F39289) (新北市社會局所提供的失能老人照護資源說明主要提供欄位包含序號、名稱、地址、電話、服務對象、服務方式)

### 防災圖資雲

- [_圖資雲_](http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CB0QFjAA&url=http%3A%2F%2Fwww.moi.gov.tw%2Ffiles%2Fmoi_note_file%2Ftcc_file_171.pdf&ei=1F3zU74vx-jwBZyvgqgB&usg=AFQjCNGk9-UT5rI0vqjQIIBZ51_81dYFdg&sig2=5b1gISOBI-pUe4mIW0g0Eg)的願景與應用情境 \- 內政部


## 災害情境說明

- 在災前、災中、災後階段，找出需要政府開放哪些資料
- 預期產出
    - 產出所需圖資列表。
    - 設定架構、列舉對應窗口。
    - 而非開發應用雛型或商業化。
- 災害種類，依據『災害防救法』第三條及中央災害防救會報規定，台灣地區各種災害的中央災害防救業務主管機關分別如下：
        1.風災、震災、重大火災、爆炸災害：==內政部==。
        2\. 水災、旱災、公用氣體與油料管線、輸電線路災害：==經濟部==。
        3.寒害、土石流災害：==行政院農業委員會==。
        4.空難、海難與路上交通事故：==交通部==。
        5.毒性化學物質災害：==行政院環境保護署==。
        6.輻射災害：==行政院原子能委員會==。
        7.生物病源災害：==行政院衛生署==。
        也可參考整理中的[台灣災害列表](https://docs.google.com/spreadsheets/d/1p0DNKBt4oNfDBgHv4ZXH-vu0bJ_PtxFFXCL7o4O_Cxo/edit#gid=1880470801)
- Emergency Management 災害管理的螺旋結構
    - Mitigation 減災
    - Preparedness 事前整備
    - Response 應變
    - Recovery 復原重建
![](https://hackpad-attachments.imgix.net/hackpad.com_LKgdTOFMlpD_p.208757_1417211641641_2014-11-29%2005%2052%2002.png?fit=max&w=882)

- 都市防災議題 (北科大 土木與防災研究所 都市防災 課程講議)
1.  台灣常見之天然與人為災害：颱風、水災、坡地災害、旱災、地震、產業災害、火災
2.  災害特性
    1.  發生與影響不確定性
    2.  過程具動態與持續性
    3.  空間與時間性
    4.  複雜與複合性
    5.  資源統合與決策急迫性
3.  都市災害特性
    1.  空間性
    2.  時間性
    3.  連鎖性
    4.  複合性
    5.  雙元性，例如看似已建立機制，但若機制僵化無彈性，反而也容易演變成大的災害
4.  時間面向：災害發生 包含 混亂期、避難行動、 避難救援、 避難生活、 重整期
5.  空間面向：六大防救災空間
    1.  避難：緊急避難 臨時避難 臨時收容 中長期收容
    2.  道路：緊急道路 救援道路 消防道路 輔助道路
    3.  消防
    4.  醫療：緊急醫療站  責任區及特定緊急傷病患指定後送醫院區域(一般 中度 重度)
    5.  物資
    6.  警察
6.  都市防災規劃流程
    1.  環境災害資料庫建置
    2.  防災空間規劃指導原則（地震災害為主 淹水災害為輔 ）
    3.  規劃範圍選定（行政區域、都市計畫區域、人口集中區域或密集發展區）
    4.  防災資源及限制分析（歷史災害 潛勢區域 風險區域）（防災限制因素）
    5.  災損模擬（haz taiwan teles 災害損失推估）
    6.  地區防災空間系統劃設（防災避難圈、救災動線系統、防災據點）
    7.  防災力評估與檢討
    8.  擬定都市防災建設計畫
    9.  落實都市防災建設計畫
    10.  安全都市
7.  防災實質規劃
    1.  潛勢區域管制：洪氾地區、土壤液化地區、地盤下陷地區、潛感山坡地
    2.  實質規劃：縣市區域防災生活圈規劃、鄉鎮區域防災災生活圈規劃、村里區域防災生活圈規劃
    3.  都市計畫與通盤檢討：主要計畫、細部計畫
    4.  防災基盤建設：防災系統建設、都市防火區劃、窳陋地區改善、指揮通信與維生線、地區防災組織
    5.  防災管理與維護：防災設施維護、防災預警監測、緊急應變能力、救援與指揮通信、教育宣導演訓

## 如何運用圖資？災害各階段的操作案例

1.  【Mitigation 減災、Preparedness 事前整備】災害發生前/減緩災害衝擊
2.  【Response 應變】已知災害即將發生/預警/緊急避難/救難/救援/臨時安置/暫時安頓
3.  【Recovery 復原重建】生計/社會重建/地域再生/產業輔導/土地規劃

### 【Mitigation 減災、Preparedness 事前整備】

災害發生前/減緩災害衝擊

- 學術研究｜**都市生活圈防災規劃原則**之研究 --以士林生活圈為例--
    - 論文下載：[http://goo.gl/DYtLTu](http://goo.gl/DYtLTu)
    - 都市防災是必須融合於都市計畫與都市設計領域中的，而針對防災之研究，必須由人民日常生活基礎做起，由生活圈內，規劃一個可自救、自助、自主之安全空間，進而達到防災生活圈之確立。透過各個安全防災生活圈之結合，才有建立安全都市之可能。**士林生活圈除了存在精采的歷史故事及都市空間紋理外，隨著時間演變及都市擴張之腳步，卻也產生了一些易致災害的更新地區及新的都市角色定位課題，若缺乏防災檢討及生活圈防災規劃設計，對於政府所給予的都市發展願景，恐怕難以實現。**而針對既成都市如何建構為安全都市以利永續發展，可謂當前國內重要之防災課題。本研究希望由小處著手，在都市生活圈的領域內，透過防災規劃之原則檢討，提出士林生活圈防災規劃之建議。並思索如何在災害未發生之平時，就能達到「減災」之目的，經由安全防災、都市計畫、都市設計、都市更新之考量達成士林生活圈之發展願景。本研究之目的如下：
        - 一、藉此研究檢討目前台北市士林生活圈之防災計畫是否落實，同時根據實地調查分析檢視當地防災課題，提出相對規劃對策，以提供政府研擬相關都市防災計畫之參考。
        - 二、依照相關文獻統整出都市生活圈防災架構，進而應用於既成都市之防災檢討，作為都市計畫通盤檢討變更之參考。
        - 三、使地方政府於執行都市計畫通盤檢討、都市更新或擴大都市計畫時，能將防災觀念落實於都市計畫、都市設計及都市更新內。
    - → 所用圖資：都市計畫書圖、建築執照、地質資料、人口分布...

- 學術研究｜地震災害-效益分析於土地使用規劃之應用應用 HAZ-Taiwan 系統
    - 網址：[http://ntur.lib.ntu.edu.tw/bitstream/246246/120268/1/](http://ntur.lib.ntu.edu.tw/bitstream/246246/120268/1/)
    - 摘要：本文主要目的在提出一套分析地震災害危險度與風險的方法，供規劃者評估地區災害風險 現況與不同土地使用方案潛在的風險–效益。文中應用國科會與經濟部合作開發的HAZ-Taiwan 系統，以土地使用計畫圖與地震風險機率模型，進行台北市士林區的地震潛勢、危險度與風險 分析。從設定之三個地震事件中，發現士林區之西南、西與南部區域為地震危險度與風險較高 之區域，三個地震事件平均估計總經濟損失約為1,137億元，年預期平均損失約為0.77億元。另 亦估計不同土地使用方案(圖)的地震風險–效益，成果顯示通盤檢討案較原方案，可平均降低 損失風險86億元(約降低總暴露價值之4.39%)。透過HAZ-Taiwan，可有效建立地震災害風險圖 及風險–效益評估方法，提供規劃者評估土地使用計畫與社區地震風險，以避免不妥適的規劃 行為。
    - → 所用圖資：

- 學術研究｜整合地理資訊系統與資料探勘技術於都會區複合性災害境況模擬之研究
    - 文件：[http://ppt.cc/1EURC](http://ppt.cc/1EURC)
    - 說明：臺灣位處環太平洋地震帶的海島環境，生活周遭常面臨颱洪侵襲、坡地坍滑、地震等天然災害。面對上 述致災因子，甚而複合性災害所帶來的威脅，將造成政府及人民財產損失並危害生命安全。臺北市為臺灣政 經首都且人口密度高，在既有之都市防災作業中，考慮複合型災害或極端性氣候下之災害防救作業，貴為當 前急需處理的首要議題。本文針對臺北市面臨強降雨量與周圍潛勢斷層，擬定四十八個複合性災害情境，透過水文、淹水分析成果與 TELES (Taiwan Earthquake Loss Estimation System)地震潛勢分析理論，進行臺北市 各行政區的複合性災害潛勢圖層套疊與避難人數評估。分析結果依資料呈現方式可區分為災前靜態的災害潛 勢圖與收容能量評估表，係以潛勢圖層進行地理資訊系统的空間與數據套疊，並結合市府目前規劃之臨時避 難場所進行收容能量的評估；在災時動態的避難人數推估曲線，為藉由資料探勘技術建構之模式預測成果繪 製而得，可即時推算臺北市各行政區遭受複合性災害時的避難人數與容受力。文末則提出結論與建議，期供 相關單位作為災害防救決策資訊之依據。
    - → 所用圖資：

- 學術研究｜鄉鎮市區層級安全管理與空間規劃分析 —以基隆市七堵區為例
    - 網址：？
    - 摘要：依據災害防救法，現行災害防救體系分為中央、縣市與鄉鎮市區公所三層級，其中鄉鎮市區層級是處理災害防救事宜的第一線，防救災任務包括：核定各該鄉（鎮、市、區）地區災害防救計畫、核定重要災害防救措施及對策、推動疏散收容安置、災情通報、災後緊急搶通、環境清理等災害緊急應變及整備措施、推動社區災害防救事宜與其他依法令規定事項，但相對地鄉鎮市區層級災害防救專職人員缺乏，因此如何從災害規模設定、潛勢資料應用、疏散避難規劃與防救災空間調查分析，協助鄉鎮市區層級進行災害防救對策之擬定是專家學者關注的重點課題，本文利用三維地理資訊系統進行土石流、水災潛勢區與防救災空間設施、設備與資源的關聯分析，結合組織、環境、行為與資源四個面向，分析與探討鄉鎮市區層級推動災害防救、安全管理的工作任務以及相關的注意事項。關鍵詞：安全管理、災害潛勢、災害防救
    - → 所用圖資：

- 學術研究｜都市計畫通盤檢討有關防災作業程序及設計準則研擬
    - 成果下載：[http://www.abri.gov.tw/tw/research/show/70/p/print](http://www.abri.gov.tw/tw/research/show/70/p/print)
    - 說明：[https://www.facebook.com/media/set/?set=oa.1671175353132700&type=1](https://www.facebook.com/media/set/?set=oa.1671175353132700&type=1)
    - → 所用圖資：

- 學術研究｜Critical Infrastructures (CIrcle) - City of Cork, Ireland
    - 文件：
        - 摘要文件：[http://publications.deltares.nl/EP3501.pdf](http://publications.deltares.nl/EP3501.pdf)
        - Flood vulnerability of critical infrastructure in Cork, Ireland：[https://www.e3s-conferences.org/articles/e3sconf/abs/2016/02/e3sconf\_flood2016\_07005/e3sconf\_flood2016\_07005.html](https://www.e3s-conferences.org/articles/e3sconf/abs/2016/02/e3sconf_flood2016_07005/e3sconf_flood2016_07005.html)
    - 說明：In a workshop with the Deltares CIrcle tools, stakeholders shared their expert knowledge on Critical Infrastructure networks in the area of the City of Cork, Ireland. The results of that session included flood vulnerabilities and possible cascading effects between different networks, for a 1/100 years flood event and a 1/1000 years flood event. This video shows that the 3D Interactive Modelling environment of CIrcle will increase understanding of Critical Infrastructure interdependencies. It is easy to play with the data, find the weak spots and test the effectiveness of protection. The CIrcle tool can be used stand-alone, using static flood inundation maps, or in combination with flood simulation software, such as Delft3D Flexible Mesh (Delft3D FM) with full 3D interactive modelling functionality.
    - 演示動畫：[https://www.youtube.com/watch?v=9tISZo8cmMY](https://www.youtube.com/watch?v=9tISZo8cmMY)
    - → 所用圖資：OpenStreetMap Data



- 學術研究｜**多元性區域環境風險評估**：以陽明山國家公園為例
    - 論文下載：[http://goo.gl/8P71Xe](http://goo.gl/8P71Xe)
    - 說明：本研究試圖建立一套評估方法，可納入多危險源、多空間單元、多受體、多元暴露及民眾對於災害的風險知覺，以進行綜合性的區域環境風險評估。並透過陽明山國家公園之案例分析，應用歷史資料、遙測資料、實地調查資料，及地理資訊系統技術處理，進行整體性的區域環境風險評估。
    - → 所用圖資：
![](https://hackpad-attachments.imgix.net/osmtw.hackpad.com_LKgdTOFMlpD_p.208757_1434938786094_IMG_1215.JPG?fit=max&w=882)
![](https://hackpad-attachments.imgix.net/osmtw.hackpad.com_LKgdTOFMlpD_p.208757_1434938801931_IMG_1216.JPG?fit=max&w=882)

- 學術研究｜跨領域地震災害風險探析：集集地震的物理與社會致災因素
    - 論文下載：[https://goo.gl/fMBoCL](https://goo.gl/fMBoCL)
    - 說明：在聯合國國際減災辦公室及政府間氣候變遷小組所定義的風險分析架構上，本研究將地震風險視為地震危害度(hazard)、人口-建物暴露性(exposure)與脆弱性(vulnerability)的總體函數。以集集地震數據作為分析案例，我們整合了人口、房屋稅、所得稅、強地動與集集地震各村里死亡人數的數據，並透過建立四個嵌套(nested)統計模型，以Poisson迴歸模型進行估計，分別檢測代表危害度、暴露性與脆弱性之不同變量及其交互項變量，對地震死亡人數的影響。研究結果顯示，模型中所有變量對於地震死亡人數都具有統計上顯著的效應，其中地震的災害變量與人口建物暴露變量的效果最為顯著，震動強度、斷層經過與集合式住宅倒塌三者的交互作用，是造成集集地震死亡的首要因素。和這些變量相較下，社會脆弱性的變量(性別比、幼年人口、家戶所得、所得標準差)雖然較弱，但有顯著的邊際效用，會擴大地震死亡人數。在學術價值上，本研究突顯跨領域理論與數據整合，對於分析與理解地震災難風險的重要性。在社會實務上，本研究建議應強化都市規劃、區域計畫、建築法規與社會扶助等機制，以降低對地震災害的暴險率與社會脆弱性。關鍵字：地震風險、脆弱性、集集地震、集合式住宅、都市規劃
    - → 所用圖資：

- 學術研究｜颱洪災害之**整合性脆弱度評估**－大甲溪流域之應用 / 洪鴻智、陳令韡
    - 論文下載：[http://goo.gl/9XJbUc](http://goo.gl/9XJbUc)
    - 說明：此研究運用許多與災害議題相關的科學資料、社會統計資料、以及民眾對於災害認知與行動偏好的普查訪談資料，綜合性地提出大甲溪流域的脆弱度（vulnerability）評估指標。其評估成果，實際上可以運用於調整土地使用與都市計畫通盤檢討之規劃，也可以應用於考量社會經濟狀況分佈的災害應變與整備，以及地區安全願景共識的凝聚。
![](https://hackpad-attachments.imgix.net/hackpad.com_LKgdTOFMlpD_p.208757_1419712038692_2014-12-24%2011%2009%2043.png?fit=max&w=882)
    - → 所用圖資：
![](https://hackpad-attachments.imgix.net/hackpad.com_LKgdTOFMlpD_p.208757_1419387529558_2014-12-24%2010%2018%2007.png?fit=max&w=882)


- 學術研究｜埤塘做為氣候變遷下水災調適工具之可行性研究
    - 網址：[http://grbsearch.stpi.narl.org.tw/GRB\_Search/grb/show\_report.jsp?id=2328754](http://grbsearch.stpi.narl.org.tw/GRB_Search/grb/show_report.jsp?id=2328754)
    - 說明：
    - → 所用圖資：
        - 埤塘圖資
        - 河川圖、
        - 行政區圖
        - 高程 DTM 圖
        - 潮位觀測站之潮位觀測資料

- 評估分析｜水災危險度、脆弱度與風險地圖 製作技術手冊
    - 網址：[https://goo.gl/C7zl82](https://goo.gl/C7zl82)
    - 說明：水災危險度、脆弱度及風險地圖之製作流程共 分 10 個程序，包括：資料蒐集、淹水潛勢模擬、脆弱度因子分類、危險度 因子分級、脆弱度因子分級、權重訂定、危險度等級計算、脆弱度等級計 算、水災風險等級計算，及水災危險度、脆弱度、風險地圖繪製。本手冊說明生命面向及財產面向對應於各步驟所採用之資料及計算方法，並且配合天然災害緊急應變之作業需求，本流程所產製之水災危險度、脆弱度及風險地圖係以村里為單位作為圖資之最小尺度供民眾及防災單位參考。
    - → 所用圖資：
        - 地文與水文資料
            - 土地利用 內政部國土測繪中心
            - 數值高程 1.縣市政府 2.內政部地政司
            - 潮位 1.中央氣象局 2.水利署
            - 雨量 1.中央氣象局 2.水利署
            - 河道斷面與堤防 1.河川局 2.水利規劃試驗所
        - 社會經濟資料
            - 村里人口數  縣市政府民政局(處)
            - 村里小孩數(14 歲以下) 縣市政府民政局(處)
            - 村里老人數(65 歲以上)  縣市政府民政局(處)
            - 身心障礙人數 縣市政府社會局(處)
            - 消防隊所在村里 縣市政府消防局
            - 樓層及地下室數目 1.稅捐稽徵處 2.縣市政府稅務局
            - 土地利用 內政部國土測繪中心
            - 河海區排距離  經濟部水利署
            - 水災損失曲線 經濟部水利署
            - 鄉鎮移動式抽水機  經濟部水利署
            - 綜合所得稅-實徵數 國稅局
            - 縣市平均每戶可支配所得 行政院主計處
            - 縣市經常收支賸餘 行政院主計處

- 評估分析｜高雄市火災風險地圖
    - 新聞：[http://www.chinatimes.com/newspapers/20161023000325-260102](http://www.chinatimes.com/newspapers/20161023000325-260102)
    - 說明：高雄市火災風險地圖是根據政府跨局處數據，包括稅捐稽徵處、社會局、消防局等提供有關房屋建照、所得資料、屋齡，獨居長者、中低收入戶居住區及火災傷亡人數等，透過資料科學模型「快篩」而來。
    - → 所用圖資：

- 學術研究｜火災風險下的社區調適策略：以林明社區為例
    - 網址：[http://goo.gl/S7t1JM](http://goo.gl/S7t1JM)
    - 說明：
    - → 所用圖資：

- [http://ntur.lib.ntu.edu.tw/handle/246246/112440#.WJWBwtxjeEc?&&layout.style=default](http://ntur.lib.ntu.edu.tw/handle/246246/112440#.WJWBwtxjeEc?&&layout.style=default)

- 學術研究｜古地名與災害 / 神話 / 習俗
    - 專案討論網址：[https://g0v.hackpad.com/4rF7N2Ihf5r](https://g0v.hackpad.com/4rF7N2Ihf5r)
    - 說明：透過群眾參與的方式，將地方災害經驗、文化祭祀中的災害描述、地名所隱含的環境潛勢 ...等，進行彙整與釐清，作為地區防救災之歷史資料。
    - → 所用圖資：[日治時期臺灣堡圖資料](http://gis210.sinica.edu.tw/website/htwn/viewer.htm)、[http://publicdomain.tw/](http://publicdomain.tw/)、文化部...

- 學術研究｜臺灣國土容受力分析與調適策略之探討
    - 說明網頁：[http://www.cpami.gov.tw/chinese/index.php?option=com_content&view=article&id=17805&Itemid=76](http://www.cpami.gov.tw/chinese/index.php?option=com_content&view=article&id=17805&Itemid=76)
    - → 所用圖資：
![](https://hackpad-attachments.imgix.net/osmtw.hackpad.com_LKgdTOFMlpD_p.208757_1456859505339_%E8%87%BA%E7%81%A3%E5%9C%8B%E5%9C%9F%E5%AE%B9%E5%8F%97%E5%8A%9B%E5%88%86%E6%9E%90%E8%88%87%E8%AA%BF%E9%81%A9%E7%AD%96%E7%95%A5%E4%B9%8B%E6%8E%A2%E8%A8%8E%202.jpg?fit=max&w=882)

- 評估分析｜台灣地震損失評估系統
    - 網站：[http://teles.ncree.org.tw/](http://teles.ncree.org.tw/)
    - 說明：
    - → 所用圖資：建築執照、...

- 評估分析｜颱洪淹水雲端系統
    - [新聞](http://www.chinatimes.com/newspapers/20141128000154-260210)
    - 說明：此系統可以協助洪氾保險的擬訂、災情受損評估 ...
    - → 所用圖資：

- 評估分析｜ FEWS_Taiwan
    - 網站：[https://plus.google.com/117804316605140411553](https://plus.google.com/117804316605140411553)
    - 說明：協助洪水預報 水情資訊供應
    - → 所用圖資：土地利用、通用版電子地圖、土壤類型、數值高程模型、水位站圖層、雨量站圖層、村里圖層

- 評估分析｜大臺北地區大規模地震衝擊情境之災害潛勢與建物人員災損分析
    - 文件：[http://digitaiwan.com/docs/References/20140200.pdf](http://digitaiwan.com/docs/References/20140200.pdf)
    - → 所用圖資：
![](https://hackpad-attachments.imgix.net/osmtw.hackpad.com_LKgdTOFMlpD_p.208757_1463830770605_9898.JPG?fit=max&w=882)
![](https://hackpad-attachments.imgix.net/osmtw.hackpad.com_LKgdTOFMlpD_p.208757_1463832583441_%E5%A4%A7%E5%8F%B0%E5%8C%97%E4%BA%BA%E5%8F%A3%E7%8F%BE%E6%B3%8116.JPG?fit=max&w=882)

- 評估分析｜關鍵設施災害脆弱度評估與風險管理
    - 文件：[http://goo.gl/os9Y4A](http://goo.gl/os9Y4A)
    - 說明：
    - → 所用圖資：

- 評估分析｜由921大地震經驗建立建物震害危險度評估模式及都市防災系統
    - 文件：[http://921kb.sinica.edu.tw/archive/nsc/eidc/1/t8.html](http://921kb.sinica.edu.tw/archive/nsc/eidc/1/t8.html)
    - 說明：本研究由震害危險度評估及都市防災相關研究，探討建物災害原因與都市防災體系。依921災害調查報告之竹山鎮資料，選擇建物毀損程度相關因子，共有與最近水系距離、土壤厚度、建物構造類別、樓層數、建造年代、使用用途、平面形狀、底層挑高及屋頂加蓋等九大評估因子，然後以羅吉特迴歸分析，建立評估模式；再而應用於台南市東區部分地區，其原因乃二地皆於距離斷層二公里內及建物型態相似之相同特性，求出可能受損建物分佈及戶數，依其可能受害人數擬定都市避難據點、醫療、警察、消防、物資及救災避難道路等都市防災系統。
    - → 所用圖資：

- 評估分析｜氣候變遷衝擊下災害風險地圖
    - 網站：[http://dmip.tw/Lthree/home.aspx](http://dmip.tw/Lthree/home.aspx)
    - 說明：本研究藉由定義災害風險與建立評估風險圖評估流程， 建立臺灣氣候變遷衝擊下災害風險圖，研究中分析近未來與世紀末兩個推估時期 下，淹水、海岸、乾旱與坡地災害風險圖。風險圖是由危害度指標與脆弱度指標 所組成，氣候變遷情境資料是採用日本氣象廳模擬之全球環流模式(簡稱 MRI-JMA AGCM 模式)的 20km 網格點資料，配合天氣研究與預報模式系統 (Weather Research and Forecasting Model 簡稱為 WRF 模式)，利用動力降尺度技 術降至至臺灣 5km 之網格點氣候資料，進而應用於評估暴雨發生的頻率(日雨量 超過 350mm 與 600mm 之發生機率)、颱風造成之暴潮衝擊以及乾旱特性，將分 析氣象特性分別作為坡地災害、淹水、海岸與乾旱災害之危害度指標。脆弱度指 標方面則是由環境脆弱度(如淹水潛勢、乾旱特性、平均潮差等)與社會經濟脆弱 度指標(如人口密度、社會發展指標、產值等)所評估。研究中利用地理資訊系統， 評估全台鄉鎮災害風險等級，以展示氣候變遷衝擊下基期(1979~2003)、近未來 (2015~2039)與世紀末(2075~2099)三個推估期下的四種不同災害風險之熱點分布。 未來決策者便可依據此災害風險圖，提出合適的調適策略以降低災害風險。目前 研究中採用單一動力降尺度模式分析氣候變遷衝擊，未來研究將採用統計降尺度 資料，採用合多模式結果並配合天氣合成模式，評估各災害類別之危害度發生的 可能行，以降低目前採用單一模式之不確定性。
    - → 所用圖資：

- 實質政策｜日本東京都綜合危險度分析
    - 網站：[http://www.toshiseibi.metro.tokyo.jp/bosai/chousa_6/home.htm](http://www.toshiseibi.metro.tokyo.jp/bosai/chousa_6/home.htm)
    - 說明：很簡單扼要的從 (1) 建築物倒塌 (2) 火災發生與延燒 (3) 避難困難；三種面向開展與綜合評估的都市危險度分析，且由都市整備局進行此危險度分析，所以相關探討成果也會融入都市改建、街區整備的實質政策中。
    - → 所用圖資：

- 實質政策｜東京都世田谷太子堂二、三丁目防災社區環境營造
    - 網站：[http://www.setagayatm.or.jp/trust/fund/library/taishidou/kyogikai.html](http://www.setagayatm.or.jp/trust/fund/library/taishidou/kyogikai.html)
    - 說明：透過居民參與的環境易致災脆弱度調查與對策工作坊，學者協助社區提出此太子居民版「社區營造中間提案」，並且由市政府接受方案內容，提出太子堂行政版「社區營造計畫」。例如：基於火災、急救的情境，現況的社區巷弄道路狹窄，社區參與者們經過一個調查過程與方案討論，提出對策，如單戶建築改建的時候將庭院空間留設於巷弄道路旁、社區開放空間預留於巷弄路口可以讓救難車輛轉彎無礙
    - → 所用圖資：建築資料、...

- 實質政策｜荷蘭還地於河計畫（Room for the river）
    - 網站：[http://www.ruimtevoorderivier.nl/english/room-for-the-river-programme](http://www.ruimtevoorderivier.nl/english/room-for-the-river-programme)
    - 說明：以科學資料、方案資料，配合基層的溝通工作，公務計畫與利害關係人之間實質交流不同的價值與理念，凝聚還地於河的共識與政策配套措施，[中文介紹](http://www.oranjeexpress.com/2014/03/20/%E6%94%BF%E5%BA%9C%E8%88%87%E4%BA%BA%E6%B0%91%E7%9A%84%E5%B0%8D%E8%A9%B1-%E8%8D%B7%E8%98%ADoverijssel-%E7%A9%BA%E9%96%93%E8%A6%8F%E5%8A%83%E6%A1%88/)。
    - → 所用圖資：氣候變遷相關預測圖資...
![](https://hackpad-attachments.imgix.net/osmtw.hackpad.com_LKgdTOFMlpD_p.208757_1437059878698_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202015-07-16%20%E4%B8%8B%E5%8D%8811.17.17.png?fit=max&w=882)
([Presentation by Robbert Misdorp](https://drive.google.com/folderview?id=0B8DS5uT8SIlKflV2OVpKVDgxemRabWN0ZUVtbDFFdE1SNmJWcmF6U0NvUXA5WTFjU1BnZm8&usp=sharing))

- 演練活動｜世界防災・減災ハッカソン 2/8(土)-9(日)
    - 網站：[http://raceforresilience.org/](http://raceforresilience.org/)
    - 說明：2014年2月、世界銀行 東京防災ハブの立ち上げを記念し、ICTを防災・減災に活用し、イノベーションを推進することを目的とし、グローバル防災・減災アイデアソン・ハッカソンを開催します。
    - → 所用圖資：

- 演練活動｜America's PrepareAthon!
    - 網站：[America's PrepareAthon!](http://www.community.fema.gov/connect.ti/AmericasPrepareathon) / [From Awareness to Action: Making It Easier for Families to Prepare for a Disaster](http://www.huffingtonpost.com/craig-fugate/from-awareness-to-action_b_5804074.html)
    - 說明：
    - → 所用圖資：

- 演練活動｜前進！青蛙隊
    - 網站：[http://kaeru-caravan.jp/](http://kaeru-caravan.jp/)
    - 說明：由大阪市 NPO 法人 Plus Arts，發起「不被稱為防災的防災」活動，結合社區娛樂活動來具體落實防災教育與演練。
    - → 所用圖資：

- 演練活動｜Community Mapping for Exposure in Indonesia
    - 網站：[https://crowdgov.wordpress.com/case-studies/community-mapping-for-exposure-in-indonesia/](https://crowdgov.wordpress.com/case-studies/community-mapping-for-exposure-in-indonesia/)
    - 說明：A priori Disaster Response. The project’s goal was to use OpenStreetMap to collect previously unavailable data, including structural data, for both urban and rural buildings and use the data in appropriate models to estimate the damages in case of a disaster. The combination of these two components and the use of realistic data led to the development of InaSAFE, an open source risk modeling software that can be used for disaster planning, preparedness, and response and for government contingency planning. The main actors in the pilot project were the Indonesian Disaster Management Agency (BNBP), the Australian Agency for International Development (AusAID), the Humanitarian OpenStreetMap Team, the Civil Society Strengthening Scheme (ACCESS), the World Bank, the Global Facility for Disaster Reduction and Recovery, and the crowd—meaning students and local people.
    - → 所用圖資：Satellite Imagery, GPS tracks and attribute data.

- 演練活動｜Storm Surge Protector application
    - 網站：[http://egis.pinellascounty.org/apps/stormsurgeprotector/index.html](http://egis.pinellascounty.org/apps/stormsurgeprotector/index.html)，[文章](http://www.emergencymgmt.com/training/Storm-Surge-App-Makes-Theoretical-Damage-Personal.html)
    - 說明：Pinellas County’s computer app gives people a realistic view of what can happen when a hurricane comes ashore.
    - → 所用圖資：


### 【Response 應變】

已知災害即將發生/預警/緊急避難/救難/救援/臨時安置/暫時安頓

The Joint Decision Model (JDM)
https://m.facebook.com/story.php?story_fbid=10161983516426666&id=624581665

- 地震應變所需空間資訊與精度關係表
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_55de961d01d148cde23795c1679c0c56.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ba503a4fd116053250d255c4dd1c19e6.jpg)

- 洪災應變所需空間資訊與精度關係表
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5a13e2ae0362bdc57ae951087a04f11f.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_327113561792f500facd494242d1ccc6.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_aca6a1aff9b281db0c70cf8c12c0e06c.jpg)

- 內政部研究計畫｜以先進航遙測技術建立災害應變製圖機制先期規劃工作
    - 網站：
    - 說明：應用航拍,UAV,地面光達等技術在災害過後進行災害範圍製圖的測試與流程評估。北科大土木系張哲豪教授。2011 內政部 地政司計畫

- 真實災害｜JKFloodRelief
    - 網站：[http://jkfloodrelief.org/](http://jkfloodrelief.org/)
    - 說明：JKFloodRelief is a volunteer driven relief and data coordination initiative effort responding to the devastating floods in J&K.
    - → 所用圖資：

- 實質政策｜強震即時警報系統 (Earthquake Early Warning System)
    - 網站：[http://eew.ncdr.nat.gov.tw/Research\_and\_development01.html](http://eew.ncdr.nat.gov.tw/Research_and_development01.html)
    - 說明：台灣已擁有超過700座強震測站，為全世界密度最高的強震觀測網，即時測站亦有100餘站，其密度亦與日本相當。中央氣象局在區域警報技術之研發已有豐碩成果，目前可透過電腦網路傳遞警報訊息給使用者進行接收測試，提供地震規模及震央位置、各地震度、S波到達倒數秒數等資訊。
    - → 所用圖資：氣象局測站圖資...

- 實質政策｜NEC 協助內政部消防署提供災時疏散收容資訊
    - 新聞網址：[http://tw.nec.com/zh\_TW/press/201505/tw\_20150508_01.html](http://tw.nec.com/zh_TW/press/201505/tw_20150508_01.html)
    - 說明： 支援防救災整備**期能結合地方基層與企業力量全面進行防救災的整備工作。**內政部消防署於今(8)日舉行「災害防救深耕第2期計畫103年度績優單位示範觀摩及頒獎典禮暨疏散收容系統功能發表會」，由內政部常務次長邱昌嶽表揚參與計畫的績優團隊，並發表NEC所建置防救災雲端資訊系統（EMIC）的「疏散收容系統功能」。因應5月汛期的到來，期能結合地方基層與企業力量全面進行防救災的整備工作。隨著全球暖化與極端氣候的常態化，災害規模不斷擴大，應用雲端智慧強化防救災應變能力已成為各國趨勢。有鑒於此，內政部消防署自2009年起接連展開「災害防救深耕5年中程計畫」、「災害防救深耕第2期計畫」，並委託NEC協助建置防救災雲端資訊系統。此系統目前已整備就緒，將可針對災害應變、調度支援、疏散收容等提供一元化的管理機制，以GIS整合氣象、交通、通訊等資訊，讓政府機關與民眾能於第一時間充份掌握災害情形。本次所發表的「疏散收容系統功能」為防救災雲端資訊系統的一環。當災害發生時，各級災害應變中心的人員能夠運用此一功能對外公布已開設的疏散收容地點，結合「災情報報」系統網頁或APP的推播通知，以一目了然的地圖畫面提供民眾最新的避難安置訊息，並透過電子化管理各地的收容名冊以便親友協尋，同時加速相關單位採取防救災資源的調度措施，確保災害應變與決策的流暢進行。如此一來，民眾在使用災情報報系統時，不僅可利用網頁或APP即時通報災情，迅速查詢全台各地的受災狀況、道路通阻、土石流與淹水的潛勢警戒，也能夠藉由GPS的定位資訊掌握最近的疏散收容場所、聯絡人資訊與可收容人數等，盡速前往緊急避難，進而將災害損失降至最低。
    - → 所用圖資：

- 研究計畫｜台灣都會區現代社會天然災害風險管理和災害識覺之研究-以新北市板橋區水患有效疏散路線規劃為例
    - 文件網址：[https://www.grb.gov.tw/search/planDetail?id=11588260&docId=0](https://www.grb.gov.tw/search/planDetail?id=11588260&docId=0)
    - 說明：

- 技術創新｜The Future of Smart Firefighting: Integrating All the Data
    - 文章網址：[http://www.emergencymgmt.com/safety/The-Future-Smart-Firefighting-Integrating-All-the-Data.html](http://www.emergencymgmt.com/safety/The-Future-Smart-Firefighting-Integrating-All-the-Data.html)
    - 說明：運用 IOT 技術，強化火災應變能力。
    - → 所用圖資：

- 技術創新｜主動備災的智能生活環境與室內地震災情辨識系統
    - 簡報網址：[http://www.openfoundry.org/of/download/openlegal/Open\_Data\_Workshop_2014/odw2014-07.pdf](http://www.openfoundry.org/of/download/openlegal/Open_Data_Workshop_2014/odw2014-07.pdf)
    - 說明：Common Alert Protocol、Image-based Disaster Damage Assessment System, IDEAS、Intelligent Guards against Disasters
    - → 所用圖資：Open BIM data, ...

- 演練活動｜救災演練平台
    - 網站：[http://sim.ushahidi.tw/](http://sim.ushahidi.tw/)
    - 說明：
    - → 所用圖資：

- 演練活動｜レッドベアサバイバルキャンプクラブ
    - 網站：[http://kiito.jp/member/2013/09/02/1157/](http://kiito.jp/member/2013/09/02/1157/)
    - 說明：NPO法人プラス・アーツが中心となり、キャンプを通して、災害時に生き抜く「たくましさ」「2つのソウゾウリョク（創造力と想像力）を養うプログラムを開発・実施しているメンバー。(紅熊生存營，親子共同參加，推動 by 神戶創意設計中心)
    - → 所用圖資：

- 演練活動｜すごい災害訓練DECO
    - 網站：[http://sugoisaigaikunren.org/](http://sugoisaigaikunren.org/)
    - 說明：地域の想定される震災の規模・内容を知る サバイバルスキルを学ぶ 基礎的なファーストエイドや医療サポーターとしてのスキルを学ぶ 地域コミュニティを知る 災害時のリーダーシップやチーム構築について学ぶ IC T スキルを高める
    - → 所用圖資：

- 演練活動｜「避難地形時間地図」（通称：逃げ地図）とは
    - 網站：[http://www.nigechizuproject.com/](http://www.nigechizuproject.com/)
    - 說明：東日本大震災直後、日建設計は東北の建築学生をオープンデスクとして東京に招き、学生とともに被災地のリサーチに取り組みました
    - → 所用圖資：

### 【Recovery 復原重建】

生計/社會重建/地域再生/產業輔導/土地規劃

- 真實災害經驗研究｜由 921 大地震重建經驗探討災前重建 準備計畫之規劃方向 Examining the Planning Directions of Pre-Disaster Reconstruction Preparation in Light of the 921 Earthquake Reconstruction Experience
    - 文件網址：[http://www.ndc.gov.tw/m1.aspx?sNo=0015660#.VYdxFlyqqko](http://www.ndc.gov.tw/m1.aspx?sNo=0015660#.VYdxFlyqqko)
    - 說明：現行災害防救法第 36 條規定，為實施災後復原重建，各級政府應依權責列入災害防救計畫，並鼓勵民間團體與企業協助辦理；公共事業應依其災害 防救業務計畫，實施有關災後復原重建事項。災後重建啟動階段(約災後 1-3 個月)的政策需同時整合各項減災措施，為達減災目標，需事前研擬一套完善災 前重建準備計畫。本研究主要目的係提供平時建構重建規劃機制(災前重建準備)，以利規劃單位於災後重建啟動階段即時啟動重建機制，確保事後重建工作推動的迅速性與即時性，達到各項重建政策的綜合性，同時在重建營造實施期(約災後 6-12 個月)達成有效之居民參與。
        - 關鍵字：大規模震災、災後重建、災前重建準備
        - 回顧相關文獻，彙整災前重建準備計畫之重要工作，應包括
            - 建立重建協調整合機制(合作關係、協調關係)、彙整災民慰助金與救助機制 (居民參與、土地權屬、經費援助、互動模式)、釐清重建工作之權責歸屬(災後檢討)等面向，藉由 921 震災經驗建構災前重 建準備計畫深度訪談，以災前管理角度研提適用我國震災災前重建準備計畫規劃方向，並提供政府部門都市計畫防災規劃之考量。
                - 1.地區資源列冊管理
                - 2.土地資源管理計畫
                - 3.民間協力平台架構
                - 4.瞭解地區災害特性
                - 5.社區資源整合交流
                - 6.地震災害境況模擬
                - 7.國外災害經驗學習
                - 8.防災資訊系統整合
    - → 所用圖資：受損建築物資料？受災戶人口資料？地區特色與產業評估相關資料？...

- 真實災害｜莫拉克風災後，尋找永久屋地區與評估過程的經驗
    - 政策網址：[http://www.cpami.gov.tw/chinese/index.php?option=com_content&view=article&id=14534&Itemid=54](http://www.cpami.gov.tw/chinese/index.php?option=com_content&view=article&id=14534&Itemid=54)
    - 說明：暫不討論永久屋整體政策推動的諸多手法爭議，僅參考「找到一塊比較安全的土地」的推估方法。
    - → 所用圖資：
        - ex 公有土地、國營事業土地的調查與地號，如軍營、台糖土地、農場土地..
        - ex 災害潛勢圖資，確認選址土地是否安全
        - ex 受災戶戶籍資料..
        - ex 公共設施資料..
        - 針對遷居者的生計需求議題，所相關的圖資

- 真實災害重建報導｜ReBuilding Haiti
    - 網站：[ReBuilding Haiti](http://apps.rue89.com/haiti/en/)
    - 說明：Four years after the earthquake, how is Haiti rebuilding itself? If you were part of the process, would you be able to make the right choices? Find out with this multimedia interactive story.
    - → 所用圖資：

- 演練活動｜居民參與的**災前重建**計畫之推動，地域協働復興模擬訓練
    - 網站：[http://www.bousai.metro.tokyo.jp/taisa](http://www.bousai.metro.tokyo.jp/taisa)[…/1000216/1000405.html](http://www.bousai.metro.tokyo.jp/taisaku/1000216/1000405.html)
    - 說明：一旦災難發生，復原重建將涉及許多事務，日本開始推動於災難發生前，模擬復原重建的情境，並提出一些軟硬體方案（貸款、共有財產如何處理、重建情境的土地與建築配置...）
    - → 所用圖資：
    -

- 研究計畫｜大規模震災災前都市重建計畫之規劃
    - 文件網址：[https://www.grb.gov.tw/search/planDetail?id=2003133&docId=0](https://www.grb.gov.tw/search/planDetail?id=2003133&docId=0)
    - 說明：

- 社會分析｜災難治政： 2014 年高雄石化氣爆後的尺度政治與不均地理發展
    - 說明：此論文分析高雄市氣爆後的災難政治發展，本研究田野資料調查與收集的時間（2012 ~ 2015年）跨越了氣爆前後，有助於分析氣爆政治發展的脈絡與歷史。資料收集來自幾個方面：第一，針對高雄市石化產業發展的相關行動者，包括中央經濟部石化產業高值化推動辦公室、高雄市 政府經濟發展局、高雄石化區域的議員、高雄地區石化業業者及居民（具有代表性的意 見領袖）、高雄地區相關學術、研發單位、環保團體之專家學者等，於2012至2015年間，成功地面對面訪談22個樣本，累積有14 萬9,000餘字逐字訪談稿，並參考受訪者所提供的書面資料。第二，在高雄研究所建立的相關基本統計材料以及剪報資料，尤其氣爆後完整的剪報資料，做為多方求證的可信證據，以建構本研究後續分析的基礎。

- 社會分析｜The Displacement Alert Project Map
    - 網站：[http://map.dapmapnyc.org/app/](http://map.dapmapnyc.org/app/#close)[#close](https://g0v.hackpad.tw/ep/search/?q=%23close&via=GNOwtyN7a4O)
    - 說明：Dap.Map is a building-by-building, web-based interactive map for NYC designed to show where residential tenants may be facing significant displacement pressures and where affordable apartments are most threatened. ANHD created Dap.Map to provide community groups, local residents, elected officials, policymakers, and the public direct and real time access to vital information on our city’s rapidly changing residential environment.
    - → 所用圖資：

## 其他

### 空間規劃方法與工具

- [Geodesign Summit Europe 2014: Geodesign for Resiliency](http://geodesignsummit.com/europe/index.html)
- [Planning for safety and managing emergencies](http://blog.3dgis.it/en/390-sirio-civil-protection-geodesign)
- [RISC-KIT](http://www.risckit.eu/np4/home.html) 歐盟 FP7國際合作計畫 分險分析工具
- [賽豬公上太空計畫](http://nspo.g0v.tw/)
- [都市計畫通盤檢討有關防災作業程序及設計準則研擬](http://www.abri.gov.tw/tw/research/show/70/p/print)

### 社群活動

- 禽流感 data jam
- [守護台灣 Open Data & Source 雲端災防應用開發者大賽](https://ossonazure.bhuntr.com/)
- [Geodesign Summit Europe 2014: Geodesign for Resiliency](http://geodesignsummit.com/europe/index.html) / [Planning for safety and managing emergencies](http://blog.3dgis.it/en/390-sirio-civil-protection-geodesign)
- [2014-08-22／民間救災系統交流小聚／台北場](https://g0v.hackpad.com/2014-08-22-WMaKLjBljub)

### 正在建造中的資訊系統

１）[臺灣的用電著色地圖，或是雷同的運用。](https://g0v.hackpad.com/iTzLaacxmov)
２）[2014-08-22／民間救災系統交流小聚／台北場／](https://g0v.hackpad.com/2014-08-22-WMaKLjBljub)


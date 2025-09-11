---
tags: 公有地大行動,公有資產
---

# 臺北市政府公有資產資源平臺構想與實作歷程

說明：本頁面紀錄「公有地大行動」專案關注者，參與臺北市政府所主揪的會議，分享「天龍特公地」網站建置經驗，以及臺北市政府建置「臺北市市有閒置空間整合查詢平台」空間資料處理課題等過程，以及空間活化後政策續行階段。

---
:::info
目錄
[TOC]
:::

## 協作歷程開始

### 20161229 晚餐聚會

- 緣起：臺北市政府代表表示，曾將「[天龍特公地](http://taipei-pop.herokuapp.com/)」網站於青年事務委員會公開展示給市長查看，會議上遂開始討論市府這邊也應該建置類似的平台，故約了一個聚會邀請天龍特公地專案參與者與市府代表交流（見[社團中的邀請貼文](https://www.facebook.com/groups/1417173811903954/permalink/1818320148455983/?pnref=story)）。
- 利益 (食物) 揭露：
    - 出席者 chewei 省了一筆晚餐費，食物含串燒數串、梅酒約 350ml。
- 討論內容簡記：
    - chewei 分享「[天龍特公地](http://taipei-pop.herokuapp.com/)」網站建置大致經驗，包含 g0v 各個參與者所協力的不同環節，至少包含資料整理過程、地圖化呈現、都更資料比對、上傳照片功能、下載單筆 GeoJson 功能、融入 NGO 與社區的觀點提供面積與局處篩選條件、撰寫出倡議文字...等等。
    - 北市府內部各局處在推動局處業務時，也會需要實體的公有空間或公有土地，例如社會局要推動社區照護或社福機構設置、市場處的市場空間活化、都市更新處的 [URS 計畫](http://www.urstaipei.net/about-urs)...等等；也會有空間供給的單位，例如財政局提供低度利用的房舍清單、文化局推動 [藝響空間計畫](https://www.culture.gov.taipei/frontsite/space/artSpaceAction.do?method=doSpaceInfoList&subMenuId=4902) 提供民間文化單位申請使用...等等。
    - 可能的工作方向：
        1.  針對供需資訊交流進行優化，例如運用線上可即時修改的協作網頁彙整空間清單，避免公文時差。
        2.  針對局處活用空間的行政流程環節，構想是否有資料混搭的需求，例如有了空間的位置，能否更即時地掌握其土地使用分區與容許使用的內容為何。
        3.  正面表列民眾端的各種使用需求，例如社區認養空地作為公共開放空間、租用或申請進駐室內空間...等等。
    - 未來推動方式：
        - 由市府端揪聚會，邀請對象至少包含資料使用對象、具有資料處理能力者、市府本議題的推動代表。
        - 資料使用對象可分為「公務員使用情境」與「民眾使用情境」，兩類對象建議可先分流籌辦聚會工作坊。

### 20170120 臺北市財政局會議

時間：1/20(五)上午9時30分
地點：臺北市政府市政大樓8樓中央區財政局討論室
出席單位：青年事務委員會委員數位、財政局、資訊局、民間社群
緣由說明：

會議前發言意見蒐集
- chewei:
    1.  ==釐清公有資產資料產製流程行政啟始端==
        - 財政局所匯整的資料，其原始來源為何？
        - 建築物類的公有資產
            - 就行政上，都發局建管處應該是業務第一線，且有一個建築管理系統，近期系統維護需求計畫書([https://drive.google.com/drive/folders/0B5EFNXxRFP3wRS1FY3pfZUdiUUU](https://drive.google.com/drive/folders/0B5EFNXxRFP3wRS1FY3pfZUdiUUU)) 或許可以整理一些事項，請建管處參與回覆；主要是因為蠻多種類的業務需求需要建管處提供相對應的資料，像是找公有屋頂裝太陽能板、或是社會局要佈點長照機構。
            - 是否能從目前的「建築管理系統」，篩選出公有資產資料？
                - 例如：使用執照、建築執照中，若「起造人、設計人、監造人」欄位內出現公部門單位與人員名稱
            - 非建管部門的市府人員，能否藉由建築管理系統而得到公有資產清單？
                - 例如：建築管理系統依照前述公有資產判斷原則，定期匯出全市公有資產清單
                - 蒐集各局處業務使用需求，除了現有建築管理系統已匯出的資料內容，局處還需要看到什麼才能輔助其業務評估、分析之用？（需求舉例：市府有再生能源推動政策，其中一項措施即於公有建築物裝設太陽能版，這樣的業務需求需要有屋頂形態、屋頂面積、屋頂現況等，另輔以高解析度衛星圖人工判釋。）
            - 以及系統內的資料轉出民間可使用的開放資料時，有沒有缺漏或需要調整
                - 例如：目前針對單一建築物是否有「開放空間」、是否有申請過「容積獎勵」，都必須於資料集內的「注意事項」欄位中，透過關鍵字比對的方式推斷。建議將這類需求新增為獨立欄位。
        - 建築物類與非建築物類的公有資產
            - 就行政上，地籍資料由地政局負責？例如 臺北市不動產數位資料庫 [https://tredb.gov.taipei/2008TPWS/Default.aspx](https://tredb.gov.taipei/2008TPWS/Default.aspx)
            - 是否能從目前的「臺北市不動產數位資料庫」，篩選出公有資產資料？
    2.  ==蒐集各局處業務使用需求==
        - 除了現有的建築與空地資料欄位與內容，局處還需要看到什麼才能輔助其業務評估、分析之用？
        - 參考文件「【閒置空間】各局處提供成功案例、遇到的困難、現有機制不足之處」
            - [https://docs.google.com/document/d/1Ef8YMdTzMuQkKVJEAGKO-19I-FUZnasplaYCrrIUMOU/edit](https://docs.google.com/document/d/1Ef8YMdTzMuQkKVJEAGKO-19I-FUZnasplaYCrrIUMOU/edit)
    3.  ==蒐集民眾端的各種使用需求==，例如社區認養空地作為公共開放空間、租用或申請進駐室內空間...等等。
        - 可透過其它公眾參與場合釐清。

會議內容簡記：
- 財政局現有的公用財產資料網站 [http://www.dof.gov.taipei/mp.asp?mp=10300B](http://www.dof.gov.taipei/mp.asp?mp=10300B)
- 開放資料平台有 閒置或低度利用的建物資料(財政局每半年向各單位調查一次)
- 部分圖資受到 國土測繪成果資料收費標準 規範
```
http://law.moj.gov.tw/LawClass/LawAll.aspx?PCode=D0060114
```
    - 地籍圖要找地政局
    - 建築測量地形圖要找都發局
- chewei
    - 再詢問 DZ1984 的天龍特公地網頁程式碼的授權，確認能否用於市府應用
> 程式碼以 MIT 授權，可自由新增、刪除、修改，以及散佈，請放心使用。
> [name=Donald Z]

> great!
> [name=che l]

    - 整理民間使用公有地的方式

會議後整理出相關議題：
==1. 開放地籍輪廓與建物輪廓資料==
- 建物與地籍輪廓資料開放的議題，這部分與資訊局開放資料業務、各項資料產製來源局處的意向、規費法現況、公參會開放資料組等相關。

==2. 設計更好用的整合查詢系統==
- 財政局列冊低度使用的公產資料，如何在市府內加以活用，如何把各局處找空間的好經驗與不好經驗納入一併探討。是使用介面的生硬、或是還有其他使用上的不便，讓有需求的局處仍需要其他單位協助查找空間而非自主查找並啟動相關行政協調程序。
- 如果低度利用認定其實是各局處自己確認後交給財政局做半年一次的彙整，或許可以構思一個各局處分散式回報的機制，更新上更具即時性。例如台南市所開發的空地空屋管理系統 ( [https://github.com/tainancity/house](https://github.com/tainancity/house) ) 。

==3. 設計更多服務==
- 民間端如何活用公有資產資料，有什麼以資料啟動的空間使用方法。

==4. 公民科技進政府==
- 討論到公民科技與政府採用、採購等機制的可能方式。相關探討可參考 [g0v.taipei fellowship](https://g0v.hackmd.io/9tq3yPW2TtO8dK2sZVVd1w)。

### 20170122 蒐集社群意見

- ==資訊局詢問民間社群意見：還需要什麼資料？預計將會轉達給地政局與都發局==
    - 說明：近期臺北市資訊局，由於公有資產清冊文件，文件中關於地理資訊的描述，僅有「地號」與「地址」，這對於市府同仁查找公有資產的過程來說有些不方便。資訊局預計將與「地政局」及「都發局」召開會議，討論前述的課題，能否透過地籍輪廓資料、建築物輪廓資料等輔助，把清冊文件地圖化。同時，資訊局想詢問民間社群意見：對於「公有資產清冊文件地圖化」這樣的目標，您認為需要什麼資料？歡迎社群朋友回覆您的意見，意見預計蒐集至本週日傍晚，謝謝～
        - 社團討論串：[https://www.facebook.com/groups/1417173811903954/permalink/1829256227362375/](https://www.facebook.com/groups/1417173811903954/permalink/1829256227362375/)
    - ==地號輪廓與建物輪廓==
        - chewei：
            - 針對地號類資料，需要每一筆「地號」與「該地號輪廓 polygon」對應關係
            - 針對建築物類資料，需要每一筆「門牌」與「該門牌所對應的建築物輪廓 polygon」對應關係
            - 若無法採取「臺北市政府資訊開放加值應用規範」釋出，建議先徵詢地政局與都發局，這些輪廓資料，是否先僅作為市府內部公務用途，以便初期能夠將財政局低度利用與閒置公有資產地圖化呈現，輔助市府同仁推動活用閒置公產的業務評估之需求。資料集建議更新頻率為半年一次，主要理由是配合財政局低度利用與閒置資料盤點頻率，也是大約半年。
        - [**Finjon Kiang**](https://www.facebook.com/finjonkiang?fref=ufi)**：**
            - 地號對應的 polygon 在 [http://ccs.land.moi.gov.tw/jsp/HomePageController](http://ccs.land.moi.gov.tw/jsp/HomePageController) 公務部門可以申請 shp 格式的資料進行轉換，地政資料因為規費法限制一般民間需要付費申請 ( [https://www.land.nat.gov.tw/index.asp](https://www.land.nat.gov.tw/index.asp) ) 台南是採取折衷的作法請地政局開放個別地號中心點位 ( [http://data.tainan.gov.tw/dataset/par](http://data.tainan.gov.tw/dataset/par) ) 方便民眾檢索位置資訊，進一步的則還是得申請，除非地方議會同意 (涉及規費法關係)。
            - 門牌與地號的對應其實就目前所知是不完整的，因為門牌是戶政單位負責，過去戶政與地政之間並沒有經常做資料交換與更新，所以可能需要經過資料整理。
    - ==空地空屋管理系統構想==
        - [**Finjon Kiang**](https://www.facebook.com/finjonkiang?fref=ufi)：台南所開發的空地空屋管理系統 ( [https://github.com/tainancity/house](https://github.com/tainancity/house) ) 就是合併門牌與土地資料的應用，也歡迎北市資訊局延伸應用 (welcome fork ?)。
        - chewei：臺北市目前處理低度利用的公有資產，目前是透過 (此業務主責單位) 財政局半年發文一次，詢問各個府內局處是否有低度利用或閒置的空間回報更新資料；台南市的空屋空地管理系統，似乎也很契合這樣的空間資料更新、分散式回報的目標。
    - ==公有資產資料清單欄位建議==
        - 林立哲：該筆資產的管理單位 聯絡方式 目前使用單位 使用方式(租? 租幾年等)

### 20170123 市府資訊局、地政局、建管處會議簡記

- 說明：以下內容為轉告知，並非實際參與會議者的紀錄。
- 會議要點：
    - 地籍輪廓資料
        - 地政局代表表示，地籍輪廓部分，受限於收費規定，無法放到資訊局的資料平台。
        - 但應該可以協助市府業務用途。
            - 由此衍伸課題：國發會與各地方政府目前推動的開放資料與平台，處理符合國際 open data 定義的資料；地籍輪廓資料的部分，現況無法成為符合國際 open data 定義的資料，但市府局處業務上也有使用需求，這類授權屬於公部門業務用途的資料需求，可以持續盤點、確認技術方案上是否可以滿足使用需求。
    - 建築物輪廓資料
        - 建管處代表表示，建築物的輪廓資料，是由都市發展局測量科產製。
        - 需要再進一步了解，都市發展局測量科產製建築物輪廓資料的流程，是否有機會將此資料作為開放資料 open data 釋出。
    - 門牌地址定位
        - 門牌地址定位，與民政局相關。
        - 民間盤點目前的操作方法，參考：
            - [https://g0v.hackpad.com/895ri3v4d41](https://g0v.hackpad.com/895ri3v4d41)
            - [https://g0v.hackpad.com/BWy6nWw2hw4](https://g0v.hackpad.com/BWy6nWw2hw4)
            - [https://www.facebook.com/groups/odtwn/permalink/1437194089628338/](https://www.facebook.com/groups/odtwn/permalink/1437194089628338/)

### 20170223 市府跨局處會議「規劃市有閒置空間整合查詢平台會議」

會議訊息：
- 開會事由:規劃市有閒置空間整合查詢平台會議
- 開會時間:中華民國106年2月23日(星期四)下午4時0分
- 開會地點:市政大樓8樓中央區財政局討論室
- 會議資料與概要：
    - 一、緣起
        - 依本府105年12月26日召開「臺北市青年事務委員會第8次大會」會議紀錄裁示事項七、(一)：「有關建立跨局處『互動式』整合查詢平台議題，請財政局邀請資訊局、王寶萱副主任委員、青委會委員與『天龍特公地網站』相關人員予以協助規劃辦理後續相關事宜，列追蹤3個月。」
        - 為瞭解「天龍特公地網站」現有功能，建立本府閒置空間跨局處「互動式」整合查詢平台。本局前於105年1月20日邀集相關人員召開非正式之討論會議，進行意見交流，並於會議中初步確認將市有閒置房地納入天龍特公地網站開放民眾查詢。會議結論請資訊局邀請地政局、都發局、建管處，參加106年1月23日公民參與委員會開放資料組例會。並請財政局年後（2月初）邀請資訊局、地政局、都發局，開會討論資料授權問題及大松提案分工。
    - 二、討論議題
        - 有關建立市有閒置房地跨局處互動式整合查詢平台後續推動方式為何?
        - 如確定將市有閒置房地資料納入天龍特公地網站開放查詢，地政局之地籍圖資料 及 都市發展局之臺北市歷史圖資展示系統 得否無償提供社群加值使用?
        - 本案倘由青委會於106年3月4日之黑客松(大松)提案，各機關應配合事項?
- 會議前：
    - chewei> 發言輔助簡報線上檔案：[https://goo.gl/1j6IsK](https://goo.gl/1j6IsK)
- 會議內容簡記：
    - 建築資料
        - 都發局歷史地圖系統提供圖磚服務
            - 這部分請都發局與法制局確認使用條款中，與當前開放資料之間是否相容或建議修正
        - 現有的地址門牌資料定位精確度不夠
            - 舊的門牌:工讀生在地圖上標示
            - 新的門牌:GPS定位，比較精確
    - 土地資料
        - 公有土地可以由各管理機關決定是不是開放各自管有的地籍輪廓，再由地政局放上開放資料平台
    - 公私合作的方式
        - 先用可以開放出來的資料到黑客松提案?
            - 公有非公用財產
    - 市府代表前往 g0v 黑客松提案，籌備頁面：[https://hackpad.com/YFjuO1wK9np](https://hackpad.com/YFjuO1wK9np)

### 20170304 g0v黑客松

- 20170304 黑客松成果：[https://goo.gl/rwGF59](https://goo.gl/rwGF59)
    - 1) 公有土地，欄位資料含輪廓
        - [https://gist.github.com/tpe-doit/c71bed6484004b2c52271457a26e6773](https://gist.github.com/tpe-doit/c71bed6484004b2c52271457a26e6773)
    - 2) 公有建築物，欄位資料含輪廓 (感謝 Ronny Wang)
        - [https://gist.github.com/ronnywang/3292e8668594106781bc8db66361fe9f](https://gist.github.com/ronnywang/3292e8668594106781bc8db66361fe9f)
        - 方法概述：建築物門牌 -> 得到經緯度 -\> 比對台北市數值地形圖 shapefile(市府尚未開放的資料) -> 判斷鄰近關係 -> 得到特定門牌及其建物輪廓
    - 3) 當天青委會委員們則整理使用者需求
        - 共筆頁面：[https://goo.gl/0kvVJ1](https://goo.gl/0kvVJ1)
    - 4) fork 天龍特公地網站 (感謝 Ronny Wang 大大協助建置)
        - [http://taitung-fan-182028.middle2.me/](http://taitung-fan-182028.middle2.me/)
- 當日提案過程的報導文章
    - 「零時政府」的第24次黑客松：挖坑和跳坑的派對
        - [https://theinitium.com/article/20170321-notes-g0v-hackson/](https://theinitium.com/article/20170321-notes-g0v-hackson/)

### 20170316 市府會議

會議訊息
- 事由：規劃市有閒置空間整合查詢平台第2次會議
- 開會時間：20170316 (四) 上午 11:30
- 開會地點：臺北市政府市政大樓 5 樓 503 會議室 (位於台北探索館樓上，可詢問一樓櫃台)
- 主持人：臺北市政府財政局局長
- 與會單位者：臺北市政府資訊局、臺北市青年事務委員會委員、臺北市政府財政局資訊室、臺北市政府財政局非公用財產管理科、劉哲瑋君
會議要點
- 市有閒置空間整合查詢平台之建置涉及本府地政局、都市發展局權管地籍圖及地形圖(建物圖層)等數值圖檔之資料開放，請本市青年事務委員會(以下簡稱青委會)委員於青委會第 9 次大會提案就屬市有資產部分之土地及建物可開放上開資料供外界查詢使用。

### 201703 青委會第 9 次大會

- 聽聞有討論此平台 ? 待詢問有參加會議的人

### 201704-05 進度簡記

- \[進度轉述\] 針對台北市公有資產平台構想，目前臺北市政府預計四月至五月初，請資訊局、都發局、地政局依據前陣子所釐清可以開放的公有土地與公有建物資料集項目，將這些項目所對應完整的資料集整理並開放。例如前陣子先透過十來筆資料試作，接下來資料應該就會更為完整。
- \[資料\] 內政部及財政部國有財產署公開經管公有土地，大概約125萬筆資料
    - 資料網址：[http://data.moi.gov.tw/MoiOD/Data/DataDetail.aspx?oid=7EFCAF0A-F102-4E85-9B79-6B4F4A70B0A7](http://data.moi.gov.tw/MoiOD/Data/DataDetail.aspx?oid=7EFCAF0A-F102-4E85-9B79-6B4F4A70B0A7)
    - 地圖初步展示 [https://kiang.github.io/pub_lands/](https://kiang.github.io/pub_lands/)
- \[地政局訊息\] 開放政府─公有土地輕鬆查
    - 本系統使用者得以地號、門牌或直接於地圖上點選查詢各筆土地資訊，如查詢之土地權屬含有公有持分，則於地圖上依公有土地權屬情形顯示顏色，例如紅色為國有、藍色為臺北市有等，並揭示現在的管理機關(如下圖2)，使用者可一次掌握臺北市轄區內各公有土地資訊，除促進閒置公有空地活化，同時使政府施政透明公開，提升民眾生活品質。本系統目前已建置完成，暫僅開放供政府機關使用，地政局已於106年4月19日起函詢臺北市轄區內共計649個公有土地管理機關，將俟各管理機關同意後開放供一般民眾查詢，敬請期待。
    - [http://epaper.land.gov.taipei/Item/Detail/%E9%96%8B%E6%94%BE%E6%94%BF%E5%BA%9C%E2%94%80%E5%85%AC%E6%9C%89%E5%9C%9F%E5%9C%B0%E8%BC%95%E9%AC%86%E6%9F%A5](http://epaper.land.gov.taipei/Item/Detail/%E9%96%8B%E6%94%BE%E6%94%BF%E5%BA%9C%E2%94%80%E5%85%AC%E6%9C%89%E5%9C%9F%E5%9C%B0%E8%BC%95%E9%AC%86%E6%9F%A5)

### 20170511 地政局交流聚會

- 地政局邀請進行交流
- 出席：地政局、資訊局、chewei
- 會議概要：
    - 地政局說明==公有土地專案==
        - 地政局分享目前公有土地資料詢問狀況，已有 70 機關回覆願意展示於地政雲。
        - 預計除了地政雲圖台上可以查找公有土地，同步會將這些機關的「公有土地地號清冊資料」提供至「資料開放平台」。
        - 小提醒：
            - **市有**土地與建物空間的資料，是財政局的權責；
            - **非市有**類，則是地政局業務相關。
    - 地政局說明==智慧生態社區==
        - 地政局目前針對二十處過去推動過地政規劃的地區，期望探討這些地區的公共環境改善。
        - 將運用地政基金來支持可行方案。
        - 這部分還在構思一些圖資與網路介面，可以如何促進與協助。
        - 「智慧生態社區」說明網頁：[https://goo.gl/PUmTiA](https://goo.gl/PUmTiA)
    - chewei
        - 介紹==土地資料展示的網頁==
            - 介紹天龍特公地網頁製作過程 [http://taipei-pop.herokuapp.com/](http://taipei-pop.herokuapp.com/)
            - 介紹紐約 Living Lots NYC [https://livinglotsnyc.org/](https://livinglotsnyc.org/)
        - 介紹==大批空間分析的專案==
            - Philadelphia Has a New Plan for Its 43,000 Vacant Lots
                - 網址：[https://nextcity.org/daily/entry/philadelphia-land-bank-2017-vacant-lots](https://nextcity.org/daily/entry/philadelphia-land-bank-2017-vacant-lots)
                - 標的類型：空地
                - 分析方向：開放空間、社區園圃、綠地、住宅、街區經濟活絡
            - Cook County Land Bank, DePaul Institute for Housing Studies – Abandoned property analytics tool
                - 網址：[http://www.cookcountylandbank.org/data-analytics/](http://www.cookcountylandbank.org/data-analytics/)
                - 標的類型：空屋
                - 分析方向：社區活絡
            - Local Code
                - 網址：[http://demonchaux.com/Local-Code-San-Francisco](http://demonchaux.com/Local-Code-San-Francisco)
                - 標的類型：空地
                - 分析方向：氣候環境分析與開放空間使用
            - 民間分析專案：在看得見的台北—角落翻轉
                - 網址：[https://invisiblecities.blog/2017/05/02/passive-space-remake/](https://invisiblecities.blog/2017/05/02/passive-space-remake/)；[https://invisiblecities.blog/2017/05/10/passive-space-remake-part2/](https://invisiblecities.blog/2017/05/10/passive-space-remake-part2/)
                - 標的類型：空地
                - 分析方向：市民使用、公共使用
        - 介紹==資料英雄計畫==
            - 過去專案成果：[http://d4sg.org/fellowship/projects/](http://d4sg.org/fellowship/projects/)
                - 高雄市消防局：火災風險地圖
                - 環境資訊協會：農地與重金屬污染交叉分析、農地種電空間變遷
    - 地政局想提供的訊息
        - 歡迎社群朋友提供對於「地政雲圖台」功能構想或是改進方向（網址：[http://cloud.land.gov.taipei/](http://cloud.land.gov.taipei/)）
        - 地政局會持續推動「智慧生態社區」（[https://goo.gl/PUmTiA](https://goo.gl/PUmTiA)）也歡迎提供意見
        - 目前預計 5 月底會將第一階段台北市內的公有土地資料釋出，目前至少有 70 機關單位同意釋出。
        - 地政局會試著聯繫「資料英雄計畫」的推動單位。

### 20170603「市有閒置房地整合查詢平台」第 1 次工作會議

會議訊息
- 時間：中華民國106年6月3日(星期六)上午9時30分
- 地點：市政大樓6樓南區605會議室
- 出席單位：臺北市政府財政局、臺北市政府資訊局、臺北市政府地政局、臺北市政府都市發展局、臺北市青年事務委員會、臺北市政府財政局非公用財產管理科、臺北市政府財政局資訊室
- 預計討論議題
    - （一）閒置、未（低度）利用之土地地籍圖及建物輪廓圖資料開放進度。
    - （二）本案後續定期召開工作會議相關事宜：
        - 1.工作會議辦理期程（會議時間、會議地點、開會次數、預定完成時間等）。
        - 2.工作會議運作模式（工作項目、工作進度、參與局處、業務分工、與會人員等）。

### 20170710 實作會議

會議前的邀請訊息
- 台北市政府財政局邀請有意願協助完成資料整理與網頁建置的社群朋友，完成此台北市公有資產活用網站：[http://taitung-fan-182028.middle2.me/](http://taitung-fan-182028.middle2.me/)
- 初步看起來工作事項有：
    - 1.整理公有土地與建物的資料集，整理成網站可以吃的格式。
    - 2.針對網頁版面之類進行必要的調整。
    - 3.整理台北市與公民科技之間的各種行政方案，例如單場型諮詢會議、委託採購機制現況、fellowship困難點等等。
- 社群朋友若您有意願協助台北市政府進行前述兩個面向的實作，且可接受此工作的酬勞必須採用工作會議形式，給予出席費 2000 元，再請聯繫我，並提供給我您的姓名與 email 我將再轉達給台北市財政局。（利益揭露：chewei 僅代為轉達與彙整名單，無涉任何利益）
- 時間：7/10(一)下午3點
- 地點：台北市政府市政大樓8樓中央區財政局討論室

會議概況
- ==20170710 網頁開發日誌 7/10 開發日誌==
    - 參與者：資訊局同仁, Finjon, Ronny, Richard
    - middle2更新postsql版本後可以連到DB
    - geojson欄位要用multipolygon的格式
    - 點擊資料後，跳出預設照片需要更換
    - 現有篩選器，其中「面積」更換成「等待活用、市府已短期活用、尚不開放提議」三種選擇
    - ==後續==：暫由資訊局同仁協助彙整，視狀況，若必要則再約會議
- ==20170710 其他行政機制推動上的討論內容==
    - 參與者：青委會委員, 財政局同仁, 地政局同仁, 資訊局同仁, chewei, Mg
    - 資產資料，流程優化
        - 針對市府內部供需資訊交流進行優化，例如運用線上可即時修改的協作網頁彙整空間清單，避免公文時差。
        - 教育局目前正在盤點餘裕空間資料，預計會開放，資訊局目前有接觸與協助中。
        - 民間社群可以整理一下空間資料流程
            - 例如從一個門牌開始，到哪邊拿到經緯度，到哪邊拿到建物輪廓，如何將清單資料與輪廓資料勾稽起來，整合好的資料會放到哪邊，如何更新資料
            - 例如從一個地號開始，到哪邊拿到該地號的形狀，如何將清單資料與輪廓資料勾稽起來，整合好的資料會放到哪邊，如何更新資料
            - 例如從一個建築物號碼開始...?
            - 其中有一些資料服務環節，在確認沒有侵犯隱私個資，例如某一個地號的輪廓形狀、某一個門牌的建物輪廓形狀，應可以考慮作為資料服務釋出。
    - 盤點公民科技與公務行政之間的協作方案
        - 各種協作方案與經驗，記錄頁面：[https://docs.google.com/document/d/1dEV9CFLt8BbMMBhOJG3NoVvKED5s66gLLV-6mYwqEsE/edit](https://docs.google.com/document/d/1dEV9CFLt8BbMMBhOJG3NoVvKED5s66gLLV-6mYwqEsE/edit)
    - ==後續推動方向==
        - 網頁建置告一階段後，可分為「公務員使用情境」與「民眾使用情境」，兩類對象建議可先分流籌辦聚會工作坊、或是詢問頁面使用經驗與感受。
        - 公部門供需者的部分：邀請各局處，從供給端或需求端的角度來看看測試上線的網頁，目前使用上的感覺，甚至一些必要的功能，例如是否有資料混搭的需求，像是有了空間的位置，能否更即時地掌握其土地使用分區與容許使用的內容為何。
        - 民間使用者的部分：例如透過工作坊，正面表列民眾端的各種使用需求，像是社區認養空地作為公共開放空間、租用或申請進駐室內空間...等等，來收斂實際上資料可以輔助的環節。

### 20170815 實作會議

會議前的邀請訊息
- [https://www.facebook.com/groups/1417173811903954/permalink/1929996180621712/](https://www.facebook.com/groups/1417173811903954/permalink/1929996180621712/)
- 台北市公有資產活用網站：[http://taitung-fan-182028.middle2.me/](http://taitung-fan-182028.middle2.me/)
會議概況
- 由資訊局同仁說明目前進度以及資料課題
- 空地類資料課題：
    - 1.目前資料呈現尚無問題
    - 2.後續希望與財政局確認其資產管理系統能否一次匯出「欄位資料+地籍形狀」
- 建物類資料課題：
    - 1.由於數值地形圖的建築外框，無法準確且大量批次處理而得到該外框所對應的門牌資料，故今日會議決議改以門牌經緯度進行地理定位，網頁上將以點位圖形的方式呈現
    - 2.後續希望與都市發展局測繪部門、門牌定位資料維護部門、資訊局等單位，共同釐清建築物外框圖資與門牌資料之間能否有便捷的整合方式。
- 本日實作：
    - 1.建物資料改以門牌經緯度定位，社群朋友協力完成
    - 2.挑選於網頁呈現的資料欄位，財政局同仁協助說明欄位意義，社群提供市民閱覽角度的意見
    - 3.確認網頁介面調整課題，課題清單由資訊局紀錄
    - 4.社群朋友推論都市發展局可能是先運用財政局所提供的公有建築物清單資料，清單資料中有提供公有建築物所坐落的公有土地地號，運用地籍圖資系統得到了地號的實際座落位與地形形狀範圍，接著比對這塊公有地號上的建築物外框圖資，藉此認定這些外框圖資代表了財政局清單資料中的公有建築物之外框。但實際看資料成果，會發現到一些並非此清單描述的建築物也被認定進來，幾個情境
        - (1) 鄰房與公有地號形狀擦邊，所以也一起被認定
        - (2) 清單內容僅描述學校中的某一棟樓，但因為整個學校共用一個大的地號，所以整個學校的建築群都被認定進來。

### 20170925 市長主持青年事務委員會大會

前期籌備
- 議題：[https://goo.gl/MWALwS](https://goo.gl/MWALwS)
    - 意見一：將公有資產資料交換與展示等功能，結合實際空間活化流程
    - 意見二：台北市政府至少先提供同仁易於使用的關鍵地理資料服務
    - 意見三：台北市政府應研擬行政事務結合公民科技的適切對策
- 簡報：[https://goo.gl/j2ZAbn](https://goo.gl/j2ZAbn)
會議概況
- 由財政局局長向大會報告本案的推動工作概要，接著由 chewei 說明網站使用方式、各種類的貢獻者協助的環節、目前的課題等，可參考簡報：[https://goo.gl/j2ZAbn](https://goo.gl/j2ZAbn)
- 大會決議：
    - 近期透過記者會的方式，推廣給更多關心公有資產的民間團體、市民、NGO組織
    - 請財政局綜整這些公有資產的活用方式，以便民眾查看資訊後，可以判斷下一步的行動方向
會後交換意見：
- 青委會委員陳德君，提到可以運用東園街已經活用的社區規劃師工作室，該處也是公有房舍活用的成果，記者朋友可以實際看到活用的效果。
- 相關可能關心此議題推動的青委會委員：陳韻竹、陳德君、陳彥良、王寶萱
- chewei 提供本階段一些執行構想
    - 記者會的部分
        - chewei 可以再整理一些已經活用公有空間的社區地點，提供給財政局評估記者會場地。
        - 屆時也可以邀請協力的社群朋友參加，分享經驗
        - 建議財政局可以著手撰寫新聞稿，屆時資訊局與民間社群，可以協助查看內容
    - 關於公有資產的活用方式，能否使用涉及到以下事項：
        - 建築物是否已從屬於某個既有的活用政策措施
            - 文化局藝響空間網（[https://goo.gl/JdjYgA](https://goo.gl/JdjYgA)）
            - 老房子文化運動（[https://goo.gl/ZXeNwa](https://goo.gl/ZXeNwa)）
            - 都市更新處都市再生前進基地 (URS)（[http://www.urstaipei.net/about-urs](http://www.urstaipei.net/about-urs)）
            - 財政部國有財產署也有相關的委託給區公所，再交由民間團體進行實質經營管理
        - 空地
            - 綠美化
                - 產業發展局農業發展科有相關執行經驗與評估方式（[https://goo.gl/BBr5Ab](https://goo.gl/BBr5Ab)）
                - 財政部國有財產署也有相關的綠美化措施辦法（[https://goo.gl/Zrfb4R](https://goo.gl/Zrfb4R)）
            - 田園基地 (社區園圃)
                - 工務局公園路燈管理處有田園基地的闢建推動經驗與相關規範
        - 依照提案者所提出的業務內容來進一步輔助檢視適宜性
            - 第一種：整體環境改善，半戶外的休憩空間、駐足空間，綠化措施等
            - 第二種：執行具體的社會福利業務行為
                - 依循社會局既有的相關評估規範
                - 可以做的是：有些評估規範可以透過圖資疊合分析、或是一些預先評估這塊空間確定不能做什麼樣的使用，讓網站瀏覽者可以更直接的了解使用限制與原因說明。
            - 第三種：社區導向的事業經營
                - 依循都市發展局土地使用分區規定既有的相關規範
                - 可以沿用都市發展局與產業發展局合作進行營業登記與空間適法性並陳檢視的工作流程（參考：[https://goo.gl/xNsKER](https://goo.gl/xNsKER)）
        - 修繕費用
            - 或許有可能，鼓勵想要活用空間的單位，透過現勘、修繕經費概估等方式，將這項需求提至參與式預算的場合，徵取更多市民的認同，以及實質預算，來啟動修繕工作
    - 除了市場對價關係之外，公益取向的空間活用機制列舉如下，但不一定是法令上嚴謹的用詞
        - 認養單位另外向其他單位申請可以提供修繕經費的公務措施（例如向都市發展局都市更新處的社區環境改造經費來改造國有財產署的房舍、或是向產業發展局農業發展科申請闢建社區園圃的經費用於警察局權管的水泥空閒置空地）
        - 以修代租
        - 公益用途而進行廉租
        - 補助租金
        - 無償使用，這部分可以善用「區公所」的角色，作為土地產權管理單位與實質認養使用族群之間中介角色
- 補充資訊
    - 民間進一步使用堪用待修的建物
        - 特點：小坪數，由社區營造組織認養，空間用途皆以籌辦社區公共活動，目前都還有在營運、舉辦活動等
        - 相關活用案例：
            - 大同區小柴屋
                - 手作學習、街區文史資訊站
                - [https://www.facebook.com/timberhouse3/](https://www.facebook.com/timberhouse3/)
            - 方方屋萬華區
                - 私有，結合社區公共活動
                - [https://goo.gl/8zxBjX](https://goo.gl/8zxBjX)
            - 大同區大橋工舍 83 號
                - 社區都市農耕
                - [https://goo.gl/6Z5sph](https://goo.gl/6Z5sph)
            - 大安區小白屋
                - 社區修理站
                - [https://goo.gl/3qBEUr](https://goo.gl/3qBEUr)
            - 大安區中央舍
                - 原為中央通訊社低度利用房舍，目前為社區手作學習空間
                - [https://goo.gl/DWXQAB](https://goo.gl/DWXQAB)
            - 桃園市草店尾一巷一號
                - [https://m.mobile01.com/topicdetail.php?f=456&t=5274147&p=1#65885715](https://m.mobile01.com/topicdetail.php?f=456&t=5274147&p=1#65885715)

### 201711 實作網站新增照片功能

- 民間社群參與者：TMonk
- 網址更換成：[http://reformspace.taipei/](http://reformspace.taipei/)
- TMonk 經驗分享的影片段落
    - https://youtu.be/L5_InAFLSHg?t=1346

### 20171115 財政局舉辦記者會

- 籌備工作階段建議
    - 記者會地點參考：[https://photos.app.goo.gl/PjG165Vf6XHcs4Bs1](https://photos.app.goo.gl/PjG165Vf6XHcs4Bs1)
- 20171115 記者會舉辦
    - 電子新聞報導
        - 市府新聞稿【市有閒置空間整合查詢平台」建置完成，後續將徵求民間提案活化閒置資產】
            - [http://www.dof.gov.taipei/ct.asp?xItem=363993167&ctNode=40183&mp=103007](http://www.dof.gov.taipei/ct.asp?xItem=363993167&ctNode=40183&mp=103007)
        - 蘋果日報【小面積市有閒置房地活化 北市徵求提案】
            - [https://tw.appledaily.com/new/realtime/20171115/1241554/](https://tw.appledaily.com/new/realtime/20171115/1241554/)
        - 自由時報【市有閒置空間整合查詢平台 邀民眾集思廣益活化利用】
            - [http://news.ltn.com.tw/news/life/breakingnews/2254541](http://news.ltn.com.tw/news/life/breakingnews/2254541)
        - 聯合報【市有閒置房地活化 北市擬徵提案、自主修繕】
            - [https://udn.com/news/story/11322/2821256](https://udn.com/news/story/11322/2821256)
        - 中國時報【財政局再出新招 徵求民間提案活化閒置資產】
            - [http://www.chinatimes.com/realtimenews/20171115003260-260407](http://www.chinatimes.com/realtimenews/20171115003260-260407)
        - 中央通訊社【市有閒置房地查詢平台上路 民眾可提案】
            - [http://www.cna.com.tw/news/aloc/201711150196-1.aspx](http://www.cna.com.tw/news/aloc/201711150196-1.aspx)
        - 工商時報【財政局再出新招 徵求民間提案活化閒置資產】
            - [https://m.ctee.com.tw/livenews/jj/20171115003260-260407](https://m.ctee.com.tw/livenews/jj/20171115003260-260407)
        - MyGoNews【建置完成 台北市有閒置空間整合查詢平台】
            - [https://yahoo-twhouse.tumblr.com/post/167729640334/%E5%BB%BA%E7%BD%AE%E5%AE%8C%E6%88%90-%E5%8F%B0%E5%8C%97%E5%B8%82%E6%9C%89%E9%96%92%E7%BD%AE%E7%A9%BA%E9%96%93%E6%95%B4%E5%90%88%E6%9F%A5%E8%A9%A2%E5%B9%B3%E5%8F%B0](https://yahoo-twhouse.tumblr.com/post/167729640334/%E5%BB%BA%E7%BD%AE%E5%AE%8C%E6%88%90-%E5%8F%B0%E5%8C%97%E5%B8%82%E6%9C%89%E9%96%92%E7%BD%AE%E7%A9%BA%E9%96%93%E6%95%B4%E5%90%88%E6%9F%A5%E8%A9%A2%E5%B9%B3%E5%8F%B0)
        - 住展房屋網【閒置空間平台 邀集創意活化提案】
            - [http://pchome.megatime.com.tw/news/cat9/20171116/51077536072922259101.html](http://pchome.megatime.com.tw/news/cat9/20171116/51077536072922259101.html)
        - 中廣新聞網【北市上百筆閒置資產 徵求民間提案活化】
            - [http://www.bcc.com.tw/newsView.3083883](http://www.bcc.com.tw/newsView.3083883)

### 20180418 財政局會議

- 民間出席者：TMonk、chewei
- 會議緣由：
    - 財政局已將六筆小坪數房舍資料放到平台上 ([http://reformspace.taipei/](http://reformspace.taipei/))
    - 財政局預計推出「臺北市政府徵求民間提案活化市有閒置房地實施計畫」
        - 計畫依據：「臺北市市有公用房地提供使用辦法」第 6 條 第 1 項 第 6 款 [(文件照片)](https://photos.app.goo.gl/rhz3AWWaHiS25cTP2)
            - [舊條文](http://www.rootlaw.com.tw/LawArticle.aspx?LawID=B010030040000800-1030715)
            - 新條文
                - [http://www.laws.gov.taipei/lawsystem/wfLaw_ArticleContent.aspx?LawID=P03D1008-20180321&RealID=03-04-4008](http://www.laws.gov.taipei/lawsystem/wfLaw_ArticleContent.aspx?LawID=P03D1008-20180321&RealID=03-04-4008)
                - 第 六 條 有下列情形之一者，公用房地得無償提供非營利使用：
                - 一 其他政府機關或學校，設置戶外運動場所及相關設備、相關監測、測試設施或公車候車亭使用。
                - 二 其他政府機關或學校為交通安全、水土保持或防洪排水需要設置護欄、護坡、箱涵、管線等相關設施使用。
                - 三 其他政府機關因應業務之急需使用、舉辦公益、節慶活動或政令宣導及軍事、防災等演習活動。
                - 四 管理機關依工會法組成產業工會之非獨立專屬辦公空間使用。
                - 五 法人或非法人團體配合管理機關執行業務之使用，並經提臺北市政府市有資產活化及運用小組（以下簡稱本小組）審議通過。
                - 六 其他報經本小組審議通過，不超過三年之閒置空間再利用計畫。
        - 首先徵求前述六筆房舍的民間活用提案
    - 想邀請社群朋友提供一些想法
- 會議要點：
    - TMonk 介紹線上收件的服務方案
        - Google 表單
        - Typeform，但上傳附件須要收費
        - 備案則是常見的收件方式：email 至承辦人信箱，或是實體收件
    - TMonk 談網站
        - 目前網站造訪者，一個月約一百人
        - 若目前財政局需要更改圖片、文字，可以與 TMonk 聯繫
        - 若要將網站的維護，調整為非工程師也可以更新與修改資料，仍須要不少工作時間
        - TMonk 協助財政局資訊室同仁建起本機 git ([http://reformspace.taipei/](http://reformspace.taipei/))
- 會議結束後：
    - chewei 提供民間空白計畫書，給財政局公產管理科同仁參考
        - (1)「空間分享計畫」
            - 由臺北市都市更新處，更新經營科主辦，針對明確標的物，欲申請使用者，須提出10頁(A4)以內的企畫書(至少包含進駐團隊介紹、進駐使用計畫、公共回饋計畫)
                - 其中一處空間 [https://www.facebook.com/SpaceShare.Taipei/posts/1576739149105697](https://www.facebook.com/SpaceShare.Taipei/posts/1576739149105697)
                - 另一處空間，面積較大，有區分提案階段
                    - 招募提案 [https://www.facebook.com/SpaceShare.Taipei/posts/1471407142972232](https://www.facebook.com/SpaceShare.Taipei/posts/1471407142972232)
                    - 初審 [https://www.facebook.com/SpaceShare.Taipei/photos/a.111301475649479.18568.109307352515558/1549813791798233/?type=3&theater](https://www.facebook.com/SpaceShare.Taipei/photos/a.111301475649479.18568.109307352515558/1549813791798233/?type=3&theater)
                    - 進駐單位出爐 [https://www.facebook.com/SpaceShare.Taipei/photos/a.111301475649479.18568.109307352515558/1561425817303697/?type=3&theater](https://www.facebook.com/SpaceShare.Taipei/photos/a.111301475649479.18568.109307352515558/1561425817303697/?type=3&theater)
        - (2)「Open Green 打開綠生活」空間改造徵件
            - 由臺北市都市更新處，更新經營科主辦，計畫說明訊息
                - [https://www.facebook.com/taipeiopengreen/photos/a.447887975235514.104977.144408682250113/1621822954508671/](https://www.facebook.com/taipeiopengreen/photos/a.447887975235514.104977.144408682250113/1621822954508671/)
            - 申請單位，例如社區組織、團體，下載的空白計畫書
                - [https://drive.google.com/.../0B1sosk5Rj5hOWjVFTlFOTFk4ZzQ](https://drive.google.com/.../0B1sosk5Rj5hOWjVFTlFOTFk4ZzQ)
        - (3) 針對空地類，例如田園城市政策，有需要可在幫忙蒐集
- chewei 與 TMonk 聊到，可以先由民間發想一套「各單位閒置資產回報流程」
    - 或許可以先設想，市府各單位使用 googlespreadsheet 記錄與維護各單位待活化的資產清單，「空地以地號」、「建物以門牌」，以方便統整
    - 地理視覺化，透過地號帶入 polygon，透過門牌帶入經緯度（建物輪廓框應該還是不容易批次帶入？）
    - 課題：會不會跟各局處自身的資產管理系統匯出機制，無法順利接軌？可能需要一個一個局處來看
    - Finjon Kiang 提供在台南的空屋空地回報專案的經驗
        - 可以用 [https://github.com/tainancity/house](https://github.com/tainancity/house) 管理，只要取得北市地籍與門牌資料
        - [https://tainan.gitbooks.io/house-land-tracker/content/](https://tainan.gitbooks.io/house-land-tracker/content/)
        - 討論串：[https://www.facebook.com/groups/1417173811903954/permalink/2061987080755954/](https://www.facebook.com/groups/1417173811903954/permalink/2061987080755954/)
    - Richard Hsieh> 倒是可以趁機建立各局處對於資產清冊的統一規格?
        - 例如針對空間的使用狀態，有教育局習慣使用的「餘裕」、也有「閒置」、「空置」、「空餘屋」、「預計標租或標售」...


### 20180423 地政局會議

- 民間出席者：chewei
- 會議前
    - 平台構想的文件：[https://www.facebook.com/groups/1417173811903954/permalink/2062140874073908/](https://www.facebook.com/groups/1417173811903954/permalink/2062140874073908/)
- 會議概要
    - chewei 說明以下三點意見
        - 可能需盤點府內相關「空地活化業務」業務機關（例如，產業發展局農業發展科綠化股，受理社區取得管理機關同意書後，提出田園基地闢建的提案計畫書給產業發展局）。
        - 同一批空地資料，可放在「資訊局開放資料平台」（例如KML格式）。
        - 建議提供民間撰寫活化計畫的「構想計畫書」基本架構，輔助管理機關與提案人，建立溝通基礎。
    - 地政局討論「地政雲-公有土地提案平台」的介面議題
- 會議後 TODO
    - chewei 提供所知的「空地改造業務機關」（輔助社區進行空地改造的局處單位）
        - 公部門
            - 補助款項適用於「空間改造類」
                - 產業發展局農業發展科綠化股，空地綠美化開口合約、社區園圃補助計畫。
                    - [http://www.doed.gov.taipei/News_Content.aspx?n=77A72A20400ADD31&sms=28439AB1106047E9&s=6ECD2C6EAD3B2315](http://www.doed.gov.taipei/News_Content.aspx?n=77A72A20400ADD31&sms=28439AB1106047E9&s=6ECD2C6EAD3B2315)
                - 環保局，低碳永續家園計畫、清除雜物垃圾空間...等。
                    - [http://www.dep.gov.taipei/News_Content.aspx?n=5317E7A3195A15CA&sms=48FF873C2D896660&s=9650D65FBBF753C7](http://www.dep.gov.taipei/News_Content.aspx?n=5317E7A3195A15CA&sms=48FF873C2D896660&s=9650D65FBBF753C7)
                - 工務局公園路燈管理處園藝科，田園基地補助計畫。
                    - [https://pkl.gov.taipei/News_Content.aspx?n=C2DFEFA42339B690&sms=A2B20440BA18ED01&s=97095D23CDF56A85](https://pkl.gov.taipei/News_Content.aspx?n=C2DFEFA42339B690&sms=A2B20440BA18ED01&s=97095D23CDF56A85)
                - 都市發展局都市更新處更新經營科，社區營造業務
                    - [https://uro.gov.taipei/News_Content.aspx?n=BEDFC53B968EAFB7&sms=4EE9770BC2190335&s=9F3F794EE2E20FCA](https://uro.gov.taipei/News_Content.aspx?n=BEDFC53B968EAFB7&sms=4EE9770BC2190335&s=9F3F794EE2E20FCA)
            - 補助款項適用於「軟體活動類」
                - 社會局老人福利科，社區關懷據點方案補助
                    - [https://dosw.gov.taipei/News_Content.aspx?n=4229B0D1B86ACD17&sms=42201946EA95A64F&s=CEE7612C932BA905](https://dosw.gov.taipei/News_Content.aspx?n=4229B0D1B86ACD17&sms=42201946EA95A64F&s=CEE7612C932BA905)
        - 私部門
            - 台北市錫瑠環境綠化基金會，綠美化微型計畫
                - [https://www.facebook.com/hsiliu.org.tw/posts/1701561716575083](https://www.facebook.com/hsiliu.org.tw/posts/1701561716575083)
            - 信義房屋社區一家，社區營造行動計畫
                - [http://www.taiwan4718.tw/](http://www.taiwan4718.tw/)
- 會議之後，地政局向大眾推出公有空地查詢與提案的新聞稿
    - 地政局【15公頃公地釋出供全民提案活化】
        - [https://land.gov.taipei/News\_Content.aspx?n=0ABE9F8A3E5B75C2&sms=72544237BBE4C5F6&s=36C9E8D84CC9E40D&ccms\_cs=1&Create=1](https://land.gov.taipei/News_Content.aspx?n=0ABE9F8A3E5B75C2&sms=72544237BBE4C5F6&s=36C9E8D84CC9E40D&ccms_cs=1&Create=1)
    - 自由時報【台北市釋出15公頃公有地 邀民眾提案活化】
        - [http://estate.ltn.com.tw/article/5213](http://estate.ltn.com.tw/article/5213)
    - 好房網【柯P又有新花樣　公地蓋什麼由你定！】
        - [https://news.housefun.com.tw/news/article/181177194439.html](https://news.housefun.com.tw/news/article/181177194439.html)
    - 蘋果日報【北市15公頃空地釋出　「蓋什麼你決定」】
        - [https://tw.news.appledaily.com/new/realtime/20180427/1342760/](https://tw.news.appledaily.com/new/realtime/20180427/1342760/)
    - MyGoNews【全民參與 15公頃公地釋出供全民提案活化】
        - [http://www.mygonews.com/news/detail/news_id/124809/%E5%85%A8%E6%B0%91%E5%8F%83%E8%88%87%2015%E5%85%AC%E9%A0%83%E5%85%AC%E5%9C%B0%E9%87%8B%E5%87%BA%E4%BE%9B%E5%85%A8%E6%B0%91%E6%8F%90%E6%A1%88%E6%B4%BB%E5%8C%96](http://www.mygonews.com/news/detail/news_id/124809/%E5%85%A8%E6%B0%91%E5%8F%83%E8%88%87%2015%E5%85%AC%E9%A0%83%E5%85%AC%E5%9C%B0%E9%87%8B%E5%87%BA%E4%BE%9B%E5%85%A8%E6%B0%91%E6%8F%90%E6%A1%88%E6%B4%BB%E5%8C%96)
    - 住展房屋網【北市15公頃公地釋出 全民來提案】
        - [http://news.m.pchome.com.tw/realestate/myhousing/20180427/index-52480861754954259101.html](http://news.m.pchome.com.tw/realestate/myhousing/20180427/index-52480861754954259101.html)
    - 台灣新生報【台北地政推提案平台 加速公有土地活化】
        - [https://tw.news.yahoo.com/%E5%8F%B0%E5%8C%97%E5%9C%B0%E6%94%BF%E6%8E%A8%E6%8F%90%E6%A1%88%E5%B9%B3%E5%8F%B0-%E5%8A%A0%E9%80%9F%E5%85%AC%E6%9C%89%E5%9C%9F%E5%9C%B0%E6%B4%BB%E5%8C%96-160000300.html](https://tw.news.yahoo.com/%E5%8F%B0%E5%8C%97%E5%9C%B0%E6%94%BF%E6%8E%A8%E6%8F%90%E6%A1%88%E5%B9%B3%E5%8F%B0-%E5%8A%A0%E9%80%9F%E5%85%AC%E6%9C%89%E5%9C%9F%E5%9C%B0%E6%B4%BB%E5%8C%96-160000300.html)
    - 中央社【活化15公頃非市有公地 北市推提案平台】
        - [http://www.cna.com.tw/news/aloc/201804270179-1.aspx](http://www.cna.com.tw/news/aloc/201804270179-1.aspx)
    - 聯合新聞網【活化15公頃非市有公地 北市推提案平台】
        - [https://udn.com/news/story/7323/3111043](https://udn.com/news/story/7323/3111043)
    - 奇摩新聞【活化15公頃非市有公地 北市推提案平台】
        - [https://tw.news.yahoo.com/%E6%B4%BB%E5%8C%9615%E5%85%AC%E9%A0%83%E9%9D%9E%E5%B8%82%E6%9C%89%E5%85%AC%E5%9C%B0-%E5%8C%97%E5%B8%82%E6%8E%A8%E6%8F%90%E6%A1%88%E5%B9%B3%E5%8F%B0-063842990.html](https://tw.news.yahoo.com/%E6%B4%BB%E5%8C%9615%E5%85%AC%E9%A0%83%E9%9D%9E%E5%B8%82%E6%9C%89%E5%85%AC%E5%9C%B0-%E5%8C%97%E5%B8%82%E6%8E%A8%E6%8F%90%E6%A1%88%E5%B9%B3%E5%8F%B0-063842990.html)

### 201806 民眾提案網頁內容改版上線

- 財政局 [http://reformspace.taipei/](http://reformspace.taipei/)  網頁因應民眾提案機制，內容調整後上線
    - 詳情洽 TMonk
        - 機制說明
        - 提供表單下載
        - 空間活用案例更新
- 財政局新聞稿
    - 北市府公告徵求市有閒置房地活化提案，竭誠歡迎市民踴躍參加
        - 發布機關：臺北市政府財政局公產管理科
        - [https://dof.gov.taipei/News_Content.aspx?n=133E08708C6AB0EA&sms=72544237BBE4C5F6&s=693CD8A38E3B2A01](https://dof.gov.taipei/News_Content.aspx?n=133E08708C6AB0EA&sms=72544237BBE4C5F6&s=693CD8A38E3B2A01)


### 201808

- 臺北市政府開始舉辦民眾提案的審查會議
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a5c7ff0e89df36da70ea95a3e8d62f43)
- 歷次進駐單位的資訊，請參考政策網站：https://www.reformspace.taipei/

[Lightbox 攝影圖書館](https://www.lightboxlib.org/) 
[河神的丸子](https://www.facebook.com/HoSngHOUSE/) 
[藝文法學交流基地](https://tclatw.org/) 
[長者健康促進場所](http://sixstar.moc.gov.tw/blog/wanta/communityAction.do?method=doCommunityView) 
咘咕居

近期還有新的空間使用單位，詳情請見政策網頁


### 20181007 g0v Summit 短講分享此計畫的推動歷程

- 短講影片，請見段落 5:25:00-5:47:08
    - https://youtu.be/lhfSYowvi8Y?t=19500
    - 邀請時任臺北市政府副秘書長 陳志銘 先生，出席分享
    - chewei 的段落
        - 講稿 https://www.facebook.com/groups/1417173811903954/permalink/2188471041440890/
        - 簡報 https://docs.google.com/presentation/d/10CTALbA9njYVaE1hyzKSo2mF5IoZG3zIUjBXh9h2iuw/edit
- 中翻英字詞庫
    - https://www.facebook.com/groups/1417173811903954/permalink/2186830374938290/

### 20190621 Richard 與 chewei 整理推動經驗並撰寫為文章

[文章] 談參與臺北市市有閒置空間整合查詢平台經驗
https://eyesonplace.net/2019/06/21/11786/


### 20201205 Lightbox 攝影圖書室參加 g0v Summit 分享推動經驗

當藝術社群遇上開放文化 —— Lightbox攝影圖書室的經驗（以及3個我們不知道怎麼解決的問題）
議程介紹：https://summit.g0v.tw/2020/agenda/2020-12-05/5ef44d7fba206b030d66a34b
議程影片：https://youtu.be/Av-Y_L63hpM


### 202012 兩處房舍釋出並招募進駐單位

士林區建業路 7 號
猛禽協會投入房舍裝修的貼文資訊
https://www.facebook.com/groups/1417173811903954/permalink/3113766858911299/

士林區至誠路一段 305 巷 2 弄 18 號
https://www.facebook.com/670946250032592/posts/1405657859894757/

### 20201227 與基隆的民間團體及公部門分享推動歷程

相關內容傳送門：https://g0v.hackmd.io/kXgIY_KzQN2uOhMYQW-JQw


### 20210901 第一批物件，重新受理提案期間

相關頁面：https://propertyspace.gov.taipei/

### 財政局建立政策網頁
- 政策網址：https://propertyspace.gov.taipei/
- 庫存頁面：https://web.archive.org/web/20200517084338/https://www.reformspace.taipei/

### 20211206 市政府釋出計畫宣傳影片
- 短版：https://www.facebook.com/watch/?v=495404888361466
- 長版：https://youtu.be/FpI1dDW95oo

<iframe width=100% height=490 src="https://www.youtube.com/embed/FpI1dDW95oo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<iframe width=100% height=490 src="https://www.youtube.com/embed/FpI1dDW95oo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### 20220215 臺北市通知將資料與業務轉移至市府其他政策頁面

Tmonk 分享市府通知資訊
https://www.facebook.com/groups/1417173811903954/permalink/3128331107454874/

下架的網站仍可至 archive.org 查看頁面留存： https://web.archive.org/web/20200517084338/https://www.reformspace.taipei/

2023.10.27 網址到期，要詢問 資訊局 是否有續約政策

## 2022.07 [民111.07]
臺北市政府推動市產活化之策略與執行，胡曉嵐‧朱大成（臺北市政府財政局副局長、科長）
https://www.audit.gov.tw/app/index.php?Action=downloadfile&file=WVhSMFlXTm9MekV6TDNCMFlWODBOVFEyTUY4MU5EUTVNVE13WHpnNU16TXlMbkJrWmc9PQ==&fname=WW54RPOKNP00VXKK44VWUSWTZSB4KKMKSSB0YSMPLPGDDCA5OKJCLOB4B0OOA4OKPOWWSS0150B0TXWW34TWIC35OPB0QLICVXYTHGB0WSECPOFGOOTSB5USSSPOGG05HCNODGIGXSSWSSIC14VWUSLK01UXMLA5POUSECQO20OKROTTYW542100EDXWPK10

### 20220223 Tmonk 分享參與經驗

https://youtu.be/L5_InAFLSHg?t=1329

<iframe width=100% height="490" src="https://www.youtube.com/embed/L5_InAFLSHg?start=1329" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## 20240201 財政局公布新法，但並沒有廣為與社會各單位討論

財政局新聞稿：臺北市公用不動產提供使用新法上路，使用年限延長為5年，租金計收兼具財政收益及公益性質
- https://dof.gov.taipei/News_Content.aspx?n=133E08708C6AB0EA&sms=72544237BBE4C5F6&s=8B94A34DFD062CE7
- 修正發布實施「臺北市市有公用不動產提供使用辦法」
    - https://www.laws.taipei.gov.tw/Law/LawSearch/LawArticleContent/FL035285

### 第 5 條

公用不動產提供使用，應由管理機關檢附契約草案及其他相關資料，詳述提供使用緣由、期間、租金及適用法規，經專案簽報核准後辦理。

前項專案簽報，如屬依第六條第三項第三款規定減收租金之案件，除前項文件外，並應檢附財務試算表等佐證文件。

第一項專案簽報，應簽會本府財政局及法務局，陳報本府核准後辦理。但有下列情形之一，並以不低於附表計收租金且無政策特殊考量者，由本府各一級主管機關首長（各區公所陳報民政局）核准後逕予辦理，無須加會本府財政局及法務局：

一、使用期限未逾一年，且無續約約定。
二、提供自來水、電力、天然氣、電信、郵政或其他公用事業使用。
三、提供本市機關學校員工（生）消費合作社使用。
四、設置自動櫃員機、自動販賣機、快照站或其他簡易便民服務設施。
五、申請續約條件未變更，且使用期間累計未超過九年。
六、經公開招租無人投標，續辦招租且底價經減價後，未低於附表所列一般使用租金百分之六十計收。

公用不動產提供移設道路上既有電力設施使用案件，經專案簽報核准者，不受第三條第二項及前三項規定之限制。

圖表附件：附表 臺北市有公用不動產租金收費基準表.pdf

### 第 6 條

公用不動產有償提供使用，應計收租金，其租金不得低於附表之基準，除提供使用用途具公益性、公共性者，或屬附表特殊使用者外，並應參考市場行情、物價指數、使用目的等因素訂之。

公用不動產有償提供使用用途經管理機關評估屬高商業價值者，得按承租人營業收入之一定比例加計租金。但供設置多媒體應用服務設施者，應按承租人營業收入加計百分之二以上之租金。

公用不動產有償提供使用，管理機關得依下列規定減收租金：

一、其他政府機關使用者，土地租金依土地申報地價年息百分之三計收。
二、管理機關為推動業務，或使用用途經目的事業主管機關評估，基於政
    策或法令規定，應予保障或輔導者，土地租金不得低於土地申報地價
    年息百分之三計收。
三、管理機關基於特殊考量，土地租金以低於土地申報地價年息百分之三
    計收者，其所計收之租金總額，不得低於依法應繳納之地價稅及房屋
    稅。

圖表附件：附表 臺北市有公用不動產租金收費基準表.pdf

### 第 7 條

有下列情形之一者，公用不動產得無償提供非營利使用：

一、其他政府機關或公立學校，設置戶外運動場所及相關設備、相關監測、測試設施或公車候車亭使用。

二、其他政府機關或公立學校為交通安全、水土保持或防洪排水需要，設置護欄、護坡、箱涵或管線等相關設施使用。

三、其他政府機關因應業務之急需使用、舉辦公益、節慶活動、政令宣導、軍事或防災等演習活動。

四、管理機關所屬員工依工會法組成工會之辦公空間使用，且其全體會員均為本府所屬員工。

五、法人或非法人團體配合管理機關或目的事業主管機關執行業務之使用。

六、其他報經本府審議通過，不超過三年之閒置空間再利用計畫。

## 202405 投入活化懷生國中職務宿舍的單位收到收回通知

https://www.facebook.com/share/p/h676P6nQXPtRVJmn/

## 202407 投入空間活化的單位收到收回通知


## 202407 臺北市政府財政局預計於116年將計畫中止

### 財政局的說明內容，轉述 by Khoo
- 終止理由：
    - 近年來能夠找到並公告的案件越來越少，民間申請的組數也不多，通常一個標的只有一到兩組提案
- 財政局表示：
    - 因為有些建物太老舊、有都更需求所以不適合繼續開放民間申請，變成太難找到可公告的標的。
    - 後續這些空間還是可以依照「臺北市市有公用不動產提供使用辦法」開放民眾租用，但就必須付租金。
    - 既有案件會由相關局處（如猛禽研究會由動保處、lightbox由文化局）尋找其他場地。

### 探討

- 疑問：歷年來財政居公告的案件數共20件，目前持續進行中的有9件。而財政局曾經評估過後，認為不適合辦理公告的案件數只有2件，其中一件為士林區中山北路五段378巷，因為屬於軍事管制區所以覺得不宜開放民間使用，另一件為大安區臥龍街129之5-13號，因為建築物老舊，應該拆除所以不宜開放。
- 疑問：107年公告了9個標的，108年公告1個標的，109年3個標的，110年4個標的，111年2個標的，112年1個標的。110年公告之4個標的中有4件為107年公告之標的。
- 財政局表示，既有的民間提案者都已經有被安置好，沒有民眾施加壓力的話比較難找到施力點。
    - chewei> 財政局所描述「都有被安置」並非事實，2024.07.24 就我所知至少 4 個目前經營空間的單位尚未確認後續會如何處理

## 202409 臺南市政府黑客松，財稅局提出「公產資產管理與活化」題目

財稅局提出「公產資產管理與活化」
- https://aithon2024.goodideas-studio.com/topic-list/
- 問題描述：台南市政府擁有相當數量的市有不動產，但其中不少資產長期處於閒置狀態，未能有效發揮其應有的價值。這些閒置資產不僅無法帶來經濟效益，還可能因缺乏管理而逐漸老化，對市府資源形成負擔。如何將這些閒置資產重新整合與活化，讓其重新投入使用，成為城市發展的一部分，已成為當前市府的一項重要課題。
- 系統現況：目前，市府對於閒置市有不動產的管理主要依賴傳統的人工方式進行，資產的狀態和使用潛力往往無法得到即時更新與全面評估。媒合閒置資產與潛在需求方的過程，也多依賴人工聯繫與協調。此外，由於缺乏一個集中的管理平台，資產的整體狀況、可利用價值以及適合的活化方案難以有效整合，導致閒置資產的再利用進展緩慢。
- 局處需求：為了提升市有不動產的管理與活化效率，局處希望引入一套數位化的資產管理系統，能夠即時更新並整合閒置資產的狀態資訊，促進資產與潛在需求方之間的媒合。此外，透過數據分析，系統應能提供最佳活化方案的建議，從而加快閒置資產的再利用進程，並最大化其經濟與社會價值。這將使市府能更有效地管理公共資產，為城市的可持續發展注入新的動力。

## 20250214 河神的丸子契約到期

https://www.facebook.com/HoSngHOUSE/posts/pfbid02wXMxJdxFLisaDFDi4qAQwz4gS2ZGnaFhVaWuQGGjiRmVEDjAKDCE6VwrsZ2qgpxel

## 2025.XX.XX 攝影圖書室 有延續使用空間

## 2025.XX.XX 猛禽協會 有延續使用空間 ?
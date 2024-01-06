---
title: "友善地號資訊查詢界面"
tags: hackpad
---

# 友善地號資訊查詢界面

> [點此觀看原始內容](https://g0v.hackpad.tw/ZrNxaKVn8jt)

地號是台灣政府處理地理時很重要的地理單位，台灣有兩千多萬塊地，不是每個地都有地址，很多地的描述都是用地號，例如「環評書地點」、「國有地資訊」、「土地買賣」等，因此這 hackpad 想要整理一下，讓大家更容易了解地號是什麼，以及如果要查詢的話有什麼方法。

### 關於地號

- 地號: 臺北市中正區城中段三小段21-2號 (這是最高法院的位置)
    - 臺北市: 縣市名稱
    - 中正區: 行政區名稱
        - 行政區資訊很重要，因為同一縣市可能會在不同行政區會有同樣的段名，Ex: 臺南市中西區正義段 和 臺南市南區正義段 兩個是不同的路段
    - 城中段: 大段名
    - 三小段: 小段名
    - 21: 母號
    - -2號: 子號
        - 號碼的呈現可能有 21-2, 00210002 兩種
        - 有可能沒有子號，那就直接寫成 21 號就可以了
- 地籍相關資訊
    - 地籍的管理是由各縣市的地政事務所所管理，因此要查詢地號的變動，必需要先知道你要查的地是哪一個地政事務所
    - 地籍是日治時代延用至今的，所以可以從現在的地號推回日治時代的地名，Ex: 龍山國中 地號是 臺北市萬華區萬華段一小段626號 ， 透過 [台北市建成地政事務所網頁](http://w2.land.taipei.gov.tw/Sub/B/NewOld/abalidb.asp) 可以查詢到在過去是 八甲段1小段21地號 ，再透過[維基百科上面整理的日治時代舊町名列表](http://zh.wikipedia.org/wiki/%E8%87%BA%E5%8C%97%E5%B8%82%E8%88%8A%E7%94%BA%E5%90%8D%E5%88%97%E8%A1%A8)，可以查到八甲段之前是八甲町，因此日治時代是 八甲町一丁目21號。日治時期住所番地查詢現今位置說明文章 [http://crgis.rchss.sinica.edu.tw/info/knowledge/20150326](http://crgis.rchss.sinica.edu.tw/info/knowledge/20150326)
- 代碼相關
    - 縣市代碼: 臺北市 A, 臺中市 B ... (與身份證字號第一碼相同)
        - [https://sheethub.com/ronnywang/中華民國縣市](https://sheethub.com/ronnywang/中華民國縣市)
        - L臺中縣 R臺南縣 S高雄縣 已於 2010 年升格成直轄市，身份證已經不再發，合併入 B臺中市 D臺南市 E高雄市
    - 事務所代碼: 臺北市中山事務所 AC, 臺中市中興事務所 BC, 彰化縣北斗事務所 NF, 臺中市豐原事務所 LA
        - [http://data.gov.tw/node/5967](http://data.gov.tw/node/5967) (資料很舊...)
        - [https://sheethub.com/ronnywang/地政事務所轄區圖](https://sheethub.com/ronnywang/地政事務所轄區圖) (上面那個資料的 SheetHub 呈現)
        - 但是舊的 L臺中縣, R臺南縣, S高雄縣 的地政事務所仍是用 L, R, S ，沒有跟著變動為 B, D, E，所以現在的臺中市裡面會同時有 L 和 B 開頭的事務所。
        - 2014/11/1 成立 LI臺中市龍井事務所，並且將LC臺中清水事務所許多路段轉移過去。
    - 段名代碼:  臺北市萬華段一小段(建成所) AB0043, 臺中市復興段(豐原所) LA0181, 臺中市中華段七小段(中山所)  BA0064
        - [http://www.land.moi.gov.tw/ngis/chhtml/query3.asp?dnformat=3](http://www.land.moi.gov.tw/ngis/chhtml/query3.asp?dnformat=3)
        - [https://sheethub.com/ronnywang/土地段名代碼表/](https://sheethub.com/ronnywang/土地段名代碼表/)
        - 同一縣市同一段名有可能會是不同段，例如 臺南市中西區正義段(DA0169 臺南所), 臺南市南區正義段(DC0404 東南所), 臺南市仁德區正義段(RF0991 歸仁所)  ，甚至同一事務所也有可能會有同段名是不同段，例如 新北市蘆洲區正義段 FG1762 , 新北市三重區正義段 FG1739 兩個都是 FG 三重事務所的。


- 複丈業務
    - 提案題目：土地複丈原圖地籍調查表，減章便民
        - 土地複丈原圖地籍調查表依現行規定因自然增加、浮覆、坍沒、分割、調整地形及界址調整而複丈者，應製作土地複丈地籍調查表，蓋章眾多，較花費時間，影響行政效率。
        - 來源：https://presidential-hackathon.taiwan.gov.tw/ProposedContent.aspx



### 圖資查詢服務

- 內政部地政司 地籍圖資網路便民服務系統 [http://easymap.land.moi.gov.tw/](http://easymap.land.moi.gov.tw/)
- 「地籍圖詮釋資料查詢」網站 [http://lisp.land.moi.gov.tw/MMS/index.aspx](http://lisp.land.moi.gov.tw/MMS/index.aspx)
- 內政部國土測繪中心 國土測繪中心圖資 [http://maps.nlsc.gov.tw/O09/mapshow.action](http://maps.nlsc.gov.tw/O09/mapshow.action)
- 依據地政單位說明，可以透過 地政電子資料流通服務網 ( [https://ccs.land.moi.gov.tw/](https://ccs.land.moi.gov.tw/) ) 提出申請
    - 政府機關申請使用應該是不用額外付費
    - 但民間單位就會收取每筆1元的費用（台南市為例）

### 開放資料在哪裡？

- 「臺南市宗地地號屬性資料」
    - 包含宗地地號區碼、區名稱、段碼、段名稱、地號、地號簡碼、宗地視中心X坐標(TWD97)、宗地視中心Y坐標(TWD97)
    - [http://data.tainan.gov.tw/dataset/par](http://data.tainan.gov.tw/dataset/par)
    - 但是沒有土地多邊形外框喔 !
- 內政部及財政部國有財產署經管公有土地
    - 附帶地號屬性資料，以及多邊形資料，以 KML 格式釋出
    - [http://data.gov.tw/node/34315](http://data.gov.tw/node/34315)
- 歡迎補充

### 討論

- 網路及需要有顯示所有地號之地籍圖。自從政府下令（？）刁難民眾不能知道其鄰近之地號後，所有網路地籍圖僅載單一地號，其他筆則皆空框。
- 能否開放「不提供個人資料」的地籍輪廓資料呢？
    - 公有土地，實際案例：國產署與內政部的開放資料，已經同步釋出土地輪廓，建議其他公家單位土地可以比照辦理
    - 私人土地，方案構想：若是私有土地，僅釋出土地輪廓，註明地號、私有
        - 欄位：
            - 縣市,鄉鎮市區,段代碼,段小段,地號,登記面積
            - 宗地輪廓（含形狀與座落位置）
            - 所有權人類別（僅顯示私有）,權利範圍類別,權利範圍持分分母,權利範圍持分分子,管理者名稱（僅顯示私有）



## 宗地地號

臺中市宗地地號視中心坐標 https://opendata.taichung.gov.tw/dataset/3afbd81c-1a9f-11e8-8f43-00155d021202

臺南市宗地地號屬性資料
https://data.tainan.gov.tw/dataset/par

## 地段圖

臺北市數值地籍地段圖 https://data.gov.tw/dataset/121186
109年高雄市地籍段界圖 https://data.kcg.gov.tw/dataset/109land-section-map

新北市 x
桃園市 x




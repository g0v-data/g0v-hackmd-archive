---
title: "關心地方政治計畫：資料收集"
tags: hackpad
---

# 關心地方政治計畫：資料收集

> [點此觀看原始內容](https://g0v.hackpad.tw/MbJYvY0Iu0E)


常有一個疑惑，想要關心自己所在的地方，卻又不知道從哪裡開始，從印象、傳聞、新聞評論或政論雜誌所看到的面貌是真的嗎？我想提個專案，從官方現有的數據開始，整理出與我們生活息息相關的指標，並轉化成直覺可解的圖像，除了瞭解地方真實的差距以外，也提供現實政治討論跟比較的基礎！

## 議題發想

具體打擊點請到：
1.  區域發展問題：[關心地方政治計畫：議題發想](https://g0v.hackpad.tw/1GTNTwXcJhy)
2.  [議員工程配合款](https://g0v.hackpad.tw/jjNta3y2alH)問題
3.  參考 [ntu datajournalism](http://datajournalism.ntu.edu.tw/)


## 各種資料數據

### 政府統計

- [政府統計總覽](http://www.dgbas.gov.tw/ct.asp?xItem=13213&CtNode=3504&mp=1)
- [縣市重要指標查詢系統](http://ebas1.ebas.gov.tw/pxweb/Dialog/statfile9.asp)：定期調查公開的縣市層級的官方統計
- 國家發展委員會 [都市及區域發展統計彙編](http://ngis.nat.gov.tw/statistic/index.aspx)
- [台灣政治地緣資訊系統](http://tpgis.nccu.edu.tw/nccu/)
- [研考會數位落差（機會）逐年報告](http://www.ndc.gov.tw/att.aspx?sNo=0028380)：[歷年數位落差調查csv](http://www.ndc.gov.tw/att/0028380/0028380_54.csv)
- 中央研究院人社中心：[個人家戶數位落差調查／個人家戶數位機會調查](https://srda.sinica.edu.tw/gov/group/58)統計資料及問卷
- [中央對直轄市及縣市一般及專案性補助款情形表](http://www.dgbas.gov.tw/ct.asp?xItem=28336&ctNode=4972)
- 食材登錄
    - 台北市 [http://foodtracer.taipei.gov.tw/](http://foodtracer.taipei.gov.tw/)
    - 台中市 (但是學校部分也可查到其他縣市）[http://175.98.115.58/cateringservice/web/main/](http://175.98.115.58/cateringservice/web/main/)
- [衛福部統計處各縣市醫療資源統計](http://www.dgbas.gov.tw/ct.asp?xItem=15428&CtNode=4625)：醫療院所、醫師、護理師、護士、病床
- [103年版教育統計](https://stats.moe.gov.tw/files/ebook/Education_Statistics/103/103edu_EXCEL.htm)（幼兒園2-6歲是教育部管）
- [衛生福利部統計處](http://www.mohw.gov.tw/cht/DOS/Statistic.aspx?f_list_no=312)（托嬰中心0-2歲是衛福部管）
- [全國教保資訊網](http://www.ece.moe.edu.tw/?page_id=2085)（幼兒園所在地、性質、公私立）
- [主計處 > 審計報告 \> 總決算審核報告](http://www.audit.gov.tw/files/11-1000-97.php) （包含各地方政府決算報告審計結果）
    - 備份： [https://github.com/kiang/www.audit.gov.tw](https://github.com/kiang/www.audit.gov.tw)
- [行政院主計總處 縣市總預算彙編](http://www.dgbas.gov.tw/lp.asp?ctNode=4971&CtUnit=756&BaseDSD=7&mp=1)
    - 備份： [https://github.com/kiang/dgbas.gov.tw](https://github.com/kiang/dgbas.gov.tw)
    - 2011~2014 各縣市比較： [http://kiang.github.io/dgbas.gov.tw/city_budget.html](http://kiang.github.io/dgbas.gov.tw/city_budget.html)

### 地理式資訊

- [內政部國土測繪中心全球資訊網](http://www.nlsc.gov.tw/)；[國土測繪圖資網路地圖服務地標資訊](https://github.com/ronnywang/maps.nlsc.gov.tw/tree/master/landmark)
- [NGIS國土資訊圖台](http://tmap.geospatial.org.tw/)；[地理圖資開放的討論](http://hackfoldr.org/POPonFire/5YtEoKVphQF)；[NGIS 圖資清單](https://docs.google.com/spreadsheets/d/tA2Vu_ajWywAx3fjsaM9Rug/htmlview)
- [台灣圖資資料](https://osmtw.hackpad.com/%E5%8F%B0%E7%81%A3%E5%9C%96%E8%B3%87%E8%B3%87%E6%96%99-yQUYI6ee30z) 整理by OpenStreetMap (TW)
- [林務局農林航空測量所](http://www.afasi.gov.tw/)
- [台灣行政區界地理資訊](http://request.data.g0v.tw/questions/7/)
- [公共建設計畫空間規劃支援系統](http://pss.ngis.org.tw/index.aspx?ReturnUrl=%2fdefault_l.aspx)，僅公務部門使用
- [公有土地管理地理資訊系統](http://comgis.moi.gov.tw/System/SystemDetail.aspx?seq=2)；[公有土地管理地理資訊系統帳號申請表](http://www.chcg.gov.tw/ch/06services/01view.asp?data_id=12176) ([由巨鷗科技所建置](http://www.geo.com.tw/BLM.html))
- [林務局的林地分級計畫](http://210.241.21.133/DOC/3492/PLAN_40_200702082303552.htm)
- [農地資訊服務網](https://talis.coa.gov.tw/asso/)
- [智慧型農地污染決策管理及支援系統](http://pollution.makoci.com/dssMgt/init)
- 近期環保署的一個採購標案：運用巨量資料於環境治理之評估及營運規劃，[網址](http://web.pcc.gov.tw/tps/tpam/main/tps/tpam/tpam_tender_detail.do?searchMode=common&scope=F&primaryKey=51365648)
- [臺灣氣候變遷推估與資訊平台建置](http://tccip.ncdr.nat.gov.tw/NCDR/main/index.aspx)
- [水利共享地理資訊系統](http://gmap.wra.gov.tw/wrahub_3wgis/default.asp)
- 地質法預計未來三四年之內將全台灣地質敏感地區予以公告，[簡報](http://www.moeacgs.gov.tw/newlaw/downloads/1030509%E7%B0%A1%E5%A0%B1%E5%8F%83%E8%80%83%E8%B3%87%E6%96%99.pdf)（地質敏感區與土地開發管理）
- [中央研究院人社中心地理資訊科學研究專題中心](http://gis.rchss.sinica.edu.tw/)
- [Philip Zheng](https://www.facebook.com/philipzh?fref=ufi)**>** 小弟剛好也用 Google Fusion Tables 做了一個台灣法拍屋地圖：[http://m.everfine.com.tw/](http://m.everfine.com.tw/)
- [Taipei, Taiwan: The age of the City](http://ronnywang.pixnet.net/blog/post/35346775) 建築物年代與建照資料 (ronnywang)
- [各鄉鎮平均家戶用電](http://ronnywang.pixnet.net/blog/post/37422853) (ronnywang)
- [房地實驗室](http://www.foundi.info/lab/)：淹水潛勢、地質狀況、癌症就診、嫌惡設施 (foundi)
- [災害情資網](http://eocdss.ncdr.nat.gov.tw/ncdrwebv2/)
- 海平面上升預測 ：[網站與地圖](http://flood.firetree.net/)
- GSM 基地台：[http://opencellid.org/](http://opencellid.org/)
- Earth：[http://earth.nullschool.net/](http://earth.nullschool.net/)
- Global Forest Watch：[http://www.globalforestwatch.org/](http://www.globalforestwatch.org/)
- PM2.5：[http://env.g0v.tw/air/](http://env.g0v.tw/air/)
- 國家公園步道巡守通報系統：[http://140.109.160.184/ushahidi/main](http://140.109.160.184/ushahidi/main)
- Flightradar24.com - Live flight tracker!：[http://www.flightradar24.com/25.39,120.63/8](http://www.flightradar24.com/25.39,120.63/8)
- Mark-a-Spot : [http://www.markaspot.de/en](http://www.markaspot.de/en)

### 區域政策

- 預算：中央政府總預算、地方預算
- 政府電子採購網的資料：[http://gov.playgroup.com.tw/](http://gov.playgroup.com.tw/)
- 各縣市[區域計畫](http://www.cpami.gov.tw/chinese/index.php?option=com_content&view=article&id=10164&Itemid=53)，將會是台灣目前最高層級的土地運用的法律與規範，並且於國土計畫法草案通過時接軌之。區域計畫其重要性，例如，中科四期公部門之所以敗訴，是因為國科會違背「區域計劃法15條之二第一項第一款」之「於國土利用係屬適當而合理」；區域計畫，對於地區的未來產業發展、土地運用布局、新訂或擴大都市計畫範圍、原住民自治區議題、區域水資源涵養管理...等，都將以區域計畫內容作為執行基礎。目前，各縣市區域計畫僅剩台東、花蓮、嘉義、澎湖，四縣尚未委託民間單位完成(2014.09.14資訊)，其餘縣市已擬定，進入審查程序中，需要各地方團體與人民的關注。
    - [全國區域計畫專區](http://www.cpami.gov.tw/chinese/index.php?option=com_content&view=article&id=10164&Itemid=53)，[「全國區域計畫」公告實施版](http://www.cpami.gov.tw/chinese/filesys/file/chinese/dept/rp2/rp1021017.pdf)(102.10.17)
    - [各縣市區域計畫辦理進度](http://www.cpami.gov.tw/chinese/index.php?option=com_content&view=article&id=13342&Itemid=53)
        - [新北市區域計畫專區](http://regional.planning.ntpc.gov.tw/)，[新北市區域計畫草案](http://www.cpami.gov.tw/chinese/index.php?option=com_content&view=article&id=17723&Itemid=53)
        - [台中市區域計畫專區](http://tp.longi.tw/index.php)，[台中市區域計畫草案](http://data.longi.tw/20131113-1.pdf)
        - [彰化縣區域計畫專區](http://www.urban.chcg.gov.tw/za/index.htm)，[彰化縣區域計畫草案](http://www.urban.chcg.gov.tw/za/nots/10303%E5%BD%B0%E5%8C%96%E7%B8%A3%E5%8D%80%E5%9F%9F%E8%A8%88%E7%95%AB(%E5%85%AC%E9%96%8B%E5%B1%95%E8%A6%BD)%E6%9B%B8.pdf)
    - 地球公民基金會，舉辦全國區域計畫工作坊活動：[http://www.cet-taiwan.org/node/2002](http://www.cet-taiwan.org/node/2002)
    - g0v專案發想：[營建署綜合計畫組神祕第六人](http://hackfoldr.org/POPonFire/7AfW6j0CHwV)


## 其他相關資料

- [參與式預算共筆](https://g0v.hackpad.tw/rsn8O1wiDyk)
- [「公有地大行動」對於地理資料的討論與資源](http://hackfoldr.org/POPonFire/5ofp8l2IWiT)
- 公督盟的 [地方議會評比](http://www.ccw.org.tw/p/21819) 以及跟監票者聯盟合作的 [議員議會改革承諾書簽署活動](http://www.observers.tw/ccw/)



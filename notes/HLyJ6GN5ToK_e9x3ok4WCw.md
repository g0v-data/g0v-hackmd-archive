---
tags: GIS
---

# Web GIS 工具與案例

內容偏向程式開發，需要程式基礎

教材：GIS 學習路徑 by Ronny
- [GIS 學習路徑 - 簡報 (P.42 開始)](https://docs.google.com/presentation/d/1e1k7EBhVX1GsNv8fk0XdQ4L_rndlA98clqEGgeoLNAc/edit#slide=id.gbf1d3245b6_0_16)

<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vSn1bP8TBgCjCHjzJ-22YGFxFO8SKuEkDdWwleOO6_7hR2wrWqRevTaY6uYujNjoUeeiMNQRwYU-TPD/embed?start=false&loop=false&delayms=3000" frameborder="0" width=100% height="480" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>

- 影片段落開始時間：[2:01:40](https://youtu.be/pCTnU69R3SA?t=7300)

<iframe width=100% height="400" src="https://www.youtube.com/embed/pCTnU69R3SA?start=7300" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---

內容概要
- Web GIS 工具介紹
    - GeoJSON
    - PostGIS / Spartialite
    - Geodjango / Python https://docs.djangoproject.com/en/3.1/ref/contrib/gis/tutorial/
    - Leaflet.js https://leafletjs.com/
    - turfJS / Node.js https://turfjs.org/
    - WMS / WMTS
        - 國內 WMS / WMTS 服務資源清單：
        - http://gis.rchss.sinica.edu.tw/qgis/?cat=18
        - http://gis.rchss.sinica.edu.tw/qgis/?cat=7
        - http://gis.rchss.sinica.edu.tw/qgis/?p=3640
    - 這個頁面蒐集各式各樣的「口罩地圖」應用案例，蠻方便看到地理資料與地圖服務的多樣性：https://mask.pdis.nat.gov.tw/
- 圖磚經驗分享
- 斧頭幫大挑戰，爬資料關卡訓練
    - http://axe.g0v.tw/
- 地理資料介接服務 API
    - [國土測繪中心](https://maps.nlsc.gov.tw/S09SOA/homePage.action?Language=ZH)
    - [地政司地政資訊](https://cop.land.moi.gov.tw/Services/service_list.aspx?ServiceType=All) 
    - 數值地形模型加值應用服務 https://dtm.moi.gov.tw/docs/slope.aspx
    - 三維國家底圖 https://3dmaps.nlsc.gov.tw/
    - 政府資料開放平臺 https://data.gov.tw/
    - 常見的衛星影像種類 來源盤點 https://g0v.hackmd.io/5QH2TlaXQR21wMo3UIKZug
        - 例如：SPOT 衛星，全台範圍的歷年年度衛星影像成果，有提供 api / wms


## 專案經驗：github, 推動歷程文章

Disfactory 農地違章工廠
- https://g0v.hackmd.io/@yukaii/Disfactory
- GitHub Repo: https://github.com/Disfactory/Disfactory
- 用 GeoDjango 做 geo spatial query
- 後臺可匯出舉報用的文件
- g0v slack #disfactory
- Deeper, yukai

大河小溪全民齊督工
- https://river-watcher.bambooculture.tw/
- https://github.com/SeanGau/river-watcher
- SeanGau

人行道地圖
- https://functionofcity.net/sidewalk
- 議題文章 https://eyesonplace.net/2021/06/02/17112/
- Richard

臺北市市有閒置空間整合查詢平台
- https://www.reformspace.taipei/
- tmonk
- 臺北市政府與民間社群參與者協作歷程：https://g0v.hackmd.io/WN_QBpNpQtO1oxd_r4IIjQ

天龍特公地
- https://taipei-pop.herokuapp.com/
- https://github.com/dz1984/taipei-pop
- dz1984

地號 GeoJSON API
- https://twland.ronny.tw/
- ronny

9d8 地點通報工具
- https://g0v.hackmd.io/L_v7mAAyT8GT-c_ukR9IYQ
- https://github.com/dz1984/9d8TW
- http://9d8.tw/
- dz1984

足跡比對工具
- https://yjlou.github.io/2019-nCov/
- 這個程式藉由比對你的手機歷史位置記錄，來判斷是否曾與病患接觸。基於隱私考量，你的資料只會在本地端處理，不會上傳到任何網路主機。
- Stimim

空氣品質相關地圖
- https://v5.airmap.g0v.tw/#/map
- http://env.g0v.tw/air/

lowiki-org
- https://lowiki.tw/
- https://github.com/lowiki-org
- superbil, pm5

Ronny 地圖作品
- https://ronny.tw/data/

Kiang 地圖作品
- https://kiang.github.io/

HeritageMapTW
- 臺灣自然與文化資產（及潛力點）地圖
- https://nebula-rubram.github.io/HeritageMapTW/
- https://github.com/nebula-rubram/HeritageMapTW
- 社團討論串 https://www.facebook.com/groups/176223359193164/posts/1975329292615886

Geemap
- https://www.facebook.com/groups/522533035776027/permalink/634120827950580/


Re:Earth (球面地理資料視覺化工具)
- https://community.reearth.io
- https://github.com/reearth/reearth
- 日文介紹文章 https://www.iii.u-tokyo.ac.jp/news/2021072615178

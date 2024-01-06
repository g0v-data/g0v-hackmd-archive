---
tags: GIS, 防災, 民防
---

# WaytoSafety 隨時隨地知道避難場所位置<br>災害避難疏散場所 (Evacuation Area)、防災避難收容處所 (Shelter)、防空避難處所 (Air Raid Shelter) 

:::info
Channel: g0v Slack #facing-the-ocean
Contributor: 
- chewei, 
- 感謝 hwan 分享韓國的 Shelter 查詢網頁，以及用詞建議 "대피소"
:::

:::warning
文件目錄
[TOC]
:::

## Evacuation Area / ひなんばしょ / 대피 장소 / 災害避難疏散場所<br>Shelter / ひなんじょ / 대피소 / 防災避難收容處所

用詞：
- Evacuation Area / ひなんばしょ / 대피 장소 / 災害避難疏散場所
    - 例如地震當下，海嘯來臨前，應前往的疏散避難場所
        - 但不一定是 避難收容處所
        - 例如地震來臨，學校空曠的操場；情況較穩定後，可選擇前往 收容處所，例如經確認餘震期間仍可判斷為安全的運動場館室內
- Shelter / ひなんじょ / 대피소 / 防災避難收容處所
    - 室內避難收容處所(優先安置學校) Indoor Evacuation Shelter ( School for Priority Shelter )
    - 室外避難收容處所(防災公園) Outdoor Evacuation Shelter ( Disaster Prevention Park )
    - 避難收容處所(備用) Evacuation Shelter ( Backup )

### Offline Map

#### 全國各村里簡易疏散避難地圖

簡易疏散避難地圖，但好像還是各村里 PDF 檔案方式釋出？
https://www.nfa.gov.tw/cht/index.php?code=list&ids=82

如何找到自己所在的村里避難地圖，推廣網頁
https://www.safetaiwan.com/blogs/disaster-prevention-column/evacuation-map

#### 特定地區或園區的避難地圖

國內研究「地形特徵圖」部分地區有產製避難路線建議章節
https://atlas.geo.ntnu.edu.tw/
- 木柵 https://atlas.geo.ntnu.edu.tw/html/muzha.html
    - 這本並沒有談到避難路線 
- 南投縣草屯鎮 https://atlas.geo.ntnu.edu.tw/html/caotun.html
    - 這本並沒有談到避難路線 
- 臺東縣成功鎮 https://atlas.geo.ntnu.edu.tw/html/chengkung.html
    - 這本並沒有談到避難路線 
- 花蓮縣玉里鎮-D018大規模崩塌潛勢區 https://atlas.geo.ntnu.edu.tw/html/antun.html
    - 這本有介紹避難路線與各部落避難建議據點
- 屏東縣來義鄉來社溪 https://atlas.geo.ntnu.edu.tw/html/laiyi.html
    - 這本有介紹避難路線與各部落避難建議據點
- 高雄市桃源區荖濃溪 https://photos.app.goo.gl/oJ1VFzUmBvSJJm1m9
    - 這本有介紹避難路線與各部落避難建議據點

產業與科學園區

交通園區

NCDR 資料釋出網址
https://datahub.ncdr.nat.gov.tw/dataset


### Data

#### Open Data / Release Data

消防署釋出全台點位資料
- 資料欄位：序號、縣市及鄉鎮市區、村里、避難收容處所地址、經度、緯度、避難收容處所名稱、預計收容村里、預計收容人數、適用災害類別、管理人姓名、管理人電話、室內、室外、適合避難弱者安置
- https://data.gov.tw/dataset/73242

個別縣市釋出資料集
- 2024.01 僅 臺中市、臺東縣、澎湖縣 有釋出 KML 地點資料，待確認是「疏散避難場所」還是「防災避難收容處所」
- 新北市 NCDR 資料平台上有釋出

盤點日本韓國類似的資料集
https://docs.google.com/spreadsheets/d/1OT-Xwx8fSfPdehkgalaF-JtxM5HvHQGLJ2wadFIUpMQ/edit?usp=sharing
🔥🔥🔥

#### Vectorization 將內容數位化為資料

民間專案曾嘗試建立線上地圖
https://github.com/lowiki-org

討論：於 OpenStreetMap 如何標記防災避難收容處所
https://hackmd.io/@osm-tw/HyUvtrOmu

討論：是否有可能用 群眾標註地圖，把簡易疏散避難地圖上面的地點，標記到 群眾標註地圖 上
- 標記測試：
    - 先找到一幅簡易疏散避難地圖檔案，以「臺北市中山區朱園里」為例
        - https://www-ws.gov.taipei/Download.ashx?u=LzAwMS9VcGxvYWQvMzEzL3JlbGZpbGUvMTI4NDEvMjMwMi9iMzJkODg0MC05MzU0LTQ2ZGYtYTFiZi1iMDY0MWRhM2MwN2QucGRm&n=NjMwMDQwMF8wMzbkuK3lsbHljYDmnLHlnJLph4xf5Lit5paHLnBkZg%3d%3d&icon=..pdf
    - 標記「避難收容處所(備用)：臺北市中山區長安國中」
        - 把地點標記在校門出入口的位置
        - https://commutag.agawork.tw/image?dataset=5e6b06a177e80cf258b9ba72&image=6596b33238c282d22899f2a2

#### 資料應用

南投縣草屯鎮日新國中，製作防災避難引導 Linebot，介紹網頁
https://rsjhs.ntct.edu.tw/p/404-1010-403933.php?Lang=zh-tw

日本，列印紙本地圖
https://kamimap.com/tw/map/2024-noto-earthquake/

## Air Raid Shelter / 防空ごう / 방공호 / 防空避難處所

用詞：
- 防空避難處所
- 防空避難設施
- 防空疏散避難設施
- 防空疏散避難設備

### Data / Online Map

線上地圖與資料集
- 內政部警政署民防指揮管制所，用 Google My Map 提供各地區防空避難處所
    - https://adr.npa.gov.tw/
- Kiang 運用政府資料製作出防空疏散避難地圖
    - https://kiang.github.io/air_raid_shelter/
- Ronny 備份
    - https://g0v.hackmd.io/Bo2u7eEcQg6pOuEoOPCADQ#%E9%98%B2%E7%A9%BA%E9%81%BF%E9%9B%A3%E8%99%95%E6%89%80
- 臺中市政府警察局列管防空避難設備統計一覽表
    - https://data.gov.tw/dataset/84017

APP
- 警政服務 App，提供「防空疏散避難專區」查詢，也是用 Google My Map 提供各地區地圖
    - https://www.npa.gov.tw/ch/app/artwebsite/view?module=artwebsite&id=1061&serno=25d5dae3-2a7d-40ea-8016-e567912ac57c

也盤點日本韓國類似的資料集
https://docs.google.com/spreadsheets/d/1OT-Xwx8fSfPdehkgalaF-JtxM5HvHQGLJ2wadFIUpMQ/edit?usp=sharing

### Evacuation Drill / Record

#### 20231230 中正紀念堂捷運站 至 NPOHub 沿途防空避難所外觀拍照

拍照：https://photos.app.goo.gl/BYcLneADj73YArEv7
討論：
- 週六下午路過 9 個點，現況統計：
    - 1 個南門市場週六下午有開
    - 3 個店面週六下午有開
    - 2 個店面週六下午沒開
    - 1 個有管理員且管理員知道此處為防空避難處
    - 2 個住宅大樓，不確定一樓大門是否常態打開
    - 地下室入口明顯程度：3 個在門口看得到樓梯，其他的從外觀看不曉得地下室樓梯在哪
- 延伸討論文件：https://g0v.hackmd.io/@paulpengtw/DigiResiTh0n-home/%2FmKkOC9PLSXi0GZg7uGm1xA
    - 需要 ranking
    - 或是有更多情景設想，例如哪些防空避難空間會更適合作為物資交流、傷患協助的場所，哪些會比較適合該棟建築物民眾避難使用
    - 「防空避難處所」數量比「防災避難收容處所」多，是否可以評估有一些離防災避難處所比較遠的社區，挑選適合的防空避難建物的非地下室空間，作為防災避難使用
    - 例如中正區的南門市場，屬於防空避難，其實建築才剛落成，也屬於公有建築物，很適合水災情境的垂直避難處所，或是地震情境時，此建築物理當相對安全，或是考量南門市場臨著羅斯福路非常空曠的道路空間，適合戶外避難，因為餘震期間街區建物無法確保安全


## 其他災時圖資

日本，透過大貨車、大客車的 GPS 追蹤資料去帶出道路是否中斷的資訊
https://www.its-jp.org/news_info/107997/
https://disaster-system.its-jp.org/map4/map/
日本，呈現加油站的營業狀態
https://www.enecho-ss.meti.go.jp/b/enecho/


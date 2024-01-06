---
title: "地號轉地圖 Land No. Mapper"
tags: 公有地大行動,hackpad
---

# 地號轉地圖 Land No. Mapper

## 構想

1.  一個【輸入代碼段小段地號，產出地圖與圖形】的工具
2.  [簡報](https://docs.google.com/presentation/d/17zoTSPLiG9wZITZkjMXuCD3y14KWRCc78PrCKBSq8fk/edit#slide=id.ga10b939f6_0_2)、[提案影片](https://youtu.be/XGRZavcD0Fc)

▼ 提案影片：

{%youtube XGRZavcD0Fc %}


### 特點

以資料表作管理
- 一般民眾可以使用
- 一般使用者整理好符合 API 所需欄位的資料表後
- 運用 [地號API](https://twland.ronny.tw/) 批次進行地理資料化

線上地圖
- 提供後台資料表編輯
- 除了必要欄位用於 API 呼叫之外，可增加欄位
- 地圖成果能有網址連結

其他
- 圖層管理的功能
- 在地圖上標註意見 (案例：[揪地霸](http://9d8.tw/))

## 整理現有類似的服務


### 關於地籍資料的取得

- ==**NEW!**==Ronny 製作的== ==[http://twland.ronny.tw/](http://twland.ronny.tw/)==！==
- 國土測繪中心
    - 相關專案 posland：[https://github.com/g0v/posland](https://github.com/g0v/posland)
    - 暫無抓下地塊的圖型檔，需要再抓下圖形檔！
    - 將圖形去背、定位等課題
- 段小段地號資料 → 地號畫圖需要參考地籍/段籍圖（全國的似乎還沒有正式公開，台北市也只有[段籍圖的開放資料](http://data.taipei.gov.tw/opendata/apply/NewDataContent?oid=0D9364CD-1677-4EAB-827B-7DA8E37785EB)）→ 得到界線資料 → 配合電子地圖來呈現
> 地號畫圖需要地籍圖，台北市公布的也只有段籍圖而已。
> [name=林立哲]

> 如果只是要看的話，國土測繪中心有提供全國的段籍圖WMTS ([國土測繪圖資網路地圖服務系統](http://maps.nlsc.gov.tw/))
> [name=林立哲]
> 用「單次點擊土地輪廓，查詢地籍資料」的方式釋出成線上地圖[https://maps.nlsc.gov.tw/open/EMAP_B/DMAPS](https://maps.nlsc.gov.tw/open/EMAP_B/DMAPS)

> ronny 正在研究，從 WMS 轉出 GeoJSON 資料，[參考演講](http://youtu.be/1dga12J26Tw?t=19m33s)；ronny 表示，成功率不太高
> [name=che l]


- [地籍圖查詢套繪系統Plugin For QGIS](http://gis.rchss.sinica.edu.tw/index.php?option=com_content&view=article&id=413:plugin-for-qgis&catid=89:2009-07-22-06-28-27&Itemid=132)  中研院之前就有開發過類似的模組，可以用地號查位地籍圖的位置等資訊，現在政府很多圖台也有類似的功能，不過重點在於這些權限目前都還是限縮在政府手上，如果能開放API等使用應該就能解決問題。

- [地籍圖KML資料取得步驟](https://docs.google.com/document/d/1BgTJjLV4glQzbn-NQcWbjOd3KtSbgy5EDTG-Nna8bAc/edit?pli=1)
    - 地籍圖資網路便民服務系統提供KML的功能已經被取消了 囧
        _系統說明:「地籍圖資網路便民服務系統」介接使用Google圖資，因授權與收費(使用者付費)問題，彈出式Google地圖與衛星影像及街景無法繼續提供服務，必須改為背景套疊網路地圖方式提供服務。本系統更版後除了提供TGOS與NLSC及OSM網路地圖背景套疊服務外，也新增了點選查詢同地段之宗地，並提供點選宗地顯示地號及經緯度坐標等功能，您可運用該坐標於任何網路地圖進行定位服務，歡迎多加利用。_
        <囧>

- 可以透過 地政電子資料流通服務網 ( [https://ccs.land.moi.gov.tw/](https://ccs.land.moi.gov.tw/) ) 提出申請，政府機關申請使用應該是不用額外付費，但民間單位就會收取每筆1元的費用（台南市為例）
- 地政司 MOI_WFS_001地籍圖WFS
    - 本服務以土地(宗地)為單位，依地號查詢取得地籍圖WFS(Web Feature Service；網路圖徵服務)，引用介接參數之坐標系統可為WGS84、TWD97、TWD67，一般使用者: 依有效回傳筆數計費，每筆 1 元 回；政府機關使用者: 免費需申請
    - https://cop.land.moi.gov.tw/Services/service_Info.aspx?serviceID=562943EA-0CA9-4758-8127-25DAD3E0605D


#### 文字前處理相關工具

- 以地號作為地址描述的的地址資料，前處理工具
    - https://github.com/travishen/sectw

- 雨蒼> 大家好，因為某些需要，我寫了一個可以把地號完整字串分割開的程式。給大家參考：[https://gist.github.com/billy3321/153935b6c6361194f6a2258e375572c3](https://gist.github.com/billy3321/153935b6c6361194f6a2258e375572c3)


## 工具實作

==**NEW!**====雨蒼製作的====[地藉資料Geojson轉換器](https://github.com/cheweiliu/csv2geojson)====！==


- 應用案例：
    - 雨蒼> 我之前寫的黨產地圖可以給大家參考。
        - [https://github.com/billy3321/billy3321.github.io/tree/master/kmt](https://github.com/billy3321/billy3321.github.io/tree/master/kmt)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4b64c435158ce7f853dbeff251bb1bff)


地號轉地圖 by DZ1984

- 「地號轉地圖 by DZ1984」目前介面：[http://codepen.io/dz1984/full/NqgVPj/](http://codepen.io/dz1984/full/NqgVPj/)
    - 以特定格式輸入，即可呈現該地號對應的輪廓。例如以下：
        - 臺北市,信義段一小段,120
        - 臺北市,信義段一小段,121
        - 臺北市,信義段一小段,430
    - ==**問題回報**====，輸入以下地號，無法產生輪廓==（補充說明：地號來源為天龍特公地頁面，數字共八碼，為光華商場八德路轉角的空地；[新聞](http://udn.com/news/story/8145/927820-%E5%8F%B0%E5%8C%97%E5%B8%8C%E6%9C%9B%E5%BB%A3%E5%A0%B4%E5%81%87%E6%97%A5%E8%BE%B2%E5%B8%82-9%E6%9C%88%E8%8F%AF%E5%B1%B1%E8%A6%8B)）
        - 台北市,成功段一小段,00130004
        - 台北市,成功段一小段,00130000
        - 台北市,成功段一小段,00130002
        - 台北市,成功段一小段,00150001
        - 台北市,成功段一小段,00100002
        - 台北市,成功段一小段,00100005
        - 台北市,成功段一小段,00100001
        - ==驚，我摸索出來以下規則後就可以了耶？==
            - 台北市,成功段一小段,0013-4
            - 台北市,成功段一小段,0013-0
            - 台北市,成功段一小段,0013-2
            - 台北市,成功段一小段,0015-1
            - 台北市,成功段一小段,0010-2
            - 台北市,成功段一小段,0010-5
            - 台北市,成功段一小段,0010-1

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f7eb0d49a09921c3290cb7f727709710)



## 相關構想

- 友善地號資訊查詢界面 by ronny：[https://g0v.hackpad.com/ZrNxaKVn8jt](https://g0v.hackpad.com/ZrNxaKVn8jt)
- 參考文章：[天龍特公地製作過程 byDZ1984](http://dz1984.info/articles/Taipei_POP/)。這篇談到  Google Maps featureStyle、土地資訊與處理事件範例
- 地號的資料上，除了圖塊之外，同時呈現其他描述欄位
- 呈現地號的圖層，可以疊上：
    - 政府公開資料，例如土石流潛勢溪流
    - 自編圖層
- 所需功能：疊圖、調整圖層透明度
- 每一種介面狀態，擁有一個連結
- 相鄰兩塊地，呈現上能否提供：
    - 每一塊都同時呈現其邊界線條
    - 相鄰兩塊地，只呈現最外緣的邊界線條，視覺上只看得到一大塊
- 上載 csv 可將地號以外的欄位內容，整合於 infobox
    - ==提問：==可將此 GeoJson 檔案下載嗎？方便應用，例如丟到 Umap 當成底圖，接著用點線面來規劃公有空地願景，請見[願景測試地圖](https://umap.openstreetmap.fr/zh-tw/map/map_50075#18/25.03983/121.54037)
- chewei> 突然很好奇世界各國的土地管理系統 (台灣是段小段&地號) ，甚至是否有國際通用的可能。
- 開放地籍資料的 \[API 的技術\] 與 \[法律疑慮檢討\]
- 摘自 Dongpo [簡報](https://www.dropbox.com/s/vpwi7vtotlyv7sp/20140819_OpenGeoMeeting.pdf)：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5f01047caaf31a17fa33d5738d006132)
- Sheet>>>polygonAPI>>>Map
- 構想來自[土地許願松](http://www.aypwip.org/webnote/poponfire)


#### 20150613 第拾肆次野百合黑客松

- 雛形：[http://codepen.io/dz1984/full/NqgVPj](http://codepen.io/dz1984/full/NqgVPj)
- 三種方向
    - 『地號圖片』：給地號，得到地號範圍的靜態圖片，方便用於配合議題文章的插圖、都市計畫書圖內文等等。
    - 『大批資料圖層』：類似天龍特公地的地號範圍與相關資料，同時呈現，編輯者用線上可協作表格方式，輸入「縣市/段小段/子母號」得到地號圖形，以及自己定義更多欄位內容，同時與地號圖形一起呈現出來。具體可參考天龍特公地與黨產地圖呈現方式。其他參考：
        - [Excel2Earth](http://excel2earth.blogspot.tw/)  （Excel--->MAP）
    - 『疊圖』：把地號變成地圖，通常還會希望有一些議題圖層來搭配，其「地理格式+內容」可能性蠻多種的。希望這個疊圖也是用線上可協作表格，甚至是與地號表格一起建置於同一個檔案中。





#### Mockup 構想

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b3e0235853306a8c00154ba61ff79c33)


## 蒐集應用情境案例

- 例如碧潭吊橋都更案的地號，與古蹟指定範圍的地號，兩者畫成地圖來對照
    - 完整請見：[碧潭吊橋都更範圍和劃定古蹟範圍 by ronny](https://github.com/ronnywang/sandbox/tree/master/20130805)）。以下擷取 [ronnywang](https://github.com/ronnywang) 繪製的地號範圍作並置，上方為古蹟地號範圍，下方為都市更新案地號範圍：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0200e64c80b5aa7c5e28ea60d26c84e4)

    - Zen Zentree> 程式跑出來的圖超厲害, 不過有一丁點誤差.(ex.146地號沒含進去. 141,563,149,150地界超出國校路) // 會不會是沒有在TWD67/TWD97/WGS84等座標系統間轉換?
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c727815fb8fa7c0c1e98252f63b3c9b6)

- 都市更新範圍地圖：[https://g0v.hackpad.](https://g0v.hackpad.tw/OdKcA5fjbuB)[t](https://g0v.hackpad.tw/OdKcA5fjbuB)[w/OdKcA5fjbuB](https://g0v.hackpad.tw/OdKcA5fjbuB)
- 國民黨黨產地號清冊地圖化（完整請見：[KMT Property](https://g0v.hackpad.com/87CNswL2g7U)）
- 協助友善小農，進行歷年田區範圍的記錄地圖 by tingyu
- 土地開發案，相關新聞應用
- 例如 Taipei 近期釋出的公有地資料集 ! 一般市民就可以用「地號轉地圖」的功能呈現出來
    - [本府經管公有土地清冊(市有、國有)](http://data.taipei/opendata/datalist/datasetMeta;jsessionid=1E5C9230F443B2587867B140378388FF?oid=eb5f3c5c-f0c1-4938-a0f1-886bf5a2fa27)
    - [本府經管未開闢及待處分公有土地清冊](http://data.taipei/opendata/datalist/datasetMeta;jsessionid=1E5C9230F443B2587867B140378388FF?oid=631f0590-6f79-46a7-a689-0551fa496485)
    - [臺北市市有財產委託經營案件明細表](http://data.taipei/opendata/datalist/datasetMeta;jsessionid=1E5C9230F443B2587867B140378388FF?oid=3058983f-199d-4af0-98a7-41a82accc2fa)
    - [臺北市政府財政局經管市有非公用閒置土地清冊](http://data.taipei/opendata/datalist/datasetMeta?oid=e5e450ea-a283-470a-8659-18381671d7b8)
    - [臺北市政府財政局經管市有非公用閒置建物清冊](http://data.taipei/opendata/datalist/datasetMeta?oid=1cebd2e1-df54-4508-97f7-3217753c6d32)




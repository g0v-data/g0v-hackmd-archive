# 違章工廠回報系統第122次小聚

###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20220413 19:30 (GMT+8)
地點：線上、實體hybrid
線上：https://meet.google.com/coc-vuaa-ykz
實體地點：地球公民基金會台北辦公室（北平東路28號9樓之2）

## 參與者簽到
- deeper
- yellowsoar
- dotsea
- ael
- oriyar
- xtim
- CRW
- peii

### 線上


## 議題近況
### 近期update
| 月份 | 回報件數 |
| ---- | ---- |
|2020.11| 24|
|     12| 46|
|2021. 1| 49|
|      2| 55|
|      3| 53|
|      4|110|
|      5| 65|
|      6|109|
|      7| 60|
|      8| 90|
|      9| 59|
|     10|104|
|     11| 82|
|     12|144|
|2022. 1| 73|
|      2|114|
|      3|191|
|      4| 27|

## 議程
19:30-20:00 新手 onboarding、議題進展
20:00-20:15 整體議題、跨網站
- g0v 黑客松 recap
20:15-20:45 大家來找廠 SpotDiff
- 後端數據分析（gold standard)
- SpotDiff debug and UI enhancement
- 分享頁面與文案

20:45-21:00 最後加點（podcast?桐花松？）
21:00～ disfactory.tw UI improvement 討論 

## 會議記錄

### 19:30-20:00 新手 onboarding、議題進展 @peii
### 20:00-20:15 整體議題、跨網站
- g0v 黑客松 recap （ @yellowsoar @bdon 似乎做了一些基礎建設）
### 20:15-20:45 大家來找廠 SpotDiff
- 後端數據分析（gold standard) @酸酸的
- SpotDiff debug and UI enhancement @David Fu
- 分享頁面與文案 @Tin @Oriyar
- 隱私權政策
### 20:45-21:00 最後加點（podcast?桐花松？）@Oriyar@peii
### 21:00～ disfactory.tw UI improvement 討論 @yukai @SL @deeper @ael

=====

### 1. crw 提出可以 mapping 工業用電的資料和 Disfactory 的資料
https://egis.moea.gov.tw/OpenData 

農地用水量會跟工廠聚集正相關
想疊起來去判斷哪些地方的用水量，用水量高但不屬於經濟部公告工業區的範圍，也許可以懷疑

花壇鄉：沿著台一線，附近都是 24 小時光照的農業（可以先去看一下）
再跟其他魚米之鄉比較

經濟發佈區劃設原則

有可能違章工廠是普查時有抓到，但是工商登記不直接跟工廠位置有關（違章還是會有可能工商登記）

yellowsoar 讓原本的經緯度資料可以用 GeoJson 了，加上 SRIO, POINT


### 2. Cluster 和分縣市顯示

https://github.com/Disfactory/frontend/issues/121

分三層：
- 縣市（不做鄉鎮市層級區分）
- cluster
- 獨立 pin (Zoom level > 16)

使用原本開給 about.disfactory.tw 的 API

### 酸酸的要測試-> 用 Netifly
有 staging 的網址可以測試嗎？

### SpotDiff

一定要改：
https://github.com/Disfactory/SpotDiffFrontend/issues/80

如何找到 SpotDiff該張地圖的經緯度：
-> inspect
-> application
-> local storage
-> search `lat` or `lng`


Gold standard 討論的結果：
https://github.com/Disfactory/SpotDiff/issues/30


`gold_standard_status`
- 太模糊無法準確判斷的 => disable => `gold_standard_status == 3`
- @deeper 會再給 @酸酸的 要 disable 的 gold standards 題組(要更改為 `gold_standard_status == 3`) 
- @deeper 會再給一批新的比較明確判斷的 gold standard 題組給 @酸酸的 （`gold_standard_status == 0`）
- 舊的已辨識的資料，沒有過 gold standard 的，就先放著（目前已被判定為 `gold_standard_status == 2`），之後可以根據 timestamp 找出 April 9-13 的資料（但 timestamp 目前格式不是人眼可閱讀的日期時間格式，需要再改）
- 有無建物和有無擴建，維持沒有「不知道」的選項。這個比第一題好辨識。

後端資料：
- 目前第一批 1000 筆資料辨識完之後（2017, 2020），想要用 2021 年的衛星空照圖資料(2017, 2021) @deeper 再給 @酸酸的 和 @davidfu 再拉


## 待辦&待討論事項

- 下次 check points
    - Disfactory.tw: 政府回應 followup status 上 produc- tion
    - Before tag 顯示錯誤 https://github.com/Disfactory/SpotDiffFrontend/issues/80
    - Update gold standards https://github.com/Disfactory/SpotDiff/issues/30
    - 地圖劃框框 https://github.com/Disfactory/SpotDiffFrontend/issues/67
- 下次討論

Cluster
https://github.com/Disfactory/frontend/issues/121

- deeper
    - GA研究

- 累積待討論
    - [motion graphic腳本](/MmcrFV3AS4qnYESGCEvBug)
- 累積待辦事項
    - 寄東西給未曾謀面的捧油



## 總文件庫
- 「大家來找廠」project spot.disfactory.tw
    - [計畫整體樣貌](https://g0v.hackmd.io/@yukaii/Disfactory/%2F5QH2TlaXQR21wMo3UIKZug) 
    - [spec](https://github.com/Disfactory/satellite/issues/2#issuecomment-866704442)
    - [mockup](https://www.figma.com/proto/TVAEC28E3ojabGHc8BawbI/%E8%A1%9B%E6%98%9F%E7%A9%BA%E7%85%A7%E5%9C%96?node-id=776%3A140800&scaling=min-zoom&page-id=599%3A433&starting-point-node-id=635%3A885)
    - [期程](https://www.notion.so/agrifactory/cf057f3b46fe4a738523b500c967ef5d?v=987e3e087e114c679142dab0c36af702)
    - [前端測試](https://disfactory-spotdiff.netlify.app/)
    - [about 設計](https://www.figma.com/file/vnvt7JjXrRcXZlqLoW2vCZ/About.Disfactory?node-id=575%3A3533)
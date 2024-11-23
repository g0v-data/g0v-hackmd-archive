---
title: "g0v 零時空汙觀測專案-網站開發共筆"
tags: hackpad
---

# g0v 零時空汙觀測專案-網站開發共筆

此區為[g0v 零時空汙觀測專案](https://g0v.hackmd.io/QeNRXR7XQQK7JU0vRrnEYA)的子分區，提供網站方面開發共筆

⚠️2024/11/23更新：airmap.g0v.tw網站已停止運作，將申請釋放網域或轉靜態頁面

## 網站開發方向大綱


### 欲整合之目標

- 即時觀測資料 (包括官方與非官方測站的觀測資訊)
- 即時排汙資料 (包括工廠排汙, 火電廠排汙, 交通排汙等資訊)
- 即時氣象資料 (包括風力, 風速, 逆溫層效應)

### 資料呈現方式目標

- 以地圖為主軸的視覺化 (包括站點圖標,  heatmap渲染, 風力線條動畫)
- 時間軸

### 應用idea（朝向無敵即時資訊網邁進！？）

- **台灣版的**[**達**](http://hedleyindex.sph.hku.hk/html/tc/index.php)[**裡**](http://hedleyindex.sph.hku.hk/html/tc/index.php)[**指數**](http://hedleyindex.sph.hku.hk/html/tc/index.php)
    - [**相關報導**](https://www.twreporter.org/a/air-pollution-honkong)**：**空氣品質變好了  香港做對的幾件事

## 網站目前開發狀態

⚠️2024/11/23更新：本專案預計於2024/11/30終止airmap.g0v.tw網頁服務

\[2018.12.29\] 網址遷移至g0v.tw- [https://v5.airmap.g0v.tw/#/map](https://v5.airmap.g0v.tw/#/map)
github repo: [https://github.com/Aspertw/airmap-laravel](https://github.com/Aspertw/airmap-laravel)

\[過期\] g0v零時空汙觀測網站新版- [http://airmap.g0v.asper.tw](http://airmap.g0v.asper.tw)
github repo: [https://github.com/Aspertw/Airmap_v4](https://github.com/Aspertw/Airmap_v4)

\[過期\] g0v零時空汙觀測網站實作測試已上線\- [http://g0vAirMap.3203.info](http://g0vAirMap.3203.info)
github repo: [https://github.com/immortalmice/Real-time-Air-Quality-Map](https://github.com/immortalmice/Real-time-Air-Quality-Map)

### 資料處理:

輸入:
- LASS: [http](https://www.facebook.com/groups/1607718702812067/permalink/1808159682767967/)[s://www.facebook.com/groups/1607718702812067/permalink/1808159682767967/](https://www.facebook.com/groups/1607718702812067/permalink/1808159682767967/)
- ProbeCube: [http://3203.info/Data/All_last.json](http://3203.info/Data/All_last.json)
- AirBox: [~http://nrl.iis.sinica.edu.tw/LASS/last-all-airbox.json~](http://nrl.iis.sinica.edu.tw/LASS/last-all-airbox.json)
- EPA:
    - (g0v mirror) [http://g0v-data-mirror.gugod.org/epa/aqx.json](http://g0v-data-mirror.gugod.org/epa/aqx.json)
    - (asper_hsu) [http://taqm-hourly.appspot.com/today.json](http://taqm-hourly.appspot.com/today.json)
    - Miaoski:
    - [https://thingspeak.com/channels/83508](https://thingspeak.com/channels/83508)
    - [https://thingspeak.com/channels/88846](https://thingspeak.com/channels/88846)
- ~Webduino:~ [~http://nrl.iis.sinica.edu.tw/LASS/last-all-webduino.json~](http://nrl.iis.sinica.edu.tw/LASS/last-all-webduino.json) 已無人維護
- 中研院與 LASS 維護資料: [https://sites.google.com/site/pm25opendata/open-data](https://sites.google.com/site/pm25opendata/open-data)
輸出:
- 全部: [http://g0vairmap.3203.info/Data/all_last.json](http://g0vairmap.3203.info/Data/all_last.json)

### 資訊框內各資料來源LOGO介紹連結:

LASS: [https://github.com/LinkItONEDevGroup/LASS](https://github.com/LinkItONEDevGroup/LASS)
ProbeCube: [https://github.com/Lafudoci/ProbeCube](https://github.com/Lafudoci/ProbeCube)
AirBox: [http://](http://pm2.5.taipei/about.jsp)[pm2.5.taipei/about.jsp](http://pm2.5.taipei/about.jsp)
EPA: [http://taqm.epa.gov.tw/taqm/tw/Pm25Index.aspx](http://taqm.epa.gov.tw/taqm/tw/Pm25Index.aspx)
Pilot: [https://github.com/miaoski/pm25](https://github.com/miaoski/pm25)


## To-Do List (已有工程師規劃填坑區)

- 2016.08.06 g0v黑客松討論
    - 新舊站移轉事項:
        - 後端資料抓取的工作會在新站建立一套獨立運作，但舊站不會立即下線供工程師測試使用。
        - 舊站immortalmice繼續改善後端不穩定的問題。
        - 日後以asper新站去更新及曝光。
        - (done) 新站保留舊站的自造者招募頁面。
        - 建置獨立自造者提交資料即自動上線的提交頁面(提交後會被分類至未審核群組，待管理員審核後才會移入使用者預先命名的群組)
            - preset site gorup
        - 舊站須能接收新站的獨立自造者更新站點
    - airbox資料串接事項:
        - 著力點: edimax官網地圖沒有做資料保護，下游資料串接亦無需要求保護
        - 可建議edimax建立("有用的")api token系統方便做下游資料利用管理

- **拆站目標區:**
    - [x] 空品站
        - [x] ronny已拆: [http://stormy-lake-70176.herokuapp.com/](http://stormy-lake-70176.herokuapp.com/)
        - [x] au已拆: [https://gist.github.com/audreyt/4175d05c0e394acc3c5a](https://gist.github.com/audreyt/4175d05c0e394acc3c5a)
    - [x] 空氣品質即時值查詢(包括溫濕度各種測值但不含PM2.5) [http://taqm.epa.gov.tw/taqm/tw/HourlyData.aspx](http://taqm.epa.gov.tw/taqm/tw/HourlyData.aspx)
        - [x] asper_hsu已拆 [http://taqm-hourly.appspot.com/](http://taqm-hourly.appspot.com/)
    - [x] 細懸浮微粒即時值查詢(PM2.5) [http://taqm.epa.gov.tw/pm25/tw/HourlyData.aspx](http://taqm.epa.gov.tw/pm25/tw/HourlyData.aspx)
        - [x] asper_hsu已拆 [http://taqm-hourly.appspot.com/](http://taqm-hourly.appspot.com/)
    - [ ] Airbox API（未公開）
        - [ ] g0v Token: EC519D9C-6363-4FBE-BEDE-2B10B18B4670 (請勿用於非g0v上)
        - [ ] ~列表—~[~https://airbox.edimaxcloud.com/devices?token=EA81A1FA-8EDB-4CA0-B07B-A881C74B0401~](https://airbox.edimaxcloud.com/devices?token=EA81A1FA-8EDB-4CA0-B07B-A881C74B0401) (已經失效)
        - [ ] ~紀錄—~[~https://airbox.edimaxcloud.com/query_history?id=~](https://airbox.edimaxcloud.com/query_history?id=)[~{~](https://airbox.edimaxcloud.com/query_history?id=&token=EA81A1FA-8EDB-4CA0-B07B-A881C74B0401)~id\]&token=EA81A1FA-8EDB-4CA0-B07B-A881C74B0401~ (已經失效)
- [ ] 改善右下角更新資訊呈現


## 許願區或其他疑問待討論 (等待工程師跳坑區)

- **資料相關區**
    - [x] 環保署的開放資料發佈時間會比觀測發佈延遲一個小時，而觀測站每次發佈又是上一小時的觀測資料，常常呈現的資料都已經是兩個小時之後，無法真正即時呈現，或許還是得想辦法拆原始的環保署測站資料，或是有人能去協調環保署同步測站發佈和開放資料平台發佈的時間。
        - 環保署空品資料發佈的流程是：
            感測器----->TQAM([空品監測網](http://taqm.epa.gov.tw/taqm/tw/default.aspx)的Server)----_每整點發佈_---->[CDX](http://cdx.epa.gov.tw/CDX/main.aspx)平台---_過幾分鐘_---->OpenData介接並Publish資料(也是每個整點)。因此卡在這每整點發佈及各平台傳輸訂閱時間的問題，所以真的收到資料已經兩小時之後～目前會再詢問環保署能否改善這狀況，真的做到即時傳輸與發佈。
> 太好了!! 如果能夠從資料源頭解決的話是最好的解法了!!
> [name=Chun-hsi T]

> 不過現在發現問題是開放平台實在太不可靠，每一個禮拜就掛會個一兩次
> [name=Chun-hsi T]

> 哈哈哈，也只好繼續寫e言堂......哀
> [name=Lee H]

> 請大家到[環保e言堂](http://forum.epa.gov.tw/EPASPS/SPSA/SPSA01001.aspx)，寫信給署長，要求發佈即時資料！
> [name=Lee H]

    - [x] 環保署的測站有觀測[氣溫濕度](http://taqm.epa.gov.tw/taqm/tw/HourlyData.aspx)，但卻沒包含在開放資料平台的資料中，可能得自己拆或去向環保署要求開放。

- **視覺化區**
    - [x] 風力視覺化有待整合[https://github.com/cambecc/earth](https://github.com/cambecc/earth)，這難度有點高但是非常值得去做。
    - [ ] 工廠排汙資料待整合，要想一下如何在地圖上呈現比較好。
    - [x] 火力電廠基載待整合，要想一下如何在地圖上呈現比較好。
    - [ ] 從google map移植到Openstreetmap作為圖資來源或許比較恰當，但在評估這坑會多大中。
> 移植是說圖磚改用 OpenStreetMap？
> [name=yellowsoar]

> 是的
> [name=Chun-hsi T]


- **附加功能區**
    - [ ] 可直接於網站介面點選顯示測站資訊的json api
    - [ ] 可於網頁上新增自造站點
    - [ ] 對於螢幕較小的筆電/手機做畫面最佳化
    - [ ] **台灣版的**[**達**](http://hedleyindex.sph.hku.hk/html/tc/index.php)[**裡**](http://hedleyindex.sph.hku.hk/html/tc/index.php)[**指數**](http://hedleyindex.sph.hku.hk/html/tc/index.php)**，**[**相關報導**](https://www.twreporter.org/a/air-pollution-honkong)
        - 建置達理指數，需要哪些材料？石國順說明，所需要的材料可分為下列幾項。
        - [ ] **1\. 即時的空氣汙染濃度，以及濃度超出世界衞生組織標準的幅度。**
        - [ ] **2\. 死亡人數、住院天數和看診次數。**
            - 評估空氣汙染所造成的醫療成本，所以須排除意外死亡（如車禍）等原因。
        - [ ] **3\. 該地區因空氣汙染而死亡、住院的風險。**
            - 比方說，每一立方米空氣中的PM10增加10微克時，會增加多少百分比的死亡風險。達理指數採用華人地區的研究。
        - [ ] **4\. 對於患者來說，看醫生的成本。**
        - 如：掛號費、醫藥費、住院費、交通成本等等。
        - [ ] **5\. 看診、住院、提早死亡所損失的生產力。**
        - 根據當地就業率、薪資中位數計算。
        - [ ] **6\. 民眾願意花多少錢避免死亡、住院。**
        - 這是衡量人命值多少的研究，香港的研究結論是每人願意花1千萬港幣（4千萬台幣）避免死亡。「但這是以前的研究，現在人命應該升值了，」香港大學公共衞生學院高級研究助理曾希達補充。
- **已知Bug**
    - [ ] IE瀏覽器使用者點選原始資料時無法正確顯示
    - [ ] 圖例色票不正確
    - [ ] 地圖載入時會有一段空白畫面，待解決
    - [x] 後端抓資料偶爾會停掉，待解決


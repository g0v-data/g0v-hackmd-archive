---
title: "水"
tags: GIS, 水資源, hackpad
---

# 水

- [hackpad 內容比較新](https://g0v.hackpad.tw/yRRVlfb5oJg)
- 單則素材
    - 水體汙染資料 https://g0v.hackmd.io/LVHnV9ZkQL6WcCkPpbMcmw


---
有質、有量、有水文

## 構想

基本目標：台灣地區的水文資料動態彙整與視覺化，形成水現況/即時循環圖，讓一般民眾了解水資源現況、用水、洪旱災、將水文資料實質彙整於在地流域地理空間呈現上，基於 gov open data 的實地水文教材。

## TODO

- 確立水循環邏輯與水資源的表達方式
    - 依照集水區與流域？
        - 翡翠水庫...
- 蒐集資料
    - 依照前述水循環邏輯，盤點國內外既有的水量資料集、資料負責單位、資料說明、資料格式、資料集網址...（參考：[OSM 整理的](https://docs.google.com/spreadsheets/d/tA2Vu_ajWywAx3fjsaM9Rug/htmlview)[OSM 整理的 GINS 圖資清單](https://docs.google.com/spreadsheets/d/tA2Vu_ajWywAx3fjsaM9Rug/htmlview) [NGIS 圖資清單](https://docs.google.com/spreadsheets/d/tA2Vu_ajWywAx3fjsaM9Rug/htmlview)）
    - [多模式水文水理氣象整合平台建置工作](http://www.ncdr.nat.gov.tw/Files/image/20150813154931764/files/121.pdf)
- 確認資料集之間的關係
    - 例如上下游位置、水系支流系統、設想入滲逕流等水利行為
    - 學理與運算程式 ?
        - 徐昇式法計算方法，請參考[文獻](http://tccip.ncdr.nat.gov.tw/NCDR/Shared_Doc/papers/%E5%BE%90%E6%98%87%E5%A4%9A%E9%82%8A%E5%BD%A2%E6%B3%95%E8%AA%AA%E6%98%8E.pdf)(PDF)
        - 颱洪淹水雲端系統：此系統可以協助洪氾保險的擬訂、災情受損評估 ...（[新聞](http://www.chinatimes.com/newspapers/20141128000154-260210)）
        - 洪水解析系統 (Integrated Flood Analysis System, IFAS)是一個免費的淹水模擬軟體，內建有全球衛星定位與地形資料，使用者可以藉由輸入降雨資料，透過系統分析而模擬出洪水危險地區，一般民眾皆可透過此軟體模擬洪水危險地區。軟體網站：[http://www.icharm.pwri.go.jp/research/ifas/](http://www.icharm.pwri.go.jp/research/ifas/)
        - 降雨逕流淹水模式 (Rainfall-Runoff-Inundation Model, RRI)是免費的降雨逕流模擬軟體，內建有二維地形模擬功能，使用者將降雨量資料與數值地形模型輸入後，透過軟體可以模擬出雨水逕流狀況雨水量高度。
        - 多維洪水模擬平台 國家研究院台灣颱風洪水研究中心
        - 定量降雨預報 國家研究院台灣颱風洪水研究中心
            - [http://www.ttfri.narl.org.tw/study02A.html](http://www.ttfri.narl.org.tw/study02A.html)
        - 定量降雨預報結果與逕流河道模擬 國家研究院台灣颱風洪水研究中心，本系統結合定量降雨預報結果與逕流河道模擬技術，進行全流域之即時降雨逕流模擬實驗
            - [http://www.ttfri.narl.org.tw/study03A.html](http://www.ttfri.narl.org.tw/study03A.html)
        - 台灣都會區淹水評估系統 國家研究院台灣颱風洪水研究中心
            - [http://www.ttfri.narl.org.tw/study03D.html](http://www.ttfri.narl.org.tw/study03D.html)
        - [FEWS_Taiwan](https://plus.google.com/117804316605140411553)：協助洪水預報、水情資訊供應，所用圖資：土地利用、通用版電子地圖、土壤類型、數值高程模型、水位站圖層、雨量站圖層、村里圖層
        - （[研擬淡水河流域都市發展與流域防災整合案總結報告書](http://www.udd.gov.taipei/pages/detail.aspx?Node=443&Page=5484)）本計畫採用 PC-SWMM 對七堵都市計畫區雨水下水道系統進行分析洪患定量分析， SWMM(Storm Water Management Model) 為美國環保署(EPA U.S.)1969~1971 年 所發展，主要依據變量流理論以一維連續方程式與動力波理論為基礎，依水流流程 之特性，將模式分成地表逕流(RUNOFF)與排水幹管輸水(EXTRAN)兩部份。 RUNOFF 模組可模擬排水系統集水區內每一集水分區之降雨逕流歷線，EXTRAN 模 組為一動態水理演算模式。地表逕流是指雨量降落地面後，流入各排水幹管前之水 流狀況，模擬方式是經由動力波逕流演算，計算匯入排水人孔之水流流量歷線。幹 管輸水部份則是利用疊代法求解動力波方程式，計算各排水幹管系統之流量以及溢 出人孔之水量。PC-SWMM 由加拿大 CHI(Computational Hyhraulics Int.)發展完成， 其以 SWMM 模式為核心，再輔以視窗化界面功能及簡易 GIS 模組功能。因此， PC-SWMM 使模式更能符合實際之情況，以真實表現當地土地利用、地形、地貌、 道路、鐵路、水路及各種結構設施（如閘門、涵洞、抽水站等）對淹水之影響，再 以此建立之模式，輸入集水區之降雨歷線（或入流量歷線）與邊界條件，藉以模擬 現況之淹水情形。
        - SWMM(Storm Water Management Model) 為美國環保署(EPA U.S.) [https://www.pcswmm.com/Downloads/USEPASWMM](https://www.pcswmm.com/Downloads/USEPASWMM)
        - 河川系集水理模式建置與相關應用
            - [http://epaper.wra.gov.tw/Article_Detail.aspx?s=C81CF9F0D03B3A1F](http://epaper.wra.gov.tw/Article_Detail.aspx?s=C81CF9F0D03B3A1F)
        - [水利工程三維數值模擬分析](https://www.dropbox.com/sh/ylrg4vnx6icpfb4/AACvLXplsER47zB05mpRbyeka?dl=0)
        - WEAP: Water Evaluation And Planning System [https://www.youtube.com/watch?v=D7YS1miuSZM](https://www.youtube.com/watch?v=D7YS1miuSZM)
        - [https://www.facebook.com/taiccat/posts/964453713621169](https://www.facebook.com/taiccat/posts/964453713621169)
        - Floodplain Modeling Using HEC-GeoRAS.
            - Part 1: [https://watergis.wordpress.com/2012/05/01/toulumne-meadows-floodplain-modeling-using-hec-georas-part-1/](https://watergis.wordpress.com/2012/05/01/toulumne-meadows-floodplain-modeling-using-hec-georas-part-1/)
            - Part 2: [https://watergis.wordpress.com/2012/07/12/toulumne-meadows-floodplain-modeling-using-hec-georas-part-2/](https://watergis.wordpress.com/2012/07/12/toulumne-meadows-floodplain-modeling-using-hec-georas-part-2/)
        - The Arc Hydro Toolset is a suite of tools which facilitate the creation, manipulation, and display of Arc Hydro features and objects within the ArcMap environment. The tools provide raster, vector, and time series functionality, and many of them populate the attributes of Arc Hydro features.
            - [http://www.amzaz.info/2015/12/downlaod-all-version-of-archydro-arcgis.html](http://www.amzaz.info/2015/12/downlaod-all-version-of-archydro-arcgis.html)
        - [地下水特論 Special Topics in Ground Water](https://nol.ntu.edu.tw/nol/coursesearch/print_table.php?course_id=521%20M5660&class=&dpt_code=5213&ser_no=72100&semester=104-2&lang=CH)
            - 本課程之目的在於根據地下水課程中所學到之基本理論為基礎，繼續研究地下水中水流及污染物傳輸控制方程式之解析解與數值解方法、參數檢定方法、試驗設計方法以及地質統計與序率地下水分析等方法。希望經由此課程之訓練能對學生從事進一步之研究與實際工作有所幫助。
        - 台灣地下水資源使用與水質現況
            - [http://www.cv.nctu.edu.tw/chinese/teacher/Ppt-pdf/teacher13\_shan/gwater\_doc.pdf](http://www.cv.nctu.edu.tw/chinese/teacher/Ppt-pdf/teacher13_shan/gwater_doc.pdf)
        - 先前我們介紹了如何利用雷達來進行定量降雨估計，但是否每次的降雨事件都會造成淹水呢，這個問題就得仰賴水利工程師來進行水文模擬了，颱洪中心吳明璋副研究員將介紹近年來水文模擬的新技術-類神經網路，詳見颱洪中心科普網連結。 [http://www.ttfri.narl.org.tw/sp/?p=1679](http://www.ttfri.narl.org.tw/sp/?p=1679)
        - （[來源](http://grbsearch.stpi.narl.org.tw/GRB_Search/grb/show_report.jsp?id=2328754)）淹水潛勢模擬部分,本研究之降雨雨型分析採用簡單尺度不變性高斯馬可夫 雨型(Simple Scaling Gauss–Markov, 簡稱 SSGM)建立,進行定量降雨 24 小時 累計雨量 150~1200 公釐之淹水潛勢模擬,為一符合隨機碎形特性與高斯馬可夫 歷程的無因次(dimensionless)雨型(鄭克聲等,1999)。SSGM 雨型(許恩菁, 1999)以非定常性一階高斯馬可夫歷程(nonstationary first–order Gauss–Markov process)描述無因次年最大值事件,具備馬可夫歷程特性,滿足尖峰降雨量統計 特性,且具有最大概似度,其優點為:
            - 符合尖峰降雨百分比之統計特性。
            - 降雨量之時間分佈與年最大暴雨事件之歷程特性一致。
            - 雨型因暴雨類型而異。
            - 經適當之尺度轉換後,雨型可適用於不同延時之設計暴雨。
            - 建立雨型所使用之降雨事件與建立降雨強度延時–頻率曲線所使用之降 雨事件大致相同。
        - [http://scitechvista.most.gov.tw/zh-tw/Articles/C/0/1/10/1/402.htm](http://scitechvista.most.gov.tw/zh-tw/Articles/C/0/1/10/1/402.htm)
        - [http://water.noaa.gov/about/nwm](http://water.noaa.gov/about/nwm)


### 資料包括（歡迎列舉）


水資料
[https://maoredman.github.io/water_alliance/data.html](https://maoredman.github.io/water_alliance/data.html)

氣象資料
- 中央氣象局  (預報、氣溫、雨量、蒸發散)
    - 潮位統計：[http://www.cwb.gov.tw/V7/climate/marine_stat/tide.htm](http://www.cwb.gov.tw/V7/climate/marine_stat/tide.htm)
流域各區資料
- 林務局 (林地區位的相關資料)
    - 霧林：[http://e-info.org.tw/node/107458](http://e-info.org.tw/node/107458)
- 地調所 (地質與水文)
    - 地下水區資料：[http://hydro.moeacgs.gov.tw/011-03.htm](http://hydro.moeacgs.gov.tw/011-03.htm)
- 水利署  (集水區、流域、水庫、流量、地下水  、伏流水、水權)
    - 水資料 [https://opendata.wra.gov.tw/Default.aspx](https://opendata.wra.gov.tw/Default.aspx)
    - [http://wise.wra.gov.tw/](http://wise.wra.gov.tw/)
    - 水利署 [水利資料整合雲平台](https://data.wra.gov.tw/Default.aspx)
    - [http://gic.wra.gov.tw/gic/HomePage/Index.aspx](http://gic.wra.gov.tw/gic/HomePage/Index.aspx)
    - 水庫即時水情 [http://water.taiwanstat.com/](http://water.taiwanstat.com/)
    - 台灣水庫近期蓄水量圖：當下及近三個月的水庫蓄水率走勢。剩餘週數取最近七天用水量之平均除當前蓄水量做預估，若近期波動大會失準，因此僅供參考。 資料來源：[經濟部水利署](http://fhy.wra.gov.tw/ReservoirPage_2011/StorageCapacity.aspx) / [資料截取程式](http://github.com/infographicstw/reservoir-history-crawler)（[http://data.infographics.tw/viz/reservoir/](http://data.infographics.tw/viz/reservoir/)）
        - [http://webb-lu.github.io/chuikhoTW/](http://webb-lu.github.io/chuikhoTW/)
> 作了視覺化之後發現已經有人在討論這部分了 ⊙⊙ (沒資料的話ctr+r refresh一下會有圖)
> [name=呂蹤影]

        - [_http://eric848976.ddns.net:8888/_](http://eric848976.ddns.net:8888/)
> _這個不知道對你們有沒有幫助 ，不能顯示可以通知一下_
> [name=王崇銘]

    - 水庫：[http://water.taiwanstat.com/](http://water.taiwanstat.com/)
    - 經濟部水利署各項用水統計資料庫：[http://wuss.wra.gov.tw/](http://wuss.wra.gov.tw/)
    - 各地方水資源管理局的數據與資料
    - [台灣地區民國101年蓄水設施水量營運統計報告.pdf](http://wuss.wra.gov.tw/annualreports/20140017%E7%AC%AC%E4%BA%94%E9%83%A8%E5%88%86%20%E5%8F%B0%E7%81%A3%E5%9C%B0%E5%8D%80%E6%B0%91%E5%9C%8B101%E5%B9%B4%E8%93%84%E6%B0%B4%E8%A8%AD%E6%96%BD%E6%B0%B4%E9%87%8F%E7%87%9F%E9%81%8B%E7%B5%B1%E8%A8%88%E5%A0%B1%E5%91%8A.pdf)
    - 水力發電：
    - 溫泉：[http://newspring.wra.gov.tw/](http://newspring.wra.gov.tw/)
- 地方政府 (水利&環保局)
- 各地水利會（用水資訊）
- 用水資料 (科學園區、工業用水、民生用水、農業用水)
- 縣市的區排、下水道、河川資料
- 汙水資料
- 野溪整治工程資料蒐集
    - [https://g0v.hackpad.tw/xxAowvCx0if](https://g0v.hackpad.tw/xxAowvCx0if)
- 濕地資料
    - [https://g0v.hackpad.tw/gTp0Gl6834m](https://g0v.hackpad.tw/gTp0Gl6834m)
- 台灣瀑布與野溪溫泉地圖 by 跟著小飛玩 Follow Xiaofei
    - [https://goo.gl/zAA5cQ](https://goo.gl/zAA5cQ)
- 漁業署的水文 OpenData 漁塭
- 氣候變遷 TCCIP [http://tccip.ncdr.nat.gov.tw/NCDR/main/index.aspx](http://tccip.ncdr.nat.gov.tw/NCDR/main/index.aspx)
- 各項地下水資料來源
    - 水利署
        - 歷史地下水查詢 [http://gweb.wra.gov.tw/hyis/](http://gweb.wra.gov.tw/hyis/)
        - 地下水水位年度統計 [http://data.gov.tw/node/22224](http://data.gov.tw/node/22224)
    - 環保署
        - 環境及生態監測／地下水 [http://erdb.epa.gov.tw/Subjects/MetaSubject.aspx?topic1=%E6%B0%B4&topic2=%E7%92%B0%E5%A2%83%E5%8F%8A%E7%94%9F%E6%85%8B%E7%9B%A3%E6%B8%AC&subject=%E5%9C%B0%E4%B8%8B%E6%B0%B4](http://erdb.epa.gov.tw/Subjects/MetaSubject.aspx?topic1=%E6%B0%B4&topic2=%E7%92%B0%E5%A2%83%E5%8F%8A%E7%94%9F%E6%85%8B%E7%9B%A3%E6%B8%AC&subject=%E5%9C%B0%E4%B8%8B%E6%B0%B4)
    - 地調所
        - 地調所水文地質資料庫 [http://hydro.moeacgs.gov.tw/011-013.asp?FindId=010&FindName=%25A5x%25A5_%25AC%25D6%25A6a](http://hydro.moeacgs.gov.tw/011-013.asp?FindId=010&FindName=%25A5x%25A5_%25AC%25D6%25A6a)
        - 地質常用WMS服務2013.kml [http://gwh.moeacgs.gov.tw/mp/Portal/wms.cfm](http://gwh.moeacgs.gov.tw/mp/Portal/wms.cfm)
    - 台北市政府環保局
        - 臺北市地下水監測結果
            - 資料集描述： 提供臺北市地下水監測結果；主要欄位說明： 監測井編號及井址、採樣時間、天氣狀況、採樣水位、水溫、pH、導電度、氨氮、氯鹽、硫酸鹽、硫酸鹽氮、總溶解固體、總硬度、鎘、銅、汞、鉛、鋅、砷、大腸桿菌群
            - [http://data.taipei/opendata/datalist/datasetMeta?oid=4e4d4023-1b84-4cf2-806a-90c82576efb4](http://data.taipei/opendata/datalist/datasetMeta?oid=4e4d4023-1b84-4cf2-806a-90c82576efb4)
    - 土地開發行為的地下水鑽探資料
        - 目前開發過程一般只會針對地質進行鑽探資料進行分析與紀錄, 而地下水深度與資料來源主要依賴水利署與台糖 監測井提供資訊( 營建工程施工過程中地下水抽水量資訊, 在施工規劃報告會有類似 "基地抽排水計畫書" 說明可能抽排水量，但實際各工地在施工時抽排水量仍有有待確認主要是因為目前監測數據相當缺乏) ,先前研究資料可參考[http://ecology.org.tw/epaper/view.php?id=367](http://ecology.org.tw/epaper/view.php?id=367) 但目前營建署與水利署在這一方面的溝通可能還有待加強。
        - 臺北市永春陂 [https://www.facebook.com/groups/349236221800216/files/](https://www.facebook.com/groups/349236221800216/files/)
水質資料
- 環保署 (水質)
    - [環保署 CDX](http://cdx.epa.gov.tw/CDX/StandardDownload.aspx)
    - [http://real.taiwanstat.com/river/](http://real.taiwanstat.com/river/)
    - [http://real.taiwanstat.com/rain-ph/](http://real.taiwanstat.com/rain-ph/)
- 肥料汙染水質之資料 (農委會)
飲用水系統
- 飲用水水源水質保護區範圍圖 [https://data.gov.tw/dataset/6377](https://data.gov.tw/dataset/6377)
- 公共飲水點之飲水地圖 [https://watermap.teia.tw/](https://watermap.teia.tw/)
水商品
- 食藥署
    - 食品製作用水、瓶裝水、加水站產業...?
- 關稅署
    - 含水產品進出口貿易資料

資料備註與討論
- 月平均降水使用資料為CRU (Climatic Research Unit) version 2.1，僅有陸地區域的降水，網格點大小為0.5°×0.5°
- 根據降尺度後（25km*25km）的氣候變遷情境網格資料，評估流域在氣候變遷A1B情境下近未來(2020~2039)河川流量的衝擊。情境概述情參考：[未來發展與排放情境](http://tccip.ncdr.nat.gov.tw/NCDR/Shared_Doc/papers/IPCC%E6%8E%92%E6%94%BE%E6%83%85%E5%A2%83%E6%A6%82%E8%BF%B0.pdf)(PDF)
- [台灣地區民國101年各標的用水量統計報告](http://wuss.wra.gov.tw/annualreports/20140017%E7%AC%AC%E4%B8%80%E9%83%A8%E4%BB%BD%20%E5%8F%B0%E7%81%A3%E5%9C%B0%E5%8D%80%E6%B0%91%E5%9C%8B101%E5%B9%B4%E5%90%84%E6%A8%99%E7%9A%84%E7%94%A8%E6%B0%B4%E9%87%8F%E7%B5%B1%E8%A8%88%E5%A0%B1%E5%91%8A.pdf)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_28eba5bb5de7004f68f0d5c18d753145)
> 這個圖其實少了一個數字，就是農業用水來自水庫主動洩水的比例，雖然從表面數字看即使把工業撥用的水拿來挹注農業用水也還是無法滿足需求
> [name=kiang]

> 哦哦@@，所以這部分，應該要看各個水庫洩水的量，並且考量該水庫附近的是否有農業區域與灌溉設施，評估該農業區使用多少的水庫洩水量?
> [name=che l]

> 既有的「農業用水」計算中不曉得是否有此項目，或是概念相近的項目？
> [name=che l]



## Tools

- 荷蘭 Deltares 研究中心提供的 水利相關 opensource 與 Freesoftware  軟體
    - [http://oss.deltares.nl/](http://oss.deltares.nl/)
    - 地下水（imod）、3維水理（delft3D）、洪水預警(FEWS) 、模式成果展示（openearth ）等
- OpenStreams
    - [https://publicwiki.deltares.nl/display/OpenS/Home](https://publicwiki.deltares.nl/display/OpenS/Home)
    - OpenStreams provides the building blocks that make up integrated hydrological models. These blocks can be complete models but also parts of models that can be used to build other models. It does not aim to be a complete framework for building and connecting models, that task is left to layers (such as OpenMI) that can be build on top of the component or collections of components.
- SeaSketch Supports Collaborative Planning for our Oceans
    - [http://www.seasketch.org/home.html](http://www.seasketch.org/home.html)
- WaterWorld
    - [http://www.policysupport.org/waterworld](http://www.policysupport.org/waterworld)
- Integrated Flood Analysis System, IFAS
    - [http://www.icharm.pwri.go.jp/research/ifas/](http://www.icharm.pwri.go.jp/research/ifas/)
    - 洪水解析系統 (Integrated Flood Analysis System, IFAS)是一個免費的淹水模擬軟體，內建有全球衛星定位與地形資料，使用者可以藉由輸入降雨資料，透過系統分析而模擬出洪水危險地區，一般民眾皆可透過此軟體模擬洪水危險地區。
- Rainfall-Runoff-Inundation Model, RRI
    - [http://www.icharm.pwri.go.jp/research/rri/rri_top.html](http://www.icharm.pwri.go.jp/research/rri/rri_top.html)
    - 降雨逕流淹水模式 (Rainfall-Runoff-Inundation Model, RRI)是免費的降雨逕流模擬軟體，內建有二維地形模擬功能，使用者將降雨量資料與數值地形模型輸入後，透過軟體可以模擬出雨水逕流狀況雨水量高度。


## idea pool

### 綜整現況水情事實，類似教科書的循環圖

- 想法說明：依照集水區區域來呈現，並且將各個集水區中的重要環境特徵、用水型態、特殊水資源地景地點...標示出來。並非抽象地呈現為「農業用水」，而是「嘉南大圳所涵蓋的農業用水」(似乎可以再更細緻?） [http://e-info.org.tw/node/107458](http://e-info.org.tw/node/107458)
- 參考：水循環示意圖，可以再加入人類使用的環節
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d242c2a6ebe82c30115f9fce0b7ea396)
- [http://mewarnai.us/images/446516-water-cycle-diagram.jpg](http://mewarnai.us/images/446516-water-cycle-diagram.jpg)
- 地球公民基金會製作高雄河川與水庫關係圖 [https://m.facebook.com/events/upcoming?ref=bookmark&app_id=2344061033#!/CitizenoftheEarth/photos/a.152858528108735.31770.148513668543221/860275864033661/?type=1&source=48](https://m.facebook.com/events/upcoming?ref=bookmark&app_id=2344061033#!/CitizenoftheEarth/photos/a.152858528108735.31770.148513668543221/860275864033661/?type=1&source=48)
- [https://www.facebook.com/1964flood/posts/855796741146541](https://www.facebook.com/1964flood/posts/855796741146541)
- [https://www.facebook.com/ajplusenglish/videos/599235236884654/](https://www.facebook.com/ajplusenglish/videos/599235236884654/)
- [http://www.nytimes.com/interactive/2016/03/24/nyregion/how-nyc-gets-its-water-new-york-101.html?smid=fb-nytimes&smtyp=cur&_r=0](http://www.nytimes.com/interactive/2016/03/24/nyregion/how-nyc-gets-its-water-new-york-101.html?smid=fb-nytimes&smtyp=cur&_r=0)
- 「大台北防洪計畫」
    - [http://www.wra10.gov.tw/ct.asp?xItem=44534&ctNode=30799&mp=10](http://www.wra10.gov.tw/ct.asp?xItem=44534&ctNode=30799&mp=10)
    - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fe17739ce5ecb71c8b4b4ec555e4836f)
- [https://www.facebook.com/fish.wang.7568/posts/299195087081518](https://www.facebook.com/fish.wang.7568/posts/299195087081518)
- 台北市的現代水文
    - 集水分區：[http://goo.gl/fxTUHV](http://goo.gl/fxTUHV)
    - 調節池：[http://goo.gl/7jKVPH](http://goo.gl/7jKVPH)
    - 抽水站：[http://goo.gl/hm8WdX](http://goo.gl/hm8WdX)
    - 下水道：[http://goo.gl/Xattq5](http://goo.gl/Xattq5)
- 水利設施地震災害通報系統建置 Establishment of Earthquake Damage Reporting System for Water Resources Facilities
    - [http://dmip.tw/Lfive/report/6/6-1-3-WRA-0-1.pdf](http://dmip.tw/Lfive/report/6/6-1-3-WRA-0-1.pdf)
    - 內文有流域、海河、水利設施清單細項列表
    - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8bef6cd7f8f817d72b192705b3db454a)
- 東港溪流域各項建設綜整圖
    - [https://www.facebook.com/yj.shie/posts/10155241663142776](https://www.facebook.com/yj.shie/posts/10155241663142776)
- 伏流水運作動畫
    - [https://www.facebook.com/groups/718089658359103/permalink/768204566680945/](https://www.facebook.com/groups/718089658359103/permalink/768204566680945/)


### 地區水議題討論：用水調度決策討論、水利設施願景政策討論、土地開發與水文保育、產業調適、水資源使用行為調整

- [都市成長管理與永續水資源利用(II)高屏溪流域都市---環境系統動力模擬建立與政策模擬分析](http://ir.lib.nsysu.edu.tw:8080/handle/987654321/39032)
- [近代地下水開發使用與所受的衝擊](http://hippo.bse.ntu.edu.tw/~wenlian/t-water/twA/twA-5.htm)，張文亮
- [我國地下水資源政策之研究](http://www.ndc.gov.tw/m1.aspx?sNo=0060210#.VXNGZ1yqqko)，中華經濟研究院
- 土地開發前後逕流零增加議題
- 臺北水源特定區管理與展望：[http://goo.gl/5mSzx8](http://goo.gl/5mSzx8)
- [http://m.appledaily.com.tw/realtimenews/article/recommend/20150812/667987/](http://m.appledaily.com.tw/realtimenews/article/recommend/20150812/667987/)
- [http://money.udn.com/money/story/7307/1111833](http://money.udn.com/money/story/7307/1111833)
- [都市水循環之研究—地表不透水率之調查及逕流量實測解析](http://readopac.ncl.edu.tw/cgi/ref/etdslink?id=090NCKU5222053)
- [http://www.sal.tokyo/rivermodules](http://www.sal.tokyo/rivermodules)
- 用水量統計報告 [http://wuss.wra.gov.tw/annuals.aspx](http://wuss.wra.gov.tw/annuals.aspx)
- 臺灣主要城市每人每日生活用水量與供（配）水量（公升）
- 水資源運用的決策 (科學園區與工業區企業廠商、城市民生用水、農業用水、備量、海水淨化廠)，所謂的「逐實穩定」
- [建置南科水資源協作雛形](https://g0v.hackpad.com/XtL7v4QBjTp)
- [http://www.newsmarket.com.tw/blog/61759/](http://www.newsmarket.com.tw/blog/61759/)：台灣面臨十年來最嚴重乾旱，嘉南農田水利會灌溉技術推廣中心研究出省水種稻法，只要一期稻延後一個月插秧，減少因為保溫需要的水量，就能節水20%，產量甚至增加8%。不過農委會認為，這項研究只是田間實驗，有待進一步評估，根據前天水利署的報告，若再不下雨，明年一期稻休耕「恐無法避免」，預計接近1、2插秧期時再做決定。
- 國家研究院台灣颱風洪水中心建置「試驗流域」，4年來詳實紀錄8800萬筆水文資料，幾乎零誤差推估上游即時流量、預測下游水位。 [http://www.chinatimes.com/realtimenews/20160823003194-260405](http://www.chinatimes.com/realtimenews/20160823003194-260405)
- 永續漁業的探討
- 水利灌溉
    - 地理資訊系統於農田水利灌溉管理之應用 by 台灣大學 生物環境系統工程學系 蘇明道 老師
        - [http://duct.cpami.gov.tw/pubWeb2/pdf/2k8d05.pdf](http://duct.cpami.gov.tw/pubWeb2/pdf/2k8d05.pdf)
        - [http://www.ae.ntu.edu.tw/people/bio.php?PID=19](http://www.ae.ntu.edu.tw/people/bio.php?PID=19)
    - 高雄農田水利會灌溉區域圖 [http://www.kfia.gov.tw/images/about_map.jpg](http://www.kfia.gov.tw/images/about_map.jpg)
-
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ed656d5c329e85a1e0ea993734881c9e)
    - 嘉南大圳歷史灌溉圖
        - [https://www.facebook.com/asgis/posts/1544122928931363:0](https://www.facebook.com/asgis/posts/1544122928931363:0)
- 水資源污染
    - 河川污染指數
        - [http://www.thenewslens.com/post/149794/](http://www.thenewslens.com/post/149794/)
    - [每洗一件衣服就會掉落近2000條衣物纖維！生態學家：恐污染全球海洋](http://www.seinsights.asia/story/614/8/2848)，[Benign by Design](http://www.launch.org/innovators/mark-browne)
    - 三張互動圖表帶你看台灣河川污染情況
        - [http://www.thenewslens.com/post/149794/](http://www.thenewslens.com/post/149794/)
    - 農業肥料污染
    - 灌排圳路受汙染潛勢
        - 立法院議案關係文書，院總第887號 政府 提案第 15100 號 之 1392 案由：行政院農業委員會函，為104年度中央政府總預算決議，針對應與環保單位及經濟部確實協調檢討工廠廢水排放標準比灌溉用水寬鬆問題，業已備妥相關資料，請列入議程，請查照案。
        - 農田水利會高汙染潛勢地區列管圳路清單 (文件第1556頁) [http](https://bit.ly/2s1MjEX)[s://bit.ly/2s1MjEX](https://bit.ly/2s1MjEX)
    - 都市上水中的污染
    - 地下水污染議題與模式
        - [旗山內門醫療廢棄物垃圾掩埋場讓在地文化及環境陷入危機](http://www.zun-huai.org.tw/news3-1_main.asp?root_id=13)
        - 黃緒瑩碩士論文-高雄平原地區地下水汙染潛事勢之研究
        - [土壤及地下水污染潛勢之研究](http://www.tasder.org.tw/meeting/2012/%E8%AD%B0%E9%A1%8C%E4%BA%8C%E7%92%B0%E5%A2%83%E7%81%BD%E5%AE%B3%E8%A9%95%E4%BC%B0%E8%88%87%E6%8E%A7%E5%88%B6%E6%96%B9%E6%B3%95%E8%88%87%E6%87%89%E7%94%A8/2-2%E5%9C%9F%E5%A3%A4%E5%8F%8A%E5%9C%B0%E4%B8%8B%E6%B0%B4%E6%B1%A1%E6%9F%93%E6%BD%9B%E5%8B%A2%E4%B9%8B%E7%A0%94%E7%A9%B6-%E5%85%A8%E6%96%87.pdf)：本研究之目的乃是在發展一套結合空間資訊而能夠有效評估區域性質的土壤及地下水 污染潛勢評估之方法論
- 在地經驗與水情監測協力
    - 宜蘭老農基於長年了解地下水狀況，倡議應儘早進行旱稻種植推廣，[來源](https://www.facebook.com/603384463096902/photos/a.603435183091830.1073741828.603384463096902/654089891359692/?type=1)。
    - [跨界結盟：台南社大環境監測網發威](http://news.pchome.com.tw/magazine/report/po/taiwan_panorama/10523/140414400003107019001.htm)
- 水的文化景觀
    - 吉哈拉艾文化景觀
    - 龜崙口泉井 據傳是漳泉移民開墾龜崙社地第一口井 位於龜山公會堂。[https://m.facebook.com/groups/851321448229543?view=permalink&id=1060820487279637#!/groups/619267858204095?view=permalink&id=632192850244929](https://m.facebook.com/groups/851321448229543?view=permalink&id=1060820487279637#!/groups/619267858204095?view=permalink&id=632192850244929)
- [歐盟水資源議題分享資料](https://drive.google.com/folderview?id=0B8DS5uT8SIlKflV2OVpKVDgxemRabWN0ZUVtbDFFdE1SNmJWcmF6U0NvUXA5WTFjU1BnZm8&usp=sharing)
- [https://www.facebook.com/watershed.japan/posts/987280661330737](https://www.facebook.com/watershed.japan/posts/987280661330737)
- 再生水
    - [https://g0v.hackpad.tw/yK5qoxCuVsw#:h=%E6%B0%B4](https://g0v.hackpad.tw/yK5qoxCuVsw#:h=%E6%B0%B4)


### 其他資料蒐集


法規
- [水利法](http://law.moj.gov.tw/LawClass/LawAll.aspx?PCode=J0110001)
    - [水利法理論與實務](https://nol.ntu.edu.tw/nol/coursesearch/print_table.php?course_id=521%20U9030&class=&dpt_code=5213&ser_no=43166&semester=104-2&lang=CH)：本課程從水利法的立法背景及過程的介紹開始，並強調水利法原始版本在台施行後，面對台灣政治、社會變化及經濟成長所形成的衝擊與挑戰，所做出的回應。課程中將研討水利法相關的水理及法理，也會對於我國水利事業及水利機關的變化加以說明。課程最後，將介紹水利工程的鑑定實例。
- [區域計畫法](http://law.moj.gov.tw/LawClass/LawAll.aspx?PCode=D0070030)
- [聯合國海洋法公約](http://zh.wikipedia.org/wiki/%E8%81%AF%E5%90%88%E5%9C%8B%E6%B5%B7%E6%B4%8B%E6%B3%95%E5%85%AC%E7%B4%84)
- 濕地法
- 漁業署
- 野保法
- 海岸法

列表盤點水資源的管理機構與相關民間單位
水資源管理單位
- 水利署
- 各地區農田水利會
- 自來水公司
流域治理相關單位
- 水土保持局
- 林務局
研究機構
- [http://hyinfo.bse.ntu.edu.tw/WRHS/Research.aspx](http://hyinfo.bse.ntu.edu.tw/WRHS/Research.aspx)

由其他資料
- 從家戶用水資料，與所排放污水量之間有無關係？
- 海洋 [https://g0v.hackpad.tw/iQV6M1XO6wj](https://g0v.hackpad.tw/iQV6M1XO6wj)

## Mockup / 呈現的方法

- 參考方法
    - [https://www.facebook.com/WaterResourcesAndDisasterManagement/videos/2046631395570670/](https://www.facebook.com/WaterResourcesAndDisasterManagement/videos/2046631395570670/)



## 協作徵人


- [ ] needOpenData
- [ ] needDesigner
- [ ] needFrontend
- [ ] needWriter




## Gobans/Hackfoldrs

1.  使用者瞭解用Goban
    - [https://goban.tw/taiwan_water](https://goban.tw/taiwan_water)
    - 也可開啟於[http://beta.hackfoldr.org/taiwan_water0](http://beta.hackfoldr.org/taiwan_water0)
2.  協作用Goban
    - [http](https://goban.tw/taiwan_water#taiwan_water&1&0)[s](https://goban.tw/taiwan_water#taiwan_water&1&0)[://goban.tw/taiwan\_water#taiwan\_water&1&0](https://goban.tw/taiwan_water#taiwan_water&1&0)
    - 也可開啟於[http://beta.hackfoldr.org/taiwan_water1](http://beta.hackfoldr.org/taiwan_water1)




---
tags: GIS, river
---

# 河川健康度 / 資料分析方法

工作頻道：g0v slack channel #river
主要工作方向：
- 診斷河川健康度
- 凝聚在地關注與追蹤
- 指認自然解方行動計畫區位

:::warning
文件目錄
[TOC]
:::

## 資料分析筆記區

輔助討論用簡報
https://docs.google.com/presentation/d/1_Z0wRR8yebTqZ_UxZxqCtcKwCdo-luNfMSqTvl6vCsM/edit?usp=sharing

<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vRQb5HZoAw4YzmDuBgHzfsb53sfW16C2-c2aKqPUy_C8dce5e_BfbjeDXbDYMDjzFIk51mqQzbktENO/embed?start=false&loop=false&delayms=3000" frameborder="0" width=100% height="480" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>

### 一、首先：河川歸戶

:::warning
討論
- 依據「探討河川健康度」的方法，需要什麼樣的「河川本體基本資料」
    - A.「治理線」作為河川範圍
        - 這個範圍裡面有 堤防與護岸、水工構造物設施、河水水體範圍、河濱公園、各種國土利用調查結果的圖塊
    - B.「集水範圍」作為會影響河川的最大範圍
        - 汙染來源
:::

#### A.「治理線」資料
- 已經有「中央管河川區域」
    - 中央管河川區域 RIVREGLN，面狀資料 + 中央管排水設施範圍REGDAREA，面狀資料
        - 下載網址：https://gic.wra.gov.tw/Gis/Gic/API/Google/Index.aspx
        - [線上瀏覽地圖](https://thunbergii.app.carto.com/map/23a9e97b-63fc-49ca-a0c0-9f1164793c7b)
        - 可能要改用 umap 來顯示資料? 
- 需要找「縣市管河川區域」
    - 找 !
    - 有縣市 https://gis.ardswc.gov.tw/
    - 筆記
        - 中央管河川還缺少基隆河在臺北市的河段
        - [已找過] 縣市水藍圖資料沒有這種資料 https://g0v.hackmd.io/HQ3u-wxdQRidmVycRdcTeA


#### B. 集水範圍 polygon
- 各種資料來源
    - (1) 全國：河川流域範圍圖 https://gic.wra.gov.tw/Gis/Gic/API/Google/Index.aspx
        - 淡水河流域僅一個 polygon
    - (2) 全國：110年度全臺839子集水區範圍圖_UTF8 https://data.gov.tw/dataset/140111
        - KML 檔案 40 mb
        - 無法放入 umap
        - 須用分批方式才能放入 Google my map
    - (3) 臺北市的集水單元
        - 臺北市78集水分區(原百齡集水區因士林北投區段徵收工程在切分出文林集水區、洲美集水區)之分布範圍及屬性資料表(KML格式) https://data.taipei/dataset/detail?id=d8085d88-0a07-4fe6-86ec-8910954342ac
    - (4) 新北市
        - 板橋土城 https://www.gtint.com.tw/service_1_detail/63.htm
        - 瓦磘溝的範圍
    - (5) ...蒐集各縣市是否有釋出更細的集水單元
- 討論：
    - 這個涉及要如何認定的問題
    - 例如臺北市北投區磺港溪的集水範圍、新北市瓦磘溝的範圍，需要採用縣市釋出的集水單元範圍
    - 這部分如何工作：
        - 考慮放入 Google My Map 把流域範圍整理一遍

#### C. 水體河道範圍 
- 水利署有釋出：全台主流資料、全台支流資料
- 縣市
    - 嘉義縣水藍圖資料，有多一些支流（但是是線條資料，不是面狀資料）
    - 桃園市區排資料，比中央釋出的河川主流支流詳細
    - 新北市
        - 大窠溪少了一段
    - 彰化縣
        - 河道中線的線條 Line 檔案
            - https://waterfusion.chcg.gov.tw/publicMap
- 討論：
    - 這份資料實際上是比較破碎的，並不是連續的面體
    - 優先使用「治理線」與「中央管河川區域」資料
        - 若無，才會評估使用這套資料再想辦法推論出類似「治理線」的範圍

#### D. 河川代碼
- 河川名稱唯一值
    - https://docs.google.com/spreadsheets/d/1iFUluCGQQtGc_oYRj7r_X4RkJ-BpVV1OKWyLiNWKqDE/edit

### 二、用鄰近程度，作為篩選依據

橫向
- 有堤防資料的河段：
    - 整合資料夾：https://drive.google.com/drive/folders/1kitIqmRCD0zHW2Ch6AL1N9ZGEYvbSmm5?usp=sharing
        - 20240225 資料包含：(1) 中央管河川的堤防 (2) 縣市只有桃園市
            - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_25e2fa6f4341b7a9b7795eb9b4bb44ff.png)
        - 中央管河川河堤，資料下載網址：https://data.gov.tw/dataset/32730
- 沒有堤防資料的河段
    - 推論方法討論：
        - 國土利用調查

縱向水體不連續
- 已有資料
    - 河溪網已有找到 水保署構造點位
- 其他單位列舉
    - 林業署
    - 臺電
    - 台水
    - 北水
    - 縣市政府

加蓋型態
- 樣態描述：橋梁、加蓋停車場、箱涵..等
- 討論：
    - 研判資料：以國土利用調查圖資，作為研判資料
        - 國土利用調查線上瀏覽：https://nsp.tcd.gov.tw/ngis/
        - 舊版檔案請洽 chewei
    - 研判範圍：「河川線」以內，符合加蓋實情的代碼列表，視為加蓋面積

河川線以內的土地使用
- 明確變動事件
    - 歷年衛星影像暨變異點展示平台 
        - https://g0v.hackmd.io/rvgNUt6cRO6Z8MXiY-j1_g?view
        - 民間已爬下點位資料
        - 可以針對變異點資料類型，建立一個從河川健康度的觀點，哪些變異類型對於河川健康度有害
- 普查資料
    - 歷年國土利用調查 
        - https://g0v.hackmd.io/TKulH3eKQJ6fL0isUPDfdw?view
        - 民間已爬下歷年國土利用調查資料
            - 例如把代碼歸納為一批「自然類」、「人工化」，「惡化／不適合在濱水帶與河川治理線之內」
                - 例如 農地，體育場(像是棒球場)，應該視為不同的影響程度
            - 探討歷年變化
            - 筆記
                - 國土利用調查似乎並不會把人工溼地調查出來，會標記為「公園綠地廣場」，不過人工溼地對於河川健康度實際會比「公園綠地廣場」來的有正向貢獻
            - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_873f7f9a58b05f0067bc59bf13e65f92.png)

水質
- 政府已有針對河川的汙染等級評定結果資料
- 集水範圍內：汙染事件、尚未納管汙染源
    - 以下資料集，可以馬上納入研判
        - (企業裁罰) 透明足跡 https://thaubing.gcaa.org.tw/
        - 農地違章工廠資料 https://disfactory.tw/
        - 全台非法與合法露營區地點 https://g0v.hackmd.io/h7CTLUQsQbeELmMJG3fzGg?view
        - 其他
            - 臺北市新生大排仍然有異味，什麼樣的資料集可以推論呈現此狀況？洗車場數量、夜市規模 ..等
- 鄰河川線一定範圍內
    - 以下資料集，可以馬上納入研判
        - 歷年衛星影像暨變異點 https://g0v.hackmd.io/rvgNUt6cRO6Z8MXiY-j1_g?view
    - 其他要想一下資料解釋方式
        - 國土利用調查 https://g0v.hackmd.io/TKulH3eKQJ6fL0isUPDfdw?view
    - 垃圾掩埋場
        - https://g0v.hackmd.io/Flb2Rik0R3OVajxSuP5uYw
        - https://www.facebook.com/share/p/7u3uDPWXX9qywXdF/

工程與計畫
- 歷史資料
    - 2013-2020 水利工程案件地點 KML https://drive.google.com/file/d/1HWp44KNrmasYWpNUpST0vG0pP84qa008/view?usp=sharing 
    - 水保工程經緯度 https://eco.ardswc.gov.tw/mis_Extention/EcologicalChecklist/EngList.aspx
- 縣市水藍圖計畫，點位資料
    - https://g0v.hackmd.io/HQ3u-wxdQRidmVycRdcTeA
- 持續中的 河川工程決標案件
    - 大河小溪 https://river-watcher.bambooculture.tw/
        - 來源是這個資料庫 Government Procurement 政府採購案件 https://openfunltd.github.io/pcc-viewer/


### 三、其他相關研究與探討

:::info
將研究方式轉化成資料普查推論方法
:::


下游主河道天然河岸長度
- 分析說明網頁 https://taibon.tw/zh-hant/indicator/aizhi/148
- 定義及計算方式：根據經濟部水利署彙整編製成「現有河川防洪設施」之公務統計報表，以河川總長度扣除水利工程設施(堤防及護岸合計)的長度，可得天然河岸之長度。各河川局及縣市政府每年填報所轄河川的幹流長度、堤防長度、護岸長度等資料。然而，報表中的河川總幹流長度為下游主河道的長度，不包含支流、野溪與未整治河川等。堤防及護岸長度包含下游主河道及支流等其他區域。此外，新建與復建的堤防及護岸長度也並無區分。因此，計算方式調整如下： 天然河岸長度=(河川總幹流長度+未整治河川項目)-(新建堤防總長度+新建護岸總長度)
- 現有資料內容及所跨年度：現有河川防洪設施(2001年至2021年)
- 資料更新內容：依據經濟部水利署公務統計報表資料經計算後，2021年下游主河道的天然河岸長度為1,276.6公里，相較2020年減少約3.79公里，並且已經低於1,300公里。該數據為未納入野溪等未整治河川項目計算結果，長期來看整體天然河岸長度正逐年下降。
- 指標趨勢：由於堤防與護岸的長度不斷增加，致使天然河岸的長度逐年減少，2001年至2021年減少約487.77公里。
- 資料管理/權責單位：經濟部水利署河川海岸組

其他一些資料來源盤點
- 流域環境情報地圖基礎地圖包 
    - 資料清單說明網頁：https://www.wrap.gov.tw/cp.aspx?n=33935
    - 下載網址：https://gofile.me/4pShY/aiKB1ME4G
    - 與河川健康度相關的資料集：
        - 待打開瀏覽
        - 2013-2020 水利工程點位資料
            - 這裡可以瀏覽資料 https://thunbergii.app.carto.com/map/23a9e97b-63fc-49ca-a0c0-9f1164793c7b?lat=24.902371&lng=121.532835&zoom=8
            - KML https://drive.google.com/file/d/1HWp44KNrmasYWpNUpST0vG0pP84qa008/view?usp=sharing
- 思源地圖曾列舉的情境及情境相關資料集 
    - https://docs.google.com/document/d/1vgIEMngmovdXS01sOAu-KVumA-VdZkN66QUKzvnrhd8/edit#heading=h.4vv7g5bazrox
- 其他筆記頁面
    - https://g0v.hackmd.io/LVHnV9ZkQL6WcCkPpbMcmw

針對拆壩的個案河川，如何呈現「變健康了」
- 前後的生態調查資料 ?

濱水區植生
- 濱水區植生演替與沖積河床演變之動態交互地貌調整機制：本研究以Google衛星影像與Google街景的資料，找出濱水區植生完整覆蓋且長期存在、不易被洪水移除的河段，並分析其溪流功率特性，研究結果發現，透過總溪流功率、單位溪流功率兩項因子的大小與其變化，可清楚的描述河川上游到下游的水流沖刷力特性，進而區分河川型態、描述河川型態因子的變化趨勢。 
    - https://www.grb.gov.tw/search/planDetail?id=11494560
- 研發遙測技術獲取礫石河床粗糙度與河川表面流態分類
    - https://researchoutput.ncku.edu.tw/zh/projects/%E7%A0%94%E7%99%BC%E9%81%99%E6%B8%AC%E6%8A%80%E8%A1%93%E7%8D%B2%E5%8F%96%E7%A4%AB%E7%9F%B3%E6%B2%B3%E5%BA%8A%E7%B2%97%E7%B3%99%E5%BA%A6%E8%88%87%E6%B2%B3%E5%B7%9D%E8%A1%A8%E9%9D%A2%E6%B5%81%E6%85%8B%E5%88%86%E9%A1%9E-4
- 多功能河川生態環境流量之區域性標準建立-子計畫四：區域性河川棲地與地表變化偵測技術研發(1/3)
    - https://researchoutput.ncku.edu.tw/zh/projects/%E5%A4%9A%E5%8A%9F%E8%83%BD%E6%B2%B3%E5%B7%9D%E7%94%9F%E6%85%8B%E7%92%B0%E5%A2%83%E6%B5%81%E9%87%8F%E4%B9%8B%E5%8D%80%E5%9F%9F%E6%80%A7%E6%A8%99%E6%BA%96%E5%BB%BA%E7%AB%8B-%E5%AD%90%E8%A8%88%E7%95%AB%E5%9B%9B%E5%8D%80%E5%9F%9F%E6%80%A7%E6%B2%B3%E5%B7%9D%E6%A3%B2%E5%9C%B0%E8%88%87%E5%9C%B0%E8%A1%A8%E8%AE%8A%E5%8C%96%E5%81%B5%E6%B8%AC%E6%8A%80%E8%A1%93%E7%A0%94%E7%99%BC13-3

歷史圖資
- 從歷史圖資來描繪人工化程度與區位區段
- 臺灣近百年來主要河流的地形變遷與其減災意涵：一個「人為地形學」的嘗試 
    - https://www.grb.gov.tw/search/planDetail?id=12287108
    - 臺灣氾濫平原地形變遷資料庫之建置，已完成臺灣堡圖、臺灣地形圖（東部陸測部地形圖、高屏昭和修測版臺灣地形圖）與政府公開資料之水利署河道圖層、內政部地政司公開LiDAR DEM 進行整合。歷史圖資數化成果包括主要流路（面符號）、次要流路（面符號）、地形崖（線符號）與堤防（線符號）。已建置完成的河流包括全數26 條中央管河川之主、支流；91 條縣市管河川中北部、西部之25 條；以及歷史圖資上西南海岸之水體（如魚塭）範圍。
- 從歷史航照與地圖追尋台灣河流身世 
    - https://www.facebook.com/101NAPCU/videos/458284418240039/
- 以「馬太鞍溪」近百年的變遷來看，近代在沖積扇進行束水築堤，支流舊河道市區化，可能也並非其「健康、理想」的河川樣貌？2025 年發生上游堰塞湖溢流，導致下游支流舊河道湧入溢流泥水
    - https://www.facebook.com/theericel/posts/pfbid03eeDnZdRetjpfzDWJ9h4qNsDPEqZ4yPPLrv3rX6B55Ni5jmNCBzi2dfvGcQwioDNl

地質與水文
- https://www.facebook.com/339919013202175/posts/345145029346240/
- 地形特徵圖 - 國家災害防救科技中心委託辦理計畫 https://atlas.geo.ntnu.edu.tw/
    - 已完成六個示範區，可瀏覽較精細的地理資料

河相分群
- https://photos.app.goo.gl/1CBYrPCswto64VUt8


水質，透過溪流水利模式，擴大沿線水質推論結果 
- https://opendata.wra.gov.tw/files/%E7%B8%BD%E7%B5%B1%E7%9B%83%E9%BB%91%E5%AE%A2%E6%9D%BE_%E5%A4%9A%E9%87%87%E6%B0%B4%E6%B7%A80.pdf
- https://photos.app.goo.gl/MjkFbLt5EKGZSHAW6

其他
- 這裡有河川往外推 30 公尺的圖資結果 https://classicdesign053.carto.com/builder/48e2d385-3328-495e-8bd8-0a352653f523/embed?state=%7B%22map%22%3A%7B%22ne%22%3A%5B21.839130732143317%2C117.09848793223502%5D%2C%22sw%22%3A%5B25.37188765563586%2C125.21738441661002%5D%2C%22center%22%3A%5B23.617413163623617%2C121.15793617442252%5D%2C%22zoom%22%3A8%7D%7D

探討：當代地表水文類型：自然河川流域、堤防內的排水分區單元、飲用水與污水的系統、水庫集水區、埤塘系統、臨海魚塭、海岸
- https://docs.google.com/spreadsheets/d/1jAc2GZfUrHS74IuPGa-2IMnagA-rarJ6Hz775Vf5pjU/edit

---

## 地圖工具筆記區

QGIS 
- QGIS 線上地圖方式 https://airtable.com/appa7UHcRt9eju3hn/shr10se71AsXb7jnK/tblnNHAWlj13RusOc/viwOp1n0BA1BrTjbu/recyAUAjNacPBzUhP?blocks=hide

Googlemymap 
- 課題：要分批放入資料
- 方便編修個別資料

umap
- 可放的資料量比 Googlemymap 多
- 但底圖沒有衛星圖

carto 
- 可放入，但免費使用期 14 天過後是否就不能顯示？(或是不能編輯？
- 目前呈現成果：https://thunbergii.app.carto.com/map/23a9e97b-63fc-49ca-a0c0-9f1164793c7b?lat=24.902371&lng=121.532835&zoom=8

tableau 
- 環社檢核圖台儀錶板案例：https://public.tableau.com/app/profile/doenergy/viz/_16539228904330/sheet1_1

## 圖台案例與公眾協力工具

思源地圖
- https://sourcingwater.lass-net.org/

公眾協力
- 拍照上傳的群眾標註工具 https://commutag.agawork.tw/
- 資料寄存所 https://data.depositar.io/about
- Line 官方帳號，提供互動
- 河流資料標註活動　Flowing Together Mapathon 針對 Sherni River Basin in India https://www.facebook.com/share/p/ggMRNhHj177TmvF4/

### 其他參考

美國壩體用途地圖
- Where the Water Flows - A multivariate map showing the flow direction and annual mean streamflow rate for all major rivers in the contiguous United States during 2022, overlaid with all federally regulated dams that hold an average water volume over 1,000,000 acre feet. 
    - http://esri.social/j85r50QGuSG
    - https://www.facebook.com/share/p/n17HUvy7tbHSAKrh/


此方法可以用於海岸，以下有海岸法陸域範圍線上地圖
- https://classicdesign053.carto.com/builder/48e2d385-3328-495e-8bd8-0a352653f523/embed?state=%7B%22map%22%3A%7B%22ne%22%3A%5B21.839130732143317%2C117.09848793223502%5D%2C%22sw%22%3A%5B25.37188765563586%2C125.21738441661002%5D%2C%22center%22%3A%5B23.617413163623617%2C121.15793617442252%5D%2C%22zoom%22%3A8%7D%7D

參考
- 英國泰晤士河流域洪水管理之案例 (Natural Flood Management)，其以透過性阻水壩 (Leaky Dam)、滯洪池 (Retention Ponds)、農業再生 (Regenerative Agriculture)等三方法來說明NFM措施之改善與效益評估
    - https://tech.ardswc.gov.tw/EPaper/Home/EPaper?PaperID=99903052-8706-4529-86ba-86b23b2434e0
- https://www.melbournewater.com.au/services/projects/reimagining-your-creek-project

## 公眾企劃

- [環境擬人化法制案例 / AI 🌄](https://g0v.hackmd.io/@chewei/H1UTdIOZc)


---

:::warning
文件目錄
[TOC]
:::
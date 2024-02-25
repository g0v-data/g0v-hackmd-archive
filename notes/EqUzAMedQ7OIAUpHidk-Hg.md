---
tags: GIS
---

# 河川健康度

概念：
- 診斷河川健康度
- 凝聚在地關注與追蹤
- 自然解方行動計畫區位

:::warning
[TOC]
:::

## 資料

一些資料來源盤點
- 流域環境情報地圖基礎地圖包 https://www.wrap.gov.tw/cp.aspx?n=33935
- 思源地圖曾列舉的情境及情境相關資料集 https://docs.google.com/document/d/1vgIEMngmovdXS01sOAu-KVumA-VdZkN66QUKzvnrhd8/edit#heading=h.4vv7g5bazrox

### 河川歸戶
- 是否要用「治理線」
    - 找資料
    - 中央管河川區域
        - 此資料比較符合本次健康度分析用途，適度整合過 
            - https://gic.wra.gov.tw/Gis/Gic/API/Google/Index.aspx
    - 找縣市管河川區域
        - 找
        - 縣市水藍圖資料看看有沒有可用資料 https://g0v.hackmd.io/HQ3u-wxdQRidmVycRdcTeA
- 河道範圍 polygon：
    - 主流 
    - 支流
- 集水範圍 polygon
    - 各種資料來源
    - (1) 比較大範圍，補網址
        - 例如淡水河流域僅一個 polygon
    - (2) 110年度全臺839子集水區範圍圖_UTF8 https://data.gov.tw/dataset/140111
        - KML 檔案 40 mb
        - 無法放入 umap
        - 須用分批方式才能放入 Google my map
        - QGIS 線上地圖方式
            - https://airtable.com/appa7UHcRt9eju3hn/shr10se71AsXb7jnK/tblnNHAWlj13RusOc/viwOp1n0BA1BrTjbu/recyAUAjNacPBzUhP?blocks=hide
        - Google Earth online
        - carto 可放入，但免費使用期 14 天過後是否就不能顯示？(或是不能編輯？)
            - https://thunbergii.app.carto.com/map/23a9e97b-63fc-49ca-a0c0-9f1164793c7b?lat=24.902371&lng=121.532835&zoom=8
     - (3) 臺北市的集水單元，補網址
- 河川代碼
    - https://docs.google.com/spreadsheets/d/1iFUluCGQQtGc_oYRj7r_X4RkJ-BpVV1OKWyLiNWKqDE/edit

### 用鄰近程度，作為篩選依據

這裡有河川往外推 30 公尺的圖資結果
https://classicdesign053.carto.com/builder/48e2d385-3328-495e-8bd8-0a352653f523/embed?state=%7B%22map%22%3A%7B%22ne%22%3A%5B21.839130732143317%2C117.09848793223502%5D%2C%22sw%22%3A%5B25.37188765563586%2C125.21738441661002%5D%2C%22center%22%3A%5B23.617413163623617%2C121.15793617442252%5D%2C%22zoom%22%3A8%7D%7D

縱向水體不連續
- 如何系統化盤點？
- 先找個別案例河川

水質
- 透過溪流水利模式，擴大沿線水質推論結果 
    - https://opendata.wra.gov.tw/files/%E7%B8%BD%E7%B5%B1%E7%9B%83%E9%BB%91%E5%AE%A2%E6%9D%BE_%E5%A4%9A%E9%87%87%E6%B0%B4%E6%B7%A80.pdf
    - https://photos.app.goo.gl/MjkFbLt5EKGZSHAW6
- 集水範圍內
    - (企業裁罰) 透明足跡 https://thaubing.gcaa.org.tw/
    - 全台合法露營區地點 https://g0v.hackmd.io/h7CTLUQsQbeELmMJG3fzGg?view
    - 農地違章工廠資料 https://disfactory.tw/
- 鄰河川線一定範圍內
    - 歷年衛星影像暨變異點 https://g0v.hackmd.io/rvgNUt6cRO6Z8MXiY-j1_g?view
    - 歷年國土利用調查 https://g0v.hackmd.io/TKulH3eKQJ6fL0isUPDfdw?view

河川線以內
- 歷年衛星影像暨變異點展示平台 https://www.landchg.org.tw/Module/RWD/Web/pub_exhibit.aspx

河川工程決標案件
- 大河小溪 https://river-watcher.bambooculture.tw/

縣市水藍圖計畫，點位資料
- https://g0v.hackmd.io/HQ3u-wxdQRidmVycRdcTeA

### 其他相關研究

濱水區植生
- 濱水區植生演替與沖積河床演變之動態交互地貌調整機制：本研究以Google衛星影像與Google街景的資料，找出濱水區植生完整覆蓋且長期存在、不易被洪水移除的河段，並分析其溪流功率特性，研究結果發現，透過總溪流功率、單位溪流功率兩項因子的大小與其變化，可清楚的描述河川上游到下游的水流沖刷力特性，進而區分河川型態、描述河川型態因子的變化趨勢。 
    - https://www.grb.gov.tw/search/planDetail?id=11494560
- 研發遙測技術獲取礫石河床粗糙度與河川表面流態分類
    - https://researchoutput.ncku.edu.tw/zh/projects/%E7%A0%94%E7%99%BC%E9%81%99%E6%B8%AC%E6%8A%80%E8%A1%93%E7%8D%B2%E5%8F%96%E7%A4%AB%E7%9F%B3%E6%B2%B3%E5%BA%8A%E7%B2%97%E7%B3%99%E5%BA%A6%E8%88%87%E6%B2%B3%E5%B7%9D%E8%A1%A8%E9%9D%A2%E6%B5%81%E6%85%8B%E5%88%86%E9%A1%9E-4
- 多功能河川生態環境流量之區域性標準建立-子計畫四：區域性河川棲地與地表變化偵測技術研發(1/3)
    - https://researchoutput.ncku.edu.tw/zh/projects/%E5%A4%9A%E5%8A%9F%E8%83%BD%E6%B2%B3%E5%B7%9D%E7%94%9F%E6%85%8B%E7%92%B0%E5%A2%83%E6%B5%81%E9%87%8F%E4%B9%8B%E5%8D%80%E5%9F%9F%E6%80%A7%E6%A8%99%E6%BA%96%E5%BB%BA%E7%AB%8B-%E5%AD%90%E8%A8%88%E7%95%AB%E5%9B%9B%E5%8D%80%E5%9F%9F%E6%80%A7%E6%B2%B3%E5%B7%9D%E6%A3%B2%E5%9C%B0%E8%88%87%E5%9C%B0%E8%A1%A8%E8%AE%8A%E5%8C%96%E5%81%B5%E6%B8%AC%E6%8A%80%E8%A1%93%E7%A0%94%E7%99%BC13-3

針對拆壩的個案河川，如何呈現「變健康了」
- 生態調查資料 ?


歷史
臺灣近百年來主要河流的地形變遷與其減災意涵：一個「人為地形學」的嘗試
https://www.grb.gov.tw/search/planDetail?id=12287108
特點：
臺灣氾濫平原地形變遷資料庫之建置，已完成臺灣堡圖、臺灣地形圖（東部陸測部地形圖、高屏昭和修測版臺灣地形圖）與政府公開資料之水利署河道圖層、內政部地政司公開LiDAR DEM 進行整合。
歷史圖資數化成果包括主要流路（面符號）、次要流路（面符號）、地形崖（線符號）與堤防（線符號）。
已建置完成的河流包括全數26 條中央管河川之主、支流；91 條縣市管河川中北部、西部之25 條；以及歷史圖資上西南海岸之水體（如魚塭）範圍。
從歷史航照與地圖追尋台灣河流身世
https://www.facebook.com/101NAPCU/videos/458284418240039/
地質與水文
https://www.facebook.com/339919013202175/posts/345145029346240/
河相分群
https://photos.app.goo.gl/1CBYrPCswto64VUt8

地形特徵圖 - 國家災害防救科技中心委託辦理計畫
https://atlas.geo.ntnu.edu.tw/

### 地圖工具

QGIS 
umap
Googlemymap 
tabelu? 環社檢核 case

## 圖台案例與公眾協力工具

思源地圖
- https://sourcingwater.lass-net.org/

公眾協力
- 群眾標註 https://commutag.agawork.tw/
- 資料寄存所 https://data.depositar.io/about
- Line 官方帳號，提供互動


https://www.facebook.com/share/p/ggMRNhHj177TmvF4/

## 其他

此方法可以用於海岸，以下有海岸法陸域範圍線上地圖
https://classicdesign053.carto.com/builder/48e2d385-3328-495e-8bd8-0a352653f523/embed?state=%7B%22map%22%3A%7B%22ne%22%3A%5B21.839130732143317%2C117.09848793223502%5D%2C%22sw%22%3A%5B25.37188765563586%2C125.21738441661002%5D%2C%22center%22%3A%5B23.617413163623617%2C121.15793617442252%5D%2C%22zoom%22%3A8%7D%7D



參考
- https://www.melbournewater.com.au/services/projects/reimagining-your-creek-project
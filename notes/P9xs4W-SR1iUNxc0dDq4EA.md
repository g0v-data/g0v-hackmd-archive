---
tags: GIS
---

# 衛星圖資應用案例

:::warning
目錄
[TOC]
:::

## 待整理
- https://www.facebook.com/groups/718089658359103/permalink/2414458812055504/
- 遙測盤點石棉瓦屋頂
    - https://www.tcsb.gov.tw/cp-28-4242-8fdf7-1.html
- 聲音與 ndvi
    - https://www.facebook.com/story.php?story_fbid=pfbid02mgS1vj8LKjQZAcWuVNEc1kEEWpLZb8tnvu4w2VGJeYu8rP1kGiqr1LS81pkvNNpl&id=889701534373509
- 國家太空中心製作的介紹與教學影片
    - https://www.nspo.narl.org.tw/activity/tsh2021/#7
    - 線上課程：
    - 1. 關於2021台灣太空黑客松 
    - 2. 福爾摩沙衛星八號課程 
    - 3. 獵風者衛星課程 
    - 4. 福爾摩沙衛星七號課程 
    - 5. 福爾摩沙衛星五號課程 
    - 6. 立方衛星課程 
    - 7. B5G低軌通訊衛星課程 
    - 8. 探空火箭課程 
    - 9. 衛星影像處理課程 
    - 10. 衛星操控中心課程 
    - 11. 整合測試廠房課程 
    - 12. 衛星多元遙測資料服務平台課程 
    - 13. 外太空探索課程
- 辨識競賽活動
    - https://codalab.lisn.upsaclay.fr/competitions/8987?mibextid=tejx2t


## 議題調查

### 森林資源調查

- Mapping Forest Loss with Landsat
    - [https://www.facebook.com/NASA.Landsat/photos/a.127807560625058.24838.104993236239824/850639111675229/?type=1](https://www.facebook.com/NASA.Landsat/photos/a.127807560625058.24838.104993236239824/850639111675229/?type=1)
- Global forest cover change mapping at Landsat resolution
    - [http://www.globallandproject.org/arquivos/news9/Feature_article5.pdf](http://www.globallandproject.org/arquivos/news9/Feature_article5.pdf)
- Applying Image Fusion to Integrate Radar Images and SPOT Multi-spectral Satellite Images for Forest Type Classification
    - [https://www.researchgate.net/publication/301681210\_Applying\_Image\_Fusion\_to\_Integrate\_Radar\_Images\_and\_SPOT\_Multi-spectral\_Satellite\_Images\_for\_Forest\_Type\_Classification](https://www.researchgate.net/publication/301681210_Applying_Image_Fusion_to_Integrate_Radar_Images_and_SPOT_Multi-spectral_Satellite_Images_for_Forest_Type_Classification)

### 農業

- NDVI：NASA 的 Global Agricultural Monitor
    - [http://glam1.gsfc.nasa.gov/](http://glam1.gsfc.nasa.gov/)
- 農業用水
    - [https://www.facebook.com/NASA.Landsat/posts/859866827419124](https://www.facebook.com/NASA.Landsat/posts/859866827419124)
- 運用 MODIS 影像製作 NDVI 觀察5年間耕地變化
    - Remotely sensed high resolution irrigated area mapping in India for 2000 to 2015 [https://www.facebook.com/groups/twlandsat/permalink/955988417867390/](https://www.facebook.com/groups/twlandsat/permalink/955988417867390/)
- 乾旱保險理賠
    - [https://www.facebook.com/eurisy1/posts/618497735016424](https://www.facebook.com/eurisy1/posts/618497735016424)
- 衛星高解析度遙測影像（Image object)於複雜農地灌溉水量之研究
    - [https://www.facebook.com/mengju.wu.50/posts/1545180752168520](https://www.facebook.com/mengju.wu.50/posts/1545180752168520)

### 都市綠覆

- 應用SPOT-5衛星影像於都市地區綠化程度及變遷之研究–以台南市區為例
    - [https://drive.google.com/open?id=0B9KyxXC_y1sLb0JYUVg5eU1Jck0](https://drive.google.com/open?id=0B9KyxXC_y1sLb0JYUVg5eU1Jck0)
- 更多案例蒐集
https://airtable.com/shr4f3DnuXOslFyss/tblOnoodEDuuujStg/viwqoiE72L5gEVoXE/rec5zOcSexoZQbrK0


### 地面溫度

- 都市熱島
```
有ndvi以後，可以用來算地表溫度 http://fromgistors.blogspot.com/2014/01/estimation-of-land-surface-temperature.html
LSE部分用NDVI公式代替 http://goo.gl/xMSOmZ
```
- 以遙感探測探討台北市綠覆率與空氣溫度之關係
    - [http://ndltd.ncl.edu.tw/cgi-bin/gs32/gsweb.cgi/login?o=dnclcdr&s=id=%22099PCCU0224006%22.&searchmode=basic](http://ndltd.ncl.edu.tw/cgi-bin/gs32/gsweb.cgi/login?o=dnclcdr&s=id=%22099PCCU0224006%22.&searchmode=basic)
- 利用影像估算不透水鋪面(ISA)
    - [http://eyesonplace.net/2017/04/19/5222/](http://eyesonplace.net/2017/04/19/5222/)


### 土壤與地質

- Soil moisture mission produces first global maps
    - [http://climate.nasa.gov/news/2275/](http://climate.nasa.gov/news/2275/)
- [**Sendo Wang**](https://www.facebook.com/sendowang?fref=ufi) 這樣講不精確，參考原文第 5、6 段可知：SMAP 衛星上裝載了雷達(RADAR)，會發射出1.2GHz頻率的微波(microwave)到地表，微波從地表反射(其實是散射的一種，並不完全等同於反射)後，被 SMAP 衛星上的無線電感測器(radiometer)接收到，透過強度與極性的改變，就可以推估地表的含水情形。另一方面，地表原本就會輻射微波，這種自然輻射的微波頻率約在 1.4GHz，沙漠發出自然輻射的速度大約是水體的 3 倍，所以一樣由 SMAP 衛星上的無線電感測器(顯然不同波段)接收到之後，就可以分析這塊地表屬於陸地或水體。不過重點是，這顆衛星的地面解析度粗到大約 40km，恐怕無法跟一般遙測衛星的光學感測器相提並論...
- [**Jhih-Cyuan Shen**](https://www.facebook.com/coop.shen?fref=ufi)  MODIS 為目前可以提供土壤含水量的(需透過資料計算與推估)光學衛星資料1km~250m，但在雲霧遮蔽情況下就無法提供資料(氣象局有持續產出中)，SMAP 衛星是為了補足這一塊，在高解析度SAR與1 to 3km(陸地 沿海地區使用) 低解析度40km(海洋區塊)的感測器配合下，希望後續如同報導中的說明可以提供9 km解析度的資料，在水文流量之推估上就可以提供更完整的參數資料資訊，隨然目前國內政府單位在政策上仍不重視這一塊資料...
- NASA technology used to find stone age structures
    - [http://phys.org/news/2016-11-nasa-technology-stone-age.html](http://phys.org/news/2016-11-nasa-technology-stone-age.html)
- 20161213 衛星遙測土壤含水量與降雨量相關文獻導讀(劉維則)
    - [https://youtu.be/uJ8X_veT2BE](https://youtu.be/uJ8X_veT2BE)
- 三維地下溫度分佈
    - [https://www.facebook.com/shoucheng.wang/posts/10155924070980575](https://www.facebook.com/shoucheng.wang/posts/10155924070980575)
- A method for the remote sensing identification of uncontrolled landfills: formulation and validation
    -    https://www.tandfonline.com/doi/abs/10.1080/01431160701311317


### 水土保持

- 衛星影像變異點查證系統：水土保持局應用 SPOT 衛星影像，每2-3個月接收一次全台灣地區山坡地範圍之衛星影像資料，進行影像比較。並建置衛星變異點查證網際網路管理系統，以網際網路為作業平台，加速衛星影像變異點查證時程，達成「違規行為立即舉發，危害情事立即排除」的目標。查證作業網路化後，水土保持局取得變異點資料後匯入系統資料庫，各縣市承辦人員即時可取變異點資料至現地查證，查證結果亦透過系統由網路直接回報水土保持局，審查核可後即更新資料庫，整個作業流程大幅簡化，有效提升作業效率。
    - [http://uav.swcb.gov.tw/telemeter02_satellite.htm](http://uav.swcb.gov.tw/telemeter02_satellite.htm)
- 103年度「臺北市山坡地衛星影像變異分析及多元尺度監測」委託專業服務案 成果報告書
    - [http://gisweb.taipei.gov.tw/opendata/resultsreport/103/B_1037007.pdf](http://gisweb.taipei.gov.tw/opendata/resultsreport/103/B_1037007.pdf)
    - 臺北市政府工務局大地工程
- 大規模崩塌防災監測技術
    - [https://www.facebook.com/246.swcb/posts/889231731136190](https://www.facebook.com/246.swcb/posts/889231731136190)
- 合成孔徑雷達 (Synthetic Aperture Radar, SAR) 在坡地防災上的應用及未來趨勢
    - [https://www.facebook.com/groups/718089658359103/permalink/957813114386755/](https://www.facebook.com/groups/718089658359103/permalink/957813114386755/)
- [https://www.facebook.com/246.swcb/posts/914162971976399](https://www.facebook.com/246.swcb/posts/914162971976399)
- [https://www.facebook.com/246.swcb/posts/918400048219358](https://www.facebook.com/246.swcb/posts/918400048219358)
- [https://www.facebook.com/246.swcb/posts/1171675206225173](https://www.facebook.com/246.swcb/posts/1171675206225173)
- https://www.facebook.com/1379229562310860/posts/2283391805227960/

### 森林火災議題

- 加州野火分析圖臺
    - https://forestobservatory.com/explore
- 找到相關範例講優勝美地國家公園的大火，結果是用 6-5-4 的 false color ，來製作出來比較圖 [http://eros.usgs.gov/views-news/rim-fire](http://eros.usgs.gov/views-news/rim-fire)
- [http://www.digital-geography.com/forest-fire-tracking-landsat-8/#.VSS9l_mUf84](http://www.digital-geography.com/forest-fire-tracking-landsat-8/#.VSS9l_mUf84)
- [http://cimss.ssec.wisc.edu/goes/blog/archives/13796](http://cimss.ssec.wisc.edu/goes/blog/archives/13796)
- 年初的澳洲大火，Digital Globe的 tomnod 也有開啟一個眾包，讓鄉民可以應用衛星圖標示受火災影響的建築物和道路：
    - 詳情： [http://aerometrex.com.au/blog/?p=977](http://aerometrex.com.au/blog/?p=977)
    - [http://aerometrex.com.au/.../2015/01/tomnod-1024x580.jpg](http://aerometrex.com.au/.../2015/01/tomnod-1024x580.jpg)
- 關於您所提這樣的圖資是否可協助森林火災，我認為是絕對有的，例如說火災前後森林面積減少的估算、地貌的改變或是延燒方向等等，對於後續災損補助的計算或災後報告的提出都有助益，另於火災當下或許圖資更新速度緩不濟急，但於事後檢討，也可藉由這樣的圖資去研判未來在同樣條件地區發生火災時，何地適合切入防火線?或是防火樹種應該建造在什麼條件的位置與地形以避免危害居民? 諸如此類的發想都需要借助圖資的輔助以及前後圖資對照的技術
- [http://www.airitilibrary.com/Publication/alDetailedMesh1?DocID=U0026-0608201016301200](http://www.airitilibrary.com/Publication/alDetailedMesh1?DocID=U0026-0608201016301200)
    - 2009年阿里山森林火災的時候用false image做了範圍跟面積的粗估~
    - [https://www.youtube.com/watch?v=fnhUxOOGyUY](https://www.youtube.com/watch?v=fnhUxOOGyUY)
- Normalized Burn Raio(標準化燃燒指數) 用來評估燃燒的嚴重程度 [http://wiki.landscapetoolbox.org/doku.php/remote\_sensing\_methods:normalized\_burn\_ratio](http://wiki.landscapetoolbox.org/doku.php/remote_sensing_methods:normalized_burn_ratio)
- [摘](https://www.facebook.com/RiChiTech/photos/a.132917840088876.21294.130017733712220/853530848027568/?type=1)『WorldView-3短紅外光(Short Wave Infrared Red / SWIR) 影像。由於SWIR擁有卓越「雲霧穿透」能力，因此在火災發生時，能即時提供地表資訊。WorldView-3可以一次取得8組SWIR資料，原始解析度還高達到3.5米，是目前唯一能提供高解析度SWIR的商業衛星』
- 搭配災後監測，也希望登山者協助現地拍照
    - [https://www.facebook.com/wayne5540/posts/995798573766479:0?hc_location=ufi](https://www.facebook.com/wayne5540/posts/995798573766479:0?hc_location=ufi)
- [https://www.facebook.com/digitalgeography/posts/1051690301642654](https://www.facebook.com/digitalgeography/posts/1051690301642654)
- 遙測及資料視覺化如何協助森林野火防救災－以2022年加州McKinney大火為例  
    - https://m.facebook.com/groups/718089658359103/permalink/2414458812055504/
- Using the Google Earth Engine (GEE) for Detection of Burned Areas
    -    https://www.facebook.com/digitalgeography/posts/1051690301642654


### 水資源

- WATER QUALITY ASSESSMENT FOR DOKAN LAKE USING LANDSAT 8 OLI SATELLITE IMAGES
    - [https://drive.google.com/file/d/0B8uVZEM9jww8U1kwSENNRkFWTk0/view](https://drive.google.com/file/d/0B8uVZEM9jww8U1kwSENNRkFWTk0/view)
- SPACE-O (Space Assisted Water Quality Forecasting Platform for Optimized Decision Making in Water Supply Services) integrates state-of-the-art satellite technology and in-situ monitoring with advanced hydrological, water quality models and ICT tools, into a powerful decision support system. This generates real-time, short- to medium-term forecasting of water flows and quality data in reservoirs, used to optimise water treatment plant operations and establish a complete service line from science to the water business sector.
    - [http://www.space-o.eu/](http://www.space-o.eu/)
- [http://www.un-spider.org/news-and-events/news/new-unesco-tool-uses-remote-sensing-data-monitor-global-water-quality](http://www.un-spider.org/news-and-events/news/new-unesco-tool-uses-remote-sensing-data-monitor-global-water-quality)
- 線上圖台 SDG6 Hydrology TEP Reporting portal, a free online visualiser for global satellite-based water quality products.
http://sdg6-hydrology-tep.eu/
- New UNESCO tool uses remote sensing data to monitor global water quality
http://www.un-spider.org/news-and-events/news/new-unesco-tool-uses-remote-sensing-data-monitor-global-water-quality
- 利用 google earth enagine 執行 水質分析
https://www.facebook.com/coop.shen/posts/5765713283445713
https://github.com/SERVIR/water-quality-gee
- 從遙測影像建立水質地圖 Creating water quality maps from remote sensed images with Python
https://www.facebook.com/groups/LASSnet/permalink/3101857496731506/

### 沙漠化

- 摘自：[https://www.facebook.com/groups/twlandsat/permalink/754177794715121/](https://www.facebook.com/groups/twlandsat/permalink/754177794715121/)
- 非洲的飢荒預警系統（FEWS NET），最近發布了一張 293 個水文點地圖，應用多種衛星影像 + 水文分析機制的方式，找到這些水文點，這張圖也橫跨了非洲十個國家。「Monitoring Small Surface Water Bodies in Africa Naga Manohar Velpuri, works with the USGS Famine Early Warning Systems Network (FEWS NET). The project has recently initiated a large-scale project to monitor surface water bodies in the pastoral regions of Africa using multi-source satellite data and hydrologic modeling techniques. Currently, a total of 293 water points are being monitored in ten countries. Velpuri shared some of the projects findings he presented at [#AGU15](https://g0v.hackpad.tw/ep/search/?q=%23AGU15&via=FTBOsiElsPY) .」
- 綠色長城介紹： [http://www.storm.mg/article/76645](http://www.storm.mg/article/76645)
- FEWS NET： [http://www.fews.net/](http://www.fews.net/)

### 砂石濫採

- 另外 經濟部礦務局 也有委託 師範大學地理系 詮華國土測繪 進行"應用衛星及航拍影像監測盜濫採砂石研究" 也會針對影像前後其有變動可能性的區域進行查報工作 主要應用福位二號和航照圖進行比對
- 應用衛星及航拍影像監測盜濫採砂石研究
    - [http://210.69.81.172/GipOpenWeb/wSite/ct?xItem=151917&mp=101&ctNode=217](http://210.69.81.172/GipOpenWeb/wSite/ct?xItem=151917&mp=101&ctNode=217)

### 災害資訊

- 即時衛星圖資協助災害資訊建置的案例 \- [tomnod.com](http://l.facebook.com/l.php?u=http%3A%2F%2Ftomnod.com%2F&h=SAQFU9vUR&enc=AZMr3Cy1UrrCqDOR-YjTTSS63OuhFVhagkYDclVSx_wYtBFwACf435eKM6MH2ADrd6yKu9GtQOq3mlTMnek5KPs1jHzlrbt9CgH70kjlb-q6DWwvODncxUs3nlg6n_VJnDNeCRXjwDbsrkhajl145qBPm_zG6kFfgO_0RmC70xhGLQ&s=1)
    - 不曉得有沒有人試過？有任何好處、壞處，以及台灣的衛星是否也可有這樣應用
    - DigitalGlobe 是一家專門處理GIS資訊、衛星圖資的公司，他們有個專案專門協助災害標示，叫做 [tomnod.com](http://l.facebook.com/l.php?u=http%3A%2F%2Ftomnod.com%2F&h=hAQGwpbhy&enc=AZNJBnCxWHUS73oRBMOX2ku40QsOMIEubuj98sKaejEzTk9yXK5v2wWT7YtdSS6JWCRe4XbS161aANldHHpQ9OQpUdjyTn4R0CSwCa2wxXlTimmAguLrluur9FaVVCu0FQ0Nm7R-TUEssL1XDLyCYGlocVEUDPICre2FsVNfb_b1Tg&s=1)，使用者直接用第一手的衛星圖資去「tag」損害的建築物、中斷的道路，一樣是 Crowdsourcing 的概念，只是這次用的是即時圖資，每一張圖都有拍攝日期的時間標示。
    - p.s. 謝謝 [Sean Wilson](https://www.facebook.com/mrseanjwilson) 提供資訊
- Tomnod 尼泊爾的即時衛星圖標示：
    - [http://www.tomnod.com/campaign/nepal\_earthquake\_2015/map/](http://www.tomnod.com/campaign/nepal_earthquake_2015/map/)
- 類似的OSM案例，不過是在畫地圖：
    - [http://goo.gl/n5EI4Q](http://goo.gl/n5EI4Q)
    - [http://wiki.openstreetmap.org/wiki/2015\_Nepal\_earthquake](http://wiki.openstreetmap.org/wiki/2015_Nepal_earthquake)
- 寮國潰壩水災
    - [https://www.facebook.com/100000212960177/posts/2252888268061583/](https://www.facebook.com/100000212960177/posts/2252888268061583/)

### 監測洪水災害

- 衛星影像判斷淹水的介紹
    - https://g0v.hackmd.io/PDwps3wdRgi0lxb7ExIRQg?view
- Open IR - 運用 IR 圖層監測洪水災害研究
    - [http://openir.media.mit.edu/main/?p=305](http://openir.media.mit.edu/main/?p=305)
    - [https://github.com/DuKode/OpenIR_ImageProcAndPrep](https://github.com/DuKode/OpenIR_ImageProcAndPrep)

### 光污染議題

- [https://www.facebook.com/groups/twlandsat/permalink/666405863492315/](https://www.facebook.com/groups/twlandsat/permalink/666405863492315/)
- [https://www.facebook.com/groups/twlandsat/permalink/642803099185925/](https://www.facebook.com/groups/twlandsat/permalink/642803099185925/)

### 夜照應用

- [https://www.facebook.com/dspim/posts/1851181058477025](https://www.facebook.com/dspim/posts/1851181058477025)
- [http://www.bbc.co.uk/news/resources/idt-sh/syria\_from\_space_english](http://www.bbc.co.uk/news/resources/idt-sh/syria_from_space_english)
- 英國廣播公司 (BBC) 使用美國太空總署的衛星照片，比對敘利亞在內戰開始前後的夜晚燈光亮度，以呈現戰爭對於電力設施的破壞程度，進而述說當地人民在困境中奮鬥的故事。
    - https://goo.gl/yIwTY6


### CO2 評估

- [https://co2.jpl.nasa.gov/](https://co2.jpl.nasa.gov/)

### carbon

- Satellites map carbon sequestered by forests, with accuracy of up to ten metres
    - [https://www.sciencedaily.com/releases/2017/04/170407091826.htm](https://www.sciencedaily.com/releases/2017/04/170407091826.htm)

### 空汙

- 輔助判斷 [https://www.facebook.com/act.twn/posts/500427746787720](https://www.facebook.com/act.twn/posts/500427746787720)
- [http://newtalk.tw/news/view/2015-12-15/67987](http://newtalk.tw/news/view/2015-12-15/67987)
- 應用地理資訊系統預測注意力不足過動症之發展：台灣出生世代研究
    - https://www.grb.gov.tw/search/planDetail?id=13135288
    - https://www.grb.gov.tw/search/planDetail?id=13544889
    - 注意力不足過動症 (Attention Deficit and Hyperactivity Disorder, ADHD) 為常見的兒童神經發展疾病之一。已有研究探討空污及高溫對 ADHD 之影響，但其相關結果不一致，現今臺灣尚無研究使用衛星資料探討出生前後細懸浮微 (PM2.5)、二氧化氮 (Nitrogen dioxide, NO2)、臭氧 (Ozone, O3)、二氧化硫 (Sulfur dioxide, SO2) 等空污及綜合溫度熱指數 (Wet-bulb globe temperature, WBGT) 對 ADHD 之影響。黃彬芳院長的研究利用地理資訊系統 (GIS) 整合空污所需之衛星、氣象因子、土地利用資料完成全臺灣 2004 至 2017 年，每日 1 公里解析度 PM2.5、NO2、O3、SO2 及 WBGT 之預測模式，並發現母親在妊娠期間至出生後暴露於 PM2.5、NO2、O3、SO2 及高溫，對兒童日後罹患 ADHD 有顯著之影響，值得民眾及政府相關單位加以注視——建議孕婦於懷孕期間及新生兒出生後應減少暴露於空氣污染物，以降低日後罹患 ADHD 的風險。

### 棲地研究

- [https://www.facebook.com/groups/twlandsat/permalink/642803099185925/](https://www.facebook.com/groups/twlandsat/permalink/642803099185925/)

### 監測外來物種

-

### 流域水質監測

- Connecticut-Sized Dead Zone Expected in Gulf of Mexico
    - [https://eos.org/articles/connecticut-sized-dead-zone-expected-in-gulf-of-mexico](https://eos.org/articles/connecticut-sized-dead-zone-expected-in-gulf-of-mexico)
    - A visualization of how nutrient runoff from farms (green) and cities (red) in the Mississippi River Basin influences algal blooms in the Gulf of Mexico. The warmer colors represent a higher concentration of algae. NOAA scientists predict that the size of the 2015 Gulf of Mexico dead zone, which is caused by the decomposition of these blooms, will be about the size of Connecticut. Credit: [NOAA](http://www.nnvl.noaa.gov/MediaDetail2.php?MediaID=1062&MediaTypeID=3&ResourceID=104616)

### 海洋污染防治與應變

- 應用衛星與遙測科技於海洋污染防治與緊急應變 [http://www.epa.gov.tw/ct.asp?mp=epa&xItem=25426&CtNode=31919](http://www.epa.gov.tw/ct.asp?mp=epa&xItem=25426&CtNode=31919)
- 為監控我國海域情況，環保署委託中央大學太空及遙測研究中心與美國國家海洋暨大氣總署(National Oceanic and Atmospheric Administration ,NOAA)共同簽署「台美建立衛星監測海上油污染技術合作協定」(ESTABLISHING SATELLITE-BASED MARINE OIL MONITORING COLLABORATIVE ACTIVITY)，定期以衛星航照監控我國領海周遭海域是否有異常狀況並通報環保署。
    - [https://udn.com/news/story/7321/3011551](https://udn.com/news/story/7321/3011551)
- 船隻沉沒後的油汙擴散情形
    - [https://www.facebook.com/HogazaiRiskMap/posts/682303365492087](https://www.facebook.com/HogazaiRiskMap/posts/682303365492087)

### 海浪觀測

- Understanding Ocean Wave Patterns from Satellite Imagery of Sun Glitter
    - [https://www.gislounge.com/satellite-imagery-sun-glitter-wave-patterns/](https://www.gislounge.com/satellite-imagery-sun-glitter-wave-patterns/)

### 海域浮游生物
- https://fb.watch/deQUOYT91M/

### 非法漁業調查

- [https://www.facebook.com/OceanSaysBlog/posts/617877588395196:0](https://www.facebook.com/OceanSaysBlog/posts/617877588395196:0)
    - 使用船隻衛星資料，似乎並非衛星圖？

### 國土利用監測

- [http://www.landchg.org.tw/landchgsys/](http://www.landchg.org.tw/landchgsys/)
- [https://www.facebook.com/landjusticehk/posts/944318055639230](https://www.facebook.com/landjusticehk/posts/944318055639230)
- 太陽能板與農地使用議題 [http://d4sg-solar.ddns.net/](http://d4sg-solar.ddns.net/)
- 臺北市政府工務局大地工程 103年度「臺北市山坡地衛星影像變異分析及多元尺度監測」委託專業服務案 成果報告書
    - [http://gisweb.taipei.gov.tw/opendata/resultsreport/103/B_1037007.pdf](http://gisweb.taipei.gov.tw/opendata/resultsreport/103/B_1037007.pdf)
    - 內容截圖 [https://goo.gl/photos/EshnBRayepy5gqWUA](https://goo.gl/photos/EshnBRayepy5gqWUA)
- 應用高解像力遙測影像於台北市建物屋頂加蓋物之監測
    - [http://tgis.org.tw/files/super\_pages/27\_3859579d.pdf](http://tgis.org.tw/files/super_pages/27_3859579d.pdf)
- 遙測技術於台北市土地覆蓋變遷之研究
    - [https://drive.google.com/open?id=0B9KyxXC_y1sLeWxLWGtkNDFUbmc](https://drive.google.com/open?id=0B9KyxXC_y1sLeWxLWGtkNDFUbmc)
- 遙測技術應用於臺灣西海岸五十年來變遷分析
    - [https://drive.google.com/open?id=0B9KyxXC_y1sLeWlkMVZQbS1QM28](https://drive.google.com/open?id=0B9KyxXC_y1sLeWlkMVZQbS1QM28)
- [https://www.facebook.com/UrbanDemog/posts/1774000262667852](https://www.facebook.com/UrbanDemog/posts/1774000262667852)
- Using deep learning and satellite imagery to improve land use classification in cities
https://www.facebook.com/UrbanDemog/posts/1774000262667852
- 空拍圖比對，農地工廠
https://g0v.hackmd.io/5QH2TlaXQR21wMo3UIKZug


### 控制點

- [http://track.egps.nlsc.gov.tw/CORS/Portal/map.aspx](http://track.egps.nlsc.gov.tw/CORS/Portal/map.aspx)

### 空地與空屋

- City goes hi-tech with aerial lasers to track abandoned properties [http://www.philly.com/philly/news/20161214\_City\_goes\_hi-tech\_with\_aerial\_lasers\_to\_track\_abandoned\_properties.html?mobi=true](http://www.philly.com/philly/news/20161214_City_goes_hi-tech_with_aerial_lasers_to_track_abandoned_properties.html?mobi=true)

### 街道

- Solving SpaceNet Road Detection Challenge With Deep Learning
    - [https://devblogs.nvidia.com/solving-spacenet-road-detection-challenge-deep-learning/](https://devblogs.nvidia.com/solving-spacenet-road-detection-challenge-deep-learning/)
- Scarchitecture: Aerial Photos Reveal Vanished ‘Ghost Streets’
    - [http://weburbanist.com/2015/12/15/scarchitecture-aerial-photos-reveal-vanished-ghost-streets/](http://weburbanist.com/2015/12/15/scarchitecture-aerial-photos-reveal-vanished-ghost-streets/)

### 軍事偵查
- 印度陸軍退休上校巴哈特（Vinayak Bhat）公布衛星照片，分析中國入侵台灣的軍事計畫細節，同時也建議台灣政府能夠如何進行更好的反擊。
    - https://news.ltn.com.tw/news/politics/breakingnews/2810058
    
### 戰爭破壞檢證

- [Forensic Architecture](https://www.facebook.com/forensic.architecture/)'s Interdisciplinary Analysis of War Scenes: Methodologies for Geo-synching, Plume Smoke, Shadow and NDVI Analysis.
    - [https://www.facebook.com/HumanPhysicalGeography/videos/1787687188136256/](https://www.facebook.com/HumanPhysicalGeography/videos/1787687188136256/)
- 200 newly damaged structures in [#Daraa](https://g0v.hackpad.tw/ep/search/?q=%23Daraa&via=FTBOsiElsPY) between June 2015 and April 2016
    - [https://www.facebook.com/UNITAR.unosat/photos/a.671616739527721.1073741827.332115900144475/1309750955714293/?type=3&theater](https://www.facebook.com/UNITAR.unosat/photos/a.671616739527721.1073741827.332115900144475/1309750955714293/?type=3&theater)
- Damage assessment of Daraa, Daraa Governorate, Syria
    - [http://ow.ly/ePLN307FEeQ](http://ow.ly/ePLN307FEeQ)
- 清真寺
    - https://www.rti.org.tw/news/view/id/2020088


### 歷史研究
- 長城歷史研究
    - https://m.facebook.com/story.php?story_fbid=pfbid0prvX8evwmNan6rqHdBM5qiPhbRQBgdTirRpamynuABNJBDK7WxfWoLzvmsSu2tFXl&id=100067002858035

### 社會議題

- predict poverty
    - Satellite images can map poverty [http://www.sciencemag.org/news/2016/08/satellite-images-can-map-poverty](http://www.sciencemag.org/news/2016/08/satellite-images-can-map-poverty)
    - Combining satellite imagery and machine learning to predict poverty [http://science.sciencemag.org/content/353/6301/790](http://science.sciencemag.org/content/353/6301/790)
- 血汗工廠
    - [https://www.facebook.com/groups/d4sg.taiwan/permalink/1917329055210344/](https://www.facebook.com/groups/d4sg.taiwan/permalink/1917329055210344/)
- 再教育營區地點
    - https://www.facebook.com/1253684782/posts/10226722418907287/

## 製圖

### 製作地圖

- MapKnitter - Make maps from aerial photos
    - [http://mapknitter.org/](http://mapknitter.org/)


## 社會應用

### 應用於教育與教學

- [福衛二號衛星影像應用於國中小社會領域教學](http://www.geo.ntnu.edu.tw/people/writing_seminar.php?Sn=538)
- LAND LINES - Start with a line, let the planet complete the picture. [https://lines.chromeexperiments.com/](https://lines.chromeexperiments.com/)

### PPGIS 或其它空間規劃參與

-

## 待整理文章

### 100 Earth Shattering Remote Sensing Applications & Uses

- 大補帖：[http://gisgeography.com/100-earth-remote-sensing-applications-uses/](http://gisgeography.com/100-earth-remote-sensing-applications-uses/)

- 中大整理遙測技術應用
    -  [http://www.csrsr.ncu.edu.tw/08CSRWeb/ChinVer/C6TechSupp/RSApp.php](http://www.csrsr.ncu.edu.tw/08CSRWeb/ChinVer/C6TechSupp/RSApp.php)

- 開源遙感探測影像分析工具Orfeo，Orfeo ToolBox Plugin for QGIS安裝步驟：
    - [http://gis.rchss.sinica.edu.tw/qgis/?p=3687](http://gis.rchss.sinica.edu.tw/qgis/?p=3687)

IDB: A Database for Remote Sensing Ιndices: [http://www.indexdatabase.de](http://www.indexdatabase.de)

Top 14 Open Source Remote Sensing Software
- [http://monde-geospatial.com/top-14-open-source-remote-sensing-software/](http://monde-geospatial.com/top-14-open-source-remote-sensing-software/)

[https://www.richitech.com.tw/8560/%E3%80%90%E7%91%9E%E7%AB%A3%E9%9B%BB%E5%AD%90%E5%A0%B1%E3%80%91landsat%E8%A1%9B%E6%98%9F%E5%BD%B1%E5%83%8F%E9%9B%B2%E7%AB%AF%E5%88%86%E6%9E%90%E6%96%B0%E5%B7%A5%E5%85%B7/](https://www.richitech.com.tw/8560/%E3%80%90%E7%91%9E%E7%AB%A3%E9%9B%BB%E5%AD%90%E5%A0%B1%E3%80%91landsat%E8%A1%9B%E6%98%9F%E5%BD%B1%E5%83%8F%E9%9B%B2%E7%AB%AF%E5%88%86%E6%9E%90%E6%96%B0%E5%B7%A5%E5%85%B7/)

## 其他不必然與衛星圖相關

- ALOS
    - [http://www.csrsr.ncu.edu.tw/csrsr\_new\_site/Website/img/index/speech/160908/0908_ALOS.pdf](http://www.csrsr.ncu.edu.tw/csrsr_new_site/Website/img/index/speech/160908/0908_ALOS.pdf)
- Terra Incognita™
    - Program for downloading web source maps or local files maps for various programs or GPS devices.
    - [http://monde-geospatial.com/download-very-hight-resolution-satellite-image-into-5m/](http://monde-geospatial.com/download-very-hight-resolution-satellite-image-into-5m/)
    - [https://sourceforge.net/p/terraincognita2/wiki/Home/](https://sourceforge.net/p/terraincognita2/wiki/Home/)
- The folks at GrindGis.com have put together a long list of 50 different applications of [#LiDAR](https://g0v.hackpad.tw/ep/search/?q=%23LiDAR&via=FTBOsiElsPY) ranging from simple DEM creation via Solar Energy Planning and Dune Monitoring to Integrated Storm Water Management. Is your application listed ... ? (-:
    - [https://www.facebook.com/LAStools/posts/1397878080274632](https://www.facebook.com/LAStools/posts/1397878080274632)
- Carbon Footprint: The Most Comprehensive Map of a City's Carbon Footprint Ever
    - [http://www.citylab.com/weather/2016/01/berkeley-climate-change-map-cities/423753/?utm_source=SFFB](http://www.citylab.com/weather/2016/01/berkeley-climate-change-map-cities/423753/?utm_source=SFFB)
- Issue Mapping
    - https://g0v.hackmd.io/eraUN0_hSnKu04fVeTD2eQ?view
- 中國圖資
    - [https://map.51240.com/](https://map.51240.com/)
    - [http://m.cnyes.com/news/id/1130808](http://m.cnyes.com/news/id/1130808)
- [https://www.youtube.com/watch?v=D75UiEkGURI](https://www.youtube.com/watch?v=D75UiEkGURI)







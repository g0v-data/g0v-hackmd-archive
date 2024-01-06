---
title: "2014-09-22 Open Geo Data for Government 第三次會議"
tags: hackpad
---

# 2014-09-22 Open Geo Data for Government 第三次會議

> [點此觀看原始內容](https://g0v.hackpad.tw/8w981qZZoeF)

內容來源：[https://osmtw.hackpad.com/2014-09-22-Open-Geo-Data-for-Government--DTEWmteznmn](https://osmtw.hackpad.com/2014-09-22-Open-Geo-Data-for-Government--DTEWmteznmn)

1.  會議資訊：9/22 (一) 中午 12:00 行政院一樓內廂會議室
2.  出席者：時任政務委員蔡玉玲、國土處郭處長
3.  報名請至：[2014 08 19 Open Geo Data for Government](https://osmtw.hackpad.com/5he3FAtUcQF)
4.  Hackfoldr：[http://hackfoldr.org/OpenGeoData](http://hackfoldr.org/OpenGeoData)
5.  [Open Geo Data for Government - legal issues](https://osmtw.hackpad.com/Open-Geo-Data-for-Government-legal-issues)
6.  [防災開放資料應用典範](http://hackfoldr.org/OpenGeoData/LKgdTOFMlpD)
7.  [NGIS 圖資清單](https://docs.google.com/spreadsheets/d/tA2Vu_ajWywAx3fjsaM9Rug/htmlview#)
8.  淺述 ODbL-1.0 及 OSMF 授權吸納模式 / 林誠夏 台灣創用CC計畫 法律項目主持人
    1.  簡報LibreOffice編輯格式下載連結：[http://www.openfoundry.org/of/download\_path/openlegal/Basic\_Introduction\_to\_ODbL\_and\_OSMF\_Contributor\_Terms/20140922.odp](http://www.openfoundry.org/of/download_path/openlegal/Basic_Introduction_to_ODbL_and_OSMF_Contributor_Terms/20140922.odp)
    2.  簡報PDF播放格式下載連結：[http://www.openfoundry.org/of/download\_path/openlegal/Basic\_Introduction\_to\_ODbL\_and\_OSMF\_Contributor\_Terms/20140922.pdf](http://www.openfoundry.org/of/download_path/openlegal/Basic_Introduction_to_ODbL_and_OSMF_Contributor_Terms/20140922.pdf)

## 會議簡要紀錄


秒懂合作模式
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f377133cb7415eddd89d2f21e8ac3fa3)
(需要編輯請[自取](https://docs.google.com/drawings/d/10jAxlbeen6ZzTuCVQtyGdeZEk4xdYl16P3qXZXUb09Y/edit?usp=sharing) )


### OSM 想要的...

Open Street Map 社群期待公部門圖資能夠開放。

### OSM 社群在乎的...

1.  群眾所繪製的圖資成果，開放 (**Open**)：
    1.  non-exclusive / 非專屬。
    2.  irrevocable / 不可撤回。
    3.  sub-license / 可再／轉授權。
2.  **Community**：社群互助，實體活動，圖客培力，接力傳承，永續繁榮(誤)。
3.  **Open Source** 的工具。

### 防災公民面對的...

- 繁多混亂的資訊「格式」，例如 PDF、電子信件中的內容...
    1.  例：高雄市氣爆後的停車場資訊。
    2.  例：沙包數量與位置的資訊。
- 「即時」是重要的。
- NCDR 的 [CAP](https://alerts.ncdr.nat.gov.tw/) 仍是目前適切的資訊平台。
- OSM 離線地圖，在救災情境中，發揮重要作用！
- 美日，防災松、避難地圖松、災害準備松 ([參考](http://hackfoldr.org/OpenGeoData/LKgdTOFMlpD))。

### Gov 想到的...

國土處提出，是否以[「國土利用調查成果圖」](http://tmap.geospatial.org.tw/)作為合作主題。
- NGIS圖台 > 土地基本 > 國土測繪中心 > 國土利用調查成果圖
- 與會社群意見：
1.  若是想掌握現有土地使用現狀，可以用軟體程式透過現有 OSM 資料庫自動對造查驗國土利用調查成果圖。
2.  此圖資已是利用基礎圖資產生出來的 metadata，而非可利用於開放街圖圖客參考使用的基礎圖資，且此圖資主題與 OSM 地圖編製內容，稍有落差。另外如土地地號、地籍圖等圖資主題，目前也並非 OSM 所支援的。
4.  關於此圖的測繪過程與方法、圖例意義，請參考 [國土利用分類說明](http://lui.nlsc.gov.tw/LUWeb/Home/Content.aspx?MUID=3670dcfe-dfea-446d-8afd-ee1ca7abc054)。
5.  國土利用調查成果圖，比較吸引國內的環境議題與國土利用的社群或環保組織利用。
6.  初步揣摩，不太理解此圖資與防災主題之間的關聯性；是否有包含建築物街道細節資訊（如外框）的圖資會更適合呢？

#### 討論

國土利用調查成果與於防災、環境議題建議： 國土利用調查成果在防災上可以提供作為 淹水模擬、洪水預警、崩塌模式等相關防災模式參數資料基本資訊來源，但目前國土地調查成果圖對外開放只利用色階資訊上提供土地利用的對應資訊，若要直接在直接使用該資料仍有一定的困難程度或。建議搭配內政部目前開放的100m 的DSM或DEM資料的解析度提供數值檔案給 osm組織進行應用，另外荷蘭研究單位有利用osm的資訊作為模式所需資料來源進行都市水資源模擬 ）
> 100M DSM/DEM 精度太低，可用性不高？
> [name=Guest]

> 不同模式需求不同 以水文模式為例 現階段若使用100m資料解析度其實相當充裕
> [name=Guest]

> 淹水模式目前最小解析度使用到5米（但目前資料屬於管制資料）
> [name=Guest]

> 由於相關土壤、地質資料解析度更低，因此在現現階段若可以提供全台100m網格的高程、土地利用、土壤、地質、土壤濕度、人口密度等相關資料對於防災應用或者相關學術研究其實可以有很多應用與探討，主要原因為目前相關資料並不容易取得，政府單位可以在持續基礎資料上進行更新與維護，在後續政府單位認為5m資料可以公開後再將全國資料提升到5m的解析度
> [name=Guest]

> 跪求荷蘭水資源合作模式的連結　thanks! 
> [name=Guest]

> 由荷蘭 Deltares 水利模式利用osm資料擷取程式 [內容](https://code.google.com/p/osm2hydro/) 前述osm工具完整應用 [說明](https://code.google.com/p/osm2hydro/)
> [name=Guest]



### Gov 與 OSM 相互貢獻...

- 授權大小事，請見：**淺述 ODbL-1.0 及 OSMF 授權吸納模式** / 林誠夏 台灣創用CC計畫 法律項目主持人
    1.  簡報LibreOffice編輯格式下載連結：[http://www.openfoundry.org/of/download\_path/openlegal/Basic\_Introduction\_to\_ODbL\_and\_OSMF\_Contributor\_Terms/20140922.odp](http://www.openfoundry.org/of/download_path/openlegal/Basic_Introduction_to_ODbL_and_OSMF_Contributor_Terms/20140922.odp)
    2.  簡報PDF播放格式下載連結：[http://www.openfoundry.org/of/download\_path/openlegal/Basic\_Introduction\_to\_ODbL\_and\_OSMF\_Contributor\_Terms/20140922.pdf](http://www.openfoundry.org/of/download_path/openlegal/Basic_Introduction_to_ODbL_and_OSMF_Contributor_Terms/20140922.pdf)
- 案例：英國 project ...?

### Gov 靈機一動：仿效 OSM 模式，自己的開放圖資自己作

- 知名案例：**USGS The National Map **
    1.  [http://nationalmap.gov](http://nationalmap.gov)
    2.  [https://crowdgov.wordpress.com/case-studies/national-map-corps/](https://crowdgov.wordpress.com/case-studies/national-map-corps/)
    3.  運用 OSM 編輯器。
    4.  與 OSM database 毫無關聯。
- 更多案例請見：[Open Geo Data for Government - Cases of OSM and Gov collaboration mode](http://hackfoldr.org/OpenGeoData/FH8Jcnpt052)
- 國內類似經驗：農委會特生中心的**路殺社**
    - [http://roadkill.tw](http://roadkill.tw)
    - 農委會評估，"放棄"權利 (精確用詞再請補充) 可以免去可預期的公務程序。
- [NGIS 2020](http://ngis.nat.gov.tw/1_5_1.aspx)
- 開放資料政策所涉及的相關規範、規費、測繪法等問題，另有政策專案研討中。
> 我覺得可以說服國發會的是利用群眾外包去蒐集資料，可以節省全面性調查的成本，相對的也不應該利用規費去回收這些成本
> [name=Guest]


### 後續發想

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9b9ff11d54ba6a2008ecc0bcc3f7283b)
([原始圖檔](https://docs.google.com/drawings/d/15AYt_Q2SCSOBZkNMnuvgmWHNRP-OTcvcMFsYm9wveN0/edit?usp=sharing) )

花絮照片
![](https://hackpad-attachments.imgix.net/hackpad.com_DTEWmteznmn_p.208757_1411389067153_DSC05729.JPG?fit=max&w=882)


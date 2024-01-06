---
title: "五星等開放資料標準"
tags: hackpad
---

# 五星等開放資料標準

> [點此觀看原始內容](https://g0v.hackpad.tw/imlFqCxzU1f)

授權：CC 4.0 BY SA



五星等開放資料標準衡量資料品質的方法，可作為政府機關、民間開放資料的衡量標準。星等是累進式的，比方：沒有一星等「開放授權」的資料，就算是機器可讀，也不會算是二星等。


### 一星等：開放授權

> 從原作來看，一星核心是資料上線，開放授權只是伴隨的條件。
> [name=nchild]

> 我以為開放授權是必要條件，不然連一顆星都沒有
> [name=Muyueh L]


開放授權是有國際公認標準，自己平台上的授權，必須與國際公認的授權相容，不然不能稱之為開放授權，國際公認開放授權：
    - [PDDL](http://www.opendatacommons.org/licenses/pddl/)
    - [ODC-by](http://www.opendatacommons.org/licenses/by/)
    - [CC0](http://creativecommons.org/publicdomain/zero/1.0/)
- 符合：
    - 要求使用者標記資料來源
- 不建議：
    - 以一次性收費方式要求使用者付費
- 不符合：
    - 需要事前申請
    - 以 Revenue Sharing 的方式要求使用者付費
    - 只針對特定對象（例如：學術單位）
    - 不準改作（例如：[http://www.npm.gov.tw/opendata/datarule.html](http://www.npm.gov.tw/opendata/datarule.html)）


### 二星等：機器可讀的結構化資料

- 原始檔，而非輸出品：諸如圖片、影片、照片等製作物。這些東西通常都是外包廠商進行製作，只有最終成果獲得保存。這一個問題是，這些素材通常解析度很低，而且不能被修改。
    - 給印刷廠的是原始檔，印出來的東西是輸出品
    - doc、docx 是原始檔，pdf 是輸出品
    - 地理資訊是原始檔，圖磚是輸出品
    - 照片是原始檔，在簡報裡面的照片是輸出品
- 可以重複被使用：假如使用者要重複使用的話，就需要人一個字一個字 key-in，無法被機器閱讀。這也包含諸如地理資訊以圖磚方式釋出。
- 機器可讀：會出現這樣的問題，絕大部份是因為政府想要發佈這些資訊，只有兼顧「給人看」，但在開放資料中，除了人看，還要「機器看」。
- [看起來最簡單就是對的](https://speakerdeck.com/clkao/lao-dong-bu-yan-xi?slide=70&hc_location=ufi)
    - 一個資料集若有多個報表，每一個[報表應該獨立抽出](https://speakerdeck.com/clkao/lao-dong-bu-yan-xi?slide=66&hc_location=ufi)
    - 不要額外標頭
    - 不要小計
    - 不要合併儲存格、不要標頭拆欄

- 符合：
    -
- 不建議：
    - 文字儲存的 .pdf
    - 過於特別的方式儲存資料
    - 骯髒的資料
    - pdf
    - .ai
    - .xls, .xlsx (Microsoft)
    - .doc, .docx (Microsoft)
- 不符合：
    - 以圖片儲存的 .pdf
    - .png
    - .jpg, .jpeg
> 我想請問，如果只有紙本公文，掃描後成為圖片儲存的pdf，這一樣是「輸出後的資料」嗎？還是這比較接近「原始資料」？
> [name=雨蒼 林]

> 如果像是一本「[內湖區都市計畫書](https://g0v.hackpad.tw/--pJUQ0AGRCO1)」，要怎麼樣變成二星等呢？思考ing... 或是說，如果要符合星等定義，既有的都市計畫內容應該如何改寫？[都市計畫書三星化 方法討論](https://g0v.hackpad.tw/--2qR2Pzdu95W)
> [name=che l]


### 三星等：開放格式

- 符合：
    - .tsv, .csv, .dsv
    - .json, .geojson, .topojson
    - .xml
    - .shp
- 不符合：
    - .xls, .xlsx (Microsoft)
    - .doc, .docx (Microsoft)

### 四星等：每行資料都有唯一超連結

- 符合
    -
- 不符合：
    -

### 五星等：資料連結

- 符合：
    - [schema.org](http://schema.org/)
    - [dbpedia.org](http://dbpedia.org/)
    - [wikidata.org](https://www.wikidata.org/wiki/Wikidata:%E9%A6%96%E9%A0%81)
- 不符合：


### 其他：




相關網站：[http://5stardata.info/](http://5stardata.info/)


---
title: "登革熱地圖"
tags: Issue-Mapping,hackpad
---

# 登革熱地圖

> [點此觀看原始內容](https://g0v.hackpad.tw/9KM0NYuFLJS)


主要延續自 [高雄氣爆和登革熱爆發地圖視覺化](https://g0v.hackpad.tw/NpPQ1UZc3Up)  ，陸續衍生了幾個地圖，如果沒有特別說明就是 MIT 授權

- [台南登革熱地圖](http://kiang.github.io/TainanDengueMap/) (kiang)
    - 資料來源： [http://health.tainan.gov.tw/tnhealth/Medical/Medical.aspx?Medical\_Index=4&Medical\_Class=0](http://health.tainan.gov.tw/tnhealth/Medical/Medical.aspx?Medical_Index=4&Medical_Class=0)
    - 村里界圖取自 [https://sheethub.com/data.gov.tw/%E6%9D%91%E9%87%8C%E7%95%8C%E5%9C%96%28WGS84%E7%B6%93%E7%B7%AF%E5%BA%A6%29](https://sheethub.com/data.gov.tw/%E6%9D%91%E9%87%8C%E7%95%8C%E5%9C%96%28WGS84%E7%B6%93%E7%B7%AF%E5%BA%A6%29) ，以 [程式](https://github.com/kiang/TainanDengueMap/blob/gh-pages/geojson/filter.php) 取出台南部份
    - 原本有想改用 [http://data.tainan.gov.tw/dataset/denguefevercases](http://data.tainan.gov.tw/dataset/denguefevercases) ，但是更新頻率不定所以就沒有切換了
    - 更新步驟
        - 下載最新 Excel 檔案，通常在下午會出現前一天最新病例統計
        - 另存 csv 到 [https://github.com/kiang/TainanDengueMap/blob/gh-pages/scripts/latest.csv](https://github.com/kiang/TainanDengueMap/blob/gh-pages/scripts/latest.csv)
        - 修改程式日期 [https://github.com/kiang/TainanDengueMap/blob/gh-pages/scripts/query.php](https://github.com/kiang/TainanDengueMap/blob/gh-pages/scripts/query.php)
        - 執行上述程式更新
        - 原始檔案備份 [https://github.com/kiang/TainanDengueMap/tree/gh-pages/raw](https://github.com/kiang/TainanDengueMap/tree/gh-pages/raw)
    - 檔案說明
        - 台南市村里界 \- geojson - [https://github.com/kiang/TainanDengueMap/blob/gh-pages/cunliTN.json](https://github.com/kiang/TainanDengueMap/blob/gh-pages/cunliTN.json)
        - 台南市村里每日登革熱病例 \- json - [https://github.com/kiang/TainanDengueMap/blob/gh-pages/DengueTN.json](https://github.com/kiang/TainanDengueMap/blob/gh-pages/DengueTN.json)
- [病媒蚊密度調查](http://weoi.github.io/TainanDengueMap/)  (weoi)
    - 資料來源： [http://data.tainan.gov.tw/dataset/2015-df-mosquito-density](http://data.tainan.gov.tw/dataset/2015-df-mosquito-density)
- [台灣2015登革熱地圖](http://kiang.github.io/TainanDengueMap/taiwan/)  (kiang)
    - 資料來源： [http://nidss.cdc.gov.tw/download/Dengue_Daily.csv](http://nidss.cdc.gov.tw/download/Dengue_Daily.csv) (ref: [http://data.gov.tw/node/gov/resource/16702](http://data.gov.tw/node/gov/resource/16702) )
    - 村里界圖取自 [https://sheethub.com/data.gov.tw/%E6%9D%91%E9%87%8C%E7%95%8C%E5%9C%96%28WGS84%E7%B6%93%E7%B7%AF%E5%BA%A6%29](https://sheethub.com/data.gov.tw/%E6%9D%91%E9%87%8C%E7%95%8C%E5%9C%96%28WGS84%E7%B6%93%E7%B7%AF%E5%BA%A6%29) ，以 [程式](https://github.com/kiang/TainanDengueMap/blob/gh-pages/geojson/topojson.php)  轉為 topojson 格式
    - 村里代碼取自 [http://www.dgbas.gov.tw/ct.asp?xItem=951&ctNode=5485](http://www.dgbas.gov.tw/ct.asp?xItem=951&ctNode=5485)
    - 更新步驟
        - 執行 [https://github.com/kiang/TainanDengueMap/blob/gh-pages/cdc/query.php](https://github.com/kiang/TainanDengueMap/blob/gh-pages/cdc/query.php) 即可完成更新
        - 目前放入 [https://github.com/kiang/TainanDengueMap/blob/gh-pages/bin/cdc.php](https://github.com/kiang/TainanDengueMap/blob/gh-pages/bin/cdc.php)  ，設定下面排程
            0 9 * * * /usr/bin/php -q /home/kiang/github/TainanDengueMap/bin/cdc.php
    - 檔案說明
        - 全國村里界 \- topojson - [https://github.com/kiang/TainanDengueMap/blob/gh-pages/taiwan/cunli.json](https://github.com/kiang/TainanDengueMap/blob/gh-pages/taiwan/cunli.json)
        - 2015 全國村里每日登革熱病例 - json - [https://github.com/kiang/TainanDengueMap/blob/gh-pages/taiwan/Dengue.json](https://github.com/kiang/TainanDengueMap/blob/gh-pages/taiwan/Dengue.json)
        - 全國村里代碼 \- csv - [https://github.com/kiang/TainanDengueMap/blob/gh-pages/data.tainan/cunli_code.csv](https://github.com/kiang/TainanDengueMap/blob/gh-pages/data.tainan/cunli_code.csv)
- [台灣2015登革熱病例分佈地圖](http://kiang.github.io/TainanDengueMap/taiwan/points.html) (kiang)
    - 資料來源： [http://cdcdengue.azurewebsites.net/DengueData.asmx/GetDengueLocation](http://cdcdengue.azurewebsites.net/DengueData.asmx/GetDengueLocation) ( 雖然後來 [http://data.gov.tw/node/gov/resource/16702](http://data.gov.tw/node/gov/resource/16702) 也有座標，但差異不大，所以就沒有特別改程式了 )
    - 更新步驟
        - 執行 [https://github.com/kiang/TainanDengueMap/blob/gh-pages/cdc/points.php](https://github.com/kiang/TainanDengueMap/blob/gh-pages/cdc/points.php) 即可完成更新
        - 目前放入 [https://github.com/kiang/TainanDengueMap/blob/gh-pages/bin/cdc.php](https://github.com/kiang/TainanDengueMap/blob/gh-pages/bin/cdc.php)  ，設定下面排程
            0 9 * * * /usr/bin/php -q /home/kiang/github/TainanDengueMap/bin/cdc.php
    - 檔案說明
        - 登革熱病例[最小統計區](http://moisagis.moi.gov.tw/moiap/match/system_common.cfm)中心點位 \- json - [https://github.com/kiang/TainanDengueMap/blob/gh-pages/cdc/points.json](https://github.com/kiang/TainanDengueMap/blob/gh-pages/cdc/points.json)
- [登革熱密度地圖](http://happychang.github.io/fever2/)  (happychang)
    - 直接使用 台灣2015登革熱病例分佈地圖 的病例資料
- [台灣2014登革熱地圖](http://kiang.github.io/TainanDengueMap/taiwan/2014/)  (kiang)
    - 使用與 台灣2015登革熱地圖 同樣的程式，主要是想要看兩年分佈的差異而製作
- [台南登革熱噴藥地圖](http://kiang.github.io/TainanDengueMap/chemical/)  (kiang)
    - 資料來源： [http://data.tainan.gov.tw/dataset/4c260d97-e268-4b4a-8b15-c0fc92a25120](http://data.tainan.gov.tw/dataset/4c260d97-e268-4b4a-8b15-c0fc92a25120)
    - 更新步驟
        - 執行 [https://github.com/kiang/TainanDengueMap/blob/gh-pages/chemical/query.php](https://github.com/kiang/TainanDengueMap/blob/gh-pages/chemical/query.php) 即可完成更新
        - 目前放入 [https://github.com/kiang/TainanDengueMap/blob/gh-pages/bin/cdc.php](https://github.com/kiang/TainanDengueMap/blob/gh-pages/bin/cdc.php)  ，設定下面排程
            0 9 * * * /usr/bin/php -q /home/kiang/github/TainanDengueMap/bin/cdc.php
    - 檔案說明
        - 噴藥行程村里與集合地點 \- json - [https://github.com/kiang/TainanDengueMap/blob/gh-pages/chemical/overlays.json](https://github.com/kiang/TainanDengueMap/blob/gh-pages/chemical/overlays.json)
- [臺南市登革熱戶外化學防疫軌跡記錄地圖](http://kiang.github.io/TainanDengueMap/tracks/)  (kiang)
    - 資料來源： [http://data.tainan.gov.tw/dataset/dengue-chemical-prevention](http://data.tainan.gov.tw/dataset/dengue-chemical-prevention)
- [台南待孳清空地空屋](http://ushahidi.olc.tw)  (kiang)
    - 資料來源： [http://data.tainan.gov.tw/dataset/dengue-dist/resource/d0fb0392-1fc2-4866-80a1-cab1062a18ea](http://data.tainan.gov.tw/dataset/dengue-dist/resource/d0fb0392-1fc2-4866-80a1-cab1062a18ea)
    - Ushahidi V3 製作 [https://github.com/ushahidi/platform](https://github.com/ushahidi/platform) & [https://github.com/ushahidi/platform-client](https://github.com/ushahidi/platform-client)
        - 中文化已經提供給官方，有興趣可以參與後續翻譯 \- [https://www.transifex.com/ushahidi/ushahidi-v3/](https://www.transifex.com/ushahidi/ushahidi-v3/)
    - 以 google map api 製作的簡化終端 - [http://kiang.github.io/ushahidi_posts/](http://kiang.github.io/ushahidi_posts/)
        - 說明 \- [http://k.olc.tw/2015/10/%e5%8f%b0%e5%8d%97%e5%be%85%e5%ad%b3%e6%b8%85%e7%a9%ba%e5%9c%b0%e7%a9%ba%e5%b1%8b-%e9%9c%80%e8%a6%81%e6%82%a8%e7%9a%84%e5%8d%94%e5%8a%a9/](http://k.olc.tw/2015/10/%e5%8f%b0%e5%8d%97%e5%be%85%e5%ad%b3%e6%b8%85%e7%a9%ba%e5%9c%b0%e7%a9%ba%e5%b1%8b-%e9%9c%80%e8%a6%81%e6%82%a8%e7%9a%84%e5%8d%94%e5%8a%a9/)
- [台灣老人分佈地圖](http://kiang.github.io/tw_population/)  (kiang)
    - 想要找尋登革熱病例分佈可能的原因所製作
    - 資料來源： [http://data.moi.gov.tw/MoiOD/Data/DataDetail.aspx?oid=F4478CE5-7A72-4B14-B91A-F4701758328F](http://data.moi.gov.tw/MoiOD/Data/DataDetail.aspx?oid=F4478CE5-7A72-4B14-B91A-F4701758328F)


其他未製圖統計資料
- 歷年登革熱病例年齡分佈統計 \- [https://github.com/kiang/](https://github.com/kiang/TainanDengueMap/blob/gh-pages/cdc/age_sum.csv)[TainanDengueMap/blob/gh-pages/cdc/age_sum.csv](https://github.com/kiang/TainanDengueMap/blob/gh-pages/cdc/age_sum.csv)
- 2015 年以來登革熱病例村里發生率（病例數除以 2015/7 人口數字） - [https://github.com/kiang/TainanDengueMap/blob/gh-pages/cdc/cunli_rate.csv](https://github.com/kiang/TainanDengueMap/blob/gh-pages/cdc/cunli_rate.csv)
- 2015 登革熱病例數字相對同年齡層人口比率 - [https://github.com/kiang/TainanDengueMap/blob/gh-pages/cdc/city\_age\_rate_2015.csv](https://github.com/kiang/TainanDengueMap/blob/gh-pages/cdc/city_age_rate_2015.csv)
- 村里病例數字變化統計 \- [https://github.com/kiang/](https://github.com/kiang/TainanDengueMap/blob/gh-pages/cdc/cunli_sum.csv)[TainanDengueMap/blob/gh-pages/cdc/cunli_sum.csv](https://github.com/kiang/TainanDengueMap/blob/gh-pages/cdc/cunli_sum.csv)


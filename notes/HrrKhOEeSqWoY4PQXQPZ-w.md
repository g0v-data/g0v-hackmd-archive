---
title: "地震資訊的視覺化"
tags: 災害,hackpad
---

# 地震資訊的視覺化


[**Kirby Wu**](https://www.facebook.com/zbryikt?fref=ufi)**>** 地震資訊視覺化也很有趣, 我覺得可以做, 但因為災害地圖是以傷亡人數來計, 感覺可以做一個主題為地震資訊的視覺化. 這些地震的資料也可以拿來比對看災害列表 wiki 裡寫的正確性或經緯度. 如果有興趣的話, 大家一起把地震資料整理到 google spreadsheet, 等我把時序泡泡圖視覺化模組做好, 就可以拿來呈現了

## 歷年地震資料來源

- 台灣地區歷史記載地震(1604-1897年) [http://gis.geo.ncu.edu.tw/gis/eq/eq1600.htm](http://gis.geo.ncu.edu.tw/gis/eq/eq1600.htm)
- 台灣地區之災害性地震(1900-1994年) [http://gis.geo.ncu.edu.tw/gis/eq/eqhazard.htm](http://gis.geo.ncu.edu.tw/gis/eq/eqhazard.htm)
- 台灣地區歷史地震資料庫的網頁資料(共 8 筆資料) [http://tec.earth.sinica.edu.tw/TEM/hisevent/hisdoc.php](http://tec.earth.sinica.edu.tw/TEM/hisevent/hisdoc.php)
- 1720-2013 共計約 76 筆 [http://zh.wikipedia.org/.../%E8%87%BA%E7%81%A3%E5%9C%B0](http://zh.wikipedia.org/.../%E8%87%BA%E7%81%A3%E5%9C%B0)[...](http://zh.wikipedia.org/wiki/%E8%87%BA%E7%81%A3%E5%9C%B0%E9%9C%87%E5%88%97%E8%A1%A8)
- 地震年表--中華民國(1912~1972) [http://921kb.sinica.edu.tw/history/quake_history.html](http://921kb.sinica.edu.tw/history/quake_history.html)
    - 參考文獻 ：
        - 清代臺灣天然災害史料彙編，徐泓，中華民國七十二年七月出版。
        - 臺灣地震目錄，徐明同編，中華民國六十八年一月出版。
        - 《明清時代破壞性大地震規模及震度之評估》，氣象學報第29卷第四期，徐明同，中華民國七十二年十二月出版。
- 中央氣象局
    - 臺灣地區地震活動特性探討 [http://gdms.cwb.gov.tw/20/chapters/ch4.html](http://gdms.cwb.gov.tw/20/chapters/ch4.html)
    - 地球物理資料管理系統 [http://gdms.cwb.gov.tw/index.php](http://gdms.cwb.gov.tw/index.php)
> 爬了一下地震列表，1995 至今: [https://docs.google.com/spreadsheets/d/1nAljjnD8iDjIOENc2KXmqx4-4iC2zWOuByN6tCURv1g/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1nAljjnD8iDjIOENc2KXmqx4-4iC2zWOuByN6tCURv1g/edit?usp=sharing)
> [name=Kirby W]

待補充
#gis 頻道，ronny 爬的資料集

- 臺北市志內紀錄的歷史地震 [https://goo.gl/photos/ZhutpKsAp9S7Ao3m8](https://goo.gl/photos/ZhutpKsAp9S7Ao3m8)
- 昭和十年台湾大震災記念画報
    - [http://rarebooks.ith.sinica.edu.tw/sinicafrsFront99/search/search_result2.htm?xmlId=0000127085&display=detail](http://rarebooks.ith.sinica.edu.tw/sinicafrsFront99/search/search_result2.htm?xmlId=0000127085&display=detail)

## 地震資料特質討論

1.  科學資料：時間、位置、深度、P波、S波、芮氏規模...
2.  描述資料或歷史文件
3.  傷亡

## 視覺化討論

案例
- 21世紀の世界の地震 21st-century Earthquakes 2016-03-01
    - https://youtu.be/W0_Z9Wga5A8
    - 影片方式，導入「聲音」向度，來呈現密集度與規模大小
- 義大利鄰近地震地圖
    - 位置、深度、芮氏規模、時間 / 2000-2012, 50000 次地震
    - http://www.arcgis.com/apps/OnePane/main/index.html?appid=3bcd16f3a7a44b678bbe0329a89ff04f
- 日本の地震 Japan Earthquakes 2017-01-01
    - https://youtu.be/VxQzVSjSAyk
    - 有擬訂圖像標註方法，處理震源深度、地震規模等
- EQ3D is a simplified version of the application program Earthquake 3D running in an internet browser.
    - http://www.earthquake3d.com/
- Mapping 100 Years of Earthquakes, in 3-D
    - http://www.citylab.com/weather/2015/10/mapping-100-years-of-earthquakes-in-3d/409894/
- A Decade of Great Earthquakes
    - https://www.youtube.com/watch?v=Ls3T5Of690I&feature=youtube_gdata_player
- Dataset of all the earthquakes from 2001 through 2015
    - https://www.facebook.com/scienceonasphere/videos/10157877630135083/
- 日本與台灣的地震，立體呈現震源深度，歷年地震
    - https://nagix.github.io/japan-eq-locator/?e=20240808164303&lng=131.7&lat=31.8&d=30&l=%E6%97%A5%E5%90%91%E7%81%98&t=2024-08-08T16:43:00+09:00&m=7.1&s=6-
- 震源深度+球體
    - https://fbwat.ch/1JSKXn44a5uL2yRi
- A Real-Time Map of Earthquakes Around the World:
- https://www.mapbox.com/bites/00267/
- 震源實體化
    - http://dmc.earth.sinica.edu.tw/papermodel/
    - http://a-chien.blogspot.tw/2016/08/6-openscad.html
- This visualization is the first global tomographic model constructed based on adjoint tomography, an iterative full-waveform inversion technique.
    - https://www.olcf.ornl.gov/2017/03/28/a-seismic-mapping-milestone/
- 平面設計構想
    - https://www.facebook.com/mapmker/photos/a.330332597408136.1073741828.310109022763827/333309937110402/?type=3&theater
- Watch seismic waves travel through and around the earth
    - https://www.facebook.com/IRISEarthquake/videos/530450397412243/

歸納
- 基本形式：
    - 互動式網頁
    - 影片
    - 實體出版品
- 平面或球面
- 要不要呈現出震源深度
- 要不要呈現震波傳遞



## 議題團體

- 台灣地震科學中心(TEC)
    - fb 社團 [https://www.facebook.com/groups/655046344513665/](https://www.facebook.com/groups/655046344513665/)
- 國立臺灣歷史博物館 National Museum of Taiwan History「地震帶上的共同體：歷史中的臺日震災」特展
    - [https://www.facebook.com/NMTH100/photos/a.434763047064.207909.310255137064/10155402313897065/?type=3&theater](https://www.facebook.com/NMTH100/photos/a.434763047064.207909.310255137064/10155402313897065/?type=3&theater)
    - [http://www.nmth.gov.tw/exhibitionlist_48.html](http://www.nmth.gov.tw/exhibitionlist_48.html)

## 其他

- TEC很用心的把歷史上的大地震作整理與推廣講座，且都到該次地震的震央所在縣市去進行講座，其實也是告訴聽眾在地的地質特性 [http://tec.earth.sinica.edu.tw/.../his\_earthquake\_list.php](http://tec.earth.sinica.edu.tw/.../his_earthquake_list.php)
- 觀察地震的歷史資料，是因為，板塊地震的週期比較長，勢利一點講，921大地震之後中部地區已經能量釋放過了，反觀台北1694年7級的康熙大地震，造成盆地土壤液化，形成台北大湖，距今也 320 年了，好像準備要..... (抖)
- 古地名與災害：[https://g0v.hackpad.com/4rF7N2Ihf5r](https://g0v.hackpad.com/4rF7N2Ihf5r)
- 




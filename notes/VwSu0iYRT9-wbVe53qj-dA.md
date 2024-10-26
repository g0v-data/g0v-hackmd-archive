---
title: "台北市路樹倒塌與風場議題探討"
tags: GIS, hackpad
---

# 台北市路樹倒塌與風場議題探討

> [點此觀看原始內容](https://g0v.hackpad.tw/PwzLda7C3bV)

專案說明：探討台北市路樹倒塌與風場的關係。

Todos
1.  建立台北市的風場模擬方法，爬資料、開源模擬模式
2.  蒐集路樹倒塌資料，爬資料、路樹倒塌成因探討
3.  探討「風場」與「樹倒」兩者關係

Need
- [ ] 爬資料
    - [ ] 建構風場模擬所需要的政府資料
        - 臺北盆地地形模型(大致為北北基範圍)
            - 內政部100公尺網格數值地形模型資料-DEM  [DEM100M](http://tgos.nat.gov.tw/tgos/Web/Metadata/TGOS_MetaData_View.aspx?MID=35122&SHOW_BACK_BUTTON=false)
            - [http://gis.rchss.sinica.edu.tw/qgis/?p=1619](http://gis.rchss.sinica.edu.tw/qgis/?p=1619) 這邊有 NASA 30m 的資料
    - [ ] 台北市建築3D模型
        - [臺北市自動化3D近似建物模型](http://data.taipei/opendata/datalist/datasetMeta;jsessionid=14AB622F7FF845BFD67BEBABFEAEEE8B?oid=9b7d78d2-0d73-4b42-9b29-c1640efed0eb)（[方法說明](http://gis.taipei/ct.asp?xItem=996149&ctNode=52159&mp=100056)）這個資料已經爬下來放在 [https://github.com/sheethub/tpe3d](https://github.com/sheethub/tpe3d) ，demo: [http://sheethub.github.io/tpe3d/3dtaipei4347-2.html](http://sheethub.github.io/tpe3d/3dtaipei4347-2.html)
    - [ ] 樹倒通報資料
    - [ ] 描述樹種/樹穴/種植現場環境的資料
- [ ] CFD (Computational fluid dynamics) 環境模擬的開源方案
    - OpenFOAM is a free, open source CFD software package [http://www.openfoam.com/](http://www.openfoam.com/)
    - code [http://su2.stanford.edu/](http://su2.stanford.edu/)
- [ ] GIS
- [ ] 視覺化 / 互動呈現
    - 參考 [施工需求的地理分析框架](http://junipertcy.info/data_taipei/)

### 問題意識列舉

- 路樹倒塌與風場有關嗎？如何梳理兩者之間的關係？
    - 是受到風廊方向影響?
    - 還是受到高樓風壓影響?
- 請問樹種/樹穴/樹形/是否妥善修剪⋯⋯等變因要如何納入?  在都市全域尺度上,目前無法確知路樹倒伏,究竟是受這些因素影響大?  還是受風場影響大?
- 理論上應先以多變量分析,就不同空間型態(這是為了簡化後續加入不同特性的風場紊流因素所做的實驗設計),確認各因素影響之比例,再行建置風場模型進行模擬較為嚴謹

### 參考文獻

風環境模擬研究論文
- [2011-2020年夏季(6-9月)盛行風風向 (參考文獻：台北盆地的夏季風紋與溫度分佈初探，作者：石婉瑜、陳品瑜)](https://www.google.com/search?q=%E5%8F%B0%E5%8C%97%E7%9B%86%E5%9C%B0%E7%9A%84%E5%A4%8F%E5%AD%A3%E9%A2%A8%E7%B4%8B%E8%88%87%E6%BA%AB%E5%BA%A6%E5%88%86%E4%BD%88%E5%88%9D%E6%8E%A2&oq=%E5%8F%B0%E5%8C%97%E7%9B%86%E5%9C%B0%E7%9A%84%E5%A4%8F%E5%AD%A3%E9%A2%A8%E7%B4%8B%E8%88%87%E6%BA%AB%E5%BA%A6%E5%88%86%E4%BD%88%E5%88%9D%E6%8E%A2&gs_lcrp=EgZjaHJvbWUqBggAEEUYOzIGCAAQRRg7MgYIARBFGDwyBggCEEUYPdIBBzQ3MWowajeoAgCwAgA&sourceid=chrome&ie=UTF-8)
- [大樓建築群開放空間風場環境之評估與檢討 以成長中地區為例](http://ir.lib.stu.edu.tw/ir/retrieve/11075/stu-101-s99735101-1.pdf)
- [行人環境風場舒適度標準性評估與數值模擬可行性研究](http://ndltd.ncl.edu.tw/cgi-bin/gs32/gsweb.cgi/login?o=dnclcdr&s=id=%22097TKU05015019%22.&searchmode=basic)
- [以數值方法模擬流經孔隙樹體風場之研究](http://ndltd.ncl.edu.tw/cgi-bin/gs32/gsweb.cgi/login?o=dnclcdr&s=id=%22102NCHU5015064%22.&searchmode=basic)
- [行道樹綠化對都市風廊道之影響─以台南市東豐路、林森路為例](http://ndltd.ncl.edu.tw/cgi-bin/gs32/gsweb.cgi/login?o=dnclcdr&s=id=%22098NCKU5347032%22.&searchmode=basic)
- [都市熱島退燒策略效益分析─以台北市民族西路周邊為例](http://www.airitilibrary.com/Publication/alDetailPrint?DocID=U0002-0102201210002800)

模擬
- 日照 [http://suncalc.net/](http://suncalc.net/)
- [Guide for the TIMCOM Ocean Model](http://efdl.as.ntu.edu.tw/research/timcom/index.html)
- Community Earth System Model (CESM)
- Climate - Weather Research and Forecasting Model [http://cwrf.umd.edu/](http://cwrf.umd.edu/)

城市氣候政策
- 香港都市氣候規劃建議圖與設計策略 [http://goo.gl/g2Giuw](http://goo.gl/g2Giuw)
- [新北市針對「風環境」進行都市設計](http://www.ettoday.net/news/20130829/263327.htm)

都市樹木倒塌研究
- 日本街路樹協會，近期在大安森林公園基金會，有技術交流
專案
- [過去一年台灣登革熱的病例統計與當地風向變化觀察, 高雄 vs. 台南 2014/9/1~2015/10/15 by 彭世平](https://www.facebook.com/max.peng.94/posts/1119629521381985)





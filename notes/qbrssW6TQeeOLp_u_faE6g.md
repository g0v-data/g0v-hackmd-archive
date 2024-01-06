---
title: "地理數據視覺化"
tags: GIS
---

# 地理數據視覺化

> [點此觀看原始內容](https://g0v.hackpad.tw/SdiXqVJICsv)


討論資訊呈現在地圖上的樣版需求及設計

### 需求

- 疾病管制 / 災害控管
- 環境汙染 ( similar to [http://env.g0v.tw](http://env.g0v.tw) pm 2.5 ? )
- 基本地理相關資訊呈現 (人口,犯罪率,得票率)

### 發想

- 視覺化手法
    - 地理區塊呈現，熱圖或泡泡圖的概念
        - 多層次顯示, 從村里 / 鄉鎮到縣市
        - 視 zoom level 或資料集顯示適當的解析度？
    - 顯示時序資料的方式？
- 資料手法
    - 利用有提供結構化資料 API 的線上協作工具做資料來源
        - 比方說 google spreadsheet
> [使用 Google Spreadsheet 建立協作資料集](https://g0v.hackpad.tw/5Ofw64qSz7P)
> [name=che l]

    - 自動比對地名，並修正歷史變化或編碼問題
- 利用手法
    - javascript library
    - embedded widget

### 參考

- 犯罪 / 統計資訊視覺化 / [https://gist.github.com/zbryikt/4696905](https://gist.github.com/zbryikt/4696905)
- 2014年九合一選舉六都視覺化 / [http://jizz5566.github.io/2014_6cities/2014ver5.html](http://jizz5566.github.io/2014_6cities/2014ver5.html)

### 工具

- [Geojson.io](http://geojson.io/) : 線上即時Geojson or 其他主要GIS格式產生器
- 線上KML產生器：[http://www.mapmash.in/kmlpoint.html](http://www.mapmash.in/kmlpoint.html)
- [http://www.r-bloggers.com/making-maps-in-r-with-ryan-peek-and-michele-tobias/](http://www.r-bloggers.com/making-maps-in-r-with-ryan-peek-and-michele-tobias/)
> 先筆記xD
> [name=Summit S]


### 其它

> 請問關於視覺化，是否必須利用OOP程式？
> [name=Xavier S]

> 又，可否建議用哪種OOP較容易上手？ 目前搜尋資訊似乎是Ruby?
> [name=Xavier S]

> 其他還有Java、python、C++等程式，懇請大家提供意見，謝！
> [name=Xavier S]

> 這感覺可以再開一個專 pad 來討論「我要怎麼入門視覺化」之類的
> [name=Kirby W]

> 視覺化從紙筆開始就可以, 很多線上工具可以用 (plot.ly etc)
> [name=Kirby W]

> 適合做視覺化的程式也有不少 (processing, R, javascript)
> [name=Kirby W]

> 比較會是想要做到什麼效果的問題
> [name=Kirby W]

> 不過要從頭學是比較困難一點, 比較建議還是先找人 cover
> [name=Kirby W]

> 關於「我要怎麼入門視覺化」，雖然我這完全不懂程式設計的人不能馬上學會，但久了後也可以自己創作，贊成！
> [name=Xavier S]

> 我之前有寫過相關的文章可以參考：[http://muyueh.com/essay/DataVisualization_LearningMap.html](http://muyueh.com/essay/DataVisualization_LearningMap.html)
> [name=Muyueh L]

> 分享一下之前在島國前進簡報的教學檔案，不用寫程式做出資訊地圖：[https://drive.google.com/file/d/0B6u4xYZl0L87UkV6Y25mYm1WSnM/view](https://drive.google.com/file/d/0B6u4xYZl0L87UkV6Y25mYm1WSnM/view)
> [name=積木陳]




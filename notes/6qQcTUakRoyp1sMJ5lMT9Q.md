---
title: "立法院風雲榜 - 需求分析"
tags: 立法院, hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/E6qO3jBwAPL)

# 立法院風雲榜 - 需求分析

## 目標客群

公民

## 專案目的

- 即時民意的實現，提供公民上網針對各法案作評鑑。
- 量化各立委實質貢獻。
- 量化各立委對各議題的態度。
- 成為制衡立委的力量之一。


## 專案目標


第一階段：
1.  客觀數據評鑑立委 ex. 出席率、投票率。或者使用公督盟的[評鑑資料](http://www.ccw.org.tw/assess/%E7%AC%AC%E5%85%AB%E5%B1%86)
2.  對法條做分析，法條對應議題的正反面 ex. [http://www.publicwhip.org.uk/index.php](http://www.publicwhip.org.uk/index.php)
3.  法條評鑑系統。 (ex. 支持、不支持、不了解)
第二階段：
1.  在各議題 邀請有公信力團體位立委做評鑑。
2.  針對立委的法條支持與否，得知立委對議題的立場。


## 功能

- 立委分類
    - 依委員會: 內政、司法及法制、外交及國防、交通、社會福利及衛生環境、財政、教育及文化、經濟。
    - 依選區: 連江縣、金門縣、桃園縣、新竹縣、苗栗縣、彰化縣、南投縣、雲林縣、嘉義縣、屏東縣、宜蘭縣、花蓮縣、臺東縣、澎湖縣、臺北市、新北市、臺中市、臺南市、高雄市、基隆市、新竹市、嘉義市、山地原住民、平地原住民、全國不分區、僑居國外國民。(22縣市)
> maybe 以後可以像 [http://www.nytimes.com/interactive/2012/12/19/us/politics/nra.html?_r=2&](http://www.nytimes.com/interactive/2012/12/19/us/politics/nra.html?_r=2&) 制作個台灣地圖，用滑鼠移動便知道各選區的立委有誰。
> [name=Lee]

> 詳細選區 [http://zh.wikipedia.org/wiki/File:2012ROCLY.svg](http://zh.wikipedia.org/wiki/File:2012ROCLY.svg)
> [name=Lee]

- 議題分類
- 即時為各立委打 星星
- 排名各立委，並列出較不適任立委

## 現有資料

- g0v立法院
    - [http://api.ly.g0v.tw/v0/collections/](http://api.ly.g0v.tw/v0/collections/)
    - ex. [http://api.ly.g0v.tw/v0/collections/bills?q=](http://api.ly.g0v.tw/v0/collections/bills?q=){%22proposal.0%22:%22%E8%94%A3%E4%B9%83%E8%BE%9B%22}
    - [http://hack.g0v.tw/g0v-ly/BfddbG2JBOi](http://hack.g0v.tw/g0v-ly/BfddbG2JBOi)
    - [https://groups.google.com/forum/?fromgroups#!topic/g0v-ly/YggUSyFio0o](https://groups.google.com/forum/?fromgroups#!topic/g0v-ly/YggUSyFio0o)
- 立委投票指南 [http://twly.herokuapp.com/legislator/about/](http://twly.herokuapp.com/legislator/about/)
    - api [https://twly.herokuapp.com/api/](https://twly.herokuapp.com/api/)


## 專案問題

評鑑相關
1.  如何計算rank分數 (統計分析的問題)
2.  評分Timline (議案而分?)
3.  預設分數有可能造成預設立場？
4.  即時評分，關係個人立場（可能不具太大意義，大眾官感的支持度？）
5.  對法案作支持度，可以得知各選區對議題的關心，或者整個台灣對議題的關心

議題相關
1.  如何清楚切割各議題？ （面向的討論）
2.  如何以非文字元素（顏色、圖形、數字）來表達各立委的立場和貢獻
3.  詢問其他從事政治與社會議題相關人士的意見
4.  法案啄木鳥 （法案對議題的正反）

網站相關
1.  使用者單一賬號，是否會造成使用者評分疑慮?
2.  個人化設置
    1.  戶籍地 \- 辨識選區


## 參考資料

- 美國議員 ranking [http://www.ranker.com/list/rank-the-current-u-s-senators/sesel88?format=GRID](http://www.ranker.com/list/rank-the-current-u-s-senators/sesel88?format=GRID)
- 公督盟評鑑 [http://www.ccw.org.tw/assess/%E7%AC%AC%E5%85%AB%E5%B1%86](http://www.ccw.org.tw/assess/%E7%AC%AC%E5%85%AB%E5%B1%86)
- 關於議題
    - 美國議員評鑑 [http://thehill.com/resources/lawmaker-ratings#senate](http://thehill.com/resources/lawmaker-ratings#senate)
    - food議題評鑑 [http://www.foodpolicyaction.org/](http://www.foodpolicyaction.org/)
    - 槍械議題評鑑 [http://www.nytimes.com/interactive/2012/12/19/us/politics/nra.html?_r=1&](http://www.nytimes.com/interactive/2012/12/19/us/politics/nra.html?_r=1&)
- 法條與立場分析
    - 議題與法條相關分析 [http://www.publicwhip.org.uk/index.php](http://www.publicwhip.org.uk/index.php)
    - 立場分析 [http://ivoter.ecrc.nsysu.edu.tw/](http://ivoter.ecrc.nsysu.edu.tw/)
- 韓國議員網站 [http://en.pokr.kr/](http://en.pokr.kr/)
    - 原始碼: [https://github.com/teampopong/pokr](https://github.com/teampopong/pokr)




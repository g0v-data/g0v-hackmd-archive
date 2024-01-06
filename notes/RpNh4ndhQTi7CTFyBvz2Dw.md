---
title: "衛福部癌症資料庫開放專案"
tags: hackpad
---

# 衛福部癌症資料庫開放專案

> [點此觀看原始內容](https://g0v.hackpad.tw/fj3KFYXmoY2)


## 緣起


想要了解全台各鄉鎮罹癌的狀況與分佈, 不過政府資料並不容易使用 (cris.hpa.gov.tw 以5~7個步驟才能索取單個鄉鎮的歷年資料), 萌生了爬取所有資料的念頭. 日前已有其他的嘗試, 例如 [http://github.com/hcchien/doh-cancer](http://github.com/hcchien/doh-cancer) 使用 phantomjs 爬取, [http://github.com/g0v/cancer/](http://github.com/g0v/cancer/) 存有全民健保癌症相關統計資料, (其中就診人數值得深入探討)

5/10 CCSP Hackathon team goog1er (from g0v) 決定來把資料爬到 github 上順便視覺化, 因此此專案便加速進行了.
Crawler repo: [https://github.com/yhsiang/cris-cancer](https://github.com/yhsiang/cris-cancer)

### 資料欄位說明

分率=某特定癌症數÷總癌症數×100
粗率=（某特定癌症新診斷或死亡人數÷總人口數）×100000
年齡別率=（某年齡層癌症新診斷或死亡人數÷某年齡層人口數）×100000
標準化率=Σ（某特定年齡別率×該年齡層標準人口數）÷Σ（某特定年齡層標準人口數）×100000

### 資料抓取參數

\[資料類型\]   指標-發生率
\[統計值\]       年齡別率
\[性別\]           男性及女性
\[年齡\]           全部
\[鄉鎮\]           各鄉鎮區
\[癌症部位\]  全部

### 視覺化網址


[http://g0v.github.io/cancer/viz/](http://g0v.github.io/cancer/viz/)

## 問題回報

資料及視覺化等若有問題或建議請留在這邊

- 「癌症地圖」的癌症定義為何？是就診？死亡？
> 是罹患人數, 資料來源為 [http://cris.hpa.gov.tw](http://cris.hpa.gov.tw) 他同時有提供粗率跟年齡化標準率, 不過我們還沒有使用, 只有單純自行計算粗率 (個案數除以鄉鎮總人數, 粗率那個 checkbox)
> [name=Kirby W]

> 我們抓的是發生率，也就是新診斷出罹患癌症的，另外有一個死亡率才是統計因癌症死亡的資料
> [name=Yuan C]

- ~(bug) 高雄市三民區應分為那瑪夏區及三民區  ~
> 已修正
> [name=Kirby W]

- ~(bug) 資料錯誤, 有些鄉鎮變成很多鄉鎮的總和~
> crawler程式有問題，已修正
> [name=Yuan C]

- (bug) 臺南市關廟區沒有資料
> 已向國民健康署反應
> [name=Yuan C]

- ~(suggest) 鄉鎮區塊可以改為點擊時顯示資料~
> 已改進
> [name=Kirby W]

- (question) 資料可以拿去用嗎?
- (suggest) 好像應該先把全部資料的大小值都拿到後再來決定 scale，這樣比較看得出來上升情形（我做看看
> 看起來效果好像沒比較好，應該要分病別，但是設定 scale 爲歷年最低到最高
> [name=Colin S]

> [g0v/cancer#3](https://github.com/g0v/cancer/pull/3)
> [name=Colin S]

> 改在這，@kirby 可以看一下\
> [name=Colin S]

> 順便做成一個可開關的選項了
> [name=Kirby W]

- (suggest) 單從人數看幾乎都集中在北高了，建議再加入城市人口數，可形成人數比例值（癌數/城鎮人口），從比例值著色的話色塊應該會有所改變。另一參考值為醫院數，可看出醫療分布均度（癌數/中小型醫院以上數量）。希望這兩個分母作為可選。


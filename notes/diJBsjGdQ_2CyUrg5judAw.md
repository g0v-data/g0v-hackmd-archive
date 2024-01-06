---
title: "台南百年文史古地圖"
tags: hackpad
---

# 台南百年文史古地圖

> [點此觀看原始內容](https://g0v.hackpad.tw/f4DSkbYYXsi)

以時間軸及歷史疊圖的方式呈現台南古蹟，古地圖與重要歷史事件之連結，甚至是建議踏查路線，讓民眾能藉著 iPad 即行動網路得知在台南做文史旅遊的導覽建議。

利益揭露
- 這要拿去參加opendata tainan hackthon. (done: 獲得首獎)

## 編輯說明

1.  來自電腦玩家的詳細[教學文章](http://www.playpcesor.com/2014/08/time-map.html)，Step by Step瞬懂
2.  ~閱讀參考案例「~[~拿破崙戰爭時間地圖~](http://timemapper.okfnlabs.org/rufuspollock/major-battles-napoleonic-wars)~」~
> ~之前看到類似的，也是時間x空間x事件：~ [~Visualizing Time For World War 1~](http://kenjispecial.github.io/visualizing-time/)
> [name=Lee]

> ~這範例也太強 ... ~
> [name=Jimmy H]

> ~看起來好像也可以幫她加個backend? XD~
> [name=HisnYi C]

3.  ~了解每一則事件的~[~格式~](https://docs.google.com/a/netivism.com.tw/spreadsheet/ccc?key=0AqR8dXc6Ji4JdFRNOTVYYTRqTmh6TUNNd3U2X2pKMGc#gid=0)
4.  ~真正開始編輯~[~台南的事件~](https://docs.google.com/spreadsheets/d/1k6OnUzASOmYhcCjGRygLjETT-H57ztkRFcbUpOlD_Bw/edit?usp=sharing)
    1.  ~另一份~[~Template~](https://docs.google.com/spreadsheet/ccc?key=0AlXBk_cWj_gIdDEtWU1pR3h4ZWpEQXA1TFcyazNydUE&usp=sharing)
    2.  ~hackthon demo 的~[~台南歷史地圖~](http://timemap.kuansim.com/anon/hc9f40-)
5.  ~可以直接在~[~測式的網址~](http://timemapper.okfnlabs.org/anon/ox8p5w-)~觀看編輯結果（但無法預覽台灣古地圖）~

test demo: [http://enigmatic-spire-2011.herokuapp.com/anon/](http://enigmatic-spire-2011.herokuapp.com/anon/vy8pbk-)[vy8pbk-](http://enigmatic-spire-2011.herokuapp.com/anon/vy8pbk-)

## Ideas pool

- users should be able to upload gps trackers to the map as tourism route.
- integrated geo reporter data to inform government that citizens wants the gov to  fix the historic.

### Todo List


- [x] integrate rchss-tainan (demo site: [http://hychen.wuweig.org/leaflet-tw/sample/rchss-tainan.html](http://hychen.wuweig.org/leaflet-tw/sample/rchss-tainan.html))
- [x] overlap layers configuration.
> 讓使用者可以選擇想要使用的古地圖, 方式為提供一個checkbox 讓使用者勾選
> [name=HisnYi C]

> need details
> [name=Jimmy H]

- [x] translate user interface messages.
- [x] CSS problem after translated
- [ ] 支援更多古地圖
    - [ ] 臺北
    - [ ] 新北
    - [ ] 台中
    - [ ] 高雄
- [ ] Better Backend

### developing repo

- [https://github.com/kuansim/timemap](https://github.com/kuansim/timemap)

## Reference

- [https://github.com/okfn/recline](https://github.com/okfn/recline)
    - A simple but powerful library for building data applications in pure Javascript and HTML.
- time mapper
    - [https://github.com/okfn/timemapper](https://github.com/okfn/timemapper)
- timeline sample
    - [http://www.philharmoniedeparis.com/en/chronologie/](http://www.philharmoniedeparis.com/en/chronologie/#vars!date=2012-09-25_17:11:22!)[#vars](https://g0v.hackpad.tw/ep/search/?q=%23vars&via=f4DSkbYYXsi)[!date=2012-09-25_17:11:22](http://www.philharmoniedeparis.com/en/chronologie/#vars!date=2012-09-25_17:11:22!)[!](http://www.philharmoniedeparis.com/en/chronologie/#vars!date=2012-09-25_17:11:22!)
- Leaflet slider
    - [http://dwilhelm89.github.io/LeafletSlider/](http://dwilhelm89.github.io/LeafletSlider/)
- 聽旅行
    - [http://www.hearhere.com.tw/](http://www.hearhere.com.tw/)
- 地誌的殘念
    - [g0v/twangry#94](https://github.com/g0v/twangry/issues/94)

## QA

- 算是鄉民關心你的一部分？
    - yap.
- 目前source data可以鎖嗎？（用 gdoc 管權限吧...？）
    - 是
- 是okfnlab fork的嗎？有何不同？（目前看到是增加台南古地圖疊圖功能、對行動裝置體驗的小調整，如果不用古地圖功能，差別在哪？）
    - 是 okflab fork，之前增加的多國語系，bug fixing, configure enhancement 都merge回去了
    - 如果不用古地圖功能，還多了timeline tagging的功能
- 每個人都可以建立自己的 timemap?
    - yes
- 頁面會中文化嗎？
    - yes，不過預設是中文的，是否你的browser設定為英文？
> oops, 真的是我 browser 設為英文的關係 XD
> [name=ipa c]




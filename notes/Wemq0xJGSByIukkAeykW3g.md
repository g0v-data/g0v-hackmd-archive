---
title: "［工具］台北租房專題／新聞作業需要的資料與工具／"
tags: 新聞作業,新聞,hackpad
---

# ［工具］台北租房專題／新聞作業需要的資料與工具／

> [點此觀看原始內容](https://g0v.hackpad.tw/gbw3lkzwd7y)

副標題：爬租屋資訊


from : [https://www.facebook.com/groups/g0v.general/permalink/673922016017541/](https://www.facebook.com/groups/g0v.general/permalink/673922016017541/)
(以下來自 ↑ 的內容...報酬之類的不要找我囧........)

## 具體方案

### 資料來源

- [ ] [台灣租屋網](http://www.twhouses.com.tw/netc/chhistory/quote.html) 2003~2014至今的租屋價格，有具體的路段
    - repo: [https://github.com/yhsiang/twrentdata](https://github.com/yhsiang/twrentdata)
- [ ] [崔媽媽基金會](http://www.tmm.org.tw/statist/) 行政、捷運、學區2001~2014年至今租金統計
- [ ] [樂屋網](http://www.rakuya.com.tw/price/deallist) 2013.7~2014.8公寓電梯大廈透天厝成交行情
- [ ] [好房網](http://rent.housefun.com.tw/) 雅房、套房、住家租屋價格
- [ ] [591租屋](http://rent.591.com.tw/) 雅房、套房、住家租屋價格
- [ ] [內政部不動產資訊平台](http://pip.moi.gov.tw/Net/A-Price/A9.aspx) 內政部的租屋成交價格

### 執行細節

1.  以上資料以台北市為例，抓出台北市租屋資料，製作成一張依照租金價格高低即顏色變化的地圖，因為有之前的資料，所以就想做從2003年至今的的價格變化，也是在同一張圖中，圖片下方為可拉動時間軸，圖片顏色會隨著時間軸的拉動而改變。
> *若網站無法呈現出動態圖，可選取幾個時間點（年），做靜態圖。
> [name=lanfon]

2.  地圖上會標示出捷運站的位置，具體的地標等。
3.  各租房資料有具體的路段，有些會有重複的部分，需把重複的部分刪除。


這是目前方案，想請問各位可行性如何？歡迎大大們跳坑！！會有報酬但我們預算也有限......操作過程中遇到任何問題或者有更好的呈現方式我們都可以一起討論修改～～！




## ＝＝　工具　＝＝

--01--
yhsiang
有試著寫一隻程式去爬台灣租屋網的資料, 晚點把data跟repo連結放上
[https://github.com/yhsiang/twrentdata](https://github.com/yhsiang/twrentdata)

\# repo , 資料也commit進去了 目前只有住宅？ XDD


--02--






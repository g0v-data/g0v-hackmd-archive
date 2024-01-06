---
title: "d|Bootcamp Taipei 共筆 - 資料視覺化：簡介與討論"
tags: hackpad
---

# d|Bootcamp Taipei 共筆 - 資料視覺化：簡介與討論

> [點此觀看原始內容](https://g0v.hackpad.tw/0oex8jxn78Z)


時間：2015/08/21 15:30 ~ 16:30
講師：李慕約
**解答版：**[https://docs.google.com/spreadsheets/d/1SVfx5jRxSQkKVpB2Nn1TUnVYzQVFtZQXaLFfmpza4Ho/edit#gid=0](https://docs.google.com/spreadsheets/d/1SVfx5jRxSQkKVpB2Nn1TUnVYzQVFtZQXaLFfmpza4Ho/edit#gid=0)



> table 是 HTML table 的意思，所以只要是抓表格就是用 table
> [name=Pomin W]

> 1 是指網頁從上面數下來第一個表格，同理要抓第二個表格可以用 2
> [name=Pomin W]

> thank you!!
> [name=Ann C]



d|Bootcamp Taipei 共筆 - 資料視覺化：簡介與討論
時間：2015/08/21 15:30 ~ 16:30
講師：李慕約 / SheetHub.com 共同創辦人
##



### 準備


[https://drive.google.com/folderview?id=0BwcMEBpS0DppflpFZ2k1WXQtOTZEa1M0Z0VMY20xZnNxdkpobW02RkVnZmtpbExxRlJqd3M&usp=sharing](https://drive.google.com/folderview?id=0BwcMEBpS0DppflpFZ2k1WXQtOTZEa1M0Z0VMY20xZnNxdkpobW02RkVnZmtpbExxRlJqd3M&usp=sharing)

### 總表

[https://docs.google.com/spreadsheets/d/1AvtnyA6KuSaJm9CMFswYCrCHtkW-Lf3U8SR1IUJJFh0/edit#gid=0](https://docs.google.com/spreadsheets/d/1AvtnyA6KuSaJm9CMFswYCrCHtkW-Lf3U8SR1IUJJFh0/edit#gid=0)


**中選會網址**：[http://db.cec.gov.tw/histQuery.jsp?voteCode=20120101T1A2&qryType=ctks](http://db.cec.gov.tw/histQuery.jsp?voteCode=20120101T1A2&qryType=ctks)


### 預處理


- 抓取選舉資料： v[http://db.cec.gov.tw/histQuery.jsp?voteCode=20120101T1A2&qryType=ctks](http://db.cec.gov.tw/histQuery.jsp?voteCode=20120101T1A2&qryType=ctks)
    - Ctrl + v
    - =importHTML

=IMPORTHTML("[http://db.cec.gov.tw/histQuery.jsp?voteCode=20120101T1A2&qryType=ctks](http://db.cec.gov.tw/histQuery.jsp?voteCode=20120101T1A2&qryType=ctks)", "table", 1)

> 請問要如何知道是"table", 1 ?
> [name=Ann C]

> 理論上是因為這是這一個頁面的第幾個表格，但實際操作，我自已都是 try-and-error
> [name=Muyueh L]


=if(ISBLANK(B2),A1,B2)
> 請問這一行是什麼意思呢？功能是什麼
> [name=Mengyan S]

=Sheet1!A1
> 複製一個待加工的資料表用的參照
> [name=Pomin W]

> 填在 A1 格，然後拉到整張資料表
> [name=Pomin W]


- 清理空白欄位
    - 手工
    - 函式
- 顯示原始來源、整理原始來源


### 邏輯


- 機智問答時間
    - 哪一個政黨的得票數比較多？
    - 哪一個政黨的女性候選人比較多？
    - 哪一個政黨最有效率？
    - 每一個政黨的候選人平均年齡？
    - 連任是不是比較有機會？
    - 女性是不是比較有機會？
    - 每一個縣市的獲勝政黨？
    - 每一個縣市的獲勝性別？
- 解答：[https://docs.google.com/spreadsheets/d/1SVfx5jRxSQkKVpB2Nn1TUnVYzQVFtZQXaLFfmpza4Ho/edit#gid=0](https://docs.google.com/spreadsheets/d/1SVfx5jRxSQkKVpB2Nn1TUnVYzQVFtZQXaLFfmpza4Ho/edit#gid=0)

- 因果不等於相關

### 圖表

- 直條或圓餅
    - 圖例
    - 顏色
    - 逗點（易讀性）

- 重複利用

### 概念

- 掌握自己的工具：學學寫程式吧 :)
- 50%-80% 的時間再做資料的準備
- 資料越來越多：自動化 /  重複利用 / 即時


[http://www.flightradar24.com/data/airplanes/b-16333/](http://www.flightradar24.com/data/airplanes/b-16333/#70da51d)[#70da51d](https://g0v.hackpad.tw/ep/search/?q=%2370da51d&via=0oex8jxn78Z)
[http://env.g0v.tw/air/](http://env.g0v.tw/air/)
[http://earth.nullschool.net/](http://earth.nullschool.net/)
[https://www.windyty.com/?25.039,121.525,4](https://www.windyty.com/?25.039,121.525,4)



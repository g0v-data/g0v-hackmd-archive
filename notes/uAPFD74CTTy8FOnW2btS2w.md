---
title: "開放都市-委員會會議記錄資料庫"
tags: 開放都市計畫,planning,hackpad
---

# 開放都市-委員會會議記錄資料庫

> [點此觀看原始內容](https://g0v.hackpad.tw/BpW2Xt7s8AH)

上層 [開放都市計畫](http://hackfoldr.urbancode.tw/)

## 緣由

每個法定都市/區域計畫都需要經過多次的委會員審議，審議就會有審議紀錄，例如[內政部區域計畫委員會紀錄](http://www.cpami.gov.tw/chinese/index.php?option=com_filedownload&view=filedownload&Itemid=68&filter_cat=6&filter_gp=8)，包含大大小小案件的審議過程、爭議點、人民陳情意見。但現在的會議紀錄公開方式只是放上pdf或doc文件，以會議編號歸檔，無法直接知道每次會議的案件有哪些，也無法檢索，如果能建立開放資料庫，就可以利用關鍵字搜尋，找出爭議案件在委員會被處裡的方式為何

e.g.下圖[竹南頭份計畫](https://github.com/g0v/urbancodeg0vtw/blob/master/planbook/%E7%AB%B9%E5%8D%97%E9%A0%AD%E4%BB%BD%E4%B8%89%E9%80%9A(%E7%AC%AC%E4%B8%80%E9%9A%8E%E6%AE%B5).pdf)就經過鎮級2次、縣級1次、部級2次，共5次都委會審議，由會議記錄與發布文件比對，就可以知道案件的爭議點是什麼，怎麼被處理
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2f5d9d71c4f1043961f66bb7f0c7dd0b)

## 專案目的

把各大委員會的會議紀錄材砍回家，作為開放資料，容易查閱檢索，串聯每一次會議過程與最終實施計畫間的關係

## 授權

- 文字：CC BY g0v.tw contributors
- 程式：MIT [http://g0v.mit-license.org](http://g0v.mit-license.org)
- 註：會議紀錄原始文件由各級委員會網站下載，版權依相關法令規範

## 協作工具

github repo: [https://github.com/g0v/urbancode-commission](https://github.com/g0v/urbancode-commission)
slack channel: urbancode

## 目前成果

- [http](https://commission.urbancode.tw)[s](https://commission.urbancode.tw)[://commission.urbancode.tw](https://commission.urbancode.tw)
- 目前只有內政部跟台北市的資料
- 表格跟圖片還沒有處理
## 協作步驟

請加入以下討論：
- [資料結構討論](https://g0v.hackmd.io/gZZ2ZzUpR7i-2evJ_ypvIQ?both)
- [API策劃](https://g0v.hackmd.io/fLtZ9bE6QZ6tWnmGsqCddQ)
- [前端策劃](https://g0v.hackmd.io/CJruYEwbRVW3tb5Ehujhew?both)

## 各縣市都委會紀錄清查

- [開放都市-都市計畫委員會盤點](https://g0v.hackmd.io/Z4oRg64JTNGH2cOWhvZ3_A)

### 其他各委員會會議紀錄網頁連結

- [內政部區域計畫委員會會議記錄](http://www.cpami.gov.tw/chinese/index.php?option=com_filedownload&view=filedownload&Itemid=68&filter_cat=6&filter_gp=8)
- [內政部審議案件書件查詢系統](http://cpabm.cpami.gov.tw/docsrc/index.do)
- [臺北市都市計畫委員會專案小組會議記錄](http://www.tupc.gov.taipei/lp.asp?CtNode=69657&CtUnit=37693&BaseDSD=7&mp=120021)
- [臺北市都市開發審議服務平台](https://www.gis.udd.taipei.gov.tw/Meet2.aspx)

## 相關專案

- OCR 的可能性

## 其他工具

- 使用的word轉txt工具:
```
http://www.pdfzilla.com/zilla\_word\_to\_text\_converter.html
```
- 批次轉存pdf工具:
```
http://www.docufreezer.com/
```
> 感覺會議記錄應該可以用 sayit -- 如立法院公報：[http://sayit.musou.tw/](http://sayit.musou.tw/)
> [name=Johnson L]

> 請洽 LY ~~
> [name=Johnson L]


## 老東西

```
1.下載委員會紀錄
1-1 找到每個縣市各自的XX委員會網站，例如臺北市都市計畫委員會
1-2 找到下載委員會紀錄的介面
1-3 把委員會紀錄通通帶回家 (用人工智慧跟工人智慧都可以)
2.上傳紀錄
傳送到 google drive
XXX = 地區碼 沿用 ISO3166-2:TW https://zh.wikipedia.org/wiki/ISO_3166-2:TW
範例：臺北市存在 /TPE/
3.轉資料 (doc / pdf -> json)
自由射擊，將原始格式轉成 json
資料結構規劃如後
4.上傳 json
傳送到 google drive
試作範例 (台北市都委會673次紀錄)：http://urbancode.tw/json_example.json
需要二次加工：
~1.與標題同行內文會被切掉~
2.表格部分要手工整理
~3.UTF-16字碼要轉成文字~
~4.特殊符號 \" quote mark 現在以 (quote) 代替~
5.原始文件換行以 \\r\\n 代替
TODO LIST
確認後端資料結構，討論頁面
前端介面 mockup
improve txt to json parser

~已經抓下大量都市計畫委員會會議記錄轉換成txt，存在~ ~google drive~
~完成第一版的 txt to json parser，json 存在~ ~google drive~
~資料庫網站mockup version1：~~https://moqups.com/monaludao/6ARZvYh3/p:a16b2c2a4~
~紀錄頁的mockup網頁版~ ~http://urbancode.tw/commission.html~



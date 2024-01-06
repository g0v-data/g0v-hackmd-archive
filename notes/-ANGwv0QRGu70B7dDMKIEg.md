---
title: "開放都市計畫- 都市計畫書資料庫化"
tags: planning,hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/pJUQ0AGRCO1)

# 開放都市計畫- 都市計畫書資料庫化

## 源起

1.  屬於 開放都市計畫專案的一部分 [http://hackfoldr.urbancode.tw/](http://hackfoldr.urbancode.tw/)
2.  目前台灣有大約  450  個都市計畫區，每個計畫區都有「都市計畫書」記載區域內每一塊土地的土地使用分區及管制內容，控制都市土地的發展，但這些都市計畫書都藏在各縣市政府的網站深處，不容易找到，且檔案格式多半為 pdf

## 專案目標

1.  專案目的在於讓這些都市計畫書專換成的資料庫形式(如markdown)
2.  資料庫形式，可以快速地取得跟閱讀，或是不同計畫書之間比較，或進行文字的轉譯(如轉譯為白話文或是更好閱讀的圖表)，等等應用

## 資料來源

[營建署網站：都市計畫查詢](http://www.cpami.gov.tw/chinese/index.php?option=com_content&view=article&id=10129&Itemid=53)
> 好像掛掉了
> [name=Richard H]


## 流程

### 1.搜集都市計畫書

- 先以通盤檢討為主?

### 2.將每一本都市計畫書內容進一步轉成資料庫格式

- csv格式?
- json格式?
> 初步想法欄位安排是這樣：
> [name=Richard H]

```

```
| 章 | 節 | 小節 | 段 | tag1 | tag2 | tag3 | 內文 |
| --- | --- | --- | --- | --- | --- | --- | --- |
```
章、節、段：原文的段落編號，如第4-2-1節的第三段內文-> 4,2,1,3
tag1、tag2、tag3：該段內文描述內容的關鍵字，如：人口、土地使用...etc
    可以做成通用版的目錄，套用在不同的計畫書上
內文：實際內文/表格/圖url

```
> 表格在hackfolder顯示不正常?!
> [name=Richard H]

> +1
> [name=che l]


### 3.轉換成好閱讀格式

- 例如gitbook?
- 範例：[http://johnlinp.gitbooks.io/neihu/content/](http://johnlinp.gitbooks.io/neihu/content/)

## 需要人力

- 爬資料
- 資料結構
- 資料轉換

## 困難點

- 關於報告書內的段落階層
    - ch \[6:39 PM\] 因為寫劃規報告書的話，markdown的階層分類太少了。公家習慣看「壹、一、(一)、1、(1)、a、i⋯」或「1.1.1.1.1」這種階層表示法」
    - clkao \[7:11 PM\] 這個可以用 gitbook, 我寫過一個 gitbook-toc-styles 的 plugin
    - mrorz \[11:15 PM\] 如果需要把「壹、一、(一)、1、(1)、a、i⋯」轉換成格式化資料的話，可以參考這個 [https://github.com/g0v/ppt-commitment-parser](https://github.com/g0v/ppt-commitment-parser)
- 圖跟表要如何整合進這些欄位中?
- [都市計畫書資料三星化｜方法討論](https://g0v.hackpad.tw/2qR2Pzdu95W)
- 每一本都市計畫書的書寫方式都不同，要怎麼有效率的建立database?
> 雖然沒有直接解法，但這篇也有開始討論政府文件資料如何符合開放資料五顆星定義：[政府開放資料品質檢驗機制](https://g0v.hackpad.tw/529BJcUTTmS)
> [name=che l]

> 針對 [環境影響評估報告書](https://g0v.hackpad.tw/--P8EaNXkcT11)
> [name=che l]


## 現有成果

- 內湖都市計畫(主要計畫)通盤檢討(公開展覽版本)已轉換成markdown格式，做成簡易的gitbook
    原始pdf計畫書：[http://goo.gl/wVs0lD](http://goo.gl/wVs0lD)
    轉出的markdown：[https://github.com/johnlinp/pdf-to-markdown/blob/master/examples/neihu.md](https://github.com/johnlinp/pdf-to-markdown/blob/master/examples/neihu.md)
    gitbook：[http://johnlinp.gitbooks.io/neihu/content/](http://johnlinp.gitbooks.io/neihu/content/)
    github原始碼：[https://github.com/johnlinp/pdf-to-markdown](https://github.com/johnlinp/pdf-to-markdown)

- 南港區都市計畫通盤檢討
    [討論頁面](https://g0v.hackpad.tw/--hzxdTtdG3QU)

- [Pomin Wu](https://g0v.hackpad.com/ep/profile/oGf5HRRuJSf) 加了小字典功能，求code!
    - [開放都巿計畫小字典](https://docs.google.com/spreadsheets/d/11T9f4IswQ2eru-8HBGUbnVcM0cskTExoNOOG-xtGq4M/edit#gid=0)

## 其他資料

- [台南飛雁新村開放資料](http://data.tainan.gov.tw/dataset/project-plan)



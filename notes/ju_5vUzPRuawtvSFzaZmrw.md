---
title: 2018 高雄市長政見比較表
tags: hacktabl
---

> TODO: 改成高雄的版本
> 11/11 已修改

# 2018 高雄市長政見比較表

## 專案簡介

[高雄市長政見比較表](https://beta.hacktabl.org/kaohsiung2018)整理了四位候選人截至目前為止，官方網站上的政見以及在媒體上講過的公開承諾。每一筆資料都希望能附上出處原文的連結，而且任何人（包含讀到這裡的你）都可以[編輯、補充、更新這份表格](https://docs.google.com/document/d/1mIsb5rUPWOVegxVs9r48P1KRBb8mn3kMT_T60IpUJPs/edit)。

希望這張表格成為 2018 高雄市長選舉的**政見目錄**，用類似維基百科的協作方式，一同記錄候選人們所做過的承諾吧！

**發起人/拋磚人**：  [Johnson Liang](https://g0v.hackpad.com/ep/profile/z4JarLrJBea)


## 要解決的問題＆預計解法

目前高雄市長的四位候選人有兩位架設了自己的官網，並且陸續更新政見；各候選人們也在各種不同的場合，提出了一些公開的承諾，有些承諾已經透過媒體採訪讓選民得知，但不一定會被寫進官網政見或選舉公報裡頭。這些見報但沒被整理的承諾，可能會左右人們投票的意向，但選舉過後就逐漸被人遺忘，成為[翻臉不認帳的幾千件政見之一](http://ninjiatext.blogspot.tw/2014/08/1998.html)。

這個專案希望能蒐集每位候選人的政見、分不同的面相而陳列在一起。每一個政見與承諾，都有標記出處，選民們選前選後可以隨時看到當初候選人是如何描述自己的這項政見的。透過公開協作，希望表格內容可以一直有熱血鄉民持續更新。

## 目標與功能


### 預定功能


記錄候選人的公開政見與所有承諾，選前讓選民參考，並留存到選後，作為監督的材料。

### 預定使用者


#### 選前

- 尚未有特定立場，希望由政見決定投票對象的中間選民
- 已經有特定立場，希望替候選人更新政見的支持者

#### 選後

- 高雄市民

### 授權方式


[程式碼](http://github.com/MrOrz/hacktabl) MIT / [文本](https://docs.google.com/document/d/1ewQ0aKlY4sYU7qSLa8ydVbToJKSVcInTFtfIhHeMjzg/edit) CC-BY-SA 4.0

### 使用資料

- [陳其邁官網](https://kaohsiungceo.tw/) / [韓國瑜官網](https://richkh.tw/index.html)
- 陳其邁 Facebook / 韓國瑜 Facebook / 蘇盈貴 Facebook / 璩美鳳 Facebook
- 各新聞平台
- 維基百科


## Related Work


### 現有類似專案


這種比較表大多由新聞記者或鄉民整理。

### 相關專案


這個專案是 g0v-hackath9n 提案的「[自經區正反意見比較表](https://g0v.hackpad.tw/iTm0MWa9h4s)」的延伸專案。[Hacktabl](http://github.com/MrOrz/hacktabl) 是兩次黑客松之間冒出來的產物，並且在[第五次萌典松](https://g0v.hackpad.tw/8-moed5ct?r=0#8-moed5ct-)上有諸多改進。


## 徵求協作者


發起人/拋磚人：  [Johnson Liang](https://g0v.hackpad.com/ep/profile/z4JarLrJBea)
分工與成員
- [x] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
- [ ] NeedsDesigner: 需要介面設計
- [ ] NeedsData: 需要資料（擷取、清理）
> 想將候選人官網政見內容擷取 archive ，先以官網內容為主，然後依照議題進行分類，目前考慮存成 archive 存成 PDF 格式，不知道有沒有其他想法可以參考@@
> [name=Rz C]

> [韓國瑜官網 \- 市政白皮書](https://richkh.tw/index.html?policies%3F4)
> [name=Rz C]

> [陳其邁官網 \- 政策白皮書](https://kaohsiungceo.tw/)
> [name=Rz C]

- [ ] NeedsTech: 需要技術支援（程式、架站 etc)
- [ ] NeedsProcess: 需要幫忙設計作業流程
- [ ] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡
> 設定成 project registry 中的 tags，需要幫忙的會自動 promote 到 g0v project hub
> [name=ET B]



## 實作細節（非技術背景可跳填）


協作工具
- github repo：[http://github.com/MrOrz/hacktabl](http://github.com/MrOrz/hacktabl)
- hackfoldr 工作資料夾網址：[http://hack.etblue.tw/mayoral-table-project](http://hack.etblue.tw/mayoral-table-project)
- google drive 共用資料夾網址：無

進度與 to-do
Hacktabl 架構已經完成，若有新功能需求，請[發新 issue](https://github.com/MrOrz/hacktabl/issues)～
目前希望這份表格裡的連結都能有頁庫存檔備份，不過因為連結橫跨 facebook、新聞、似乎不容易 @@
> HTML 的部分用網頁爬蟲應該可先行，腳本寫好後再補上~
> [name=Rz C]


## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）

[2018 高雄市長政見比較表](https://beta.hacktabl.org/kaohsiung2018)已經上線，內容仍有賴大家一同協作。


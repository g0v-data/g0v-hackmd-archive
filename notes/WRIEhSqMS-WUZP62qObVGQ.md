---
title: "發文附上判決書運動"
tags: Judical,hackpad
---

# 發文附上判決書運動

> [點此觀看原始內容](https://g0v.hackpad.tw/hQ12Bq8UQIq)


2015/5/20 司法院裁判書查詢網站新增加了歷審判決功能，並且讓裁判書列表頁的外連解除，所以現在是可以分享單一判決連結的。許多新聞或是維基條目都是跟判決相關的，但是新聞常常會缺少原來判決書連結或是判決字號，導致當媒體亂報偏頗時，讀者難以從原始判決書求證，但是現在因為方便可以外連了，因此應該是可以在新聞連結下面附上判決書位置資訊，讓對該新聞有問題的讀者可以進一步從判決書求證

### 相關資料

- [2015/6/13 g0v hackath14n 提案投影片](https://docs.google.com/presentation/d/1sx3kcJKfU833DGJhFQdt9mFn6TEIIxdl-aB7lWECaT0/edit#slide=id.ga122bd45a_1_58)
- [陽春裁判書 parser](https://ronnywang.github.io/tw-court-parser)
    - [https://github.com/ronnywang/tw-court-parser/](https://github.com/ronnywang/tw-court-parser/)
- [臉書社團](https://www.facebook.com/groups/409440439257651/)  [https://www.facebook.com/groups/show.me.the.court.case/](https://www.facebook.com/groups/show.me.the.court.case/)

### 計畫部份

- 教戰手冊
- 判決

### 專案需求

- 寫一個懶人包，教網友怎麼透過新聞的描述文字，至司法院裁判書網站找到該相關的判決書字號
- 發起網友張貼判決書網址運動，讓網友願意在找到判決書之後，會主動附在新聞留言、PTT推文或者是維基百科條目中，以方便讀者可以更容易連到裁判書。
- 成立臉書社團，讓大家一起來幫忙找判決新聞對應的判決書位置
> 會有神秘的 api 加速查詢嗎？ XD
> [name=Finjon K]


### 寫手草稿

fb介紹：
你有「伸判決書」的習慣嗎？你是否懷疑過新聞報導陳述的判決結果可能偏頗，想找判決書原文，卻苦尋不到？

加入《來個判決書吧》群組，你就可以盡情伸判決書：貼上判決新聞連結，就有法律魔人網友幫找判決書原文網址，供你下載或轉貼，將真相公諸於世！

教學：
\- 裁判書查詢：
司法院： [http://jirs.judicial.gov.tw/FJUD/FJUDQRY01_1.aspx](http://jirs.judicial.gov.tw/FJUD/FJUDQRY01_1.aspx)
法源法律網： [http://fyjud.lawbank.com.tw/index.aspx](http://fyjud.lawbank.com.tw/index.aspx)

\- 取得裁判書分享網址：
- **司法院版：**
Step 1: 在司法院官網找到裁判書原文後，滑鼠右鍵點擊「友善列印」，複製其網址。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4f8bdbf90133e8bd8b96d11a73834a03)

Step 2: 將連結貼到 [陽春裁判書 parser](https://ronnywang.github.io/tw-court-parser) URL欄，點擊「Get」。「分享網址」出現內容即為可分享的網址。

- **法源法律網版：**
Step 1: 在法源法律網找到裁判書原文後，複製法院與字號整行文字。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_24dd2c2483361108d0e2f40d15a0d363)

Step 2: 將該行文字貼到 [陽春裁判書 parser](https://ronnywang.github.io/tw-court-parser) URL欄，點擊「Get」。「分享網址」出現內容即為可分享的永久網址。




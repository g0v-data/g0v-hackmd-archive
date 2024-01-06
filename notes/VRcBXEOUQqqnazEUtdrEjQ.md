---
title: "判決庭期檢索系統民間版"
tags: Judical,hackpad
---

# 判決庭期檢索系統民間版

> [點此觀看原始內容](https://g0v.hackpad.tw/pZlnxVzdHVY)

[5 月萌典松: moed10ct](https://g0v.hackpad.tw/5-moed10ct) 雨蒼開坑，[提案直播](https://www.youtube.com/watch?v=n3x8T3iXRsY)（AM11:44）

## 資料來源

司法院法學資料檢索系統 [http://jirs.judicial.gov.tw](http://jirs.judicial.gov.tw)
- 裁判書查詢
- 簡易案件查詢

資料開放範圍
[http://jirs.judicial.gov.tw/datascop.asp#fjud](http://jirs.judicial.gov.tw/datascop.asp#fjud)
-

## 坑形

> 雨蒼要不要把坑的摘要寫在這？
> [name=venev]

### 目前問題

- 官方版搜尋結果，只看得到主文，但看不到含兩造主張、事實、理由的「全文」

### 嘗試解法

- 雨蒼：先寫爬蟲，將目前網站上有的資料爬下來，再分析怎麼處理
- 考慮語意分析，抓出關鍵字
    - 問一下法規亦毒氣
- 常見案由組合，例如醫療糾紛案通常會包含哪些案由或法條
> for curation / mapping 法律 - 媒體 / 產業界對於案件不同命名描述。
> [name=venev]

> 例如法律世界是以（業務）過失傷害......來定性「醫療糾紛」中發生的法益損失
> [name=venev]

> [Simon Pai](https://g0v.hackpad.tw/ep/profile/n949ofsGwsB) 之前我們討論過關於「列出醫糾判決」，你還記得有沒有文字紀錄嗎
> [name=venev]



### 誰來填坑

- [x] 爬蟲
> 雨蒼填坑
> [name=雨蒼 林]

- [ ] 資料庫規劃
- [ ] 介面設計

## 認識判決書及裁判檢索

《[法官法](http://law.moj.gov.tw/LawClass/LawAllIf.aspx?PCode=A0030243)》教戰手冊之裁判檢索篇
[http://www.jrf.org.tw/newjrf/rte/myform_detail2.asp?id=3798](http://www.jrf.org.tw/newjrf/rte/myform_detail2.asp?id=3798)

刑事判決書架構主要分成三欄位：主文、事實、理由
[http://nccur.lib.nccu.edu.tw/bitstream/140.119/32643/7/75302607.pdf](http://nccur.lib.nccu.edu.tw/bitstream/140.119/32643/7/75302607.pdf)
- 主文：被告及犯罪結果
- 事實：犯罪事實描述
- 理由：裁判邏輯、法官心證

[判決書閱讀指南](https://g0v.hackpad.tw/niuy1UZbH4H)
[https://docs.google.com/spreadsheets/d/1AICuZnbPe_kFkDEcR0m9mbckvOJDdtv37RglC8VhAp0/](https://docs.google.com/spreadsheets/d/1AICuZnbPe_kFkDEcR0m9mbckvOJDdtv37RglC8VhAp0/)


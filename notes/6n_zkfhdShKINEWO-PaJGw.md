---
title: "藥物不良作用查詢"
tags: hackpad
---

# 藥物不良作用查詢

> [點此觀看原始內容](https://g0v.hackpad.tw/72TVP8zYYfs)

Background: 台灣進入老年化社會, 老年人口瞬間上升

Problem: 年紀大, 疾病多, 藥物可能開的也多, 但是藥物也有可能產生問題. 約30%住院病人是因為(多重)藥物產生之不良作用造成

Data: 台灣藥物資訊查詢多由個別醫院提供, 但民眾未必會仔細看

> 原本有一個 "藥品交互作用資料庫系統" ，但[因為預算被砍而消失](http://ys34485257.imgshelf.com/1856/1856-1-2.htm)，後來有一個 [中西藥交互作用資料庫平台](http://www.mohw.gov.tw/CHT/DOCMAP/DM1_P.aspx?f_list_no=755&fod_list_no=0&doc_no=44962) ，作的方式是開一個研究計畫案找彰化基督教醫院、國衛院、中醫藥研究所針對中藥交互作用建置「國內本土版」資料庫，目前是四年期計畫，終極目標是開放 API 給各醫院 HIS 去接，但是大約會在 105 或 106 年度。
> [name=Finjon K]

> 藥師全聯會，他們有接 TFDA 「建構社區藥局藥事照護平台與友善環境先導計畫」，裡面有要做藥局資訊系統以及交互作用資料庫，西藥也會採行一樣模式，由國內某醫院出人力去生content，參考的資料來源就是 Lexicomp (UpToDate), MDX, DIF, PubMed 等。
> [name=Finjon K]

> (以上消息來自某人臉書)
> [name=Finjon K]


外國仿單資料：
- [http://www.fda.gov/ForIndustry/DataStandards/StructuredProductLabeling/default.htm](http://www.fda.gov/ForIndustry/DataStandards/StructuredProductLabeling/default.htm)
- [http://dailymed.nlm.nih.gov/dailymed/index.cfm](http://dailymed.nlm.nih.gov/dailymed/index.cfm)

國內藥物外觀資訊查詢系統
- [http://www.chimei.org.tw/showmed/query.asp](http://www.chimei.org.tw/showmed/query.asp)
- [http://www.cch.org.tw/DRUG/online\_service/Drug\_01.aspx](http://www.cch.org.tw/DRUG/online_service/Drug_01.aspx)
- [http://www.fda.gov.tw/MLMS/(S(asvtska0eamdlqfz0dqassb2))/H0004.aspx](http://www.fda.gov.tw/MLMS/(S(asvtska0eamdlqfz0dqassb2))/H0004.aspx)

Solution: 根據 [http://data.fda.gov.tw/](http://data.fda.gov.tw/) 提供之核可藥物資料 及 [http://open.fda.gov](http://open.fda.gov) 美國openfda 之資料 整理合併, 提供方便查詢之介面

## open.fda.gov API

紀錄一下 open.fda.gov API 用法 , 提供 仿單 和 fda 通報兩個 database
單一藥物查詢 "Oxcarbazepine"
\[1\] 資料來源: 從仿單(廠商): Label

API [https://api.fda.gov/drug/label.json](https://api.fda.gov/drug/label.json?)[?](https://api.fda.gov/drug/label.json?)

\[drug_interactions\]
[https://api.fda.gov/drug/label.json?search=drug_interactions:Oxcarbazepine](https://api.fda.gov/drug/label.json?search=drug_interactions:Oxcarbazepine)

\[adverse_reactions\]
[https://api.fda.gov/drug/label.json?search=adverse_reactions:Oxcarbazepine](https://api.fda.gov/drug/label.json?search=adverse_reactions:Oxcarbazepine)

其實這邊英文的說明就很多了 (如果中文做到這樣就讚讚讚)
並且和從 [http://www.accessdata.fda.gov](http://www.accessdata.fda.gov) 抓回來1.7G解開的xml 內容一樣, 等於是openfda 把那些xml 已經parse 成 json 格式,所以可以直接接上 !!!!

\[2\] 資料來源: 從fda 通報系統(上市後)

API [https://api.fda.gov/drug/event.json](https://api.fda.gov/drug/event.json?)[?](https://api.fda.gov/drug/event.json?)

\[症狀統計\]
[https://api.fda.gov/drug/event.json?search=receivedate:%5B2004-01-01+TO+2014-12-18%5D+AND+(Oxcarbazepine)&count=patient.reaction.reactionmeddrapt.exact](https://api.fda.gov/drug/event.json?search=receivedate:%5B2004-01-01+TO+2014-12-18%5D+AND+(Oxcarbazepine)&count=patient.reaction.reactionmeddrapt.exact)

API Ref :[https://open.fda.gov/drug/label/reference/](https://open.fda.gov/drug/label/reference/)


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_163c2d697266174199448011cb92ba2b)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7ef4c9e02d349cb10c21553c3b3043c5)


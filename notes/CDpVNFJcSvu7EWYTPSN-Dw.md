---
title: "中資關係監控"
tags: hackpad
---

# 中資關係監控

> [點此觀看原始內容](https://g0v.hackpad.tw/zWfJ8Mi10Vt)


## 前言

中國國營的中信集團將與台灣中國信託互相參股，中國信託每年行銷金額近30億台幣，透過抽放廣告即可對台灣媒體施壓。紅頂商人們如頂新、徐旭東、郭台銘都想過要購買中嘉，徐旭東正在想辦法規避黨政軍條款。由於中國可以操控台商的利益，這些台商很有可能成為中國對台灣媒體施壓、對政治人物、集團輸送政治獻金等。中國要買下關鍵產業來控制媒體、控制政治人物的動作越來越明顯。
## 專案目標

### 1.呈現中國政府對陸台商、在台陸商的潛在影響力：

有五種關係能讓中國對台商施壓：成為投資人、成為客戶、許可執照、補貼與稅務優惠。
### 2.呈現紅頂商人對台灣政治人物的潛在影響力：

與政治獻金、黨營事業資料庫連結。

## 概念：

### 中國官員對企業利潤有很大的影響力：

以下幾個條件越強，中國政府對企業能施加的壓力越大：
1.  投資：各級政府（國營企業）、共產黨（黨營企業）投資，或他們的子公司孫公司來投資，成為股東或董事。
2.  執照：很多行業需要執照才能營業，例如汽車、水泥、石化、金融等等（執照與特許不一樣，在中國特許其實是加盟的意思）
3.  客戶：跟國營企業、黨營企業做生意
4.  補貼：
5.  稅務：中國查不查你稅，關係到你睡的好睡不好

### 中國可以透過以上的影響力去對台灣公司施壓，讓台灣公司去施壓台灣政治人物


我們要做的事情就是：找出每個立委所有的政治獻金捐贈者，看看這些捐贈者有沒有在中國投資？如果捐款者是公司法人，那就看公司的股東有沒有在中國投資？

以蔡正元為例：
營利事業捐贈者中，亞利通運（ [http://twcom-analysis.herokuapp.com/company/id/94781149#](http://twcom-analysis.herokuapp.com/company/id/94781149#) ）可以追溯到徐旭東的集團，而徐旭東在中國經營石化、水泥等需要政府許可的產業，徐旭東也正在努力想辦法買下中嘉。

我們想更有系統的去建立這些關係，找出捐贈者（公司）背後屬於那個集團？這個集團有沒有在中國有生意？在中國的生意有沒有中國政府的投資？


## 專案策略

1.  一間公司，或是一個人，就是一個節點（node)
2.  判定兩個節點的關係、方向、強弱：兩個nodes中間可以有 edge, edge 有種類,、有方向、有強弱，例如說一間公司與他的股東就可以用"投資"這個關係連起來，（從股東指向公司，持股比例或張數代表強弱），人跟人之間也可以透過"在同一間公司當股東"這種關係連起來，但這中關係沒有方向性，但如果我的公司可以控制你的公司，那這樣就有方向。
3.  我們最終想要找出的是，中國政府對於台灣立委有沒有影響力？影響力有多大？
4.  所以我們需要定義清楚每一種 x 對 y 有影響力的關係，然後建立這個關係資料庫。
5.  然後透過這個關係資料庫去做一個樹狀搜尋，看看能不能從台灣立委連到中國企業或甚至中國政府。

如何定義這個"有影響力" 的關係，就需要再研究，到最後也許做個立委的"紅色指數" 來衡量立委潛在受中國影響的程度。

## 需要的幫忙

1.  砍資料：需要所有台商在中國的股東、董事名單。(hackpad內有資料連結）
2.  找資料：
2.1判定哪些股東是中國各級政府的國營企業、黨營企業。
2.2判定哪些產業是高度管制、需要執照才能經營的行業。
2.3不曉得財報能不能看出該企業拿到的中國政府補貼？
2.4企業的大客戶、商業合作夥伴會有資料嗎？
3.設計呈現方式：目前概念是想要讓使用者輸入公司名稱或股東姓名，即可呈現他與中國政府、台灣政治人物的關係。可能資料完整一點後才會明朗
其實就是想要延伸Gilbert 的「黨營事業知多少」，納入台商與中國政治集團的關係。[http://weichengliou.github.io/blog/blog/2014/08/09/kmtnew/](http://weichengliou.github.io/blog/blog/2014/08/09/kmtnew/)
g0v 2014 summit Presentation:
[https://www.youtube.com/watch?v=kFftUb1gYtQ](https://www.youtube.com/watch?v=kFftUb1gYtQ)
感謝各位的幫忙與指教。



## 目前有的公開資料


2.台灣方面：
### 黨營事業知多少

[http://weichengliou.github.io/blog/blog/2014/08/09/kmtnew/](http://weichengliou.github.io/blog/blog/2014/08/09/kmtnew/)
g0v 2014 summit Presentation:
[https://www.youtube.com/watch?v=kFftUb1gYtQ](https://www.youtube.com/watch?v=kFftUb1gYtQ)

### 政治獻金類：

開放政治獻金Overview：[https://g0v.hackpad.com/8ow2GnliH48](https://g0v.hackpad.com/8ow2GnliH48)
政治獻金視覺化：[http://chungheng.github.io/g0v/page/index.html](http://chungheng.github.io/g0v/page/index.html)
資料位址：[https://github.com/ntuaha/GovCash](https://github.com/ntuaha/GovCash)

### 台灣公司資料類：

公司關係圖：[http://twcom-analysis.herokuapp.com](http://twcom-analysis.herokuapp.com)
台灣公司資料：[http://gcis.nat.g0v.tw](http://gcis.nat.g0v.tw)

### 來台陸資名單：

[陸資來台投資事業名錄.xls](http://www.moeaic.gov.tw/system_external/ctlr?PRO=DownloadFile&t=4&id=712)
in case 連結失效：
Sortable table
[https://lu-invest.herokuapp.com](https://lu-invest.herokuapp.com)
[https://github.com/hsin421/lu-invest](https://github.com/hsin421/lu-invest)

中國類：
### 香港交易所 披露易

[http://www.hkexnews.hk/reports/issuerinfo/issuerinfo_c.htm](http://www.hkexnews.hk/reports/issuerinfo/issuerinfo_c.htm)
董事名單 -\> 可以一次下載
股權披露 -\> 必須要分別查各公司

## 中國方面：

上海、香港的證交所資料，可以查到股東名單，但須判定哪些機構背後金主是國營事業或黨營事業。不過上海的資料待砍，希望有高手能幫忙！
### 上海證交所XBRL

[http://listxbrl.sse.com.cn/companyInfo/toCompanyInfo.do?stock\_id=600020.SS&report\_year=2014&report\_period\_id=5000](http://listxbrl.sse.com.cn/companyInfo/toCompanyInfo.do?stock_id=600020.SS&report_year=2014&report_period_id=5000)
定期報告
[http://www.sse.com.cn/disclosure/listedinfo/regular/](http://www.sse.com.cn/disclosure/listedinfo/regular/)
很完整，有股東結構
爬蟲：[https://github.com/dwhuang/sse_crawler](https://github.com/dwhuang/sse_crawler)
> Di-Wei ++ 太強大！
> [name=Tzu-Yao L]


BEIJING 公開所有公司中國名錄 - 以上市與未上市 但無股東資料
[http://beijing.mingluji.com/](http://beijing.mingluji.com/)

深圳證交所
[http://disclosure.szse.cn/m/drgg.htm](http://disclosure.szse.cn/m/drgg.htm)

其他非公開資料庫：
EMAGE 付費公司名錄
[http://international.emagecompany.com/big5/world/world.html](http://international.emagecompany.com/big5/world/world.html)

中國國有企業名單：
[http://baike.baidu.com/view/191098.htm](http://baike.baidu.com/view/191098.htm)
（中央）
[http://www.sasac.gov.cn/n1180/n1226/n2425/](http://www.sasac.gov.cn/n1180/n1226/n2425/)
[Wiki](https://g0v.hackpad.tw/ep/profile/r9VpeBqEplV)
[https://zh.wikipedia.org/wiki/Category:中华人民共和国国有企业](https://zh.wikipedia.org/wiki/Category:中华人民共和国国有企业)
Economists
[http://www.economist.com/news/china/21614240-reform-state-companies-back-agenda-fixing-china-inc](http://www.economist.com/news/china/21614240-reform-state-companies-back-agenda-fixing-china-inc)
"But most of the 155,000 enterprises still owned by the central and local governments..."



[http://www.saic.gov.cn/ywbl/zxcx/djqyxxcx/index.html](http://www.saic.gov.cn/ywbl/zxcx/djqyxxcx/index.html)

## 7/5 待辦事項

上海：有所有PDF資料，包括股權分配，需要想辦法整理成excel \- Ai-Lei Sun 偉哥
        上海證交所簡易爬蟲: [https://github.com/dwhuang/sse_crawler](https://github.com/dwhuang/sse_crawler) (資料已經爬回來了，有需要自行取用)
> DW5566好強！！
> [name=Tzu-Yao L]

解讀private 資料庫 csv file - Ai-Lei Sun
香港：找到董事代表的股東名單
理解財報，何謂B,H股，好倉淡倉
如何判定官股
查：
1.  國營企業名單 [Tzu-Yao Lin](https://g0v.hackpad.tw/ep/profile/u03RKfJH5nv)
2.  太子黨名單（ptt 怎麼查到的） [Sophia Li](https://g0v.hackpad.tw/ep/profile/Al8J0mZuIvW)
3.  需要執照的產業清單



現在有資料只有1，但需要判定國營企業和黨營企業, 未來希望補足2~5
客戶名單應該不好找，但是產業自由也許有指數或相關研究可以找？
要不然賴中強是怎麼知道水泥石化是高度管制產業？

## 可能呈現平台

1.  立委求職中 prototype:

如果客戶佔總營收 20% (maybe) 會揭露
捐款資料
財報：關係人揭露
持股超過20% 重要關係人
持股50% 直接影響力
台灣企業持股很分散

Cynthia: 揭露財報的規定，編制準則
財報：會定義影響力
台灣財報
看哪些東西是被需揭露的

財報查核事務所
但是中國在削弱四大

北京
深圳


中信:
抽銀根
聯貸案


呆帳有規定要揭露



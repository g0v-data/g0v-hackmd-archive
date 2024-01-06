---
title: "budget.g0v.tw - 中央政府總預算"
tags: 預算,open spending,hackpad
---

# budget.g0v.tw - 中央政府總預算

> [點此觀看原始內容](https://g0v.hackpad.tw/yCG1Z85irwO)

> CC-BY g0v-contributors
> [name=Chia-liang K]


## 2016 Reboot


[總預算](http://www.dgbas.gov.tw/ct.asp?xItem=26269&CtNode=5389&mp=1) / [中央政府各單位預算機關](http://ebas1.ebas.gov.tw/address/gbaagenooutput.asp)

各預算機關釋出中的「歲出計畫提要及分支計畫概況表」(BCME3440)是最細的資訊，各機關應該會提供 xls or xml (通常是 zip) (根據 「[公布(告)中央政府歲計會計書表電子檔案格式應行注意事項](https://drive.google.com/file/d/0B00j8_vTJFGUZTk3UnUxaUJiV1M2bnZ1TTdaTTVaRHZiczRv/view?usp=sharing)」 )

TODO: 整理所有的「[分支計畫概況表](https://ethercalc.org/twebas)」

TODO: xml 檔案格式說明（目前找不到）

### 分支計畫 xml 與 xls 的差異 (bcme3440 表)

- xml objectno 需參照 [中央政府第一級至第三級用途別科目分類定義](https://www.dgbas.gov.tw/public/Data/552984733GEYI9Z14.pdf)
> 這定義竟然沒有數位化 T____T
> [name=Tonyq W]

- 單筆預算「承辦單位」須從代號查詢 (對照表待補)
- 「計畫內容」與「預期成果」分拆在兩個特殊的 BCDTMEMO bc_key 中
> 看起來困難點在 bc\_key 上...似乎也跟 ba\_budgetno 有些關係？
> [name=Tonyq W]


- xml 無小計，全部是 raw data

#### BCTDBUDGETDETAIL

        <BCTDBUDGETDETAIL_row>
            <ba\_fiscalyear>106</ba\_fiscalyear>
> 年份
> [name=Tonyq W]

            <ba\_fundkind>1</ba\_fundkind>
            <ba\_budgetkind>1</ba\_budgetkind>
            <ba_specialbudgetno/>
            <ba\_agenno>02001</ba\_agenno>
            <ba\_agentype>C</ba\_agentype>
            <ba\_budgetstate>1</ba\_budgetstate>
            <ba_versiondate/>
            <ba\_budgetyear>106</ba\_budgetyear>
> 預算年份
> [name=Tonyq W]

            <ba\_budgetno>32020010100</ba\_budgetno>
            <ba\_subprojectno>01</ba\_subprojectno>
            <ba\_departno>09</ba\_departno>
            <ba\_objectno>0111</ba\_objectno>
            <ba\_budgettype>E</ba\_budgettype>
            <ba\_budgetsource>1</ba\_budgetsource>
            <ba\_mergetype>1</ba\_mergetype>
            <ba\_budgetamt>110416000.00</ba\_budgetamt>
            <ba_flowflag/>
            <ba_signflag/>
            <ba_signno/>
            <ba\_key>11  </ba\_key>

> 底下是跟主計總處確認過的欄位說明
> [name=Tonyq W]

 <BCTDBUDGETDETAIL_row>
            <ba\_fiscalyear>106</ba\_fiscalyear>
            //會計年度

            <ba\_fundkind>1</ba\_fundkind>
            //基金別

            <ba\_budgetkind>1</ba\_budgetkind>
            //預算別 一般公務 特別預算

            <ba_specialbudgetno/>
            // 特別預算代號 (A0/A1...)

            <ba\_agenno>26001041</ba\_agenno>
            // 26-001-041 2-3-3

            <ba\_agentype>C</ba\_agentype>
            //A 主管 B 彙編 C 單位

            <ba\_budgetstate>1</ba\_budgetstate>
            // 概算、預算、法定預算

            <ba_versiondate/>

            <ba\_budgetyear>106</ba\_budgetyear>
            //跨年度預算會用到

            <ba\_budgetno>52260014400</ba\_budgetno>
            <ba\_subprojectno>01</ba\_subprojectno>
            // 以上兩個一組可以說明預算跟對應的分支計畫（分支計畫單位自己編的）
            // 應該要有 name

            <ba\_departno>02</ba\_departno>
            // 承辦單位 （單位自己編的）

            <ba\_objectno>0250</ba\_objectno>
            //用途別

            <ba\_budgettype>E</ba\_budgettype>
            //R 代表歲入 E 代表歲出

            <ba\_budgetsource>1</ba\_budgetsource>
            // 年度預算

            <ba\_mergetype>1</ba\_mergetype>
            //

            <ba\_budgetamt>14000.00</ba\_budgetamt>


            <ba_flowflag/>
            <ba_signflag/>
            <ba_signno/>
            <ba\_key>11  </ba\_key>
        </BCTDBUDGETDETAIL_row>

#### BCTDMEMO

        <BCTDMEMO_row>
            <bc\_fiscalyear>106</bc\_fiscalyear>
            <bc\_fundkind>1</bc\_fundkind>
            <bc\_budgetkind>1</bc\_budgetkind>
            <bc_specialbudgetno/>
            <bc\_agenno>02001</bc\_agenno>
            <bc\_agentype>C</bc\_agentype>
            <bc\_budgetstate>1</bc\_budgetstate>
            <bc\_reportno>BCME3440</bc\_reportno>
            <bc\_key>3202001901101xxxxxx04xxxxxxxE1x0</bc\_key>
            <bc_versiondate/>
            <bc\_content>汰換副禮車2輛，每輛4,100千元，合共8,200千元。</bc\_content>
        </BCTDMEMO_row>

每個「工作計畫名稱及編號」都有一個國庫署的代號：[各年度國庫收支應用科目及其代號表](http://data.gov.tw/node/12010)

#### 機關別清單

[http://www.dgbas.gov.tw/public/data/dgbas01/106/106hb/106B/B/(8)%E4%B9%99-106%E5%88%86%E7%B4%9A%E8%A1%A8(%E5%AE%9A%E7%A8%BF)(%E5%B9%B8%E6%95%8F).doc](http://www.dgbas.gov.tw/public/data/dgbas01/106/106hb/106B/B/(8)%E4%B9%99-106%E5%88%86%E7%B4%9A%E8%A1%A8(%E5%AE%9A%E7%A8%BF)(%E5%B9%B8%E6%95%8F).doc)


### 機關別 xml/xls 預算對照 (BAME5480)


### 一行 xml 轉 csv (並移除小計)


```
npm i xml-json json2csv
./node\_modules/.bin/xml-json  106-0000-歲出機關別預算表-20160829110420.xml BAME5480\_row |sort  | jq  -s '[ .[] | {agentype,displayname: .mh\_budgetname,budgetno\_conver,amount:.tyear\_amt,amount\_previous:.lyear\_amt,description:.bc\_content,subsection: .budgetno\_conver[0:2], admin: .budgetno\_conver[2:4], agency: .budgetno\_conver[2:6], item: .budgetno\_conver[6:10], year: 2017, budget\_type: "proposed"  } | select(.subsection != "00" and .agency != "") ]' | ./node\_modules/.bin/json2csv

```
### 內容


> 我試著比照了一下同一筆資料，總預算 xls 跟 xml 的資料。
> [name=Tonyq W]

```
<BAME5480_row>
   <BAME5480_row>
    <budgetno>32020010401</budgetno>
    <agenno>02001</agenno>
    <agentype>C</agentype>
    <mh\_budgetname>國家發展研究及諮詢</mh\_budgetname>
    <displayname>國家發展研究及諮詢</displayname>
    <budgetno\_conver>3202010401</budgetno\_conver>
    <tyear\_amt>12626000</tyear\_amt>
    <lyear\_amt>8569000</lyear\_amt>
    <byear\_amt>7676401</byear\_amt>
    <b\_amt>4057000</b\_amt>
 <bc_content>本年度預算數之內容與上年度之比較如下：&lt;#H1&gt;國政規劃與諮詢經費8,078千元，較上年度增列專案議題會議幕僚作業等經費2,000千元。&lt;#H1&gt;國政建言經費1,793千元，與上年度同。&lt;#H1&gt;兩岸關係與區域發展經費2,755千元，較上年度增列出國考察及參與研討會等經費2,057千元。</bc_content>
</BAME5480_row>

```
xls
| 款 | 項 | 目 | 節 | 說 明 | 本年度預算數 | 上年度預算數 | 本年度節與上年度  
比 較 | 說 明 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | 1 | 4 | 1 | 3202010401  
國家發展研究及諮詢 | 12,626 | 8,569 | 4,057 | (中略) |
> tyear_amt = 本年度預算數
> [name=Tonyq W]

> lyear_amt = 上年度預算數
> [name=Tonyq W]

> b_amt = 本年度節與上年度比較
> [name=Tonyq W]

> bc_content = 說明
> [name=Tonyq W]

> 沒有款項目節，這樣變得很難判斷預算歸屬....只能從 budget number 推了。（-_-）
> [name=Tonyq W]

> agenno 好像有意義，總統府中 1-1 都是 02001 , 1-2 開始是 02010 ，1-3 換成 02030
> [name=Tonyq W]


> 看起來拼圖應該是 budgetno
> [name=Tonyq W]


> 00-02-00-0000 總統府主管 (1)
> [name=Tonyq W]

> 00-02-01-0000 總統府 (1-1)
> [name=Tonyq W]

> 32-02-01-0000 國務支出 (無款項目節)
> [name=Tonyq W]

> 32-02-01-0100 一般行政(1-1-1)
> [name=Tonyq W]


在 [http://data.gov.tw/node/12010](http://data.gov.tw/node/12010)  裡面的 104年度國庫收支應用科目及其代號表.pdf ，page  7 找到這個。

1.本年度歲出機關別預算科目**第 1 組「款」代表政事別(參閱附錄 2)**，**第 2、3 組「項」代表主管及機關別(參閱附 錄 3)**，**第 4 組「目」代表業務計畫**，第 5 組「節」代表工 作計畫(參閱附錄 4)。例如:第 10 款「財務支出」(40)、第 1 項「財政部」(1701)、第 1 目「一般行政」(0100)，其代號及檢查號碼為 4017010100-7。

不過有趣的事情是完全一致的對照組是在 budgetno_conver 元素裡面。
> budgetno 第五位多一個 0
> [name=Chia-liang K]


[主管及機關別](https://ethercalc.org/z2bl5nzi472q): [https://ethercalc.org/z2bl5nzi472q](https://ethercalc.org/z2bl5nzi472q)
轉 json 然後補齊到四碼 [https://gist.github.com/tony1223/a650a3510275912db8fa4f2e41b6f82f](https://gist.github.com/tony1223/a650a3510275912db8fa4f2e41b6f82f)

歲出 budgetno  前兩碼款別(政事別) 對照表
json [https://gist.github.com/tony1223/afe26b9a8bec1c814e176cc76056471e](https://gist.github.com/tony1223/afe26b9a8bec1c814e176cc76056471e)

| 名稱 | 款之編號 |
| --- | --- |
| 政權行使支出 | 31 |
| 國務支出 | 32 |
| 行政支出 | 33 |
| 立法支出 | 34 |
| 司法支出 | 35 |
| 考試支出 | 36 |
| 監察支出 | 37 |
| 民政支出 | 38 |
| 外交支出 | 39 |
| 財務支出 | 40 |
| 邊政支出 | 41 |
| 僑務支出 | 42 |
| 國防支出 | 48 |
| 教育支出 | 51 |
| 科學支出 | 52 |
| 文化支出 | 53 |
| 農業支出 | 58 |
| 工業支出 | 59 |
| 交通支出 | 60 |
| 其他經濟服務支出 | 61 |
| 社會保險支出 | 66 |
| 社會救助支出 | 67 |
| 福利服務支出 | 68 |
| 國民就業支出 | 69 |
| 醫療保健支出 | 71 |
| 環境保護支出 | 72 |
| 社區發展支出 | 73 |
| 退休撫卹給付支出 | 75 |
| 退休撫卹業務支出 | 76 |
| 債務付息支出 | 79 |
| 還本付息事務支出 | 80 |
| 專案補助支出 | 84 |
| 平衡預算補助支出 | 85 |
| 其他支出 | 89 |
| 第二預備金 | 90 |

政事別大分類表
[https://gist.github.com/tony1223/d3802fc7503402d9d138ee0c0a354e4e](https://gist.github.com/tony1223/d3802fc7503402d9d138ee0c0a354e4e)

objectno  (106 年)
[https://docs.google.com/spreadsheets/d/1xgUP3OFiuPjLFRKTvO5HSroKilnRKYznyZmrKUhyUqA/edit#gid=110726157](https://docs.google.com/spreadsheets/d/1xgUP3OFiuPjLFRKTvO5HSroKilnRKYznyZmrKUhyUqA/edit#gid=110726157)

其他
Fiscal Data Package: [http://specs.frictionlessdata.io/fiscal-data-package/](http://specs.frictionlessdata.io/fiscal-data-package/#which-dimension-type)[#which](https://g0v.hackpad.tw/ep/search/?q=%23which&via=yCG1Z85irwO)[-dimension-type](http://specs.frictionlessdata.io/fiscal-data-package/#which-dimension-type)
TonyQ: [https://github.com/tony1223/tpe-2016-budget](https://github.com/tony1223/tpe-2016-budget)

各機關資料： [http://ebas1.ebas.gov.tw/address/gbaagenooutput.asp](http://ebas1.ebas.gov.tw/address/gbaagenooutput.asp)

## Archive

## About


### 資料來源


目前使用的資料是主計處公布之：
- 2007-2013 年經立法院審議通過之法定預算
- 2014 - 中央政府總預算案
目前僅處理歲出部分。[原始資料](http://www.dgbas.gov.tw/ct.asp?xItem=26269&CtNode=5389&mp=1)
- [原始資料](http://www.dgbas.gov.tw/ct.asp?xItem=26269&CtNode=5389&mp=1)
- [處理程式](https://github.com/clkao/twbudget)
- [處理過的純細項資料](https://github.com/g0v/twbudget/tree/master/app/assets/data)

## TODO


- 加入歲入部分
- 預算案與法定預算比較
- 追加預算
- 地方政府預算

> 週三(10/19)下午要去主計總處聊有沒有可以界接預算視覺化的部分，有沒有任何具體需要的或有沒有任何人想一起去的？ 
> [name=Tonyq W]

> 來龍去脈是上週五在資訊地方聯席會議碰到主計總處的資訊處長潘處長，提到做了預算視覺化，希望能有進一步的合作或交流。
> [name=Tonyq W]

> 或許有些我們現在還缺的資料或說明也可以請他們再協助提供？
> [name=Tonyq W]


## 2016 1019 會議討論


1.  預算視覺化
2.  資料分析

- 歲出計畫提要及分支計畫概況表  到二級 （中央政府第一級至第三級用途別科目分類定義）

- 可以用 agent number 對照遺漏的

- 開放諮詢小組


<ba\_budgetno>52260014400</ba\_budgetno>
<ba\_subprojectno>01</ba\_subprojectno>
兩個一組 key

BA 是總預算
BC 是單位

## FAQ


### 為何有黑色的圈圈？


黑色是無法對應到前一年相同預算科目的項目，常發生在政府組織改造，新舊科目編號改變時。

### 單位換算很白痴...


其實一開始只是為了諷刺媒體常常做奇怪的單位換算，所以我們都先幫媒體算好了。

視覺化目的在於降低資訊流通的門檻，單位換算同時也提供了話題性，有輔助的功用。光就單位換算無法達到監督政府的效果，但它吸引了更多的目光(包括你)，讓我們有機會向你解釋我們所做的一切。

### 單位換算有政治影射，你們到底是藍的還是綠的？


單位換算是基於當時的時事而設計，並沒有針對特定的政黨。然而，參與者有各種政治光譜，唯一共同的是所有程式、文件，需以開放原始碼釋出，讓任何人都能檢驗、修改、重製、再利用。如果你覺得哪邊有偏頗，可以提出回報討論不恰當的地方，或是直接修改，或者把整份程式及資料拿去做出一個你認為更中立的版本。

### 預算視覺化不是重點，看懂預算的眉角不是這個，不要以為人民都要看你們這個才看得懂。


我們的出發點其實是讓自己稍微看得懂，並且把成果（含清理好的原始資料）分享出來，讓想改進，或者有相關專業知識的人，也都能更容易的處理資料，讓人民可以不需經過媒體報導，即可閱讀第一手的資料，自行去選擇希望關注的議題。

一開始參與的人是的確是沒有相關背景的，只是藉著資料處理跟視覺化的能力，在兩三天中，把這樣的雛形做出來。如果你對預算解析有心得，並願意分享一些值得注意的點，或者有呈現方式上的想法的話，歡迎你參加討論，或者直接實作。

### 你們以為視覺化可以解決一切問題，但是視覺化的資料會失真，更加誤導人。


資訊視覺化是一種方便解讀資料的工具，最常見的例子就是各式的圓餅圖或折線圖，例如常見的股市K線圖。這樣的工具在不當的使用時的確會造成誤導的效果，端看使用的人能否公正的去看待資料。

像是選舉時常看到的選票地圖，有些區域人很少但面積很大，的確有誤導之虞，這就是個說明視覺化資訊失真很好的例子，事實上也有一些方法在嘗試解決這個問題，例如將地圖面積依數值比例作縮放的 cartogram ，我們在實作台灣地理資訊函式庫時也有試著加入這樣的功能，可參見 [http://github.com/g0v/twgeojson/](http://github.com/g0v/twgeojson/)

換句話說，視覺化並不會導致資訊失真，而是人為操作上的失誤導致的。我們在進行資訊視覺化的同時，除了歡迎各方指出我們實作可能產生的盲點，也會將源碼與資料來源公開，任何人都可以協助修正。

### 研究預算是智庫等級的事情，輪不到你們來做吧？


在維基百科出現前，編輯百科全書也是智庫等級的事情。我們認為，成果開放、讓任何人都可以改進，也是一種探討真相的方式。

另外，我們所做的事情重點在於讓資訊更容易被取得；當資訊更容易取得時，就更有機會讓其他民間專業人士進行研究，這樣子才能提供更多不同面向的資訊解讀，而不會僅僅由政府告訴人民什麼是對的。

我國立法院預算中心，也期待全民參與預算的審查與研究，已連續第三年舉辦[中央政府總預算研習講座](http://www.taiwanthinktank.org/chinese/page/2700/print)。更多立法院預算中心的[介紹](http://www.ly.gov.tw/06_lyacc/acc.jsp)與[研究成果查詢網站](http://www.ly.gov.tw/06_lyacc/acc.jsp)。

### 可以不透過網站視覺化，直接篩選、下載預算的數字表格嗎？


當然沒問題，請自行瀏覽[處理過的純細項資料](https://github.com/g0v/twbudget/tree/master/app/assets/data)。

### 為何不做地方政府預算，或是解析度更詳細的部門分項預算？


所有的參與都是自主的，每個人時間有限，先做自己關心的部分很正常。你可以提供相關連結、excel 檔、或者清理過的資料，在[這裡](https://github.com/g0v/twbudget/issues)回報。

## 延伸閱讀


[網路廣播《深音》談 g0v.tw：分散協作的實力與潛力](http://blog.g0v.tw/post/60348667148)
相關專案：[立法院預算中心神祕第六人](https://g0v.hackpad.tw/PycBHXfQPHM)
[Examples of Fiscal Data Visualisations](https://goo.gl/D8a25f)




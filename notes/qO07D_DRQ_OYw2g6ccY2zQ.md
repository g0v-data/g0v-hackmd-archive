---
title: "<progress>市長承諾</progress> @ g0v unconference 2014"
tags: Promise Tracker,hackpad
---

# <progress>市長承諾</progress> @ g0v unconference 2014

> [點此觀看原始內容](https://g0v.hackpad.tw/6oAR9BlZDoH)

> 命名：市長按摩站 對市長施壓(?)
> [name=Johnson L]

> 市長馬殺雞 (?)
> [name=Johnson L]

> any alternatives / naming candidates?
> [name=Shelling F]

> 市政，給力嗎(?) // 剛好和「市長，給問嗎？」呼應。也是要看想不想和沃草名稱這麼像
> [name=Shelling F]

> 另外，此專案可以成為長期獨立小松「市政松」？「承諾松」？「新政松」？
> [name=Shelling F]

> 市政滿意度 municipal gratification => github.com/g0v/munigratify ? => 覺得名字不錯就開幹
> [name=Shelling F]

> update: 忍不住就開了 repos [https://github.com/g0v/munigratify](https://github.com/g0v/munigratify)
> [name=Shelling F]

> 其實我現在想要往 promise tracker 的方向走去耶 XD 弄成一個 general 的 promise tracker，不管是市長還是黨派還是焦點團體想要監督哪個部會，都可以用這個。
> [name=Johnson L]

> 好阿，那就換個名字 :D 
> [name=Shelling F]


↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓
**討論請移駕至 hackfoldr【**[政治承諾追蹤網](http://beta.hackfoldr.org/ppt)**】**
### 本 pad 是 g0v unconference 2014 時的提案，留存並 moderate 以供日後查找。

↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑

## 專案簡介

All g0v unconference 2014 sessions in lounge area: [http://beta.hackfoldr.org/g0v-summit-2014-unconf/](http://beta.hackfoldr.org/g0v-summit-2014-unconf/4psifYRIWBJ)[4psifYRIWBJ](http://beta.hackfoldr.org/g0v-summit-2014-unconf/4psifYRIWBJ)

政治人物會以已達成的政見，來說明自己的執行力；但沒有當初競選時的所有承諾作為「分母」，我們很難公允地去評價一個政治人物的執行能力。以臺北市長選舉為例，在選舉前我們已經[透過協作方式，列出了候選人的選舉承諾](https://g0v.hackpad.tw/2014--9LS2taj2E2A)；在選後，個別的壓力團體與利益團體，也會緊盯他們所關注的支票是否有兌現。市長發言會強調他做到的部分，壓力團體開記者會責成市長政見跳票的部分，但到底這個市長整體的執行力如何呢？我們認為可以將當初的各項承諾，加上進度條（政見研擬 > 議會排案 > 議會通過 \> 實際實行 v.s. 跳票 + 跳票理由）來追蹤。對個別議題有興趣者，可以在這裏連結到相對的壓力團體；一般的選民則可以透過全面的承諾進度來評定這個市長的執行力。

- 監督當選人的施政
- 給市議員以及市民的 checklist，施壓也能施對地方


[https://www.youtube.com/watch?v=3OR0W1MvP3U](https://www.youtube.com/watch?v=3OR0W1MvP3U)


**發起人/拋磚人**：  [Johnson Liang](https://g0v.hackpad.com/ep/profile/z4JarLrJBea)

## 要解決的問題＆預計解法


我們希望用政策的完成率，來評估一個政治人物的執行力。因此，我們需要一個共同協作的政治承諾追蹤（promise tracking）平台。承諾追蹤平台上面列好所有該政治人物的承諾，如：

```
市府公布 2015 已編列預算，鼓勵全民審查，擠出 100 億
2015 後匡列 100 億預算額度，公開由公民提案後交由專家評選或市民網路投票、議案確定後執行
開放預算資訊交由專家或市民審查
年滿 18 歲的台北市民可用自然人憑證或手機網路投票
市長先提出政務官人選、市民上網圈選，市長擇優任用
數字績效評鑑制度引入市府，人民直接評鑑局處首長年終考核

```
當相關新聞發生時，使用者（或許是此政治人物的支持者？）可以來到這個平台，找到相對應的承諾，貼上新聞鏈結，並且更新進度條。

## 目標與功能

### 預定使用者

當候選人爭取連任時，供選民可參考
一般公民可隨時關心施政狀況

### 預定功能

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_691cd9ca843c9ed26033a430f47df7af)
#### 進度條

進度條是 visualize 「執行力」一個很直觀的方式。
各自政見承諾，會有各自的 progress bar，如「研擬中」「進議會」等等；另外我們也可以結算此政治人物的總進度。
進度由全民更新，需要檢核（像 code review）；更新進度時，要提供出處。
> news update
> [name=Johnson L]

> 法規，市議會，通過
> [name=Johnson L]

> 每個階段都可以 checklist，每個步驟都要有附上新聞
> [name=Johnson L]

> 加上社交/訂閱功能，因為會想要知道
> [name=Johnson L]

> conflict resolve? wikipedia 型式，保留討論，由管理者處理
> [name=Johnson L]


#### 政見需求

政見和 promise 需細分成具體可考核。
一些如「任期間家人絕不干預市政」的政見，進度則每日更新，期滿才 100%。
每個 promise，要寫上負責的局處單位（某個局長，或跨局合做的話就是各個局）(及其聯絡方式? 信箱/電話)。

#### 其他（Nice-to-have）

- 相關壓力團體的鏈結
- 和議員政見比對，列出相關議員以及聯絡方式
- 任期倒數
- 無法評斷「進度」的政見，只讓大家貼新聞（或主動 crawl）。
- propose 變更

## Related Work


### 現有類似專案


### 智利對總統承諾的 promise tracking

[http://deldichoalhecho.cl/](http://deldichoalhecho.cl/) by lfalvarez @ Chile
其中，個別承諾（promise）是人設定的。
之後，他們釋出了一個 open source 的 promise tracker (django app!)：
Source code: [https://github.com/ciudadanointeligente/check-it](https://github.com/ciudadanointeligente/check-it)

### 其他 promise tracker

[http://promesometro.pe/](http://promesometro.pe/)
歐巴馬 meter & 共和黨 meter
[http://www.politifact.com/truth-o-meter/promises/](http://www.politifact.com/truth-o-meter/promises/)

### MIT Center for Civic Media - Promise Tracker

[https://civic.mit.edu/promise-tracker](https://civic.mit.edu/promise-tracker)
```
Promise Tracker will allow citizens to see evidence documenting the origin of a promise, collect data about the status of a promise—for example, going to the location of a proposed health clinic and taking a photo of the site—and then take action if the promise has not been fulfilled. Actions can take many forms. For example, citizens can notify civic leaders of their concerns, approve of the progress being made, recruit others to help collect data about the topic, or amplify a story about unfulfilled promises to journalists.


```
### 柯Ｐ新政進度條

[https://www.facebook.com/kpmeter](https://www.facebook.com/kpmeter)
Facebook 專頁，由小編更新資訊圖表，公開進度計算方式：[https://www.facebook.com/kpmeter/info](https://www.facebook.com/kpmeter/info)



### 相關專案

[2014 臺北市長政見比較表](https://g0v.hackpad.tw/2014--9LS2taj2E2A)

### 授權方式

Source code MIT

### 使用資料

[2014 臺北市長承諾一覽表](https://docs.google.com/document/d/1ewQ0aKlY4sYU7qSLa8ydVbToJKSVcInTFtfIhHeMjzg/edit)

## 徵求協作者


發起人/拋磚人：  [Johnson Liang](https://g0v.hackpad.com/ep/profile/z4JarLrJBea)
分工與成員
- [x] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
- [ ] NeedsDesigner: 需要介面設計
- [ ] NeedsData: 需要資料（擷取、清理）
- [ ] NeedsTech: 需要技術支援（程式、架站 etc)
- [ ] NeedsProcess: 需要幫忙設計作業流程
- [x] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡
> 設定成 project registry 中的 tags，需要幫忙的會自動 promote 到 g0v project hub
> [name=ET B]


## 實作細節（非技術背景可跳填）

ReactJS + flux
Storage: pgrest, firebase.io, parse.com

## Future work

這樣的系統其實可以套用在任何需要修法的承諾。
中央執政團隊「承諾推動」到「實際立法」到「法案上路」是條漫長的過程，而且可能會橫跨很多不同的法律，例如說自經區條例之外，也修改了農產與教育相關的條例等等。
這樣的系統提供一個完整的 list of checkpoints，讓大家看看從「整體政策」的角度來看個別相關法修法的進度到哪裡。

以 [http://mag.stormmediagroup.com/transgender/16/](http://mag.stormmediagroup.com/transgender/16/) 為例，文中的「消除⋯⋯公約」是由[行政院性別平等會](http://www.gec.ey.gov.tw/News_Content.aspx?n=9AC8D0E0C33FF2BF&sms=8D9E42E64BBA4FB6&s=3FA23562B533982A)負責，最新消息裡面有寫：
```
本院於101年6月21日函頒「性別平等大步走－落實消除對婦女一切形式歧視公約計畫」，建置法規檢視系統，由各級政府機關進行法規檢視，並於法規檢視系統中填報檢視案件數計3萬2千餘件法規、命令及行政措施，召開11次CEDAW法規檢視專案審查小組會議，經檢視不符合之法規及行政措施計74件，已完成修法8件，送立法機關審議中7件，餘在行政機關修訂程序中。預訂於103年底全面完成法規之制（訂）定、修正或廢止及行政措施之改進。
```
這裡就有修法進度可以參考。

## 提議

- 是否可以先採用一般的 issue tracker 如 [github issue tracker](https://guides.github.com/features/issues/) 或是 [trello](https://trello.com/) 來管理政見的實施進度，再來反思泛用的 issue tracker 面對這種特殊用途（市長承諾）來說有什麼不足的地方？
> 這是很酷的出發點！我之前一直從 Wikipedia 的角度在思考 promise tracker，覺得 promise tracker 只要貼連結、更新進度，應該比起其他群眾協作的 Wikipedia 或 [市長承諾表](http://hacktabl.org/taipei-mayoral-election-2014) 還要平易近人一些。
> [name=Johnson L]

> TODO list 應用如 Trello，是一個我之前從來沒有想到過的切入點。我認為可以先把過去市長的政見放進 Trello（像是下面的 2010 胡自強政見），然後從 2 種使用者的角度，來觀察這個 issue tracker 是否合用：
> [name=Johnson L]

> 1) 剛看到一則相關新聞，想要來更新某特定政見進度的「公民編輯」，能不能輕鬆地找到相關政見，進行更新？
> [name=Johnson L]

> 2) 連任選舉將至，想要來看看這位行政首長的整體施政能力的「選民」，能不能從這個介面找到他最想要的資訊？
> [name=Johnson L]

> 至於 github issue tracker，他的優點是[milestone](https://help.github.com/articles/viewing-your-milestone-s-progress/) 會用 progress bar 呈現。我們可以用一個 github repo 代表一個候選人、一個 milestone 代表一個種類的政見（如「教育」）、 一個 issue 代表個別承諾（如「選擇一所公立國中與國小進行教育實驗，提高實驗教育至 3%~5%，使公立/私立/實驗教育三軌併行 」），或甚至是全台灣的市長通通放進一個 github repo，然後每個 milestone 是一個市長 XD  然而，github 的 issue 只有兩個 state (open/close)，而且整體設計比較重在 issue 的討論過程，並非讓進度的更新與表列更加容易，因此「公民編輯」與「選民」這兩種目標使用者角色，似乎滿難在 github issue tracker 上面有所發揮。
> [name=Johnson L]



## Unconference 工作區


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cffd8f7c92ed30d2ba2bd6f75078f4f0)

> 以下待整理
> [name=Johnson L]

問題：有些政見無法 progress 化。馬英九有計算他的政見達成率，是怎麼算的？

### 參考連結

[http://www.hi-on.org.tw/bulletins.jsp?b_ID=135443](http://www.hi-on.org.tw/bulletins.jsp?b_ID=135443) # 馬總統九成七政見達成率是怎麼算的
```
即將併入國發會的行政院研考會日前提出一分報告，指馬總統二○○八年提出的大選政見，至去年上半年為止，在四百十四項政見中，「已完成」及「具階段性成果」者共計四百零一項，完成比率高達九十六點九％。研考會能將政見的追蹤考核「量化」到這種出神入化的地步，真不愧是形式主義的大師。
https://github.com/ronnywang/50d50v/blob/master/20141103/result.csv
2014年與六都市長相關新聞列表
http://penghu-chien-885739.middle2.me/?keyword=胡志強+承諾
上面可以查 2010 整年度聯合新聞網與五都市長(加當時的桃園縣)候選人相關新聞




```
### 討論紀錄


郝明義發起「希望地圖」
每年由專家學者評估，因為客觀的 progress 可能不等於實際的 progress。

陳水扁：
當選後，要求局處研擬具體方案，分四年（不可能）。會在每年預算與市政報告時，呈報給議員。

nchild: 透過關係（？），把不明確的政策講清楚。

雨蒼：「民眾觀感/主觀達成率」：可以讓大家有個 switch，留下說「你覺得這個東西達成了沒」，但 assume 每個人都會來 actively 更新是否達成。

淑芳：一年後去追蹤就消失

雨蒼：以朱立倫先動土才發包，
發包 > 動土 \> ⋯⋯ 的 progress bar 就會失靈。

Yuren: 對於一則新聞，vote 還沒做 / 開始做 / 有達成，用這個去算「達成率」

個別承諾變成三種 stage，換成燈號，但每個大項目可能可以是 progress bar
> 首頁可以撈出網友最新回報的新聞，問 visitor 說「你覺得這個新聞 (還沒做 開始做 有達成 沒達成 ）ＸＸＸＸＸ承諾？」
> [name=Johnson L]


> 為什麼要上來回答？大多是不滿
> [name=Johnson L]

> 像是 create issue -> create branch -> code review -> merge 的概念
> [name=Shelling F]

> milestone 是 柯P 新政的大項，下面的 issues 應該還沒具體決定，或等待市府團隊/市民決定
> [name=Shelling F]

> milestone has many issues
> [name=Shelling F]

> create branch 開始做
> [name=Shelling F]

> code review 過市民接受門檻才 merge
> [name=Shelling F]

> progress bar: merged issues / issues belongs to a milestone
> [name=Shelling F]

> 柯P 新政三十項，就三十條 progress bars
> [name=Shelling F]


> 補你的想法，看你要貼哪或補充都可
> [name=Shelling F]

> github 概念套過來，但是是附加在你的 progress bar 上面的
> [name=Shelling F]

> 也就是說，有個獨立的 progress bar 介面
> [name=Shelling F]


> 吸引人進網站（回答更多問題）：可以特別地去針對某些重要新聞證件，找過去的資料做成比較華麗（？）的燈號問題，然後讓人進來
> [name=Johnson L]


ex: 幼稚園比例，現在跟之前比差多少

新聞: 參考用，但沒有新聞就什麼都沒有
有可能同一件事情，不同新聞渠道來，會讓人有不同的「完成度感受」
\-\-\-\-

這會變成一個超大的問卷有很多題
可以把問卷切割成模塊丟出去，主動把工作分給很多人

\-\-\-

### 收集連任者（胡志強）


2010~2014
### 政見

臺中軟體園區預計102年8月底前全區開發完成，可望吸引80億元投資額，年產值上看150億元，並可創造5000個就業機會
[http://www.nownews.com/n/2012/12/21/350910](http://www.nownews.com/n/2012/12/21/350910)

#### 一日生活圈、六大政策方向、八項系統建設」交通運輸發展主軸

\[Yam 天空部落 2010年10月19日 [http://blog.yam.com/simon821143/article/31743508](http://blog.yam.com/simon821143/article/31743508)\]

2010 - 九大社會福利政策:
1\. 台中縣、市婦女生育每位新生兒補助一萬元。
> 「金額為單胞胎新臺幣ㄧ萬元，雙胞胎新臺幣三萬元，三胞胎以上，每胞胎新臺幣兩萬元。」台中市社會局：[http://www.society.taichung.gov.tw/faq/index-1.asp?Parser=27,8,28,,,,809,15](http://www.society.taichung.gov.tw/faq/index-1.asp?Parser=27,8,28,,,,809,15)
> [name=Johnson L]

2\. 滿六十五歲以上老人，每月一千元免費搭乘公車。
> 「免費乘車額度：每月自動儲值1,000點(山地原住民每月1,500點)」台中市交通局 [http://www.traffic.taichung.gov.tw/content/index.asp?Parser=1,7,183,52](http://www.traffic.taichung.gov.tw/content/index.asp?Parser=1,7,183,52)
> [name=Johnson L]

3\. 提供一百輛以上的小型復康巴士供民眾使用。
4\. 放重陽敬老禮金一千六千元。
5\. 大台中市區轉車八公里內刷卡免費。
6\. 台中縣、市民共同享受免費搭捷運公車，讓兩個縣市的民眾來往更方便。
7\. 守望相助隊每隊每年編五十四萬元工作費。
8\. 原住民就讀公立學校每學期補助八千五百元，就讀私校補助一萬元。
9\. 提高國小教師員額，由每班平均一點五人，增加到一點七人，並增加教學設備費與校舍修繕費。預計可增加一千四百多位教師名額，紓解「流浪教師」的出路問題，讓小學生的受教權更受重視。
[http://www.nownews.com/n/2010/07/27/654760](http://www.nownews.com/n/2010/07/27/654760)

八項系統建設包括：
「一轉」: 建構一座世界級的**國際經貿客運城**，整合國道客運及中部地區公路客運之轉運功能，設置**國道客運轉運中心**、**車輛研發中心**、**車輛維修產業中心**及**中台灣客運派遣中心**等。

「雙港」：以台中港及台中清泉崗國際機場為基礎，擴大自由貿易區(Free Trade Zone)，配合境外航運中心轉運功能的連結，設置兩岸直航及亞太地區的海空雙星自由貿易港區。

「三鐵」: 台鐵台中都會區鐵路高架路段，由大慶延伸至烏日。台鐵縱貫線(海線)全面雙軌高架化，開闢台鐵「豐原-東勢」支線。另外配合高鐵、捷運系統，形成三鐵交織的路網，使大台中的交通升級。

「四纜」:結合各地遊憩景點，規劃興建「谷關-大雪山」、「大坑-新社」、「石岡(情人木橋-五福臨門)」纜車，並評估中橫「棃山客貨纜車」，帶動地區繁榮，發展地方觀光產業。

「五馬」: 推動大台中自行車道雙環計畫及英雄鐵馬道計畫，串聯現有約262公里的縣市自行車路線。並評估建構500公里通勤型與休閒型自行車道，同時推動自行車租借示範計畫。

「六線」:民國100年將新增「山、海、環」四條免費TTJ捷運公車路線。搭乘基本里程8公里範圍內的市公車均免費，這項措施將約有90%的旅次可享受免付費的優惠;在此同時，將建構六條主要軸線的幹線公車，確保尖峰時段內，每5~10分鐘即有一班車。
\-\-\-
六條路線或計畫：

l. TTJ和平山線(和平-東勢-石岡-豐原-神岡)

2\. TTJ新社山線(新社-東勢-石岡-豐原-神岡)

3\. TTJ海環線(大甲-清水-沙鹿-龍井)

4\. TTJ豐安線(豐原-后里-外埔-大甲-大安)

5\. TTJ市區公車拓展計畫

6\. BRT中港線公車捷運計畫
\-\-\-
「七捷」則是串聯整個大台中的快速軌道系統，也是最重要的交通建設計畫，包括捷運紅線、橘線、黃線、綠線、藍線、棕線、紫線七條線路個軌道系統完工後，大台中各鄉鎮將緊密聯結在一起，共同朝向國際之都發展。

\-\-\-\-
胡志強表示，在大眾運輸方面，將提高大眾運輸系統服務品質，讓運輸系統的時間及空間無縫接軌，提升民眾的使用意願，同時擴大民眾運輸系統服務範圍，並讓費率合理化，提高整體大眾運輸使用比例，降低私有機動車輛的使用。

低碳環保方面─以台中機場、台中港及高鐵烏日站與台鐵台中站為國內外旅遊節點，在各節點提供完整、多元的綠色交通方案，以達到低碳運輸的目標。並拓展區域內各大公園、風景區、與生態觀光區的自行車道路網，提供給外來旅客與區域內市民可以悠閒地騎著自行車遊憩在大自然風景中。

國際競爭方面─大台中區域具有交通中心與國際海空港的條件，可據此將台灣各地與大台中區域內「科技走廊」─中部科學園區、精密機械園區等所生產之貨物，運送至大陸、東南亞、東北亞等世界各地，使大台中成為台灣鏈結兩岸與世界各地的樞紐，增加大台中區域內產業發展的國際競爭力。

多核心發展方面─將建構大台中便捷的公路與軌道系統，搭配高水準的公車服務，快速輸運人流、物流，發揮區域產業特色，創造多核心且城鄉均衡發展的大台中。

安全第一方面─交通設施的設計均以安全為第一優先，透過五個E（Education教育, Engineering工程, Enforcement執法, Encouragement鼓勵, Evaluation評估)，改善交通設施，建構更安全的交通環境。

「八聯」則為打通省道、縣道與國道，讓向內、聯外道路均四通八達，提供地方民眾更便捷的交通網路。計畫內容包括：完成國道4號豐原-潭子段、國道清泉崗機場支線、國道１號中彰系統交流道、國道3號大甲高架快速聯絡道路、國道4號豐原東勢快速道路、提供潭子地區快速進出國4之嘉仁聯絡道、生活圈2號線(環中路)全線高架化、生活圈4號線、生活圈5號線、生活圈4號線大里聯絡道、生活圈4號線大肚延伸段、港區聯外道路、特三號道路港區延伸段、台17(國4~港區)高架快速道路、國際機場走廊站前綠園道、中科北(東、西)向聯外道路、 60米 高鐵門戶綠園道工程、拓寬縣道129號（大坑~新社~東勢）段、 30米-37道路新建工程(生活圈4號線-大慶車站)


### 政見新聞

「一轉」
- 2014 年：[原訂10月啟用 台中水湳轉運站還未動工](http://news.ltn.com.tw/news/local/paper/816144)   『水湳經貿園區的簡易轉運站，市府原本宣稱今年十月完工啟用，但現場仍是「一片雜草」；林良泰回應時表示，目前已找到建築師，都市設計審議中，但由於預算、設計都在「檢討」中，因此「還沒有動工」。』

「雙港」
- 2013 年：[斥資近39億 清泉崗機場 國際航廈啟用](https://tw.news.yahoo.com/%E6%96%A5%E8%B3%87%E8%BF%9139%E5%84%84-%E6%B8%85%E6%B3%89%E5%B4%97%E6%A9%9F%E5%A0%B4-%E5%9C%8B%E9%9A%9B%E8%88%AA%E5%BB%88%E5%95%9F%E7%94%A8-004224179.html) ：沒有提到自貿港區，只是蓋了新航廈

「三鐵」
- 2012 [鐵路高架化只到「大慶站」　顏清標要市府舉行協調會](https://tw.news.yahoo.com/%E9%90%B5%E8%B7%AF%E9%AB%98%E6%9E%B6%E5%8C%96%E5%8F%AA%E5%88%B0-%E5%A4%A7%E6%85%B6%E7%AB%99-%E9%A1%8F%E6%B8%85%E6%A8%99%E8%A6%81%E5%B8%82%E5%BA%9C%E8%88%89%E8%A1%8C%E5%8D%94%E8%AA%BF%E6%9C%83-135323842.html) 鐵路高架化只到台中大慶站，引起烏日居民不滿，立法委員顏清標9日上午要求交通部、鐵路局、市府交通局人員在烏日區公所舉行協調會，地方砲聲隆隆

「四纜」
- 2011 [台中纜車 大坑等4線規劃興建拼觀光／興建一條六年 支票恐跳票](http://ea00336.pixnet.net/blog/post/26237956) : 觀光旅遊局長: 已展開大坑─新社、谷關─大雪山、谷關─梨山、石岡情人橋─五福臨門四條纜車評估規畫案
- 2012-2 [新社大坑纜車 空中地面併行](http://www.appledaily.com.tw/appledaily/article/headline/20120217/34030834/) ：台中市新社至大坑（簡稱新大線）以及大雪山到谷關（簡稱雪谷線）兩條纜車路線終於定案，已有兩、三家廠商透露出承包意願
- 2014-3 [建雪谷線纜車 環團反對](http://news.ltn.com.tw/news/life/paper/760399) : 環保團體質疑：「蓋纜車為虛、蓋旅館才是實。」日後業者大興土木，恐衝擊山林。
- 2014-10 [台中雪谷線及新大線空中纜車，招商啟動](http://goo.gl/pQLTFS)

「五馬」
- 2012 議員何敏誠昨天批評，光是評估建構五百公里通勤型及休閒型自行車道，同時推動「自行車租借示範計畫」就「跳票」，低碳城市是空談。\[[說到做不到 胡自行車道政見跳票](https://tw.news.yahoo.com/%E8%AA%AA%E5%88%B0%E5%81%9A%E4%B8%8D%E5%88%B0-%E8%83%A1%E8%87%AA%E8%A1%8C%E8%BB%8A%E9%81%93%E6%94%BF%E8%A6%8B%E8%B7%B3%E7%A5%A8-202900033.html)  自由時報 2012年10月25日 上午4:29\]
- 2014-7 [台中iBike上路 年底前設20站](http://www.chinatimes.com/newspapers/20140719000119-260210) : iBike已在台灣大道市政大樓、秋紅谷、逢甲大學設置3處示範站，提供100輛公共自行車

「六線」
- 2010-12 [滿城ＴＴＪ？政見跳票 元旦起要付錢](https://tw.news.yahoo.com/%E6%BB%BF%E5%9F%8E-%E6%94%BF%E8%A6%8B%E8%B7%B3%E7%A5%A8-%E5%85%83%E6%97%A6%E8%B5%B7%E8%A6%81%E4%BB%98%E9%8C%A2-20101229-120101-432.html) : 元旦起將有七條路廊幹線公車啟動，包括五十路大里霧峰幹線（統聯）、五十一路太平幹線（豐原客運）、五十三路文心幹線（統聯）、五十四路黎明幹線（和欣）、五十五路潭子豐原幹線（豐原客運）、五十六路五權幹線（統聯）、五十八路崇德幹線（全航）。在相關預算尚未通過的情況下，這七條路線將依一般市公車的票價收費。
- 2011-1 [4客運線先延駛 台中幹線公車 8公里內免費](http://www.appledaily.com.tw/appledaily/article/headline/20110130/33151019/)：4條全日免費TTJ捷運公車，預定7月上路
- 2013 [90、91、92免費公車恢復收費公告](http://www.fybus.com.tw/data/city/90.htm) (和平山環線)
- 2014 [臺中BRT藍線7月27日中午起開放搭乘](http://www.traffic.taichung.gov.tw/news/index-1.asp?Parser=9,4,20,,,,2949) 臺中BRT藍線7月27日中午起開放自由搭乘，中午12點起從臺中火車站、靜宜大學雙向發車，之後每6分鐘一班車
- 2014-8 [胡志強稍微胖了：捷運跳票後派 BRT 上火線，但市民不領情](http://buzzorange.com/2014/08/08/see-taichung-mayor-performance-brt/)

「七捷」
- 2014 中時 [台中捷運綠線車廂 即起體驗搭乘](http://www.chinatimes.com/realtimenews/20141109002162-260405)：即日起至12月7日每天下午2點至晚上8點，在臺灣大道市政大樓惠中樓旁開放參觀

「八聯」
- 2014 [國4豐原潭子段 110年可望通車](https://tw.news.yahoo.com/%E5%9C%8B4%E8%B1%90%E5%8E%9F%E6%BD%AD%E5%AD%90%E6%AE%B5-110%E5%B9%B4%E5%8F%AF%E6%9C%9B%E9%80%9A%E8%BB%8A-092502531.html)：大台中高快速公路網「最後一塊拼圖」國道4號豐原潭子段有進展，交通部國工局明年初起準備動工，預估110年上半年可通車。


### 問卷鏈結

 燈號版：[https://mrorz.typeform.com/to/rWC2KR](https://mrorz.typeform.com/to/rWC2KR)
 Progress 版：[https://mrorz.typeform.com/to/OwHBc3](https://mrorz.typeform.com/to/OwHBc3)




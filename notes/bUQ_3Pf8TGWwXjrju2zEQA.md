---
title: "護病比查詢"
tags: hackpad
---

# 護病比查詢

> [點此觀看原始內容](https://g0v.hackpad.tw/L4KNanSM67U)

> 跪謝Yutin、Ben、If、邵楷等等等的討論，專案：cc-by 4.0
> [name=羅佩琪]


## 目前成果


網址：[https://g0v.github.io/npratio](https://g0v.github.io/npratio/)[/](https://g0v.github.io/npratio/)
原始碼：[https://github.com/g0v/npratio](https://github.com/g0v/npratio)


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5ce6f605c60af76e405e6a3c0bf282ae)


## 資料來源

- ==專案英文名稱：nurse patient ratio==

> to yutin →→ 這樣名字會太長嗎Q____Q
> [name=羅佩琪]

> npratio
> [name=劉宇庭]


- ==csv：====[https://drive.google.com/open?id=0B8FUkAVQF5YGaVJCVGV5d2RQNGM](https://drive.google.com/open?id=0B8FUkAVQF5YGaVJCVGV5d2RQNGM)==
- github：[https://github.com/g0v/npratio.git](https://github.com/g0v/npratio.git)
- 目前資料：[LINK](https://docs.google.com/spreadsheets/d/18MYhOb2_FcfhAGwR6eS6xnb8mtn6JDDcbn5njs5fL34/edit?usp=sharing)

- 各醫院護病比open data：[LINK](http://data.nhi.gov.tw/Datasets/DatasetDetail.aspx?id=440&Mid=A110908) (每季公開，有院所代碼)
- 健保特約醫療院所名冊壓縮檔：[LINK](http://www.nhi.gov.tw/webdata/webdata.aspx?menu=18&menu_id=703&webdata_id=660) (尚非open data，有院所代碼 & 醫院地址電話)


## 護病比計算方式

- 資料來源：健保署健保資訊網服務系統(VPN)醫院依醫院評鑑基準公式自行填報資料（資料下載日期：105年7月21日）=> ==資料是醫院自填申報的==

- 註1：醫院評鑑護病比公式：醫院該月每一個病房之(急性一般病床床位數×佔床率×3)加總後÷每月每日平均上班護理人員數之三班小計加總。

- 註2：全日平均護病比為各醫院急性一般、經濟病床（含精神病床）之統計數據，四捨五入至小數位第一位。

- 註3：本表依各層級按各醫院104年加成率11%之月數高低排序，月數相同者，以12月護病比由低至高排序。另區域醫院、地區醫院以104年12月占床率>=70%(區域)、65%(地區)列計(部分地區醫院因占床率較低，護病比值極低)。

> 有看到的問題是，有護理人員反映不應該算入阿長~
> [name=羅佩琪]



## 想做什麼

- [LINK](https://docs.google.com/presentation/d/16uIG6bk6hhLJzD4zr2Isc42zI_A2FyjqSGWQjHct-34/edit?usp=sharing)：想做一個「key醫院名字」就可以查詢的平台【[LINK](https://s.e2d3.org/4790eb3/44136fa/fb969ba5a3ee5f1574325bf324ca089f)】


## ==未來可以加入的功能 (TO DO)==

- 網站要有標題《護病比查詢器》、說明文字
> 加上了簡單的標題與說明。
> [name=邦皓 劉]

- 醫院間的比較
> 會需要設計比較多數個醫院的UI
> [name=邦皓 劉]

    - 針對類型/地區進行 分類/比較
- 有沒有更久的資料，可以做趨勢分析
- 可以加針對這個醫院狀況的留言
- 介面優化

### 看到資料想到的問題：

- 直接取全國平均真的沒問題嗎，有沒有更適當的比較方法？
> \[From Slack\] [clkao](https://g0v-tw.slack.com/team/clkao)  [_\[_](https://g0v-tw.slack.com/archives/general/p1470537296001540)10:34 AM_\]_ yutin: 平均是直接把數值平均嗎？因為醫院權重不同 應該是要找到他原始的三班數數量 分別乘回去再一起當分母
> [name=邦皓 劉]


## ==放網站上的反映管道==


橫軸是月份，縱軸就是傳說中的「護病比」！也就是「一個護理人員要照顧幾個病人」，數字越高越血汗。

如果你覺得某家醫院的數字「是假的！」，可以試試看：〈盡量附上相關事證依據喔！〉

找政府！寫信到衛福部健保署署長信箱：
[http://opinion.nhi.gov.tw/iftpa/PA01T02.php](http://opinion.nhi.gov.tw/iftpa/PA01T02.php)

找醫勞盟！傳訊息給醫勞盟粉絲團：
[https://www.facebook.com/TMAL119/?fref=ts](https://www.facebook.com/TMAL119/?fref=ts)

找民代！從立委咖電喂找立委反映：
[https://docs.google.com/spreadsheets/d/17hkvPVgqW06rO7TQMQGgIpJMiJ4QTiGQXGDzoNXGjKE/edit#gid=0](https://docs.google.com/spreadsheets/d/17hkvPVgqW06rO7TQMQGgIpJMiJ4QTiGQXGDzoNXGjKE/edit#gid=0)


## ==FB文案==


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6635e1f5c6c93ae5d15bd6b579c3ab3f)


【護病比查詢器】哪家醫院的護理人員最血汗！

gov衛福部最近開始按季公開各醫院的「護病比」(護理血汗指數)，g0v社群把這些數字做成了「護病比查詢器」，來瞧瞧不同醫院中、一個護理人員分別要照顧多少病人？

網址：[https://g0v.github.io/npratio/](https://g0v.github.io/npratio/)
原始碼：[https://github.com/g0v/npratio](https://github.com/g0v/npratio)

_:emoji_1f3e5:_ 如果你是一般民眾：來查查你常去的醫院的護理血汗指數！

_:emoji_1f3e5:_ 如果你是護理人員：趕快來看看你家醫院申報出來的資料，是不是真的？還是其實是「假的！」~

\[使用指南\]

Step ① 打上你想查詢的醫院名稱。
Step ② 瞧瞧這家的護病比，護理人員有多辛苦。
Step ③ 如果你是護理人員，跟衛福部、醫勞盟等單位反映：你家護病比數字「是假的」！

\[延伸閱讀\]

護病比是什麼↓↓
[https://goo.gl/uuwVZs](https://goo.gl/uuwVZs)

官方新聞稿 & 護病比開放資料 (計算公式)
[http://goo.gl/GtfejG](http://goo.gl/GtfejG) / [http://goo.gl/Wk1rUv](http://goo.gl/Wk1rUv)


==========================================================




(延伸閱讀)
- 護病比是什麼？

- 如果我發現我的醫院申報的護病比跟現實狀況差很大，怎麼辦？
    - 連到立委咖電委專案？(連到醫院所在地區的立委的資料？)
    - 連到健保署署長信箱？
    - 附上健保免付費專線？
    - 給醫勞盟






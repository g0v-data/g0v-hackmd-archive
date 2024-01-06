---
title: "動民主 - 真度計"
tags: 動民主,hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/lzGKZQAwe7e)


## 專案簡介

### 專案說明

    希望可以讓平常比較少參與政治的公民，
    也可以在投票前夕，很快地看出來，
    哪些候選人開的政見比較有機會跳票。

**發起人/拋磚人**：
    動民主家族裡的某個人…？
    是在 [2.0 app a.k.a. 1.337](https://g0v.hackpad.tw/iBRhXaRlfZh) 裡看到的XD

### 相關專案：


- 選舉黃頁
> [http://k.olc.tw/2014/07/%E9%81%B8%E8%88%89%E9%BB%83%E9%A0%81%E4%B8%8A%E7%B7%9A%EF%BC%8C%E9%82%80%E8%AB%8B%E5%A4%A7%E5%AE%B6%E4%B8%80%E8%B5%B7%E4%BE%86%E5%8F%83%E9%81%B8%EF%BC%81/](http://k.olc.tw/2014/07/%E9%81%B8%E8%88%89%E9%BB%83%E9%A0%81%E4%B8%8A%E7%B7%9A%EF%BC%8C%E9%82%80%E8%AB%8B%E5%A4%A7%E5%AE%B6%E4%B8%80%E8%B5%B7%E4%BE%86%E5%8F%83%E9%81%B8%EF%BC%81/)
> [name=Bestian T]



## 目標與功能（要如何解決）

### 預定功能

- 把現在舉辦的選舉裡的候選人，仔細挑出來，
    檢視他們之前參選時，都提了什麼政見，
    如果有當選，那就要一項一項看他們施政的成績如何。
- ~一個人的每項政見，這裡都會跟著一串新聞，每一則新聞都可以讓大家評論，~
    ~是正向的新聞 (有在認真做事) 還是負面的新聞 (亂做一通) ，~
    ~累積起來，就知道這個人說話有沒有算話。~
    目前是的決定是以客觀事實為基礎，
    所以會調閱與其相關的公文和預算書來看，
    判斷這項政見有沒有實現。
- 在政見和~新聞~相關公文與預算書蒐集和整理這部份，可以半自動地來用爬蟲加上一些人工的處理，
    但是在評論~和正負向~的標註，這就一定要靠群眾來做了。

### 預定使用者

- 平常就有在關心政治的人
    這一群人可以負責對~新聞~公文與預算書做評論~，標註正負向~，
    也可以新增一則新聞到一個政見裡。

- 到投票前一天才會關心要投給誰的人
    可以上來點幾下滑鼠，
    很快就看出來選區裡的候選人，哪一個的鼻子最長。

## 要解決的問題

現有類似專案
（現成的是否可以直接使用？或者有什麼不足之處？國外專案可參考？）
- 候選人政見專案 [https://g0v.hackpad.com/SP93kHqeeFM](https://g0v.hackpad.com/SP93kHqeeFM)
- 歐巴馬真度計 [http://www.politifact.com/truth-o-meter/promises/obameter/](http://www.politifact.com/truth-o-meter/promises/obameter/)
- 觀政見 [http://www.visionplatform.tw/](http://www.visionplatform.tw/)
- 市長，安安，政見給窺嗎？ [http://mayorgame.thenewslens.com/](http://mayorgame.thenewslens.com/)
> 這個遊戲好好玩!!!
> [name=John L]

- 2014 台北市長承諾一覽表 [http://hacktabl.org/taipei-mayoral-election-2014](http://hacktabl.org/taipei-mayoral-election-2014)
- 政見 Pickup [http://vote.kueiapp.com/](http://vote.kueiapp.com/) \- 使用選舉黃頁 api 做的
- 你投哪位候選人？\- [http://topic.cw.com.tw/2014election/index.aspx](http://topic.cw.com.tw/2014election/index.aspx)

相關專案
（衍生自某專案/衍生出某專案/API串接自某專案.）
希望可以有爬新聞的 API …
> 爬新聞可以參考 [https://github.com/ronnywang/newsdiff](https://github.com/ronnywang/newsdiff)
> [name=Finjon K]

> 我在選舉黃頁加了相關新聞([範例](http://k.olc.tw/elections/candidates/view/53c028c2-acf4-43de-9288-5dffacb5b862))，不過礙於著作權關係，只有抓摘要文字，並沒有全文引用
> [name=Finjon K]

> 這個是不是只能爬最新的新聞呢？
> [name=John L]

> 但是我其實比較希望可以爬歷史的新聞，通常新聞網站會把新聞留著這麼久嗎？
> [name=John L]

> 目前只有 201308 到現在的資料，其實那些網站很多舊新聞都會隱藏，需要有特定權限才能夠查詢
> [name=Finjon K]

> 原來如此，不過還是很棒的 data ，謝謝您的資訊!
> [name=John L]


授權方式
（程式碼部分如 MIT/BSD /文件部分，如 CC-BY）
我之前自己都是用 BSD 3-Clause ，但因為還沒有開始寫  ，所以其實都可以XD

使用資料
[http://disa.csie.org:5566/data/](http://disa.csie.org:5566/data/)
> 我也爬了一份 [https://github.com/kiang/db.cec.gov.tw](https://github.com/kiang/db.cec.gov.tw)
> [name=Finjon K]

> 太厲害了XD
> [name=John L]

> 不過您好像沒有加上投票日，可以加在 elections.csv 裡嗎？
> [name=John L]

> 感謝提醒，加進去了
> [name=Finjon K]

> 謝謝您!
> [name=John L]


專案目前狀態
（構想 / 規劃 / 雛形 / 實作）

請見最下面的 "成果展示" 。

## 徵求協作者

發起人/拋磚人：
分工與成員 (請自行填寫)
- [ ] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）：
- [ ] NeedsDesigner: 需要介面設計： bestian
> 如果有gh-page版, 我可以參一腳，可支援一點點SASS
> [name=Bestian T]

> 但現場會議無法參加，僅能非同步協作
> [name=Bestian T]

> 好! 我這個週末就來改成 gh-page 版!!
> [name=John L]

> 謝謝~
> [name=Bestian T]

> 已改成 gh-pages ：
> [name=John L]

> [http://j](http://johnlin.tw/nose-meter/)[o](http://johnlin.tw/nose-meter/)[h](http://johnlin.tw/nose-meter/)[n](http://johnlin.tw/nose-meter/)[l](http://johnlin.tw/nose-meter/)[i](http://johnlin.tw/nose-meter/)[n.t](http://johnlin.tw/nose-meter/)[w](http://johnlin.tw/nose-meter/)[/](http://johnlin.tw/nose-meter/)[n](http://johnlin.tw/nose-meter/)[o](http://johnlin.tw/nose-meter/)[s](http://johnlin.tw/nose-meter/)[e](http://johnlin.tw/nose-meter/)[-](http://johnlin.tw/nose-meter/)[m](http://johnlin.tw/nose-meter/)[e](http://johnlin.tw/nose-meter/)[t](http://johnlin.tw/nose-meter/)[e](http://johnlin.tw/nose-meter/)[r](http://johnlin.tw/nose-meter/)[/](http://johnlin.tw/nose-meter/)
> [name=John L]

> 但是只有做好 AngularJS 的部份，還沒有和 Firebase 連起來…
> [name=John L]

> 已開始修樣式，但無編輯權限，可以開成wiki或是加我進去嗎?
> [name=Bestian T]

> github id: bestian
> [name=Bestian T]

> 已經加您進去了~
> [name=John L]

> 謝謝! 剛push了一筆更新 :+1:
> [name=Bestian T]

> 太好了，我也 push 了一筆更新，把 Firebase 接進來，
> [name=John L]

> 現在可以讓資料可以正常地顯示了。
> [name=John L]

> 不過候選人的頁面的 css 好像壞掉了…
> [name=John L]

> [http://johnlin.tw/nose-meter/candidate.html#游錫堃](http://johnlin.tw/nose-meter/candidate.html#游錫堃)
> [name=John L]

> css資料夾名稱改了一次的關係，忘了把html上的link跟著改，現在修好了
> [name=Bestian T]

> 謝謝您!
> [name=John L]

> 現在想要把 Github 的連結加在首頁裡面，可是不確定要怎麼排版比較好看…
> [name=John L]

> 如果您覺得首頁很難看的話，砍掉重練其實是最好的辦法XD
> [name=John L]

> Github issue 的 link 在這裡：
> [name=John L]

> [averangeall/nose meter#3](https://github.com/averangeall/nose-meter/issues/3)
> [name=John L]


- [ ] NeedsData: 需要資料（擷取、清理）：
- [ ] NeedsTech: 需要技術支援（程式、架站 etc)：
    - [ ] Backend: John
    - [ ] Frontend: John, bestian
> 如果有gh-page版, 我可以參一腳，可支援angularJS,angularFire,angularLeaflet, 一點點Livescript
> [name=Bestian T]

> 但現場會議無法參加，僅能非同步協作
> [name=Bestian T]

> 我對 AngularFire 有一點疑問，我稍微研究一下再請教您好嗎？
> [name=John L]

> 謝謝[這份 Google Doc](http://goo.gl/vJRX1n)!
> [name=Johnson L]

> 其實幾乎都是@小米可整理的，感謝她!
> [name=John L]

> 好，我會的都盡量回答，其他的就再一起學，如果初次用firebase + AngularFire, 可參考最近在匯整的前端學習網中集的firebase官網和angularFire官網：
> [name=Bestian T]

> [http://bestian.github.io/frontend/index.html#bt_frontend&1&28](http://bestian.github.io/frontend/index.html#bt_frontend&1&28)
> [name=Bestian T]

> [http://bestian.github.io/frontend/index.html#bt_frontend&1&29](http://bestian.github.io/frontend/index.html#bt_frontend&1&29)
> [name=Bestian T]

> 好的，感謝您~
> [name=John L]

> 我現在想要設計 database ，可是我覺得我設計的會像 relational database 一樣…
> [name=John L]

> 這樣會有什麼缺點嗎？
> [name=John L]

> 就先衝吧？遇到明顯問題再修囉 ;)
> [name=Finjon K]

> 衝!!!
> [name=John L]

- [ ] NeedsProcess: 需要幫忙設計作業流程：
- [ ] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡：edgar

## 實作細節（非技術背景可跳填）

### 協作工具

- github repo：[https://github.com/averangeall/nose-meter](https://github.com/averangeall/nose-meter)
- hackfoldr 工作資料夾網址：N/A
- google drive 共用資料夾網址：N/A

### Todo List

- [ ] 把[曾經當選過的縣市長候選人們](http://disa.csie.org:5566/data/elected/)的政見手動慢慢輸入進去。
    - [x] 優先是把每個人 "最近一次當選" 的政見輸入進去。
    - [ ] 然後再來其他的政見輸進去。
- [ ] 把這次候選人的學經歷整理好，在[這份 Google Doc](http://goo.gl/vJRX1n) 裡。
> 不好意思, 我已經發過request, 但還是沒有這份doc的權限, 麻煩加我: iling.liu@gmail.com  謝謝~
> [name=小米 可]

> 已經加妳了!!
> [name=John L]

> 補上wiki能找到的候選人資料, 另外新增一欄位(參選縣市), 空白的部分要再另外找資料
> [name=小米 可]

> 太猛了… 效率好高XD
> [name=John L]

- [ ] 調閱公文，以評估政見執行程度。
- [ ] 找比較老舊而缺漏的選舉公報。
- [ ] 整理這一屆市長候選人的政見。
- [x] 把 Github 的連結放到[首頁](http://disa.csie.org:5566/)裡。
- [ ] 用 local storage 把選取的縣市存起來，供下一次拜訪網站的時候參考。
- [ ] 針對每一條政見，可以讓大家在留言區進行討論。
- [ ] 尋找預算書的電子檔。
    - 預算彙編 \- [http://www.dgbas.gov.tw/lp.asp?CtNode=4971&CtUnit=756&BaseDSD=7&mp=1](http://www.dgbas.gov.tw/lp.asp?CtNode=4971&CtUnit=756&BaseDSD=7&mp=1)
        - 轉檔： [https://github.com/kiang/dgbas.gov.tw/tree/master/city_budget](https://github.com/kiang/dgbas.gov.tw/tree/master/city_budget)
    - 決算 \- [http://www.audit.gov.tw/files/11-1000-97.php](http://www.audit.gov.tw/files/11-1000-97.php)
        - 備份： [https://github.com/kiang/www.audit.gov.tw/blob/master/budget\_audit\_reports.csv](https://github.com/kiang/www.audit.gov.tw/blob/master/budget_audit_reports.csv)
> 原則上預算會有美化的疑慮，從決算資料比較看得出實際執行情況
> [name=Finjon K]

> 猛... 謝謝您!
> [name=John L]

- [ ] 設計一個真度計的 logo ，還有網頁的 favicon 。

缺漏的選舉公報：
1989 縣市長選舉 - 宜蘭縣 - 縣長
1998 縣市議員選舉 - 桃園縣第 3 選舉區 - 縣議員
1998 縣市議員選舉 - 基隆市第 2 選舉區 - 市議員
1998 縣市議員選舉 - 基隆市第 6 選舉區 - 市議員
1998 縣市議員選舉 - 苗栗縣第 4 選舉區 - 縣議員
1998 縣市議員選舉 - 彰化縣第 1 選舉區 - 縣議員
1998 縣市議員選舉 - 彰化縣第 4 選舉區 - 縣議員
1998 縣市議員選舉 - 屏東縣第 6 選舉區 - 縣議員
1998 縣市議員選舉 - 澎湖縣第 1 選舉區 - 縣議員
2002 縣市議員選舉 - 基隆市第 6 選舉區 - 市議員
2002 縣市議員選舉 - 彰化縣第 1 選舉區 - 縣議員
2002 縣市議員選舉 - 南投縣第 3 選舉區 - 縣議員
2002 縣市議員選舉 - 屏東縣第 6 選舉區 - 縣議員
2002 縣市議員選舉 - 澎湖縣第 1 選舉區 - 縣議員
2002 縣市議員選舉 - 金門縣 - 縣議員

## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）


初步構想的 wireframe
[https://docs.google.com/presentation/d/1B3d_9Bh5cXysQUSUKMfDO9z1qF7r6ZmIkhfGQhY4mtc/pub?start=false&loop=false&delayms=3000](https://docs.google.com/presentation/d/1B3d_9Bh5cXysQUSUKMfDO9z1qF7r6ZmIkhfGQhY4mtc/pub?start=false&loop=false&delayms=3000)
> 有，非常有幫助 XDD 內容可以找政治專業的來幫忙想，像是 [Edgar Chan](https://g0v.hackpad.tw/ep/profile/z3zNKW3jeAH)
> [name=ET B]

> 太好了，不知道 [Edgar Chan](https://g0v.hackpad.tw/ep/profile/z3zNKW3jeAH) 願不願意 : ' )
> [name=John L]

> 突然發現被點名！驚！！！那就5/16來討論一下囉。
> [name=Edgar C]

> 太感人了 : ' )
> [name=John L]

> hi~ 我對這個專案很有興趣, 默默follow了一陣子, 但是不知道該怎麼加入 orz
> [name=小米 可]

> 哈囉，目前我們已經有的資料是 "哪些市長候選人之前有當選過公職人員" ，
> [name=John L]

> 還有 "當選的時候他們提了什麼政見" ，
> [name=John L]

> 現在要做的事情是 "調閱出預算書來檢查這些政見有沒有實現" ，
> [name=John L]

> 我們今天晚上七點在慕哲咖啡有要約討論，您有空的話可以一起來~
> [name=John L]

> OK~ 我七點左右下班, 可能要七點半以後才能到
> [name=小米 可]

> 好的，我們就在那裡等你!
> [name=John L]


Database 的 ER Diagram
[https://docs.google.com/draings/d/1EGtlENxrRaW0bpdZnxlqV516nmoz8VtOhoIZpqnrG1Y/edit](https://docs.google.com/draings/d/1EGtlENxrRaW0bpdZnxlqV516nmoz8VtOhoIZpqnrG1Y/edit)

目前~空虛的~已經有一些候選人的基本資料了的首頁
[~http://disa.csie.org:5566/~](http://disa.csie.org:5566/)
- 已移至 Github pages  [http://johnlin.tw/nose-meter/](http://johnlin.tw/nose-meter/)
> 修了一下首頁樣式，希望大家喜歡 :)
> [name=Bestian T]

> 感謝您!!
> [name=John L]



- 展示一下目前有的資料  [http://disa.csie.org:5566/data/](http://disa.csie.org:5566/data/)
> 效率這麼高是什麼妖術？！
> [name=ET B]

> 希望更多人來一起整理，效率會更高!!
> [name=John L]


我把這二十幾年比較大的選舉都爬進 database 裡了，整理成以下：
[http://disa.csie.org:5566/data/elected/](http://disa.csie.org:5566/data/elected/)
可以看現在的候選人們，哪些之前有當過公僕的。
> 這個連結失效囉~ 有其他備份嗎? 候選人學經歷大致完成(剩下找不到資料的, 只好等選舉公報了?)
> [name=小米 可]

> 可以開始來整理候選人之前的政見了
> [name=小米 可]

> 好像一些不明原因而故障了… 剛剛重開一下 server 就可以了。
> [name=John L]

> 政見的話，目前我把裡面每個人最近一次當選的政見都有輸入了，
> [name=John L]

> 您可以檢查看看內容是否有誤。
> [name=John L]


試著用星等來標註政見的完成度：
[http://disa.csie.org:5566/about/stars/](http://disa.csie.org:5566/about/stars/)
不知道適不適合，請各位批評討論。
然後實際上標註出來可能會是像這種感覺：
[http://disa.csie.org:5566/candidate/%E6%B8%B8%E9%8C%AB%E5%A0%83](http://disa.csie.org:5566/candidate/%E6%B8%B8%E9%8C%AB%E5%A0%83)
資料還是半假半真，請大家包涵…
> note一下資料尚待補完如何?
> [name=Bestian T]

> 已補上，謝謝提醒!!
> [name=John L]



### 使用者許願

- 網站或 app 可以一打開就跳出我上次選的地區嗎？就不用重選了 lol
> 應該存一個小 cookie 就可以了XD
> [name=John L]

> 這部分我覺得可以有兩個選項，1.進入上次所選地區；2.選擇其他地區。可能會有人想要有好幾區~XD
> [name=Edgar C]

> 用local storage存起來就行了，html 5中替代cookie的方法
> [name=Bestian T]

> 有道理，可以列到 todo 裡。
> [name=John L]


- 想要好笑的 pk 畫面…… XD
> 我還滿愛畫動畫的，行有餘力可以來畫畫看!!
> [name=John L]



## 討論問與答整理

### 真度計沒約松 2014/10/22

- 要討論的事情
    1.  是否要分別 "空洞的政見" 和 "有具體目標的政見"
        - "空洞的政見" 例子： "推動觀光產業發展，營造休閒願景，打造觀光休閒大縣。"
        - "有具體目標的政見" 例子： "爭取南投市祖師大橋聯絡東草屯交流道之新建工程，成為南投市往來埔里鎮之主要道路。"
        - "虛虛實實的政見" 例子： "打造十八尖山成為藝術森林公園。"
    2.  如果一條政見有好幾個目標，是否要拆開來當成好幾條政見？
        1.  例子： "我們要透過河川水土的全流域整治、防災避難體系的整合、均衡的都市發展策略、循環再利用的水利工程、低碳生活空間與綠色交通網的建構，來實現環境永續的生態高雄。"
    - 尋求議員幫忙調公文與預算書
    - 請 edgar 找人來教大家怎麼看懂預算書
> [https://www.facebook.com/groups/openbudget/](https://www.facebook.com/groups/openbudget/) 這兒有些相關討論與資料、活動的連結 ;)
> [name=Finjon K]

> 糟了… 我沒有臉書的帳號，請問一定要有帳號才可以看嗎？
> [name=John L]

> 我借到一個免洗帳號來看了XD 但我沒有找到類似 "笨蛋也看得懂預算書" 的文章…
> [name=John L]

> 基本上預算書還是需要一些經驗才看得出眉腳，我也是霧裡看花 XD
> [name=Finjon K]



### 真度計沒約松 2014/10/1


- 候選人資料確認，學歷、經歷必填項目． 資料彙整：[http://goo.gl/vJRX1n](http://goo.gl/vJRX1n)
- 政見整理（將講故事的政見條列化）．
- 政見執行程度，上回討論以公文書為依據，edgar協助確認公文書調閱事宜．
- 找比較老舊的市議員選舉公報 （在 [http://disa.csie.org:5566/data/elected/](http://disa.csie.org:5566/data/elected/) 裡有標註星號為缺少待補  ）
> 村長說這個 [http://logbot.g0v.tw/channel/g0v.tw/2014-10-04/33](http://logbot.g0v.tw/channel/g0v.tw/2014-10-04/33) 我看不懂...
> [name=ET B]

> 是我 code 寫爛了… 已修好…
> [name=John L]

- 把[顯示政見的頁面](http://disa.csie.org:5566/candidate/%E6%B8%B8%E9%8C%AB%E5%A0%83)分層，看起來比較清楚。
- 放進這一屆競選的政見。
- 加入 tag 的功能。

> 樓上捧由記得報名 g0v summit 第二天 unconf，跟第一天是分開的喔！想說要不要在 unconf 弄一個動民主 track [http://g0v-tw.kktix.cc/events/g0v-summit-2014-unconf](http://g0v-tw.kktix.cc/events/g0v-summit-2014-unconf) XD
> [name=ET B]

> 糟糕，沒票了… 第一次聽說 unconference 這種東西，好酷XD
> [name=John L]

> 然後動民主 track 不錯耶!
> [name=John L]

> 沒票了+1
> [name=Bestian T]

> 發現新網站觀政見：[http://www.visionplatform.tw/](http://www.visionplatform.tw/)，收集各縣市長候選人的政見，感覺有合作的可能性．
> [name=Edgar C]

> 我也是前幾天看到的，覺得他們微量捐款的方法很酷!!
> [name=John L]


### 動民主松 2014/5/16


Q: 要選哪些政見放進來？
A: 以縣市議員為例，政見主要有這幾個來源：
    1.  選舉公報、媒體報導
    2.  演講場（造勢活動），自己辦的場子，在不同地區會有不同政見。
    3.  各類團體活動，針對不同團體提出相關政見。
    4.  選民聚會（廟口泡茶、公園拜訪或三五人小型聚會），交際應酬的談話。
其中 a 與 b 一般民眾要幫忙比較方便判斷，而 c 與 d 必須有當地或該團體的人才能夠收集到。此外，應該要設計 Double Check 機制，避免重複、亂入的情形。



_政見來源會有幾個：_
_選舉公報、媒體報導---如果找各縣市的民眾去採訪候選人，讓g0v做媒體，這樣可行嗎?_

> 有引用出處，非原創即可吧，像維基百科那樣
> [name=Bestian T]



Q: 怎麼判定一個政見有沒有實現？
A: 例如蔡正元立委說要把松山機場拉到外海，然後黨內有提案被擋，應該還是不算完成，但至少一開始有做。我希望在真度計裡是看得出來 "完全沒做" 、 "只有剛當選時有在做" 、 "一直都在努力做" 這三個的差別。
絕對不能像研考會一樣，只要有上公文都算完成，就會變成[馬英九 97% 政見完成率](http://www.cna.com.tw/news/aipl/201401150182-1.aspx)。

> 政見即使完成，不一定對人民有益，比方說都更? 是否可以加一個人民對此政見最後完成結果的簡單表態功能?
> [name=Bestian T]

> 我的確想要一個簡單的留言功能，但又不想要臉書的留言，請問有什麼好辦法嗎？
> [name=John L]

> 可以用 [http://vanillaforums.org/](http://vanillaforums.org/) ，目前選舉黃頁就是用它的嵌入功能為每個候選人設置留言板
> [name=Finjon K]

> 謝謝 [Finjon Kiang](https://g0v.hackpad.tw/ep/profile/G4yGGowBe3x) ，可是它好像是給 PHP 用的，還是其實 Django 也可以用呢？
> [name=John L]

> 程式是 PHP ，但只要設定好再於指定頁面嵌入 js code 就可以了，可以參考選舉黃頁個別候選人頁面的原始碼，就 <div id="vanilla-comments"></div> 跟後面那一段 js code 即可
> [name=Finjon K]


> 如果是需login的留言，一個簡單的辦法是用hackpad > pad setting > embad > Editable Hackpad
> [name=Bestian T]

> 謝謝兩位，我來研究看看!
> [name=John L]




Q: 政策和政見的關係是什麼？
A: 政見，你就想像是執政者提出來的 "戰略" ，執政後我就會要我的管轄群提出各種政策 (戰術) 。用經濟政策來說，我要完成 633 這個政見的話，我就要進行甲、乙、丙這些政策，讓 633 可以呈現。
"政見"是計畫與承諾。"政策"是執行的方法。

Q: 一條政策是怎麼擬定出來的？
A: 政策擬定本身有幾個特質 ，而且很多不是獨立，是連動的：
    1.  事務官擬定：事務官在其自身專業範圍內想要推動的政策。
    2.  團體或請願：通常見於團體或一些人民請願案。
    3.  執政者的提案：依照政黨或執政者個意識進行提案或施行。
    4.  創制：目前台灣還是沒有辦法做這件事情的案例。


Q: 目前台灣的政策提出以及陳列方法的問題有哪些？
A: 從 a0kman 的說明裡，整理出這幾點：
    1.  執政者或黨擺上去的政務官，以及而政務官指派單位的局、所長是否適任。
    2.  政務官過度凌駕事務官。

Q: 英國的文官長制度是怎麼回事呢？
A: 政務官提出需求之後，各相關單位的事務官則研擬各種可能政策，供政務官去選。
這樣子做，不僅可以篩選掉一些過度偏激的政策，更可以讓全民看到各種的考量變化，這樣之後因為施政後可能帶來的變化也有可能比較容易接受。或許也可以讓一些團體或小黨提出來的法案更容易被看見也更容易被一些大一點的政黨或團體接納或吸納。

_以上只是簡單的整理，如果想看完整討論在這裡：_
[https://g0v.hackpad.com/ur06eAVZRGo#:h=2014/5/16-(併啥密松](https://g0v.hackpad.com/ur06eAVZRGo#:h=2014/5/16-(併啥密松))





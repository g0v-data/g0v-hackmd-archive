---
title: "客廳工廠黑客松專案構想（Idea Pool）"
tags: hackpad
---

# 客廳工廠黑客松專案構想（Idea Pool）

> [點此觀看原始內容](https://g0v.hackpad.tw/ZhayTz2Om0n_2dDsvCQu1g8)

> ~6/8-8/10之間想到的提案都在這裡寫吧~
> [name=ipa c]

> 已經有國民大會黑客松構想，請前往 [Idea Pool](https://g0v.hackpad.tw/d3UYGxZtxw2)
> [name=nchild]


### 如果你有一個概略的想法，請直接加在這裡。


如果你想把這邊的想法變得更完整，請用 g0v.hackpad.com 或者 google doc，新增一份文件，然後把它加入 [https://ethercalc.org/g0v-hackath3n](https://ethercalc.org/g0v-hackath3n) 最後一行 (url 前面請空一格 以便縮排)

 說明：
\- 授權方式：程式碼部分（如 MIT/BSD）、文件部分（如 CC-BY）
\- 需求：NeedTech, NeedDesign, NeedWriter, NeedTalktoRealPerson （可加
在 ethercalc 中第三欄）

請幫忙從之前 hackathon 文件回收 Idea：
[第零次](https://hackpad.com/ul6fMthof2S)
[第壹次](https://hackpad.com/lIoCjaeMWzC)
[第貳次](http://hack.g0v.tw/#/g0v-hackath2n/1qotCK6_ccR3MucEVtTrZ7nKdYXniS7bncZR2Dm85qbQ)
 [pre-hackath3n](https://g0v.hackpad.com/g0v-pre-hackath3n-Y9xV1sIIuTt)

## People Watch


-  民主就是自由，監督就是和平，知識就是力量
- 一個用來即時反映民意的應用，並且提供歷史紀錄，不讓媒體與政府造成的失憶症繼續猖狂
- 工作目標：
    - 介接新聞動態、立法院公報與使用者分享的資訊，讓使用者所關心的政黨、立委、議員等做了什麼事、講了什麼話可以被即時的監督
        - 不過立院公報雖然有前輩的努力，要接上應用看起來還需要做不少工作，因此會先用 dummy data
        - 新聞動態則是取決於是否有可用的新聞 API
    -  前述的每個動態都可以被轉發、評論。並且以相關的功能，讓使用者表達基於這則動態，對該政黨、民意代表的立場
        - 只有支持、反對與「不表示支持」三種立場，沒有所謂的中立這回事
        - 不是表達僅針對該事件使用者的立場，是改變或維持使用者對該政治對象的整體立場
        - 歷史紀錄是重點：使用者可以在選舉投票前，檢查自己曾經因各事件所表示過的立場
    - 另外有功能是可以反映使用者的意見，並統計起來的功能
- 目前進度
    - 已經有幾個重要的 API 規格確定，並在設計實作中
        - 目前有修訂中的 [API 規格](https://docs.google.com/spreadsheet/ccc?key=0AjqwG7n2gs71dEZibjZkQmZKUFM5RXdrVVBGcmJ2U3c&usp=sharing)跟[草圖](https://cacoo.com/diagrams/rmqQe2ZZenRKC6NW)
    - 前端的介面目前使用 HTML5 先刻加快速度。再評估移到 Android 或 iPhone 上效能等會不會需要重新以原生功能重做
    - 後端使用 GAE，不過目前先不 deploy 而是使用 local 版開發
    - 目前已經有前端的部份功能 (函式等級) 可以使用
- 授權：GPLv3
-  目前人力狀況與徵求伙伴
    - 目前已經有前後端開發者各一
    - 需要有了解新聞 API 與立院公報剖析、文字處理的伙伴，可以加速與增強整個計畫
    - 如果 HTML5 應用還是不適合，需要有原生應用的開發者
- 目前有思考到可能的營運模式，如果這個概念可以成長茁壯也許可能成為社會企業



## 施壓立委 & 立委態度意向揭露


- 專案簡介：化憤怒為施壓行動
- 工作目標：
    - 說明： 發想源自 hlb [抗議台版 sopa 頁面](http://g0v.github.io/stop-taiwan-sopa/#)，議題簡單說明之後有 do something 和 i don't care 按鈕。延伸出去可做成以下方案，日後不同議題能重複利用：
    - do something 頁面
        - 方案一 施壓立委專頁：用 [http://gcaa.oRg.tw/callnow](http://gcaa.oRg.tw/callnow) 改一個版本
> 新版 html / css / js 在此 [http://etblue.github.io/rwd/](http://etblue.github.io/rwd/) （尚未套資料）
> [name=ET B]

> 新版 html / css / js 原始碼 [https://github.com/ETBlue/rwd](https://github.com/ETBlue/rwd)
> [name=ET B]

        - 方案二 **立委態度意向表**：有一列表顯示立委通訊、立場
> 可參考綠盟的列表 [https://docs.google.com/folder/d/0B0NsS2a-Qx8ZOTJjTkJGckZSWkk/edit?docId=0AkBrSh6Fg50ydDVDYk00MVl2WWpTeTM5MG45WTI2clE](https://docs.google.com/folder/d/0B0NsS2a-Qx8ZOTJjTkJGckZSWkk/edit?docId=0AkBrSh6Fg50ydDVDYk00MVl2WWpTeTM5MG45WTI2clE)
> [name=ET B]

    -  i don't care
        -  方案一：馬囧倒數
        - 方案二：以議題另外發想
- 授權方式：[open source](http://opensource.org/)
- 狀態：雛形、實作
- 徵求夥伴：在有興趣的主題下簽名，並加上希望達成什麼、補充資訊、需要什麼幫忙的 tag
    - NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案 etc）
    - NeedsDesigner: 需要介面設計
    -  NeedsTech: 需要技術支援（程式、架站 etc)

相關資訊 [http://lqfb-test.g0v.tw/g0v/initiative/show/30.html](http://lqfb-test.g0v.tw/g0v/initiative/show/30.html)


##  社會議題懶人包 / 你的懶人包

狀態：構想
（從 irc 抓過來的）
Toby_ 我想作一個自動的社會議題懶人包，大概就是有 spider 會撈特定文章和圖片、有 ranking 機制、做類似 data visualization 的東西，\[01:44\]        Toby_        恩，這個好像是討論導向的，但我比較想做資料整合和視覺化的部份，我想把重點擺在「價值觀祛除」去陳述一個事件每個立場的聲音。
會先設定幾個立場，欸，我想舉例樂生
立場就會分成 政府（行政院、捷運局、地方政府） 、樂生居民、樂青 等等
會按時間序排列抓到的資料，然後按一個指數決定顯示的大小、頻率、重要度等等
也有考慮讓一群管理階層（各立場對事件本身有一定瞭解的特定鄉民）決定立場及一部分的指數
\[01:59\]        clkao        'd love to see a prototype classifying [http://www.news-pac.com/topic?topic=%E6%A8%82%E7%94%9F](http://www.news-pac.com/topic?topic=%E6%A8%82%E7%94%9F)
> 感覺分類、價值觀去除這點，要自動作比較難，因為什麼樣的事情該被稱為「事件」，或是下標題的方式本身，就帶有立場，要自動判斷有點難。要不要是給個懶人包製作平台？讓人類很容易收集網路各方資訊、標出立場，集合成一份文件，讓其他人可以看，之後再來針對懶人包作 tag、ranking、classifying
> [name=Ddio C]

> 公民記者們應該會很需要懶人包產生器... XDDDD
> [name=ET B]

> 可以收集媒體上的相關新聞，依照時間序串起來，再讓鄉民來下 tag，如：事發原因、結果、分析、後續發展、護航文... 等等。
> [name=rad]



## 我的失憶政府

狀態：構想
（也是從 irc 抓過來的）
hlb        今天也有人跟我說
應該可以有個國家 todo list 的頁面
\[13:23\]        才不會事情一直都被新聞洗掉
> 新聞議題的追蹤功能
> [name=ET B]


##  Alternative To 壟不斷，你來亂（名稱暫訂 XD）

狀態：構想
（e.g. 統一）
真實版的 alternativeto.net
 用錢投票，讓世界更美好
 [http://murmur.tw/ronnywang/5312765](http://murmur.tw/ronnywang/5312765) -\[1999 年的千面人事件，統一因中時晚報刊登 7-11 負面消息，因此將中時晚報移到最下層造成銷售量大減，讓中時晚報必需跟統一道歉。從此媒體不太敢再報統一集團的壞話。這次毒澱粉也是一樣，跟義美用過期原料一樣都該被譴責，卻沒見到統一被以相當的力道批評，統一已經是掌握了媒體的巨獸 - murmur.tw\]

統一集團：7-Eleven、星巴克、家樂福、無印良品、Mister Donut、Duskin、Cold stone 等。此外自行創設品牌包括：統一夢時代購物中心、康是美藥妝店、速邁樂加油中心、二十一世紀風味館、統一速邁自販、博客來網路書店、統一渡假村、伊士邦健身俱樂部、統一速達

    ronnywang:
        用整理新聞的? 像統一以前幹過把中時晚報放到最下面和商周下架
    時間軸的呈現方式?
        針對媒體的部份我比較有印象是這兩個，至於食品安全問題的已經有滿多人整理出歷年記錄了。能做的就是盡自己所能抵制所有統一品牌的東西，包括 7-11, 星巴客, Mr.Donuts, 康世美, code stone, 無印良品, 黑貓宅急便, 21 世紀, 家樂福, 統一阪吉, 博客萊...
    ETBlue:
        這樣說來應該要附上統一集團替代品才行
        不吃甜甜圈和冰淇淋可以減肥，不去康是美去屈臣氏，喔喔喔天啊我不知道無印良品也是統一的
        「台灣統一大陸」公司光名稱聽起來是有點威.....
    clkao: alternativeto.net 真實世界版
    Ted: 好奇的是，剛隨機在 alternativeto.net 查看。Ms OneNote and Evernote, 我知道 Evernote 好像不是透過 alternativeto.net, 而是可能透過親朋好友, 或者強勢媒體呢?
    Brecht:
            [Ted Chen](https://g0v.hackpad.tw/ep/profile/-28z7eLyok9kX88BMj09UVM) alternativeto 的使用情境是，我已經知道 A 了，但是因為某些緣故無法用 A，所以希望找替代品 B，因此不管 B 本身是如何由人得知，alternativeto 告知的訊息是 A->B 的關係。也許有人知道 OneNote，也知道 Evernote，但是在心中並沒有建立起這個連結。也有可能他知道很多替代品，但不知道哪個是比較好的選項。
    Ted:
        [Brecht Huang](https://g0v.hackpad.tw/ep/profile/-3yQfXx0dDLq4du9UcOfpRh) 我的意思有點類似 [ET Blue](https://g0v.hackpad.tw/ep/profile/1J58IcIJNw5JiAl9D0Vrqr) 在下面的，社會議題追蹤網，內的註解。【_連 Google Trends 都沒辦法真的找到正在熱議的議題了，所以不可能去除「人」的因素，八卦版之所以能追蹤熱議是"貼、追、推、回、爆、匿、隱、眾"而成 news hub ，沒有人就沒有意義了。 】。好像重點就像賣東西，最後重點還是 Marketi。_
資料：台灣無基改活動：拒買拒吃
[http://gmo.agron.ntu.edu.tw/noGM/no%20GM%20Food-2.htm](http://gmo.agron.ntu.edu.tw/noGM/no%20GM%20Food-2.htm)
\[活動\] 全民合力抵制統一，大家一起來參加 \- 政治社會八卦版 \- WeTalk 時事論壇 - 台灣最大的新聞論壇! [http://www.wetalk.tw/thread-3793-1-1.html](http://www.wetalk.tw/thread-3793-1-1.html)
[每一口都在服毒 請以行動抵制無良企業](http://www.naipo.com/Portals/1/web_tw/Knowledge_Center/Editorial/publish-90.htm)


## 鄉民關心你 @hychen

 狀態：規劃
專案網址: [kuansim ](https://g0v.hackpad.tw/mynkDCEAXgc)

主治鄉民健忘症，讓鄉民能
    - 找對窗口
    - 釐清問題及權責
    - 表達意見或提案
    - 進度追蹤
    - 改善自己生活的環境
        -  e.x 馬的，台灣什麼時候道路可以跟日本一樣平?
        - e.x 馬的, 台灣什麼時侯行人才可以永遠有人行道可走, 說好的騎樓呢?
        - e.x 馬的, 台灣什麼時候屋頂才可以都沒有違建，說好的整齊市容呢?
        - e.x 馬的, 台灣什麼時候......


 成就系統 XD
> 詳細希望！ XDD
> [name=ET B]



##  路見不平

狀態：規劃
- 專案簡介：台北市有路平專案，各地也有種種因政績、或消耗預算需求產生的造橋鋪路行為。從次數看來，我們應該有更便利平穩的行路品質，事實上卻非如此。我希望藉由這個計畫，記錄與顯示地方鋪路、修路的頻率，由此追究包商施工品質，反映地方運量與承載規劃是否得宜，從而了解路平專案實施成效與稅金流向。我們都值得更美好的生活，在路上。
- 工作目標：
    - 找出公部門造橋、鋪路、修路發包記錄，從而統計固定時段（如十年內）分區域的修路頻率
    - 由上述資料統整包商名冊，量化計算後公開於網站，並分享黑名單給公部門
    - 製作連結修路頻率與交通流量比較之地圖
- 授權方式：應該是 [open source](http://opensource.org/) 的吧？
- 使用資料：
- 徵求夥伴：以下統統需要，請在有興趣的主題下自行簽名
    -  NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案 etc）
    - NeedsDesigner: 需要介面設計
    -  NeedsData: 需要資料（擷取、清理）
    - NeedsTech: 需要技術支援（程式、架站 etc)
    - NeedsProcess: 需要幫忙設計作業流程
    -  NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡

## 社會議題追蹤網


發起人： Twitter @yorkxin

-  專案簡介：做一個類似 issue tracker 的系統，來追蹤各種社會議題，避免太多新聞事件導致有些重要的事情被轉移目標（例如林益世貪污案被另一件事給救了）。不過八卦事件原則 上不追蹤（例如某大爺酒駕撞死人），這個系統只整理政治、人權、社會公益等等的事件。
- 工作目標：
    - 請幫忙把各項整理成容易分組進行的小項
- 授權方式：程式：MIT License；內容：CC ? 但引用資料有版權問題
- 狀態：構想
- 徵求夥伴：在有興趣的主題下簽名，並加上希望達成什麼、補充資訊、需要什麼幫忙的 tag
    - NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案 etc）
    - NeedsDesigner: 需要介面設計
    -  NeedsTech: 需要技術支援（程式、架站 etc)
    - NeedsProcess: 需要幫忙設計作業流程

初步的構想是像 Redmine 這種東西，每個議題 (issue) 有自己的頁面，每個議題可以更新當前的狀態，介面像是 Facebook 動態時報，最新的消息放在上面。

議題可以 assign 給負責人，例如智財局要推鎖網法，就把這事 assign 給智財局長。當然系統裡不會內建他的帳號，要找個方法表現出這是他要負責的。 assignee 可以多個人。

更新事件的時候可以設 milestone ，例如林益世貪污案宣判結果出來了，就設一個 milestone。瀏覽 timeline 的時候以 milestone 為主，在 milestone 下面再貼新聞、參考資料、評論等等。

貼新聞或引用他人在 blog / Facebook 的評論，可能會有著作權的問題？當然超連結一定要附上。

更新議題是要手動進行的，若要自動抓新聞的話或許可以接「社會議題懶人包」？ Google 電子快訊？

要維護每個議題也很累的，萬一沒人維護的話漏掉新聞就糟了。或許有些可以讓關心這件事情的人來當志工認養？例如樂生事件，可以請樂生青年的朋友來維護。

要有方法來把熱門事件給放在首頁顯眼的地方。

要開放 API ，讓別的程式可以直接抓到這個網站上的資料，動態時報也可以開放 RSS 。

Q: 這跟「我的失憶政府」、「社會議題懶人包」有點像？就議題追蹤而言也跟「鄉民關心你」有點類似。
> 失憶政府的內容一模一樣，我想直接跟追蹤網合併就好？ XD
> [name=ET B]

> 其實 tracking 的部份從第零次就被提出，不過我覺得可能題目太大，要一次做到一個程度有困難。在想是不是各個 project 先 workout 一兩個 user story，然後看有什麼 common 的東西可以共用，設計 API 來分工。
> [name=Chia-liang K]

> 今天智財局跟國安法的事情讓我想到，需要有某種方式讓大家可以繞過煙幕彈，已經很多次了，之前貪污除罪法案也是在某個煙幕彈之後偷偷通過...
> [name=ET B]

> @Muser @ETBlue 連 Google Trends 都沒辦法真的找到正在熱議的議題了，所以不可能去除「人」的因素，八卦版之所以能追蹤熱議是"貼、追、推、回、爆、匿、隱、眾"而成 news hub ，沒有人就沒有意義了。 digg / reddit / hacknews 與網路殺神可參考
> [name=ET B]

> @ETBlue @Brecht @Muser 這麼說來，其實應該要爬八卦版的熱門文章然後抓出裡面的關鍵字來做長期追蹤，應該比爬傳統媒體所獲得的關鍵字精準的多？XD 這專案的原始構想是幫忙公民建立長期記憶，隨時方便追蹤該議題的後續狀況，免得一個議題炒起來馬上忘了上一個 = =b [https://twitter.com/ETBlue/status/341870184916713472](https://twitter.com/ETBlue/status/341870184916713472)
> [name=ET B]

> 所以，議題炒起來後被遺忘或許是因為【現在有太多議題了】?
> [name=Ted C]

> @Muser @ETBlue 對於社會議題追蹤，我覺得比較好的做法是「如何展示關於這個議題的全面」，可參考 WolframAlpha，情境是：眾人推崇某個條目向上堆疊，閱讀者點開後會有類似樹枝狀\\魚骨圖\\放射圖\\類心智圖 方式顯示這個條目的相關資訊，讓閱讀者一次能綜觀整個議題的全象圖。 [https://twitter.com/Muser/status/341949153305321472](https://twitter.com/Muser/status/341949153305321472)
> [name=ET B]

> @ETBlue @Brecht 想到另一件無關（？）的事情，就是像蘋果資料室那樣，熱議資料紅完爬完以後默默的存起來，平常也許沒人會理他，但一旦出現類似的熱議事件就把資料庫裡的祖宗十八代都一起翻出來 XD [https://twitter.com/ETBlue/status/341922630615568384](https://twitter.com/ETBlue/status/341922630615568384)
> [name=ET B]

> @Muser @ETBlue 參考：[http://www.slideshare.net/denisparra/columbia-qmssnetwork-visualizationtennis](http://www.slideshare.net/denisparra/columbia-qmssnetwork-visualizationtennis) … 這是人際關係圖的研究，但是如果應用在議題上，從連結與反連結去擴展議題面貌或相關性，也可以少很多「相關文章」的區塊，且各方面的聲音都可以被看見。類似 PageRank Maps。 [https://twitter.com/Muser/status/341954861786595328](https://twitter.com/Muser/status/341954861786595328)
> [name=ET B]


##  跑跑跑，向前跑

by [Johnny Sung](https://g0v.hackpad.tw/ep/profile/12HS2pCKS5QlA9uw3DpqSR)
-  專案簡介：
這 idea 是從一個愛慢跑的朋友想到的，他無時無刻都會搜集很多活動資料並且參加
分享其活動照片。
如果有個系統把所有的路跑活動搜集起來，提供一個按鈕輕易加入至 Google 行事曆
甚至把路跑紀錄搜集起來。像是打 Game 一樣，到了一定的里程數還會有額外獎勵及頭像。


- 工作目標：
    - 請幫忙把各項整理成容易分組進行的小項
- 授權方式：[open source](http://opensource.org/)
- 使用資料：
- 狀態：構想

 Brecht：
        目前這裡的資料 ([http://www.taipeimarathon.org.tw/contest.aspx](http://www.taipeimarathon.org.tw/contest.aspx)) 就已經蠻豐富了，也許可以以這裡的資料為底作進一步的應用?

## Taiwan Debt Clock

- 拋磚人：ipa（稅務國債完全不熟，先筆記，有興趣請撿來作）
- 專案簡介：台版國債（可納入 budget.g0v.tw）
- 關鍵字：國債、赤字、預算、債留子孫
- 參考：
    - [http://www.usdebtclock.org/](http://www.usdebtclock.org/) 米國
    - [http://www.linyuda.url.tw/OurDebtU8.htm](http://www.linyuda.url.tw/OurDebtU8.htm) 台版（好像是稅改會做的？）
> 看了一下 html source，數字是寫死的，即使 refresh 也不會變。不確定是不是 daily 改數字。
> [name=Jeff H]

        - 這是[公平稅改聯盟](http://blog.yam.com/fairtax)上的一個 widget - [說明](http://blog.yam.com/fairtax/article/18495233)、[語法](http://blog.yam.com/fairtax/article/18378233)
- 工作目標：
    - 列出希望呈現數據 1\. 國家預算前三名 2. 赤字 3. 稅收 4. 國債（先亂想）
    - 找相關數據
        - [主計處](http://www.dgbas.gov.tw/)\- [政府統計總覽](http://www.dgbas.gov.tw/ct.asp?xItem=13213&CtNode=3504&mp=1) 以及於 [data.gov.tw](http://data.gov.tw/)  開放的[資料](http://data.gov.tw/opendata/orgList?oid=2.16.886.101.20003.20071) 。
        - [\[資料\] 台灣國債鐘記錄](http://huangkai2001.blogspot.tw/2013/01/national-debt-clock.html)
        - [財政部統計處](http://www.mof.gov.tw/mp.asp?mp=62)
        - [財政統計資料庫查詢(系統)](http://web02.mof.gov.tw/njswww/WebProxy.aspx?sys=100&funid=defjspf2)
> 看不懂，不曉得怎麼解讀。:-(
> [name=Jeff H]

> 是這個數字嗎？ \- 選 各級政府歲入歲出淨額 > 預算數 \> 歲出淨額按政事別分：政府別選「總計」，政事別選「債務支出」，按「查詢」可得到 101 年為 143,179 百萬元。
> [name=Jeff H]

- 授權方式：[open source](http://opensource.org/)
- 使用資料：
- 狀態：胡思 ，純粹拋磚
    - 可以做個 numbers.g0v.tw，先從政府已經 open 的資料開始做起，朝向將[政府統計總覽](http://www.dgbas.gov.tw/ct.asp?xItem=13213&CtNode=3504&mp=1) 或類似數字來源，以方便易用的方式「開放」出來。
        - 像 www.usdebtclock.org 的 dashboard 顯示現狀與趨勢
        - 提供分類完善的數字目錄 (directory)
        - 每個數字都應該有相關說明，並有 link 連到原始來源
        - 每個數字都應該有對應的 API 可以供其他專案使用。
- 徵求夥伴：在有興趣的主題下簽名，並加上希望達成什麼、補充資訊、需要什麼幫忙的 tag
    - NeedsDesigner: 需要介面設計
    - NeedsData: budget.g0v.tw資料？
> 除了 data.gov.tw 已經開放的資料以外，也可以按照[政府統計總覽](http://www.dgbas.gov.tw/ct.asp?xItem=13213&CtNode=3504&mp=1) 的目錄，運作要求政府開放更多的資料 (到 data.gov.tw)。這需要人力與時間來推動。
> [name=Jeff H]

    - NeedsTech: 需要技術支援（程式、架站 etc)

## 快速搜尋 uBike 地點

拋磚人：jslee
- 專案簡介：有外國人很喜歡用台北的 uBike 但是很難找到哪裡有 uBike 的資訊
- 討論：目前 android 上好像就有數個，官方版也有。所有還希望能提供哪些目前沒有的服務呢？
- hacking thursday 有位外國朋友做了Android App 「自行車朋友」
> Plus bike friendly routes? 相關新聞：[自行車道標線一市多制 車友抓瞎](http://www.libertytimes.com.tw/2013/new/jul/4/today-taipei4.htm?Slots=TPhoto)
> [name=nchild]

- 工作目標：
    - 建立一個 cross plafrom (ios andorid) 的 app 很簡單成現哪裡有 uBike
-  授權方式：[open source](http://opensource.org/)
- 使用資料：台北 uBike google map 地點
- 狀態：構想
- 徵求夥伴：在有興趣的主題下簽名，並加上希望達成什麼、補充資訊、需要什麼幫忙的 tag
    - NeedsDesigner: 需要介面設計
    - NeedsData: 需要資料（擷取、清理）
    - NeedsTech: 需要技術支援（程式、架站 etc)
    - NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡
    好像已經有了耶
    [http://www.youbike.com.tw/home.php?eng=0](http://www.youbike.com.tw/home.php?eng=0)

## 全民警察廣播電台

拋磚人：＠ymow
- 專案簡介：打電話進去警廣報路況太麻煩了，不如變成Voice Tweeter
- 討論：Voice Twitter其實市場上有不少成功案例，因此我覺得這個是有機會幫助市民更方便的生活與互助，有機會的話希望能變成VoicePTT
- 工作目標：先搶警廣的飯碗(誤)...把Voice Twitter先做出來，讓民眾可以用這個報案，警廣的音樂部分與新聞部分可以用類似Now.In點播的方式(From Youtube or Grooveshark or SoundCloud 等串接，解決Nowin版權問題)，有機會從全民警廣轉形成全民記者或是任何進階版再討論
- 授權方式：[open source](http://opensource.org/)
- 使用資料：目前想到是Waze API跟警廣報案資料[http://rtr.pbs.gov.tw/realtime/RoadAll.php](http://rtr.pbs.gov.tw/realtime/RoadAll.php)
- 狀態：構想
- 徵求夥伴：在有興趣的主題下簽名，並加上希望達成什麼、補充資訊、需要什麼幫忙的 tag
    - NeedsDesigner: 需要介面設計
    - NeedsData: 警廣資料[http://rtr.pbs.gov.tw/realtime/RoadAll.php](http://rtr.pbs.gov.tw/realtime/RoadAll.php)
    - NeedsTech: 需要技術支援（程式、架站 etc)
    - NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡

關係

forward 1 to 1
- used by:
    - message
    - transfer a file

backward 1 to 1
- used by:
    - belongs to
        - a man belongs to a group

2-way 1 to 1

- used by
    - is the same as
        - 台北縣是新北市

forward 1 to many

backward 1 to many

2-way 1 to many

forward many to many

backward many to many

2-way many to many



## 全民警察廣播電台1.0 Citizen Police Radio, CPR

拋磚人：＠ymow
-  專案簡介：打電話進去警廣報路況太麻煩了，不如變成 Voice Tweeter
-  討論：Voice Twitter 其實市場上有不少成功案例，因此我覺得這個是有機會幫助市民更方便的生活與互助，有機會的話希望能變成 VoicePTT
-  工作目標：先搶警廣的飯碗 (誤)... 把 Voice Twitter 先做出來，讓民眾可以用這個報案，警廣的音樂部分與新聞部分可以用類似 Now.In 點播的方式 (From Youtube or Grooveshark or SoundCloud 等串接，解決 Nowin 版權問題)，有機會從全民警廣轉形成全民記者或是任何進階版再討論
- 授權方式：[open source](http://opensource.org/)
- 使用資料：目前想到是 Waze API 跟警廣報案資料 [http://rtr.pbs.gov.tw/realtime/RoadAll.php](http://rtr.pbs.gov.tw/realtime/RoadAll.php)
-  狀態：構想
- 徵求夥伴：在有興趣的主題下簽名，並加上希望達成什麼、補充資訊、需要什麼幫忙的 tag
    - NeedsDesigner: 需要美術套版
    - NeedsBackEnd:messenge delive


## 世界奇觀

![](http://www.hawkaoc.net/bbs/data/attachment/forum/dvbbs/20031071133156749.jpg)
伐木工：
- littleq0903 ([http://about.me/littleq](http://about.me/littleq))
- hychen
- snowmantw

- 專案簡介：~蓋滿 180 天後獲得勝利~ 把大家需要用的共同資料整理成 Graph，讓大家自行取用
- 專案期限：當然是 180 天了
- 工作目標：（分成N階段）
    1.  先用假資料填充，模擬 Graph API 運作情形。
    2.  資料完成結構後再來寫 server
    3.  後端 stream-in 跟前端 stream-out 各 API 討論
    4.  各種權限控管
        1.  stream-out clients: 如何增加 relation, object ;以及如何管理、註冊、刪除 App
        2.  stream-in sources: 如何增加來源，以及來源需要的屬性設定
            1.  例如該來源的資料是 mutable 或 imutable
-  狀態：填充假資料中
- github repo: [https://github.com/g0v/ww-simulation/](https://github.com/g0v/ww-simulation/)
- example api call
    - \[1\] [http://g0v.github.io/ww-simulation/api/1/this](http://g0v.github.io/ww-simulation/api/1/this) (先用 this 代替空白）
    - \[1 -> news\][http://g0v.github.io/ww-simulation/api/1/news](http://g0v.github.io/ww-simulation/api/1/news)
-  徵求夥伴：
    - NeedTxtHacker: 需要 txt hackers 來幫忙填充假資料
    - NeedBackendDeveloper: 幫忙寫 Graph server 的 backend server


## 台灣炒地皮地圖

[https://www.facebook.com/groups/g0v.general/permalink/481399471936464/](https://www.facebook.com/groups/g0v.general/permalink/481399471936464/)
都更+徵收地圖，閒置廠房+閒置土地地圖，住宅區空屋地圖，各種炒地皮因子整合在同一張地圖上，並標出政務官/議員及其親屬名下的土地座落

同場加映：癌症+環境污染地圖
[https://www.facebook.com/groups/g0v.general/permalink/478633568879721/](https://www.facebook.com/groups/g0v.general/permalink/478633568879721/)

## 網路封鎖列表

- 目的：NCC沒有完整揭露鎖網清單，難以監督其言論管制標準。若是透過實測，自動生成列表，若有誤殺狀況，或者其他異常，比較能夠早期發現並反映。
- 功能：
    - 測試對象：從流量排名找URL當成預設清單，也開放user submit疑似遭到封鎖的URL。
    - 測試方式：從位在台灣的幾個不同節點測試是否連得上，並比對海外節點（VPN, VPS, or Tor）。
    - 網頁界面：
        - 列出目前被封鎖網域或網頁。
        - 查詢網站被封鎖的歷史紀錄。
        - 為了評論該網頁是否應該被封鎖，透過proxy或內部cache直接顯示被封鎖內容（有爭議），或者提供google cache, wayback machine之類外部服務的鏈接。
- 工作目標：
    - crawler
    - web front end
- 討論：
    - 如何有效率得知那些網站被封鎖
- 進度：初步想法，還沒有實作
- Ref: [https://hackpad.com/Against-the-Master-Switch--sr1MxStPAO5](https://hackpad.com/Against-the-Master-Switch--sr1MxStPAO5)
> [Victor Wei-Yin Chen](https://g0v.hackpad.tw/ep/profile/HxEAAVK1pfH) 已經有[國民大會黑客松構想](https://g0v.hackpad.tw/d3UYGxZtxw2#%26%2323560%3B%26%2326696%3B%26%2324037%3B%26%2320316%3B%26%2322283%3B%26%2327665%3B%26%2322823%3B%26%2326371%3B%26%2340657%3B%26%2323458%3B%26%2326494%3B%26%2323560%3B%26%2326696%3B%26%2327083%3B%26%2324819%3B%26%2365288%3BIdea%20Pool%26%2365289%3B)，請將專案移過去喔！
> [name=nchild]

> moved. thanks!
> [name=Victor C]




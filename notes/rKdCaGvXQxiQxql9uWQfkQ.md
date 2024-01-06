---
title: "5 月萌典松: moed4ct 含直播及文字轉播"
tags: event,moedict,hackpad
---

# 5 月萌典松: moed4ct 含直播及文字轉播

> [點此觀看原始內容](https://g0v.hackpad.tw/926nwUKC90j)

> 所以以後萌典松場次數字是要加在 "e" 還是 "i" 哩（轉眼珠）
> [name=venev]

> 這種都見機行事
> [name=Simon P]

> 轉回來了 XD
> [name=Audrey T]

> 那我 BOOKSHOW 行事曆再改回來 XD
> [name=venev]


時間: 5/25 11am-9pm (歡迎遲到早退)
地點: [Bookshow.tw](http://bookshow.tw/traffic/)  基隆路一段 141 號 6 樓之 7（捷運市政府站步行三分鐘）
名額: 25 人: [報名頁面](http://g0v-tw.kktix.cc/events/moedict-5-25) 。
內容: 比照前三次萌典松方式，採「併松」模式舉行，歡迎 g0v 各大小專案加**萌**參加。
**費用**: 採量力而捐、自由贊助方式。如有剩餘，捐給下次黑客松。
直播 / 影片: [https://www.youtube.com/watch?v=B9jAzO1oI68](https://www.youtube.com/watch?v=B9jAzO1oI68)
照片（CC By）：
參與者：[NewCliCker](https://g0v.hackpad.tw/ep/profile/Aq3Xw5pjIMW)、au、venev、BP、ETBlue、poga、Truman、何容、欣怡、Bestian、kiwi、yhsiang（Ly）、a0kman、a-tsioh、A-Han、Mu-An Chiou、大雄、Melody、Moon_C、Nicemaker、ericlive、Jimmy、ipa
> 睡醒補 XDDDD
> [name=venev]

> 辛苦了，自己先來簽到（格式是這樣嗎？）
> [name=NewCliCker]


## 萌典相關開發項目

- 這個月新增的 [CSLD 資料集](https://drive.google.com/folderview?id=0B9tD1zENsweyTVhIa21IY0w4V2s&usp=sharing) (CC-By 4.0) 看有什麼可以用/轉的
- 建立 [http://terms.naer.edu.tw/](http://terms.naer.edu.tw/) 往 JSON 的 pipeline，也許和英法德一樣併進萌典裡?
- 將之前 ethantw 接近完成的使用者自定界面 UI 合併進 master
- [TMuse](http://naviprox.net/tmuse/) 整合進英/法/德參照界面
- 將閩客語的中文定義用重編國語詞典[斷詞](https://www.moedict.tw/下雨天留客留我不留)
- 缺字筆劃/部件檢索 (see [issue list](https://github.com/audreyt/moedict-webkit/issues?page=1&state=open))
- 關於詞條內容的爭議與修正，e.g. 台語「飄撇」有主張為「[漂泊](http://blog.sina.com.tw/sofia/article.php?pbgid=33853&entryid=603569)」。雖然以教育部為主亦可，不過關於用字標準或協定，教育部與民間一直有不同的意見→**思考如何開放協作詞條內容？**

- 萌典量詞與分類詞的區別，目前所分類詞和量詞都沒有區分，如[台語分類詞](http://twblg.dict.edu.tw/holodict_new/index/cimu_level4.jsp?level1=23&level2=85)。已有的成果（有區分）如[政大何萬順指導的碩論](http://nccur.lib.nccu.edu.tw/handle/140.119/59185)（竟然沒開放）。相關文獻都是紙本，網路上沒有電子文獻。A-Han可取得相關資料。
- 量詞與分類詞的區別，會有太多詞條身兼二類；學理與教學需求（萌典的性質）未必相同，或可考量是否有區別必要？

## 併松

### 農域松

- [http://hack.g0v.tw/agriculture](http://hack.g0v.tw/agriculture)
- 最近農藥篇副本狂開，坑已經到達一種很恐怖的量!!!(副本持續加開中)
- 目前重要副本種類: 神農的作物分類樹(作物種類定義)、娜塔雅的藥劑混合交集(不同作物間的共用藥劑)、凱因的武器作用機制(藥劑作用機制標定)
- 先感謝子龍XD![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_48ba42a2674441f55ca9b48e67332efa)
-
-
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c88bba7ecc1fa124cbf8f798ef95b1c4)




### 農學地圖&hackmap

    現有成果：[http://g0v.github.io/farmer/](http://g0v.github.io/farmer/)
    - 已偷跑部份：
        - 將手屋地圖模組([shackhand](http://www.github.com/bestian/shackhand))，加上以etherclac當後台的功能，用在農學地圖上
        - 雙後台功能：
            - firebase+fb用以個人登入自己
            - etherclac用以快速共筆資訊(e.x.農夫市集, 未註冊FB的農友)
        - 分成兩圖層顯示
        - 最大相容目標：etherclac後台建設，要與hackfoldr相容 :+1:
            - 同樣的資訊可以在hackfoldr也可以在shackhand地圖上呈現
            - 只要在第六欄輸入概略地址，程式執行時會自動get再post回去，將第七欄的經緯度補上，就不必手動輸入經緯度
> 經緯度格式要小心，目前寫etherclac後台時，都以「?? 」取代「,」，以免當作csv讀時，多一個逗號變成多分一欄
> [name=Bestian T]


    - 下一步：
        - 多圖層獨立設定
        - Css優化
        - Debug
        - Bowyer的相容性
        - hackmap的後端架設
        - 農學地圖
            - 製作適合的表單
            - 製作適合的過濾器
> _後兩部份有模組改一改內容即可_
> [name=Bestian T]

            - Mobile App

    需要：
    - [ ] 視覺設計
    - [ ] 後端設計
    - [ ] 前端設計
    - [ ] Mibile App設計
    - [x] [Ethercalc Post](https://github.com/audreyt/ethercalc/issues/74)的技術支援  \-\- 已偷跑完工，感謝 [Audrey Tang](https://g0v.hackpad.tw/ep/profile/DaKXhWfoD7Q) 的技術支援


### 自經松

- 自經區現有研究成果： [https://musou.hackpad.com/ngjF3YSdE9B](https://musou.hackpad.com/ngjF3YSdE9B)
- 要做什麼：
    - 還在想要做什麼
    -
    - 各領域針對條文的整理?
    - 更佳的視覺化?

### 動民主家族松

- 各網路民主、直接民主專案交流 \+ 小衝刺↓以下開放各專案寫自己要做的東西
    - 打算來作公民臉書
        - 結果做了便利貼 lol
    - 打算來整理可以幫助 poga 作公民臉書的文件，像是動民主家族結構藍圖……or whatever poga says
        - 結果都在喇賽
    - 發想台灣版 democracy.com
        - 沒做…（被毆
    - ipa: 參加公民憲政會議
        - 和 jimmy, au, a0kman, ... 討論後感想→需要 billlab，參考 a0kman 文官系統概念
- 開發資源收集區↓（好像可以開一個專門 pad 來收集）
> 找到可以內嵌(embad)的social polling/voting服務
> [name=Bestian T]

> [http://www.opinionstage.com](http://www.opinionstage.com)
> [name=Bestian T]

> 或許可以整併來做網站開發，省下從頭寫polling/voting的力氣
> [name=Bestian T]

> 目前做到的討論+公投=群策，用的是現成的服務+輕量的科技，較果還不錯[https://glassy.github.io/we/hold/](https://glassy.github.io/we/hold/)
> [name=Bestian T]

> 有考慮看看 [Poplus](http://poplus.org/) 的 lib 與 spec 嗎
> [name=Simon P]


### 政獻松：需要 OCR 功能 / debug 攻城獅、美術獅、以及沒有人

> 沒人陪我政獻松的話，就來參與謝頓松（"基礎建設松"的縮寫梗是什麼）
> [name=venev]

> 是葉隊長嘛? 我幫開一個 hackpad 把實作提案放進去好了，不然萌典松 pad 會爆長～～
> [name=venev]

> 我是葉隊長（？）沒錯，掃描組..
> [name=Nicemaker]

> 有神快拜！（FYI, 如果不想露出中文全名，可以點左上三條線功能鈕，進入帳號設定改顯示名稱）
> [name=venev]

> 改好了XD 感謝
> [name=Nicemaker]

剛才討論的實作內容已新開 pad，請到這裡討論噢：==[525 萌典併政治獻金松實作提案](https://g0v.hackpad.tw/NxMrvI4uYcP#525-cy)==
- 目前開放政治獻金相關討論，都在 [g0v cy collection](https://g0v.hackpad.tw/ep/group/mgUOtpJUUSt) 裡

### 基礎松

- 補完新版 hackfoldr + people-project hub 企畫 [http://g0v.github.io/g0v-tour-guide/public/hack.html](http://g0v.github.io/g0v-tour-guide/public/hack.html)
- poga 建議人坑介面做好之前先發佈零時坑報，lanfon 馬上開了第一份坑報 pad [https://g0v.hackpad.com/i8tMqWAFi39](https://g0v.hackpad.com/i8tMqWAFi39)

## 文播


### 11:30 開場 (au) 及自介


農域松 (a0kman)
- 農業的幅員廣闊，包括上下游各端，目前區分為三個系統，但以藥劑為出發點。
- 藥劑系統是一個洛克人的概念，也就是讓農民可以在面對 boss (作物) 時，挑選適合的武器 (農藥)，並且充份瞭解它們的效果。⋯⋯（轉接頭有點問題，先換手）

政獻松 (venev)
- 政治獻金明細從監察院帶出來之後，因為電腦辨識率不完美，所以讓鄉民幫忙辨識，目前已經到達三校 60 萬格，也已經做成 Excel 和 open data 版本。
- 目前工作流程的 SOP 已經大致順暢，目前上下游的重點是:
    1.  透過 FB 粉絲團，邀人進入監察院掃描，提供紙本
    2.  下游希望有 data scientist、journalist 等，用「有梗」、「視覺化」的方式呈現
- 今天雖然榮尼王沒有來，但是也歡迎直接找 venev 分流。

動民主 (ETBlue)
- 想和 poga 做「公民臉書」和完成基礎建設松的待辦事項。

poga: 同上

truman: 資訊背景有關心動民主專案，有個透明黨社團雖然跟 g0v 沒關係但是對資訊系統有些想法所以想整合，讓動民主跟其他公民資訊系統連結，找到更多使用者

何容：我喜歡畫畫，我讀的是松山家商室內設計科一年級，需要我幫忙的話可以找我

欣怡：我還沒學寫程式，今天來想支援農學地圖的網站，很單純希望不管搬到台灣哪裡，可以利用這個地圖找到當地友善的農產品，在任何地方都可以買得到友善農業或自然濃法的東西，可以用這個圖查到，因為我常常買菜可以提供這方面資訊，可以做一些版面設計畫是小插畫

唐宗浩：今天來要分享、找人幫忙的是地圖專案，本來在掙扎今天要不要present，這個是樣品而已啦，之前本來最的是自學地圖，之前跟直接跟農夫買的人聯絡上它們希望可以有多圖層，可已有多後台…有些在ethercalc有些在？？比較需要的部分是版面跟使用者經驗的設計，程式碼的部分有些bug可能需要修，希望盡可能把背後程式碼抽出來變成模組，套用在其他地方，讓其他地圖專案可以在一小時內生出地圖，現場後端的人有興趣支援的話有個idea可以做成hackm,ap，現在hackfoldr很流行…blah可以後台做得跟hackfoldr很像，在某個欄位加上地址列，程式界自動把經緯度補上去，打的人不用打經緯度，這樣網站上有hackfoldr的地方就自動讀，叫做 hackmap～需要兩頭，一頭是視覺跟使用者設計，一個是程式碼擴充

kiwi：我是來支援民主相關專案的，後端會，有需要可以聊

a0kman 補充農域松：下午會有個小短講講上禮拜的…這個系統前面兩個做好後第三個是最重要，……連接到後面的氣象……現在講副本，在screen那些資料時以為很快就會生出來，沒想到發現農民會比較需要使用到的，主成分有自己的中文名，但商品名不同，哪種紀行，安全採收期是什麼，一個禮拜要用多少次，那一公頃的使用量、為服不規定、藥到底可不可以賣（使用證）……比較麻煩的負本事找一種菜可以找到三種藥，但局科業菜內有好幾種藥，但當初不是登記給筒蒿的…blah…總之就是沒辦法直接去找我用什麼植物可以用什麼藥。台灣農業有個特殊現象是同一塊田裡面小小兩分地種了三種作物，因為分散風險＋輪作，或者這一季就這些是最好賣的，他有客戶要交，這種混種就會出現A藥不小心用在B作物身上，被檢測出來有嚴重殘留、被罰。哪些蔬菜是適合種在一起的也需要可以在裡面被找到。

a-tsioh: 今天早上 open source (終於!) 了 TaigiIME for Android，本來想弄得比較乾淨(初次寫 Android App)，但還是就先 GPL 出來了 (含法文變數名稱)。有 bug list，可以從這邊開始。然後可以用同一個 data schema 做出客家話的手機輸入法，可以一起討論。

大雄：文化總會，漢字開放資料應用及推廣計畫，三大個工作關於漢字開放資料及的分析和產書、推廣、漢字藝術的鑽研。還有十幾個資料及只是初審，想說過一陣子再丟，也可以把初稿丟上去給大家debug，開放資料服務平台年底才會做完，下次萌典松在報告會產出哪些

melody：ditto大雄

子龍（moon_c）：專案間的流動人口，視覺設計、繪圖

鈕克力（NewClicker）：零時直播平台工廠，狡兔有三坑所以要看有什麼可以支援的地方，程式只懂基本，有時間的話可能會簡單介紹現在作的東西，對動民主有興趣。零時直播介紹：名稱暫訂g8v.tv，名字背後有憤怒的來源…套au大大的向日葵數~為~位體驗營後，發現傳統電視新聞媒體有明顯特定立場言論，因為憤怒及無力感產生此坑，想解決的問題是營隊的時候很多直播畫面用hackfoldr整理，但現場需要有個電視牆系統，身在現場的中控或直播監看人員需要同時間看各個鏡頭，所以我用現成的東西修改，每個元素都是半透明的，背景圖也可以更換，右測試直播鏡頭選擇介面，內場、外場、電視新聞、irc…主畫面是電視牆。用justin.tv作為支援平台，因為是台灣直播人會用的平台，雖然最近種種原因不少人又回流到ustream…上面hackpad筆記區是方便文播人員邊看邊打。irc是一定要的 lol。在實際直播的時候，斷掉或沒畫面的可能原因很多種，比方說因為風吹導致防水布蓋住鏡頭，或有人惡意破壞。要能即時反應這些狀況，網路有程式去ping但布遮住要用監看的。當天華山試用，可以把畫面移動到畫面（地圖）上相對應的位置，不只可以監看還可以偷看其他網路實況。希望不只把直播實況拉進來，也把離線但已經存成串流的影片拉進來。可以做明顯的對照，可以打媒體臉～其他應用：立法院公聽會，講者引述某個立法院決議，希望聊天室使用者找到影片連結貼出來，其他人只要點連結就可以跳出畫面，實際對照講者講的話跟實際上當時的決議是不是相符。還有考慮到分享，希望剛才的對照畫面可以透過長短網址分享，短網址可以用在推特、bbs，長網址可以給facebook貼（預覽需要）。最終目標是成為方便閱聽者判斷的公信平台

ly：我也不知道今天來幹嘛，看有什麼坑…
> orz ....
> [name=Yuan C]

### 12:12 午餐時間

au: 大風吹時間，敬請期待更多食物，下個節目是短講

venev 表示 12:30 會有正規的午餐送到。

林昆翰 (a-han)自介:  政大語言所博士生，第一次參加！之前因為g0v在政大演講有去聽，聽完以後知道有黑客松，我不會寫程式，想要多聽多想看能幫什麼

### 13:30 a0kman 兩段短講

- 國家煞車推進系統？？
    - 國家政策運作的時候，有其政策擬定的推進或剎車方法，好得政策該被好好推動，有問題的則先剎車檢察，就以觀察舉出四個最明顯運作的系統(重點會比較放在少被論及，但是卻應該是在第一線的公務體系)
    - 學者-受到派系、經費等影響
    - 新聞媒體-  目前媒體有下圖的一些問題
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4a9ad28352bf24d7e37ce088d804506b)
    -
    - 公務人員-金字塔型官僚體系內基層卻有其專業的人無法正常發聲，真的有出國考察的專業報告以及帶回來的可討論政策、技術被埋沒，e.g.英國文官長制度，政務官（執政者安排）跟事務官（常任）分得很清楚，能源政策提出時，相關部會集結起來生出十幾個版本，分析優缺利弊，交給政務官選擇，事務官發揮專業（分析可能性、需求等），政務官選擇並必須承擔責任← 這是公務人員出國考察帶回來的資訊，過往都有許多好東西好內容，但被長期封存在資訊網中，頂多只有內部的分享討論，沒有被更廣泛善加利用討論。有許多希望出國帶回來的東西對國家政策或發展有利公務人員，一定也希望帶回來的東西被看到！學運期間很少聽到公務員(常任文官)的聲音，因為公務員被很多法律鉤住，不敢說。很多公務員對學運的態度不是負面，但不敢講。公務員內部有很多聲音，只是對外發言必須一致，擁有專業的人不能講。
    - 人民-政策如果最後的的最後總需要人民來採煞車會發生…（各國狀況不同，這邊指的不是一些國家常見的抗爭，比較像是劇烈反應的踩剎車抗爭），但許多都是對社會有所衝擊的事件，然而如果很多事情最終只能由人家不斷開副本進行剎車，久了不僅疲乏，也失去了代議制度以及公務體系該發揮的效果。
- 你以為的○○ (很多領域你以為的OOO實際上可能不如你所想，這邊舉農業為例子)
    - 農民真的都是窮苦嗎?有農民開法拉利、雙B去田裡耕田，也有一塊高麗菜田在適當的時機下賣12萬，花農家裡有三台賓士，當然也有農民真的因為資訊不足非常辛苦困頓…然而農業真的都是窮苦嗎？農夫的收入呈現鐘形曲線，這些都是應該要去思考的。
    - 這個圖為什麼要放？我忘了……這個圖為什麼要放？我忘了……
> XDDDDDD 上次講完我真der忘了
> [name=曼 奧]

    - 年輕人不一定有用新的想法耕田，許多有經驗的老農或專職農民可以承受數次虧損都不怕，但年輕人在經濟衰退下，資本只夠撐兩三次失敗，也有人說「上網找資料但真的種下去以後爛掉一半…」年輕農夫沒有足夠資源去做事情。(農業沒有所謂新手運這件事情)
    - 農藥真的很毒嗎？不一定。e.g.氯化鈉高劑量也是毒物，許多物品都有他因過量而出現毒害的情形，應該要冷靜探究其使用的需要以及正確使用的方法。
    - 多吃飯真的能拯救農業嗎？山水米作假。需要有更好的機制確認台灣米、農藥安全米。外來米也不一定不好，日本高階米很好吃…如何拯救農業不是單純的多吃飯，這只是其中一個方法，也需要配套。可以標示為台灣茶的標準不是百分之百，而是混入一定比例。
    - 推薦書籍：[美援時代的鳥事並不如煙](http://www.books.com.tw/products/0010563684)（封面是一個海灘男背影）了解台灣為何有這麼多麥製品和過往的農業政策以及和美國在這上邊的恩怨情仇。

### 13:54: 紐克力 G8V

- 電視牆 live demo: [http://hackfoldr.org/G8VTV](http://hackfoldr.org/G8VTV)
- 有個控制台，左上角三個點點，按了可以出現…
    - 按右邊可以展開justin.tv的實況列表，開始整合ustream跟其他實況平台，用tag方式分類，tag由觀眾決定，e.g.核四。可以點影片出來看、拖曳位置、調整大小、透明度，透明度是因為背景底圖可以放map，目前是圖檔，未來希望可以跟google map串起來…希望使用者連到電視牆時，可以點地圖上紅點跑出實況畫面。目前底下bar隱藏，hover才出現，也希望聲音可以hover才出聲。因為電視牆的問題是一打開就全部畫面都有聲音，要一個一個去關掉。
    - 可以把純文字編輯器或hackpad嵌入，給文播的人用
    - irc 正在努力中，live irc 因為flash安全問題不能用打算換成kiwi irc。一樣可以移動跟調整透明度大小。justin 跟 us 聊天系統都是 irc 架構，打算串進來。
    - 現在進展：
        - [http://hackfoldr.org/G8VTV/http%253A%252F%252Fa0000778.github.io%252Fg8v%252F](http://hackfoldr.org/G8VTV/http%253A%252F%252Fa0000778.github.io%252Fg8v%252F) 按左上角「選項」可以新增url…分享網址可以把電視牆畫面跟大小配置分享出去。
        - 嵌入 hackpad 功能：從「新增頁面」欄位新增。
        - 未來這些元素希望可以做到傻瓜機制，現在自由度很大，將來希望預先幫使用者做好幾個排版，2x2、2x3之類的，不用自己拖拉放大縮小。
        - layout [http://hackfoldr.org/G8VTV/1GI6xzYENeC5e-HQucEXFkRHDV6cpx1oQuulJcLxThio](http://hackfoldr.org/G8VTV/1GI6xzYENeC5e-HQucEXFkRHDV6cpx1oQuulJcLxThio)
        - 實況頻道 justin.tv 有做b api 可列出清單，雖然有版權管理機制，但裡面一些動畫 blah 其實可能損害電視台播映權。打算用引用新聞是否算合理使用來解釋合法性但實務上可能有問題，當我把電視台新聞當作報導對象時是沒有問題的，但如果是一直把電視上播的一直播出可能會有疑慮。希望有更積極的作為，也許會找電視台談網路上的播映方式，利基點是電視台也有部分想要加強跟網路社群的合作，所以可能性也不是沒有，詢問過一些媒體的朋友，電視台基於增加觸及率的立場也希望有網路管道。
        - 為什麼要一直說新聞串流，是因為目前掌握社會資源的年齡層接收新聞來源是電視，人類大腦習慣精緻化的資訊，公民記者的實況可能看了沒幾分鐘就關掉，因為使用者習慣看到畫面馬上有爆點。冗長的影音有意義的片段就那三五分鐘，這是平台要克服的問題，除了忠實流水帳式的呈現，也需要導播台，剪輯有意義的片段跟 google map 結合，讓忙碌的人可以…三五分鐘精彩片段懶人包

### 17:00 Bestian 農學地圖：

- 地圖多了icon會縮放的功能，而且有可愛動畫效果……因為很多使用者可能是家庭主婦，所以用親和畫面會有效果！全螢幕還可以像rpg（8-bit新手村）一樣用鍵盤操作，按空白鍵還會跳出最接近的地點的泡泡，將來功能抽出來，其他專案可以在上面放一些人或專案～～～

### 17:19 venev 政治獻金：

- 成果集結在此 [525 萌典併政治獻金松：實作提案](https://g0v.hackpad.tw/NxMrvI4uYcP)
- nicemaker  最節省時間成本的列印SOP，子龍˙做了pdf檔，等 ronny 切 ok 再釋出，目前是縮印 3x3
- 葉隊長整理了副本任務包
- 子龍監察娘！傲嬌屬性，小寵物老鷹，另一隻手原本想拿放大鏡結果被萌典用走了…
- kiang: 平民申請市議員政治獻金專戶SOP，有支持他的可以… XDDDD←nicemaker : 如果我缺錢…（不用成立基金會也不用開公司就可以光明正大收錢的方法！） XDDD
> 後來查了一下，要五萬元保證金，得票數要大於可投票人數的10%，也就是成本是五萬元。(台北市里長大概要幾百票、鄉下要百來票)
> [name=Nicemaker]

> 使用規定基本上是空的XD  只要說「為了選舉」就可以，而且可以分四年用，理由是「為了下次選舉」XDD
> [name=Nicemaker]

> 保證金是候選人登記才需要，申請政治獻金專戶完全不需要這種東西，而且專戶申請後不去登記也不會被打，只要乖乖的把帳丟出來就好了（目前看到是這樣，就看會不會被發公文來糾正 XD ）
> [name=Finjon K]

> 是為了募款啦，成本只要五萬元可以躲過許多奇怪的審查
> [name=Nicemaker]

> 如果只是要募款，就完全不需要成本啊，註冊獻金帳戶就好囉 ;)
> [name=Finjon K]

- 推坑兩位粉絲專頁管理員！

### 17:05 《Internet Freedom and Political Space》讀書會：

- 網路自由和政治空間，一個美國智庫叫做蘭德公司(RAND)做的調查報告，整理了幾個案例，埃及、敘利亞革命，中國、俄國網路事件。網路對獨裁政權的影響。今天進度是埃及、序利亞、中國。成果：
    - 用 [ethercalc](https://ethercalc.org/j3yge6wpqi)把每個國家的狀況作試算表，之所以用這個是因為不會被紀錄到我的名字，不會被政府容易追蹤到…（既然我們都在讀網路中立性的書了）
    - 推薦大家看埃及，狀況跟台灣像，讀書會朋友研究剛好……做了許多補充。
    - 敘利亞部分：作者之所以提敘利亞、埃及，想讓大家知道網路是雙面刃，序利亞現在沒有穩定，陷入長期內戰，網際網路扮演的角色：只有20%的人能上網、100萬個fb帳號，6000個twitter帳號，因為fb被官方封鎖，所以能上facebok要跨越政府的防火牆，跟中國一樣。雖然在找翻牆的方法，唯二電信商故意把網速弄很慢撥接52k，很多人跑去網咖上網，以前翻牆就可以上網，被政府發現後，伊朗支援網路監控大升級，政府要求上網必須實名制，登記證件。如果不用登記的網咖，都有安裝監控軟體。這個機制讓他們逮捕發佈國際消息的政治部落客。
    - 革命期間敘利亞政府控制網路的策略：封鎖大部分外界的social media，讓少數人透過獨特技術才能上網，政府之所以默許，就是要讓這些人容易被鎖定。有計畫地偷偷放管道讓他們能夠這樣做。用skype串連也需要翻牆，政府發展一套skype通訊加密軟體其實是做監聽。很多技巧和思維是進步的，因為伊朗在後面幫助他。而伊朗的資助來自中國。
    - 敘利亞的案例的有趣結論是，網際網路的角力是世界技術和中國/中東國家監控技術的角力。
    - 敘利亞抗爭期間狙擊手針對拿手機拍照的人射殺。
    - 埃及比較像台灣是因為沒有任何的篩選機制，個人覺得有點像是還沒解嚴的台灣，是個獨裁政權，為了提升經濟跟西方國家親近，網路公開，為了避免暴動，公開網路，感受機方世界的氛圍。上網人口只有30%，就是 2400萬，埃及因為總人口多所以上網人口多。因為沒有封鎖，上網人口中有一半上fb。埃及的茉莉花是fb開始的無誤（書中證實），因為沒有封鎖的條件下可以用fb發起運動，讓一般人可以集結。跟台灣318類似的是，埃及把fb用在各種組織工作（社團），並不只是傳遞訊息。相對地敘利亞則用來傳遞訊息居多。兩者之間social media使用狀況最大差異在此。
    - 埃及在沒有做網路篩選的背景下，第一件事是斷網，結果越斷網人民越上街頭，所以發現斷網不行。後來要求電信公司傳簡訊叫使用者不要上街頭，結果不知道的人也知道要上街頭了…為什麼革命在某個層面上會生效，關鍵是很多背景因素影響的。現在中東掀起對網路管制的思考，因為獨裁的都怕。台灣也可以借鏡。
    - 最後：請大家不要在網路上留自己的資訊，請不要 tag 我。

### 19:30 成果發表

au: 今天做的事情是把 hackfoldr 弄成可以用 google spreadsheet 做後端，支援私密編輯、權限控管。
live demo：
- create spreadsheet 名字隨便打
- 把ethercalc貼過來（目前還不能有空行）
- 發佈到網路後得到網址
- 拿試算表 id 貼到 hackfoldr.org 後面，沒有意外的話……竟然沒爆掉 XD
- 跟muan討論時發現這樣沒辦法有個好記得名字，目前作法是超過 40 英數就去 google spreadsheet 抓。
- 之後不用等 ethercalc 加功能，小蜜蜂什麼就可以直接做

poga: ET 叫我幫他做便利貼系統…像 loomio 提案前應該有個 brainstroming 的步驟。動民主其中一部份是作公民臉書……
- mockup：把便利貼想成一份 list，大家可以在上面加加減減加標籤grouping投票…etc，上面的 bar 可以顯現這個 list 裡頭大家同意度的分佈。這是一個類似便利貼的系統，但不是像其他動民主需要有階段性，內容會不停被修改，沒有停止的一天。這個系統沒有說要什麼時候決議，是永無止境的演化，團體可以在某個時間點把這個清單當下的狀態收割走，當作是他的民意基礎去做他要做的事情。這個系統不負責後面的事情。
- 另外[公民臉書](http://g0v.github.io/don-republic/public/index.html)的部分…參考 github 把大家的操作行為弄成 timeline 的形式，現在還沒做。

Kiwi補充：Airesis可以跑了，大致準備如下
- Airesis是一個與其他開源軟體緊密結合的rails軟體，一個環節沒扣上就不會動，基本社群服務功能都有，所以也需要許多資源來正式架設
- poga fork [https://github.com/poga/Airesis](https://github.com/poga/Airesis)
    - 驗證過這個版本有解決讀取yaml語系文件的問題(自從ruby 1.9以來使用psych yaml parser的utf8處理方式，這與其他branch的airesis使用的是ruby 1.8版的syck來讀取而有所不同，但現在沒人在裝1.8了...)
    - 有些hard code的訊息之類的...是義大利文，不知道是做啥用的
- 一個可以用的domain name，至少要有一個"."，如webserver.tw
    - 他的url_for有改過，盡量要讓domain name長得像www.xxx.xx或xxx.xx。有用subdomain作為group的設計，多個xxx.airesis.tw都可以跑在同一個site上而不會混亂。
- 正式上線需要資源
    - 要正式上線要申請一堆social app的app_id ... 跳過(device, omniauth-xxx)
    - 需要一個正式的mail relay server，大量認證信和電子報才不會被擋(maktoub, resque)
        - [如何讓我公司的 MAIL 不會被設定為「垃圾郵件」](http://vovo2000.com/phpbb2/viewtopic-336398.html)
    - solr server與rails的db分開，將rails的db,solr,redis擺在一起的話，那就要加個SSD還是硬碟免得IO卡在一起
- wkhtmltopdf(wicked_pdf)
    - 下載wkhtmltopdf的binary至一個特定目錄並且設定config/initializers/wkhtmltopdf.rb:WickedPdf.config
- PostgreSQL > 8.4
    - 雖然有看到文章說要9.1不過我測試schema是OK的
- Redis > 2.6 (resque, redis)
- Solr > 3.5, rake sunspot:solr:run/start (sunspot, sunspot-solr)
    - [https://github.com/sunspot/sunspot/wiki/Upgrading-sunspot_solr-Solr-Instance](https://github.com/sunspot/sunspot/wiki/Upgrading-sunspot_solr-Solr-Instance)
    - 正式上線必須評估是不是要使用solr 3.5，3.5已經是很久以前的東。很奇怪的是sunspot好像沒打算解決solr4的相容問題，此外現在solr開發主力都移往solr4，將來會難以維護
- nodejs  > 0.10 (coffee-script, execjs)
- Faye > 1.0 , rackup private\_pub.ru -s thin (-D) (faye, private\_pub)
- 將config/*.yml.example複製成*.yml
- rake db:setup
- 建立測試帳號
    1.  建立帳號，你將會收不到驗證信
    2.  用email在rails console裡找到你的user
    3.  confirmed\_at = updated\_at, user_type = UserType.find 1
    4.  save
![](https://dl.dropboxusercontent.com/u/16968403/g0v/airesis_1.png)
![](https://dl.dropboxusercontent.com/u/16968403/g0v/airesis_2.png)
![](https://dl.dropboxusercontent.com/u/16968403/g0v/airesis_3.png)


### 收播後特別節目

書櫃小區聊天：
- 公務單位組長、科長、第一線承辦之間斷層（ a0kman 順序是這樣嗎？）；輿論
- 海埔新生或邊緣弱勢之三不管地帶→（要資源或關注）→跨部會小組（政務委員名單）→疊床架屋大政府
- a0kman: 有些條文可能暗示會出現的填海作業及污染工業；自經區與難以監督的前店後廠；農地轉工業用地，農地縮減，真糧食危機
- [問題家庭共筆](https://hackpad.com/dJuZFfVKopG)、台灣戰後嬰兒潮 / 解嚴世代、島國 mobility 與壓力鍋處境、標籤思維習性

ETBlue: g0v.tw 大改造: [http://g0v.github.io/g0v-tour-guide/public/hack.html](http://g0v.github.io/g0v-tour-guide/public/hack.html)  [http://g0v.github.io/g0v-tour-guide/public/g0v.tw-achievement-moc.html](http://g0v.github.io/g0v-tour-guide/public/g0v.tw-achievement-moc.html) demo + LY [http://g0v.github.io/g0villa/](http://g0v.github.io/g0villa/) \+ JimmyHuang (themeforest parallax theme, 連結待補)

LY: 6/14 下午 Front End 新手教學松
- 參考實驗室松鼠
> 松鼠松XD [Bropheus Huang](https://g0v.hackpad.tw/ep/profile/GpC5QLM6Mdf) 說昨天一群人圍著坐著的 ly，[陷人於坑](http://logbot.g0v.tw/channel/g0v.tw/2014-05-26/24)的重力坑形沒錄到好可惜。以後收播後還是繼續錄影才是～
> [name=venev]

    - 投影片 [https://speakerdeck.com/muan/project-lab-squirrel-number-1](https://speakerdeck.com/muan/project-lab-squirrel-number-1)
    - 教材 [https://gist.github.com/muan/2383d8f8700ba363cfe8](https://gist.github.com/muan/2383d8f8700ba363cfe8)

## 總務

> 這次 h1 都要兩個字嘛
> [name=venev]

> 先來補眠，晚點再補
> [name=venev]

場務
- 脫鞋松：BOOKSHOW 可以穿鞋啊但這次大家都自發脫鞋（這樣比較輕鬆？）以後可以比照辦理自由穿脫。但鞋子擺在簾後收納區比較不卡門。
- 直播影片很長，事後不易搜尋時間碼，下次可在直播中，直接記錄時間碼
- 神秘的轉接頭爆掉事件（有請 BP 補器材）

熱量
- 飲料：冰黑咖啡、去冰綠茶、可樂、雪碧、水
> ipa or au: 咖啡是比 wifi 更底層的基礎需求 XDDDD
> [name=venev]

- 鹹點：a0kman IKEA 丸子、誰贊助的港式茶點（感謝）、品客洋芋片、多力多滋
- 甜點：SAISON du SOLEIL 紅豆 / 芋頭麻糬丸、義美巧克力 / 杏仁白巧千層派
- 午餐：肯德基炸雞薯條等；達美樂大披薩
- 晚餐：常旺熱炒（感謝 ET、A-Han 外帶團）

基金
- mo3dict 結餘 4,356，本次小松香油錢 1,307 元，食物支出 6,800，**總計 -1,137 元**（[明細](https://docs.google.com/spreadsheets/d/1JLdXfMQops2lBsgwpnQHE_L_S4yLi3yB4Y4yRuaYBd4)）
- 大雄：文化總會將贊助本場小松 10,000 元，一樣餘款移交下次松，待通知入帳～


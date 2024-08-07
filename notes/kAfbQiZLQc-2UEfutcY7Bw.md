---
title: "[R0] 配線 / Wiring @g0v Summit 2016"
tags: hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/iSbcxP4yRXo)

同步、協作與進擊，打造跨界群眾串連的神經網絡 / Intersectoral networks: Synchronizations, collaborations and demonstrations
主持人: 林祖儀

more info: [g0v Summit 2016 hackfoldr](http://beta.hackfoldr.org/g0v-summit-2016/)
現場直播網址 (live url) [http://summit.g0v.tw/2016/live](http://summit.g0v.tw/2016/live)

↓文字轉播、線上討論↓

## ==媒體無間道 — 我在新聞界臥底的日子 / My Covered Life in Journalism==

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2e4a29f6b06ad4867ed1ec90551128f0)












> Kirby! Kirby!Kirby!!!
> [name=羅佩琪]


大家好我們在2012跟村長一起參加yahoo hack day，此時g0v還沒開始，那時我什麼都不知道，做預算視覺化，當時是參考國外的紐約時報的網站。

總預算網站參考紐約時報的預算視覺化。

其實在國外資料新聞大概2009衛報就開始了，2012年的時候g0v出現的時候國內的媒體在做什麼呢？......《奇怪欸，女師2度颱風登山》在報這種資料很多錯誤的報導，例如該女師沒有男友 媒體還寫男友勸她下山......(子虛烏有處族繁不及備載)

我們一直都知道媒體有這樣的問題，不是要怪誰，感受到有些地方不太對勁，既然都有g0v了，就想說應該要想辦法混到媒體，想說要開始就先從娃娃、學校開始。

這些照片都是側拍，在世新課程上面拍的；也有從0開始的新聞網站，在做資料新聞訪談；也有一些中廣報導......發現越來越多媒體想跨到新媒體跟網路世界；又例如去年我們也做了資料新聞實戰營，我們自己也發起了一個專案叫做零傳媒，舉辦資料新聞分享會。

我們想從根本面上我們可以為學生帶來什麼？台大、政大、世新、文大......我至少做了幾千張投影片(1362)，這些學校只是比較常去講的學校。

資料新聞的步驟：先從案例開始、提案、找資料、open refine、spreadsheet、cartoDB、程式設計、p5.js就很適合因為把圖像...框起來。
kimono:網路爬蟲好工具

我們做了許多專案，但是結果都是用javascript做的。給大家看一些案例：

- 冰桶挑戰：當時有人說這只是噱頭，直接看金額，30min爬資料、30min視覺化，整理出來發現那幾天的捐款佔七年來70%。
- PM2.5：濃度變化動態看的到。
- 急診人生：30秒可以loading完成，從遊戲了解醫師的生活，弄到一半病人會起來打你。
- 伊斯蘭恐攻視覺化：都是用程式來做，沒有工具套件可以產生。
- PTT視覺化：也會開源
- 台灣癌症資料......

寫程式真的對記者滿有用的，林辰峰就曾說：

    這些記者用程式語言[Python將網路上的數據取出](http://first-web-scraper.readthedocs.org/en/latest/)，再利用[統計語言R來清理資料並做數據分析](http://www.scoop.it/t/r-for-journalists)。當需要比對與整合多比資料庫時，他們[寫出一條又一條SQL程式碼](http://www.reg.ca/faq/PhpMyAdminTutorial.html)，將多筆資料庫綁在一起。他們用[D3.js設計出互動圖表](http://alignedleft.com/tutorials/d3/)，在碰到含有地理資訊的數據則用[Leaflet](http://leafletjs.com/examples.html)或[QGIS](http://www.qgistutorials.com/en/)製作出精美的地圖。他們不是電腦工程師，也談不上是設計師，他們是記者。一群會寫程式，了解視覺設計，又懂採訪寫作的記者。他們有時也被稱作資料記者或數據記者(data journalist)。
    [https://www.twreporter.org/a/opinion-data-journalist](https://www.twreporter.org/a/opinion-data-journalist)


我們可以想像到記者會變成三頭六臂，可以幫阿宅設計「阿宅者聯盟」，包括大三還有VR、各種演算法都應用上來，另外還有更多更多多媒體設計、網路平台服務等，建議資工系加入「採訪寫作、傳播理論、新聞倫理、新聞編輯、影像報導」等，比較軟的能力，怎麼溝通、怎麼採訪，感受到不同領域的需要性。

常用工具如下
python：程式語言
R：數值分析
SQL：資料庫
QGIS：圖形資訊系統

很多同學不見得那麼上手，還是會回去學工具，「要做小遊戲」、「視覺化」等，工具很多完全可以列給他，實在太多了，多妳可以挑精要的來用，例如excel....例如有六成圖表不能使用，立體圖不能用；再來會不會服務終止？例如kimonolabs這就會很痛苦。

又例如open refine開源但就比較沒有維護，這些情況最後就會讓學生回去學寫程式。資料記者於是有挫折曲線......所以這件事有點弔詭，記者真的需要寫程式嗎？

新聞+程式的職缺，會發現要不就是內容冗長，要不就真的是真的要工程師；我們有時候是一個因果關係，記者+設計師+工程師要三者都會很難，職缺也不多。

回到主流媒體的報導，會發現除了內容的問題，表現也是一個問題，各單位網站也都很像，傳統→新媒體就會有這種思維，報紙丟到網路就是新媒體？寫文章會精煉化，上網路後為什麼不也做精煉呢？── 這是表現形式的弱點。

也因此後台常常就只是一個貼文字、貼內容的地方，沒有發揮輝空間。最後是這樣的東西似乎沒有效益。

我們做了林義雄的專題，發現按讚跟互動大概差兩倍；右邊的採訪花的時間少很多但獲得的關注更多。

進入門檻高、訓練成本高、人事成本高；進入媒體後發揮空間小、系統包袱大、投資報酬率也低 \-\- 這跟產業轉型有關。聽完這些問題後，我有辦法去改變嗎？

於是我們開始希望試著去改變，突破文字突破的表達形式，從視覺化來做，我們這在做[plotDB](http://plotdb.com/)  ，大概長這樣：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ea20c419449e2d802b55726f9b9bd127)


我是預計他可以從四個層面出發。

例如這是連接散佈圖，可以看到年代，例如想看離婚率跟兒童犯罪率的關係，這些資料表有不同欄位 ── 這些資料不用特別做這什麼，只要把資料拖過來就會呈現出來。拉出來的線條非常神秘......
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_77ba7ea8c547b15787d679008ac39f0c)


這是很快就把圖表做出來的，對不寫程式的人來說是很大的優點。但有時我們不一定知道表現方式為何，此時可以利用Explore來找，找合適的圖表類型。

> 跟raw這個網站有點像？！([http://app.raw.densitydesign.org/](http://app.raw.densitydesign.org/))
> [name=羅佩琪]

> 請問這個是什麼軟體？
> [name=Ru L]

> 請問有這個demo中網站的網址嗎OwO?
> [name=Grass J]

> localhost? XD
> [name=Ru L]

> 登愣
> [name=Grass J]

> localhost連不上？
> [name=Yi-Ping C]

> [http://plotdb.com/](http://plotdb.com/)
> [name=Yiling C]

> 謝謝>////<
> [name=Grass J]

> 這裡有demo [http://plotdb.com/chart/?demo](http://plotdb.com/chart/?demo)
> [name=Ru L]

> repo [https://github.com/zbryikt/plotdb](https://github.com/zbryikt/plotdb)
> [name=noracami]


〈Kirby現場demo中〉

資料對比、數值變化，很快就可以看出變化，這是第二個層面找到很多圖表類型應用。

第三個特點，程式碼是開放的，可以馬上把實線變虛線；也可以把數字相減就有排序功能了；但這時會覺得記者不會寫程式怎麼辦？

第四個特點，可以跟社群連動，請社群幫忙做。

這樣的圖表可以成為一個可以嵌入的畫面，媒體也可以這樣使用並去突破，有更多的多樣性，小結四個介面：

- 資料與表現的介面
- 故事與表現的介面
- 創意與表現的介面
- 社群與表現的介面

總結來說，實戰營學生都很優秀，雖然不會寫程式，都可以互相合作；這是最後的實戰營照片，每次看都會覺得這些記者都可以在未來新聞界佔有一席之地、影響這個生態。

**Q：資料科學越來越興盛，工程師思維跟使用者思維怎麼連結**？

建議對互相的領域要有了解，記者要知道這個東西怎麼運作。我們不知道對方的能耐，很難想像就很難溝通，反之亦然。這是比較軟的實力。

**Q：想請問圖表的工具有給實際新聞從業者使用過嗎**？

這個東西還沒開發很久，還需要更多實際作者來使用。


## ==鍵盤宅的輔選經驗談 / Campaigning Experiences of a Geek==


我在g0v裡面參加的主要都是國會相關的專案。
我在大埔期間聽到「依法行政」的時候，覺得他們依的法怎麼跟我認知的差很多？

在這邊我想做個小小的調查在這邊我想做個小小的調查：（現場調查中），這邊有自己想參選或身邊有人曾經想要參選的嗎？舉個手？（現場一些人舉手）


1.  所有經驗都是個案
2.  資訊能力的運用

我得說，所有經驗都是個案。就像我最近要去日本工作，就搜集很多日本的資訊，但每個人都不太一樣。我今天分享的，我相信他也完全無法完全應用在每個地方，大家就自己去斟酌。

我發現雖然我是g0v的宅宅，但在輔選過程中，資訊能力會因為選戰規模而受到侷限。

我朋友選的是一個小小的地方代表。柯文哲在資訊戰上打得非常成功，但我朋友選的是小小地方代表，資訊能影響的程度就小很多，我自己調整過後，雖然我以前比較常寫程式，現在我就比較少把主力放在程式上

我先講結論：如果你要幫朋友輔選，把他當手機賣就對了！
投票不用成本，所以就只是把消費券拿給他，讓他可以自己買。因為沒有成本，所以大家投票不會那麼謹慎。

我的朋友選的是苗栗鎮的市民代表，台灣國裡有個獨立的苗栗國，投票總是國民黨獲勝，我現在分析一下：

苗栗大概有五十六萬人口左右，頭份市超過十萬，苗栗市大概只有六萬人左右，是苗栗人口最多的地方。如果要在苗栗選縣長，只要在頭份竹南獲得大部分的支持就可以贏得選戰（現任縣長徐耀昌就是根據這條路走上去的）。我朋友在頭份第三選區，竹科/外來人口/新住戶，新外人口是傳統選戰無法觸及到的，所以這些人都有機會成為我們的票源。

> 大家一起打同一段好像會lag，共筆的時候錯開一下
> [name=zoeL]


（圖，展示朋友的選舉公報）
朋友：黎煥強
選舉公報上第三、第四條寫：兩個孩子的爸、鐵馬上武嶺，我們這是故意這樣寫的。
有人跟我們說：「你們沒有玩社團不用想選，選舉公報上面都馬是什麼什麼理事長。」好，所以我們就這樣子寫了。有刻意寫不一樣的內容，例如兩個孩子的爸爸，結果確實也有引起一些注意。

朋友是深藍家族，因為要無黨籍參選和家族意見矛盾。
第三選區的人口數約32000人，20-45歲佔約40.4%，約為13000人，約估1500票當選，十個人要有一個人投票支持。

最後選舉結果，我們第三名、拿2087票，算是相當不錯的。
落選第一名是民進黨的候選人，（所有候選人中有兩位是確定沒有買票的....可能是因為很年輕所以沒有錢.....）。

花費
★事先詢問現任代表的花費
★目標8萬
★實際18萬，募得15萬+選票補助
~★交友不慎~ 沒有計入人事成本~（血汗）~

拜訪竹南鎮民代表，對方說自己第一次選的時候花100萬，連任時花了60萬。他最大的人事成本都被我們這些血汗的朋友吸收了。（通霄鎮也有一個年輕代表，他真的花了8萬就選上。）

他第一次選花了一百萬，連任的時候，大概花了六十萬。這是一個我們那邊竹南（已經比頭份好一點）選代表的數目。我們一開始設定八萬，實際上花了十八萬，還包括一個小小造勢活動。還加上一些選票補助，剛好打平。

但因為交友不慎，人事成本都被我們吸收了～
十八萬算是有點低估，要選這種層級的代表的話，可能要再高一點。不過我們有聽到通霄鎮有一位年輕人代表，他好像真的是花了八萬，第一次出來參選就選上。

錢都花在哪裡？做文宣品，就像這是我幫他做的文宣品。這是我幫他做的扇子，我們希望把選舉做得開心一點，做既典風的扇子，我要強調，這把扇子一把7.5元！很貴！

我們就很猶豫，到底要做便宜的，還是這把7.5的扇子？我就堅持，因為大家拿到也比較開心。事實也證明，阿嬤都比較喜歡拿我們的扇子，覺得「搧起來比較有風」，後來證明我們的決定是對的。

選前一週我們做汽球，我們沒有辦法掛大布條，就放大氣球。路上看到媽媽跟小孩介紹說：他就是那個氣球叔叔！還蠻有用的。不過有風顯示如果風很大，就會吹走。

這是沿路掃街，不斷鞠躬哈腰，看到人就大招呼。老人家會拿面紙，面紙很重要。晚上騎腳踏車（有ＬＥＤ），讓大家看得到。

[http://toufen.net/](http://toufen.net/)
網站我一開始提到說，對小規模選舉而言，資訊影響很小。但ㄅㄅ**網站還是很重要**。

當有人打進關鍵字，發現這個網站比別人好的時候，就會對這個年輕人印象不一樣（跟以前的候選人不一樣）。我們會在網站中描述我們的困境，看網站的人就會覺得他好像有責任要投票，一票感覺很少，但對我們來說差一票就差很多！

文宣品大家都會做，但我要強調一點不一樣的是，以扇子來說，其他人做扇子，他們會把臉放上去。但我們堅持我們都不放候選人的臉，會覺得政治味很重，大家都不想拿出來。我們就故意包裝成這是「頭份」的扇子，不是候選人的扇子，我們都採取這樣的策略。

老一輩的人還是會問說你們這樣怎麼知道誰要選？但事實證明，選到後來大家根本不在乎候選人長什麼樣子。所以人家願意拿你的扇子，比上面有沒有你的臉，重要多了。

有催票效果。

以扇子來說，其他苗栗候選人會把臉放上去；放臉政治味很重。老一輩覺得一定要放臉，但老人家其實是以名字來辨識要投的候選人（所以照片真的不重要）。

不斷地討論黎煥強是個怎麼樣的人（ex: 馬英九是個陽光大男孩，但過了幾十年之後.......所以人渣文本提出陽光大男孩可能是個失敗的形象）

很不幸的，黎煥強就是一個陽光大男孩！我們就從這種方式，強化這種方式。他喜歡運動、漫畫、但是他是政治素人，

苗栗很有趣，你有看到七十歲的老人讓座嗎？為什麼，因為一個八十歲的阿嬤上來了。在苗栗，三十幾歲的人出來選是非常年輕的。

之後大家就會介紹：他就是很年輕出來選的那個！

宣傳就是要把候選人形象強化到每個選民的心中，

就算大家覺得口號不重要，我們還是很用心的在想口號。在路上的時候，你只有三十秒可以介紹你這個人，如果他會問你問題，你要準備一分鐘的內容，如果他開始罵你，你就有五分鐘。如果他願意聽妳五分鐘，那這個人的票就拿到了。

另外就是設計很重要（相較於寫程式／在這樣小規模的選舉）

獨立參選最大的對手都是自己
我們相信任何一個人解釋老代表跟黎站在一起，都會覺得黎煥強比較好。選舉的時候最重要就是宣傳，不要把眼光侷限仔對手手上，而是如何把自己介紹給更多人。

理解其他族群（大家都是選民）
他是深藍家庭出身，他知道國民黨人在想什麼。但他知道如何跟國民黨人相處。假設你今天有機會選上，你討厭的人也是你的選民、你要服務的對象，你不能把他當作敵對的族群。很多人犯的錯就是把敵對族群畫得太明顯了。

我們的經驗經老人家反而很希望把票投給年輕人，不管他原本是支持國民黨還是民進黨的。

選舉很常談基本盤，但這在小規模選舉是不存在的，大家通常都是投票日那天出門看心情投票的，多數都是空氣票。

一開始決定參選的時候，我們問自己：除了勝選以外我們還要什麼？你的核心價值是什麼？是什麼讓你寧願選不上也要堅持？

Q：除了勝選，更重要的是？Ａ：讓頭份年輕人相信自己。

我們問國民黨朋友這個問題，他說，選不上什麼都沒有啦。我們當然很生氣。

假設你很需要錢，有建商要給你一百萬，你要不要？如果你選後只要幾個提案發摟他，你要不要？你做了九十八件好事，只做兩件壞事，你要不要？

我們最後決定，要給頭份的年輕人一個好榜樣。

小規模選舉中基本盤是不存在的（除了藍綠死忠選民）

自我評估
好時機（柯文哲、給年輕人機會）+恰當方式+黎煥強自己很認真

年輕人要談理想？自己開會的時候談就好，路人不在乎，他會覺得你太高調、太遙遠，真正在乎理想的人已經站在你旁邊幫你了。

談理想，規劃策略的時候談，執行策略的時候一點都不要談。

1\. 談核心價值（選不上也沒關係的核心價值）
2\. 形象設定（定義黎煥強這個人）
3\. 資源分配與差異化(窮嘛!)
4\. 設計與執行（最後就是花足夠時間掃街、強化你的形象）

Q. 你們用很成功的策略完成選舉的過程，成功勝選，選後你們有沒有想過用這些技巧來做更多的應用？還是只為了勝選？

A. 我們在選舉時我自己也是參與g0v，我們強調透明化，不斷跟選民說會讓你知道我們的代表以後會做什麼，我們實際上也是做，像代表會質詢的內容都拿出來，也做逐字稿。讓頭份是的市民看到本來就應該看到的——待表到底在待表會上做了什麼。只要夠多人看，頭份的政治會更好，且對我們的下次選舉會更有幫助。如果別人沒做只有我們做，我們當然有優勢，如果別人一起做，政治就更好啦。

Q. 2018有可能砍掉第三級地方自治，你們會把這樣的技術用在哪裡？
A. 我朋友雖然選上市民代表，但他希望頭份是被砍掉ＸＤ
他進入代表會之後他也理解到，這樣的代表有點多餘。你旁邊一條路，鄉鎮市公所可能沒有路權，路權是縣的，反而製造了很多拖延的機會，他反而希望可以把這個拿掉。

他進入實務之後發現市民代表能做的事情有限，如果沒辦法往上的話，苗栗縣在地的議員想要採用這樣的方式繼續下去，我們很樂意分享。

最後我想講，如果你有朋友想選的話，還有一兩年，要趕快去做在地的倡議組織。他們會是你在選舉時非常大的人力來源。


## ==從滅頂秒退地圖看網路世代無組織社運 / Netizen and Self-Organized Movement: A Case Study with Boycott Mapping==

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0be6003fe3b1294ed1d8b6008bdd9e70)

\[[slides](https://docs.google.com/presentation/d/1McErnxOtxVF1e7S5HzByj3lUZ52jKC-tU5ZrHMAgscU/pub?start=false&loop=false&delayms=3000&slide=id.p)\]


我今天想分享的題目就是從滅底地圖看網路世代組織社運。大家就把焦點放在網路世代組織社運上，因為畢竟滅頂是有點爭議的（笑）

我們先看目前的結果：
2015年營收少50億，和上年度比起來虧損17%，淨虧損19億
近三個月營收少28%、25%、31%
costco已經把林鳳營下架了，但是把義美上架，雖然義美也下架了，但是他是被消費者用台幣下架的！
UCC股權全數退出
Calbee股權準備退出
頂新味全告頂新

如果聽完這個talk想跟我做其他交流，（聯絡方式）jimhorng

我的立場很簡單，就是希望平常吃東西可以吃得心安，就是希望黑心商從台灣消失。

我只是個參與者，這是無組織的運動，我無法詮釋或代表任何的行動。（focus 在行動及解法, 而不focus 在道德論證）

先從大局觀來看，人民要的就是吃的心安，所以食安很重要。食安法的立法、執法、監督的面向，人民雖然都可以著力，但這幾個面向，人民要著力，很曠日費時。

我們有一定共識的黑心商，統Ｘ、頂Ｘ，還是在法律訴訟程序之內，沒辦法講太直接。人民另一個參與的方式就是用市場淘汰機制，抵制、秒退，我今天的架構會專注在秒退的活動，跟抵制黑心商其中一個子集團，味Ｘ這家公司。

滅底的起源，就是2013~2014有三次很重大油品的狀況，在2015居然全部被判無罪，人民可以接受嗎？

要滅頂，透過司法程序要好幾年，而且他們很龐大，有很多事情可以做，官商的關係，之類的。日本有對我們做一些很好的示範，雪印、麥當勞有一些食品的事件，民眾就靠自己的力量讓它們倒閉。

給台灣的啟示就是，自己的黑心商自己滅！

我們的目標：頂新大魔王
他在2015年的總資產2.5兆，等於台灣1/6的總資產。

他有很多資源，媒體上帶風向、頂級律師、長期降價出售，個人認為要推倒這個大魔王比Ｋ黨高，但是Ｋ黨推了七十一年才半殘，難度真的很高。

他的產品超過一萬種，集團公司超過一百個，更不用說是他的通路。這都是網路的懶人包跟ＡＰＰ冰的啦

就像超大的巨人，一踩，小小的人民就ＧＧ了。

怎麼辦呢，我們只好先推中頭目，味全。

> 休息一下交給你們orz
> [name=zoeL]



面對國王的感覺是他們是超大的巨人，嘗試去抵抗但巨人一踩人民就ＧＧ了，只能從中頭目味全開始，做投影之前應該上一下資訊課，造成中途木什麼影響？2014年中人民開始抵制，年底頂新味全營收年增長率將到底，2015年底又回升回來，看到紅色現年增長，跟去年比變成正，抵制力量越來越弱，味全又開始復活，這時剛好發生一審無罪，全民抵制力量更強量，2016營收降下來，有非常顯著影響，看不出來是秒退還是因為全民憤慨，光抵制加上秒退整地掉下來，和去年同期比起來，秒退可能有一定程度的影響。

那我們稍微待一下秒退這件事情，發起人Mr. Yen是先生，讓味全直接產生營收損失，如果讓味全產生更大損失。可以長痛不如短痛，

秒退地圖：
把秒退行動和目前大魔王的狀況結合的視覺表示，最上面可以看到總秒退經歷多少時間，目前大魔王血量，自己想辦法抽出幾個關鍵性指標。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e8276a980de12ff5b0aa025a4efe419f)



魔王很強所以需要長期抗戰，人民的力量是分散的，秒退地圖縮短長期抗戰的時間，秒退的挑戰第一個是爭議性的問題，第二個是行動本身的問題（需要親自到目的地去，忍受民眾和店員的目光）。秒退地圖可以把秒退狀況視覺化，把數據視覺化之後，比較可以組織與策劃下一步的目標。需要有人維持系統、推廣、蒐集登入資料等（系統本身的）挑戰。

如果不靠抵制靠秒退的話需要退 4800萬林鳳營，但是一個現代公民要關係的事情實在是太多了。網路上有一篇文章「[長大是什麼感覺](https://www.ptt.cc/bbs/Gossiping/M.1457003863.A.501.html)」我覺得說得很好。

公民很忙，副本有公投、醫療、勞工、兩岸、課綱，長大是什麼感覺，不懂為什麼大人回家躺在沙發上睡著，長大就就知道是什麼感覺，秒退遇到的挑戰很多

熱度維持，可能有這幾種方法：
樹立目標感，透過社群力量互相扶持，持續立即的反饋跟報酬
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5ae73048966cbc3c33666b0f9481c5ad)

之前秒退的狀況，可以從數據來看，藍色的線是當時段秒退的總經額，紅色是秒退的次數。可以看到一開始都很高，但到後面，紅色將很低，金額還是很高，代表什麼？都是重度使用者，次數退的不多但金額都很大。

我們就能擬定後續的策略，如何把輕中度的使用者找回來、跟如何鼓勵重度使用者繼續下去。

最熱衷是ＰＴＴ每篇都被推爆，
可惜最後還是卡關了，原因就是最大的通路下降，其他通路都不給退。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_90b617994d39084b224e99cdbee8aaf8)

pol.is 的
綠色是贊成秒退比較多，紅色是反對秒退比較高，綠色還是比較多。

PTT平均一夜的推裡面會有一個噓，跟一個中立的，風向是贊成比較多
DCARD就是愚蠢沒有下限、濫用權力，秒買秒退是浪費，負面的
01的，都是小屁孩
yahoo，不讚同占六成，也是負面的

觀察行動的目前效果需要從各個網站蒐集資料，才知道目前的風向怎麼樣。

網友自發論述辯證，各種角度辯證，這裡要解決認同感的問題，小弟初步估計超過千則，越多人辯證越清楚。
風向走勢一開始比較低，後來變得比較高

接下來有人提出ＳＯＰ，就說如何秒買秒退效率最高？不會增加員工工作量？這就是一種開放協作（Open Collaboration）的方式，大家一起想解決方式

各種揪團，PTT、LINE、遍地開花的感覺

秒退地圖下面看到遍地開花的感覺，還是有些網友整理懶人包，讓不清楚議題的人可以看懶人包進入狀況。

地圖構想完全是跟跟藍委計畫致敬，就是我們的主持人林祖怡先生進行的。雖然細緻度差很多。

（比較圖）

滅頂要五到十年，不斷地制，經過賣場、便利商店，要一直克制自己不要買，長期、每天不斷在發生的事情。

主要是組織差異，滅頂是無組織的，但割藍委有一個核心團隊做資源統籌把資源效率最大化。

比較兩活動差異，割闌尾時配合選舉可以達到這樣的地步，公民聯署需要家投票，滅頂這篇要打持久戰五到十年，每個人要不斷去抵制，經過賣場要克制自己不要買這樣才可以去做，是長期跟每天都發生的事情，組織上滅頂比較像無組織，割闌尾有核心團隊進行資源將團隊資源的效率最大化。

割闌尾的結構，我心中想像的是這樣（圖）

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a8f935f3828d92dab36e91637ed26b40)


有管理員做資料驗證，發票資訊，確認沒問題才會正式登錄地圖裡面。技術部份都很簡單。

秒退就比較虛，大家都是靠網路上的分享。是分散式的概念。但有個好處，其中一個節點被超掉之後，還能繼續進行。但是資源沒辦法做有效率的應用，跟定比較高層的策略。



[秒退地圖](http://jimhorng.github.io/return_as_buy/)，有四大指標，頂新持股、董事會席次、資產（四個）
地圖就像實價登入地圖，點進去可以看到更細的資訊。

地圖淨資產想像是實價登錄地圖可以看到更細部資訊，紅色是最終秒退金額、幾次等等，對一般人來講可以找比較熱絡的點加入會找未開化地區發起。在google doc裡面都是開放的，可以讓做這個活動的人有種競爭的感覺，看怎麼樣衝比較高，也讓登錄比較簡便。

對一般人來講，可以看到附近比較熱絡的點可以加入。或是還有未開發的地區可以主動發起。所有登錄訊息都放在google文件，都看得到、可以做進一步的分析。

有視覺化資料、縣市之間排名，讓參與者有一點競爭的感覺。
不同的登錄方式、開放資料，為確保登錄是公平的，怕有人一次填十萬罐，怎麼可能，管理員就會做驗證發票、確認沒問題之後才登錄在地圖上。

技術就很簡單，都是開放的、大家常用的。最貴就是人力，工具都是不用錢的。

還有很多要填的坑。

最重要的事，不管你是服務或產品，沒有人使用，一切都枉然。我看這個活動花很多精力在做推廣。

PTT八卦版、有些粉專（靠北工程師、因帝大帝）各種推廣
有時候會踢到鐵板，有些人不想收到信，嗆聲要檢舉之類。

最後希望這個行動能成功，是能變成遊戲化的程度，導入等級系統，例如七個等級：（圖）
如果青銅等級是玩一玩就忘記了，更上面是願意不斷去秒退，可以扛著批評。

有訂一些KPI（但結果都是自嗨，都沒達到）。

滅頂之挑戰？
RPG是以個人戰績為目標，但是現在是匿名的。
如何把ＫＰＩ量化，例如味全營收不透明，要怎麼量化，都是問題

目前尚缺裝備：
秘密揪團系統（讓揪團更有效率讓揪團（需要私密的揪團系統）、總任務儀表板、每天狀態成長量、風向指標趨勢圖、開放專案量表

最後：「接下來就是我們的事了」
我的部分就到這裡

各位來賓大家好請容許我戴口罩報告，很像恐怖份子吼
大家一定覺得很奇怪，這個行動其實有些前因，好幾個成因共同組成，看起來像是無組織，其實是精心策劃，好市多退貨保證全球一致，要研究好市多商業結構，每一個環節都環環相口，生鮮食品一律銷毀，問題是回收利用，商業結構為我們所用

好市多不反對就是支持，繼續支持我們的話會員會增加，因為有商業門檻是會員制
再來新聞炒越熱，對好市多商業是增加的，要命中他的核心，他就可以為你所用
臉書觀察茉莉花革命他是最大推手，行動平台的串連跟發生的時候使用臉書可以變免因誤你的對手檢舉你導致整個平台當機，因為檢舉會讓你停權，發生會有問題

再來的話就是臉書有個爆料公社，這公社很好玩，會爆料很奇怪的事情，越聳動越想爆料，媒體懶得找新聞就會去這裡找，越聳動越想找
法綠層面民法345條買賣，只要雙方同意就成立

再來是好事多會員制，一百啪無條件滿意保證是雙方行為，只要有效就可以確定秒退行動繼續推動
再來是個資法保障個人隱私避免被對手起底，讓操作可以單像位記者新聞，可以操控主褲權

再來是行動規範，為什麼會有是因為三一八有大量奮青被激起行動力量，可以推動最困難部分就是民眾目光跟抵制，要簡單化、一致化才可以易於模仿，要符合情理法，要不然很容易被推翻。

行動原則上先建立大架構，社會運動論述是補術，要靠其他人完成

這行動最重要是靠臉書和google這兩個系統來免費發聲，這不是中央集權制的沒有核心，是一個變形蟲緻度收與放必須在行動一開始就明確定義

露出跟發酵的話，要先跟好事多確認到底可不可行，還要確認公司立場，這是事先確認過的，要玩就玩最大的，味全最大的產品是林鳳營，推動過程要想辦法讓行動露出易於模仿學習要儀式話，這樣人家才會關注，不然很容易被忽略

再來就是頂新集團，因為很大而且會買廣告記者法官，可是他有個東西沒辦法買，就是公民行動的良心跟憤慨，這是我們最重要的核心精神。

一旦發起需要串連各式各樣資源，臉書是很好平台。日本藉由拒用兩年，台灣沒有這個閒功夫，我們就必須創新改良他們的拒買，我們是秒退，差異在哪裡，秒退會有立即型損失，退貨銷毀避免二次加工，從三個月壓縮到一瞬間，導致財務缺口無限放大，一旦放大它的股價會立即影響，味全才會非常緊張，之前的拒買他都沒感覺，老神在在，一個秒退金額不大從地圖看只有兩百多萬為什麼這麼恐慌，會導致味全這間公司崩潰，要引起話題就是浪費，去驗證合法與否。

因為產生論述會引進我方力量繼續增加，發起時間點非常奇妙12/8是在12/12反頂新遊行之前，為什麼選擇這時間點，前面有總統大選，所有媒體把反頂新遊行壓住了，必須透過爭議性話題引爆他引起社會關注，因為三一八學運導致新世代行為模式，你知道他怎麼行為模仿學習，驗證你的東西是真的假的，要掌握才能夠做。

這個是他的首po，把退貨資料都放上去是讓他知道怎麼學習，所有動作都是為了學習，再來是利用媒體特性，只要他抓住我們從回應置入訴求去引爆這話題，這是秒退平台、懶人包
因為行動持續進行中會隨著法院判決民刑事求償部分會繼續發酵，請各位盡情期待，謝謝。





## ==謎之 g0v 開放跨界？Blupa 跨界量表與案例 / "Bluepa" Metrics and Case Studies for Interdisciplinarity: the Mystery of Openness and Interdisplinary in g0v==

題目改成：開放協作到底行不行
> 今天最想聽的part來啦~~~呼嚕呼嚕呼嚕
> [name=羅佩琪]

> 聽主題歌！！【謝謝恩恩書記官】
> [name=羅佩琪]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7baee51b81a50689ceb8097fff1a0312)

### IPA

今天想要分享開放協作到底行不行？真的嗎？行嗎？有時候覺得不太行，開放協作一直都是會聽到的梗，好像有些限制在裡面，到底能不能擴大參與、跨界合作是我們想要分享的一個點。

為什麼叫blupa，etblue想分享去ngo蹲點的事情，我們就跳坑了，產生了一個blupa量表，是一套思考開放社群跨界合作知間怎麼做會比較好的方法，幫助我們選擇比較好的開放模式。

自我介紹一下，我是g0v社群的共同發起人，我不會寫程式，拍過片寫過書，挖坑推坑跳坑，我是一個新手媽，兒子有參與量表開發。

為什麼要開放協作？現在這個時代問題好像很複雜，需要更多人一起解決事情，開放這個方法好像是不錯的可以靈活參與的方法，我如果進一步想會希望什麼樣的結果，這就是我的答案：如果讓更多人跳進來一起做事情，理性討論、累積知識、重複運用成果、擴大參與，又有效能，我相信越靈活會越有力量，開放也就是產生靈活度的重要元素。

第一個部分我會分享組織之間不同的方式，還是從g0v這個名字奇怪的社群開始談，這三年來開發了非常多專案，有些純粹寫程式，後面加上實體參與的專案，這些混種的方式創造出一些新的可能性，過程中也會思考社群和組織，社群是去中心化的，和組織有什麼不同，拆成幾個面向來看，為什麼會來，為什麼做這些事情。

社群裡面理由很分散，你不爽就做，做了就爽，做了之後不想做就離開，組織就有比較一致的動機，誰來做？社群比較多元想來就來，先承認你是沒有人的沒有人，每個人都可以來。做什麼事情？因為去中心化的平台，比較模組化，把他講成是坑，比較能想像的單位，其他組織性的組織會有不同單位，how的部分怎麼樣去做，這是開源社群很重要的推動力，到底怎麼樣去做出這些事情？

這個動力就是開放，先開放授權我的東西別人可以用，在開放參與，可以在開源社群常常聽到勸人跳坑的話術，例如做了就趕快丟出來，想做什麼就丟出來，可接力。那什麼時候完成的時候，有時後開源社群就很悲劇，可能下次或再下次黑客松。

這兩個羊粗左邊從重度到輕度都是比較開放的，how參與方式都是開放的，比較有可能到爲參與者，很多社群會有一種事情發生，有人提了東西就超展開，這是為什麼g0v有這麼多人，我們會宣稱g0v在全世界開放政府的光譜非常大，但這不是我想講的重點，我想講的是這個==but==，在這個領域有三個雷區，一個是太展開、逆展開、沒展開。

太展開是可能一個專案便成三個最後做不出來，沒展開大部分是這樣沒做出來，逆展開可能政府退縮或事情推到更之前的狀態，卡關之後開源社群需要更多方式來跨界，運用開放方式跨界，需要釐清哪些是開放。

一個案例是政治獻金數位化，這是需要很多人參與的案例，把資料變成數位、資料讀取，這是一個典型開放專案，中間紅色是跟ngo組織協作，第二個專案是罷免立委，剛剛主持人就是主持這個專案的坑主，一個組織自己先關起門來討論出一個具體策略，到開放社群例如g0v來提案，找到開發者讓開發者作出讓更多微參與者參與的平台，這就是一個混種，可以靈活把決策部分封閉起來，可以專心做決策，最後結果也有時間控管，不是全部都發散。

今天現場有很多是開源拓荒者，用開源的做事方式潛入到各種單位，有人在社運組織工作，有些在新媒體實驗，做了分析之後有個表，這個表有點像是心理測驗，我們可以分析透過時間、費用、複雜度這些元素來考量，如果你手上的事情比較像是這行綠色自，你可能比較適合選擇開放方式，不是的話有死線要花錢有實體活動，可能比較適合紅色是不開放的。這個測驗可以上網看去選擇自己的分數。

最後很快想要分享一下，你們之後可以看很多的表，重點我們想要傳達開放或封閉收起來或是需或實，應該是收放自如可以虛實合一的，像現在一百多人是紅心的型態不像傳統g0v是所有人都可以，我在跨界的混種碰撞區有更多想像出來，這些新出來的東西如果是開放授權，即使我們剛剛講那些雷區都有留下一些痕跡，這些辦成果或共筆都可以重複被利用、分享，例如割闌尾成果後來在氣爆、塵爆又變成捐血平台。上半節到這邊。

> ipa的part太讓人共鳴了~~~~~~
> [name=羅佩琪]


### ETBLUE

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e7b7c453388b52687773902a707ff7d3)

大家好我的ＩＤ很好既就是對應中文名字，反服貿佔領立院後才跟公民團體有比較深戶動，今天內容主要是從網路星期二演講衍生出來( 應該是這場 [http://nettuesday.tw/events/2015/05/486](http://nettuesday.tw/events/2015/05/486)  )，有興趣可以從投影片點進去看。

投影片(?)：[https://g0v.hackpad.com/ep/pad/static/blupa](https://g0v.hackpad.com/ep/pad/static/blupa)

IPA講了一些概念，實際上跨界專案怎麼進行呢？有四個部分，會先講用什麼方式分享跨界專案，再來會講兩個案例，最後是心得。

分析方式是blupa量表，專案部分首先我們會檢查專案的體質，看體質是比較開放還是封閉，怎麼檢查就是從時間費用複雜度數位性模組性通用性公開性來評分，整個總分加起來分數越高表示體質越不像是典型g0v專案越不開放，檢查完會看實際進行方式跟體質知間有沒有什麼關係，會把專案生命週期的問題企劃開發營運分開來看，封閉紅色開放綠色中間黃色，還會看他的進展時程，什麼時間會抵達生命週期的哪個階段，很順利的上去還是一直來來回回卡關。以上是坑的部分。

人的部分會把不同程度參與者協調人重度輕度拆開來看，
假設很開放會飆呈綠色，有些標成紅色，中間黃色，最後會看參與者成分，最上面是個人最不受到法規制度數斧，再來是社群，再來是民間團體，最後是政府，束縛最多最不自由，以上是分析跨界專案的工具。

**第一個案例：**13年反服貿運動剛開始要協助ngo做網路宣傳就做的插圖


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_17318a718ef18e63f3ad275b0e109738)

圖上很多小人所以叫做服貿小人圖，因為時間要配合運動團體時程，有個明確的死線，時間是紅色的，費用沒有就是阿宅窩在家裡畫圖，需要插畫家跟議題工作者，複雜度中等，數位化程度就是電腦繪圖，模組化程度很低，小人角色都是為了服貿主題特別設計，通用性也算滿低，進行過程牽涉運動詛織策略所以不是完全公開，公開性在中間，全部加起來總分八分介於中間，
開放度體質算是半開放跟半不開放狀態。

實際上如何進行？賴律師一個人默默分析兩岸經貿問題是紅色，企劃是黑客松才產生插畫專案，我們放在google drive也有信件群組所以是黃色，最後營運是放在g0v public所有人可以下載優改是綠色，從構圖完稿總共四天，參與者大多是用開放方式參與，少數是跟ngo參與用半開放，除了公民團體和g0v還有素昧平生的推有來參與。以上是服貿小人圖專案。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_891ebb820876d43daa696aec2644cad0)

第二個例子是14年發生佔領立院，佔領現場要做直播需要網路，有批工程師就跑去架戶外網路，這個叫線路松，拉網路的黑客松雖然大家都是自主參與，情勢滿緊張的對自己要求很高，不太允許斷線狀況發生，時程是紅色的，裡面有些網路設備是滿貴的，但對於工程師可以負擔是黃色，需要參與排班牽線複雜度也是黃色，後面幾個都是紅色，加起來12分已經距離一般g0v專案非常遙遠，他天身體制是不開放的，這樣紅通通專案如何進行？

大部分時候是用黃色半開放方式，核心是封閉的方式，時程要配合佔領現場狀況，需要重新規劃拉線，產生這個崩潰的曲線，參與者部分大多是用半開放方式，核心的協調人是封閉方式進行，雖然這是非常組織化的中央集權專案，但參與者大多是非組織社群或個人。以上是立院線路松專案。


看完這兩個專案可以歸納出一些心得，首先跟專案體質也就是0-14評分表，如果分數越高表示專案先天越不開放，大家就自然而然選擇不開放方式執行，即使是一個不完全開放的專案，生命週期裡還是可以找到環節借用社群力量幫忙，通常複雜度整合度越高的專案，越需要大量溝通，過程需要在企劃之間來來回回，你手上專案如果有鬼打牆狀況表示你在做很偉大的專案。

跨界專案參與者組成可能是外圈封閉內圈開放，也可能外圈開放內圈封閉，case by case，主要影響專案進行方式還是先天開放度體質，一開始想做blupa量表的時候想說做一個像分類帽的東西，把專案參數丟進來就知道身為開源人如何跟封閉組織合作，後來實際做出半頂分類帽，前面講專案體制開放度量表，即使幫專案評分知道體質開放封閉，還是不知道適合用什麼方式進行，因為跨界混種實作方式太多元了，可以做的就是盡量收集各種跨界專案。


如果你手上有什麼跨界專案可以到[http://](http://g0v.hackpad.com/blupa)[g0v.hackpad.com/blupa](http://g0v.hackpad.com/blupa)，blupa處於alpha接段，有什麼想法歡迎直接在上面comment或留言，這場議程處理主要是跨界本身要怎麼做，至於成功跨界之後又會遇到其他問題，明天下午家華會跟大家分享，特別感謝peggy雨蒼家華.....2016summit工作人員。

最後有一首主題曲：[https://blend.io/etblue/blupa](https://blend.io/etblue/blupa)
> 也太好聽了XD 好洗腦
> [name=Ann H]

> 腦袋會被清空啊
> [name=雨蒼 林]

> 這一場真的聽了好感動啊
> [name=羅佩琪]


Ｑ：不知道為不會讓量表複雜化，評分項目會不會重要性不一樣，比如有些死線非常重要？項目比重不一樣？
Ｉ：你可以來改良表
Ｂ：012是大概分法訂的很粗，是希望大家注意顏色，才不會本來很質性的東西變成量性，也許之後可以用色票的方式呈現，beta版可以試試。

Ｑ：不知道小群組裡面有幾個人，一開始是否關心很不錯會合作，假設有天關係變換不能一起合作，誰可以接待，會交給哪些團體，還是暫停？
Ｉ：因為是開源極端份子，最後結果都是授權大家使用，只要事先溝通好，有些專案是cc0完全放棄授權就是公共財產，很多專案是這樣，你也可以選擇不要，交惡的時候就會有類似問題。
Ｂ：我可以回答你的問題一部分跟ngo合作他們走了怎麼辦？如有件事情大家覺得重要人就多，議題不太重要可能就找不到合作對象。

> 下一場交給其他人接手可以嗎><  感謝～～～
> [name=Ann H]



## ==如何推廣公民科技給非技術宅？ / How to spread the civic tech movement to non-techie people?==


首先先自我介紹 我是Shigeomi Shibata

水戶和次成在東京郊區，水戶也是日本納豆很有名的地方，東京是首都在正中央，所以城市當中我們有個叫做德川的基地，是幕府時代重鎮，日本國圖中央也可以看到日本傳統食物相當盛行，納豆＿＿＿＿是醬油煮藥進食，在台灣有類似的食物叫豆腐，今天主題是如何把公民科技散播到非科技背景的人，我改的比較簡單，因為訂定議題時其實當時跟39個不同的社區團體正在做，還有其他20個比較小的團體，總共60個小的科技團體聯繫，在code for japan我一直在想

背景是一樣但討論時用同樣語言或討論很技術層面的東西，可是對一般人，我們的世界很少人瞭解，想為社會做事情時非科技人常常不了解我們在做什麼，我一直想解決這個問題，不同領域溝通問題，讓理念技術傳達到非科技背景的人身上。這是為什麼非科技專長也是我們非常珍惜的，希望能邀請像ngo或其他單位跟我們一起合作。

How to spread the civic tech movement to non-techie people?
But ...Does this theme or problem is right question?

我一直在想這些團隊背後的意義，當中有一個委員會, 開始懷疑一個問題，我所設定的主題是一個對的主題嗎？還是本身就是一個問題？想藉由這個機會做分析分享。

日本最南端有個城市叫鹿兒島，在日本國土西南方，鹿兒島最西方還有一個地點叫做肝付町，城鎮形狀如地圖所示。當地有一萬六千居民，居住當地是非常大城鎮，

自北至南車程約2hr，人口不算多, 所以不太有交通堵塞的問題
。居住密度很低，每平方公里50個人，和台北相比起來，台北是該地的200倍。
每平方公里50人

許多年輕人外移，去找更好的工作, 當地剩下的都是老人，工作機會變少， 因此面臨到的是人口不斷減縮, 從十年起就以每年一萬人的速度減縮。日本已經老人化很嚴重，這個城鎮更嚴重。日本65歲以上佔全人口25%以上。該地比率則更高。

肝付町有個火箭發射場，和控制用的天線塔台，位在海邊，山海夾雜的城鎮，旁邊有公路。

多數居民年齡介於65-79歲之間（看圖），右圖是日本2060年的
肝附町就是50年後的＿＿city
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f9c1a015fa216516df76f33fd8a8cdb0)
老人想要多跟其他人交流，因為他們住處都相離很遠，他們走路也不方便，他們就只能孤單的在家裡

老人認為嚴重的事情才能打電話，所以在他們的觀念中，講電話長舌是不對的。所以我們沒有太多方式可以和他們談這個議題或支持他們。最大的問題是loneliness孤單/孤寂，

老人並不一定每天都有重要的事情打電話, 另外還有一個方式, 是他們可以用skype, 視訊, 平板, 手機啊, 但是老人根本就不會用這些新的產品。在這個情況下要怎麼解決他們的問題呢??
沒有kpi或科技方法解決，老人無法決定自己要做什麼或不做什麼，我們是否有責任幫助解決問題？


The problem
How to cope with this real though situation?
What can we do as a civic hacker to support them?

為什麼我會把這

這個機器人叫做pepper，是由法國公司Aldebaran 所開發，後來由日本電信公司softbank推出
在這種情況之下, 日本的老齡化的客戶, 就開始期待人工智慧的發生, 但是機器人的開創者, 他認為這個機器人有其他的任務, 因為目前人類對於老齡化社會並沒有一個解決辦法, 所以他希望用這個機器人可以娛樂老人家或是定期拜訪老人。因此它不只娛樂老人家, 小孩, 也可以娛樂成人。
我們可能覺得它不過是個機器人, 但是pepper 的智力其實就像是小學生或是中學生, 但是它只要被教育就可以學習。我們可以看到幾個人圍著pepper 想要互動, 看起來很好玩, 這樣子的工作坊舉行了很多次。有沒有辦法創造出更多像pepper 這樣子的機器人, 讓它可以解決人類無法解決老人化的問題。


有一天機器人如果完全沒有原因的壞了, 要修理他的方法只能重新開機, 要花超過一個小時等它開機完。但在這個地方一個小時以後, 我們沒有辦法確定這個城鎮裡的老人家可以忍受等待一個小時的時間。所以一個小時會是對於老人來說很重要, 獨處忍受的一個極限。

Not using techie word. It can not be understood, this information is not an information.

find a key driver person.
not from the structure, but from the flow.

這句話指的就是剛剛的機器人, 第二點我想要說明的是, 找到一個重要的人, 就是一件重要的事, 幫助我們做重要的決定。他們本身不是科技人, 但是他們跟客戶的關係良好, 也了解議題的本質, 所以總之我們是要從大眾當中獲得結果, 結構不過只是計畫的框架而已。確實計畫沒有框架的話沒法形塑, 但是框架要調整多次, 不過如此做就讓人失去動力, 所以要讓框架調整的次數減少。
（回到前面的投影片）
How to spread the civic tech movement to non-techie people?
But ...Does this theme or problem is right question?

要如何讓公民科技散播, 或許這個主題有點傲慢。我們應該要去考量到客戶的想法, 他們的議題要納入考量。

"A problem is a difference between things as desired and things as perceived."
by Gerald Weinberg, "Are your lights On?"

如果今天解決了一個問題, 後面會有接踵而來的問題, 所以不斷的解決問題, 才是我們正確的心態。公民科技是未來, 而且可以創造更好的未來。



---
title: "[R1] 藍圖 / Blueprint @g0v Summit 2016"
tags: hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/UFvxbyoxsL4)

### ==線上即時提問：Slido.com 輸入 514==

Audience question collection online: Slido.com enter 514
傳送門 / Direct Link： [https://app2.sli.do/event/xxxrdr7t/ask](https://app2.sli.do/event/xxxrdr7t/ask)

拼湊政府公開資料的圖像，數位代議民主的轉型與未來 /Towards digital representation: A jigsaw of open government data endeavours
主持人: 唐鳳

more info: [g0v Summit 2016 hackfoldr](http://beta.hackfoldr.org/g0v-summit-2016/)
現場直播網址 (live url) [http://summit.g0v.tw/2016/live](http://summit.g0v.tw/2016/live)


↓文字轉播、線上討論↓

## ==用 EveryPolitician 的資料，來增進公民科技重用 / Powering civic tech reuse with EveryPolitician data==

Bio
- Jen is the International Projects Manager at mySociety. If you email international@mysociety.org, Jen will be the one who responds to you first. She lives in London and works directly with organisations anywhere in the world, helping them with the practicalities of deploying our code and maintaining the resulting websites.
- With a background as a working on media development and broadcasting reform projects in the Middle East and North Africa for BBC Media Action, she’s used to pitching in wherever needed for all sorts of projects.
- Jen travels widely to meet our partners on their home ground: it’s always helpful to see our projects in the places where they’ll be deployed, and meet the people who will be using them. She’s passionate about ensuring that projects meet local needs and spending time with groups in their own countries helps her start to understand their motivations.

Abstract
EveryPolitician 計畫，透過群眾外包蒐集許多資料，例如世界上每個國會的性別分布。為什麼我們要收集這些開放資料？它們如何被利用在不同的媒體上？我們將以各國驅動公民科技的網站，來展示資料運用的真實案例──希望可以鼓勵大家，做出新的創造！

EveryPolitician 的故事
兩年前 Tony 想建立一個工具，查詢議員的紀錄
已有開源的格式已經存在了，當時
目表：所有世界上議會成員的資料，使用一致化的格式

[http://everypolitician.org/](http://everypolitician.org/)

找不到的資料是沒記錄或是不開放
格式 json csv 沒有 API
學生記者使用 csv
每天讓人寫爬蟲程式，幫助全部
現在請人幫忙找資料來源，自己寫爬蟲，因為長久之計很麻煩

可使用 EveryPolicticssBot
[https://medium.com/@everypolitician](https://medium.com/@everypolitician)
[https://github.com/everypolitician/everypolitician](https://github.com/everypolitician/everypoliticianbot)[bot](https://github.com/everypolitician/everypoliticianbot)
> 有誤請更正
> [name=Tsai M]


我們希望有更多的資料來源，吸引更多人來使用我們的資料

Data Layers
我們希望取得歷史資料


許多國家利用EveryPolitician建立了自己的工具：
ex: 表決紀錄網站。
幫助烏克蘭了解資料

PMO （Parilment Monitor O ?）
烏干達、辛巴威

利用聯絡資料建立工具讓民眾方便聯絡
odekro
使用 mySociety 的工具
從此工具使加納議員的高缺席率現行

gender-balance.org
立法機關性別比的交叉比較，看台灣的資料並跟世界做比較
（也能夠看出性別平等的程度）
這些多元的應用也是讓我們感到興奮的原因。

More accessible data = more standardtion


What is Next
需要資訊來做研究，還是提供資料


Q&A
Q1:大部份是手動還是抓取的？Where do those politician data come from? Key in manually or scrape automatically
A1: 從政府網站或是其他人給的資料，雖然有同步但他們

Q2: 網頁如果格式改了呢？多久調整一次?
How often do scrapers break? What's the cost of maintaining this database?
A2: 我們沒有建立資料庫，只有JSON和CSV的格式
因此維護成本低，上述資料格式可作為快照，很快就可以取得。
我們每天會維護爬蟲，有兩個人會注意爬蟲的運作，以及格式

Q3:From the Panama papers, we know that politicians use delegates to open offshore accounts. Do the data include politicians' associates and family members?
A3: 我們沒有議會成員以外的資料，下一步希望有一個。

Q4: 如果資料內容有錯呢？有何機制？
How do you sure that the data is corrected or not? Is there any validated mechanism?
A4: 我們不太會確認資料格式，關於這問題我們可以找同事 Dave 來回答，歡迎來 Call Out

Q5: 有無方法讓政府有動機整理資料成你們想要的格式？
A5: 很好的問題，會有那些政府會做呢？不確定，但希望他們能公布能給，希望當前的議員監控網站可以建立有公信力的資料，以前英國政府有迫使他們提供議員資料，因為我們逼迫他們很多次！希望用此模式，用在地經驗建立網站，要政府提供資料。

Q6: 中文名字因為拼音高度重疊的問題要怎麼解決？
A6: 我們會辨識資料（目前無法解決？如果你們可以幫助我們作拼音-真實姓名之間唯一辨識的話，歡迎聯絡我們）

Q7: 有多少人會管資料方面的解析度
A7: 目前有 5 個人，Tony 更新爬蟲, crays 管理網站

Q8:可以展示一頁資料看看嗎？
A8: 如果要看 JSON 可以休息的時候找我，

Q9: 有多少人監視我們的資料
A9: 想用就用，我們沒有監控使用過程的機制，（有謠傳有人用我們的資料辨識巴拿馬文件，但即使如此我們還是沒有對使用過程作監控）

(現場發問)
Q10: （聽不清楚 ...）
A10: 只要享用我們都可以用

Q11: 資金來源
A11:

Q12: Politician transfro (有沒有標準做政治家產銷履歷（？）？)
A12: 目前沒有計畫，因為目前拿到的是比較表面的資料。未來如果有比較詳細的資料可以進一步作這方面的認證。



## ==公民科技監督國會：長久之計 / Civic Tech in Monitoring Legislatures: The Long Game ==

- Abstract
    - 公民科技領域裡，所要解決的問題常常是近在咫尺：修理人孔蓋、監督政府、公開資料等等。而我們因此創造出的工具，常常能立即為使用者產生價值。但這次我將分享一場持久戰的故事，要到五年後的現在，好處才開始浮現。
    - 這個故事是世界各地的組織們，如何建立一套軟體元件架構，來監督立法。這是從 2011 年在華沙所共享的一個願景開始的。2012 年，開始了資料互換格式標準化的工作，建立了軟體元件之間的協定。有兩個組織在 2013 年裡，開始用這個格式撰寫後端資料管理工具。2014 年，第一個能面向使用者的工具，出現在堆疊架構的頂端。而在 2015 年裡，因為有更多易學易用的工具流通，政府們終於開始採用這個資料標準。
    - 這段旅程將會造訪世界各地許多組織和計畫，從 mySociety 到 OpenAustralia 到 Sunlight，和從 Poplt 到 Councilmatic 到 Represent 等等。這段旅程我們已走了五年，而仍然有許多路要走。在我們徹底解決的立法監督的基本問題，讓它成為理所當然的事情之前，還要花上許多年的光陰。
    - 這次的報告和「拆後重建」題材有關。立法監督的網站，通常包含從官方網站拆出來的資料，並且重新歸納出整合式的資訊。經由政府採用像是 Popolo 這樣的資料標準後，我們就能免去砍站的程序，然後將良好的資料發布守則，重建成政府的一部份。
- Biography
    - James McKinney regularly contributes to civil society initiatives relating to government, legislative and corporate transparency. He is currently focusing on Popolo (a set of legislative data specifications, used by parliamentary monitoring organizations and members of Poplus.org) and on Influence Mapping (a group of organizations that draw the networks of relations between politically exposed people and organizations). James is especially interested in how data standards can facilitate cooperation between organizations and individuals.James previously founded Open North, a Canadian nonprofit that creates websites to promote government transparency and public participation. He is co-lead of the Open Government Partnership's Open Data Working Group's Standards Stream. He was a member of the Open Contract Data Standard core team and of the W3C Government Linked Data Working Group. He has presented on open government and open data, most recently at the International Open Data Conference, Canadian Open Data Summit, and Spaghetti Open Data.

[http://www.popoloproject.com/](http://www.popoloproject.com/)
唐鳳：我們希望藉由建立資料標準格式 的工具，希望全地球有統一的格式互相交換，讓這些朋友們 5 - 10 年長久使用
（命名為“藍圖”意旨：為了未來而作，像是水和電一樣，讓十年以後的人可以自由使用）

我在做資料標準
Data standard
用**標準程序**，讓爬蟲不再麻煩，我們來看

web scraper
一個直接存取網站資料的爬蟲，這就是爬蟲所做的，爬蟲可以自動將網頁上的資料提取出來，公民科技目前的樣子是長什麼樣子？我們可以用這個來作例子，如果你輸入網站上的位置，可以看到地方議會的代表以及如何聯絡他們，甚至政治人物的資料，所以可以從這邊取得資料，我們從幾年前看這個資訊，但我們發現並沒有議會可以用可讀取的方式，但我們有爬蟲、黑客松的方式，用爬蟲的方式進行執行，用多種程式語言進行爬蟲，我們維護了數個爬蟲，但維護爬蟲在不同的格式或者是語言(php python ruby)是我常常看到公民科技，並且經過修改之後有各個優點，並且維護的時間一個月一天就可以了，這個我常常看到的模式。…所以寫了更多的爬蟲，建立一個工具組讓你的○，但最後會花許多的時間來修改那一些scraper…，這一些爬蟲的計畫未來的狀況是什麼。2035年我們在火星上住了數百萬人，但○還在修改scraper，我們要如何避免這個狀況？AI、群眾外包及資料標準。

如果是AI我們可以訓練機器人，我們目前沒有看到人工智慧百分之百來辨別這一些資訊或者是…，這個是可行的方案。

第二個方案是**群眾外包**，唯一的前提是如果沒有很急著取得這一些資訊或者是最終不會取得資訊或者是你的任務本身規模不大，比如維基百科，最終會替加拿大更新他們的聯邦及省級政府代表的名稱，但並沒有地方政府議員的名稱。第一個問題是AI，我們把這個任務一起做，或者是把任務發給人類做，如果是資料標準的話，把難題丟給政府，是一個很明白的解決方案，因為政府已經在公布資料了，但並不是標準可繼續讀取的。如果他們是以CSV格式的話，我們要讓政府公布這一些機器可以讀取的資訊，人民就可以去使用它。

像我們可以聚焦在我們的能力，聚焦在我們想要做的事，比較少人在做這方面的工作，所以現在我要進入到我的資料標準之前，我要先告訴你們光從政府取得這一些機器取得的訊息還不夠，舉例我們現在有政府用不同的標題，你就必須要把每一個讀取，然後整理出一套標準。再舉一個例子，我們做（）影響地圖，許多的組織都在建立系統，他們希望給人民力量，給予有這樣的訊息可以使用，這是其中一類的組織。

假設我想要找出關於我的PM的訊息，例如像圖片裡面看到，你就必須要去這一些網站讀他們的文件，找出怎麼樣去讀取這一些訊息，你需要寫信給他們讓他們回覆你，同樣你在這一些網站上得到想要讀取的訊息，為什麼要有這樣的（），所以你就寫出一個需求的訊號，它就找出這個訊息。這個功能還滿好用的，因為我不需要根據這個再去寫出所有適應的系統來讀取不同的網頁。

如果API的話就不需要多做一些功夫來取得這一些訊息，接下來是如何讓政府採用你所提出的標準呢？你要如何讓政府公布說這一些當選人候選人政治人物的資訊，像2012年有人問我需要使用什麼樣的資料規格？我就給他我的規格，他就用這個規格來公布他的資訊，但是只有一個政治人物是這樣子跟我溝通的。在一段時間之後，我拿到一筆資金去推廣我的想法，我們就準備了一個頁面像是這樣（如PPT）我們也根據這個格式來製作網頁，我們把這一些訊息跟開放的組織合作，所以人們比較清楚我們推廣的是什麼。

我們再把mail連結寄給會眾，就會開始出現一些人利用這一些格式，接著有人對我們反應到目前為止這個月，像隔壁這個誠城市或者是這個區域或哪一個地方採用這樣的規格，因此讓更多的地方一併使用這樣的規格。

在過程之中我們去看看這樣的訊息、格式是不是有比較多的人，像加拿大來說有62個地方開始使用，總共有23個議員、人民代表也開始使用規格，如果可以讓這個數字上增加到60幾個的話，會是更好的方式，就訊息跟人民的人口來說，這部分其實我希望再更廣泛地推廣，在過程之中我們全部的工作都是透過mail來完成，也許你會覺得很奇怪，但這最終可以促成我最想要的目的，這是我從事的其他活動。

可以看到這邊都是有參與的（如PPT），所以我需要用社會正面，像是告訴你的朋友參與什麼活動，我們有二個使用器，也可以讀網路上的訊息。第二個是最好有朋友在政府內部，因此在從事這些活動的時候，可以把這一些訊息帶開公開訊息，在過程之中可以知道這一些訊息得到是否足夠，如果不夠的話，是不是可以再進入更細節的訊息。再來就是需要找一個朋友，如果有朋友告訴我們想要告訴你的訊息，可能比較容易去傾聽，也就是建立一個動能有做事情、有動力，所以要告訴政府說現在有一個新的適用性，然後再說上一次做了什麼事、帶起什麼活動，再來就是讓你的訊息出現在各個不同的平台，而政府也有在使用。舉例來說：像在加拿大你在墾伐樹林，環保組織會很反抗，他們在高速公路上買看板，可以知道反對的聲音，利用媒體、新聞或報紙來傳遞他們的訊息，這一切當然都可以創造出這個現象，也就是這個議題是非常熱烈討論，因此需要一個動能、需要創造出來，至少要呈現出這樣的現象；當然你可以寫一篇文章、製給政府，讓大家注意。

再來你也可以在地方政府的網路，在他們的會議提出你想要發的聲音，即便是政府沒有在讀取你的訊息或你寫的文章，至少你會找到他們，在跟他們見面時，你比較能夠知道現在你可以跟他提出你的想法。

下一個策略是同儕壓力，在訊息傳達當中我們可以知道哪一些城市、哪一些地方使用資料標準。

因為小城市會想是大城市才會採用標準這一種東西，或是可以跟小城市說其他小城市有在做一樣的事，這會幫助我們的推行，另外一個策略是用我們的名聲，（）在加拿大算是享譽盛名，如果沒有人的話，可以讓其他人或其他組織幫你做這一件事，可以幫你背書，他們的權威即使沒有參與活動，也可以幫你說服。接下來你必須要有禮貌並且提出你的幫助，這有一點爭議性。如果你在爭取政治獻金當中的透明性，你可以有一個進取的態度，但如果一個國家、一個政府公布所有的資料了，你想要他們使用標準資料，你就必須要用不同的方法，也就是要建立一個合作性的環境，可以透過溝通並顯示你是有好的想法、你的出發點是好的，你是非常瞭解當地的狀況為何，並且採用資料標準的困難處要釋出善意，也許你很希望我們致力於一個共同目標來前進，可以讓更多人來使用這個標準。

在接下來的訊息當中可以告訴政府說「可以幫助你們嗎？」，而不是「為什麼這麼久還沒有採用我們的標準？」，接著是我早期有提過其實內部有幫助的，但其實政府不太會聽內部的人，我跟內部知情人士聊，我會將他們的好點子發布在新聞當中，將這一些消息跟政府講，如果你跟政府機關一起合作的話，你可以跟政府人士說一些體制之外人的好點子。並且，另外出現一些證據為很多人在使用你的資料，政府會怕沒有人會使用這個資料，但其實像（）這個計畫就是數百萬計的使用率，而且許多人都知道這個計畫，但你想要讓政府採用你的標準，比方我當初在跟地方政府合作時，我從PDF上截取資料，並且建立一個滑冰場的地圖資訊，其實當時就引起政府的注意了，你可以建立一些小的，但它是足夠的，因此可以顯示這一些資料是有用的，如果這一些資料當初沒有存在，你可以從其他政府取得。

接下來還有二個策略，第一個是「尊重政府的需求」。比如在建立資料的時候，你在資料表標頭上。抱歉，投影片出了一些狀況，可以了，照片又回來了，剛剛有看到。

尊重政府的需求，我們必須用可以繼續讀取CSV的格式，用特定的名稱或者是用正確的檔案格式，因為人類是人類，需要正確的方式使用資料。最後一個策略是「截止日期」，可以用標誌性的活動來督促政府，只要在政府在某一定的時間內達成目標就可以督促其他的政府。而且有截止日期的好處是讓政府知道、進行他們所謂的採用資料的標準動作。

我們來看看如何監控立法機關及到最後來談我本來的主題[POPOLO](http://www.popoloproject.com/)，比如立法委員講什麼話等等，我們看到這一個人在POPOLO的格式是這樣子（如PPT），等一下的系統就會長這個樣子。在2012年…每一個人都有自己的想法，但並沒有分享他們的編碼，如果沒有這個編碼的話，就沒有辦法做出反應，舉例來說像臺灣政府，把這一些資訊分解成小的部分、小的單位，然後這一些單位可以再被分開使用，但就在這個時候，這只是一個想法，當時在會議這樣提出，接下來在2012年的時候，就開始建立一個網頁來監督我的地方政府。我當時在尋找這一些資料的規格，而是而是看其他人怎麼做，我就看到W3C，W3C有一個會員、組織，我就加入他們，開始看他們的用法，我就採用這樣的工具。同時我也做一些研究，當時找到有各式各樣的標準，這一些標準其實沒有辦法滿足當時的需要，所以我就開始再去找出有沒有一個工動的標準，幾個月之後，在2015年早期 myScoiety 與 sunlight 得到了一筆資金，也就是…提出來的一件事，很感謝的是早期我所做的工作變成了[http://poplus.org/](http://poplus.org/)，接著這個工作就被其他的組織接手，接著在2014年的時候這張是智利的照片，這個是對國會監督的工作，當時我們想要知道的是如何透過這個工具進行我們的工具，當時我提出了POPOLO，當時也進行了國會投票，當時要求他們使用這一套標準。

2015 事情很順利，當時使用 mySociety 制衡很多國際組織及國家，其中有一個是來自於歐洲的NGO採用了POPOLO，當時紐約與芝加哥使用這工具緊接著澳洲、歐洲也採用˙…當時我想要做的一件事是想要建立監督政府，其他這一些組織有採用了我所用的工具。我想要留一些時間進行Q＆A。

工具有時候複雜是因為世界本來就很複雜，在很多狀況上也必須進行更多的研究，接著是為什麼要建立在前人的工具，也就是他們所做的工作多少有一些可信度，你就不需要再進行二倍的工作，如果接手做的話，也會認為這是你的想法，而是一群人是有可信度，我的意思是現在要建立一套系統，其中一個策略就是人們會去使用這一些開放的資訊，當然你如果去採用這一些訊息的話，像採用POPOLO可以馬上得到這一些好處，可以再將這一些訊息輸入到其他的軟體。例如：你的訊息是可以轉在別的地方使用，像在城市採用這樣的系統，就可以採用POPOLO訊息去整合起來，下一個訊息是找出你的問題底端在哪裡。簡單來說是建立一個工具，而工具可以收集訊息，再透過API來公布，而API會接著去利用，這些人其實不太在乎這一些格式是什麼，因為這一些訊息是可以輕鬆被讀取，但用API不論你用多少工具，其實他們不太需要知道POPOLO，所以很多人不自覺就在使用。

更重要的是像一些會議，你需要在這些會議裡與其他人一起合作，所以我覺得如果沒有到處去宣傳的話，POPOLO今天不會這麼受歡迎，。另一個策略中 （），2016年我不是標準格式的專家，但我接手了一些工作像mySociety Sunshine Society 。2012 年我開始工作，政府也採用這個標準，中間我進行這項工作沒有很久但大家認為我應該是專家，如果認為我應該要建立專長的話，應該跟其他的組織交流，如果希望可以有這一些訊息跟他聯絡的話可以跟我聯絡。我現在說的訊息是重要的，為什麼要適用（），在過程中是不是需要別人的認同，但我今天想要說的目標就是在scrape這一件事是很好的幫手，你需要企劃時你當然要專區這一些訊息，所以scraping是好的，如果你要建立網頁，而是要長期監督政府的網頁，你可能會想說要如何去找出一些共同的標準，然後去從事這一項事情，所以要做的事情很多是利用這一些共享的資源程式編碼，就長遠來說你要如何去寫編碼…

Q&A
Q1: 標準化的資料如何處理？
A1: 取得共同的資料元素，例如姓氏，不同物品最長的名稱是什麼？使用方法是什麼

Q2: 各種標準程序已經建立，但是後可以讓全民參與還是只有政府可參與？
A2: 如果能發揮監督，有很多細微的特徵需要去處理

Q3: 需要標明某些部分已經是「機器可讀」的嗎？這是有幫助的嗎？
A3: 現在有多標準如JSON 可以讓大家採用
例如：姓名。目前還是需要人工辨識。但我們可以透過「微格式」來將某些部分確定下來。

Q4: 公部門要從私部門拿資料什麼方法嗎？
A4:

Q5: How do you work for that? 若線上沒有紙你該怎麼辦（僅有實體資料、無法上網查到）？
A5: 需要有類似 "[開放政治獻金](http://campaign-finance.g0v.ctiml.tw/)" 的方法來 OCR 整理資料 —  Jen

Q6:
A6: JSON-LD 格式


## ==morph.io: 國際公民科技社群建立的資料抓取平台 / morph.io: the international civic tech scraping platform==

- Abstract
    - OpenAustralia 基金會主持多項公民科技專案，有幾十萬人使用。「拆解網站資料」對這些專案來說，是不可或缺的。每次寫一套砍站程式時，我們都面對同樣一系列的問題──要在哪裡跑程式？如何儲存和取得資料？如果出現問題要怎麼除錯？這就是為什麼我們建立了 morph.io──為國際公民科技社群打造，自由開放源碼的砍站平台。
    - 有了 morph.io 後，程式碼就會留在它該待的地方──GitHub 上。我們支援 5 種最流行的程式語言，好讓你可以用自己了解和喜愛的語言來砍站。程式會依照自定的排程在雲端上執行，如果有任何問題，就會用電子郵件通知。資料可以下載成 CSV 檔，也可以用簡單的 API 來做 SQL 查詢。
    - 在這次的報告中，我將會介紹 morph.io，並且展示幕後的運作細節。然後我們將會從幾千個現有的砍站程式裡，挑幾個來看看它們如何彙集數千萬列的資料。最後，各位如果想知道如何動手砍站，來建立下一個公民科技專案，我會提供一趟旋風式的導覽。
- Biography
    - Henare was goaded into his first ever open source contribution in a chance encounter at a free software conference 7 years ago. Hacking on civic tech was the creative outlet for his passion for politics and open source that he'd been looking for. He's been volunteering at the OpenAustralia Foundation ever since and is now one of the first full-time staff where he does everything from software development to decoding government jargon into plain language. He has spoken at, and helped organise, civic tech and transparency conferences around the world and is a major contributor to several international open source civic tech projects. He has recently been teaching intensive scraping workshops. In these he has helped people with almost no programming knowledge write their very own scraper in just 4 hours. When not hacking democracy he is an enthusiastic amateur cook and is considered by some to be a master barbequist.

Ask questions here: [https://app2.sli.do/event/xxxrdr7t/ask](https://app2.sli.do/event/xxxrdr7t/ask)

砍站方法，即使不會寫程式， 4 小時包你砍站下來！
[https://morph.io/](https://morph.io/)
> 好high呀!!
> [name=Yang-Hsiang C]

須使用 github 登入
2009
OpenAustralia Foundation

都更陳情網~ 輸入地址就可以讓你看到地址，看到附近的開發案申請。
Netbean  如果你要把房自拆掉這個留言，將會送給那個機關，讓他們反應以指開發案進行，我們認為大個計畫是錯，這
PlanningAlerts
我們看到有 200 million 使用個功能，來提醒哪些開發案，功能如何建起？
當地政府會發布不同計畫的資料，有些用 API 有些放網頁，如何抓取，使用爬蟲，通過下載爬蟲的方式取資料，但不好，於是我們讓很多人來參與這些資料，對這些志願者來說，我們讓這些人可以用，程式碼很麻煩

ScraperWiki
使用協作的方式來開發爬蟲，很不幸的事 wiki 才開始起步，找不到商業模式，所以很快就關門了，只好從頭開始寫，聽起來瘋狂。某個耶誕節某人沒有去度假，而將ScraperWik改寫，產生了morph.io。但人開始把爬蟲放到 wiki 上，我們想要試試看，我們可用多個語言，放到平台上執行。以上的 scraper 是連到 planAlert
我必須做很多示範，首先先登入，我已經有資料，但登入很慢，
進入後點入 New Scraper ，有時很好有時很慢
我們來決定要爬什麼東西，首先先拿 g0v 的訊息，來看看訊息網站是不是
我們建立一個爬蟲，
程式碼準備好了，首先下載網頁，然後放進資料庫內，
現在我只需要來抓就好了！

接著你可從 morph.io 看到跑的狀態，然後一些資訊，抓到的資料可以用 JSON 或是 CSV Download 下來，或是下 SQL
還是有些問題要做，比說設定參數，設定帳密

我查找 "Food"，我可以找到很多有關食物的資料
可以進行篩選的動作！

They vote out for you.
我們可以用這訊息，放到上面，就很像公民團體

下一步我們進行 platform

Merge
What 's  next to build?
How can we build it?

Thank you!

Q&A
Q1: 程式如果不想公開的話
A1: 已經是商業模式，不考慮採用，可讓其他人採用公開寫作
Docker Image 是開源的，沒什麼空間限制。大部份是說

Q2: 可以抓取限制 IP 瀏覽的網站嗎？
A2:

Q3: Open Refine 已經被當作資料庫處理，
A3: 可以來促進合作


## 開源數位平臺，跨越尼泊爾公民與地方政府間的鴻溝 / Open Source Digital Platform for Bridging the Gap between Citizens and Local Government in Nepal

提問平台 / Ask questions here: [https://app2.sli.do/event/xxxrdr7t/ask](https://app2.sli.do/event/xxxrdr7t/ask)

加德滿都有愈來愈多移民人口，推測 2011 年至少有 500 萬人口，尼泊爾沒有好的地方機構，政府結構混亂複雜，但有夠多的年輕世代和網路設施。
全國有 29.78 % 的網路人口（2011, 今年來到 50% 左右），但也有很多人不識字，無法使用手機，而大部份網路資訊是英文的。

#### GalliGalli

1.  Foucus on dialogue
2\. Work online as platform
3\. work offline also

1.  聚焦於對話
2.  建立線上平台
3.  組織志工

平台：Nalibeli.org
其實失敗很多次，也用過 wikipedia ，但不符合大家的使用習慣，2015 9月開始使用現在的平台，試著用起來更簡便。
1. 收集、包裝、發佈政府的資
2\. Crowdsourcing

why build it?
1\. 對話價值
2.參與政策決定
3\. 資訊流

人民和政府都會把資料放到這個網站，政府甚至會直接來接觸我們。

#### 上面有哪些資料？

location、timing、cost、form、process
有申請例如護照的文件、步驟，也被翻成各種語言。

重點是試圖讓資訊能被搜尋，人們也容易使用，我們也希望有互動，政府官員就會進來參與。
創建論壇，讓人們可以談論如何讓事情可以更快速的完成。

試圖找到中間點，幫助人又不在中間造成混亂 (?)


#### 碰到的問題

貢獻者少：語言問題？
如何增加瀏覽數
有影片的網站使用者體驗差
讓網站更user-friendly （要跟 Facebook 等網站競爭）

#### 做法：

整合更多社交媒體的功能
讓搜尋更方便
解決尼泊爾文難輸入的問題
接觸更多使用者

#### 我們的目標：

- 打造橋梁
- 讓更多人討論公眾事務
- ......

#### 下一步：

- 重新設計網站，提高使用者體驗
- 打造 app
- 優化美感、導覽、輸入、社交媒體整合
- 聚焦於新聞曝光

#### 兩年內願景：

- 超過十萬個活躍使用者
- 在社交媒體產生動態的對話和社群
- 提供對企業或組織的諮詢來營利

可以看到一張圖，介紹加德滿都的寺廟，透過這樣的地圖我們能到任何想去的地方。

問題：
要從何開始學起?

在尼泊爾需要服務通常是要找中間人（一些機構）他們再去政府找出服務。
opensource軟體通常是使用英語，尼泊爾常常停電，要使用online services網路也不夠好，所以會有很多需要考慮的

問：
尼泊爾有 12 種以上不同的語言，政府就有做跨語言服務嗎?

沒有足夠的語言專家
有試著找一些學生、組織，做翻譯的志工，但這工作非常龐大。

問：
政府有沒有用到這裡的資訊來改善電力、網路等設施
答：
加德滿都上個月希望我們提供志工，把資訊加到平台、教導民眾使用網路。
也有一些人想了解議題，會直接來辦公室。詢問廢棄物處理等議題，
也有軍隊、警察等等向他們諮詢

問：有跟一般的主流媒體合作嗎?
答：
我們經常在新聞上出現，即便是出現在對話中。兩個月前有個詳細的報導就是在我們平台上，因此產生很多瀏覽量。

問：政府有 open data portals嗎?
答：
政府有設這機構，但過去會覺得簡直沒有人在，民眾需要找中間人並付費，才能取得這資訊，政府其實不喜歡開放自己，會阻斷收入。

問：你們有將你們的系統應用在災害管理上嗎？例如前幾個月發生的大地震
答：
地震後我們很忙碌，把志工分成三個部份，簡督政府。
我們在做的就是促成開放資訊。



## DemTools - 公民科技如何擴大規模、永續延展？ / DemTools - Can we solve sustainable civic tech through scale?

When Free Isn't Cheap Enough.
Ask questions here: [https://app2.sli.do/event/xxxrdr7t/ask](https://app2.sli.do/event/xxxrdr7t/ask)

Chris Doten (@cdoten, cdoten@ndi.org)

Chris manages the Technology and Innovation team at NDI ([https://ndi.org](https://ndi.org)), an international development organization focused on working with civic and political groups.

Slides are available here: [http://ndite.ch/demtoolszh](http://ndite.ch/demtoolszh)


[https://dem.tools/](https://dem.tools/) by NDItech

人人相連到天邊
反覆出現的問題
小抗爭繼續
大型抗議 拆後不理
公部門想跟 卻沒錢沒力
民主體制 蝸步改革
聖戰士超會這

問題是？商用軟體又缺又貴 開發者很少為開發中國家設計 能用開源軟體的人 多數是宅宅們

未來已經到來，只是分佈不均。


並不是沒有好的科技，但分佈不均

Dem tools 裡面，有 NDI 製作的也有其他組織製作的，並被寫成各種不同語言
源始碼都在 [https://github.com/nditech](https://github.com/nditech) 歡迎使用

但還不夠好，免費的科技像免費的小狗，你需要花時間在上面，例如公民團體的領導者，他不夠宅，無法使用這些科技，沒辦法延續。曾經跟人權團體合作，後來再回去看，首頁只剩下圖片了，網頁被駭、沒人管理，發展中國家中更慘，我們持續在解決已經被解決的問題（不停重新造輪子）

很多問題規模是很大的

而現今由於雲端等技術，軟體成本很低，造 Dem tool 可以解決規模性的問題。

 各種威脅增加中 獨裁進化中
 用法令來打擊公民運動者


必需善用資源、運用槓桿，例如 CloudFlare, Amazon Web Services

[https://dem.tools](https://dem.tools)

簡單介紹平台裡的軟體：
1.  想知道哪個候選人能解決我的問題?
    issues
    在平台上向侯選人發問
2.  這個選舉有沒有問題
    [Election](https://dem.tools/elections)：與奈及利亞人共同開發的，透過 SMS 搜進資訊
3.  想了解支持者
    CiviCRM：與支持者溝通，在 Dem tool 受歡迎的
4.  附近有問題如何回報？
    1.  基礎建設有問題
    2.  貪污
5.  如何提案 ?
    Petition 是白宮建立的公投、請願平台
6.  如何分享資料
    聽過一個很棒的演講，開源不是重點，重點是去影響政策。
    Dkan（nucivic）以圖表來說明資料
DemTools 是一場實驗，在商業軟體並還沒有很好的應用，請支持我們

問：如何在地方上使用
答：












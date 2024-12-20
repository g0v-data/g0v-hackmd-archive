---
title: "判決書心證分析"
tags: Judical,Legal,hackpad
---

# 判決書心證分析

> [點此觀看原始內容](https://g0v.hackpad.tw/wE1lPGzD9s4)

## 目標

司改會在申訴不適任法官與檢察官的過程中發現，許多判決的**案情事實、背景近似**，適用的法規也雷同，**但不同的法官卻做出迥然不同的判決結果**，在**法定刑與法官自由心證**之間是否有法官恣意的問題，因此希望透過資訊工具進行分析量化。

## 相關專案or參考

[貪汙判決分析](https://g0v.hackpad.tw/--OoaenzjVDKK)
[裁判書小幫手](https://g0v.hackpad.tw/AoHSTKneEw7)
[Data-Centric Government 的二十大類資料](https://g0v.hackpad.tw/Data-Centric-Government--NoJ1mbwsqkQ)
[妨害性自主量刑分析研究小組期中報告-以刑法第221條第1項強制性交罪為例](http://www.judicial.gov.tw/revolution/%A7%AB%AE%60%A9%CA%A6%DB%A5D%B6q%A6D%A4%C0%AAR%AC%E3%A8s%A4p%B2%D5%B4%C1%A4%A4%B3%F8%A7i-%A5H%A6D%AAk%B2%C4221%B1%F8%B2%C41%B6%B5%B1j%A8%EE%A9%CA%A5%E6%B8o%AC%B0%A8%D2.doc)
[https://dsp.im/](https://dsp.im/)

## 工作內容

### 可能方法

1.  [決策樹](http://zh.wikipedia.org/wiki/%E5%86%B3%E7%AD%96%E6%A0%91)
2.  文本關連分析
3.  從實際案例回推
    1.  去掉部分資訊，ex被告

### 呈現

1.  判決產生器
2.  心理測驗

### 目標選定

1.  初步可先從一位法官單一罪名開始
2\. 妨害性自主
3\. 或者立基於[貪污判決分析](https://g0v.hackpad.tw/--OoaenzjVDKK)的結果，所做出來的database為分析
  4\. 妨害性自主案件
> 妨害性自主的類型通常是不公開案件，沒辦法作…         
> [name=Koko]

  5\. 標的案件
a. 已定讞案件
b. 三審判決確定近十年
c. 由三審判決往三→二→一審抓
> 我倒覺得應該從一審抓，因為三審判決常常寫得很簡略。二審是會針對一審的結果決定改判或維持原判，所以結論就是一審無論如何都避不掉。
> [name=Miffy C]

> 會由三審往回爬資料，是因為必須是已三審定讞的案件，所以先由三審的判決書做判決書的範圍的圈定。
> [name=Miffy C]

> 法律法源網的判決查詢，會附歷審判決，可能有幫助
> [name=張淵智]


- 暫定資料蒐集目標：台灣高等法院 刑事庭法官 曾德水 (2015/02/14)
      1.  資料庫：法源，關鍵字：曾德水
    法源網址：[http://www.lawbank.com.tw/](http://www.lawbank.com.tw/)
      2\. 時間：以2014年12月31日往前推10年
      3\. 設定查詢條件：刑事（高等法院）、承審法官：曾德水
      4\. 撈取資料下載：[http://station.ninthday.info/~jeffy/law-bank.zip](http://station.ninthday.info/~jeffy/law-bank.zip)（2015/05/18）
    說明：共抓取曾德水法官資料共 9,995 筆（86年~104年），爲了方便大家瀏覽做了一個目錄菜單方便大家選菜。檔案解壓縮後直接使用瀏覽器開啓根目錄下的 lb_index.html。左邊有一個年份列表，點選後右邊會開啓那個年份的資料列，點選想看的判決書會另外開啓新視窗。
> 曾德水法官的案件已經砍好柴了，這幾天料理一下再讓大家夾菜~
> [name=Ninthday S]

> 祝大家用餐愉快~
> [name=Ninthday S]

1.  **資料欄位**
    1.  法官姓名
    2.  罪名
    3.  ==案情事實====dropbox==
        1.  使用斷詞系統去比對案情結構的相似度→詞句組成及詞頻分析→量化
        2.  決策樹
    4.  判決結果
        1.  刑期
            1.  死刑、無期徒刑、有期徒刑
            2.  如以殺人案件為例，分成死刑、無期徒刑、10年以上有期徒刑；如果是貪污案，則可能可以分為"污多少錢判多少
    5.  ==判決理由（法官心證）==
        1.  使用斷詞系統去比對案情結構的相似度→詞句組成及詞頻分析→量化
            1.  義憤殺人
            2.  小孩殺父母
> 我本身有做語言學言辭分析的經驗，如果有需要幫忙可以找我～
> [name=淑華]

> 太感謝了！2/14的大松淑華會去嗎？想和你聊聊 :D　[我的FB](https://www.facebook.com/miffy.chen.12)
> [name=Miffy C]

> 目前不會！因為時間卡到了～但可以線上技術交流～
> [name=淑華]

> 好噢！謝謝你 :D
> [name=Miffy C]

> ＋＋
> [name=淑華]


- 判決書內容的用詞語句
「猶不知悔改」前，是指被告前科
「等語云云」前法官說的話，是法官不採的
「惟」是法官的想法
補充一下，「惟」是轉折語氣，通常是有「但是」的意思，未必完全是法官想法，但會是法官在判決時的考量。（比方說先前判決是XXXX，惟考量OOOO因素，故ZZZZ）

最末段為量刑

## 所需技術

- [x] 爬資料
> 搭啦~~~ 今天帶了增援兵力來, 除了肚子吃很撐以外果然也有成果啦!!! 哈哈哈~~~ 這位也是我們同系的學弟, 技術部分也很強~ 今天抓資料的成果就再請他上來簡略描述一下囉 :DDD
> [name=Keith N]

> 嗨，大家好，我是吃飽飽不小心掉坑的蜜蜂，在上次的大松和大家有一面之緣。目前以抓曾德水的資料做測試，分批慢慢的抓回來先放在資料庫裡存放。
> [name=Ninthday S]

> 阿嘍哈~~更新一下爬資料進度，曾德水法官的案件列表已經抓完，正在一篇篇的抓判決的內容，有9,968篇。溫柔的抓取，沒有使用暴力，所以拉長抓資料的間隔~！請稍待片刻唷~
> [name=Ninthday S]

> 各位大家好，已經上菜嘍~祝大家用餐愉快 ;)
> [name=Ninthday S]

- [ ] 斷詞
- [x] [機器學習（決策樹）](http://zh.wikipedia.org/wiki/%E5%86%B3%E7%AD%96%E6%A0%91)：格致
> 先來認領一下... 大家好我是格致, 語言基礎的機器分類及學習方法這邊我或許可以幫得上忙 :D
> [name=Keith N]

- [ ] 社群網絡分析
- [ ] 語言學言辭分析


> 建議：以下都是考量重點，但一開始可以先盡量簡化，再陸續加上viarables (變數)，分階段進行。例如，全部的判決，可以只先看法官是誰、"判決結果"亦即主文的罪名和刑度即可，刑度的部分，可以僅看死刑、徒刑和罰金(併科罰金)，而先忽略褫奪公權部分，判決的事實和法官心證形成的理由，也可以在第一階段蒐集資料時先忽略。也就是說，抓data 的範圍應由寬到窄採"十分逼近法"，我們只要關心"關聯性"即可，先不用思考太精細的部分。
> [name=Keith N]

> 根據KOKO上方提到的相同概念, 在資訊科學領域的應用方法就是決策樹, 我這邊附上上次國發會一個類似案例的投影片供大家參考  : [1999 投訴案件最後指派給環保局處理的決策過程](https://www.dropbox.com/s/905dvw11t5hnd6o/20150123%E5%B7%A8%E9%87%8F%E8%B3%87%E6%96%99%E5%BA%A7%E8%AB%87%E6%9C%83_p35.png?dl=0) ;
> [name=Keith N]

> 另一個是Wiki : [Dicision Tree](http://en.wikipedia.org/wiki/Decision_tree_learning) 上的圖例, 是根據已沉沒的鐵達尼號乘客的資料以及罹難與否, 反過來看罹難與乘客資訊的關係 : [Survival of passengers on the Titanic](http://en.wikipedia.org/wiki/Decision_tree_learning#mediaviewer/File:CART_tree_titanic_survivors.png) (當然這例子是有點古怪);
> [name=Keith N]

> 因此應用在判決書的心證分析上, 我們就需要先針對單一法官的判決書內容進行關鍵因素分析及提取(專家人工), 然後建立出類似像 1999 或是鐵達尼號乘客資訊那樣子能將重點資訊羅列的資料表, 資料量夠的話就可以熵基礎的資訊理論(Entropy-based [Information Theory)](http://en.wikipedia.org/wiki/Information_theory), 用現成的決策樹工具(CART, C4.5, ID3..etc)為基礎建立出上面例子所顯示的決策樹, 也就等於是萃取出了該法官的"心證地圖". 然後接著才能夠進行單一法官或是多個法官的心證分析或預測. 
> [name=Keith N]

> 我們去訪談一位法官吧XD，在法官的訓練過程中應該是有這方面的訓練，也許可依此建立判決的標準決策樹，然後再試著丟案件進去，看看這個決策樹的判決結果。
> [name=Miffy C]

> Oh yeah~ 吃吃喝喝! (誤)
> [name=Keith N]

> 感謝Keith 的加入~  資訊人和法律人需要進一步溝通，才會知道我們要如何來解析"法官心證<-->判決"這個玩意兒。因此有拜訪法官的想法。
> [name=Koko]



### 普遍性的抓取項目

1.  法院別：例台北地院、高雄地院。可看城鄉、地域差距。
2.  案號：例102年度訴字第254號。基本的判決要素，方便回查。
3.  被告：不同被告會有不同的事實、罪名、刑度，也才能回查。
4.  判決日期：隨著時間的變遷，法院整體、個別法官可能都會有變化。
5.  法官
6.  辯護人：有無辯護人，或誰辯護會對案件結果有影響。
7.  罪名：例殺人罪。
8.  有罪否：可能會出現有罪、無罪、其他(例：免訴)
9.  刑度：要注意有所謂的「宣告刑」和「執行刑」的差別。比較有實質意義的是「執行刑」。**另外，考量到定執行刑是數罪併罰的結果，在分析刑度上其實還要納入罪數的考量。**
10.  案由：例詐欺。因為在抓取上非常容易，沒什麼理由不抓。好處是可以將不同案件很大略地分類，缺點是並不精確。
以上為各類案件皆重要且容易抓的項目。


### 各罪論的差異

犯罪事實、證據取捨、量刑因素隨著不同的案件類型，會有不同的常見模式或是問題。但是這麼內容分析的東西，我實在不知道怎麼用程式來作分析，有點難以想像。
以收受賄賂類的案件為例，我們在看案件時會重視的證據有：金流證明(提存款記錄、帳冊)、違背或不違背職務的行為、送錢者的證詞、共犯證詞。此類案件送錢者、共犯的證詞常常是定罪的關鍵，而最容易出問題的狀況就是直接證據只有送錢者(即白手套)的證詞，另外就是檢調為了取供而讓涉案者轉汙點證人，調查局的不正訊問(之後會出現翻供的問題)。
以販毒案為例，我們在看案件時會重視的證據有：毒品類型(一級、二級)、重量、有無通聯、有無監聽譯文、監聽譯文有無暗語、證人證詞、是否有販毒相關工具(分裝袋、磅秤、帳冊)、是否釣魚辦案。其中證人證詞最常出現問題，因為證人供出毒品來源可減刑，然後吸毒者供詞也經常反覆。然後販毒案非常常見的抗辯是合購、代買，行為類型很像，但是因為涉及販賣、轉讓、幫助吸食的差異，所以在判斷上又很難分。所以販毒案比較容易出現坐雲霄飛車的情形，一審判無期，二審判一年，或是剛好倒過來。
以幫助詐欺案件(但宣稱帳戶被盜用)為例，我們在看案件時會重視的證據有：帳戶被盜者被騙經過的證據(求職剪報、通聯、即時通、e-mail、line…)、掛失止付的記錄、報警記錄、窘迫處境的證據、帳戶狀況(是否常用、裡面是否有錢)。不過更為嚴重的與其說是證據取捨，而是例稿判決的問題。也就是不怎麼查，就直接判有罪的問題。
也就是說，不同的案件類型，真的值得分析的東西其實很不一樣(性侵類就先不說了，反正絕大多數是不公開判決)，要怎麼用程式來抓這些分析要素，我真的不太懂…。
> 請問例稿判決的話是不是在判決書上就會出現制式文句?如果是的話可以用文句比對之類的方法來判斷嗎?
> [name=jennyjmgbwcy@gmail.com]

另外，如果要監督法官的不當判決，還有另一種方式，就是看例稿駁回數。
之前我有做過刑訴361條，上訴二審未附具體理由。原本的立法意旨是避免空白上訴，結果有部分的二審法官濫用，只要他覺得上訴理由看起來沒什麼道理就直接駁掉，根本不開庭。把哪些法官最常用361駁回上訴，其中有多少件是幾乎相同的例稿，可以用來了解法官的認真度。
也就是說，可以詢問律師，知不知道實務上有哪些打混摸魚的判決方式，掌握這種模式，透過程式來抓出哪些法官喜歡用這種模式來判案，就可以了解這個法官的認真度。

## 參考文獻

"Competing Approaches to Predicting Supreme Court Decision Making" (2004) ([http://www.wusct.wustl.edu/media/man1.pdf](http://www.wusct.wustl.edu/media/man1.pdf))
> 這篇文章其實是這個model 的簡明版介紹，裡面有提到他們是如何建立這個model，和對照組就是以"法律人"的組成來判斷聯邦最高法院的判決。方式值得參考。
> [name=Miffy C]



> 本文就是在玩一種猜猜看的遊戲。比較專家和統計誰比較會預測最高法院(或某個法官)的決定。專家就是考量各種因素作出預測，而統計就是依據過去的案例來作預測。
> [name=Miffy C]

> 統計作預測的方式是：抓取案件中的某些特徵，從過去擁有某些特徵會傾向得出某些結果，來預測在將來出現有類似特徵的案件，最高法院就會作出類似決定。
> [name=Miffy C]

> 舉例：預測O’Connor法官(保守派)的決定
> [name=Miffy C]

> 1.下級法院的決定是自由派的？是，則撤銷改判
> [name=Miffy C]

> 不是的話，則往下走。
> [name=Miffy C]

> 2.案件是來自於第二、三、特區、聯邦巡迴上訴法院？是，則維持。不是的話，則往下走…(請自行參figure 1)
> [name=Miffy C]

> *這邊我不是很懂，案件來自哪個法院，為何與O’Connor法官的決定有關？可能是因為我不了解美國法院的生態就是了。
> [name=Miffy C]

> 也就是說，統計作預測的方式，是以在言詞辯論前即已存在的某些特徵，來預測言詞辯論後的結果。但是本文也強調，此處抓取的特徵與決定的結果，在解釋上並沒有因果關係，比較像是相關而已。
> [name=Miffy C]

> 而本文的結論是：統計作的預測比專家作的預測來得準。
> [name=jennyjmgbwcy@gmail.com]


> 我目前看不出來本文是用程式去抓取相關特徵而得出。甚至我覺得資料庫比較像靠手工完成的(或至少有部分必須靠手工)。理由就是：一個決定到底屬於自由派或保守派，其實難以單靠電腦程式來判斷，或者至少是，如果是用電腦程式來判斷，我看不出本文是如何設計這個程式。
> [name=jennyjmgbwcy@gmail.com]


> 本文對我的啟示是：其實不一定要抓取很多判決的細節，有些看似很容易抓取的特徵，對結果來說，就有一定程度的預測性。
> [name=Miffy C]


> 不過如果從監督法官判決的角度來看，我覺得本文的啟示性有限。
> [name=undefined]

> 關於二呆林所說「一個決定到底屬於自由派或保守派」，我覺得可能是先判斷做出決定的法官屬於保守派或自由派(藉由法官判決以外的言論表態甚至是其選民性質，事先預設法官屬性)，再依照法官判斷該決定屬於保守或自由派。
> [name=jennyjmgbwcy@gmail.com]





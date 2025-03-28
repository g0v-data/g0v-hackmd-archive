---
title: "[R2] 鷹架 / Scaffold @g0v Summit 2016"
tags: hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/RW9M2GMq3Rp)

剖析災變，以數據力支援的智慧應變方案 / Analyzing disasters: Data-based contingency planning
主持人: 衷嵐焜

各位朋友午安，我是這場主持人衷嵐焜，本身在逢甲大學地理服務系統服務，我們在做什麼？我們在做一個app，拿開放資料來做迪士尼排隊預測資料，以後會告訴你最佳的排隊流程。今天我們的場次跟災害有關。這五位講者在公部門跟私部門都非常重要。第一位我們請到KNY，他說他是彰化的金城武，要帶給我們強震及時警報，我們請到app作者帶來精彩分享。

more info: [g0v Summit 2016 hackfoldr](http://beta.hackfoldr.org/g0v-summit-2016/)
現場直播網址 (live url) [http://summit.g0v.tw/2016/live](http://summit.g0v.tw/2016/live)

==↓文字轉播、線上討論↓==

## 強震即時警報 EEW / EEW: Early Earthquake Warnings



大家好，我是KNY，今天要講強震即時警報。這是我的個人簡介，有一些關鍵字，app、忙救災、地震，我的身份在網路上就查KNY就可以查到所有料，我的身份在網路上是透明的。我是地震災害防治的主任委員，最近都做跟地震有關的關係。這是一個app，之前是拿政府資料作的app，政府還沒開放資料我就已經拿來用了。這幾年一直在倡議開放資料。以前還沒開放資料前就已經去抓。如果你是android去查KNY就可以抓得到這個app了。我們來做一下地震模擬，地震發生的時候要：趴下、掩護、穩住。有沒有聽過黃金三角？沒有這麼一回事喔。如果現在發生地震，現在發生地震喔。你應該先趴下，找到一個安全的地方掩護自己。如果現在發生地震你會做什麼事情？聽到這聲音要怎麼辦？我剛剛講啦，地震當下應該躲到桌子底下，或是馬上離開建築物。有人知道從這邊到離開建築物要幾秒嗎？你看一下你頭上有多重的東西？我要講一個故事，十七年前， 如果你20歲，十七年前應該是三歲，那個晚上的秋天很悶熱，還是數據機上網的時代，上網愈久就愈貴，一點多的時候覺得該睡了因為明天還要上課。正要把電腦關掉時發現外面好像停電了，然後就開始搖了。1999年的時候，將近二十年前，你一輩子至少會遇到一個很大的地震。地震發生的時候要趴下、掩護、穩住。那時候我在這個地方，我在震央旁邊。沒有任何機會讓你做剛剛這三個動作，當時就是被上下甩左右丟，我在台中太平這邊震度是七級，沒辦法作任何應變反應只能尖叫。我們出來之後，幸好住的房子沒有倒掉，沒有人敢在進去建築物。跑出來之後，完了，我車鑰匙沒拿，手機沒帶。我不知道我家人怎麼了，後來兩點多開始變冷了，鼓起勇氣進去拿手機把鑰匙拿出來，進去學校找人。我騎了很久因為很多建築物都倒了。921這次給了台灣非常大的提醒，在二十年前，我先放一些照片讓大家勾起回憶。這是台中、石岡水壩、整個水壩是潰提的。地震後一週我就到體育場去當志工，幫忙扛水。有些人一進去，出來之後都不敢講話。你看一下這情況是什麼情況。一樓是不見的。一樓是孝親房，爸爸媽媽都住在那邊。台北得部分，離震央這麼遠，還是倒了。新北、最下面新聞的字卡：奸商過了追溯其免訴。豐原的光復國中，現在已經變成博物館。斷層直接經過那邊。有沒有勾起你們的回憶？如果現在發生這樣的地震，你確定你能活下來嗎？覺得明天會先到還是災難會先到？問一下自己，明天哪一個會先到？佛家講這個是無常。明天假設會先到，你可以做風險評估、保險。災害先到要做什麼事情？假設像921，你要先讓自己復原、重生。這兩天不是在考試嗎？有人在說是要坐在位置不能動，你要記得，命是你自己的。只有命留下來才有可能家族留下去。

地震的小知識，地震發生時有幾種波，P波比較快，每小時兩萬八千多公里。現在人造物還沒辦法飛到這速度。S波是每秒四公里。現在最快的太空梭是每小時兩萬八千公里。如果可以提早知道地震的話是利用一些地震的基本物理現象，再利用科學去告知。P波是壓縮的，S波是上下震動的。前幾天在宜蘭發生地震時，新聞也有講，會先上下震動，再左右甩。P波的速度比較快，科學儀器偵測到之後，S波接著P波震動而來，最後是最可怕的表面波。當地震發生時，P波比較快，接下來是S波。P波經過測站被偵測到後，在經由ACDR技術傳出來給大家，電信商再送給各個手機。你可以看到藍色這圈是P波的位置。

剛剛你有看到台北大概預計是一級兩級，不要輕忽，還是要做應變反應。五秒內立刻躲到桌下。每個時間點的應變反應都不一樣。假設我們收到這樣的簡訊，該做怎樣的反應？家庭的應變反應是什麼？需要先做過一遍從你家到樓下需要多少時間，如果30秒來不及需要知道你家最安全的房間在哪裡。不要打卡，可能30秒之後你就消失在這個世界上了。

剛剛S波速度是每秒四公里。五十公里左右半徑可能已經搖過了才收到訊號，這一群稱之為盲區。這邊是來不及的。盲區的話還有救嗎？我來講一下之前一個故事，1995年日本阪神大地震統計，如果你是受災被救出來的人，有七成是自己把自己救出來的，兩成是朋友救出來的，一成是官方救的。這含意是，日本每個人救災都非常放在心裡面。假如發生最嚴重的地震的時候，會有什麼情況？日本政府認為若發生南海大地震的話直接死亡人數是三十二萬人，你想下一下三十二萬人次是多少人？三重是三十八萬人，新店是三十萬人，花蓮可能整個都不見了。他們認為未來三十萬年內發生的機率是70%。所以這些區域的地方政府一直在做救災防制的演練。這一區可能會有複合性的災難，像是之前三一一海嘯捲走。想像一下在大台北區域發生很重大的地震，類比成剛剛日本的數據，你覺得死亡人數是多少？官方有提過，但我們的因應措施是什麼？你只要查國震中心、地震等關鍵字就查得到。假設向那樣的餘震發生在台北，你認為我們的國家體系有辦法面臨這樣的災變嗎？如果倒了四千棟，誰要去救你？

我們還活著，我們還有明天，我們的反應是什麼？我覺得基金會是可能的解法。

問：網路上資料說是天氣的APP沒有地震功能，怎樣開啟跟氣象局的合作的？
答：因緣際會參加一些組織後認識氣象局的人，氣象局應該是技術單位，我是APP跨界小組協會理事長，99%的APP不應該由官方來做，很多公共服務應該可以讓民間來做。若官方做一個APP下載數不高，他們會怎樣？應該就是編列預算去行銷什麼的。我之前的APP下載就已經超過一百萬，所以我就去跟他門講過這樣的公私合作，提供資料，推給民眾。傳統公共服務是公部門提供標案，但未來應有愈來愈多服務是民間幫忙去做的。氣象局態度蠻開放友善的。


## 傳染病開放資料過去、現在、未來-以登革熱為例 / The Past, Present and Future of Open Communicable Disease Data - Using Dengue Fever As An Example


我們最早時候在2014年高雄登革熱疫情，那是因為七月底八月初高雄氣爆。當時大家關心那些管線怎麼走？但後來發現高雄登革熱疫情變很大整個燒起來，後來有一些醫師在想這疫情是不是跟氣爆有關？因為後來下來一場大雨。後來在想是不是有怎樣的資料或方式讓民眾知道現在的疫情變怎樣。後來去找現在有些資料是否足夠，但後來有點失望，因為沒有細部的資料。於是後來想盡辦法去爬高雄市政府網路資料，那是PDF檔，後來就做成流行病曲線跟地圖。當時我跟G0V沒有這麼熟，因為當時口號是拆政府，我在想是不是一個匪類的團體。後來大概在十一十二月左右，有個g0v的演講，有興趣一起來研究登革熱的事情，我們請高處長跟醫師來演講，不是摸頭啦，是從他們的角度來看要給民眾什麼？我們要提供什麼。這時候就開始在想可以做一些什麼。2015年之後，整個登革熱疫情燒起來，並超出我們的想像之外，我們開始想有沒有可能做一些事情，八月底的時候我們在OPEN DATA的社群，去提出request說，因為疫情的關係所以希望提供更多資料。很感謝PEGGY與我們積極的幫忙，來跟g0v積極的互動，來把一些東西放上g0v。後來社群很熱烈反映有很多意見，我們就在八月底釋出登革熱病歷的資料，台南市政府很勇敢的率先釋出每日登革熱資料，他們用人工處理我們用機器處理。

有拿來做一個全世界埃及斑蚊分布區域，貢獻最多是巴西，再來是台灣
下一步 CBS的方式 居住附近或前往地方有疫情也會有CBS發布訊息

也跟商業公司合作HTC萌寶日記App 小朋友出生要打疫苗
未來走向一個open data的平台計畫 希望做一點點應用 做幾個示範
未來做幾件事情 規劃地圖網站 open data 也會open source放在github上美國也試著去做一些事情 還有在做傳染病從日治時代就有相關統計資料 第二次世界大戰斷掉
傳染病open data的考量 太快 資料出去是否造成房價下跌 但是經過這次觀察一年到半年並沒有發生但其他疾病就會非常顧慮還是會case by case去考慮 資料越透明越公開越好還是會污名化
Feed back
人力是滿大的問題 台北市小彭也在板上貼一個問題究竟這樣人才在哪邊 火力靠研發替代役 107年後是不是還有新鮮的肝
未來其他資料越來越多會提供英文版 也許open data和其他國家交流增進關係

References
\* 登革熱防治網 \- [http://dengue.gov.tw/#/](http://dengue.gov.tw/#/)
\* 歡迎 \- 臺南市政府資料開放平台 \- [http://data.tainan.gov.tw/](http://data.tainan.gov.tw/)
f

## ==ICT 與群眾外包的災難適應力，亞洲開發銀行的案例研究 / Disaster Resilience with ICT and Crowdsourcing, a case study from Asian Development Bank project==

災害發生大家可能會亂成一團 國際上台灣也是是在災害發生時許多人想要幫助 資訊 物資在網路上PTT發酵翻滾著 整合協調把政府救災民眾想看的資訊送到他手上 這是我們想做的 我自己在跑國際 我也參加在電信標準 從2011.做群眾資訊的搜集 其實台灣的ICT能力不錯 不過今天是講跟亞洲開發銀行的案例

這些銀行過去幫開發中國家需要一些金錢援助的區域去借款 會看到很多硬體工程師是亞洲開發銀行發包過去
人手一支智慧型手機 我們選了幾個國家 我旅行非常累 阿美尼亞 孟加拉 北極
整個計畫來講是這樣子 用一個簡單方式來講 這些災害有很多事件發生 應該要把他派給正確的人去解決 進度如何 解完沒 一件一件去搞定
日本有很多演練跟說明 發生很多緊急災害該怎麼做 阿宅可不可以做的系統化一點 要不要回報給權責單位 尤其台灣很多事情是垂直負責 最近很多是1999 假設1999都佔線如何回報

你要去顯示這些問題在哪些地方大家都有智慧型手機用數位化顯示是很正常的方式
孟加拉首都達卡分南北兩區兩千萬人左右人真的多到無法想像交通也是很厲害看到google map很OK 從google earth衛星圖去看 完全不會有商業價值 這個地方不會有商業行為 要去做災害防救或人道行救活動 需要open street map 帶出不同的一點像wiki一點是
倒不如有沒有工具讓志工協助建立起來 用這些資訊做人道救援活動 有聽過就繼續貢獻 每個人都可以像wiki一樣貢獻建立起來
[http://www.missingmaps.org/](http://www.missingmaps.org/)

打開地圖看滿完整 像西非發生伊波拉事件
讓當地社群有防災意識 舉一個孟加拉例子 那邊有地震那邊有火災那邊會淹水 那邊有一個防災中心 一樓只有柱子 二樓很有趣可以放牲口牲畜 以農業為主 所以在設計牲口可以牽到二樓 三樓才是住人 平時有些這種應變中心 可以作市集開啟交易 從衛星圖看起來只是建築物就這樣 所以為何要跟當地合作把能量突顯出來
海燕颱風菲律賓 所謂災損評估 點點是房子 教堂在哪個地方 有什麼方式 這樣子的地圖未來也有可能繼續畫出來 怎樣數位化大家可以使用 再來跟我們有關係 KNY提到避難出口往哪邊逃 但是有其他不同緊急事件 可能對外通訊都斷掉 我就要想背著包包要撤到哪裡去 避災地圖應該會有地震風災要往哪裡走 其實手機一查 就知道要往哪裡去 這些東西平日建立好 會變防災能量 這些資訊應該是要有的

很多資訊地圖數位化 把大家常用的ideditor變成手機化 地圖松 防災松 建立相關資訊 拿著這樣工具去修改資訊

不管是地圖志工或政府派出去職員人員應該都要搜集建築物資訊 可能建築物資訊 經過跟亞洲不同專業團隊(如 日本ATRC)

整個來說尼泊爾加德滿都地震後 有很多資訊可讓人道救援團隊使用 能把防災資訊建立起來

### 三個ISSUE

- 第一，**問題在什麼地方**
- 第二，**怎樣回報**
    - 究平安
        - Android 版本  [https://play.google.com/store/apps/details?id=com.geothings.geobingan&hl=zh_TW](https://play.google.com/store/apps/details?id=com.geothings.geobingan&hl=zh_TW)
        - iOS 版本  [https://itunes.apple.com/us/app/geobingan/id719858654?mt=8](https://itunes.apple.com/us/app/geobingan/id719858654?mt=8)
        - 究平安: [http://geobingan.geothings.tw](http://geobingan.geothings.tw)
        - Facebook: [https://www.facebook.com/geoBingAn?fref=ts](https://www.facebook.com/geoBingAn?fref=ts)
    - 斐濟案例
        - 版本變得更直覺(我要回報，再選個類別，傳送出去) 希望變得像instgram 會知道淹水在哪個地方 有web可以看
        - 之前遇過問題網路都斷線怎麼辦 平常出去搜集救災資訊和勘災時 可以上傳到Amazon或者MS Azure
        - 斷線若還有手機訊號可以用簡訊傳輸位置和狀況
        - 完全斷線用離線方式紀錄做災害統計回報(假設沒衛星設備的時候，把大家蒐集到的資訊同步到手機，帶著手機開著車、騎著馬，把資訊帶去中央政府、帶出去)
- 第三，**誰來處理這些資訊？**
    - 目前有合作的國家/政府單位
        - 斐濟 \- 國家災防中心
        - 菲律賓 \- 衛福部
        - 台灣 \- 宜蘭市政府、賑災基金會
            - 有地點有照片有時間就可以做後續處理
            - 資訊應該被串接起來，組織對組織
            - 台灣每一個直線的災害回應單位都有自己的累積，還沒有橫向串起來
            - 希望後續能在導入回台灣，與政府, NGO...等組織合作將整個流程串起來

台南高雄0206地震學校受到損害
在後續重建如何用ICT工具來解決(有系統的整理資訊)
ICT怎麼做災損統計？（傳統請在地單位回報運用excel列表，但用geoBingAn拍照標示或許更直覺，可以統整大範圍的狀況）
透過衛星圖做到災損評估，整合到整個系統

在台灣目前都
## 開放街圖在外交援助計畫上的應用 / Using OpenStreetMap to help other countries and improve foreign relations


講者：詹為翔 WSJhan
派駐：聖多美與普林西比
    中非兩小島組成的一個國家
    熱帶雨林氣候
    前葡萄牙殖民地
    我國友邦

OpenStreetMap: 仿照維基百科，開放編輯地圖
任何時間可以編輯
因為當地圖資相當缺乏
- 聖多美國家介紹
- 瘧疾防治顧問團工作
當地有很高的瘧疾盛行率，講者至當地進行公共衛生的資料建立，
但數位圖資缺乏，沒有路名，沒有地址沒有道路，一般民眾也沒有電腦

Google Map 對於泥路內的村莊以往不會標記出來
瘧疾病人也因此找不到

OSM
[http://www.openstreetmap.org/](http://www.openstreetmap.org/#map=17/1.64008/7.42101&layers=N)[#map](https://g0v.hackpad.tw/ep/search/?q=%23map&via=RW9M2GMq3Rp)[=17/1.64008/7.42101&layers=N](http://www.openstreetmap.org/#map=17/1.64008/7.42101&layers=N)
Google Map
[https://goo.gl/maps/fKpUYJ6GWo62](https://goo.gl/maps/fKpUYJ6GWo62)
實地探查實地畫出道路與村莊，泥路區連當地人都不知道在哪裡
使用拍照全景方式來建立街景，從空白建立出來，一個個慢慢標出來
全景圖涵蓋的資訊很多：
    水源地
    房子高度
    當地圖 3D 顯示

當地銀行因為沒有法規，因此當地收入中低，一堆銀行來洗錢！

標記出村莊，將病人一一量化
以往都用相對位置（地址：某某村正中間廣場樹下人所指示之處）

使用 Garmin 來標記GPS，可以直接讀取OSM資料
Mapsme App 有顯示較多聖多美地圖詳細位置

對瘧疾發生的永久與暫時孳生源記錄位置，詳細紀錄後分析。
蚊子分成1~4期階段，家蚊雖不帶有瘧疾，但會一併紀錄與清除

我國瘧疾防治屬於世界數一數二，因為徹底根除瘧疾，因此曾被拍成紀錄片（英國 History，Mission Malariaf）

講者離開後，2012 年開始有更多資料

Conclusion:
    Set up STP Map 聖多美及普林西比基本圖資
    Local trainng 當地員工教育訓練
    Analytics 孳生源、病例空間分析
    Application 其他地理圖資應用

台灣小巷道繼續標示出小道路

## OpenStreetMap 與 LocalWiki 的整合：支援社區層級災害系統管理 / Integration of OpenStreetMap and LocalWiki for supporting community-level disaster information management


鄧東坡
將兩個獨立社團整合的故事

LocalWiki [https://localwiki.org/](https://localwiki.org/)

下午是一連串OSM的進擊。我們不約而同拿OSM做運用。這個案例比較特別是今年二月才開始，實作的部分也是現在才開始。所以今天的演講我比較心虛因為沒有太多實作可以講。但這件事情會有什麼效應今天會跟大家報告清楚。

如同題目所說，一個是管理地理資訊，一個是共同編輯地方資訊，這兩個結合在一起要如何來做防災社區管理？我們從一張圖開始說起，剛剛的報告裡面有提到，所謂的[內政部消防署疏散避難圖](http://www.nfa.gov.tw/main/ftplist.aspx)在全台灣每個村里都有，只要到消防署網站就可以看到，目的是提醒大家，在自己的環境裡面當災難發生的時候要怎麼避難。我想問各位，有多少人去下載來看過？或是大家根本不知道有這張圖在網路上看得到？
> 厲害之處在於提供的圖竟然是jpg!!!!
> [name=YenWei Z]

> 要讓政府用 OSM 嗎？
> [name=Tsai M]

> WoW jpg
> [name=Mario C]


再者我們來看這張圖的有趣之處，圈起來的部分是防災位置，這是我住的地方新北市一心里，這是台北市的邊緣，只有一個水溝之隔。這個水溝之隔造成這張圖的規劃有很大不一樣。紅圈圈的地方是宜興里的位置，建議災害發生時去白雲國小，大概要走十五到二十分鐘，依腳程不一樣。這張圖告訴你避難場所在哪裡，還有主管機關在哪裡。這白雲國小跟東方科學園區。這樣的規劃是否合理？如果我是當地居民，我不會選擇這樣避難。因為我旁邊就是中研院，我會選擇去中研院避難。因為中研院也有很大的綠地。所以我心中很大的疑問是，為什麼避難要捨近求遠？那這邊紅色的部分就是剛剛講的宜興里的位置，這些舊庄國小等都是離我最近的，我不會選擇到白雲國小或東方科學園區。為什麼會這樣規劃是因為行政區不一樣。因為宜興里屬於汐止區，但中研院屬於台北市，所以行政層級不一樣規劃就不一樣，跟我們生活場域是不一樣。在我們日常生活要逃難是絕對不會像他一樣的規劃的。這樣由上而下的規劃沒有符合我們生活場域，這樣這張圖要幹埋麻？就有點像蚊子館一樣，這張圖就放在那裡沒人管。當災害發生的時候，沒有家可以回的時候，應該要知道哪裡可以拿到飲用水跟維生資源，在OSM裡面我們習慣把藥局等等資訊標在上面，這樣才能提供足夠地理資訊讓防災使用。

所以呢，我們就在想說如果我們可以進一步使用OSM取代防災地圖，是不是能夠把這件事情做的更完善讓更多人參與?但台灣面臨的災害不只一種，可能有水災、或是天然災害、人為災害像毒氣等等，我們的避難方式就會不同？政府端也有想到這問題。我們看到嘉義縣朴子市去針對淹水、地震、毒化事件等等做防災地圖，但請各位看一下，看到這圖的時候有沒有想說自己在哪裡，因為最精華的那一塊全部標記都擠在一起。這張圖能夠充分告訴你避難的資訊嗎？這也不符合我們現在多數人使用手機來看地圖的需求。這樣的紙面來做地圖，雖然是網路下載下來，但不代表這是網路地圖。

### 避難地圖缺少什麼


接下來的避難地圖缺少什麼？有四個因素。一是參與，在地民眾沒有參與地圖的製作過程，缺少合作的概念，沒有居民提供的資訊，就沒有在地的知識在裡面，這些只有在地民眾生活在這裡才會知道的。就像剛剛簡報分享說第一層可能不住人，或是幾年前曾經淹過水，這些在地知識若從政府由上到下，沒辦法充分累積民眾的在地知識，在防災層級來說對於社區就沒有凝聚的效果。這是我對於防災地圖缺乏要素的看法。因此避難疏散地圖應該要進入2.0，這概念有兩大項目。2.0應該要容易去作整合，這些資料必須結構化，資料結構化之後才能夠重複被使用，跨系統平台被使用。資料跟格式需要被開放，最好是使用開放源碼，另外要邁入行動裝置，若行動裝置無法相容，就無法符合當代人使用資訊的需求。另外需要跟當地居民協調合作，逃難跟生活場域是有關的，在地知識需要跟防災做結合。這平台需要提供防災知識的累積跟交流，也要培養防災的意識。這是我對於避難疏散的地圖跟想法。基於這樣理由就不會用過去的紙面的地圖。

NCDR 防災社區網站：[http://community.ncdr.nat.gov.tw/](http://community.ncdr.nat.gov.tw/)
台灣的政府並不是沒有作為，剛剛提到的災害過程中，中央層級的國家防救災研究中心，很大的項目在做防災社區，有專家有學者幫助當地社區做防災工作，協助社區避難。但這樣仍是由上而下的防災社區建構，政府已經跟專家者訂製了架構，才去找當地的團隊跟意見領袖，這樣菁英式的管理方式，會使得參加的人不會這麼全面。所以呼應g0v的主題，我們呼籲資訊志工的加入。從地圖、災情的資蒐集，來建構平台提供給居民使用，不應該單單的由上而下，而是要注入由下而上的力量。所以我們在想說開放街圖是由下而上的地圖，這樣可能會幫助防災地圖更有幫助。
> NCDR 社區參與的災害地圖，個案社區: 嘉蘭社區 [工作坊影片](https://www.youtube.com/watch?v=Uwro-5Y2-JU)
> [name=che l]

> GeoThings 究平安 [https://geobingan.geothings.tw/](https://geobingan.geothings.tw/)
> [name=Yiling C]

> 在社區內推動環境地圖、災害地圖，我自己覺得 Google Earth 似乎比較常使用，實際上有些特性例如山區地形，整合各種既有資料格式等等。但因為是單機版，不曉得有沒有線上協作版？我以豐南地區的一個社區截圖為例：
> [name=che l]

> ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_23a9ab797e89ab3eadf1a50d3f4a91c6)
    
> [name=che l]


開放街圖是開放自由的地圖，使用開放格式與源碼，用開放授權的開放出來的地理計畫，全球民眾透過這平台都可以使用。他是wiki化的地圖，也是合作協同的製圖方式。在OSM剛開始的時候，第一張地圖的繪製就是英國倫敦的繪製，拿GPS多走幾次，合成出來的樣子，但這圖沒辦法使用，需要再向量化，才可以重複使用。這張圖的重點是群眾共同創建而來，共同生產地圖，國際上也有很多人共同參與地圖，讓很多人共同繪製，也可以獲得免費地圖。OSM是全球草根性的繪製地圖。現在有很多高解析度的衛星影像，有些人再家就把這些給繪製出來。繪製出來之後再給他適當的屬性資料，例如畫好的四邊形是房子，這些就會變成地理資料存在OSM的資料庫裡面。每個國家現在也愈來愈多開放資料，最多的是美國。你會發現地圖不是一個人畫的，也不是國家畫的。而是每個人都可以提供與修改繪製。大家把地圖彙整在一起之後，就可以玩地圖，所以在同一個區域，可以有九種以上不同的顯示。這九張地圖都來自同一份資料。

OSM Overpass API
那我放進去的地理資料要怎麼拿出來？OSM overpass API有個好玩的地方是可以指定某幾個類別要的資料，就可以直接抽出來。這個案例就是直接抽取台北市有傻瓜電擊器（AED）的資料。所以他就會把所有資料顯示出來。這個地圖不是只有一張地圖，事實上他還有很多資料，是因為你已經撈出來。你可以再把部份資訊疊上去，我們可以再自己設計一些icon把資料疊上去，讓地圖顯示的更完整。從這個道理來看OSM變成很大的地圖資料庫再使用。所以如果政府的防災資訊可以一一的建置進OSM地圖，很多人就可以直接進去OSM看更完整的地圖資料。

這些資料都可以先丟進去OSM裡面，若有人要開發防災疏散的地圖就可以進去使用。救災物資在哪裡、水在哪裡等等資訊都能夠整合。如果說我們把地理資料放入OSM裡面，以社區防災角度來描述這些防災系統再輔以OSM資料，就能夠更幫助社區的民眾。那 LocalWiki 到底可不可以用？這是描述在地的地理位置跟照片等等，overpass API可以協助把OSM的東西拉入LocalWiki，可以省下描述物件的動作，這就是為什麼我們要做這件事情的原因。

### 我們的概念是OSM搭著LocalWiki的方式


所以我們的概念是OSM搭著LocalWiki的方式，來做社區的防災疏散地圖。但第一個問題就是前述要進行整合，第二就是OSM有特定的描述方式，需要大家的共識，之後做整合才有更結構性的資訊。但目前防災的專家並沒有這樣的概念，所以我們需要來說明為什麼政府資訊需要丟到OSM裡面去。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d8bcd9bd4ff91d557ff5e2d0495f09ae)

這個概念圖很複雜，但是我前面都講過了。要進去LocalWiki的時候，要先查一下有沒有這個地名的頁面，如果有就去編輯，如果沒有就新開。然後再去OSM裡面找一下是否已經有這個地方，如果有的話就直接import到 LocalWiki，如果沒有的話會發訊息給開發者請他去OSM裡面輸入資料。這樣資料就可以匯集在一起。但這還是在概念的層級，實作面我們還沒開始進行。一個防災社區的樣版大概具有社區基本資料、社區有哪些避難場所、有哪些設備、緊急聯絡網？都必須是基本資訊。年底之前我們會來做釋出。這不只在防災社區使用，這樣的方法應該可以擴充到更多議題上使用。
> 針對防災社區，基本資料我覺得也會包含「災害潛勢」，內容來源有政府或專業研究的成果，也有在地知識與實體的踏查而得到，也需要有不同災種，所以勢必會需要有圖層管理，或是用「情境、事件」來引導出部署所需資料項目
> [name=che l]


Q&A
Q1:
A1:

GSDI 台灣防災產業的活動：[http://conf.gsdi.org/index.php/conferences/gsdi15](http://conf.gsdi.org/index.php/conferences/gsdi15)


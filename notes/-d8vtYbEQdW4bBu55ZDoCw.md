---
title: "給新北市研考會為民服務組的開放 1999 提案 (2015/10/12)"
tags: 資料蒐集,hackpad
---

# 給新北市研考會為民服務組的開放 1999 提案 (2015/10/12)

> [點此觀看原始內容](https://g0v.hackpad.tw/tQoaOuOYp8U)


> 大家好，我是 Johnson（g0v irc/slack ID: MrOrz），目前在新北市當替代役。
> [name=Johnson L]


> 日前新北市替代役資訊小組開會的時候，研考會為民服務組組長跟我們說，上個月的颱風 \+ 停水導致大量陳情電話湧入，1999，湧入 20000 通電話，但人力僅能處理 8000 通左右。
> [name=Johnson L]


> 組長想要請資訊小組的役男們開發一款 app 與 1999 資料庫對接，以分流的方式減輕 1999 第一線客服的壓力。役男們與組長表示，由於會打 1999 的民眾通常都沒有能力自己上網汲取資訊，app 的受眾與電話服務的受眾交集甚小，因此專門替 1999 開發專用 app，並不會減輕客服業務量。不過在討論中，組長口頭表示 1999 的資料可以公開出來，讓我個人有些興趣，希望協助研考會將 1999 的資料以 machine readable 的方式開放出來供大眾使用。組長與兵役科的科長則希望役男可以提出一份報告讓他們參考，我認為這是**_介紹 open data 概念_**，**促使新北市開放 1999 資料集**的一個好機會。
> [name=Johnson L]


> 在下週一（10/12）我會以「新北市替代役資訊小組役男」的身份，具名將下面這份報告上呈給替代役資訊小組承辦人，預計會轉交給研考會為民服務組的組長。這份報告會向組長介紹目前國內的案例與國外的開放標準（Open311），並且標明是由社群成員的一起寫出來的。只是，我在這之前並沒有參與過任何 Open data 相關的 project，報告內容可能對個專案的含義有誤解或含混不明的地方，希望社群的大家可以不吝指教 m(_ _)m
> [name=Johnson L]


> 參考資料：[Open311Pitch](http://wiki.open311.org/Open311Pitch/)、[open311.org/learn](http://www.open311.org/learn/)
> [name=Johnson L]


### ＊此份提案報告以 CC0 釋出至公共領域＊

> PDF 輸出：[https://drive.google.com/file/d/0B1tiWyU4jeioZVhIMHE0d3VackU/view?usp=sharing](https://drive.google.com/file/d/0B1tiWyU4jeioZVhIMHE0d3VackU/view?usp=sharing)
> [name=Johnson L]


由於提案對象是新北市研考會，故行文會以新北市作為主體；非常歡迎大家自由重製、改作、以及推廣至各級政府喔！

> 以下是報告本文，歡迎直接增補與討論。
> [name=Johnson L]



## 壹、前言

> 說辭參考資料：
> [name=Johnson L]

> [https://en.wikipedia.org/wiki/3-1-1](https://en.wikipedia.org/wiki/3-1-1)
> [name=Johnson L]

> [http://wiki.open311.org/Requirements_analysis/](http://wiki.open311.org/Requirements_analysis/)
> [name=Johnson L]

> [http://www.open311.org/learn/](http://www.open311.org/learn/)
> [name=Johnson L]


1996 年，美國馬里蘭州巴爾的摩市推出「311」電話服務，在「911」緊急服務之外另闢渠道，供市民舉報陳情各項市務。北美最大規模的 311 服務在多倫多，自 2009 年成立以來持續成長，至今每週接聽超過 2 萬通電話 \[1\]，累積了大量的陳情資料。在全球各處 311 服務發展完善的城市中，311 在已經成為公眾共同舉報與追蹤非緊急市務的公民工具；多倫多、芝加哥等城市甚至更進一步地將 311 的資訊公開出來，不僅可以減少重複舉報的處理成本，透過開放透明、鼓勵大眾檢驗，每一件政府處理完成的小事，市民都看得到，能夠提升人民對政府的信任與滿意度。著名的例子有英國的 FixMyStreet 與美國的 SeeClickFix。

\[1\] 資料來源：311 Toronto [Performance Reports : 2015 Monthly metrics](http://www1.toronto.ca/wps/portal/contentonly?vgnextoid=63ceef04153ac410VgnVCM10000071d60f89RCRD)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9f344a55e949f7039231e814c5cb7eac)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_db0e0ce23e896791624936083fcccab5)
```
FixMyStreet（上）與 SeeClickFix（下）。FixMyStreet 的界面著重現在陳情案件的地點，而 SeeClickFix 則是在呈現問題、政府回應以及民眾參與（投票）。

```
將 1999 / 311 的資訊公開出來的好處並不僅止於此，看似零散的派工資料結合並且開放，第三方的公民們就能運用資料，對社區規劃進行更深化的討論：找出哪些十字路口不太安全、標示哪些地方需要一條腳踏車道，或者提議哪些空地適合建造新的公園；國內也有人用台南的 1999 開放資料，協助標記台南登革熱需要留意病媒蚊的空地空屋。

本文將舉登革熱疫情、蘇迪樂颱風災情與八仙塵爆作為國內開放資料的應用案例，隨後詳細介紹國際間使用的 Open 311 資料開放框架，最後提出新北市開放 1999 資料的架構方案。


## 貳、案例探討：國內災防資料開放


近年民間對開放資料的運用與發展有高度興趣，不僅舉辦了公民自發的大小活動與團體 \[2\]，也產出了一些成果，體現社群的高度行動力與活力。以下以時序近至遠，先介紹政府在各事件中開放了哪些資料，然後說明公民社群參與者如何運用所開放的資料。

\[2\] 如 [開放文化基金會](http://ocf.tw/)、[g0v 零時政府](https://g0v.tw)、[資料科學愛好者年會](http://datasci.tw/)、[OpenData/Taiwan 臉書群組](https://www.facebook.com/groups/odtwn/)等等。


### 一、台南待孳清空地空屋資訊

> Reference: slides [https://docs.google.com/presentation/d/1McldFdpvMFwAyO4PSYyEd7V\_5kzorG-J31CGu9Y68sM/edit#slide=id.gbd817e2b4\_0_352](https://docs.google.com/presentation/d/1McldFdpvMFwAyO4PSYyEd7V_5kzorG-J31CGu9Y68sM/edit#slide=id.gbd817e2b4_0_352)
> [name=Johnson L]


> Blog post
> [name=Johnson L]

> [http://k.olc.tw/?p=576](http://k.olc.tw/?p=576)
> [name=Johnson L]


家住台南的 kiang（本名江明宗）在經濟部舉辦的臺泰跨國黑客競賽中，修改非洲海地大地震所用的 Usashidi 系統，把它用於呈現台南 1999 通報的待孳清空地空屋資料。這些土地常常缺乏整理、雜草叢生，是滋生病媒蚊的溫床；然而，熱心民眾透過 1999 所回報的地點資訊往往有重複通報的情形，而且筆數眾多（1070 筆）、地方政府防疫人力吃緊，無力對此項資料進行對照匯整，也無法有效率地派工。kiang 的系統以群眾外包（crowd sourcing）的方式來解決資訊提供的問題，希望能協助政府有效準確地控制登革熱疫情。
> 事實上現在版本已經跟海地大地震當時有很大差異了，當時比較像是拼裝車，這次黑客松用的是最新版本，所以舒服很多 ;)
> [name=kiang]

> :+1: 不過我提海地大地震，80% 是想要借由知名國際事件來增加說服力這樣 XD
> [name=Johnson L]

> (Y)
> [name=kiang]


#### (一) 政府所釋出的開放資料


臺南市政府資料開放平台 [1999民眾通報待孳清地空屋資料](http://data.tainan.gov.tw/dataset/dengue-dist/resource/d0fb0392-1fc2-4866-80a1-cab1062a18ea)。目前共 1070 筆資料，最近一次更新是 2015/9/11。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0bf05c2c6d2808fc7499c45904c61bb3)
```
臺南市政府公佈的 1999 實際空屋資料共 1070 筆，圖中顯示前 10 筆。

```
然而，臺南市給出的資料裡，地址資訊跟民眾呈報的狀況混雜在一起，無法看出是否有重複呈報；行政機關僅能在可能有重複的狀況下逐案處理，造成行政資源的浪費。所幸臺南市政府將這份資料公開供民眾下載，kiang 的團隊也才有機會在黑客松活動來整理這份資料。


#### (二) 社群成果


kiang 的團隊透過語意處理取出地址的部分，使用 Google 提供的服務查詢經緯度，最後將 1070 筆民眾通報案件，點在地圖上，可供民眾、政府共同檢視參考。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_92029202c33db6902f145cf702aa01e6)
```
kiang 團隊製作的地圖視覺化。每一個藍色的標記點都是一個案件，而密集的案件則用顏色圈圈表示，中間的數字表示該處的案件數量。網址：http://ushahidi.olc.tw/views/map

```
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_98b67c7d2dd437dce0f4544f84b2e20c)
```
（承上）若我們放大檢視到里的層級，原本的顏色圈圈就會變成分開的藍色標記點。不難發現圖中仍有不少標示「2個案件」與「3個案件」的綠色圓圈，表示單一地點重複通報的情形並不在少數。

```
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_47cd0d0b5c00cc251f5d4eb3d1a01d37)
```
（承上）在台南東區，甚至有一處聚集了 9 個疑似重複的通報案件。在這裡的居民相當熱心，可能是在彼此不知情的狀況底下，前後通報了同一處空地。有了 kiang 的分析工具，市政府就能畢其功於一役，不需要往此處派工 9 次。

```
由於重複的狀況眾多，而且語義分析得到的地址不一定準確，kiang 的團隊也製作了一個編輯界面，可以讓群眾編輯地點，以及把一樣的案件「連結」在一起，讓案件重複的狀況能夠實際地被減少。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ffd6b35266d3b39fb27a7acab8bea976)
```
kiang 團隊製作的重複案件回報界面，圖中 A 與 E 地點相近，分別為「158 巷 135 號對面」與「158 巷 134 弄」，應該是針對同一處的通報。

```
> 報告的這個部分一直不斷強調「重複案件」「重複派工」的問題與解法，是希望可以讓行政機關了解，人民是來協助政府的，不只是監督而已；開放資料確實會耗費行政成本，但產生的價值，也可以讓行政單位受益。
> [name=Johnson L]


> 是說我發現台南的[資料來源](http://data.tainan.gov.tw/dataset/dengue-dist/resource/d0fb0392-1fc2-4866-80a1-cab1062a18ea)只給「立案案號」，但是[台南 1999 的 API](http://1999.tainan.gov.tw/OpenExplain.aspx) 要查詢案件進度，用的是「案件編號」（「使用說明」裡有 request example，格式跟案號完全不同⋯⋯），這樣我們在幫政府更正 1999 回報的同時，也不知道政府是不是已經處理好這份資料了 orz
> [name=Johnson L]

> 其實是有連結的，可以看我做的備份 [https://github.com/kiang/1999.tainan.gov.tw_datasets/](https://github.com/kiang/1999.tainan.gov.tw_datasets/)
> [name=kiang]

> 但說真的資訊並沒有揭露的很徹底，所以到底有哪些案子被隱藏，或是有哪些案子其實沒有處理完就被關掉，被關掉的也無法 reopen ，甚至案件之間的關聯脈絡也沒有對應的資訊可以瀏覽
> [name=kiang]



### 二、登革熱疫情視覺化，引發公眾討論


台南登革熱疫情已經持續數月，地方將人力優先投入救災，因此整理資訊、進行公開的人手嚴重不足。衛福部疾管署（CDC）在八月底開始接手，協助各縣市整理資料，每日釋出統計資料；開放資料的社群也對需要開放的資料提出了實質的建議 \[3\]。

\[3\] 見疾管署公開資訊的[討論文件](https://hackpad.com/CDC-RCq1iirBb6N)、[資料與應用匯整](http://beta.hackfoldr.org/1rbs-NLFxGvrT8whiwNIq-u3DB0MFV_zg58so5Ak1zdM)。


#### (一) 政府所釋出的開放資料


疾管局開放兩份資料，每日更新：

1、登革熱 1998 年起每日確定病例統計（104/10/6 時共 55103 筆）
2、登革熱近 12 個月每日確定病例統計（104/10/6 時共 33175 筆）

兩份資料格式相同，資料如下所示。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_81fda0e124fe37e417278e2f3965b854)
```txt
兩份資料都採取 CSV 格式，可以在試算表軟體中用表格的方式呈現，記載著每個案例的性別、大概年齡層、在哪裡感染的、什麼時候發病的，還有案例的居住位置的「最小統計區」中心點坐標。


```
#### (二) 官民討論互動


在[政府開放資料平台下方留言區](http://data.gov.tw/node/21025)，可以看到民眾一致的正面回應。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b87adbb43cad2193419e57dac1e99c74)
```
1998 年起每日登革熱資料頁面下方的民眾留言，正面而有建設性。網址：http://data.gov.tw/node/21025

```
疾管署在釋出個案資料的同時，也[向開放資料社群尋求建議](https://hackpad.com/CDC-RCq1iirBb6N)；上述的資料已經包含了下面由社群提出的需求：

1、在資料內增加「最小統計區」的中心點坐標，這樣就能在不侵犯個人隱私的狀況下，從資料中看出登革熱在街道之間的擴散趨勢。
2、每個個案加入年齡區段與性別欄位。
3、社群回報的十數筆資料內的村里名稱登打錯誤。

開發者社群是資料的第一級使用者。由於開發者的應用程式（無論是網站還是手機 App）直接面對一般大眾（第二級使用者），開發者對開放資料的每一項回饋，都是精確瞄準某一項價值而來——「若政府多加上某某資料欄位，身為開發者的我就能提供什麼什麼新功能讓大眾使用」。透過政府與開發者社群的通力合作，開發者能提供更多給一般大眾使用者、並且向政府回報資料的錯誤之處；政府能提升開放資料的品質，而一般大眾使用者則可以享有更高價值的應用程式。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_61081055e213f5c029389df3bd064e31)


#### (三) 社群成果


疾管署匯整了[至今的社群成果](http://beta.hackfoldr.org/1rbs-NLFxGvrT8whiwNIq-u3DB0MFV_zg58so5Ak1zdM)，茲舉數例簡介之。

1、[台灣登革熱 2015 地圖](http://kiang.github.io/TainanDengueMap/taiwan/points.html) (kiang)

前面「台南待孳清空地空屋資料」的作者，利用 2014 年底 lycheetw 製作的[高雄登革熱地圖](http://lycheetw.github.io/KaohsiungDengueMap/)，搭配疾管署新發佈的全台病例資料，做成台灣 2015 登革熱地圖。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8c15a8c3f9499fd8e54d1160476eeb13)
```
在地圖上點擊特定里，會顯示該里的統計病例數；下方的病例數統計長條圖也會跟著更新。


```
2、[發病日病例數 v.s. 氣象站氣溫圖](https://www.facebook.com/groups/odtwn/permalink/1320531584627923/)

民間學者則利用開放的登革熱病例數，與[中央氣象局的觀測資料](http://e-service.cwb.gov.tw/HistoryDataQuery/index.jsp)一同比對，製作成圖表，引發公眾討論疫情成因。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bb1d9e534ac732a28fd5cf4f5cbce20a)
```
網友將登革熱資訊與中央氣象局的氣象站氣溫合在一起，與社群成員觀看趨勢與討論。

```
3、[即時病例 \+ 噴藥資訊](http://real.taiwanstat.com/dengue-spatial-temporal/) (用數據看台灣)

數據視覺化專題網站「用數據看台灣」則是選擇把病例數比較顯著（數量超過整體 3%）的區域標記出來，並且另外結合臺南市開放資料集的噴藥資料集、病媒蚊資訊\[4\]做整體資料呈現。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_da5aa1772fb9db225c74871da4424ea4)
```
橘紅色區域為3天內病例數達到整體3%的範圍。綠色與橘色的小蟲標記是病媒蚊資訊，點擊後可以看詳細數據。藍綠色的小圓圈是七天內噴藥區域。

```
\[4\] [臺南市 104 年登革熱噴藥場次](http://data.tainan.gov.tw/dataset/104-df-chemical-control)有 104 年 8~10 月每個月的派工日期、地點、人力等資訊；[104 年登革熱病媒蚊密度調查](http://data.tainan.gov.tw/dataset/2015-df-mosquito-density)則有以周為單位的密度調查表。

#### (四) 案例觀察


以上視覺化的網站，都在[網路上](http://beta.hackfoldr.org/1rbs-NLFxGvrT8whiwNIq-u3DB0MFV_zg58so5Ak1zdM)完全開放存取。自登革熱疫情爆發以來，民眾人人自危，其中一個造成恐慌的緣由，就是不知道自己所在的區域是否是登革熱的熱區。有了這些官方資料與民間的應用，民眾在居住或前往台南時，就可以參考這些地圖，對自己的活動區域的疫情熱度建立正確的認知，並依此準備必要的自我防護。


### 三、臺北蘇迪勒、杜鵑颱風災情與恢復狀況


蘇迪勒颱風在 8/8 臨晨四時登入；兩天前的 8/6，台北市政府資訊局就介接消防局的 EOC 資料，製作成[開放的資料集](http://beta.hackfoldr.org/TPEDisasterSummary)，並且每 30 分鐘更新一次。


#### (一) 政府所釋出的開放資料


臺北市政府資訊局釋出的消防局 EOC 資料集，包含六個資料集：

1、某時段的翡翠水庫資料：包含水庫時水位、入流量、出流量、蓄水量等資訊，每 30 分鐘更新一次。
2、最新撤離勸離人數統計表：包含撤離速報發送時間、地點、撤離時間、預計撤離人數、實際撤離人數、收容處所等資料，每 5 分鐘更新一次。
3、最新避難收容所開設統計資料：包含收容場所、開設起訖時間、累積收容人數、聯絡方式等等資料，每 5 分鐘更新一次。
4、最新災害專案災情資料：包含災情種類細項名稱（如「廣告招牌掉落」）、災害地點經緯度、是否已處理完畢、發生時間等等資料，每 5 分鐘更新一次。
5、最新匯報指示決策資料：包含會報名稱、會報主席、指示事項（如「請各單位準備相關救災設備」這樣的文字），每 5 分鐘更新一次。
6、最新受損情形資料：包含鄉鎮市區別（如「信義區」）、累計停水戶數、累計停電戶數、累計停話戶數、累計瓦斯受影響戶、未處理完成停水、停電、停話、瓦斯戶數、速報發佈時間資料，每 5 分鐘更新一次。

詳細資料列表與範例載於[規格說明書](https://drive.google.com/file/d/0B3Whe0iG1C1UaThUTzR3aXBzUWs/view)。


#### (二) 社群成果


台北市資訊局[在社群發佈資料集資訊](https://www.facebook.com/groups/odtwn/permalink/1285210781493337/)，並收集了 7 項[網友作品](https://www.facebook.com/liu.jean.94/posts/10153701004245799)。目前各個資料來源與網站都仍然可以運作，只是時至今日已經沒有 EOC 的案件數，所以各作品都是空空如也的狀況。目前僅「最新災害專案災情資料」仍有兩筆「1002 大雨」專案的災情資訊。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a17c78d9189d8d08371365d4622c563a)
```
由 Kuro Hsu 製作的災害動態資訊，介接「最新災情資料」，點擊個案可以看地點與狀況。在颱風襲擊的當周，整張地圖密佈著地圖標記點，所幸已全數恢復。圖中兩筆淹水資訊，都是 10/02 大雨的災情。


```
### 四、雙北八仙塵爆

> [http://beta.hackfoldr.org/627pray/](http://beta.hackfoldr.org/627pray/)
> [name=Johnson L]


今年 6/27 晚上，八仙樂園發生粉塵爆炸意外，400 名燒燙傷傷患經過一夜檢傷、急救、分級轉診，在 6/28 有了完整的傷患名單與醫院消息，需要公告發佈給民眾，並呼籲一般民眾就醫時，請避免前往正全力搶救八仙傷患的醫院。

#### (一) 開放資料來源


6/28 中午，台北市資訊局將傷患資料製成[開放資料](https://github.com/kptaipei/coloe-issue-20150628)，公開上網，並且在 6/28～6/30 內更新了十餘次。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_670b5f00f14120167464628602d4cb8f)
```
台北市資訊局開放的資料中，有收治單位、去識別化姓名、檢傷與即時動向，可供民眾查詢家屬動向。


```
#### (二) 社群成果


台北市的[八仙塵暴專區](http://www.gov.taipei/mp.asp?mp=2015FFC)，列出了 9 個民間社群網友所提供的查詢系統。其中 YuTin Liu 的開放資料查詢系統最為完整，將「家屬尋人」、「醫院收容概況」與「捐血資訊」在一個網站裡同時呈現；另外，這個查詢系統在手機上，也可以正常瀏覽。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3585d28747f63e97960b09a75a4266b5)
```
「家屬尋人」功能，可以輸入名字查詢，即會顯示即時動向、醫院電話、該區社服中心電話。某些醫院週邊有旅館願意提供家屬免費住宿，點擊「家屬免費住宿」可以獲得旅館資訊。


```
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_48b82d7e41c940325bfecbd379a7cc7f)
```
「醫院概況」功能則是使用同一份傷患資料，統計每一間醫院的重傷、中傷、輕傷、加護病房、一般病房的八仙傷患人數，可以得知每一間醫院所承受的八仙病患人數，還有八仙事件傷患整體的復原進度。

```
> [https://www.facebook.com/g0v.tw/posts/937305806310706:0](https://www.facebook.com/g0v.tw/posts/937305806310706:0)
> [name=Johnson L]

> Like 1482, 444 shares
> [name=Johnson L]

> hackfoldr 的 google analytics 流量報表？
> [name=Johnson L]

> 此項應該是枚舉範例裡，使用率最高的服務，希望能有數據 support。
> [name=Johnson L]



#### (三) 案例觀察


八仙塵暴事件與前述範例不太相同。前述災害都有較長的應變時間、政府有應對經驗以及 SOP，但塵暴沒有。政府在第一時間做的就是統計與安置，光是收集正確的數據就已經相當困難了，更遑論訊息的公告周知；但是在事件發生的當下，家屬們最需要知道的，莫過於政府手上所擁有的正確資訊。這一次市府收集資訊之後，選擇將手邊資料做個資模糊化處理之後直接開放，讓民間自行建構自己所需要的查詢系統，讓市府不需花費過多的資訊人力，就能讓各方訊息有效匯流整合，是一個相當經典的官民分工合作案例。


### 五、小結


上述案例，後三者是與災防直接相關的，其中兩例是由台北市政府底下的一級機關——資訊局所促成的跨局處合作，新北市政府資訊中心的所在的政府位階，職權上或許較難在災害發生時做出這樣的平行整合，但下轄的 1999 為民服務資料仍然有公開的價值，如台南 1999 的待孳清空地，就在登革熱防疫上能夠派上用場。

近年開放資料的國內運用實例如雨後春筍般般出現，足見開放資料社群的活躍程度，以及開發者社群、新創團隊替政府建構資訊佈達系統的熱情；民間也對 1999 開放資料有著[相當的期待](http://data.gov.tw/node/8019)。目前 1999 資訊公開做得最好的是[臺南市](http://1999.tainan.gov.tw/OpenExplain.aspx)，除了開放資料集之外，也有可供應用程式介接的伺服器（API server），不過跟國際城市的開放 311 資訊相比，仍然有一段落差；台北市也有開放 [1999 的派工資料](http://data.taipei/opendata/datalist/datasetMeta?oid=b796f87a-0ed8-4e57-89f6-225a4941b1ed)，正朝[及時更新](https://www.facebook.com/groups/odtwn/permalink/1338029269544821/)努力。希望新北市可以在 1999 開放資訊方面迎頭趕上，並與國際接軌。


## 參、國際 open311 規範簡介


國際間提供 1999 / 311 服務的城市越來越多。紐約市的非盈利組織 OpenPlans 為 311 服務設計了一種開放資料的格式規範，能夠適用於任何有 1999 / 311 服務的城市，並且設計中有考慮到查詢與新增陳情案件的功能。目前已經有芝加哥、舊金山、華盛頓特區、多倫多(加拿大)、波昂(德國)等 [15 個城市](http://wiki.open311.org/GeoReport_v2/Servers/)採用 open311 規範來呈現 311 公開資訊。


### 一、資料格式

> 以資源為中心來做簡化，給非資訊人員看。
> [name=Johnson L]


根據 [Open311 GeoReport v2](http://wiki.open311.org/GeoReport_v2/) 規範，機關應該要開放兩類資料：Service 與 Service Request，以及資料使用者能夠怎麼取用這些資料。


#### (一) Service


Service 就是政府在 311 上提供的服務種類，舉凡路燈維修、交通號誌維修、路面平整，都是一項 Service。每一個 Service 裡要包含服務名稱、服務簡介說明等資訊。


#### (二) Service Request


Service Request 就是一件一件的陳情案。一筆 Service Request 資料包含所屬 Service 名、處理狀態（未處理、已處理）、處理情形、陳情內容、地址、經緯度等資料。


#### (三) 如何取用這些資料


[Open311 GeoReport v2 規範](http://wiki.open311.org/GeoReport_v2/)設計了一組應用程式界面（API），讓開發者的程式能查詢或新增陳情案。提供開放 311 資料的政府機關需要架設一檯網頁伺服器，當民間開發的應用程式（網頁或行動裝置 app）造訪這些網頁連結的時候，政府的伺服器要將程式所要求的 Service 或 Service Request 內容傳去給應用程式。這檯網頁伺服器要與政府內部使用的現有 311 資料庫更新同步所需要的資料，這樣網頁伺服器才能提供民間應用程式最新的數據。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9596584dfeac507eebd2b87efca7960f)


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ae6f4a481beacd1cb1afed71b5fb7550)
```
舊金山政府的 open311 伺服器所回傳的 Service Request 資訊。圖中的瀏覽器向舊金山政府 open311 伺服器詢問「2015/10/1 以來的所有 Service Request 有哪些？」，而下面每一對大括號 `{...}` 裡的就是一筆陳情案。圖中第一筆回報的是路燈維修，有詳細的地址與經緯度，而政府還沒處理此陳情案（status: "open"）；第二筆則是有人回報人行道上有用過的用過的針頭（"Used needle on sidewalk"），並且附上照片網址。政府機關的處理情形則是「處理完成。沒有看到針頭。」（"Case Closed. Case Completed. resolved: nothing found."）

```
民間的應用程式也可以用[Open311 GeoReport v2 所規範](http://wiki.open311.org/GeoReport_v2/)的方式來對政府的 open 311 伺服器發送新陳情案。若要開發可以向政府送陳情案的第三方應用程式，開發者要先跟政府登記申請開發金鑰（API Key），因此政府可以透過 API Key 來控管第三方應用程式發送的陳情案。


### 二、Open311 的應用


Open311 GeoReport v2 建立了國際通用的標準，每個城市都使用相同的格式來呈現 311 的資料；依照 open311 標準建構出來的應用程式，也可以跨程式通用。


#### (一) "[FixMyStreet](http://fixmystreet.org/)" by mySociety


英國的公民計畫 mySociety 開發了 FixMyStreet 查詢與舉報系統，這個系統可以透過 open311 規範，與任何政府 open 311 伺服器介接，顯示 311 陳情案件與將 311 案件舉報給政府；由於此系統是基於網站的應用程式，因此不用安裝就能在手機、平板與桌面環境運作。由於 FixMyStreet 是開放原始碼的系統，大家都可以免費地架起 FixMyStreet，這也吸引了全球[地方政府或地方機關](http://fixmystreet.org/sites/)團體架設 FixMyStreet 做為 311 服務的網路與手機終端介面。德國的非營利組織則開發了另一套使用 Open311 的網頁應用程式 [Mark-a-spot](http://www.markaspot.de/en)，同樣做為開放原始碼專案，與源自英國的 FixMyStreet 分庭抗禮。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_043557902f7b77300bffd7b5afe5b46e)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_dd69bc58c200e9213276e91cbd4f22d3)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_32cc8d9b8364c863f06805e4eebeb5d6)
```
 英國蘇格蘭大城市愛丁堡(上)、瑞士首都蘇黎世(中)、馬來西亞城市書邦在也 (下) 的 311 案件系統，都是使用 mySociety 所開發的 FixMyStreet 系統。拜 FixMyStreet 為開放改作的開放原始碼專案所賜，各城市都各自做了一些介面上的客製化，也將介面的語言修改成該國的母語。


```
#### (二) "Chicago Works for You" by Smart Chicago Collaborative


芝加哥公民組織 [Smart Chicago Collaborative](http://smartchicagocollaborative.org/) 使用芝加哥政府的 Open311 服務，替芝加哥政府做了一個非常精美的案件視覺化網站 [Chicago Works for You](http://chicagoworksforyou.com/)，顯示每天芝加哥政府接收到的 311 陳情案。視覺化時使用行政區作為區分，配色單純但清晰，帶給民眾「芝加哥政府每天都照顧著所有行政區的居民」的感受。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fe641d5b0d124a1557f04dbeec97f592)
```
chicagoworksforyou.com 一連進去的畫面，左邊列出所有芝加哥 311 的服務，右邊則是案例數統計。有趣的是 0 request 也有上顏色，而且顏色跟其他數量都很接近，這樣看起來好像全市每區每天都至少有一個 311 案件要處理一樣，讓使用的民眾感受到 Chicago is the City that Works.

```
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_12b58e05ced92fedf536694f0a21e10f)
```
點擊個別市政服務，可以看到對該市政服務的詳細介紹，是為民服務業務的優良曝光機會。左邊的長條圖，是各行政區（Ward）一周以來案例數。


```
#### (三) 新創業者加值應用


311 開放資料，也讓有才華的新創業者可以一展長才，介接政府的 Open311 伺服器，並且提供從個案管理、伺服器架設到行動裝置應用程式的全套 Total solution，如 [Connected Bits](http://www.connectedbits.com/)、[PublicStuff](http://www.publicstuff.com/) 與 [SeeClickFix](http://gov.seeclickfix.com/) 等等。開放資料的加值應用是國內資通訊創業者小試牛刀的寶貴機會，不但可以增加政府服務的價值，也可以讓新創團隊獲得群眾關注，民眾也得以享受到創業者用熱情與專業創造的高優質應用程式所帶來的便利生活。開放資料在提升公眾利益的同時，更能促進資通訊產業的創新發展。


## 肆、新北市開放 1999 計劃草擬


新北市 1999 自 2008 年開辦以來已超過 8 年，背後已經有穩定的資訊系統在支持 1999 案例的建檔與追蹤。下面提出開放 1999 的計劃，嘗試以**不更動 1999 現有資訊系統**為原則，提出開放 1999 資料的解決方案。計劃分近程與遠程兩階段，「先求有、再求好」，第一階段先研究如何釋出資料並實際釋出，第二階段再架設 Open331 伺服器，提供民間社群開發者介接。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_96848349bdf8c584e76c61f3b8027061)

這份計劃僅會提及，若要開放 1999 資料，大概需要有哪些事項要執行。實際的執行者、執行時程、執行細節，需要在確認現有資料庫的實際內容之後，才有辦法進行規劃。


### 一、近程計劃


#### (一) 整理過去 1999 資料，公佈至[新北市政府資料開放平台](http://data.ntpc.gov.tw/)


[新北市政府資料開放平台](http://data.ntpc.gov.tw/)上面目前有 261 個開放資料集，包含市內土地公告現值、AED 設置位置、福利補助資訊等等，提供方便程式處理的 XML、JSON 等格式，或讓非程式人員也能著手分析的 Excel 資料檔下載。近程計劃的第一步，就是將現有的 1999 歷史資訊，整理成資料集，放到新北市政府資料開放平台之上。

1999 的資料大致分成兩大類：「1999 服務種類」與「陳情案件」。參考 Open311 的資料集與欄位設計後，以下提出新北市 1999 開放資料集的欄位與內容。
> Service（服務種類）資料：路面損壞、交通標線不良⋯⋯等等
> [name=Johnson L]

> Service Request 資料：實際案件，以及處理方式
> [name=Johnson L]



1、1999 服務種類（Service）

此項資料相當於 [Open311 GeoReport v2](http://wiki.open311.org/GeoReport_v2/#get-service-list) \`GET Service List\` 的回傳資訊，希望能整理成類似下面這樣的資料表：

| service_code | service_name | description | keywords | group |
| --- | --- | --- | --- | --- |
| 1001 | 妨害安寧案件 | 如狗吠、人的噪音等 | 噪音 | 社會安寧 |
| 1002 | 違規停車處理 |  | 違規停車,違停,亂停 | 違規處理 |
| 1003 | 路霸排除 | 需要及時排除的可移動式路障、出入口受阻 | 路霸,路障 | 違規處理 |
| 2001 | 交通號誌故障 | 重大路口全熄、原紅黃綠三色運作路口跳閃光、一直紅燈不變燈、紅綠燈同亮、燈號亂跳。 | 紅綠燈,號誌燈 | 交通號誌問題 |
| 2002 | 交通號誌桿損壞、傾斜 |  | 紅綠燈,號誌燈 | 交通號誌問題 |
| 3001 | 路燈未關 |  | 路燈 | 路面與路燈 |
| 3002 | 路燈不亮 |  | 路燈 | 路面與路燈 |
| 3003 | 路面損壞 | 路面有坑洞、龜裂、凹陷、人手孔蓋週邊破損、人手孔蓋欠平順等等 | 道路,路面,柏油路,人手孔,人孔蓋 | 路面與路燈 |
| 3004 | 交通標線問題 | 交通標線磨繪不清或設置不當 | 道路標線,標線,紅線 | 路面與路燈 |
```
表格內文字來自新北市 1999 市政快速服務的文件。

```
表格欄位說明如下：

- \`service_code\`：識別代碼，每個服務不同，用於把「陳情案件」與「服務種類」連接在一起。
- \`service_name\`：給使用者看的服務名稱。
- \`description\`：服務簡介。
- \`keywords\`：幫助使用者辨認、尋找服務的標籤、關鍵字或縮寫。關鍵字間以半行逗號`,` 分隔。
- \`group\`：服務所屬分類。例如說數個服務都跟衛生有關，那這些服務的 \`group\` 欄位就寫「衛生」。


2、陳情案件（Service Request）

此項資料相當於 [Open311 GeoReport v2](http://wiki.open311.org/GeoReport_v2/#get-service-list) \`GET Service List\` 的回傳資訊，希望能整理成類似下面這樣的資料表：

| service\_request\_id | status | status_notes | service_name | service_code | description | agency_responsible | service_notice | requested_datetime | updated_datetime | expected_datetime | address | zipcode | lat | long | media_url |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 591220 | closed | 新莊區公所回覆如下：「化成路531巷為私人土地,通報位址應屬五工路66號旁道路,為私人土地」謝謝你對本市道路之關心 | 路面損壞 | 3003 | 進入化成路531巷裡面，從巷口一直進去到貨運公司前面，沿路都坑坑疤疤的 | 新莊區公所 | 工務局將在4小時內先設置安全維護措施，並於 4 日內修復 | 2015-06-08T10:17:00+08:00 | 2015-06-09T10:03:00+08:00 | 2015-06-12T10:17:00+08:00 | 新北市新莊區五工路化成路531巷 | 242 | 25.0632602 | 121.4581256 |  |
| 591236 | closed | 僅方正修復 | 路面損壞 | 3003 | 淡金路一段上，水源接口到北新路口，往北方向沿路都很爛 | 陳立苑 | 工務局將在4小時內先設置安全維護措施，並於 4 日內修復 | 2015-06-08T10:28:00+08:00 | 2015-06-15T16:40:00+08:00 | 2015-06-12T10:28:00+08:00 | 新北市淡水區淡金路一段 | 251 | 25.1970513 | 121.445542 |  |
| 635827 | open |  | 路面損壞 | 3003 | 生東路上(板橋往中和方向)接近中山路一段，該處轉角的柏油路面有2個約手掌大的小坑洞，已畫白線記號 (.) |  | 工務局將在4小時內先設置安全維護措施，並於 4 日內修復 | 2015-10-08T12:16:00+08:00 |  |  | 新北市板橋區漢生東路 | 220 | 25.01271 | 121.4689416 |  |
| 635880 | closed | 僅修補坑洞 | 路面損壞 | 3003 | 鶯歌路鳳鳴橋下有鐵板 | 鶯歌區公所 | 工務局將在4小時內先設置安全維護措施，並於 4 日內修復 | 2015-10-07T12:00:00+08:00 | 2015-10-08T13:52:00+08:00 | 2015-10-11T12:00:00+08:00 | 鶯歌區 鶯歌路鳳鳴橋 | 239 | 24.9722425 | 121.332313 | [http://rdm.ntpc.gov.tw/ROAD/Upload/ConstructionPic/201510/130887571466962500.jpg](http://rdm.ntpc.gov.tw/ROAD/Upload/ConstructionPic/201510/130887571466962500.jpg) |
```
表格內容整理自「路平報馬仔」實際案例：
http://rdm.ntpc.gov.tw/ROAD/SatisfySurvey.aspx?id=591220
http://rdm.ntpc.gov.tw/ROAD/SatisfySurvey.aspx?id=591236
http://rdm.ntpc.gov.tw/ROAD/SatisfySurvey.aspx?id=635827
http://rdm.ntpc.gov.tw/ROAD/SatisfySurvey.aspx?id=635880


```
以上欄位有一些是政府回覆的內容，有些是民眾填寫的內容。表格欄位說明如下：

- \`service\_request\_id\`：案件編號。
- \`status\`：目前案件狀態。\`open\`：剛被民眾回報；\`closed\`：已處理完畢。
- \`status_notes\`：此案件狀態的解釋或說明。
- \`service_anme\`：這個案件所屬的，給使用者看的服務名稱。
- \`service_code\`：這個案件所屬的服務的識別代碼。
- \`description\`：案件陳情內容。
- \`agency_responsible\`：承辦單位或承辦人。
- \`service_notice\`：陳情人通報結束後，告知陳情人此陳情應該會如何被處理的資訊。
- \`requested_datetime\`：陳情人通報時間。w3 日期格式。
- \`updated_datetime\`：案件的最後更新時間。
- \`expected_datetime\`：案件原定處理完畢的時間。如[快速服務業務](http://www.rde.ntpc.gov.tw/web66/_file/1397/upload/1999web/a-08-1030609new.html)都有規定完成時間。
- \`address\`：地址資料。
- \`zipcode\`：陳報地點的郵遞區號。
- \`lat\`、\`long\`：所陳報地點的緯度、經度（[WGS84](https://en.wikipedia.org/wiki/World_Geodetic_System) projection）
- \`media_url\`：陳報案件所附的照片或影片 URL。


#### (二) 程式自動發佈每小時最新資訊


對於陳情案件（Service Request）資料，從現有資料庫轉換到上述格式，大部分只是欄位名稱的的代換、自動查詢經緯度等作業，應該可以使用程式腳本自動化處理，每隔一小時就從現有 1999 資料庫截取新陳情案件資料，轉換成上面的格式之後，自動發佈到新北市政府資料開放平台。


### 二、遠程計劃


進程計劃提供民眾資料來做分析；但若想要支援新增陳情案件，我們會需要建立起一個符合 Open311 GeoReport v2 的 Open311 伺服器。這樣的伺服器必須符合下面性質：


#### (一) 提供查詢用的應用程式界面（API）


[Open311 GeoReport v2](http://wiki.open311.org/GeoReport_v2/) 規定了伺服器應該要提供 \`GET Service List\`、\`GET Service Definition\`、 \`GET Service Requests\` 與 \`GET Service Request\` 四個資源的取用方式、伺服器應該接受與回傳的資料欄位等等。由於這些程式界面背後介街的資料格式與近程計劃中所規劃的一模一樣，因此若近程計劃有執行到位，那麼近程計劃中所產出的資料集以及自動轉換格式程式，都可以直接沿用。

當查詢用 API 完成之後，民間開發者就可以用 [FixMyStreet](http://fixmystreet.org/) 或其他支持 Open311 客戶端應用程式，將過往與現在新北市 1999 的業務製作精美的視覺化圖表，透過展示案例來顯示新北市政府為民服務的歷程軌跡。


#### (二) 提供報案陳情的應用程式界面（API）


[Open311 GeoReport v2](http://wiki.open311.org/GeoReport_v2/) 規定了伺服器若要接受民眾報案陳情，應該接收的資料欄位與格式。這個部分是整個遠程計劃中，需要最多工夫的一步——Open311 伺服器不只是跟現有 1999 資料庫拿資料而已，它還要知道如何把新的陳情案寫入現有 1999 資料庫，才能將第三方應用程式透過 Open311 伺服器送出的陳情案，整合進現有的 1999 資訊系統中。

Open311 GeoReport v2 提到， Open311 伺服器應該提供 [Service Definition 資訊](http://wiki.open311.org/GeoReport_v2/#get-service-definition)，來規定送出各種不同服務的陳情案時，應該要請使用者填入哪些欄位。搭設 Open311 的單位可以參考現有[路平報馬仔系統](http://rdm.ntpc.gov.tw/Road/NewCase.aspx)給使用者填寫的欄位，來設計所需要的 Service Definition。


#### (三) 查詢用的應用程式界面（API）以 CDN 承受流量


由政府架設 Open311 伺服器，在特殊情況（如颱風、地震等特殊期間）下會有龐大流量需求。一般的高流量服務都會租用 CDN（內容網路遞送服務）來承受大部份的流量，CDN 遍佈各地的機房部點與負載平衡機制會確保在極多人同時連線的狀況底下，仍然能將資訊傳遞給使用者。國內中華電信有[提供 CDN 服務](http://www.cdn.hinet.net/info-1.html)，國外也有 cloudflare 免費 CDN 服務可供選擇。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e1d033db1ff7a4da47dadc7707827703)


#### (四) 中文版技術文件


為促進國內開發者介接新北市 Open331 伺服器來開發加值應用，新北市需要公佈伺服器的應用程式界面（API）技術文件。所幸技術文件所需要記載的所有資訊，在 Open 331 官方資訊站上都已經有了[英文版本](http://wiki.open311.org/GeoReport_v2/)，市府只需請技術人員粗略翻譯之後，連同原本英文版的連結一併公佈在[新北市政府資料開放平台](http://data.ntpc.gov.tw/)即可。


#### (五) 鼓勵與搜集 App 範例


Open331 官方資訊站搜集了採用 Open331 規範來與伺服器進行溝通的[開放原始碼應用程式清單](http://wiki.open311.org/GeoReport_v2/Resources/)。新北市政府也可以拋磚引玉，直接使用開放原始碼的 [FixMyStreet 專案](http://fixmystreet.org/) 或 [Mark-a-spot](http://www.markaspot.de/en)，架設新北市版本的 1999 視覺化網站；但市府無須擔心，官方示範會成為 1999 應用的絕響。
> FixMyStreet 程式有點混亂，建議用 Mark-a-spot
> [name=kiang]

> 好的！我還沒實際看過 code，感謝 Kiang 的經驗分享！
> [name=Johnson L]

> 這個做中文翻譯的苦主說的 XD - [https://github.com/misgod/fixmystreet](https://github.com/misgod/fixmystreet)
> [name=kiang]

> 不知道為什麼 missing 了 QQ 補個剛剛 google 到的 blog post xd
> [name=Johnson L]

> [http://35around.blogspot.tw/2014/06/311.html](http://35around.blogspot.tw/2014/06/311.html)
> [name=Johnson L]

> 我發現 [Mark-a-spot](https://github.com/markaspot/mark-a-spot) 是 GPL 耶，希望是政府不介意把改過的 Mark-a-spot 也 open source。
> [name=Johnson L]


以率先開放 1999 資訊的臺南市為例，2014 年就有[熱心的開發者 Cuda](https://www.ptt.cc/bbs/Tainan/M.1432738997.A.793.html) 替台南 1999 開發了[免費的 Android 應用程式](https://play.google.com/store/apps/details?id=tn.opendata.tainan311)，平均評價是 4.3 / 5，不但持續更新維護，而且也[開放專案原始碼](https://github.com/newmanchen/tainan-1999)供大家檢視、協作。由於作者 Cuda 以富有彈性的 Apache-2.0 授權條款釋出專案的原始碼，任何開發者都可以基於 Cuda 的作品推出新北市版的 app，或協助 Cuda 將新北市的開放 1999 服務直接整合進 Cuda 的 app。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c76fafe59d138e6bb46e3641230df584)
```
熱心開發者 Cuda 所開發的台南 1999 app。一般民眾下載這個 App 之後，在路上看到違規停車或路面問題需要修補，只要拿起手機就可以輕鬆舉報，拍照、定位、送出陳情案，一氣呵成。

```
新北市政府可以效仿[台北市八仙塵爆專區](http://wiki.open311.org/GeoReport_v2/Resources/)，主動搜集這類使用開放 1999 服務的案例，鼓勵民間對公共事務的參與，也向協助市府推動 1999 服務的開發者們致謝。


### 三、開放 1999 的挑戰


以下列出開放 1999 過程中可能會遇到的阻力，以及可能的解法。


#### (一) 資料內容方面


一份開放資料的價值，不是在於開發者們做了哪些應用，而是在資料的品質——資料本身有多少值得運用的內容。若資料久久更新一次，或資料太少，民間的開發者也巧婦難為無米之炊。


1、內容品質

從現有的[新北市路平報馬仔系統](http://rdm.ntpc.gov.tw/ROAD/SatisfySurvey.aspx?id=591220)來看，裡頭的絕大多數都可以對應到 Open311 所規範的 Servie Request 資料欄位中；然而各段資料的填寫方式，不一定方便程式處理。以下面[路平報馬仔的通報案件](http://rdm.ntpc.gov.tw/ROAD/SatisfySurvey.aspx?id=591220)為例：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_40bcb727db192782c52e1bce6c8e4a0e)
```
個案網址：http://rdm.ntpc.gov.tw/ROAD/SatisfySurvey.aspx?id=591220

```
熱心民眾填入的「反應地點」並不是一般常見的地址，一般的地址解析服務不一定有辦法將這樣的服務轉換成精確的經緯度；政府的「回覆說明」欄位，實際的內容只有新莊區公所的回覆部分。

政府在開放資料前，可以評估整個現有資料庫需要清理的資料占有多少比例、思考是否應該播用人力來進行資料清理（data cleaning）。不過，以 1999 派工資訊來說，上面通報案件這樣的品質雖然美中不足，但也堪用；畢竟即使臺南市政府的 [1999民眾通報待孳清地空屋資料](http://data.tainan.gov.tw/dataset/dengue-dist/resource/d0fb0392-1fc2-4866-80a1-cab1062a18ea) 這種地址跟其他文字敘述完全混合在一起的資料集，也有使用的價值。新北市 1999 資料集開放前是否需要資料清理、應該清理到如何的程度、以及要花多少時間來進行清理，需要實際檢視資料集內容才有辦法估算，不過對於已經相當結構化的 1999 資料庫而言，估計不會有「資料亂到毫無價值」的情形發生。
> 如果能夠，其實把所有住址轉座標的資料變成一份開放資料，並且持續更新，相信會蹦出更多應用。之前[主管單位的說法](https://www.facebook.com/groups/odtwn/permalink/1314631875217894/) ，這是縣市權責，如果縣市單位能夠直接開放應該是美事一樁（當然，雖然我也知道這是踢皮球遊戲）
> [name=kiang]


2、更新頻率

更新頻率也是影響開放資料本身價值的一環，若更新頻率越快，因為提供的資料即時性高，能做的應用可能就更寬廣；每小時或每分鐘更新的 1999 資料集，透過精準且即時的案例自動分類器，甚至還有可能能成即時重大災情佈告欄系統！

然而，要達成每天、每小時或甚至每分鐘的更新，整個開放資料的發佈流程，就必須完全以程式自動化。完全自動化的資料處理，需要克服以下挑戰：

- 現有 1999 資料庫需要以程式界接，才能定時自動截取新案件（近程計劃需要），以及寫入新陳情案件（遠程計劃需要）。
- 若評估 1999 的資料需要資料清理，那清理作業也要能以程式自動完成。
- 近程計劃中所使用的「[新北市政府資料開放平台](http://data.ntpc.gov.tw/)」，也需要支援以程式自動發佈更新的功能。

上面提及的事項都與現有架構與現有資料庫內容有關，要在實際檢視系統與內容之後才有辦法評估可行性。


3、第三方新增資料的疑慮

在遠程計劃裡，我們預計會提供報案陳情的應用程式界面（API），讓開發者所開發的應用程式也能發送新的陳情案進現有 1999 資料庫。政府方面或許會對開放第三方新增資料有疑慮，認為這會讓 1999 資料庫中充斥著測試用假報告或惡作劇報告。

Open311 GeoReport v2 規範有考慮到政府方控管第三方新增資料的需求，在發送新陳情案的 API 中，設計了開發金鑰（API Key）機制——開發者需要先跟政府取得開發金鑰（由數個英文與數字的亂數字串），寫進程式裡發送陳情案的機制當中，因此政府可以追蹤第三方新增的陳情案，是由哪個開發者所開發，必要時可以把帶有同一份 API key 的陳情案全部調出，逐條檢驗或刪除，甚至是禁止特定 API key 對 Open311 server 再發送新的陳情案。政府也可以透過規定開發者發送測試用假報告的格式，或提供獨立的測試伺服器，來滿足開發時的測試與除錯需求。


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_97833a7d862d2e7ebff4d56b77a0ddc3)
```
多倫多政府給開發者申請 Open311 API key 的頁面（網址：https://secure.toronto.ca/webwizard/start.jsp?\_wiz\_id=API\_key\_request）。除了搜集基本資料、軟體預定用途之外，也附上了額外的服務條款以及技術須知。

```
> 突然發現 Toronto 管好多，如果要開發一個可以送 service request 的 app，你還要把 app 寄給當局請他們幫你測試，政府確定你的 app 沒問題之後才會給你正式 api key⋯⋯
> [name=Johnson L]

> 這是有好處的，可以確保使用者體驗，但反向就是管太多吧
> [name=kiang]



#### (二) 法律方面



1、開放資料運用相關規範

政府機關或許會認為資料開放出去，還要另外設計使用規範，相當費時耗力，又不見得有成效。確實，政府的資源開放出去之後，如果沒有使用規範來明定資料使用者與政府之間的權利義務，確實會在未來衍生責任劃分的問題。所幸，國發會已經在 104 年 7 月頒訂《[政府資料開放授權條款](https://政府開放授權)》明定政府授與開發者的權利，以及開發者使用政府資料時所應盡的義務，並且替提供資料的政府訂下免責防火牆。

> 註：新北市政府資料開放平台上，目前資料大多以 CC BY 3.0 釋出，沒有政府（資料提供方）的免責條款，對資料使用的規範也只有「[不得違法、不得違背善良風俗、不得誤導](http://data.ntpc.gov.tw/ns/qa/detail?oid=4FFEBB68-257A-476E-BABC-ED017FC1E2FA)」等概括性的規定。然而，《[新北市政府電子資料公開作業要點](http://www.rde.ntpc.gov.tw/_file/1397/SG/26216/D.html)》卻有資料不得轉錄、重製與交予他人使用的規定，其實與 CC BY 3.0 好像不太 compatible。
> [name=Johnson L]



2、個人資料保護法

> 路評報馬仔資料集絕對沒問題，因為已經開放了。
> [name=Johnson L]

> 法律界對 ETC 資料開放的反彈
> [name=Johnson L]

> [https://www.facebook.com/liu.jean.94/posts/10153701004245799](https://www.facebook.com/liu.jean.94/posts/10153701004245799)
> [name=Johnson L]

> 1999 使用者條款是否有授權？
> [name=Johnson L]


這裡我們來檢視前述進程計劃與遠程計劃，是否含有個人資料。近程計畫中，政府將開放 1999 資料的「1999 服務種類」（Service）與「陳情案件」（Service Request）兩項資源，其中前者是政府服務的介紹，由市民提供的資料是後者——陳情案件。

陳情案件（Service Request）在現有 1999 資料庫裡面，或許有記錄報案人資訊的欄位，以供告知處理結果；然而，近程計劃中將開放的 16 個欄位，僅有報案人描述案件的資訊（文字敘述、地點、照片）與政府機關的回應（處理情形、處理說明）。因此，近程計劃所釋出的資料裡頭，並沒有任何報案人提供的資訊符合[個資法第二條定義](http://law.moj.gov.tw/LawClass/LawSingle.aspx?Pcode=I0050021&FLNO=2)的「個人資料」。然而，報案人是否會在報案時於文字敘述欄位中刻意透露自身或他人個資、或足以用間接方式識別的個人資料，以及這樣的情形是否存在，有待檢視實際現行 1999 資料庫，再行討論。

遠程計劃主要提出架設 Open311 伺服器來接收新陳情案，設計上可以透過 Service Definition \[5\] 獲得報案人的個人資料以填入現行 1999 資料庫，但是資訊公開的部分，並沒有提供比近程計劃更多的資料，因此也沒有泄露報案人個資的疑慮。

\[5\] 由於報案時，各城市需要向報案人搜集的資訊不盡相同，因此 Open311 GeoReport v2 設計了 [Service Definition 資源](http://wiki.open311.org/GeoReport_v2/#get-service-definition)，政府可以枚舉某項服務種類（Service）需要報案者提供的資訊，讓開發者在設計報案表單的時候參考。然而，Open331 GeoReport v2 的 [Service Request 界面](http://wiki.open311.org/GeoReport_v2/#get-service-request)並沒有公佈報案者填寫的這些資訊的設計。


3、隱私權問題

探討開放一項資料是否侵犯到個人隱私權，會比「探討開放這些資料欄位是否觸犯個資法」稍微深入一些，因為只要資料沒有辦法判別出任何個體，就不會有透露個資與觸犯個資法的問題，但是將大眾填寫的資料公開，觀感上還是會引起一些隱私疑慮。因此，建議在實行計劃時，尋求專家進行隱私風險評鑑（Privacy Impact Assessment），並且制定 1999 服務的**隱私權條款**，在提供 1999 服務之前讓大眾使用者知道其所提供的文字資料將會開放出來，較為妥適。


## 伍、結語


研考會所頒布的《[新北市政府行動應用軟體(App)發展及管理作業原則](http://www.rde.ntpc.gov.tw/web66/_file/1397/upload/law/App.pdf)》發展原則第一款：「各機關發展 App 宜優先評估透過本府公開資料平台(Open Data)所提供之資料，鼓勵民間運用加值開發，以擴大民眾參與並降低本府開發成本。」這條原則的核心並不只是在節省成本而已，而是看到了開放資料的背後，提升公眾參與的外部效益，以及政府用資料 empower 一般群眾後，所能激發的無限潛能。

當地方政府將資料以合適的、開放的格式釋出給大眾，熱心的公民與渴求群眾關注的新創業者就能夠投入心力替政府找出有價值的資料用法，並且開發應用程式來服務一般大眾。這讓地方政府可以專心投入政府所擅長，而且也只有政府有職權、有能力做的事情——匯整各方資訊、提供官方且正確的資料，放手讓各方的開發好手，用同一份完整的官方資料去相互競爭，做出最讓人喜愛的 App。這會是政府、新創企業/NGO/開發者社群 與大眾使用者三贏的局面。

除了報告中提出的社群網友作品之外，開放資料社群每年舉辦[台灣資料科學愛好者年會](http://datasci.tw)，參與者橫跨官產學，也吸引包括新聞與資訊技術背景的民間參與者共襄盛舉，分享一年來的成果；每兩個月也有 [g0v 零時政府黑客松](https://g0v.tw/zh-TW/actinfo.html)，開發者們可以在這樣的聚會發表自己想做的開放原始碼專案企劃，邀請有興趣的人一起把專案做出來。政府機關與社群還可以有更緊密的合作：台北市政府資訊局最近半年邀請 OpenData / Taiwan 臉書社群來市政府開會，共同商研開放資料與災害防治的可能性，目前有兩次的會面，會後資訊局依照討論結果決定資料開放方向與資料內容細節，也完全開放會議紀錄\[6\]供其他縣市參考。

新北替代役資訊服務團隊希望能用下面的參與方式，與新北市政府研考會一同促成新北市 1999 資料的開放：

一、在組長認可下，役男與新北市政府資料中心工程師一起檢視現在的 1999 資料庫，區分可以開放的資料與可能有疑慮的資料。隨後，向組長報告預計開放的資料集，並且向上級請求資源，針對有疑慮的資料集進行隱私風險評鑑 (Privacy Impact Assessment)。研考會可能需要研擬 1999 服務的隱私權條款。

二、實際執行近程計劃：役男與資料中心工程師分工整理資料與撰寫開發自動化發佈程式腳本。腳本開發完成後，由資料中心部署程式與將資料開放。

三、實際執行遠程計劃：參考[現有 Open311 伺服器實作](http://wiki.open311.org/Software/)，役男與資料中心工程師討論適合政府機關維護的 Open311 伺服器程式架構，並且協同架設 Open311 伺服器。

四、新聞露出：新北市開放 1999 服務，符合國際 Open311 規範，歡迎各界利用。

上述執行方案的時程，需要實際檢視現有 1999 資料庫的資料內容，並且與新北市政府資料中心的工程師一起討論之後，才有辦法規劃出來。即便如此，替代役資訊小組認為，資訊小組與政府溝通開放 1999 的過程也相當值得其他縣市參考，因此未來在上面的執行過程中，也希望能夠將會議筆記裡不包含機密（如資料庫技術細節等資訊安全相關敏感資訊）的溝通磨合過程，在 Hackpad 上公開上網供各界閱覽與留言，向 OpenData / Taiwan 社群的做法看齊。

以上是新北市替代役資訊小組對新北市 1999 資料開放的計劃提案。這是新北市政府資料開放、與國際標準接軌的契機，希望役男們有機會能躬逢其盛。


\[6\] 北市府與開放資料社群的會議紀錄： 第一次開會 [https://odtw.hackpad.com/x-u1MNznTEgSV](https://odtw.hackpad.com/x-u1MNznTEgSV) ，第二次開會 [https://hackpad.com/20151006--4ogA1YY1QZU](https://hackpad.com/20151006--4ogA1YY1QZU)


## 參考資料

### 國外

芝加哥 Open311 Server：[所有服務](http://311api.cityofchicago.org/open311/v2/services.json)、[路燈壞掉的 service requset](http://311api.cityofchicago.org/open311/v2/requests.json?service_code=4ffa9cad6018277d4000007b)

[Open311 GeoReport v2](http://wiki.open311.org/GeoReport_v2/)

### 國內

台北市資訊局 與社群的[災害應變會議記錄](https://hackpad.com/20151006--4ogA1YY1QZU) （1999），會後[小彭](https://www.facebook.com/groups/odtwn/permalink/1338029269544821/)放上 1999 資料

政府 [開放資料授權條款 v1](http://data.gov.tw/license)
[臺北 1999 派工開放資料](http://data.taipei/opendata/datalist/datasetMeta?oid=b796f87a-0ed8-4e57-89f6-225a4941b1ed) 每月更新
[台南 open 1999 伺服器](http://1999.tainan.gov.tw/OpenCase.aspx)  [範例輸入輸出](http://1999.tainan.gov.tw/OpenExplain.aspx)  [新聞露出](http://housebaba.tw/archives/4391)

### 市府內

[路平報馬仔](http://rdm.ntpc.gov.tw/Road/SearchRoad.aspx)

### 民間

[台南1999(beta) app](https://play.google.com/store/apps/details?id=tn.opendata.tainan311&hl=zh_TW) [程式原始碼](https://github.com/newmanchen/tainan-1999) 「他是民間的噢，民間的」「官方的目前還沒有耶」

群眾關注例子：民間 youbike [http://www.inside.com.tw/2013/08/16/ubike-app-case-study](http://www.inside.com.tw/2013/08/16/ubike-app-case-study)
東森財金專訪 SMD Labs [https://www.youtube.com/watch?v=lXIrQWwK_QM](https://www.youtube.com/watch?v=lXIrQWwK_QM)



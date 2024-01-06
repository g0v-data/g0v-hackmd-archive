---
title: "台灣輻射地圖"
tags: hackpad
---

# 台灣輻射地圖

> [點此觀看原始內容](https://g0v.hackpad.tw/91ZImrFjGvx)

使用請見：[空白模版使用方式](https://g0v.hackpad.com/QUrgIRJEpv4#%E7%A9%BA%E7%99%BD%E6%A8%A1%E7%89%88%E4%BD%BF%E7%94%A8%E6%96%B9%E5%BC%8F)

本次提案PPT
[https://docs.google.com/presentation/d/1dEk1ZdYDNJzLGEceoCJK4XmVl56wOHmjmkFLf7L_SzU/edit?usp=sharing](https://docs.google.com/presentation/d/1dEk1ZdYDNJzLGEceoCJK4XmVl56wOHmjmkFLf7L_SzU/edit?usp=sharing)

## 專案介紹 | Project Readme / Meta

民間版輻射偵測地圖
[#核能](https://g0v.hackpad.tw/ep/search/?q=%23%E6%A0%B8%E8%83%BD&via=91ZImrFjGvx)  [#核電廠](https://g0v.hackpad.tw/ep/search/?q=%23%E6%A0%B8%E9%9B%BB%E5%BB%A0&via=91ZImrFjGvx)  [#輻射](https://g0v.hackpad.tw/ep/search/?q=%23%E8%BC%BB%E5%B0%84&via=91ZImrFjGvx)
我們想製作一個輻射地圖APP，讓每個關心台灣輻射污染現況的人，可以簡簡單單像量測溫度一樣，自行量測周遭的輻射值，並把檢測結果拍照/打卡/上傳到網路共，同來繪製一個台灣（未來也可發展為"世界"）輻射地圖網站。
## 來龍去脈（想解決什麼問題）

目前台灣的兩個輻射地圖，比較專業，希望能開發一個一般民眾可以簡單使用的app地圖網站，透過拍攝核輻射探測器的照片，就能直接打卡上傳，讓臉書友人知道測試者所測得的數值、地點與劑量在台灣地圖上所代表的顏色，若常態超標，並將予以告知。
> 原先這邊討論太長，干擾專案本文閱讀，故移至最下方。
> [name=nchild]


#### 靈感來源

近年來台電利用燒卻法處理低階核廢料，把核輻射物質直接燒入空氣中，以至於北台灣很多地方的輻射背景值經常高於人體可負荷之法定值。根據反核部隊許多成員將近一年來的測試，發現北台灣輻射背景值，很多時間竟遠遠超過日本東京，我們懷疑這是造成台北近年來肝癌、肺癌、肺腺癌甚至女性乳癌罹患率遠高於其他地區的主因之一。
> 怎麼想到要做這個東西
> [name=ET B]

> 空氣中輻射的來源很多, 例如台中火力發電廠是世界最大的燃煤發電廠, 燃煤也會產生輻射, 所以造成週邊輻射量測結果較高. 
> [name=Richard L]

> 再來, 量測的方式也是最大的問題, 如果只是手持式便宜的輻射量測器, 說不定只是自己嚇自己. 
> [name=Richard L]

> 更何況, 是不是應該先做出輻射吸收量對這些病症的影響, 再來做流行病學研究. 
> [name=Richard L]

> 這幾年蘭嶼的流行病學調查, 並沒有特別高的癌症發生. 
> [name=Richard L]


蘭嶼人罹癌的情況很嚴重，你可以看看這篇新聞。但蘭嶼沒有把核廢料拿來燒，反而因為台灣的低階核廢料不能運去蘭嶼，現在都用燒的，相信很多輻射現在早已進到你我的體內了
[http://www.appledaily.com.tw/appledaily/article/headline/20120106/33940854/](http://www.appledaily.com.tw/appledaily/article/headline/20120106/33940854/)
> 拿一個人就說蘭嶼人罹癌很嚴重, 蘭嶼才多少人? 一個人就可以讓平均值偏差極高. 
> [name=Richard L]

> 拿蘭嶼也不準
> [name=Richard L]

> 看看輻射屋的流行病學吧
> [name=Richard L]

> [http://www.aec.gov.tw/webpage/info/files/index\_11\_6-11.pdf](http://www.aec.gov.tw/webpage/info/files/index_11_6-11.pdf)
> [name=Richard L]


#### 主旨

希望能發起台灣輻射地圖的推廣，透過全民量測的推廣，收集大量測試數值來呈現台灣核輻射污染的現況，使社會大眾對週邊無所不在的核輻射污染有所警覺。
> 想用什麼方式達成目標
> [name=ET B]

> 垃圾進垃圾出, 這是學 CS 的都知道的事情, 日本專家來台都會搞錯的量測. 
> [name=Richard L]

> 產生出來的東西恐怕只是變成手持輻射偵測器廠商賺錢的工具
> [name=Richard L]

> [https://zh-tw.facebook.com/NuclearMythbusters/posts/157828324404755](https://zh-tw.facebook.com/NuclearMythbusters/posts/157828324404755)
> [name=Richard L]


#### 牽涉領域

環保 / 核能 / 醫療 / 保健
> e.g.教育 / 環保 / 醫療 / 社福 / 核電 / 都市計畫 / 勞工權益 / 食品安全 ...（會變成專案 tag）
> [name=ET B]


#### 現有類似專案

- 行政院原子能委員會輻射偵測中心環境輻射偵測 [http://www.trmc.aec.gov.tw/](http://www.trmc.aec.gov.tw/)
- 主婦聯盟版台灣輻射地圖政府公告數值與實際測試數值 [http://www.knownuke.tw/map/](http://www.knownuke.tw/map/)
- **國際輻射地圖網站** [http://blog.safecast.org/maps/](http://blog.safecast.org/maps/)
> 現成的是否可以直接使用？或者有什麼不足之處？國外是否有類似的專案可參考？
> [name=Chia-liang K]

> 主婦聯盟版地圖基於 Ushahidi，能否直接套用它的行動版 ([Android](https://play.google.com/store/apps/details?id=com.ushahidi.android.app) 、[iOS](http://itunes.apple.com/app/ushahidi-ios/id410609585)) 作為上傳 App?
> [name=Audrey T]

> 我個人的想法是 responsive web app 就好，有人要改成 mobile app 可用這邊的資源
> [name=nchild]

- 日本官方的即時偵測資料 [http://radioactivity.nsr.go.jp/maps/ja/](http://radioactivity.nsr.go.jp/maps/ja/)
- 香港官方的即時偵測資料 [http://www.weather.gov.hk/radiation/rmn\_hourly\_c.htm](http://www.weather.gov.hk/radiation/rmn_hourly_c.htm)
- 輻射屋（?） http://
- [Safecast](http://blog.safecast.org)
- Air Quality Egg [http://airqualityegg.com](http://airqualityegg.com)

#### 相關組織單位

> 以下參照第一次台灣輻射地圖開發製作研討會名單
> [name=nchild]

劉黎兒（日本資訊）、綠色消費者基金會方儉、爸爸反核陣線李卓翰、蠻野心足蔡雅瀅、主婦聯盟代表美音（邀請中）、立法委員田秋堇、反核部隊Ada（澳洲及國際資訊）、Jimi、吳春蓉（貢寮代表）、台灣環境輻射地圖發起人林瑞珠、環保聯盟李秀容
> e.g.公督盟/綠盟/司改會/苦勞網/泛科學...（會變成專案 tag）
> [name=ET B]

> 呃, 有沒有更專業一點的單位, 例如傳說中賺很大的 SGS 
> [name=Richard L]


相關專案
> 可能能用的服務： [http://www.ushahidi.com](http://www.ushahidi.com)
> [name=Jimmy C]



授權方式
> 程式碼部分（如 MIT/BSD）
> [name=ET B]

> 文件部分（如 CC-BY）
> [name=ET B]


#### 使用資料

透過全民量測的推廣，收集測試數值。
> 據反核部隊 Jimi：台灣已有數百位反核成員擁有核輻射探測器。
> [name=nchild]


#### 專案目前狀態

構想
> 構想 / 規劃 / 雛形 / 實作
> [name=ET B]



## 目標與功能（要如何解決）


#### 預定使用者

社會大眾

#### 預定功能


- 它的功能是當測試者完成測試時→可以利用手機拍下偵測器的畫面→現場透過網路上傳→結合現有的地圖網站→將資料上傳到資料庫→在地圖上顯示並紀錄該筆測試的位址、數值以及區間顏色，並在資料庫內留存上傳畫面、上傳帳號、上傳者聯絡資訊等資料可供備查。
- APP同時提供中、英、日文，方便其他核電國家民眾下載使用，共同繪製世界輻射地圖。
- 我們希望能另外增加一個查詢空氣污染狀況的功能，以提昇APP下載率。

#### 使用方式



## 實做細節（非技術背景可跳填）

> [主婦聯盟版地圖](http://www.knownuke.tw/map/) 基於 Ushahidi，能否利用其行動版 ([Android](https://play.google.com/store/apps/details?id=com.ushahidi.android.app) 、[iOS](http://itunes.apple.com/app/ushahidi-ios/id410609585)) 作為上傳 App?
> [name=Audrey T]

目前還不行，他們家app還沒有開發
> Ushahidi app 是通用的，只要主婦聯盟的那個網站有開啟對應功能，上述兩個 app 就可以通報資料。我自己架設的測試平台是有遇到圖片無法透過手機上傳的問題，但文字內容的通報並沒有遇到狀況(Android app)
> [name=Finjon K]


使用技術
- 測試 [Ushahidi](http://www.ushahidi.com) crowdmap
- 使用的 vagrant box 版本 / 網址：

協作工具
- github repo：
- hackfoldr 工作資料夾網址：
- google drive 共用資料夾網址：[https://drive.google.com/](https://drive.google.com/#folders/0BxQ-5_SEyZgjOEFBeW5nUFhmRkE)[#folders](https://g0v.hackpad.tw/ep/search/?q=%23folders&via=91ZImrFjGvx)[/0BxQ-5_SEyZgjOEFBeW5nUFhmRkE](https://drive.google.com/#folders/0BxQ-5_SEyZgjOEFBeW5nUFhmRkE)
- google groups 討論群組：
- irc channel：

產出檔案格式

進度與 to-do
> 僅供參考
> [name=ET B]

- [ ] product planning（recommanded procedure from justin lee / 李易修）
    - [ ] strategy
    - [ ] scope
    - [ ] structure
    - [ ] wireframe
    - [ ] visual
- [ ] web front-end
- [ ] web back-end
- [ ] ui / visual design

### Ushahidi相關


```



```
## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）

目前規格及process規劃文件請見連結：[https://drive.google.com/](https://drive.google.com/#folders/0BxQ-5_SEyZgjOEFBeW5nUFhmRkE)[#folders](https://g0v.hackpad.tw/ep/search/?q=%23folders&via=91ZImrFjGvx)[/0BxQ-5_SEyZgjOEFBeW5nUFhmRkE](https://drive.google.com/#folders/0BxQ-5_SEyZgjOEFBeW5nUFhmRkE)
Demo網站：
[http://u273.stark.tw/](http://u273.stark.tw/)


## 開發者


技術指導

分工與成員
iOS App: Kent, Charles
Ushahidi: Stark

- [ ] NeedPM: 需要坑主（專案經理）Jimi 0930-800-316
- [ ] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
- [ ] NeedsDesigner: 需要介面設計
- [ ] NeedsData: 需要資料（擷取、清理）
- [ ] NeedsTech: 需要技術支援（程式、架站 etc)
- [ ] NeedsProcess: 需要幫忙設計作業流程
- [ ] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡

## 會議記錄

會議時間：1/17 （五）下午16:00~19:00
會議地點：立法院中興會館

一、黎兒發言：
1.福島核災之後，在最受日本民間最受信賴的早川輻射地圖顯示（群馬大學早川由紀夫製作的輻射污染地圖），便是民間上傳測到的輻射劑量製作的，成為最權威 的輻射地圖，民眾靠這圖判斷自己採購食物、旅居等參考。

 ２.日本災後開發的家庭用輻射劑量器是，言明是２０％，而且是偏低２０％，不會差那麼多倍，同樣的機器在東京絕對測不到那麼高。以100公分高度為測量基 準，因為100分是對人體（大人或小孩）影響最多１個高度。如果測水溝、樹叢、沙堆等會更高。 我家在東京西邊，東京核災前約0.03微西弗，目前約為0.05微西弗，台北的家高岀很多，几乎是２倍以上。目前在立院這裡測得的輻射背景值為0.18微 西弗/小時。 台灣各地輻射劑量偏高是事實，即使其他組織（宜蘭人文、媽盟等）或日本專家學者等用再精密的輻射偵測器也測不到原能會公佈的低劑量。
> 問一下是什麼學者? 
> [name=Richard L]

> 使用儀器為何? 規格為何? 
> [name=Richard L]



３.跟世界最大擁核組織IAEA（國際原子能總署）關係密切的ICRP（國際輻射防護委員會）根據NAS研究報 告，在2007年提出勸告，承認輻射被曝沒有安全下限，但核電國家因使用核電而不得不承擔1年1毫西弗的容許劑量，這1毫西弗也是會有1萬分之1的額外致 癌、死亡，就是台灣兩千萬人因用核電而每年會有兩千人額外致癌，而且是年輕人、小孩致癌，但核電國家認為即使讓1萬分之1的人口致癌也要用核電。
> 一般資料, 若核電未出事, 造成的背景輻射極低, 請問資料來源. 
> [name=Richard L]

> [http://zh.wikipedia.org/wiki/背景輻射](http://zh.wikipedia.org/wiki/背景輻射)
> [name=Richard L]

> 自然背景輻射有兩個主要的來源：[宇宙射線](http://zh.wikipedia.org/wiki/%E5%AE%87%E5%AE%99%E5%B0%84%E7%B7%9A)和源自地球的，全球平均的背景[劑量](http://zh.wikipedia.org/wiki/%E5%90%B8%E6%94%B6%E5%8A%91%E9%87%8F)為每年每人2.4[毫西弗 (mSv)](http://zh.wikipedia.org/wiki/%E8%A5%BF%E5%BC%97)[\[1\]](http://zh.wikipedia.org/wiki/%E8%83%8C%E6%99%AF%E8%BC%BB%E5%B0%84#cite_note-1)，台灣年平均天然輻射約為1-2毫西弗。[\[2\]](http://zh.wikipedia.org/wiki/%E8%83%8C%E6%99%AF%E8%BC%BB%E5%B0%84#cite_note-2)這些曝露幾乎全都來自宇宙射線和環境中的天然放射性核素。這個數值遠大於人造的輻射曝露，在2000年的一年當中，累積歷年的核武試驗、核電廠意外和核能工業操作的總合，為年平均值5μSv[\[3\]](http://zh.wikipedia.org/wiki/%E8%83%8C%E6%99%AF%E8%BC%BB%E5%B0%84#cite_note-rrjhjx-3)；並且也大於來自醫療接觸，由0.04至1mSv的年平均值。老舊的燃煤發電廠未能有效攔截的粉塵才是人造背景輻射的最大來源。
> [name=Richard L]

> ICRP的規定和是不是核電國家無關，ICRP的規定是包括所有輻射應用的輻射劑量，包括醫療和工業的輻射應用，而核電廠造成的劑量也根本只有１毫西弗／每年的千分之一不到。
> [name=黃增德]


４.台灣四處經常測得0.15以上，政大0.16，成大0.17，台大甚至測得高達0.2，高雄地區也經常測得0.2微西弗/小時的高數值。而原能會地圖 顯示卻只有0.04～0.06微西弗/小時。我跟我先生的感想是最近每次返台，測到的輻射劑量１次比１次高。 台灣按理是背景值是0.04到0.05微西弗／小時，但現在哪裏都不可能測到那麼低的數值／
> 同上
> [name=Richard L]



５.關於輻射劑量多少才超標？ 根據IAEA以及ＩＣＲＰ勸告，台灣這種擁有核電國家，要忍受的總輻射劑量基準也是１毫西弗／年，亦即0.11微西弗／小時， 但這0.11微西弗／小時，是內曝加上外曝，亦即５分之４的內曝（體內被曝，吃的、喝的、吸的，影響比體外被曝嚴重）約0.08以及5分之１的外曝 0.02（空間劑量） 因此自然環境劑量＋（５分之一）0.02微西弗﹦0.06或0.07微西弗小時），亦即超過0.07微西弗／小時就是超標。 我們在台北等各地都測不到0.07微西弗以下的地方，像內湖測好幾次都是0.17微西弗。 盼望能有一個簡單又有效率、公正的網站讓大家能回報測到的輻射值，製作一份台灣的輻射污染地圖。 即使忍受要忍受的基準也是１毫西弗／年，也是台灣２千萬人每年有１千人是因為擁有核電而會致癌死亡，這還是有守住１毫西弗基準，但事實上台灣現在是法定１ 毫西弗的好幾倍。
> 請問這是扣除背景輻射值還是沒有, 
> [name=Richard L]

> 來源請求. 
> [name=Richard L]



６.台灣會測到這麼高的數值，可能的原因有兩點： 第一是核電廠老舊，核電廠內有長達幾萬公尺的配管，都可能會因為老舊外漏，日本每12個月歲修45天－60天，台灣每18個月才歲修24天，老朽核電廠為 修非常花錢，台電根本不肯花錢維修，像連瞄定螺栓壞了都不換； 第二是減容中心燃燒低階核廢料，台電自創號稱全球最厲害的減容技術，將每100桶燒成一桶。在金山野柳那邊的減容中心燒核廢料，污染就隨著高煙囪飄進台北。

二、雅惠分享主婦聯盟公民地圖的資料（請見簡報）

1.網站連結：
[http://www.knownuke.tw/map/index.php/main](http://www.knownuke.tw/map/index.php/main)

2.若大家自行測量不使用網站上傳，也可以將自行拍攝的照片上傳到臉書
[https://www.facebook.com/tw0usv](https://www.facebook.com/tw0usv)

3.主婦聯盟目前遇到的困難：
上傳照片需<1.5 MB
雖有建構APP概念但苦無技術人員
部分選項應修改為下拉式選單(EX.儀器種類)
總儲存空間較小
監測網未跟國際接軌

4.另外主婦聯盟美音推薦這個網站，可以直接使用他們的app+測量器，直接接了設備就可以測量，目前已有現成軟體（for iPhone），只是沒有中文化。這個可以請g0v看看是否可以直接拿來修改使用？
[https://sites.google.com/site/geigerbot/](https://sites.google.com/site/geigerbot/)

補充：請教了黎兒這個測量器跟app在日本的風評，似乎使用的人不算多，精準度不高。

三、瑞珠分享台灣環境輻射地圖的資料（請見簡報）
瑞珠的輻射地圖測量方式有系統而完整，未來仍會以專業訓練後的工作小組來檢測為主。
台灣環境輻射地網址：[http://gammausv.blogspot.tw/](http://gammausv.blogspot.tw/)

四、Ada分享推薦的國外輻射地圖

1.這次回來台灣測得數據都遠比澳洲高，澳洲很少0.1微西弗以上的地方，只有一次在澳洲南部測到。因為那個地方是核能實驗室，每年會有一次歲修，會有輻射外洩。桃園火車站前測到0.25，連總統府前都測到0.15。

selfcast網站連結：
[blog.safecast.org](http://blog.safecast.org/)
[http://blog.safecast.org/maps/](http://blog.safecast.org/maps/)

hakatte民眾隨手拍照片上傳
[http://hakatte.jp](http://hakatte.jp)

五、g0v 英凱、孝先

1.  介紹 g0v 的角色
    1.  g0v 是關注資料開放的社群，特別是政府資料開放，但不會對特定議題有立場
        1.  目前 IRC 討論狀況，無論擁核、反核立場都很關注資料正確性
    2.  需要反核部隊或其他人擔任坑主（PM），進來 g0v 找尋其它人協助完成這個計劃
        1.  輻射地圖和其他專案一樣需要和其他專案競爭資源
    3.  2月份大會時可以一起來參加，或許現場就能解決
> 下次大型活動時間確定了：2/22（六） 第柒次【[自由時代黑客松](http://g0v-tw.kktix.cc/)】，活動前兩週會開始報名～
> [name=nchild]

2.  提出關於現有輻射地圖資料正確性的問題
    1.  \[瑞珠\] 說明（略）
        1.  \[英凱\] 瑞珠的研究數值很有價值，會想下載利用
    2.  \[主婦\] 於稍後第二次發言時對此點加以回應，針對不同裝置正確性比較，並提出正確偵測程序的複雜性
> 所以原先想以此輻射地圖做正確偵測可能性低，必須賦予其他意義
> [name=nchild]

3.  目前想到的作法可以用這樣的視覺方式呈現
    [http://g0v.github.io/twgeojson/air.html](http://g0v.github.io/twgeojson/air.html)
    [https://www.facebook.com/photo.php?fbid=639508362757120](https://www.facebook.com/photo.php?fbid=639508362757120)
4.  若可以使用以下的軟體來修改的話，製作會很快
    [http://www.ushahidi.com/](http://www.ushahidi.com/)

六、田秋堇委員發言：
1.  希望方便民眾使用的輻射地圖app可以在三月遊行前出來。
2.  308遊行之前是媒體關注重點，希望反核團體能就好好發揮運用。

七、結論：
最後跟黎兒商討後，歸納以下結論。
1.  目前兩大輻射地圖各有不同的特色，效度較高。若要開放民眾使用，應另外開發一個中文化的輻射地圖以及app，方便一般民眾使用，最好能結合臉書打卡機制+google map
2.  這個地圖最大的目的是讓民眾可以有參與感，提昇民眾對環境輻射的關注，並且可以自行測量真實的數據。至於精準度，因為個別資料的測量方式無法掌控，可能沒有辦法要求保證精準。
3.  g0v的部份，Jimi會進來平台系統，邀請g0v成員幫忙，再請孝先協助。另外，我們未來需要一個網址空間，可以作為放置輻射地圖使用。
4.  媽盟目前手邊還有一些輻射探測器，數量待Kevin盤點，每個希望參與輻射地圖製作的團體，有需要的話可以提出輻射探測器數量需求，媽盟有的就先從媽盟取得，不夠的話我們會設法從國外引進，再請團體統計數量後跟我說。至於費用，請Kevin再報價給大家，後續不夠的我們再一起採購。
5.  黎兒提到有人願意樂捐測量儀器，到時候我們再去問問看是否有機會取得贊助。

> 手持核輻射探測器誤差極大, 
> [name=Richard L]

> Atomtex-AT6130               ；0.1 µSv/h - 10 mSv/h
> [name=Richard L]

> Atomtex AT1125A             ；30 nSv/h - 100 mSv/h           
> [name=Richard L]

> 最低量測範圍至少要0.1 µSv/h，0.01 µSv/h更好。
> [name=Richard L]

> 但要了解的是，台灣的天然背景輻射平均值為0.1~0.2μSv/h，所以在沒有輻射汙染的環境之下，是否能監測出正確值還需要實際拿儀器測量。
> [name=Richard L]

> Ref. 
> [name=Richard L]

> [http://www.mobile01.com/topicdetail.php?f=330&t=2083873&p=1](http://www.mobile01.com/topicdetail.php?f=330&t=2083873&p=1)
> [name=Richard L]

> 目前我們採用的儀器是日本銷售了數十萬支的機型，誤差值是15～20％，但我們實際上測得的數值是超過政府公告數值200％～500。舉例來說，這儀器就好比是電子血壓計，你可以去醫院借用水銀血壓計，它的誤差可能會比電子血壓計精準個5％，但你當然也可以買一個簡易的電子血壓計自己來量測血壓。
> [name=Jimi C]

> 這是你引用圖中的其中一台
> [name=Richard L]

> [http://gs.flir.com/detection/radiation/handhelds/identifinder2](http://gs.flir.com/detection/radiation/handhelds/identifinder2)
> [name=Richard L]

> 誤差很小
> [name=Richard L]

> NT$2000 左右的就大很多了
> [name=Richard L]

> [http://www.ebay.com/itm/NEW-Inspector-Alert-V2-Handheld-Radiation-Monitor-Geiger-Counter-/181328969264?pt=BI\_Security\_Fire_Protection&hash=item2a380c7e30](http://www.ebay.com/itm/NEW-Inspector-Alert-V2-Handheld-Radiation-Monitor-Geiger-Counter-/181328969264?pt=BI_Security_Fire_Protection&hash=item2a380c7e30)
> [name=Richard L]

> 血壓計大不了就是在10% 偏差, 你也不會在乎. 
> [name=Richard L]

> 想必你手上儀器就是 2000 元等級的. 我實在想不出來, 能夠測 usv/h 等級的機器 2000 元可以買得到. 
> [name=Richard L]

> 如果各位可以解釋一下原理, 我想我會心服口服啦 ^_^
> [name=Richard L]



> 日本目前有數十萬家庭這麼做，累積了上千萬筆自主測試的資料。很多家庭因為這樣，搬離了輻射高污染地區。
> [name=Jimi C]

> 這和資料的正確性沒有關係, 全日本都用, 結果你量測的方式是錯的, 那還是錯的. 
> [name=Richard L]


> 輻射測試計我們反核團體陸續已經引進了幾百支，目前也已經準備要再辦理進口，一支費用約莫只要一千多元，未來只要app出來，方便大家使用，就能累積數據，讓民眾自己瞭解所身處環境的輻射污染嚴重性。
> [name=Jimi C]

> 上面講的問題就在於, 你要量測的東西單位太小. 機器誤差值太大. 
> [name=Richard L]

> 而且 1000 元就要量到 uSv/h , 不知道你能提供更多的資訊嗎?
> [name=Richard L]

> 新聞報道上寫的 [http://www.ettoday.net/news/20130309/172701.htm](http://www.ettoday.net/news/20130309/172701.htm)
> [name=Richard L]

> "他邊走邊拿出「核輻射計量器」當場測量，測得數值0.1微西弗"
> [name=Richard L]

> "據行政院原子能委員會環境輻射即時監測資訊資料顯示，稍早前台北地區數值為0.056微西弗／時。一般來說，測量值在0.2微西弗／時以下屬一般背景輻射範圍，超過20微西弗／時以上，才會執行輻射緊急偵測"
> [name=Richard L]

> 何來 200% ~ 500% . 如果是的話, 原能會應該早就要出動了吧. 
> [name=Richard L]




> [http://www.mobile01.com/topicdetail.php?f=330&t=2083873&p=1](http://www.mobile01.com/topicdetail.php?f=330&t=2083873&p=1)
> [name=Richard L]

> 在科技業而且做過實驗就知道, 像這樣精密的儀器還需要校正, 沒有校正過的儀器量測出來是有誤差的. 
> [name=Richard L]

> 不知道手持輻射偵測器怎麼能解決這個問題.
> [name=Richard L]

> 這問題無法解決，以民間力量來說，目前另外兩個地圖量測都要經過嚴謹程序，所以無法擴張，這個普及地圖要賦予正確性以外的其他意義才行，詳見最下面會議記錄。
> [name=nchild]

> 如果不是取用正確資料, 能賦予什麼意義? 嚇唬一般民眾嗎? 
> [name=Richard L]

> 記得福島事件時, 就有人做 Android App 直接取用原能會的資料, 結果看一看也沒有什麼大變化 (不需要逃命)
> [name=Richard L]

> 所以我不知道拍攝打卡輻射上傳這個意義在那邊 (P.S 印像手機輻射會影響
> [name=Richard L]

> 就拿這些團體提供的 Safecast data 來說, 他們有提供 Sensor 
> [name=Richard L]

> [http://blog.safecast.org/faq/data/](http://blog.safecast.org/faq/data/)
> [name=Richard L]

> 如果真的要做地圖, 加入 Safecast 是不是比較好的選擇呢? (還是這些人自己都沒有看過 FAQ 就硬幹起來了?)
> [name=Richard L]

> 你可以讀讀這篇文章，我們有參考Safecast，他使用移動式的測試儀器，不方便讓民眾開放使用，實際上在日本的評價不高，目前台灣研究輻射地圖的兩個單位，是比較過很多日本的網站後，採取比較精實的作法所製成。
> [name=Jimi C]

> 不見得一定要絕對正確才會有需要製作，如果只是想到嚇唬民眾，那就太沒想像力了，舉例來說，公民培力就可以是一個好理由，以公民的力量去檢視政府資料的正確性，當差異性極大的時候，理當是由握有資源，提出政策的政府來提出說明。
> [name=nchild]

> 請問若同一個地點由不同人量測出來的數值有顯著差異，是否有適當的機制可以去檢視其有效性？上傳的照片是不是應該對其規格（測量方式、儀器校正證明）有所審查？
> [name=Seiken]

> 上次有個日本人在蘭嶼量測出一個極高的值, 發表了"抓到了" 結果被政府打槍, 該日本人也承認是自己的錯
> [name=Richard L]

> 我是有看反核團體給出的座標和數據去查大概是什麼地方輻射值很高. 
> [name=Richard L]

> 很有趣的是,不是在儲存核廢的週圍, 而是還要再往外走一點 (我印像)
> [name=Richard L]

> 依常理判斷, 如果是核輻射污染, 應該是整片都有, 但是該日本人只測到單點有就發表了
> [name=Richard L]

> 最後還是要承認錯誤
> [name=Richard L]

> 參考資料：[http://pansci.tw/archives/57033](http://pansci.tw/archives/57033)
> [name=nchild]



[https://www.facebook.com/momlovestaiwan/photos/a.214032908732304.53403.213063155495946/405632062905720/?type=1&theater](https://www.facebook.com/momlovestaiwan/photos/a.214032908732304.53403.213063155495946/405632062905720/?type=1&theater)
> [http://zh.wikipedia.org/wiki/背景輻射](http://zh.wikipedia.org/wiki/背景輻射)
> [name=Richard L]

> "自然背景輻射有兩個主要的來源：[宇宙射線](http://zh.wikipedia.org/wiki/%E5%AE%87%E5%AE%99%E5%B0%84%E7%B7%9A)和源自地球的，全球平均的背景[劑量](http://zh.wikipedia.org/wiki/%E5%90%B8%E6%94%B6%E5%8A%91%E9%87%8F)為每年每人2.4[毫西弗 (mSv)](http://zh.wikipedia.org/wiki/%E8%A5%BF%E5%BC%97)[\[1\]](http://zh.wikipedia.org/wiki/%E8%83%8C%E6%99%AF%E8%BC%BB%E5%B0%84#cite_note-1)，台灣年平均天然輻射約為1-2毫西弗。[\[2\]](http://zh.wikipedia.org/wiki/%E8%83%8C%E6%99%AF%E8%BC%BB%E5%B0%84#cite_note-2)這些曝露幾乎全都來自宇宙射線和環境中的天然放射性核素。"
> [name=Richard L]

> "背景自然輻射的強度也會因地而異，有些地區明顯的高於平均值[\[4\]](http://zh.wikipedia.org/wiki/%E8%83%8C%E6%99%AF%E8%BC%BB%E5%B0%84#cite_note-4)，這些地區包括伊朗的[藍薩](http://zh.wikipedia.org/wiki/%E6%8B%89%E5%A7%86%E8%96%A9%E7%88%BE)、巴西的[瓜拉巴里](http://zh.wikipedia.org/w/index.php?title=%E7%93%9C%E6%8B%89%E5%B7%B4%E9%87%8C&action=edit&redlink=1)、和印度的[克拉拉](http://zh.wikipedia.org/w/index.php?title=%E5%85%8B%E6%8B%89%E6%8B%89&action=edit&redlink=1)[\[5\]](http://zh.wikipedia.org/wiki/%E8%83%8C%E6%99%AF%E8%BC%BB%E5%B0%84#cite_note-5)、澳洲北部的[夫林德嶺](http://zh.wikipedia.org/w/index.php?title=%E5%A4%AB%E6%9E%97%E5%BE%B7%E5%B6%BA&action=edit&redlink=1)[\[6\]](http://zh.wikipedia.org/wiki/%E8%83%8C%E6%99%AF%E8%BC%BB%E5%B0%84#cite_note-6)、和中國的[陽江](http://zh.wikipedia.org/wiki/%E9%99%BD%E6%B1%9F)[\[7\]](http://zh.wikipedia.org/wiki/%E8%83%8C%E6%99%AF%E8%BC%BB%E5%B0%84#cite_note-7)。在藍薩曾經紀錄到的年峰值劑量是260mSv[\[8\]](http://zh.wikipedia.org/wiki/%E8%83%8C%E6%99%AF%E8%BC%BB%E5%B0%84#cite_note-8)。"
> [name=Richard L]


> 除了背景輻射值不同外, 那 0.3usV/h 的數值是怎麼出來的. 
> [name=Richard L]

> RAW DATA 為何, 機型為何? 拿了這麼多台, 1950 個測試至少有個 10000 組數據, 各機型的數據為何? 
> [name=Richard L]

> 基本上都有這些數據了, 應該直接就可以丟出來做地圖了吧. 
> [name=Richard L]


> 但是我的問題還是一樣,可以重現嗎? 
> [name=Richard L]


> 另一個問題是, 就算是  0.3usv/h 的, 以激效來說, 可能對人體還真的影響不大
> [name=Richard L]

> 請問你們是依據那份醫學期刊或是資料做出這樣的評論?
> [name=Richard L]


## Q/A

### Q1

[宇峰](https://www.facebook.com/chen.feng.581?fref=ufi) 別人家拿台電資料就急著當人扣帽好嗎，我只想問貴團"夥伴"到底是如何檢測的，檢測結果怎麼和原能會差別這麼多而已呀！
原能會網站有提出他們使用機型，包含
[http://www.trmc.aec.gov.tw/utf8/big5/](http://www.trmc.aec.gov.tw/utf8/big5/)

"假如要紀錄測不到很容易，就是像政府測量的方式，同一的地方偵測很多次，然後把最低與測不到的數值記錄下來就行了。"
您哪裡看到原能會有哪時說台灣沒測到輻射值？
原能會輻射監測網站全台灣一直都有輻射值存在阿

各儀器都在測不同狀況的輻射值，然後要各種儀器交叉比對下還要檢測背景輻射值，貴團後端中心如何處理測得的輻射值？貴團如何在購物平台買到如此等級的檢測儀器？
再者，輻射測量是一項精密的測量，測試方式不對都會造成不只數十倍數百倍的誤差。
再者貴團投影片第一頁及有許多疑問，貴團稱"有核國家一年容許值為0.1mSv"那是要扣除自然背景輻射值，貴團測的時候有扣除背景輻射值嗎？否則每名地球人每年接受輻射值為3.65mSv，大家都超標啦？
參考資料
[http://www.blogcdn.com/....../media/2011/03/radiationv3.jpg](http://www.blogcdn.com/....../media/2011/03/radiationv3.jpg)

還有貴團第一頁的投影片稱"0.11uSv/hr的輻射值每一萬人有一人因此得癌死亡"。參照上列參考資料，每一根香蕉輻射值為0.1uSv，，所以超過一根香蕉放在我身邊就可能罹癌了？普通人一"年"接受的背景輻射值是3.65mSv耶(1mSv=1000uSv)換算一天就有10uSv，所以只要吸收自然背景輻射就有極大機會罹癌了？那沒有罹癌的都住在真空實驗是不與自然界接觸嗎？

以上幾點還請解惑，在麻煩提出資料引述可以嗎？謝謝
### A1

安全值跟自然背景值應該是沒有關係的，這可直接參考自台電核能月刊100年10月346期57頁的翻譯：
在 1985 年 ICRP 巴黎會議聲明公眾劑量限度降至每年 1 毫西弗；ICRP 60 規定 1 年 1 毫西弗並保持在特殊情形下 5 年平均每年 1 毫西弗的彈性。
[http://info.taipower.com.tw/TaipowerWeb//upload/files/34/TNM\_346\_I6.pdf](http://info.taipower.com.tw/TaipowerWeb//upload/files/34/TNM_346_I6.pdf)
另外HSP（Health Physics Society）對ICRP的說明進行解釋：
[http://hps.org/publicinformation/ate/q8900.html](http://hps.org/publicinformation/ate/q8900.html)
透過Google翻譯的概念是說，在1mSv/y的累積下，應該可以在75歲之前不至於發生病變，當然這是保守估計，許多核能相關員工承受的劑量遠高於這個值，因此工作的週期不能過長

### Q2

[黃士修](https://www.facebook.com/hyuui?fref=ufi) 日本民眾使用很普及，但你們的測量方法是錯的，量出的數據很高但沒有意義。無知又不願意去瞭解正確的知識，被指正又不承認錯誤，你們滲透進[g0v.tw 台灣零時政府](https://www.facebook.com/g0v.tw)，是何居心？
[http://www.st-c.co.jp/air-counter/measure/measure_001.html](http://www.st-c.co.jp/air-counter/measure/measure_001.html)
### A2


### Q3

手機App偵測輻射？
### A3

技術上可行但實用性可能很低，其利用CMOS感應原件接收不可見光gamma-ray並呈現在圖片上為基礎開發，利用計算gamma-ray在影像上產生的面積來估計輻射量。
由於不同手機的硬體與軟體規格不同，且難在一般環境下維持實驗室的精確環境，因此即使可行也很難有實用性。
### Q4

### A4


## 政府相關資料

【輻射背景值監測】2014全國NGOs環境會議暨民間環境國是會議
[https://www.youtube.com/watch?v=kukRJMpQeg4](https://www.youtube.com/watch?v=kukRJMpQeg4)

校正文件：
[http://hr.taftw.org.tw/service/doc_pdf/0355.pdf](http://hr.taftw.org.tw/service/doc_pdf/0355.pdf)
[http://hr.taftw.org.tw/service/doc_pdf/0440.pdf](http://hr.taftw.org.tw/service/doc_pdf/0440.pdf)
[http://hr.taftw.org.tw/service/labinfo.aspx?code=0604](http://hr.taftw.org.tw/service/labinfo.aspx?code=0604)
查詢網址：[http://service.taftw.org.tw/tafweb/CNLA/lab-directory_1.aspx](http://service.taftw.org.tw/tafweb/CNLA/lab-directory_1.aspx)

原能會輻射偵測歷史資料
[g0v/magic mirror#6](https://github.com/g0v/magic-mirror/issues/6)
圖表：[http://ppt.cc/5Oqf](http://ppt.cc/5Oqf)

原能會ICRP第103號新建議書概要
[http://www.aec.gov.tw/webpage/control/rad/files/seminar_04-01.pdf](http://www.aec.gov.tw/webpage/control/rad/files/seminar_04-01.pdf)

台電核能月刊100年10月346期 - 游離輻射防護系統發展新趨勢－ 國際放射防護委員會（ICRP）第 103 號報告（2007建議）解讀與評析（11）
[http://info.taipower.com.tw/TaipowerWeb//upload/files/34/TNM\_346\_I6.pdf](http://info.taipower.com.tw/TaipowerWeb//upload/files/34/TNM_346_I6.pdf)

泛科學上關於輻射量測問題的文章，可能還是要想一下量測的正確性怎麼做會更好囉~
[http://pansci.tw/archives/57033](http://pansci.tw/archives/57033)


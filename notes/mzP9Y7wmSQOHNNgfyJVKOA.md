---
title: "天龍特公地－介面設計"
tags: 土地,公有地大行動,hackpad
---

# 天龍特公地－介面設計

> [點此觀看原始內容](https://g0v.hackpad.tw/6UvvtZqOfN5)


招募設計師！
- 天龍特公地：[http://taipei-pop.herokuapp.com/](http://taipei-pop.herokuapp.com/)







一些近期發想的 Idea
- 大大地顯示網站中公有土地總面積的數字：
    - 14034 筆
    - 1983434.69 平方公尺 = 198.343469 公頃 = 599988.993725 坪
- 透過「地號比對」來作資料集之間的串聯
    - 天龍特公地資料集內劃入都市更新範圍的地號總筆數與面積：劃入都更面積：3958 筆數，350166 公頃
    - 比對國產署&台北市財政局所釋出的 103 年後已租售地號，以此方式來掌握這批資料的動態；是否已都更完畢，也是類似的地號比對邏輯 → 以此達到一萬四千筆的進度追蹤
- 已上傳的圖片，目前點選後呈現頁面會炸開XD
- 呈現台北市都市更新範圍
    - 台北市都市更新地號總筆數與面積
    - 使用者透過「圖層功能」來呈現/關閉 地圖上都市更新範圍的資訊
    - ex 中正區 福和段一小段 01580000 被劃入都市更新單元中 (更新地區編碼 098228)
        - 紅色色塊是公有土地 (天龍特公地資料集)
        - 紅線範圍是都市更新範圍 (都市更新地號資料集，地號們的邊緣線?)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6eecfda6ab6a91f3201baeea3abe0fd6)


20141220
- 首圖，底色，字顏色
- 若有照片，則會顯示照片 icon

## 拍照上傳功能(20141105)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2b03452c06d62782e965046bcf3ef50e)


## 都更地號資料整合 (20140928)

將一萬四千筆地號，對照台北市都市更新地號資料庫，發現約有三分之一正在都更中！
目前已呈現於網站上，並且附上都更進度頁面
- 紅色：都更中
- 黃色：並無劃入都更


## 曝光前的修正 (20140915)

page2
- [x] 增加文字：台北市十年間  ==**(2001-2010)**==  賣掉
- [x] 增加文字：至今被都市更新==**所開發，目前還有許多已被劃入都市更新單元中**==
- [x] 增加文字：至今被 BOT==**所開發成功，目前還有許多正在促參程序中**==
page4
- [x] 增加文字：面積下拉選單部分，增加「==**坪**==」的單位
- [x] 增加文字：500坪 的選項較特別，請增加「==**1650 平方公尺**==」，方便使用者理解國有財產法第53條的內容
- [x] 版面上適當位置，增加資料特質描述文字：
###     ==本資料特性說明==

###     ==1.公有土地==

###     ==2.位在可建築分區==

###     ==3.該土地無建築物登記，例如預計開發的空軍總部舊址有建築物登記，就未顯示於本次資料==

###     ==4.土地面積單位為平方公尺==

###     ==5.國有財產法 53 條明訂 500坪 (1650平方公尺) 以上非公用公有土地禁止標售==

page5
- [x] 增加文字：每塊土地所顯示的面積單位為「==**平方公尺**==」 (若技術上太過繁瑣，則用 page3 文字說明即可)


## 介面設計課題 (20140901)

1.  改版時請綜合考量
    1.  初次造訪者的閱讀順序｜議題內容與訴求→地圖搜尋功能
    2.  重複使用地圖功能者的閱讀順序｜地圖搜尋功能→其他
    3.  訴求有兩種：短版訴求與長版訴求
    4.  「填寫你的訴求」網址：[http://goo.gl/ENiqf7](http://goo.gl/ENiqf7)  (google 表單) 待整合
    5.  「大家的訴求」填寫成果呈現網址：[http://goo.gl/WppF0p](http://goo.gl/WppF0p) 待整合
    6.  「[facebook粉絲頁](https://www.facebook.com/POPonFire)」
    7.  「案例資料庫與後台編輯」
    8.  「About me」待整合
    9.  onepage 或分頁式，請設計經手者決定～
    10.  logo 需要設計
2.  功能待優化
    1.  地址查詢
    2.  經營單位查詢
    3.  出圖速度，選擇「全部呈現」，跑較慢



## 20140831 黑客松 Lightning Talk

DEMO：[http://taipei-pop.herokuapp.com/](http://taipei-pop.herokuapp.com/)

## 又進化：20140814 文案小松，融合民眾觀點版

本次文案小松的參與者，揣摩一般民眾的處境，提出再進化調整。


## 第零頁：網站設計

- [x] **置頂導覽列**
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_46b6aee6482368647a81e9e8cf72e0b2)
> 後來覺得可以放一個「置頂導覽列」(參考：[http://spaceshare-taipei.net](http://spaceshare-taipei.net)) 輔助使用者，提供參考囉
> [name=che l]

> 頁數超展開，是需要一個 NavBar了！
> [name=Donald Z]

- [ ] 綜合已提出的 Mockup 內容與使用者模擬，請經手設計的朋友決定 one page 或是分頁式
- [ ] 【上傳案例圖片+表單編輯系統】：預計用於呈現「負面個案」、「土地好願景」、「民眾參與好案例」的圖文介紹，讓非資訊專業者專案夥伴可以編寫內容
> 我不知道怎麼稱呼這個東西XD...
> [name=che l]


## 第一頁：公有土地火大啦

計算出變賣數字，實際爭議案例圖文，強調出議題嚴重性。

### 變賣數字 (資料 from OURs)，加上可體會的面積換算單位輔助解釋

- [x] chewei：台北市內 90-99 年，十年間已賣掉 62 公頃，相當於 2.5 座大安森林公園 (或 5.3 個國父紀念館)
> [新數字](https://www.facebook.com/housingmovement2.0/photos/a.1450499925210768.1073741828.1450442028549891/1459644020963025/?type=1&theater)：自2000~2009這十年，我們政府共賣掉了 2,473 公頃的國有土地。光台北市賣了377公頃，等於14.5個大安森林公園。
> [name=che l]

- [x] chewei：台北市內已被都市更新的 3 公頃，土地面積相當於 7 處萬華區青年段 270 戶社會住宅
- [x] chewei：台北市內已被 BOT 3 公頃，土地面積相當於 1.5 個臺北小巨蛋的面積
> 負責任但不專業評論：大安森林公園的面積我有概念，但寶清段 500 戶社會住宅和青年段 270 戶社會住宅 ，就不知道多少空間了！有沒有辦法找個普羅大眾都有的基準單位。
> [name=Donald Z]


| 名稱 | 面積 |
| --- | --- |
| 大安森林公園 | 25.894 公頃 |
| 國父紀念館 | 11.55公頃 |
| 遠雄大巨蛋 | 10公頃 |
| 空軍總部舊址 | 6.6公頃 |
| 臺北小巨蛋 | 2公頃 |
| 台北車站建築 | 1.7 公頃 |
| 台北市立圖書館總館 |  |
| 松山區寶清段 500 戶社會住宅 | 0.9684公頃 |
| 萬華區青年段 270 戶社會住宅 | 0.4075公頃 |
| 228 和平公園 | 7.6 公頃 |
| 龍山寺 | 0.594 公頃 |
> 利用google map 算台北車站面積約 1.7 公頃 ([附圖](http://i.imgur.com/wllYR6j.png))。
> [name=Donald Z]

> [公園走透透 \- 二二八和平公園](http://onlinepark.taipei.gov.tw/web/index.php?option=com_content&view=article&id=27&Itemid=54&pid=31)
> [name=Donald Z]

> [維基-艋舺龍山寺](http://zh.wikipedia.org/wiki/%E8%89%8B%E8%88%BA%E9%BE%8D%E5%B1%B1%E5%AF%BA)
> [name=Donald Z]



### 整理不好&怪怪的案例，slide 照片小介面


| 左圖： | 中圖： | 右圖： |
| --- | --- | --- |
| [https://docs.google.com/file/d/0B5EFNXxRFP3wakh3OUdfTThRRWM/edit](https://docs.google.com/file/d/0B5EFNXxRFP3wakh3OUdfTThRRWM/edit) | [https://docs.google.com/file/d/0B5EFNXxRFP3wSmRZcGo1a3JWR2s/edit](https://docs.google.com/file/d/0B5EFNXxRFP3wSmRZcGo1a3JWR2s/edit) | [http://setmoney.blob.core.windows.net/newsimages/2014/06/03/89117-XXL.jpg](http://setmoney.blob.core.windows.net/newsimages/2014/06/03/89117-XXL.jpg) |
| 信義聯勤俱樂部 | 文萌樓都市更新案 | 遠雄大巨蛋 |
| 標售給新光人壽再賣給元利建設，蓋兩棟31、35層豪宅 | 近698坪公有土地被劃入更新，卻不受國有財產法500坪禁售限制 | BOT 的過程與週邊環境衝擊持續爭議中 |
POPonFire 照片集
[https://drive.google.com/?tab=mo&authuser=0#folders/0B5EFNXxRFP3wOUEzWkhoempDajg](https://drive.google.com/?tab=mo&authuser=0#folders/0B5EFNXxRFP3wOUEzWkhoempDajg)

案例參考：[http://g0v.photos/](http://g0v.photos/)

 「負面案例」隨選呈現的功能，並且有小後台，讓專案內的土地議題熟悉者，可以增加新的負面案例，未來也可以應用在其他的場合中，這部分，是否建立一個相簿，上傳圖片(圖片包含文字)至這個相簿？案例格式：一張「全貌」的圖，加上文字說明，文字應包含：名稱、開發方式、敘述
- chewei：國產署標售，台北市大安區信義聯勤俱樂部變賣與暴利的故事
- chewei＋Afey：國防部土地處分，台北市士林區岩山新村
- chewei＋Jo-ying：都市更新，文萌樓的都市更新案，台北市警察宿舍土地與臺灣銀行的土地
- chewei：都市更新，新生南路上台灣大學對面，國防部土地為主的更新案，瑠公圳開蓋段遺址，「R097702，擬訂臺北市大安區龍泉段一小段169地號等27筆土地都市更新事業計畫案」，誠美建築開發股份有限公司，[案件進度](http://www.gis.udd.taipei.gov.tw/r_progress.aspx?case_id=09706271)。圖片考慮用資料庫所呈現的公有土地(衛星地圖)＋更新單元範圍的框線
- chewei：都市更新，新生南路上台灣大學對面，該都更基地約六四八坪，台大持有面積佔四十八．六％，私有地則五十一．三％；由於公、私有地比例差不多，都委會也曾質疑為何台大不主導都更，省去建商開發管銷成本？但台大仍堅持由四方開發建設股份有限公司擔任實施者。[新聞](http://news.ltn.com.tw/news/local/paper/800593)。圖片考慮用資料庫所呈現的公有土地(衛星地圖)＋更新單元範圍的框線。
- chewei：BOT，遠雄大巨蛋
- chewei：BOT，廣慈博愛院
- chewei：設定地上權，洪致文家族捐出的土地
- chewei：萬華區萬禧大樓，楊氏捐地作為機關使用，公部門卻改建為高級住宅大樓
- chewei：日治時期被接收成黨產，放送台變成中廣再變成帝寶
- chewei：前國產署副署長蘇維成圖利建商被判刑，現在在賣豆花兼做房地產，以及在補習班教授土地法規
- ？：新北市中和區灰磘，[新聞](http://www.mygonews.com/news/detail/news_id/104030/%E4%B8%AD%E5%92%8C%E5%A4%A7%E5%88%A9%E5%A4%9A%EF%BC%81%E8%BB%8D%E6%96%B9%E8%A7%A3%E9%99%A4%E6%96%B0%E5%8C%97%E5%B8%82%E7%81%B0%E7%A3%98%E5%9C%B0%E5%8D%80%E7%A6%81%E5%BB%BA)
- ？：新北市永和區國父紀念館

## 第二頁：我們的訴求


### 我們是誰

- [x] 整合 [facebook 粉絲頁](https://www.facebook.com/POPonFire)
- [ ] 簡介文字：
> 把長版簡介稍微修剪一下，看能不能再簡化
> [name=Hsin-yu W]

> 其實我不懂「火線上」的意思，是指緊急狀態，或指??
> [name=Hsin-yu W]

> 緊急、需要被關注~
> [name=che l]

> 了解，那這樣我比較知道怎麼修改! :)
> [name=Hsin-yu W]

> 我也刪刪刪來詞喔!
> [name=Hsin-yu W]

> 可以盡量在20字以內，點到為止，有言簡意駭意味。若是內容太長無法在精簡，建議就在劃新的一頁放 Aboutme 。
> [name=Donald Z]

> 對於About me 同感，另再刪一個20字左右的標語
> [name=Hsin-yu W]


### 我們的訴求


20字標語：救援火線公有地 使用全程透明化

About me
#### 公有土地，知道他，守護他

     「火」我們是一群怒火中燒的公民，我們要知道公有土地政策形成的過程，這從未能完整透明活化呈現出來。
     我們想知道：哪裡有公有地，並準備要被賣掉、開發的土地有多少？有的是一去不復返的私有化，有的是假公真私地被開發，想彙整政府「如火線上般」緊急的公有土地資料，公共地呈現出來，便於使大家了解。也會介紹重要的實際案例！
    我們可以：進一步監督公有土地有沒有好好運用！
    每一筆公有土地被開發、處分，原因是什麼、為什麼、如何進行、結果是什麼？
    具體的訴求與監督可以展開；更可以使群眾想像，什麼才是好的公有土地運用方式？期待你我一同來參與。
\-\-\-
另一種版本：
台灣的公有土地總量逐年下降，即私有化，許多公有土地開發的公共監理機制未盡完備而淪為地產炒作的標的。我們將透過此專案，指認出必須關心的公有土地，找到它的資料來源，將這些「火線上」的公有土地資料匯整，並且公開地呈現給民眾，凸顯出公有土地的公共監理議題，讓更多人參與土地政策的倡議與改變。
\-\-\-

### ==總結上述之訴求，與公民息息相關要點====，即「短版」====：==

1\. 修訂公有地處份法令，行政院國土活化督導小組不得閉門決策。
> (or改寫成"必須公開決策、直播錄影")
> [name=Hsin-yu W]

2.全民參與公有土地決策過程，防止土地資源被不當使用。
> 防止不當或被獲取暴利使用
> [name=Hsin-yu W]

3.我國非公用與低度利用的公有土地，其地理資訊必須公佈於網路。
4.公開公有土地的開發財務細節，公開說明規畫與未來 開發方向。
5.設定公有地地上權時間上限，避免財團變相將公有土地私有化。

#### 訴求列點pool：

> 訴求需有短版與長文，短版用於介面，常版可讓議題關注者進一步閱讀
> [name=che l]

- 國有財產法，500坪以上禁售，修正成變成100坪以上禁售
- 公眾參與公有土地的用途討論，決策過程要公開！
- 開放公有土地資訊查詢。
- 不要變賣我的家園（或不要賣掉我生命中的綠樹）！
- 不該非法變更公有土地用途，禁止財團炒作浮報地皮！
- 公有土地全面禁止標售。
- 公開國營事業、官股銀行不動產資產明細，禁止標售。
- 設定地上權不得延長。
- 土地開發範圍內有公有土地的開發案件，強制絕對公開土地開發財務細節，說明地產利潤獲益與規劃方向，供公眾檢視。
- 任何涉及公有土地與建築的開發案件的資料，格式進行整合，以開放格式釋出資料
- 公有地不應該強制參與都市更新。
- 公有土地相關審議會議資訊公開直播錄影。
- 公有土地的使用用途與開發目的，回歸公眾需求與地區生活需求，不是誰說了算，大家來討論！
- 從公有土地裡榨錢，不是解決我國稅務財政問題的方法！
- 公有土地回歸實質規畫目的，區域計畫、都市計畫、落實實質民眾參與！
- 建築業、石化業，都不是產業火車頭，但他們很愛搶公有土地。
- 參考：[巢運訴求四：修訂公地法令、停建合宜住宅](http://socialhousingtw.blogspot.tw/2014/08/blog-post_94.html)
    - 立即修訂諸如《國有財產法》、《都市更新條例》、各級機關《非公用土地設定地上權作業要點》等與公地處份相關法令，要項包括：
    - (巢運) 1.全面清查檢討非公用及低度利用之公地，結合地理資訊強制上網公開，接受全民監督。
    - (巢運) 2.一定面積與價值以上之公地處分，無論採BOT、都更、標售等模式，於政策定案前，應辦理「聽證會」聽取公民意見，納入做為處分與否及後續開發內容的基本規範。
    - (巢運) 3.公地採都更方式處分，分回之土地房舍以不出售為基本原則，並優先做為公益設施及社會住宅；公地採BOT與標售方式處份，所得價款應提撥一定比例專用於地方公共設施投資。
-
- （請丟）

### 對於訴求的認同與關注，的表達方式

- 對於訴求要點，如果瀏覽網頁的人覺得認同，可以按讚，或是簡單的小動作的方式，累積起來大家的認同
> 認同的按扭是像FB的讚嗎？是需要登入FB嗎？還是單純這只是計數器！
> [name=che l]

> 將認同改成關注的理由，是不需要理念上認同，而是想獲得實際行動上的關注
> [name=che l]


### 「我愛公有地」公有土地心願牆 (chewei提議)

- 「填寫你的訴求」網址：[http://goo.gl/ENiqf7](http://goo.gl/ENiqf7)  (google 表單)
- 「大家的訴求」呈現網址：[http://goo.gl/WppF0p](http://goo.gl/WppF0p)
> 不知道是否有那種免費的便利貼平台，可以讓使用者表達對於他關心公有土地的出發點與想說的話
> [name=che l]

> 需登入 [https://pw.aotter.net/](https://pw.aotter.net/)
> [name=che l]

> 免登入 [http://www.aypwip.org/webnote/FUN](http://www.aypwip.org/webnote/FUN)
> [name=che l]

> 或是 google 表單
> [name=che l]

> 案例 [http://nyc.changeby.us/](http://nyc.changeby.us/)
> [name=che l]



## 第三頁：公有土地大搜查

### 資料轉出地圖功能

天龍特公地 v 1.0 製作過程（by [Donald Zhan](https://g0v.hackpad.com/ep/profile/sUiBIOVIzQO)）：[http://dz1984.info/articles/Taipei_POP/](http://dz1984.info/articles/Taipei_POP/)

### 查詢功能

- [ ] 是否能增加「地址定位」的輸入篩選
> 會想到這個是因為，蠻多人可能會想知道特定地址附近的狀況，設想，他若是輸入松江路93巷，可以判讀出是位在中山區，因而地圖也顯示出中山區的 料也顯示出中山區的資料與錨點圖示
> [name=che l]

> [google maps js api連結 ](https://developers.google.com/maps/documentation/javascript/geocoding?hl=zh-tw)
> [name=Renee L]

- [ ] 「經營管理單位」：選單加上文字篩選
> 用打字，打第一個字，然後會浮現出資料庫中有的名稱（我不知道這個功能的術語@_@"）沒有浮現的，就表示沒有這個經營管理單位的資料
> [name=che l]

> 不建議使用AutoComplete方式找經營單位，原因是除非有看過這份資料，或是對公有地有充份了解的人，不然，對一般民眾而言，會無從下手。
> [name=Donald Z]

> 下拉式選單，預計提供筆數最多的7~10 個經營單位，剩下就用**其他**，先看看UX如何?！ 
> [name=Donald Z]

> 可用 chosen.js [http://harvesthq.github.io/chosen/](http://harvesthq.github.io/chosen/) ，其 UI 同時有下拉選單及 autocomplete 的形式。畢竟下拉選單適用範圍，大約是選項有「幾十個」的數量級，選項更多時，還是需要 autocomplete 類的 UI 輔助
> [name=Kang-min L]

> 這工具不錯，我收下了！ thx  
> [name=Donald Z]

> 初步想法，是控制下拉選單項目，如果~經營單位分太細，會變成超展開，後續有需要才加入AutoComplete功能。 
> [name=Donald Z]

- [x] 「面積篩選」：
- 全部
- 500 坪以上
- 500 坪～20坪以上
- 20 坪以下
> 坪數選擇說明：[國有財產法明定 1650平方公尺(500坪)以上基本上不得標售](http://www.appledaily.com.tw/appledaily/article/headline/20111215/33889080/)；20坪以上，有潛力成為鄰里公園與公共活動空間，可以鼓勵在地的社區與NGO團體進行爭取活用，成為公共開放空間
> [name=che l]

是不是需要一個[需求功能列表](https://g0v.hackpad.tw/quQyYm7cGrH#需求功能列表)，定義各功能需要的input/output，再把相關需要的連結放在裡面

## 第四頁：地圖補完計畫

目前一萬四千筆的土地資料
- 如何讓大家可以協助補充現地狀況與資料？
- 以及如何透過既有的公部門資料庫，來動態更新這批資料呢？

### 資料庫架設討論：

> 勾選現場資料維護對象均不拘嗎？任何人都可維護？維護歷史資料要保留？
> [name=Donald Z]

> 有想要另外拉出來變 **Wiki  功能**，提供資料更新維護，方便後續公有地追蹤，天龍特公地只呈現最新資料結果。
> [name=Donald Z]

> **後續追蹤公有地**
> [name=Donald Z]

> 1.接下來是否會定期匯入臺北市可用公有地資料？
> [name=Donald Z]

> 2.如何持續監督Follow每筆公有地，應該用工人智慧瘋狂追蹤，得知每筆公有地之後下落？
> [name=Donald Z]

> 3.從國產署做交叉比對，將得標公有地歸類成已處置資產，持續追蹤開發單位行為是否符合規範。
> [name=Donald Z]

> Wiki是指真正的維基百科嗎？土地會超海量耶XD 每塊地肯定是事實，但蠻多沒有故事內容素材與引用文獻，若[中文維基百科](https://m.facebook.com/groups/132122180308896)願意合作好像蠻有趣的。Wikidata ([http://www.wikidata.org/](http://www.wikidata.org/))  還是說架一個［公有土地wiki］的站，大家去那個站裡面編寫與補充資料，每一個地號就有一個條目。
> [name=che l]



### ==NEW!== 地圖中的單筆土地資料呈現＋協作功能


#### 1.既有資料：面積、段小段、地號、管理者、使用分區

> 長遠來看，既有的資料也可能會變動 XD..........
> [name=che l]

#### 2.外部連動資料

- [x] ==_是否被劃入都市更新單元內_==，若想了解這批資料裡的土地，是否已被劃入都市更新單元，其實可以用電子查詢，都市更新案件進度（[查詢頁面](http://www.gis.udd.taipei.gov.tw/r_progress.aspx)）用地號去查，不知道有沒有可能整合進來呢？
    可能呈現方式:
    - 在modal中增加_都更情形_欄位 (未加入都更、審查中、已核准)
    - 增加過濾選項，讓加入都更的土地可單獨
    - 將加入都更的土地用不同顏色標示
> 你好~這裡我有寫好簡單crawler可以輸入資料查詢結果了，請問是要用成API之類的嗎?
> [name=sherry l]

> 水喔！ :+1:API 可以容易使用。 感謝你 :heart_eyes:
> [name=Donald Z]

> :+1:
> [name=che l]

> [API example](http://urban-renew-progress.herokuapp.com/bySec/%E6%B0%B8%E6%98%8C%E6%AE%B5%E4%B8%80%E5%B0%8F%E6%AE%B5/0031/0006)  目前會將網頁的結果轉成json格式，包含都更案件編號 進度 詳細資料的url 等等
> [name=sherry l]

> 有其他的需求我再加~
> [name=sherry l]

> Git: [https://github.com/solring/UrbanRenewProgress](https://github.com/solring/UrbanRenewProgress)
> [name=sherry l]

> [sherry](https://g0v.hackpad.com/JQZkxwtgfbd#sherry)  :+1:  剛小玩了一下！許願: 希望可以有都更地號 :D
> [name=Donald Z]

> 是把所有已經在都更的地號爬出來嗎？努力爬中...... 
> [name=sherry l]

> 補充一下一個網友的工人智慧結晶，台北市都市更新地圖：[青黃不接](https://maps.google.com.tw/maps?f=q&source=embed&hl=zh-TW&geocode=&q=http://maps.google.com.tw/maps/ms%3Fmsid%3D210457882292151060872.0004a8de4e22852482c67%26msa%3D0%26ll%3D25.085366,121.524882%26spn%3D0.035797,0.040555%26output%3Dnl&aq=&sll=25.089602,121.523337&sspn=0.017898,0.020278&brcurrent=3,0x3442ac6b61dbbd9d:0xc0c243da98cba64b,0&ie=UTF8&ll=25.041749,121.554794&spn=0.043236,0.171318&z=13)
> [name=che l]

> 這個地圖是人工建的!? 太強大了...
> [name=sherry l]

> 似乎是耶，太瘋了XD 我可能會寫個信聯絡看看，[部落格](http://taipeiensis.blogspot.tw/p/test.html)
> [name=che l]

> [Donald Zhan](https://g0v.hackpad.tw/ep/profile/sUiBIOVIzQO) 不好意思我好像有誤會 "都更地號"是指案件編號嗎? 像這個: R089201
> [name=sherry l]

> 有案件號碼可直接查詢細節 [http://www.gis.udd.taipei.gov.tw/ua\_frmEasyCase.aspx?case\_code=R089201](http://www.gis.udd.taipei.gov.tw/ua_frmEasyCase.aspx?case_code=R089201)
> [name=sherry l]

> 遲來的 "北市可建築公用地 都更中地段地號表"
> [name=sherry l]

> [https://drive.google.com/file/d/0Bx-9opsSMy6Lb3Z1QUVXcU1VY00/edit?usp=sharing](https://drive.google.com/file/d/0Bx-9opsSMy6Lb3Z1QUVXcU1VY00/edit?usp=sharing)
> [name=sherry l]

> [sherry lin](https://g0v.hackpad.tw/ep/profile/x7Hh4B7mUzZ)  :+1: 水喔！ 可以在幫個忙嗎？研究如何用地號與天龍特公地串在一起。
> [name=Donald Z]


- [ ] ==建築物登記== (台北市建管處建照記錄 by ronnywang [http://tpebuilding.g0v.ronny.tw/](http://tpebuilding.g0v.ronny.tw/))
- [ ] ==周邊地價換算==
> 臺北市房地產整合資訊
> [name=che l]

> [http://opendata.tca.org.tw/od\_app\_detail.php?aid=3](http://opendata.tca.org.tw/od_app_detail.php?aid=3)
> [name=che l]

> 會想到這個項目，的出發點比較看到許多賤賣的土地案例，也衍生出兩個面向的討論：這樣一來會不會是鼓勵政府賣地，只要賣的價錢合理，這樣嗎？
> [name=che l]

- [ ] 以該筆土地面積換算成「社會公共單位」
> 例如說，這個800坪的公有空地，可以換算成一個市民菜園(600坪)+老人活動中心(200坪)，0.5 公頃的土地可以蓋 250 戶社會住宅(案例 萬華區青年段社會住宅 4075平方公尺預計蓋出270戶 )
> [name=che l]

> 有整理換算基準單位嗎？ 可以使用 infographic 方式呈現出換算視覺效果。
> [name=Donald Z]


| 「社會公共單位」換算單位表 |  |  |  |
| --- | --- | --- | --- |
| 項目名稱 | 某個面積作為單元 | 可以轉化成比率來推估 | 參考來源 |
| 社會住宅 | 0.5 公頃可蓋出270戶 | X | 萬華區青年段社會住宅 4075平方公尺預計蓋出270戶 |
| 市民菜園 | 500 坪可以有168個家庭來種菜 | 一個家庭 2 坪 | 松山區幸福農場 500坪，有168個家庭來認養種植 |

#### 3.開放協作部分

- [ ] ==「勾選」==
- 是否有住人
- 是否有老房子
- 是否有建築物登記：( 這批一萬多筆資料的預設為：「無」)
- 是否有老樹
> 或許可以連動著「台北市受保護樹木資料庫」，[資料查詢](http://www.culture.gov.tw/frontsite/tree/treeProtectListAction.do?method=viewTreeList&subMenuId=34&siteId=MTA2)，有樹木座落的地址資料，而非地號
> [name=che l]

- [ ] ==「上傳照片」==
> 授權提醒
> [name=che l]

- [ ] ==「填寫」==
- 使用者與維護者：(例：里長維護綠地)
> 有沒有人在這塊地上進行維護管理；例如松山區有一塊國防部的土地，讓在地的社區種菜成為幸福農園，[新聞](https://www.facebook.com/video/video.php?v=466970766658145)
> [name=che l]

- 開放描述的欄位：
> 例如可以這塊地的歷史故事、聽說這塊地如何如何、小時候與這塊地的互動記憶，等等等，例如該土地關於建築開發的「風聲」（新聞案例：[台北市舊議會](http://cwhung.blogspot.tw/2014/06/blog-post_22.html)/[中山樓開發案](http://news.housefun.com.tw/news/article/18463769305.html)）
> [name=che l]



## 第五頁：土地好願景

以圖文內容，相關團體的外部連結，來介紹公有土地也可以有好的營造過程與公共使用目的。

### 土地好願景［小標題＋一張圖片＋微短文＋外部連結］：


| 排序 | 標題 | 相關單位 | 圖片網址 | 圖片來源說明 | 故事 | 故事來源 |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | 信義區富陽自然生態公園 | 荒野保護協會 | [http://parklight.tcg.gov.tw/Fuyang/images/fl-0-01.jpg](http://parklight.tcg.gov.tw/Fuyang/images/fl-0-01.jpg) | 圖片來源，台北市公燈處 | 富陽自然生態公園位於臺北市大安區富陽街底，鄰近臥龍街、和平東路及辛亥隧道。西側與福州山相鄰，向東可連接四獸山，北二高臺北聯絡道由其南面穿過。  
  
日據時代為軍事彈藥庫，國民政府遷臺後繼續沿用，至民國77年駐軍撤出，期間一直是管制森嚴的地區。今日園區內有多個凹谷，是當時彈藥庫及軍需建築之遺址。 | [http://parklight.tcg.gov.tw/Fuyang/fuyang-1.htm](http://parklight.tcg.gov.tw/Fuyang/fuyang-1.htm) |
| 2 | 松山區幸福農場 | 復健里里辦公處 | [https://docs.google.com/file/d/0B5EFNXxRFP3wZEVWMFhQR2plc1U/edit](https://docs.google.com/file/d/0B5EFNXxRFP3wZEVWMFhQR2plc1U/edit) | CCBY | 幸福農場」是松山區復建里利用國防空地所建造，附近里民在此認養綠地，開發成自已的小小菜園，細心栽培不同的農作物，彼此交換植哉心得及分享農作物的收成，臉上所露出的幸福感是如此的燦爛，處處佈滿幸福感，可謂「小確幸」。 | [http://www.ssdo.taipei.gov.tw/ct.asp?xItem=75197679&ctNode=45085&mp=124011](http://www.ssdo.taipei.gov.tw/ct.asp?xItem=75197679&ctNode=45085&mp=124011) |
| 3 | 萬華區南機場樂活園地 | 忠勤里里辦公處 | [https://scontent-a.xx.fbcdn.net/hphotos-xfa1/t1.0-9/p480x480/10552658\_326782487498419\_5093993076732433938_n.jpg](https://scontent-a.xx.fbcdn.net/hphotos-xfa1/t1.0-9/p480x480/10552658_326782487498419_5093993076732433938_n.jpg) | 圖片來源，SUN SELF HOTEL Nanjichang 太陽自創旅館南機場 facebook |  | [https://fbcdn-sphotos-d-a.akamaihd.net/hphotos-ak-xpa1/v/t1.0-9/59491\_320022468097843\_1710030872\_n.jpg?oh=fdaa0f270c7df631f7917b5dbb8fb9b5&oe=547B008F&\_\_gda__=1417398115_cd1472cf204b8c2db49c63007f55420c](https://fbcdn-sphotos-d-a.akamaihd.net/hphotos-ak-xpa1/v/t1.0-9/59491_320022468097843_1710030872_n.jpg?oh=fdaa0f270c7df631f7917b5dbb8fb9b5&oe=547B008F&__gda__=1417398115_cd1472cf204b8c2db49c63007f55420c) |
| 4 | 松山區寶清段社會住宅 | 社會住宅推動聯盟 | [http://static.ettoday.net/images/309/309597.jpg](http://static.ettoday.net/images/309/309597.jpg) | 圖片來源，台北市都市發展局 |  |  |
| 5 | 中山區 FutureWard 未來產房 | FutureWard 未來產房 | [https://fbcdn-sphotos-b-a.akamaihd.net/hphotos-ak-xfp1/t1.0-9/p480x480/10339679\_249682165234858\_7142478842126817407_n.jpg](https://fbcdn-sphotos-b-a.akamaihd.net/hphotos-ak-xfp1/t1.0-9/p480x480/10339679_249682165234858_7142478842126817407_n.jpg) | 圖片來源，FutureWard 未來產房 facebook |  |  |

> 若要再增加更多案例，請參考之前的 pad [活用願景](http://hackfoldr.org/POPonFire/09RaHIX5QCC)
> [name=che l]

> 動人故事是最有力的行銷工具。
> [name=Donald Z]



=============================================================================================
以下是歷史記錄：

## 20140814 Mockup

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_33c546d57e0af85e63b73a179d503868)

> 賀喜老爺！ 終於生出來了！ :+1:
> [name=Donald Z]

> 負責任的不專業評論：字多到畫面很滿！ XD
> [name=Donald Z]

> XD 需要再刪刪來詞囉！
> [name=che l]


## 再進化：20140804 與 OURs 交流後的行動倡議版

再進化的緣由說明：20140804 下午 chewei 前往「[OURs專業者都市改革組織](http://www.ours.org.tw/)」交流，OURs 預計於九月份會有一個具體的行動記者會，訴求不要再隨便賣掉、開發掉公有土地，屆時可以為這個「天龍特公地」網站宣傳，鼓勵大家多來使用網站。Mockup：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_18e3ec9ef95a714d0e655954c4f8b9aa)


## 誕生：公有地大行動子計畫：台北市公有可建築空地

子專案網址：　[http://g0v.github.io/POPonFire/](http://g0v.github.io/POPonFire/)

### 下點誇張，可以吸引別人注意力的標題

> 標題是每一頁的「死肉梗」簡短有趣，像下新聞標題一樣！
> [name=Donald Z]

> 哦哦
> [name=che l]


### 增進 [介面](http://codepen.io/dz1984/full/zLgjr/) 細節與功能

- 把它玩到出問題
- [x] 頁面滾到最末端的地圖之後，滑鼠因為停留在地圖上面，所以頁面滾不回上面，只會一直縮放地圖
> 已經有修正了！
> [name=Donald Z]

> 五分鐘之後，我又有點懷念縮放功能了 ＠＿＿＿＠" 抱歉抱歉@@"
> [name=che l]

> 會不會，於地圖瀏覽區中，增加一個「跳回地區下拉式選單」的按鈕
> [name=che l]

> 讓滑鼠滾輪用於地圖縮放？  提供參考
> [name=che l]

- [x] 當我選好了行政區之後，目前是要用滑鼠滾輪滾到最下面地圖，這個動作能否讓頁面自動移動呢？因為若是要用滑鼠的話，也是會陷入地圖的縮放功能中，而不能滾動頁面到底部
> 選完地區後，直接跳到地圖
> [name=Donald Z]

> 逆害～
> [name=che l]

- [x] 有朋友說，點進網頁後，他一時之間不知道要往下滾動
> 加了往下圖示連結，應該比直覺一點。
> [name=Donald Z]

> 逆害～
> [name=che l]


- 功能增設建議
- [x] 地圖能否提供：地圖/衛星圖，兩種模式
> 使用Google Map內建
> [name=Donald Z]

> 我幻想ing 不要理我，套疊台灣百年歷史地圖 [http://gissrv4.sinica.edu.tw/gis/t](http://gissrv4.sinica.edu.tw/gis/twhgis.aspx)[whgis](http://gissrv4.sinica.edu.tw/gis/twhgis.aspx)[.aspx](http://gissrv4.sinica.edu.tw/gis/twhgis.aspx)
> [name=che l]


- [x] ~我覺得可以「提醒」使用者，切換成「衛星圖」的按鈕在地圖右上方，讓使用者看到土地的現況地貌~
> 感覺會有點多餘咧！XD
> [name=Donald Z]

> 嗯嗯
> [name=che l]


- [x] ~是否考慮有一種選項，同時呈現 12 個行政區的資料？~
> 已納入新版功能
> [name=Donald Z]


- [x] 增加標示，原始資料來源：零時資料中心
> 加入g0v零時資料中心連結
> [name=Donald Z]


- [x] 授權格式說明
> 程式是MIT，文宣是CC，但這份資料來源尚不知，是否套用CC
> [name=Donald Z]


- [ ] 網友發想：map上是否可以再細緻用顏色區分，例如紅色是國有，黃色是北市，樣也可以做些分析 ；例如在公有土地當中，台北市政府實質有發展權的，土地有多少，然後會受限於國家政策的土地有多少  (這是我自己想的啦XD) (PS.這不是 chewei 寫的啦)

- 介面視覺設計
- [x] ~宅宅對顏色沒有感覺，所以~色系怪怪的，想想看要怎麼配色！~
> 顏色先醬子好了！ :dancer:
> [name=Donald Z]

> 你為什麼可以打出一個卡門？(指)
> [name=che l]

> 你也可以呀 ！ "**:dancer**" 　:alien:
> [name=Donald Z]

> ！  :dancer:
> [name=Donald Z]


- 建立一個 FB 粉絲頁
- [x] 於此介面中設置連結或是FB窗框
- [x] 決定粉絲頁名稱，因該也是主專案會使用吧？
- 急切感
    - 火線上的公有土地　　　<<沖脫泡蓋送
    - 放下那塊地！　　　<<放下那個女孩！
    - 惡魔燒肉大師の公有土地搶救噴水遊戲　　　<<嗯...每一塊地都像是一塊生肉，被惡魔燒肉大師夾起來放到火炭爐上的鐵網，滋滋的肥油，我們要去搶救這些肉，可是我突然也想吃一下燒肉@@，心境設想失敗勇者也被惡魔化了...
    - 不要告別公有土地　　　<<嗯...不要告別東海岸
    - 公有土地守護平台
    - 公有土地搶救陣線
    - 不賣不棄，公有土地
    - 土地妖孽打擊平台　　　<<嗯...鯨吞蠶食魚肉吃豆腐
    - 公有地大行動
    - 地檢署　　　<<嗯...@@?
    - 打地鼠
    - 灶
    - 公有土地守護著你　　　<<嗯...有嗎?
    - 土地松
    - 公土不二
- 群眾意見
    - 大家的公有土地
    - 你的我的公有土地
    - 大家來規畫
    - 公有土地公眾目的
    - 公有地大擂台
    - 公有地大辯論
    - 好土好民
    - 好土Design / HOWTO Design
- 其他
    - 公有地必備常識筆記　　　<<嗯...地震必備常識筆記
    - 下班時間扭轉未來

### ~預計加入文案頁面~

- [x] ~什麼是公有地？＋為什麼要關心公有地？，~[~內容生產中~](http://hackfoldr.org/POPonFire/2FD7oDRhqqR)
- [x] ~如何妥善公共運用這些公有地，願景說明頁面，~[~內容生產中~](http://hackfoldr.org/POPonFire/09RaHIX5QCC)
    - ~這部分可以用換算的說法，有點像是之前中央政府總預算換算成便當，共計198公頃的土地，可以如何如何~
- [x] ~一些統計數字與資料特性簡短說明~
    - ~例如共計198公頃~
    - ~每個行政區各有多少，圖片化？~
> 文案頁面已移至進化版完成。
> [name=Donald Z]


### 資料 TODOs

- [x] 將每塊資訊放上去。
> 把面積、路段、地號、管理者、使用分區的資訊放上去
> [name=Donald Z]

- [x] 佈署到正式環境。
> 因為~只有靜態頁面，就搬到github.com 為[天龍特公地 v 1.0](http://g0v.github.io/POPonFire/)。
> [name=Donald Z]

> [天龍特公地製作過程](http://dz1984.info/articles/Taipei_POP/) by DZ1984
> [name=che l]


=============================================================================================

## 其他聯想

### 標語口號

- 公有地現身！
> 以領養代替棄養？關注代替漠視
> [name=che l]

- 轉角遇見公有空地
- 198 公頃＝＿＿＿＿個葉世文

### 本批資料的特質分析討論

[http://hackfoldr.org/POPonFire/TEJgsQ1yQWf](http://hackfoldr.org/POPonFire/TEJgsQ1yQWf)

### 後續追蹤公有地

- 接下來是否會定期匯入臺北市可用公有地資料？
- 如何持續監督Follow每筆公有地，應該用工人智慧瘋狂追蹤，得知每筆公有地之後下落？
- 從國產署做交叉比對，將得標公有地歸類成已處置資產，持續追蹤開發單位行為是否符合規範。

### 面積呈現的探討

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6ac1d36fcf060ca3e532f7c981830dd6)
- 左邊是全面積呈現，右邊是只顯示單筆500坪以上（國有財產法規範500坪以上原則禁售）
- 就土地開發的邏輯來說，左手邊的圖資更富有公有土地鄰近整合的意味，不用每一筆都很大，而是土地實質相鄰、產權機關越少越好
> 結論是什麼？ 是只需關注未超過500坪公有地？或是防止500坪以上公有地做分割？
> [name=Donald Z]

> 都需關注，但我目前想不出明確的issue。大大塊分割+小小塊們聚成很大一塊+招標與開發方式有一套邏輯，是目前觀察到的切入觀點
> [name=che l]


### 資料小截圖

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_73de121d3a8b784b49b03f03962eecaf)


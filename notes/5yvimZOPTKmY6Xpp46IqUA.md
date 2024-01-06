---
title: "十月第⑰次萌典松 moed17ct"
tags: event,moedict,hackpad
---

# 十月第⑰次萌典松 moed17ct

> [點此觀看原始內容](https://g0v.hackpad.tw/lSO9U2PIh2X)

時間：10/1（六） 11am-8:00pm（歡迎遲到早退）
地點：台北市信義區忠孝東路五段293號3樓（Bookshow 說書會）
名額：43 人（[報名頁面](http://moe.kktix.cc/events/moedict-10-1)）
內容：比照之前萌典松，採「併松」模式舉行，歡迎 g0v 各大小專案加**「萌」**參加。
費用：採量力而捐、自由贊助方式。如有剩餘，捐給下次黑客松。
活動守則：[https://g0v.io/coc](https://g0v.io/coc)
直播連結：[https://www.youtube.com/watch?v=YBurrfE0WOs](https://www.youtube.com/watch?v=YBurrfE0WOs)
> Youtube 收播後轉檔失敗，已上傳電腦裡的存檔
> [name=venev]

> (上) [https://youtu.be/iyCangB8Wxg](https://youtu.be/iyCangB8Wxg)
> [name=venev]

> (下) [https://youtu.be/n1zDKkVYq8c](https://youtu.be/n1zDKkVYq8c)
> [name=venev]

為何直播連結無法撥放?無法度看著???

> 歡迎追蹤 g0v [Google+](https://plus.google.com/+g0vTW) 或 [Youtube 頻道](https://www.youtube.com/user/g0vTW) 接收開播通知
> [name=venev]

聊天室：[https://app.sli.do/event/v394b8d2/ask](https://app.sli.do/event/v394b8d2/ask)

## 萌典相關開發項目

- 四縣客語白話字 [audreyt/moedict webkit#188](https://github.com/audreyt/moedict-webkit/issues/188)

- 修萌典的音標查詢
- [https://github.com/g0v/moedict.tw/blob/master/sites-available/moedict.tw#L20](https://github.com/g0v/moedict.tw/blob/master/sites-available/moedict.tw#L20)
- [https://github.com/audreyt/moedict-webkit/blob/master/main.ls#L827](https://github.com/audreyt/moedict-webkit/blob/master/main.ls#L827)

- **iTaigi 愛台語 網站**[**http://itaigi.tw/**](http://itaigi.tw/)**  、**[hackpad](https://g0v.hackpad.tw/moed7ct-taigi-neologism#iTaigi)**、**[github](https://github.com/g0v/itaigi)
    預計分組進行，不會寫程式的人也可以充分參與，[本次萌典松待執行項目](https://g0v.hackpad.tw/moed7ct-taigi-neologism#:h=20161001萌典松)歡迎補充

## 併松

> 歡迎把想做的專案 / 計畫寫在這裡，讓更多人看到一起幫忙！
> [name=venev]

### 《情境遊戲》南萬華群眾命名

需要前端工程師
需要知澔收服大家
提案介紹：[https://paper.dropbox.com/doc/vs8DUuUZI7YRddWVhyMfS](https://paper.dropbox.com/doc/vs8DUuUZI7YRddWVhyMfS)
介面mockup
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1fb83549fe5e2d9135429cad1e50e4ec)
技術需求
- mobile web (js) 定位、取得座標
- mobile web (js) Google Maps API，根據座標顯示附近的地圖
- mobile web (js) 上傳圖檔

上傳圖檔meta data
- 座標（固定不能更改）
- List of comments: {user id, name of place}
    - 每個comment都要有兩個分數：正分和負分

hosting
- [http://www.digicity.ws/](http://www.digicity.ws/)
上傳圖檔儲存需要server空間
- 好像可以用cloudinary
圖檔metadata需要text-based db
- 好像可以用firebase
My city.

### 陳文豊：視音漢字表

簡報檔：[https://drive.google.com/file/d/0B4W4blozmO71cWhYVGRtMDMtX1U/view](https://drive.google.com/file/d/0B4W4blozmO71cWhYVGRtMDMtX1U/view)
- 主旨：跳脫2003officeWord魔束
    建構出［個人用螢幕式點盤］
    能配合方塊字的長寬慣性
- 期待：網際化的程式建構落實［輸入法］模式


### [臺語語音轉文字輸入法](https://g0v.hackpad.tw/q5zhtMJeVQm)**相關詳情請點按左側專案介紹

我是宜蘭相褒龍~莊文龍，2002年開始佇學校教臺語，推廣臺語七字仔四句聯相褒歌。一大夢想是做[臺語語音轉文字輸入法](https://g0v.hackpad.com/q5zhtMJeVQm)，但是可能程序設計這方面需要高手大力幫贊。
> 像電腦、手機輸入&衛星導航，電腦拍文件，像咱對話免拍字用麥克就有字出現，留下會議紀錄等。
> [name=莊文龍]

> 薛丞宏:我做一個簡單的網站，予逐家傳音檔
> [name=薛丞宏]

> [https://github.com/sih4sing5hong5/TaiwaneseInputMethod](https://github.com/sih4sing5hong5/TaiwaneseInputMethod)
> [name=薛丞宏]

> 若有老師先錄音，先加減用。
> [name=薛丞宏]

> 網路頂錄音，工足大的，
> [name=薛丞宏]

> 我這馬無法度做，建議10/1去萌典松報告，揣別的工程師做伙來做
> [name=薛丞宏]

> 錄音檔案一開始就要wav檔
> [name=莊文龍]

> 如果一開始毌是，轉檔的音檔品質就有問題。
> [name=莊文龍]

> 取樣頻率盡量選48000HZ
> [name=莊文龍]

目前詞條試錄製至1455條。可提供試開發者運用。因尚未直接可以在網路錄音還要轉檔上傳，很麻煩費時!還有技術架構是否可行?我完全外行!我不敢大力推動錄音工程，及其他工作。希望這次能找到志同道合又有時間的專家來合作完成。感恩逐家!!!


## 短講

### 介紹語音合成的準備流程


        [http://www.slideshare.net/chenghunghsueh/ss-66617202](http://www.slideshare.net/chenghunghsueh/ss-66617202)

### 短講 :介紹台灣創意週活動


### 短講：讓我們來談談廁所 by Abby（大家請記得上廁所）

Abby被推坑，再推坑Mg，一分鐘從短講變成談話性節目

Mg Q: 家裡面廁所也沒分性別，到底是什麼時候，公領域的廁所開始分性別？
- 18/19世紀才有「公共廁所」這個概念
- 在美國，性別不平等，男主外，公廁只有男廁——公共廁所開始就是性別不平等的
- 一開始的時候功能根本沒有分別，只是分入口

Mg Q: 所以在一開始在性別不平等的狀況下的廁所，男廁和女廁的功能有不一樣嗎？
- 就只是先有男廁，女廁就是後來附加的而已。

Mg Q: 跨性別者自己在選擇廁所的時候你會怎麼選擇？心理影響是什麼？
- 我們在使用廁所的時候，會對進來的人做「性別檢查」
- 對進來的人的外表有期待，通過檢查才能進入
- 大家都是好寶寶，上廁所完一定要洗手
- 跨性別者在洗手的時候會很低調
- Abby: 我本人很海派，遇到問題會順便給你性別教育一下

Mg Q: 我自己很急也想用男廁，如何改變公共廁所分男女？如何推廣「通用廁所」
- 廁所的本質：解放、舒服、排除廢棄物
- 有些地方的基本要求：廁所蓋起來，有一定的整潔，這裡「把文化去掉」反而很平等。回歸到一個資源不足夠的社會，只要蓋一間廁所，讓大家可以去上就可以。所以就能把文化性質去掉，回到生活本質。
- 法律上，性騷擾不分性別
- 大家為了自己的假想害怕
- 男生被女生覺得都很危險：歧視啦
- 通用廁所設計三原則，性別
    - 標示、空間設計不能標示性別（例如：漆成藍色和紅色）—60分
    - 可以依照自己的習慣選擇器具—20分
    - 可以有隱私—20分
    - 很簡單！一件廁所裡面有各式器具、有鏡子、有洗手台

Mg: 讓廁所回歸最原始的功能，請Abby作結？
- 身為跨性別者常常遇到言語不適當、歧視
- 我自己很樂意對話，有蠢問題也可以問
- 性別友善，每個人都可以做，害羞害怕也可以表現性別友善
- g0v的特性：願意推動，讓每個人過得更好
- 性別友善利人利己 :heart:
- 黑客松除了吃東西、coding，也請記得要上廁所

venev: 不要有標誌，在實作上有什麼困難？運動者有沒有一個標誌能包容所有性別和需求？
Abby: 紫色是通用的顏色。
Abby: 沒有問題就要登出囉！

## 成果報告

liz: iTagi

呂北：用 excel 2016 圖像化呈現三年局屬氣象站氣候（雨量）

[https://www.youtube.com/watch?v=4Y-gcTm_OvI](https://www.youtube.com/watch?v=4Y-gcTm_OvI)

## Q&A 沙發區

> 因本次萌典松舉辦時機，與 原主揪 [au 就任數位政委](https://www.facebook.com/audreyt.org/posts/10154662700674928) 有所巧合，如果有問題要==向與會的唐鳳政委提問，請先參考這份====[共筆 FAQ](https://g0v.hackpad.tw/g0v-x-gov--zZD5rfTKDNg)== ==，並到== ==[這裡](https://wiselike.com/audrey-tang)== ==發問==；如果有跟「萌典松」活動相關的問題，可在本區發問。
> [name=venev]


- 10:30 會前採訪的媒體朋友，線上提問請分流到唐鳳開的聊天室 [https://app.sli.do/event/zvor4k2m/ask](https://app.sli.do/event/zvor4k2m/ask)
- 萌典松會前唐鳳聯訪紀錄（CC by 4.0）、場邊半島電視台採訪（CC0）
    影片 [https://www.youtube.com/playlist?list=PLEqOx80MURMyxxLpIZ1ATiJl3SvR7GJLJ](https://www.youtube.com/playlist?list=PLEqOx80MURMyxxLpIZ1ATiJl3SvR7GJLJ)
    音檔 [https://soundcloud.com/bookshow/20161001-audreytang-interview-audio](https://soundcloud.com/bookshow/20161001-audreytang-interview-audio)


## 工作區

### 點餐

> 活動前 1~3 天訂購
> [name=venev]


### 帳務

- [明細](https://docs.google.com/spreadsheets/d/1JLdXfMQops2lBsgwpnQHE_L_S4yLi3yB4Y4yRuaYBd4)

### 萌工募集

- mglee

### \[template\] 會前提醒

> 活動前 2~3 天提醒，透過 KKTIX 報名系統發信
> [name=venev]

Hello,

（日期） 的第___次萌典松就在這週___了！
這封信除了歡迎你開開心心來提案、hacking、交流之外，附上幾點小提醒：

【共筆協作】這兩天歡迎先到 hackpad 登記提案、短講
（hackpad 網址）

【別迷路囉】請參考場地交通指南，或上 Google Map 搜尋「」
（交通指南或地圖網址）

【我愛地球】萌典松提供飲料、餐點，請盡量攜帶自己的杯子、餐具
> 以下 optional，各次主揪個案提醒
> [name=venev]


【音樂募集】 徵求用餐、hacking 時段的「背景音樂」，歡迎帶你的歌單到導播台，和萌友分享：
    ♫ 讓人輕鬆歡樂、食慾大開，容易和新朋友熟起來的曲子～
    ♫ 讓你專注工作、靈感湧現，進入心流，飛快 coding 的音樂～
    ♫ 音量以不干擾大家工作聊天為原則，Youtube playlist, iTunes, soundcloud…...皆可

==線上投稿（by Shoichi Chou）XD==：

[https://soundcloud.com/chou-shoichi/hackathonjpver080215-remixed](https://soundcloud.com/chou-shoichi/hackathonjpver080215-remixed)

==投稿午餐音樂（應該會聽到睡著） ==
> 12:53 放送中
> [name=venev]

[https://open.spotify.com/user/lazurloner/playlist/3v0zH9pkmyYvX6y3jWz2v5](https://open.spotify.com/user/lazurloner/playlist/3v0zH9pkmyYvX6y3jWz2v5)

==投稿古典樂==
- [https://youtu.be/30it4hbfQ7A](https://youtu.be/30it4hbfQ7A)
- [https://www.youtube.com/watch?v=_dJ2nNQYl5o](https://www.youtube.com/watch?v=_dJ2nNQYl5o)
- [https://youtu.be/5BPhkY6xIP8](https://youtu.be/5BPhkY6xIP8)
- [https://youtu.be/XZTeavJ9frA](https://youtu.be/XZTeavJ9frA)
- [https://youtu.be/disqzLW1QJA](https://youtu.be/disqzLW1QJA)
- [https://youtu.be/KweXColOsgQ](https://youtu.be/KweXColOsgQ)
- [https://youtu.be/OKNHp-daefk](https://youtu.be/OKNHp-daefk)

因為這次報名額滿後，還有幾位朋友詢問能否參加，
如果臨時不克前來，請記得上 KKTIX 取消報名
[https://kktix.com/dashboard/overview](https://kktix.com/dashboard/overview)


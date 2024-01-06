---
title: "政誌 - 討論與建議"
tags: hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/nGRHg4knibC)

**\[**[fact.g0v.tw](http://fact.g0v.tw)**\]**

## 想解決什麼問題 \- 詳參考 [Github專案](http://github.com/g0v/twangry)


## 如何加入？

請參考  [**Github專案**](http://github.com/g0v/twangry)

## 錯誤回報

別跑錯地方，到github report bug ~~
[https://github.com/g0v/twangry/issues?state=open](https://github.com/g0v/twangry/issues?state=open)

## Idea Pool



### 國民大會真人面對面討論議程及紀錄：

- ~Tag（若有編輯在的話）~ [Fumi Miyabe](https://g0v.hackpad.tw/ep/profile/EpzFgKw1Qcd)飛越入坑了！
    - ~沒有編輯 Q_Q~
    - ~完全沒有編輯 Q_Q ~
    - ~完完全全沒有編輯 Q_Q~
- parser邏輯討論
    - 目前討論是，如果語意parse出來前後有東西，就直接畫黃線~~~
    - 抓出來畫重點的部份用 #000, 前後文就 fade out, 讓被抓到的文字看起來像從原本維基文的段落中浮出來~
- 功能細節討論
    - timeline library
        - 可以用在首頁的時間軸
            - [http://okfnlabs.org/blog/2012/12/04/javascript-timeline-libaries-a-review.html](http://okfnlabs.org/blog/2012/12/04/javascript-timeline-libaries-a-review.html)
            - [http://www.inside.com.tw/2011/12/20/timeline-websites-and-dev-tool](http://www.inside.com.tw/2011/12/20/timeline-websites-and-dev-tool)
            - ChronoZoom [https://github.com/alterm4nn/ChronoZoom/](https://github.com/alterm4nn/ChronoZoom/)
            - 由慕約提供的sample video [http://parallax.freebaseapps.com/](http://parallax.freebaseapps.com/)
    - 訂一個可以寫在 mediawiki 條目裡的給機器讀的時間軸格式 (JSON?), 不用顯示出來, 但是讓非 geek 也容易編輯
    - HTML 有一個 time tag 可以用
        - [http://www.w3schools.com/tags/tag_time.asp](http://www.w3schools.com/tags/tag_time.asp)

### 維基人小聚討論紀錄

- [https://www.wikidata.org/wiki/Wikidata:Main_Page](https://www.wikidata.org/wiki/Wikidata:Main_Page)
- 跟維基首頁的「歷史上的今天」結合
> [http://el.dbpedia.org/apps/DayLikeToday/](http://el.dbpedia.org/apps/DayLikeToday/)  <\- dbpedia已經有人做過了.. XD
> [name=Jimmy H]

- 有人說「[卡市達](https://www.facebook.com/pages/%E5%8D%A1%E5%B8%82%E9%81%94%E5%89%B5%E6%A5%AD%E5%8A%A0%E6%B2%B9%E7%AB%99/372467782832468)」可能歡迎g0v （玩笑？）
- [https://www.wikidata.org/wiki/Wikidata:List\_of\_properties/Events](https://www.wikidata.org/wiki/Wikidata:List_of_properties/Events)
- 據說直接去wikidata攻城掠地比較實在 XD
- 雖然從維基上抓資料比較快速方便，但有些事件敘述仍舊冗長，放在時間軸會過於混雜，建議再重新編輯改寫簡短一點。

### Slogn

覺得目前首頁「勿忘政治」溝通力有點弱，以下slogan徵求希望:
- 「好好盯住政治人物，要不然明天連歌都沒得唱了。」伊坂幸太郎《蚱蜢》(自己先送上一個)
- 來提幾個
    - 永誌不忘（想法來源 [https://www.moedict.tw/](https://www.moedict.tw/#誌)[#誌](https://g0v.hackpad.tw/ep/search/?q=%23%E8%AA%8C&via=nGRHg4knibC) 的第一個解釋）這裡的"誌"作動詞用[記錄](https://www.moedict.tw/#記錄)、[記載](https://www.moedict.tw/#記載)
    - 政之事，誌之（想法來源 [https://www.moedict.tw/](https://www.moedict.tw/#誌)[#誌](https://g0v.hackpad.tw/ep/search/?q=%23%E8%AA%8C&via=nGRHg4knibC) 的第二個解釋）
    - 我們的政治，我們誌之（上面的白話文版）
    - 我們的政治，全民的政誌
    - 大條代誌，攏底政誌
    - 不看政誌，會出代誌  (+1)
    - 我們記得
    - 眾誌成城
    - ~脫韁的政府，來自未盡監督責任的鄉民~ 這是鄉民關心你的 slogan orz

### 頁面改善:


### 現有頁面：

- 首頁（所有的事件）
- 事件頁（單一事件的細節呈現）

### 首頁

- 事件metadata /tag
    - 如：智財局封網事件 current status : 「準備借屍還魂」 You can: 「關注/支持網路中立性立法」
    - 如：林益世案最新進度
        - 可能可以用Tag的方式來實作~例如林益世的tag就會有「貪污、弊案、借屍還魂中」
    - 目前Tag完全照自由心證，以下開放建議的種類
        - 人權、國家安全、土地開發、政客、政策、環境、糧食、網路
        - 外交、國防、經濟、教育、環保、產業
        - \_\_\_\_\_\_
- 改善首頁排版、呈現方式（目前已改為直式~但功能不齊全）
    - 直式：這樣想的主要目標是能做篩選，例如：「土地開發」，能夠篩選出來「美麗灣、大埔、中科四期」... ，一眼就看出來到底這幾年發生哪些
        - sample 1- fb like - [http://www.9lessons.info/2012/01/facebook-timeline-design-using-jquery.html](http://www.9lessons.info/2012/01/facebook-timeline-design-using-jquery.html)
        - sample 2- [http://37signals.com/about](http://37signals.com/about)
        - sample 3- Google Plus
        - [#](https://g0v.hackpad.tw/ep/search/?q=%23%E7%9B%AE%E5%89%8D%E6%98%AF%E7%9B%B4%E5%BC%8F%E5%90%A7&via=nGRHg4knibC)[目前是直式吧](https://g0v.hackpad.tw/ep/search/?q=%23%E7%9B%AE%E5%89%8D%E6%98%AF%E7%9B%B4%E5%BC%8F%E5%90%A7&via=nGRHg4knibC)？規則是什麼呢？不是FB的左右時間順序？
    - 橫式：Facebook timeline 呈現方式好像不夠精簡? 我覺得目前的 timeline 比較能同時容納多一點事件, 有集中爆發的感覺，就是可以一個一個「slide」，仔細看看
        - sample - [http://timeline.verite.co/](http://timeline.verite.co/)
    - 直+橫式
        - 上面橫式，下面直式~(from pm5)
        - 可用密技爆破（上上下下左右左右）
    - 因為目前事件頁是用橫式，如果首頁也是橫式的話會不會有使用者使用上混亂的問題。直式的話可以把在同一時間內很多的事件變成只有標題，或是濃縮起來點下去在展開來完整資訊？
    - 或是都用橫式但畫面上應該要有些跟 event pages 有區別。
- ~增加首頁篩選功能，包含依照時間起迄、Tag篩選、或關鍵字搜尋~ （已經[上線](http://fact.g0v.tw)！）
- 讓使用者可增加事件 （[先用google doc擋著](http://fact.g0v.tw/gdsmw.html?doc=/README.txt)）
    - 少數使用者方式：以 github更新TW-history方式即可，但問題是不是每個keyword都有wikipedia條目（希望可以到不只網站維護者來幫助，可能一些文字編輯者也可以很容易去更動）
    - 很多人可加：需要嗎... ?（如果要的話可能需要檢舉、或定期去查看）
- slideshow 播放功能
    - 可能可以播放一個 tag, 或是一組 event, 可以看到服貿協議二讀之前就會有一堆小議題冒出來混淆視聽.
- Google Culture Institute 的[範例](http://www.google.com/culturalinstitute/browse/?projectId=the-holocaust)


### 事件頁

- 以wikipedia 的資料為基礎，讓使用者可為其增加額外的媒體  (包括可以提出觀點或是詮釋對台灣的影響嗎?)
- ~wiki parse需要處理wikipedia的reference~ ko !!!
- ~定期更新wikipedia進度（需考量熱門度）  ko!!!~
- 讓使用者可驗證後，增加事件（有需要嗎？）
    - 以email或簡訊認證後產生cookie為主，不需login，不綁任何social media
    - 也許可以用[http://www.mozilla.org/en-US/persona/](http://www.mozilla.org/en-US/persona/) 做auth.
- ~利用苦勞網的 tag 去 google 搜尋自動得到各種事件的維基主題（也必須設計機制是手動刪除抓錯的）~
> ~我來寫 api 抓~
> [name=Wu H]

> [~Wu Min Hsuan~](https://g0v.hackpad.tw/ep/profile/p410lKWpWzP) ~太太太好了！！！~
> [name=Jimmy H]


### 內容

- 參考一下天下網站的[互動圖表](http://www.cw.com.tw/PicChannelPage/pic_article_cw52902.jsp)

### 視覺改善

- 2013/8/11 [示意](https://docs.google.com/file/d/0BwrZHGLz2h7mN0N2VTEtaGl5dHc/edit?usp=sharing) /waiting
- [logo](https://docs.google.com/file/d/0BwrZHGLz2h7mNWFoZzF1ZUpkY1E/edit) (by [Weiting Tseng](https://g0v.hackpad.tw/ep/profile/HjE8bg6th3B)) \- fact.g0v.tw素材庫請到最下方
> 年份怕不夠放，不過好棒~「政誌」的字體是你用出來的嗎？
> [name=Jimmy H]

> 我也有想到，想說可能要伸縮？？  字體是改出來的XD
> [name=Weiting T]

> 字體我想就直接上了，有svg可以來一下？若沒向量檔，就png 24bit背景透明
> [name=Jimmy H]

> 好！ 我有ai檔，轉檔沒找svg格式，所以先轉png [放這裡](https://docs.google.com/file/d/0BwrZHGLz2h7mNWFoZzF1ZUpkY1E/edit?usp=sharing)
> [name=Weiting T]

> 好有氣魄的logo
> [name=Hsin-yu W]

- 目前想改用這個，去掉藍色變灰色，刊頭用waiting的style [http://tympanus.net/Blueprints/VerticalTimeline/](http://tympanus.net/Blueprints/VerticalTimeline/)
- 一些時間軸網頁參考：
    - [時間軸網站大集合與網頁製作元件](http://www.inside.com.tw/2011/12/20/timeline-websites-and-dev-tool)

### 其他令人振奮的

- 怒氣值：讓使用者可張貼Facebook Link(例如粉絲專頁)，為事件增加怒氣值
- 當有怒氣破表時，首頁的爆氣效果...（請自行想像）
- 可以用顏色來區分分享次數的多寡，如果多的話在首頁的顏色可以不一樣或是 border 不一樣（記得 facebook 好像有 api 可以去算文章分享和按讚在 facebook 上的次數）
- 歷史上的今天：讓使用者可以看到歷史上的今天，發生什麼政誌令人難忘。

### 名稱想法整理

- ~怒政事件簿（應該可換掉）~
- ~鄉民的震怒（強調怒！） ~
- ~鄉民的正怒（強調即時性）~
- ~鄉民的政怒（強調政治...）~
- 移到github上去做[最終決定](https://github.com/g0v/twangry/issues/30)了~（政誌）

## 後援

### 開發者

[howard chi](https://g0v.hackpad.tw/ep/profile/uldM12vxAYG)
[Pomin Wu](https://g0v.hackpad.tw/ep/profile/oGf5HRRuJSf)
[Jimmy Huang](https://g0v.hackpad.tw/ep/profile/EcUrTWSKroj)
[Wu Min Hsuan](https://g0v.hackpad.tw/ep/profile/p410lKWpWzP)
[Ian Wu](https://g0v.hackpad.tw/ep/profile/tvOkovzkQU8)
[stardog](https://g0v.hackpad.tw/ep/profile/qKwIKfWuAUC)

### 企劃/視覺設計

[Weiting Tseng](https://g0v.hackpad.tw/ep/profile/HjE8bg6th3B)

### 首頁編輯

[Fumi Miyabe](https://g0v.hackpad.com/ep/profile/EpzFgKw1Qcd)
[Pomin Wu](https://g0v.hackpad.tw/ep/profile/oGf5HRRuJSf)
[Jimmy Huang](https://g0v.hackpad.com/ep/profile/EcUrTWSKroj)
[Wu Min Hsuan](https://g0v.hackpad.tw/ep/profile/p410lKWpWzP)

### 技術指導

[Chia-liang Kao](https://g0v.hackpad.tw/ep/profile/AHlg3ouwI8g)
gsklee
au
....

### 素材庫

- [google drive](https://drive.google.com/folderview?id=0B-wTztKH2tKiOFF1a0NoWkxWRTA&usp=sharing&tid=0B0NsS2a-Qx8ZN19uV1p6YWd6TXc)
- 政府部會的報告 (雖然都是一堆廢話)










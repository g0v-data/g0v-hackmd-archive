---
title: "fr0ntend-bridge 第零次前端教學松"
tags: 零時的學習不能等,event,hackpad
---

# fr0ntend-bridge 第零次前端教學松

> [點此觀看原始內容](https://g0v.hackpad.tw/sYHY4dqb1OE)

_注意: 這是一個變相的填坑教學松，若你不想被推坑請慎入_ :smiley_cat:

## 目標

最早是想辦jsgirls，另外也有人想弄cssgirls，還有muan也有辦實驗室松鼠。加上g0v蠻多人想要學習前端技術，於是有了front-bridge。主要目的就是**自己的下線自己教**，希望讓更多人學習網頁設計的技術，進而幫助專案填坑的速度。有鑑於有許多前端社群，還有許多的rails教學團隊，所以課程目的會著重於填坑技術。若是希望能快速學前端技術成為一技之長者，可以建議參加前端或rails社群所發起的課程，也可以嘗試[innovatist](https://www.facebook.com/innovatist)。
> 可惡, 想參加，可以開個台南場嗎?
> [name=HisnYi C]

> 南部場也許可以找場地直播討論，
> [name=Yo C]

> 有直播歡迎鍵盤參加, IRC發問 orz
> [name=Yuan C]


## 規劃

- 一個月舉辦一次
- 教學內容採取直播錄影
- 助教以參與g0v的人為主，最好是專案開發者來找下線
- 對象為想學習前端技術的g0v支持對象 (要有參加以後被推坑的心理準備)
- 事先規劃問題已釐清各位的自身程度是否適合參與這次課程

## 遠端參與方式

Lesson 1 @ BOOKSHNOW 已規劃直播
除高畫質直播外，由講師 [Yuan Hsiang Cheng](https://g0v.hackpad.com/ep/profile/FurgGRVDQsl) 考慮，打算用哪種方式跟遠端觀眾互動，再選擇適合的通訊工具配合。
- 文字：YouTube 影片評論
- 文字：開 IRC Channel
- 語音：Skype → 現場喇叭播音（類似 call-in）。但 YouTube Live 直播會延遲最多 1min，要架第二軌較低畫質但更即時的直播 / 語音（hangout / skype...）兩方才能來回對話，不用每次換觀眾講話都要等 1min。
> 可能暫時不考慮用skype ，昨天討論的結果是在實作時間可以線上IRC問問題
> [name=Yuan C]

- 語音：RC語音，可以比較即時的傳遞聲音，只是沒試過１０人以上的品質。
> RC語音太多人同時發出聲音會很混亂，Windows Only，手機的音質似乎不太好，多人同時聽則沒有問題
> [name=a0000778]


## Lesson 1  (6/14) @ [Bookshow](http://bookshow.tw/traffic)

報名：[http://g0v-mini.kktix.cc/events/fr0ntend-bridge](http://g0v-mini.kktix.cc/events/fr0ntend-bridge)
時間：6/14 14:00~17:00
地點：BOOKSHOW 說書會（台北市信義區基隆路一段141號6樓之7，[交通地圖](http://bookshow.tw/traffic)）
費用：附飲料、點心，請自由贊助，量力而捐，如有剩餘，歸入[小松基金](https://docs.google.com/spreadsheets/d/1JLdXfMQops2lBsgwpnQHE_L_S4yLi3yB4Y4yRuaYBd4/edit#gid=0)，下次小松繼續用
直播：[https://www.youtube.com/watch?v=qDW-RqKDn1c](https://www.youtube.com/watch?v=qDW-RqKDn1c)


第一堂課的目標在教大家網頁設計的入門，如何撰寫正確的  html、css  和  javascript，還有如何簡單的使用  chrome  瀏覽器所提供的網頁開發者工具。
這堂課我會著重在  chrome 開發者工具的使用技巧上面。
因為  html、css  或  javascript  基本上網路上都可以找到教材來看，但是很少人再分享如何操作開發者模式(其實  [html5rocks](http://www.html5rocks.com/en/)  也有影片教學)。

### 時間表 (2pm - 5pm)

開場
入門導覽
練習
填坑
成果報告
> 看來要準備很小的坑才有辦法成果報告…（抓頭）
> [name=ET B]

> 我想成果報告不是必要，填坑過程才是必要，能解掉一些bitesized issue都可以報告XD
> [name=Yuan C]

> (點頭) 那來設計一些 issue 給 airos 解好了喔呵呵
> [name=ET B]


### 鑑別問題

> 這是參加前還是參加後要會的？ XD
> [name=ET B]

> 參加後要會的，參加前已經會的請報名擔任助教
> [name=Yuan C]

> 有進階班嗎XDD 剛發現是L1  ...只好等後面的場次了XD
> [name=lanfon]

> 可能要等下個月喔，報名當助教
> [name=Yuan C]

> 6/14期末考前兩天QAQ L2就可以出沒了YA
> [name=lanfon]

1.  是否知道甚麼是正確的html格式
    1.  doctype  的寫法
    2.  為什麼我的網頁會亂碼 (hint: meta)
2.  是否知道甚麼是正確的  css  格式
    1.  知道何謂  selector
    2.  會分辨  id  和  class  的不同
3.  知道怎麼使用 chrome 開發者模式
    1.  檢查元素
    2.  修改  style
4.  找到[柯P網頁](http://kptaipei.tw/)藏的彩蛋
> 上面這題超簡單的拉，大家快點去玩
> [name=Yuan C]


### 開發環境

請參與者一定要準備自己的筆電，因為會有「很多」練習時間，尤其最後有所謂的實際填坑時間，請務必自備筆電。
會教大家設定 類似於 g0v.tw 的網頁開發環境。
> 其實我正在想辦法把gullet變得比較好用一些 orz 
> [name=Yuan C]

> 下面項目是會簡易教學?  還是要提前灌好 XD
> [name=Lee]

> 需要現場幫裝 sublime 之類的嗎... XD?
> [name=Poga P]

> 盡量事先裝好基本的 nodejs, github for windows, sublime text
> [name=Yuan C]

> 會準備好教學
> [name=Yuan C]

> 太可惜了，如果早一天就可以推坑 sublime 團購 (誤)
> [name=Lee]

> 我團購了sublime 可是再用atom ....
> [name=Yuan C]

- nodejs
- git

### 教材參考

這邊包含新手入門、線上互動教材，參與者若是事先有空也可以先行練習。
> 大家可以多多提供新手適合的教材
> [name=Yuan C]

> 這邊會在整理過
> [name=Yuan C]

- 實驗室松鼠教材: [#1](https://speakerdeck.com/muan/project-lab-squirrel-number-1)、 [#2](https://speakerdeck.com/muan/project-lab-squirrel-number-2)
- [米奧的CSS教學](https://dl.dropboxusercontent.com/u/13573030/css_tutorial.pdf) 及[教材](https://dl.dropboxusercontent.com/u/13573030/css-tutorial-example.zip)
- Mozilla Developer Network ([MDN](https://developer.mozilla.org/))
- Codecademy [(html & css)](http://www.codecademy.com/tracks/web)
- Code School [(html-css path)](https://www.codeschool.com/paths/html-css)
- CodeCombat ([JS](http://codecombat.com/))
- [前端半條龍](https://g0v.hackpad.tw/g0v-designer-set--R7BEW2muCbU)
- [CSS Diner](http://flukeout.github.io/) (CSS selector互動教學)
> 這個好玩XDDD↑
> [name=lanfon]

- CCSP 課程 [HTML](http://ccsp.ntumobile.org/webdev/html.html#/) , [CSS](http://ccsp.ntumobile.org/webdev/css.html) , [JS](http://ccsp.ntumobile.org/webdev/js.html#/) 課程投影片，以及學運期間為了在立法院上課的學生而做的[課程錄影](https://g0v.hackpad.tw/fgnqWJOCb63#課程錄影)。
- [GeneralAssembly Dash](https://dash.generalassemb.ly/) , HTML + CSS 的手把手實作教學，最後網站結果都很不錯看，而且設計上還有少許 gamification
- [Chrome DevTools 的教學](https://developer.chrome.com/devtools/index)（google 官方），以及[教學影片](https://developer.chrome.com/devtools/docs/videos)。
- [Git 入門繪本教材](https://speakerdeck.com/yunico/20140601-github-kaigi-yunico?slide=16)
- [http://www.ustwo.co.uk/blog/the-ustwo-pixel-perfect-precision-handbook-2/](http://www.ustwo.co.uk/blog/the-ustwo-pixel-perfect-precision-handbook-2/)
- [http://blog.cgmlife.net/](http://blog.cgmlife.net/)
- [nodeschool](http://nodeschool.io/) 可以離線使用的 node.js 教學 package 。NodeUp  有[一期](http://nodeup.com/fiftyfive)專門講它。
- [goingnative](https://github.com/rvagg/goingnative) nodeschool 風格的 node native extension 教材，由 nan 作者發起。

自學自幹工具參考, for airos
- 本身已經會視覺設計，想快速製作網頁
    - adobe muse
    - google web designer (free)
- 從常用的語法開始熟悉，建立網頁運作的基本概念
    - 英文可
        - codeschool
        - codecademy (free)

### 報名 (上限27人)

報名者請記得要準備填坑的項目來參與，若是沒有準備的話，請接受主辦方的推坑 :smile_cat:
報名前往: [http://g0v-mini.kktix.cc/events/fr0ntend-bridge](http://g0v-mini.kktix.cc/events/fr0ntend-bridge)
> 以現有的 g0ver 為主？給已經是填坑獸，需要加強技能的人，還沒填坑的就排後面點… XD 
> [name=ET B]

> 還沒填坑可以參加 但是要有當天被推坑的心理準備 XD
> [name=Yuan C]

> 印象中萌典松當天說要來的有：ipa、a0kman、昆翰、moon_c、
> [name=ET B]

> 求報名網址！(還是應該推在下面？)
> [name=jbytw]

> 先推在下面吧，晚點會釋出報名網址 ，若是沒有組隊的話順便括號註明一下是學生還是助教
> [name=Yuan C]

> 感謝開課QQ會認真填坑報答
> [name=Moon C]

> 樓上快簽名 XD
> [name=ET B]

> 是說我禮拜六都有可到一點半，所以可能會遲到XD
> [name=Moon C]

> 據說是兩點開始喔
> [name=Yuan C]

> 看地點在哪啦~我需要移動時間，是說去哪報名.......
> [name=Moon C]

> 看來是在萌典松同一地點 bookshow XD venev++ 來的路上不要趕時間，安全第一
> [name=ET B]

> 滿了嗎?嗚嗚嗚嗚嗚嗚嗚嗚嗚嗚嗚嗚嗚嗚嗚嗚嗚嗚嗚嗚嗚嗚嗚~~~~~~~~(大哭跑開)
> [name=溫翊伶]

> No~~~~ 一回神已售完...
> [name=jbytw]

- ETBlue (挖坑獸) → airos (填坑獸)，填坑主題：g0v summit 電子版文宣
- jbytw (野生準備被推坑, 學生)
- [NewCliCker](https://g0v.hackpad.tw/ep/profile/Aq3Xw5pjIMW) ( 狡兔有三坑的學生 )→ [溫翊伶](https://溫翊伶) (被慫恿入坑的助教)　填坑主題：G8V電視牆介面CSS調整 （學生自作主張指定坑）
- Lee 挖坑 -> 帶交大學弟 (張xx)  填坑主題： 產生月份公報頁面框
- ipa (挖坑填坑推坑, 學生)，填坑主題：g0v.tw 官網修修補補
- venev 填坑推坑學生，填坑主題 g0v.tw 官網、leve1up 或基礎建設
- [Rick](https://g0v.hackpad.tw/ep/profile/sdju6K3QYly) (<=超級新手)
- AceChen (荒廢多年的程式苦手) 填坑主題：研究 ocf.tw 的坑有多深 / 啥米松人力後台

### 待填的坑

- 開放文化基金會網站 landing page：[詳見零時坑報 2014 年 5 / 6 月號](https://g0v.hackpad.tw/i8tMqWAFi39)
- **自學地圖上也來挺一下**  [http://map.alearn.org.tw/we/index.html#/%E5%8F%B0%E5%8C%97#%E9%9B%B6%E6%99%82](http://map.alearn.org.tw/we/index.html#/%E5%8F%B0%E5%8C%97#%E9%9B%B6%E6%99%82)

### 行前通知

各位助教、同學大家好，

明天(6/14)，下午2點在BOOKSHOW舉行第零次的零時前端教學松，大家不要忘記來喔，活動會準時開始也請記得盡量不要遲到，一起把握短暫的學習時光。以下有幾點注意事項，請大家務必仔細閱讀。

共同要記得的是攜帶一台筆電，為了增進大家肌肉記憶力，所以安排了不少實作時間，要是沒有筆電可能會無法度過愉快的時光。

報名學生票的朋友，可以的話，先將環境準備好，需求環境如下。
1.  安裝nodejs
2.  安裝git (推薦使用github的視窗軟體, 如github for windows 或 github for mac)
3.  安裝編輯器 (推薦使用Sublime text 2)

若是不會安裝的朋友也不用擔心，到現場會有助教幫忙，但是會請大家一起協作安裝說明文件，以利後面的人學習參考。
報名助教票的朋友，請準備最愉快的心情，面對分配給各位的前端初心者。

### 當天投影片

[https://www.icloud.com](https://www.icloud.com/iw/#keynote/BAJK-EYT33f5Gy-NKoeB7bLG8mumVvmtwoGF/fr0ntend-bridge)[/iw/](https://www.icloud.com/iw/#keynote/BAJK-EYT33f5Gy-NKoeB7bLG8mumVvmtwoGF/fr0ntend-bridge)[#keynote](https://g0v.hackpad.tw/ep/search/?q=%23keynote&via=sYHY4dqb1OE)[/BAJK-EYT33f5Gy-NKoeB7bLG8mumVvmtwoGF/fr0ntend-bridge](https://www.icloud.com/iw/#keynote/BAJK-EYT33f5Gy-NKoeB7bLG8mumVvmtwoGF/fr0ntend-bridge)

### 當天文字轉播


14:14 (自我介紹)
ly: 怎麼稱呼你、你是學生或助教、你的背景，讓你的助教 / 學員找到你
可以看一下高二生寫的「攝理生活記」部落格 [http://blog.cgmlife.net/](http://blog.cgmlife.net/)
14:16
pipi
14:12

stella 使用者體驗設計，學生
mimi，台大新聞所學生，想用在  E 論壇
justin 阿平的朋友，插畫漫畫，學生
rick 學生，節能，幾乎不會，一點 c html css
科比，零傳媒
lee，=  jessy，韌體工程師，g0v 公報組，現在去帶學弟張家興
SUMMIT，在中研院統計所研究助理，專長統計分析，想學資料分析跟前端，準備被推坑　>_^
venev：小馬學生，場地主人，飲食可自由取用，電梯卡不足…要不要把卡交出來，場地有問題可找我
alice，助教，可是我會不好意思……原本想報學生但是額滿了…現職前端互動工程師
貝裘，沃草行銷，學生
mrorz，ccsp 助教
Rene，設計師，會一點 html ，愛用（複製貼上XD） bootstrap
brecht，在 ithome 工作，前端，助教
poga，稍微碰前端，助教
acechen，學生，推坑 summit，
tka，github 按綠色按鈕
etblue: 插畫，助教，p.s. 今天文播輸入法亂打，請大家幫改錯字
airos，summit 視覺，平面設計師
ipa：文字影像，學前端
simonpai，前端，做動民主跟超濃郁
pm5，沃草工程師
米奧，助教，網頁設計師
張加薪，交大機械工程碩士，學生（lee 學弟）
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_63f12b8c6918f338ca264d8979a679f7)
[http://first-launch.com/images/girl-animation.png](http://first-launch.com/images/girl-animation.png)

14:28
因為 rails girls 讓我們有點眼紅，就想辦 js girls、css girls，慕安帶實驗室松鼠教大家寫網頁，所以我們也想說來弄…有很多專案提案畫 mockup，一直有人想學網頁，因為自己的下線自己教，有次萌典松不知道為什麼這個責任就默默的落到我身上…默默決定了日期……

純粹學前端技術的話前端跟 rails 社群都有，想投入產業的話有很多其他管道，為了展現 g0v 特色，除了教學外主要實際填坑。

### #29

網頁到底怎麼運作？以前要跟長輩敘述瀏覽器就是桌面上有個藍色的 e，但是從輸入網址到呈現發生了哪些事情呢？

### #3

大家都有去餐廳過，麥當勞的話會有服務生或點餐的人，點完以後他會把訂單（上面的字你可能看不太懂）送到廚房，廚師做完後才給外場。
對應到網頁開發，網址就是告訴 browser 你要什麼菜，瀏覽器跟後端廚師之間有個 http 協定，然後會回傳一些西，200 ok，404 找不到，500……這個過程是跟你上餐廳點菜類似的。

### #5

在廚房裡有冰箱，存放東西，這就是資料庫。知名的 database： blah。程式語言就是像廚師，只是有不同的流派，有 ruby php，但處理的都是一樣的食材。最後透過機器（server）幫我們做食材處理，server有linux，windows。這是後端。
前端有 html css javascript，對應的概念是，html 像是擺盤、css 像是裝飾。那為什麼用 ps 做版的前端設計師要學 js 呢？js 像是調味，如果每道菜一樣的擺盤跟裝飾，調味可以讓他變得更好。
瀏覽器網址有 domain name，電腦則是看 ip。在瀏覽器輸入網址時，電腦會去找伺服器在哪，抓 code 回來，然後瀏覽器會把這些東西變成你看到的網頁。

#### html 超文本標示語言 #7

他爸爸叫 sgml，是標準的規範語言的表示方法，原本的概念是…像作文，我們會用破折號、引號標註文字，html 就是在文字上做標示，包括斜體標籤。後來有人說，可以更進一步表示，最早的網頁只是用來放論文等，html 能力不是很強…html 的開頭就是開始的標籤、結束的標籤，合格的 html 包括：
head 宣告，告訴瀏覽器怎麼處理這些內容
body 就是網頁內容
head 頁面上看不到

### #10

doctype：html 當初是一個很簡單的概念，早期提出時東西不豐富，常碰到的問題是每家瀏覽器實作的方式都不太一樣，後來有人提出要標示文件的型別，就是 doctype。4.0 版 html 後面有更長一串的宣告，現在到 html 5 就不用那麼長，單純寫 doctype html 就好了。

### #11, 12, 13, 14

head 裡面常常用到這些標籤，title 是瀏覽器分頁上顯示的標題，script js，link 是外連的 css 檔案… blah。常用的就這些。
比較特別的是 meta，是沒有 close tag 的 tag，比方說 charset utf8，中文網頁沒有宣告這一行的話，編碼… blah。tag 裡面一個空白接一個英文字，這就是這個 tag 的屬性 attribute，寫法是(名稱)="(值)"。
head 還可以做 seo，像是 facebook 的 open graph，就是從裡面拉資料出來。
body 裡面常用的標籤是這些，他們的命名其實都是有意思的，h1 是 header 1，p 是 paragraph，最有爭議的是 img 是 image，當初有人提出用 img 代表圖片時，很多人吵很久，說為什麼不用 pic、photo…吵很久以後，網頁圈跟 g0v 一樣先做先贏，所以最後就… XD
a 連結，原本意思是 anchor，錨點。本來的作用是可以跳到一頁裡面的特定地方，最當初是這個用意。後來被廣泛應用在超連結。
ul 跟 ol 是 unordered list, ordered list。table 是表格。
早期的概念其實沒有 css，但 html 本身並不豐富，要怎麼排版呢？就有人想出用 table 排版的方法，可以做出在構圖上很複雜的東西。現在覺得是惡夢，但當初只有這種作法。
後來的 div 跟 span 是有 css 以後才有人提出的。
後面幾個是最近 html 5 以後才有的標籤。
到底可以用哪些標籤？可以去 mdn (mozilla dev network) 查。
(為了連 mdn )
直接進入練習時間。
有網路的話可以去這幾個不同的網站，可以線上直接寫 html /  css / js
plunker, codepen, jsfiddle, jsbin

15:35 成功打開 mdn～
html element ref, attribute ref
常用的attr簡介
打開 codepen -
解釋 haml 跟 jade，因為 html 要一直寫開關標籤很煩，所以……但大家可以不用那麼早知道。

15:39
學網頁的過程跟學習語言類似…早期要記一些東西

html 比較單調，直接標籤上去會變成黑白的單調文字頁，但是大家現在看到很多變化的網頁，要怎麼做到呢？就是用 css。css 中英文就這樣寫…是一個描述性語言。
html 也是描述性，兩者不同在於，css 每個都是一個 rule，代表顏色大小輕重等，
解釋 css 語法，冒號分號… balh
光這樣寫不會對 html 產生影響，你要用 selector 指定他影響的 element，裡面寫的規則就是在說要對這個元素做什麼事情。至於這個 selector 怎麼選擇呢？
（打開 mdn css reference）常用的有 background color、border…

每個原素有兩個重要屬性，一個是 id，一個是 class，id identity 是唯一的，一個 html 裡面只有一個人元素能叫這個 id。class 是類別，一群相同 group 的元素都會套用到這個 class 裡的 css，一個元素可以有很多個 class，用空白分開就好。class 在 css 裡面是 . 開頭，id 是 # 開頭。
css rule 後面的會蓋掉前面的。
html 之所以要有 < > 這些語法，適用來標註結構化…
attribute 屬性，（mdn attr ref)

(chrome debug tool)
:hover pseudo selector
可以在 cdt 裡面直接改東西

可以在 cdt 的 network 裡面看那些檔案是怎麼載入進來的，還有每個檔案的花費時間。
如果 10 秒內沒有回應，表示網頁真的太慢，loading 時間是分秒必爭的。這裡可以看哪些檔案拖慢 loading 速度。
cookie 是存一些資料在本地端…
有些網頁鎖右鍵，但在 cdt 裡面這是沒有用的，可以直接存圖跟找影片串流的原始連結 *grin
timeline 做 performance 研究
profiling... blah
resources > cookies，可以看在本地端存了哪些資料
console：原本只知道會噴錯誤，後來在 Y! hack 才知道可以在這裡呼叫一些既定的 js obj，或者會自動完成 blah，例如 window.document 可以看到整份的 source，window.location 可以看這個網址的 func 跟 list ...
element


## 教學松海報及視覺概念

by tuiry++ (CC By 4.0) 下載 [.psd 檔](https://drive.google.com/file/d/0ByIhLWSAeA3gR3JrWXN3QmpYYmc/edit?usp=sharing)
設計概念：被推坑教學松隕石坑的臉紅紅 ly，帶著挖坑鏟和教材歡樂飛舞～～～（好像還有透明發光的小鼠？）
> 沒錯沒錯~~~是兩隻小老鼠唷~~~
> [name=Tuiry H]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d7908c1dde42557cb0389ac628bfc416)
## 心得&回饋

pipi：很謝謝ly老師的講解把我好幾年前的回憶給找了回來，希望下次能繼續參與！
NewCliCker： 今天超感謝 ly 老師的 HTML + CSS 教學，精闢入理，深入淺出，讓不是資訊背景的人也能輕鬆上手，而且還提供了完整的 Reference 給需要深入查閱的學生參考 :thumbsup:
ipa: 感謝助教 jimmy 協助我卡關一陣子的基礎問題。上課氣氛比較容易把卡關問題解決！ly 準備的教材也讓我重新複習一下基本觀念 :100:
moon: 謝謝ly老師還有我細心強大的米奧助教，抱病一直為我講解真的是太敬業了（哭，感覺在大家的協助下真的可以無痛獲得新技能！！教材也好棒好容易懂！
Summit: 感謝 ly老師 & brecht 助教大大～說實話國中玩過一陣 Dreamweaver跟flash之後就沒碰過網頁了xDD 希望把 HTML/CSS 摸熟之後朝 jQuery & D3.js 出發！
> 我也是學dreamweaver & flash的耶，上次很艱困得生出一個網頁被說dreamweaver幾年沒用了，害我覺得自己好GOV.....XDDDD
> [name=Moon C]

> XDDDD
> [name=Summit S]


## 庶務討論


本次報名未到
- 助教 x1 - 想報學員報不到於是報了助教，行前才嚇跑（？）
> 本來我是想用這招報助教的啊。但最後很認份的沒按下報名鍵，乖乖在IRC看直播了XD
> [name=A-Han L]

- 學員 x1 - 不認識的
可能的解決方式
- 報名人初步篩選，e.g. 確認有參與社群或有人認識，事前可以聯絡得到，當天不會人間蒸發

組隊方式
- 上線跟下線自己橋好成一隊（最理想！）
- 其他人：主辦單位視個人狀況分配
    - 需要有報名人的基本背景資料，包括來自哪些領域、做過哪些專案、擅長哪些技術…等，才能配得妙 XD



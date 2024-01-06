---
title: "2013 Yahoo Hack Taiwan 揪團"
tags: hackpad
---

# 2013 Yahoo Hack Taiwan 揪團

> [點此觀看原始內容](https://g0v.hackpad.tw/mJdAOpjEhqh)

> 零時政府第 τ 次雅黑灣黑客松
> [name=Audrey T]

> [http://survey.bnext.com.tw/events/2013yahoo/index.html](http://survey.bnext.com.tw/events/2013yahoo/index.html)
> [name=Audrey T]


## 已報名隊伍


### g1v - 立院組

- clkao
- etblue (以設計師名義)
- yhsiang
- tkirby

- [x] 預計參賽作品(可以亂寫)(150字以內):
- [x] 團隊開發經驗(不能亂寫)(作品網站連結):
- [x] 過去是否用過 Yahoo開放API或其他開放API？如果有，請說明使用了哪些功能?
- [x] 過去是否用過台北市政府公開資訊? 如果有，請說明使用了哪些資料?
最常使用的開發語言和工具為何？C/C++ C# Ruby Python PHP Perl Scheme Lisp Haskell Node.js R Scala JavaScript CoffeeScript LiveScript CSS SASS Compass Bootstrap Plack RoR Angular.js D3.js Django GWT Android iOS AWS Heroku MapReduce Debian Ubuntu FreeBSD PostgreSQL Nginx Redis MongoDB Firebase Git GitHub Illustrator InDesign Photoshop Fireworks SublimeText2 Fire.app AfterEffect

### g4v - 動民主組

- pm5 (以設計師名義)
- ttcat
- CindyLinz
- tkalu

預計參賽作品(可以亂寫):
團隊開發經驗(不能亂寫):


### g9v (滿)

- ronnywang
- muyeh
> 滿的意思是？就已經爆滿了！
> [name=Jimmy H]

> Jimmy可以加入g4v，我只是人頭
> [name=ipa c]


預計參賽作品(可以亂寫):
團隊開發經驗(不能亂寫):


### ?（滿）

- iamblue
- ???
- ???
- yuting Liu

預計參賽作品(可以亂寫):


團隊開發經驗(不能亂寫):
我....我們只會nodejs和angularjs

### g0.0v 萌典團 (已報名)

- au
- miau715
- poga
- caasi

預計參賽作品(可以亂寫)(150字以內):
萌典網站及 App 以教育部辭典與創用CC授權的公開資料集為基礎，共收錄十六萬筆國語、兩萬筆台語、一萬四千筆客語條目，常用字詞亦附上筆順動畫及真人發音。
本次黑客松預計將拓展萌典的 API 以支援 oEmbed 協定，並在行動裝置上提供楷書、注音拼音直橫混排、以及整合其他字音字型相關應用。

團隊開發經驗(不能亂寫)(作品網站連結):www.moedict.tw
最常使用的開發語言和工具為何？
C/C++ Ruby Python PHP Perl Haskell Node.js ActionScript Flex JavaScript CoffeeScript LiveScript CSS SASS Compass Bootstrap Plack Angular.js D3.js Drupal Android iOS AWS Debian Ubuntu FreeBSD MySQL SQLite PostgreSQL Nginx Redis MongoDB Firebase Git GitHub Vim OmniGraffle Glyph.app FontForge Audacity Audition PremierePro Photoshop Illustrator SublimeText Fire.app
Ruby JavaScript C#
JavaScript HTML CSS

### g0_ov 動民主補血團？

- ~pm5~ (跑去 g4v了)
- jimyhuang？
> \+ ttcat 影分身
> [name=ET B]

> \+ yhsiang 影分身
> [name=ET B]

> \+ tkirby 影分身
> [name=ET B]


### 潛在下線


- [x] tuiry：光速插畫家，週六要值班無法參加 QQ ~週六下午可能會離開一下，目前只有桌機，到現場協作的話需借用筆電~
- [ ] evenwu：裝置藝術家（尚未邀請）
- [x] miau715：網頁全端設計師（尚未邀請(其實 au 有私推邀請(原來如此XD(但是ET可以補推啊(夾擊！(已夾擊(已擊落(\\o/)))))))）
- [x] hlb, racklin, kcwu: 遠端參加
- [x] 鴨七：（邀請中（已失敗））
- [ ] 缺電腦 op 可以協助準備 (假設 op 公司 team 有上的話..)


\-\-\-\-

10/3 截止
Goal: 列出各種 g0v project 裡頭，覺得可以在 24hr 內完成的「單一 component」，讓大家挑選來作為 yahoo hackday 的題目，順便揪團。

揪團方式：再有興趣的主題下面簽名，自行搶隊員

可以盡量選擇具有互動性，而不只是呈現資料的主題

## 立院相關


ivod player
並列質詢片段與全影片（因為官員報告會在質詢之前，沒有單一片段）。
- 提供單主題各立委表現 PK (user feedback)
- 讓 user 做公報 timecode link

議案追蹤
單法案的追蹤，以 user 追蹤數量顯示各委員會中

法案草擬器
從法規資料庫取出現有條文、提供共同編修、討論。輸出成立法院使用的正式格式、讓其他人連署附議

立委臉部辨識（純挖坑...）
用ffmpeg把ivod的影片切成image frame
用[人臉分析](http://blog.mashape.com/post/53379410412/list-of-50-face-detection-recognition-apis)，把影片做出人臉的index
做一個介面，讓編輯可以標示該臉的人物
做一個頁面，讓網頁把人臉/人名 -\> ivod的index建立完成

昨天clkao提到與soundcloud類似的東西，但是需要先產生一個webform
可以把聲音的波紋對應到影格甚至是文字稿，有些協商聲音就可以看的出來
> 聲紋應該會比臉部辨識準確！good idea
> [name=Jimmy H]


23:17 < yhsiang> clkaoud: mapping劇本 跟 質詢 -> 用立委臉產生 電影海報
23:30 < yhsiang> 把質詢混搭電影trailer + 電影海報 ...

## open data 系列

> 既然主辦單位說盡量使用 open api……那就來弄 open data 好了（跳躍式思考） XD
> [name=ET B]






## 動民主相關


tkirby 的 0.5？
yhsiang 的 1.0 變成 mobile 版？
pm5 的 irc 整合
想完成tkirby提的custom font idea
同步表決立法院正在進行的法䅁
給立委們開帳號，把她們的發言同步到動民主上，給大家自由委任，最後看表決結果跟實際的差多少


## others


name: 臉書小幫手（？沒創意）

issues to slove:
- facebook 舊的訊息幾乎很難再找到，雖然現在有搜尋外掛（QSearch），但還是必須要「記得」或「知道」有這哪些「關鍵字」才可以。
- 大部份的 NGO 現在都轉向用 FB fan page 來經營自己的社群、發佈訊息、轉流量到網站，但是 fan page 只允許 1 則ㄒ訊息置頂。
- 想關注的 Facebook 訊息很多，想用自己的 tag 來為自己整理
- 某些 fb 舊的訊息、曾經有過的好的討論、組織這陣子的重要訊息、Must read etc.. 如果可以有一個 important timeline 就太好了。

functions:
- 結合新的 fb embed 單篇 post 功能，把所有想要記錄下來的 post 記錄在服務端
- 每篇 post 被記錄下來的，可以用 timeline 或瀑布呈現
- 可自訂自己的分類, tag, 和移動調整每篇 item 的順序
- 有分類（資料夾） / 或 tag 瀏覽畫面（每個頁面有獨立網址，可設定該頁面 public/locked）
- 瀏覽器外掛：
    - chrome/ff
    - facebook 瀏覽時，like share follow 後面增加一個按鈕：pin/star/??? this
    - 會出現 tooltip 可以輸入 tags or 點掉（已經儲存）
- Facebook APP：
    - 粉絲團可以建立自己的帳號後，把自己記錄下來的 posts 頁面，變成 Facebook APP add 到粉絲團的按鈕：e.g 綠盟的重要文章、新手必讀、熱門文章
- 除了頁面檢視、facebook app 檢視，也開放 embed / api 讓組織套用到自己的網頁上，讓網頁的瀏覽者同時看到組織最熱門/最想要 promote 的 posts.
- 每篇 post 可以隱藏 / 刪除。
- 可在服務頁面手動增加 posts
- 簡單的 search engine
- 未來：可開放 share 共同編輯某個分類/頁面 etc..

Features:
- 個人使用時會變成自己的 facebook 專用書籤、粉絲團使用時可以變成粉絲團文章精華區
- 方便同時追蹤好幾篇正在關注的訊息、或是即時追蹤不同粉絲團 posts like/share 的變化（因為每個 item 就是 embed facebook post 可以留言、按讚、分享 etc）
- 可以變成官方網站上面的 Facebook 專區，取代原本的 facebook 提供沒什麼用處的爛 fan page plugin.

有興趣者：ttcat



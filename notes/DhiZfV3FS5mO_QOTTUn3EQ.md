---
title: "11/23 萌典松 moed1ct"
tags: event,moedict,hackpad
---

# 11/23 萌典松 moed1ct

> [點此觀看原始內容](https://g0v.hackpad.tw/qOZ7FM72G10)


### 活動紀錄

- [播放清單](https://www.youtube.com/playlist?list=PLIWDjrXDaTHmBESpo0HrD8A4eNP-bqkp3)共 14 影片，50 分鐘，含開場、各專案報告、萌典團隊與教育部交流成果報告、以及結語提及的萌典松未來計畫。
- [新聞報導](http://http:­//www.cdnews.com.tw/cdnews_site/docDetail.jsp?coluid=121&doc­id=102545719)同日參與辭典啄木鳥茶會與教育部交流。

### 參考資料

美麗島黑客松的簡報：[**http://tinyurl.com/hackath5n-moedict**](http://tinyurl.com/hackath5n-moedict)
美麗島黑客松的待辦事項：[https://g0v.hackpad.com/tDx3D5FZya5](https://g0v.hackpad.com/tDx3D5FZya5)

### 有想實作的點子、想法請直接列在這裡：

- 射擊遊戲，飛機子彈敵人跟怪物都是文字，要懂文字的意義才能有效殺敵。　參：擊破傳
> 續上　提供[2002年不成熟的遊戲企劃書](https://drive.google.com/folderview?id=0B6ASgY1GMSOhWnZsdVk5UnFZdjg)
> [name=Michael_Li]

- 原創遊戲／要有中國（文字）風味／例如可以參考日本花札（動畫夏日大作戰呈現很好）
> 花札[教學](http://blog.yam.com/rodsiza/article/28608094)[程式](http://www.gamedesign.jp/flash/hanafuda/hanafuda.html)[＜－－（維基百科）遊戲](https://zh.wikipedia.org/wiki/%E6%B8%B8%E6%88%8F)[中國傳統遊戲列表](https://zh.wikipedia.org/wiki/%E4%B8%AD%E5%9C%8B%E5%82%B3%E7%B5%B1%E9%81%8A%E6%88%B2%E5%88%97%E8%A1%A8)
> [name=Michael_Li]

> 花札的概念似乎蠻簡單，但是有蠻容易表達出【風味】的?  又讓我想到記字詞的卡片。
> [name=Ted C]

> 以上都是把萌典從工具，轉變成玩具，以期促進接觸人口增加。
> [name=Michael_Li]

- [http://direct.moedict.tw/lab/moe/ivod/frame.html](http://direct.moedict.tw/lab/moe/ivod/frame.html)
> 被藍白拖砸到，螢幕會裂開
> [name=小蟹 李]

> 被藍白拖砸到的人會淤青
> [name=小蟹 李]

- 萌典 x 查字典
> 想查某個字，卻發現不會念打不出來(因為以前念法都是錯的)，但又不會注音以外的輸入法，這時可以提供查字典的功能
> [name=Wen-Chi C]

    - ~部首查詢：目前每個字都有註明是哪個部首+幾畫，例如「臺：至+8=14」，由此反推，系統先提供部首清單供點選，再輸入筆畫數，之後就顯示搜尋結果清單供點選。~
> 阿咧，部首查詢已經有了[https://www.moedict.tw/#~@](https://www.moedict.tw/#~@)
> [name=Wen-Chi C]

    - 筆順查詢：提供九宮格讓USER直接畫出來，再加以對照~應該很炫，但變成圖形識別，難度好像會很高...
    - 永字八法：拿這八種筆畫元件拼出來再去查~感覺上應該可以做成遊戲給小朋友邊玩邊學認字
        [http://upload.wikimedia.org/wikipedia/commons/e/e2/8\_Strokes\_of\_Han\_Characters.svg](http://upload.wikimedia.org/wikipedia/commons/e/e2/8_Strokes_of_Han_Characters.svg)
- 筆順資料
    -  清理 zh-stroke-data 的根目錄
        [g0v/zh stroke data#2](https://github.com/g0v/zh-stroke-data/issues/2)
    -  用圖畫出 path
        [g0v/zh stroke data#5](https://github.com/g0v/zh-stroke-data/issues/5)
    -  把 Makefile 整理好
        [g0v/zh stroke data#3](https://github.com/g0v/zh-stroke-data/issues/3)
    -  看看 triangulate 後的字能不能用在 box2d 上
        [g0v/zh stroke data#4](https://github.com/g0v/zh-stroke-data/issues/4)
- 筆順資料 x ivod.ly.g0v.tw
    -  希望 ivod 可以有 postMessage APIs
        [g0v/ivod.ly.g0v.tw#5](https://github.com/g0v/ivod.ly.g0v.tw/issues/5)
> 最近有再研究postMessage了 orz
> [name=Yuan C]

> 感謝！還想著大概要自己填這坑了。
> [name=caasi H]

- 萌典 x 零時藝術家
    - 人類已經無法阻止萌典了之成人版/字宙版/鋼彈版萌典娘插畫——一起來畫出你心目中的萌典娘吧！
    - 人類已經無法阻止萌典了之萌典主題曲創作
    - 其他非萌典類的見 [https://plus.google.c](https://plus.google.c)  [om/u/0/+ETBlue/posts/6cRgWxL1rGJ](https://plus.google.com/u/0/+ETBlue/posts/6cRgWxL1rGJ)
- 3du.tw 首頁
    - 做一個簡單的 landing page，除了各平台版本的萌典之外，也讓比較難找到/安裝的平台（如 yllan 的 OSX Dictionary）、API docs，和新的應用可以浮現。repo: [https://github.com/g0v/3du.tw](https://github.com/g0v/3du.tw)
    - 應用
> 先憑印象亂寫，正確名稱之後要校正一下 XD
> [name=ET B]

        - 萌典本人（查字典用的）
            - web  osx android ios fxos win8 meego chrome-extension
        - 萌典啄木鳥
            - web
        - 萌典方塊遊戲
            - 詞彙版
                - web
            - 注音版
                - web
            - 部件版
                - web
        - 對撞機
            - web [https://www.moedict.tw/lab/lhc/?字](https://www.moedict.tw/lab/lhc/?字)
        - 國字測繪局
            - web
        - 聯想詞 [https://www.moedict.tw/lab/tmuse/](https://www.moedict.tw/lab/tmuse/?字)[?字](https://www.moedict.tw/lab/tmuse/?字)
            - web
        - 形似音似
            - web [https://www.moedict.tw/lab/ball/](https://www.moedict.tw/lab/ball/)
    - 介面
        - 連往 [3du.tw](https://g0v.hackpad.tw/ZNwaun62BP4) hackpad，或是連往 [http://apiary.io/](http://apiary.io/)  這類 API server

    - 資料
        - 連往 [http://data.g0v.tw/tags/3du/](http://data.g0v.tw/tags/3du/) ...也許稍微 style 一下。
            - -\> 待填的坑：列出已經轉換過的資料
    - 源碼
        - 連往 [http://hack.g0v.tw/project#3du](http://hack.g0v.tw/project#3du) （理論上將來要會動）
- 萌典 x 正常人中心
    - 包括授權中心跟軟體中心，專門放一些正常人看得懂、可以直接使用的東西
    - 授權中心裡包含萌典及各 g0v 專案的 logo、吉祥物等
    - 軟體中心裡包含萌典及各 g0v 專案的應用
    - 雛形 [http://g0v.github.io/moc-license-center](http://g0v.github.io/moc-license-center)
- cite4Share
    - 概念: 類似ettoday 會附上原網址, 想說有沒有辦法複製以後, 自動產生網址並且自帶#id，使得別人可以輕易地做quotation, 這邊可以分成兩種, ctrl+c 變成產生網址, 或者 ctrl+c 一樣是複製文字,另外用ctrl+C 之類的產生網址, 讓使用者自由選擇
    - 使用描述: 滑鼠標記一段文字 自動產生link, 別人貼上link 會跳到這個div 並且highlight這段文字
    - 分成angular module\[1\] 或者 chrome extension\[2\]
        - 網站開發者使用angular module即可簡單使用此功能 (也可以寫jQuery plugin)
        - 沒有安裝這功能的網站, 可以利用browser extension達到相同功能
    - 預計使用javascript + firebase 來達成
- pokopong x moedict
    - 靈感來自於 pokopong
    - 遊戲目的：加強字詞熟悉和字詞聯想
    - pokopong遊戲方式:
        - 截圖:[http://www.appguru.com.tw/ck-upload/555/images/pokopang.jpg](http://www.appguru.com.tw/ck-upload/555/images/pokopang.jpg)
        - 拼圖連線遊戲
        - 有小炸彈，大炸彈，彩虹炸彈和combo模式
        - 串聯消除方塊造成怪獸傷害
        - 最低要求三個方塊
    - moepong遊戲方式
        - 將拼圖改成字或者是有背景圖塊的字(初階模式?)
        - 有相同部首(或部件)字的可以串聯消除
            - 某些部首或部件可以引發特殊效果，例如"火"燒，"水"淹
            - 更進階可以玩五行串聯: 火燒木部件的字，水可以滅火部件字，金->木->水->火->土->金
        - 或者可以連成有意義詞的字組例如：一條龍或我是一條龍?
> 這邊的有趣玩法還沒想到
> [name=Yuan C]

        - 串聯消除字句造成立委傷害(疑，怎麼又是立院影城 :P)
- linepop x moedict
    - 靈感來自於line pop ( 或是zookeeper類型遊戲)
    - 遊戲目的：字詞聯想
    - linepop遊戲方式
        - 截圖:[https://lh4.ggpht.com/tzRaE2dIiMP4EfAp9q0b-V9h54q9O6yL6cN7ph3PBxiOg85NMiC7uulBESCO7euiqsI=h900-rw](https://lh4.ggpht.com/tzRaE2dIiMP4EfAp9q0b-V9h54q9O6yL6cN7ph3PBxiOg85NMiC7uulBESCO7euiqsI=h900-rw)
        - 移動圖案達成連線，只能上下左右
        - 最低要求也是三個圖案成一直線
    - moekeeper
        - 將圖案都換成字
        - 只能上下左右移動字，能連成有意義的詞就消除
        - 單人遊玩
            - 特殊效果
> 可以參考上面的部件玩法但是覺得都一樣又不好，只好努力想新的玩法
> [name=Yuan C]

        - 多人對戰
            - 比誰連線的詞多
- 女書支援
    - 這邊允許我先做命名，如果萌典真的能支援女書，女書部份我想稱為"婓典"
        - 婓可以拆成非和女，非的象形有違背的意思，可取之與世道主流違背之意，女可以取其女書。非女也可以想成非男亦非女不應該以性別做尊卑，甚至又有這不是傳統女書的非女典，加之婓又有女神的意思，因為可以援引的意思相當豐富，故命名為婓典。
> yhsiang:所以萌典也要支援女書 XD
> [name=Yuan C]

> au:樓上要幫忙連絡中南民族大學團隊嗎？ ([http://www.arocmag.com/ar](http://www.arocmag.com/arocmag/ch/reader/view_abstract.aspx?file_no=201209094)[ocmag/ch/reader/view\_abstract.aspx?file\_no=201209094](http://www.arocmag.com/arocmag/ch/reader/view_abstract.aspx?file_no=201209094) ) 如果能說服他們 Open License 字型，可以挑一塊 PUA 來做。
> [name=Yuan C]

> yhsiang:原來還有這個團隊 剛剛看了好多source都沒有字表之類的東西可以下載 ...是可以聯絡看看 不確定自己能否說服對方 XD
> [name=Yuan C]

> au:字表在 [http://std.dkuug.dk/jtc1/sc2/wg2/docs/n4376.pdf](http://std.dkuug.dk/jtc1/sc2/wg2/docs/n4376.pdf) 。之前的 U+1B000 在 Unicode 6.0 已經挪做古代片假名用，所以目前女書重新在 U+1B100 提了一次，高品質的 corpus + font 或許有幫助。
> [name=Yuan C]

> 還有女書這文字!? 真是增長見聞了。這個讓我想到，越文也有一種字體叫喃字。[http://zh.wikipedia.org/wiki/%E5%96%83%E5%AD%97](http://zh.wikipedia.org/wiki/%E5%96%83%E5%AD%97)。不過就我所知當初無法普及、通行。
> [name=Ted C]

    寄信給作者了，靜候佳音。

也可以到 [https://github.com/audreyt/moedict-webkit/issues](https://github.com/audreyt/moedict-webkit/issues) 開新的 issue。

### 活動資訊

**【時間地點】**2013/11/23(星期六) 1100~2000
睡不著咖啡館 地址：台北市大安區泰順街60巷8號B1

**【活動形式】**如果你期待看到某些萌典的功能，或是想運用更多教育部的公開資料，又或是對 g0v.tw 的各專案有興趣，都歡迎自由參加！

另外，當天 2pm~4pm 在附近的和平東路一段179號11F，有國教院辭典維護團隊的啄木鳥活動茶會，有興趣的人(最多 4 位)也可以從萌典松走去晃晃。

### 硬體支援

- 冷光燈
    - x3 - ipa
- 延長線
    - x2 - jimyhuang
    -


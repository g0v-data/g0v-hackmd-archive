---
title: "千影(chikage) - HTML5 GlyphWiki Editor"
tags: hackpad
---

# 千影(chikage) - HTML5 GlyphWiki Editor

> [點此觀看原始內容](https://g0v.hackpad.tw/GTzs0q6jKyQ)


## 專案簡介


### 緣由

    GlyphWiki.org 目前39萬個中文字型，是花園字型(Hanazono Font) 的底層資料庫，唯其字型是採用日本規範。

    基於 Glyphwiki 現有的龐大部件庫(光一個木字就有數十種變體)，以及Kage 字形產生引擎，打造一個符合台灣字形規範的群眾造字/調字平台。

### 要解決的問題

    一）動態組字 (從IDS產生字形) 的美觀度問題。
    二）GlyphWiki 提供的編輯器是以Flash開發，改為HTML5 之後可在更多平台使用。
    三）缺字IDS及組字資料交換平台，讓各種字典辭書的缺字有統一的交換碼。

### 預定使用者

    一）古文字、古文獻相關研究。（e.g. 合文、減字譜）
    二）字形設計者
    三）CJK電子書編輯者
    四）需要造新字表達新概念的場合。(如新的化學元素)

### 可能的延伸功能


#### 蒐集未收錄到Unicode裡的字

- 哪些字被造出來
- 出自何處
- 整理後可以提交Unicode Consortium/ISO IEC JTC1 SC2...IRG

#### 整理成IVD

即Unicode Consortium的異體字資料庫，現在都是日文有註冊，中文只有香港要提出港台用字不同的異體字庫。台灣目前好像還沒有要做這件事的計劃。

### 預定功能

（成品要有哪些功能來滿足上述使用情境）

### 現有類似專案

- GlyphWiki 的 [Flash 編輯器](http://glyphwiki.org/wiki/u840c?action=edit)
- Prior art: 丞宏的 [han3\_ji7\_tsoo1_kian3](https://github.com/sih4sing5hong5/han3_ji7_tsoo1_kian3) （漢字組建專案）
- [GlyphWiki Drawfont Tool](http://sourceforge.net/projects/gwdrawfonttool/#screenshots)
- [極限社區 \- KAGE 服務器做好了](http://bbs.themex.net/showthread.php?t=16879740)
- [漢文博士](http://blog.yam.com/ebag/article/60218630) (無造字功能，字形metadata很完整)

### 相關專案

- [GlyphWiki](http://glyphwiki.org/)
- [KAGE/engine](http://fonts.jp/engine/) GlyphWiki 使用的組字引擎
    - [CHISE project](http://www.kanji.zinbun.kyoto-u.ac.jp/projects/chise/)
        最下面有 git 位址，要使用 kage 可以下`git clone [http://git.chise.org/git/chise/kage.git](http://git.chise.org/git/chise/kage.git)`
- [花園フォント](http://ja.wikipedia.org/wiki/%E8%8A%B1%E5%9C%92%E3%83%95%E3%82%A9%E3%83%B3%E3%83%88)
- [idskage](https://github.com/g0v/idskage) Generate Kage glyph format from IDS
- [kage.json](https://github.com/g0v/kage.json) 將 KAGE system 的檔案格式轉換成 JSON ，方便 HTML5 工具使用
- [篆刻網](http://www.mebag.com/) 站主曾向上地宏一先生當面請益缺字處理的相關問題，這是他的 [blog](http://blog.yam.com/ebag/article/88606293) 。主要完成的七千多個缺字，收錄在「[引得市](http://www.mebag.com/index/)」的「[古文字缺字資料庫](http://www.mebag.com/index/quezi/list.asp)」，已經完成的缺字可以嘗試轉換直接取用，不需重複再造字。
- [在「glyphwiki」缺字製作的錄影記錄連結](https://youtu.be/vFJN4kszg9k)。

### 參考資料

- [GlyphWiki AFDKO Font Generator](https://github.com/kawabata/glyphwiki-afdko) 介紹 KAGE system
- [GlyphWiki: Shareable Glyph Database System for Chinese Characters](http://fonts.jp/kamichi/1112hk.pdf)
    投影片第七頁解釋了筆畫格式，第九頁解釋了組件格式。
- [GlyphWiki and OpenType: A Collaborative Glyph Development Environment and its Font Exporting System](http://www.atypi.org/type-typography/glyphwiki-a-wiki-based-glyph-design-and-font-production-system.-taichi-kawabata-and-kamichi-koichi)
    第四頁解釋了 name rules 。
- [台語字典缺字列表](https://ethercalc.org/koktai-ids)

### 資源與授權方式

- GlyphWiki 有自己的[授權](http://glyphwiki.org/wiki/GlyphWiki:License)。
- KAGE/engine 是 [GPL](http://git.chise.org/gitweb/?p=chise/kage.git;a=blob_plain;f=engine/COPYING;hb=HEAD) 。
- [kage.json](https://github.com/g0v/kage.json) 是 [CC0-1.0](https://creativecommons.org/publicdomain/zero/1.0/) 。

### 專案目前狀態

- [x] kage => JSON: [kage.json](https://github.com/g0v/kage.json)
- [ ] JSON => kage
- [x] API server
- [ ] HTML5 editor
####

### 利益揭露

提供造字服務的公司。

## 徵求協作者


發起人/拋磚人：
- [ ] NeedsWritingSystemExperts: 需要文字學家，或對異體字有研究的人
- [ ] NeedsDesigner: 需要介面設計
    - [ ] Glyph Editor
    - [ ] Website
- [ ] NeedsData: 需要資料（擷取、清理）
    - [ ] KAGE <=> JSON
- [ ] NeedsTech: 需要技術支援（程式、架站 etc)
    - [x] API server
    - [ ] 把資料放在 firebase 等服務上的可能性
- [ ] NeedsProcess: 需要幫忙設計作業流程
    - [ ] dump.tar.gz => KAGE => JSON
- [ ] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡
- [x] 連絡陳信良先生，詢問改良意見 (曾在Glyphwiki editor 造過數千字)


## 實作細節（非技術背景可跳填）


### 協作工具

- github repo：[https://github.com/g0v/chikage](https://github.com/g0v/chikage)
- hackfoldr 工作資料夾網址：
- google drive 共用資料夾網址：

### 進度與 to-do

- [ ] product planning（recommanded procedure from justin lee / 李易修）
    - [ ] strategy
    - [ ] scope
    - [ ] structure
    - [ ] wireframe
    - [ ] visual
- [ ] web front-end
- [ ] web back-end
- [ ] ui / visual design

### GlyphWiki  Editor 功能簡介

[http://glyphwiki.org/wiki/GlyphWiki:GlyphDesignMethod](http://glyphwiki.org/wiki/GlyphWiki:GlyphDesignMethod) 官方英文簡介

[http://glyphwiki.org/wiki/u65e5?action=edit](http://glyphwiki.org/wiki/u65e5?action=edit) 末級部件  點 「専用エディタで編集する」
進入後點英文介面。
筆劃編輯：
    點一個筆劃(日第一豎筆)，可以選筆劃類別：(straight line, curve, bend line ,etc)
    每種筆劃有不同的head 和 tail 可選。
    head/tail 設定決定了筆劃的修飾(起筆、收筆)以及和其他筆劃的連繫。
字框編輯：
    [http://glyphwiki.org/wiki/u840c?action=edit](http://glyphwiki.org/wiki/u840c?action=edit)  複合部件 點 「専用エディタで編集する」

其他功能
按 Freedraw 可以用手繪方式寫字，系統會自動產生合適的筆劃。
    實作：應該是用 [Path Simplification](https://www.google.com.tw/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CB4QFjAA&url=http%3A%2F%2Fpaperjs.org%2Fexamples%2Fpath-simplification%2F&ei=5OoxVZaNIYOj8AXhmoCIBA&usg=AFQjCNGLt8Q24Os_ZKsAMxOFbpiThG3DcA&sig2=269BsFjgCkfTo6mb_cdjVQ) ，先把輸入的很多點轉成2~4個控制點。再找出最可能的筆劃。

### 技術規劃

前端：

    [KAGE/engine](http://fonts.jp/engine/) 已經實作了輸出 SVG 的工具， 剎那工坊的 [kzy 專案](https://github.com/ksanaforge/kzy)藉此完成了字型繪製。

    以React撰寫，筆劃新增刪除、類型選取、移動控制點、字框調整、鄰近字選取等介面。將編輯中的字形，交由Kage 產生，繪製到 一個透明底的overlay SVG layer。SVG layer 純顯示編輯結果，不處理事件。

    目前已經可以從server讀取json資料，繪製出單線體。前端已改用ES6撰寫，不用學LiveScript。

    此編輯器必須很容易嵌入，在任何網頁或Web base App看到不夠漂亮的組字時，點一下即可開始編修，結果送回伺服器。

後端：
    glyphid 每筆組字資訊的唯一代碼

    API ：
        1)以Unicode, IDS取得組字資訊，供Kage 於client side 組字。
        2)以Unicode取得所有glyphid (如「木」，取得「木-01」「木-02」。
        3) 以Unicode 取得 IDS (中研院or CHISE or other)
        4)以glyphid取得所有使用它的glyphid。例：「木-01」得「杉」「木-02」得「李」 (豎木旁和李字的木豎筆較短)
        4)寫入調整組字資訊。glyphid and glyphdata
        6)取得組字編修記錄。(contributor)
        7)以Unicode, IDS 取得的應用例(如古書某一頁)。

    目前有兩個可能的方向，一是在 server 展開所有的 link （99 開頭的部件），成末級部件，編輯器只要 request 一次就好。或者在編輯器 pipeline request ，減少 request 次數，例如 `[https://server/glyph/?json](https://server/glyph/?json)\[\]=u8279-03&json\[\]=u660e` 。

    database engine: 未決定。(Redis ? LY 則建議 [http://www.rethinkdb.com/](http://www.rethinkdb.com/)  )
    目前已經用 redis 先弄了一個：[https://github.com/g0v/kage.json/commit/4c3a8f064497e9f325f955267bfd62b88b161283](https://github.com/g0v/kage.json/commit/4c3a8f064497e9f325f955267bfd62b88b161283)

### 線條種類與頭尾形狀

- stroke types
    - straight line 2pts, 1
        - free, 0
            - free 1:0:0
            - connect(h) 1:0:2
            - connect(v) 1:0:32
            - L-btm corner 1:0:13
            - R-btm corner 1:0:23
            - slash left 1:0:4
            - L-btm(G/T) 1:0:313
        - connect(h), 2
            - free 1:2:0
            - connect(h) 1:2:2
            - connect(v) 1:2:32 illegal
            - L-btm corner 1:2:13 illegal
            - R-btm corner 1:2:32 illegal
            - slash left 1:2:4 illegal
            - L-btm(G/T) 1:2:313 illegal
        - connect(v)
            - free 1:32:0
            - connect(h) 1:32:2 illegal
            - connect(v) 1:32:32
            - L-btm corner 1:32:13
            - R-btm corner 1:32:23
            - slash left 1:32:4
            - L-btm(G/T) 1:32:313
        - L-top corner, 12
            - free 1:12:0
            - connect(h) 1:12:2 illegal
            - connect(v) 1:12:32
            - L-btm corner 1:12:13
            - R-btm corner 1:12:23
            - slash left 1:12:4 illegal
            - L-btm(G/T) 1:12:313
        - R-top corner
            - free 1:22:0
            - connect(h) 1:22:2 illegal
            - connect(v) 1:22:32
            - L-btm corner 1:22:13
            - R-btm corner 1:22:23
            - slash left 1:22:4
            - L-btm(G/T) 1:22:313
    - curve 3pts, 2
        - free
            - slash left 2:0:7
            - slash right 2:0:0 illegal
            - stop for dot 2:0:8 illegal
            - hook left 2:0:4 illegal
            - hook right 2:0:5
        - connect, 32
            - slash left 2:32:7
            - slash right 2:32:0 illegal
            - stop for dot 2:32:8 illegal
            - hook left 2:32:4
            - hook right 2:32:5
        - L-top corner, 12
            - slash left 2:12:7
            - slash right 2:12:0 illegal
            - stop for dot 2:12:8 illegal
            - hook left 2:12:4 illegal
            - hook right 2:12:5 illegal
        - R-top corner, 22
            - slash left 2:22:7
            - slash right 2:22:0 illegal
            - stop for dot 2:22:8 illegal
            - hook left 2:22:4
            - hook right 2:22:5
        - narrow for dot, 7
            - slash left 2:7:7 illegal
            - slash right 2:7:0
            - stop for dot 2:7:8
            - hook left 2:7:4
            - hook right 2:7:5 illegal
    - bend line 3pts, 3
        - free, 0
            - free 3:0:0
            - hook up 3:0:5
        - connect(v), 32
            - free 3:32:0
            - hook up 3:32:5
        - L-top corner, 12
            - free 3:12:0
            - hook up 3:12:5
        - R-top corner, 22
            - free 3:22:0 illegal
            - hook up 3:22:5
    - OTSU curve 3pts
        - free, 0
            - free 4:0:0
            - hook up 4:0:5
        - R-top corner, 22
            - free 4:22:0
            - hook up 4:22:5
    - complex curve 4pts, 6
        - free, 0
            - slash left 6:0:7 illegal
            - slash right 6:0:0 illegal
            - stop for dot 6:0:8 illegal
            - hook left 6:0:4 illegal
            - hook right 6:0:5
        - connect, 32
            - slash left 6:32:7
            - slash right 6:32:0 illegal
            - stop for dot 6:32:8 illegal
            - hook left 6:32:4
            - hook right 6:32:5
        - L-top corner, 12
            - slash left 6:12:7
            - slash right 6:12:0 illegal
            - stop for dot 6:12:8 illegal
            - hook left 6:12:4 illegal
            - hook right 6:12:5 illegal
        - R-top corner, 22
            - slash left 6:22:7
            - slash right 6:22:0 illegal
            - stop for dot 6:22:8 illegal
            - hook left 6:22:4
            - hook right 6:22:5
        - narrow for dot, 7
            - slash left 6:7:7 illegal
            - slash right 6:7:0
            - stop for dot 6:7:8
            - hook left 6:7:4
            - hook right 6:7:5 illegal
    - vert slash 4pts, 7
        - free, 0
            - slash left 7:0:7
        - connect, 32
            - slash left 7:32:7
        - L-top corner, 12
            - slash left 7:12:7
        - R-top corner, 22
            - slash left 7:22:7 illegal

## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）







---
title: "十一月第⓭次萌典松菸 moed13ct"
tags: moedict,hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/fC9waMmFmnN)


時間：11/14 11am-7:30pm（歡迎遲到早退）
地點：台北市松山文創園區北向一樓[公民廣場](https://g0v.hackpad.com/PDrdUgO6vA6)（信義區光復南路133號）
名額：20 人（[報](http://moe.kktix.cc/events/moedict-11-14)[名](http://moe.kktix.cc/events/moedict-11-14)[頁面](http://moe.kktix.cc/events/moedict-11-14)）
內容：比照之前萌典松，採「併松」模式舉行，歡迎 g0v 各大小專案加萌參加。
費用：採量力而捐、自由贊助方式。如有剩餘，捐給下次黑客松。
活動守則：[https://g0v.io/coc](https://g0v.io/coc)
直播：[https://www.youtube.com/user/g0vTW/live](https://www.youtube.com/user/g0vTW/live)

### 萌典相關開發項目

- 〈國語注音符號手冊〉電子書化 \+ 修正需求 (每個一個 issue)
    - [https://github.com/g0v/bopomofo-standard-gitbook](https://github.com/g0v/bopomofo-standard-gitbook)
    - **原手冊的注音符號尺寸及比例過於~吹毛求疵~，故CLReq有所修正，但細節可能需要進一步討論（如33% → 25%、注音拼式整體改為垂直方向置中等）**
> 「吹毛求疵」改成「主要供印刷使用」？
> [name=Bobby]

    - 需要從 PDF 裡提取 SVG 檔，或從 [EPS](http://www.edu.tw/files/site_content/m0001/juyin/download.htm) 轉換，歡迎幫忙補完。
    - 注音符號「ㄧ」（U+3127）的直橫排問題
        - [Unicode 8.0 Errata](http://www.unicode.org/versions/Unicode8.0.0/erratafixed.html)
        - **由於共用碼位，故決定直、橫排皆以「橫線ㄧ」為主**
            - 並在〈重訂標點符號手冊〉註明連接號用於注音時，使用乙式～
        - **附注：過去曾在橫排時使用「直線ㄧ」，思源黑體中以OpenType功能'hist'來提供取代字形，故兩者都能顯示。**
    - 注音符號「ㄜ」的變體（早期字形）
        - [收字區段討論](http://unicode.org/wg2/docs/n4695-Discussion%20of%202CEF1.pdf)
        - 國音已經沒有的字似乎不用特別提？
        - OK!
    - 方言音符號：這本手冊不處理
- **注音調號（國語注音/方言音）透過OpenType功能的實作：請教育部另開研究案處理。**
    - 研究結果提交W3C i18n作為Group Note建議Browser vendor進行實作。
- 〈重訂標點符號手冊〉電子書化 \+ 修正需求
    - **最後出英文版（至少有名稱，也就是檔名）**
    - [https://github.com/g0v/punctuation-standard-gitbook](https://github.com/g0v/punctuation-standard-gitbook)
    - 避頭點：不添寫。
        - 原手冊只在括號（夾注號）、乙式書名號有避頭尾規定；句號有類似的要求。
    - **書名號/專名號：連續排列時，二個書名號/專名線不得相連。**
        - [http://www.w3schools.com/cssref/playit.asp?filename=playcss_text-decoration-style&preval=wavy](http://www.w3schools.com/cssref/playit.asp?filename=playcss_text-decoration-style&preval=wavy)
    - **刪節號⋯⋯：需列於中線。**
    - **連接號：用於注音時，使用乙式～**
    - **在該手冊中註明Unicode碼位**
    - **希望能使用・ katakana middle dot（U+30FB），提需求發文到Unicode** **Consortium提案**
    - **夾注號與破折號——的字型與輸入法實作問題**
        - **夾注號與破折號不可分斷於兩行**
        - **—，U+2014：兩個連續時使用kern讓其相連**
        - **⸺，U+2E3A：輸入兩個連續U+2014時，以U+2E3A取代**
        - **鼓勵中文字型內含U+2E3A，但目前輸入上仍使用兩個U+2014**
        - **夾注號乙式的禁則處理無法自動化處理**
    - 希望加入著重號、分隔號等，並以附注形式提及其他形式的括號（〔〕【】）
    - 夾注號可否加上別名「括號」？
    - [http://www.edu.tw/files/site_content/M0001/hau/c2.htm](http://www.edu.tw/files/site_content/M0001/hau/c2.htm)

- 聯絡台語小組事項：
    - **《台灣閩南語羅馬字拼音方案・聲調排序與標記位置》陽入聲的技術處理：寫入CLREQ的行間注台語羅馬字中**
    - [http://bobbytung.github.io/TaigiHakkaIdeograph/](http://bobbytung.github.io/TaigiHakkaIdeograph/)
> [Audrey Tang](https://g0v.hackpad.tw/ep/profile/DaKXhWfoD7Q) 是否可以增加一些脈絡？例如會議記錄
> [name=Bobby T]

> 本國語文中文資訊處理專案國語小組第1次會議
> [name=Audrey T]

> 104年10月27日(星期二)下午2時30分至4時20分
> [name=Audrey T]

> 決議：
> [name=Audrey T]

> 一、有關本部既有之國語文成果資料，運用於中文資訊處理時，會議中討論了以下4項需求：
> [name=Audrey T]

> (一)現行注音符號手冊修訂及中文資訊處理。
> [name=Audrey T]

> (二)現行標點符號修訂及中文資訊處理。
> [name=Audrey T]

> (三)標點、注音及其他符號於鍵盤的配置。
> [name=Audrey T]

> (四)中文字樣擴編及資訊應用。
> [name=Audrey T]

> 二、請與會者預為設想解決方案，於下次會議討論。
> [name=Audrey T]

> 三、成果於「教育部語文成果」網站發布時，建議列出網站內機器可讀之資源（例如筆順網裡的「常用國字標準字體表」），獨立成為條目。
> [name=Audrey T]

> got it
> [name=Bobby T]


    - 參考資料：[CLREQ中文排版需求](http://www.w3.org/TR/clreq/)
    - 參考資料：[GB/T 15834-2011 標點符號用法](https://www.dropbox.com/s/y20kngpzvrl5nw3/punctuation.pdf?dl=0)
    - 參考資料：以OpenType實作注音調號位置的嘗試（[中文版計畫@hackpad](https://g0v.hackpad.tw/OpenType-Font-bFFqBpPmcz0)、[英文版文件](https://www.dropbox.com/sh/zurhpcv2ek919cw/AADfOtnnNPow0m6dMGSMhz1-a?dl=0)）
        - <ruby>植<rt>ㄉㄧㆵ͘</rt></ruby>
        -  <ruby>一<rt>ㄧㆵ</rt></ruby>
        - <ruby>二<rt>ㆢㄧ˫</rt></ruby>
| yin entering tone p | ㆴ | U+031B4 | BOPOMOFO FINAL LETTER P |
| --- | --- | --- | --- |
| yin entering tone t | ㆵ | U+031B5 | BOPOMOFO FINAL LETTER T |
| yin entering tone k | ㆶ | U+031B6 | BOPOMOFO FINAL LETTER K |
| yin entering tone h | ㆷ | U+031B7 | BOPOMOFO FINAL LETTER H |
| yang entering tone p | ㆴ | U+031B4 | COMBINING DOT ABOVE RIGHT |
| yang entering tone t | ㆵ | U+031B5 | COMBINING DOT ABOVE RIGHT |
| yang entering tone k | ㆶ | U+031B6 | COMBINING DOT ABOVE RIGHT |
| yang entering tone h | ㆷ | U+031B7 | COMBINING DOT ABOVE RIGHT |
        - (note that extension bopomofo symbols extends until U+031B3.)
    - 參考資料：[W3C i18n CJK上對間隔號的討論](https://lists.w3.org/Archives/Public/public-i18n-cjk/2014OctDec/)
    - (四)中文字樣擴編及資訊應用：
        - **建議造字使用 CNS 1+2 字面取代「Big5」**
> 這部份沒有問題。
> [name=Audrey T]

        - **並且以 2009 增補過的 CNS1 取代「甲表」**
> 這部份沒有問題。
> [name=Audrey T]

        - **CNS1-4 作為標準造字的字碼範圍（不含異體字）**
> 如果是泛用漢字（含簡繁體），仍建議以 Unihan _第一批 20902 字為主。_
> [name=Audrey T]

萌典離線全文檢索 (Yap)
- [https://github.com/ksanaforge/dualfilter-sample](https://github.com/ksanaforge/dualfilter-sample) [簡報](https://docs.google.com/presentation/d/1zISRs0dgHAcGfd2qd7xwon7WDb7ljD4DiVIBtRIW-YM/edit?usp=sharing)

### 2015-12-08 國語小組共識


#### 《國語注音符號手冊》

(一)為推廣注音符號，建議將本手冊製作成以中、英文的電子書形式呈現。
(二)注音符號筆順的部分，製作SVG(可縮放的向量圖)檔案格式。除了圖例之外，其他的資料都以網頁(如HTML5)方式，分別提供。
(三)Unicode8.0 Errata已將U+3127的形式修訂為橫的「ㄧ」，爰建議本手冊未來修訂時，將注音符號韻符「ㄧ」(U+3127)，改為以橫式為原則。
(四)為避免注音韻符「ㄧ」橫書時，與標點符號「連結號」甲式－混淆的情況，建議於《國語注音符號手冊》內文附註：標點符號的「連結號」與注音符號相鄰時，以使用標點符號「連結號」的乙式～為原則。
(五)為解決中文資訊應用時，直式注音調號能落在正確位置的技術，建議以研究案方式，進行OpenType技術之研究，其成果可提供開發瀏覽器的、開放作業系統者利用。至於其他語別是否可同時合併處理，可再進一步討論。

#### 《重訂標點符號手冊》

(一)將本手冊製作成中、英文版的電子書。其英文版至少能提供每一個標點符號的標準英文翻譯。
(二)建議破折號採用之 Unicode 符號，與夾注號有別，以實作後者之避頭尾點規則。
惟目前中文字型廠商所開發的字形檔，多未內含「雙字寬橫線」U+2E3A，爰鼓勵中文字型廠商，於未來開發字型時，納入U+2E3A的符號。在過渡期間，還是可以用相同的符號，來表示夾注號與破折號。
(三)為避免注音韻符「ㄧ」橫書時，與標點符號「連結號」甲式－混淆的情況，建議於《重訂標點符號手冊》內文附註：標點符號的「連結號」與注音符號相鄰時，以使用標點符號「連結號」的乙式～為原則。
(四)本手冊對於刪節號的說明，建議增加「需列於中線，由六個點組成」等說明文字。未來可向國際申請增加刪節號的Unicode。

### 2015-12-22 本國語文中文資訊處理專案國語小組第3次會議

大致同上次共識，新增項目如下。接著會逕送中文資訊處理專案大會：

#### 《國語注音符號手冊》

- 明訂 EPUB3 為至少應具備之電子書格式，但亦可提供 HTML5 線上、PDF 印刷等版本。

#### 《重訂標點符號手冊》

- 明訂 EPUB3 為至少應具備之電子書格式，但亦可提供 HTML5 線上、PDF 印刷等版本。
- 為因應中文橫式排版，建議於手冊中考量增列相關輔助符號，如「／」及常見誤用符號之說明。
- 建議未來修訂標點符號手冊時，夾注號採甲式，連接號採乙式，破折號仍採用雙字寬橫線。

- [x] 如果教育部同意取消夾注號乙式的禁則，那就讓U+2E3A作為夾注號乙式及破折號；若否，則以U+2014作為破折號，U+2E3A作為夾注號乙式。(ethan, bob, au)
> 目前朝向「夾注號不推薦使用乙式」、「連結號不推薦使用甲式」處理
> [name=Audrey T]

> 這樣雙字寬橫線（無論用 U+2014 U+2014 或 U+2E3A 打），就一定是破折號了
> [name=Audrey T]

- [x] 目前多數排版軟體、出版品是不處理U+2014的禁則的，所以取消禁則不會有legacy問題；夾注號乙式的視覺形態不同於具強烈開合意味的甲式和引號，毋須使用禁則亦可確保閱讀時的流暢，加上夾注號乙式的禁則容易打亂排版體例——希望能以這二點來說服教育部。(ethan)
> 已經納入決議，禁則無意義（因為已經不推薦了）
> [name=Audrey T]

- [x] 中線六點刪節號向 Unicode Consortium 正式提出 codepoint 編碼需求時，提出的可選名稱：Midline six-dot ellipsis、Ideographic long ellipsis 等。(au, ethan)
> 已經納入決議，名稱為 Midline six-dot ellipsis。
> [name=Audrey T]

- [x] 以附注形式，澄清舊手冊中各種符號誤用的問題，例如以全形句點「．」作為間隔號、以製表符作為破折號等——用以提醒讀者不再誤用。(au, ethan)
> 已經納入決議。
> [name=Audrey T]

- [x] 納入分隔號 U+FF0F fullwidth solidus。 ／ (ethan)
> 這不是直式符號（手冊是直橫共同），所以擬另開「橫式符號」一章來討論，已納入決議。
> [name=Audrey T]


## 併松

> 歡迎把想做的專案/計畫列在這裡！
> [name=Audrey T]


### 2016 總統大選承諾一覽表

> 協作區網址：[http://beta.hackfoldr.org/president2016-folder/2016--cHFy9BCqxjx](http://beta.hackfoldr.org/president2016-folder/2016--cHFy9BCqxjx)
> [name=Johnson L]

- 新增政見
- 強制讓表格裡每個 item 一開始只顯示 N 行（N 可在[表格設定](https://ethercalc.org/president2016)中指定）
- 把出處們用 archive.org/web 做備份
- 縮寫過長的政見；對沒有在 FB group 的編輯者，先搜集要改的項目貼在 FB group，然後寄 email 通知編輯者說我們未來會這樣改。

### 救救臺灣龜

共筆：[https://g0v.hackpad.com/tFDaeOtsSbU](https://g0v.hackpad.com/tFDaeOtsSbU)
目標：
- **收集整合呈現資料：**
    - **收集呈現目前所有保育類淡水龜走私案件的資訊，散布給大眾知道這件事。**
- **凸顯野保法之缺失：**
    - **藉由呈現這幾年龜類走私數量，與最終法律判刑的刑期與罰金，兩者之間的不平衡，讓大眾瞭解目前臺灣野生動物保育法的不足，以及討論出需要的補足與修改方向。**
- **幫助未來推廣**
    - **資訊的收集整合也對於未來推廣者，尋找資料有幫助。**
- Wed Code：[https://github.com/g0v/cuora](https://github.com/g0v/cuora)
- hackfolder：[https://hackfoldr.org/turtle-cuora](https://hackfoldr.org/turtle-cuora)

### 開源導向(政府)出版品的特性列舉

- 共筆：[https://g0v.hackpad.com/SBFSdruovNE](https://g0v.hackpad.com/SBFSdruovNE)
- 概念起源：[https://www.facebook.com/data.visualize/posts/401806636656451](https://www.facebook.com/data.visualize/posts/401806636656451)
- cc [che wei liu](https://g0v.hackpad.tw/ep/profile/zsVEYFJyWhm) W3C DUB IG [Advancing Portable Documents for the Open Web Platform: EPUB+WEB](https://w3c.github.io/epubweb)
- IDPF [EPUB 3.1 Work Plan](http://www.idpf.org/workplans/2015/epub/)
> thanks!
> [name=che l]



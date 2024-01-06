---
title: "3du.tw"
tags: hackpad
---

# 3du.tw

> [點此觀看原始內容](https://g0v.hackpad.tw/ZNwaun62BP4)


我們想要還文於民，這階段的工作是提供中文字資料的開放 API 和範例 client app。

線上聊天室： [irc:](http://webchat.freenode.net/?channels=g0v.tw) [#g0v](https://g0v.hackpad.tw/ep/search/?q=%23g0v&via=ZNwaun62BP4)[.tw on freenode](http://webchat.freenode.net/?channels=g0v.tw)  \[[web 介面](http://hack.g0v.tw/irc)\]  \[[log 紀錄](http://hack.g0v.tw/irc/log)\]
線上工作組：[https://groups.google.com/forum/?fromgroups#!forum/3du-tw](https://groups.google.com/forum/?fromgroups#!forum/3du-tw)

歷史記錄：g0v hackath1n 當天的 hackpad: [3du.tw @g0v hackath1n |  台灣零時政府第壹次公地放領黑客松](https://hackpad.com/krYNczYQzTI#3du.tw%20%40g0v%20hackath1n%20%20%26nbsp%3B%26%2321488%3B%26%2328771%3B%26%2338646%3B%26%2326178%3B%26%2325919%3B%26%2324220%3B%26%2331532%3B%26%2322777%3B%26%2327425%3B%26%2320844%3B%26%2322320%3B%26%2325918%3B%26%2338936%3B%26%2340657%3B%26%2323458%3B%26%2326494%3B)

以下粗略列出需要做的事，想參與的人，請直接把名字寫進去。

### 資料來源

[教育部電子辭典](https://www.edu.tw/Content_List.aspx?n=83D8D70FE4468412)  網頁列了不少辭典，我們以《[教育部重編國語辭典修訂本](http://dict.revised.moe.edu.tw/)》和《[成語典](http://dict.idioms.moe.edu.tw/)》為起點，其他的有機會再加進來。

### 資料收集（Collection）

參與人：Audrey Tang, TonyQ Wang, kcwu, Hanfei Sun
- 《[教育部重編國語辭典修訂本](http://dict.revised.moe.edu.tw/)》：
    - 2013 年一月底抓的, [html raw data (tar.bz2)](http://kcwu.csie.org/~kcwu/moedict/dict-revised.rawhtml.201301.tar.bz2)
    - 另外有 2002,2004,2006 抓的版本, 可以找 kcwu 要
- 《[成語典](http://dict.idioms.moe.edu.tw/)》：TonyQ 的 [github](https://github.com/tony1223/3du.tw-phrase)
    - 資料下載: [http://files.tonyq.org/export.json](http://files.tonyq.org/export.json)
    - 資料結構說明: [https://gist.github.com/4646548](https://gist.github.com/4646548)
        - MnO2: s/sourceDescripton/sourceDescription/
        - SQL: [http://files.tonyq.org/data.sql](http://files.tonyq.org/data.sql) (1/27 晚上重爬得一百筆）
    - 原始資料：[https://github.com/BuzzAcademy/idioms-moe-unformatted-data](https://github.com/BuzzAcademy/idioms-moe-unformatted-data) (正文 5153 筆、附錄 25107 筆)
- [《教育部臺語常用詞辭典》](http://twblg.dict.edu.tw/holodict_new/index.html)
    - 教育部提供的最新資料（Excel，CC-BY-ND 3.0 授權，不含華語索引）：
        [http://www.audreyt.org/newdict/twblg\_data\_20130325.rar](http://www.audreyt.org/newdict/twblg_data_20130325.rar)
    - 華語索引（自行取得，不屬於上述授權範圍）：
        [http://www.audreyt.org/newdict/mandarin-to-twblg.txt](http://www.audreyt.org/newdict/mandarin-to-twblg.txt)
    - @happyman 於 2013/3/24 取得的網頁資料： [http://211.20.181.250/~happyman/taiwan_language.tgz](http://211.20.181.250/~happyman/taiwan_language.tgz)
    - 另可參考 pcchen 用 lift xml 格式定義的河英詞典 [nan.lift](https://github.com/pcchen/nan.lift) (CC BY-SA)
- 《[教](http://hakka.dict.edu.tw/hakkadict/index.htm)[育部臺灣客家語常用詞辭典](http://hakka.dict.edu.tw/hakkadict/index.htm)》
    - @au 於 2013/03/25 取得的網頁資料（「[標註出處、不可改作、不可作商業利用](http://hakka.dict.edu.tw/hakkadict/qa.htm)」授權，含華語索引）：
        [http://www.audreyt.org/newdict/hakka.tar.gz](http://www.audreyt.org/newdict/hakka.tar.gz)
> 2015/02/02 輾轉接到客語典維護團隊的訊息：
> [name=Audrey T]

> 授權雖然有和 BY-NC-ND 雷同的字樣，但**並非創用 CC**，而是團隊自行擬定的授權條款。
> [name=Audrey T]

> 兩年前在黑客松取得資料時未詳細查證，是我的疏失，也感謝維護團隊主動指正。
> [name=Audrey T]

- 《[教育部異體字字典](http://dict2.variants.moe.edu.tw/variants/)》
    - 字表: [https://github.com/kcwu/moedict-variants](https://github.com/kcwu/moedict-variants)
- 《[國語辭典簡編本](http://dict.concised.moe.edu.tw/)》
    - @au 於 2013/05/18 取得的網頁資料： [http://www.audreyt.org/newdict/concised.tar.gz](http://www.audreyt.org/newdict/concised.tar.gz)
- 《[漢越詞典摘引](http://www.hanviet.org/)》
    - 原始字詞來源: [Hán Việt Tự Điển Thiều Chửu](http://nguyendu.com.free.fr/langues/hanviet.htm)
    - 這個網站資料整裡的其他參考來源
        - [Quốc Ngữ Từ Điển 國語辭典(Taiwan)](http://140.111.34.46/newDict/dict/index.html)
        - [Hán Điển 漢典](http://www.zdic.net/zd/zi/zdice7zdic9dzdic96.htm)
        - [Chinese Chinese Dictionary](http://www.chinese-tools.com/tools/chinese-dictionary.html)
        - [Tân Hoa Tự Điển 新華字典](http://xh.5156edu.com/html5/139741.html)
        - [MDBG Chinese-English Dictionary](http://www.mdbg.net/chindict/chindict.php?istm=1)
    - 版權問題尚待釐清
- [國際電腦漢字及異](http://chardb.iis.sinica.edu.tw/)[國際電腦漢字及異體字知識庫](http://chardb.iis.sinica.edu.tw/)[體字知識庫](http://chardb.iis.sinica.edu.tw/)
    - 可用來補充目前《教育部重編國語辭典修訂本》單字收入釋義不足的尷尬
    - 提供了豐富的電腦異體字訊息
    - 地址：[http://chardb.iis.sinica.edu.tw/](http://chardb.iis.sinica.edu.tw/)
- [小學堂](http://xiaoxue.iis.sinica.edu.tw/)
    - 「小學堂文字學資料庫」是一個形、音、義綜合的文字學資料庫。內含甲骨文、金文、戰國文字（秦簡牘、楚簡帛）、小篆的資料，以及上古音、中古音、近現代方言等資料。
    - 地址：[http://xiaoxue.iis.sinica.edu.tw/](http://xiaoxue.iis.sinica.edu.tw/)
    - 內含兩個資料庫：
        - [漢字古今字資料庫](http://xiaoxue.iis.sinica.edu.tw/ccdb)
            - [http://xiaoxue.iis.sinica.edu.tw/ccdb](http://xiaoxue.iis.sinica.edu.tw/ccdb)
        - [漢字古今音資料庫](http://xiaoxue.iis.sinica.edu.tw/ccr/)
            - [http://xiaoxue.iis.sinica.edu.tw/ccr](http://xiaoxue.iis.sinica.edu.tw/ccr)
- [漢字字源資料庫](http://www.chineseetymology.org)
    - 字形圖片來源於說文解字，六書通，金文編，甲骨文編
    - Crawler: [https://github.com/hanfeisun/Chinese-Etymology-Crawler](https://github.com/hanfeisun/Chinese-Etymology-Crawler)
    - 資料下載：[https://www.dropbox.com/s/3n67pwlcxau3vvw/gbk.zip](https://www.dropbox.com/s/3n67pwlcxau3vvw/gbk.zip)
> 原來有這個資料庫！這樣或許就不需要掃描之前跟 au 提過的下面這本
> [name=nchild]

- 《增訂六書通》（實體書）[範例頁](https://www.dropbox.com/s/5cdwaibxqr15s1w/Sample%20324-325.pdf)
    - 著作財產權應該可由繼承取得，再授權本專案
www
### 資料解析（Parsing）

參與人：kcwu, MnO2, favonia
- 《[教育部重編國語辭典修訂本](http://dict.revised.moe.edu.tw/)》：kcwu
    - 工作內容：用 2007 年版的 html raw data 當輸入檔，把需要的欄位抽出來。程式在 [moedict-process](https://github.com/g0v/moedict-process), 輸出的 json 檔在 [moedict-data](https://github.com/g0v/moedict-data),  bz2 在[這](http://kcwu.csie.org/~kcwu/moedict/)
    - 前述的 json 跟後述的 sqlite db 檔中對於造字仍保留 {\[xxxx\]}
    - 整理編碼和造字圖的基礎工作請看 [3du.tw Encoding Meshup](https://hackpad.com/uGgOPAFgxDM)，成果的 unicode 對照表在 [moedict-epub](https://github.com/g0v/moedict-epub)
- 《[成語典](http://dict.idioms.moe.edu.tw/)》：MnO2
    - MnO2: 將典故等HTML欄位的sanitizing & re-structuring, 目前只有很 naive 地把東西拔掉， 請見 pull request log: [https://github.com/tony1223/3du.tw-phrase/pull/2](https://github.com/tony1223/3du.tw-phrase/pull/2)
    - TonyQ: 已 Merge
- 《[教育部臺灣閩南語常用詞辭典](http://xn--i6q78bz8rrjsrofsqvznntoa798at5o/)》
    - CSV 及 JSON 檔，含造字資料：[https://github.com/g0v/moedict-data-twblg](https://github.com/g0v/moedict-data-twblg)
    - dict-twblg.json 檔格式和 dict-revised.json 大致相容，惟 synonyms/antonyms 提到 heteronyms 層級（而非 definitions 層級）。
    - 造字請見 [3du.tw Holok Hakka Map](https://hackpad.com/wLO3GClHOUO)（共筆檢字已結束）
- 《[教育部臺灣客家語常用詞辭典](http://hakka.dict.edu.tw/hakkadict/index.htm)》

### 資料儲存與索引（Database and Indexing）

參與人：albb0920
工作內容：瞭解《[教育部重編國語辭典修訂本](http://dict.revised.moe.edu.tw/)》和《[成語典](http://dict.idioms.moe.edu.tw/)》的資料欄位，設計出儲存和索引的方式（一開始不必最佳化，先求有，再改良），好實作 API。
- albb0920: [Schema](https://hackpad.com/8I4XU6xc4QJ#3du.tw%20DB%20schema%20draft)
[online lexicography. 辭典學](http://www.christianlehmann.eu/ling/ling_meth/ling_description/lexicography/)
- [辭典學字典結構 與 moedict 資料結構的比對](https://g0v.hackpad.com/-moedict--lcEFcpToerf)

### API 設計


參與人：[Ping Yeh](https://hackpad.com/ep/profile/-3othgyRWJMbj5G6yJcfaP0)
第一步只提供 RESTful interface，回傳 JSON。細節詳見 [3du.tw API Design](https://hackpad.com/95jKjray8uR)。
- 2013-01-27 12:45pm [Ping Yeh](https://hackpad.com/ep/profile/-3othgyRWJMbj5G6yJcfaP0) 初步 API 完成。

### API 實作

參與人：albb0920, au, viirya
- 使用 rails 3 實作
    - [https://github.com/albb0920/dict-3du](https://github.com/albb0920/dict-3du)
- 另一個實作，單純用靜態 json 檔加上 nginx 模組 -au
    - [https://github.com/g0v/moedict.tw](https://github.com/g0v/moedict.tw)
    - 已穩定運行在 dotCloud 上: [https://www.moedict.tw/uni/%E6%B7%B7](https://www.moedict.tw/uni/%E6%B7%B7)
    - 目前有三個端點:
        - /raw/ 是 kcwu 抓的源 json 檔，Big5 區之外的字以造字碼 {\[abcd\]} 表示。
        - /uni/ 是把 {\[abcd\]} 轉成相應的 Unicode 字元。<-- 客戶端用這個通常最方便。
        - /pua/ 與 /uni/ 相同，只是動態組字改用 @medicalwei 的造字替代。
        - 另支援 JSONP，但 callback= 參數須固定為 moedict\_jsonp\_callback:
            - [https://www.moedict.tw/pua/%E9%9A%B8%E8%AE%8A?callback=moedict\_jsonp\_callback](https://www.moedict.tw/pua/%E9%9A%B8%E8%AE%8A?callback=moedict_jsonp_callback)
            - 用 $.ajax 的話，設定 { jsonpCallback: "moedict\_jsonp\_callback" } 即可，如：
                - $.ajax({ url: "[https://www.moedict.tw/pua/%E9%9A%B8%E8%AE%8A](https://www.moedict.tw/pua/%E9%9A%B8%E8%AE%8A)", dataType: "jsonp", jsonpCallback: "moedict\_jsonp\_callback" , success: console.log })
        - 也支援 CORS (Access-Control-Allow-Origin: *)。
    - 此外，「內文自動斷詞」的端點在 /a/：
        - 例如：[https://www.moedict.tw/a/萌.json](https://www.moedict.tw/a/萌.json)
        - 斷詞後的所有條目（with URI Escape key）可在 [https://www.moedict.tw/a/autolinked.json](https://www.moedict.tw/a/autolinked.json) 取得。
        - 從簡寫 JSON 還原到 HTML 的三項 regex 替換，請見 [https://github.com/audreyt/moedict-webkit/blob/master/main.ls#L176](https://github.com/audreyt/moedict-webkit/blob/master/main.ls#L176)
- 用 node.js + sqlite 的伺服器版本 -
    - [http://moedict-viirya.dotcloud.com](http://moedict-viirya.dotcloud.com)
    - [https://github.com/viirya/moedict-web](https://github.com/viirya/moedict-web)
- 將全形句號「．」（FF0E）替換為真正的間隔號「·」（00B7）。
- 建議可以加上威妥瑪拼音——漢語拼音為主、威式為輔，某些地名條目（如台北市）比較不突兀。

### 伺服（Serving）

參與人：adaam（主機）, j100002ben（web framework）
- 目前位置在 dict.3du.tw
- 目前更新到kcwu的最新DB(2013/1/31)
- j100002ben：Send me email to request the login pem file or anythings for the server :)
    - ~54.249.240.69~（Amazon Large 關機中XD）：Ubuntu 12.04 with Nginx, nodejs, Ruby on Rails, Percona Mysql Server, and MongoDB
    - 54.249.232.225（Amazon Micro）：Ubuntu 12.04 with Nginx, rbenv, Ruby, Bundler, Rails, sqLite

### Client 範例

- Web client: bananaplle, pingooo
    - mockup初版 [http://docs.google.com/drawings/d/1OWonzGqD7veiilxYJf1l8m3WqnM-NUvohb3wW8ZbFIY/edit](http://docs.google.com/drawings/d/1OWonzGqD7veiilxYJf1l8m3WqnM-NUvohb3wW8ZbFIY/edit)
    - 搜尋的方式如果畫這樣： [http://docs.google.com/drawings/d/1KlVIQwVOjC0_M7mbhDKqwRwNvTPb0fauAH5D9yWimRo/edit](http://docs.google.com/drawings/d/1KlVIQwVOjC0_M7mbhDKqwRwNvTPb0fauAH5D9yWimRo/edit)
- 網頁版: au
    - [https://moedict.tw/](https://moedict.tw/)
    - 定義部份的每個字都可以點按，也適合在手機上交叉檢索。
        - [x] **定義部份點按的斷詞有一點問題**
> 像講義([https://www.moedict.tw/](https://www.moedict.tw/#講義)[#講義](https://g0v.hackpad.tw/ep/search/?q=%23%E8%AC%9B%E7%BE%A9&via=ZNwaun62BP4))  解釋裡的「闡釋說明書籍的義理」會被切成「闡釋-說明書-籍-的-義理」，「學校教師為學生編輯的」也會被切成「學校-教師-為學-生-編輯-的」
> [name=Kuang-che W]

> 斷詞的問題可以考慮用中研院的中文斷詞系統([http://ckipsvr.iis.sinica.edu.tw/](http://ckipsvr.iis.sinica.edu.tw/)) 來解決
> [name=Kuang-che W]

> 如果這個階段有需要解決這樣的問題的話我願意認領
> [name=Kuang-che W]

> 太好了，請逕行認領，源資料在 [https://github.com/g0v/moedict-data](https://github.com/g0v/moedict-data)  裡 (dict-revised.json)，請將斷詞程式及結果放在 GitHub 上，我會合併。
> [name=Kuang-che W]

            - 斷詞程式做好了。東西放在 [https://github.com/chyiro/moedict-data-chunker](https://github.com/chyiro/moedict-data-chunker) ，輸出的結果在 moedict_data/dict-revised-chunked.7z 裡面(原始檔是164MB)。
    - 各瀏覽器（含 PhoneGap 版）皆支援自動完成。
    - **我（Chen Yijun）的一些建議改進方向：**
        - [x] 將全形句號「．」（FF0E）替換為真正的間隔號「·」（00B7）。新版的\[「漢字標準格式」將會支援顯示此符號為「全形」\]([http://css.hanzi.co/lab/201302/biaodian\_fuhao\_yangshi.html](http://css.hanzi.co/lab/201302/biaodian_fuhao_yangshi.html))。
            - 已實作，感謝! -au
        - [x] 是不是應該支援HTML5的History API？而不是只用「#!」？
            - 目前已使用 History API。-au
        - [x] 建議不要用等寬字體顯示拼音，Georgia或無襯線字體搭配標楷體會比較好看。
            - 已實作，感謝! -au
        - [ ] 注音符號可以直接加在條目名稱上（\[「漢字標準格式」支援直式標註\]([http://css.hanzi.co/lab/201302/manual.html#hanzi_zhuyin](http://css.hanzi.co/lab/201302/manual.html#hanzi_zhuyin))），並用cookies記錄使用者偏好以何種註音（注音、漢語拼音、威妥瑪拼音或不標註）來標註條目名稱。
        - [x]  把字詞都用`<a>`包裹後，就會出現避頭點的問題，下面是竹取直排JS的解決方法：
            - `<span style="display: inline-block;"><a href="[#嗎](https://g0v.hackpad.tw/ep/search/?q=%23%E5%97%8E&via=ZNwaun62BP4)">嗎</a>？</span>`
            - 已實作，感謝! -au
        - [x] 連接號乙式無論全形或半形，看來都很怪，\[建議改用甲式\]([http://www.edu.tw/files/site_content/M0001/hau/h15.htm](http://www.edu.tw/files/site_content/M0001/hau/h15.htm))。
            - 已實作，感謝! -au
    - Ihc:歹勢我現在才把我組字的程式傳去github，我有暫時把很簡單的資訊寫在javadoc的首頁上了
        - [https://github.com/sih4sing5hong5/han3\_ji7\_tsoo1_kian3](https://github.com/sih4sing5hong5/han3_ji7_tsoo1_kian3)
        - 對了，我ＩＲＣ都連不進去＠＠

- Web client and REST API: viirya
    - [http://moedict-viirya.dotcloud.com/](http://moedict-viirya.dotcloud.com/)
    - [https://github.com/viirya/moedict-web](https://github.com/viirya/moedict-web)
    - 網路查詢介面透過 REST API 即時取得自動完成結果
    - API 查詢方式如 au 的 [https://gist.github.com/4648550](https://gist.github.com/4648550)，輸出 JSON
- 手機 client: (也請參考下面 "轉換為現有的字典格式/add-on" 區)
    - iPhone client :
        -  jpsun 因為有 server 可用了，開發網路查詢版。
        - 我可以寫iOS版，先用離線寫，速度會比較快。 (dryman) 目前功能有
            - Core Data，他內建的cache機制還是比sqlite快
            - NSBurstTrie，支援prefix search
            - 使用table view來呈現data
        - 已完成 iOS 版 API Client
        - [典雅的 iOS 版](https://github.com/jamessa/MoeDict)，這版的想法是希望在 iOS 內建繁體中文字典時，能有個簡便的界面，讓所有的中文 app 可以使用 3du.tw 的成果。
        - [萌字典 iOS App](https://github.com/pct/moedict-ios-app) (pct)，使用 Titanium 撰寫
    - PhoneGap client: au
        - [https://github.com/audreyt/moedict-webkit/tree/master/android](https://github.com/audreyt/moedict-webkit/tree/master/android)
        - 把 WebKit client 包進 Cordova 裡，直接做成離線 App
        - JSON 資料庫平均切成 1024 份，分別存成 txt 檔再動態載入。
        - 已上傳至 [Google Play](https://play.google.com/store/apps/details?id=org.audreyt.dict.moe) 及 [App Store](https://itunes.apple.com/tw/app/meng-dian/id599429224)。
    - Firefox OS/Mobile web client:
        - (問一下這是可以自己認領的嗎 yurenju (當然可以 -au))
- Tablet client: 待認領
- 離線 Standalone App
    - au: 簡單的 bin/moe: [https://gist.github.com/4648550](https://gist.github.com/4648550)
        - 以 [https://github.com/g0v/moedict-epub/blob/master/db2unicode.pl](https://github.com/g0v/moedict-epub/blob/master/db2unicode.pl)  轉為 Unicode-only database
    - racklin: 跨平台 moe-dictionary-app: [https://github.com/racklin/moe-dictionary-app](https://github.com/racklin/moe-dictionary-app)
        - Wiktionary 維基詞典 Add-on 完成。
        - 以 [https://github.com/g0v/moedict-epub/blob/master/db2unicode.pl](https://github.com/g0v/moedict-epub/blob/master/db2unicode.pl)  轉為 Unicode-only database
        - TonyQ 成語典 Add-on 。
    - racklin: 新版跨平台 App，以 moedict-app 為基礎開發：
        - 測試版下載: [http://app.moedict.org/](http://app.moedict.org/)
        - GitHub Repo: (待補)
    - tonytonyjan: Chrome Extension：[http://goo.gl/ZEC2B](http://goo.gl/ZEC2B)
        - 使用畫面：[http://youtu.be/oetCzmsT6IY](http://youtu.be/oetCzmsT6IY)
        - Github: [https://github.com/tonytonyjan/hahadict](https://github.com/tonytonyjan/hahadict)
        - JSON 格式字典 [http://tonytonyjan.net/downloads/3du/dict.json.bz2](http://tonytonyjan.net/downloads/3du/dict.json.bz2) (根據 kcwu 提供的 [development.sqlite3](http://kcwu.csie.org/~kcwu/tmp/moedict/development.sqlite3.bz2))
        - 不妨參考 [WebKit 網頁版](http://www.audreyt.org/newdict/moedict-webkit/)  的動態載入方式... ([GitHub repo](https://github.com/audreyt/moedict-webkit))
            - 謝謝，我最後還是沒有用這個方式 Orz
    - Sars: Windows Store app (Win8/8.1): [https://github.com/](https://github.com/SarsTW/moedict-win8-app)[SarsTW](https://github.com/SarsTW/moedict-win8-app)[/moedict-win8-app](https://github.com/SarsTW/moedict-win8-app)
    - .[NET LINQ版應用範例](https://github.com/darkthread/MoeDictNet): 不依賴DB, 將JSON資料轉為.NET物件後序列化保存, 直接使用LINQ方式查詢
- 轉換為現有的字典格式/add-on
    - stardict 格式: elleryq ([字典檔下載](http://goo.gl/jvqGf) , [轉換程式](https://github.com/elleryq/moe2stardict) )
        - 做 android 上的 colordict 自動安裝字典 add-on: 待認領 (colordict 可以直接用startdict 的字典檔，但是需要打包自動安裝)
    - epwing 格式: 待認領
    - Kindle 辭典格式：freedom
        - 字典檔: [content.mobi](https://www.dropbox.com/s/pzypawtlo97wtek/content.mobi)
        - For Android: 放到 SD Card 上的 Android/data/com.amazon.kindle/files/ 底下, 名字必須叫做 B00AZOHEFU_EBOK.prc, 然後就有一個萌典了
        - For iPhone/iOS, Apps/Kindle/Library/eBooks/ 底下名字必須叫做 B00AZOHEFU_EBOK.azw, 然後就有一個萌典了
        - How to build the .mobi and what still can be done, see [https://www.icloud.com/iw/](https://www.icloud.com/iw/#keynote/BALcDGUOsEe4e2HBQnaBbs3WUtxhoCja75qE/moedict-for-kindle-app)[#keynote](https://g0v.hackpad.tw/ep/search/?q=%23keynote&via=ZNwaun62BP4)[/BALcDGUOsEe4e2HBQnaBbs3WUtxhoCja75qE/moedict-for-kindle-app](https://www.icloud.com/iw/#keynote/BALcDGUOsEe4e2HBQnaBbs3WUtxhoCja75qE/moedict-for-kindle-app)
        - 上面的連結失效了，我重新用 stardict 格式轉換了一份 mobi 格式，放在 Dropbox：[https://www.dropbox.com/sh/w04p3up4mfdbuu1/FAx6BlFJge](https://www.dropbox.com/sh/w04p3up4mfdbuu1/FAx6BlFJge)
        - Dropbox在大陸地區無法訪問,百度網盤: [http://pan.baidu.com/s/1sj4vKkd](http://pan.baidu.com/s/1sj4vKkd)
        - 備用: [http://pan.baidu.com/s/1hq0Au0k](http://pan.baidu.com/s/1hq0Au0k)  密碼: ides
    - Pleco: [http://www.plecoforums.com/threads/the-moe-dictionary-is-now-open-source.3606/page-4#post-29408](http://www.plecoforums.com/threads/the-moe-dictionary-is-now-open-source.3606/page-4#post-29408)
    - yllan: Mac OS X 字典: [https://github.com/yllan/moedict-mac](https://github.com/yllan/moedict-mac)
        - [http://moe.hypo.cc/](http://moe.hypo.cc/)
            - 最新 build 好的字典檔（越新的在越下面 orz），解開放到 ~/Library/Dictionaries 底下，再開啟 Dictionary.app 即可。如果沒看到的話要去 Preferences 裡面把萌典勾起來。
        - [http://ci.hypo.cc/](http://ci.hypo.cc/)
            - 有 push 上 github repo 就會自動 build，不過盡量不要來這台抓 artifacts，因為是辦公室網路。純抓檔請用 [http://moe.hypo.cc/](http://moe.hypo.cc/)。
        - 以 [https://github.com/g0v/moedict-epub/blob/master/db2unicode.pl](https://github.com/g0v/moedict-epub/blob/master/db2unicode.pl)  轉為 Unicode-only database
- 翻譯
    - [http://audreyt.org/newdict/dict-revised.unicode.json](http://audreyt.org/newdict/dict-revised.unicode.json)
        - 英、法、德語，由 a-tsioh 與 Hugo_Lz 製作, 結構為:
            - {"translation": {"francais":\["germer"\], "Deutsch":\["Leute, Menschen  (S)","Meng  (Eig, Fam)","keimen, sprießen, knospen ausschlagen "\], "English":\["to sprout","to bud","to have a strong affection for (slang)","adorable (loanword from Japanese `萌~え moe, slang describing affection for a cute character)"\] }}
        - Source: [https://github.com/audreyt/moedict-webkit/blob/master/Makefile#L64](https://github.com/audreyt/moedict-webkit/blob/master/Makefile#L64)

### 字詞發音

- GCIN的作者有自己錄製給GCIN使用的發音檔，是以注音符號為檔名，應該可以直接關聯起來。(授權為 GNU LGPL3 or GNU GPL3 dual license) [http://cle.linux.org.tw/trac/wiki/GcinDistros#gcinvoicedata](http://cle.linux.org.tw/trac/wiki/GcinDistros#gcinvoicedata)
    - 感謝，已放到 GitHub 上：[http://audreyt.github.io/gcin-voice-data/](http://audreyt.github.io/gcin-voice-data/)
    - Source OGG: [http://audreyt.github.io/gcin-voice-data/ogg/%E3%84%85%E3%84%9A/3.ogg](http://audreyt.github.io/gcin-voice-data/ogg/%E3%84%85%E3%84%9A/3.ogg)
    - Converted MP3: [http://audreyt.github.io/gcin-voice-data/mp3/%E3%84%85%E3%84%9A/3.mp3](http://audreyt.github.io/gcin-voice-data/mp3/%E3%84%85%E3%84%9A/3.mp3)
- Zhspeak也有發音檔在 sourceforge 上，以漢語拼音為檔名。[http://www.eguidedog.net/ekho.php](http://www.eguidedog.net/ekho.php) (GPL v2) 另外espeak中的中文詞發音規則也可以使用？
- 連線使用 Google Translate 的發音？
- [FORVO, 全球使用者自行錄音，有提供 RESTful API, 目前已有【2,070,823](http://zh.forvo.com/)[個詞語 2,124,148個發音 306種語](http://zh.forvo.com/)[言】](http://zh.forvo.com/)
- [http://shtooka.net](http://shtooka.net)


### git repository 整合

參與人：待認領
把大家的 code 和 data 整合起來，方便散佈，並討論選定授權條款。
這部分是整合大家的code到github上面嗎? 帳號是有公用的還是先用自己的?

目前的 repo 列表：
- [https://github.com/g0v/moedict-epub](https://github.com/g0v/moedict-epub) 圖字列表、ePub 生成、WebFont
- [https://github.com/g0v/moedict-process](https://github.com/g0v/moedict-process) HTML 轉 SQLite3
- [https://github.com/g0v/moedict-data](https://github.com/g0v/moedict-data) 轉出來的 json 檔
- [https://github.com/racklin/moe-dictionary-app](https://github.com/racklin/moe-dictionary-app) XUL 離線 App
- [https://github.com/yllan/moedict-mac](https://github.com/yllan/moedict-mac) Mac OS X 用字典檔格式
- [https://github.com/audreyt/moedict-webkit](https://github.com/audreyt/moedict-webkit) WebKit 網頁版、PhoneGap 離線版
- [https://github.com/g0v/moedict-app](https://github.com/g0v/moedict-app) 上述離線版預先整理好的 app，含資料檔
- [https://github.com/albb0920/dict-3du](https://github.com/albb0920/dict-3du) JSON API
- [https://github.com/tonytonyjan/hahadict](https://github.com/tonytonyjan/hahadict) Chrome Extension 離線版
- [https://github.com/pct/moedict-ios-app](https://github.com/pct/moedict-ios-app) iOS App (需配合底下 moedict-server)
- [https://github.com/pct/moedict-server](https://github.com/pct/moedict-server) API Server (using node.js)
- [https://github.com/viirya/moedict-web](https://github.com/viirya/moedict-web) Web client、REST API
- [https://github.com/ericsk/moedict-rt](https://github.com/ericsk/moedict-rt) WinRT Component (給 Windows 8 App 用的元件)
- [https://github.com/](https://github.com/SarsTW/moedict-win8-app)[SarsTW](https://github.com/SarsTW/moedict-win8-app)[/moedict-win8-app](https://github.com/SarsTW/moedict-win8-app) Windows Store App (Windows 8 App)
- [https://github.com/zonble/sublime_moedict](https://github.com/zonble/sublime_moedict) SublimeText plugin (on audreyt.org JSON api)
- [https://github.com/zonble/MOEDict](https://github.com/zonble/MOEDict) Cocoa Touch 離線版
- [https://github.com/tomjpsun/3du.tw-ios](https://github.com/tomjpsun/3du.tw-ios)  Cocoa Touch 線上查詢版[上架](https://itunes.apple.com/tw/app/g0v-yun-duan-zi-dian/id606170413?l=zh&mt=8)
- [https://github.com/jamessa/MoeDict](https://github.com/jamessa/MoeDict) Cocoa Touch 線上版
- [https://github.com/g0v/moedict-data-twblg](https://github.com/g0v/moedict-data-twblg) 臺灣閩南語常用詞辭典的資料檔
- [https://github.com/elleryq/moe2stardict](https://github.com/elleryq/moe2stardict)  轉為 stardict 辭典檔的程式
- [https://github.com/rschiang/moedict-meego](https://github.com/rschiang/moedict-meego) MeeGo Harmattan (N9) App[上架](http://store.ovi.com/content/375495)
- [https://github.com/darkthread/MoeDictNet](https://github.com/darkthread/MoeDictNet) 教育部國語辭典JSON檔解析及應用(.NET版)
- [https://github.com/wildjcrt/moedict-extension](https://github.com/wildjcrt/moedict-extension) 萌典 Chrome extension
- [https://github.com/wildjcrt/moedict-addon](https://github.com/wildjcrt/moedict-addon) 萌典 Firefox Add-on
- [https://github.com/kuanyui/moedict.el](https://github.com/kuanyui/moedict.el)  Emacs版的client(需網路)
- [https://github.com/yllan/moedict-csld-mac/releases/](https://github.com/yllan/moedict-csld-mac/releases/) 兩岸常用詞典 Mac 版

[https://github.com/g0v/moedict-data-twblg](https://github.com/g0v/moedict-data-twblg)


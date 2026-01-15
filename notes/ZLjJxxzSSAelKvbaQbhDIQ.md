---
tags: gxv,CY 零時監察院,工人智慧,gxv
---

# GXV: Guan Xi Visualized 關係視覺化

親族關係+公司關係->政商金權透明化
Hackfoldr [http://hackfoldr.org/gxv](http://hackfoldr.org/gxv)
[Facebook 社團](https://www.facebook.com/groups/1541475416064830/)
[簡報素材](https://goo.gl/JizT0N)
> 對話閒聊請到本 pad 最下方
> [name=venev]


## 願望

**拆解**、梳理「**權 / 貴 / 政 / 金**」間的裙帶與臍帶關係，讓政商網絡資訊盡可能透明化，並善用資訊視覺化（data visualization）及群眾外包（crowdsourcing）力量，在未更動資本主義和民主選舉的前提下，提高民意 / 消費者監督與投票 / 消費選擇的效率。

## 近期實作類專案

### 台灣政商人物資料庫，從點到線的資料協作 by H.C. Chien, READr
- https://whoareyou.readr.tw/
- https://propose.summit2020.g0v.tw/proposal-detail/5ef99ae9ba206b030d66a39d
- 摘：於是我們利用開放原始碼的內容管理工具—Keystone.js 製作了一個資料庫管理介面，接下來我們將會使用 google spreadsheet 或其他類似的工具，提供給一般使用者也可以進行資料的協作，並且讓 spreadsheet 可以跟資料庫進行資料的同步。有了同步功能之後，便可以進行協作，讓所有人可以將相關資料利用這些工具加強資料庫的完整性。

### Gilbert 政商關係專案

- https://g0v.hackpad.com/hxJBK9v7frt

### GuanXi Prototype 關係圖欄位試作 by venev

- [https://docs.google.com/spreadsheets/d/1G\_vipmrSaG\_bkRTREvvQbra2aqmnSJzt0yLhcVsRatQ/edit](https://docs.google.com/spreadsheets/d/1G_vipmrSaG_bkRTREvvQbra2aqmnSJzt0yLhcVsRatQ/edit)
- [關係資料討論紀錄 @萌典松](https://g0v.hackmd.io/AuoafWXQRDqBqSCMeUDcQQ)

## TODOs

#### 項目

1.  先提高工具可用性，可單兵上陣
2.  **建構資料素材庫**，蒐集關係資料來源，添內容血肉 e.g. keyin 總統的親戚、監察院帶政治獻金專戶細目
3.  製作幾張關係圖範例，搭配時事，作成偵探懶人包
4.  群眾超展開
*   拆任務讓人認領（低技術門檻坑）
> 政治獻金數位化，鄉民 OCR 一戰成名 XDDDD
> [name=venev]

* 設計前端瀏覽介面（infographics + interpretation? 搜關鍵字導入近期新聞?）
5.  結合其他 g0v 專案，例如[企業資料與汙染源資料](https://g0v.hackpad.tw/cAbxJt2yt94)

#### 交流與合作

1.  舉辦 Meetup / Sunlighthon / GuanXithon
    - **推動模式：**
        1.  藉由**陽光松 / 黑客松**
            1.  邀請政商議題研究者
            2.  hacker 產出好用工具
            3.  發展有趣的企畫 (ex同步搜集政商照片)
            4.  指認各種重要公部門/民間資料庫，釐清 Licenses 再利用課題
            5.  [活動構想初擬](https://hackfoldr.org/gxv/PnYEREPBYqH)
        2.  藉由**好用工具\+ Licenses**，讓個人&媒體&研究機構，貢獻其所知道的關係知識
            1.  平時：累積人物關係資料、更新人物關係資料
            2.  應用：針對特定事件，輔助研究計畫
2.  Work with Academia｜與研究機構交流、合作
3.  Work with Media｜找傳統媒體協作，善用他們跑「政治財經線」的經驗和議題敘事能力，來弄台版 [littlesis](http://littlesis.org/)，等於有一個共同維護的政商關係 database
> 曾和 g0v 聯絡過、已知對這主題有興趣的記者或窗口，請幫忙補充
> [name=venev]

1. 壹週刊（記者梁鴻彬）
2. 天下
3. 新新聞
4. 風傳媒
5. [UDN DJ - 聯合報系新媒體部資料新聞學](https://www.facebook.com/udnNewMediaLab)


## 工具&Data


### 打造工具與資料庫（搜尋 / 圖像介面 for 鍵盤柯南 / end user）

- 台灣公司資料：[g0v 站](http://gcis.nat.g0v.tw/) / [ronny 本鋪](http://company.g0v.ronny.tw/)
    - 隱藏版地址檢索功能 /index/search?q=address%3A該地址，[使用範例](http://www.ptt.cc/bbs/Gossiping/M.1413257093.A.991.html)
- [政商關係圖 from Gilbert](http://hackfoldr.org/gxv/hxJBK9v7frt)
    - RESTful API [https://github.com/WeiChengLiou/twcom](https://github.com/WeiChengLiou/twcom)
    - website：[http://twcom-analysis.herokuapp.com](http://twcom-analysis.herokuapp.com)
- [財團 / 社團法人檢索](http://foundations.olc.tw/)（kiang++）/ [github repo](https://github.com/kiang/foundations)
- [開放政治獻金資料庫](http://campaign-finance.g0v.lackneets.tw/)
- [政府採購網資料](http://gov.playgroup.com.tw/gov_notice)（公告蒐集，可檢索、訂閱推播）
- [金錢報，公職人員財產申報](http://sunshine.cy.g0v.tw/)
- addressbook-grano / [github repo](http://github.com/g0v/addressbook-grano)
- 人物關係生產器
    - [公眾人物關係圖](http://%20http//zbryikt.github.io/ppllink/) / kirby 開發中 / [github repo](http://%20http//github.com/zbryikt/ppllink)
    - 線上族譜 [MyHeritage](http://www.myheritage.cn/)（簡中）
    - 單機軟體 [My Family Tree](http://chronoplexsoftware.com/myfamilytree/index.htm)（[電腦玩物介紹](http://www.playpcesor.com/2012/01/my-family-tree.html)）
    - [https://familysearch.org/search](https://familysearch.org/search)
    - [http://www.genopro.com/?ReferrerID=daring](http://www.genopro.com/?ReferrerID=daring)
    - [http://yesdaring.tripod.com/intro_genpro20040106.htm](http://yesdaring.tripod.com/intro_genpro20040106.htm)
- 公司關係圖生產器
    - [公司關係圖](http://company-graph.g0v.ronny.tw/) / ronnywang 開發中 / [github repo](https://github.com/ronnywang/company-graph)
        - what if 整合股票代碼 -> 上市上櫃、有更多可公開監督資料？
        - 公司全名整合上市櫃股票代碼， [8 月萌典松: moed5ct (含直播及文字轉播)](https://g0v.hackpad.com/8-moed5ct) 併政獻松，被 [johnny](https://g0v.hackpad.com/ep/profile/xQfy2Z4YLPO) 和我解開啦挖哈哈 / 以下貼自 [政治獻金 / 政商關係搜尋介面 mockup](https://g0v.hackpad.com/FbTZjGOYRUK)
> ！公職人員財產申報的股票是登記縮寫 ex: 1314 中石化 ，但政治獻金是登記全名 [中國石油化學工業開發股份有限公司](http://www.cpdc.com.tw/) 。考慮撈證交所公開資訊觀測站「公司名 / 股號 / 公司名縮寫」對應資料
> [name=venev]
> Johnny 撈到資料了喔耶！
> 
> [excel資料](https://github.com/thewayiam/cy/blob/master/data/xlsx/stocksymbol.xlsx)，目前一萬四千筆股票申報可辨別出一萬兩千筆，未辨識出的包含未上市櫃、以及國外的股票，以及一些比較難的，例如：台灣積電=?台積電、台塑化=?台灣塑化、中美晶...等等，可能須手動加入這些俗稱
 > [name=venev]
- 家系圖軟體的雛形與初步研究
    - [https://www.facebook.com/yurenju/posts/10154065231736631](https://www.facebook.com/yurenju/posts/10154065231736631)


### Data（柴 / 生肉 for 重度使用者 / 攻城獅）


#### 資料格式參考

- Popolo - International open government data specifications
    - https://www.popoloproject.com/

#### 名單，統編 (不涉及政商關係)

- 公示資料（統編）查詢系統
    - [https://g0v.hackpad.tw/WhCmazsSmry](https://g0v.hackpad.tw/WhCmazsSmry)
#### 監察院

- [陽光法案主題網](http://sunshine.cy.gov.tw/)：[申報資料查詢](http://sunshine.cy.gov.tw/GipOpenWeb/wSite/ct?xItem=4664&ctNode=443&mp=2)，包含
    - [公職人員財產申報](http://sunshine.cy.gov.tw/GipOpenWeb/wSite/sp?xdUrl=/wSite/SpecialPublication/baseQuery.jsp)（[g0v repo](https://github.com/g0v/sunshine.cy)）
    - [政治獻金收支結算](http://sunshine.cy.gov.tw/GipOpenWeb/wSite/sp?xdUrl=/wSite/PoliticAccount/PAQuery.jsp&ctNode=353)
    - [近五年廉政專刊電子書](http://sunshine.cy.gov.tw/GipOpenWeb/wSite/lp?ctNode=442)
    - 以上需備份，避免五年時效經過後被選擇性移除，例如[連戰](https://plus.google.com/+%E6%9E%97%E9%9B%A8%E8%92%BC/posts/FKN1ZbhHkWN)財產申報紀錄，[官方載點於 2014/9 已失效](http://sunshine.cy.g0v.tw/people/%E9%80%A3%E6%88%B0/property/overview/)

#### 司法院

- [透析貪污判決--揭露與查詢網站](https://g0v.hackpad.com/--OoaenzjVDKK)
- [社團 / 財團法人登記資料](https://github.com/g0v/foundationtw)（g0v repo, Jimy++）
    - [http://foundations.olc.tw/](http://foundations.olc.tw/)
    - data from 司法院 [法人及夫妻財產登記公告](http://cdcb.judicial.gov.tw/abbs/wkw/WHD6K00.jsp)

#### 行政院

- 經濟部商業司
    - [公司登記資料](http://company.g0v.ronny.tw/)
- 經濟部工業局
    - [工廠登記公示資料](http://gcis.nat.gov.tw/Fidbweb/index.jsp)
    - 爬蟲 & 資料 - [https://github.com/kiang/twfactory/tree/master/Console/Command/data](https://github.com/kiang/twfactory/tree/master/Console/Command/data)
- 公共工程委員會
    - [政府電子採購網](http://gov.playgroup.com.tw/gov_notice)
- 財政部
    - [公益彩券盈餘分配辦理社會福利事業情形](http://www.nta.gov.tw/web/AnnA/uptAnnA.aspx?c0=391&p0=6531)
- 主計總處
    - 政府捐助財團法人名單 [http://www.storm.mg/article/241478](http://www.storm.mg/article/241478)
#### 臺灣證券交易所

- [公開資訊觀測站](http://mops.twse.com.tw/mops/web/index) (證交所的持股資料，公司名稱與公司名，代碼，股號..)
#### 報紙資料

- 報紙資料庫：
    - 中央
    - 聯合
    - [慧科](http://www.wisers.com/corpsite/global/b5/home/index.html) (新聞資料很齊全)
    - [中評網](http://hk.crntt.com/) (個案報導深入)
#### 企業資料

- 千大企業調查資料：ex 天下雜誌調查資料、徵信社(有授權與應用課題需釐清)、[臺灣三千大企業資料](http://hackfoldr.org/gxv/Vif2RRMBe95)
- 中華徵信 [http://www.credit.com.tw/creditonline/cfcontent/book_web/index.cfm](http://www.credit.com.tw/creditonline/cfcontent/book_web/index.cfm)
- 個別公司所發行年報與公開資料：ex《台灣中油刊物》...
#### 關係文本

- 公開可搜尋的關係事實與文本：ex《總統的親戚》...
- 聯誼會：老牌[三三會](http://www.sansanfe.org.tw/index.php?target=about.php&sn=9)、中部[磐石會](http://realblog.zkiz.com/greatsoup38/53844)、[全國商業總會](http://zh.wikipedia.org/zh-tw/%E4%B8%AD%E8%8F%AF%E6%B0%91%E5%9C%8B%E5%85%A8%E5%9C%8B%E5%95%86%E6%A5%AD%E7%B8%BD%E6%9C%83) ... [https://www.facebook.com/ijintsai/posts/1786906621329056](https://www.facebook.com/ijintsai/posts/1786906621329056)
- 紅白場，訃聞資料，喜帖 ...
    - 基隆市無黨籍議員王醒之貼文談議員交際支出
        - https://udn.com/news/story/7328/3634150
- 場合資料：政商豪宅物業管理相關紀錄資料(頗要害也難浮上檯面，例如出入人士紀錄、行跡、公司與可疑機構、例郝伯村與仁愛敦南大樓..)，交誼場地(例如餐廳、酒店..)

#### 研究機構資料庫

- 中研院台灣政經結構變遷資料庫
    - [http://www.rchss.sinica.edu.tw/cibs_air/link.php](http://www.rchss.sinica.edu.tw/cibs_air/link.php)
    - 該資料庫由「中央研究院人文社科中心制度與行為專題中心」補助，陳恭平、徐永明等兩位教授負責規劃與執行。整個資料庫分別由﹙1﹚立委政治經歷資料庫﹙2﹚行政首長暨官僚資料庫兩個子資料庫所構成。立委政治經歷資料庫，主要收集第一～第七屆，在台灣透過民主選舉過程產生之立法委員，其個人的出生年、性別、籍貫、黨籍，以及從政經歷等資料。而行政首長暨官僚資料庫，收集一九八四～二零零九年間，行政院所屬一級行政機關，行政首長、次長，以及一九五一～二零零九年間，省直轄市長、省轄縣市長等行政首長資料，包括個人的出生年、性別、籍貫，以及中央、地方行政等經歷。兩個資料庫到目前為止已經建置完成，並且持續進行資料的增加與更新。
- 行政首長暨官僚資料庫
    - [http://www.rchss.sinica.edu.tw/cibs\_air/database3/index\_1.htm](http://www.rchss.sinica.edu.tw/cibs_air/database3/index_1.htm)
- 立法委員政治經歷資料庫
    - [http://www.rchss.sinica.edu.tw/cibs\_air/database1/index\_1.htm](http://www.rchss.sinica.edu.tw/cibs_air/database1/index_1.htm)

## 相關 g0v 專案 / g0v grant

政治人物 / 政商關係
- [人物關係圖](https://g0v.hackpad.com/ZPZKg4Coom0)
- [政商關係圖](https://g0v.hackpad.tw/hxJBK9v7frt)
- [開放政治獻金](https://g0v.hackpad.com/8ow2GnliH48) / [g0v cy 開放監察院 hackpad collection](https://g0v.hackpad.tw/ep/group/mgUOtpJUUSt) / [hackfoldr](http://hack.g0v.tw/g0v-cy)
- [立委投票指南](http://vote.ly.g0v.tw/) / [g0v ly collection](http://vote.ly.g0v.tw/)
- [透析貪污判決--揭露與查詢網站](https://g0v.hackpad.tw/--OoaenzjVDKK)
- [2014 政治家族候選人名單](https://g0v.hackpad.tw/2014-6tTa8onqqmQ)
企業研究
- [肥貓專案](http://hackfoldr.org/gxv/y4Fhms4cK5Q)
- [企業資料與汙染資料的鏈結](https://g0v.hackpad.tw/rInrPBeYd5I)
- [兩岸環境監督](https://g0v.hackpad.tw/cAbxJt2yt94)
- 台灣企業集團母子公司關係與環境社會責任
    - [https://g0v.hackpad.tw/mrLdO0LdB5P](https://g0v.hackpad.tw/mrLdO0LdB5P)
    - [https://grants.g0v.tw/projects/596c662fd60a0d001ed1f8ea](https://grants.g0v.tw/projects/596c662fd60a0d001ed1f8ea)
    - 摘：產出的API將會放在github 中供大家存取使用
        - 以集團為主的 JSON 樹狀檔案，一個集團一個檔案，檔名以集團ID命名，如果有500大集團，就有500個檔案。
        - 集團的子母階層 CSV 檔案，可能欄位是 根階層ID（母集團）、父階層ID（上一個關係企業）、企業ID、企業名稱、企業統編、企業股票代號... 等。
        - 集團清單 CSV 檔，可能欄位是 集團名稱、集團ID、集團統編、集團基本資料 ... 等。
- 移轉訂價年報檢索系統
    - [https://grants.g0v.tw/projects/59634490ae3dd8001e1bfd28](https://grants.g0v.tw/projects/59634490ae3dd8001e1bfd28)
    - 本專案希望可以建構一個開源全球英文年報檢索資料庫，讓國稅局或企業在衡量或規劃當年企業留在各國的利潤是否合理時，透過本資料庫找出業務性質相類似，承擔相同功能風險的10~20間公司，並進一步找出一個合理客觀的利潤區間。
- 政治人物行程探測雷達
    - [https://grants.g0v.tw/projects/5890af6a725c74001e8818b5](https://grants.g0v.tw/projects/5890af6a725c74001e8818b5)
    -  希望透過「政治人物行程探測雷達」平台，達成「政治人物行程透明化」的目標。一開始將先以立委為主要資料收集對象，未來擴大到總統、行政院長、六都首長等其他政治人物。以立委來說，我們會將立委的行程分成國會事務、地方事務及媒體公關活動等類型，透過行程分類、時間軸、行事曆等資訊視覺化的呈現方式，讓公民更容易檢視立委的行程、監督瞭解民意代表。在累積相當資料後，我們也將尋求政治評論者分析政治人物的行程，以評論報導的方式擴大影響力。

## 範例

初步歸納常見形式
* 族譜，血緣或姻親關係
* 互動關係圖
    * 圖表類
    * 資料互動網站
* 地圖
* 具體化，例如將企業贊助單位logo與該名政治人物

### 關係資料實作案例參考


台灣
- 「台灣政商集團聯姻局部示意圖」
    - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2709a597b6b0260b253453bbf000a54f)
    - [https://farm8.staticflickr.com/7344/14174868431\_09561f122e\_o.jpg](https://farm8.staticflickr.com/7344/14174868431_09561f122e_o.jpg)
    - [http://talkecon.com/party\_state\_capitalism/](http://talkecon.com/party_state_capitalism/)
- [票選十大鴨霸政治家族](http://taiwanlnversion.blogspot.tw/2014/11/3520333481248-112-1191110-1-l-l-l-2-l-l.html)： [2014政治家族候選人名單](https://g0v.hackpad.com/6tTa8onqqmQ#2014%E6%94%BF%E6%B2%BB%E5%AE%B6%E6%97%8F%E5%80%99%E9%81%B8%E4%BA%BA%E5%90%8D%E5%96%AE)
- 洪案人物關係圖：[http://zbryikt.github.io/ppllink/?542](http://zbryikt.github.io/ppllink/?542)
- 北市長參選人家世
    - 漫畫創作：[《北三都太子黨》](http://imgur.com/a/2lhaU)
- 【捲入戰火的人們（三）桃園中壢吳家】
    - [https://www.facebook.com/photo.php?fbid=10152340252973618&set=a.10151834790708618&type=3&theater](https://www.facebook.com/photo.php?fbid=10152340252973618&set=a.10151834790708618&type=3&theater)
- 立委二代接班 [http://topic.cw.com.tw/2015politicaldynasty/](http://topic.cw.com.tw/2015politicaldynasty/)
- 台灣政商集團聯姻局部示意圖：[https://www.facebook.com/linkourworld/posts/10153073643693218](https://www.facebook.com/linkourworld/posts/10153073643693218)
- [國內政府組織機構檔案的初步盤點](https://m.facebook.com/notes/%E5%BB%96%E5%BD%A5%E8%B1%AA/20151222%E9%97%9C%E6%96%BC%E5%9C%8B%E5%85%A7%E6%94%BF%E5%BA%9C%E7%B5%84%E7%B9%94%E6%A9%9F%E6%A7%8B%E6%AA%94%E6%A1%88%E7%9A%84%E5%88%9D%E6%AD%A5%E7%9B%A4%E9%BB%9E%E8%AC%9B%E7%A8%BF%E5%8F%B0%E5%A4%A7%E7%A4%BE%E6%9C%83%E7%B3%BB/10153817427842138/)
- 李宗榮, 2016, “企業權力與民主：台灣企業集團2008年立委選舉的政治獻金分析”, 台灣社會學, 31, 99-139.
    - [https://www.facebook.com/wearytolove/posts/10158910450800694](https://www.facebook.com/wearytolove/posts/10158910450800694)
- 遠通 <\- 遠傳 <\- 遠鼎投資 <\- [遠東新世紀](http://company-graph.g0v.ronny.tw/?id=03522600)（即遠紡） <-\> 亞泥
    - 徐元智 -\> [徐有庠](http://zh.wikipedia.org/wiki/%E5%BE%90%E6%9C%89%E5%BA%A0) -\> 徐旭東（[家族脈絡](http://www.coolloud.org.tw/node/24120)）
    - 注意：泥紙林礦特許業，上承耕者有其田，下接當前大財團的關係
- 日月光
    - 日月光張家：[https://newtalk.tw/news/view/2017-06-12/89075](https://newtalk.tw/news/view/2017-06-12/89075)
    - 日月光買矽品：[https://www.facebook.com/elielin/posts/10207455114950586](https://www.facebook.com/elielin/posts/10207455114950586)
- 日勝生集團關係圖：[http://company-graph.g0v.ronny.tw/?id=12373243](http://company-graph.g0v.ronny.tw/?id=12373243)
- 統一集團
    - 母控股公司[高權投資](http://company-graph.g0v.ronny.tw/?id=22267853)，㊣家庭企業
    - 高清愿的姨表姊賴蓮樵，是吳修齊元配[\[1\]](http://blog.ifeng.com/article/24635033.html)  [\[2\]](http://archive.is/bVAQn) -\> [吳三連](http://zh.wikipedia.org/wiki/%E5%90%B3%E4%B8%89%E9%80%A3)（政）、吳修齊、吳尊賢（台南幫，南紡、環泥；[第二代](http://realblog.zkiz.com/greatsoup38/54169)）
- 張作霖
    - [https://www.facebook.com/fengyi.chang/posts/10214794489478837](https://www.facebook.com/fengyi.chang/posts/10214794489478837)
- [邱文達、李祖德、張珩、楊原平、徐大麟...關係圖](https://www.facebook.com/photo.php?fbid=728954573843624&set=a.162786293793791.40993.100001872656795&type=1&theater) ，林淑芬製作
- 宜蘭縣羅許基金會
    - [監委被提名人許國文爭議](https://www.youtube.com/watch?v=68aIABLKfzA)
    - [宜蘭蜜月灣海岸國有土地開發](http://m.ltn.com.tw/news/life/breakingnews/1050581)
- [台東美麗灣開發案與德安開發股份有限公司代表人黃春發關係說明影片](http://youtu.be/0_2igDMI23s?t=2h12m16s) (中研院學者黃應貴發言)
    - 摘：「我的高中同學，美麗灣事件只是他旗下小公司在搞的事情，你永遠抓不到他，可是真正決策的是他，而且他影響了整個政府的政策，所以我來看根本搞錯了(『敵人』是政府或是資本的台下提問)，而且台東縣兩個候選人全部都是用他的政治援助，所以選上之後，不管是誰一定都支持他的政策，我可以保證。...他有辦法買下都蘭山三十幾甲地再把地目變更，設立企業總部...」
- 六都加新竹808位議員候選人117位具地產背景，囤房稅在議會能出頭嗎？ https://new7.storm.mg/article/4580677
- [台北縣現任議員(第13屆)從事營建相關行業一覽表](http://ago.gcaa.org.tw/issue/mountain/87011504.htm) (財訊雜誌1998年1月號)
- 中部地區黑派紅派關係圖
    - [https://www.facebook.com/Menfromyouth/photos/a.276015255833249.47263.109589515809158/1108121519289281/?type=3](https://www.facebook.com/Menfromyouth/photos/a.276015255833249.47263.109589515809158/1108121519289281/?type=3)
    - https://www.facebook.com/100002478118417/posts/1986298974796020/
    - 2020/01/16 從台中顏家輸到雲林張家，立委選舉重挫代表地方派系被殲滅了嗎？
        - https://www.thenewslens.com/article/130133
- 陳俞融https://www.facebook.com/share/p/zbpXPapfUYN5XoWP/
- 顏家企業 https://m.facebook.com/story.php?story_fbid=pfbid0ZSGUEdub8NYJ9XB8G7F7mgwDdQE3TrZuJQQsQMNUG35qqDvPYbtAwdpyVGLhUkLSl&id=140282406003843
- https://www.facebook.com/103032645529885/posts/113373044495845/
- 摘：根據廠商名冊，謝新興正是南彰化知名地方政治家族謝家成員，是甫成新科立委、「為母復仇」的國民黨立委謝衣鳳伯父
    - https://ec.ltn.com.tw/article/breakingnews/3052575
- 雲林女婿、政治素人韓國瑜
    - http://www.xmind.net/m/KXRJ
    - https://www.voicettank.org/single-post/2018/11/08/Han-Kou-yu-and-Heijin
- [談力霸集團王又曾家族企業的文章](http://www.coolloud.org.tw/node/3884) (殷乃平文章)
- [退輔會旗下事業董事長名單整理圖片](https://www.facebook.com/photo.php?fbid=10202692127970030&set=a.1387252527032.59599.1403610586&type=1&theater) (Pei-Jun Huang 整理)
- [邱文達, 李祖德, 張珩, 楊原平, 徐大麟...醫院醫材產業關係圖](https://www.facebook.com/photo.php?fbid=728954573843624&set=a.162786293793791.40993.100001872656795&type=1&theater) (林淑芬製作)
- [頂新違法版圖關係圖](https://www.facebook.com/linshufen.tw/posts/806702649402149:1) (林淑芬製作)
- [萬海陳氏八仙家族](https://www.facebook.com/photo.php?fbid=10153204117362639&set=a.10150626112292639.394426.502652638&type=1) (Torrent Pien 製作)
- 國內外品牌名稱關聯
    - [https://goo.gl/CDTdK0](https://goo.gl/CDTdK0)
- 臺南市焚化爐底渣處理議題
    - [https://www.facebook.com/huannjang.hwang/posts/1165988960127172](https://www.facebook.com/huannjang.hwang/posts/1165988960127172)
- 彰化溪洲「謝許英文化藝術基金會」
    - [https://www.facebook.com/sidelight/posts/2276196979060945](https://www.facebook.com/sidelight/posts/2276196979060945)
- 永豐何家與基隆顏家
    - [https://www.mirrormedia.mg/story/20170411fin013/](https://www.mirrormedia.mg/story/20170411fin013/)
- （連結失效）
    - [https://www.facebook.com/armigil/posts/10211211268145652](https://www.facebook.com/armigil/posts/10211211268145652)
- https://www.facebook.com/100000133181724/posts/2405222162825533/
- 邱茂男之女邱議瑩，其阿公，也就是邱茂男的爸爸，已經是屏東地方政治人物，當過屏東市長。
    - [https://www.facebook.com/tzyhao/posts/10210946825971606](https://www.facebook.com/tzyhao/posts/10210946825971606)
- 政治世家的新聞
    - [http://news.ltn.com.tw/news/politics/paper/549876](http://news.ltn.com.tw/news/politics/paper/549876)
- [登報說明參與中國閱兵典禮的彭蔭剛以及他的兩岸關係](https://www.facebook.com/photo.php?fbid=901964616592477&set=a.103352273120386.4053.100003368404056&type=1&theater) (王醒之整理)
- 台塑的海外關係企業組織圖
    - [http://mops.twse.com.tw/nas/t10img/13012012.pdf](http://mops.twse.com.tw/nas/t10img/13012012.pdf)
- [https://www.facebook.com/legal.taiwan/posts/1552833814774157](https://www.facebook.com/legal.taiwan/posts/1552833814774157)
- [http://www.cw.com.tw/article/article.action?id=5086097](http://www.cw.com.tw/article/article.action?id=5086097)
- [https://m.facebook.com/notes/%E5%8D%9E%E4%B8%AD%E4%BD%A9/%E6%94%BF%E6%B2%BB%E7%8D%BB%E9%87%91%E8%B3%87%E6%96%99%E6%8C%96%E5%87%BA%E4%BB%80%E9%BA%BC%E8%99%B9%E8%86%9C%E7%94%9F%E7%89%A9%E8%BE%A8%E8%AD%98%E8%8D%89%E6%A1%88%E8%83%8C%E5%BE%8C%E7%9A%84%E6%94%BF%E5%95%86%E9%97%9C%E4%BF%82%E9%96%80%E9%81%93/10155438440707639/](https://m.facebook.com/notes/%E5%8D%9E%E4%B8%AD%E4%BD%A9/%E6%94%BF%E6%B2%BB%E7%8D%BB%E9%87%91%E8%B3%87%E6%96%99%E6%8C%96%E5%87%BA%E4%BB%80%E9%BA%BC%E8%99%B9%E8%86%9C%E7%94%9F%E7%89%A9%E8%BE%A8%E8%AD%98%E8%8D%89%E6%A1%88%E8%83%8C%E5%BE%8C%E7%9A%84%E6%94%BF%E5%95%86%E9%97%9C%E4%BF%82%E9%96%80%E9%81%93/10155438440707639/)
- 台塑的海外關係企業組織圖
    - http://mops.twse.com.tw/nas/t10img/13012012.pdf
- 運用網絡分析探討政策掮客在政策過程中的角色：以解嚴前後台中市都市發展為分析案例
    - [http://www.airitilibrary.com/Publication/alDetailedMesh?DocID=10281649-201404-201406060041-201406060041-31-88](http://www.airitilibrary.com/Publication/alDetailedMesh?DocID=10281649-201404-201406060041-201406060041-31-88)
- https://www.facebook.com/shigosanTemple/posts/1959310034150821
- 用政治人物合影照片，來標註該政治人物的判刑紀錄
    - https://www.ptt.cc/bbs/Gossiping/M.1535895096.A.CD7.html
- 談「公務員財產來源不明罪」
    - https://www.facebook.com/legal.taiwan/posts/1552833814774157
- 專題報導《數據看天下》揭露2016立委選舉5大金主：遠東、裕隆、台泥、潤泰、仰德
    - http://www.cw.com.tw/article/article.action?id=5086097
- 政治獻金資料挖出什麼〈虹膜生物辨識草案〉背後的政商關係門道
    - https://ppt.cc/fpb2Zx
- 企業聯姻 研究
    - https://www.facebook.com/100004299135381/posts/2238477966305486/
- 霧峰林家
    - https://www.facebook.com/661878810493340/posts/2846322998715566/

香港
- [http://www.vjmedia.com.hk/articles/2018/01/04/174846/%E8%B2%B7%E6%A8%93%E6%85%8E%E5%85%A5%EF%BC%8C%E6%9C%89%E5%9C%96%E6%8F%AD%E9%9C%B2%E6%94%BF%E5%95%86%E9%BB%91%E5%9C%8D%E6%A8%99%E7%8E%8B%E5%9C%8B/](http://www.vjmedia.com.hk/articles/2018/01/04/174846/%E8%B2%B7%E6%A8%93%E6%85%8E%E5%85%A5%EF%BC%8C%E6%9C%89%E5%9C%96%E6%8F%AD%E9%9C%B2%E6%94%BF%E5%95%86%E9%BB%91%E5%9C%8D%E6%A8%99%E7%8E%8B%E5%9C%8B/)

中國
- 中國君主家族樹
    - https://www.facebook.com/toku1325/posts/10211068043358935
- [WSJ 互動數據圖：中國富豪們的參政狀況](http://cn.wsj.com/big5/20130108/PHO161748.asp)（需登入）
- [周永康案關係圖](http://datanews.caixin.com/2014/zhoushicailu/) by [财新数据新闻与可视化实验室 | Data Journalism & Visualization Lab](http://datanews.blog.caixin.com/)
- 海航及关联人物／公司在美房产分布图和列表
    - [http://chinadigitaltimes.net/chinese/2017/08/%E6%B5%B7%E8%88%AA%E5%8F%8A%E5%85%B3%E8%81%94%E4%BA%BA%E7%89%A9%EF%BC%8F%E5%85%AC%E5%8F%B8%E5%9C%A8%E7%BE%8E/](http://chinadigitaltimes.net/chinese/2017/08/%E6%B5%B7%E8%88%AA%E5%8F%8A%E5%85%B3%E8%81%94%E4%BA%BA%E7%89%A9%EF%BC%8F%E5%85%AC%E5%8F%B8%E5%9C%A8%E7%BE%8E/)
- KK 園區
    - https://www.facebook.com/share/p/1BCob5KRye/?mibextid=wwXIfr

亞洲
- [SINGAPORE’S STRAITS CHINESE BANKING FAMILIES 新加坡海峡华人银行家族](http://thehearttruths.com/2014/09/10/singapores-straits-chinese-banking-families-%e6%96%b0%e5%8a%a0%e5%9d%a1%e6%b5%b7%e5%b3%a1%e5%8d%8e%e4%ba%ba%e9%93%b6%e8%a1%8c%e5%ae%b6%e6%97%8f/) (Roy Ngerng Yi Ling 鄞义林製作)
- [Who owns Malaysia's key telcos?](https://www.facebook.com/theedgemalaysia/photos/a.10153411955793086.1073741830.64839963085/10155756868208086/?type=3)
- https://medium.com/@kaerumy/image-corpus-of-malaysian-peps-5ae3bee7d273

美國
- ClintonCircle
    - [https://clinton.media.mit.edu/clinton](https://clinton.media.mit.edu/clinton)
    - How do you construct these networks? For all three networks, nodes (a.k.a. circles) are people and links (a.k.a. lines) between nodes indicate that two people were on a common e-mail thread. The size of a node shows the number of e-mail threads in which a person participated. The size of a link denotes the number of shared e-mail threads between two people. Each node is algorithmically assigned to a community (a group with a disproportionately large number of links among them), which is shown by node color.
- Astoundingly Complex Visualization Untangles Trump’s Business Ties
    - [https://www.wired.com/2017/01/kim-albrecht-trump-data-viz/](https://www.wired.com/2017/01/kim-albrecht-trump-data-viz/)

國際間
- TPP , RECP , 東協 各組織成員國關係圖：
    - [http://www.likawind.com/WebDataVis/Pages/Test\_d3js\_0007\_01\_n01.html](http://www.likawind.com/WebDataVis/Pages/Test_d3js_0007_01_n01.html)
- LittleSis
    - [http://littlesis.org/about](http://littlesis.org/about)
    - source：[https://github.com/littlesis-org/littlesis](https://github.com/littlesis-org/littlesis)
    - **機構**、**人物**、**公司**：[http://littlesis.org/map/101](http://littlesis.org/map/101)
    - **戰爭事件**，也成為一個項目：[http://littlesis.org/maps/238-updated-stephen-hadley-and-the-ministry-of-peace](http://littlesis.org/maps/238-updated-stephen-hadley-and-the-ministry-of-peace)
- Panama Papers: Who were the big players?
    - [http://www.taxjustice.net/2017/04/03/panama-papers-big-players/](http://www.taxjustice.net/2017/04/03/panama-papers-big-players/)
- Influence Explorer：[http://influenceexplorer.com/industries](http://influenceexplorer.com/industries)
- Linked Jazz
    - [https://linkedjazz.org/](https://linkedjazz.org/)
    - At the heart of our work are oral histories of jazz musicians. We are currently expanding our data sources to include other document types and music-related datasets.
- [http://dailynous.com/2018/07/18/digital-maps-spinozas-ethics/](http://dailynous.com/2018/07/18/digital-maps-spinozas-ethics/)

### 多元形式

地圖

- Partying for dollars: Mapping five years of political fundraisers 政商聚會交流的地圖化
    - [https://sunlightfoundation.com/2013/09/16/partying-for-dollars-mapping-five-years-of-political-fundraisers/](https://sunlightfoundation.com/2013/09/16/partying-for-dollars-mapping-five-years-of-political-fundraisers/)
    - 資料來源：Sunlight’s Party Time - Upload an Invitation
        - [http://politicalpartytime.org/](http://politicalpartytime.org/)
        - 民眾匿名提供政黨與政治人物的活動訊息與邀請函，如宴會、餐會、募款活動資訊...等
- 摘：政府官員會去吃的地方，應該是很好吃的吧！於是 SL Kim 做了一個專案，將政府官員吃飯的發票做成了地圖，還有金額可以供參考。 
    - https://www.facebook.com/100014990599426/posts/605724659937215
- 金庸迷繪製的武俠地圖，除了地點外還有人物移動路線 ex: 萧峰阿朱追踪大恶人路线
    - 地圖說明：[https://zhuanlan.zhihu.com/p/35867449](https://zhuanlan.zhihu.com/p/35867449)
    - 地圖網址：[https://www.ageeye.cn/map/12518/#6/35.836/108.699](https://www.ageeye.cn/map/12518/#6/35.836/108.699)

政治獻金贊助具現化

- 加州非賣品 [CaliforniaIsNotForSale.com](http://californiaisnotforsale.com/)
    - [https://www.facebook.com/amos.yang.104/posts/1634114863505505](https://www.facebook.com/amos.yang.104/posts/1634114863505505)
    - 摘：他們的提案: "當政客發言時，強制政客穿戴他們十大贊助者的標幟（就像 NASCAR 駕駛員穿戴他贊助者的標幟一樣！）" 他們的戰術: 利用加州的「投票提案(ballot initiative)」機制，只要有足夠的簽名連署與支持票，提案就會成為法案
- [Representative John Boehner Top 20 Contributors](http://www.upworthy.com/exposed-gop-speaker-of-the-house-john-boehner-in-racing-gear-i-feel-sick)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a6f719318dd81d63572f6998e2c8a9ce)

### 資料研究

- 《集團化公司治理與財經犯罪預防》
    - [https://g0v.hackpad.tw/ggmUFj7nbuK](https://g0v.hackpad.tw/ggmUFj7nbuK)
- 貪污與跨國投資---貪污類別和投資來源的進一步分析
    - [https://www.grb.gov.tw/search/planDetail?id=1582857&docId=271176](https://www.grb.gov.tw/search/planDetail?id=1582857&docId=271176)
- 貪腐相關因素分析：地理加權迴歸的應用
    - [https://www.grb.gov.tw/search/planDetail?id=8311247&docId=438708](https://www.grb.gov.tw/search/planDetail?id=8311247&docId=438708)
- Gilbert's Data Lab [http://weichengliou.github.io/blog](http://weichengliou.github.io/blog)：[黨營事業知多少](http://weichengliou.github.io/blog/blog/2014/08/09/kmtnew/)、 [KMT Property](https://g0v.hackpad.com/87CNswL2g7U)


人物歷史學的研究方法

- [中國歷代人物傳記資料庫（CBDB）](http://isites.harvard.edu/icb/icb.do?keyword=k35201)：將傳記、人物互動關係資料...，建置成跨國共享的資料庫。
    - [CBDB User's Guide in Chinese: 中國歷代人物傳記資料庫用戶指南.pdf](http://isites.harvard.edu/fs/docs/icb.topic1080142.files/%E4%B8%AD%E5%9C%8B%E6%AD%B7%E4%BB%A3%E4%BA%BA%E7%89%A9%E5%82%B3%E8%A8%98%E8%B3%87%E6%96%99%E5%BA%AB%E7%94%A8%E6%88%B6%E6%8C%87%E5%8D%97.pdf)，其中談到關係資料的結構。
    - 包弼德谈哈佛中国历代人物数据库 [http://www.thepaper.cn/baidu.jsp?contid=1419136](http://www.thepaper.cn/baidu.jsp?contid=1419136)
- TBDB 構想探討
    - 中國史的領域已經受益於 China Biographical Database 中國歷代人物傳記資料庫（CBDB）多多，陸陸續續有越來越多基於 CBDB 的研究出現。在台灣文史方面，如何也能建置類似的資料庫，來促進相關的研究，是一個值得思考的問題。有興趣利用數位工具、資料庫來進行台灣文史研究的朋友，歡迎報名產加。給我們建議、批評、指教，與我們一起打造TBDB，開創一些可能的研究、教學新途徑。
    - [http://tadh.org.tw/index.php/2017/04/27/tbdb/](http://tadh.org.tw/index.php/2017/04/27/tbdb/)
    - [https://drive.google.com/file/d/0B_FdoTA4ll-wWHpGTTVQV3FkbDA/view?usp=sharing](https://drive.google.com/file/d/0B_FdoTA4ll-wWHpGTTVQV3FkbDA/view?usp=sharing)
- 清代《缙绅录》資料庫
    - [http://vis.cse.ust.hk/](http://vis.cse.ust.hk/)
-  習近平語錄資料
    - [http://jhsjk.people.cn/](http://jhsjk.people.cn/)


## 資源與機構

媒體
- [hychen](http://logbot.g0v.tw/channel/g0v.tw/2014-06-08#446)：可以順便申請open news的財務補助 [http://opennews.org/hackdays.html](http://opennews.org/hackdays.html)
- [财新数据新闻与可视化实验室 | Data Journalism & Visualization Lab](http://datanews.blog.caixin.com/)
    - 曾製作專題： [周永康案關係圖](http://datanews.caixin.com/2014/zhoushicailu/)，處理人名與介紹、企業關係
    - 開發想法：[《Empire Building》数据可视化项目的开发思路文章](http://datanews.blog.caixin.com/?p=203)，"整个项目是基于HTML5的Canvas技术开发的，没有用到其它第三方可视化库。"
    - 先丟一些連繫要點：
        - 詢問：是否有意願將此工具，開放出來，給更多人使用 ?
        - 詢問：程式碼是否願意 open ?
        - 詢問：
            - 「義父母」、「緋聞對象」、「私生」也是以關係類別來處理 ?
            - 「時間」要素如何展現 ?
            - 是否考慮發揮「地理位置」要素，例如台灣有很明顯的地方派系 ?
            - 是否考慮追查國企與公共支出的關係 (OpenSpending) ?
            - 分享觀點：[從台資與台商「登陸」歷史思索兩岸服貿協議](http://www.coolloud.org.tw/node/75216)
            - 分享好書：chewei 願意送書《總統的親戚》一本
            - 邀請協作：[http://hackfoldr.org/gxv](http://hackfoldr.org/gxv)

學術
- 中央研究院社會學研究所｜社會與企業主題研究小組 ([http://www.ios.sinica.edu.tw/ios/?pid=6](http://www.ios.sinica.edu.tw/ios/?pid=6))
    - 召集人：李宗榮
    - 成員：張晉芬、呂玉瑕、鄭陸霖、謝斐宇、熊瑞梅、陳明祺、鄭力軒、林宗弘、川上桃子
- 演講題目：解構家族資本主義：台灣家族企業的聯姻與政治獻金之研究
    - https://www.facebook.com/csrsurvey.taiwan/posts/2932333693704790
- 家族法與家族史的研究交流
    - [https://www.facebook.com/legalhistorytw/photos/a.315521245321461.1073741829.315116678695251/441611442712440/?type=3&theater](https://www.facebook.com/legalhistorytw/photos/a.315521245321461.1073741829.315116678695251/441611442712440/?type=3&theater)



## 國際相關專案

### Project / Database / Revealing

- [LittleSis](https://littlesis.org/) \- LittleSis* is a free database of who-knows-who at the heights of business and government.
- EveryPolitician http://everypolitician.org/
- Political Database of the Americas (PDBA) - [http://pdba.georgetown.edu/](http://pdba.georgetown.edu/)
- The Latin American Databank (LAD) - [http://ropercenter.cornell.edu/latin-american/latin-american-databank.html](http://ropercenter.cornell.edu/latin-american/latin-american-databank.html)
- [PopIt](http://popit.poplus.org/) ([Poplus](http://poplus.org/)) \- Store and share lists of politicians  ([video](http://youtu.be/LqOjzhYHkhI?t=10m40s))
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_760cb117420ab167840592c9426b91ce)
- [https://www.facebook.com/groups/d4sg.taiwan/permalink/1817589631850954/](https://www.facebook.com/groups/d4sg.taiwan/permalink/1817589631850954/)
- [Investigative Dashboard](http://investigativedashboard.org/) \- Investigative Dashboard helps investigators expose illicit ties that cross borders.
- [Explore Campaign Finance](https://www.kickstarter.com/projects/12095995/explore-campaign-finance) by [Solomon Kahn](https://www.kickstarter.com/projects/12095995/explore-campaign-finance/creator_bio)
- [Influence Explorer](http://influenceexplorer.com/) \- Our data is provided by the [Center for Responsive Politics](http://www.opensecrets.org/), the [National Institute for Money in State Politics](http://www.followthemoney.org/), [Taxpayers for Common Sense](http://taxpayer.net/), the [Project On Government Oversight](http://www.pogo.org/), the[EPA](http://www.epa-echo.gov/echo/) and [USASpending.gov](http://www.usaspending.gov/).
- The Center downloaded 850,000 forms from about 250,000 nonprofits that were recently released in electronic format by the IRS; we extracted the grant data and made $170 billion reported over five years searchable.
    - [https://www.publicintegrity.org/2016/08/03/20027/new-search-tool-traces-sources-dark-money](https://www.publicintegrity.org/2016/08/03/20027/new-search-tool-traces-sources-dark-money)
- Follow the Money 
    - https://alephdata.github.io/followthemoney/
    - https://www.facebook.com/groups/odtwn/permalink/2908875692460163/
- OpenSanctions 
    - https://www.opensanctions.org/
    - https://www.facebook.com/groups/odtwn/permalink/2908875692460163/
- [OpenInterests.eu](http://www.openinterests.eu/) \- Who has financial or political interests in the European institutions?
- [Fundación Ciudadana Civio](http://quienmanda.es/) \- Envíanos imágenes que muestren vínculos entre empresarios y políticos para nuestro fotomandón o sugiere historias interesantes. Escríbenos a[contacto@civio.es](mailto:contacto@civio.es). (西班牙，上傳政商圖片介紹政商故事)
    - [\[Open Data x Open Gov x g0v\] clkao 環球考察分享會 (全)](http://youtu.be/MMLTaq-Ycw4?t=1h27m38s) 1:27:54
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bfe990ba26d4dc7eb40b2f4a7c929b74)
- [K-Monitor](http://k-monitor.hu/) \- A K-Monitor Független Közpénzfigyelő Iroda a közpénzek elköltésének átláthatóságáért küzdő civil szervezet. (匈牙利)
- [Poderopedia](http://www.poderopedia.org/) \- Quién es quién en los negocios y la política en Chile, Colombia, Venezuela y contando. (中南美洲)
- [In](https://interest/)[spector de Intereses](http://www.inspectordeintereses.cl/) \- [簡介投影片](http://slidesha.re/1v8TRUv)by Felipe Álvarez、[直播錄影](http://bit.ly/1v8TQjk) (智利)
- [Gasto Público](http://www.gastopublico.cl/) \- ¿Cómo distribuye nuestro gobierno el impuesto que se descuenta mes a mes en tu sueldo? (智利，稅與薪資的匿名調查)
- 緬甸公司登記資料，以及 opencorporates API：[https://www.globalwitness.org/reports/myanmarjade/](https://www.globalwitness.org/reports/myanmarjade/) (緬甸，軍方、毒販、執政黨、玉石產業..)
- **CCP Elite Database (中共精英资料库)** [http://www.jonghyuklee.com/home](http://www.jonghyuklee.com/home)
- 《太子党关系网络》、趙家人 
    - https://www.facebook.com/theinitium/posts/631596077016948
    - https://github.com/programthink/zhao
    - 『赵家人俱乐部』https://ZhaoJiaRen.Club
- 韓國
    - https://newstapa.org/
    - https://data.newstapa.org/
- Pacific civil society organizations discuss anti-corruption reforms
    - [https://sinarproject.hackpad.com/Anti-Corruption-Workshop-for-Pacific-CSOs-Fiji-13yLgF2k00h](https://sinarproject.hackpad.com/Anti-Corruption-Workshop-for-Pacific-CSOs-Fiji-13yLgF2k00h)
    - https://www.unodc.org/southeastasiaandpacific/en/2015/12/pacific-anti-corruption/story.html
- [Grano](http://granoproject.org/) \- Map influence in government and business. Grano is an open source tool for journalists and researchers who want to track networks of political or economic interest. It helps understand the most relevant relationships in your investigations, and to merge data from different sources.
- [MapLight](http://maplight.org/corework) \- Revealing money's influence on politics
- [Partying for dollars: Mapping five years of political fundraisers](http://sunlightfoundation.com/blog/2013/09/16/partying-for-dollars-mapping-five-years-of-political-fundraisers/) 政商密會交流的地圖化；資料來源：[Sunlight’s Party Time - Upload an Invitation](http://politicalpartytime.org/) 民眾匿名提供政黨與政治人物的活動訊息與邀請函，如宴會、餐會、募款活動資訊...等
- [opencorporate](http://opencorporates.com/) \- The Open Database Of The Corporate World
- [Represent.Us](https://represent.us/) \- We’re building the movement to end corruption
- [Global Witness](http://new.globalwitness.org/) \- We find facts, We uncover the story, We change the system
- [The Organized Crime and Corruption Reporting Project (OCCRP)](https://reportingproject.net/occrp/index.php/en/about-us) \- The Organized Crime and Corruption Reporting Project (OCCRP) is a not-for-profit, joint program of a number of regional non-profit investigative centers and for profit independent media stretching from Eastern Europe to Central Asia.
- [The World Top Incomes Database](http://topincomes.g-mond.parisschoolofeconomics.eu/) \- The World Top Incomes Database Geographic Coverage
- [Small Arms and Ammunition - Imports & Exports](http://arms.dat-friends.appspot.com/) \- the global trade in ammunition rivals the global trade in actual weapons, and how the arms trade relates to specific conflicts worldwide. ([https://github.com/dataarts/armsglobe](https://github.com/dataarts/armsglobe))
- [The Observatory of Economic Complexity](http://atlas.media.mit.edu/) \- The Observatory of Economic Complexity was developed by [Alex Simoes](http://www.datawheel.us/company/) and [Cesar Hidalgo](http://www.datawheel.us/company/) at MIT, and visualizes over 50 years of UN Comtrade data. It is a tool that allows users to quickly compose a visual narrative about countries and the products they exchange. The site provides new ways of viewing world trade data by introducing new statistical measures and a new type of network visualization, The Product Space.
- [https://www.facebook.com/uxbackpacker/posts/696061123868724](https://www.facebook.com/uxbackpacker/posts/696061123868724)
- 【逃稅的體驗設計】犯罪一向都是最強的體驗設計....來看看世界逃稅地圖吧。
    - https://www.facebook.com/uxbackpacker/posts/696061123868724
- [Wikileaks](http://wikileaks.ch/), [台灣相關文件](http://billypan.com/wiki/%E9%A6%96%E9%A0%81)
- [https://www.facebook.com/OCCRP.org/](https://www.facebook.com/OCCRP.org/)
- How France’s Linkurious helped reporters use data visualization to make sense of the Panama Papers
    - [http://www.rudebaguette.com/2016/04/07/how-tech-enabled-journalists-to-sift-through-2-6-tb-of-raw-data/](http://www.rudebaguette.com/2016/04/07/how-tech-enabled-journalists-to-sift-through-2-6-tb-of-raw-data/)
- [https://www.facebook.com/592510510/posts/10160440254040511/](https://www.facebook.com/592510510/posts/10160440254040511/)

### Open Government Spending

- [OpenSpending](https://openspending.org/) \- By understanding how governments spend money in our name can we have a say in how that money will affect our own lives. The journey starts here.
- [Tender Monitor](http://tendermonitor.ge/en/root/about) \- Tender Monitor provides the public with an in-depth look at government spending in Georgia by making detailed information about state procurement available. (喬治亞)

### Constitution

- [Constitute](https://www.constituteproject.org/#/) \- The World's Constitutions to Read, Search, and Compare

### Tools

- https://kumu.io/tour
- Visualization Tools for Investigators.
    - [https://vis.occrp.org/](https://vis.occrp.org/)
    - a graph visualization library using web workers and jQuery
    - 一個主要做關連（關係）圖的視覺化平台
- Onodo
    - [https://onodo.org/](https://onodo.org/)
- arborjs
    - [http://arborjs.org](http://arborjs.org)
    - a graph visualization library using web workers and jQuery
- HTML5版圖形Graph繪製工具
    - [https://www.facebook.com/ComputerScienceTT/posts/1454612884650636](https://www.facebook.com/ComputerScienceTT/posts/1454612884650636)
- [Untangled](http://untangled.knightlab.com/) \- Social Network Analysis for Journalism. Analyzing social networks has always been fundamental to journalism. New technology makes it even easier. Untangled will help you understand it.
    - [Tools](http://untangled.knightlab.com/tools.html) : Search tools and databases to do your own network analysis
    - [Investigations](http://untangled.knightlab.com/investigations.html) : Explore stories and news apps based on network analysis
    - [Readings](http://untangled.knightlab.com/readings.html) : Learn more through original case studies and suggested books and articles
- [S&P Capital IQ](https://www.capitaliq.com/) \- S&P Capital IQ is the powerful new combination of offerings previously provided by Capital IQ, elements of S&P including Global Credit Portal and MarketScope Advisor, enterprise solutions such as S&P Securities Evaluations and Compustat, research offerings including Leveraged Commentary & Data, Global Markets Intelligence, and company and fund research. To learn more about S&P Capital IQ and our additional offerings
- [Network Mapper](http://www.google.com/ideas/projects/network-mapper/) (Google ideas) - Mapping power networks. Mapping out and visualizing the connections between people and groups can dramatically improve our understanding of the affiliations and key nodes of influence between them.
- [Sinar Project](https://www.facebook.com/sinarproject/photos/a.495271137305754.1073741828.494376390728562/506024489563752/?type=3&theater)：
    - [http://poplus.org/posts/popit-central-to-malaysian-transparency-efforts](http://poplus.org/posts/popit-central-to-malaysian-transparency-efforts)
    - [https://www.facebook.com/sinarproject/photos/a.495271137305754.1073741828.494376390728562/506024489563752/?type=3&theater](https://www.facebook.com/sinarproject/photos/a.495271137305754.1073741828.494376390728562/506024489563752/?type=3&theater)
- 基于HTML5的Canvas技术（[《Empire Building》数据可视化（开发总结）](http://datanews.blog.caixin.com/?p=203)）
- MS Accces （參考 [中國歷代人物傳記資料庫（CBDB）](http://isites.harvard.edu/icb/icb.do?keyword=k35201)，定義出欄位，累積關係資料）
- EXCEL 外掛 [NodeXL](http://nodexl.codeplex.com/)（[教學](http://www.slideshare.net/beckett53/nodexl), [NodeXL Tutorial](https://www.youtube.com/watch?v=pwsImFyc0lE&feature=youtube_gdata_player), 不懂可問 yhsiang XD）
- Gephi
    - [https://gephi.org](https://gephi.org)
    - [https://youtu.be/zayMkF32k7Q](https://youtu.be/zayMkF32k7Q)
    - [https://youtu.be/2iLdFTcyVYA](https://youtu.be/2iLdFTcyVYA)
- Pajek (可用於網絡分析圖)
- UCINET (可用於網絡分析，資料少則 ok)
- [https://www.facebook.com/permalink.php?story_fbid=1219901598105397&id=151485241613710](https://www.facebook.com/permalink.php?story_fbid=1219901598105397&id=151485241613710)
- 族譜繪製工具蒐集頁面：[http://yesdaring.tripod.com/intro_genpro20040106.htm](http://yesdaring.tripod.com/intro_genpro20040106.htm)
- 「如何描述一位人，欄位有哪些？」
    - A person (alive, dead, undead, or fictional). [http://schema.org/Person](http://schema.org/Person)

### Event/Action/Idea

- [2014 Popluscon : Mapping/modeling relationships (between people) ](https://popluscon.hackpad.com/Mappingmodeling-relationships-between-people-2n0MfHg5SyB)
    - Goal / What types of relationships do we care about? / What do we want to be able to say about these relationships? / Use cases
- [StampStampede](http://www.stampstampede.org/) \- StampStampede is project of People Power Initiatives, a Vermont based nonprofit organization. Our 501c3 fiscal sponsor is the International Forum on Globalization, based in San Francisco.  Every dollar you stamp will reach 875 people, if you stamp 5 dollars a day for a year, that's over a million. Together, we can create a stampede that Congress can't ignore.
- [Representative John Boehner Top 20 Contributors](http://www.upworthy.com/exposed-gop-speaker-of-the-house-john-boehner-in-racing-gear-i-feel-sick)
- The Trump Archive
    - [http://archive.org/details/trumparchive&tab=collection](http://archive.org/details/trumparchive&tab=collection)
    - The Trump Archive collects TV news shows containing debates, speeches, rallies, and other broadcasts related to President-elect Donald Trump. This evolving non-commercial, searchable collection is designed to preserve the historical record for posterity.
- 「貪污一日遊」：墨西哥城與布拉格的另類觀光
    - [https://theinitium.com/article/20170402-dailynews-corruptour/](https://theinitium.com/article/20170402-dailynews-corruptour/)

## 書單、閱讀材料

> [facebook 後勤中心](https://www.facebook.com/groups/g0v.general/permalink/558807730862304/)
> [name=venev]

### 台灣

- 《台灣地方派系調查專報》，內政部調查局 1952
- 《台灣地方政治的變遷與特質》，作者趙永茂 2002
- 《台灣風雲人物》，卜少夫 [https://www.facebook.com/yenhao.liao/posts/1320902134591411](https://www.facebook.com/yenhao.liao/posts/1320902134591411)
- 天下雜誌 462 期（ 2010/12）專題：[血脈、人脈、錢脈交織華麗一族](http://www.cw.com.tw/article/article.action?id=5006676)
- [政大台灣企業史資料庫：各期電子報](http://bh.nccu.edu.tw/epapers.html)：台灣企業史料、台灣家族企業
- 中華徵信所所編纂之《臺灣地區企業集團匯編》，以及《臺灣地區集團企業研究》
- [《土地、財團、選舉》](http://www.books.com.tw/products/0010194229) 天下編輯群, 1990
- 《台灣營造業百年史》
- 《紡古織今：臺灣紡織成衣業的發展》[https://readmoo.com/book/210076513000101](https://readmoo.com/book/210076513000101)
- [《總統的親戚：揭開台灣權貴家族的臍帶與裙帶關係》](http://www.books.com.tw/products/0010514053)陳柔縉, 2011 ([本書內容討論筆記區](https://g0v.hackpad.com/DI1m03CzBl1))
- [〈台灣企業間的親屬網絡〉](https://www.dropbox.com/s/7kvab5cgq3ku6vz/%E3%80%88%E5%8F%B0%E7%81%A3%E4%BC%81%E6%A5%AD%E9%96%93%E7%9A%84%E8%A6%AA%E5%B1%AC%E7%B6%B2%E7%B5%A1%E3%80%89%E6%9D%8E%E5%AE%97%E6%A6%AE_%E8%A3%9C%E5%85%85%E3%80%8A%E7%B8%BD%E7%B5%B1%E7%9A%84%E8%A6%AA%E6%88%9A%E3%80%8B.pdf)中研院社會學研究所李宗榮
- [協力網絡與生活結構 台灣中小企業的社會經濟分析](https://www.facebook.com/photo.php?fbid=10154395227354038&set=gm.1777272529151783&type=3&theater)
- [《台灣戰後經濟分析》](http://www.books.com.tw/products/0010531679)〈終章 總過程－官商資本的結構與運動〉劉進慶, 2012
- 國家發展委員會，[法規鬆綁建言平台](http://law.ndc.gov.tw/index.aspx)，[國發會法制協調](http://www.ndc.gov.tw/m1.aspx?sNo=0000128#.VBMplPmSw-8)（外商建言及協調 ‧ 歐洲在台商務協會 ‧ 台北市美國商會 ‧ 台北市日本工商會 ‧ 主要推動成果 \* 國內工商建言及協調 ‧ 全國工業總會建言書及協調 ‧ 國內工商團體建言及協調）
- [《解構黨國資本主義》](http://ts.yam.org.tw/ts_old/critical2004/party-media/index.htm)，陳師孟等，1991。
- [《法人刑事法―實體、程序與沒收新法》研討會](https://www.facebook.com/taiwanlawsociety.org.tw/posts/792112627555379)

### 香港與東亞

- [《官商同謀——香港公義私利的矛盾》](http://www.enrichculture.com/bk/275/%E3%80%8A%E5%AE%98%E5%95%86%E5%90%8C%E8%AC%80%E2%80%94%E2%80%94%E9%A6%99%E6%B8%AF%E5%85%AC%E7%BE%A9%E7%A7%81%E5%88%A9%E7%9A%84%E7%9F%9B%E7%9B%BE%E3%80%8B.htm)顧汝德（Leo Goodstadt）,2011
- https://www.facebook.com/100002620142695/posts/4252945984802698/
- [《東南亞華人史》](http://www.kingstone.com.tw/book/book_page.asp?kmcode=2016380002631&lid=search&actid=wise)李恩涵, 2003
- 《亞洲教父：透視香港與東南亞的金權遊戲》周博 （Joe Studwell）, 2010
    - [https://pan.baidu.com/share/link?shareid=3733804837&uk=2265966056&errno=0&errmsg=Auth+Login+Sucess&&bduss&ssnerror=0](https://pan.baidu.com/share/link?shareid=3733804837&uk=2265966056&errno=0&errmsg=Auth+Login+Sucess&&bduss&ssnerror=0)
    - [http://www.books.com.tw/products/0010458090](http://www.books.com.tw/products/0010458090)
- [日本華族](http://zh.wikipedia.org/wiki/%E8%8F%AF%E6%97%8F_(%E6%97%A5%E6%9C%AC)) 與 [華族令](http://zh.wikipedia.org/wiki/%E8%8F%AF%E6%97%8F%E4%BB%A4)

### 歐美

- [《FRIENDLY FASCISM》](http://www.amazon.com/FRIENDLY-FASCISM-Bertram-Gross/dp/B0091L2H0U)Bertram Gross，美國豪門網絡
- Domhoff《Who rules America》
- 目前我國這樣的分析很難做，因為台灣有法人董事制度，很多企業的董事都是替身。不過非營利組織卻大部分都是自然人理監事，這樣的分析反而好做，隨手挑了幾個（一點也不隨手），但也只做到這樣為止，再深入就是一篇博論了，我一點興趣都沒有。
- [《Gossip Family Handbook》](http://www.amazon.com/Gossip-Family-Handbook-Andrew-Barrow/dp/0241110971)Andrew Barrow，英國貴族網絡
- 談法國貴族
    - https://www.facebook.com/learnfrenchtaipei/posts/3292595460805008
- [The Trilateral Commission](http://www.trilateral.org/)
- [Bilderberg Meetings](http://www.bilderbergmeetings.org/index.php)

## 土撥鼠探頭名單（自主挖坑入坑）

- ronnywang
- kirby
- pofeng
- venev
- yhsiang
- Michael_LI　//文編
- [che wei liu](https://g0v.hackpad.tw/ep/profile/zsVEYFJyWhm)
> 雞婆地把你加進來了，謝謝你在後勤中心貼文 inspire 這個 pad 的出現＆持續貢獻！
> [name=venev]

> 非程式部分若需協助的事情再請通知！
> [name=che l]

- 不小心撿到強者 James：有很棒的分析資料

## Hacking 實作討論紀錄

- [2014/09/20 & 11/22 萌典松討論](http://hackfoldr.org/gxv/byvCrtHhRML)
- [20141108 gxv 拜訪中研院社會所](http://hackfoldr.org/gxv/jtG0viyVzPl)
- Licenses 課題
    - 諮詢：台灣創用CC計畫 [http://creativecommons.tw/](http://creativecommons.tw/)
    - 探討
        - 「連戰的兒子名叫連勝文」這類家族譜系知識是否直接是 public domain ? 「連勝文」是否有權力提出任何反對此資料庫的意見呢？
            1.  初步判斷沒有。
            2.  毀謗、妨礙名譽...?
        - 公部門的資料：例如公司登記資料、公職人員申報資料、貪汙判決書資料、證券交易資料、電子採購網資料...但前述這些資料庫是否能 Public domain/ODbL 方式匯入 GXV Database？政府釋出的資料，也會附加一些規定與警語，需考慮相容性。
        - 台灣民間的資料庫：例如徵信社與企業名冊資料庫，這樣的商業服務的企業，可以進一步交流看看，是否有意願以 public domain/ODbL compatible 的方式開放？
        - 跨國合作的資料庫：例如中國 [财新数据新闻与可视化实验室 | Data Journalism & Visualization Lab](http://datanews.blog.caixin.com/)
        - 關係資料，如何檢證？


## IRC log: 起心動念

20140109 [美河市弊案](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09#40) -\> [日勝生關係圖](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09#42) -\> 結合政治獻金、總統的親戚，使[政商關係透明化](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09#333)：

- [venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/333) ronnywang++ # 日勝生關係圖（跟政治獻金、總統的親戚結合起來，應該會很強大）
- [venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/338) 等下把 FB 後勤中心的[這串訊息](https://www.facebook.com/groups/g0v.general/permalink/558807730862304/)整理到 hackpad，再看可以怎麼發展（不然都沉沒了好可惜 ><）
- [clkao_](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/340) venev++
- [V1ctor](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/342) g0v 現在有 graphic database 嗎 (挖坑) # 關係圖
- [pofeng](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/343) venev: 有沒有(線上)族譜的程式阿, 號召大家來輸入政商族譜 :p
- [tkirby_](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/345) 忽然發現洪案姐姐有跑去填人物關係圖, 連同事同學都出來了
- [venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/348) pofeng: 我也覺得很需要線上族譜程式。親族譜＋公司譜，政府透明化有望矣
- [venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/351) 但目前好像沒看到？總之我會持續發摟這個主題，有新資訊再跟大家 update
- [yhsiang](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/352) 前幾天好像有人說他的完成了graph db後端的部分
- [tkirby_](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/353) venev: 其實人物關係圖的願景就是做到個人,家族還有集團的關係
- [tkirby_](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/354) venev: 只是停擺了好一陣子.. xD
- [pofeng](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/355) venev: 剛剛亂 google 一下 [http://www.playpcesor.com/2012/01/my-family-tree.html](http://www.playpcesor.com/2012/01/my-family-tree.html)
- [kcwu](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/356) pofeng's url: \[My Family Tree 族譜製作軟體，用家庭樹畫家族誕生史 -電腦玩物\]
- [yhsiang](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/358) 如果沒有要線上的話 其實我覺得很好用的就是NodeXL XDD
- [venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/359) tkirby_: 好，那就讓我來責編人物關係圖和公司關係圖吧！另外 Family Tree, NodeXL 我也收下了（還在追 log .....）
- [tkirby_](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/360) 糟, 看來要開始修 bug 了 XD
- [yhsiang](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/361) venev: NodeXL 是excel的外掛~
- [venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/362) tkirby_: ronnywang: 人物 / 公司關係圖有掛在 g0v 的 github 下嗎？
- [tkirby_](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/363) venev: 人物關係圖目前在我的 repo 下 ( [http://github.com/zbryikt/ppllink](http://github.com/zbryikt/ppllink) )
- [tkirby_](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/366)也可以把它弄到 g0v 下去, 這樣搞不好更有動力開發.. XD
- [tkirby_](http://logbot.g0v.tw/channel/g0v.tw/2014-01-09/367)應該要挖掘新血繼續跳坑才對
- [ronnywang](http://logbot.g0v.tw/channel/g0v.tw/2014-01-10/1) venev: 公司關係圖我還沒掛到 g0v, 明天一起把他弄好好了
- [venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-10/2) tkirby_: 把任務明確化之後，招新血跳坑就會容易得多 # how to crowdsourcing
- [venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-10/3) 開好 hackpad 再來通知大家 cc pofeng tkirby_ ronnywang

## 零感始終來自於閒聊

> 簡寫不知道能不能叫 GXV（開始亂想 Video 文案）。其實這個 pad 也是泛監察院系，先歸入 g0v cy collection。
> [name=venev]

> gxv <<有政權祕密的感覺
> [name=che l]

> GXV = Guan Xi V____ ? 
> [name=che l]

> Guan Xi Viva ... 關係萬歲 ? 
> [name=che l]

> Guan Xi Visualized? 
> [name=venev]

> ++ 
> [name=che l]

> Visualization ?
> [name=che l]

> -
> [name=che l]

> 已請出版社的朋友試著聯繫**陳柔縉，**似乎可以聯繫的上，屆時可以想想如何與她交流
> [name=che l]

> 太好了！這是我發願想辦的活動之一，那來辦政商 / 陽光松？請陳作為 special guest 來分享想法，傳承爬梳資料的經驗？另也把公司關係圖、人物關係圖等工具介紹給大家；順便來松 g0v-cy 相關專案？// 9/20 [9 月萌典松: moed6ct (含直播及文字轉播)](https://g0v.hackpad.com/9-moed6ct) 來談談怎麼舉辦好嗎？
> [name=venev]

> 好哇！這樣我當天就有事情做了！XD 希望陳可以於週末前回個信，btw 我有寄信給李宗榮研究員20140915，目前未回覆 Q_Q；另外，我知道台大社會系的[陳東升](http://sociology.ntu.edu.tw/~dschen/index.htm)可能有興趣，寫過專書《金權城市：地方派系、財團與台北都會發展的社會學分析》1995；陽光松，聯想到 [透析貪污判決--揭露與查詢網站](https://g0v.hackpad.tw/--OoaenzjVDKK) 專案
> [name=che l]

> 20141019 小記錄：今日參加【從頂新餿水油事件看兩岸權貴資本】的座談會，會後我向中研院社會所林宗弘老師，提到了政商關係 (暫稱 gxv) 的專案構想，林宗弘老師說，他主要是從徵信社的企業資料庫 (需購買使用授權 ex一年15萬) 來進行企業與經濟議題的研究；李宗榮老師，則是以政商家族為基礎來建構資料。整理幾個要點：

> 1\. 他目前是希望能將兩邊 (企業資料庫、政商家族) 的資料，看看如何整合起來

> 2\. 關於徵信社的資料，會有授權應用的課題，也需要溝通與解決；有向資料廠商談過一次，是否可以成為中研院非營利用途資料，沒有太明確的結論

> 3\. 我有提到 g0v 公司登記、財團法人、公職人員..等等專案的資料也可整合

> 4\. 11/08 g0v年會，林宗弘老師表示可以直接來辦公室看看徵信社的資料庫，或是另外約時間

> 5\. 左岸書系秀如主編表示，年底之前還會遇到陳柔縉，會再向她說明；秀如主編也有提到會向李宗榮老師提醒一下「有年輕人找他作此事，希望他不要拒絕」(因為我說李老師沒回我信XD)

> 6\. 吳介民老師提到他常以四個新聞資料庫來源，來勾勒兩岸政商關係：中央、聯合、[慧科](http://www.wisers.com/corpsite/global/b5/home/index.html)(新聞資料很齊全)、[中評網](http://hk.crntt.com/)(個案報導深入) 

> 20141115 宗榮老師回覆：「哈囉，劉先生，抱歉我現在人在荷蘭訪問，可能短期內無法碰面討論。你們做的計劃非常有意義。也希望你們加油。如果在分析資料或觀點上有需要討論的地方可以再來信討論。」可以開始蒐集與李宗榮老師交流請教的課題，例如是否願意與 g0v 社群朋友討論看看，如何將譜系資料數位化與群眾協力... 請至 [http://hackfoldr.org/gxv/58nYHoNHaoA](http://hackfoldr.org/gxv/58nYHoNHaoA)
> [name=che l]

> [衛城出版](https://www.facebook.com/acropolispublish/posts/882246005128493)：Piketty 這次訪臺，意義除了以兩場一個小時的演講(一場TICC，一場中研院)陳述他的研究外，以及跟各位讀者見面，更重要的是，他也是來瞭解臺灣加入WTID的資料問題。目前中研院經濟所已取得財政部授權的財稅資料，不久的將來，也許臺灣會正式成為WTID研究的對象之一。也請大家期待經濟所何時能將資料初步研究成果公開。編輯只能跟大家說，有幸見到那些資料與圖表，才明白臺灣社會瀰漫的分配不均的情緒，原來不是假的，是如此真實存在於那些數據當中。
> [name=che l]

> 20141207 chewei> 目前覺得：運用 MS Accces 所建置的 [中國歷代人物傳記資料庫（CBDB）](http://isites.harvard.edu/icb/icb.do?keyword=k35201)，已經有一些人物資料欄位定義、原則確立，是否，可以依照該資料庫的架構，將《總統的親戚》、〈聯誼會文件〉、《產業史資料》...等資料，透過「群眾寫作工作坊」推廣 key-in
> 我還沒有好好研究 CBDB 的資料架構有沒有支援，現代企業、法人、NGO ... 非自然人的存在... (例如經濟部公司資料、工廠資料)
> CBDB 內，對於一個人人生不同時間點所擔任的不同職位、一段關係是否包含有這段關係的時間資料 ...有沒有在資料結構上有所應對？
> 2017 chewei> 以 CBDB 的基礎，探討建立臺灣人物資料庫的活動！
[http://tadh.org.tw/index.php/2017/04/27/tbdb/](http://tadh.org.tw/index.php/2017/04/27/tbdb/)
> [name=che l]

> 「內線交易與操縱股價法律與政策」研討會 [https://docs.google.com/forms/d/e/1FAIpQLSebo8miHYkOVRa38NSmZYuOYgpB\_SuChcwwQXclu4Bmlh\_HTw/viewform?c=0&w=1](https://docs.google.com/forms/d/e/1FAIpQLSebo8miHYkOVRa38NSmZYuOYgpB_SuChcwwQXclu4Bmlh_HTw/viewform?c=0&w=1)
> [name=che l]

> 《集團化公司治理與財經犯罪預防》
[http://www.press.ntu.edu.tw/?act=book&refer=ntup_book00951](http://www.press.ntu.edu.tw/?act=book&refer=ntup_book00951)
> [name=che l]

> 《法人刑事法―實體、程序與沒收新法》研討會
[https://www.facebook.com/taiwanlawsociety.org.tw/posts/792112627555379](https://www.facebook.com/taiwanlawsociety.org.tw/posts/792112627555379)
> [name=che l]

> 這串貼文有蒐集一些近期相關活動、研討會
> [https://www.facebook.com/groups/g0v.general/permalink/976491209093952/](https://www.facebook.com/groups/g0v.general/permalink/976491209093952/)
> [name=che l]


> [點此觀看原始內容](https://g0v.hackpad.tw/5gygVb26WId)

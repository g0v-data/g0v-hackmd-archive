---
title: "關係資料討論紀錄 @萌典松"
tags: gxv
---

# 關係資料討論紀錄 @萌典松

> [點此觀看原始內容](https://g0v.hackpad.tw/byvCrtHhRML)

活動 [11 月萌典松: moed7ct (含直播及文字轉播)](https://g0v.hackpad.tw/11-moed7ct?eid=urvzaNXyaqB)
活動 [9 月萌典松: moed6ct (含直播及文字轉播)](https://g0v.hackpad.tw/9-moed6ct)

## 11月萌典松


#### 社會所企業資料 TODOs

- [ ] 製作一個 CC 版本，融合宗弘老師的意向，提供給老師做考量與決定
- [ ] 將宗弘老師確認同意的授權條款，與 dta 檔 & xlsx 檔打包起來
- [ ] 線上供檔位置：

#### 歸納「唯一值」

- 統一編號 VAT number +公司名稱+存續時間
- 工廠登記編號+工廠設立許可案號+工廠名稱+存續時間
- 社團/財團法人名稱+存續時間
- 部會職稱+人名+擔任時間
- 公司職稱+人名+擔任時間
- 社團/財團職稱+人名+擔任時間

探討：兩種角色
1.  自然人
2.  公司，法人，民間團體、非正式團體、工廠、政府機構...
3.  這些是否有「唯一值」？
    - 統一編號
    - 身份證字號

#### 整理已被指認的資料集清單與描述及其來源

監察院
- [陽光法案主題網](http://sunshine.cy.gov.tw/)：[申報資料查詢](http://sunshine.cy.gov.tw/GipOpenWeb/wSite/ct?xItem=4664&ctNode=443&mp=2)（監察院）
    - [公職人員財產申報](http://sunshine.cy.gov.tw/GipOpenWeb/wSite/sp?xdUrl=/wSite/SpecialPublication/baseQuery.jsp)（[g0v repo](https://github.com/g0v/sunshine.cy)）
    - [政治獻金收支結算](http://sunshine.cy.gov.tw/GipOpenWeb/wSite/sp?xdUrl=/wSite/PoliticAccount/PAQuery.jsp&ctNode=353)
    - [近五年廉政專刊電子書](http://sunshine.cy.gov.tw/GipOpenWeb/wSite/lp?ctNode=442)
司法院
- [透析貪污判決--揭露與查詢網站](https://g0v.hackpad.com/--OoaenzjVDKK)  （司法院）
- [社團 / 財團法人登記資料](https://github.com/g0v/foundationtw)  data from [法人及夫妻財產登記公告](http://cdcb.judicial.gov.tw/abbs/wkw/WHD6K00.jsp)  （司法院）
行政院
- [公開資訊觀測站](http://mops.twse.com.tw/mops/web/index) （行政院 臺灣證券交易所）
- [政府電子採購網](http://gov.playgroup.com.tw/gov_notice) （行政院 公共工程委員會）
經濟部
- [公司登記資料](http://company.g0v.ronny.tw/) （經濟部）
- [工廠登記公示資料](http://gcis.nat.gov.tw/Fidbweb/index.jsp)、[爬蟲 & 資料](https://github.com/kiang/twfactory/tree/master/Console/Command/data)（經濟部）
民間
- 千大企業調查資料：ex 天下雜誌調查資料、徵信社(有授權課題)
- 個別公司所發行年報與公開資料：ex《台灣中油刊物》...
- 公開可搜尋的關係事實與文本：ex《總統的親戚》...
- 聯誼會：老牌[三三會](http://www.sansanfe.org.tw/index.php?target=about.php&sn=9)、中部[磐石會](http://realblog.zkiz.com/greatsoup38/53844)、[全國商業總會](http://zh.wikipedia.org/zh-tw/%E4%B8%AD%E8%8F%AF%E6%B0%91%E5%9C%8B%E5%85%A8%E5%9C%8B%E5%95%86%E6%A5%AD%E7%B8%BD%E6%9C%83) ...
- 紅白場，訃聞資料，喜帖 ...
- 報紙資料庫：中央、聯合、[慧科](http://www.wisers.com/corpsite/global/b5/home/index.html)(新聞資料很齊全)、[中評網](http://hk.crntt.com/)(個案報導深入)

#### 蒐集與李宗榮老師交流請教的課題

- [http://hackfoldr.org/gxv/58nYHoNHaoA](http://hackfoldr.org/gxv/58nYHoNHaoA)




## 9 月萌典松

### 近期案例

1.  [邱文達、李祖德、張珩、楊原平、徐大麟...關係圖](https://www.facebook.com/photo.php?fbid=728954573843624&set=a.162786293793791.40993.100001872656795&type=1&theater) (林淑芬製作)
2.  [羅淑蕾持千附107萬股 監院申報僅50萬股](http://newtalk.tw/news/2014/09/19/51583.html)（newtalk2014.09.19 ）
- 初步討論：羅淑蕾擔任千附實業的獨立董事，政府的責任是，建構乾淨的資料，提出公部門糾察的機制。
- 相關資料對照：股東會年報、證交所持股資料 101-104、立委財產申報、金錢報、500萬
- 相關資料與工具：

| 工具 | 資料來源 / 柴 |
| --- | --- |
| g0v 人物關係產生器 | 工人智慧 with domain knowledge / crowdsourcing |
| g0v 金錢報 | 監察院陽光法案主題網 |
| g0v 公司關係圖 | 經濟部商業司公司及分公司登記資料 |
|  | 公開資訊觀測站（母/子公司、董監事大股東持股、財報營收等） |
|  | 各公司公開資料（理論上應該 >= 公開資訊觀測站） |

    1.  人物關係生產器
    2.  金錢報：公職人員財產申報
        - [羅淑蕾](https:// http://sunshine.cy.g0v.tw/people/%E7%BE%85%E6%B7%91%E8%95%BE/property/stock/)
    3.  經濟部公司資料與[公司關係圖](http://company-graph.g0v.ronny.tw/)
        - [千附實業股份有限公司](http://company.g0v.ronny.tw/id/12378253)，羅淑蕾 (獨立董事)
    4.  [公開](http://mops.twse.com.tw/mops/web/index)[資訊](http://mops.twse.com.tw/mops/web/index)[觀測站](http://mops.twse.com.tw/mops/web/index)
    5.  千附公司的年報、公開資料
> 各公司自家官網公開資料，理論上應該 >= 公開資訊觀測站（依法應公開資訊），實務上猜測是等於
> [name=venev]

    6.  監察院廉政專刊 (?)


### TODOs

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3cce5bbf3065e0fc5de138aae3f5bdfc)

- [ ] [公眾人物關係圖](http://%20http//zbryikt.github.io/ppllink/)，介面上的課題 feature 改善與討論
- 關係的類型：
    1.  人物之間的關係，例如 [親朋稱呼表](http://dict.revised.moe.edu.tw/htm/fulu/cw.htm)、聯誼會（如老牌[三三會](http://www.sansanfe.org.tw/index.php?target=about.php&sn=9)、中部[磐石會](http://realblog.zkiz.com/greatsoup38/53844)）
> @@@@神秘 !
> [name=che l]

    2.  人與公司的關係
    3.  公司與公司之間的關係
- 探討：三種關係
    4.  血緣 (自然人與自然人之間)
    5.  事緣 (自然人與自然人之間、法人與法人之間)
    6.  自然人擔任法人職務或影響法人團體行為 (自然人與法人之間)
- 關係的「方向」
    - 關係是否有雙向的？連戰－父子－連勝文；蔡惠媚－姑姪－蔡依珊
- 可以先以**中性泛用的關係**來界定，例如：
    - 「婚姻」比「娶嫁」、「夫妻」好
    - 「親子」比「父子」好
    - 義父？
- **實際的權力與人脈的移轉**，是需要關注的，例如：
    - 姻親關係讓朱立倫承襲了其岳父的政商界人脈
- 關係建立與擔任職位，的「時間」與「時期」
- 人與公司的背景介紹，可援引外部資料庫
    - 可整合 wiki 資料
    - google 關鍵字查詢結果（避免菜市名干擾，可指定搜尋關鍵字 "王大明"+新聞）
    - 經濟部公司登記資料
- 圖片
    - 可整合 wiki 上已公開的人物圖片
    - 可整合公司形象商標

- [ ] 參考一下[《Empire Building》](http://english.caixin.com/2014-05-14/100677364.html)数据可视化项目的开发思路（[文章](http://datanews.blog.caixin.com/?p=203)）
- 視覺式直覺呈現出資料特性
- 有定義出資料的特質
- 可是，沒有時間資訊，例如某個人控制某個公司的時間，為期多久
- 有用「動態小球」與路徑，來表達關係方向
- 滑鼠滑過、滑鼠點選...
- [ ] 去信財新網開發者任遠：詢問有無放上 github / gitcafe 的程式碼，開源一起改善？
    - [新浪微博](http://www.weibo.com/u/2248451955) / [作者開發經驗談](http://datanews.caixin.com/2014/jindaoming/index.html)
- [ ] 編輯者，於資料表格中輸入資料 → 再轉出關係圖
- [ ] 應用情境討論
- 情境一：有時事熱門案件時，即可應用此 tool，建構出關係圖
- 情境二：平時就可以填寫資料，匯聚為資料庫
- 情境三：歷史專題的製作

### 下次與左岸聚會時的介紹

- Tools：人物關係器 [http://zbryikt.github.io/ppllink](http://zbryikt.github.io/ppllink)
- Tools：公司關係圖 [http://company-graph.g0v.ronny.tw](http://company-graph.g0v.ronny.tw)
- OpenData：台灣公司登記資料 [http://company.g0v.ronny.tw](http://company.g0v.ronny.tw)
- OpenData：政治獻金 [http://campaign-finance.g0v.ctiml.tw](http://campaign-finance.g0v.ctiml.tw)
- OpenData：金錢報 [http://sunshine.cy.g0v.tw](http://sunshine.cy.g0v.tw)
- OpenData：天龍特公地 [http://taipei-pop.herokuapp.com](http://taipei-pop.herokuapp.com)
- [萌典 – 教育部國語、臺語、客語辭典民間版](https://www.moedict.tw/%E8%90%8C)；[阿美語字典數位化](http://ckhis.ck.tp.edu.tw/~ljm/amis-toufu/index.php)
- 說明我們對 陳 的期待
    - **邀請 陳 成為 special guest 講者？授權我們數位圖表化書中內容？**
    - **「陽光松」**活動預期：
        - 內容：爬梳資料、陽光法案相關專案、政治獻金...
        - 預期時間：未定
        - 透過 陳 的內容，號召更多人參與
> 特定化 task 邀請鄉民參戰 / 好用工具發表 / 
> [name=venev]

- 詢問左岸書系中相關的政治書籍，是否有機會參與合作？
    - 左岸書系：[http://www.books.com.tw/web/sys_puballb/books/?pubid=leftbank](http://www.books.com.tw/web/sys_puballb/books/?pubid=leftbank)
    - 作者參與、打書，例如，食安議題

### 專案整體討論


- 政商關係，其實牽涉了許多種類的資料項目：
    - [金錢報，公職人員財產申報](http://sunshine.cy.g0v.tw/) (監察院)
    - [開放政治獻金資料庫](http://campaign-finance.g0v.lackneets.tw/)  (監察院)
    - 監察院廉政專刊、出版品 (監察院)
    - [透析貪污判決--揭露與查詢網站](https://g0v.hackpad.com/--OoaenzjVDKK)  (司法院)
    - [公司登記資料](http://company.g0v.ronny.tw/) (經濟部)
> 經濟部的公司資料，包含董監事的擔任時間點
> [name=che l]

    - [公開資訊觀測站](http://mops.twse.com.tw/mops/web/index) (臺灣證券交易所,行政院)
> 證交所的持股資料，公司名稱與公司名，代碼，股號
> [name=che l]

    - [政府電子採購網](http://gov.playgroup.com.tw/gov_notice) (公共工程委員會,行政院)
    - 個別公司所發行年報與公開資料：《台灣中油刊物》...
    - 公開可搜尋的關係事實與文本：《總統的親戚》...
    - 紅白場，訃聞

- 資料協力的來源路徑
1.  **專業調查**
    1.  專業調查者的行動目的，經常出於議題導向的資料建構，有敘述策略的目的
        1.  中研院社會所
        2.  地方線記者
        3.  社會運動議題關注者
        4.  土地政策研究學者
        5.  企業公司史的研究者
    2.  但是，有時候，研究者因為簽署保密協議，不可公開資料
    3.  仿照 OpenStreetMap 模式，提供研究者更方便管理關係資料的工具
2.  **群眾補充**
    1.  平時即可增加關係資料
    2.  仿照 OpenStreetMap 模式，讓參與者以某種授權方式回饋關係資料

- 專案效果
1.  讓關係資料更方便瀏覽，增加監督意識
2.  政治獻金、財產申報的資料，協助選民於選舉判斷，例如議員與首長
3.  政府的責任是：建構乾淨的資料，且針對資料提供來源提出糾察的機制 (如財產申報人所申報的資料是否正確)

### ideal pool

- Open 訃聞，蹲點殯儀館XD
- 外資、港資、中資
- 採用 OpenStreetMap 的概念，提供研究者一套工具，資料可以選擇適合的授權條款，回饋到公眾開放的知識與資料領域
- 連勝文、蔡依珊
    - 連勝文家族
    - 蔡依珊的姑姑，蔡惠媚(蔣孝武)清水蔡家，為蔣孝武的妻子
- **G**uan**X**i **V**isualized, GXV
> Visualization ?
> [name=che l]



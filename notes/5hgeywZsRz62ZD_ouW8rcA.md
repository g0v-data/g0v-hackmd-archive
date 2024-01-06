---
title: "農作物開放資料(Seargetable)"
tags: 農業,hackpad
---

# 農作物開放資料(Seargetable)

> [點此觀看原始內容](https://g0v.hackpad.tw/kCmdNxq7RUe)

【重要說明】本hackpad上的文字與未來網站資料為cc-by 4.0授權。
Ｉ公共頻道Ｉ=\> [https://gitter.im/seargetable/rg0v/](https://gitter.im/seargetable/rg0v/)

## 實施計畫

```
關鍵點：
農業的東西一直都有人做，政府也一直在推動，關鍵點是這個議題“聲量”不夠。至於聲量為什麼不好，原因很多，
譬如：
  \ 各自為政？
  \ 不相信任？
  \ 太難太複雜？
其實大致還是“人”的問題，這計畫就是要逐一破關。ＸＤ
```
### \*all-stage\* PR&&GROWTH

    大家都應該摻一咖！
### stage-0 意象設計+landingpage

    我有點想忍不住幹一個了。有人會**長輩式排版（efd, elder-friendly design）**或寫**長輩文案**嗎？wwwwwww
```
ie. 認同請按讚 認同請轉發 大字 ....（但要真的長輩觸擊率高的）

```
### stage-1 詞庫

    有許多農業資料的網站都不錯，但是作物的市場名與俗名有些差異，民衆有時想搜尋時名字不一致，希望能將對應整理起來，並提供作物的相關資訊連結。
### stage-2


### stage-3 入口


> 我目前有些想法還是滿“**文青”**的，麻煩大家幫忙一起討論一下。xdxd 
> [name=Chun-Hao P]

## 計畫使命

#### 當初為何發起 seargetable ？

[https://flaing.github.io/seargetable/](https://flaing.github.io/seargetable/)
我們覺得農業應該是一個國安議題，並且要透過一個真實存在的動態產業來推動這件事情。目前台灣其實只有農業貿易業、農業博弈業，不算真的具備農業產業。...

> _  我目前有些想法還是滿“_**_文青”_**_的，麻煩大家幫忙一起討論一下。_
> [name=Chun-Hao P]


## 頁面名稱

1.  Agrisync 阿基芹 （很潮但芭樂名）
2.  Seargetable 搜蔬 （很潮好記加有故事）
3.  Beshu 比蔬 （好打加白痴翻譯）

## 簡報

[https://goo.gl/8ifIof](https://goo.gl/8ifIof)

## 頁面樣式

[https://goo.gl/GhVwLv](https://goo.gl/GhVwLv)
> 話說我們最後還是得需要手機版的~神奇寶貝圖鑑~吧 !? 先忽略 ?
> [name=彥瑾 李]

> 有不錯的畫面把它貼在[最下面](https://g0v.hackpad.tw/temp-kCmdNxq7RUe#:h=參考畫面)
> [name=陳幸延]


## 先將整理的資料放在這裡吧

[https://goo.gl/cc9PMD](https://goo.gl/cc9PMD)

## Beta

[http://a0726h77.github.io/open_crops/](http://a0726h77.github.io/open_crops/)

## Landing Page

- HEADER
    讓每個農業從業人找到他要的數據

- FEATURES
    \* 匹配超準確
    \* 每個人都能準確拿到自己要的
    \* 每個人都超想分享自己資料的！

- HOW IT WORKS
    \* 幫你整理公開資料變成鍵盤鄉民 readable
    \* 彙整異名同義的資料
    \* 全台鄉民都超想幫農糧署、農委會一起 debug ！


## 科技

### 系統構想

> 先開 spec 好了？
> [name=Chun-Hao P]

> 先列出我們可以用的現成 API，以及哪些 data 我們可能要自己來  (ex: 取得當日的價格資訊）
> [name=彥瑾 李]

> [https://g0v.hackpad.com/aco0Hxp4IEz](https://g0v.hackpad.com/aco0Hxp4IEz) 中文分詞斷詞的一些工具
> [name=Chun-Hao P]

> for scrapying data ->> [http://stackoverflow.com/questions/22168883/whats-the-best-way-of-scraping-data-from-a-website](http://stackoverflow.com/questions/22168883/whats-the-best-way-of-scraping-data-from-a-website)
> [name=Chun-Hao P]


### 主頁

    前端 ~clojurescript~ javscript
> 語言要選用這個團隊作多人會用的比較好，要直接套用 framework 嗎 ?
> [name=彥瑾 李]

> 只是覺得 clojure 從技術分析到前端都超威 ... 自幹方便，套別人的也沒有 sideeffect 
> [name=Chun-Hao P]

> [https://github.com/SnootyMonkey/coming-soon](https://github.com/SnootyMonkey/coming-soon)
> [name=Chun-Hao P]

> 我先弄個 comingsoon landingpage 好了 ...
> [name=Chun-Hao P]

> 這邊也有很多很好的參考
> [name=Chun-Hao P]

> [https://github.com/RailsApps/rails-prelaunch-signup](https://github.com/RailsApps/rails-prelaunch-signup)
> [name=Chun-Hao P]

> clojure 很爽很方便啊啊啊啊，問題在會用 or 會想要用的人不多，所以這個時候就入進隨俗吧
> [name=彥瑾 李]

> clojure +1，不過維護應該會出事...
> [name=Jin-Kuen L]

    後端(不自建) cljs~,~ sheethub  ...
> 後端目前看起來應該是使用現成的 DB ，我們可能另外建立程式幫我們計算歷年的菜價等資訊，並傳送到 sheethub (如果沒有現成的 API 可用的話)
> [name=彥瑾 李]

### x

    _

## 參考資料

### 目前作物名稱最多的網頁

    台灣農產品標準分類編碼系統
    [http://coa.gs1tw.org/app/COA/COAUser_Search.jsp?MTOP=A](http://coa.gs1tw.org/app/COA/COAUser_Search.jsp?MTOP=A)
> 農業標準碼 [http://www.gs1tw.org/twct/en/img/Produce_coding.pdf](http://www.gs1tw.org/twct/en/img/Produce_coding.pdf)
> [name=陳幸延]

> 編碼 spec [http://www.gs1.org/sites/default/files/docs/barcodes/GS1\_General\_Specifications.pdf](http://www.gs1.org/sites/default/files/docs/barcodes/GS1_General_Specifications.pdf)
> [name=YGhost Y]


    農產品交易行情站
    [http://amis.afa.gov.tw/](http://amis.afa.gov.tw/)
> 有 parser 及相關資料 [yhunglee](https://github.com/yhunglee)/[**agri\_data\_crawler**](https://github.com/yhunglee/agri_data_crawler)
> [name=陳幸延]

> 目前也有 API，行政院農業委員會資料開放平台 [http://data.coa.gov.tw/Query/ServiceDetail.aspx?id=037](http://data.coa.gov.tw/Query/ServiceDetail.aspx?id=037)
> [name=陳幸延]


### 作物介紹

    蔬菜列表
    [https://zh.wikipedia.org/wiki/%E8%94%AC%E8%8F%9C%E5%88%97%E8%A1%A8](https://zh.wikipedia.org/wiki/%E8%94%AC%E8%8F%9C%E5%88%97%E8%A1%A8)

### 作物分類

    3-2-2蔬菜之分類
    [https://market.cloud.edu.tw/content/vocation/garden/ul_ag/library/ch3/322.htm](https://market.cloud.edu.tw/content/vocation/garden/ul_ag/library/ch3/322.htm)

    台灣植物資訊整合查詢系統
    [http://tai2.ntu.edu.tw/PlantInfo.php](http://tai2.ntu.edu.tw/PlantInfo.php)

    蔬菜列表
    [https://zh.wikipedia.org/wiki/%E8%94%AC%E8%8F%9C%E5%88%97%E8%A1%A8](https://zh.wikipedia.org/wiki/%E8%94%AC%E8%8F%9C%E5%88%97%E8%A1%A8)

    植物保護手冊
    [http://www.tactri.gov.tw/wSite/ct?xItem=3691&ctNode=333&mp=11#cat3](http://www.tactri.gov.tw/wSite/ct?xItem=3691&ctNode=333&mp=11#cat3)

    認識蔬菜及栽培管理作業
    [http://www.tdais.gov.tw/files/web\_articles\_files/tdares/7222/2246.pdf](http://www.tdais.gov.tw/files/web_articles_files/tdares/7222/2246.pdf)

### 菜價

    農產品交易行情站
    [http://amis.afa.gov.tw/](http://amis.afa.gov.tw/)

    臺北農產運銷股份有限公司
    [http://www.tapmc.com.taipei/price1.asp](http://www.tapmc.com.taipei/price1.asp)

    市場行情通
    [http://www.markettrade.com.tw/](http://www.markettrade.com.tw/)

    全台蔬菜交易視覺化(1,905)
    [http://muyueh.com/30/veggieprice/ggplot2/](http://muyueh.com/30/veggieprice/ggplot2/)

### 栽培法

    有機農業全球資訊網 \-\- 全年菜園管理-蔬菜播種時間及適溫
    [http://info.organic.org.tw/supergood/front/bin/ptdetail.phtml?Part=22-2&PreView=1](http://info.organic.org.tw/supergood/front/bin/ptdetail.phtml?Part=22-2&PreView=1)

    種子工坊
    [http://ww.sollong.com/NewGrow/gardeningcalendar.aspx?PageID=5](http://ww.sollong.com/NewGrow/gardeningcalendar.aspx?PageID=5)

    台灣雜糧作物品種圖說續版
    [http://webpac.ilccb.gov.tw/Webpac2/store.dll/?ID=4038&T=0](http://webpac.ilccb.gov.tw/Webpac2/store.dll/?ID=4038&T=0)
> 這本有講好多種植細節
> [name=陳幸延]


### 病蟲害

    超農域系統
    [http://g0v.github.io/agriculture/pesticide/usages/](http://g0v.github.io/agriculture/pesticide/usages/)

### 產銷履歷&種植農友

    臺灣農產品安全追溯資訊網
    [http://taft.coa.gov.tw/](http://taft.coa.gov.tw/)

### 本質上的概念 => 農業資訊社群化 -\> 國安


#### 當初為何發起 seargetable ？

[https://flaing.github.io/seargetable/](https://flaing.github.io/seargetable/)
我們覺得農業應該是一個國安議題，並且要透過一個真實存在的動態產業來推動這件事情。目前台灣其實只有農業貿易業、農業博弈業，不算真的具備農業產業。...

### 團隊聊天室

    telegram->“seargetable2” 。請在 telegram 敲我 @flaing12 。

    ~快一起聊八卦吧ＸＤ~
    一些節錄：
```
陳 幸延, [19.10.15 23:51]
其實我覺得農夫的操作不能沒有系統化，甚至係有很多大數據的

陳 幸延, [19.10.15 23:52]
另外農夫也不應該很窮困

Rudiger Peng, [19.10.15 23:52]
台灣農業困境是比較難向中國澳洲美國那樣規模化所以不能吸引資金組織成企業，經濟上會往小農散戶靠攏。所以本質上我們要創造的事小農散戶 central 的環境。

Rudiger Peng, [19.10.15 23:54]
但台灣一直以來推動台灣農業的方法，是管制模式，那就比較像是政府對法人的概念。台灣的農業在這個情境之下就一直鬼打牆，真正農夫窮，隨便一個路人可冒充農夫領津貼。

Rudiger Peng, [19.10.15 23:54]
追求效率會衍生成形式主義，這在大企業與政府的關係中或許是用，但在於小民小農的國家體系這是不是用的。

Rudiger Peng, [19.10.15 23:55]
所以我們思路必須往開放共享靠攏，讓利益與風險散開，削弱農糧署農委會控制力，也承擔包商的風險壓力等等。

Rudiger Peng, [19.10.15 23:59]
農業在台灣最佳狀態 就是讓他變成自成的知識體系、資料體系，每個人都不需擔心壟斷資料，但每個人又分擔了市場的風險，以及政策或天災的風險與責任。我相信所有島民（真鄉民？ＸＤ）也都是期待這樣的一天

Yen-Chin Lee, [20.10.15 00:00]
太理想了 ......

Rudiger Peng, [20.10.15 00:00]
多講一點

Yen-Chin Lee, [20.10.15 00:00]
夢不要作這麼遠啊啊啊啊啊 好吧 我比較踏實

Rudiger Peng, [20.10.15 00:01]
我覺得遠近都重要。實作絕對要看近，思路要看遠，兩個不衝突

Rudiger Peng, [20.10.15 00:01]
你講得很好

Rudiger Peng, [20.10.15 00:03]
工程師有工程師優勢，但其他也有值得考慮的方方面面，如果只考慮一個點，就很難讓“沒有人”迭代。

Rudiger Peng, [20.10.15 00:03]
反正現在只是講八卦時間而已 xd

Yen-Chin Lee, [20.10.15 00:03]
想遠是對的，但是我總覺得東西發散了

Yen-Chin Lee, [20.10.15 00:03]
反正我只關心要做什麼就對了 XD

Rudiger Peng, [20.10.15 00:04]
知道拉

```
> 歡迎補充
> [name=Chun-Hao P]

> 歡迎跳坑
> [name=Chun-Hao P]

> 不見得要實質幫忙，加進來給點意見，聊聊天也好
> [name=Chun-Hao P]

> 歡迎每個關心這個議題的人關注此事，提供意見，提供心力 
> [name=Chun-Hao P]

## I AM IN !!!!

介紹一下大家好了，有興趣的就自己留一下，有助於大家合作的氣氛與默契：
// (也歡迎自己修正)

*張尊國教授 ： 「以身作則，誠正又熱情」的台大教授，熱血不老戰士。總是以不為人知的方式幫助學生。我與他認識是在大四時候創建 seargetable 時與他請教，我們素昧平生，他卻爽快答應。他的兒子現在也是軟體圈內人，我與他兒子在 rails pacific 上認識...。

*Kaikai Huang：他是從小就很喜歡奇想的男子，在大學時就是怪咖＋才子 ... 我們在大二網路上認識（因為女友在他們班拉）發現頗為合拍，遂在大四一起弄了 seargetable 項目，他為我們的設計塑造了超強的使用流程還有視覺體驗。他畢業後先在台灣的智能硬件公司設計募資專案，之後去了北京當台勞資深設計師，目前在一家互聯網金融公司服務。

*陳幸延：他先前是科技人，深耕台灣社群，今年開始也開始深耕菜園，走了與我們一般人不一樣的路，是位非常有勇氣的智者。他希望務實達到科技農夫的境界。我們在 Hacking Thursday 認識的，他一直是該團隊主要的值日生（ co-organizer ）。

*Yen-Chin Lee：他是非常有天份的駭客，因為家住嘉義接觸電腦較晚，但大學之後寫程式就迅速變成了強大的駭客，是一個能從硬體 kernel 到軟體到前端都能自幹的「真.FULLSTACK」。個性低調，但是在 github 和 emacs 社群非常自 high ，有很多奇妙的作品，被國際上的開發者使用，受邀在 coscup 上有多次演講。我是與他在網路上面認識的。（我好像大多數朋友都是網友，我跟女友也是...）
> 這邊的介紹太誇張了，我只是小魯蛇一枚  =口=
> [name=彥瑾 李]


*YGhost ： 他是有理想並善良的軟體工程師，平時熱心公益、教育小朋友，目前服務於一家台灣的金融公司負責研發公司內部的產品。我與他是在 Hacking Thursday 上面認識。

*johnny ：

*c3h3 ：

*flaing ： 小推手

*Ming ：雖然不知道自己可以幫上什麼忙，但覺得很有意義的活動，也大家意義的活動，也大家一個大讚先！

*badboy99：軟體工程師，現在是幸延在菜園的學弟！

....請自己補充

## 構想畫面

![](http://cdn8.staztic.com/app/a/3874/3874795/plant-vs-zombies-2-fan-guide-10-2-s-307x512.jpg)

![](http://www.liukung.org.tw/images/qa/001.jpg)


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8b25dc3f729e05f8f4c6d883a143b3d2)


### 進度

1.  2015/10/24 資料欄位確認 [link](https://docs.google.com/spreadsheets/d/1XicH3lQKfWnyAsCsUIFSQYqy2fqJ86J-f1uImOnTjeA/edit?usp=sharing)
### Todo:

1.  幸延先開一個開發用的 database, 應該會是 mongodb (或自行架設)
2.  爬資料 : 依欄位需求爬
    1.  **爬爬 台灣農產品標準分類編碼系統** [link](http://coa.gs1tw.org/app/COA/COAUser_Search.jsp?MTOP=A)
    2.  爬爬 wiki (域界門綱目科屬種)  有沒有 API？ [link](https://zh.wikipedia.org/wiki/%E7%94%98%E8%97%8D)
    3.  爬爬 菜價 (要把個各市場的平均起來)  [link](http://data.coa.gov.tw/Query/ServiceDetail.aspx?id=037)
    4.  爬爬 栽培法 (人工 parse 資料...)  [link](http://info.organic.org.tw/supergood/front/bin/ptdetail.phtml?Part=22-2&PreView=1)


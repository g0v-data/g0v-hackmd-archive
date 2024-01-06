---
title: "d|Bootcamp Taipei"
tags: hackpad
---

# d|Bootcamp Taipei

> [點此觀看原始內容](https://g0v.hackpad.tw/DpZLa4EWHRu)

> rename to d|Bootcamp "Taipei" according to Justin's comment
> [name=Kirby W]


### SIte: [http://dbootcamp.taipei/](http://dbootcamp.taipei/) (含議程)


Who: Journalists
Along with: [Data Science Conference Taiwan](http://datasci.tw/)
- Date: 2015/08/21 (training) + 08/22~23 g0v hackathon
- Seats: 99 (sold out as Jul 14)
- Cost: NT$2980pp

### 演講內容

- 國外講者：high level、實際 DJ 範例
- 座談：邀請媒體界有嘗試在新聞室裡從事data journalism的團隊（eg. udn），分享實作的挑戰，新聞室對data journalism合理的期待。
> panel 還差一位未決定
> [name=Liang K]

- D1 結束前鼓勵隔天到 g0v 提案（簡介 g0v 社群運作方式），當作製作新聞的流程練習

### 課程內容


講師建議的進行方式：每個 session 會由實際成果開始展示，倒推回如何做出(20min)、相關知識技巧(15min)、實作練習(20min)、進階議題關鍵字或展示(5min)

- 空間時間 (快速 timeline 上手) / Jimmy
    - 應用 google spreadsheet 加現有服務，輕鬆製作 Timemap / Timeline
    - 對跨越時間的資訊呈現方式，有多一層了解
    - 能聽聞更多地理和時間製作新聞主題的案例
    - 進階
        - 將資料表以年份或者位置做樞紐分析
        - reuse 資料，變成 geoevent
- 找資料 / Ronny
    - 哪裡有現成的資料可以找
        - open data
            - 各開放平台
            - world bank
        - not open data
            - 社經資料庫
            - 主計處
    - 沒有現成資料要怎麼抓
        - google spreadsheet importData
        - PDF 抓出資料:tablua
    - 資料抓下來怎麼先看看長什麼樣子
        - What is JSON, CSV, XML
        - JSON: [http://konklone.io/json/](http://konklone.io/json/)
        - XML: .....
        - 倒進 spreadsheet ，處理 CSV 編碼
    - 進階：
        - JSONView
        - =importHtml
        - kimonolabs
- 清資料 (What's a clean dataset? OpenRefine) / Kirby
    - 希望學員上完後獲得什麼技能
        - 快速將不勘用的資料變成可以分析的資料
    - 希望原來就已經會這個技能的人，來聽了之後多了什麼洞見
        - 「原來還可以這樣做」
    - 想選用的範例資料：
        - 人口資料、犯罪率資料、房屋轉移資料
    - 說明為什麼要做資料清理
        - (比方說,為什麼國字要轉數字)
    - 進階：
        - vlookup
- 畫資料 / Muyueh
    - [ ] 需要有大家的 gmail
    以 google spreadsheet 為主
    - 前半段介紹基本的拉資料
        - bar - line - donut
        - fusion table map
    - 後半段，找一些選舉報導的例子
        - difference
        - 選舉地圖
    - 概念：
        - 資料-計算-假設
        - 重複利用
    - 視覺錯覺
        - bar 從中間
        - 因果不等於相關
        - 圓餅圖超過 100%
> 我覺得媒體常會 為了做圖 而做圖 muyueh 你手邊有案例可以當反面教材嗎？
> [name=Silva S]

    - 進階：

可能的數據
- 鬼月
- 颱風
- 塵爆
- 選舉
    - timemap : [柯文哲行程](https://www.google.com/calendar/embed?showTitle=0&showNav=0&showDate=0&showPrint=0&showTabs=0&showCalendars=0&showTz=0&mode=AGENDA&height=200&wkst=1&hl=zh_TW&bgcolor=%23FFFFFF&src=tkuqrha1ksg9jhletv4315g1co%40group.calendar.google.com&color=%23B1440E&ctz=Asia%2FTaipei)

### 課程討論及調整

(四大主題，如何串接討論中)
- 找個題目做為資料新聞實作的範例？
    （目前媒體最關心兩大話題：選舉、醫療資源。要滿足他們兩個最大需求，還是再想第三個，媒體沒注意的話題？）
- 媒體常用的 spreadsheet 功能（基礎知識）
    - split, vlookup, 基本運算（＋-x/）
-

### 其他參考


- 新加坡 bootcamp: [http://hackfoldr.org/databootcamp/](http://hackfoldr.org/databootcamp/)
- DJ handbook: [http://datajournalismhandbook.org/](http://datajournalismhandbook.org/)
- clkao 公務單位演講的「一秒判別是不是資料」（待補）
- Ronny 之前在聯合報教 spreadsheet 的綱要: [Google Doc](https://docs.google.com/document/d/1-56MFuYufbl0PRYO896q7ifNPo4dqbM_B8Eefq_s5JQ/edit)

### 課程參與度規劃

- 行前問卷 (google form + require login) **DUE 7/24**
    - 是否參加黑客松
    - session specific questions
    - 整理資料篇
        - 是否曾經用 Google Spreadsheet 整理過資料？
        - ( 承上 )  spreadsheet 的內建函式：
            - (多選) 下列哪些曾用過？
                - SUM
                - IMPORTHTML
                - SUBSTITUTE
                - IF
                - REGEXREPLACE
                - VLOOKUP
        - 用過 open refine 嗎？
        - 若手上有一萬筆地址要畫到地圖上，你的做法：
            - 我會自己一筆一筆貼到 google maps 查經緯度
            - 我知道幫忙轉換的網路服務，會把資料上傳過去做轉換
            - 我會使用 open refine reconcile 工具做大量轉換
            - 我會寫程式利用 Google Place API 批次轉換
> ^^^移到資料整理
> [name=Singing L]

    - gmail / slack
    - 以下網站用過哪些: \[多選\]
        - data.gov.tw 政府資料開放平台
        - 社會經濟資料庫
        - 行政院主計總處
        - 中央選舉委員會選舉資料庫
        - data.worldbank.org 世界銀行
        - Google Public Data
        - 內政部實價登錄
- 如何選題？
- 課前準備
    - kimono lab 帳號
    - google account (請大家填寫某個 spreadsheet?)
> google form 好像可以限登入使用，因此可以請他們填一個 google form ，把一些資訊先提供，上課時再請助教協助關切一下還未填的
> [name=Ronny W]

- 分組 (大概十組)
> 大約10人一組嗎？
> [name=Silva S]

> y
> [name=Liang K]

- hackfoldr?
- hackdash?
    - hack.dbootcamp.taipei
        - 一個介紹 hackpad page
        - 四個課程 hackpad page
        - 各組一個 hackpad page

### 宣傳


- [x] 第一波
- [ ] ~第二波（講者大頭，等 muka++）~
- [x] 新聞稿

pre-event 新聞稿 ：
[https://docs.google.com/document/d/1zcqJwsoqklBYDGCgv-nd2GU5mfF9GTFfFqllvL1G7Fw/edit#](https://docs.google.com/document/d/1zcqJwsoqklBYDGCgv-nd2GU5mfF9GTFfFqllvL1G7Fw/edit#)

媒體窗口聯絡名單：
[https://docs.google.com/spreadsheets/d/1CUiAMW3DOuxT0qTG6IbkYmK-AAcu7N_E6fK4WV9Pg7Y/edit#gid=0](https://docs.google.com/spreadsheets/d/1CUiAMW3DOuxT0qTG6IbkYmK-AAcu7N_E6fK4WV9Pg7Y/edit#gid=0)

參考資料：
- data bootcamp 是由 [Global Media Development Program](http://wbi.worldbank.org/wbi/content/wbis-media-program) 支持的 [Open Data 需求與參與發展](http://opendatatoolkit.worldbank.org/en/demand.html) 計畫，著重在增進新聞工作者的資料能力，從 2012 年起在非洲、拉美，去年開始有亞洲與美國。
- [News Yo](https://docs.google.com/presentation/d/1RoZeNxtMfcSVQxdyuZnNty5Nnldee237PE8qUnDdTfs/edit)  [u Can Use](https://docs.google.com/presentation/d/1RoZeNxtMfcSVQxdyuZnNty5Nnldee237PE8qUnDdTfs/edit)
- 訪談（有提到肯亞女孩學業變化與廁所關係的調查報導）：[http://radar.oreilly.com/2012/11/justin-arenstein-africa-data-journalism.html](http://radar.oreilly.com/2012/11/justin-arenstein-africa-data-journalism.html)
- Fabiola (玻利維亞, bootcamp june 2013, data clinic 2014): [http://www.lostiempos.com/lt-data/](http://www.lostiempos.com/lt-data/) in one of the biggest newspapers in Bolivia and has been infusing data in the blog (writes about it here): [http://www.lostiempos.com/lt-data/blog/periodismo-de-datos-en-los-tiempos](http://www.lostiempos.com/lt-data/blog/periodismo-de-datos-en-los-tiempos) ... After the 2014 data clinic, Fabiola (and a developer from Los Tiempos, who also attended the 2014 clinic) created “Elige Bien”, a candidates Q&A platform modeled after one created in Argentina. [http://eligebien.lostiempos.com/](http://eligebien.lostiempos.com/)
- 比較累積下來的是工具
-


宣傳曝光管道：
- [x] [雜誌公會edm](http://www.magazine.org.tw/)
- [x] [新媒體研究所](https://www.facebook.com/groups/XinMeiTi/)
- [ ] OCF 粉絲頁
- [ ] g0v 粉絲頁


======
### 行前通知信


親愛的資料科學愛好者，您好：

☞ 請您於 8/9 (日) 前，使用 google 帳號登入後，填寫本問卷：.... ，以利講師準備更貼近您需求的課程內容。

感謝您報名 8/21 (五) 資料新聞實戰營 d|Bootcamp Taipei，您的票券可自由參加 8/22-23 (六、日) g0v 零時政府黑客松活動，讓課程中的分組專案延續，成果更為完整。如果您預計出席黑客松活動，請在問卷中註明，以確保您的用餐及入場權益，並可加速年會籌備工作進行，謝謝您的配合。

由於課程中將會使用 google spreadsheet 的服務練習，若您尚未有 google 帳號，要請您先申請：[https://accounts.google.com/signup](https://accounts.google.com/signup)

2015 資料科學愛好者年會 籌備小組 / 資料新聞實戰營 籌備小組
2015.08.05

=======
### 分組後通知信


親愛的資料新聞實戰營 d|Bootcamp Taipei 與會者，您好：

資料新聞實戰營將在8月21日正式舉行，為了您的提昇學習效果，以及讓您隔天到黑客松提案時有更多想法，我們先將各位安排編組，方便小組間學習討論，同時，每一小組也將有專屬的助教協助課程的練習。

您的分組是：第 $group 組

每一組都有專屬的頁面，您可以到這裡先和同組的朋友與助教打聲招呼，與分組討論區請至：[http://beta.hackfoldr.org/dbootcamp](http://beta.hackfoldr.org/dbootcamp)，同時這邊也會是活動進行時大家的共筆，可以在上面進行討論。

此外，為了協助大會準備週六與週日的餐點，如果您尚未填寫問券，請至：<url>

g0v 黑客松共筆入口：[http://beta.hackfoldr.org/g0v-hackath15n](http://beta.hackfoldr.org/g0v-hackath15n)

最後提醒大家，請務必攜帶自己的電腦，也建議您先看一下課程共筆，每堂課會有一些希望您預先準備的事項（如 google 帳號，chome/firefox 瀏覽器等）

大家下週見囉！

資料新聞實戰營籌辦團隊 敬啟

=====

課前作業：視覺化課堂上會實際用學員所製作的資料視覺化當作案例，討論如何可以增進圖表。假如你自己已經有製作圖表，歡迎寄到 muyueh@gmail.com
> 大家覺得直接寄給我妥當嗎？還是有其他做法？
> [name=Muyueh L]

> 請他們貼到共筆上 會不會比較方便？
> [name=Silva S]




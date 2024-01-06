---
title: "服貿協議相關 g0v 專案"
tags: 反黑箱服貿串連,hackpad
---

# 服貿協議相關 g0v 專案

> [點此觀看原始內容](https://g0v.hackpad.tw/SUkMbG4IV6v)


> 先前臨時會議記錄、reference 移到最下方
> [name=nchild]

> 之前服貿東西太亂了，'031221 之後專案工作請先看這份，其餘有空才慢慢整理
> [name=nchild]

> 在服貿開箱聞的資料成熟以前，想先合併到「你被服貿了嗎？」下方的「說明」部份
> [name=WeiHung]


## 你被服貿了嗎？（服貿協議行業對照工具rutisa）

- 發起人/拋磚人：nchild
- 狀態：
    - 最新狀態，[beta](https://tisa.g0v.tw) 測試，預計2014/3/30之後公開
        - 功能、建議、bug 討論回報，請先用此表 [服貿@g0v 測試討論](https://g0v.hackpad.tw/2spPf82j4ZH#服貿@g0v-測試討論)
    - g0v.tw hackath7n（'031221）再次[挖坑](http://youtu.be/K1ooVjoWLaU)     ，進入開發階段
    - ∂：[http://goo.gl/kuWwq1](http://goo.gl/kuWwq1)
- 專案簡介：源自於[服貿協議行動串連](https://groups.google.com/forum/?fromgroups#!forum/tisa-action)，服貿協議極重要但不易讀、不易懂，政府簽訂前各產業幾無人知，因分類用詞不同，簽訂後究竟包含哪些行業（特別是小類、細類）還是不易判斷（[經濟部新聞稿](http://www.moea.gov.tw/Mns/populace/news/News.aspx?kind=1&menu_id=40&news_id=32375)）。原因在於服貿協議開放承諾行業別是依照聯合國暫行分類，但在我國需轉換成主計處行業別，同樣地，在中國開放之行業別亦須轉換。進一步討論服貿協議前，需要先了解哪些行業被包含。（[短講](http://youtu.be/WNMQ8Sstbvo)    －說明 g0v 與服貿關係）
- 工作目標：
    - 透過行業查詢建立民眾與服貿連結，增加進一步了解的動機與興趣。
    - 初步想法：
        - 透過關鍵字、公司行號名稱搜尋找出營業項目結果，並在可能受影響項目標色
        - 搜到多筆營業項目結果時，推定使用者應該可以自行判斷相關的營業項目
        - 點擊營業項目得到該業別的開放狀態（你被服貿了）、官方評估、民間影響⋯⋯
            - （Opt.）結合其他資訊，如救濟配套措施
            - （Opt.）結合服貿地圖
    - 進階：
        - 營業項目的附註，對照表括號裡的條件，連結至政府相關[行業分類說明](http://www.stat.gov.tw/ct.asp?xItem=28907&ctNode=1309)
        - （Opt.）兩岸開放承諾比較，參考[這裡](http://goo.gl/Gj2ryV)
        - （Opt.）眾包的編修，同類、包含項目補充
        - 群眾回饋（你服不服？量表）
        - 鼓勵民眾前往[白宮連署](https://petitions.whitehouse.gov/petition/oppose-trade-agreement-between-taiwan-and-china/C80BsZ11)
> succeded
> [name=nchild]

- 授權方式：CC BY 4.0（圖文）、Open Source 條款 MIT (X11)（程式碼）
- 使用資料：
    - g0v 服貿協議資料庫 [http://goo.gl/10WcZx](http://goo.gl/10WcZx)
        - 政府釋出之行業對照表，見 [http://goo.gl/fmdAOf](http://goo.gl/fmdAOf)（請先看說明檔）
        - 官方兩次評估報告
    - 主計處[行業標準分類](http://www.dgbas.gov.tw/ct.asp?xItem=28854&ctNode=5479&mp=1)

### 目前工作項目：

1.  分類對照資料庫處理 by [Shelling Ford](https://g0v.hackpad.tw/ep/profile/nl9nKXU6Z1L)
2.  行業分類連結、關鍵字處理 by [Shenk Wang](https://g0v.hackpad.tw/ep/profile/BBGX8lqNMr7)
3.  視覺設計 by 凜希
4.  前端網頁 by [Johnson Liang](https://g0v.hackpad.tw/ep/profile/z4JarLrJBea)， [Lucien Lee](https://g0v.hackpad.tw/ep/profile/qaqB0AtENES)
5.  例外處理、關鍵字補充（手動）
    1.  電信
        1.  我國分類除一類二類之外，二類尚有一般、特殊區別，需參照電信法規
> nchild 我先認養，提出可能的處理方式再跟大家討論
> [name=nchild]

    2.  金融
        1.  因為較為繁複，服貿協議附件就有獨立出來
> 看看有無對產業較了解的人能協助？
> [name=nchild]


- 徵求夥伴（有興趣直接簽名）：
    - NeedsWriter: ~需要文案幫手~（~改寫承諾內容為看得懂的話~）交給「開箱聞」專案
    - NeedsDesigner: ~需要介面設計~~（Optional，有最好）~
    - NeedsData: ~需要資料（~~現有文件為 PDF 或 Word 格式~~）~
        - [Chia-liang Kao](https://g0v.hackpad.com/ep/profile/AHlg3ouwI8g) 介紹 Tabula 可抓取 PDF 內容
    - NeedsTech: ~需要技術支援（程式、架站 etc)~
    - NeedsProcess: ~需要幫忙設計作業流程~~（Optional，有最好）~
    ....我不知道QQ 即時編輯整個壓力太大腦袋一片空白。
> 請有興趣的人拿去做或是提供想法 囧
> [name=lanfon]

> 行業對照碼這個賴律師與某教授作過了接到，這裡有資料，或許8/10可參考。
> [name=Kriis L]

> 有的，等下我會補鄭教授的資料上去。
> [name=nchild]

> 請問資料對應關係是看，舉例台灣某細項 m, n 對到 CPC 類別 a, b 二種來說，只有 (n 屬於 a 且 n 不屬於 b 若 a 不等於 b) 才會成立，還是 (m, n 屬於 a 且 m 屬於 b ) 成立？
> [name=Yau-Hsien H]


## 服務貿易協定受影響的產業地圖(tisa-map)

- 發起人/拋磚人：chiliJung
- 狀態：目前前端大概完成，需要一些設計，還有應該還需要一些文字的敘述。目前整個 project 差後端尚未完成，希望能在 hackathon 時完成整個計畫。
- 專案簡介：這個專案在 github 上為 tisa-map ( [https://github.com/g0v/tisa-map](https://github.com/g0v/tisa-map) )，目前規劃是要把所有在台灣會受創的產業列在一個台灣地圖上，也可以讓使用者可以加入反抗的連署，還有上傳反抗標語。
- 工作目標：hackathon 時完成
- live demo: [http://g0v.github.com/tisa-map](http://g0v.github.com/tisa-map)
> 這個現在變404了！
> [name=nchild]

- 授權方式：\`MIT (X11)\`
- 使用資料：[https://github.com/ronnywang/twcompany](https://github.com/ronnywang/twcompany)
- 徵求夥伴（有興趣直接簽名）：
    - NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案 etc）: WeiHung [wayne93024](https://g0v.hackpad.tw/fmMzGxzjh7A#wayne930242)[2](https://g0v.hackpad.tw/fmMzGxzjh7A#wayne930242)
    - NeedsDesigner: 需要介面設計
    - NeedsData: 需要資料（擷取、清理）
    - NeedsTech: 需要技術支援（程式、架站 etc):chilijung, shelling
    - NeedsProcess: 需要幫忙設計作業流程
- advanced
    - 目前我還規劃想要做公民運動的反抗地圖，可以讓使用者可以依不同的運動自己發起自己的反抗地圖。（不只侷限在這次的服務貿易協定）
    - 希望以後的運動都可以有這麼一個平台可以讓人民快速連署，然後再台灣地圖上標出（可能可以給使用者上傳一句話之類的簡單功能）。
    - 目前我已經 fork 一個專案到我自己的 github 上([http://github.com/chilijung/protest-map](http://github.com/chilijung/protest-map))
    - 當然這相較 tisa-map 來說比較沒那麼急
### 網站進度

- 功能：
    - 列出所有立委的資料
    - 使用者上傳標語
    - 使用者可以連署、並把使用者的位子記錄在地圖上
    - 把所有受害的廠商列在地圖上（有用廠商搜尋、用統編搜尋、用位子搜尋）
- 後端：目前都大致完成(shelling)，api 列表可以到 [http://github.com/g0v/tisa-map](http://github.com/g0v/tisa-map) 看
> 目前應該是兩個或三個營業項目才算入，建議排除「營事業代碼 _ZZ99999_ 除許可業務外，得經營法令非禁止或限制之業務」，讓納入的廠商資料更多更精確。
> [name=nchild]

- 前端還差上傳標語、連署、受害廠商列出來
- Github repo : [http://github.com/g0v/tisa-map](http://github.com/g0v/tisa-map)

## 3CFA 全民開黑箱

Introducing 3CFA -> [https://3cfa.hackpad.com/](https://3cfa.hackpad.com/)
"一起懂協議，一起爭權益" 開箱文太難寫，不如大家一起讀一起了解吧

挖坑總司令：小B (Littlebtc)

目前進度成果：
- 服貿 FAQ 初版完成-> [https://3cfa.hackpad.com/-FAQ-5TGrUxxB7ft](https://3cfa.hackpad.com/-FAQ-5TGrUxxB7ft)
- 自由貿易協定比一比 -\> [https://docs.google.com/spreadsheet/pub?key=0At2YbEvZjcMFdE9KNXczQjEzbktOaFZpRml5SklaUGc&gid=0](https://docs.google.com/spreadsheet/pub?key=0At2YbEvZjcMFdE9KNXczQjEzbktOaFZpRml5SklaUGc&gid=0)
- 不過很顯然路還很長 囧

短期計畫：
思考如何跟上述網站有所關聯

## 服貿開箱聞


有沒有辦法用一個視覺化的方式，讓人可以簡單地看懂這份協議：
- 服貿開放了什麼？
    - 原先是什麼
    - 職業被服貿了嗎？
        - 被服貿了
            - 服貿前
            - 服貿後
        - 沒被服貿：現在如何
### 要解決的問題和方法

> 政府真的有想讓人看懂嗎？
> [name=WeiHung]

- 兩岸用語不同
    - 透過行業對照表去對照
- 文字難讀到爆
    - 直接進行翻譯
[https://docs.google.com/spreadsheets/d/1T0joOZTioAXNSfjni7a89AycTSO8SmO57FMZ36abYj0/edit#gid=0](https://docs.google.com/spreadsheets/d/1T0joOZTioAXNSfjni7a89AycTSO8SmO57FMZ36abYj0/edit#gid=0)
> 勘誤一下：「除加入世界貿易組織水平承諾中內容和合同服務提供者 (附二) 外，不作承諾」並不是「不開放」，而是「比照 WTO 水平承諾只開放部分，只是我不承認你是國家，所以要重寫一次合同服務提供者這一段」。我先直接改了。
> [name=Hsiao-Ting Y]

- 排列方式混亂，難以比較
    - 接到「你被服貿了嗎？」上面
- 和現狀不知道怎麼比對
    - 接到「你被服貿了嗎？」上面
###  參考文件

- [資料夾：](https://drive.google.com/#folders/0B6ZiS9f8Cm9qaXJtdXh1R192aFE)[https://drive.google.com/](https://drive.google.com/#folders/0B6ZiS9f8Cm9qaXJtdXh1R192aFE)[#folders](https://g0v.hackpad.tw/ep/search/?q=%23folders&via=SUkMbG4IV6v)[/0B6ZiS9f8Cm9qaXJtdXh1R192aFE](https://drive.google.com/#folders/0B6ZiS9f8Cm9qaXJtdXh1R192aFE)
    - [服務貿易特定承諾表](http://www.ecfa.org.tw/EcfaAttachment/%E9%99%84%E4%BB%B6%E4%B8%80%E3%80%81%E6%9C%8D%E5%8B%99%E8%B2%BF%E6%98%93%E7%89%B9%E5%AE%9A%E6%89%BF%E8%AB%BE%E8%A1%A8.pdf)
    - 兩岸洽簽服務貿易協議對我總體經濟及產業之影響
    - [電腦名稱譯名](http://www.iicm.org.tw/term/termb_I.htm)[http://www.iicm.org.tw/term/termb_I.htm](http://www.iicm.org.tw/term/termb_I.htm)
    - 「網友 SLMT(小山) 依官方文件整理」[https://docs.google.com/file/d/0B6SwtGgTE4bCT0pnMTQxN1Z2ejQ/edit](https://docs.google.com/file/d/0B6SwtGgTE4bCT0pnMTQxN1Z2ejQ/edit)
###  項目

- 商業服務業
- 通訊服務業
- 營造與相關工程
- 配銷服務
    - 批發
    - 零售
    - 經銷
- 環境服務
- 健康與社會服務
- 觀光及旅遊服務
- 娛樂、文化及運動服務
- 運輸服務
- 其他
- 金融服務

## 懶人藝術家 x 服貿

[http://hack.g0v.tw/lazy-artist/3pKTjb5MCj4](http://hack.g0v.tw/lazy-artist/3pKTjb5MCj4)

## 文化部創作

目前存放[於此](https://drive.google.com/folderview?id=0B0NsS2a-Qx8ZQjVERzlDLUlHTFk&usp=sharing)，另可能有一些流落在外，需要整理。

## 參考資料

### 服貿協議的文本

正體／兩岸服務貿易協議\> 文本及附件
[http://www.ecfa.org.tw/SerciveTradeAgreement1.aspx?pid=7&cid=24](http://www.ecfa.org.tw/SerciveTradeAgreement1.aspx?pid=7&cid=24)
簡體／海峡两岸服务贸易协议（全文）
[http://www.gwytb.gov.cn/lhjl/laxy/201306/t20130621_4352344.htm](http://www.gwytb.gov.cn/lhjl/laxy/201306/t20130621_4352344.htm)

兩岸開放項目比較表：
[https://docs.google.com/file/d/0B6SwtGgTE4bCT0pnMTQxN1Z2ejQ/edit](https://docs.google.com/file/d/0B6SwtGgTE4bCT0pnMTQxN1Z2ejQ/edit)

PS.鄭秀玲教授／兩岸服貿協議對我國的衝擊分析／.pdf
[http://homepage.ntu.edu.tw/~ntuperc/conference-1-files/20130725\_3\_1.pdf](http://homepage.ntu.edu.tw/~ntuperc/conference-1-files/20130725_3_1.pdf)
[http://www.youtube.com/watch?v=ByWKj4S5Jts](http://www.youtube.com/watch?v=ByWKj4S5Jts)
[http://www.youtube.com/watch?v=vKm9DBxbFnQ](http://www.youtube.com/watch?v=vKm9DBxbFnQ)
[http://www.youtube.com/watch?v=amcYBpY533g](http://www.youtube.com/watch?v=amcYBpY533g)

CPC與W120對照表
[http://db.wtocenter.org.tw/w120.asp](http://db.wtocenter.org.tw/w120.asp)
Hung Pin 的微地圖，他說服貿地圖資料準備好之後也可以 meshup

## Hackathon 小記

### 0222 自由時代

- 改用政府對照表初稿
- 行業分類內容抓取
- 以視覺設計成果建置網頁
- 服貿文本試翻譯
- [Shenk Wang](https://g0v.hackpad.tw/ep/profile/BBGX8lqNMr7)、[Johnson Liang](https://g0v.hackpad.tw/ep/profile/z4JarLrJBea) 加入


### 12/21 勞動基準

- [nchild](https://g0v.hackpad.tw/ep/profile/tXyPGAkvFX9)  [挖坑](http://youtu.be/K1ooVjoWLaU)\+ [短講](http://youtu.be/WNMQ8Sstbvo)
- 重新定義對照方式
- 凜希、[洪偉](https://g0v.hackpad.com/ep/profile/CNcWt1F6Rge)、[Hanyu Chen](https://g0v.hackpad.tw/ep/profile/sTQBdtmoxp6) 加入
- 增加開箱聞專案

### 10/20 美麗島記錄

目前手上幾分對照表已經可以涵蓋需求，將先整合到線上試算表，惟其中有些註解（如不完全對照）部分處理方式無法確定，整合過程將累積這些問題請教專家，但其他確定部分就會請後端處理，目前想法是結果至少分三級，受影響、不受影響、可能受影響，需要後者的原因是，此次服貿開放的某些項目太細（如第二類電信特殊業務之中的三項），無法僅以主計處行業分類判斷是否受影響，此部分需要精確處理尚缺主管機關那邊的資料，故此類情形先列為可能受影響。

*以下是原先以為可以用的方式，但經濟部於公聽會推翻之前中經院報告對照，所以改等待經部正是針對服貿的對照
    各個環節的資料表鏈結
    Provisional CPC -> 主計處第八版的對照表: [http://www.wtocenter.org.tw/SmartKMS/fileviewer?id=105311](http://www.wtocenter.org.tw/SmartKMS/fileviewer?id=105311) 第十一頁
    服貿 -\> Provisional CPC 的表是 [http://www.rexhow.com/pdf/201306_842.pdf](http://www.rexhow.com/pdf/201306_842.pdf)
    所以再配上八版->九版對照表就應該可以做出(主計處分類->是否受影響)的表
    營業項目->主計處分類表: [http://gcis.nat.gov.tw/cod/v8\_ref\_BASD\_TAX\_CLASSIFICATION.xls](http://gcis.nat.gov.tw/cod/v8_ref_BASD_TAX_CLASSIFICATION.xls)

    全部資料都有了，不用相似字串了 \\o/
    ~太棒了，晚上我來確認一下~

### 10/1 小黑客松紀錄

by nchild: 記錄一下，我這邊做服貿文本對照行業分類， shelling_ 是用假規則先做出不同程度影響的呈現，另一方面 au 會研究相似字串比對（服貿減大陸地區人民投資項目），作出讓群眾驗證的介面（商業司營業項目對照主計處行業分類）。

### 8/10 國民大會綜合意見

- 烽益：直接用公司名稱查詢，列出營業項目，以營業項目比對
- 默默：相對於公司登記，應加入商業登記部分（商號／行號）
- S.C.：用商業登記字串比對營業項目，解決商業登記的行業別問題
- 冠宇、Cate：納入104人力銀行等資料進行比對，解決營業項目過多問題


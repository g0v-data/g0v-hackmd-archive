---
title: "vTaiwan.tw 行政院法規線上諮詢系統"
tags: EY,hackpad
---

# vTaiwan.tw 行政院法規線上諮詢系統

> [點此觀看原始內容](https://g0v.hackpad.tw/oWRxOF4ilfx)

上層：[動民主 lab](https://g0v.hackpad.com/-lab-BBRFMB6Ptw6)
下層：[網站文案](https://g0v.hackpad.tw/vTaiwan.tw--Why)、[參考文獻](https://g0v.hackpad.tw/vTaiwan.tw--aAkUCc44qRt)、[前端架構](https://g0v.hackpad.tw/vTaiwan.tw--SAG54HPVKK5)、[後端架構](https://g0v.hackpad.tw/vTaiwan.tw--RxmNaJogwnc)、[運作流程](https://g0v.hackpad.tw/vTaiwan.tw--yIoh6OFRR8o)、[問答集](https://g0v.hackpad.tw/vTaiwan-FAQ-bNNRo8iHKVf)、[宣傳文案](https://g0v.hackpad.tw/vTaiwan.tw--4iwJwiLu2ZB)
建置中：[GitBook](https://crowdfunding.vtaiwan.tw/) ↔ [Forum](https://talk.vtaiwan.tw/c/6-category)


### 緣由

可以不去開曼設公司嗎？

[g0v tw hackath11n 提案 g0v × gov 可以不去開曼設公司嗎？ 第拾壹次開放報禁黑客松](https://www.youtube.com/watch?v=QMS4HuFzwcE)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e71122b9288c12a88216b4dd6b5751f5)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ca668f10fab8caf1b011bd3f51b0e335)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7fbcae4b90431d70d03723b24a4ecf8e)

### 背景說明

初步的想像是用 [Regulation Room](http://regulationroom.org/rules/consumer-debt-collection-practices-anprm) 這類工具，對各議題使用行之有年的 IETF  SIG（工作組）模式：
- 一群對特定議題感興趣的人定期線上+線下聚會
- 一系列協定文件的各版本草稿（可即時討論，以及 fork，類似  GitBook）

**編輯**人員的工作是：
- 整理成定期公報、回應看到公報的人提出的問題
- 彙集每次參加的（人際）聯結和（網址）連結
- 預先設定的時程裡寫出初步意見稿、草稿和定稿

在[循環圖](https://docs.google.com/drawings/d/1_AYWazW9FMLgNwfNj_och4r5nIMbhFyi2IhZpXyMxh8/edit)上，這次試驗處於「提案」的位置。
運作機制請參考[社群媒體與政策制定](http://www.slideshare.net/autang/ss-42792460)建議書：



### 跳坑區

- 主揪: jaclyn, helena
- 前端: au, yhsiang, pm5, soidid
- UX 設計: ginger, soidid
- 後端（格式轉換、上稿系統）: billy3321, pm5
- 懶人包: peggy
- 版面管理（執行版主工作，不需法律科系背景）: 婷宇
- 素材提供（包括字典維護）: stella, veronia
- 打雜: pofeng,路人甲(這是一個id),  kiang, pm5
> 請打雜人士和其他跳坑的朋友幫忙訂正 [vTaiwan.tw 網站文案](https://g0v.hackpad.tw/vTaiwan.tw--Why)，感謝！
> [name=Audrey T]

- 工作組後勤：ronkuo, jim

### 工作項目

- [x] 翻譯[社群媒體與政策制定](http://www.slideshare.net/autang/ss-42792460)建議書（au）
    - [x] 註冊 vtaiwan.tw 和 vtw.link 網域（au）
    - [ ] vtaiwan.tw 做成 landing page 給討論、草案參與者用（ginger）
    - [x] vtw.link 做成 hackfoldr 給專案工作組用（au）
- [x] 挑 2 項法規調適主題，提出說明和影響範圍簡述（Sean）
    - [x] 確定是「閉鎖型公司」（經濟部）與「群眾募資」（金管會）為第一波主打（helena）
    - [x] 上傳到 vtw.link (veronia, 12/22)
        - [x] 目前權限設定為[只有編輯團隊](https://drive.google.com/drive/u/0/#folders/0B9tD1zENsweyU21IaTdrQ0J4eXc/0B9tD1zENsweyRDQ2YmliYmRrdVU) 看得到（au）
        - [x] 決定這些文字素材是否能採 CC BY 4.0 授權釋出（jaclyn, 12/23 已確認，詢問原作者中）
        - [ ] 轉成適合 GitBook 使用的 Markdown 格式
    - [ ] 寫 Charter，組成工作組
    - [x] 社群相關討論彙集到主題裡（billy3321）
        - [x] PTT
        - [x] FB（目前僅可抓取自己的貼文）
- [x] 於開放報禁黑客松提案（Jaclyn）
    - [x] 黑客松成果報告（au）


## vTaiwan架構草稿

> 模糊聽模糊寫XD 我對三個階段的內容還是有點亂，歡迎幫改啦~~~
> [name=羅佩琪]


### 起源

- 台灣許多公司都會跑去開曼群島之類的地方設立，為什麼不願意留在台灣呢?
- 我們希望能透過具體的法律制度，完整討論這個問題、進而為解決這個問題形成法規草案。

### 核心想法

- 政策形成與法令訂定過程透明化，預計用公司法與群眾募資相關法規當第一場實驗。
- 為什麼是公司法與群眾募資?  公司的主要功能之一，便是募集資金以持續經營。而群眾募資也是一種吸引投資資金的工具。這兩者都是台灣值得進一步檢討的地方。
- 參考：[regulationroom.org](http://regulationroom.org/)

### 運作方式

#### step 1：Discussion - 提出要討論的問題

- 範例：[LINK](http://regulationroom.org/rules/consumer-debt-collection-practices/discussion/telling-consumers-whats-happening-their-debts)
- 概念：不是一開始就給法規草案討論，而是「提出問題」來討論。ex.很多新創事業想透過群眾募資平台來進行投資，現行制度卻不見能滿足這些新創事業，那會有什麼問題，以及該怎麼規範呢？
- 討論方式
    - 依照問題、子問題，列出what、why、how，topic下再分sub topic
    - 使用者可以任意在想討論的區塊comment，網路上討論的FB、twitter可以用嵌入的方式也納入討論
> 未來這個部分如果有被納入法規，也需要一套機制反饋給原FB留言者
> [name=羅佩琪]


    - 這階段的討論將會形成一個草案版本，在vTaiwan的處理方式，可能會抓出幾個討論中~特別吵~參與良好的人形成工作小組，工作小組負責做出該法規/議題的gitbook，並有實體會議，線上直播，草案逐條完成的過程大家都看的到。
> 或許這個階段，可以針對所提議題，彙整現有的 [科技部科技計畫管理資訊平台](https://nscstp.stpi.narl.org.tw/index.htm )(國科會計畫、研究報告)、[內政部遊說法資訊專區資料](http://www.moi.gov.tw/lobby/)、國家發展委員會 [法規鬆綁建言平台](http://law.ndc.gov.tw/index.aspx)、[國發會法制協調](http://www.ndc.gov.tw/m1.aspx?sNo=0000128#.VBMplPmSw-8)、[電子採購網中判斷與討論議題有關的資料](http://gov.playgroup.com.tw/) ...等，作為預設的盤點工作，挑出與議題相關的建言與遊說意見，提供公眾閱讀與參考。
> [name=che l]


#### step 2：Draft Discussion - 草案版本討論

- 範例：[LINK](http://regulationroom.org/rules/consumer-debt-collection-practices-anprm/draft-discussion-summary/telling-consumers-whats#nid-327)
- 討論方式
    - 針對step1所形成的草案版本進行大亂鬥comment
    - 針對step1所形成的草案版本，民間NGO及團體可以也提出自己的版本，最後就會變成【step1產生的版本】 vs 【NGO版本一】 vs 【NGO版本二】....
    - 此時可以用給問：抓出幾個關鍵爭議議題，要求幾個版本的發起人限期回答，如果沒有回答就會有通知alert
> ps. 沃草表示：給問剛才已經open了
> [name=羅佩琪]

> 感謝！已 fork 到 [https://github.com/g0v/react-ask-app](https://github.com/g0v/react-ask-app)
> [name=Audrey T]

> 會開始整理 codebase 做[分項提案問答](http://2014final.wethepeople.tw/candidates/7/questions)頁面
> [name=Audrey T]


#### step 3：Final Discussion Summary - 收斂

- 範例：[LINK](http://regulationroom.org/rules/consumer-debt-collection-practices-anprm/final-discussion-summary/final-summary-introduction)
- 收斂負責人：政府機關內主責單位，ex.經濟部(公司法)、金管會(群眾募資)
- 進行方式
    - 因為step2可能會run很久，目前想法是可以設個期限，或是設定第二輪run的次數上限，例如四次之後就要收斂。
> 這邊意思是說run完1次後草案會修正然後再run 下一次嗎？
> [name=Yuan C]

> 是的。但如果 step 2 工作組聚會後都覺得沒問題，草案就成為 step 3 定案。
> [name=Audrey T]

    - 至於機關怎麼收斂？這部分最困難......至少可以做的事情是，針對有被提出的爭議點，去說明為什麼接受某一版本的說法，而不是其他版本=>至少把接受/拒絕原因寫出來
    - 這個階段的收斂版本出來後，基本上不會再有新的討論，除了是法規撰寫上的錯字、條號錯誤等

#### 其他討論

- 使用這套流程的順序：先用比較沒人注意的開曼試試看，衛福部、國發會最後再進來，因為可能會比較有爭議
- 問題：以一些法規利害關係人不會用網路怎麼辦，ex. 遊民。=> 有些國家會在戶政事務所來做審議民主(搭配手勢)，有人做逐字稿，再把這些實體世界的意見貼回平台。
> 議題利害關係人與溝通偏好，應該在第零階段有一些評估與掌握？或是於第一階段中，不論什麼議題都要檢視、盤點相關利害關係人是否可以充分參與。例如醫療政策，也需要配合醫療從業人員的作息邀請他們參與？
> [name=che l]


## 參考網站：[regulationroom.org](http://regulationroom.org/)

vTaiwan的參考原型是cornell university做的[regulationroom.org](http://regulationroom.org/)，運作約兩年，強烈建議大家打開網站先瀏覽，對於理解vTaiwan的規劃會很有幫助。以下簡記今天聽au介紹這個網站的幾個重點：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ec4ab9e9c1cc309862fe75a8ca0ed4a6)

### 首頁的說明

有非常~有煽動性~說服力的網站說明圖文與影片，包括：
- What is RegulationRoom?
- What is rulemaking?
- Why should you participate?
- What is effective commenting?

### 階段一：討論

- 在[頁面](http://regulationroom.org/rules/consumer-debt-collection-practices/discussion/telling-consumers-whats-happening-their-debts#nid-184)上有「愛心」的圖示，可以訂閱討論牆
- 會詳列目前方案的做法、優缺點、成本等背景知識
- 名詞都會有明確定義 (滑鼠移上去就會看到)
- 除了有民眾comment外，也有moderator做回應
- 為了增加有效討論，moderator 會把好的/有效的 comment 標注為推薦（愛心圖案）

### 階段二：草案

- 第一階段是丟問題、背景知識，第二階段是討論的彙整，讓大家來超級大亂鬥

### 階段三：定案

- 完全是法規的文字了
- 也會附上最後成為法規的連結、負責機關的法規頁面超連結


## 提問

#### 如果有參與者對於第二階段的討論無法同意，對於第三階段的定案結果，也無法滿意，這個情境會如何？行政訴訟XD ?


- 定案結果由於屬於政策，非屬行政行為，只能依照請願法進行請願，不得進行行政訴訟。請願法第二條：人民對國家政策、公共利益或其權益之維護，得向職權所屬的民意機關或主管行政機關請願。
- 另外，定案結果如果是法案，由於法律還需要經過立法程序，因此人民仍可以透過立法委員在立法流程中表達意見。
- 如果定案結果是制定法規命令，依照行政程序法第154條，法規命令之制定應公告周知，任何人得於所定期間內向指定機關陳述意見之意旨。另外如主管機關依照第155條舉行聽證，也可以透過聽證程序表達意見。

#### 問題的架構（要討論哪幾個主題）是由主管機關/發起人都出來的，如果參加者不同意的話，是要接受目前討論的框架就是這樣嗎？（例如列出了 a, b, c, d, e 五個子主題，參加者認為應該還要討論 f 這個主題才算是完整）


- 目前在第一階段（背景及意旨討論）的主題是機關提出的，但當第二階段（草案）開啟時，工作組聚會可以將與草案內容相關的新主題納入討論，兩階段主題列表不需相同。
> 贊成將這兩塊分階段，一來是讓大家於第一階段知道公部門的初心(?)，第二階段可以盡情提供不同的問題架構觀點，改變問題框架、議題的多元影響評估之類的。
> [name=che l]


#### Bill Lab [https://github.com/clkao/billab](https://github.com/clkao/billab)  的應用情境，可以視為支援第三階段的法規條目編修過程？


- 對，如果是對既有法規的修正，那 billlab 式的呈現是不可或缺的。
- 如果是新增法規或解釋文的話，則不需要。

[頁面](http://regulationroom.org/rules/consumer-debt-collection-practices/discussion/telling-consumers-whats-happening-their-debts#nid-184)


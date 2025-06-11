---
tags: vTaiwan小松
---
# 20250611 vTaiwan 小黑客松
時間 Time ：19:00 - 20:00
地點 Location ：線上 Online
參與者 Participants: Peter, Bestian, Joey, Tim, Yuting, 阿南Anan
線上參與連結 / Link：https://meet.jit.si/vtaiwan
![](https://g0v.hackmd.io/_uploads/ryIoggwmgx.png)

今日會議討論：
7:01分花蓮地震 

Bestian:部落格 新增流程和 Peter確認

Peter:(上禮拜的骨折 比較偏審議 )上禮拜在美國所以上禮拜沒有參加。
用ＡＩ用於數位公民審議部分，有一個美國公民組織 people powered(群眾賦能) 探索數位工具再審在和公民討論的做用，他們也知道 vTaiwan，和vtaiwan業務性質相近，他們之前對口 熱吵民主協會（拿到 諾曼基金會的經費，去做一些相關的研究）vTaiwan之前也有拿過這個基金會的支援，所以之前有收到諾曼基金會信件說「people powered(群眾賦能)」有在做審議調查，目前有用信件 connection 中，爭取明天和他們聯繫討論，彙整之前的討論意見。用AI把活動前收集意見做摘要，事前徵集意見，活動過程當中也用AI即時性的更新大家的回饋（有發現字詞問題，大家的問題變得比較難閱讀，另外是ＡＩ生成分析過程中，會有一些奇怪的模式）上禮拜跟新參加者骨折討論後，下禮拜要花時間修正共筆，希望在每個共筆上建立清晰的架構。像請問大家共筆架構有沒有想法和建議可以幫我我讓共筆更清楚？
* Freankly測試
* 網站更新
* 專案管理更新
* 對外的拓展 T aisa?
* 
* 
* 

Anan阿南：作為一位新參者，不太能看懂文件，但目前透過三次會議和共筆做紀錄來理解 VTaiwan，但我確實想花時間看 先前 vTaiwan 的 Threads資料，但目前還沒有時間。

Joey:還是之後可以把共筆整理成一個資料庫 ，自動化跑一些更新。

Tim：(to Bestian: 題外話，關於處理螞蟻，以我過往的經驗可以去超商買螞蟻藥 

Bestian:網站的部分是可以讓新參者快速了解內容。我想請問 Peter 是否你只要編輯靜態資料（自動 push到網站），你就不用更新網站，對Peter來說會不會是一個障礙？

Peter:我蠻贊成用靜態資料。理想狀況下是我能在網站上發布新活動資訊，包含審議活動內容，像Medium那樣可以ＰＯ文章，次佳的方式是像ＦＢ。

Bestian:那就是像blog，將文章送到 Firebase，你可以看一下https://vtaiwan.pages.dev/blogs/

Peter:我覺得豆腐之前的架構蠻理想的。

Bestian:之前就是和豆腐之前的架構一樣。測試貼文，目前有點問題，已經寫成 issue: https://github.com/g0v/vtaiwan-neo/issues/9
靜態資料會變成電腦裡的 json資料(array of object)，只要有活動介紹和網址，就可以編輯成靜態資料。可以省新增編輯器工程。

Joey:原來如此！感覺很方便

Peter:靜態資料長怎樣？不是連 MD檔案，也可以連結網站？

Bestian:可以。像 hackborder? 

Peter:之前我是很常用 book架設網站。我接下來會想做的 Actions lists如下：
- 把網站更新時程排出來（主視覺）（年底上線）要約會議時間來抓Milestone時


Bestain:Github有 milestone功能 可以用來抓時程，示範中....豆腐卡關中的，我可以幫忙，但要等豆腐提出來。

Peter:我習慣在slack非同步，但也想學習Github的非同步。要成立一個 line 或 FB Messagger的工作群。

Bestian:Github的好處，會將討論寄email到信箱，可以同步管理很多專案。

Peter:好啊，用Githhub的email管理挺好，因為我現在頻繁用不同工具溝通。會同步準備一些內容，讓新參加者更容易理解。Frankly的測試空間，TFGA 的活動開始前有很多議題（例如數位身分）,可以先來測試。利用每週小松時間，先在 g0v招募有沒有人有興趣來做小規模的Frankly測試

Betian:Frankly中文化已經處理。但是上游在部署的問題上還在解決。

Peter:我認為要寫一下Frankly使用說明。從ＮＧＯ著手，若有一個線上討論工具，就可以進行不同議題的討論：司改會偏數位人權的NGO都有審議和討論的需求，我有在教育部但任審議的業師，我也可以推薦給他們。

Bestain:還在等Frankly的 close beta釋出中，他們開發還需要時間。

Peter:用現有的測試空間來測試就好，沒關係。今天討論還是比較發散，我會再整理。上禮拜我去華府參加ＡＩ相關活動，那個活動比較偏向 AI 和 國防展覽。但我朋友有揪一個討論蠻有趣的，之後我會把資料放給大家看。也有發現大家利用審議民主不管是解決民主倒退是有興趣存在的，人工智慧的出現也可以幫忙貢獻一些。

Tim:那大概會約什麼時侯測試 Frankly 呢?第三次議題小聚共筆何時要整理？

Peter:有標準化程序了。但是第三次議題小聚共筆 還沒有....?議題小聚緣起，討論內容 事前議題徵集方式 會在 slack開一個訊息的thread讓大家來跳坑

Tim:測試 Frankly時間還要再約嗎？

Peter:Bestian我想確認一下如何開Frankly？

Bestian:用開 event的方式來跑

Tim:Bestian覺得何時內部測試較好？

Bestain:任何時間都可以。因為要等他們中文化部署不知道要等到何時。但是核心功能都已經完成了。所以才會有 close beta讓大家測。

Peter:我發現宇亭有上來。總結今天會議討論中：下次討論Github 網站製作時間六點半會議先開始；共筆更新讓新參加友善，到時也請新參者阿南Anan幫忙看看，也會和豆腐要視覺.....已經取得錄音檔和逐字稿會邀請大家一起來協作....我發現最近我自己要調整一下，因為工作忙，要找時間投入專案。今天告一段落，如有疑問，請在 slack丟上來。（請 Peter再自行整理補充）


#### (會後update網站最新情況)

已用純Vue框架複刻整個專案，並重新部署，以解決框架層級的bug
https://github.com/g0v/vue.vTaiwan-neo

> [name=bestian]


## 自我介紹與新手導覽
- [新手簡報](https://docs.google.com/presentation/d/1ELAVIpaPVCmAx7nq-7e8-SVrckZ4ohRwn3V-TSpe78U/edit?usp=sharing)
### 自我介紹
- Peter :vTaiwan協調人 坑主 最近和豆腐在想如何讓手上工具使用的更頻繁一點
- Bestian: 有螞蟻 暫時關鏡頭 主要是在非營利組織 自主學習促進會資訊長 和 vTaiwan的關係是最近參加了 Frankly中文化開發 也想多了解中文審議工作，之後也可以幫忙協助網站開發
- Joey: 我是 Joey 目前是實驗教育高一生一枚 前幾週缺席了好多次小聚 今天終於有空參加ㄌ 三個關鍵字：議題探索、攝影、科技工具研究 
- 阿南Anan: 第三次參加，可以幫忙網站程式，和參加審議活動，比較偏技術，目前確實常常在做 Vibe Coding,AI會的我應該都可以幫忙解決問題

- Tim：哈囉我是Tim，三個關鍵字：事實查核、vTaiwan、視覺化
 
## 小小的分享
- 目前 vTaiwan 專案近況
    - 前幾次活動紀錄
    - 網站更新
        - content 維護與治理機制
    - 共筆更新
        - 讓新參者更容易加入
    - 主視覺更新
        - 
    - 專案管理機制更新
        - 從 notion 轉到 github
### Action LIst
- 利用 github 的 milestone 來抓時程
    - 例如如果要年底上線的話，就可以反推樣稿與最小可動版本上線的時間。
    - 7月底：樣稿完成
    - 9月底：MVP 完成
    - 12月底：網站上線

![](https://g0v.hackmd.io/_uploads/rJD83kwmgl.png)


- 網站更新的部分，要每兩週約一個會議，可能利用小松以前例如18:30。
    - 如果在 github 上非同步的話，每兩週開會
    - 需要成立 github 以外的訊息？
        - github 可以同步到信箱
### 讓新參者更友善的方式
- 
### 官方網站更新
> vTaiwan新網站fork至[g0v/vtaiwan-neo專案](https://github.com/g0v/vtaiwan-neo)
> 在cloudFlare Pages上部署成功：https://vtaiwan.pages.dev/
> [name=bestian]
> 請問這個 CLOUDFLARE 是 G0V的嗎？[name=阿南Anan]
> 是用個人帳號上去部署的
> G0V好像只有Github社群，並沒有一個自己的cloudFlare帳號
> [name=bestian]
> 上週五和tofus連線，把部落格功能做成登入後可以post文章了[name=bestian]

後續的架站優先順序，請在[此Github議題](https://github.com/g0v/vtaiwan-neo/issues/5)討論
### 美國行
- AI與國防和地緣政治
- 審議民主相關討論(之後再放上channel)
- 
## 主視覺更新
- facebook、IG、twitter 要一併更換
- 之後的 ppt 模板也要修改
- 本週把更新主視覺的各種文案處理好
:::info
預計下週要把文案生出來
#### Facebook 粉專文案

#### IG 文案

#### Twitter 文案

:::
- 更換大頭貼的圖片放置區
- Facebook 的背景也要重新繪製
- [主視覺雲端硬碟](https://drive.google.com/drive/folders/1vyFi55rPWi0nHuRTm4C1J4JwiMVcbRUx?usp=sharing)

## 專案管理

目前g0v上的[Github project vTaiwan](https://github.com/orgs/g0v/projects/2)和[g0v/vtaiwan-neo專案](https://github.com/g0v/vtaiwan-neo)的議題區是可以連通的

目前新的議題可以同步呈現在project的TODO上


### Github 帳號

> 骨折也可以在slack 把你Github 帳號 發私訊給我 [name=bestian]


## 審議小聚程序想法
- [FNF AI 用於數位公民參與共筆](/nJUYukWFSWuEsG-XQalHcA)
- 樹狀圖分組
    - 分組先，再看仔細分析
    - 
- 前後兩次問題vs一次討論一次結論
- AI整理想法
- 是否需要更多onboarding

## Frankly 坦白說測試空間
- [vTaiwan Frankly 空間：對話工具的可能性](/i2uTLlqcSzm6w-3akHfjLA)
- 是否有人願意跳坑，來試試看辦一場小規模的線上討論會？

> 這個Bestian應該可以跳坑嗎?就用「教育部的手機統一保管政策草案」這個主題?加上Bestian也熟 Frankly。[name=阿南Anan]

> 其實我也沒有用過Frankly主持會議，建議由熟悉主持的人來主持。另，填問卷與依答案分組的流程可能要先預演過。[name=bestian]

- 議題？
    - 利害關係人分布比較分散
- 參與者？
    - e.g. 全台灣各地的學生討論學校禁手機（不可能只訪問台北的學校）
    - e.g. 還包含家長或老師等等
- 進行方式？
    - 參與車馬費是否需要支付? 如何遠程支付? (高中生不一定有銀行帳號)
    - 高中生不一定會覺得時間成本一定需要支付


## TFGA 
- [vtaiwan x Tech for Good Asia 合作](/PdvNjkLlSd-WytXN_otWbQ)


    > 豆腐：Peter最近談到的一個合作...進行的流程和 VTaiwan傳統流程一樣，要寫出報告就有經費。另外最近和豆泥談數位身分，今天也和韓國朋友談數位身分的落地。WorldID 最近很紅？
    

## 數位身分
- world id 議題？
- 政府與數位證件之間的關係
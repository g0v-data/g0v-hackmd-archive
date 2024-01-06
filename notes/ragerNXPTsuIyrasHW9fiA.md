---
tags: Health, 健檢
---

# 智慧健檢平台

## 目的

每個人都可能因為對於健檢規劃的不同，而忽略潛在疾病的發生。本專案希望透過建立一個智慧健檢平台，讓使用者可以根據個人基本資料、家族與個人疾病史，以及預算提供健檢檢查項目與分級的建議。目前正在招募資料彙整與分析、網頁前後端工程師、設計師以及想要改變複雜健檢資訊的夥伴。

* 降低健檢成本（時間、金錢、知識）
* 降低整體醫療支出
* 清楚易懂，翻譯蒟蒻
* 提醒使用者，了解自身更需要健檢的項目，並且也可以在常見的健檢項目機構中選用

---

## 資料收集清理及前後端技術招募中
### 報名<數位發展部公民科技試驗場域示範案>

- 健檢資料收集彙整
    - 跳坑：
    - 工作事項：
        - 健檢相關模型訓練資料收集彙整清理
        - 介接公部門取得資料及支持
- 聊天機器人LLM模型開發
    - 跳坑：Thomas
    - 工作事項：
        - 以基底LLM模型強化學習健檢內容
        - 提供後端api取用LLM服務
- 後端工程師
    - 跳坑：,(Thomas)
    - 工作事項：
        - 接收聊天機器人的資料紀錄於db
        - 連接LLM提供回答及問follow up問題
        - 以LLM整理使用者聊天紀錄彙整並建議健檢注意事項提供前端
- 前端工程師
    - 跳坑：
    - 工作事項：
        - 網頁呈現使用者的填寫內容，網頁或提供一份 PDF 文件下載網址
        - 網頁健檢相關知識及專案服務的宣導推廣
        - 未來? 如果使用者不想在Line,可以提供使用者在網站登入填寫
- 地方政府衛生局
    - 跳坑：
    - 工作事項：
        - 協助模型訓練內容準備及審核
        - 健檢宣導內容提供及審核
        - 推廣專案服務



# 會議筆記

20220616 會議筆記，與臺南市衛生局交流
https://docs.google.com/document/d/1gUcOg3-X5XidE9b_InzO6SWwvPlQyhxGUxxDAp4jSqU/edit


# 產品定位探討

依照健檢前、執行健檢、健檢後等階段，定位已知政府與產業角色
並嘗試放入產品位置，[簡報編輯網址](https://docs.google.com/presentation/d/1KRO7IxPdtlzYEVS4n6Ik6sxmKiZN_PpAM6mMmwYVZQs/edit)
<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vSLo2bvDL-Osr8omA4fwlrAfAJQgKy1ubeXBJkXeJWw7Rbi4sJGrmiIapNYtEy1mAAEfrscUKM0Gihd/embed?start=false&loop=false&delayms=3000" frameborder="0" width=100% height="460" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>

# 產品構想

## 使用者

- 使用者本人填寫自身的資料
    - 情境：勞工健檢前，希望填寫並了解自身健檢重點
    - 情境：病人家屬，基於家族病史與親人照護的經驗，會有健檢的動力
- 使用者填寫他人資料
    - 代替長輩填寫


## 功能

使用者完成「pre-健檢的個人資料」
- 使用者填寫基本資料，形成「pre-健檢的個人資料」
    - 功用一：讓民眾，可以先填好自己的基本資料，讓這份資料已經準備後，對接健檢
    - 功用二：過程中，讓民眾知道，每一題填寫的內容，會影響後續的檢查項目是否精準

使用者取得「pre-健檢的個人資料」所判斷的檢查建議
- 依據填寫的基本資料，提供幾個重大疾病的危險性、檢查建議
    - 根據死亡人口、生活習慣等等，要找更多的研究、統計資料
    - 可參考「業界既有產品」：https://g0v.hackmd.io/Sks_r0RMSnGWT3Ng2DzS3w
- Linebot 
    - 介紹影片：https://youtu.be/qRy6eZ3TC2Q
    - 簡報：https://docs.google.com/presentation/d/16mamO2o-w7ukE_r2taY1IdeH1fkhVY8w-UxqKFZpXK0/edit#slide=id.p
    - 填寫後，給使用者的回答
        - https://integri-mount-llm-studio.notion.site/integri-mount-llm-studio/2380a0061e2442818f2a2cb3f50f3626#73fb32e35da34492a41daf1c5c7dbe97

使用者查找可提供自身所需健檢項目的健檢單位
- 健檢服務提供者地圖：讓使用者更容易依據檢查項目、預算、地區等條件找到自己想要的健檢項目
    - 價格、健檢方案、使用者回饋等等
    - 可參考「業界既有產品」：https://g0v.hackmd.io/Sks_r0RMSnGWT3Ng2DzS3w
    - 討論筆記：
        - 業界產品是否還有課題缺口？
        - 可由社群維護？
        - [QGIS](https://qgis.org): 開源軟體、可使用者協作

## 健檢前，要輸入的資料

- 完整項目，可參考「臺南愛篩檢-成人健檢問卷」：https://g0v.hackmd.io/IEWMklrsSk2nbxBoTHqmPg
- 填寫項目舉例
    - 基本資料（性別、年紀、生活習慣。儘量量化，精準量化才能建模）
        - 性別：男、女、其他
        - 生活習慣:
            - 抽煙（煙齡、一天幾包）
            - 喝酒（一週幾次，一次多少，或一週多少 cc）
            - 嚼檳榔
            - 幾點起床，幾點睡
            - 工作類型，幾小時 (be more specific 可能是每天加班多久)
        - 運動習慣：
            - 一週幾次每次多久
        - 飲食習慣：
        - BMI
    - 家族（父、母、兄弟姊妹）、個人病史
    - 預算（月/年）
    - 使用者自己已知的且重要的健檢項目
    - 使用者額外對某些項目更在意，如時事新聞、自己的判斷等


### 問項題目清單參考
- 參考：台南市政府衛生局建立的線上問卷
    - https://www.surveycake.com/s/aLAbK
- 參考：中央釋出的項目
    - 衛生福利部109年8月21日修正發布「醫事服務機構辦理預防保健服務注意事項」，自110年1月1日生效。
    - https://www.hpa.gov.tw/Pages/Detail.aspx?nodeid=838&pid=13055
    - pdf: https://www.tma.tw/doc/1198收文_附件1.pdf
    - 例如國民健康署定量免疫法糞便潛血檢查表
        - http://sc-dr.tw/health_form/inquire/06_13.pdf
    - http://www.rootlaw.com.tw/Attach/L-Doc/A040170071010500-1070718-17000-005.pdf
    - [醫事服務機構辦理預防保健服務注意事項](https://ws.nhi.gov.tw/Download.ashx?u=LzAwMS9VcGxvYWQvMjkyL3JlbGZpbGUvMC8yMjUyNS%2FnmbzluIPkv67mraPjgIzphqvkuovmnI3li5nmqZ%2Fmp4vovqbnkIbpoJDpmLLkv53lgaXmnI3li5nms6jmhI%2FkuovpoIXjgI0oMTA2LjA1LjAx55Sf5pWIKS5wZGY%3D&n=55m85biD5L%2Bu5q2j44CM6Yar5LqL5pyN5YuZ5qmf5qeL6L6m55CG6aCQ6Ziy5L%2Bd5YGl5pyN5YuZ5rOo5oSP5LqL6aCF44CNKDEwNi4wNS4wMeeUn%2BaViCkucGRm)
    - https://www.tma.tw/doc/1198收文_附件1.pdf
- 可以找認識的醫生朋友，看看醫生通常都問哪些問題，來引導看診者選擇健檢方案


### 技術方案

- 智慧表單，一開始從簡單的問題開始，隨著模型越來越精準 & 更多的專業建議，可以問更詳盡更精確的問題。
- Linebot 介紹影片 https://youtu.be/qRy6eZ3TC2Q

<iframe width=100% height="490" src="https://www.youtube.com/embed/qRy6eZ3TC2Q" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>


#### 未來：可串接代入的資料
* 健康存摺，就醫紀錄，健康存摺介紹: 
    * https://www.youtube.com/watch?v=O_O9mtMOOxs
    * 近三年之西醫門診、中醫門診、牙醫門診，以及用藥、手術、住院、過敏資料、檢驗（檢查）結果、影像或病理報告、醫療影像、出院病歷摘要
    * 健保快易通 APP >「健康存摺」>「檢驗檢查結果」
    * 可以輸入自己的健檢歷程嗎？
        * 可以, 自行輸入需要一筆一筆自行輸入, 會導致低使用率
        * 自108年7月起新增病人同意醫療院所協助上傳之自費健康檢查資料。
    * 截至108年7月底，「健康存摺」登入及使用人數達138萬人
    * 與健保局合作的醫療院所，都會提供至健康存摺
    * 但個人健檢自費檢查，可能需要特別要求健檢單位上傳資料，而不會預設上傳
    * 內建的風險評估項目
        * 有提供「肝癌、腎病、心血管」的風險評估，應該是直接帶入存摺內有儲存的健檢數值，也可單次輸入後計算
* 健康存摺，如何記載健檢資料？
    * 同一個抽血檢測項目，寫法不同 
        * CA199
        * CA-199
        * Ca 199
            - https://testdirectory.questdiagnostics.com/test/test-guides/TS_CA_19-9/ca-19-9-serum?p=r
            - Quest Diagnostics could serve as the standard
* 串接申請說明
    * SDK https://www.nhi.gov.tw/Content_List.aspx?n=A5407A276376FECC&topn=5FE8C9FEAE863B46
    * 使用者的身份證字號
* 健保資料庫開放資料可做研究整理台灣各區域各年齡性別好發疾病(需IRB及申請)
    * Pages 30-36: https://www.cdc.gov.tw/Uploads/files/80b59ada-1010-4fc4-9b2c-d88aabb152e8.pdf
    * 找看看是否有研究成果，已公開的內容 > 初步搜尋目前相關論文好像為2009年:
        * 運用資料探勘技術於全民健康保險研究資料庫之研究－以國人六大死因疾病為例
    * [政府資料開放平臺-死因統計](https://data.gov.tw/dataset/5965)、[內政部人口統計資料](https://www.ris.gov.tw/app/portal/346)
        * 根據死因統計去得知特定年齡性別的疾病死亡風險
        * 之後還需要醫療專業方面的協助來推薦適合的檢查項目？
* 法規
    * 醫事服務機構辦理預防保健服務注意事項
      https://www.hpa.gov.tw/Pages/Detail.aspx?nodeid=838&pid=13055
      https://www.tma.tw/doc/1198收文_附件1.pdf

#### 未來：不確定如何串接的資料來源
- 運動習慣
    - Google Fit 
    - 運動類 app
    - Fitbit and Ouraring have APIs ready to retrieve data
        - https://dev.fitbit.com/build/reference/web-api/
        - https://cloud.ouraring.com/docs/
- 飲食習慣
    - 手 key
    - 每餐拍照
        - FoodyLife

## 完成健檢後，保存資料、取用資料、研判資料

使用者需要保存自己的健檢資料
- 推薦作法：做完檢查的數據，請健檢單位上傳資料至「健康存摺」
- 健檢資料數位化的工具或服務
    * thomas> 自費健檢項目醫院一般不會上傳, 但可要求醫院上傳到健康存摺(上傳內容的呈現方式是否適合人閱讀待驗證, 健康存摺會有**三年**內的資料)
    * chiwen> 私人專門做健檢的機構有
    * yvonne> 國泰是給紙本+光碟
    * chewei> 個人健檢經驗，都是拿到紙本報告...
    * 相關產品：[「Health Pass 健康護照」App，使用者 拍照掃描紙本報告上傳保存](https://www.techbang.com/posts/68696-healthpass-app)

使用者需要取用自己的健檢資料
- 匯出上一次健檢的資料，讓醫生了解過去的檢查歷程
    - 目前的健康存摺是否已有此功能？
        - Previous version had this function. However, this function has been cancelled. 
    - 健檢後資料匯入後，匯出報告或建議內容，變成一個套版成果報告
        - Dante Lab provides each WGS user a personal medical report, which integrates the user's WGS-based genetics report and medical history provided by the user.
- 訪談醫生（例如家醫科），瞭解實務上有什麼需要幫助的地方、遇到的困難
    - Comments: It doesn't really matter whether this process is automatic or not. These reports don't help diagnosis much in a clinical setting, while a letter from another MD would be helpful.

使用者不曉得健檢完後的 actionable action 有什麼？
- 需要自己依照健檢結果，接續門診追蹤（為什麼要自己另外約）
- 健康飲食
- 運動（with real incentives. ex. discounts, gym membership）

使用者下一次健檢前可以收到提醒與通知
- 規則化項目
    - 例如政府有公告的特定年齡，可受補貼選入的健檢項目；大腸相關健檢，每三年；子宮頸抹片健檢項目
        - 參考病後人生，https://afterthatday.blogspot.com/
    - 如何實作
        - 使用者留下 email？

使用者在自己的健檢結果，撰寫註解、筆記
- 情境舉例
    - 子女註記長輩的健檢項目與生活狀況，例如大腸鏡有區分長度，若並未採用足夠的長度，就無法完整檢查大腸，因而並不是聽起來那麼完整，所以縱是長輩說「我也有照過大腸鏡了」，也需要了解該次大腸鏡的規格
- 如何實作


## 蒐集 Rule Base，給相關年齡者的推薦注意事項與建議

* 家醫科
    * 對於家醫科來說，為了讓看診的民眾了解該做哪些健檢項目，應該有一套問答的流程與歸納
* 乳癌
    * 抽血，其中一個項目可以透過數值？
    * 年齡因素？
        * 超音波、X光
        * CT
* 健保補助健檢項目：
    *https://www.hpa.gov.tw/Pages/List.aspx?nodeid=189
* 健保資料庫開放資料可做研究整理台灣各區域各年齡性別好發疾病(需IRB及申請)
    * 找看看是否有研究成果，已公開的內容
        * Pages 30-36: https://www.cdc.gov.tw/Uploads/files/80b59ada-1010-4fc4-9b2c-d88aabb152e8.pdf
* 針對年長者族群，老人照護預防策略重點(下方紅字指出要注意的事項)
    - 老人隨年紀衰弱過程中如何事先預防/延緩進一步衰弱照護重點，「三段五級預防策略」
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0442c55bcce862f4887d7feb8332b2ba.png)
    - 雖然不一定對應到明確健檢項目，但與主要族群會關心的生活注意事項相關，也涵蓋生活輔具使用注意提醒
    - 相關聯的健檢項目：骨質流失、骨質疏鬆、骨質密度、肌肉流失狀況
    - 相關生活調整：輔具使用、飲食調整、長照資源資訊地圖（https://ltcpap.mohw.gov.tw/public/index.html）

其他
* 23andMe　基於唾液的個人基因組檢測
* Clinicas del Azucar
* [生活因子與慢性疾病關聯示意圖](https://g0v.hackmd.io/SiKrp6uVRe2oEimB0KpDCg)，但屬於學術研究示意圖，不是很好理解，也還需要翻譯、轉譯

## 使用者的困境

沒有健檢的動機
* 迷思：門診與健檢，兩者功用混淆
* 我是不是用掛號門診，就可以開啟檢查？不是的！
* 門診醫生開檢查，是為了診斷某些疾病，也會更有類型導向，而不是如健康檢查較為全面
* 診間發生只會針對不舒服的部分，不會安排全身健康檢查，例如病人因為胃痛來看診，針對胃潰瘍來進行診療，但就不會另外檢查其他項目（例如大腸癌）；這部分也會有所謂的「假性安全感」，因為針對特定病症有進行改善，但不代表全身健康程度。
* 慢性病，高齡者，其實也建議進行健康檢查
    * 有慢性病，但身體保持一定的健康程度，也會建議健檢
    * 70 歲女性，有抽煙，有糖尿病，也需要健康檢查


不理解這些健檢項目實際的內容
* 不知道到底買了什麼健檢項目
* 為什麼要這麼多錢（飛機上的wifi vs 雞蛋/牛奶）
* 現在的健檢中心提供的packages複雜又不知道哪個划算
    * HTC vs Apple）
        * HTC 較混亂的規格名稱
        * Apple 有明確的 Pro 規格、每一個版本等
    * Iedal: personalization, within my budget, 推薦理由 
* 定價策略（套餐 vs 單點）
    * 某些單點項目（ex. 抽血）可以在小診所做，不一定要去健檢中心 > 省時省力省錢
    * 補充：醫院同仁提醒, 各大醫院健檢都是套餐收費, 要求套餐外自行指定項目一般費用不便宜.. 對於使用者來說，了解自己較需要的健檢項目，但不一定會在套餐內
* 產品資訊整合服務，參考案例：
    * 汽車保險 Geico 
        * https://www.geico.com/
    * 人壽保險 FINFO
        * https://finfo.tw/
        * 新型專利: https://gpss2.tipo.gov.tw/gpssbkmusr/00029/TWBA-M544061.pdf


## 專案產品可能遇到的問題
* 法律責任（漏掉需要檢查的項目？）
    * 使用前，請使用者先同意相關條文
* 個資需謹慎處理
* 如何和各個角色有效配合
    * 角色：健檢中心、醫院、診所、病人、醫生
* 易讀性
    * 思考年長者族群，也可以很快了解自身需求
    * 轉化成一般民眾可以
    * 從「病症」
        * 甲狀腺超音波，可以看甲狀腺結節，但甲狀腺結節對於民眾可能不理解
        * 哪些檢查項目，可以提早發現 十大癌症 哪些癌症
* 健檢中心目前主推 package，可以選購需要的項目？（如果需要跑很多間診所、醫院做檢查太麻煩了）
* 可以放廣告，不過需要衡量讓廣告不影響使用者瀏覽網頁與評估
* 健檢中心的產品是否可以被抓到其他網頁上呈現
* 如果走公益方向, 如何募款及永續經營參考:
    * https://neticrm.tw/report/2020


## 發想

目前健檢流程途徑，已有「健康存摺」此環節有明確命名，扮演資料收攏
用「存摺」所屬的金融術語系統，來幫「本專案致力的功能環節」取名
特點：
- 折扣想像
    - 填問卷省更多
        - 健檢產品打折
        - 透過更精確的項目，減少醫事成本
    - 健檢 coupon
- 使用者知道自己更應該要健檢什麼項目
    - 更精確的支出項目
        - 已知平均每位國人要花費多少健檢支出
    - 健檢導航
        - 健檢項目不迷茫
        - 自費項目不迷茫
- 讓使用者知道自己的健檢成果，涵蓋多少 
    - 完整的健檢項目，你完成了哪些？
    - 健檢關卡，解鎖
    - 健檢組合
    - 10 萬方案的各種項目
        - 30 歲以前要完成的完整健檢項目
        - 攤提，五年一次
- 協助使用者填完重要的問卷
    - 每天了解一些，完成一份問卷
    - 每天一分鐘，一個星期完成健檢前的評估問卷，吸收 20 種健檢豆知識
    - 完成一份專屬於您的健康狀態評估
    - 與（角色名稱）一起完成健檢前的評估問卷
        - 案例：萬芳醫院-萬小芳 https://mymkc.com/article/content/23155
        - 案例：知己小姐 https://voiceforyou-nongchunxiang.com.tw/
- 使用者知道更多的健檢知識
    - 豆知識
    - 健康知識的小額投資
    - 儲存小額健檢知識
    - 健檢知識可以用一輩子，可以協助親友
    - 健檢小幫手
    - 健檢管家
- 陪伴概念, 做使用者的夥伴一起完成任務Clear
    - 檢伴
        - 關心的健康煩惱陪著你一起討論
        - 健康檢查好像很重要但沒有時間去了解
        - 檢伴陪伴你把健檢相關煩惱減半花費時間減半
        - 更多國民早期發現早期治療健保費支用減X?


## Pros and Cons

- LINE Robot
    - Pros: Easy to implement
    - Cons: Functional constraints; doesn't meet HIPPA requirements

- Passive collection of data
    - Pros: Users have full control of data sharing
    - Cons: Laziness; reluctancy; data leaking

- Smart Questionnaire
    - Pros: Flexible
    - Cons: Lacking of pre-organised question sets; didn't recruit large-scale EHR data in advance
        - NINDS might be a good reference
            - https://cde.nlm.nih.gov/cde/search?selectedOrg=NINDS
        - NHI data for AI modelling



## Good Apps

- WebMD
    - Knowledge base
    - Interactive robot
- ZOE Health Study
    - World-wide data collection
    - AI-based computation for association analysis


## Good projects

- Open Humans
    - https://www.openhumans.org/explore-share/






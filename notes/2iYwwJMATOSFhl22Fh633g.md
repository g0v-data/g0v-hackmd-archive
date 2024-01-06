---
image: https://i.imgur.com/8VtA0sr.jpg
tags: 紓困振興, vtaiwan,
---

# 2021 疫情紓困振興方案整理 💰

說明：本共筆係為對於2021年政府因應疫情而開啟的紓困方案整理。
貢獻者簽到區：peter, wade, Ronny, HY, Shirley, Tofus , chewei, did1335

# 工作區

## 6/26 大松徵人

資料蒐集
(1) 願意幫忙整理資料、會用或想學 [Airtable](https://airtable.com/shrlcP2TQBxLzSUdA) 的人
(2) 提供[「民間主辦的紓困措施資訊」與可接受捐款的網址資訊](https://airtable.com/shrlcP2TQBxLzSUdA/tblv38PrQpTY3cJaL/viw9LVbd5axB88E6t/rec2rDAZN9WCp8CmO?blocks=hide)
(3) Airtable 編輯權限申請、專案討論，歡迎至：slack channel #vtaiwan

爬資料
(4) 爬 [1988 中央專區](https://1988.taiwan.gov.tw/) 上面的資料

架網頁
(5) 歡迎 網頁前端架設 查找網頁 (目前的[模板成果](https://sheet2site.com/api/v3/index.php?key=1yhRyeTzmZgw05qN1jDqoMb11LFjDciYyKQ_BQgLx6OM))

## 專案定位討論

1. 基於中央政府的 1988 紓困措施專區並無提供 api 或可介接的的資料管道，經評估透過志工手動搬運，仍會有疏漏，這部分有點尷尬，==是否要搬？如何檢查都搬了？==
2. 縣市政府，由於幾乎都沒有提供引導式標籤，且部分縣市並未成立專區網頁，所以專案志工採用 **hackmd** 方式，將該縣市可被搜尋的措施資訊彙整集中
3. 針對**各大學學生紓困措施**，專案志工進一步整理出各大學的網址讓學生參考
4. 持續彙整**民間提供紓困措施資訊**，例如公關協會、新巨輪協會等，並採用對象標籤方式彙整讓使用者查找
5. 持續彙整**民間接受捐款的資訊**，標籤「我想要捐款支持」
6. 討論請至 g0v slack #vtaiwan
:::spoiler ------------------點開看 架構評估圖----------------------
<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vT17jjm9q8S4FYGb9o-6rvrebBDFrEXAt5usqupJG6oj62NzmmZZsbvArp3wtwXVZ-4dZRICQOTT6Bn/embed?start=false&loop=false&delayms=3000" frameborder="0" width="100%" height="431" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>

- [架構圖編輯網址](https://docs.google.com/presentation/d/1WAU2Z_6l1phZZk8z1ncI8lV8JPT8msNlAgw45_WoDvo/edit)
:::

## Airtable 整理資料

- 可瀏覽網址：https://airtable.com/shrlcP2TQBxLzSUdA
- [可編輯網址](https://airtable.com/invite/l?inviteId=invsNAGjxLWc9bHjk&inviteToken=e07954409e06b4deea6e772cdd381c4e9bc05053701e6eac47c2c41f25d0263c&utm_source=email )

### TODO 標記內容
- (1)「中央部會」
    - hackmd 有，但還沒登載到 airtable，還有嗎？
    - 要巡 1988 專區，找出 airtable 還沒有的
        - 例如：財政部
        - ==評估是否要爬 1988 上面的資料==
- (2) 依照「縣市政府紓困內容」，標註相關的對象： 
    - [done] 22 個縣市措施目前已先在 airtable 上面建立資料列，網址導到 hackmd 縣市段落
    - [todo] 縣市拆分，已完成：基隆市、南投縣、臺中市、宜蘭縣
    - [todo] 若不拆分，則依照各縣市的措施內容，在 airtable 標註 紓困對象，如：新北市(若有餘力要拆分也是 ok 的)
- (3) [持續蒐集] 民間單位的紓困措施
- (4) [持續蒐集] 捐款企劃
- (5) [done] 各大專院校網址，已登載 by Shirley

:::spoiler ------------------點開看 資料登載方法--------------------
(1) 依照共筆架構，將資訊分別填入對應的欄位
- 把文字貼到 Airtable 儲存格的時候，請注意下方的儲存格的內容是不是也被覆蓋掉
- 若擔心有覆蓋而未能察覺，建議可以把單列資料，點擊展開後，進行編輯，不會影響到其他列

(2) 「對象標籤」的設定原則
- 在對象標籤的用詞上，會需要思考一下使用者會怎麼搜尋，盡可能以最直覺的身份別來標定（例如學生、農民）
- 如果有條件限制，則補在「對象資格條件附加說明」的欄位即可，舉例：
    - 對象：國中生
    - 對象資格條件附加說明：國高中生且同時具有身障者身份

(3) 措施拆分原則，正面列舉：
- 同一個單位的「紓困」、「貸款」，拆開成兩筆資料
- 從查找者的角度，行業或職業身份，若適合拆分，例如農委會的紓困政策可拆分成「農業」、「漁業」
:::

### 定期檢查回報內容、sns 
- sns FB：https://www.facebook.com/g0v.tw/posts/5750038601704045
- sns twitter：https://twitter.com/g0vtw/status/1406964211608035333
- FB group: https://www.facebook.com/groups/g0v.general/permalink/4008931615849881/
    - 留言中的 教育部體育署運動產業紓困已登載至 airtable
- 資訊回報表單連結：https://forms.gle/z5Ci9zPKnz4mXoHs6 
    - [表單回答結果](https://docs.google.com/spreadsheets/d/1rKkAXoy_QfZ3suz87wRyht5ujkyf0DaCBip09SJXBjY/edit)
    - 20210702 chewei 檢查：無新增內容
- 意見回饋表單連結：https://forms.gle/JghQyWL4UKazBoig6
    - 評估先不放，放 FB 社團貼文網址、slack 頻道等加入討論區的網址


### 網頁維護

- 前台網頁：http://bit.ly/relief-money
    - [網址](https://sheet2site.com/api/v3/index.php?key=1yhRyeTzmZgw05qN1jDqoMb11LFjDciYyKQ_BQgLx6OM)
    - [網頁的後台 sheet](https://docs.google.com/spreadsheets/d/1yhRyeTzmZgw05qN1jDqoMb11LFjDciYyKQ_BQgLx6OM/edit#)
    - [圖卡工作簡報](https://docs.google.com/presentation/d/1X8lMGjvPr6JJ-NKHcZ0vBAYO-ArGstaiXLTzyg6SiOc/edit)
- 網頁上的資料呈現順序，chewei 會在 airtable 的順序欄位 key 好
    - 1988專區：順序1
    - 年齡：順序2-1 , 順序2-2 ...
    - 職業：順序3
    - 大學：順序4
    - 新增，則預設為：順序5
    - 縣市：順序501基隆 , 順序501-1 , 順序502 ... 順序522
- TODO：標籤能否固定順序？


## 紓困措施的開放資料架構與發佈流通課題

Issue 問題特性描述
- 資料歷程
    - 1
    - 2
    - 純線上可完成申請
    - 1
    - 電話專線的前提、申請習慣仍有電話聯繫的環節
    - 1
    - 填入與帶入資料
    - 1
- 協助客服
    - 讓客服知道公部門各部門措施
    - 讓客服知道民間各單位措施
- 協助申請者
    - 直接打電話

哪些議題、事項、政策推動，有類似的問題？
- 123


:::spoiler 點開看 0531-0611 討論歷程

#### [done] 0611討論過程
架設網站：google spreadsheet 
欄位：部會名稱
sheet2site？有標籤的google spreadsheet 
歸納一下查找的標籤

目標：如何讓不同族群的人能夠查找？
用「對象」來作為標籤

第一步要怎麼做？
名稱 ｜主辦機關 ｜網址 ｜敘述｜資格
先整合在一個sheet裏面
主辦機關

sheet 權限可以開編輯的

#### 0607進度更新
1. 更新了地區政府的相關資訊
2. 與chewei敲定會議時間

#### 0531 進度更新
1. 新增中央部會農委會、勞動部、交通部等
2. 將地方政府紓困振興方案相關網站連結放上
3. 補上立法院相關預算案資料
:::

# 紓困方案政策資訊
![](https://i.imgur.com/8VtA0sr.jpg)
![](https://i.imgur.com/MNM692d.jpg)

[20210603行政院會後記者會 紓困4.0全場](https://youtu.be/T19C0Sey3ro?t=460)
|時間軸|內容|簡報檔|
|--|--|--|
|[24:14](https://youtu.be/T19C0Sey3ro?t=24m14s)| 4.0方案簡報| https://reurl.cc/eEE8jK
|[34:06](https://youtu.be/T19C0Sey3ro?t=34m06s)| 衛福部|https://reurl.cc/6ay1bO
|[39:04](https://youtu.be/T19C0Sey3ro?t=39m4s)| 勞動部|https://reurl.cc/rga75b
|[45:37](https://youtu.be/T19C0Sey3ro?t=45m37s)| 農委會|https://reurl.cc/En291n
|[49:24](https://youtu.be/T19C0Sey3ro?t=49m24s)| 教育部|https://reurl.cc/En2xRm
|[56:44](https://youtu.be/T19C0Sey3ro?t=56m44s)| 經濟部|https://reurl.cc/9rZl6X
|[1:01:04](https://youtu.be/T19C0Sey3ro?t=1h1m4s)|交通部|https://reurl.cc/6ay1lk
|[1:04:47](https://youtu.be/T19C0Sey3ro?t=1h4m47s)|文化部|https://reurl.cc/0jDA2A
|[1:09:30](https://youtu.be/T19C0Sey3ro?t=1h9m30s)|財政部|https://reurl.cc/pgml1b
|[1:33:47](https://youtu.be/T19C0Sey3ro?t=1h33m47s)|QA打工族|

Source: [中央社5/28報導](https://www.cna.com.tw/news/firstnews/202105285011.aspx)（5/30 12:28 更新）

## 中央部會

### 行政院
    1. 家庭防疫津貼：家有國小以下孩童，或國、高中特教學生，發放一次性定額現金，每人補助新台幣1萬元，約250萬人受惠，預計6月15日起發放，三級管制期結束前出生的新生兒都可領取。
[預計發放方式](https://udn.com/news/story/120974/5497752)
   
    2. 個人補貼：
        -中低收入戶
        每月加發生活補助金1500元，3個月共4500元

        -無相關社會保險者
        可申請急難救助金1至3萬元

        -農漁民
        可申請1萬元，甲級漁工3萬元

        -自營工作者（指獨立從事勞動或技藝工作獲致報酬，且未僱用有酬人員幫同工作者）
        每月1萬元補助金，3個月共3萬元

        -觀光業從業人員
        導遊、領隊及國旅領團人員、計程車、遊覽車司機，3個月共3萬元補助金

    3. 申請方式：尚未公佈，去年已申請請領者毋須申請，將直接入帳。補貼撥付流程朝向「不必到職業工會申請」規劃，符合條件勞工可直接透過網路登錄核發。

[1988紓困振興專區](https://1988.taiwan.gov.tw )

#### 教育部

https://www.edu.tw/COVID-19


#### 文化部 
5/17公告
針對5/11-6/8第二級警戒所生損失之事業補助
[補助申請須知](https://mocfile.moc.gov.tw/files/202105/b15a92f2-816e-4583-a8c1-90daa0a69140.pdf)
本須知是針對營運損失之事業補助，只要是在我國設立登記或立案之 *法人*、*非法人團體*或*負責人具我國國籍之商號*(如*個人工作室*等)，並且具 備下列條件:
一、 必須是經營或從事表演藝術展演、流行音樂演出、電影國片商業 映演事務或前述相關事務者。
二、 因 110 年 5 月 11 日中央流行疫情指揮中心宣布提升疫情警戒至 第二級，致使營運受到衝擊者。

後續的補助目前尚在研擬中。
[紓困3.0](https://www.moc.gov.tw/information_250_129659.html)

#### 農委會
5/11公告
[5/11生效之紓困措施](https://www.coa.gov.tw/COVID_19/index.php?theme=publication&id=4510)

[農民生活補貼作業規範](https://www.coa.gov.tw/COVID_19/index.php?theme=ws&id=2510958)

#### 原住民族委員會
[原住民族委員會因應嚴重特殊傳染性肺炎振興措施行動支付回饋](https://www.cip.gov.tw/portal/getfile?source=2D838540F5D6F659FAFB9859EF31AC3B381A272F479D65D98D902DFAAFC2E154373B86F62596D6AFF9853DCA7700200FE27ABC5E6CBC12A63B91B9DF71659F0C&filename=294DA3263340917113A77C2C393E97BF51A6AFE36888516D0A4F693AA45DCB6749EDD438147D39BBA852238F00A7C162)

#### 經濟部
[1988紓困4.0](https://www.moea.gov.tw/MNS/covid-19/home/Home.aspx)

6/3上線，目前正在研擬相關措施

#### 金管會
預計各銀行的個人／企業貸款及信用卡費的優利緩繳措施（申請至6/30）會延續，近期會公告。

#### 勞動部

[紓困措施](https://www.wda.gov.tw/cp.aspx?n=BE047C8B0FA72893w)
[勞、就保保險費及勞工退休金緩繳協助措施](https://www.mol.gov.tw/announcement/2099/48500/)
[勞保局e化服務系統](https://www.edesk.1955.gov.tw)
[部分工時勞工生活補助](https://pt.10000.gov.tw/)

#### 交通部

[交通觀光紓困措施](https://event.motc.gov.tw/index.jsp?webid=202002100001)

#### 衛福部

[照顧服務紓困措施](https://covid19.mohw.gov.tw/ch/cp-4755-52904-205.html)
[衛生福利部紓困4.0 五大措施](https://www.mohw.gov.tw/cp-16-61223-1.html)
[紓困五大措施.pdf](https://www.mohw.gov.tw/dl-69466-51f31b35-8e69-4027-8caa-32967e090266.html)
[☎️ 衛福部 1957 專線，社會福利電話諮詢專線](https://1957.mohw.gov.tw/)
- 衛福部從 2010 年開始設立了 #1957 專線 ，希望能幫助生活遇到困境的人可以得到所需的資源。衛福部設置的社會福利電話諮詢專線（目前為家扶基金會承辦）， 提供全國民眾各項社會福利諮詢服務，包含急難救助、社會救助、老人福利、身心障礙福利、兒少福利、國民年金保險等資訊。民眾若有相關社會福利資訊等相關需求服務， 歡迎民眾多加運用。 
    - 電話直撥 1957，即可接通專人服務： 
    - ✔️ 服務對象：全國民眾 
    - ✔️ 服務時間：每日早上 8 點至晚上 10 點；週一至週日，假日照常服務 
    - ✔️ 使用方式：市話、公共電話、月租型手機、五大電信之預付卡手機，直撥1957皆免費。
    - ✔️ 其他服務方式： 
        - 1957官網：https://1957.mohw.gov.tw/
        - （提供線上會談）
        - 1957 LINE@：@1957mohw


## 地方政府

### 基隆市
1. 設立中小企業紓困單一窗口專線電話02-2422-4897，協助工商企業貸款、基隆市政府及中央相關紓困資訊諮詢及轉介服務。
2. 規劃1億元中小企業防疫喘息貸款（110年6月至12月）。
3. 提供100萬元青創融資及5年利息補貼。

[基隆市防疫住宿補貼計畫](https://www.klcg.gov.tw/tw/News/Detail2?NewsId=155100C5&i=2)
[基隆市紓困計畫](https://www.klcg.gov.tw/Images/eoc/基隆市政府紓困措施.pdf)

### 臺北市
1. 失業給付線上即時申辦。
2. 失業勞工子女就學費用補助，高中職最高1萬2000元，大專、大學最高2萬6000元。
3. 住安心檢疫所、防疫旅館補貼最高14日7000元。
4. 加強版防疫專責旅館從業人員體恤補貼最高14日2萬8000元。
5. 市⺠急難救助⾦，單⾝補助3000元，弱勢家庭補助6000元。
6. 企業貸款本⾦與利息遞延繳付，最⻑展延6個月。
7. 藝文專案補助計畫，最高30萬元。[文化局公告](https://culture.gov.taipei/News_Content.aspx?n=63F36AA6E434AD08&sms=78D644F2755ACCAA&s=D4C2623B8DE64D00)

[臺北市短期紓困措施](https://www-ws.gov.taipei/001/Upload/304/relfile/0/104114/3b2bb8df-f63c-4332-bbfd-0ff1bcb9b42d.pdf)

### 新北市
>[新北市110年防疫助扶方案](https://www.ntpc.gov.tw/ch/home.jsp?id=476f8c4752b7e74c)

1. 急難慰助
    1. 家庭總收入平均每人每月低於3萬9000元
    2. 全家人口包含存款、有價證券、汽車及投資等，每人每年未超過20萬元者
    - **符合上述這2條件，即可提出申請1萬元。**
    - 消息來源-新北市政府衛生局：[新北市推出急難慰助採用線上申請 因受疫情影響致生活困難者每戶1萬元 申請期間生活有急迫里鄰長贈民生物資 服務專線0800-292929（要救要救要救）](https://www.sw.ntpc.gov.tw/home.jsp?id=6918f79d690935a2&act=be4f48068b2b0031&dataserno=aa719d90c1bb0b40b89bdb039eefe288&mserno=f2d603f5908a2f57a5d1cee327060ddc)
2. 關懷救助
－按陷困各戶所需，發送民生物資。
3. 青年見習
－招募300名設籍新北市就學大專院校在學生或應屆畢業生，參與7-8月市政創新規劃。
4. 勞工協助
－提供律師費、裁判費、生活費等勞資爭議訴訟補助。
－失業勞工除子女就學費用補助，加給生活扶助金最高1萬1800元。
5. 社宅租金
－申請前4個月每月租金緩繳50%，第5個月起分12期無息攤還。
6. 稅金減收
－停業期間，減徵房屋稅及停徵牌照稅；稅款分期可展延1年或分36期。
7. 娛樂等地方稅減免
－查定課徵的娛樂稅業者，減徵5月15日至8月31日查定稅額的30%。
－飯店、旅館及其他營利事業已停用或縮小營業面積者，及配合政府防疫政策停業的場所，其房屋稅率由原3%降為2%。
－配合政府防疫政策停業的業者，停業期間停徵娛樂稅。
8. 藝文支持
－場館費用全額退費，快速核發補助款。
9.租金、權利金減收（減免期間為110年5月15日至8月31日）
－促參廠商及設定地上權業者的營運權利金，最高減免35%。
－市有不動產出租作營業使用者，租金減收50%。
－公有市場攤商使用費減收50%。
－租金、使用補償金、權利金、市場使用費等規費與各項罰緩，繳納期限一律展延3個月。
10. 罰單緩繳
－應到案日自5月15日起至6月14日止，且應到案處所為新北市交通裁決處的罰單，無須檢附任何文件，繳納期限可展延至7月14日。
11. 建期展延
－公共工程工期可申請延展；民間工程工期延長2年。
12. 交通紓困
－公車業者補助先撥付8成；新北市交通局委外管理之停車場，按同期減收比例各自分攤一半原則減收；碼頭減半收取使用費。
13. 農漁產銷售與漁民紓困
－輔導農會、漁民推出美味農業得來速。
－補助漁民、漁會宅配運費電商上架費。
新北市政府官網防疫專區設置「新北市110年防疫助扶方案」，專線電話02-2960-3456分機5298。



### 桃園市
> [桃園紓困10帖](https://www.tycg.gov.tw/ch/home.jsp?id=10553&parentpath=0,10405)


1. 中小企業融資紓困諮詢、企業融資診斷服務及政府相關資源轉介等服務，免付費專線0800-505-158。
2. 市有場館規費及權利金減免，包含桃科園區管理費、旅遊遊憩景點委外空間權利金、體育場館委外空間權利金、市有不動產房地租金、公有停車場站委外租金權利金等。
3. 失業勞工子女助學補助計畫、關廠歇業或重大勞資爭議案件勞工生活補助金及急難紓困措施。
4. 受疫情影響導致工作減班休息之民眾，公部門提供臨時打工工作機會。
5. 旅行業、旅宿業及觀光遊樂業融資周轉貸款協助及利息補貼、桃園市防疫計程車補貼、桃園市客運業者防疫物資補貼、桃園捷運定期票及回數票優惠退票方案。
6. 「肺炎疫情稅捐申辦專區」提供紓困減稅，並可展期、延期或分期繳稅。
7. 減收今年5至6月公有市場使用費。
8. 青創貸款還款展延、桃園市青年創業及中小企業信用保證融資貸款還款展延。
9. 協助桃園市農漁業行銷度難關。

### 新竹縣
>[新竹縣紓困方案](https://www.hsinchu.gov.tw/News_Content.aspx?n=153&s=234996)
> 直接google會找到2020年的舊方案

1. 圓夢紓困貸款:對象為設籍新竹縣4個月以上，年齡介於20-65歲、在縣內經營事業，若屬小規模商業(免辦商業登記，僅設稅籍登記)最高可貸100萬元，設有公司或商業登記之中小企業最高可貸200萬元，資金用途以提供其購置或租用營業所需之廠房、營業場所、機器、設備、裝潢以及營運週轉金使用。

2. 減稅：因應疫情被強制關閉的休閒娛樂場所(域)，主動停徵車輛停止使用期間之使用牌照稅及適用查定課徵娛樂業停止營業期間之娛樂稅。另外，休閒娛樂場所、觀展觀賽場所、教育學習場域等，在停止營業期間其使用房屋之房屋稅調降。而接受隔離治療、居家隔離、居家檢疫、集中隔離或集中檢疫，110年開徵之房屋稅准予展延，假始繳納困難，也可申請分期延期繳納。

3. 文化局紓困方案：為協助縣內表演團隊度過疫情難關，成立各項演出及補助單一窗口（表演藝術科03-5510201*302呂小姐），提供更便捷服務。因疫情影響於演出前7日函請調整檔期或取消演出者，場地租金全數退回。

4. 充電再出發職訓津貼（參訓勞工每月最高可領到1萬9,200元的訓練津貼）、失業勞工的安心即時上工計畫（每月最高12800元，最高補助6個月）及薪資補貼。申請辦法如附檔。

5. 期間限定-在地有機蔬菜箱：農業處在疫情期間，強化地產地消行銷通路、鼓勵在地消費，協助新竹縣農會整合在地有機蔬菜農戶，推出「期間限定-在地有機蔬菜箱」進行促銷，

### 新竹市
1. 推出總金額3億元「防疫安心貸」紓困貸款，鬆綁貸款資格，商號最高可貸款50萬元，公司最高1000萬元，利率2.17%，貸款期間最長7年。
2. 因防疫措施受影響行業調降適用房屋稅率，如飯店及旅館業、電影院。受影響期間，由營業用稅率3%改按「非住家非營業用」稅率2%課徵；樹林頭夜市，將依契約規定免收租金及權利金。
3. 受疫情影響公有市場與市府公有場館，仍有營業者租金或權利金減半、暫停營業者免收租金或權利金。
4. 受影響勞工：
－非自願離職者即可領取失業給付，按平均月投保薪資60%發給。
－失業勞工可申請子女就學補貼高中職至少4000元、大專院校至少1萬3600元。
－勞工若因疫情影響造成「減班休息」（無薪假），可申領勞工投保薪資與實領薪水差額一半的補助。
－勞工在減班時段（無薪假）參加訓練課程，可申請訓練津貼補助，每小時比照基本工資160元發給，每月最高120小時，總計1萬9200元。
5. 全市建築工程工期自動延長1年，業者無須申請。

[稅捐紓困專區](https://www.hcct.gov.tw/ch/home.jsp?id=468&parentpath=0,6)
[漁會漁業補助](https://www.hccg.gov.tw/ch/home.jsp?id=48&parentpath=0,16&mcustomize=municipalnews_view.jsp&t=MunicipalNews&dataserno=202005090001&mserno=201601300307&toolsflag=Y)

### 苗栗縣
[紓困振興專區](https://www.miaoli.gov.tw/cl.aspx?n=6538)
> 裏面的資料多為去年的資料，尚未更新。

1. 工商紓困關懷專線559880。
2. 傳統市場租金減免。
3. 地方產業創新研發計畫（SBIR）加碼補助10%。
4. 建築執照展延2年。
5. 中小企業貸款舊貸展延、營運貸款、振興貸款申請延至110年6月30日止。
6. 中小企業信用保證融資貸款還款展延。
7. 安心就業計畫、安心即時上工計畫、充電再出發訓練計畫。
8. 七大稅務紓困：例如因疫情短期不用之車輛，向監理機關辦理停駛後，按日停徵使用牌照稅；因疫情停業的十大類場所可以減徵房屋稅及娛樂稅；因疫情接受隔離、治療、檢疫者，110年房屋稅可延期、分期繳納等。

### 臺中市
> [臺中市政府 Covid-19 紓困10方](https://www.economic.taichung.gov.tw/1793685/post)

1. 夜市或市集配合停業期間租金免收
2. 市場及夜市6-9月使用費減半
3. 成立資金紓困單一窗口，提供貸款協助
4. 溫泉使用費分期繳納
5. BOT、OT及相關委外場館權利金及租金減免或延繳
6. 承租財政局經管市有非公用不動產租金減收
7. 勞工相關
    - 非自願失業勞工生活補助及子女就學補助擴大辦理
    - 青年創業貸款利息補貼延長一年
    - 安心即時上工
9. 稅捐緩繳：接受治療、隔離或檢疫者，房屋稅延至6月底；受疫情影響繳納困難者，最長延期1年，最多可分36期
9. 稅捐減免：房屋稅、娛樂稅及牌照稅輔導減免；強制停業主動減房屋稅、娛樂稅
10. 表演藝術紓困補助

### 彰化縣
[紓困振興](https://www2.chcg.gov.tw/main/main_act/main.asp?main_id=35992&act_id=420)
1. 幸福圓夢貸款一年免息。
2. 社福救助單一窗口1957。
3. 安心就業與訓練補助。
4. 稅捐減免緩繳。
5. 藝文紓困補助。
6. 建築在建工程施工期限展延。
7. 縣府委外場館規費減緩繳。
8. 縣內26處公有零售市場6到9月攤位租金減半。

### 南投縣
1. 縣府地租減收2成。
2. 青創貸款利息補貼。
3. 建雜照延長建築期限1年。
4. 房屋稅主動調降稅率。
5. 牌照稅車輛停用免徵。
6. 娛樂稅申請核減稅額。
7. 繳稅困難可延／分期。
8. 展演活動藝文紓困。

[勞工紓困](https://www.nantou.gov.tw/covid19/index.asp)

[觀光紓困](https://www.nantou.gov.tw/covid19/page.asp?cid=2679)

[企業紓困](https://www.nantou.gov.tw/covid19/page.asp?cid=2680)

[農林漁牧](https://www.nantou.gov.tw/covid19/page.asp?cid=2678)
> 裡面是去年的資料

[租稅紓困](https://www.nantou.gov.tw/covid19/page.asp?cid=2681)


### 雲林縣
1. 文藝表演紓困補助，縣府加碼補助5000元。
2. 租稅緩繳及減免，可申請延期或分期繳納。
3. 合法夜市及傳統市場租金減免。
4. 促參案及縣有出租場館租金減緩繳。
5. 雲林縣政府企業紓困諮詢單一窗口電話（05）5522169。
6. 110年建雜照自動延長建築期限1年。

[雲林紓困2.0](https://www.yunlin.gov.tw/News_Photo_Content.aspx?n=12634&sms=17417&s=338564)

[藝文表演紓困補助](https://www.yunlin.gov.tw/News_Photo_Content.aspx?n=12634&sms=17417&s=338515#lg=1&slide=0)
> 部分與文化部紓困計畫重疊

### 嘉義市

> [嘉義市 紓困專區入口](https://www.chiayi.gov.tw/cp.aspx?n=4365)
- [一般民眾因應新冠肺炎社政、勞政單位紓困方案懶人包
](https://icmp-ws.chiayi.gov.tw/Download.ashx?u=LzAwMS9VcGxvYWQvMzk5L3JlbGZpbGUvMTIxMTAvNDI0NTg2L2NjZDU1Y2QzLTBhNzgtNDllZC04NGQ0LTgxYzFiOGYyMjM3MC5wZGY%3d&n=MTEwMDUyNOWboOaHieaWsOWGoOiCuueCjuekvuaUv%2bOAgeWLnuaUv%2bWWruS9jee0k%2bWbsOaWueahiOaHtuS6uuWMhS5wZGY%3d)
- [中小企業紓困貸款](https://www.chiayi.gov.tw/News.aspx?n=4308&sms=12110&_CSN=1742)
- [中小企業稅務減免、延期、分期](https://www.chiayi.gov.tw/News.aspx?n=4308&sms=12110&_CSN=1748)
- [農牧業紓困及振興措施](https://www.chiayi.gov.tw/News.aspx?n=4308&sms=12110&_CSN=1747)
- [藝術文化紓困方案](https://www.chiayi.gov.tw/News.aspx?n=4308&sms=12110&_CSN=1740)



### 嘉義縣
[紓困與振興專區](https://www.cyhg.gov.tw/bir/)

1. [農漁業行銷及紓困補助](https://www.cyhg.gov.tw/bir/News.aspx?n=85120D51EE64E025)
3. [租稅緩徵與減免](https://www.cyhg.gov.tw/bir/News.aspx?n=EC52B040AE716643)
5. [藝文表演紓困補助](https://www.cyhg.gov.tw/bir/News.aspx?n=7AB43476636EC0ED)
6. 促參案及縣有場館租金減緩繳。
7. 減收產業園區公共設施維護費。
8. 青創貸款本金緩繳。
9. 110年建雜照延長建築期限1年。
10. [原住民紓困](https://www.cyhg.gov.tw/bir/News.aspx?n=6133A524600A38E5)
11. [安心即時上工計畫](https://www.cyhg.gov.tw/bir/News.aspx?n=C0F9749AD5F00EC2)
12. [醫療產業](https://www.cyhg.gov.tw/bir/News.aspx?n=5BCEFD9636EDFFE4)
13. [交通觀光](https://www.cyhg.gov.tw/bir/News.aspx?n=7F51C13E02054BD3)


### 臺南市
> [本府紓困振興方案](https://www.tainan.gov.tw/News.aspx?n=28581)


1. 農業局：振興、補貼、貸款
![農業局：振興、補貼、貸款](https://w3fs.tainan.gov.tw/Download.ashx?u=LzAwMS9VcGxvYWQvMS9ja2ZpbGUvOTg1ZDY3MDYtNTRiZS00YWI5LThiNDctNWEyODBhNWExOWM1LmpwZw%3d%3d&n=bWVzc2FnZUltYWdlXzE2MjI0Mjg3MTk2ODguanBn&icon=.jpg)
2. [財政稅務局：延期、展期、減稅、減租](https://www.tntb.gov.tw/_document/files/artsinfo/1622430729-m0.pdf)
3. [觀光旅遊局](https://www.twtainan.net/zh-tw/event/newsdetail/4445)
    - 方案一「旅宿業因應防疫整備補助計畫」
    - 方案二「台南好給力-觀光產業紓困貸款利息補貼」
    - 貼心方案「感心安心住-獨居長者等候新冠肺炎疫情篩檢期間入住防疫旅館補助計畫」
4. [文化局](https://culture.tainan.gov.tw/latestevent/index?Parser=9,3,248)
    - 藝術編創補助
    - 線上影片製作補助
    - 線上策展補助
5. [勞工局 紓困振興方案](https://web.tainan.gov.tw/labor/cp.aspx?n=23877)
    - 安心即時上工計畫：本府為使受疫情影響勞工朋友有增加收入之機會，每個月最多工作時數80個小時，每小時160元，每月最高補助12,800元，計畫執行期間，每人最長補助6個月(進用人員參與本計畫最長期間6個月)，110年執行期間延長後，原預計上工至110年6月30日止之進用人員，可順延至參與本計畫滿6個月止
    - 安心就業計畫：勞動部為因應嚴重特殊傳染性肺炎（COVI D-19）對國內就業市場之影響，於勞雇雙方協商同意暫時縮減工作時間及減少工資期間（以下簡稱減班休息），運用薪資差額補貼措施，以穩定就業，特訂定本計畫。
    - 已開放20歲以上勞工申請最高10萬元之 #紓困貸款。相關申請細節請見[網頁](https://www.tainan.gov.tw/News.aspx?n=28581)
6. [經濟發展局](https://economic.tainan.gov.tw/cl.aspx?n=23768)
    - [經濟部紓困方案-瓦斯紓困振興方案](https://economic.tainan.gov.tw/News_Content.aspx?n=23824&s=7768628)
    - [受肺炎影響發生營運困難事業資金紓困振興貸款](https://economic.tainan.gov.tw/News_Content.aspx?n=23830&s=7658024)
    - [小規模營業人簡易申貸方案](https://economic.tainan.gov.tw/News_Content.aspx?n=23872&s=7768627)
7. 社會局
![社會局](https://w3fs.tainan.gov.tw/Download.ashx?u=LzAwMS9VcGxvYWQvMS9ja2ZpbGUvYWJjYjgwZjItYzAyMi00NzhjLWI3NjUtOGJkNWM2ZTZlNjRkLmpwZw%3d%3d&n=ZjVmNDkxODEtOTlhNy00OTBkLWExNmMtMTZiYjQ2MDFlNjI2LmpwZw%3d%3d&icon=.jpg)


### 高雄市

[紓困專案](https://www.kcg.gov.tw/2019nCoV/cp.aspx?n=14B668C288C3F3D5)
紓困專線07-822-0300。

1. [齊心防疫2.0專案貸款](https://www.kcg.gov.tw/2019nCoV/cp.aspx?n=4A52ECFB7BED6622#2-1)
2. [觀光補助](https://www.kcg.gov.tw/2019nCoV/cp.aspx?n=ED8E36DA878A4076)
3. [社會紓困](https://www.kcg.gov.tw/2019nCoV/cp.aspx?n=E119EAAD8E1D1978)
4. [青創貸款還款展延及利息補貼](https://www.kcg.gov.tw/2019nCoV/cp.aspx?n=F8905958B4A7D17F)
5. [市有產業園區規費](https://www.kcg.gov.tw/2019nCoV/cp.aspx?n=E0E393934F280DD2#4)
6. [市有地租金減免](https://www.kcg.gov.tw/2019nCoV/cp.aspx?n=4A52ECFB7BED6622#5)
8. [公有市場攤商規費減半](https://www.kcg.gov.tw/2019nCoV/cp.aspx?n=E0E393934F280DD2#6)
9. [安心就業計畫](https://www.kcg.gov.tw/2019nCoV/cp.aspx?n=19DBEE09E10E6505#7)
10. [（線上）職訓津貼補助](https://www.kcg.gov.tw/2019nCoV/cp.aspx?n=19DBEE09E10E6505#8)
11. [勞工失業生活及其子女就學補助](https://www.kcg.gov.tw/2019nCoV/cp.aspx?n=19DBEE09E10E6505#9)
12. [稅捐緩繳減（免）](https://www.kcg.gov.tw/2019nCoV/cp.aspx?n=4A52ECFB7BED6622#10)
13. [市府場館規費減緩繳](https://www.kcg.gov.tw/2019nCoV/cp.aspx?n=E0E393934F280DD2#11-1)
14. [市府演藝場館規費](https://www.kcg.gov.tw/2019nCoV/cp.aspx?n=F7928C7656F2381C)
15. [農](https://www.kcg.gov.tw/2019nCoV/cp.aspx?n=7286A5BA435E5CA5)[漁](https://www.kcg.gov.tw/2019nCoV/cp.aspx?n=5F964210F716A547)業多元行銷及補助。

### 屏東縣
[懶人包](https://www.pthg.gov.tw/News_Content.aspx?n=528607F80E455D7F&s=13A5432069E8C0BF)
1. 居家隔離者入住防疫旅館補助，居家隔離民眾補助每日1000元，最高1萬4000元；入住防疫旅館每日加碼補助500元，最高7000元，最高共補助2萬1000元；入住安心旅館補助每戶最高5000元。
2. 防疫旅館補助，補貼清潔封房每房最高2500元，補助清潔人力每日1000元。
3. 藝文產業減收租金50%，表演團體補助、場地費用減免。
4. 公有市場租金免收3個月。
5. 稅捐減免緩繳。
6. 物資銀行物資包擴大發放對象。
7. 公有土地、場館租金減徵。
8. 安心就業薪資差額補貼。
9. 安心上工提供就業。
10. 充電再出發職訓補助。
11. 中小企業貸款還款展延、利息全額補貼。
12. 農業大學貸款展延、利息全額補貼。

### 宜蘭縣
[宜蘭縣政府紓困方案](https://www.e-land.gov.tw/cp.aspx?n=32074C1D315BAFA5&s=2C40F0BFE4F886E2)

1. 促參民間機構權利金減收、租金減半及延繳3個月
2. 縣有委外場館租金，政府公告停業期間免收，5-7月其餘期間減半及公告停館期間延長履約期限
3. 非營業用途公有土地或房屋租金使用補償金延繳3個月
4. 藝文事業營運損失補助
5. 安心即時上工提供就業機會
6. 安心就業薪資差額補貼
7. 失業勞工子女就學補助
8. 稅捐減免及延緩繳納
9. 縣府公共工程依疫情影響程度展延履約期程
10. 建造執照工期主動展延一年
11. 地政證照、公安、消安申報主動展期

### 花蓮縣
- 花蓮縣衛生局
    - [FB](https://www.facebook.com/hlgov/)
    - [Line](https://line.me/ti/p/%40qpd0523w)
    - [連絡電話](03-8227171)
    - [新冠狀肺炎專區](https://www.hlshb.gov.tw/News.aspx?n=8766&sms=14641)
- [110年紓困專區](https://csa.hl.gov.tw/hlcovid-19/cl.aspx?n=23652)
    1. 東大門夜市停業期間免收租金。
    2. 公有出租場館租金減收2成。
    3. 縣政府優惠獎勵防疫旅館補助。
    4. 109年領得建築執照及雜項執照自動展延兩年。
    5. 公有房地租金減（緩）繳。
    6. 稅捐緩繳減免。
    7. 勞工失業生活及子女就學補助。
    8. 充電再出發訓練計畫。
    9. 安心即時上工計畫。
    10. 急難紓困實施方案。
    11. 花蓮縣青年安心創業及中小企業貸款還款展延。
    12. 青創利息補貼延長至5年。
    13. 原民青創紓貸支付回饋。
    14. 部落景觀優化產業行銷。
    15. 配合中央紓困方案，無縫銜接紓困4.0加速從優。

### 臺東縣

- 專線：089-340681
- [相關報導1](https://udn.com/news/story/120974/5495733)
- [相關報導2](https://www.ettoday.net/news/20210531/1995579.htm)

1. 稅賦減免（適用期間：110年5、6月）
－110年5、6月娛樂稅減徵50%。
－休閒娛樂場所、旅館業停用樓層房屋稅減徵1/3。
－旅館或民宿房屋稅稅率由營業用（3%）調降為非營業用（2%)。
－房屋稅分期或延繳。
2. 租金減收（適用期間：110年5、6月）
－觀光夜市、正氣路固定鋪位、第三市場、縣有非公用不動產等租金減收20%。
－觀光夜市暫停營業期間免收租金。
3. 勞工減班或失業協助（適用期間：110年全年度）
－補貼減班勞工投保薪資差額50%。
－提供6個月職訓生活津貼。
－失業勞工子女就學補助。
4. 疫情期間行政罰鍰可延期或分期繳納。
5. 單一窗口協助縣民申請房貸、車貸等個人金融性產品緩繳或延期繳納。
6. 資金融通
－繁榮家園專案貸款利息補貼展延1年（規劃中）。
－繁榮家園貸款專案額度增加1倍。
－貸款零利率補貼計畫。

### 澎湖縣
[澎湖縣社會處紓困專區，項目可能會持續更新](https://www.penghu.gov.tw/society/home.jsp?id=352)
- 依照 6/16 公告資料，紓困項目包含：
- 視覺功能障礙者從事按摩工作補貼
- 公告「補助地方政府辦理身心障礙者庇護性就業服務計畫」因應嚴重特殊傳染性肺炎(COVID-19)疫情之協助措施補助項目範圍
- 勞動部「補助地方政府辦理身心障礙者庇護性就業服務計畫」因應嚴重特殊傳染性肺炎（COVID-19）影響之相關防疫補助措施公告
- 衛生福利部托嬰中心.居家保母紓困內容
- 育有未滿2歲孩童家庭防疫補貼
- 本縣托育機構及居家托育人員因應新冠肺炎相關重要防疫作為
- 因應嚴重特殊傳染性肺炎(COVID-19)第三級警戒，調整育有未滿2歲兒童育兒津貼之受理申請日
- 暫停提供托育服務期間，其紓困措施與收退費及家長托育費用補助等事宜
- 自營作業者或無一定雇主之勞工生活補貼
- 防疫補償申請(受隔離或檢疫者)
- 110年因應疫情擴大急難紓困發放
- 疫情紓困弱勢加發生活補助

[2020短期紓困計畫](https://event.penghu.gov.tw/wuhanpneumonia/home.jsp?id=6&act=view&dataserno=202004140003#image-1)


### 金門縣

1. 津貼發放，中低收入戶每人核發新台幣6000元、安心即時上工計畫等。
2. 
[社會處紓困](https://social.kinmen.gov.tw/Content_List.aspx?n=CA354CDAC23985D9)
> 裡面是去年的資料
3. [稅捐減免，包括地方稅（娛樂稅、房屋稅）、縣有不動產租金、委託經營權利金及規費等4項稅捐費用減免及延繳](https://kmtax.kinmen.gov.tw/Content_List.aspx?n=154F7857DE551E7F)
4. 經營協助，包括補助產業專案行銷及強化電商銷售、建照及雜照工期自動展延1年及補助商圈業者購置餐具清洗殺菌乾燥設備等。
[建設處振興方案](https://ead.kinmen.gov.tw/News_Content.aspx?n=22D5C7FFA693BE32&sms=5394872914A6C125&s=6B2EB658AC3B6A2D)
5. 產業紓困，包括串接中央紓困貸款加碼利息補貼、推動線上職訓津貼等。
[觀光處紓困振興方案](https://kmtd.kinmen.gov.tw/Content_List.aspx?n=1852F471D9F31608)

### 連江縣
[連江縣政府-嚴重特殊傳染性肺炎及紓困振興特別條例](https://www.matsu.gov.tw/chhtml/content/371030000A0011/2019)
![紓困防疫十五招](https://www.matsu.gov.tw/attached/image/20210531/20210531180055_3912.jpg)



## 紓困方案對象

### 藝文產業

藝文團隊疫情紓困資訊整理共筆
https://hackmd.io/@b3ss/arts_rescue_2020/

### 中小企業
－中小企業貸款總額加碼1000億元（總金額達4000億元），且區分為3種貸款額度上限方案，分別為400萬元、1600萬元和50萬元，其中50萬元方案預計可惠及500萬小規模營業人。

### 服務業

－對象：商業服務業、會展業者等

### 觀光業
－對象：旅宿業、旅行業、觀光遊樂業等

### 航空業：
－航空業者及機場業者之相關使用費及權利金等補貼
－北中高機場國際航廈商業服務設施業者紓困補貼

### 教育業：
－運動產業、社區大學、留遊學服務業紓困補貼
－私立幼兒園、短期補習班、兒童課後照護中心停課紓困補貼
－高中職以下學校停課影響團膳業者食材損失補償

### 農漁業：
－農漁經營者紓困補貼

### 長照產業：
－紓困4.0 照顧服務受嚴重特殊傳染性肺炎影響之紓困措施
－[https://covid19.mohw.gov.tw/ch/cp-5193-61208-205.html](https://covid19.mohw.gov.tw/ch/cp-5193-61208-205.html)
－照顧服務提供單位-紓困QA(0603版).pdf
－[https://www.mohw.gov.tw/dl-69370-093de031-74b3-4bc7-96a8-3e9371d470a1.html](https://www.mohw.gov.tw/dl-69370-093de031-74b3-4bc7-96a8-3e9371d470a1.html)
－衛生福利部對受嚴重特殊傳染性肺炎影響其他照顧服務提供單位發生營運困難紓困措施申請審核作業規定(1100607修正).pdf
－[https://www.mohw.gov.tw/dl-69511-a16f72f4-dcda-496d-835c-872554b05d01.html](https://www.mohw.gov.tw/dl-69511-a16f72f4-dcda-496d-835c-872554b05d01.html)
－住宿式機構受嚴重特殊傳染性肺炎影響之紓困措施
－[https://covid19.mohw.gov.tw/ch/cp-5191-61206-205.html](https://covid19.mohw.gov.tw/ch/cp-5191-61206-205.html)
－附件1-住宿式機構紓困QA.pdf
－[https://www.mohw.gov.tw/dl-69460-442b19c3-17ce-438e-a16d-9f2a2a73bf2e.html](https://www.mohw.gov.tw/dl-69460-442b19c3-17ce-438e-a16d-9f2a2a73bf2e.html)
－附件2-住宿式機構紓困流程圖.pdf
－[https://www.mohw.gov.tw/dl-69461-64656680-e801-4b6f-85a9-f50295f0fd99.html](https://www.mohw.gov.tw/dl-69461-64656680-e801-4b6f-85a9-f50295f0fd99.html)

## 相關 QA

### 產業面
1. 目前有哪些產業已經列入紓困方案中？
A: 根據行政院長蘇貞昌表示，紓困4.0的對象，將包括因三級管制停業的
(1) 休閒娛樂業
(2) 觀展觀賽業
(3) 教育學習業
(4) 受衝擊的農漁民
(5) 觀光旅宿
(6) 領隊導遊
(7) 餐飲
(8) 計程車
(9) 遊覽車
(10) 還有小攤商與無固定雇主的勞工等自營作業者

2. 如何查詢自己的產業是否有在紓困方案的對象當中
A: 目前採取從寬認定

### 申請面

https://covid19.mohw.gov.tw/ch/cp-5188-61205-205.html

1. 關於此次的紓困方案，一般民眾要如何申請？
(1) 去年有申請補助且合格者，免填資料，可直接入帳
https://www.cna.com.tw/news/firstnews/202105280103.aspx 

(2) 新申請者：目前詳細的流程尚未公布，但蘇揆指示將從寬認定
6/7-6/30 可以上衛福部 110年度因應疫情擴大急難紓困線上申辦系統 線上申請
或者是郵寄申請
https://swis.mohw.gov.tw/eip/index.jsp

2. 110年個人紓困條件查詢網址
- [110年個人紓困條件查詢網址](https://edesk.bli.gov.tw/na/na_gsp_login.jsp)
- 教學文:[https://ghsha.com/articles/547](https://ghsha.com/articles/547)
- 紓困試算工具
    - 試算網頁：https://fii.bengkuei.me/mohw_10000.html
    - 原始碼：https://github.com/yhl/mohw_10000
    - 作者與網址來源：https://www.ptt.cc/bbs/Tainan/M.1622711789.A.72D.html


# 立法院相關預算資訊

- [案由：行政院函請審議「嚴重特殊傳染性肺炎防治及紓困振興特別
條例第十一條及第十九條條文修正草案」案。](https://lci.ly.gov.tw/LyLCEW/agenda1/02/pdf/10/03/14/LCEWA01_100314_00108.pdf)
    - [議事流程](https://misq.ly.gov.tw/MISQ/IQuery/misq5000QueryBillDetail.action?billNo=1100513070100100)
    - 草案重點
        - 提高本條例所需經費上限為新臺幣六千三百億元
        - 延長本條例及其特別預算施行期限至一百十一年六月三十日止
    - 三讀通過
        - 上限為新台幣八千四百億元
- [嚴重特殊傳染性肺炎防治及紓困振興特別預算 各月會計報告](https://data.gov.tw/dataset/122610)


## 資訊來源整理
中央社報導：
https://www.cna.com.tw/news/firstnews/202105285011.aspx 
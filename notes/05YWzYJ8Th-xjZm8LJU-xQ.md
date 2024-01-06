---
tags: vaccine,COVID-19,
tittle: Vaxx.tw 2.0 專案規劃會議
description: 
---

# Vaxx.tw 2.0 專案規劃會議

## 基本資訊
時間：2021/5/30 14:00-15:05
Time:2021/5/30 14:00-15:05 

## 參與者
* kjcl
* Freddy
* au
* mei-chi
* peggy
* ael
* 龐一鳴
* SL
* isabel

> [name=kjcl] 拜託大家幫忙我英翻中 Q_Q
> [name=peter]done
> 

## Meeting Objective 會議目標
* 了解政府與公民科技社群參與者能夠如何分工 (Understand the division of labor between g0v and the government)
* 確認一下政府現在有提供什麼樣的開放資料以及在開始打下一組疫苗之前能夠實現什麼成果。
* 確認一下 PDIS 以及其他政府單位正在開發什麼樣類似的案子。


# Vaxx.tw 2.0 Plan

## Mission 目標
* Get official data from hospitals quickly. 
快點從醫院拿到資料

## What Data does government have? 政府有什麼資料
* Freddy: Understanding that the process for getting self-paid vaccines is annoying.
    * The problem for government-paid vaccination is the clinics. They have no online system and rely on phones.
    * Various local-governments have their own systems. So if they can provide machine readable data, then things will be better.
    * Came to g0v a week ago. Talked with au. 
    * 指揮中心需要跟各級政府溝通，看他們願不願意來串接這個平台。
    * 若沒有系統，看來用目前政府正在開發的平台就可以用了，不需要請inline協助導入。
    * imaging the platform to be a place that you can see where the closest sites are. 一個能夠讓你找到最近的接種地點的平台。
    * 政府做的一定是最基本的資料，相信vaxx可以做更友善的運用。
    * 
* 美琪
    * 期待在大量注射疫苗前就先開通系統（跟指揮中心討論日期）
    * 中央對地方的疫苗發放，然後地方縣市自行掌握施打點（衛生所、社區站等）
    * 民眾在線上自行預約，也可以在超商、藥局進行預約。
    * 分上午、下午、晚上，依照行政區查詢
    * 地方會每天會更新疫苗狀況，希望每個晚上回報接種量給cdc，讓隔天的預約可以更精準。
    * 中央到地方的發放劑量data 是 open的，地方的data會由地方決定是否要開放資訊。
    * 接種的數量還是會回到cdc 的系統上。只要了解每個縣市的施打數量（分子）就可以知道每個地方的施打狀況
    
* Pofeng
    * 另外開發？不是IVIS?
    * 這兩邊的系統最後是怎麼連結的？
    * 沒有抓到庫存，預約就沒有意義？


* 美琪
    * 另外一個系統，這是預約注射系統，而Pofeng說得比較像是目前已在使用疫苗回傳系統
    * 預約與回報的對象都是CDC


* Kevin: 名額的公開和已接種疫苗的公開，會以機器可讀的方式公開嗎？
* 美琪：
    * 符合可以施打對象，會由 CDC 公開
    * 每個縣市有多少劑量
    * 打完之後，每個點會回傳到 CDC

* Kevin：這是國家在開發的統一預約系統嗎？這個數據是開源的嗎？

* 美琪：
    * 以後是鼓勵每個人打疫苗，符合的國人只要疫苗量是夠的，就會鼓勵大家去打
    * 很少數沒有健保卡的人，還是用醫院的體系進入。 
    * 不是每個醫院都會接軌新的系統，看他們的意願
 
* Pofeng :希望可以同步？

* 美琪：目前還在談

* SL：
    * 確認Kevin的意思，既然是開源的，是否民間的人也可以去使用這個服務

* Kevin: 
    * 今天如果我需要這個制度，是否我就可以在1922.cdc.gov看到全國的預約?
    * 未來只要去 1922 系統就可以預約嗎？預約全國的？
    * 規劃是要有統一的預約系統？
    * 以我們的身份可以寫一些補充的資料進來網站，協助看看這些無法接軌的醫院的資料網站？
    * 1922 的 data 能不能串連到 vaxx.tw 網站嗎？

* 美琪：
    * CDC分配給各個縣市的量一定會opendata，但是各個縣市分配到各個接種站點的量，是否會開放要看各縣市。是不是機器可以判讀可能要考慮一下，政委說要幫忙的就可以進來，是有預留這個系統的。

* Freddy:資料是機器可以判讀的嗎？

* au :當然

* ael 
    * 有診所或醫院不一定會接1922，疫苗在各地的實體庫存量，中央只知道地方上有多少，但是地方政府不希望開放資料就不會有。目前接1922的方法有超商藥局健保快意通，而對於民眾來說，重要的是要怎麼做一個平台理解目前的施打狀況，離我最近的醫療站點，能不能選廠牌。
    * 目前的系統是各地接種點會回報資料，資料會回到1922的資料庫。
 
* au 
    * 要近open data再出去，現在的就是open data，從口罩實名制來的。現在中央疾管署與健保署是兩套各自的體系，開放資料會方便民間進行協作。

* 美琪：
    * 超商完成後，盡量不要造成注射點的負荷，在關貿有一個按鈕說完成注射那就是會送資料回到CDC，這樣CDC就會拿到資料了。
    * 現在的回報系統跟之前診所使用的系統是分開的（？）
    * 由醫護人員，在注射完後按一個紐，資訊就會回去到cdc了，現場的醫療人員負責直接回報，這個回報會直接變成data送到cdc資料庫裏

* POfeng
    * 診所是直接回到NHI上面，再由NHI來回報
    * 「診所誰施打了」的資料回到NIIS，不是CDC的那個系統
    * CDC是處理預約掛號，負責發疫苗到縣市政府，
    * 預約那邊會有一堆資料（CDC）注射完的資料是回到NIIS

* 美琪：
    * 把這兩個資料串在一起，是CDC的部分

* POFENG:比較困惑的是怎麼串接？

* AU:除了診所外，1922進行預約

* POFENG
    * 完全禁止現場掛號，要插其他看病的就再想辦法。
    * 類似口罩實名制，藥局會分配一段時間發口罩，其他時間可以進行自己的業務

* ael 
    * 基層診所要現場回報，又要回報到NIIS

* pofeng
    * 要對兩次，因為可能會有錯誤發生

* rosalind
    * 地方政府與醫院與醫事人員怎麼處理？

* 美琪：
    * 本來就是有管轄關係的

* Pofeng
    * 地方政府在open data上會有考量（地方政治上的考量）這也是為何要給予選擇的原因。要讓公民自己去設定challenge的機制

* ael
    * 診所會先登記有多少疫苗，誰給預約系統資料，哪個點分配了多少疫苗？

* 美琪：
    * 疫苗到了每個縣市，讓各地縣市政府自己去分配，各縣市的衛生所衛生局去處理這部分的問題。而不是診所回報多少量，民眾再去預約。

* ael
    * 地方的衛生局會直接給1922預約系統說，每個點有分配給多少量，在搭配給診所用掉的多少，是1922上能接受的量

* 美琪：
    * 先放上去的劑量有多少，民眾才可以去預約

* Kevin
    * 分配的量有多少名額是兩個不同的事，因為醫護人員的考量或時間的考量
    * 最後決定診所有幾個名額是誰決定的，由誰管制

* 美琪：
    * 衛生局分配給各個接種點，回報後，會出現可以預約多少個人，然後才開放給民眾登記。

* ian
    * 新聞講說，醫院拿到的劑量，以瓶來說可施打的人數並非固定值以此例為條件，一般診所如何知道自己分配的劑量要如何分配疫苗的施打

* 美琪：有去請教cdc，cdc系統開通後要跟衛生局開會討論運輸，每個疫苗一瓶的劑量會打多少，都會有一個說明配著。

* Kevin:
    * 估計什麼時候可以開始去看這些開放資料，然後去使用他？
    * 他的API可以提供test data嗎（在還無法取得開放資料前）

* au:
    * 量的疫苗落地的那一刻
    * 這裏要分兩個點，opendata的schema一定可以，本來要資料程式才寫的出來，但是給接種點的不保證，因為要配合衛生局，要配合口罩地圖，這些不iterate幾次我們做不出來

* pofeng
    * 長輩預約好疫苗後我們會拿到什麼資料？

* au
    * 當然會有名單，想要打電話的確可以，但是目前系統設計是不打手機也可以預約
* 有些人之前有買過口罩，我們就會有他的電話
* 去藥局買東西的人不一定會有valid的手機

* Pofeng
    * 不用通知可能會額外的effort？

* au
    * 有考量留資料但是不強制。

* rosalind
    * 接下來全國普遍施打疫苗，是否會針對高風險例如年紀大或高風險？
    * 這套預約系統是否會針對此十大類做優先排序的動作？
    * 會用日期來解決優先預約的事情？
    * 目前新北有大量案例需要預約，因此會想要前置篩選他的接觸史與症狀史；在思考是否疫苗的施打也可以參考以上的流程，因而有此問題

* au
    * 有一個列表，這個列表是cdc會給名單，所有下一週有資格預約的人，沒錯優先順序會由指揮中心來安排

* kevin 
    * 正在做十個類別的翻譯，想知道資訊？

* au:類別會變動，我們就是一串具體資料的id 

* ael
    * 唯一不確定的部分，是大醫院不一定會使用這個系統；民間診所或社區接種站都會強迫要使用1922的系統

* au
    * 會開發官方的/Kevin開發民間版
    * 目前想知道的是民間版有什麼是可以幫忙、補漏、體制無法做的

* SL
    * 中央的系統難拿到醫院的系統
    * 民間是否可以用旁觀的方式獲得醫院的資訊
    * 幫忙用其他更好的方法察看全台施打狀況
 
* Pof
    * 1922要說服醫院用這一套、民間版說服診府用民間版

* Kevin/ael
    * 原版本31個自費疫苗的網站，民眾要去看是非常不容易的
    * 目前在做的就是便於民眾可以看到有哪些網站可以施打疫苗
    * 但目前因為疫情爆發，似乎沒有分配給民眾自費施打的疫苗，因此想詢問已經有中央的平台的狀況下，民間版還能做什麼
    * 目前唯一知道的中央版問題：大醫院可能不會配合使用1922系統
    * 或許這就是民間版可以做的事?

* isabel
    * 預約之後會安排一個序號嗎？

* 美琪
    * 以國人習慣，目前會給國人一個時段，如早上下午晚上

* isa：
    * 以此看來排隊系統會變得相對重要
    * 現場的部分交給現場的管控去做
    * 系統的目標是配合國人需求分配時間

* Kevin
    * 可以幫忙協助沒有使用1922系統的醫院取得數據外，還能做什麼
    * 想請問1922網站上線之後，會提供多少語言？
    * 因民間版的優勢在於語言的多國化

* au：
    * 以eMask的例子只有中文英文，且英文會晚一點

* ael：若民間自主翻譯，可以送patch嗎

* au：
    * 1922目前有藥局超商網站三個介面，並且使用快意通做一次性認證碼登入；四大超商或會自己處理翻譯；藥局不需要翻譯
    * 網站本身的翻譯是可以討論沒有問題的

* Kevin
    * 結論公民參與版可做的事：
        * 可以補充醫院沒有接軌的資料
        * 並且可以協助網站未翻譯的多國資料
* au
    * 1922是公費預約的系統；但未來若有自費的系統並不在目前1922系統的預設項目 ，故而未來民間版若有自費預約的部分仍可做保留

* ael
    * 之前去打疫苗的時候，會發生因為人數不足、診所不開而無法打疫苗的狀況

* au:此問題存在，但並不在此預約系統需處理的項目
 
* ael: 想問 au 還有什麼建議給 Kevin 嗎？

* au: 目前只有上午下午晚上的時段選擇，從通知到排隊應該還有些個別狀況無法一個個處理。
 
* isa:接下來還會有些宗教團體或企業自行採購或外展疫苗施打

* au：這個部分由企業自己處理，類似旅遊外展，此部分1922不處理

    
Mei-Chi: 
* Progress update
* Before mass vaccination, once we have stabilized vaccination plans, open up for scheduled. We are working with CECC for a date. 
* CECC -> 22 Counties/Cities and they distribute themselves. 
計畫進度更新
*在大型疫苗注射開始前，一旦確立了疫苗注射計劃，就可以開始進行預約。目前等指揮中心通知可以開放預約的時間
*指揮中心->22 個縣市自己分配

Questions: 
* what date do we anticipate this coming online? 
* What date do we anticipate opening up next round of government-paid vaccinations to the public? 
* 1922.gov.tw will come online. 
*我們預計什麼時間點上線
*我們預計什麼時候開放下一輪的公費疫苗注射
*1922.gov.tw 將會上線

## Assumption
My assumption is that government cannot provide real-time data directly, so we will have to collect it from the hospitals and clinics ourselves. I propose, for our MVP, we develop a VERY simple app we can give to hospitals/clinics to update whether or not they have appointments. 

我的假設是政府無法直接提供即時的資訊，因此我們需要自己從醫院與診所端蒐集。我建議我們的最小可行計畫是研發一個簡單的app並讓醫院診所利用這個app來回報他們的預約掛號狀態。

## Visualized flow: 流程圖

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_57108f3316c83ea66e8b3743d93ec4f7.png)


![](https://www.dl.dropboxusercontent.com/s/uoig3iu1i2pyxd4/vaxx_flow.jpg?raw=1)
> [name=SL] Listing out all the information I gathered so far from the slack channel for the sake of alignment and conversation. I hope this is what the flow is supposed to look like! Tiny black boxes = touchpoints.
> 簡單畫出在slack上看到的一些資訊，希望能幫助對焦。（希望沒有完全搞錯流程）小黑框裡面是會使用的接觸點。[high res image](https://www.dl.dropboxusercontent.com/s/uoig3iu1i2pyxd4/vaxx_flow.jpg?raw=1)

> [name=ael] 初步整理的一些流程
https://miro.com/welcomeonboard/4oAwhaBJbNI9GRULglb1fS9KjZh83TbJWgrz5yR42sJtfVHdYOyj3ueathsQ9egS


## Stakeholders: 利害關係人
* Users 使用者
    * Make vaccination reservation 預約打針 （主要）
    * Figure out if one is qualified to get vaccinated 查詢打針資格 
    * Check out Taiwan's vaccination status 了解疫苗施打狀況
    * Understand vaccination details 了解疫苗相關資訊
    > [name=SL] Listing out potential scenarios for users interacting with vaxx.tw. Knowing that vaxx reservation seems to be the main purpose of the site, I believe it would be possible to lift some communcation burdens from health care providers if people can first equipt themselves wih some knowledge.(i.e. if they are qulified or not, etc)
        > 先列出一些使用vaxx.tw的可能情境。知道預約打針是主要的功能，但猜想要是能同時溝通一些資訊（像是打針資格）應該可以減少很多民眾與地方醫護人員的溝通成本。
* g0v community
* Government 
    * 衛福部（MOHA）
    * Local governments（地方縣市衛生局）
        > [name=ael] This will be harder than mask map APIs as different locol governments have very different protocols
        > 這會比口罩地圖更棘手，因為地方政府會有自己的規範跟架構
* Hospitals
* Clinics
* 臨時設立施打疫苗站
* 標案廠商： e.g. 健保卡系統

### g0v 零時政府要做的事
* Develops vaxx.tw website.
開發 vaxx.tw網站 
* Develops system (app? mobile website?) for updating vaxx.tw 
開發app或手機網站來更新網站 vaxx.tw 上的資訊
* Develops API for updating vaxx.tw 
開發API來更新網站
* Develops scrapers (for big hospitals) for updating vaxx.tw
發展爬蟲程式(用在大醫院)來更新網站

Because of app store review times, it may take too long to put vaxx.tw on the app stores
由於 AppStore 審核要一些時間，把 vaxx.tw 網站做成app放到 Store 可能會花太多時間

### Government/Hospitals/Clinics
* Government pushes hospitals to use the vaxx.tw updating system.
請政府單位鼓勵醫院來使用這個網站
* Government provides: 政府要做的是
    * Easy-to-access data on what hospitals are offering vaccines. 
容易獲取有提供疫苗施打的醫院資料
    * (Give us all the data on this website:給我們以下網站上的所有資料 https://www.cdc.gov.tw/Category/MPage/swSqcNmV1UbHeJaVZJAJwg)


### Questions

> [name=ael] 我覺得要先釐清政府會做什麼，和醫療端疫苗的申請、配送、紀錄是怎麼進行的，才能知道 g0v 的版本可以做什麼。
> 我先大概整理了需要知道資料怎麼被傳送的方式https://miro.com/app/board/o9J_lBtuSmQ=/?moveToWidget=3074457359457666723&cot=14


> [name=mei-chi] 目前了解CDC疫苗未能公布剩餘量是因為，疫苗先分給22縣市衛生局，衛生局分給轄下醫療院所，每家醫療院所對於分配的量驗分別為二類院內醫護人員量及民眾量。目前CDC 對於疫苗是知道各衛生局總量，非各醫療院所，以上這些資訊也供大家參考。

> [name=freddylim] 接著疫苗除了醫療院所，應該診所也會可以打AZ，但診所很多還是用人工掛號的方式，所以我也正在兜看他們能否使用inline或其他的模式，提供機器可判讀的數字出來。（我也會透過診所的公會去跟診所強烈建議） (edited) 
>
> [name=ael] 想問 Mei-Chi，疫苗施打量是可以透過健保卡紀錄查得到的嗎？跟藥局刷了幾張健保卡領取口罩一樣？

### Updates from au: 
> [name=au] 目前 vaxx.tw 感覺比較像口罩地圖（口罩 1.0）的系統，是現有醫院的狀態整合。我們今天起正在開發的像是 eMask（口罩 2.0）系統，是公版的公費預約系統，需求端是：
    1. 行動接種站
    2. 衛生所
    3. 合約診所
    4. 想轉換到國有預約系統的醫院系統 （但只能轉進不能轉出，也不可以雙軌）
前面 1.0 的各醫院系統我自己目前沒有參與。
Currently, vaxx.tw feels more like Mask Map 1.0, and currently has availability from hospitals. We are currently building the equivalent of Mask Map 2.0, which is a public government-paid vaccination appointment system. We aim to include:
    1. Mobile vaccination sites
    2. Clinics
    3. Contract Clinics(?)
    4. Hospitals that wish to switch over to our system. (Hospitals can only switch directly in and not out, and cannot use both systems). 


My understanding: Government currently does **not** have data on real-time appointment availability and will not be able to provide it unless we provide an additional method of data collection. Because each hospital and clinic has its own appointment system, government cannot standardize this process. Is this true? 
Responses requested from `AU`, `mei-chi`, `freddylim`
我的理解是，政府目前並沒有即時的施打預約資料，且在我們能提供資料整理的方式前應該都沒辦法提供。因為各地的診所與醫院都有自己的預約掛號系統，讓政府無法標準化地取得這些資訊。請問這是正確的嗎？

> [name=kjcl] 了解！
想請問一下 @au
所以部分醫院如果無法轉換預約系統的話，還是會需要 vaxx.tw 類似的爬蟲去搜尋名額嗎？
到時候 2.0 系統上線之後，會開放 API 讓我們方便統一顯示名額在 vaxx.tw 上嗎？避免使用者需要跑兩個網站
那麼我的了解是，vaxx.tw 應該等待 2.0 上線，然後開始寫無法接軌的醫院的爬蟲。估計我們會什麼時候知道不能接軌的醫院有那一些嗎？
Understood, I would like to ask @au,
does this mean that for hospitals that are unable to switch to the government vaccination system, we will need a project like vaxx.tw to crawl websites for vaccination appointments? After we have the government system for appointments, will there be an API to allow us to show government appointment availability on vaxx.tw? This will prevent users from having to go to two websites. 
My understanding is that vaxx.tw should wait until this API is online, and then write the remaining crawlers. Do we have any idea when we will know the hospitals that are not participating in this program? 

> [name=au]
> 2.0 的 API 我明天可以談～ 
> I can talk about the 2.0 API tomorrow. 
> 目前已知的就是 旅遊醫學門診 其他都還未知
> Currently, we know that the travel medicine clinics are not partiicpating. Others I am unsure. 

> [name=kjcl] 
請問一下在會不會開 API 查詢名額跟哪些醫院已同意接軌有進展嗎？
@au, has there been any more progress around opening up an API and which hospitals will be included in the system? 

 > [name=au]
在接種端已規劃運用 API 讓第三方介接。
系統不會指定有哪些醫院（但會保持所有院所的接軌空間），醫院加入要由指揮中心協調、地方政府衛生局協助醫院上預約系統建立接種點資訊，才會在預約端出現。
We have planned an API around vaccination appointments, allowing third parties to connect. 
The system is not hospital-specific but provides the possibility of migration to all hospitals. Hospitals joining need CECC direction, and the assistance ofg local governments, for appointments to appear. 

## May 25 討論

關於政府疫苗登記 API 2.0

Freddy:
自己刷哪些醫院還有剩很麻煩

有跟衛福部薛次長討論，也有跟唐鳳政委討論
各級醫療院所都有系統，要怎麼給機器能夠判讀的資料很重要。
目前已經有一個系統了，聽起來可能診所和接種站更願意串接這個平台。

基層醫師公會討論

指揮中心要跟各級政府討論（轄區內的醫療院所要如何串接）

診所沒有系統的可以用 InLine，但現在 PDIS 的系統應該就可以做這件事，不用找 ＩｎＬｉｎｅ

到時候掛載1922.gov.tw下面，現在正在開發的新的系統。

實體健保卡和健保快譯通都可以用

如果本來就有了，就可以機器可讀資料上傳
這些資料都會是公開的。政府做的應該是最基本的資料。
公民科技可以做更友善的利用。

Meichi：


會期待在大量註冊疫苗之前，就把系統開通。讓符合的對象做預約，日期跟指揮中心做配合。

架構：

施打點的疫苗注射預約系統

配送：中央到地方疫苗發放釦連，由中央配送到22個縣市
注射：未來注射點不會只限定在醫療院所，除了偏鄉衛生所，還會有社區站（像是流感疫苗注射的公共空間）

政府方面會希望符合對象（有名冊），民眾在預約的時候，只要用健保卡，不用輸密碼，用快意通。

不會使用快譯通的人，可以去超商、藥局去預約，就直接引到施打點，例如早上、下午、晚上，行政區。

地方自己會去維運這個系統，自己去控管分配量

每天打的量會回傳到 CDC
也需要不重複登打，有些家屬會幫家人預約，造成重複預約的情況。

> [name=ael] 中央什麼時候能拿到地方政府的資料？
> A: 

目前只跟四大超商、健保署與FDA進行部內協調，已經在開發，但還沒到地方政府的權限上。
希望能夠測試一下，避免一上線民眾就過來。

政委有在跟民眾協調相關的內容，

目前使用google doc進行暫行紀錄：












## Abandoned Plans

1. 現在診所有名額可以打疫苗
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_00508e1a096e740781b4859fb44741a8.png)
 > [name=ael] I just want to add here that users may need help to check if they are legit to get the free vaccines. Government announces which categories can get free vaccines on one page and change once in a while. And the hospital websites only say if you are in 1st-4th categories you can get free vaccines, sometimes not even linking to CDC free vaccines category page. And the numbers of how many vaccines left may need to divide into 公費、自費疫苗。
 >我想要補充，有些使用者在確認自己是否為公費身份時會需要協助。政府有在一個網頁公佈公費資格，也會不時變動，然後醫院的門診網站告訴你除非你是第一級到第四級才能打公費疫苗，而且有時跟CDC 公布的公費資格並沒有吻合。現有的疫苗數量資料應該要分成公費及自費疫苗來呈現。
> 
> 若流程是有共識的，大家應該就可以分別去思考，怎麼讓地方政府可以簡單地協助上架、怎麼讓回報是簡單的，怎麼讓使用者簡單查詢施打資格＆場所等。我覺得這樣可以更有效率的分工。

2. 診所掛號已滿，工作人員打開 vaxx.tw APP。簡單按一下 「無名額」
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6167d0553f56e06fae575399a177c9de.png)

> [name=ael] I am not sure if this step is neccessary because government's central database of 健保卡 may have the realtime data with some latency.
> 我不確定這一步是否有必要，因為政府建置的健保資料庫應該會有即時的資料（雖然可能會有點延遲）
> [name=kjcl] Depends on our conversation with the government, but my understanding is that this data does not exist. That is why they need our help. 
> 需要視我們跟政府的溝通而定，不過我的理解是這些資料應該不存在，也因此政府會需要我們協助。
> [name=ael] There are also two scenarios. One is registration is full. The other is full registration but not everyone showing up and the vaccines are about to expire in 6 hr or so.
> 即使如此也可能發展成兩種情況，其一是掛號已滿，另一個是雖然掛號滿了但是有人no show導致有零星需要緊急施打的疫苗釋出。
> [name=ael] I distinguish hospitals and clinics because hospitals all have thier own online appointment registration system but not clinics. It just came to my mind that probably there will be irregular vaccine stations around the city on certain dates like the flu vaccines every year.
> 我將醫院與診所分開因為醫院都有他們自己的線上掛號系統，但診所沒有，而且我突然想到特定日期可能還會有醫院與診所以外的臨時接種站（如衛生所）就像是每年的流感疫苗接種一樣。
> [name=kjcl] We cannot cover all these cases for MVP, but worth considering down the line. 
> 我們目前以最小可行計畫來做，應該無法處理到所有情況，但考慮到這些是好的
> 

3. 網站更新資料，顯示現在沒有名額
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b94b19345dd9c0e43a4cea564e5ab84b.png)
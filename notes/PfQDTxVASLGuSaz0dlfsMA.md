---
title: "義務律師陪偵平台"
tags: g0v,hackpad
---

# 義務律師陪偵平台

> [點此觀看原始內容](https://g0v.hackpad.tw/h6fOoDAd9qZ)


## 近日活動

1/25(日) 10:00 - 18:00 [第零次法律松](http://g0vlawthon.kktix.cc/events/2abadbd7)@民間司改會[簡報](https://drive.google.com/open?id=1koIls6ubIReXBGkO0l5-xzbdd9bKJe1WEEDEPb29thg&authuser=0)


## 什麼是陪偵？

- 一般抗議活動時往往會有抗議民眾被警方帶走偵訊，為維護這些抗議民眾的權益，司改會協調義務律師前往現場協助民眾面對偵查。往往是事件驅動，並隨著各種事件的大小而有不同程度的驅動量。
- 本平台目的是確保每位當事人皆有律師陪同偵訊，並降低NGOs（目前平台為司改會）與當事人、律師間反覆確認的聯繫行政工作。
- 陪偵平台不僅可用在陳抗案件，一般檢警陪偵也同樣需要有效的案件認養系統（法扶陪偵專案）。

## 為什麼發起？

- 因為 TonyQ 去參與民間司改會 323 聯合訴訟時，跟執秘梅慧聊到他是資訊人，所以意外跌坑。主要是他們現在並沒有一個可以讓律師認養陪偵案件的有效系統，在聯繫律師的過程往往需要透過大量電話簡訊往返與確認，而且如果沒有辦法馬上接到回音的話，容易有多個律師去協助一個陪偵當事人的資源浪費的狀況。（除非案子很特殊，不然通常不需要一位當事人一位律師陪偵）
> 請問這是不是代表某些時候的確需要不只一個律師？如果是這樣的話，資料欄位或許可以加數量？ 
> [name=Tonyq W]

> 之前跟梅慧確認時提到這種時候通常非常特殊（ex.魏揚），可以作為特例處理。
> [name=Tonyq W]

> 了解。雖然我覺得以資料庫和寫程式的角度來說，加上數量其實不難 xD
> [name=Tonyq W]

> 我覺得可以保留擴充空間 就初期來講先以簡化介面為主 XD  （用最小單位推進） (ps.我想用 mongo XDD)
> [name=Tonyq W]

> 喔如果只是介面的話就先當作 n = 1 顯示第一個律師之類的 (mongo 會讓這件事情比較困難嗎？）
> [name=Tonyq W]

> 不會 可能比較簡單 因為他可以巢狀存資料。只要多 push 一個律師進去就好 XD
> [name=Tonyq W]

> 我的個人意見是一開始就要用 list, 但是 UI 先顯示第一個（如果非空）
> [name=Tonyq W]

> Sure :)
> [name=Tonyq W]

> 或者是說，因為司改會及律師之間也不容易掌握現場有多少律師，所以許多熱心的律師就乾脆直接到現場，但有時候其實現場的律師已足夠
> [name=Tonyq W]

- 加上民間司改會目前沒有太多行政人力可以做這件事情，如 318 學運期間曾有上百次的陪偵需求，聯繫相當浪費資源，若未來面對可能更大的抗爭規模，能否即時做出準備讓義務律師團能夠盡最大心力幫忙，是此一平台很重要的事情。
> 且其實目前我們較難協助中南部的陪偵（中南部是有義務律師的），希望未來此平台也可以協助中南部的陪偵
> [name=A-Han L]

> 我有一點想法想確認一下：請問這個平台提供公民需求尋找義務律師，那麼律師是否僅透過司改會聯繫？
> [name=A-Han L]

> 之所以提出這問題的想法是：如果該平台僅提供公民聯繫司改會，那麼由司改會單向聯繫各律師，縱使避免「公民有需求卻無法及時有義務律師」以及「無須過多律師確有太多義務律師到場」等兩種情況，聯繫過程也仍是資源消耗。
> [name=A-Han L]

> 假若公民和律師「雙方」都透過該平台聯繫呢？也就是說，作為一個及時為公民服務的平台，公民有「及時找到律師」的需求，而義務律師也希望「及時到現場且避免『過多律師造成不必要』」，所以對於律師來說，律師也要能在平台上確認及時資訊，而非被動聯繫。不知司改會覺得這樣的建置方式如何？
> [name=A-Han L]

> NGO做為中介者的原因是，需要有人去確認訊息的正確性及是否重覆，以避免律師空跑，平台設計是可讓多個NGO都能成為窗口。另外，案件也並非是一次陪偵就結束了，可能會有後續的發展，律師團仍然需要NGO去組織，相關案件也需要去追蹤，並且消化行政工作（以318-428的案件為例，大約有200多件辯護）。個人覺得還是需要NGO做行政平台，不過不一定是司改會。
> [name=Miffy C]

- 功能需求：（以下是以需求暨規劃書的方式列出，如得有現成套件可以取代可以討論、但請注意功能是否符合）
- 期望解決的問題：
    - 確認衝突發生時可陪偵的律師
    - 線上認養陪偵案件
    - 案件狀態回覆（ex:顯示已認養、多久到達陪偵現場）

## Wireframe

[Link1: NGO](https://www.dropbox.com/s/vh5q4dencfqixtz/64995_-_suferer%20%282%29.png)
[Link2: Lawyer](https://www.dropbox.com/s/vzsi6hc8j48knpv/Untitled_Page_%281%29%20%283%29.png)
- Web NGO使用 [https://moqups.com/miffy.dandelion@gmail.com/o1gI6Iyb/](https://moqups.com/miffy.dandelion@gmail.com/o1gI6Iyb/)
- App 律師登入使用的 mockup [https://moqups.com/pbear6150/0BBskG71/p:afa876067](https://moqups.com/pbear6150/0BBskG71/p:afa876067)
    - [x] 帳號設定（所有欄位皆可以修改）
    - 案件清單
        - [x] 只顯示未處理的案件
        - [x] 點案件可顯示較詳細的案件資訊：多「案由」及「地址」，在詳細案件資訊中有「接案按鈕」
        - [x] 按「接案」後可看到案件的聯絡電話，並轉入「發簡訊」的頁面，傳簡訊通知當事人「我是XXX律師，約多久後會到達」。
    - 先做NGO的Web及律師的APP，所以NGO的APP介面先緩緩～
> ==另外在「帳號設定」的icon旁邊，需不需要加入一個user自己接案清單的icon？還是律師一般接案就有自己的記錄了？==
> [name=Bear P]

- 圖D 問題：
    - 如果案子很多，是否下拉即自動載入下一頁？
        M: 或者是否就不分頁,讓他直接全部顯示,往下捲就可以往下讀(不確定APP的介面是否可以這樣呈現?)
    - 增加「關鍵字搜尋」功能？
        M: 個人覺得初版APP不一定要包涵此功能~大家可以討論一下~
    - 是否允許 user 可以看見丁小勝的基本聯絡資料？（加入超連結）
        M: 可以顯示律師的姓名,手機號碼,其他的不顯示~

## FLOW

#### Client

#### request - (A)

    - 求救窗口
    - 律師還未到場的注意事項（搜集現場證據）
#### have state - (N)

    - 簡訊回覆：XXX律師約於OO時間到達。若有問題，請致電（律師電話，及NGO號碼）。
#### Middleman

#### have(A) - (B)

#### make sure (A) is ture - (C)

#### register this event - (D)

    - 填表格-案主資料
        - 接案的NGO單位（下拉式選單-可以新增 NGO 單位）
        - 姓名
        - 電話
        - 逮捕原因（案由）
        - 案主地點：自由選填+縣市（下拉式選單）
        - 陪偵律師
#### connect with lawyer - (E)

    - On-call 的律師清單
        - 姓名
        - 可陪偵地點
        - 手機
        - 是否是法扶律師
    - E-mail
#### have(G) - (H)

#### have candidate - (I)

    - 從陪偵清單上，得知案件處理狀況
#### sent Detail & change state - (K)

#### notify client - (M)

#### Laywer

#### get the request - (F)

    - 陪偵清單：
        - timestap
        - 接案的NGO單位（下拉式選單-可以新增 NGO 單位）
        - 案主資料
            - 姓名
            - 電話
            - 逮捕原因（案由）
            - 陪偵地點
        - ==案件處理的狀況==
            - ==未認領==
            - ==已認領==
            - ==已到場（系統自掀到場時間）==
            - ==已結束==
        - 認領案件（按鈕）
#### answer variable - (G)

    - 陪偵清單：回覆之後，顯示律師的名稱（或帳號）連結，內有聯繫資訊
#### get feedback - (J)

#### get detail - (L)


## Web 欄位資料-主要 user

### NGO

（目前暫以司改會為主，將來希望能有更多NGOs加入）
- 接到電話，確認訊息正確性
- 登入帳號密碼
- 填表格-案主資料
    - 接案的NGO單位（下拉式選單-可以新增 NGO 單位）
    - 姓名
    - 電話
    - 逮捕原因（案由）
    - 案主地點：自由選填+縣市（下拉式選單）
        - 派出所地址+警員
- 新增律師
    - 姓名
    - 律師證號
    - 登錄公會
    - 可陪偵地點
    - 手機
    - E-mail
- 審核律師註冊資料
- 陪偵清單：timestap+案主資料+案件處理的狀況
- On-call 的律師清單
### 律師

- 登入帳號、密碼
- 註冊成為義務律師
    - 帳號（email）
    - 密碼
    - 姓名
    - 律師證號
    - 登錄公會（可多選）
    - 可陪偵地點（下拉選單，律師可修改）
    - 手機
    - E-mail
- 個人設定
    - 可以控制自己線上／線下的狀況
    - 修改資料
- ==被推播通知==新案件成立（最好可以是所在地的案件）
    - ==on call才通知？==
    - ==全部都通知（建議皆通知，就先前經驗主動的律師較少眾）==
- 陪偵清單：案主資料+案件處理的狀況+認領案件（按鈕）
- On-call 的律師清單
### 案主

- 求救電話的清單
- 律師還未到場的注意事項（搜集現場證據）
- 公民不服從手冊
- 小市民權益99招
- 可自行key檔（組織者確認後訊息post上平台）

## User Story

王小明是一個關心社會議題的年輕人，今天他為了反自由貿易經濟區，再次走上街頭。在捷運上，他先點開最近安裝的 App 「律師陪偵平台」，閱讀「若被逮捕」的注意事項。

到達目的地後，沒想到警察忽然強制驅離，王小明在混亂中被壓制在地逮捕，並被帶到中正一分局，過程中他的手機摔壞了。一旁的朋友陳大福看到，馬上拿出手機也點開「律師陪偵平台」App，點進「通報案件」，從提供法律協助的 NGO 清單中，隨便挑一個打電話。

Miffy：「喂，司改會，您好」
陳大福：「你好，我的朋友王小明被逮捕了，請問有律師可以協助嗎？」
Miffy：「好的，請先提供一下你朋友的資料。請問他的姓名？手機？目前所在的派出所？被逮捕的案由？您的電話？接下來我們會聯繫律師，大約需要 XX 分鐘，結束後會以簡訊傳送處理結果，你也可以再打電話過來確認。」

Miffy 打開「律師陪偵平台」網頁版，登入之後，把剛剛的通報資料key-in。接著，打開陪偵清單，確認一下剛剛通報的案件內容。接著，等待大約 10 分鐘，看看陪偵清單上的案件狀態，是否有律師認領；或是主動聯繫on call的律師。

正在永康街家中的律師曾小凱，手機螢幕顯示了有中正一分局的案件通報，他馬上打開 App，看見有人因為違反社會秩序而被拘留于中正一分局，於是按下「認領案件」按鈕，並且馬上打電話到中正一分局，與王小明聯絡。

## USE CASES

- 操作[網頁版介面](https://moqups.com/miffy.dandelion@gmail.com/o1gI6Iyb/)可以做的事情：
    - 關於 NGO:
        - 新增NGO
        - 新增使用者到某一NGO下 (初期可能使用者和NGO是一對一關係)
> 可能一個NGO有多位使用者
> [name=Miffy C]

    - 關於律師:
        - 新增律師
        - 邀請律師? 可以討論一下要哪些步驟 初期可以先用"新增律師"就好
> 因為律師得安裝APP先註冊，我們才能新增，我們可以發E-mail邀請其他律師安裝
> [name=Miffy C]

        - 看律師詳細資料 ex: 手上案件、是否有空(包含未來有空時間? 還是只看當下是否有空?)
> 只看當下是否有空（在律師APP的介面中可自己設定是否on Call）
> [name=Miffy C]

        - 刪除律師(初期不做)
        - 通知律師(?)
> 新增案件後在律師APP上會推播提醒
> [name=Miffy C]

    - 關於案件:
        - 新增案件
        - 修改案件資料，是否要可以指定接案律師? 還是只能由律師自己按認領
> 律師認領後，NGO使用者可以再修改，也可修改案件進度（所以若無人接的案件，NGO可透過修改指定律師）
> [name=Miffy C]

        - 通知有空的律師(?)
> 新增案件後在律師APP上會推播提醒
> [name=Miffy C]


## 欄位過往討論

Hackath9n 簡報：[http://goo.gl/2o3Ywx](http://goo.gl/2o3Ywx)　文稿：[http://goo.gl/v2CHQ2](http://goo.gl/v2CHQ2)

- 舊 hackpad： [https://hackpad.com/--ltsoiiHdSbX](https://hackpad.com/--ltsoiiHdSbX)
- 專案代號  JRF-_attorney_
> accompany/defend 會不會比 follow 合適？或乾脆用 attorney xD
> [name=Miffy C]

> 可以XDD
> [name=Miffy C]

> xD 用 attorney 感覺有潛力包括其他可能的服務 xD
> [name=Miffy C]

> android的bundle id也用這個嗎？＠＠，是的話我就把整個換掉
> [name=Takuma L]

        -
        - 資料庫，資料表有
            - 律師資料
                - 姓名
                - 律師證號
                - 登錄公會
                - 可陪偵地點
> 【可陪偵地點】此欄位需要律師可自行編修
> [name=Tonyq W]

> 會在 app (client) 區的規劃裡面
> [name=Tonyq W]

                - 手機
> [Miffy Chen](https://hackpad.com/ep/profile/AymLJPx1IpL) 連手機都需要切到日夜這麼細嗎 QQ
> [name=Tonyq W]

> 如此安排是因為希望可確保夜間的聯繫，所以特別強調出來，我也猜想此欄位應該會與白天的一致，但在與雨凡討論後覺得還是細分，以避免聯繫上的狀況
> [name=Miffy C]

> 初版先不分日夜，只留手機
> [name=Miffy C]

                - E-mail
                - Line ID（選填）
> 若平台有類似聊天室的功能，讓義務律師們可留下訊息，那就更完美了XD 就不需有Line ID這個欄位
> [name=Tonyq W]

> 流行的聯絡方式一直變，建議不要綁死 Line
> [name=Tonyq W]

> 同意，或許平台上是否可能有留言板的功能，讓彼此可留下資訊
> [name=Tonyq W]

> 建議可用 {聯絡方式/資訊} 一組。例如 {skype/xxx} {line/ooo}
> [name=Tonyq W]

            - 案件資料
                - 姓名
                - 電話
                - 逮捕原因（案由）
                - 陪偵地點：地名(通常都是派出所)、地址、map
                - 陪偵地點區域（縣市，因為律師需要註冊該縣市律師才能執業，所以區域很重要）（至少 UI 中由陪偵地點自動推出）
                    - 基隆律師公會
                    - 台北（含士林，板橋，台北地方法院）
                    - 桃園
                    - 新竹
                    - 苗栗
                    - 台中
                    - 南投
                    - 彰化
                    - 雲林
                    - 嘉義
                    - 台南
                    - 高雄
                    - 屏東
                    - 台東
                    - 花蓮
                    - 宜蘭
> 看起來「陪偵地點區域」可以由「陪偵地點」推出。
> [name=Tonyq W]

> agree 當初是不知道有哪些律師公會，剛跟 isabel.hou 討論後找到律師公會名單應該能看看能不能再簡化介面
> [name=Tonyq W]

> 看來最好的設計，是 UI 會幫你推，但不強制一定要一致，這樣可以手動調整應付特殊狀況
> [name=Tonyq W]

> 這個陪偵地區要去對上面律師資料中的”可陪偵區域“才有辦法發訊息。
> [name=Tonyq W]

> 先確認律師工會的清單是變動性不大的吧 XD   原則上這清單會從 server 來。(web) 
> [name=Tonyq W]

> 這些推論和檢查我認為都是合理的，但我認為都要保留手動違反這些限制的空間，應付資料來不及更新、奇妙的特殊狀況等問題。
> [name=Tonyq W]

                - 案件狀態（依照 新收案、已確認陪偵、陪偵中、已結束、取消）
                - 接案律師（資料庫中允許多位，但 UI 先最多顯示一位）
                - 預計到達時間
                - 到達時間
                - 陪偵結果紀錄
        - 介面
            - 公開介面
                - 目前沒有規劃頁面，TonyQ 有建議，可以把義務律師接的案子列出來作為對義務律師的正回饋（還在討論中）。
            - 內部介面（草案是以  jrf.org.tw domain 的 gmail 作為驗證）
                - 司改會 key in 案件資料表單
                    - Key 完後直接發 notification 給所有該陪偵區域律師詢問他們意願
                - 顯示所有案件資料列表（依照 新收案、已確認陪偵、陪偵中、已結束）
                - 顯示特定律師承接的案件與狀態
                - 司改會確認律師註冊是否正確的設定頁（律師需要先註冊再由司改會確認）
                - 司改會邀請律師註冊的頁面
> 讓司改會也可邀請律師如何？這樣可能可以讓平台轉換更容易。
> [name=Tonyq W]

> 有道理。
> [name=Tonyq W]

> 同意。
> [name=Tonyq W]

    - App (iOS/Android)
        - 主要 user：律師
        - 介面
            - （選擇性）靜音：可以預先設定目前願意服務範圍，超出的請求不會吵。或乾脆全靜音。
            - 通知：當可服務區域內有案子時會收到通知，並決定、回應是否去處理。（若接案時已有人處理會顯示已有人處理，(目前)一案以一人為主。）
> 反正目前 UI 只能輸入一筆，n == list.size() 就代表不需要幫手了
> [name=Tonyq W]

            - 註冊：同網站律師資料表，註冊後等待司改會 approve（如果被邀請則免）<< 這裡需要填寫可服務範圍
> 但有可能律師剛好今天跑到其他地方去啦（我的意思就是這沒有解決物理性位置）
> [name=Tonyq W]

> 律師要先登記才能服務
> [name=Tonyq W]

> 這是指登錄區域，不是物理性位置。
> [name=Tonyq W]

> 聽起來現在是需要再切一個平常可以服務的區域跟登錄區域? 我原本的想法是直接用登錄區域<
> [name=Tonyq W]

> 我覺得如果要讓律師覺得好用，可能要有「靜音」功能 xD
> [name=Tonyq W]

> yep 加個讓他可以選擇只只接收哪些區域好了（但一定在登錄區域內） （hackpad這系統是不是跟新酷音有仇啊Q_Q）
> [name=Tonyq W]

> 直接忽略就好了啦。真的，一開始不要想太複雜。我不太可能每天去手動調位置，老實說。不過要能不要一直響。
> [name=Tonyq W]

> 好吧先做第一版出來再來調整 XD 我也覺得應該先收斂需求 哈哈
> [name=Tonyq W]

> 那就先用振動吧，這個通知該怎麼做可以再想一想。（狀態顯示正在刻 web） XDDD
> [name=Tonyq W]

            - 接案：可選擇是否接案，接案後要寫預計到達時間跟用律師手機簡訊通知當事人
            - 案件管理：瀏覽過去兩個月案子(?)
            - 帳號管理：更新註冊資料
> 讓律師願意主動回報目前所在地點或是被動選擇案件區域如何？假設大家都同樣有空、意願相似的話，是不是比較近的人去移動成本最小？（這跟司改會通知要發給誰是兩回事）
> [name=Tonyq W]

> 我沒有寫清楚，目前其實計畫會是 pool ，就是傳送給該區的所有人，看誰先回應這樣。（是有談到一個可以讓律師設定在線上或不在線上，但我覺得這個有點太複雜） （另外這個系統也應該要可以允許非原本的義務律師來加入）
> [name=Tonyq W]

> 對我的意思就是這樣。至少讓律師被動的選擇願意接受的範圍。
> [name=Takuma L]




## APIs


### App

url: /app_login (POST)
input:
- name (String/ 律師名字（本名） ) ,
- cellphone(String/律師電話)
- locations (Array\[String\], 可陪偵區域(json array),ex. \['基隆律師公會','台北律師公會'\]  )
- Email (String/Email)
- authType (enum("FB","Google"),登入類別（目前接受 'FB' 跟 'Google' 兩個值 ） )
- authToken (登入資料中 Google or Facebook 的 access token (由 android/iOS 預先認證好丟上來) )
output:

url:/getAttorneyInfos/<PENDING | OFFLINE | ONCALL>
input:
- limit (int)
- offset(int)
output:
- layerID
- name
- license
- cellphone
- email
- createDate
- status ( 0 : 未確認, 1:offline,2:online)
- locations
- last_modify


### Web


/getNGOList/
    @param {number=} opt_limit
    @param {number=} opt_offset

/saveNGO/
    @param NGO: {name: 'ngoName'}

// User: 可以登進網頁系統填單者
/getUserInfos/
    @param {number=} opt_limit
    @param {number=} opt_offset
    @return UserInfo: {userId: 'id', name: 'userName', cellphone: '0912345678', orgName: 'orgName'}

/getUser/id/
    @return User: {userId: 'id', name: 'userName', cell: '0912345678', landline: '(04)8765-4321', org: {name: 'ngoName'}}

/saveUser/
    @param User: {userId: 'id', name: 'userName', cell: '0912345678', landline: '(04)8765-4321', org: {name: 'ngoName'}}

/getAttorneyInfos/<PENDING | OFFLINE | ONCALL>/
    @param {number} opt_limit
    @param {number} opt_offset
    @return Array.<id: 'id', AttorneyInfo: {id: 'id', name:'attorneyName', locations: 陪偵縣市, numCases: 案件量, cell: '0912345678'}>

    AttorneyStatus = {PENDING: 0, OFFLINE: 1, ONCALL: 2}

```
{"isSuccess":true,"errorCode":0,"data":[{"time":"","name":"\\u738b\\u666f\\u5f18","cellphone":"0975772843","location":"\\u53f0\\u5317\\u5e02","status":0,"attorney":{"name":"test","status":0,"id":"5482a25a9d8d3f7017000029"},"0":"createDate","createDate":1417856419000,"id":"5482c5a39d8d3f141300002c"}],"errorMessage":null}

```
/saveCase/
    @param CaseInfo: {caseID: 'id', eventTime: 'time', name: 'name', cell: '0912345678', location: '縣市', address: '地址', description: '案由', status: PENDING | MATCHED | IN_PROGRESS | CLOSED, note: 備註, attorney: '接案律師'}

## APP 功能列表

- 登入 By Facebook, Google mail
    - Android 同時進行
> 目前已先添加Facebook SDK與建立Android平台，如果iOS還沒建也需要的話請通知一下m(_ _)m
> [name=Takuma L]

- 律師列表：
    - Android順序1
- 案件清單

## 進展

    - [~Tonyq Wang~](https://hackpad.com/ep/profile/HUoUqaJnV2n) ~認養 Web~
        - [~https://github.com/JRF-attorney/jrf-attorney-web~](https://github.com/JRF-attorney/jrf-attorney-web)
            - [ ] 移進 g0v
                - [ ] 跟司改會確認過 open 的問題
            - [ ] 建立正式測試站
                - [x] api 的註冊(register method) 並可回傳 sid
                - [x] 後台權限認證
                - [ ] 建立/編輯案件
                - [ ] api 查詢相關 method
                - [ ] android client  [Takuma Lee](https://g0v.hackpad.tw/ep/profile/Ezy723qvidk) 認養、[小說](https://github.com/668Jerry/democrasafe)認養
> android有人認了嗎? 沒有的話我要~
> [name=Peng]

> 我認養了不過歡迎一起做lol，所以認養要寫後面嗎？
> [name=Takuma L]

> 不知道耶XD 目前android的專案是下面Android Repository的連結嗎? 現在到哪邊了?
> [name=Peng]

> 我打算重開一個專案，會用JRF-_attorney這個代號來命名，目前還沒什麼進度lol，不過其實應該可以先開始做UI_
> [name=Takuma L]

> 我開一個小專案了，[https://github.com/668Jerry/democrasafe](https://github.com/668Jerry/democrasafe)，想把他加入g0v專案，但我不太會操作github >  <，目前把fb功能架起來，希望能夠和Android神手們一起做(新手中...)；如果需要吸收專案、合併或取得push權限直接找我就行囉。
> [name=小說]

                - [ ] iOS client  [Bunny Lin](https://g0v.hackpad.tw/ep/profile/CyfaBr0immZ)認養

    - 張晏甄（第九次hackathon的code）：[https://github.com/gigenchang/lawyer995](https://github.com/gigenchang/lawyer995)
> 我有個想法：也許之後還可以做給當事人用的 app.
> [name=Tonyq W]

> 同意
> [name=Tonyq W]

> 像是社運的場合如果可以單鍵送出似乎很方便。不過也許要先跟司改會註冊帳號之類的。
> [name=Tonyq W]

> 之前警方函送幫社運直播的公民記者時，我們在直播社團（[**公民議題網路直播現場攝影與網路監看組**](https://www.facebook.com/groups/1484094481805577/)）有討論過這件事，[Rhozan](https://g0v.hackpad.com/ep/profile/v2FoVsCJSQ7) 當時也有和司改會及義務律師團搭上線，當時的討論在這邊 [https://www.facebook.com/groups/1484094481805577/permalink/1502955929919432/](https://www.facebook.com/groups/1484094481805577/permalink/1502955929919432/)
> [name=Tonyq W]

> 目前對於目前對於當事人最主要的問題在於身份的確認與回報的正確性，目前還沒有足夠多的資料與經驗來佐證這些事情，可能之後再跟司改會來討論後續的發展。我是覺得如果能夠有信得過得中介人來幫忙回報，對系統會有不錯的加分。因為如果是錯務的回報對這制度還是蠻麻煩的。XD
> [name=Tonyq W]

> 其實這是我們最期盼的狀況，完全的開放給大眾，將報案、義務律師接案、律師聯繫當事人並前往陪偵，完全在平台上進行，不過如同TONYQ所說，在確保訊息驗證的部分我們還沒想出可以解決的好方法。
> [name=Tonyq W]

    - 最新 Repo [https://github.com/JRF-attorney/lawyer995](https://github.com/JRF-attorney/lawyer995)
> 抱歉一陣子沒關心了，剛上去看有個swift的ios project....是要改成swift嗎？是說，都可以啦，我也開始改了，原本的fb應該是fb端沒設定好，我用我自己的fb develop app設定好就可以登入了。打算開始串API了，可是我找不到API server 的URL在哪啊 請 tonyQ 大大出來解救一下啊
> [name=Bunny L]



8/2 司改會辦公室討論項目:
- 架在 instance-based service 上
- Android Repository：[https://github.com/TakumaMochizuki/LawyerDetector](https://github.com/TakumaMochizuki/LawyerDetector)
- Admin Repo: [https://github.com/ychi/lawer995-admin](https://github.com/ychi/lawer995-admin)

2014/1/12 網頁端更新:
- Admin Repo: [https://github.com/ychi/lawer995-admin](https://github.com/ychi/lawer995-admin)
- sync下來後把 js/conf.js裡的 apiURL 指定成 [http://jrf.tonyq.org/api/](http://jrf.tonyq.org/api/)
- 放上 web server; 如果要直接從本機檔案系統打開的話，chrome 會因為[安全考量](https://developer.chrome.com/extensions/xhr)不給開
- 目前律師頁面是比較可以參考的，會從 Tony mock 好的 API 真的拿一筆資料回來
- 接下來要做的 :
    - feature: 把 angular modules 換成用 bower install
    - feature: 讓使用者頁面和案件頁面也都用API拿資料
    - bug: 在案件或律師tab 按 f5, tab 顯示會有問題
    - feature: 在律師資料列上點擊後打開一個modal, 顯示律師完整資料 並且可編輯儲存。案件、使用者亦同
    - epic: 身分認證和權限

## 法扶檢警中心（初討論）：第零次法律松

### 現況及未來可能發展

1.  律師駐點（警局排班）
    1.  一警局（或地檢署）一律師值班
    2.  討論中
    3.  會先找試辦警局
    4.  可能狀況：當有多位當事人時，律師仍不足
2.  一個地院一個分會
3.  律師排班表
4.  多分會的整合
    1.  警局會依轄區找到相應的法扶

### 法扶陪偵平台

1.  警局或當事人自行上網登檔
    1.  申請人
        1.  重罪（下拉式選單）
        2.  原住民
            1.  警員有時會刻意誤導當事人：「法扶不用錢但律師要錢」，使當事人簽放棄委任律師
            2.  也許可要求切結書有固定內容或格式，否則該切結書無效（修刑訴）
        3.  身心障礙者（無法陳述者）
            1.  可備註特殊需求
2.  律師自行上網排班
    1.  工作人員可修改
3.  推播律師分優先次序
    1.  輪值律師
    2.  備班律師
    3.  相近時間排班律師
        1.  當班±1天的輪值及備班律師
4.  系統抓律師出發時間回家時間
    1.  未來可發展自動計算律師預計到達時間（Uber）
5.  45分鐘內律師必須到（原住民等距離較遠者4小時）
6.  律師回報
7.  警局
    1.  已出發
    2.  已到達
    3.  陪偵結束
    4.  已回家
8.  地檢署（函送）
    1.  已出發
    2.  已到達
    3.  陪偵結束
    4.  已回家
9.  陪偵結束後律師線上填寫
    1.  案件記錄表（連動付費）
    2.  ==律師意見回函線上填寫==
        1.  可先做
10.  與法扶內部資訊系統連接






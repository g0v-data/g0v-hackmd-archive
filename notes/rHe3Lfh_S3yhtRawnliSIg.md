---
tags: g0vernance
---
# g0v slack 治理機制討論

:::info
目錄
[TOC]
:::

源起
---
因為目前 slack 缺少治理機制，有遇到一些問題：
1. admin 無更新機制，目前名單是 2014 年延用至今
2. 免費版 slack 只能安裝 10 個 app，現在已經滿了，需要刪減機制
想藉由這份共筆擬出一個治理機制
3. [update 2021-05-22] slack 會有 custom Integrations 也佔用 app 名額，而且會佔 4 個無法刪除，因此現在能安裝的 app 要降到 5 個才安全了。

現有 admin 名單如下：
Owner: clkao, gugod, yhsiang
Admin: acechen, au, grass, ipawei, caasi, hlb, nfsnfs, ronnywang

現有 App 名單如下： (以下內容在 hackmd 上不會再更新，請參考 [Spreadsheet](https://docs.google.com/spreadsheets/d/1xg6Cb28J7IYTwonrqqBR2mQ2V1dqP3K-K9dZgLmy4mQ/edit?gid=342719512#gid=342719512))
* awesome-g0v-projects
    * 功能：在 #awesome-g0v-projects 頻道有 awesomeg0vprojects 帳號
    * 申請人：John Huang
    * 申請時間：2020-05-29
> John: 這個可以刪除。我正在做新的黑客松系統ARAY，希望可以留一個位置給ARAY~
* g0v summit 2020 (可刪除)
    * 功能：g0v summit 2020 討論區登入用 
    * 申請人：Howard
    * 申請時間：2020-05-21
* Github
    * 功能：
    * 申請人：mrorz
    * 申請時間：2020-03-27
    > 請刪除升級為新的 Github app 唷，感謝感謝 [name=mrorz]
* GitHub Enterprise Server
    * 功能：[GitHub 提供 Git 專案的線上原始碼託管服務，具備強大的協作、程式碼審查與問題追蹤功能。此整合功能會將 GitHub Issues 上的指令、提取請求和活動張貼至 Slack 中的頻道。](https://g0v-tw.slack.com/apps/A0F7YS2SX-github-enterprise-server)
    * 第一安裝人：csc（當時還未有申請機制，人人可安裝）
    * 申請時間：2015-12-31
* Google Drive
    * 功能：[可以預覽google drive的文件](https://g0v-tw.slack.com/services/BG7376L0Y)
    * 第一安裝人：claire
    * 安裝時間：2017-10-03
* 揪松小幫手 Jothon Helper
    * 功能：最早是[備份 slack 訊息](https://g0v-slack-archive.g0v.ronny.tw/)，後來擴充到 [線上揪松](https://meet.jothon.online)
    * 第一安裝人：Ronny Wang
    * 安裝時間：2018-09-14
* Matterbridge
    * 功能：同步 slack 訊息到 Mattermost instance https://chat.g0v.xyz/ ，後者由 intl 支援 pm5 管理， facing-the-ocean 正在使用
    * 申請人：superbil
    * 申請時間：2020-03-13
* Pingdom
    * 功能：
    * 申請人：k62
    * 申請時間：2020-03-30
* Trello
    * 功能
    * 第一安裝人：chloe
    * 安裝時間：2019-06-03
* Trello Alerts
    * 功能：
    * 第一安裝人：kooioao
    * 安裝時間：2018-02-05

App 相關記錄：
- slack 免費方案最多只允許安裝 10 個 apps
- slack g0v workspace 是於 2014-08 創立
- 一開始預設是設定成任何人都可以安裝 apps ，無需審核，一開始 slack 也未嚴格執行安裝 10 個 apps 的限制(因此上面有些 app 記錄不是「申請人」而是「第一安裝人」)
- 2020-03-11 由 Ronny Wang 將 workspace 設定改成安裝 app 需要在 #slack-apps 頻道公開審核，並刪除了一些舊有無人使用 app
- 2021-05-22 發現 Custom Integrations 會佔用 app 名額，因此必須要刪除到剩下 5 個 apps 才能使用


202209 admin 去留機制討論
-----------------------
因為 2022-08-28 [Isabel](https://g0v-slack-archive.g0v.ronny.tw/index/channel/C01RDCVDGHZ/2022-08#ts-1661665188.202979) 提出了 au 身為數發部長是否適任 g0v slack admin　的討論，有鑒於目前 slack 機制並未有 admin 的「被退出」機制，因此在 2022-09-03 的基礎松開啟此討論：

預計討論點如下：
1. slack admin 技術上能做什麼不能做什麼？[共筆](https://g0v.hackmd.io/xc7Ay8r_R2Wo9NqeR4NpSw)
2. 治理機制是否要加入 admin 被退出機制，如果 admin 會讓社群成員感到不安（例如特定 admin 被確認有盜用帳號竊取隱私記錄），是否可被汰除，如何被汰除？
3. 數發部部長是否是不適合的條件？什麼樣的公職會是不適合的條件？

### 相關資料
- [2022-07-20 Isabel 與 au 對談](https://sayit.pdis.nat.gov.tw/2022-07-20-isabel-hou-%E4%BE%86%E8%A8%AA#s512305)
- [為了方便討論 slack 治理機制需要如何限制 admin ，這邊想要條列在技術上 admin 能做到和不能做到的事情，以便知道需要在哪些能做到的事需要多加限制，以及當有人疑慮時，可以用已測試過確認 admin 做不到來做澄清。](https://g0v.hackmd.io/xc7Ay8r_R2Wo9NqeR4NpSw?view)

### 2022-09-03 基礎松討論共筆

## 修訂(參考g0v宣言)
- [x] 一定要在基礎松提案、討論
    - [x] 已於 2022/09/3 提案
- [x] 需要至少一個坑主
    - [x] 2022/09/3 治理機制坑主：@Ronny
- [x] 需要公開基礎松討論紀錄和任何 follow-up meeting 的討論紀錄
    - [x] 2022/9/3 基礎松討論紀錄在這份文件
- [ ] 一定要有 public review 兩週
    - [ ] 貼 #general、#jothon、#g0v-slack、Fb 後勤中心


- 移除管理員機制規範：

如3位管理員就某管理員繼續執行權限有疑慮時，可以先暫停管理員職務（技術上先移除權限）兩週，並於期間內，由社群進行正反討論及意見徵集，期間屆滿後，如管理員多數決議維持原議時，即正式移除權限，反之，則需恢復其管理員權限。

- Slack 權限層級：

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c855675878949cbeef38cbc183b08fa7.png)

- slack admin 多樣性
    - 目前admin：男性、技術人、資深參與者居多
- 數位部長：
    1. 外界觀感
    2. 對於一定層級以上的政府官員擁有權限上可做的事，是否會有參與者有疑慮？
    3. 宣言


未來目標
-------

### g0v slack admin

* 為了確保保持 app 以及 admin 的活躍度，需要有 bot 機制協助每年或每季確認 app manager 或是 admin 是否有要繼續使用，若不續用就停止的機制
* 可能需要像 sns 的隨機抽 reviewer 機制
* 目前已開設 slack 管理頻道 #g0v-slack

### app 申請/開發者

以下開放申請者自由填寫

* 為了節省 app 量，線上揪松預計要增加以下功能：
    * 可以讓大家申請後，透過線上揪松 app 在各頻道自動機器人發言的功能
* 為了節省 app 量，g0v slack 備份預計要增加以下功能：
    * 可以讓大家訂閱公開頻道的對話新增，以便做互動機器人
* 為了節省 app 量，Matterbridge 預計要增加以下功能：
    * 可以讓大家申請後，與其它 slack workspace 或 matterbridge 已支援的頻道同步訊息
    * 可以讓大家透過 matterbridge & mattermost 提供自動翻譯 bot

內容討論
-------

### 各類筆記區

#### [注意] slack 一個註冊連結每註冊滿 400 人就會失效

- 需定期更新
- 更新紀錄：
    - 20240424 Ronny

#### Slack Pro - Connections 功能 - 特點筆記
- g0v Slack Pro - Connection 建立紀錄：
    - 2023.03.22，由 chewei 操作
        - 連接「Code for All Slack #events 頻道」
        - 建立「g0v Slack #events-code-for-all 頻道」
            - 頻道名稱可以自訂
            - 加入網址：https://join.slack.com/share/enQtNDk3Mzg0NTM4NDAwNy01MDRlMDFmYTk4NWRkMmNlMjc1YTZkZWVkN2UxYWYwY2Y0Y2VkNGM4ZThlOWQ4OWQwZjFhMzFiNzg4MjZmYTky 
    - 功能筆記
        - 需要兩邊都是 Slack Pro 版本，才能維持 Connections Channel
        - 雙邊的 emoji 會同步顯示與計數，且兩邊各自上傳的 emoji 素材庫，也會同步 😱

#### Slack Bot 引導新參者的案例

g0v slack 歡迎訊息，草稿共筆文件
- https://g0v.hackmd.io/@jothon/S1pZe539_

其他公民科技社群的 Slack 歡迎訊息
- 案例共筆：https://g0v.hackmd.io/5oqT3zO8Rdq_pX46h7fEig
- Code for All
    - 第一則訊息：
        - 引導使用者前往「自我介紹頻道」
        - 明確提供 code of conduct 文件網址，並提醒使用者注意 code of conduct
        - 若遇到騷擾或其他疑問，訊息中有提供 Core Team 成員暱稱，可私訊 Core Team 成員，也有一個匿名表單可填寫
        - 提供官網網址
        - 提醒使用者 @channel is disabled
    - 按下 I want to learn more 按鈕
    - 第二則訊息
        - 提供 most popular channels
        - 提供 Communities of Practice (CoPs) channels
        - 也告知使用者，可以自己建立頻道
- Code for Japan
    - 第一則訊息
        - 提供共通頻道們，傳送門與一句話簡介
            - #01_general Code for Japanからのお知らせをお届けします
            - #02_introduction 新規メンバーの紹介をします
            - #03_events シビックテックに関するイベント情報を知ることができます
            - #04_join_project プロジェクトの参加メンバーを募集しています
            - #05_flyinghigh 嬉しいこと、感謝したいことを共有する場です
            - #06_random 参加メンバー全員が自由にお知らせをできる場です
            - #07_questions 何か分からないことがあれば、質問ください
            - #08_photos イベント活動の様子などを紹介しています
        - 提醒使用者請勿使用 @here、@everyone、@channel
    - 按下「フォームを開く」
    - 跳出輸入框，請使用者填寫以下自我介紹問題簡答
        - 問題有以下：
            - Code for Japanを知ったきっかけ / いつ頃からCode forに関わっていますか？
            - あなたの普段の活動、お仕事
            - 拠点とされているエリア
            - あなたの興味あること / 関心ごと
            - ご自由にメッセージをどうぞ(選填)
        - 送出後，不確定是在哪邊顯示？
    - 第二則訊息
        - 提供 Code for Japan 兩個熱門頻道傳送門附上頻道人數 

#### ChatGPT app for Slack

- 共筆：https://g0v.hackmd.io/jtzzoJ9rQhy2rBfwJuhWXA?view


#### g0v Slack 使用者閱讀完畢的系統稱讚語句
- https://g0v.hackmd.io/N6bGxyqSRZaAnNSmBevZVg?view


---

# g0v slack 治理機制總章

## 通過和修訂(參考g0v宣言)
- [x] 一定要在基礎松提案、討論
    - [x] 已於 2021/05/22 提案
- [x] 需要至少一個坑主
    - [x] 2021.05.22 治理機制坑主：@Ronny
- [x] 需要公開基礎松討論紀錄和任何 follow-up meeting 的討論紀錄
    - [x] 5/22 基礎松討論紀錄在這份文件
- [ ] 一定要有 public review 兩週
    - [ ] 貼 #general、#jothon、#g0v-slack、Fb 後勤中心

## 說明
- g0v slack 治理機制的目的：g0v slack 是社群運作的重要工具，涵蓋參與者彼此的溝通，或是運用 slack 系統進行專案相關開發，故建立管理機制以因應工具相關事務。
- 管理模式說明：
(1) 任何人使用 g0v slack 皆必須認同 [g0v 行為守則（CoC）](https://g0v.hackmd.io/s/COC)
(2) 設置「管理員」，並搭配「更新機制」
(3) 設置 g0v-slack 頻道，提供管理員及社群成員參加，並於此推動治理機制討論與工作
(4) 建立 slack app 管理機制

## (1) 行為守則

### 帳號註冊與內容表達
- 任何人只要同意 [g0v 行為守則 g0v Code of Conduct](/s/COC) 皆可透過 https://join.g0v.tw 註冊帳號
- 行為守則規範涵蓋：
    - 個人帳號暱稱與顯示名稱
    - emoji 
    - 貼文內容 (文字、圖片、影片、檔案)
- 若違反 CoC，管理員可刪除其留言或停用其帳號
- 若發現違反 CoC 的行為，每一位社群參與者皆可進行勸導，若勸導無效，可於 #g0v-slack 頻道提報處理

### 頻道創立
- 任何人皆可創立頻道
- 頻道宗旨與設立目的，若違反 CoC，管理員可刪除其頻道

## (2) 管理員

### 管理員更新機制
- 管理員由現有管理員邀請制加入 (2021.03 共有 11 位)
- 需在共筆公開現有管理員名單
- 管理員需要每年確認是否有留任意願
- 需有公開頻道公告管理員更新，以及管理員進行管理員動作的記錄
- 若累積三次未執行管理員職務，在無其他管理員反對下將解除管理員身份。
- 違反ＣＯＣ跟本文件，經過Ｎ個管理員決議解除管理員職務。
> 需要*被*退出機制嗎? [name=pm5]

## (3) app 管理機制

### app 管理機制
- 免費機制下最多僅能安裝 10 個 app，Custom Integrations 佔用 4 個 app ，因此只能額外安裝 6 個，為了預留可以更新既有 app 空間，最多只允許安裝 5 個。
- app 分為既有 app 及自行開發 app （既有 app 為 slack app directory 內已經 slack 認證之 app ，如 Google Drive, Trello, Pingdom, Github ... 等，自行開發則是為了社群目的另外開發，如線上揪松、g0v summit 2020 ... )
- app 需要申請人，申請人需要至共筆文件中(待建立)填寫以下資訊
    - 申請人
    - 申請目的
    - 預計申請期間（可為限期或永久）
    - 相關程式碼（若為自行開發 app ，需要開放原始碼）
    - 若開發中，預計開發多少
    - 使用資料範圍
- app 申請需要在 slack 上超過 10 人透過 emoji ++ 連署
- 如果自行開發 app 需開源
- app 申請人需要加入 slack 管理頻道 #g0v-slack，並且每季需要回報該 app 是否繼續再使用或預計開發進度說明，若無使用將會解除安裝其 app 將額度留給其他服務
> 這裡的機器人是哪個機器人? [name=pm5]
> 這邊我會使用「揪松小幫手」的名額來開發此功能 [name=ronny]
> 在揪松小幫手的名額上增加這個功能，可以節省 app 數，立意良好。但我有點擔心這樣會讓 slack admin 與揪松團的關係不明確。可以請 slack admin 們同意請揪松團協助開發此功能，並留下文字記錄嗎？[name=pm5]
> 我同意 pm5 的說法，一開始機器人開發前可能先用 [google spreadsheet](https://docs.google.com/spreadsheets/d/1xg6Cb28J7IYTwonrqqBR2mQ2V1dqP3K-K9dZgLmy4mQ/edit#gid=342719512) 工人智慧的方式處理，等後續需求較多時再改用機器人處理，改用機器人時需得到 admin 的同意。我覺得上面 wording 可能也要先拿掉「機器人」三個字，讓 admin 可以自行決定確切作法。[name=ronny]
- 若有緊急需求但已無 app 空間，經超過半數管理員同意後，可提早進行與 app 申請人確認是否繼續使用的動作
- 若無 app 願意解除安裝，將由管理員決定保留及解除安裝之 app ，管理員需用以下因素判斷
    - 是否可以同時給多個專案使用
    - 上線後使用頻率
    - 對社群和社會的影響力
    - 社群成員意見
    - 在不滿10個app的狀況下，只要不違反COC就可以使用。
> 我覺得判斷一個 Slack bot 能不能裝的一個評判基準可以是有沒有辦法讓不同的專案共用 [name=ael]
> 
> 我先在自己的 workspace 實驗看看能不能共用一些大家都想要的權限，例如 conversations(channels) list 和 users list [name=caasih]
> 

## (4) 治理機制上線流程
- 預計在 2021-06-22（？） 基礎松後一個月內完成治理機制上線
- 需在 #general 公告本治理機制草案，收集意見
### admin 更新機制
- 現有 admin 需要在 2021-06-15（？） 以前在 #g0v-slack 表達留任意願，若不留任直接取消
- 需要在 #g0v-slack tag 各位 admin ，確保 admin 有在 slack 得知此份治理機制上線
### app 汰除機制
- 若對現有 app 有需求的使用者，需在 2021-06-15（？） 以前在 #g0v-slack 表達意見，若無人提出則直接解除安裝
- 需要在 #g0v-slack tag 各位 app 的安裝者，確保 app 的使用者有確認到本治理上線
- 原申請人無回應續用 app 或決定不續用，但有其他人有意願，可接手成為申請人
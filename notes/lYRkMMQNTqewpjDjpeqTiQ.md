---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210407 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, 文武
:::

## :potable_water: Release pipeline

### :star: Released to production

#### 🗄️ rumors-db

- [Schema versioning mechanism](https://github.com/cofacts/rumors-db/pull/53)

### :rocket: Staging

#### :electric_plug: API

[DIFF](https://github.com/cofacts/rumors-api/compare/0c42992c82eb25851433f3f275b663eef84defab...7e05f572452c9d00ce1df5ebcb78f28c972dadc1)

- [#254 Google & IG login](https://github.com/cofacts/rumors-api/pull/254) [name=nonumpa]
- [#252 Slug validation API](https://github.com/cofacts/rumors-api/pull/252)
- [#255 Graph API v10](https://github.com/cofacts/rumors-api/pull/255)
- [#253 Update DB schema](https://github.com/cofacts/rumors-api/pull/253)

#### :globe_with_meridians: Site

##### Bugfixes

- [#422](https://github.com/cofacts/rumors-site/pull/422) Infinite redirect on mandarin slug

DB fix should fix the following bugs:

- [#399 slug](https://github.com/cofacts/rumors-site/issues/399)
- [#386 user does not exist](https://github.com/cofacts/rumors-site/issues/386)

##### Testing checklist

http://dev.cofacts.org/

- [x] Test if FB login works
- [x] Test if user are blocked from using slugs with URLs components like `/` or `#`.
- [x] Test if #399 can no longer be reproduced
- [x] Test if #386 can no longer be reproduced

##### 未竟之處
- [x] Google, IG 要取使用者 email 的 scope，才能 merge accounts
    - https://github.com/cofacts/rumors-api/pull/256
- [x] 藏起 IG login button
    - https://github.com/cofacts/rumors-site/pull/424
- [ ] Login button color - 再用 figma 配個色 https://github.com/cofacts/rumors-site/issues/427

## Devs - Q2

- [x] 修復 iOS 登入
- [x] Slug unicode support 
- [x] [Google sign-in](https://github.com/cofacts/rumors-api/issues/234) [name=nonumpa]
- [ ] 驗證使用者 slug
- [ ] 評分回應 profile page tab
    - [ ] 圖：https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/Cofacts-website-MrOrz-s-copy?node-id=2923%3A220
- [ ] 4 月初：公開 profile page 
    - [ ] revert the PR that [hides profile](https://github.com/cofacts/rumors-site/pull/378)
    - [ ] 補充的人的 profile / 名字（figma 已有，開票）
- [ ] Dockerize rumors-line-bot
    - nodejs + tesseract base image + 2-stage build
    - [ ] 然後放到 AWS 用 [ECS](https://aws.amazon.com/tw/ecs/features/) 管 （[estimated pricing](https://docs.google.com/spreadsheets/d/1m_9UeSsSvwX-tFF1Uw2W-7pXie-n1_6bP99TUEFeQ6o/edit?usp=sharing)）


### Postponed

- [ ] 4 月初：deploy API header 讓第三方接取 [name=mrorz]
- [ ] apply 日文翻譯 --> ja.cofacts.org / ja.cofacts.tw
- [ ] [LINE bot 送出流程改版](https://github.com/cofacts/rumors-line-bot/issues/214)
    - 目標：更簡單地送出流程、LIFF 不要 send message to chatroom (為 share dialog 做準備)

## 4/14 會議調整

4/13 (二)？4/15（四）？
4/15 是台南崑山大學場

:::success
4/13 週二晚上開會
:::

## Thought on branching

rumors-line-bot: 想要維持，因為 heroku 直接追蹤。

但 rumors-site 想要只留 master branch。
- 雖然 docker hub 會 follow master & dev，但其實應該只要 follow 最新
- 手動 deploy
- 現在 deploy 也都是 master fast-forward 到 dev 所在之處，沒必要開兩個 head

:::info
再看看
:::

## 4/10 小聚 rundown

- [x] 問酒精、體溫誰負責 [name=bil]

松菸創作者工廠有酒精跟額溫槍
當天報到二樓門會打開開
進來的人會噴酒精跟量額溫

---

- 週三會議
    - [x] 發布 LINE 推播 --> 週四 8 pm schedule
    - [x] 換 rich menu
- 週五早上
    - [x] KKTIX 行前通知：提醒時間、筆電
    > Hello 你好，
	>
	> 明天就是 4 月 10 日的編輯小聚囉！
	> 編輯小聚需要大量查詢資料，請自備筆電 💻 與充電器 🔌。
	>
	> 時間：4/10（六）14:00
	> 地點：AIC 美國創新中心 - 松菸創作者工廠 / 110台北市信義區光復南路133號2樓 松菸創作者工廠內
	> 可以從市政府站 1 號出口右轉直直走，進入松菸內後上二樓(走路時間約10-15分鐘)
	> 
	> 費用全免，會很準時開始。
	> https://www.facebook.com/groups/cofacts
	> Cofacts 編輯 VIP 臉書社團在這裡，請先加入吧＝Ｄ說你會來編輯小聚優先加入（真的）
	>
	> 感謝你的閱讀。
	>
	> 那麼明天見囉😊
	>
	> 比鄰敬上
    - [x] 開場使用材料更新：https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit
    - [x] 準備空 Spreadsheet + 上 bit.ly 短網址
    	- [x] https://bit.ly/cofacts24-1 （[樣板檔](https://docs.google.com/spreadsheets/d/1K_2WYW-yZ2gbQbFteJxNfrx9xKHBtKbq6ejsuZ2B8OU/edit#gid=0)）
    	- [x] https://bit.ly/cofacts24-2 （[樣板檔](https://docs.google.com/spreadsheets/d/1j75M_qh7s1JE0hUx3YQHN6-ncL6u2gMCdoHfm1sweeI/edit#gid=0)）
	- [x] 準備 Slido `#cofacts24`
		- [x] 放投影片網址 + spreadsheet 1
- 攜帶
	- [ ] 貼紙 - bil
    - [ ] 食物 - bil 帶餅乾
    - [x] 簽到單 - orz
    	- [x] sticky note
    	- [x] pen
	- [x] 黏土 - orz
    - [x] 編輯小聚的牌子 - orz
    - [x] Wifi 機 - mrorz
        - [x] Netgear 本體
            - [x] usb type-c 充電線與插座
            - [x] 電池
            - [x] 4G 天線
        - [x] Asus RT-N12
            - [x] 電源線
            - [x] 5dBi 天線
            - [x] RJ45 線
- 13:00 - 場佈
  - [x] 樓下貼好按開門的 sticky note
  - [ ] 簽到
      - 要給每個人指定一個 **1 ~ 25 的號碼，分工要用**
  - [x] 排桌子椅子
  - [x] 麥克風
  - [x] 引導牌
  - [x] Slido - 白紙寫 slido room number `#cofacts24`
  - [x] WIFI
      - [ ] 貼 SSID
  - [x] 產生「有回過、沒 feedback」 spreadsheet
      - 每人 20 篇
      - 25 人
      - 只產出 `repliedButNotEnoughFeedback` 的網址
    - [x] 匯入進 https://bit.ly/cofacts24-1
  - [x] 產生「沒回過」spreadsheet
      - 每人 10 篇
      - 25 人
      - 只產出 `newest, mostAsked` 的網址
    - [x] 匯入進 https://bit.ly/cofacts24-2
  - [ ] WIFI
      - [ ] 佈機x2
      - [ ] 連結 netgear 與 asus WAN port
      - [ ] 白紙寫 SSID Cofacts meetup(_5G) + wifi password 貼牆上
      - [ ] 192.168.2.1 進入 netgear admin 看 asus 的 IP
      - [ ] 開好兩台 router admin 監測連網狀態
      - [ ] (optional) netgear 換成 5GHz only?
  - [x] 投影的電腦開好：
    - [x] browser tab: [投影片](https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit)
    - [x] browser tab: [Instant](https://cofacts.github.io/community-builder/#/bignum?start=2021-02-21T14%3A00&panels=replied&panels=feedback)
    - [x] browser tab: [KKTIX](https://cofacts.kktix.cc/events/cofacteditor23)
    - [x] browser tab: [Slido admin](https://admin.sli.do/event/8v46trhh/questions)
    - [x] browser tab: [Slido](https://wall.sli.do/event/8v46trhh?section=68e498f2-c951-421f-b5b0-80c20f3f6b44)
    - [x] browser tab: [開場影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs)
    - [x] BGM
- 14:00 - 14:20 開場
    - 先放[影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs) 8min
        - 血多、台灣吧、圖文不符、闢謠編輯現身
    - 場地介紹、Slido 、Cofacts 機器人系統簡介
- 14:20 - 14:40：介紹 mission 1 - 按讚
    - 介紹「幫回應按讚」的用途，以及怎麼做；什麼樣的回應可以按「有用」、哪些可以跳過、哪些真的母湯要按「沒用」，如何就事論事的給 feedback
- 14:40 - 15:00：按讚時間
    - 讓大家從 Slido 打開 spreadsheet 1，直接點進自己號碼的那個 sheet
    - 然後幫每一篇按有用或沒用
- 15:00 - 15:30 休息、自我介紹、交流
    - 閒聊「看到覺得最好的回應、覺得哪裡好」
- 15:30 - 15:50：介紹 mission 2 - 寫新回應
    - 如何找全文、拆解回應、附出處
- 15:50 - 16:30：挑回應來回
    - 大家從 Slido 打開 spreadsheet 2，直接點進自己號碼牌的那個 sheet
    - 先挑選「一篇」覺得最有興趣的回
    - 回完之後如果行有餘力，再挑一篇
    - 如果都覺得不想回，去「等你來答」挑，不要硬回 XDDD
- 16:30 - 17:00：閒聊時間
    - 讓大家講感想
    - 介紹 RSS、文章列表、filter 功能
    - 最後拍合照

## 防詐顯名

- 標題與按鈕文字是要求顯名的一部分，不然會跟其他 bot 不同
- 按鈕 URI 也是顯名的一部份。
    - 並不是競品的關係
    - 我們的顯名規定讓資料可以回流、造成正循環。使用開放資料就應該要遵循此顯名規定
    - (1) 導向到 Cofacts LINE bot 可以使新訊息回流，美玉姨實作此 URI action 後，有相當顯著的效果；(2) chatbot 會推播新的回應給使用者，即使一則訊息還沒有回應，也可以透過 Cofacts 推播讓使用者得知最新回應。由於網站沒有上述二功能，因此導向到網站並沒有此效果。

:::info
bil 回信
:::

---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20230705 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, Dennis, mrorz
- 線上出席：4000, nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: Collab
https://github.com/cofacts/collab-server/releases/tag/release%2F20230629

#### :electric_plug: API
https://github.com/cofacts/rumors-api/releases/tag/release%2F20230629

#### :globe_with_meridians: Site
https://github.com/cofacts/rumors-site/releases/tag/release%2F20230629

## 大松檢討

> https://g0v.hackmd.io/@cofacts/meetings/%2FUpvWnVNKREmzgS1jmy3-0A%3Fview

- 7/1 忘記影像記錄 [name=bil]
  - 因為坑主要講話，所以如果要拍坑主與參與者對話，需要第三人協助拍攝

## CCPRIP

### [Comm layer] 逐字稿

> https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ
> [name=nonumpa]

#### History v.s. API

- History 下週

#### UI
> 我覺得無論有無逐字稿，都可以把圖片固定同一邊（這樣視覺上應該會比較統一 [name=maxchiu1234]
> 有逐字稿的影片在可疑訊息列表顯示，文字右側接圖片的地方太密了，希望能有間距 [name=cai]
- 知道怎麼改 [name=nonumpa]

> 逐字稿使用者可以打很多斷行，撐開版面，不太好 [name=4000]
- 如果逐字稿很長，那在寫回應的時候要拉很遠 [name=4000]
- 有注意到逐字稿會被視為一篇文章，覺得合理
- 逐字稿可以斷行其實是 feature [name=nonumpa]
  - 文章中間有斷行 OK
  - 如果連續斷很多行，這樣不太好
  - 可以做到如果有連續斷行，就只斷一個
- 或許逐字稿可以折疊就行 [name=mrorz]

> 逐字稿位置不方便邊打邊比對的缺點，有辦法弄成另開可以移動的小視窗去輸入逐字稿嗎？(PC限定) [name=cai]
- 桌機版瀏覽器如 Firefox 可以把影片開成 picture-in-picture [name=mrorz]![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_aaadb1be1a3eb0bd0b870f9449a4acb7.png)
  - 影片子母畫面可以解決 [name=cai]

:::success
nonumpa 開票與實作
:::

#### AI
> https://g0v.hackmd.io/@cofacts/rd/%2Fwkx286lmTDaFUpgRhnUawQ

Code touchpoints
- `ListArticles(filter: {mediaUrl})`:
  - 目標為取得 media 的 text，進行 `more_like_this`。
  - 取得 text 有多層 cache:
    1. 從 `queryInfo.id` 找相近 media hash 的 articles.text：經過 crowed-source 修正的逐字稿。
    2. 若 1 無結果，至 `queryInfo.id` 找相對應的 airesponses：取得 AI 逐字稿。若影片或圖片無文字，至少應該也有一個 airesponses 的 `text` 是空的。
    3. 若 2 沒有任何 airesponses，就去呼叫 third-party API (OCR or STT) [建立新的 ai response](https://g0v.hackmd.io/wkx286lmTDaFUpgRhnUawQ#The-AI-responses).
       - 重複利用 ai reply 的 [awating LOADING logic](https://github.com/cofacts/rumors-api/commit/44aeba1c0ce2a297ceb9c184a47e14240284ead8)
       - 此為建立 media hash 與 transcript 關聯（ai response 文件）的主要管道——使用者用 LINE bot 進行查詢時，都會自動進行文字辨識
       - 可用一個 boolean argument 決定是否要 cerate ai response。可以控制只有特定的 app 可以開啟這個 boolean argument
  - mediaUrl 跟 text 都放進 `shouldQueries`
  - 類似 `Article` type 的 `relatedArticles` 的現有邏輯

- `CreateMediaArticle`
  - 同樣需要取得 media 的 text，但行為一致
    - 通常 `CreateMediaArticle` 前會先 `ListArticle`，可預期大部分 `CreateMediaArticle` 應有 airesponse 可取用 AI 逐字稿
  - 建立 Y doc 並寫入 article text ==BLOCKED by collab API==
    - 但還沒做的話，也只是 AI 逐字稿沒辦法拿來 crowd-source 而已，不影響 airesponse 機制運作

### [Op layer] API management

- Focus on Cofacts website first
- SSR + authenticated info with tokens [name=thistle@g0v-hackath56n]
  - 但目前使用者的 nextjs 版本很舊，SSR 與 client render 的邏輯是共用的
  - landing SSR 的東西，在點擊到下一頁時會用 client render 的方式取東西
  - 若拆開：要從 API 拿資料的都改寫到 `getServerSideProps`
  - 要拆開不如升級 next.js 用 React server component 重寫⋯⋯
- 可能還是在 rumors-site proxy login + graphql + [persisted operation](https://the-guild.dev/graphql/yoga-server/docs/features/persisted-operations)
- Skill-set: 要熟 GraphQL server + NodeJS server + apollo client react。NextJS / Typescript 其次。
- 希望年底（11/30 以前）開發完成 or (2023/09 ~ 2024/2/E)

:::info
Johnson: 
- update https://g0v.hackmd.io/@cofacts/rd/%2Fj27XFAQ0R0Cuqi2jDLJuWw & design choice
- 準備 JD
  - 期中: login + 1 endpoint 可以打 API
  - 期末：UI 可以正常運作
Bil: 確認 budget
nonumpa：沒有把握

----

Whisper code change: ~11/30
Cloudflare / API: 2024/Feb
:::

## 基隆小聚 rundown

- [x] 地點：
  - 2023/7/9 (日) 2pm - 5pm
  - [金豆咖啡](https://goo.gl/maps/nzJ2Zm6T63aS4n8T7)
- [ ] 食物？統編？現場飲品
- [ ] 場地費：2500
- [ ] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Slido 暖身
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息（詢問拍攝）
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：雙北基隆宜蘭
- [x] KKTIX:https://cofacts.kktix.cc/events/cofactseditor36
- [ ] 誰會來呢：bil, (nonumpa), mrorz, dennis
- [ ] 記得帶：貼紙、環保杯(飲料8折)
- [ ] LINE 文案: 用過TPASS了嗎！！搭起來真的很划算，可以一起來基隆看看港都，從台北出發也只要半小時喔！這是一場免費的志工培訓工作坊，和 Cofacts 真的假的 用一個下午的時間對抗假訊息，小小公民面向資訊戰的最前線。
時間：2023年07月09日（日） 14:00-17:00
地點：金豆咖啡 基隆市仁愛區忠三路75號2樓 (活動當天可帶外食)活動參與者自備環保杯的話飲料 8 折。
誠摯邀請您的參與＝Ｄ

----


- 週三會議
    - [x] 週四 8 pm schedule
    - [x] 換 rich menu
- 週六早上
    - [x] KKTIX 行前通知：提醒時間、使用電腦而非手機
    > Hello 你好，
	>
	> 明天就是 7 月 9 日的志工培訓囉！
	>
	> 志工培訓需要大量查詢資料，請自備筆電 💻 與充電器 🔌 並帶著愉快的心情來參加。帶順手的平板也可以的！如果願意協助聽打影片字幕，請自備耳機唷🎧  ！
	>
	> 🕒 時間：07/09（日）14:00
	> 📍 地點：基隆市仁愛區忠三路75號2樓 金豆咖啡
	> 
	> 費用全免，會很準時開始。
	> 
	> Cofacts 真的假的 查核協作 VIP 臉書社團在這裡 👉 https://www.facebook.com/groups/cofacts
	> Cofacts 真的假的 查核協作 Discord 在這裡 👉  https://cofacts.tw/discord
	> 說你會來查核小聚優先加入 ＝Ｄ
	> 
	> 感謝你的閱讀。
	>
	> 那麼明天見囉😊
	>
	> 比鄰敬上
    - [x] 開場使用材料更新：https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit [name=mrorz]
	- [x] 準備 Slido `#cofacts36`
		- [x] 放投影片網址
    - [x] 幫 Netgear 充電
- 當日準備 / 攜帶
    - [x] 樓下用的標語
    - [x] 貼紙 - bil
    - [x] 黏土 - orz
    - [x] 延長線 x 1 - mrorz
    - [x] 編輯小聚的牌子 - orz
    - [x] Wifi 機 - mrorz
        - [x] Netgear 本體
            - [x] usb type-c 充電線與插座 （已充飽電，無需插座）
            - [x] 電池
            - [x] 4G 天線
        - [x] Asus RT-N12
            - [x] 電源線
            - [x] 5dBi 天線
            - [x] RJ45 線
- 13:15 - 場佈
  - [ ] 簽到
  - [ ] 排桌子椅子
  - [ ] 麥克風
  - [ ] 延長線佈置
  - [ ] 門口黏引導牌
  - [ ] Slido - 白板寫 slido room number `#cofacts37`
  - [ ] WIFI
      - [ ] 佈機x2
      - [ ] 連結 netgear 與 asus WAN port
      - [ ] 白紙寫 SSID Cofacts meetup(_5G) + wifi password 貼牆上
      - [ ] 192.168.2.1 進入 netgear admin 看 asus 的 IP
      - [ ] 開好兩台 router admin 監測連網狀態
      - [ ] (optional) netgear 換成 5GHz only?
  - [ ] 投影的電腦用 google chrome 開好
    - [x] Google Chrome tab: [投影片](https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit)
    - [x] Google Chrome tab: [Bignum](https://cofacts.github.io/community-builder/#/bignum/setup)
    - [x] Google Chrome tab: [KKTIX](https://cofacts.kktix.cc/events/cofactseditor34)
    - [x] Google Chrome tab: [Slido admin](https://app.sli.do/event/tEukhBqJ2wwcVx9WgRaFkb)
    - [x] Google Chrome tab: [Slido](https://wall.sli.do/event/tEukhBqJ2wwcVx9WgRaFkb?section=6e3063a1-a3cf-429a-b87d-f2a39f0645e6)
    - [x] Google Chrome tab: [開場影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNVuJ9S-In4k93trnO_D2s6R)
    - [ ] BGM
    - [ ] Analytics
- 14:00 - 14:20 開場
    - 放[長影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs) 8min
    - 場地、Slido、Cofacts 機器人系統簡介
- 14:20 - 14:40：引導註冊網站、介紹評價現有回應
- 14:40 - 14:50：實作評價
    - 讓大家從網站找訊息按讚
    - 提醒 15:00 結束時會問大家有沒有想要分享的心得
- 14:50 - 15:10 介紹補充資訊
- 15:10 - 15:40 實作補充資訊、自我介紹、休息
    - 閒聊「看到覺得最好的回應、覺得哪裡好」
- 15:40 - 16:10：介紹撰寫新回應
- 16:10 - 16:40：實作撰寫新回應
    - 大家從網站挑選「一篇」覺得最有興趣的回
- 16:40 - 17:00 介紹 RSS、社群、合照

## 影片拍攝

- 5min 影片，2023/11/30
- 如果拍得好再公開即可
  - mrorz + dennis 雙機拍攝
  - bil 訪談打字
  - 第三方要用的話，再去問問影片裡的人再問
- COSCUP 需要紀錄（RightsCon）
- 短影音行銷

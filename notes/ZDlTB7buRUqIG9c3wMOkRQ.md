---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20230913 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz
- 線上出席：cai, nonumpa, 4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

- DB: https://github.com/cofacts/rumors-db/pull/66
    - Has run reindex script
- API: https://github.com/cofacts/rumors-api/pull/316
- Site: https://github.com/cofacts/rumors-site/pull/545
- Collab-server: https://github.com/cofacts/collab-server/pull/4
    - Has run migration script

#### :globe_with_meridians: Site
##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：
- [x] 不可編輯逐字稿

登入自有帳號後檢測：
- [x] 可載入逐字稿
- [x] 可編輯逐字稿
- [x] 可見編輯紀錄

##### ⛔️ Release Blockers



##### 未竟項目


### :eye: Under review

## CCPRIP

### [Comm layer] 逐字稿
> https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ
> [name=nonumpa]

#### History
> [name=nonumpa]

- 今晚 release
- unit test / monorepo 整理

#### AI

##### API 寫入 ydoc
> Design doc https://g0v.hackmd.io/wkx286lmTDaFUpgRhnUawQ#CreateMediaArticle
> Related discussion on 2023/8/2: https://g0v.hackmd.io/0tPABSZ6SRKswBYqAc1vZw#API
> [name=mrorz]
> 

繼續完成 https://github.com/cofacts/rumors-api/compare/master...write-ai-transcript

#### Auth
> [name=mrorz]

No progress yet

## 小聚 rundown

- 週三會議
    - [x] 週四 8 pm schedule
    - [x] 換 rich menu
- 週六早上
    - [x] KKTIX 行前通知：提醒時間、使用電腦而非手機
    > Hello 你好，
	>
	> 明天就是 9 月 17 日的志工培訓囉！
	>
	> 志工培訓需要大量查詢資料，請自備筆電 💻 與充電器 🔌 並帶著愉快的心情來參加。帶順手的平板也可以的！如果願意協助聽打影片字幕，請自備耳機唷🎧！
	>
	> 🕒 時間：9/17（日）14:00
	> 📍 地點：台中市西區民權路53巷10號 好民文化行動協會
	> （可由民權路的「植作茶」飲料店旁的窄巷進入）
	> 
	> 費用全免，會很準時開始。若不克前往，記得取消報名 :)
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
    - [ ] 開場使用材料更新：https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit [name=mrorz]
	- [x] 準備 Slido `#cofacts38`
		- [x] 放投影片網址
		- [x] 測試問卷：https://forms.gle/9yHxkHWaxq3LU7MX8
    - [x] 幫 Netgear 充電
- 當日準備 / 攜帶
    - [x] 樓下用的標語
    - [ ] 貼紙 - bil
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
- 13:30 - 場佈
  - [ ] 簽到
  - [x] 排桌子椅子
  - [ ] 麥克風
  - [x] 延長線佈置
  - [x] 門口黏引導牌
  - [ ] Slido - 白板寫 slido room number `#cofacts38`
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
    - [x] Google Chrome tab: [KKTIX](https://cofacts.kktix.cc/events/cofactseditor38)
    - [x] Google Chrome tab: [Slido admin](https://admin.sli.do/event/kWWAt4BkwvTALXq2rUHhdT/)
    - [x] Google Chrome tab: [Slido](https://wall.sli.do/event/kWWAt4BkwvTALXq2rUHhdT?section=f1e2a4af-a89b-476a-a561-b7895115fff5)
    - [x] Google Chrome tab: [開場影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNVuJ9S-In4k93trnO_D2s6R)
    - [x] BGM
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

---

其他台中空間
- 好伴 https://www.happen.tw/space [name=cai]

- 跟好民確認 [name=bil]
  - 延長線：都有
  - 桌子數量、擺放:最舒適是14人，已約定桌子
  - 樓下是否可以貼導引牌：活動在一樓，都可以貼，也會借我們畫架跟白板

## 下週開會

9/20 https://blindegg.kktix.cc/events/202309gai
:::success
移到 9/21 (四) 8pm
:::

## Oslo 自由論壇
> 10/18 (三)
> 背板要放的資訊

1. Cofacts, also known as "真的假的", is the first open-source, crowd-sourced fact-checking chatbot in the world. It supports text, image, and video messages, utilizing both crowd and AI-powered text recognition and transcription to compare with hundreds of thousands of internet-transmitted texts and multimedia messages in its database. This results in a crowd-sourced fact-checking response. As a civic tech community, Cofacts not only hosts regular fact-checking meetups and media literacy lectures, but also provides open data research and fact-checking chatbot development toolkits. These resources assist everyone in effectively combating fake news.

Cofacts 真的假的 是第一個提供開放原始碼與群眾協作的事實查核聊天機器人，支援文字、圖片與影片訊息，具備群眾與 AI 協作的文字辨識與逐字稿，比對資料庫中的數十萬則網傳文字與多媒體訊息後，回傳群眾協作的查核回應。真的假的 公民科技社群除了有定期的事實查核聚會、媒體識讀講座、也提供開放資料研究與事實查核聊天機器人開發教學工具包，協助所有人對抗假新聞。

5. Social media:
website : https://en.cofacts.tw/
Instagram / X: cofacts.tw
Facebook: https://facebook.com/cofacts.tw
LINE：https://line.me/R/ti/p/%40cofacts
LINE id @cofacts 

6. Goal: ~~Cofacts hopes to influence more participants to be devoted to contributing to the civic tech community, and to help reduce the information gaps within society. We are eager to have global cooperation to help international partners to combat disinformation via technology tools.~~

Cofacts aims to encourage more individuals to actively contribute to the civic tech community, with the goal of bridging the information disparities within society. We are fervently seeking worldwide collaboration in assisting international partners in the fight against disinformation through the use of technology tools.

7. Call to action: 

~~Add the chatbot as a contact and chat with it, or add the chatbot to your 100 members close chat, Cofacts will fact check for you inside the chat room. Cofacts held fact-check workshop regularly. The participants would be invited to understand the fact-checking chatbot's system, and to experience how to contribute to the civic tech chatbot via simple steps. Upon completion of the tasks, they'll receive little gifts - such as stickers, snacks, and thank you cards.~~

You can either add the chatbot as a contact for one-on-one interactions or integrate it into your private chat encompassing 100 members. Cofacts will perform fact-checking for you within the chat room itself. Additionally, Cofacts routinely conducts fact-checking workshops. These sessions provide an opportunity for participants to explore the fact-checking system of the chatbot, and to learn how to contribute to this civic-tech chatbot through simple steps. Upon accomplishing the tasks, participants will receive appreciation gifts, such as stickers, snacks, and thank-you cards.

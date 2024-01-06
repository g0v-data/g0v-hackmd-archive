---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20231115 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz, nonumpa, T
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

- [1] [Simplify postback handler signatures #372](https://github.com/cofacts/rumors-line-bot/pull/372)
- [2] [simplify text handlers as well #371](https://github.com/cofacts/rumors-line-bot/pull/371)
- [3] [Move selectedArticleId from context to action payload #369](https://github.com/cofacts/rumors-line-bot/pull/369)

#### :robot_face: rumors-line-bot

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [ ] 應可送出「全新訊息」
    - [x] 問訊息來源時選擇「我自己打的」會被擋下。
    - [x] 選擇「整篇轉傳」後會詢問是否要送出訊息。
    - [x] 不同意送出訊息後可以收到感謝。
    - [x] 同意送出訊息後就會送出訊息，並得到：
        - [x] Cofacts article page 按鈕
        - [x] 寫理由的按鈕
        - [x] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面
        - [x] 「分享到 Facebook」、「分享到 LINE」且可以正常運作
    - [ ] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [ ] 可以再打開理由視窗，此時會載入上次填寫的理由。修改理由送出後，查看 article page 看理由是否有被送出。

- [x] 送出「沒回應」的舊訊息，應可送出新理由
    - [x] 文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。
    - [ ] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [ ] 可以修改理由送出。查看 article page 看理由是否有被送出。
    - [ ] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應
    - [ ] 選擇回應之後可以幫回應 upvote --> 壞掉
    - [ ] 可以再次選擇 downvote
    - [ ] 選完回應之後，還可以捲回去選其他回應
    - [ ] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [x] Rich menu 測試
    - [x] 「設定」更改後再次打開，應該會保留原本設定
    - [x] 「教學」可以觸發教學流程

- [ ] Bug https://github.com/cofacts/rumors-line-bot/issues/327 should be fixed

- [ ] 群組測試
    - [ ] 在群組中可以觸發 chatbot


##### ⛔️ Release Blockers

若有多則回應，選擇回應的功能直接壞掉
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_14241b6b171af5d5f5c70bc18b5bf07f.png)


##### 未竟項目

### :eye: Under review

- [1] [Simplify postback handler signatures #372](https://github.com/cofacts/rumors-line-bot/pull/372)
- [2] [simplify text handlers as well #371](https://github.com/cofacts/rumors-line-bot/pull/371)
- [3] [Move selectedArticleId from context to action payload #369](https://github.com/cofacts/rumors-line-bot/pull/369)

## 小聚 rundown

- 週三會議
    - [x] 週四 8 pm schedule
    - [x] 換 rich menu
- 週五早上
    - [x] KKTIX 行前通知：提醒時間、使用電腦而非手機
    > Hello 你好，
	>
	> 明天就是 11 月 18 日的志工培訓囉！
	>
	> 志工培訓需要大量查詢資料，請自備筆電 💻 與充電器 🔌 並帶著愉快的心情來參加。帶順手的平板也可以的！如果願意協助編修影片逐字稿，請自備耳機唷🎧！
	>
	> 🕒 時間：11/18（六）14:00
	> 📍 地點：曬書店×新營市民學堂 台南市新營區中山路93-2號
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
    - [x] 開場使用材料更新：https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit [name=mrorz]
	- [x] 準備 Slido `#cofacts39`
		- [ ] 放投影片網址
		- [ ] 測試問卷：https://forms.gle/9yHxkHWaxq3LU7MX8
    - [x] 幫 Netgear 充電
- 當日準備 / 攜帶
    - [x] 樓下用的標語 - orz
    - [x] 尾款 2500 - orz
    - [x] 貼紙 - orz
    - [x] 黏土 - orz
    - [ ] 延長線 x 1 - rosalind
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
  - [x] 簽到（問飲料）
  - [ ] 排桌子椅子
  - [x] 麥克風
  - [x] 延長線佈置
  - [ ] 門口黏引導牌
  - [x] Slido - 白板寫 slido room number `#cofacts39`
  - [x] WIFI
      - [ ] 佈機x2
      - [ ] 連結 netgear 與 asus WAN port
      - [ ] 白紙寫 SSID Cofacts meetup(_5G) + wifi password 貼牆上
      - [ ] 192.168.2.1 進入 netgear admin 看 asus 的 IP
      - [ ] 開好兩台 router admin 監測連網狀態
      - [ ] (optional) netgear 換成 5GHz only?
  - [ ] 投影的電腦用 google chrome 開好
    - [x] Google Chrome tab: [投影片](https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit)
    - [x] Google Chrome tab: [Bignum](https://cofacts.github.io/community-builder/#/bignum/setup)
    - [ ] Google Chrome tab: [KKTIX](https://cofacts.kktix.cc/events/cofactseditor39)
    - [ ] Google Chrome tab: [Slido admin](https://admin.sli.do/event/jkZtEfky1jGbrhrV5xLVYV/questions)
    - [x] Google Chrome tab: [Slido](https://wall.sli.do/event/jkZtEfky1jGbrhrV5xLVYV?section=0de97ed8-b0d4-4922-aa6b-71a9619add69)
    - [ ] Google Chrome tab: [開場影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs)
    - [ ] BGM
    - [ ] Analytics
- 14:00 - 14:20 開場
    - 放[長影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs) 8min
    - 場地、Slido、Cofacts 機器人系統簡介
- 14:20 - 14:40：引導註冊網站、介紹評價現有回應
- 14:40 - 14:50：實作評價
    - 讓大家從網站找訊息按讚
- 14:50 - 15:10 介紹補充資訊
- 15:10 - 15:40 實作補充資訊、自我介紹、休息
    - 閒聊「看到覺得最好的回應、覺得哪裡好」
- 15:40 - 16:10：介紹撰寫新回應
- 16:10 - 16:40：實作撰寫新回應
    - 大家從網站挑選「一篇」覺得最有興趣的回
- 16:40 - 17:00 介紹 RSS、社群、合照


## 回溯型公眾投資

Google sheet done
https://docs.google.com/spreadsheets/d/1iOq2FOQPQ9mn5ZbN7xoUA9AGU7gThs72OEMMU_l0DyU/edit#gid=0 (僅協作者可見)

- 實驗團隊發現，沒辦法直接買回發出去的其他人的 Hypercert。
- 本實驗經過平方投票後的金額，需要用虛擬貨幣支付給團隊或團隊成員。

目前想法

1. Cofacts 錢包 mint Hypercert to Participents
    - Participants 不一定需要 claim Hypercert
2. 實驗把給 Cofacts 錢包，我們再另外按照比例轉給各個 participant。

## Llama Impact Grants

- 感謝 @Chen-Hung, Pai 提出與 @rockhung 協助 m(_ _)m

> https://g0v.hackmd.io/UjjgCfiYShu8V4GdOw3Qyg (僅協作者可見)

- Deploy https://github.com/MiuLab/Taiwan-LLaMa
- 實作 https://g0v.hackmd.io/oz-49rOSSPW3J8AbG0yRSA#Comm-ChatGPT-aid-fact-checking 的想像，但改用 Llama XD
- Software development, involves RAG, retrieval on the internet, updates and revamps to the website UI, MLOps, etc
- Hold offline workshops for crowd-source fact-checkers to revise the design
- Open-source, sharing findings and end results openly

## CCPRIP

### [Comm] Transcript

Collab server test
更新到 docker 4.25 剛好又遇到[問題](https://github.com/docker/for-mac/issues/7047) -> 4.25.1 解決了

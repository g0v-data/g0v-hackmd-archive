---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240527 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
#### :globe_with_meridians: Site
#### :robot_face: rumors-line-bot

### :rocket: Staging

#### :robot_face: rumors-line-bot

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [ ] 應可送出「全新訊息」
    - [ ] 問訊息來源時選擇「我自己打的」會被擋下。
    - [ ] 選擇「整篇轉傳」後會詢問是否要送出訊息。
    - [ ] 不同意送出訊息後可以收到感謝。
    - [ ] 同意送出訊息後就會送出訊息，並得到：
        - [ ] Cofacts article page 按鈕
        - [ ] 寫理由的按鈕
        - [ ] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面
        - [ ] 「分享到 Facebook」、「分享到 LINE」且可以正常運作
    - [ ] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [ ] 可以再打開理由視窗，此時會載入上次填寫的理由。修改理由送出後，查看 article page 看理由是否有被送出。

- [ ] 送出「沒回應」的舊訊息，應可送出新理由
    - [ ] 文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。
    - [ ] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [ ] 可以修改理由送出。查看 article page 看理由是否有被送出。
    - [ ] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [ ] 送出「有回應」的舊訊息，應自動回傳回應
    - [ ] 應列出訊息所有的回應
    - [ ] 選擇回應之後可以幫回應 upvote
    - [ ] 可以再次選擇 downvote
    - [ ] 選完回應之後，還可以捲回去選其他回應
    - [ ] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [ ] Rich menu 測試
    - [ ] 「設定」更改後再次打開，應該會保留原本設定
    - [ ] 「教學」可以觸發教學流程

##### ⛔️ Release Blockers
##### 未竟項目

#### :globe_with_meridians: Site
##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [ ] Article list
  - [ ] Filter works
  - [ ] Sorting works
  - [ ] Can go to article page
- [ ] Replies list
  - [ ] Filter works
    - [ ] 不允許選擇 Replied by me
  - [ ] Sorting works
  - [ ] Can go to article page
  - [ ] 不允許 upvote / downvote replies
  - [ ] Can see vote reasons
- [ ] Hoax for you
  - [ ] Filter works
  - [ ] Can go to article page
- [ ] Article detail
  - [ ] Can see similar messages
  - [ ] Cannot submit, upvote, downvote reply request
  - [ ] Cannot submit, upvote, downvote reply
  - [ ] Cannot add, remove, upvote, downvote category
- [ ] Search
  - [ ] Can use global search to perform search
  - [ ] Can use textarea in header to perform searchs
     - Known issue: firefox 無法
  - [ ] Can list searched articles
    - [ ] Filter works
    - [ ] Can go to article page
  - [ ] Can list searched replies

登入自有帳號後檢測：
- [ ] Replies search page
  - [ ] can upvote / downvote replies
- [ ] Replies list
  - [ ] 可選擇 Replied by me
  - [ ] can upvote / downvote replies
- [ ] Article detail
  - [ ] Can submit, upvote, downvote reply request
  - [ ] Can submit, remove own reply
  - [ ] Can upvote, downvote other's article reply
  - [ ] Can add, remove, upvote, downvote category
- [ ] Can go to profile page on menu
    - [ ] Can edit own name, bio, URL
    - [ ] Can see own replies
- [ ] Can logout

##### ⛔️ Release Blockers

##### 未竟項目


### :eye: Under review

## RightsCon 2025

## 小聚 Rundown

- 週五早上
    - [ ] KKTIX 行前通知：提醒時間、使用電腦而非手機
    > Hello 你好，
	>
	> 本週日就是 3 月 24 日的志工培訓囉！
	>
	> 志工培訓需要大量查詢資料，請自備筆電 💻 與充電器 🔌 並帶著愉快的心情來參加。帶順手的平板也可以的！如果願意協助編修影片逐字稿，請自備耳機唷🎧！
	>
	> 🕒 時間：3/24（日）14:00
	> 📍 地點：新北市青年局青職基地 / ~~新北市板橋區中山路一段 166 號 1 樓~~新北市板橋區民權路170號1樓
	> 
	> 費用全免，會很準時開始。若不克前往，記得取消報名 :)
	> 
	> Cofacts 真的假的 查核協作 VIP 臉書社團在這裡 👉 https://www.facebook.com/groups/cofacts
	> Cofacts 真的假的 查核協作 Discord 在這裡 👉  https://cofacts.tw/discord
	> 說你會來查核小聚優先加入 ＝Ｄ
	> 
	> 感謝你的閱讀。
	>
	> 那麼後天見囉😊
	>
	> 比鄰敬上
    - [ ] 開場使用材料更新：https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit [name=mrorz]
	- [ ] 準備 Slido `#cofacts41`
		- [ ] 放投影片網址
    - [ ] 幫 Netgear 充電
- 當日準備 / 攜帶
    - [ ] 樓下用的標語 - orz
    - [ ] 貼紙 - orz, bil
    - [ ] 黏土 - orz
    - [ ] 手板 - bil
    - [ ] 一次性杯子 - bil
    - [ ] 延長線
    - [ ] 編輯小聚的牌子 - orz
    - [ ] Wifi 機 - mrorz
        - [ ] Netgear 本體
            - [ ] usb type-c 充電線與插座 （已充飽電，無需插座）
            - [ ] 電池
            - [ ] 4G 天線
        - [ ] Asus RT-N12
            - [ ] 電源線
            - [ ] 5dBi 天線
            - [ ] RJ45 線
- 13:30 - 場佈
  - [ ] 簽到（問飲料）
  - [ ] 排桌子椅子
  - [ ] 麥克風
  - [ ] 延長線佈置
  - [ ] 門口黏引導牌
  - [ ] Slido - 白板寫 slido room number `#cofacts41`
  - [ ] WIFI
      - [ ] 佈機x2
      - [ ] 連結 netgear 與 asus WAN port
      - [ ] 白紙寫 SSID Cofacts meetup(_5G) + wifi password 貼牆上
      - [ ] 192.168.2.1 進入 netgear admin 看 asus 的 IP
      - [ ] 開好兩台 router admin 監測連網狀態
      - [ ] (optional) netgear 換成 5GHz only?
  - [ ] 投影的電腦用 google chrome 開好
    - [ ] Google Chrome tab: [投影片](https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit)
    - [ ] Google Chrome tab: [Bignum](https://cofacts.github.io/community-builder/#/bignum/setup)
    - [ ] Google Chrome tab: [KKTIX](https://cofacts.kktix.cc/events/cofactseditor40)
    - [ ] Google Chrome tab: [Slido admin](https://wall.sli.do/event/8SsE7k5tiiGy1FWA4hYMhi?section=ab7f5336-effb-42cb-9d6a-f4da9324a066)
    - [ ] Google Chrome tab: [Slido](https://wall.sli.do/event/nm76YwhjPaWEMvAgvELMLp?section=1b43b8ac-95c8-4b6a-8b21-1f92464b0c21)
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

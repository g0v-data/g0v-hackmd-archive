---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20230104 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：Bil, mrorz
- 線上出席：4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Community builder

- Upgrade stuff in https://github.com/cofacts/community-builder/pull/15

## 一月小聚

- [ ] 時間：1/15 (日)
- [ ] 場地：NPO Hub
  - 哪一間：4Ｆ廚房
  - Keyholder：Ronny
- [ ] 食物？統編？
- [ ] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：
- [ ] KKTIX：https://cofacts.kktix.cc/events/cofactseditor34
  - 人數調 25 因為廚房比較小
  - 因為有重複報名所以往上調一點
- [ ] 誰會來呢：bil, mrorz, nonumpa
- [ ] 無法來：
- [ ] LINE 文案
年節期間受不了親戚朋友傳來的假新聞，善良的你如果用一個下午的時間，參與本次志工活動，將可以對社會創造偉大的貢獻！
Cofacts 真的假的 在01月15日本週日下午 2 點- 5點 ，徵求查核協作志工，沒有年齡職業限制、活動完全免費，邀請你的到訪與參與！用鍵盤與智慧，為周圍的朋友與大家帶來和諧的力量。
(記得帶筆記型電腦與充電線唷！)如果願意協助聽打影片字幕，請自備耳機唷！
時間：01月15日(日) 下午 2 點- 5點
地點：台北市中正區重慶南路三段 2 號 4 樓廚房
最近的捷運站是中正紀念堂站2號出口

:::info
From [20221228](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2F6c3CpKXhQwOtFX8kf31ePA):
教學：comment 的教材提醒可以打影片逐字稿在 comment 處。
:::


## 檢舉回應

:::info
Target: 
[2022/12/23 下午 9:21:25 檢舉的](https://docs.google.com/spreadsheets/d/1q-iMJ9tZtoyHNfwInAb3z-eIg2x4-w1yp7XGTiaLB-w/edit?resourcekey#gid=1583640334&range=A525:M528)

- 移除不封鎖，公告在 takedown
- 指出內文錯誤段落、資料佐證
- 檢舉有提供理由、查核報告，才去檢視連結
    - 一到兩週討論，才會移除 [name=bil]
    - 不會下架
- Ex: https://github.com/cofacts/takedowns/blob/master/2022/0217-privacy.md
:::
事由：
Cofacts真的假的工作小組（Cofacts WG）接獲檢舉，有查核協作者引用到不實資訊，恐有散佈錯誤資訊之虞，而需要進行修正。
流程：
回應內容含有不實資訊散布的檢舉狀況，需要滿足檢舉者提供相對應之資料佐證，確認該筆資訊確實為誤用，並且提供理由，才能進行處理。僅是檢舉特定協作者，聲稱含有不實資訊並不能進入檢核流程。
判定：
根據檢舉者提供的理由調查，該名查核者引用他人言論進行回應，理由書中亦提供佐證資料。然而其內容含有不實訊息散布的狀況，判定予以移除。
處理：該則回應予以移除，協作者帳號維持開放。

https://www.mygopen.com/2023/01/punch.html

## TODO follow-up

### Monitoring
- ✅ Community builder MUI 升級
- 🏗️ [Community builder 改版](https://g0v.hackmd.io/VVIOZobARkegK3vxYdG52Q#community-builder-%E6%94%B9%E7%89%88)

:::success
先把 builder 做完
:::

### CCPRIP
https://g0v.hackmd.io/BRsJOevWSbyUMBSZEVVWrA#Operation-layer-%E7%B6%AD%E9%81%8B%E5%B1%A4

- 🏗️ Op layer: [Anti-SEO spam](https://g0v.hackmd.io/@mrorz/cofacts-rd/%2FXBJS-KEtScWyVCuQ9P_iNQ
) M2~M4
- Op layer: [API client app management](https://g0v.hackmd.io/@mrorz/cofacts-rd/%2F51wwLHgvSUqtBDaP-yAVnA)
    - Have update: towards deprecating web apps
- Content layer: [crowd-sourced transcript](https://g0v.hackmd.io/@mrorz/cofacts-rd/%2FOhGIQzoxR5eF6audQuS_FQ)

### Site enhancement
- https://github.com/cofacts/rumors-site/issues/520
- https://github.com/cofacts/rumors-site/issues/521
- 新增：可疑訊息 filter [name=bil]
    - 我沒回過的（排除自己無法 vote 的）
    - 沒有回應的（把時間花在寫新回應用）



### GA4 support

Design: https://g0v.hackmd.io/@mrorz/cofacts-rd/%2FQRRlVa_URk-wT0QqahLN-w

Response from Google:

- Q1. Cofacts 真的假的 chatbot 的流量分為 chatbot callback server 的伺服器端事件（使用者與聊天機器人的對話），與嵌入網頁（LIFF）的流量。後者或許可以對應到 web data stream，但 chatbot 伺服器的流量不確定應該使用何種 data stream。
    - A1: 如果是伺服器端的資料我們是建議使用Measurement Protocol，但由於GA4現在是基於網頁/App的資料為主的分析工具，伺服器資料我們也是預期會先有頁面的瀏覽，才能進行Measurement Protocol的資料串接。等等下一題詳細回答技術細節。
- Q2. 即使使用 GA4 的 Measurement Protocol，也會因為不知道 client_id 應該填入什麼而有問題( 具體問題如此技術文章 https://taichunmin.idv.tw/blog/2020-11-21-linebot-google-analytics.html )
    - A2: Client ID可以在網頁取得(方法), 之後用同一個client ID傳送Measurement Protocol，即可將伺服器端資料傳送至GA4
- Q3. Cofacts 真的假的除了 chatbot 之外，還另有網站如 https://cofacts.tw，且使用者不互通。過往我們會設定多個 universal analytics 的 GA property，但不確定轉換到 GA4 後，應該使用多少個 GA4 property、或應該使用單一個 GA4 property 裡面開很多 data streams。（已閱畢相關文件，但不確定我們的狀況應該何者較適合）
    - A3: 一個GA4 property 會有一個web data stream 和多組 iOS / Android data stream，但暫時沒有開放其他的資料源。可參考[這篇外部文章](https://support.google.com/analytics/answer/9679158)了解資料串流的概念。

---

- GA4 not designed for chatbot and is difficult to work with chatbot servers
- What can we do?
    - Change to Woopra
        - Pros:
            - Freedom in event fields, etc
            - Great visualization, including journey
        - Cons:
            - Cannot expose to Google Data studio
            - 500K actions/mo, 90-day data retention
    - 優先考慮 google 因為 rumors-api 已經有 GCP service account 可以撈 google 的資料
        - Send events to Google BigQuery?
        - Google Pubsub --> BigQuery --> Data studio
        - [Firebase](https://firebase.google.com/products/analytics) --> ?? --> Data studio ?
- 問臉書 / g0v slack / 回 google 信

## 色情 mitigation
https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2F6c3CpKXhQwOtFX8kf31ePA

## 訂閱功能

- 圖片應該顯示縮圖
- IFTTT Telegram 可以更新成 discord (https://ifttt.com/discord) [name=cai]
- 開個 cofacts 的 discord (?)
    - 先接 IFTTT
    - 再看要不要與 g0v slack #cofacts sync

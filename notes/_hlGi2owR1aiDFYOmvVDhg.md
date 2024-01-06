---
tags: cofacts, meeting note
---

20190306 會議記錄
=====
> bil, mrorz, ttcat, lucien
 
 
> 前次會議記錄：https://g0v.hackmd.io/s/ry5r12mI4
> 

## 大松籌備

會到場：bil, mrorz, darkbtf

### 我愛家我解惑
- 待輸入與待回應資料：TBD
    - FB 討論, Hackmd (optional), answerfamily link, 已標出段落, 已全部回應
    - FB 討論: 用 ＡＰＩ 撈撈
- 投影片介紹：MrOrz
    - 以一個訊息為例
    - 介紹 flow: 搜尋 --> 文章頁面 --> 超連結 --> 逐字稿
    - 徵求：法律人、對平權有熱心的人
- 系統改進
    - ~~刪除 article 功能~~
    - too many clauses bug: https://github.com/answerfamily/answerfamily-api/issues/3
    - search paragraph UI 應該要參考 article UI

### 我愛家我聯絡
- 成果報告再提及 ~~or 提案時就講？~~


### Cofacts


- 找協助回應的人
    - TA：bil
- 程式需要協助：
    - github.com/cofacts 的 issue
    - TA: mrorz, darkbtf
    - bug triage:
        - https://github.com/cofacts/rumors-site/labels/good%20first%20issue
        - 
- Designer
    - Lucien 到場之前請他們畫 badge? 小聚的圖？
    - 徵求 visual designer

## 新 idea

- 類似我愛家我聯絡，但對象改成一般 FB post / comment
- 投傘兵 + 提供回應樣板
- 使用 Facebook [embedded post](https://developers.facebook.com/docs/plugins/embedded-posts) / [embedded comment](https://developers.facebook.com/docs/plugins/embedded-comments) social plugin
- 一次傳 5 個，3 分鐘內完成一次任務。使用 [web notification](https://developers.google.com/web/fundamentals/push-notifications/) 提醒使用者接新任務。
- 後續對話，可以引導使用我愛家我解惑資料庫。
- 問題：怎麼取得待回應的一般 FB post / comment 列表？

:::warning
在解決下面兩件事情前先 on-hold

1. 我愛家我解惑資料庫應更完備，才有辦法應付回應與搜尋待回戰場。
2. 「待回戰場」若 FB API 撈不出來，可能又要做成使用者回報（facebook chatbot 轉傳或許可行）。
:::

## ttcat

編輯回完系統之後，出處可能會失效，應該要自動截圖截下來。
編輯體驗完全相同，但使用者點擊連結之後，點進去就會是前導

orz
我們已經會有 puppeteer 爬網頁。
但存圖有點麻煩，或許可以用 wayback machine。
我覺得可以做，不過我會希望導流量給原本的網站。
可以做成在網站上的「頁庫存檔」連結嗎？

ttcat
但是如果是 LINE 訊息，就沒辦法。使用者點進去失效，會覺得我們的回應是假的。

orz
但我還是要讓闢謠網站得到 clicks。
還是應該弄個 proxy，如果後面壞了才顯示頁庫存檔。
這樣我 redirect 給闢謠網站的時候還可以幫他插入 utm_source 之類的東西。

ttcat
wayback machine 好像有陽春的 api
這可以再研究

:::info
Github issue: https://github.com/cofacts/rumors-api/issues/125
:::

### ttcat & lucien

lucien: 有訂 wireframe 但不在這一台電腦
我應該會上傳到 github

ttcat：可以直接做還是討論？

lucien：還要討論

ttcat: 要不要 schedule 一個時間討論？
一個禮拜三晚上可以討論完，還是要另外約時間？

lucien:
如果是網站，應該可以在禮拜三晚上

ttcat:
4/7 那個禮拜可以討論嗎
下週三可以嗎？

:::info
結論：下週三晚上討論網站
:::

## 資訊媒體素養講座巡迴
今日 9:30pm 討論簡報

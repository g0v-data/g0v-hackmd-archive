---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250609 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, nonumpa, 4000, mrorz
- Gather Town: https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## 本次會議待追蹤項目

*   **Open165 重構**: Open165 重構相關 PR (Open165/worker #5, Open165/site #37) 已開啟，但尚未測試。
    *   Open165 TODOs: 將 DB schema 移動到 worker 管理、在 worker 中建立子 workflow、建立資料交換格式、Website display。
*   **資訊安全**: 把 cofacts 用的服務改用 cofacts.tw email，避免使用個人 gmail
    *   Johnson 先用 cofacts email 取得服務的管理者權限
    *   Johnson invite 大家的 cofacts.tw email
    *   Johnson 移除非 cofacts.tw email access
*   **小聚籌備 (06/15)**: 確認食物、投放目標設定 (06/03 推播，目標雙北)、KKTix 活動頁面、LINE 文案、VOOM 發文、FB 發文、攜帶物品 (貼紙、不太環保杯)。

## Langfuse update

- Background migrations all resolved ![](https://g0v.hackmd.io/_uploads/r1ebwAW4Xle.png)
    - 先前最後一個 task 一直卡住，可能是未知原因下他的 lock 沒 release
    - restart worker container 重跑就好了
- 3.56.0 --> 3.66.1 ![](https://g0v.hackmd.io/_uploads/r1JMZMEXlg.png)
    - LLM-as-a-Judge 與 Playground 功能變成免費的 https://langfuse.com/blog/2025-06-04-open-sourcing-langfuse-product


## 小聚 rundown

- 週六早上
    - [x] KKTIX 行前通知：提醒時間、使用電腦而非手機
    > Hello 你好，
	>
	> 本週日就是 6 月 15 日查核志工培訓囉！
	>
	> 志工培訓需要大量查詢資料，請自備筆電 💻 與充電器 🔌 並帶著愉快的心情來參加。帶順手的平板也可以的！如果願意協助編修影片逐字稿，請自備耳機唷🎧！
	>
	> 🕒 時間：06/15（日）14:00 - 17:00
	> 📍 地點：新北市青年局青職基地2樓 / 新北市板橋區民權路170號2樓(近板橋捷運站)
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
	- [x] 準備 Slido `#cofacts`
		- [x] 放投影片網址
- 當日準備 / 攜帶
    - [ ] 樓下用的標語 - bil
    - [x] 貼紙 - orz, bil
    - [x] 黏土 - orz
    - [ ] 手板 - bil
    - [ ] 講義 - bil
    - [ ] 一次性杯子 - bil
    - [ ] 延長線 - bil / mrorz
        - 比鄰有三條
    - [x] Wifi 機 - mrorz
        - [x] rt-ax57 go
        - [x] 電源線
    - [x] 多帶一條 type-c 公公線 for dongle 的電
    - [ ] 備用 wifi 機 [name=nonumpa]
- 13:00 - 場佈 [排法](https://g0v.hackmd.io/0rzXk22PQZ2g5aswKIAXdw?view)
  - 桌子一邊 4 張椅子
  - [ ] 簽到（問飲料）
  - [ ] 排桌子椅子 
  - [ ] 投影位置？
  - [ ] 麥克風
  - [ ] 延長線佈置
  - [ ] 門口黏引導牌
  - [ ] WIFI
      - [x] 佈機，手機 USB 選擇網路分享，等待白燈亮
      - [x] 用 ASUS Device Discovery 確認可連線到 ASUS
  - [ ] 投影的電腦用 google chrome 開好
    - [ ] Google Chrome tab: [投影片](https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit)
    - [ ] Google Chrome tab: [Bignum](https://cofacts.github.io/community-builder/#/bignum/setup)
- [ ] browser tabs
    - [x] Google Chrome tab: [KKTIX](https://cofacts.kktix.cc/events/cofactseditor47)
    - [x] Google Chrome tab: [Slido admin](https://admin.sli.do/event/rFQZd27cVvgEMyJAgv4BqT/polls)
    - [x] Google Chrome tab: [Slido](https://wall.sli.do/event/rFQZd27cVvgEMyJAgv4BqT/?section=215e56d0-a002-4b7e-9bf0-c58acbacc9bf)
    - [x] Google Chrome tab: [開場影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs)
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


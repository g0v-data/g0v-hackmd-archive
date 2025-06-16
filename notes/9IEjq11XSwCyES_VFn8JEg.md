---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250616 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO Hub 出席：bil, mrorz, nonumpa
- 線上出席：
- Gather Town: https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## 本次會議待追蹤項目

*   **Open165 重構**: Open165 重構相關 PR 已開啟，待測試。TODOs: 將 DB schema 移動到 worker 管理、在 worker 中建立子 workflow、建立資料交換格式、Website display。
*   **資訊安全**: cofacts 用的服務改用 cofacts.tw email。Johnson 將協助取得管理者權限、邀請大家使用 cofacts.tw email，並移除其他非 cofacts.tw email 的權限。

## Open165

- 先手動停掉了 site 的 Github workflow 避免 race condition https://github.com/Open165/site/actions
- Cloudflare 有一直執行，但剛好上週都沒更新。6/16 20:00 執行結果：成功
- 因為跑 test 那些其實都會需要 DB schema，會先發 PR 之後下一個 PR 處理 DB schema
- 檢查 Github Open165 organization 為何 webhook 不會觸發

## CCPRIP

### [Op] Takedowns

- 1 個 true positive, 3 個 false positive

## 小聚檢討

> 小松果：https://g0v.hackmd.io/y4-U7ZZ1SGOtYL1gXgoBWg?view

- 新排法
  - 使用 5 張折疊桌
  - https://docs.google.com/drawings/d/1yyAbWFmCC16Ur0lEf7m3szZVZ7en1rSpXx8BHlyrcN0/edit?usp=sharing
  - 工人先把下面兩張桌子佔起來，參與者自然就會坐到螢幕前 [name=bil]
- 報到率 ~ 50%
  - 報名 30 人
  - 事前取消 3 人
  - 報到 15 人
- 人數
  - 30 太多人，跺腳 [name=bil]
  - 30 很完美，因為上圖有畫出來的桌子最多就是 30，當天坐 15 也很好 [name=mrorz]
    - 報到率一般 50% --> 很好
    - 就算真的 100% --> 還是很好
    - 當然繼續 30 人
- 14:00 整點才 3 人，大多 14:06 才來
  - 播放影片很重要 XD 
- 時間分配
  - 這次一開始 5min lead, 14:45 評價結束 [name=mrorz]
  - 評價因為後面還能再做，所以還可以再短 [name=bil]
  - 自我介紹比較重要，因為要用來寫報告 [name=bil]
- 網路
  - New Taipei 不一定能用
  - 網路 Cofacts meetup / Cofacts meetup 5G 順暢
  - Cofacts Meetup 2 沒人連

青職基地框時間
- 0817 小聚：已借
- 1026 小聚
  - 青職基地休週一，但國定假日休息
  - 總之 10 月沒了
  - 10/26 用[行天宮小樹屋](https://thehapp.com/space/267) 1F capacity=24人且偏擠 [name=bil]
  - 看看 11/1 青職基地 [name=mrorz]
- 1228 期末感恩茶會


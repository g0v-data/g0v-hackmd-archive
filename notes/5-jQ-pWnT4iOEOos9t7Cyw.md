---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20241202 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO hub 出席：bil, nonumpa, mrorz
- 線上出席：品君, T, EJ
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

- belong112++
https://github.com/cofacts/rumors-site/releases/tag/release%2F20241202

#### :robot_face: rumors-line-bot

### :rocket: Staging

#### :electric_plug: API

blockUser API


## Badge

> EJ

- Lint pending https://github.com/cofacts/rumors-db/pull/74
- The need of `issuer` field --> `issuers`
- badge color --> border image to allow more flexible border setups

## CCPRIP

### [OP] 檢舉現象

- 有可疑使用者
- 有 Cofacts 帳號但沒有什麼活動

### [Op] Automated spam removal

> Design doc: https://g0v.hackmd.io/@cofacts/rd/%2Fum7DyY_ESbu2LL78kLw3pg


#### Phase 1: Script execution automation
> MrOrz

- API done
- 先把 spreadsheet 改成生成 curl command, header 假設在環境裡有 env var
  - 在有 key 的電腦都能執行，不再需要 ssh 進主機
  - 或者只在 swagger UI 上執行，不用另外發 key

#### Phase 3: Automated detection
> nonumpa


## 小聚籌備

- [ ] 日期：01/05 (日)   - 已經訂好了
- [ ] 食物：
- [ ] 場地：NPO Hub Foundry（大的那間)
- [ ] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Slido 暖身
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：
  - 推播日：12/27 or 12/22
  - 目標：雙北
- [ ] KKTIX: https://cofacts.kktix.cc/events/cofactseditor45
- [ ] 誰會來呢：bil,orz,nonumpa
- [ ] 記得帶：貼紙、環保杯
- [ ] LINE 文案： TikTok 上熱門到轉傳給 LINE 的影片說皮蛋在顯微鏡下都是會四處蠕動的寄生蟲，真的假的呀？這其實是一個合成過的影片，前半段雖然真的是把皮蛋切片放在載玻片並用顯微鏡觀察，但後半部有蟲蟲危機的片段卻是合成剪接後的結果。顯然眼見為憑並不為真。網路上許多影片圖片需要你的查證公開，就能幫助更多身邊的人。 Cofacts 真的假的 第 45 次志工查核工作坊需要你的加入，活動完全免費，（請自備電腦）最近的捷運站是中正紀念堂站，連結內報名：https://cofacts.kktix.cc/events/cofactseditor45
- [ ] VOOM 發文
- [ ] FB 發文

## 12 月開會
- 12/30 (一) 開會改成 1/2 (四)

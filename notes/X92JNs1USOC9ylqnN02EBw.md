---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250127 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz, nonumpa, 4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
- Langfuse integration https://github.com/cofacts/rumors-api/releases/tag/release%2F20250121

### :rocket: Staging

#### :robot_face: rumors-line-bot

- Langfuse integration https://github.com/cofacts/rumors-line-bot/pull/400

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 應可送出「全新影片訊息」並且讀到 AI 回應
    - [x] 可對 AI 回應 upvote / downvote

- [x] 送出「沒回應」的舊影片訊息，可以看到 AI 回應
    - [x] 可對 AI 回應 upvote / downvote

##### ⛔️ Release Blockers
##### 未竟項目

#### :globe_with_meridians: Site

- Langfuse integration https://github.com/cofacts/rumors-site/pull/596
- News update https://github.com/cofacts/rumors-site/pull/595

預期行為
- 任何 AI reply 都能 vote feedback
- 但只有在 langfuse 有 trace 的新 AI reply 才會在 [score list](https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/scores) 有 trace name
  - 就算 trace 不在 langfuse 上，也能用 trace ID 查找 AI response

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] 可對任何 AI 回應 upvote / downvote

##### ⛔️ Release Blockers

- [x] Feedback dialog
  - 沒打字應該 disable
  - 送出後應該要感謝

### :eye: Under review

Langfuse integration
- https://github.com/cofacts/rumors-site/pull/596
- https://github.com/cofacts/rumors-line-bot/pull/400


## RightsCon & Satelite Events

- 2/22 (Sat) 大松：https://g0v-jothon.kktix.cc/events/g0v-hackath65n 
- 2/24 (一) Side-event 17:00~18:00 比鄰演講
- 2/25 (二) 9:00~10:00 NDI Panel
- 2/25 (二) 14:00 ~ 15:00 Cofacts 自己的 talk - ID # 23894 – “Crowd-sourced fact-checking in AI era - Lessons learned by Cofacts
  - 地點：South Lobby of the 2nd floor
- 2/26 (三) **早上**擺攤
- 2/26 (三) 12:45-13:45 大平台 ~~(Promote 攤位)~~
- 2/27 (四) 11:30~12:30
  - NiemanLab / Panel Discussion / Challenge around deepfake detection
- 2/27 (四) 12:45~13:45 ID # 25017 - Global Giants, Local Influence: The Role of International Social Media in Shaping National Discourse
  - 地點：201E

### Sessions we may participate

- 2/24 OCF sattlelite event
- 2/26 (三) DWeb panel 10:15~11:15 (Promote 攤位)
- 2/24~2/27 OCF＆司改會一起擺攤

### 2/26 (三) 09:00~13:00 擺攤

時間
- 8:30 ~ 9:00 設攤
- 9:00 ~ 13:00 擺攤

空間
- 3F Networking Lounge https://www.rightscon.org/venue2025/#floor3 / https://www.ticc.com.tw/wSite/vr360/index.html
- 先在 1F Help Desk 報到，才知道在哪個 booth
- 180 cm x 60 cm 桌子
- 2 張折疊椅
- 牆上不能貼東西
- 不一定有電，延長線自備
- 沒有推車與幫手，進場撤場都是手搬

### Material

https://drive.google.com/drive/folders/1U-etbZSOiFzpXgOr0GtBxkwYKk666nni

- [x] 局部上光 bil 名片
  - 加中文「比鄰」小字
- [x] 更新英文版網站 news
- [ ] 文宣更新與印刷
  - [x] 英文（achoo）
    - 250 張起跳 http://www.soho8d.com.tw/Form2/F102.aspx?csubid=73
    - 要更新 QR code
  - [ ] 豆腐版
  - 借放在 OCF 攤位 & 自己攤位上
- [ ] 宣傳用：Logo 貼紙（透明 or 長的）
  - 透明 Logo + Cofacts
  - Soho 500 張起跳，算模 http://www.soho8d.com.tw/Form2/F102.aspx?id=147
  - Soho 數位標籤貼紙有透明版
    - 長方形, 500 張透明 NTD1484 http://www.soho8d.com.tw/Form2/F102.aspx?id=501
  - ~~StickerHD：https://www.stickerhd.com/ ![](https://g0v.hackmd.io/_uploads/H1PwznoPye.png)~~
- 投影片放在多頁的透明資料夾



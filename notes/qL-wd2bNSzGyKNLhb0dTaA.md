---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250219 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### 🌎 Community Builder

https://cofacts.github.io/community-builder/#/analytics/setup

### :rocket: Staging

Carried over from last week
- Internet archive logging 
- uploadMedia refactor 

New
- Gemini transcript https://github.com/cofacts/rumors-api/pull/359
- Gemini model & location selection https://github.com/cofacts/rumors-api/pull/361
- Badge related API

#### :robot_face: rumors-line-bot

- LINE bot - long response handling https://github.com/cofacts/rumors-line-bot/pull/401
  - Fixed redis reply-token & batch handling


##### Testing checklist

https://lin.ee/1QUzEX4nI

- [ ] 應可送出「全新文字訊息」
    - [ ] 同意送出訊息後就會送出訊息，並得到 AI reply
- [ ] 應可送出「全新影音訊息」
    - [ ] 同意送出訊息後就會送出訊息，並得到 AI reply
- [ ] 送出「沒回應」的舊訊息，應可顯示 AI reply
- [ ] 送出「有回應」的舊訊息，應自動回傳回應

##### ⛔️ Release Blockers

##### 未竟項目

## Badge

> EJ
> https://g0v.hackmd.io/@cofacts/rd/%2Fzx_Au6iiRN601tnMK7gx3A


## CCPRIP

### [Op] Automated spam removal

> Design doc: https://g0v.hackmd.io/@cofacts/rd/%2Fum7DyY_ESbu2LL78kLw3pg

### [Comm] AI transcripts

> Last week: https://github.com/cofacts/rumors-api/pull/361#issue-2839000967

## 大松準備

## 小聚籌備？

## RightsCon & Satelite Events


- 2/22 (Sat) 大松：https://g0v-jothon.kktix.cc/events/g0v-hackath65n 
- ~~2/24 (一) Side-event 17:00~18:00 比鄰演講~~ 取消
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

- [2/23 (日) OCF sattlelite event](https://ooni-research.ocf.tw/docs/blog/2025/02/rightscon25-tor-tails-ooni/)
  - 活動日期：2025/02/23
  - 工作坊 14:00 – 17:30 如何使用 Tor 避開審查並匿名瀏覽
  - 工作坊 18:00 – 19:00 如何使用 OONI 偵測與觀察網路審查狀況
  - 演講座 19:30 – 21:00 Tor 在網路監控的世界中捍衛個人線上隱私權
- 2/23 (日) 3pm-6pm[【工作坊】打造韌性網路：動手實作「不需海纜」的網路](https://airtable.com/appWd48vvxh0VJS1D/shrLERQDlmu6j3jMz)
- 2/26 (三) DWeb panel 10:15~11:15 (Promote 攤位)
- 2/24~2/27 OCF＆司改會一起擺攤

### 2/26 (三) 09:00~13:00 擺攤

人
- Johnson & Bil
- Stella & Yutin

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

https://drive.google.com/githubdrive/folders/1U-etbZSOiFzpXgOr0GtBxkwYKk666nni

- [ ] CCC 的 Cofacts 遊戲
- [x] 局部上光 bil 名片
  - [x] 加中文「比鄰」小字
- [x] 更新英文版網站 news
- [x] 文宣更新與印刷
  - [x] 英文（achoo）
    - 250 張起跳 http://www.soho8d.com.tw/Form2/F102.aspx?csubid=73
    - 要更新 QR code
  - [ ] 豆腐版
  - 借放在 OCF 攤位 & 自己攤位上
- [ ] 宣傳用：Logo 貼紙（透明 or 長的）
  - Soho 數位標籤貼紙有透明版
    - 長方形, 500 張透明 NTD1484 http://www.soho8d.com.tw/Form2/F102.aspx?id=501
    - 6cmx2cm
![](https://g0v.hackmd.io/_uploads/ryV7zLUYJe.jpg)
![](https://g0v.hackmd.io/_uploads/SJlVldBUY1l.jpg)
![](https://g0v.hackmd.io/_uploads/HyxqXM8UKkx.jpg)
    - 喜歡白底 [name=bil]
    - 建議左邊倒數第二個或左邊最後一個 [name=mroprz]
    - 左邊倒數第二個在黑底比較不突兀 [name=T]
    - 左邊倒數第二個 [name=nonumpa]

- 投影片放在多頁的透明資料夾



---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250219 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO Hub 出席：bil, nonumpa, mrorz
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
- Gemini transcript https://github.com/cofacts/rumors-api/pull/359
- Gemini model & location selection https://github.com/cofacts/rumors-api/pull/361

New
- Badge related API

#### :robot_face: rumors-line-bot

- LINE bot - long response handling https://github.com/cofacts/rumors-line-bot/pull/401
  - Fixed redis reply-token & batch handling

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 應可送出「全新文字訊息」
    - [x] 同意送出訊息後就會送出訊息，並得到 AI reply
- [ ] 應可送出「全新影音訊息」
    - [ ] 同意送出訊息後就會送出訊息，並得到 AI reply
- [x] 送出「沒回應」的舊訊息，應可顯示 AI reply
- [x] 送出「有回應」的舊訊息，應自動回傳回應
- [ ] 在 loading 時追加送訊息會發生什麼事？
會三個彩色點點跑跑跑，問是不是同一個人傳的，送進資料庫。文字跟影音都會存在資料庫，會提供訊息很新（少於一分鐘），不要相信ＡＩreply [name=bil]
- 如果使用者回答「是」就代表使用者說謊，或他沒看懂我們寫的訊息。不知道怎麼解 [name=mrorz]

##### ⛔️ Release Blockers
2min Transcript 成功
https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/jYguHpUBpiYdBld_-Fz9?observation=83701c5d-f96a-4419-af1c-131303391fdf

但後續處理好像有問題
![](https://g0v.hackmd.io/_uploads/Byhux8Q91l.png)

檔案來源：https://cofacts.tw/article/zueOBJUBYrjt7MSMFMVL

## CCPRIP

### [Op] Automated spam removal

> Design doc: https://g0v.hackmd.io/@cofacts/rd/%2Fum7DyY_ESbu2LL78kLw3pg


## 大松準備

- Cofacts：整理爛爛的逐字稿，之後用 LLM transcript AI 一次處理？
  - Canva 主視覺加時間，印出來 + QR code to Agenda
  - 帶 logo 貼紙、傳單
- Open165 沒空準備 ._. --> 取消

## RightsCon & Satelite Events


- 2/22 (Sat) 大松：https://g0v-jothon.kktix.cc/events/g0v-hackath65n 
- ~~2/24 (一) Side-event 17:00~18:00 比鄰演講~~ 取消
- 2/25 (二) 9:00~10:00 NDI Panel
- 2/25 (二) 14:00 ~ 15:00 Cofacts 自己的 talk - ID # 23894 – “Crowd-sourced fact-checking in AI era - Lessons learned by Cofacts
  - 地點：South Lobby of the 2nd floor
  - 投影片：https://docs.google.com/presentation/d/1_FGSKvgP2jh9o_22FhKSuDWLI-cu4lY3u95PL5lVb9o/edit
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

材料

https://drive.google.com/drive/folders/1U-etbZSOiFzpXgOr0GtBxkwYKk666nni

- [ ] CCC 的 Cofacts 遊戲
- [x] 局部上光 bil 名片
  - [x] 加中文「比鄰」小字
- [x] 更新英文版網站 news
- [x] 文宣更新與印刷
  - [x] 英文（achoo）
    - 250 張起跳 http://www.soho8d.com.tw/Form2/F102.aspx?csubid=73
    - 要更新 QR code
    - 背面有疊影，需處理掉四色黑
  - [ ] 豆腐版
  - 借放在 OCF 攤位 & 自己攤位上
- [x] 宣傳用：Logo 貼紙（透明 or 長的）
- [ ] 投影片放在多頁的透明資料夾

## 小聚籌備

3/29 大松，3 月不會有小聚
bil hold 新北板橋志工聚會

## 3 月起場地

- 202
  - 從樓梯上來


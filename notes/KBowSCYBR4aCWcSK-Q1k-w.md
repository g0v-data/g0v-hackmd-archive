---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250203 會議記錄
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

https://github.com/cofacts/rumors-site/releases/tag/release%2F20250127
- AI reply feedbacks
- News

#### :robot_face: rumors-line-bot

https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20250127
- AI reply feedbacks

### :rocket: Staging

#### :electric_plug: API

- Internet archive logging https://github.com/cofacts/rumors-api/pull/358
    - Found that my internet archive secrets is rotated.
    - Archiving is back to work after I update the secret on Feb 1st
- uploadMedia refactor https://github.com/cofacts/rumors-api/pull/360
    - Upgrade GCS SDK used in media-manager https://github.com/cofacts/media-manager/pull/11
- Gemini transcript https://github.com/cofacts/rumors-api/pull/359 (WIP)

#### :robot_face: rumors-line-bot

- Fix AI reply sender name https://github.com/cofacts/rumors-line-bot/pull/402
- Long response handling https://github.com/cofacts/rumors-line-bot/pull/401

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [ ] 應可送出「全新訊息」
    - [ ] 選擇「整篇轉傳」後會詢問是否要送出訊息。
    - [ ] 同意送出訊息後就會送出訊息，並得到：
        - [ ] Cofacts article page 按鈕
        - [ ] AI reply
        - [ ] 寫理由的按鈕
        - [ ] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [ ] 送出「沒回應」的舊訊息，應可顯示 AI reply
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
    - [ ] 「教學」可以觸發教學流程

##### ⛔️ Release Blockers
##### 未竟項目
### :eye: Under review
- LINE bot https://github.com/cofacts/rumors-line-bot/pull/401
- API (WIP) 


## Badge

> EJ
> https://g0v.hackmd.io/@cofacts/rd/%2Fzx_Au6iiRN601tnMK7gx3A

## CCPRIP

### [Op] Automated spam removal

> Design doc: https://g0v.hackmd.io/@cofacts/rd/%2Fum7DyY_ESbu2LL78kLw3pg


## AI reply feedbacks analysis


## Communication

- Global Alliance for AI
- TES

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



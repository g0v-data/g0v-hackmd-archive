---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250120 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：品君, nonumpa, EJ
- NPO Hub: bil, mrorz
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :electric_plug: API

- Add langfuse integration https://github.com/cofacts/rumors-api/pull/355
    - Use doc ID as trace ID so that we can attach scores later

#### :robot_face: rumors-line-bot

##### Testing checklist

https://lin.ee/1QUzEX4nI
Staging 可能在睡覺，可以先用「教學」戳醒 chatbot


- [x] 應可送出「全新影音訊息」（staging 上，影片需在 32mb 以下，以避開 [cloudrun response size 限制](https://cloud.google.com/run/quotas)）
    - [x] 影音訊息送出會有逐字稿
    - [x] 影音訊息會有 AI reply
- [x] 應可送出「現有影音訊息」
    - [x] 可以搜得到該則影音訊息
- [x] 送出與「現有影音訊息」相同的「新」錄音檔，應可搜到該則影音訊息

##### 未竟項目
- Staging 很慢 [name=bil]

## Badge

> EJ
> https://g0v.hackmd.io/@cofacts/rd/%2Fzx_Au6iiRN601tnMK7gx3A

- build and push badge API [name=mrorz]


## 通聯

- 那個資安的信: 不要理他
- Initiatives that link AI to democracy - world mapping project
  - intereseted in knowing more [name=mrorz]


## RightsCon & Satelite Events

- 2/22 (Sat) 大松：https://g0v-jothon.kktix.cc/events/g0v-hackath65n 
- 2/24 (一) Side-event 17:00~18:00 比鄰演講
- 2/25 (二) 9:00~10:00 NDI Panel
- 2/25 (二) 14:00 ~ 15:00 Cofacts 自己的 talk - ID # 23894 – “Crowd-sourced fact-checking in AI era - Lessons learned by Cofacts
  - 地點：South Lobby of the 2nd floor
- 2/26 (三) 報名了半天擺攤，**來信通知已錄取** 
- 2/26 (三) 12:45-13:45 大平台 (Promote 攤位)
- 2/27 (四) 11:30~12:30
  - NiemanLab / Panel Discussion / Challenge around deepfake detection
- 2/27 (四) 12:45~13:45 ID # 25017 - Global Giants, Local Influence: The Role of International Social Media in Shaping National Discourse
  - 地點：201E

### Sessions we may participate

- 2/24 OCF sattlelite event
- 2/26 (三) DWeb panel 10:15~11:15 (Promote 攤位)
- 2/24~2/27 OCF＆司改會一起擺攤

### Material

https://drive.google.com/drive/folders/1U-etbZSOiFzpXgOr0GtBxkwYKk666nni

- [x] 局部上光 bil 名片
  - 加中文「比鄰」小字
- [x] 更新英文版網站 news
- [ ] 文宣更新與印刷
  - [ ] 英文（achoo）
    - 250 張起跳 http://www.soho8d.com.tw/Form2/F102.aspx?csubid=73
    - 要更新 QR code
  - [ ] 豆腐版
  - 借放在 OCF 攤位 & 自己攤位上
- [ ] 宣傳用：Logo 貼紙（透明 or 長的）
  - Soho 500 張起跳，算模 http://www.soho8d.com.tw/Form2/F102.aspx?id=147
  - Soho 數位標籤貼紙有透明版 http://www.soho8d.com.tw/Form2/F102.aspx?id=502
  - ~~StickerHD：https://www.stickerhd.com/ ![](https://g0v.hackmd.io/_uploads/H1PwznoPye.png)~~
  - [ ] 「適時查核？那你來查呀」
  - [ ] 「含有個人意見」
- 投影片放在多頁的透明資料夾


## Open165

[jimyhuang](https://speakerdeck.com/jimyhuang/ru-he-can-yu-g0v-tan-tan-fa-qi-zu-zhi-ling-shi-zheng-fu-zhuan-an-zheng-zhi-de-xin-lu-li-cheng)++
- https://github.com/Open165/165cases
- https://165case.cofacts.tw/
- 165 資料使用疑慮 --> 是否要知會？

## 辦公室使用

> bil
漲租金搬遷



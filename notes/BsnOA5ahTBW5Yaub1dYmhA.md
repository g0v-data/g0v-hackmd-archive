---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250210 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：nonumpa, bil, T, mrorz
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

Carried over from last week
- Internet archive logging 
- uploadMedia refactor 

New
- Gemini transcript https://github.com/cofacts/rumors-api/pull/359
- Gemini model & location selection https://github.com/cofacts/rumors-api/pull/361

#### :robot_face: rumors-line-bot

- LINE bot - long response handling https://github.com/cofacts/rumors-line-bot/pull/401


##### Testing checklist

https://lin.ee/1QUzEX4nI

- [ ] 應可送出「全新文字訊息」
    - [ ] 同意送出訊息後就會送出訊息，並得到 AI reply
- [ ] 應可送出「全新影音訊息」
    - [ ] 同意送出訊息後就會送出訊息，並得到 AI reply
- [ ] 送出「沒回應」的舊訊息，應可顯示 AI reply
- [ ] 送出「有回應」的舊訊息，應自動回傳回應

##### ⛔️ Release Blockers

Token timeout 訊息出不來！
- 即使調短了 timeout 也不會出來！

:::warning
連 API 一起先暫緩 release
:::

##### 未竟項目

- LINE 有改變部分影片的分享方式 [name=nonumpa]
- video > 32MB --> timeout (Google Cloud Run payload size)
- 遭遇 loading indicator 結束後也沒有 token collector 的問題 [name=mrorz]

## Badge

> EJ
> https://g0v.hackmd.io/@cofacts/rd/%2Fzx_Au6iiRN601tnMK7gx3A


## CCPRIP

### [Op] Automated spam removal

> Design doc: https://g0v.hackmd.io/@cofacts/rd/%2Fum7DyY_ESbu2LL78kLw3pg

### [Comm] AI transcripts

> Last week: https://github.com/cofacts/rumors-api/pull/361#issue-2839000967

Pending items
- test on various datasets
- apply to old, invalid transcripts

### [Comm] Communication 

2/11 採訪
- NPO Hub 場地已借
- 可以提：種族/民族主義傳播模式。用「日本人反對沖繩獨立」來 justify 中國人反對台灣獨立。沖繩位置的戰略地位。

[SITCON 2025] 社群攤位申請邀約
- 時間：2025 年 3 月 8 日禮拜六
- 地點：中央研究院 人文社會科學館
- 參與人數：約莫 1200 位
- 受眾：90％ 為學生
:::success
Johnson 可以去
bil 不行
:::

## AI reply feedbacks analysis

100+ feedback on new AI responses
- 23 downvotes out of 145 submissions
    - 16% downvote, 84% upvote

例子
- 網傳黃仁勳公開信 https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/IOcctZQBYrjt7MSMA0tj
    - 4 人覺得沒用，7 人覺得有用
    - 其實重點是這是網傳黃仁勳公開信，內文分析沒啥幫助
- 大 S 自動回應 https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/1eevyZQBYrjt7MSM4mRy
    - 1人覺得模稜兩可，給了負評
    - 其他 5 人覺得有幫助，給了正評
- AI 假影片賀歲 https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/7-dYk5QBYrjt7MSMmx_Q
    - 語音辨識沒很準
    - somehow 也有 2 人覺得有用 XD
- 中天街訪 https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/Ted9oJQBYrjt7MSMljJG
    - 1 人覺得有幫助、1 人覺得沒幫助
    - 單純只有文字。沒有使用到影像部分（街訪 context）
- 網傳研究報導 https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/nOcstpQBYrjt7MSM9ExB https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/POdjxpQBYrjt7MSMMWGm 、 詐騙回報 https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/DOfmw5QBYrjt7MSM3l0j 、 神秘截圖 https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/vOdpxZQBYrjt7MSMNl_k
    - 1 人覺得沒幫助
    - 但我覺得 AI 做得不錯⋯⋯

----

- 如果 AI 自動回應也用上 visual (改用 Gemini)，對 upvote 比率的提升可能有限
    - 不確定 Gemini 本身是否比 gpt-3.5-turbo 好 [name=mrorz]
    - 但 Gemini 可以開 Google search grounding，我也滿好奇是否有幫助 [name=mrorz]

:::success
- Gemini AI reply 可以做，但先放著
- 在 RightsCon 引用此數據
:::

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



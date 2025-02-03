---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250203 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO Hub 出席：bil, nonumpa, mrorz
- 線上出席：T
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

- [x] 應可送出「全新訊息」
    - [x] 選擇「整篇轉傳」後會詢問是否要送出訊息。
    - [x] 同意送出訊息後就會送出訊息，並得到：
        - [x] Cofacts article page 按鈕
        - [x] AI reply
        - [x] 寫理由的按鈕
        - [x] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [x] 送出「沒回應」的舊訊息，應可顯示 AI reply
    - [x] 文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以修改理由送出。查看 article page 看理由是否有被送出。
    - [x] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應
    - [x] 選擇回應之後可以幫回應 upvote
    - [x] 可以再次選擇 downvote
    - [x] 選完回應之後，還可以捲回去選其他回應
    - [x] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [x] Rich menu 測試
    - [x] 「教學」可以觸發教學流程

:::success
Wording 也無需調整

2/5 Release if no issue in PR
:::

##### ⛔️ Release Blockers

無

##### 未竟項目

![](https://g0v.hackmd.io/_uploads/BkKOUV0dkg.png =x500)
- batch message queue 沒有在處理完畢時清掉 [name=mrorz]

![](https://g0v.hackmd.io/_uploads/BJQTDVROJg.png =x800)
  - 感覺是兩張圖有時間差，兩張圖一起的 search session ID 蓋掉了前面只有一張圖時的 session，所以「好，請繼續」失效了 [name=mrorz]
    - 應該是以前遇到這種情形，會因為都默默分析所以不會有這件事，但現在會在分析前主動說「會花點時間」，所以這種「前一張在分析了，第二張才進來」的現象變得明顯 [name=mrorz]
  - 「好、請繼續」跟下面的請問確實是同時出現的 [name=nonumpa]
  - 理論上，下面的「請問這 2 則訊息」會吃掉前一則的「好，請繼續」選項。上面這個現象應該是 race condition [name=mrorz]

:::info
第一個問題開票
第二個 race condition 可能解不了
:::

### :eye: Under review
- LINE bot - long response handling https://github.com/cofacts/rumors-line-bot/pull/401
- API (WIP) - LLM transcript https://github.com/cofacts/rumors-api/pull/359


## CCPRIP

### [Op] Automated spam removal

> Design doc: https://g0v.hackmd.io/@cofacts/rd/%2Fum7DyY_ESbu2LL78kLw3pg

### [Comm] AI transcripts

Experiments
https://g0v.hackmd.io/@cofacts/rd/%2Fwkx286lmTDaFUpgRhnUawQ#Gemini-Experiments

Todo items
- 蒐集 test dataset 做 prompt engineering
  - 聲音跟影像都沒啥字的
  - 影片字幕跟聲音不一致
  - 字幕跟影片聲音一致、語言相同
  - 翻譯字幕
  - 台語、法語

## AI reply feedbacks analysis

:::warning
沒時間，下週討論
:::

100+ responses on new AI responses
- 23 downvotes out of 145 submissions
    - 16% downvote, 84% upvote

例子
- 網傳黃仁勳公開信 https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/IOcctZQBYrjt7MSMA0tj
    - 4 人覺得沒用，7 人覺得有用
    - 其實重點是這是網傳黃仁勳公開信，內文分析沒啥幫助
- 大 S 自動回應https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/1eevyZQBYrjt7MSM4mRy
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



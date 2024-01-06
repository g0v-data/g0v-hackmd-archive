---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20231122 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：mrorz, bil, nonumpa, cai, T, 4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :robot_face: rumors-line-bot

- [1] [Simplify postback handler signatures #372](https://github.com/cofacts/rumors-line-bot/pull/372)
- [2] [simplify text handlers as well #371](https://github.com/cofacts/rumors-line-bot/pull/371)
- [3] [Move selectedArticleId from context to action payload #369](https://github.com/cofacts/rumors-line-bot/pull/369)
- [4] [Fix choosing reply action](https://github.com/cofacts/rumors-line-bot/pull/373)

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 應可送出「全新訊息」
    - [x] 問訊息來源時選擇「我自己打的」會被擋下。
    - [x] 選擇「整篇轉傳」後會詢問是否要送出訊息。
    - [x] 不同意送出訊息後可以收到感謝。
    - [x] 同意送出訊息後就會送出訊息，並得到：
        - [x] Cofacts article page 按鈕
        - [x] 寫理由的按鈕
        - [ ] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面
        - [x] 「分享到 Facebook」、「分享到 LINE」且可以正常運作
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以再打開理由視窗，此時會載入上次填寫的理由。修改理由送出後，查看 article page 看理由是否有被送出。

- [x] 送出「沒回應」的舊訊息，應可送出新理由
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
    - [x] 「設定」更改後再次打開，應該會保留原本設定
    - [x] 「教學」可以觸發教學流程

- [x] Bug https://github.com/cofacts/rumors-line-bot/issues/327 should be fixed

- [x] 群組測試
    - [x] 在群組中可以觸發 chatbot


##### ⛔️ Release Blockers
##### 未竟項目

## 小聚檢討

> 小松果 https://g0v.hackmd.io/9dUXtimbTTiDM65OuUnYUw

## CCPRIP

### [Comm] 查核協作者培訓：徵詢講者

現況
- 2 個月一次
- Cofacts WG 處理場地食物、推播、宣傳文案
- MrOrz 主講

想要新增的部分
- 社群講者自願舉辦
    - 自選時間地點、找小幫手
    - 時間盡量避免與 Cofacts WG 主辦的小聚重疊，避免分身乏術無法支援
    - 自行準備宣傳文案或其他宣傳方式
- 形式與內容
    - 僅需充分讓參與者知道「評價」「補充」「回應」的運作原理，並且確實實作
    - 其餘形式（長度、安排方式、穿插介紹之內容）不拘。
- Cofacts WG 支援的部分
    - 場地食物「費用」
    - LINE 推播現成文案
    - 線上 on-call 技術協助

> 類似過去出十傑講課的做法 [name=mrorz]

- 不會取代 Cofacts WG 自己舉辦的雙月培訓 [name=mrorz]
- 在雙月培訓之外增加社群講者舉辦的培訓 [name=mrorz]
- 那講者要先來這邊講一次嗎？[name=cai]
    - 如果來過查核協作者培訓，會比較知道我們如何達成「充分讓參與者知道「評價」「補充」「回應」的運作原理，並且確實實作」這件事 [name=mrorz]
    - 知道了 Cofacts WG 版本的做法之後，社群講者可以自行發展內容
    - 需要討論的話我們可以一起討論
- 政黨類的來申請怎麼辦 [name=cai]
    - 確實可能會需要多解釋一些 [name=bil]
    - 但實際上因為要投入資源，可能沒有那麼容易發生 [name=bil]
    - 可以理解這個 concern，不過有這個狀況的話，或許另一個政營的人也會考慮來辦？[name=mrorz]
        - 想得太美ㄌ [name=bil]
    - 如果發生，大概是市議員或里長等級吧？ [name=cai]
    - 我們的教材公開，如果他們真的想要幫自己培養「網軍」，那他們不靠我們提供的支援也能達成 [name=mrorz]
    - 如果要我們支援，那我們可能以 Cofacts LINE 推播只能是 Cofacts 相關事務、參雜其他東西有可能會讓我們違反與 LINE 的合作回絕 [name=mrorz]
    - 但我們人也不一定會在那裡控場，不確定有沒有參雜其他東西 [name=bil]

:::warning
大家回去想想這個 concern 怎麼 mitigate
~~MrOrz 後續：在 FB / Slack 公告徵求需要支援辦培訓這件事~~
:::

### [Comm] Transcript

> @nonumpa
測試ing，下週 PR

### [Comm] Multimedia support

影片縮圖、聲音 preview 開 good first issue
- API 有 ffmpeg 可以用了


### [Infra] Google cloud billing

- 有台灣發票
- 目前約 40 USD / mo
    - 未來搬移更多服務後會更高
- 建立 Cofacts 專用 billing account 填 OCF
    - 目前定捐 5000 TWD / mo
- MongoDB 現在是付錢給 MongoDB 公司，但[好像可以轉成在 GCP 支付](https://www.mongodb.com/docs/atlas/billing/gcp-self-serve-marketplace/)；未來 [Elasticsearch 亦同](https://www.elastic.co/guide/en/cloud/current/ec-billing-gcp.html)
- 另外 Linode（80USD/mo）、Redis 之類的還是沒發票，另外處理
- 問題：invoice 裡面有 VAT number 就可以免除 20% 嗎？還是境外服務就是 20%？

:::success
MrOrz 問 Rock
:::

## Hypercerts 回溯公眾投資

- 12/9 11:30 要[簡報拉票（7min）](https://heptaedu.notion.site/QV-ft-12-g0v-92023140672a47a881fcddef3b153d07)
- 不會去大松的要提供 email 才能投票
- 出席：MrOrz

## g0v summit
- 社群軌：bil 會開一個 panel discussion 

:::success
bil follow-up
:::


---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240110 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：MrOrz, cai
- Workis：bil, vickie 記者 8 人, nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API

- API fix https://github.com/cofacts/rumors-api/releases/tag/release/20240104


### :rocket: Staging

#### :electric_plug: API
- [Rewriting spammer reply](https://github.com/cofacts/rumors-api/pull/331) [name=eliot]++
- [Collab server tests](https://github.com/cofacts/collab-server/pull/5) [name=nonumpa]++

#### :robot_face: rumors-line-bot
- （上週測過但有問題的）[Refactor bubbles](https://github.com/cofacts/rumors-line-bot/pull/378)
- （上週測過但有問題的）[Multiple msg handling](https://github.com/cofacts/rumors-line-bot/pull/379)
  - 修復「查看這篇的回應」故障問題：主因是 choosingArticle 原本會讀 `context.msgs[0]` 來紀錄 event 到 bigquery，「查看這篇的回應」是新的 context 因此 `context.msgs` 為空。
  - 此 PR 改寫邏輯，只有確定 context 恰有一個 msg 的狀況下才會讀取`context.msgs[0]`
  - 選擇資料庫訊息的 wording 已更新
  - 「有 0,3 則」bug wording 已修復
- [README update](https://github.com/cofacts/rumors-line-bot/pull/381) [name=jtsaich]++
- [Article & reply time](https://github.com/cofacts/rumors-line-bot/pull/382) [name=jtsaich]++

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 應可送出單則「全新圖片影片」
    - [x] 會詢問是否要送出訊息。
    - [x] 不同意送出訊息後可以收到感謝。
    - [ ] 同意送出訊息後就會送出訊息，並得到：
        - [x] Cofacts article page 按鈕
        - [x] AI reply (依照逐字稿內容)
        - [x] 寫理由的按鈕
        - [x] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面
        - [x] 「分享到 Facebook」、「分享到 LINE」且可以正常運作
    - [x] 剛才送出的訊息應該要在「查過的訊息」列表

- [ ] 送出多則訊息（圖文）
    - [x] 全部訊息都不在資料庫
        - [x] 詢問是否要送進資料庫
        - [ ] 拒絕的話就全數停止
        - [x] 確定的話就會送出訊息，顯示查詢結果
            - [x] 查詢結果會包含剛才送出的訊息
            - [x] 選擇剛才送出的訊息（還沒回應）會顯示 AI reply
            - 已知：只有 text messasge 會顯示 AI reply --> 未盡項目
        - [x] 剛才送出的訊息應該要在「查過的訊息」列表
    - [x] 部分訊息不在資料庫
        - [x] 詢問是否要送進資料庫
        - [x] 確定的話就會送出訊息，顯示查詢結果
        - [x] 剛才送出的新訊息會出現在「查過的訊息」列表
        - [ ] 從點擊現有訊息後，現有的訊息也會出現在「查過的訊息」列表
          - 不會。

    - [x] 全數訊息都在資料庫
        - [x] 直接顯示查詢結果
        - [x] 剛才查的訊息，無論是否有在資料庫，都應該要在「查過的訊息」列表

- [x] 送出「資料庫內有多則相似」的單則舊訊息，會列出相似訊息
    - [x] 若為圖片，會顯示圖片
    - [x] 如果目前查詢的不在茲料庫，會列出相似訊息、「沒有我查的訊息」選項
    - [x] 選擇「沒有我查的訊息」選項會詢問是否要送進資料庫


##### ⛔️ Release Blockers

無

##### 未竟項目

- 如果沒出處，就沒有回應日期 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_36f3f036b953385de5d1973e9f94c0c3.png)
  - 可以移到下面「⬆️ 綜合以上，回應者在 2023-12-12 認為它不在查證範圍。」
  - https://github.com/cofacts/rumors-line-bot/issues/385
- 先用其他 type 寫出處後，改成不在查證範圍，再送出，LINE 會顯示出處 [name=cai]
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8a51f37e206102ef351038051b994829.jpg)
  - https://github.com/cofacts/rumors-line-bot/issues/386


#### :globe_with_meridians: Site

- [Donation link & footer for mobile](https://github.com/cofacts/rumors-site/pull/557) [name=Simon]++
- (Actually API, can test on site) [Allow empty slugs](https://github.com/cofacts/rumors-api/pull/330) [name=Jade]++
- [Add fallback when terms fail to load](https://github.com/cofacts/rumors-site/pull/558)

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] **On mobile**, can access terms & donation link
- [x] Can view User Agreement from new footer

**登入**下檢測：
- [x] Can edit slug and save
- [x] Can remove slug and save

##### ⛔️ Release Blockers

無

##### 未竟項目

- remove slug 後 user link 不會更新，按 F5 會壞掉 [name=cai]
  - 應該也要 redirect 到 ?id=xxx 的 page 避免此狀況
  - 但這比較少發生，可以另外開票做 [name=mrorz]
  - https://github.com/cofacts/rumors-site/issues/563


### :eye: Under review

- [Add fallback when terms fail to load](https://github.com/cofacts/rumors-site/pull/558)

## 大松檢討

https://g0v.hackmd.io/@cofacts/meetings/https%3A%2F%2Fg0v.hackmd.io%2FTnZpbsAeT1GGPcTStcl8Kw%3Fview

- 帶板子很清楚

Left over items
- Ground truth 改 Vertex AI 結構 https://github.com/cofacts/ground-truth/pull/2
  - 詢問中：我是否可以 proceed 還是要等他
- Too many feedbacks issue https://github.com/cofacts/rumors-site/pull/556
  - 答應要修改 [name=marcuss]++

## CCPRIP

### [Op] Transcript spam
> nonumpa
> https://g0v.hackmd.io/vKCvrqSQTlm7GEx9MAXGaw?view#op-Transcript-spam-處理

- https://github.com/cofacts/rumors-site/pull/559

### [Comm] Cooccurrence


- [x] Fix blocker & bugs
- [x] 大松
- [x] 選前週會 test & release (如果沒問題)
- [ ] Implement website display cooccurrences
- [ ] 選舉
- [ ] 實作 ASKING_CONTEXT (Optional?)


## DDoS attack mitigation

Summary: https://drive.google.com/drive/folders/1_g5QAg8X9zioEmoZ3BfSGDO9Adp71aMg?usp=sharing (Open)
Downtime: 15:28 ~ 15:42 共計 14 分鐘

### 過程

- 15:28 Cloudflare monitor 回報服務全數下線 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e09c77cd040e7689f94dc773ad85a0e9.png)
- Cloudflare 瘋狂洗版 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a684737519051ca06653c4291ede0904.png)
- 15:32 關 notification, 分析中
  - Server 上的 load ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_006779618708243aee80caf4e2779693.png) ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_045d2cad1387f7b6655886cf6ccf7c72.png)
- 15:42 - 設定 WAF 後服務全數恢復

### 討論

- 投資詐騙：前幾天有人來 spam 這一頁，輸入協同造假內容 https://github.com/cofacts/takedowns/blob/master/2024/0105-cib.md
- Analytics 有影響嗎 [name=nonumpa]
  - 沒有，看起來不是瀏覽器打的
- Cloudflare notification 也太頻繁⋯⋯
  - 關閉 DDoS Alert 的 notification，有 downtime alert 就好
- Cloudflare ddos protection ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9f58b2b4aad80bfa546987351490eaee.png)
  - WAF 設定：加了一個要擋的 path

## Facebook privacy terms review

- 每年都會檢查 privacy
- fix

## 徽章

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_659a2c65c337a4df0ac70f0ee8dcecc7.png)

- 縮小成左右 2cm
- 不打樣直接做


## 放大視野 follow-up

影片已經上架
- https://youtu.be/11Hqe5rjA7I
- https://www.youtube.com/watch?v=lYL4SohQp70

（Youtube 有自己空耳一個 transcript）

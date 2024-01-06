---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20231018 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：mrorz, bil, nonumpa, T, zoey, 維妞
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :electric_plug: API
Adding non-null to Article and Reply and ArticleReply
https://github.com/cofacts/rumors-api/pull/320

Only include high confidence paragraphs in OCR
https://github.com/cofacts/rumors-api/pull/321




#### :robot_face: rumors-line-bot

Rewrite webhook handlers with Typescript
- https://github.com/cofacts/rumors-line-bot/pull/366
- https://github.com/cofacts/rumors-line-bot/pull/365

Remove `selectedArticleText` and `selectedReplyId` from context
- https://github.com/cofacts/rumors-line-bot/pull/368

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 應可送出「全新訊息」
    - [x] 問訊息來源時選擇「我自己打的」會被擋下。
    - [x] 選擇「整篇轉傳」後會詢問是否要送出訊息。
    - [x] 不同意送出訊息後可以收到感謝。
    - [x] 同意送出訊息後就會送出訊息，並得到：
        - [x] Cofacts article page 按鈕
        - [x] 寫理由的按鈕
        - [x] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面
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
    - [ ] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [x] 送各種圖片訊息進資料庫，可以正確 OCR


##### ⛔️ Release Blockers

##### 未竟項目

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8518dd71826e2e2297cb8b5fa2240b0d.png =x200)
- `@imygopen` 已經失效了（沒付錢 XD?）
- 換成真的 ID

送文字也會 timeout
- 純文字無 URL
- extend timeout to 1 minute
  > Reply tokens must be used within one minute after receiving the webhook. Use beyond one minute isn't guaranteed to work.
  > https://developers.line.biz/en/reference/messaging-api/#send-reply-message

舊的圖的逐字稿不見了
- 沒有歷史紀錄 [name=nonumpa]
- 原因不明 [name=mrorz]

#### :globe_with_meridians: Site

- Marcuss++! https://github.com/cofacts/rumors-site/pull/551

##### Testing checklist

https://dev.cofacts.tw

- [x] 未登入時，無法開啟「我想補充」輸入框
- [x] 登入後，可以開啟「我想補充」輸入框並輸入內容


## Hypercert 回溯公共投資

> 給參與者的說明書
https://docs.google.com/document/d/1SohXAnJh68R7YgLBc6g0KEEIrb06IbIypytW6Xso53w/edit
>
> Test spreadsheet https://docs.google.com/spreadsheets/d/184UR3jZAcDZFwOvQfoEASvyF7dlBmDkq-jJ0BmP1uJE/edit#gid=0

- 可能還是會改成列出所有 article reply feedback，再用 sheet 公式計算 +1、-1 人數

:::success
- Cofacts 錢包：https://optimistic.etherscan.io/address/0xB0d82dAB5Bd13d1a91Aadef498D0ec84c29336F2
- mrorz: sync
- bil: sync
:::

## 一起辦謠言惑眾獎

> From MyGoPen Robin
> - 過去 https://www.mygopen.com/p/award.html
> - 票選結果 https://www.mygopen.com/p/blog-page_86.html
> - 時程
>   - 4/2 前產出入圍名單
>   - 4/2 群眾投票
> - 期待
>   - 一起產出入圍名單（入圍名單含括 Cofacts 資料庫）
>   - 要是「有被破解的謠言」才會入圍
>   - MyGoPen 會去跟贊助單位拉抽獎

- 好 [name=bil]
- Cofacts Analytics 排名一整年的 [name=bil]

:::success
回覆 Robin
:::

## CCPRIP

### [Infra] Migrate to Cloudrun

- EN & JA production chatbot now on Cloudrun
- Nginx 忘記拔掉，導致 2023/10/15 22:00 - 10/16 09:40 [機器人無法用](https://hackmd.io/i0GcWSSVQNeDQ_OBebyk6Q#20231015-2200---1016-0940-Chatbot-not-accessible)
- Redis email notification
  > The number of connections for your database has reached 93.33% of the connections limit.

### [Comm] crowd-sourced transcript

> https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ
> [name=nonumpa]
> 

Prosemirror 開票：https://github.com/cofacts/rumors-site/issues/550

- 做 Colab server test [name=nonumpa]

### [Comm] AI transcript

- OCR Threshold 已調降到 0.75，PR 變更變少

#### Migration

- 還沒繼續

#### Whisper hallucination

開票：https://github.com/cofacts/rumors-api/issues/322

### [Comm] Article group / cooccurrence implementation

- https://github.com/cofacts/rumors-line-bot/pull/369 打算修 https://github.com/cofacts/rumors-line-bot/issues/327 但還沒做完 [name=mrorz]

## 大松檢討
> https://g0v.hackmd.io/hb5doTr1Re2OjGFCO2Ob8w#%E5%8D%94%E4%BD%9C

## 檢舉處理

- https://cofacts.tw/article/ieq9mmkmhq9l 個資
  - 無法確認檢舉者是否是當事人、只有一人回報 [name=mrorz]
  - 先放著 [name=bil]
- https://cofacts.tw/reply/WfWzIIsBAjOeMOkltBBR 疫苗陰謀論者
  - 去社群問
  - 「一堆"帳號"不做功課就說這些是假的」與下面的東西是針對回應的回應，並非針對原始訊息。
  - 問大家 claim 是否確實是 false
  - 這應該放在評價，而非回應，先例不該開，不然大家就都用回應回回應 [name=bil]
  - 如果內容就是有錯誤解讀，那就符合散佈不實資訊，可以逕行下架 [name=T]

## TFC 公民查核者計畫

- TFC 做認證課程 [name=orz]
  - 希望有一個只有認證的人才能發表查核回應的園地 [name=summer]
  - 認證是任何人都可以來上課取得的，所以公平 [name=summer]
  - MrOrz propose: 如果是認證後的人有個 Badge 如何 --> Summer 覺得也不錯
- 維持開放但有 badge 很理想而正面 [name=bil]
- 有 badge 的人寫的東西排比較前面如何 [name=bil]
  - 可能要考慮有 badge 的人拿到 badge 之後寫很爛的狀況 [name=orz]
  - 排序不變，但有 badge 的回應有特別的顏色、或特別的標記。API 也會有，第三方 bot 也能自行調整顯示方式。
- 工程上的困難度？ [name=bil]
- 可以先請使用者手動改名 [name=bil]
  - 程式不用調整 [name=bil]
  - 十傑的做法 [name=mrorz]
- 可以視為 organization? [name=mrorz]
  - 允許小帳？ or 切換以 orgnization 身份發文與否
- 有 badge 的人若違反某些 rule 可以被申訴
  - 被申訴成立太多次就拿掉 Badge [name=T]


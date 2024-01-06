---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20200805 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：nonumpa, gore, mrorz, bil
:::

## Cofacts Next! 追蹤

- [收尾] Chatbot notification
    - MongoDB Atlas 正常運作中
        - 400+ `userSettings`, 1400+ `userArticleLink`
    - 過去對話紀錄轉 userArticleLink
        - 對話紀錄 get
        - script: https://github.com/cofacts/rumors-line-bot/blob/dev/src/database/backtrack.js
        - 先備份 production 資料庫？
    - Progress
        - ~~8/5 前放入 old user article link~~
        - 8/5 討論 rich menu、啟動推播 cron job 但預設不把使用者通知啟動（只啟動部分人的通知）
        - 8/6 release rich menu
        - 8/13 看看通知的狀況（頻率、cron job 執行狀況、使用者回應）
    - MongoDB backup mechanism
        - owner: GGM
        - 是否需要 read-only user?
        - Mongodump --> 到哪裡？GCS?
        - Plan

- Article analytics from GA
    - Owner: Zoe
    - Tracking board: https://github.com/orgs/cofacts/projects/7
    - PRs: API * 4 under review - https://github.com/cofacts/rumors-api/pulls
    - Plan: 8/10 for API, 9/7 for UI

- `ArticlePageLayout` refactor
    - Owner: MrOrz
    - Spec: https://g0v.hackmd.io/h8rP0TOGTh2Clxi_Oi_QKw
    - Plan
      - 2nd PR:
        - 主 PR: https://github.com/cofacts/rumors-site/pull/288 8/9
      - 3rd PR: 8/15 [萌典松](https://g0v.hackmd.io/-KiPYTO3T96V-KJM_dRdyw) 做做看⋯⋯

- User ID refactor
    - Owner: MrOrz
    - Spec: https://g0v.hackmd.io/ZcoUOX_-RQSkJyl5xz4_Zg?view#%E6%96%B9%E5%90%91-2-%E9%87%9D%E5%B0%8D%E6%AF%8F%E5%80%8B-backend-user-%E9%83%BD%E7%94%A2%E7%94%9F%E4%B8%80%E5%80%8B-user-document
    - Plan: GG

- 教學頁 spec
    - owner: Lucien
    - ETA：

## 討論事項

### RSS URL

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0ba9e2b82831c6e4cd5ff57cc9b16861.png)


原 article list URL: 162 byte (但 REPLY_BY_ME 還另外需要 user id)
```
filters=REPLIED_MANY_TIMES%2CNO_USEFUL_REPLY_YET%2CREPLIED_BY_ME&types=OPINIONATED&categoryIds=lT3h7XEBrIRcahlYugqq%2Ckj287XEBrIRcahlYvQoS%2CmD2n7nEBrIRcahlYLAr7
```

> 但這個會被 UI 設計的 URL 影響，有點麻煩。如果是 API query 會用的 json 的話彈性最大，因為 cofacts-api 的 filter 不太會變動。 [name=mrorz]

query json：358 byte
```
{"filter":{"replyRequestCount":{"GTE":1},"categoryIds":["lT3h7XEBrIRcahlYugqq","kj287XEBrIRcahlYvQoS","mD2n7nEBrIRcahlYLAr7","mj2n7nEBrIRcahlYdArf"],"replyCount":{"GTE":3},"hasArticleReplyWithMorePositiveFeedback":false,"articleRepliesFrom":{"userId":"AVqVwjqQyrDaTqlmmp_a","exists":true},"replyTypes":["OPINIONATED"]},"orderBy":[{"lastRequestedAt":"DESC"}]}
```

json + urlencode: 520 byte
```
%7B%22filter%22%3A%7B%22replyRequestCount%22%3A%7B%22GTE%22%3A1%7D%2C%22categoryIds%22%3A%5B%22lT3h7XEBrIRcahlYugqq%22%2C%22kj287XEBrIRcahlYvQoS%22%2C%22mD2n7nEBrIRcahlYLAr7%22%2C%22mj2n7nEBrIRcahlYdArf%22%5D%2C%22replyCount%22%3A%7B%22GTE%22%3A3%7D%2C%22hasArticleReplyWithMorePositiveFeedback%22%3Afalse%2C%22articleRepliesFrom%22%3A%7B%22userId%22%3A%22AVqVwjqQyrDaTqlmmp_a%22%2C%22exists%22%3Atrue%7D%2C%22replyTypes%22%3A%5B%22OPINIONATED%22%5D%7D%2C%22orderBy%22%3A%5B%7B%22lastRequestedAt%22%3A%22DESC%22%7D%5D%7D
```

json-url (lzma + base64): 332 bytes
```
XQAAAAIsAQAAAAAAAABBKYjGk5HEXfadWXKw7jepkVvpHoaw6thdjhrr-b1XehFIp1i0lfNrdYZgFkEbF3OF5gn8efegcgyfPNxJUo1ugsbXwWOwRZ5d67whl8PiANl3KmDjNbsg1xWrJY5S3_cdF2twLn2_u5RKgHrQE-DPp_568wT_wym2FAQlLV6pr-bhqJEwOsubFr4Ih4vp37oJEVyT1kjMcRSLBlEycFbnSkTK9sVPQyWfwMnc5634qeydZhieKsknWJI7U7oWtEfsvqnk5boOkkzM0EVC_PneGyjKvck3KpXqE25WwyyIF411o32v_v_mSwQA
```

ljharb/qs: 535 byte
```
filter%5BreplyRequestCount%5D%5BGTE%5D=1&filter%5BcategoryIds%5D%5B0%5D=lT3h7XEBrIRcahlYugqq&filter%5BcategoryIds%5D%5B1%5D=kj287XEBrIRcahlYvQoS&filter%5BcategoryIds%5D%5B2%5D=mD2n7nEBrIRcahlYLAr7&filter%5BcategoryIds%5D%5B3%5D=mj2n7nEBrIRcahlYdArf&filter%5BreplyCount%5D%5BGTE%5D=3&filter%5BhasArticleReplyWithMorePositiveFeedback%5D=false&filter%5BarticleRepliesFrom%5D%5BuserId%5D=AVqVwjqQyrDaTqlmmp_a&filter%5BarticleRepliesFrom%5D%5Bexists%5D=true&filter%5BreplyTypes%5D%5B0%5D=OPINIONATED&orderBy%5B0%5D%5BlastRequestedAt%5D=DESC
```
:::success
左上角 time range 、右邊 sort by most asked:
RSS 不支援，所以要自動擋掉、跟使用者說不支援這些選項
:::

### 上次未竟事項開票
> https://g0v.hackmd.io/r3NK7xssSwCNPFxthlw7tA#%E5%A4%A7%E6%9D%BE%E6%AA%A2%E8%A8%8E

- Hide obsolete category - https://github.com/cofacts/rumors-api/issues/192
- category UI 不好用 - https://github.com/cofacts/rumors-site/issues/306
- 每頁 25 個 article - https://github.com/cofacts/rumors-site/issues/307
- Preview URL titile in article list - https://github.com/cofacts/rumors-site/issues/308
    > 最近剛好在重整 article list
週日 4000 提到，文章列表裡面希望可以放文章超連結的 title。
下面是我用志超 search result 的 UI，拿掉 URL description 之後試排的結果。我比較喜歡沒有 URL 的版本 XD [name=mrorz]
    - Desktop https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/Cofacts-website-MrOrz-s-copy?node-id=2675%3A221
    - Mobile https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/Cofacts-website-MrOrz-s-copy?node-id=2673%3A220
- Reload preview API - https://github.com/cofacts/rumors-api/issues/193
    > We can have 2 APIs, both block non-logged in users.
    >
    > The first API update the article's `hyperlink` with latest fetch result in `urls`.
    > The second API fetches new scrap result
    > 
    > 重整預覽應該夠直觀 [name=gore]
    > 我不會想按，因為我沒有意識到說按下去他會改變 [name=bil]
    > 可是我想按 [name=mrorz]
- Use "OK" button instead of "X" in mobile article filter - https://github.com/cofacts/rumors-site/issues/309
- Reason submission button jumps around when clicking - https://github.com/cofacts/rumors-site/issues/310
ＲＳＳＲＳＳ

### RSS 訂閱教學影片
> 1 分鐘內的短片
> 放在 UI 裡：https://github.com/cofacts/rumors-site/pull/305

- 形式： Google slide 投影片 + 字幕 + 旁白。
- 強調是透過 IFTTT ；略過 IFTTT 帳號註冊步驟，但要告知使用者要「免費」註冊 IFTTT。
- 第一幕就放接好之後會長怎樣的圖、最後再首尾呼應

#### Slack 版

> （Cofacts -- IFTTT -- Slack 示意圖、以及 IFTTT 在 Slack 回報的截圖）
> 透過 IFTTT，您可以在 Slack 上收到最新的 Cofacts 回報訊息。
> 
> （zoom in 到 IFTTT）
> 首先，您要先免費註冊 IFTTT 帳號。
> 
> （轉到 Cofacts，hoax for you 設定 filter，按下訂閱、選擇 IFTTT 訂閱）
> 在 Cofacts 找到您想訂閱的訊息列表、設定好您想要訂閱的主題，然後選擇透過 IFTTT 訂閱。
> 
> （複製 Feed URL、按下訂閱）
> 在視窗中複製 Feed URL 並按下「訂閱」
> 
> （IFTTT 巨大 switch UI）
> 這會帶你到 IFTTT 、啟用此 applet。
>
> （LINE notify 設定頁面）
> 設定您要接收訊息的 Slack workspace 以及 channel。
> 
> （LINE RSS 設定頁面）
> 最後，在「Feed URL」的地方貼上剛才複製的 Feed URL，按下確定，就完成訂閱囉！
>
> （Cofacts -- IFTTT -- Slack 示意圖、以及 IFTTT 在 Slack 回報的截圖）
> 之後 Cofacts 的這個列表有新的訊息時，IFTTT 就會將這些訊息傳到你指定的 Slack 聊天室。
> 一起來回應這些被回報的可疑訊息吧！

#### LINE 版 (Telegram 版也類似)

> （Cofacts -- IFTTT -- LINE 示意圖、以及 IFTTT 在 LINE 回報的截圖）
> 透過 IFTTT，您可以在 LINE 上收到最新的 Cofacts 回報訊息。
> 
> （zoom in 到 IFTTT）
> 首先，您要先免費註冊 IFTTT 帳號。
> 
> （轉到 Cofacts，hoax for you 設定 filter，按下訂閱、選擇 IFTTT 訂閱）
> 在 Cofacts 找到您想訂閱的訊息列表、設定好您想要訂閱的主題，然後選擇透過 IFTTT 訂閱。
> 
> （複製 Feed URL、按下訂閱）
> 在視窗中複製 Feed URL 並按下「訂閱」
> 
> （IFTTT 巨大 switch UI）
> 這會帶你到 IFTTT、按下 Connect。
>
> （Connect to LINE 設定頁面）
> 在與 LINE 連接之後，在「Feed URL」的地方貼上剛才複製的 Feed URL。
> 
> （LINE RSS 設定頁面）
> 最後，選擇您要接收訊息的聊天室，或使用 LINE Notify 一對一聊天，按下 Save，就完成訂閱囉！
>
> （Cofacts -- IFTTT -- LINE 示意圖、以及 IFTTT 在 LINE 回報的截圖）
> 之後 Cofacts 的這個列表有新的訊息時，IFTTT 就會將這些訊息傳到你指定的 LINE 聊天室。
> 一起來回應這些被回報的可疑訊息吧！


- IFTTT 的步驟好像不夠清楚 [name=gore]
- 講太明白的話我怕大家不想嘗試，因為 IFTTT 真的有點複雜 XDDD [name=mrorz]
- 如果 env var 沒有 youtube link 的話，可以把 video 先藏起來ㄇ [name=mrorz]


:::success
Do it!

沒影片的話先藏 video
:::


### chatbot 不問來源
> 上週討論＆溯源：https://g0v.hackmd.io/r3NK7xssSwCNPFxthlw7tA?view#chatbot-%E4%B8%8D%E5%95%8F%E4%BE%86%E6%BA%90

LIFF Analytics 上線後 funnel:

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6b32ab5e50eca7fa78ed6dffb1c1f8bb.png)

- 顯示按鈕：`644 + 12 + 120 = 776`
- 成功打開 LIFF：`181` (Conversion rate: 23%)
- 點按 LIFF 按鈕（含陷阱）：`152`（Conversion rate: 84%）

> 「公開訊息」會讓人有個資或訊息被偷看的感覺 [name=bil]
>「公開」這件事情會讓我覺得是連結到自己、是「我這個人公開的」這樣，我就會關掉 [name=gore]
> 如果是「申訴」呢 [name=bil]
> 我還是希望使用者認知到說，這件事情會被攤在陽光下 [name=mrorz]
> 只要不要連結到我身上就行，例如「傳送到公開闢謠清單」[name=gore]
> 「貢獻到公開資料庫」[name=bil]
> 申訴專區呢 [name=mrorz]
> 不太能叫申訴 [name=bil]

> 方案二：請問這個訊息是 LINE 或網路上? 是 / 我自己打的
> or 請問這個訊息是你自己打的嗎? 是 / 別人傳給我的 [name=mrorz]
> 
> （眾微笑點頭，並不表示任何意見）

> 另外也可以在使用者確認公開時，直接跳出 reason LIFF，使用者要按送出才會送訊息（但可以不甜）
> 但是這就會遇到 LIFF 的 conversion rate 只有 23% 的狀況 [name=mrorz]
> 方案一「確認」感覺會讓人比較容易選擇、方案二先問問題，會讓人亂選有一種罪惡感，這樣擋起來比較有效

:::success
「公開」--> 「貢獻」、「資料庫」-->「清單」

方案一、二平手⋯⋯
:::


- - - 
討論至此已經 10pm，接下來是 concall，故散會
- - -


### 誤認 Cofacts 為訊息來源的 case

- 有人把 Cofacts 當成謠言來源：https://www.facebook.com/100004743373440/videos/1661616297339800/
- 3 個人把 Cofacts 當成主辦單位：https://cofacts.g0v.tw/article/2ic0n2moc0ppy
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_be85b0359450b581c2f3a513e7b08b1f.png)
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4250ec14eb4ba71bb88726f62a4014c4.png)
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_147c30edfd00616923683fb4a3810a35.png)


:::info
Any thoughts?
:::

### LINE bot onboarding UX

> 過去的討論：https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2F%40mrorz%2FS1cpqgCpr
> 後來沒有留下成果圖 QQ
> 

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b875d6ca30afbb259c1c8f59006973ec.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_27609bb865e00c8127ee064b9476a2d4.jpg)

### LINE bot menu 討論
> - [20200325](https://g0v.hackmd.io/@mrorz/HkqrDEOLI#LINE-chatbot-rich-menu) Rich menu 選項討論
> - [2018](https://hackmd.io/@mrorz/SyivqlIrf?type=view#Rich-menu) 初次討論 menu
> - [2019](https://g0v.hackmd.io/@mrorz/S1D8FVqf4?type=view#rich-menu-%E8%A3%A1%E9%99%84%E4%B8%8A%E7%AF%84%E4%BE%8B) 討論附上範例的做法（失敗）

功能：

- 我問過的訊息 `https://liff.line.me/1563196602-R1zEXaDB/liff/index.html?p=articles`
- 推播設定 `https://liff.line.me/1563196602-R1zEXaDB/liff/index.html?p=settings`
- 教學（重新觸發 on boarding UX？）

### Reply search 相關討論

:::warning
Lucien 今天請假所以 skip
:::

- Related issue: https://github.com/cofacts/rumors-site/issues/295
- Discussion item see [20200729 meeting note](https://g0v.hackmd.io/r3NK7xssSwCNPFxthlw7tA#Reply-search-%E7%9B%B8%E9%97%9C%E8%A8%8E%E8%AB%96)

## 編輯小聚
> 前次討論 https://g0v.hackmd.io/9qp8dE7dReK2q8FTeP9Feg#8%E6%9C%88%E7%B7%A8%E8%BC%AF%E5%B0%8F%E8%81%9A%EF%BC%9F
> NPO Hub 小松填單 - https://g0v.hackmd.io/@jothon/hsiaothon/

bil: 8 月萌典松的話，可以改辦在 9 月

## :potable_water: Release pipeline

### :star: Released to production

- [0731 website release](https://github.com/cofacts/rumors-site/releases/tag/release%2F20200731)
- [0731 chatbot release](https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20200731)

### :rocket: Staging

No pending items on the rocket :rocket: this week.

### :eye: Under review

- [修正 reply request 無法顯示超過 10 個](https://github.com/cofacts/rumors-api/pull/187)
    - 放了 10 天，預計週四 merge 唷。
- [RSS API](https://github.com/cofacts/rumors-site/pull/304)
- [RSS UI](https://github.com/cofacts/rumors-site/pull/305)

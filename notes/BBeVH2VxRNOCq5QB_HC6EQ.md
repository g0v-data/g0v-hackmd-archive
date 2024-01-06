---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210413 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：mrorz, bil
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API

[2021/4/8 Release](https://github.com/cofacts/rumors-api/releases/tag/release%2F20210408)

#### :globe_with_meridians: Site

[2021/4/8 Release](https://github.com/cofacts/rumors-site/releases/tag/release%2F20210408)

## 小聚檢討

https://g0v.hackmd.io/_CxbPud9QwyR05VJNj7mFQ

- Wifi status?
    - 號碼 > 10 連 classroom，其他連 guest (手動 load balance)
- bug: 沒有username不能改名字 - https://github.com/cofacts/rumors-api/issues/257
- bug: iOS 13 無法使用網站 - https://github.com/cofacts/rumors-site/issues/426
- Generated spreadsheet 應該要改用 cofacts.tw，不能用 cofacts.g0v.tw 不然 iOS 會每次點進去都要重新登入 -- [fixed](https://github.com/cofacts/need-to-check-list-generator/pull/6/files), nonumpa++

## Code for Sch001ing Camp
4/15 @ 崑山科大
三堂課、小學校模式
實作：
- 直接從 article / hoax-for-you page 挑回應過的訊息按 upvote / downvote
- 可能不是情願參加 (?)
- Contribution 格子亮起來
    - 約要 3 個 vote 才會亮起來

## Devs - Q2

[LINE bot 送出流程改版](https://github.com/cofacts/rumors-line-bot/issues/214)
- 目標：更簡單地送出流程、LIFF 不要 send message to chatroom (為 share dialog 做準備)
- 目前 LIFF：
    - `urlToken` / `lineIDToken` 雙身份認證
        - `urlToken`（chatbot 自發 JWT 在 URL）沒有比較省 request，卻有洩漏風險，應被淘汰
        - `lineIDToken` 可以在 external browser 使用，更泛用
    - `articles` 看過的訊息
        - 使用 `sendMessage` 傳回到 chatbot 觸發顯示 article
            - 需要使用者允許，也有[使用者質疑](https://www.facebook.com/groups/cofacts/permalink/2672723192959493)
            - 若 LIFF 以 external browser 開啟，則沒有作用
        - 解方：實作 [LIFF 版 article page](https://g0v.hackmd.io/0RX4MsjRRJmBqJSKVilWMA#article-amp-reply-LIFF)
            - 顯示謠言與回應
            - 用 LINE 使用者身份 upvote / downvote / comment
            - 相關 mutation API, input & output objects 可用 GraphQL API stiching 機制處理？
    - `settings` 設定：已經使用 API 溝通，無 `sendMessage`
    - `source`：送出來源，應該使用[「方案二」](https://g0v.hackmd.io/r3NK7xssSwCNPFxthlw7tA?view#chatbot-%E4%B8%8D%E5%95%8F%E4%BE%86%E6%BA%90)在 chatbot 中完成，較流線化。
    - `reason`：送出理由 / comment，目前使用 `sendMessage`
        - 若照[方案二](https://g0v.hackmd.io/r3NK7xssSwCNPFxthlw7tA?view#chatbot-%E4%B8%8D%E5%95%8F%E4%BE%86%E6%BA%90) 移到最後一步，那用起來就跟 feedback 很像，可以改成用 API 處理。
        - 相關 API（CreateReplyRequest）或許可以用 API stitching 處理？
    - `feedback/yes` 與 `feedback/no`：混用
        - 點入之後會[立刻送 `voteReply` 到 LINE bot GraphQL API](https://github.com/cofacts/rumors-line-bot/blob/dev/src/liff/pages/PositiveFeedback.svelte#L16-L20)
            - `voteReply` API 不帶 article / reply ID，仰賴「同一個 search session」
        - 填寫理由後卻又會 [sendMessage](https://github.com/cofacts/rumors-line-bot/blob/dev/src/liff/pages/PositiveFeedback.svelte#L26-L30) 回到 LINE bot 繼續互動
- TODO breakdown
    1. 移除 `urlToken` 機制
        - [似乎可以無痛拔掉？](https://github.com/cofacts/rumors-line-bot/blob/dev/src/liff/lib.js#L41-L44)
    2. 修改 LINE bot GraphQL API 
        - GraphQL schema stitch `ListArticle`, `CreateReplyRequest` 或直接複製一份 API（如 [`voteReply`](https://github.com/cofacts/rumors-line-bot/blob/dev/src/graphql/typeDefs.graphql#L26)）
        - 應從網址帶 article id, reply id 等參數，移除對 search context 的依賴，透過 UI 設計（顯示正在 feedback 的文章與回應內文）來避免 reply hijacking（針對錯誤文章與回應做評價）
    3. 改寫送出流程為[方案二](https://g0v.hackmd.io/r3NK7xssSwCNPFxthlw7tA?view#chatbot-%E4%B8%8D%E5%95%8F%E4%BE%86%E6%BA%90) 移除 `sendMessage`
    4. 改寫未有回應的 reply request 流程，送出 reply request 後直接顯示[方案二](https://g0v.hackmd.io/r3NK7xssSwCNPFxthlw7tA?view#chatbot-%E4%B8%8D%E5%95%8F%E4%BE%86%E6%BA%90)最後的按鈕 bubble
    5. 改寫看回應的流程
        - 「分享」按鈕與「覺得有用」、「覺得沒用」應該同時出現，「分享」不該被 feedback 擋住
        - 「覺得有用」、「覺得沒用」在 LIFF 內告知已送出，不要再 `sendMessage` chatbot
    6. 實作 [LIFF article page](https://g0v.hackmd.io/0RX4MsjRRJmBqJSKVilWMA#article-amp-reply-LIFF) 
    7. 移除 `sendMessage` scope 以及 [external browser check](https://github.com/cofacts/rumors-line-bot/blob/dev/src/liff/lib.js#L85-L99)

:::info
#### [兩種 auth 機制](https://github.com/cofacts/rumors-line-bot/blob/dev/src/graphql/index.js#L47-L94)：
- authorization: bearer
    - 如果 URL 有 token 就會採此方式
    - token 內有 exp、有 sessionId
    - 若採此方式，會檢測 sessionId 是否與現在使用者的 sessionId 相符，避免使用者點到過老的按鈕
    - URL token 建立於 `getLIFFURL()` 時，獲 feedback/yes, feedback/no, source, reason 頁面採用
    - 因為需要有 session id 才知道 upvote / downvote / source / reason 對象，所以要阻擋 external browser 使用。
- authorization: line
    - 永遠使用最新的 chatbot context
        - 但其實也用不到 context⋯⋯
    - 用在 settings, articles 頁面

`bearer` 機制的誕生是因為送出文章流程時，文章還沒有 ID，且文章很長，只能放在 redis 然後靠 current context 處理。

- 其實可以從 context 換成某個暫存的 ID 放在按鈕的 URI action，使用者回頭點擊按鈕時若 redis 裡這個 ID 指到的資料還在，那還是可以繼續操作
- 除了填寫理由與出處之外，其實其他地方都可以把操作的對象（article, reply）的 ID 用 URI action 傳給 LIFF，根本不用靠 current context 儲存。這樣採 line ID 確認身份即可。

#### Schema stiching

- Remote schema: https://www.graphql-tools.com/docs/remote-schemas/ 可以自訂 executor 用來填入 x-app-secret
- Schema stitching: https://www.graphql-tools.com/docs/stitch-type-merging


:::

### Postponed

- [ ] 驗證使用者 slug
- [ ] 評分回應 profile page tab
    - [ ] 圖：https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/Cofacts-website-MrOrz-s-copy?node-id=2923%3A220
- [ ] 4 月初：公開 profile page 
    - [ ] revert the PR that [hides profile](https://github.com/cofacts/rumors-site/pull/378)
    - [ ] 補充的人的 profile / 名字（figma 已有，開票）
- [ ] Dockerize rumors-line-bot
    - nodejs + tesseract base image + 2-stage build
    - [ ] 然後放到 AWS 用 [ECS](https://aws.amazon.com/tw/ecs/features/) 管 （[estimated pricing](https://docs.google.com/spreadsheets/d/1m_9UeSsSvwX-tFF1Uw2W-7pXie-n1_6bP99TUEFeQ6o/edit?usp=sharing)）
- [ ] 4 月初：deploy API header 讓第三方接取 [name=mrorz]
- [ ] apply 日文翻譯 --> ja.cofacts.org / ja.cofacts.tw

## 防詐顯名

- Cofacts 是 OCF 合作專案，可協助處理
- 介紹 attribution
- 尋找符合內規的替代方案
- 週五 follow-up

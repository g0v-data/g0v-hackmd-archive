---
tags: cofacts, meeting note
GA: UA-98468513-3
---


20241111 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO Hub 出席：Conrad, bil, mrorz
- 線上出席：T, nonumpa, 4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
- Typescript admin script https://github.com/cofacts/rumors-api/releases/tag/release%2F20241107

### :rocket: Staging

#### :electric_plug: API

- https://github.com/cofacts/rumors-api/pull/351
    - Regression of https://github.com/cofacts/rumors-api/pull/338/files

## CCPRIP

### [Op] 外部整合：Admin API

> 最近 Cofacts 有兩個與外部整合的功能：[自動 spam 移除](https://g0v.hackmd.io/@cofacts/rd/%2Fum7DyY_ESbu2LL78kLw3pg) 以及 Badge 發送功能，會需要「只有特定人能存取」的 API 需求
本來自動 spam 移除的「封鎖某使用者」功能，是打算用 Google Pub/Sub 來避免開外部 API，使用 Google 帳號來管理誰能下該指令，但實作的過程覺得
> - 開個 API 要要蓋 topic + subscription 感覺很囉唆
> - 自動 spam 移除這個 use case 更像是 RPC 而非 message queue
>
> 所以想要 propose 一個新方式：
> - 自動 spam 移除的「封鎖使用者」與發送 badge 的 API，都做成 GraphQL mutation 或 Open API ([feTS](https://the-guild.dev/openapi/fets))
> - 這些 API 直接用 Cloudflare Zero Trust 保護起來，必須持有 Cofacts 這裡另外交給呼叫者的 service token 才能存取（之前對 Cloudflare Zero Trust 的研究：https://g0v.hackmd.io/51wwLHgvSUqtBDaP-yAVnA#Alternative-Implement-using-Cloudflare-Zero-Trust）
>
> 由於 Cofacts 這裡本來就有打算在 GraphQL API 這裡也用 api key 之類的機制保護起來的想法，想說先做在新的 endpoint 上試點，等較為熟練 + 時機成熟後再擴到大主要的 `/graphql` endpoint，好像也是個不錯的路徑。
> [name=mrprz]
>
> badge 部分 可以來pilot這個沒問題 [name=EJ]
> 我會偏好OpenAPI 這樣在ZeroTrust設特定endpoint需要service token會比較簡潔 [name=Alex2002]
> 
> 我這裡應該會直接讓 rumors-api 的 pm2 起另一台 nodejs http server 跑 OpenAPI
然後直接用獨立的 admin-api.cofacts.tw 與 admin-dev-api.cofacts.tw 這兩個網域分別指到 production 與 staging 的 OpenAPI
這樣要上 ZeroTrust 也不會影響現在的 api
> [name=mrorz]

- Implement Admin API on rumors-api, start server at port 6000
- Don't add reverse proxy on Nginx; use [cloudflare tunnel](https://community.cloudflare.com/t/can-i-use-cloudflared-in-a-docker-compose-yml/407168/2) instead to ensure all inbound network goes through Cloudflare
- Access: Allow `cofacts.tw` emails & service tokens
    - Different service tokens gets access to different applications (set of APIs)
- Audit logs: Admin API logs authorized user's JWT content (injected by Cloudflare) in console (and collect via GCP logging)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d963e70d60f7562b2170ac56c0da8ed1.png)

預計會有的 host name：
- dev-admin-api.cofacts.tw --Cloudflare tunnel--> cofacts-api-staging:6000 on Staging docker-compose network
- admin-api.cofacts.tw --Cloudflare tunnel--> api:6000 on Production docker-compose network

預計會有的 endpoint：

- `/docs`: Swagger UI generated by [feTS](https://the-guild.dev/openapi/fets/server/quick-start)。允許 Cofacts WG 與 service token 持有者存取。
    - Question: service token 持有者要怎麼在瀏覽器看文件？
- `/moderation` 系列：Cofacts WG 登入者與 Cofacts WG 持有的 service token 才能存取
    - POST `/moderation/blockedUser`: block a user (or update block info). Map to current `blockUser` script.
    - POST `/moderation/article/media`: replace the media of an article. Map to current `replaceMedia` script.
    - POST `/moderation/aiReply`: regenerate AI reply. Map to current `genAIReply` script.
- `/badge` 系列：可發 badge 之組織持其 service token 存取（僅供示意； 實際 endpoint 以 EJ 的 design doc 為準）
    - POST `/badge`: create or update badge
    - POST `/badge/user`: add a badge to the specified user
    - DELETE `/badge/user`: retract a badge from the specified user

### [Op] spam removal automation


> Design doc:  https://g0v.hackmd.io/@cofacts/rd/%2Fum7DyY_ESbu2LL78kLw3pg


### Phase 1: Command ~~via Pub/Sub~~ via admin API

> @mrorz

- Rewrite https://github.com/cofacts/rumors-api/pull/337 to feTS server
    - put server under `src/admin/index.ts`
    - put moderation resolvers under `src/admin/moderation`
- docker-compose: https://github.com/cofacts/rumors-deploy/pull/27/files
- Update design doc to replace pubsub with API + cloudflared tunnel

### Phase 3 Automatic spam detection
> @nonumpa
> 

pr preview

https://github.com/nonumpa/UnityPluginSnippets/pull/2

https://github.com/nonumpa/UnityPluginSnippets/pull/3

- 指令直接打在 PR description 裡 OK
- 不用表格
- Sections:
  - 使用者 + url
  - List or table of 偵測到的內容 + 發布時間
  - 違規樣態（用分類對應到固定的文案）
  - 處置：原 footnote 內容

## [Infra] Migrate to GCE

> https://g0v.hackmd.io/Pq1xffBaQW69lGyrp7JFng?both#Infra-%E8%99%9B%E6%93%AC%E4%B8%BB%E6%A9%9F%E6%89%93%E7%B5%B1%E7%B7%A8

> Follow-up on migrating to GCE: 我發現 Container-Optimized OS 沒有 package manager、不能執行非 dockerized 的 script，也沒有內建的 dcoker-compose 感覺用起來很 hardcore
> 我還是用普通的 debian 好了……XD
> [name=mrorz]

Updated design doc: https://g0v.hackmd.io/BRsJOevWSbyUMBSZEVVWrA#Phase-2-Move-the-rest-of-services-to-GCE

## Langfuse

- On GCE instance (dev or prd 機器) + 便宜的 [Google Cloud SQL](https://cloud.google.com/products/calculator?hl=en&dl=CjhDaVF6TVRFeFpHTTROaTA0TXprekxUUm1aVGd0T0ROak5pMW1PRGs1WTJReE56a3hNbUlRQVE9PRAHGiQ5QzU4RDlCRi1FOTg0LTQ4MzYtODJGRC05MTlEOUI0M0QxMjI)
- Connect with [auth proxy](https://cloud.google.com/sql/docs/mysql/connect-auth-proxy)
    - 現在 linode / vultr 就能用用看
    - 搬家之後資料仍然放 Cloud SQL，不會掉

:::success
Design doc 紀錄
:::

## 「修改重發」功能

> 過去針對「編輯回應」有這些討論：https://g0v.hackmd.io/OC7BneJ3TEGJHge1hWV-0w#%E8%A8%8E%E8%AB%96%EF%BC%9A%E8%AE%93%E4%BD%9C%E8%80%85%E8%83%BD%E7%B7%A8%E8%BC%AF%E5%9B%9E%E6%87%89 （天啊 2020 年）
>
> 還開了[一張票](https://github.com/cofacts/rumors-api/issues/184)想要改 API，不外乎就是要解決
> - 回應會被自己、被別人加到不同訊息下，此狀況下什麼樣的編輯算合理？
> - 編輯後，針對舊文字的 feedback 怎麼辦？
>
> 因此，現在的 status quo 就是請使用者刪掉重發，這樣最單純。
> 我覺得比起「編輯」，其實更容易做的是把「修改重發」自動化，也就是針對現有回應做出「更動」後，系統其實不會動原有的回應，而是
> 1. 新增新的回應
> 2. 把新的回應加到原有回應連結的訊息上（僅限作者自己加的）
> 3. 把原有回應刪除（僅限作者自己加的）
> 也就是現在查核協作者可以自行操作的動作，改成一鍵完成這樣。UX 細節如下：
> - 回應作者在任何自己撰寫的回應上點擊「修改重發」，會被導向到該 reply 的 detail 頁面。
> - reply detail 新增編輯模式，可修改「我認為」分類、內文與出處。
> - 送出按鈕上面的用語為「修改重發」，前面說明文字簡述說，修改後的文案會同時套用到自己所連結的可疑訊息，也就是下方「此查核回應尚被用於以下的可疑訊息」列出的訊息中，由自己加的那些。
> - 按下「修改重發」後，跳出彈窗列出那些會被套用的網傳訊息，以及確認按鈕。
> - 按下確認後，彈窗顯示套用的進度，以及往新回應 detail 頁面的連結。
>
> 以上功能都可以用現有 API 做到，不用開新的欄位，只要改 rumors-site。
> [name=mrorz]

:::success
- Figma mockup for edit UI + dialog
- 開 rumos-site 的票放需求 & Figma https://github.com/cofacts/rumors-site/issues/584
- 標 good first issue
:::

## 文宣 / 印刷品

- 在甦活有儲值
  - 可以印這些 http://www.soho8d.com.tw/Form2/F101.aspx?scroll=1
  - 可以印[衛生紙](http://www.soho8d.com.tw/Form2/F102.aspx?csubid=186)
  - LOGO 貼紙 - 透明 http://www.soho8d.com.tw/Form2/F102.aspx?id=147
  - Slogan 貼紙
    - 脾氣糟的手機人
    > 適時查核？
    > ~~你是有捐錢膩~~
    > 那你來查啊
  - 手拿布條
    - 攤位可用
    - 60x150 10才
    - 薄的 http://www.soho8d.com.tw/Form2/F102.aspx?id=557
      - 畫布、帆布都太重
  - 印春天 Cover photo 作為 banner
    - [100~150dpi 即可](http://www.soho8d.com.tw/Form2/F102.aspx?id=557)

:::success
- 今年沒空，目標 RightsCon 前做完
- 訂規格 --> 設計 --> 下單 --> 拿到東西
- 明年看
:::

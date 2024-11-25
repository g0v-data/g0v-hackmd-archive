---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20241125 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO Hub 出席：
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API

Admin API scaffold release https://github.com/cofacts/rumors-api/releases/tag/release%2F20241125
- https://admin-api.cofacts.tw/ with `/ping` now available

### :rocket: Staging

#### :globe_with_meridians: Site

- https://github.com/cofacts/rumors-site/pull/581

##### Testing checklist
http://dev.cofacts.tw/

檢查 feedback 是否為
- 有文字的在前面，沒文字的在後面
- 都有文字 or 都沒文字：新的在前面，舊的在後面

### :eye: Under review

- Badge schema https://github.com/cofacts/rumors-db/pull/74
- blockUser admin API https://github.com/cofacts/rumors-api/pull/352
    - Unit test: broken after order switch

## 大松檢討

> https://g0v.hackmd.io/@cofacts/meetings/%2FXSpjp40-QEGVAPeTrvxZeQ

## CCPRIP

### [Infra] Downtime

:::info
Record to https://hackmd.io/@cofacts/incidents
:::

### [Infra] DDoS 帳單攻擊預防

[鬼故事 by ihower](https://www.facebook.com/share/p/18HpYzXc1Q/)：

> 大約半年前，我客戶網站上的一張放在 Google Cloud Storage (台灣 asia-east1 區) 的圖片，被 DDoS 攻擊，持續下載同一張圖片(500MiB/s，每秒 8k requests 來自歐美的七個 IP 位址) 持續了兩天。雖然發現後立即加上 Cloudflare 防火牆 (還是免費版即可，早知道就..... 哎) 就擋住了，但仍造成了約 USD 11,000 的鉅額 GCP 帳單，而這平常一個月的流量只需要 USD 15 元。
>
> 後續透過代理商 i 社多次和 GCP 爭取退款或流量費減免，在經歷長達半年的焦慮等待，包括無數次的客服聯繫、反覆確認攻擊細節、通知X部門審查、確認我身份、申請至Y部門、再等待Z部門確認、被拒絕後重送工單 N 次(感謝代理商持續跟進)。最終 Google Cloud Billing Support 的回覆仍是申請失敗，僅爭取到 Google 業務給予的 USD 2000 補助 credits。

Lessons learned by iHower: https://www.facebook.com/ihower/posts/pfbid02NSGjkquioV7TEq5GpTCRnK9uT38NDTqEgzT31x2w8hmTgF5GLZFKWXy3zPzT66sBl

- ✅ 設定帳單提醒
- [在 GCS bucket 前擋 Cloudflare](https://stackoverflow.com/a/35895422/1582110)：好像要[設定 load balancer](https://cloud.google.com/load-balancing/docs/https) 或把[整個 bucket 改名字](https://cloud.google.com/storage/docs/hosting-static-website-http)才能綁網域
    - 直接把 GCS 的網址對外，即使是 signed URL 也是可能被攻擊 

---

#### Possible Solution: GCS bucket --> Cloudflare R2

Thanks to @alex for proposing the idea!

Pros
- [No egress fee](https://developers.cloudflare.com/r2/pricing), class A & B operation 比 GCS 的便宜
- [Sippy](https://developers.cloudflare.com/r2/data-migration/sippy/) incremental migration
    - 可以先只改 rumors-api 輸出 URL 的部分，讓它輸出 R2 URL

Cons
- 未來開發 Gemini transcript 時，傳檔給 Vertex AI 似乎一定要用 GCS，因此 GCS 上傳還是不可少
- Cloudflare 無法開發票（好像要企業版），需走墊款流程
- by bucket 只能設定 [location hint](https://developers.cloudflare.com/r2/reference/data-location/#location-hints)，精確度到「APAC」--> 代表可能會被放到[日本、新加坡、甚至⋯⋯中國？](https://www.cloudflare.com/network/)
- 如果只用 sippy 而不是整個搬去 Cloudflare R2，會有以下兩個問題
    - Double 資料存放費用 (GCS & Cloudflare) --> 但 cost 很少，即使乘二也不貴
    - 如果要下架圖片，要記得改 Cloudflare 這端的圖

## 檢舉怪象

- 「磨告」

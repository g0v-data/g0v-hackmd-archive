---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20241118 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO Hub: bil, nonumpa, mrorz
- 線上出席：Alex, 品君, EJ
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API

- [Top-level await bug](https://github.com/cofacts/rumors-api/releases/tag/release%2F20241112)

### :rocket: Staging

Admin API
- https://github.com/cofacts/rumors-api/pull/337
- https://github.com/cofacts/rumors-api/pull/352

#### :electric_plug: API

https://dev-admin-api.cofacts.tw/docs
- Cloudflare setup
- API implementation for "greetings" endpoint
- API audit logs


### :eye: Under review

## Badge system design review

> EJ (https://g0v.hackmd.io/zx_Au6iiRN601tnMK7gx3A?both)


## CCPRIP

### [Op] Automated spam removal

> Design doc: https://g0v.hackmd.io/@cofacts/rd/%2Fum7DyY_ESbu2LL78kLw3pg


#### Phase 1: Script execution automation
> MrOrz

Design doc updated as [last week's proposal](https://g0v.hackmd.io/_e0nyj04SoCzxdM38CzuYQ#Op-%E5%A4%96%E9%83%A8%E6%95%B4%E5%90%88%EF%BC%9AAdmin-API).

- [API part](https://g0v.hackmd.io/um7DyY_ESbu2LL78kLw3pg?view#API): documented as last week
- [Cloudflare part](https://g0v.hackmd.io/um7DyY_ESbu2LL78kLw3pg?view#API): new. Documented the configuration on Cloudflare.


#### Phase 3: Automated detection
> nonumpa
> 

根據不重複發 pr、closed pr 之後不要再被偵測等需求，目前程式邏輯為：
1. 每次撈 25 筆最新 replies，過濾掉已知使用者後再丟 Gemini
2. pr 內會顯示最近十筆該使用者的 replies 做為要不要下架的更多參考依據

討論：
1. takedown 指令更新？knownuser 要存在哪裡？mongodb?
2. GitHub app owner transfer
    - 已 grant GH org admin [name=mrorz]
    - NodeJS 呼叫 GH app 對 repo 做操作
    - NodeJS script 本身要跑在 GH action 還是其他地方（cloud function / cloudrun）都可以
4. prompt 公開與否？
5. 先 schedule 在 github action 上跑看看 

- takedown bot
https://github.com/apps/takedown-bot
- https://github.com/octokit/auth-app.js/


### [Infra] DDoS 帳單攻擊預防

[鬼故事 by ihower](https://www.facebook.com/share/p/18HpYzXc1Q/)：

> 大約半年前，我客戶網站上的一張放在 Google Cloud Storage (台灣 asia-east1 區) 的圖片，被 DDoS 攻擊，持續下載同一張圖片(500MiB/s，每秒 8k requests 來自歐美的七個 IP 位址) 持續了兩天。雖然發現後立即加上 Cloudflare 防火牆 (還是免費版即可，早知道就..... 哎) 就擋住了，但仍造成了約 USD 11,000 的鉅額 GCP 帳單，而這平常一個月的流量只需要 USD 15 元。
>
> 後續透過代理商 i 社多次和 GCP 爭取退款或流量費減免，在經歷長達半年的焦慮等待，包括無數次的客服聯繫、反覆確認攻擊細節、通知X部門審查、確認我身份、申請至Y部門、再等待Z部門確認、被拒絕後重送工單 N 次(感謝代理商持續跟進)。最終 Google Cloud Billing Support 的回覆仍是申請失敗，僅爭取到 Google 業務給予的 USD 2000 補助 credits。

Lessons learned by iHower: https://www.facebook.com/ihower/posts/pfbid02NSGjkquioV7TEq5GpTCRnK9uT38NDTqEgzT31x2w8hmTgF5GLZFKWXy3zPzT66sBl

- ✅ 設定帳單提醒
- [在 GCS bucket 前擋 Cloudflare](https://stackoverflow.com/a/35895422/1582110)：好像要[設定 load balancer](https://cloud.google.com/load-balancing/docs/https) 或把[整個 bucket 改名字](https://cloud.google.com/storage/docs/hosting-static-website-http)才能綁網域
    - 直接把 GCS 的網址對外，即使是 signed URL 也是可能被攻擊 


## Langfuse

LLM Observability
> https://g0v.hackmd.io/_e0nyj04SoCzxdM38CzuYQ#Langfuse

- https://langfuse.cofacts.tw
- 架在 Staging，透過 cloudflare tunnel 導向到該網域
- 目前只有 cofacts.tw email 可以註冊
- 接到 CloudSQL ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e13e0011c17bc5ce4b140c1c205bbded.png)


Project 規劃：每個 repository 放一個 project
- 主因：一個 repo 裡起一個 langfuse instance、都送到同一個 Langfuse Project 比較好維護

- rumors-api 會放：
    - AI reply
    - AI transcript （與未來的 LLM transcript）

- rumors-line-bot 會放：
    - 1 on 1 對話（不是 LLM，但可以利用 Langfuse 來 visualize chat session 以及處理時間）

花費：每天 0.3USD；月花 USD $9
（跟 MongoDB 差不多）

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1c2dbe55d303f5e2ec574f13cab5e4fe.png)

之後有其他 relational DB 需求，可以放在同一個 instance

## 小聚籌備

大松可能會在 2 月（本週末確定）
那小聚可以辦在 1 月

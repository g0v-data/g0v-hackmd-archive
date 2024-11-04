---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20241104 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- npo hub: bil, nonumpa, mrorz
- 線上出席：T, Conrad
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API

- https://github.com/cofacts/rumors-db/pull/70
- https://github.com/cofacts/rumors-db/pull/71
- https://github.com/cofacts/rumors-db/pull/72
- https://github.com/cofacts/rumors-api/pull/342 

Reindxing executed: https://github.com/cofacts/rumors-api/pull/342#issuecomment-2452310190

### :rocket: Staging

https://github.com/cofacts/rumors-api/pull/338/files
- 主要在轉 Typescript
- 有把部分 mutation 轉 typescript，`CreateOrUpdateArticleReplyFeedback`
 改得比較多一點

#### :globe_with_meridians: Site
##### Testing checklist
http://dev.cofacts.tw/

登入自有帳號後檢測：
- [x] Replies search page
  - [x] can upvote / downvote replies

##### ⛔️ Release Blockers

##### 未竟項目

## CCPRIP

### [Infra] 虛擬主機打統編
> https://g0v.hackmd.io/@cofacts/rd/https%3A%2F%2Fg0v.hackmd.io%2FBRsJOevWSbyUMBSZEVVWrA
機器：
- Production: Linode 16GB plan - 6vCPU, 96USD/mo
- Staging: Vultr 4GB plan - 20USD/mo
    - 同一個 billing account 下還有我個人的專案 2.5USD/mo
    - Vultr 東京的速度好像很不錯，但 Linode 代理[測起來是 Linode 比較快](https://yangsheep.art/website-diary/5457/)
- Google Cloud 已有代理商

計畫：
- Vultr 聽說[可以開發票](https://www.facebook.com/a.tech.guy/posts/vultr-%E4%B8%83%E6%9C%88%E4%B8%80%E8%99%9F%E4%B8%BB%E6%A9%9F%E8%B2%BB%E9%96%8B%E5%A7%8B%E5%8A%A0%E6%94%B6-5-%E7%87%9F%E6%A5%AD%E7%A8%85%E5%A6%82%E5%9C%96%E6%89%80%E8%AA%AA%E4%B8%8D%E9%81%8E%E7%99%BB%E5%85%A5%E5%BE%8C%E5%8F%B0%E4%B9%9F%E6%B2%92%E6%9C%89%E7%9C%8B%E5%88%B0%E5%8F%AF%E4%BB%A5%E5%A1%AB%E5%AF%AB-vat-id-%E7%B5%B1%E7%B7%A8%E7%9A%84%E5%9C%B0%E6%96%B9%E9%96%8B%E4%BA%86%E4%B8%80%E5%80%8B-ticket-%E5%95%8F%E9%80%99%E5%A1%8A%E5%8B%A2%E5%BF%85%E4%B9%8B%E5%BE%8C%E9%82%84%E8%A6%81%E5%95%8F%E4%B8%80%E4%B8%8B%E6%9C%83/2017561981647571/)
    - 但好像跟 Google 一樣，開的是[美金](https://vrabe.tw/blog/vultr-started-issuing-uniform-invoices/)？
    - 想要[填統編](https://www.ptt.cc/bbs/Web_Design/M.1683539619.A.444.html) 試試看
- 如果 Vultr 可以打能報帳的統編：
    - Staging 換到 Cofacts 專用帳號下
    - Production 可能也換成 deploy 到 Vultr
- 如果 Vultr 不能打統編
    - Staging 不動
    - Production 找代理（Ronny 推薦零壹科技）開發票
- 如果要搬家，搬到台灣 GCP 好像更好?
    - 放台灣會變快
    - SSH 的部分可以用 Google 的權限 (?)
    - 但海纜斷掉可能還是不能用，因為 [Google Cloud IP 連線時會走美國](https://stackoverflow.com/questions/41988170/why-do-google-cloud-platform-static-ip-addresses-list-mountain-view-ca-in-rever?answertab=votes#tab-top) [name=nonumpa]
    - [Machine resource types](https://cloud.google.com/compute/docs/machine-resource), [Region availability](https://cloud.google.com/compute/docs/regions-zones#available)
    - [E2: 4vCPU, 16GB ram, 1-year committed use discount](https://cloud.google.com/products/calculator?hl=en&dl=CjhDaVEzTW1RMk16RmxNUzFoWldJMkxUUXhNakF0WW1ZMU1DMWpPRGhoTldKalpEZ3hNVGtRQVE9PRAIGiQzOTA0OEYxQi01OTUzLTRBREYtQkYwNy03ODBBN0UwQjU3MUQ): 75.70USD/mo 
    - [N2D: 4vCPU, 16GB ram, 1-year commutted use discount](https://cloud.google.com/products/calculator?hl=en&dl=CjhDaVJqTlRKaU9HRm1OUzA1TnpjMUxUUTJOalF0WVRabU5DMHlNREl5TXpZNE5tUTNZbUVRQVE9PRAIGiQzOTA0OEYxQi01OTUzLTRBREYtQkYwNy03ODBBN0UwQjU3MUQ): 92USD / mo
    - [C3D: 4vCPU, 16GB ram, 1-year commutted use discount](https://cloud.google.com/products/calculator?hl=en&dl=CjhDaVE1TW1ZM01qUmlNeTB6WVRWbExUUTBNR1V0T0dNeE5TMDNaVGN5WVRZMFpHSTBOV1lRQVE9PRAIGiQzOTA0OEYxQi01OTUzLTRBREYtQkYwNy03ODBBN0UwQjU3MUQ): 97.63USD/mo
- CCPRIP Infra 機器 migration 流程可能就能簡化，不用所有東西都上比較貴的 cloud run [name=mrorz]
  - Cloud Run 會省錢是在開開關關，但 production service 會一直保持開啟

:::success
先 Staging Vultr --> [E2 Medium](https://cloud.google.com/products/calculator?hl=en&dl=CjhDaVJqT1RjMFltVmxZeTA1WkRoaUxUUmhNVFF0WWpWbU1pMWhaVE0yWTJWak5tWTVaaklRQVE9PRAIGiQzOTA0OEYxQi01OTUzLTRBREYtQkYwNy03ODBBN0UwQjU3MUQ) 看狀況，測試重點：
- 跑不跑得起來
- SSH 管理
  - 可能每個人都有資料夾 [name=nonumpa]
    - 可能就讓每個人都能 su 成 docker
- Maybe try [Container-optimized OS](https://cloud.google.com/container-optimized-os/docs/concepts/features-and-benefits)?
  - 指令會不太一樣
:::

### [Op] spam removal automation


> Design doc:  https://g0v.hackmd.io/@cofacts/rd/%2Fum7DyY_ESbu2LL78kLw3pg


### Phase 1 Command via Pub/Sub
> @mrorz

- https://github.com/cofacts/rumors-api/pull/337
- https://github.com/cofacts/rumors-api/blob/master/ecosystem.config.js 裡的 [commandListener](https://github.com/cofacts/rumors-api/pull/337/files) 會去 subscribe admin 指令的 topic
- 用 terraform 設定 google pubsub topic + schema https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/pubsub_topic 
    - schema 可以放在 rumors-db （讓其他地方，如 github script 可以引用）；terraform 因為要讀 schema 所以也放 rumors-db
    - bq 也可以從自己寫的 script [轉成 terraform](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/bigquery_table.html)
    - Alternative: 原案 - schema 放 rumors-api，設定 pubsub 的指令寫在 README 就好
      - 優點：簡單做
      - 缺點：PubSub 的 type 被鎖在 rumors-api 裡，很難在其他地方（如 publish event 的 script）裡使用
- schema definition
  - 用 avro 寫
  - [codegen 轉 typescript](https://github.com/ovotech/castle/tree/main/packages/avro-ts#readme) 然後 commit 進 repo
  - 可以在 CI 呼叫 codegen 確保 type 有更新（若沒更新就 fail CI）

:::success
- Event schema 放 rumors-db
- Terraform 先不要，跟 BQ 一樣寫在 rumors-db 的 README 就好
:::

### Phase 3 Automatic spam detection
> @nonumpa

- 目前用 Gemini [structured-output](https://ai.google.dev/gemini-api/docs/structured-output?lang=node) 拿到程式可以使用的結果，之後要寫自動發 PR
    - bot 產生 pr like: https://github.com/cofacts/rumors-db/pull/42 [name=nonumpa]
    - 可以用 `secrets.GITHUB_TOKEN` 用 Github Action 的身份在 github 上做事，一樣有 bot label
      - 需要[用 `permissions`](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/controlling-permissions-for-github_token) 設定 GITHUB_TOKEN 能做到什麼事 [name=mrorz]


## Badge 功能

- 要不要把「TFC 幫使用者上 badge」從 API + token 也改成用 PubSub + script？ [name=mrorz]
    - badge 相關指令可以有「建立新 badge」與「把人加上 badge」
    - badge 相關指令可以是獨立於 admin command 的新 topic
    - 針對 TFC 的 service account 設定 [topic-level](https://cloud.google.com/pubsub/docs/access-control) 的 Pub/Sub Publisher 權限
    - script 裡檢查「把人加上 badge」的 service account 是否有權限增添此 badge

:::success
和 EJ 聊聊這條路
:::

## Langfuse

> [name=mrorz]

- 預計直接在 answerfamily 上修改 docker-compose
- 參考 https://github.com/langfuse/langfuse/blob/main/docker-compose.yml
    - 官方說這樣做[不是 production ready](https://langfuse.com/docs/deployment/local) 但我們其他服務也一直都這樣做 XD
    - 可能 pg data 的部分 mount 到 disk 而非 docker volume

:::success
Blocked by staging migrating to GCE
:::

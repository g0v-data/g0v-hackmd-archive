---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20241104 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
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
- [ ] Replies search page
  - [ ] can upvote / downvote replies

##### ⛔️ Release Blockers

##### 未竟項目

## CCPRIP

### [Infra] 虛擬主機打統編

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
    - [Instance types](https://cloud.google.com/compute/docs/general-purpose-machines)
    - [E2: 4vCPU, 16GB ram, 1-year committed use discount](https://cloud.google.com/products/calculator?hl=en&dl=CjhDaVEzTW1RMk16RmxNUzFoWldJMkxUUXhNakF0WW1ZMU1DMWpPRGhoTldKalpEZ3hNVGtRQVE9PRAIGiQzOTA0OEYxQi01OTUzLTRBREYtQkYwNy03ODBBN0UwQjU3MUQ): 75.70USD/mo 
    - [C2D: 4vCPU, 16GB ram, 1-year commutted use discount](https://cloud.google.com/products/calculator?hl=en&dl=CjhDaVE1TW1ZM01qUmlNeTB6WVRWbExUUTBNR1V0T0dNeE5TMDNaVGN5WVRZMFpHSTBOV1lRQVE9PRAIGiQzOTA0OEYxQi01OTUzLTRBREYtQkYwNy03ODBBN0UwQjU3MUQ): 97.63USD/mo


### [Op] spam removal automation


> Design doc:  https://g0v.hackmd.io/@cofacts/rd/%2Fum7DyY_ESbu2LL78kLw3pg


### Phase 1 Command via Pub/Sub
> @mrorz

- https://github.com/cofacts/rumors-api/pull/337
- https://github.com/cofacts/rumors-api/blob/master/ecosystem.config.js 裡的 [commandListener](https://github.com/cofacts/rumors-api/pull/337/files) 會去 subscribe admin 指令的 topic
- 用 terraform 設定 google pubsub topic + schema https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/pubsub_topic 
    - schema 可以放在 rumors-db；terraform 因為要讀 schema 所以也放 rumors-db
        - 用 avro 寫 + [codegen 轉 typescript](https://github.com/ovotech/castle/tree/main/packages/avro-ts#readme)
    - bq 也可以從自己寫的 script [轉成 terraform](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/bigquery_table.html)
- schema

### Phase 3 Automatic
> @nonumpa


## Badge 功能

- 要不要把「TFC 幫使用者上 badge」從 API + token 也改成用 PubSub + script？ [name=mrorz]
    - badge 相關指令可以有「建立新 badge」與「把人加上 badge」
    - badge 相關指令可以是獨立於 admin command 的新 topic
    - 針對 TFC 的 service account 設定 [topic-level](https://cloud.google.com/pubsub/docs/access-control) 的 Pub/Sub Publisher 權限
    - script 裡檢查「把人加上 badge」的 service account 是否有權限增添此 badge

## Langfuse

> [name=mrorz]

- 預計直接在 answerfamily 上修改 docker-compose
- 參考 https://github.com/langfuse/langfuse/blob/main/docker-compose.yml
    - 官方說這樣做[不是 production ready](https://langfuse.com/docs/deployment/local) 但我們其他服務也一直都這樣做 XD
    - 可能 pg data 的部分 mount 到 disk 而非 docker volume


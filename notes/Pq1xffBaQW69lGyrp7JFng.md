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
## [Op] spam removal automation


> Design doc:  https://g0v.hackmd.io/@cofacts/rd/%2Fum7DyY_ESbu2LL78kLw3pg


### Phase 1
> @mrorz
> 

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



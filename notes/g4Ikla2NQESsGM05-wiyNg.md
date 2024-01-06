---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20231101 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz, nonumpa, cai, T
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
- https://github.com/cofacts/rumors-api/releases/tag/release%2F20231027
    - remove apparent hallucination
    - Fix nullable

#### :globe_with_meridians: Site
https://github.com/cofacts/rumors-site/releases/tag/release%2F20231026
- Fix crowdsource transcript line breaks


## CCPRIP
> https://g0v.hackmd.io/@mrorz/ccprip

### [Infra] Log cost saving
> 8/23 https://g0v.hackmd.io/Fmkhf62_SKGIlwwwLrRnAw#Infra-Log-cost-saving Estimate: 「好像不用錢」
> 9/21: changed https://g0v.hackmd.io/ulv1SGtBRWmhxnE9Lpv9TQ#Infra-Log-cost-saving

10 月帳單：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3d5f7f3b162099c3e3e9f6502c5add52.png)

- Pricing: https://cloud.google.com/logging?hl=en#section-7
- 超過 50GB 免費額度 17GB * 0.5 USD -> 8.5USD

### [Infra] Migrate to Cloud Run: cost analysis
目前：
- production en, ja site
- staging en, ja, zh site
- production en, ja line-bot
- staging zh line-bot

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4a5bc7c57636c3a172dfe3c8dd445f09.png)

#### Breakdown
Almost all are rumors-site
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_50b8b58191e02d276385f9f9cbc80163.png)

TODO:
Add labels to differentiate cloudrun in cost reports https://cloud.google.com/resource-manager/docs/labels-overview

- `component`: `line-bot`, `site`, `api`
- `environment`: `prod`, `staging`
- `locale`: `tw`, `en`, `ja`

### [Comm] Transcript

#### Crowd-sourced
> [name=nonumpa]
> 

[Run Elasticsearch 6 on an Apple Silicon Mac](https://stackoverflow.com/questions/68877644/how-to-run-elasticsearch-6-on-an-apple-silicon-mac)

先用別人build的image代替
`docker run -d -p "62223:9200" --name "rumors-test-db" docker.elastic.co/elasticsearch/elasticsearch-oss:6.3.2`
⬇️
`docker run -d -p "62223:9200" --name "rumors-test-db" webhippie/elasticsearch:6.4`

monorepo + jest module reference 要再研究一下

#### Transcript Migration
- 7238 video transcribed

#### VAD to reduce hallucination
- Migration 時用的是 faster-whisper，內建 Silenro VAD，沒有實作 [dedup](https://github.com/cofacts/rumors-api/pull/323)
- 還是會有不少 hallucination
    - 可能 VAD 覺得有聲音，沒濾掉，但 whisper 還是會幻
    - 應該

## Hypercert 回溯公眾投資

要統計哪些使用者？

:::success
- 取消 11 月的發放，12/15 一次發放 9~12 月的貢獻
- 請參與者開錢包
:::

## 小聚籌備

LINE VOOM 發文(文案見上週)
推播？

> Cofacts 真的假的 第一次前往新營！！
> 感謝這份難得的緣分，好喜歡一層層樓梯間曬書店的雅緻與對議題的重視。
> 免費的志工培訓就在 2023年11月18日 14:00-17:00 曬書店，期待各位的參與，讓我們一起透過鍵盤與查找資料，用民眾草根的力量對抗假資訊的威脅。記得帶電腦唷！
> 730台南市新營區中山路93-2號（請上樓）

:::success
本週五推播 + LINE VOOM
台南、嘉義、雲林
:::

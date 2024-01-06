---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20230921 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
- https://github.com/cofacts/rumors-db/releases/tag/release%2F20230913
- https://github.com/cofacts/rumors-api/releases/tag/release%2F20230913
#### :globe_with_meridians: Site
- https://github.com/cofacts/collab-server/releases/tag/release%2F20230913
- https://github.com/cofacts/rumors-site/releases/tag/release%2F20230913


##  CCPRIP

### [Infra] Log cost saving
API switched to Google cloud log on 2023/9/16 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1d25c378f879229bacd2bfe6c108b9b8.png)

AWS cost estimates
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_288a284940e3a63ae29e482bcf68bf8b.png)
- June: USD 60 in cloud watch ([previous assessment](https://g0v.hackmd.io/@cofacts/meetings/%2F5Pn97RTPTpmsrW4opnSKNA))
    - 6/7 make log compact
- 8/17 log cost saving deployed https://g0v.hackmd.io/Fmkhf62_SKGIlwwwLrRnAw#Infra-Log-cost-saving
- 9/16 switch to GCP

#### Google cloud log
- 同一個 project 的 log 通通都放在同一個 bucket, 可 filter by instance ID
- 30-day retention
- May connect to BigQuery (but not yet activated) for free (?)

#### Follow-up
- Move chatbot log?
    - will be moved when we migrate line bot to cloudrun

### [Infra] Migrate to Cloudrun

> https://g0v.hackmd.io/BRsJOevWSbyUMBSZEVVWrA#Phase-1-rumors-site-amp-rumors-line-bot-%E4%B8%8A-Google-cloud-run
> 

#### Original

(Web Request) --> Cloudflare --> Linode nginx --> Linode site

Linode nginx handles:
- map to correct site
- adding link headers ([alternative](https://developers.google.com/search/docs/specialty/international/localized-versions?hl=zh-tw) tags, block robots to staging site)
- redirect `/hack`, `/analytics`
- cofacts.g0v.tw --301--> cofacts.tw
- cofacts.g0v.tw SSL

#### Now

(Web Request) --> Cloudflare --> Cloud run (with [domain mapping](https://cloud.google.com/run/docs/mapping-custom-domains))

Now on Cloud Run:
- Staging sites
- Production EN & JA sites
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dfe5a72c693f9b0fd2b5278250f3c276.png)
- Connect zh.cofacts.tw to cloudflare; cofacts.tw still on Linode
- All domains must turn on "Full SSL" on Cloudflare
    - because cloud run must be accesed with HTTPS; it will redirect HTTP requests
    - Under "flexible SSL", Cloudflare will always use HTTP to connect to upstream, causing infinite redirects
    - Added "Cloud run HTTPS" as Cloudflare configuration rules

Nginx settings migrated to Cloudflare:
- adding link headers ([alternative](https://developers.google.com/search/docs/specialty/international/localized-versions?hl=zh-tw) tags, block robots to staging site)
- redirect `/hack`, `/analytics`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9bc1f69172e40f58d6fd6f6d6c79a8bd.png)

#### Observing

- CPU & RAM utilization
  ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e956f5e83f44b3d972f86a59f98a33dd.png) ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a0e058bc8bed688018bf8c7d60f3b743.png)
- Instance count
- Cost ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_57ef87ddaf5c5315b6aea6957bc249bf.png)

#### TODO
- Github action image build --> deploy to corresponding cloud run
- Maybe use a dedicated service account for Github action deploys? ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_625877e01b5bc24c9fa6b37c3a81c0a6.png)
- Move cofacts.tw to Cloud Run?
    - Have 30min ~ 60min downtime when setting Cloud Run domain mapping https://stackoverflow.com/a/60063505
    - Observe billing on en & ja sites first


### [Comm] Transcript

> https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ
> [name=nonumpa]

#### AI: API 寫入 ydoc
> Design doc https://g0v.hackmd.io/wkx286lmTDaFUpgRhnUawQ#CreateMediaArticle
> Related discussion on 2023/8/2: https://g0v.hackmd.io/0tPABSZ6SRKswBYqAc1vZw#API
> [name=mrorz] 

繼續完成 https://github.com/cofacts/rumors-api/compare/master...write-ai-transcript

#### Auth
> [name=mrorz]

No progress yet

## 小聚檢討

> 小松果 https://g0v.hackmd.io/lXd4Ypg_S12HLxs5z9wAkQ

- 出席人數：11 / 報名：23 (出席率 50%)
- 場地很好
    - 好民場地不是最便宜的 [name=cai]
    - 苗栗～彰化、南投都算近 [name=cai]
    - 南園酒家再高價一點，二樓獨立樓梯上去，比較高價 [name=cai]
    - 可以看好民臉書他們辦在南園酒家的活動照片
    - 對台北跟高雄來說超便宜，又在 1F、有交通 [name=bil]
    - 缺點是比較窄 [name=bil]
- 前一週宣傳非常好，11 月比照辦理 [name=mrorz]
- 減少「可以怎麼做」的 instruction、改成「希望如何」[name=bil]
    - 我會介紹「可以」然後再建議 [name=mrorz]

## 新營小聚
- 11/18, bil 不在, rosalind
- 開 32 人 (場地 capacity)
- 先改完海報過去給他們貼兩個月 [name=bil]
- 前一週 LINE 宣傳：嘉義、台南

## 檢舉處理

### NX 多重帳號案
https://cofacts.tw/reply/Is-kVYoBrkRFoI6rzOOr

- 處理投票時，應該一並考慮 category vote

### Ace chan
https://cofacts.github.io/community-builder/#/editorworks?showAll=1&day=365&userId=K_RHp4oBAjOeMOklr6MS

- 可以只讓登入的使用者看嗎 [name=bil]
    - 現在還沒有這個機制，除非刪掉他 [name=mrorz]
    - 那不要處理好了
- 未來可以討論要不要折疊負評的回應 [name=mrorz]

### 楊不梅
- https://cofacts.tw/user/%E6%A5%8A%E4%B8%8D%E6%82%94
- https://cofacts.github.io/community-builder/#/editorworks?showAll=1&day=365&userId=js8xZYoBrkRFoI6rjelx
- 回得不好，但好像也沒有太違反使用者條款 [name=mrorz]
- 社群討論 [name=bil]

:::success
Johnson 社群討論
:::

## Rollbar over limit

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_302294981fe1d042444976fa047352a8.png)

- 應該是因為我們把 `otherFields` 拿掉了? https://github.com/cofacts/rumors-line-bot/pull/361/files [name=mrorz]
    - First peak 9/2 --> due to [Release](https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20230902) ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c6dbe250ababac3242a84640718ac735.png)
- 有一個月的時間修 XD ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5d2e578f8ce74f08ec5703793beca0b3.png)

:::success
nonumpa++
:::

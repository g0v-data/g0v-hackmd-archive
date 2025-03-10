---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250310 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API

- LLM transtript: https://github.com/cofacts/rumors-api/releases/tag/release%2F20250303

## LLM transcript follow-up

> 昨晚我們將之前開發的 LLM-based 逐字稿推到 production 囉。看起來滿好的，不過有些例外
> https://cofacts.tw/article/oOgGX5UBYrjt7MSMJFkX 完全無人聲也沒字幕，會變成一般的 video summarization。
> 如果同一則影片會有非常相近的描述，那代表同一則影片可以被歸類在一起，這樣倒還算不錯？
> https://cofacts.tw/article/7ui3XpUBYrjt7MSM3Vhq 沒有逐字稿
> 但至少不再有啥「在網際網路上傳播的影片的逐字稿」、「字幕由 Amara.org 社群提供」了
> [name=mrorz]

![](https://g0v.hackmd.io/_uploads/By1Y_r2syx.png)

- 88% Video
- 8% Audio
- Others text output + input
- $3 per day; approx. 100USD per month

## Langfuse follow-up

Langfuse v3 clickhouse is taking up space:
```
(2025/3/8 ~4PM)
VOLUME NAME                                                        LINKS               SIZE
answerfamily-deploy_langfuse_clickhouse_data                       1                   11.72GB
answerfamily-deploy_langfuse_clickhouse_logs                       1                   1.881GB
```

```
(2025/3/10 ~7PM)
VOLUME NAME                                                        LINKS               SIZE
answerfamily-deploy_langfuse_clickhouse_data                       1                   14.14GB
answerfamily-deploy_langfuse_clickhouse_logs                       1                   1.71GB
```

--> ~1GB per day......

Clickhouse logs to stderr when disk is full, which is captured by cloud logging:
![](https://g0v.hackmd.io/_uploads/rkO9Y42jkx.png)
![](https://g0v.hackmd.io/_uploads/BkuXcE2ikg.png)

- 3/7 Disk full
- 3/8 Cleanup disk with docker system prune (10GB)

Even after disk space is freed up, Clickhouse in docker would continue sending log to stderr until it is restarted

Logs in volume:
![](https://g0v.hackmd.io/_uploads/BJtgvbnj1x.png)
- It is emitting log into logfile every second
- Everyday is about the same

:::spoiler Log content
clickhouse-server.err.log repeatedly complain about memory every second:
![](https://g0v.hackmd.io/_uploads/r1EA7I3ikl.png)

clickhouse-server.log 被 error log 洗版
:::


Mitigation

- Disk size issue
    - `docker system prune` --> Frees 10+ GBs
    - Use [GCS](https://langfuse.com/self-hosting/infrastructure/clickhouse#blob-storage-as-disk) to store Clickhouse data
    - Optimize storage usage https://github.com/orgs/langfuse/discussions/5687#discussioncomment-12323498
- Logging issue
    - Don't send stderr to cloud logging for Clickhouse
    - Investigate Clickhouse log

## SITCON 學生計算機年會擺攤檢討

擺攤 for 年輕學生
- 有大地遊戲：先加 Cofacts 好友才給蓋章（指向小戊傳單的 QR code）
  ![](https://g0v.hackmd.io/_uploads/SyZIeI2sJx.png)
    - 小戊漫畫傳單非常有用
- 摺頁傳單還是滿重要，應該加印
    - 被問到準確性問題，可以指著說明「會問有用程度」
    - 豆腐版印成 A3 字還是太小，站著的會眾看不清楚桌上的豆腐版傳單
    - 摺頁傳單上也有巨大 QR code，比小戊的大
- 影響力傳單沒啥吸引力
- 因為放大視野 & Oslo freedom forum 背板都有提 Cofacts 有用 AI，不少人來問用在哪裡
    - AI 回應傳單忘記帶，應該會很有用
    - 提到查核協作者培訓的機會不多
- 看情況推新北志工
    - 「如果你有缺志工時數⋯⋯」

## 大松
- [ ] 台南好想



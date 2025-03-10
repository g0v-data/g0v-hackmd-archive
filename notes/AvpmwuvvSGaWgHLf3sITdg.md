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

Even after disk space is freed up, Clickhouse in docker would continue sending log to stderr until it is restarted

Logs in volume:
![](https://g0v.hackmd.io/_uploads/BJtgvbnj1x.png)
- It is emitting log into logfile every second
- Everyday is about the same

Mitigation
- `docker system prune` --> Frees 10+ GBs
- Don't send stderr to cloud logging for Clickhouse
- Investigate Clickhouse log


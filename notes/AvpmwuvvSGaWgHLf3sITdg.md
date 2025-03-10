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
VOLUME NAME                                                        LINKS               SIZE
answerfamily-deploy_langfuse_clickhouse_data                       1                   11.72GB
answerfamily-deploy_langfuse_clickhouse_logs                       1                   1.881GB
```

Clickhouse logs to stderr when disk is full, which is captured by cloud logging:



Logs in volume:
![](https://g0v.hackmd.io/_uploads/BJtgvbnj1x.png)
- It is emitting log into logfile every second
- Everyday is about the same

Mitigation
- `docker system prune` --> Frees 10+ GBs
- Don't send stderr to cloud logging for Clickhouse
- Investigate Clickhouse log


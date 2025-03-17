---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250317 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

### :rocket: Staging

#### :electric_plug: API

- Admin API GET `/openapi.json` bug https://github.com/cofacts/rumors-api/pull/364
- Extract video transcript logic to experiments https://github.com/cofacts/rumors-api/pull/363
    - Previously discussed in https://g0v.hackmd.io/@cofacts/meetings/%2F3WGAMK9hRQ2pPQE-0x_vOQ#LLM-based-AI-transcript

#### :robot_face: rumors-line-bot

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [ ] 應可送出「全新影片訊息」
    - [ ] 同意送出訊息後就會送出訊息，並得到正常逐字稿

##### ⛔️ Release Blockers
##### 未竟項目

### :eye: Under review

- Extract video transcript logic to experiments https://github.com/cofacts/rumors-api/pull/363

## CCPRIP

### [Op] Automatic takedown

> Design doc: https://g0v.hackmd.io/@cofacts/rd/%2Fum7DyY_ESbu2LL78kLw3pg

https://github.com/cofacts/takedowns/pull/184

- API & Body format
- PR check
- Take action after merge

### [Comm] LLM transcript

Pricing update: Still ~= 100USD per month

![](https://g0v.hackmd.io/_uploads/ry8mjBShkl.png)

Langfuse estimations are somehow larger ![](https://g0v.hackmd.io/_uploads/B1eAoHHn1e.png)

## Langfuse update

- Clickhouse: 把 clickhouse config 拉出來，關閉了一堆 log 也做了很多設定（參考 https://chatgpt.com/share/67d12291-0048-800b-9a9e-b0c7eae6e45c ）
    - Turn off loggers in tables
    - `max_concurrent_queries` to 4
    - Lower `background_pool_size` and related pools
    - Lower `mark_cache_size` to 128M
    - `max_server_memory_usage_to_ram_ratio` to 0.5 (4GB * 0.5 = 2GB)
- 在本機用 docker-compose `mem_limit: 2000m` 限制 clickhouse RAM --> 沒事
- 在 staging 啟動 Clickhouse 就會噴 error 
    > <Error> MergeTreeBackgroundExecutor: Exception while executing background task {...}: Code: 241. DB::Exception: (total) memory limit exceeded: would use 2.64 GiB (attempt to allocate chunk of 4361808 bytes), current RSS 1.48 GiB, maximum: 2.64 GiB. (MEMORY_LIMIT_EXCEEDED), Stack trace (when copying this message, always include the lines below):
- 把 elasticsearch 先停掉、清掉 system tables 後重啟 clickhouse
    - 沒有一直噴 error
    - 好像好了
    
## Link to MyGoPen


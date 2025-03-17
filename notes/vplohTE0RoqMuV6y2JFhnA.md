---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250317 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, nonumpa, mrorz, T
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

### :rocket: Staging

#### :electric_plug: API

- Admin API GET `/openapi.json` bug https://github.com/cofacts/rumors-api/pull/364
- Extract video transcript logic to experiments https://github.com/cofacts/rumors-api/pull/363
    - Previously discussed in https://g0v.hackmd.io/@cofacts/meetings/%2F3WGAMK9hRQ2pPQE-0x_vOQ#LLM-based-AI-transcript

#### :robot_face: rumors-line-bot

- https://github.com/cofacts/rumors-line-bot/pull/404

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 應可送出「全新影片訊息」
    - [x] 同意送出訊息後就會送出訊息，並得到正常逐字稿

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
    - 空的 clickhouse 其實是可以運作在 2GB ram 的機器上
- 在 staging 啟動 Clickhouse 就會噴 error 
    > <Error> MergeTreeBackgroundExecutor: Exception while executing background task {...}: Code: 241. DB::Exception: (total) memory limit exceeded: would use 2.64 GiB (attempt to allocate chunk of 4361808 bytes), current RSS 1.48 GiB, maximum: 2.64 GiB. (MEMORY_LIMIT_EXCEEDED), Stack trace (when copying this message, always include the lines below):
- 把 elasticsearch 先停掉、清掉 system tables 後重啟 clickhouse
    - 沒有一直噴 error
    - 好像好了
    
## Link to MyGoPen

> 有user傳cofacts問事，cofacts AI問是否分享案例，user把含個資的圖片傳給cofacts，結果cofacts AI就直接把案例含個資給PO出來了，user急的想刪但cofacts界面沒有刪除選項，user說cofacts回應他如需客服可以找MYGOPEN真人，所以user跑來找我們，底下是含個資的cofacts連結：
[https://cofacts.tw/article/Nuh7dZUBYrjt7MSMGoHF](https://cofacts.tw/article/Nuh7dZUBYrjt7MSMGoHF)
> 1. 這user分享到cofacts後，要如何刪除或編輯？
> 2. user反應cofacts AI界面問是否分享案例，user當時單純想分享請cofacts幫忙查，但並沒有想要PO上網路，這部份cofacts是否可考慮在AI界面上說清楚"分享案例"的實際作為就是cofacts送上網，避免user將敏感資訊送上cofacts網路然後又沒有地方可以刪除或編輯
> 3. MYGOPEN是cofacts客服？
>
> [name=robin]

> 去年的討論 XD https://g0v.hackmd.io/@cofacts/meetings/%2FUaO0a5gETTeRTP8sH7NGlg#%E9%80%81%E5%87%BA%E8%A8%8A%E6%81%AF-wording 關於 2 的部分，後來我們改了送出訊息的流程，現在非常明確就是公開在網站上，也確定公開的意願
> 關於 1： 刪除與編輯這兩者，根據上面的會議紀錄，是不希望做的 怕大家問完就刪除或編輯掉，不符合公共效益。
> 原來去年有討論到說，可以在 MyGoPen 旁邊新增聯絡 Cofacts，這部分後來沒做
> 關於 3，目前我們在使用者自行打字輸入時，會回說可以去 MyGoPen 問。
> [name=mrorz]

> 認真回應第三點，文句應該沒有任何地方表示「mygopen是cofacts 客服」，因為並不是，mygopen bot 是一個獨立的產品。這是基於試圖猜測使用者可能是希望有真人回應的情況下導流到mygopen帳號，另一個期待是讓mygopen增加好友數。如果這件事情會造成mygopen困擾，隨時都可以移除這個功能，請告訴我們。
> [name=bil]

> 使用者不應該要不認真閱讀文字
> [name=nonumpa]

    
:::info
- 開票設計表單的部分
- 考慮拿掉 MyGoPen 的連結
:::

## 小聚籌備

3/29 大松

4/20 (日) 2pm
- OK: orz, nonumpa, bil
- 辦在青職基地
    
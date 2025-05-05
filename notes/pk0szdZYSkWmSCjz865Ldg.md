---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250505 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO Hub: bil, mrorz, nonumpa
- 線上出席：Tim
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

- https://github.com/cofacts/rumors-site/releases/tag/release/20250429 Badge

#### :robot_face: rumors-line-bot

### :rocket: Staging

- https://github.com/cofacts/takedowns/pull/203

## CCPRIP

### [Op] Automatic takedown

- 調整 CCPRIP 自動下架功能過濾邏輯
- Code review [name=mrorz] (takedowns PR #203) -- Done

## Downtime

- Downtime 是否與 elasticsearch 太舊有關，並檢查 DB log 輸出。
- 處理 2025/4/25 攻擊事件中的台灣 IP：加進黑名單、分析 pattern 看為啥會漏掉
  - cofacts website 效率不高，每次 pageview 會有複數個 API call 導致看起來很多 request [name=mrorz]

## Langfuse Clickhouse follow-up

Upgrade Clickhouse to 25.3 LTS
- 從 25.1 升級到了 25.3
- ttl config `finish_time_us + toRelativeSecondNum(1 * 3600)` 仍會造成此 error
    > Illegal type UInt32 of argument of function toRelativeSecondNum. Should be Date, Date32, DateTime or DateTime64: While processing finish_time_us + toRelativeSecondNum(1 * 3600). (ILLEGAL_TYPE_OF_ARGUMENT)
- ttl 修正為 `finish_date + INTERVAL 1 DAY DELETE` --> 沒問題

clickhouse index 大小穩定
```
    ┌─database─┬─table────────────────────┬─total_size─┐
 1. │ default  │ observations             │ 14.87 MiB  │
 2. │ default  │ traces                   │ 10.58 MiB  │
 3. │ default  │ event_log                │ 6.43 MiB   │
 4. │ default  │ scores                   │ 521.96 KiB │
 5. │ system   │ opentelemetry_span_log   │ 317.54 KiB │
 6. │ system   │ query_metric_log         │ 137.81 KiB │
 7. │ system   │ query_log                │ 52.39 KiB  │
 8. │ system   │ processors_profile_log   │ 29.28 KiB  │
 9. │ system   │ part_log                 │ 17.86 KiB  │
10. │ system   │ trace_log                │ 17.04 KiB  │
11. │ system   │ query_views_log          │ 13.17 KiB  │
12. │ system   │ text_log_0               │ 9.06 KiB   │
13. │ default  │ dataset_runs_CIhUb       │ 5.07 KiB   │
14. │ system   │ asynchronous_metric_log  │ 3.39 KiB   │
15. │ system   │ opentelemetry_span_log_0 │ 1.09 KiB   │
16. │ default  │ project_environments     │ 1.00 KiB   │
17. │ default  │ schema_migrations        │ 641.00 B   │
    └──────────┴──────────────────────────┴────────────┘
```

:::success
處理完畢，結案
:::

## Open165

urlscan.io integration
- urlscan: 德國服務
  - 由美國公司 SecurityTrail 與 RecordedFuture 贊助，後者已被萬事達卡收購
- 提供 [API](https://urlscan.io/docs/api/)
  - submission：把輸入 url 存成新的 scan 結果，回傳 scan id
  - result 與截圖 API: 輸入 scan id 回傳 scan 資料
    - 範例網頁 https://urlscan.io/result/01969aae-df49-7768-b5f4-df2120f1e861/
        - "Similar" 頁面有我們要的東西：DOM 一樣的、IP 一樣的、ASN 一樣的網站 (需登入)
        - 但 similarity search 要 USD$1000/mo ![](https://g0v.hackmd.io/_uploads/r1lMlrzBell.png)
    - 範例 API https://urlscan.io/api/v1/result/01969aae-df49-7768-b5f4-df2120f1e861/
    - 可用欄位：https://urlscan.io/docs/result/
        - `page.ip`
        - `page.title`
        - `page.asn`
        - `task.reportURL`
        - `task.screenshotURL` --> 存到 cloudflare？
        - `task.domURL` --> 可以載下來自己比對
  - 搜尋：輸入 url 與其他東西，回傳搜尋結果
    - [可搜尋欄位](https://urlscan.io/docs/search/) 包含 URL 與 title

### Open165 架構

列表來源：每週 165 公告與 API
- 拆開 title 與 URL 獨立成頁 (name detail 與 url detail)
- 送進 Urlscan

Ad hoc 來源：單一 URL --> 呈現 host detail
Ad hoc 來源：單一名稱（ooo是真的嗎） --> 呈現 name detail


Detail 頁面：
- 165 目前公告結果
- URL scan 結果與送出到 urlscan
- 各種反詐、防治二次詐騙文案

首頁：
最新 name 列表、url 列表、urlscan 結果


## 大松
- 5/25 (日) https://g0v-jothon.kktix.cc/events/g0v-hackath67n
- 09:30(+0800) ~ 21:00(+0800)
  - 要夜場嗎？ [name=bil]
  - 看參與者，都沒有參與者了的話就離開 [name=mrorz]
- 現場：bil, mrorz
  - 吃這島
- bil 需更新投影片：https://docs.google.com/presentation/d/10VRulY_MFMZK4wQNPN6Yjm8N8S9_wi-K1vUwelicwiQ/edit
- 線上：nonumpa

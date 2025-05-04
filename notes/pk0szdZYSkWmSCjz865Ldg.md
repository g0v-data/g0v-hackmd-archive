---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250505 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO Hub:
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

#### :robot_face: rumors-line-bot

### :rocket: Staging

#### :globe_with_meridians: Site

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [ ] Replies list
  - [ ] Nothing breaks

##### ⛔️ Release Blockers

##### 未竟項目

- 行動版 Replies list 頭像右側空間過大 ([issue #603](https://github.com/cofacts/rumors-site/issues/603))

### :eye: Under review

## CCPRIP

### [Op] Automatic takedown

- 調整 CCPRIP 自動下架功能過濾邏輯
- Code review [name=mrorz] (takedowns PR #203) -- Done

## Downtime

- Downtime 是否與 elasticsearch 太舊有關，並檢查 DB log 輸出。
- 處理 2025/4/25 攻擊事件中的台灣 IP：加進黑名單、分析 pattern 看為啥會漏掉

## Langfuse Clickhouse follow-up

Upgrade Clickhouse to 25.3 LTS
- 從 25.1 升級到了 25.3
- ttl config `finish_time_us + toRelativeSecondNum(1 * 3600)` 仍會造成此 error
    > Illegal type UInt32 of argument of function toRelativeSecondNum. Should be Date, Date32, DateTime or DateTime64: While processing finish_time_us + toRelativeSecondNum(1 * 3600). (ILLEGAL_TYPE_OF_ARGUMENT)
- ttl 修正為 `finish_date + INTERVAL 1 DAY DELETE` --> 沒問題

## Open165

urlscan.io integration
- urlscan: 德國服務
  - 由美國公司 SecurityTrail 與 RecordedFuture 贊助，後者已被萬事達卡收購
- 提供 [API](https://urlscan.io/docs/api/)
  - submission：把輸入 url 存成新的 scan 結果，回傳 scan id
  - result 與截圖 API: 輸入 scan id 回傳 scan 資料
    - 範例網頁 https://urlscan.io/result/01969aae-df49-7768-b5f4-df2120f1e861/
    - 範例 API https://urlscan.io/api/v1/result/01969aae-df49-7768-b5f4-df2120f1e861/
    - 可用欄位：https://urlscan.io/docs/result/
        - `page.ip`
        - `page.title`
        - `page.asn`
        - `task.reportURL`
        - `task.screenshotURL` --> 存到 cloudflare？
        - `task.domURL` --> 可以載下來自己比對
    - 但 similarity search 要 USD$1000/mo ![](https://g0v.hackmd.io/_uploads/r1lMlrzBell.png)
  - 搜尋：輸入 url 與其他東西，回傳搜尋結果
    - [可搜尋欄位](https://urlscan.io/docs/search/) 包含 URL 與 title

### Open165 架構

列表來源：每週 165 公告與 API
- 拆開 title 與 URL 獨立成頁 (name detail 與 url detail)
- 送進 Urlscan

Ad hoc 來源：單一 URL --> 呈現 ne detail
Ad hoc 來源：單一名稱（ooo是真的嗎） --> 呈現 name detail


Detail 頁面：
- 165 目前公告結果
- URL scan 結果與送出到 urlscan
- 各種反詐、防治二次詐騙文案

首頁：
最新 name 列表、url 列表、urlscan 結果


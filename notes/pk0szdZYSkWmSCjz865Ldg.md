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

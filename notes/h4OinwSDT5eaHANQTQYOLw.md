---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250623 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO Hub 出席：
- 線上出席：
- Gather Town: https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## 本次會議待追蹤項目 (由 2025/06/16 會議記錄結案)

*   **Open165 重構**: Open165 重構相關 PR 已開啟，待測試。TODOs: 將 DB schema 移動到 worker 管理、在 worker 中建立子 workflow、建立資料交換格式、Website display
    --> 本週沒有更新
*   **資訊安全**: Johnson 將協助取得管理者權限、邀請大家使用 cofacts.tw email，並移除其他非 cofacts.tw email 的權限。
    --> 本週沒有更新
*   **Open165 Github Organization Webhook**: 檢查 Github Open165 organization 為何 webhook 不會觸發。
    --> 本週沒有更新
*   **小聚場地預定**: 確認 11/1 青職基地的可用性。
*   **期末感恩茶會場地預定**: 查詢 12/28 期末感恩茶會的場地。


## :potable_water: Release pipeline

### :star: Released to production

### :rocket: Staging

#### :electric_plug: API

- https://github.com/cofacts/rumors-api/pull/369
- https://github.com/cofacts/rumors-api/pull/370
- https://github.com/cofacts/rumors-api/pull/371

#### :robot_face: rumors-line-bot

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [ ] 應可送出「全新影片訊息」

##### ⛔️ Release Blockers
##### 未竟項目

#### :globe_with_meridians: Site
##### Testing checklist
http://dev.cofacts.tw/

登入自有帳號後檢測：
- [ ] Article detail
  - [ ] Can submit reply with external links

##### ⛔️ Release Blockers

##### 未竟項目


### :eye: Under review

## CCPRIP

### [Comm] Analytics

https://cofacts.tw/analytics fixed
- 除了 Opendata article trend, article 超過 100MB (經過 BigQuery external table 後應該可解)
- Opendata 好像也沒過濾掉 spam XD

### [Comm] AI 逐字稿
- 升級 NodeJS 到 22 (Gen AI SDK 要 NodeJS 20)
- 升級2l4 

### [Comm] AI chatbot

https://github.com/MrOrz/adk-agents
已升級 ADK 到正式版

## Discussions

<!-- Add discussion items here -->

## Actionable items

<!-- Add actionable items identified during this meeting -->

```
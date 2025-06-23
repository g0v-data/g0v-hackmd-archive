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
    --> 應該有？![](https://g0v.hackmd.io/_uploads/Sy76mu8Egg.png)
    --> 運作正常，無需再追蹤
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
- Vertex AI sdk 換成 [Gen AI SDK](https://github.com/googleapis/js-genai)
- 上次比較：https://g0v.hackmd.io/3WGAMK9hRQ2pPQE-0x_vOQ?view#LLM-based-AI-transcript
- gemini 2.5 pro 一直撞到限制，測不完（shared quota 用完）
- 2.5 flash vs 2.5 flash-lite: 內建可關閉的 [thinking budget](https://ai.google.dev/gemini-api/docs/thinking#set-budget)
    - 但有開 thinking 反而容易撞到 loop error
    - thinking token 會算在 max output token 裡
    - 如果有開 thinking，要記得放大 max output token 否則會在 thinking 階段就用完 token，啥都沒輸出

![](https://g0v.hackmd.io/_uploads/BJxBBfOLNeg.png)
https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/datasets/cm7ri4we80004ql0bfu6lvtoi/compare?runs=cmc8115n9005olr0869ptby94&runs=cmc7y45eo003ulr08zef9jtd1&runs=cm9pyw5mr00mfjy061mdp8mbd
- Gemini 2.5 flash 是正式版，速度跟 1.5 pro 差不多，但比較便宜
- Gemini 2.5 flash-lite 是 preview 版，會 hallucinate，速度差不多
- Gemini 2.5 系列 endpoint 都沒在台灣，location 可以填 `global`
- PR 換成 2.5 flash

### [Comm] AI chatbot

https://github.com/MrOrz/adk-agents
已升級 ADK 到正式版


### [Op] Takedown

replaceMedia 很難自動化
- Github image URL 會重新導向，不能拿來用
- 不支援一次處理[多個 API body](https://github.com/cofacts/takedowns/pull/243)
    - 有需要嗎？好像不常見 [name=mrorz]

## 大松籌備

- 7/13 Sun. 10:00-21:00
- 要填 https://g0v.hackmd.io/@jothon/g0v-hackath68n/https%3A%2F%2Fg0v.hackmd.io%2Fs%2FCOC

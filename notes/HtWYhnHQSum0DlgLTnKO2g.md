---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250630 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- Gather Town: https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## 本次會議待追蹤項目 (由 2025/06/23 會議記錄結案)

* **Open165 重構**: Open165 重構相關 PR 已開啟，待測試。TODOs: 將 DB schema 移動到 worker 管理、在 worker 中建立子 workflow、建立資料交換格式、Website display
* **資訊安全**: Johnson 將協助取得管理者權限、邀請大家使用 cofacts.tw email，並移除其他非 cofacts.tw email 的權限。
* **小聚場地預定**: 確定小樹屋的時間（十月）。
* **期末感恩茶會場地預定**: 確定 12/28 期末感恩茶會的場地及細節。
* **Release pipeline - Site**: 影片問題 (影片比較久、會有 error、單傳影片沒有反應)。
  > - [20250219 error](https://g0v.hackmd.io/qL-wd2bNSzGyKNLhb0dTaA#%E2%9B%94%EF%B8%8F-Release-Blockers)
  > - [20250224 各種分析](https://g0v.hackmd.io/10oQ0SXwToG7xu_YxJ37wg#LLM-Transcript-update)
  * 應是 API 超過 100 秒無回應，由 Cloudflare 斷開 ([524](https://developers.cloudflare.com/support/troubleshooting/http-status-codes/cloudflare-5xx-errors/error-524/))
  * Production 不會有該等問題
* **CCPRIP - Analytics**: 解決 Opendata article trend, article 超過 100MB 問題、LINE Bot menu & notification usage 壞掉的表。
* **CCPRIP - AI 逐字稿**: 將 PR 換成 Gemini 2.5 flash。
* **CCPRIP - LLM based category**: 思考 classifier 處理單一 category 耗 token 問題，以及實作方式 (Cloudflare worker 或 rumors-api)。
* **CCRIP - Takedown**: 解決 replaceMedia 自動化問題 (Github image URL 重新導向, 不支援一次處理多個 API body)。
* **大松籌備**: 填寫 https://g0v.hackmd.io/@jothon/g0v-hackath68n/https%3A%2F%2Fg0v.hackmd.io%2Fs%2FSOC。

## :potable_water: Release pipeline

### :star: Released to production

### :rocket: Staging

#### :electric_plug: API

- GraphiQL https://github.com/cofacts/rumors-api/pull/372
- 6/23
  - https://github.com/cofacts/rumors-api/pull/369
  - https://github.com/cofacts/rumors-api/pull/370
  - https://github.com/cofacts/rumors-api/pull/371

#### :robot_face: rumors-line-bot

##### Testing checklist

- [ ] 應可送出「全新影片訊息」
  - 需 < 32MB
  - 處理超過 100 秒會壞掉，正常現象；production 可以超過 100 秒

##### ⛔️ Release Blockers
##### 未竟項目

#### :globe_with_meridians: Site
##### Testing checklist

##### ⛔️ Release Blockers

## CCPRIP

## :speech_balloon: 討論

## :white_check_mark: 結論




## :calendar: Next meeting

Next meeting: 2025-07-07

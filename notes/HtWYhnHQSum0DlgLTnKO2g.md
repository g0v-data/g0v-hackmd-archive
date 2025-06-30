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
    * 尚無更新
* **資訊安全**: Johnson 將協助取得管理者權限、邀請大家使用 cofacts.tw email，並移除其他非 cofacts.tw email 的權限。
    * 尚無更新
* **小聚場地預定**: 確定小樹屋的時間（十月）。
* **期末感恩茶會場地預定**: 確定 12/28 期末感恩茶會的場地及細節。
* **Release pipeline - Site**: 影片問題 (影片比較久、會有 error、單傳影片沒有反應)。
  > - [20250219 error](https://g0v.hackmd.io/qL-wd2bNSzGyKNLhb0dTaA#%E2%9B%94%EF%B8%8F-Release-Blockers)
  > - [20250224 各種分析](https://g0v.hackmd.io/10oQ0SXwToG7xu_YxJ37wg#LLM-Transcript-update)
  * 應是 API 超過 100 秒無回應，由 Cloudflare 斷開 ([524](https://developers.cloudflare.com/support/troubleshooting/http-status-codes/cloudflare-5xx-errors/error-524/))
  * Production 不會有該等問題
* **CCPRIP - Analytics**: 解決 Opendata article trend, article 超過 100MB 問題、LINE Bot menu & notification usage 壞掉的表。
    * 尚無更新

## :potable_water: Release pipeline

### :star: Released to production

### :rocket: Staging

#### :electric_plug: API

- GraphiQL https://github.com/cofacts/rumors-api/pull/372
- 6/23 carry over
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

### [Comm] LLM based category & new `worker` repository

- 想實作在新 repo https://github.com/cofacts/worker
- 用 cloudflare workflow 週期性地呼叫 API 處理
    - 優點：
        - 原本 category 系列就是與 API 拆開（rumors-ai），所以放外面 OK
        - Cloudflare workflow 自動平行化、輕鬆 retry 的機制，很適合 LLM batch processing https://github.com/cofacts/worker/pull/1
    - 缺點：
        1. 多維護一個 repo
        2. 沒 public API 的作業無法寫在 cofacts/worker
        3. Cloudflare dependency
- 把 https://github.com/cofacts/ground-truth 上的 17K 測資放到了 langfuse dataset
    - 打算用這個做實驗
    - 實驗對象：
        - [一個大 prompt](https://github.com/cofacts/worker/pull/1/files#diff-a2a171449d862fe29692ce031981047d7ab755ae7f84c707aef80701b3ea0c80R88-R111)
        - (還沒寫) 一個分類一個 prompt
    - 比較基準
        - cost
        - accuracy & confusion matrix

### [Comm] cofacts.ai

> https://g0v.hackmd.io/@cofacts/rd/%2FmU8qi721RZeAQ9PDfj7XRA#Functionality

> mrorz@g0v-tw 發現 Gemini API 可以直接讀取 URL context，這樣就不用自己爬下來再餵給他 <https://ai.google.dev/gemini-api/docs/url-context>

- 這樣其實就能先做 groundness check agent
- 查訊息是否有出處 back 其文字，跟查特定回應文字是否有出處 back 其文字，都很方便
- 本來還想說是不是要先弄個 archivebox 啥的去處理 URL fetch，但 gemini API 有內建 tool 很完美，這樣只要準備 prompt 就好
- 可以直接做進 beta.cofacts.ai


## :calendar: Next meeting

Next meeting: 2025-07-07

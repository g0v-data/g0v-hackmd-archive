---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250707 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：mrorz, bil, nonumpa
- Gather Town: https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## 本次會議待追蹤項目 (由 2025/06/30 會議記錄結案)

* **Open165 重構**: Open165 重構相關 PR 已開啟，待測試。TODOs: 將 DB schema 移動到 worker 管理、在 worker 中建立子 workflow、建立資料交換格式、Website display
    * 尚無更新
* **資訊安全**: Johnson 將協助取得管理者權限、邀請大家使用 cofacts.tw email，並移除其他非 cofacts.tw email 的權限。
    * 尚無更新
* **CCPRIP - Analytics**: 解決 Opendata article trend, article 超過 100MB 問題、LINE Bot menu & notification usage 壞掉的表。
    * 尚無更新
*   **cofacts.ai Groundness Check**: 實作 groundness check agent 使用 Gemini API URL context 到 beta.cofacts.ai
    * 尚無更新

## :potable_water: Release pipeline

### :star: Released to production
- https://github.com/cofacts/rumors-api/releases/tag/release%2F20250702
  - GraphiQL
    - 但是要 load 超級久
  - Gen AI SDK & new transcript model
- https://github.com/cofacts/rumors-site/releases/tag/release%2F20250702 Badge related

## 2025/7/2 倒站

Downtime: 2025/7/2 20:24~21:08 共 44 分鐘

- **2025-07-02 21:10** mrorz：url-resolver 不會用超過 1GB，這次問題應該是 url-resolver 卡住，重開 url-resolver 之後就解掉了
- **2025-07-02 21:08** mrorz：正常了
- **2025-07-02 21:07** mrorz：然後 restart url-resolver
- **2025-07-02 21:05** mrorz：先 `docker-compose restart db`
- **2025-07-02 21:02** mrorz：docker stats 卡死
- **2025-07-02 21:01** mrorz：Cloudflare traffic 看起來正常
- **2025-07-02 20:59** mrorz：Load 34 很辛苦捏
- **2025-07-02 20:57** mrorz：倒站了囧
- **2025-07-02 20:24**: Cofacts monitor 🚨@g0v-tw 回報 line-bot.cofacts.tw 狀態不健康 (HTTP timeout)

---

- 收到通知的當下測試網站跟 LINE bot 都是好的 [name=bil]
  - 那好像真的是要等一下才會爛掉 [name=mrorz]
- 要重寫一個新的嗎 [name=nonumpa]
  - 想架 https://archivebox.io/ [name=mrorz]
  - 或 https://developers.cloudflare.com/browser-rendering/platform/puppeteer/
    - Example: https://github.com/Open165/worker/blob/d97649f169bee5ecd3566bf18f5c6b51a31f2dbd/src/handlers/screenshot.ts
  - 現在的 url-resolver 用 grpc 覺得痛苦（因為要 build binary 以及 sync proto files），換掉很不錯 [name=mrorz]
  - 在 url-resolver 開票追蹤

## Planned changes to Github repositories
### Claude Code Action

想在每個 github repo 加上 [claude code action](https://github.com/anthropics/claude-code-action)
- 可以 `@claude` 讓 AI 產 code 發 branch
  - Claude Github Action 沒有修改 workflow file 與開 Pull Request 的權限，這部分要手動
  - [Jules](https://jules.google.com/) 適合 ad-hoc task，Claude Code 能跟 github issue 整合很棒
- 連接到 Vertex AI 算在 Cofacts GCP 帳上

### adk-agents 移動到 cofacts 下

- https://github.com/MrOrz/adk-agents 已經 deploy 在 beta.cofacts.ai
- 更名為 cofacts/beta-ai
  - 未來有 cofacts.ai 時，因為 GUI 會自己寫、不使用 ADK web，所以應該是獨立的 repository [name=mrorz]


## 大松籌備

- 一樣 good first issue
- Open165 沒空
- 防災 goods

## :calendar: Next meeting

Next meeting: 2025-07-14

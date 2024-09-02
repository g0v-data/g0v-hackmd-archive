---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240902 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
- GraphiQL https://github.com/cofacts/rumors-api/releases/tag/release/20240827

#### Open165
- Automatic data renew https://github.com/cofacts/open165/pull/24
    - 用了 Ronny 的 midd [name=ronny++]
    - https://github.com/cofacts/open165/actions/workflows/update-db.yaml
- 「反詐筆記」與螢光筆效果 https://github.com/cofacts/open165/pull/25

### :rocket: Staging

#### :electric_plug: API
- Store to Wayback Machine https://github.com/cofacts/rumors-api/pull/344

#### :robot_face: rumors-line-bot

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [ ] 應可送出「全新訊息」
    - [ ] 送出 Wayback machine 上沒有的 URL 後，應該可以觸發 Wayback machine 產生 job ID (API log)

#### :globe_with_meridians: Site
##### Testing checklist
http://dev.cofacts.tw/

登入自有帳號後檢測：
- [ ] Article detail
  - [ ] Can submit own reply with URLs not in wayback machine
  - [ ] URLs in both reply text and reference should trigger Wayback machine job

##### ⛔️ Release Blockers

##### 未竟項目

### :eye: Under review

- Store to Wayback Machine https://github.com/cofacts/rumors-api/pull/344
- Wayback machine envs 


## Wayback machine API

API: https://archive.org/details/spn-2-public-api-page-docs-2023-01-22

Notes
- Cannot handle FB; should handle Youtube
- Screenshot (PNG) are snapshots of an artificial URL  `http://web.archive.org/screenshot/<url>`
- After submission, it takes several minutes for the archived URL to appear on wayback machine site, even after its status API said it's done.
- There is no API to get the HTML content. Need to scrape by our own if that is needed.

Questions
- Whose keys to use?
    - Just use arbitrary account? Or share account?
    - Data sent by API is not shown anywhere after logging in, though
- Show in UI?
    - Link to `https://web.archive.org/web/*/<canonical url>`
    - Screenshot: `https://web.archive.org/web/*/http://web.archive.org/screenshot/<canonical url>`
        - Example: https://web.archive.org/web/*/http://web.archive.org/screenshot/https://tfc-taiwan.org.tw/articles/9311
- Job ID & status?
    - Do we need to handle or record them?
- Backfill (archiving old URLs)?
    - Can directly backfill using `article_hyperlinks` or `replies_hyperlinks` in HuggingFace dataset

---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240902 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO hub：bil, Conrad, mrorz, nonumpa
- 線上出席：T
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

NPO Hub 冷氣壞了！


## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
- GraphiQL https://github.com/cofacts/rumors-api/releases/tag/release/20240827

#### Open165
- Automatic data renew https://github.com/cofacts/open165/pull/24
    - 用了 Ronny 的 https://github.com/g0v-data/165-data [name=ronny++]
    - https://github.com/cofacts/open165/actions/workflows/update-db.yaml
- 「反詐筆記」與螢光筆效果 https://github.com/cofacts/open165/pull/25

### :rocket: Staging

#### :electric_plug: API
- Store to Wayback Machine https://github.com/cofacts/rumors-api/pull/344

#### :robot_face: rumors-line-bot

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 應可送出「全新訊息」
    - [x] 可以觸發 Wayback machine 產生 job ID (API log)
    - [ ] 圖片也可以觸發

#### :globe_with_meridians: Site
##### Testing checklist
http://dev.cofacts.tw/

登入自有帳號後檢測：
- [x] Article detail
  - [x] Can submit own reply with URLs not in wayback machine
  - [x] URLs in both reply text and reference should trigger Wayback machine job

##### ⛔️ Release Blockers

##### 未竟項目

沒有 http:// or https:// 開頭的都沒有辨識出來
https://dev.cofacts.tw/article/GduxspEBoURTSGJKAAMu
- Known issue, API `hyperlinks` 欄位的 extraction 使用的 regex 本來就不處理「沒有 http:// or https:// 開頭的 URL」
- 跟 API hyperlinks detection 一起開在 rumors-api

修改逐字稿是否要重新觸發 Wayback Machine 儲存？
- 放著
- 開 issue

:::success
https://github.com/cofacts/rumors-api/issues/345
:::


### :eye: Under review

- Store to Wayback Machine https://github.com/cofacts/rumors-api/pull/344
- Wayback machine envs https://github.com/cofacts/rumors-deploy/pull/26

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
    - Conclusion: No need for share account for now. [name=bil]
- Show in UI?
    - Link to `https://web.archive.org/web/*/<canonical url>`
    - Screenshot: `https://web.archive.org/web/*/http://web.archive.org/screenshot/<canonical url>`
        - Example: https://web.archive.org/web/*/http://web.archive.org/screenshot/https://tfc-taiwan.org.tw/articles/9311
    - Open issue in rumors-site, `#design`, post to g0v slack #design channel
    :::success
    https://github.com/cofacts/rumors-site/issues/576
    :::
- Job ID & status?
    - Do we need to handle or record them?
    - No need [name=bil]
- Backfill (archiving old URLs)?
    - Can directly backfill using `article_hyperlinks` or `replies_hyperlinks` in HuggingFace dataset
    - 開票，good first issue，可以是一個 python notebook --> good first issue to rumors-api 

## Open165 license

> 我今天想要再 raise 一下「把 Open165 license 換成 AGPL 來讓詐騙集團很難直接 clone 來用」這件事，看有沒有人有 concern。
> 想法是
> - AGPL 強制 host Open165 的人都要開源
> - 詐騙集團應該不會想開源（會暴露多餘的資訊），此時我們可以試著向詐騙網域的 Domain registrar 發 copyright infrigement 要求其下架該網域
>
> 看大家對這件事情有沒有什麼想法（這會 work 嗎、轉 AGPL 是否有其他隱憂⋯⋯> 等）
> [name=mrorz]

:::success
已在 Slack
:::

## ＧＡＩ的教學
By Conrad ++ https://docs.google.com/presentation/d/1inqEXQ1zHySQQMt9EYDGyqbVhzRF9jOzEEmn64jASgM/edit#slide=id.p

- LINE

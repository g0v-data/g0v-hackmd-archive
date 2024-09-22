---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240923 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :female-police-officer: Open165

Summary + accordion + 165 官方公告連結
https://165.g0v.tw/name/%E4%B8%8A%E6%B5%B7%E6%9C%9F%E8%B2%A8%E4%BA%A4%E6%98%93%E6%89%80

- [Direct hit display in detail pages #26](https://github.com/Open165/site/pull/26)
- [Sync announcements in 165 to DB #27](https://github.com/Open165/site/pull/27)
- [Name detail page summary and refactor #28](https://github.com/Open165/site/pull/28)

#### :globe_with_meridians: Site
#### :robot_face: rumors-line-bot

#### :electric_plug: API

- https://github.com/cofacts/rumors-api/pull/347

### :rocket: Staging

- https://github.com/cofacts/rumors-line-bot/pull/398

#### :robot_face: rumors-line-bot

##### Testing checklist

:::info
上週發生什麼事：https://g0v.hackmd.io/UHKMm7h_QIe5EB4Z0cGQ3g?view#%E2%9B%94%EF%B8%8F-Release-Blockers
:::

https://lin.ee/1QUzEX4nI

- [ ] A 回報一組圖文
- [ ] A 在網站上回覆其中一個 article
- [ ] B 把同一組圖文 + 一個多的文字，回報成新的 cooccurrence
- [ ] 觀察現有 article 的 reply request count

##### ⛔️ Release Blockers
##### 未竟項目

### :eye: Under review

## Open165

- Wayback machine 方面：
  - 其實很多 165 回報的網址都已經被 Wayback machine 存檔 [name=mrorz]
  - 除了少數部落格型態的會被正常存檔外，其他 SPA 很容易壞掉
  - 可能自己存比較好
- New discoveries: https://g0v.hackmd.io/xl7YbrcTRECluGKK_HGo6Q#%E7%B6%B2%E7%AB%99%E5%85%A7%E6%96%87
  - 可以比外觀、code、IP
  - 針對 165 沒有收錄的網址，也能爬一下外觀、code、IP，與已知詐騙比對 --> 能及早發現換湯不換藥的詐騙！
- 需要 [browser rendering worker](https://developers.cloudflare.com/browser-rendering/)
- 網站移動到 github.com/Open165/site ，recon worker 放 github.com/Open165/worker
- 之後打算 recon endpoint 用 turnstile (Cloudflare 的 captcha) 保護

## CCPRIP

### [Infra] Logging & Observabilty

> CCPRIP doc
> https://g0v.hackmd.io/BRsJOevWSbyUMBSZEVVWrA#Logging-and-monitoring




## RightsCon


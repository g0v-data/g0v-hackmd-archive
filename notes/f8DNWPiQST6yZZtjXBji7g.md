---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210331 會議記錄


:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, lucien, ggm
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

[0325 release](https://github.com/cofacts/rumors-site/releases/tag/release%2F20210325)

- Absolute date for UI [#419](https://github.com/cofacts/rumors-site/pull/419) [#420](https://github.com/cofacts/rumors-site/pull/420)
    - kerrickstaley++
- Wrap long text in detail page [#418](https://github.com/cofacts/rumors-site/pull/418)
    - playpool513++

#### :electric_plug: API

- iOS login fix [rumors-api#251](https://github.com/cofacts/rumors-api/pull/251), [rumors-deploy#18](https://github.com/cofacts/rumors-deploy/pull/18)


### :rocket: Staging

#### 🗄️ rumors-db

- [Schema versioning mechanism](https://github.com/cofacts/rumors-db/pull/53)

:::info
Deployment steps

1. [x] Perform backup
2. [x] Setup SSH tunnel
    ```
    ssh -L 62222:<elasticsearch-ip-on-server>:62222 <server url>
    ```
3. [x] Execute
    ```
    npm run reload -- users
    npm run reload -- articles
    npm run reload -- replies
    npm run reload -- urls
    ```
:::

#### :globe_with_meridians: Site

##### Bugfixes

DB fix should fix the following bugs:

- [#399 slug](https://github.com/cofacts/rumors-site/issues/399)
    - Have infinite redirect issue...
- [#386 user does not exist](https://github.com/cofacts/rumors-site/issues/386)

##### Testing checklist

http://dev.cofacts.org/

- [ ] Test if #399 can no longer be reproduced
- [ ] Test if #386 can no longer be reproduced

## Devs

- [x] 修復 iOS 登入
- [x] Slug unicode support 
- [ ] [Google sign-in](https://github.com/cofacts/rumors-api/issues/234) [name=nonumpa]
- [ ] 4 月初：deploy API header 讓第三方接取 [name=mrorz]
- [ ] 4 月初：公開 profile page 
    - [ ] revert the PR that [hid profile](https://github.com/cofacts/rumors-site/pull/378)
- [ ] apply 日文翻譯 --> ja.cofacts.org / ja.cofacts.tw
- [ ] [LINE bot 送出流程改版](https://github.com/cofacts/rumors-line-bot/issues/214)
    - 目標：更簡單地送出流程、LIFF 不要 send message to chatroom (為 share dialog 做準備)

## 4/10 小聚 @ AIC

- [ ] 問酒精、體溫誰負責 [name=bil]

## 防詐顯名

1. 圖改成機器人的圖
2. 「看看 Cofacts 上，大家怎麼說」-->
「Cofacts 聊天機器人為您查證」
3. 「覺得不安全，回報給防詐達人」-->
「看 Cofacts 真的假的協作平台」
4. URL 試試看 https://line.me/xxxx/x/https://cofacts.org/article/xxxxxx


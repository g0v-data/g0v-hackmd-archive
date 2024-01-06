---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210303 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, hsiao, zoe, nonumpa
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site
- 2/25 release https://github.com/cofacts/rumors-site/releases/tag/release%2F20210225

#### :robot_face: LINE bot
- 2/25 release https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20210225

#### :electric_plug: API
- [DIFF](https://github.com/cofacts/rumors-api/compare/d679bc118185a4df2dcc5dbda464b548a82629c8...bb6778705fdc41c61284601359f8ecdfb5f0a479)
    - #247 Avatar related changes

#### :pray: Community Builder
- #4, #5 [Thank-you editors](https://cofacts.github.io/community-builder/#/editorworks) Feedbacks & comments list
    - Known issue: 2nd page does not work...

### :rocket: Staging

#### :electric_plug: API
- #248 Contribution API on `GetUser`

#### :globe_with_meridians: Site
- #398 impact report translation & animation
- #395 edit avatar
- #402 contribution graph

大家看一看自己的 contribution graph 會不會壞掉～

- 「了解更多」 --> 要使用 context [name=hsiao]
- adaptive max contribution
    - `max(10, max(user_contribution))` 作為 contribution graph 的 max scale
- Mobile 等比例縮小會太小
    - 參考 github cropping ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_62e15ade0ddef5b1111d9d3d7aab998d.gif)
- 1次、2次的 contribution 會被 round 成沒有 contribution 的顏色 [name=nonumpa]
    - 改用 `Math.ceil`

:::success
開票：https://github.com/cofacts/rumors-site/issues/413
:::

## 2021 三月計畫

- 3/start 寄送 impact report
- 3/1：零時小學校＠台南
- 3/5 簡訊設計影片完成
- 4 月初：enforce API header

### Impact report

- 寄送對象
- Report 開發進度
    - [x] 1st fold, intro, participate, video, donation, features, footer
    - [ ] ecosystem + 香檳塔 - ongoing
    - [ ] 新詩、媒體報導、演講經歷
    - [ ] 得獎紀錄 timeline
    - [ ] 影響、特色、理念 etc
    - [ ] 不實訊息案例

### 零時小學校

- profile page URL 不能用中文 - https://github.com/cofacts/rumors-site/issues/399
- iOS 必須使用 cofacts.g0v.tw；cofacts.tw 會無法登入 [name=mrorz]
    > production 是 cofacts-api.g0v.tw -> cofacts.g0v.tw
    > staging 是cofacts-api.hacktabl.org -> dev.cofacts.org
    > 所以 prod 不會有登入的問題 [name=zoe]

### Group chatbot analytics

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6e9553d895c520d1a6bf82625a11b7f2.png)

本週沒空分析 QQ 下週ㄅ

## Further TODOs

Walk through tickets in API, site & LINE bot

### Features
- [Cofacts API header for apps](https://github.com/cofacts/rumors-api/issues/244)
- [Google sign-in](https://github.com/cofacts/rumors-api/issues/234)

### Bugfixes
- [編輯 URL 不能用中文](https://github.com/cofacts/rumors-site/issues/399)
    - 與 [#242](https://github.com/cofacts/rumors-api/issues/242) 接近
- [ListArticle sorting 應該與 filter 相關](https://github.com/cofacts/rumors-api/issues/243)

## Show join date on profile page

> 參與零時小學校之後，看到開始有新血加入，覺得很開心～～
> 我突然想起之前 [profile page pilot study](https://g0v.hackmd.io/lIedGsQWTeScBTWfr4Zq0w) 時，有編輯提到：
> > 在看了其他人貢獻之後，會好奇他加入 Cofacts 的時間
>
> 我剛才也有想看看這個人什麼時候加入 Cofacts 的想法。想問其他編輯對這個功能有什麼疑慮嗎？沒有的話我就開票紀錄囉～？ [name=mrorz]

> 這應該有隱私疑慮？:thinking_face:
> 要讓使用者能決定要不要公開 [name=lucien]

> 那感覺也可以做成
> 某個等級之後讓使用者能設定是否要隱藏
> 但對低等級編輯來說就是一率公開
> 例如說 spammer 通常等級都很低
> 如果強制顯示註冊日期
> 在社群討論的時候就能直接貼出 profile page 們，讓大家看到這些人在同一天註冊、然後又針對同一篇回應做操作之類的，比較容易讓社群進行 anti-spam 檢舉
> [name=mrorz]

> 應該沒有太隱私，滿多社群都有顯示這個
> contribution 不能 hide 的話，其實也能看得出來什麼時候活躍 [name=zoe]

:::success
[開票](https://github.com/cofacts/rumors-site/issues/412)，先不考慮「隱藏」功能
:::




---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250203 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
#### :globe_with_meridians: Site

https://github.com/cofacts/rumors-site/releases/tag/release%2F20250127
- AI reply feedbacks
- News

#### :robot_face: rumors-line-bot

https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20250127
- AI reply feedbacks

### :rocket: Staging

#### :electric_plug: API

- Internet archive logging https://github.com/cofacts/rumors-api/pull/358
    - Found that my internet archive secrets is rotated.
    - Archiving is back to work after I update the secret on Feb 1st
- uploadMedia refactor https://github.com/cofacts/rumors-api/pull/360
    - Upgrade GCS SDK used in media-manager https://github.com/cofacts/media-manager/pull/11
- Gemini transcript https://github.com/cofacts/rumors-api/pull/359 (WIP)

#### :robot_face: rumors-line-bot

- Fix AI reply sender name https://github.com/cofacts/rumors-line-bot/pull/402
- Long response handling https://github.com/cofacts/rumors-line-bot/pull/401

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [ ] 應可送出「全新訊息」
    - [ ] 選擇「整篇轉傳」後會詢問是否要送出訊息。
    - [ ] 同意送出訊息後就會送出訊息，並得到：
        - [ ] Cofacts article page 按鈕
        - [ ] AI reply
        - [ ] 寫理由的按鈕
        - [ ] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [ ] 送出「沒回應」的舊訊息，應可顯示 AI reply
    - [ ] 文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。
    - [ ] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [ ] 可以修改理由送出。查看 article page 看理由是否有被送出。
    - [ ] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [ ] 送出「有回應」的舊訊息，應自動回傳回應
    - [ ] 應列出訊息所有的回應
    - [ ] 選擇回應之後可以幫回應 upvote
    - [ ] 可以再次選擇 downvote
    - [ ] 選完回應之後，還可以捲回去選其他回應
    - [ ] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [ ] Rich menu 測試
    - [ ] 「教學」可以觸發教學流程

##### ⛔️ Release Blockers
##### 未竟項目
### :eye: Under review
- LINE bot https://github.com/cofacts/rumors-line-bot/pull/401
- API (WIP) 


## AI reply feedbacks analysis



## Communication

- Global Alliance for AI
- TES


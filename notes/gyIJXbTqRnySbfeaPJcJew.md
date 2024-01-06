---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220406 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, nonumpa, mrorz
- 線上出席：Jiahe
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :electric_plug: API

- [List api enhancements #275](https://github.com/cofacts/rumors-api/pull/275)
- [Install pino logger and add query logging plug-in #276](https://github.com/cofacts/rumors-api/pull/276)
    - Staging 上的 log 預設關閉，因為有人會定期戳 staging [name=mrorz]

#### :robot_face: rumors-line-bot

- [Reply request form for LIFF #300](https://github.com/cofacts/rumors-line-bot/pull/300)

- [ ] Rich menu / LIFF 測試
    - [ ] 「設定」更改後再次打開，應該會保留原本設定
    - [ ] 「查過的訊息」可以正常運作
- [ ] Comment LIFF 運作正常
    - [ ] 在 LINE 裡面送出 https://liff.line.me/1563196602-X6mLdDkW?p=comment&articleId=3tu9btf8s50sm 後再點開連結，跳出 comment LIFF
    - [ ] 可送出 reply request
        - [ ] 字數太少會跳窗指導說要長一點
        - [ ] 如果有寫字，送出後會先謝謝使用者，再關閉
            - [ ] 此時按取消的話就可以繼續打 comment
        - [ ] 沒有輸入的話，會先跳窗指導說要寫長一點。如果繼續，就不會謝謝使用者而直接關閉。
    - [ ] 再次點開，可以顯示之前寫的 reply request


https://liff.line.me/1563196602-X6mLdDkW?p=comment&articleId=1bwwy8y2st6p8

##### ⛔️ Release Blockers

##### 未竟項目
- 電腦版 LINE：
    - 如果有跳登入，就會關不掉
        - 似乎是瀏覽器行為 [name=mrorz]
    - 如果已經登入，就可以關得掉
- Alert「article not found」
    - 因為之前沒有送過 reply request
    - 但之後在 chatbot 裡，一定會先送過空的 reply request 才會給這個連結，所以應該 OK [name=mrorz]
- 無法清空 reply request，送出後下一次還是會有字 [name=mrorz]
    - 此行為可以接受

### :eye: Under review

- [Reply request form for LIFF #300](https://github.com/cofacts/rumors-line-bot/pull/300)

## 大松籌備

- 50 份傳單
- bil 提案

## 無回應流程 Revamp

- 理想的新 state diagram: [![State diagram](https://docs.google.com/drawings/d/e/2PACX-1vSjTIcpV0M5UAsmMNWl3Feph3jTgvZ3yykC7r4lUtHWWvSdYwNjpfMkO9jTwTdja7ZaKFf-I4F6xB2N/pub?w=1614&h=1046)](https://docs.google.com/drawings/d/1jnrRJG8zs8HZTjgey0FbNQjo5FpylE47_-jiPiuD3iY/edit)
- 無論是新訊息送 reason 還是無回應送 reason，都會導向到 `handlers/askingReplyRequestReason`
    - `handleInput` 裡會偵測 LIFF 送的 prefix，但兩者都會送進 `ASKING_REPLY_REQUST_REASON` state ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2be4e09dbe4b150be260afead991aedb.png)
    - 現況似乎與 state diagram 不符 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_624a469f5fb3bab62266b1a85d36ab0c.png)
- 由於 create message 路徑仍然會用到 `handlers/askingReplyRequestReason` 裡的邏輯，所以此 handler 暫時拔不掉
- 還在 update unit test，下次檢查是否有弄壞 create message flow

:::success
不要動到 asking reply request reason 邏輯，先出一版更新 choosing article 的就好
:::

### Wording change
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_42057d7e3432a10dd76d6b7c195a53f8.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d1d64e46a2a9cc2286cd23b5144e6675.png)

- Using flex message to avoid user sharing the same wording to chatbot again
- But flex message cannot have hyperlinks
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_63b75bf9325f3e28cc6a3d258f7bc5c3.png)
- Add button? Add card in carousel?

:::success
Add button solution
:::

## Multimedia 開發時程

https://docs.google.com/document/d/1CI9YoWvKkCWYFtdHYJbH_oE3Viii8HZF4ADB7GCXjpA/
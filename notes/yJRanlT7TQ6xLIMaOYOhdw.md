---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240701 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
https://github.com/cofacts/rumors-api/releases/tag/release%2F20240630

### :eye: Under review

## CCPRIP

### [Op] 已封鎖訊息仍會被搜尋
> Ref: https://g0v.hackmd.io/iCoUCvJXTrSh2eddLcti0Q?both#%E8%A9%AD%E7%95%B0

- TXT 的 source map 無法指定 last mod time，不會觸發重抓
- 針對沒有重抓的 514 網頁重做 XML 的 source map --> 還是沒有重新爬取⋯⋯ ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2ea03b23602b8e9792fffb6fd9ca32a6.png)

### [Comm] AI transcript improvement
> Design doc: https://g0v.hackmd.io/@cofacts/rd/%2Fwkx286lmTDaFUpgRhnUawQ

Gemini multimodal LLM
- 同時可處理影像與聲音
- 一個 prompt 可以用在無人聲有字幕影片，也能用在有人聲無字幕影片
- 沒有貴很多

問題
- 要先傳到 GCS or File API (不穩定)
- 即使是 flash，速度也沒很快
- RECITATION error 問題
- 莫名 safety filter


## LINE bot long response handling

https://github.com/cofacts/rumors-line-bot/blob/master/src/webhook/handlers/singleUserHandler.ts#L78

figma: 

- chat window
- singleUserHandler
  - stores latest webhook event's reply token in context
  - send() reads token from context instead of the webhook event that triggers this query
  - when timeout, send a message to ask user to "continue" ad snack message
    - when the user press continue, it replies nothing, just update reply token
- handlePostback/processOOO 等回傳 Result 的東西

---

特殊狀況：
- send 被呼叫時，已經是下一個 search session 了
  - 不要做任何事情
  - 或者把 reply token 花掉，真的好了的時候用 [send push message](https://developers.line.biz/en/reference/messaging-api/#send-push-message)
- Result 回來、send() 呼叫時已無 reply token（使用者沒按「繼續」）
  - 把 replies 存起來等使用者按「繼續」時立即回應
  - 動用 push message API


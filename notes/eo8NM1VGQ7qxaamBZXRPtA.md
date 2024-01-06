---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220316 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz, nonumpa
- 線上出席：cai, 4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### need-to-check-list-generator
備用 - https://github.com/cofacts/need-to-check-list-generator/pull/8

## 演講 feedback
- 聲音如何闢謠
    - chromaprint https://g0v.hackmd.io/aJqHn8f5QGuBDLSMH_EinA#Hashed-file-names
    - https://oxygene.sk/2011/01/how-does-chromaprint-work/

## 小聚檢討

[小松果](https://g0v.hackmd.io/Dw2J8hqsRcqRO0abDxTkBQ)
- 人很多很開心 [name=bil]
    - 報到率 8 成
    - 3~4 個人沒有報到名還是來了
- 下次不會有揪松幫我們做紅龍
    - 可以借紅龍
    - 直的 A4 中間插進去
- 下次要約 keyholder
    - 洗手台有很多杯子 > 30 個
- 場佈
    - 一排六張桌子有點難前後移動 [name=mrorz]
    - 改成一排 4 張、放 3 排
- 很早到的人怎麼辦 [name=bil]
    - 搬桌子
    - 聊天 (?)
- 假訊息的邏輯性，治療跟防範意義不一樣
    - 對身體好 != 可以治病
- Airplay 不太穩定 [name=mrorz]
    - 影片很卡
    - 視窗、投影片切換偶爾會卡
    - 如果 HDMI 可以 work，就使用 HDMI
- 網路不一定要架
    - 有遇到問題的人，是連到 cofacts 很慢，所以換 NPO hub 變快
- 二樓有助於提升報到率 (?)
    - 易達性比 4F 好
    - 有 walk-in 的人（只有一個地方）沒有門鈴擋住
    - 其他人有遇過街道聲音太吵、需要虛掩樓梯間門的狀況，但 Cofacts 還好
- 表單應開放所有人編輯
    - 有備用很好
    - 讓 walk-in 可以改 tab name
    - 每個人可以記錄自己做到哪

## 送出訊息 wording

[![State diagram](https://docs.google.com/drawings/d/e/2PACX-1vSjTIcpV0M5UAsmMNWl3Feph3jTgvZ3yykC7r4lUtHWWvSdYwNjpfMkO9jTwTdja7ZaKFf-I4F6xB2N/pub?w=1614&h=1046)](https://docs.google.com/drawings/d/1jnrRJG8zs8HZTjgey0FbNQjo5FpylE47_-jiPiuD3iY/edit)

### Limitations

Quick reply label lengh: max 20 characters ([Ref](https://developers.line.biz/en/reference/messaging-api/#postback-action))

### 1. Nothing is found - Ask for source

:::info
Wording see discussion in [20220223](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2FReVDO3iiSQ28qG0XTOovKQ)
:::

> Unfortunately, I currently don't recognize "`${inputSummary}`", but I would still like to help.
> May I ask you a quick question?
> 抱歉我目前還不認得「`${ inputSummary }`」這個訊息，可是我還是想幫你查證。
> 想先請教您一個問題：

> Did you forward this message as a whole to me from the LINE app?
> 請問這個訊息是你從 LINE 裡整篇分享給我的嗎？

Quick reply options

> - Yes, I forwarded it  as a whole
>   是，我整篇分享過來的
> - No, typed it myself
>   否，我自行打字輸入的

### 2. Listed articles don't match - Ask for source

> I am sorry you cannot find the information "`${ inputSummary }`" you are looking for. But I would still like to help.
> May I ask you a quick question?
> 抱歉沒有找到你想要查詢的「`${ inputSummary }`」。可是我還是想幫你查證。
> 想先請教您一個問題：
 
> (詢問來源同 1)


### 3. Not forwarded - Explaination & Suggestion

:::info
如果被擋住，要解釋真的假的是個機器人的概念、只接受網路上分享轉傳的訊息，沒辦法直接回答疑問、引介真人查證
:::

> I am a bot which only recognizes messages forwarded on LINE, therefore it is important to send me the **entire message** that is being passed around so I can identify it.
> 我是一個機器人，只認得在 LINE 上面傳來傳去的訊息，所以把**整篇**訊息給我，我才能辨認唷！
> 
> You can try:
> 請試試：

Carousel of suggestions
> - Try again with the whole message
>   重新傳整篇訊息給我
>   If you have access to the whole message on LINE, please use the "Share" function to share it with me.
>   如果你在 LINE 上收到這則訊息的全文，請長按該訊息並使用「分享」來把訊息分享給我。
>   Button: See Tutorial (Enters tutorial) 查看教學
> - Find a real person to help you verify this information on MyGoPen
>   求助 MyGoPen 真人查證
>   You can forward your question to another LINE account which provides a human response
>   你可以把問題傳給其他有真人查證服務的 LINE 帳號。
>   Button: MyGoPen 真人查證

- 詐騙 165、市政 1999
    - 直接從手機打電話會有點貴 [name=bil]
    - 建議保持資訊簡單

### 4. Is forwarded - Ask for consent

> I see. Don't trust the message just yet!
> 這樣呀。請先不要相信這個訊息唷！
> 
> Do you want someone to fact-check this message?
> 你要請人查查這則訊息嗎？
>
> Currently we don't have this message in our database. If you think it is most likely a rumor, **press “🆕 Report to database” to make this message public on Cofacts database** and have volunteers fact-check it. This way you can help the people who receive the same message in the future.
> 目前資料庫裡沒有您傳的訊息。若您覺得它很可能是一則謠言，**請按「🆕 送進資料庫」在 Cofacts 真的假的資料庫公開這則訊息**、讓好心人查證與回覆。您可以幫助到未來同樣收到這份訊息的人。

Quick reply options

- 🆕 Report to database 送進資料庫查核
- Don't report 我不想回報訊息

-----

- 「成為首位～的人」有點長 [name=mrorz]
    - 搶頭香來請志工查核？
    - 來搶叫人查核的頭香

### 5. Don't publish - Thanks

> The message has not been reported and won't be fact-checked. Thanks anyway!
> 好的，那就不查囉。還是謝謝你！

### 6. Agree to publish - Thanks

- Reason LIFF prompt
- Notification setup (if not turned on)

> The message has now been recorded at Cofacts for volunteers to fact-check. Thank you for submitting!
> 訊息已經被收錄至 Cofacts 真的假的，讓好心人來查證。謝謝您的回報！
> - Button: View reported message 檢視回報訊息
>
> In the meantime, you can:
> 接下來您可以：

Carousel of follow-up actions

> - Provide more detail
>   提供更多情報
>   It would help fact checkers a lot if you provide more detail :)
>   您可以提供更多關於此訊息的情報給查證志工，讓好心人更容易查真假唷！
>   - Button: Provide detail 提供更多情報
> - 🔔 Receive updates
>   開啟小鈴鐺
>   You can turn on notifications if you want Cofacts to notify you when someone replies to this message.
>   若希望我在有人回應這則訊息時通知你，請開啟通知功能唷！
>   - Button: Go to settings
      前往設定
> - Ask for help
>   請教親友
>   We all get by with a little help from our friends 🌟 Share your question to friends, someone might be able to help!
>   遠親不如近鄰🌟問問親友總沒錯。把訊息分享給朋友們，說不定有人能幫你解惑！
>   - Button: Share on LINE 在 LINE 上問人
>   - Button: Share on Facebook 請教臉書大神

### 7. No replies - Thanks

> This message has already published on `${articleUrl}` , and will soon be fact-checked by volunteers. Don’t trust the message just yet!
> 此訊息已經被收錄至 `${ articleUrl }` 有待好心人來查證。請先不要相信這個訊息唷！
>
> In the meantime, you can:
> 接下來您可以：

Carousel of follow-up actions - see 6.

## 送出流程開發 breakdown

- 先做 7
    - 拿掉一個 state
    - 做新的 reason LIFF
        - 吃一個 article id 而非 session ID
        - 送出後直接在 LIFF 中感謝使用者，不需要 sendMessage 到 chatroom
        - 把現有 reason LIFF 更名 legacy reason LIFF，之後拿掉
- 再做 1~6
    - 切不開⋯⋯
    - remove legacy reason LIFF & source LIFF


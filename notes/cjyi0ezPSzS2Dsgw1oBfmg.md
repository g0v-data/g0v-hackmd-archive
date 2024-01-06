---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20210630 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: rumors-line-bot

https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20210623

### :rocket: Staging

#### :robot_face: rumors-line-bot

- #267 Common LIFF components
- #268 Replace svelte-material-ui with common components

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [ ] 應可送出「全新訊息」
    - [ ] 問訊息來源時選擇「我自己打的」或「LINE 外面看到的」，應該會被擋下。
    - [ ] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，訊息應該還是有被送出。
    - [ ] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [ ] 選擇回應之後可以幫回應 upvote
    - [ ] 可以再次選擇 downvote

- [x] Rich menu 測試
    - [x] 「設定」更改後再次打開，應該會保留原本設定

##### ⛔️ Release Blockers

送出 upvote / downvote 理由會變空的。
必須修好才能上，否則會收不到理由。

##### 未竟項目

## 大松檢討

[成果](https://g0v.hackmd.io/K2UA8LDXT7qGIa0WZV77OA#Cofacts-Hackath44n-%E5%8D%94%E4%BD%9C%E9%A0%81%E9%9D%A2)

- 過程很好 後來人很多 [name=bil]
- 佈置很好 [name=bil]
- 放音樂 [name=bil]
    - 但等於是其他人不能放音樂 ._. [name=mrorz]
    - 可以讓小精靈放音樂不想聽的自己靜音，想講話或宣布訊息才不會也被靜音 [name=nonumpa]
- 投影進度滿好的 [name=bil]

## 小聚

- 時間
    - 7/24 (六) 2pm - 4pm
    - 7/10 (六) 2pm - 4pm 解封前
- 規劃 
    - 線上活動 3hr 有點累 [name=bil]
    - 休息 10min

### 人數估計

- 60% 報到率 --> 上限 50 人
- Gather 可能對年長者不友善
    - 不能指定年齡的話應該改用 jitsi？ [name=bil]
    - 可以舉手 + slido
    - 依照 workshop 經驗，參與者會需要 30min 熟悉 gather
- 優先發給不會去的地方
    - ex: 東部
    - ex: 除了台中台南高雄台北桃園新竹的西部
    - demography 指定地區就不能指定年齡

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bba60bb88ecedbeb7c0fe6f79423eb20.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_76c510cf78889c5d1dd71176f491e473.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7b0573731459496c6771aa9f7b308809.png)

- kktix 22nd https://cofacts.kktix.cc/events/cofacteditor22 audience 27,750 --> 報名 18

## 回信

- [獨角文化](https://www.facebook.com/watch/108244427419964/606662173300943)
    - 要去台中拍
    - https://ws.ndc.gov.tw/Download.ashx?u=LzAwMS9hZG1pbmlzdHJhdG9yLzEwL3JlbGZpbGUvMC8xMzEzOC9lMWNiOTg1Mi1hZGQxLTQyZTMtOWQ0MS1mNWE0MDI2ZjEzYWMucGRm&n=5ZyL55m85pyDMTA4MTIxOOaWsOiBnueovy0tIOWci%2bWutuaWsOWJteWTgeeJjOOAjFN0YXJ0dXAgSXNsYW5kIFRBSVdBTiDjgI3mm53lhYkucGRm&icon=..pdf


## numbers
authentic media work


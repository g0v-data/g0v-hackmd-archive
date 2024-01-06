---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210616 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz, nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

No production releases this week.

### :rocket: Staging

#### :robot_face: rumors-line-bot

- [Storybook for LIFF component](https://github.com/cofacts/rumors-line-bot/pull/262)
    - Deployed storybook: https://cofacts.github.io/rumors-line-bot/
- [Change main branch to master](https://github.com/cofacts/rumors-line-bot/pull/261)

### :eye: Under review

#### :robot_face: LINE bot

- [Storybook for LIFF component](https://github.com/cofacts/rumors-line-bot/pull/262)
- [Include Cofacts API schema in repo](https://github.com/cofacts/rumors-line-bot/pull/263)

## Migration 後一週觀測

### LINE
人數持續下滑
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2cf57c16eb3b21f1f31eb9a5a7e68bce.png)

##### 6/8 ~ 6/12

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5b258b5a45ba2450363aad12ebfa224d.png)

30 errors
- 2021/06/08 凌晨改 web concurrency = 3（重開期間得到 2 個 error 502）
- 絕大多數為 Request timeout
- 1 個 500 error (日本時間 6/08 17:01:38	 ~ 17:01:38)
- 1 個 521 error (日本時間 6/12 10:00:00 ~ 10:00:03)

##### 6/12 ~ 6/16

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7aa92233c65abf7a827cc8cac4c0ab29.png)

23 errors
- 絕大多數為 Request timeout
- 2 個 "Connection timeout: https://line-bot.cofacts.tw/callback"
- 1 個 521 error (日本時間 6/12 10:00:00 ~ 10:00:03)

### Linode

擷取時間：2021/6/16 15:00

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2442c3945ecad65a5646a255235c6406.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f04d9d60f3a3700f158697a1561d2c85.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_66f52f63728e37a982b13bc538485eb8.png)

### Cloudwatch

LINE bot production 的對話紀錄現在會放進 Cloudwatch (東京機器)

最早 log：2021-06-06T01:33:01.078+08:00
已存放：296.85 MB

--> 10 天 300MB, 一個月 1GB

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5a081e5cc6067c320020b8065c481889.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0567d9a46940c585a48177ef3ccfdcae.png)


## Dev

### Article LIFF

https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/?node-id=3004%3A224
1. [x] 實作 common component storybook
2. [ ] 實作 feedback form + 使用在目前的按鈕上
3. [ ] 實作 reply request form + 使用在目前的按鈕上
4. [ ] 實作 article & reply
5. [ ] 實作 reply request list
6. [ ] 實作 related article

## 總統文化獎

目的：讓社群能量被看到
如 [IFCN 獲得諾貝爾和平獎提名](https://newtalk.tw/news/view/2021-01-22/527219)

https://www.gacc.org.tw/events/award/current

> 青年創意獎　青年是國家社會的新創造力
> 四十歲（1981年1月1日（含）後出生）以下，展現新世代之創意文化，具有顛覆與創新之思維與實踐，具有卓著影響的青年朋友。
>
> 社會改革獎　改革是社會進步的動力
> 長期致力於推動社會改革、倡議社會進步價值，提出解決方案，對於台灣社會發展具有重大貢獻者。

以團體參加：`「Cofacts 真的假的」訊息回報機器人與查證協作社群`

歷屆得獎名單：https://zh.wikipedia.org/wiki/%E7%B8%BD%E7%B5%B1%E6%96%87%E5%8C%96%E7%8D%8E#%E5%BE%97%E7%8D%8E%E5%90%8D%E5%96%AE

1. 用個人代表團體的話就用不到基金會名義
2. 青年創意獎有年齡限制，團體不知道怎麼算
    - 「豪華朗機工」

> 5 部影片
> - 台灣吧影片（使用）
> - 圖文不符形象短片（貢獻）
> - 編輯的影片
> - 提案的影片
> - (This video)
>
> 時長：無限制
> 操作網站、chatbot、analytics 的影片
> 1. chatbot 送訊息回傳回應
> 2. chatbot 送新訊息，網站回應，chatbot 收到推播
> 3. analytics 與 downstream bots (?)

- 創意面：
    - 公民科技運用在事實查核上，作為公共議題討論的基礎
    - 設計細節（含有個人意見 etc）
- 影響面：
    - 大家都能查核的 social movement
    - 使用量與使用人數
    - 開放資料效益
    - 外國效仿


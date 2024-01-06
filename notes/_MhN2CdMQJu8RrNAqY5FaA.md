---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220623 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz, nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :eye: Under review

- [ListArticle articleReplies filter](https://github.com/cofacts/rumors-api/pull/283)
- [ListArticleReplyFeedback for author](https://github.com/cofacts/rumors-api/pull/285)

## Media support
> https://github.com/orgs/cofacts/projects/9

目前 staging 的圖：打算刪掉
- 用 production 備份蓋掉 staging 上的內容
- 重新傳開發用圖
- 可以在 media manager 支援縮圖之後再做

`@cofacts/media-manager` package
- All PRs merged
- Bumped to 0.1.0
- Deployed via Github action https://www.npmjs.com/package/@cofacts/media-manager
  - Needs to adjust 2fa setting to work - https://github.com/semantic-release/npm/issues/209#issuecomment-712366750

Chatbot image proxy
- https://github.com/cofacts/rumors-line-bot/pull/311
- CI 不知道為什麼抱怨 package.json 跟 lockfile 不符
  - 不知道抓到什麼 node 版本 [name=nonumpa]
  - master 的 build 不知道怎麼過的 [name=mrorz]

## Trend and Contribution
> https://github.com/orgs/cofacts/projects/10

- https://github.com/cofacts/rumors-api/pull/285
  - list article reply feedback by `replyUserId`, `articleReplyUserId` or `authorId` (= `replyUserId` OR `articleReplyUserId`)
  - Migration 時發現 chatbot bug https://github.com/cofacts/rumors-line-bot/issues/310

## Chatbot feedback bug

> https://github.com/cofacts/rumors-line-bot/issues/310

修理：
- feedback LIFF 改從 URL 讀 `articleId`, `replyId`
  - TBA: 看看裡面還要啥資料
  - 取代 context
- 直打 API 取代 sendMessage
  - 取消 `ASKING_ARTICLE_REPLY_FEEDBACK` state
  - 把 share bubble 往前搬
  ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6735b81c16a2ea504b4ef3c19ae40472.png =x500)


> [name=mrorz]
> 我在自己機器試跑 https://github.com/cofacts/rumors-api/pull/285 的 migration script 時，發現百餘份 feedback 的 articleId 跟 replyid 根本對不起來。追蹤了一下才發現，是因為 chatbot context 錯亂導致的。只要使用者往回捲，按了前一個回應的是否有用，那個 feedback 就會被送到最下面的 reply 上。
> 這個有點嚴重，不知道多少個 feedback 是因為這樣給錯的，我想要立即處理 QQ
>
> 我在想會不會有些莫名其妙的 feedback 就是這樣來，因為使用者可能會有這樣的流程：
> - 查了一則訊息，cofacts chatbot 吐出數則類似訊息待選
> - 選了一則訊息，chatbot 給了一個回應，使用者不滿意
> - 使用者捲回去選另一則訊息，chatbot 給了另一個回應，使用者覺得有用，所以給了好評
> -使用者想要捲回去給前面看到的回應負評，但此時因為此 bug 的原因，這個負評會給到下面的回應，還會把原本的好評取消掉
> 或這個流程：
> - 查了一則訊息，cofacts chatbot 吐出數個回應待選
> - 選了一個回應，使用者不滿意
> - 使用者捲回去選另一則回應，使用者覺得有用，所以給了好評
> - 使用者想要捲回去給前面看到的回應負評，但此時因為此 bug 的原因，這個負評會給到下面的回應，還會把原本的好評取消掉
>
> 根據 2018 年的統計，「chatbot 使用者捲回去點前面的按鈕」這件事，每天大概會有兩百次
https://github.com/cofacts/rumors-line-bot/issues/49#issuecomment-439603502
> 當然這不代表說每次使用者點舊按鈕都是為了打分數啦，可能是回頭選 article 或回頭選 reply
> 但這也告訴我們，chatbot 使用者是很常會往回捲的，只要按鈕不會再對話紀錄中消失，就要非常注意其設計，最好每顆按鈕都不該 depend on context，或是該動作的所有參數都已經放在 action 上


:::success
MrOrz 本週末修掉
:::


## Moderation

### 腦控洗版
- 決議：至 FB group 發文討論 https://g0v.hackmd.io/Gf45qq-9T9GLMkSrsfXG1A#%EF%BC%A8%EF%BC%A3%EF%BC%B2-%E8%85%A6%E6%8E%A7
- 尚未貼文

### 政治立場不同者的檢舉 

- 決議：不修改資料庫 https://g0v.hackmd.io/Gf45qq-9T9GLMkSrsfXG1A#%E9%87%9D%E5%B0%8D-Lopi-%E7%9A%84%E6%AA%A2%E8%88%89
- 尚未撰寫 Cofacts WG 判斷

### 疫苗陰謀論遭檢舉

- 被檢舉人資訊 https://cofacts.github.io/community-builder/#/editorworks?showAll=1&day=365&userId=cyWkqn4BvUvLpBdgXhV_
- 不用封鎖
- 尚未撰寫 Cofacts WG 判斷

:::success
先不用貼去 FB 討論
:::

## 大松檢討

- 沒有人 QAQ
- 自己帶網路很棒
    - 有用 netgear 沒用到 router
    - 升級會議中心松江 101 館會議室有對外窗可接收到 4G 信號

## Google 停用帳號與文件

- 已經在 6/19 發現恢復使用
- 告知有[兒少性剝削相關內容](https://support.google.com/accounts/answer/40695?hl=zh-Hant#zippy=%2C%E5%85%92%E5%B0%91%E6%80%A7%E8%99%90%E5%BE%85%E8%88%87%E5%89%9D%E5%89%8A)
- 今年下半年 Google drive --> GCS 的時候，會再進行過濾

## Interviews & invitations

### Khazanah Research Institute
- 22:00 today
- governance (data quality)
    - classification decisions
    - consistency across editors
- amount of resources & how does it scale
    - num of developers
    - how much resources
- 其實是不是該弄個採訪共筆囧 [name=mrorz]
- OpenDream

### 關鍵大人物
- 已有訪談：https://becomingaces.com/article
- 改採共筆

:::success
等他共筆
看他有沒有要[拍照](https://becomingaces.com/article/219)
:::

### 成功登大人-新鮮人成長營

- 入學營隊
- 9/1(四) 14:00~17:30 攤位與論壇
- 6/28 前回覆

:::info
住宿？
再看看
:::

### ai4sg 共筆開放

:::success
最後有刊出 --> https://www.facebook.com/systextaiwan/photos/a.452231404863295/4132260923526973/
問 CC
:::


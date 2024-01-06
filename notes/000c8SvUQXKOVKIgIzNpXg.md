---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20221012 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: rumors-line-bot

https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20220930
- Fix thank message in LIFF
- Remove unnecessary env vars (@miles170 ++)
- Numerous doc fixes (@miles170 ++)

### :rocket: Staging

#### :electric_plug: API

- Remove `MEDIA_SUPPORT` https://github.com/cofacts/rumors-api/pull/292

#### :robot_face: rumors-line-bot

- Support video and audio https://github.com/cofacts/rumors-line-bot/pull/336

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 應可送出「全新訊息」
    - [x] 圖片
    - [x] 影片
    - [x] 聲音
- [x] 重送剛才的訊息，應該會顯示「已被收錄」的字樣
    - [x] 圖片
    - [x] 影片
    - [x] 聲音
- [x] 送出已經回過的訊息，可以自動顯示回應
    - [x] 圖片
    - [x] 影片
    - [x] 聲音
- [x] Rich menu 測試
    - [x] 「設定」更改後再次打開，應該會保留原本設定
    - [x] 「查過的訊息」可以顯示
        - [x] 圖片
        - [x] 影片
        - [x] 聲音
    - [x] 「教學」可以觸發教學流程

##### ⛔️ Release Blockers
##### 未竟項目

#### :globe_with_meridians: Site

- Support video and audio https://github.com/cofacts/rumors-site/pull/507
- Article type filter for Article list, Reply list and Profile page https://github.com/cofacts/rumors-site/pull/508
- Comment list in profile page https://github.com/cofacts/rumors-site/pull/509

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] Article list
  - [x] Filter works
  - [x] Sorting works
  - [x] Can go to article page
- [x] Replies list
  - [x] Filter works
    - [x] 不允許選擇 Replied by me
  - [x] Sorting works
  - [x] Can go to article page
  - [x] 不允許 upvote / downvote replies
  - [x] Can see vote reasons
- [x] Hoax for you
  - [x] Filter works
  - [x] Can go to article page
- [x] Article detail
  - [x] Can see similar messages

登入自有帳號後檢測：
- [x] Replies list
  - [x] 可選擇 Replied by me
- [x] Article detail
  - [x] Can submit, upvote, downvote reply request
  - [x] Can submit, remove own reply
  - [x] Image, video, audio
- [x] Can go to profile page on menu
    - [x] Can edit own name, bio, URL
    - [x] Can see own replies
- [x] Can logout

##### ⛔️ Release Blockers

##### 未竟項目


### :eye: Under review

## Multimedia support

宣傳文案
- TA: Facebook 粉專
- 支援圖片搜尋、查核
- （小字：收集影片謠言與語音謠言中）

## 搭配圖文 design doc (article group)
https://g0v.hackmd.io/f_Ze19PhQuqx_fzOAOkohQ

另一個想法：不改 chatbot，網站實作類似舊版網站[「查看該用戶回報的所有文章」](https://old.cofacts.tw/articles?searchUserByArticleId=3tfnnm6rexabx&filter=all&replyRequestCount=1)功能
- 有暴露該 LINE 使用者送出歷程的疑慮
- 最多只能顯示第一次送出的搭配，不會顯示其他使用者的搭配

## g0v 十週年系列活動

### 10/22 (六) 大松 @ 中研院
- bil 去演講無法出席
- mrorz 會出席提案
  - 義大利
- https://docs.google.com/presentation/d/1Bi1ulm_l6oMYPc6AidFAQ8fGNmKwuLuzmJPZBw8qsqE/edit#slide=id.g115e08f7c67_0_87
- 圖片訊息、影片訊息、影音訊息
- 幫圖片找回應？

### 10/23 (日) 生日趴 @ 社創中心
- standup: https://docs.google.com/presentation/d/1oM_DqQNw6kZ3GTayL8KM_p4SXWC19wQesY81v2SfVLM/edit#slide=id.gc4cef832ac_0_124
- 跳跳：bil
- Workshop：LINE 傳來的圖是真的假的？網傳圖片查核工作坊 [name=bil]
    - 15:00 ~ 15:40
    - 圖片查證技巧
    - 比鄰拿麥克風直接講
    - 看網站操作，不順就成為修正網站的參考
    - google lens / yandex
    - 分兩組下去巡

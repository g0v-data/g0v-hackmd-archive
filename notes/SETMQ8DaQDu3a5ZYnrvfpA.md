---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220112 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, nonumpa, mrorz, 柏寬
- 線上出席：cai
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
https://github.com/cofacts/rumors-api/releases/tag/release%2F20220107

- Hide blocked contents by default; add status filter to fields

#### :globe_with_meridians: Site
https://github.com/cofacts/rumors-site/releases/tag/release%2F20220107

- Update homepage snippet in Google search
- Show blocked content for spammers
- Fix reply detail page bug

#### Community builder

Fix editor works tables

## 小聚檢討

小松果：https://hackmd.io/Sjn7PSQDQEabSMYcm0XwBg

- 群組回文門檻太高？
    - https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2Ff0V7J5ceTS-1vnKh0RwILw
    - SIMILARITY_THRESHOLD: 0.75
    - 看一看 Events？
        - 有觸發查詢且查到 : UserInput/ArticleSearch/ArticleFound
        - 每一篇：`Article/Search/<articeId>`
        - 有 identical doc, valid category, valid article reply --> `Reply/Selected/<replyId>`
    - Job queue 掛掉ㄌ from 11/15 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2fb2614b045089d31a8bacb614323bed.png)
    :::success
    Johnson: Fix group chat (job queue 壞了？)
    看壞掉之前的 event 數
    :::
- 教學文章不容易被看過
- 告示牌要貼一張在電梯裡面

----

- TBA: NPO Hub 二樓是否可以借用（可以從旁邊上去）
- TBA: 3 月小聚時間
    - 3/12 or 3/19

:::success
bil: 協調時間、通知「[日曆](https://g0v.hackmd.io/BNHyH7ESSxSlu12BV2U9TQ#%E7%94%B3%E8%AB%8B%E6%96%B9%E5%BC%8F)」是壞的
:::

## TODO 排序

- [PRIORITIZED: Johnson] 測試現有圖片與 hash 的效果
    - Hash: https://g0v.hackmd.io/aJqHn8f5QGuBDLSMH_EinA
    - 看哪些會有相同的 hash、圖片有多不同就會算成另一個 hash、hash 之間的距離與圖片的相似度
- 檢舉按鈕 & 表單: [M5](https://g0v.hackmd.io/hk1v8Ka5TCmIZinQ6zKU9Q)
- 把 yegogo 整合到新 blocked 機制：[M4](https://g0v.hackmd.io/hk1v8Ka5TCmIZinQ6zKU9Q)
- 列出所有 spammer & spam content
- 編輯教學 https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2F-G9Md9IyQauRoalIXJgenQ
- 繼續 LIFF
    - https://g0v.hackmd.io/E1-ajzinSwCyacGG228VsQ#Article-LIFF
- 分配 App ID
    - https://g0v.hackmd.io/51wwLHgvSUqtBDaP-yAVnA
    - https://github.com/cofacts/rumors-api/pull/270
- Multimedia support phase 0 - https://g0v.hackmd.io/aJqHn8f5QGuBDLSMH_EinA
- article detail 的「Line 詢問」加入 LIFF open count

## 提醒使用者刪除個資？

- line 使用者傳謠言的時候要跳視窗提醒記得把個資刪掉嗎？ (最近詐騙有感 [name=cai]
    - https://cofacts.tw/article/347wu0eoxuuf
    - https://cofacts.tw/article/vpxaz0makyh5
    - https://cofacts.tw/article/1xqptuqyfwhzv
    - https://cofacts.tw/article/2zr9skucanz9y
    - https://cofacts.tw/article/3l2v78yjbhmdf
- 有點難 [name=nonumpa]
- wording 上已經有提醒使用者「是否要送出到公開資料庫」了，或許他們不在意 [name=bil]
- 如果他們事後反悔，還是可以聯絡 cofacts WG 拿掉 [name=mrorz]
    - 而且要當事人提出 [name=bil]

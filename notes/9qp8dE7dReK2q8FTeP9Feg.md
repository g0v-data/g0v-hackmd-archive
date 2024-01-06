---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20200722 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：MrOrz, bil, 文武, GGM, Gore, 志超
:::

## Cofacts Next! 追蹤

- [收尾]  Chatbot notification
    - GA
        - Owner: MrOrz
        - PR ready for review：https://github.com/cofacts/rumors-line-bot/pull/206
        - TODO: 補 env var README 後 merge
    - Notification
        - owner: 文武
        - PR: approved, not rebased yet https://github.com/cofacts/rumors-line-bot/pull/207
            - TODO: listed in [20200715](https://g0v.hackmd.io/OC7BneJ3TEGJHge1hWV-0w)
        - ETA: 7/22
    - New `userArticleLink`
        - owner: GGM
        - Code all merged :tada: 
        - TODO
          - MongoDB backup mechanism
- Article analytics from GA
    - Owner: Zoe
    - Tracking board: https://github.com/orgs/cofacts/projects/7
    - 加了 Exclude URL Query Parameter ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_82097cf7004fae4724c2c9232c5e4a0a.png)
        - URL param 統計：https://docs.google.com/spreadsheets/d/1_KjmSLc1uwKDZPV_wG7tynN_alR_9r-GhqPbq1ViJ5k/edit#gid=1298620982
    - 加了 Content grouping ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c7482792e9952cb58f881fd9e2af0fa5.png)
    - ETA Plan: 8/10 for API, 9/7 for UI

- `ArticlePageLayout` refactor
    - Owner: MrOrz
    - Spec: https://g0v.hackmd.io/h8rP0TOGTh2Clxi_Oi_QKw
    - Plan
      - 2nd PR:
        - 主 PR: https://github.com/cofacts/rumors-site/pull/288 ~~希望 7/20 ready~~ 大松前？QQ
      - 3rd PR: 大松後 QQ

- User ID refactor
    - Owner: MrOrz
    - Spec: https://g0v.hackmd.io/ZcoUOX_-RQSkJyl5xz4_Zg?view#%E6%96%B9%E5%90%91-2-%E9%87%9D%E5%B0%8D%E6%AF%8F%E5%80%8B-backend-user-%E9%83%BD%E7%94%A2%E7%94%9F%E4%B8%80%E5%80%8B-user-document
    - Plan: GG

- 教學頁 spec
    - owner: Lucien
    - ETA：下週

## 大松籌備

### Category

[Cofacts 標籤定義](https://g0v.hackmd.io/D4KfdMRWS-OmCKd-Fhli2Q)

0708 提案：`COVID-19 疫情`、`國際關係`

### 分工

ggm, mrorz, bil

bil 主持人要松前哈拉、主持早上開幕、下午短講、晚上結束

首頁：
https://beta.hackfoldr.org/1yXwRJwFNFHNJibKENnLCAV5xB8jnUvEwY_oUq-KcETU

category:
- 分文章
- 選擇 category 然後針對內文評分
- 重點：收 feedback
    - UI / UX 方面
    - 分的類
    - 分類的說明

ggm
新增一個分類的話有兩個狀態

1. 全新大項目（之前沒出現過 ex: 國際關係）
2. 依附在大項目下的（泛指醫療 --> COVID-19）

會影響 training

ex: COVID-19 train 的時候可以針對子 category train
例如政治的就不會拿來 train，針對醫療類做 training
model 會比較準

如果是大項目，就是整個 data set 的重 train

所以 category 已新增為主

ex: 新增「愛滋病」之後（空），隱藏舊的「性少數與愛滋病」
從「性少數與愛滋病」分配 -> 重標去「愛滋病」與、重 train

:::success
工具：spreadsheet 分配 URL[](https://)
:::

## New issues

### mLab migration

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c7f0a266b30a7114e1d43aad08b8679d.png)

> mLab free sandbox  --> MongoDB Atlas M0 free quota 的搬家指南
> https://docs.mlab.com/how-to-migrate-sandbox-heroku-addons-to-atlas/

- cloud.mongodb.com
- 一樣有 mongo URI
- 可以 `mongorestore` & `mongodump`
- staging & production 開 project invite Cofacts developers

:::success
MrOrz: 8/26 開 mongo db
:::

### Misuse of "comment"
> 補充功能被用來回應回應 ._.
> https://cofacts.g0v.tw/article/1d0lu8giqz323
> [name=MrOrz]

bil
之前有人
他知道放在上面不會變成回應
但他只想提供資訊
讓編輯來完成回應

都是很好的用法

:::warning
先放著
:::


### Emoji for reference?

> Emoji 選單很棒 <3
> https://cofacts.org/article/3i3l9grtm802g
> 不過我連出處都想用 emoji，我現在是在回應視窗點出 emoji 之後在複製貼上下去 ._.
>
> [name=MrOrz]

bil
會在內容做 emoji
但出處不會想放

:::warning
先放著
:::

## :potable_water: Release pipeline

### :star: Released to production

https://github.com/cofacts/rumors-site/releases/tag/release%2F20200716


### :rocket: Staging

本週暫停一次

- Website: 沒有顯著外觀與功能上的差異
- Chatbot:
    - LIFF 設定修好了，之前少了 LINE login channel ID
        > 之前改 verifyIDToken 忘記補在 README 上了[name=nonumpa]
        > 我在 [analytics PR](https://github.com/cofacts/rumors-line-bot/pull/206/files#diff-b2041cec6cc741dec054652f4570ced0) 有在 `.env.sample` 補註解。不過 README 也應該提沒錯～ [name=mrorz]
    - 有 userArticleLink 很棒！
    - 但需要 migrate away from mLab⋯⋯

### :eye: Under review

## 8月編輯小聚？

- 日期 & 主題
- 場地：NPO Hub?

bil
下次黑客松：10/24
8/15 萌典松
9 月 google 開查核工作坊

npo hub

8/29, 8/30 選一天下午


## 回應小技巧整理

我自己在寫 Cofacts 回應的時候，有掌握到一些讓回應比較好讀好入口的小技巧，整理在這裡（草稿）：
https://hackmd.io/@cofacts/S1XQu2c1D
大家可以把看到覺得寫得很好的 Cofacts 回應提供給我唷，這份文件的每一個 tip 都需要案例 QQ
也說不定可以從案例中歸納出新的技巧。
目前 hackfoldr 裡面，針對編輯的有 [UI 操作說明](https://beta.hackfoldr.org/1yXwRJwFNFHNJibKENnLCAV5xB8jnUvEwY_oUq-KcETU/https%253A%252F%252Fhackmd.io%252Fs%252FSyKNjDUCe)，或者是涵蓋比較全面（從分析到撰寫）的[奇幻旅程](https://hackmd.io/@mrorz/B1ul5U86-/%2Fs%2FSJyNsLIpb?type=book)。此份文件聚焦在寫作技巧，希望讓編輯有不同的靈感

文武
從最多讚的回應來歸納
也比較有代表性

:::info
- Continue? OK
- Examples? 從統計資訊出發
:::


## 互動式成果報告

> 目標 11 月上線

- 定位：非營利組織的年度報告 / 工作報告
    - 初次接觸 Cofacts
    - 今年做了什麼事情（每年）
- 讀者
    - 不想加入 Cofacts 成為使用者，但可能想資助 (?)
    - 對 Cofacts 好奇
    - like-minded partner (國際間有興趣複製 Cofacts 到自己國家的人)
- 散佈媒介：FB fan page, email, etc
- 內容
    - 20? x 查核的訊息 - Impact 面
        - 國內版可以放國內訊息
        - 英文版可能放跨國相關資料
        - 有 analytics 可以用於 storytelling
            - 在傳的時候當時的新聞
    - Cofacts' contribution - 運作面，上述 impact 是怎麼做的
        - Editor's contribution
        - Developer's contribution
        - 線下活動紀錄
        - 2020 新功能:
            - gamification
            - tools
            - AI label

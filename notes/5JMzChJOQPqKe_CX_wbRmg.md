---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20200909 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：orz, bil, nonumpa
:::

## Cofacts Next! 追蹤

- [收尾] Chatbot notification
    - Migration: Going to unblock
        - 已確認 `userArticleLink` 有正常生成
        - 已進行 `UserSettings` migration
            - 85180 document(s) restored successfully. 657 document(s) failed to restore.
        - 需推播介紹「訊息列表」與「設定」功能
        - （再下週）啟動 Cronjob
    - MongoDB backup mechanism
        - owner: GGM
        - progress?
- Article analytics from GA
    - 本週 release
- `ArticlePageLayout` refactor
    - 2nd PR
        - https://github.com/cofacts/rumors-site/pull/288 ready to review
        - 還有 header 等重用的 UI 沒有處理
    - 3rd PR Remove ArticlePageLayout 下週有機會  (?)
- User ID refactor
    - Owner: Zoe
    - https://github.com/cofacts/rumors-db/pull/47
- 教學頁設計
    - owner: 志超
    - https://g0v.hackmd.io/sB_zayWjTo-W0R7xe_U34w

## Rich menu deploy

2020/9/7 Rich menu 上 production、[設計檔案公開](https://drive.google.com/drive/folders/16oqUdnAMqaMFQtcauoJFqpN97VjIxIrP)

有兩個版本：
1. 主選單（一般）
2. 主選單（小聚報名中）

### 連結

- 教學：`https://hackmd.io/@mrorz/Bk06LhrxG?type=view&utm_source=rumors-line-bot&utm_medium=richmenu`
- 小聚資訊：
    - 一般：`https://cofacts.kktix.cc?utm_source=rumors-line-bot&utm_medium=richmenu`
    - 小聚報名中：`https://cofacts.kktix.cc/該次小聚path?utm_source=rumors-line-bot&utm_medium=richmenu` 
- 官網：`https://cofacts.g0v.tw?utm_source=rumors-line-bot&utm_medium=richmenu`
- 推薦 Cofacts 給朋友：`https://line.me/R/nv/recommendOA/@cofacts`
- 設定推播功能：`https://liff.line.me/1563196602-R1zEXaDB/liff/index.html?p=setting&v=20200812&utm_source=rumors-line-bot&utm_medium=richmenu`
    - `v` 參數是用來 cache bust 用的，因為 LINE 開過一次 LIFF URL 之後會把頁面 cache 起來，下次開啟不會重抓
- 問過的問題：`https://liff.line.me/1563196602-R1zEXaDB/liff/index.html?p=articles&v=20200812&utm_source=rumors-line-bot&utm_medium=richmenu`
    - `v` 參數同上

### 追蹤

使用 [google analytics utm](https://support.google.com/analytics/answer/1033863?hl=zh-Hant) 追蹤點擊。

- `utm_source`: `rumors-line-bot`
- `utm_medium`: `richmenu`

各個按鈕的 traffic 會送進下面 GA properties：

- 教學：Official hackfoldr
- 小聚資訊：Cofacts kktix (本次新開設，在 kktix 上已設定)
- 官網：cofacts
- 設定推播功能：production line bot
- 問過的問題：production line bot
    - 點擊選項時會觸發 GA event (category: `LIFF`, action: `ChooseArticle`, label: 被選的 article id)

### 推廣使用

Schedule: TBD

:::warning
Bil 會做
:::

- Cofacts group & 粉專
    - 試水溫
- LINE 推播

## 編輯小聚
上週討論：https://g0v.hackmd.io/c5wpuEPaQLWwM_5vxuo_Yw?view#%E7%B7%A8%E8%BC%AF%E5%B0%8F%E8%81%9A

- [x] 主題：
    - 孔子媽媽待產日
    :::success
    by nick this sunday
    :::
- [x] 時間：9/27 (日) 14:00-17:00 Ronny keyholder(借13:30-17:30)
- [x] KKTIX:https://cofacts.kktix.cc/events/cofacteditor21
- [x] 準備貼紙
- 場地：青平台
    - [x] 場地單
    - [ ] 食物
        - 論語裡有什麼食物嗎 [name=mrorz]
        - 樓下的甜點 La Grotta 很好吃，會問一下是不是要提早訂 [name=bil]
    - [x] 延長線 (場地有)
    - [ ] wifi
        - [ ] Nighthawk M1 + 4G sim
        - [ ] ASUS RT-N12 Wireless N300 (2x 5dbi高增益天線)
- [ ] 誰會來呢？
    - mrorz, bil, ~~lucien~~, nonumpa, zoe (maybe)
- [ ] 誰不會來
- [ ] LINE 文案
呀哈！！！9月27日星期天下午2點到5點，Cofacts 真的假的要在教師節前一天教你使用查假訊息的事實查核工具(⁎⁍̴̛ᴗ⁍̴̛⁎)，新聞自己查、柯南自己當！當然也歡迎一起來回應新的謠言。本年度僅此一次查核工具工作坊，免費教學，附贈點心。(座位有限，請先報名唷！記得帶電腦來喔💻)
https://cofacts.kktix.cc/events/cofacteditor21

## New open data

https://github.com/cofacts/opendata
- `/data/*.zip` 換成放在 git LFS
- 增加 [analytics.csv](https://github.com/cofacts/opendata)
- announced in Slack; should we do it in Facebook group as well?

:::success
orz 貼 facebook group
:::

## RSS 訂閱教學影片

- 腳本： [Cofacts RSS 訂閱腳本](/TfCHhvtFTLmP0YKmaU1yVA)
- [影片用 Keynote](https://www.icloud.com/keynote/0uSJhzhXm6ti2ua9frzQuqubw#Cofacts_subscribe_tutorial) 

:::success
nick有意願接
給nick看 youtube https://youtu.be/9tu-K1P2_-Q
:::

## Versioning rumors-db schema

- 原本參考一般資料庫，整體有一個 version https://github.com/cofacts/rumors-db#index-mapping-versions
- 考量到 reindex 花時間、每次也可能只會改少數 index，我們應該每個 index 分開 versio
    - export `VERSION` const in each schema
    - reindex command script / function (用來在 migration script 呼叫) for one schema
- README 記載
    - schema version 資訊
        - When to bump version
            - 一定要 reindex 的情形，例如修改現有欄位 analyzer
            - 不用 reindex 的情形，例如新增欄位、新增 index
        - 如何 bump version
    - 規定如何撰寫 migration

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
https://github.com/cofacts/rumors-api/compare/a9a68b9d1d5a3b75a32b021c8b799dd58c1fb01c...869bfcb4f24791793781f9a89d546d830e614fad

- #216 `WEB_CONCURRENCY` env vars
- #213 highlight field for search result

### :rocket: Staging

https://github.com/cofacts/rumors-site/compare/master...dev

##### Features
- #315 Line chart in article detail page

##### Bugfixes
- #211 Takes 2 back button to get out of article detail page

##### Testing checklist

http://dev.cofacts.org/

**未登入**下檢測：

- [x] Article list
  - [x] Can go to article page
  - [x] Press `back` exactly once can go back to article list

- [x] Article detail
  - [x] Can see similar messages ( https://dev.cofacts.org/article/1fi7dla9wtwjn )
  - [x] Cannot submit, upvote, downvote reply request
  - [x] Cannot submit, upvote, downvote reply
  - [x] Cannot add, remove, upvote, downvote category

登入自有帳號後檢測：

- [x] Article detail
  - [x] Can submit, upvote, downvote reply request
  - [x] Can submit, remove own reply
  - [x] Can upvote, downvote other's article reply
  - [x] Can add, remove, upvote, downvote category

##### ⛔️ Release Blockers

##### 未竟項目

- Pixel 2, Pixel 3a 點 hoax for you 好像會 crash
    - 桌面版沒事
    - iOS safari、Andorid Firefox 沒事
    - 但 production 正常
    - 可以在 localhost 重現，疑似是超長內容導致的問題
    - production 沒問題，很可能只是沒有一樣的內容
        - 發現只要列表頁面有 http://dev.cofacts.org/article/1qdrhpprhoozr 就會 crash，無論是 /hoax-for-you 、/articles、甚至是 detail 頁面都會 crash
    - chrome inspect 會在沒有 error 的狀況下直接斷線，看不出 error 在哪裏
    - 20200731 版也可以重現，所以是老問題，並非此 release 導致
    - 很可能是 Chrome for Android 的 bug⋯⋯

### :eye: Under review

- [cofacts/rumors-site#319 Reasons dialog](https://github.com/cofacts/rumors-site/pull/319)
- [cofacts/rumors-site#288 Remove `ArticleItem`](https://github.com/cofacts/rumors-site/pull/288)
- [cofacts/rumors-line-bot#218 Highlight](https://github.com/cofacts/rumors-line-bot/pull/218)

## 貼圖

出常用的
- 早安
- 晚安
- 謝謝
- 對不起

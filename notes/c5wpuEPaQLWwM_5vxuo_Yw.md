---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20200902 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, nonumpa, lucien, 志超
:::

## Cofacts Next! 追蹤

- [收尾] Chatbot notification
    - Migration: Going to unblock
        - 今天放 rich menu
        - 本週進行 `UserSettings` migration、確認 userArticleLink 有正常生成
        - 推播介紹「訊息列表」
        - （下週）啟動 Cronjob
    - MongoDB backup mechanism
        - owner: GGM
        - progress?
- Article analytics from GA
    - UI: https://github.com/cofacts/rumors-site/pull/315
- `ArticlePageLayout` refactor
    - Blocked by 0831 release
    - `ArticleReplyFeedbackControl`: 50% complete
    - 2nd PR https://github.com/cofacts/rumors-site/pull/288 not ready yet
    - 3rd PR Remove ArticlePageLayout 遙遙無期 orz
- User ID refactor
    - Owner: Zoe
    - 1 個月 workload
- 教學頁設計
    - owner: 志超
    - https://g0v.hackmd.io/sB_zayWjTo-W0R7xe_U34w

## 討論事項

### RSS 訂閱教學影片

已經加上 LINE 設定的部分，需要重錄聲音
https://youtu.be/9tu-K1P2_-Q

- 腳本：見 [20200826 會議記錄](/PQf7jdWBTSiw376UMm-2Xg)
- [影片用 Keynote](https://www.icloud.com/keynote/0uSJhzhXm6ti2ua9frzQuqubw#Cofacts_subscribe_tutorial) 

RSS tracking:
每個 service 實作不太一樣
feedly subscribe 的時候會送 subscriber 數量
固定時間 fetch 的時候就不會再送 follower

feedrabbit 跟 feedly 不太一樣
user subscribe 的時候不會送 follower 但每次 fetch 的時候會回傳

IFTTT 直接從 applet 看有幾個人
feedly 也有 API

:::success
還是先把每個往`api/articles/[feed]` 的 request 資訊送進 GA event
之後再看怎麼 aggregate 資訊
:::

### Deploy rich menu

結案～

缺原始檔、CC0 宣告
最後放進 Cofacts google drive 的一個 folder

## 編輯小聚
上週討論：https://g0v.hackmd.io/DjY6dVLxQFG6moNlM98_OQ?both#%E7%B7%A8%E8%BC%AF%E5%B0%8F%E8%81%9A

- [x] 主題：
    - 孔子媽媽待產日
    :::success
    放課本孔子圖
    「明天我生日ㄛ」
    :::
- [x] 時間：9/27 (日) 14:00-17:00 Ronny keyholder(借13:30-17:30)
- [x] KKTIX:https://cofacts.kktix.cc/events/cofacteditor21
- [x] 準備貼紙
- 場地：青平台
    - [x] 場地單
    - [ ] 食物
    - [ ] 延長線 (揪松有 3~4 條，但可以再帶)
        - [ ] MrOrz 一條
    - [ ] wifi
        - [ ] Nighthawk M1 + 4G sim
        - [ ] ASUS RT-N12 Wireless N300 (2x 5dbi高增益天線)
- [ ] 誰會來呢？
    - mrorz, bil, lucien, nonumpa, zoe (maybe)
- [ ] 誰不會來
- [ ] LINE 文案

## :potable_water: Release pipeline

### :star: Released to production

0831 release: rolled back to https://github.com/cofacts/rumors-site/tree/article-stats-feature-branch

Mitigation: https://g0v.hackmd.io/qinBlfq0QQG1U_rWOpGAWQ

:::success
目前 root cause 不明，不知道是 apollo-client 3 還是 next-apollo 的問題。
暫時先 rollback 回 apollo client 2⋯⋯
:::

Lucien: 我們暫時升到 3.1 但沒用到 SSR
覺得 3 很多雷，還在修但已經上正式版號了
建議 Cofacts rollback 到 2

### :rocket: Staging

無，都在處理 Release 0831 QQ
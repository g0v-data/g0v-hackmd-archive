---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240221 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO Hub 出席：bil, nonumpa, orz, pierre
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: rumors-line-bot

https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20240216


## 小聚檢討

> https://g0v.hackmd.io/wJwWw-ztS4-8E65X_n1l7g

- 投影片忘記放新功能：搭配訊息

### 歷次小聚數據

https://docs.google.com/spreadsheets/d/1XjEQZ9esNKfkGd8XYd1p3E8DTgB0f5QPDl5ghf-JxE0/edit#gid=0

- 報名:推播 = 1~3:10000
- TBA: 計算貢獻留存
    - 有沒有建立實際關係（如 FB 好友）有差，有加的比較會長期貢獻 [name=bil]
- Funnel widening:
    1. 認知到假訊息問題
        - DTL、IORG、假清、黑熊也在做
    2. 使用 Cofacts LINE bot
        - 目前沒人其他人幫忙
        - 媒體露出
        - 打廣告？
        - 把 google 上查訊息的人變成 LINE 使用者
    3. 參與培訓
        - 推播
        - 野生查核工作坊？
    4. 產生貢獻
        - 每週感謝++
        - 進 Slack / discord / FB group 後持續有東西討論
        - 後續活動？
          - 再發訊息給來過的人 [name=bil]
          - 每半年到一年發訊息給曾經來過的人，請他們再來一次，可以不用聽，來喝飲料做志工

:::success
先放進 CCPRIP https://g0v.hackmd.io/@cofacts/rd/https%3A%2F%2Fg0v.hackmd.io%2FBRsJOevWSbyUMBSZEVVWrA
OP Layer
:::


## CCPRIP

### Follow-ups Article group
數據

```sql
SELECT * FROM `industrious-eye-145611.line_bot.events` WHERE STARTS_WITH(text, 'Batch: ')  AND createdAt > "2024-02-15 20:19:13.868000 UTC" LIMIT 1000
```

2024-02-15 20:19:13.868000 UTC ~ now:
Batched messages - 340 包含 iscooccurrence 事件

```sql
SELECT evt.* FROM `<table name>`, UNNEST(events) AS evt WHERE evt.action = "IsCooccurrence" LIMIT 1000
```
2024-02-15 20:19:13.868000 UTC ~2024/2/21 共 131 次
No: 15 次，其餘 Yes

- 使用者們傳送 batch 共 209 次 (=340-131），顯示是否為 batch 的 Yes/no 選項
- 55% 使用者選 Yes, 7% 選 No，其餘不回應
- 有少數是一次傳 10+ in batch


## CCPRIP

### [Op] Transcript spam
> nonumpa
> https://g0v.hackmd.io/vKCvrqSQTlm7GEx9MAXGaw?view#op-Transcript-spam-處理


### [Comm] article group 收尾
> nonumpa

### [infra][op] API key

community-builder 改 server-side render
- https://github.com/cofacts/dashboard
- Deploy to: https://dash.cofacts.tw

TODO
- [x] prettier + CI workflow
- [x] shadcn
- [ ] stats
- [ ] editor works

### [Op] FB 申請與 Google 非營利
> MrOrz

- 本週無進度
- 會址更新狀態：Not yet [name=bil]

## 會議時間
- 週三好忙 [name=mrorz]
- 週一如何 [name=bil]
  - OK X 3
  - 2/29 保持開會
  - 3/4 (一) 開始改成週一

## 2024/2/17 Downtime


- 17:30 cofacts.tw, api.cofacts.tw, line-bot.cofacts.tw HTTP timeout
- 17:50 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_48e434c47614da7fe26a08ae256f87e8.png)
  - https://askubuntu.com/questions/259739/kswapd0-is-taking-a-lot-of-cpu
  - Swap full, kswapd0 busy
  - All process not responsive
- 18:00 `echo 1 > /proc/sys/vm/drop_caches`, issue resolved
  - Source: https://serverfault.com/a/696185
- Future:
  - Website revamp nextjs 14 --> memory & CPU 應該要下降
  - ES 6 --> 8, host 在外面（100USD?/mo）
  - ES 升級可以外包


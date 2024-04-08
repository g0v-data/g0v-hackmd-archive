---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240408 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: rumors-line-bot

- https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20240406

### :rocket: Staging

#### :globe_with_meridians: Site

https://github.com/cofacts/rumors-site/pull/567

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [ ] Links to MyGoPen and votes work

### :eye: Under review

## CCPRIP
### [Op] Transcript spam
> nonumpa
> https://g0v.hackmd.io/vKCvrqSQTlm7GEx9MAXGaw?view#op-Transcript-spam-處理
> 

Deploy process
> Scripts: https://github.com/cofacts/collab-server/pull/7
- [x] rumors-db schema update
- [ ] rumors-api populate new contributors
- [ ] migration script

## 謠言惑眾獎

> Previous plan https://g0v.hackmd.io/dBog_HZ2TBuXjRxuJNrV-Q#%E8%AC%A0%E8%A8%80%E6%83%91%E7%9C%BE%E7%8D%8E

- 前次收錄票數：2.7K
- 本次收錄票數：截至 4/8 14:35 為 1.4k (Cofacts 0.4k, MGP 1k)
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1a2e93fbaeb4b9d1891aa85652a4ed53.png)
- 週二推一波？
    - 回覆率 60% 計，希望多 1K 票 = 點擊數須為 1.7K
    - Cofacts 推播 CTR [計算](https://docs.google.com/spreadsheets/d/1XjEQZ9esNKfkGd8XYd1p3E8DTgB0f5QPDl5ghf-JxE0/edit#gid=0)： Click / Delivered ~= 1%
    - 故推播到 170K 人，可得 1.7K Click、1K 完成問卷
    - 170K 人
        - 雙北 + 台南 + 高雄
        - 全部去掉雙北、台南

### 已實施
- 剪ㄇㄚ
- LINE bot 最後顯示 quick reply 連到活動頁面 (週六開始)
- 

## Issue discussion 

https://github.com/cofacts/rumors-site/issues/548

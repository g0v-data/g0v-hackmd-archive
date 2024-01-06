---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220817 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz
- 線上出席：nonumpa, 4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :eye: Under review

- [Chatbot image search](https://github.com/cofacts/rumors-line-bot/pull/316)
    - PR comments pending
    - maxHeight 只有 box 能用，現在是 hero->image，用 flex simulator 改成 hero->box->image，上下會多一個 padding [name=nonumpa]
    - 如果不用 hero 而直接在 body 或 header 放 box 呢？ [name=mrorz]
    - 100% match 邏輯會再改，改完就能 merge
- [Chatbot image submission](https://github.com/cofacts/rumors-line-bot/pull/318)
    - GA: 應該 label 找 image 就可以了，其他都跟純文字訊息一樣，還沒仔細檢查有沒有漏掉的 event
    - 需要 Review wording

## Image support
> https://github.com/orgs/cofacts/projects/9

### Processing existing image

- 流程：https://g0v.hackmd.io/uZ3gouRWRamtrCFzKFrgnw?both#Process-existing-images
- 有機會在 Google Colab 上執行，就不用 download

## 大松準備

- [x] check Good first issues
- [x] 出席：bil, mrorz
- [x] 講者：bil

## 在地青年培訓

- Train the trainer - 學員回去教人用 chatbot
    - 推廣者 [name=mrorz]
- 10 月
- 目標：宜蘭




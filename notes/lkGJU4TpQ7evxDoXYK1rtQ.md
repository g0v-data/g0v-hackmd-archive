---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220209 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：orz, bil, nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

[Cofacts user blocking mechanism](/hk1v8Ka5TCmIZinQ6zKU9Q) 已全數完成。
- https://github.com/cofacts/rumors-site/releases/tag/release%2F20220126
- https://github.com/cofacts/rumors-site/releases/tag/release%2F20220127

檢舉表單
- Spreadsheet: https://docs.google.com/spreadsheets/d/1q-iMJ9tZtoyHNfwInAb3z-eIg2x4-w1yp7XGTiaLB-w/edit
- Public link: https://docs.google.com/spreadsheets/d/e/2PACX-1vRdcwXdC36xfgXfSMSk527Zbel9A-__vwRXkQ0NjkzSXoSPETCFc7sI7SoaAFdPCfskugtQL-Md8JgH/pubhtml?gid=438362561&single=true
- Markdown 格式：https://github.com/cofacts/takedowns/blob/master/2022/0129-spammers-and-2nd-scammers.md

### :eye: Under review

- [Multimedia support phase 0](https://github.com/cofacts/rumors-api/pull/273)

## 圖片 hash 效果

:::info
Previous research: https://g0v.hackmd.io/bhL6csQ8T1e81E2De7ZS5Q#Search-with-similarity
針對「如何 search vector 間的距離」
本週探討 hash 作為 vector 本身的可行性，以及找尋適合用於 index images & dedup 的 hash 參數
:::

- UI visualization: https://github.com/MrOrz/cofacts-collected-image
- [Cofacts research on image-hash](/LHhF_VQ1RdS12C0k0ESQ_Q)
- Current parameter (bits=16) is good for dedup
    - TBA: analysis of bits=12 (144-bit) hash
- Similarity search
    - also use bits=16?
    - d<=10 --> Highly similar (95% similar)
- 如何找 d <= 10 的 hash? [name=nonumpa]
    - 我們的數量級 10K images，直接掃 [name=mrorz]
        - 256 bit hash 每 4 bit 做 XOR 查表 --> 64 次 XOR 與加法可完成一個 hamming distance 計算
        - 改成 Uint16Array 每 16 bit 做 XOR 查表 --> 16 次 XOR 與加法（但 dist lookup table 要 65536 個這麼大）
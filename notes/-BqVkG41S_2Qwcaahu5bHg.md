---
title: "[NCKU/Embedded] Week#3"
tags: hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/19DsoqSfyel)


> 遲到了QQ
> [name=孟勳 楊]


## 面試分享


### 計算機組織重點

- MMU
- TBL(uTLB)
    - set associate
- pipeline
- L1 L2 cache
- dma (跟cache的關係)
    - cache invalide

### OS

- interrupt/exception/trap
- reentrancy
- stack vs heap
    - stack frame
- deadlock/race condition
- mutex vs semaphore
- mutex vs spinlock

### 面試關鍵

就是因為你可能忘記，才面試你
- 經驗
    - 以自己實作經驗來回答題目
- 知識
讓對方覺得你可以成為一份子
- 誠實不騙
- 對工作內容了解＆有興趣
- 願意學習

### 暑假就要開始準備研替


## 課程


- fork
    - 產生parent、child
    - 結果有不確定性，必須確認parent或child誰先執行

- POSIX標準
[http://en.wikipedia.org/wiki/POSIX](http://en.wikipedia.org/wiki/POSIX)

- context switch
    - 當task轉換時，要保存前一個task的數值所需要的時間


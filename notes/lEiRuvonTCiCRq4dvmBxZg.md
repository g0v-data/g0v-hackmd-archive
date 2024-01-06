---
tags: cofacts, meeting note
---

20181031 會議記錄
====

> 前次會議記錄：https://g0v.hackmd.io/nRRlIkzMQYy5RPd-15T4vw
> 

## Dev

### Old bug identified

- introduced last year
- issue amd reproduction steps: https://github.com/cofacts/rumors-line-bot/issues/111
- PR: https://github.com/cofacts/rumors-line-bot/pull/113

需要知道為何當初要判斷 state change 才更新 `context.issuedAt`

:::success
已經把 PR deploy 至 staging，尚未測到有問題。

預計可以上線。
:::


### tagging
> 蝴蝶

### Bug: 覺得有用 / 沒用的分數最多只有 10
> MrOrz

issue: https://github.com/cofacts/rumors-api/issues/77

### 顯示覺得 article reply 沒用的理由；使用者在網站上按 Ｘ 時也詢問理由
> MrOrz

issue: https://github.com/cofacts/rumors-site/issues/97

## 讓 LINE 使用者可以回頭按按鈕，讀其他則文章或回應
issue: https://github.com/cofacts/rumors-line-bot/issues/49

> GGM

## 對外

### NTU interview
deadline: 本週末

https://docs.google.com/document/d/1tdysg3_bj291D1rS2fJAxZa5yuMT6jbqHzaYHZ2A8_k/edit?usp=sharing

### Invitation to Participate in a Research Study

11/19 這週希望與 MrOrz 碰面

:::success
會回信請他參與 11/21 在 workis 的會議
先給資料，說明我們不是研究單位，可能沒辦法提供太多客觀數據與 insight，但期待研究者研究這些資料。
:::



### 平權社會對話資料庫：你愛家我解惑

- 資料： https://g0v.hackmd.io/c/B1iHBvVPQ
- 作為[平權社會對話群組](https://www.facebook.com/groups/517938412059225/)的搜尋框，提高其產出的利用率
- 段落 <> 回應 資料庫
- Use case：
    - 提供網站服務，首頁有個搜尋框，可以貼上訊息文字、URL、圖片，然後得到針對其段落的回應
    - 可以送出新文章，增加待回應段落
    - 現有「段落列表」與「回應列表」
- 回應不標記正確 or 錯誤，僅提供反面 or 不同想法
- TA: 拿到愛家宣傳文章、傳單、圖片，心生疑惑，想看針對此文宣的不同意見的人 


#### Code
- API - https://github.com/answerfamily/answerfamily-api
- Site - TBA

#### Content based image matching:

- https://hub.docker.com/r/linekin/delf_service/
- https://github.com/linekin/delf_service/

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_50735b7bd2a7aefc95a0ff82adf5bdd7)

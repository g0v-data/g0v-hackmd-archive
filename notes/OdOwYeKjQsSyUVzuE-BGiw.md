---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220330 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis: bil, mrorz, nonumpa
- 線上出席：4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## 4/9 大松準備

Prev discussion: https://g0v.hackmd.io/bTVlJ8yYRb2nfDmGz09Psg#49-%E5%A4%A7%E6%9D%BE%E6%BA%96%E5%82%99

- 印刷品已拿到
    - 50 份帶去台南？
- 報名

## 送出流程改版開發

- `p=comment` 獨立頁面，使用 `ArticleRequestForm`
- 「用 article ID 讀取使用者回過的 reply request 填入」的功能可能要改 API 比較順
  - LIFF 拿得到 LINE 的使用者 token
  - 現況必須先打 Cofacts API GetUser 拿到自己的 ID (users index ID) 再拿那個 ID 去 `ListReplyRequest`
  - 考慮仿造 `ListReply` 在 `ListReplyRequest` 上加 `selfOnly`
  - 順便考慮：
    - 推廣到所有 ListOO APIs
    - `ids` filter 讓有一堆 OO ID 的人可以列出來 OO。這也可以讓 chatbot schema stitched API 可以[用 batch 方式](https://www.graphql-tools.com/docs/schema-stitching/stitch-type-merging#batching)有效抓取 article
    - `createCommonFilter()` 收納 `createdAt`, `appId`, `userId`, `selfOnly` 與 `ids` filter arg 定義
    - `attachCommonFilter(filterQueries, argsFilter)` 把 filter args 轉成 elasticsearch filter context commands 
  

## Multimedia 開發

- 4/9 前：[送出訊息改版](https://g0v.hackmd.io/bTVlJ8yYRb2nfDmGz09Psg#%E9%80%81%E5%87%BA%E6%B5%81%E7%A8%8B%E9%96%8B%E7%99%BC-breakdown)
- 4/28, 29: 現有圖片整理 - hash, 距離, 協作 article ID
    > 不過有個想法是，可以把我們搜集到的謠言圖片，跟 Cofacts article ID 做 mapping
    > 因為有些圖可能已經被人工 OCR 後送進 Cofacts 資料庫
    > 也有可能有些是文字配圖轉傳，此時就可能會很多種不同文字配同一張圖
    > 但這件事情我們這裡要先準備，把圖檔先 dedup 後，取出有被傳好幾次的，然後再來做人工標記




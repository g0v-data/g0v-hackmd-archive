---
tags: infras
---

# g0v 時間軸

## 簡介

- Site: https://timeline.g0v.tw/ 
  - 輸入你的關鍵字 https://timeline.g0v.tw/here-am-i 
- Code: https://github.com/Stimim/g0v-timeline
- Data: [g0v Timeline Spreadsheet](https://docs.google.com/spreadsheets/d/1UBWZTLHtjaleq5qAc03OGKMRGMknUmz9PnKob-iFIk4/edit#gid=1086308132)
  - 需要更多資料
  - 需要英文版資料

## 治理機制
- 在 g0v-slack 上開一個 public channel
    - Channel Name: `#g0v-timeline`
    - 使用者上去回報不適合的資料
    - 一般管理者可以投票 (++)
    - 主要管理者可以執行下架
        1. 可以用 https://timeline.g0v.tw/take-down-event/ 網站下架 (WIP)
        2. 可以用 gCloud Datastore 後台直接操作

## TODOs
- [P0] 把 take-down-event 修好
    - [x] 目前在主頁面上無法看到 event-id ，需要改主頁面
- [P1] 申請 g0v domain: `timeline.g0v.tw`
    - [x] Create an issue on https://github.com/g0v/domain/issues/
        - [example](https://github.com/g0v/domain/issues/60)
        - [created issue](https://github.com/g0v/domain/issues/65)
    - [x] 申請通過後上架到新的網址
    - [ ] 嵌入 g0v.tw
- [ ] [P2] 呈現英文版資料
- [ ] [P3] 用 React 會比較好嗎？
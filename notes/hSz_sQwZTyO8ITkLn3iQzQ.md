---
title: 2019/11/01 LINEBot 市容幫手｜3rd 小聚會（工程師）
tags: LINE, libot, 里長, 市容幫手
description: 用 LINE BOT 來幫助市民、里長與公務員。
---

2019/11/01
LINEBot 市容幫手｜3rd 小聚會（工程師）
===


#### 已完成
- [x] 接 Line API：JAQQ
- [x] server (heroku): JAQQ
- [x] 溝通使用者：班班（里長約到一名，10/19訪談；公務員未約）

#### 未完成

- [ ] UI (Maggie): Flex message、reach menu、card。
- [ ] 接 google sheet: Mars
- [ ] data science、structure: Foucault
- [ ] 多個檔案免費儲存問題: Mars、JAQQ


小聚當天討論的事項
---

### Google Sheet 欄位討論

[Google Sheet 連結](https://docs.google.com/spreadsheets/d/15Ul8nJUa8ifThZcg4VyifqauP9nL7xHlzi94we3DDZs/edit#gid=422969468)

為了因應使用者講到一半就跑走了，決定分成三種類型儲存。其中，每次對話都會對 database 做一次 request。

1. user
存使用者屬性，及處理過的 case 。另外還有當下在對話中的 case。

2. case
放經由程式篩選過的資料，並由 dialogIDList 收集所有的對話記錄。如果使用 Google Sheet，尚未解決多張圖片、影片、聲音的儲存問題。

3. dialog
記錄使用者和Line Bot的雙向對話，包含文字、貼圖、圖片，userId為0代表機器人


### 下次聚會時間：線上討論



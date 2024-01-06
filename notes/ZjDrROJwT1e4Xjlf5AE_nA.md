---
title: 2019/9/20 LINEBot 市容幫手｜1st 小聚
tags: LINE, libot, 里長, 市容幫手
description: 用 LINE BOT 來幫助市民、里長與公務員。
---

2019/9/20
LINEBot 市容幫手｜1st 小聚
===

哈囉，我們的第一次小聚將在 9/20 台北都蘭診所。
希望各位參加小聚前，能準備好以下事項，讓討論更順暢！:smile:

1. 看完這篇會前整理（也歡迎提出想增列討論的事項喔）。
2. 想一想我們計畫的正式名稱，最好可以**容易連結**、**知道是機器人**、**好記憶**。每人準備一個名字吧！
3. 先看看實際的[對話紀錄](https://www.notion.so/257345c7b6794342b34b58a777102ded)，討論起來會更有感覺。
4. 去[自我介紹區](https://www.notion.so/80a23bb3f9d640789a216c35791828cb?v=7c65208721ab4fb18ced6c02aaf69c00)，寫下你的專長，可以順利接到小任務。


以下是小聚當天要討論的事項
---

### LINEBot 市容幫手瞄準的目標
- 覺得 HELLO TAIPEI（1999）難用的族群，例如：年長者。
    - 是否不一定是里長？
    - 里長可能不想要寫自己是誰
    - Hello Taipei 是市政府的回報 app，需要先做身份認證和同意，數位版 1999
    - 不用的人可能會找里長講
- 覺得 LINE 群組洗版很崩潰的人，例如：公務員。

> :warning: **注意：** 兩個族群的目標不同，有可能互相排斥。
> 誰會比較難用？
> 


### 小聚議題

- [ ] 對話劇本：班班將流程圖寫在 notion 上面，麻煩 fly 提供 template角色扮演：模擬使用者與機器人對話過程。
    - 對話過程我已初步整理在 [miro](https://miro.com/welcomeonboard/qZ6bgkw2HsOdSdVgtD0jhAvCoFww1v8kuZgqsTfAk3fdLJJ83Rm2fZprVCo2uTkj)。
    - 可以回憶一下大家在大松構思的 [mindmap](https://miro.com/welcomeonboard/uQgWh6nPn3IJu0bJhuRbKmjhxHezJiJ2210sxS7jZb38ANe2rCwNoUiyFrUHCAAN) 流程。
- 分配任務：列出該有的需求，以及技術層面整理。
    - [ ] 溝通使用者：班班
    - [ ] 劇本：班班、ST。**之後要給 line API、UI**。
    - [ ] UI (Maggie): Flex message、reach menu、card。
    - Bot：
        - [ ]接 google sheet: Mars
        - [ ]接 Line API：JAQQ
        - [ ]server (heroku): Mars
        - [ ]data science、structure: Foucault
        - [ ]Line@ 帳號申請：班班
    - 建 Hackfoldr 跟分工： ael
- [ ] 下次小聚時間：
    - 10/18（五）晚上 7:00 線上，fly 給連結
    - https://meet.google.com/yto-tbqf-nmv
- [ ] 哪一種開源：開源方式和授權討論。
    - 程式碼：MIT
    - 資料：待決定（ael 去問資料授權）
- [ ] 取名字：幫我們的計畫取個可愛的名稱吧。
    - 以下開放提議 ( ´▽` )ﾉ ～～～
        - 英文名： libot
        - 中文：~~阿里伯、里丟伯、里都伯、里長伯~~、**派工讚（暫定）**、服務讚
        - 班班：修理伯、咻修叫
        - 
- [x] 遠端工作介面：HackMD、Notion、Slack、Hackfoldr......
    - 程式碼： GitHub
    - 專案管理用：Notion
    - 文件用：HackMD
    - 協作入口用：Hackfoldr
    - 溝通：Slack
    - 約吃飯：Facebook。有人談進度就請他去 Slack


### 2019/09/20 會議記錄

- Line bot 最小試用範圍(公務員)
    - (144人？) 全市/公燈處
    - 12人/區
    - 3人　燈、公園(可說服)、樹(可說服)

- Line bot 最小試用範圍(里長)
    - 53人
    - active 10人/區

- 避免爭議，最好是用 line@，由公務員做申請

先丟一個我覺得整理的很好的 g0v 專案協作入口：
https://beta.hackfoldr.org/cofacts

Mars：API 可以 tag 機器人。

小班：觸發機器人出來，讓里長填表單，之後公務員完成之後直接回群組，不透過 linebot。或是公務員貼上編號，觸發機器人（重點是主動回報要錢）。所有問題會匯集到 sheet 上面。



#### MVP

先從一個區的群組裡公園處的主要 3 個負責人
一個區群組裡的里長試用

（班班已經不在群組裡了）

1. 里長寫 bot 的名字作關鍵字觸發
2. Flex message 按鈕跳出
3. 點按可以進入與 linebot 一對一對話，歡迎訊息供里長點按選擇，加到 spreadsheet。可以加好友也可以不加好友，不影響能不能反映問題
4. 公務員用電腦看 spreadsheet 確認可以，（公務員開權限可以改 spreadsheet）
5. 公務員手動貼回應進 Line 群組

（下一階段：里長可以看到自己填的單子和處理進度）

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a55a5c5c56299a54d3ea67cc497f2c99)


#### 里長與 linebot 對話流程需要的功能：
1. card（小圖 ＋ 類別）or 浮起 reach menu。參考福岡市的 linebot
2. 選時間、GPS 定位
3. 上傳照片
4. 建立每個案件的編號
5. linebot 要記得：里長 ID、案件編號（primary key 或 ID）


寫 chatbot 對話劇本 Workflow 用 Notion，有 template 嗎？
（cofacts 是用什麼？）




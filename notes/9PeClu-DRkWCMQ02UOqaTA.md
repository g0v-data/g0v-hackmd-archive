---
title: CoTeach 教案共享平臺 1091024 會議紀錄
tags: edu, CoTeach
---

# CoTeach 教案共享平臺 1091024 會議紀錄
slack channel：[#edu-coteach](https://app.slack.com/client/T02G2SXKM/C01D21G7F0E)
[專案簡介](https://github.com/coteach/web/wiki)
[提案簡報](https://docs.google.com/presentation/d/1eQKuXvn96uC7v50fkLaEmdWHgsyIB9b9Ue81HXsaLDk)
:::info
時間：1091024 hackath41n

參與者：
**教育**：孟庭、Tumi（科大行銷系老師）、緯修（任職於安置機構）
**後端**：嘉豪
**前端**：震龍、Ken、Ivy
**其他**：Ada（工程師）、阿格（Stancode 助教）、品佳
:::

### 分工

 - 前端prototype設計: Ivy
 - aws cloud: 嘉豪
 - 訪綱: 震龍


### 其他討論
Tumi：
 - 假新聞教案缺乏、遠距上課工具學習及備課，老師各做各的

Ada：
 - narrow down 協作部分 format
 - narrow down TA，鎖定幾個主題（e.g. 媒體素養），擴增年齡層 or 鎖定年齡，廣收主題
 - 固定一個格式 template（搜尋引擎因授權問題無法達成）
 - 使用者不一定限縮於老師，可以是產官學提供知識，再由老師設計成教案 or 老師提需求，再由產官學提供知識
 
孟庭：
 - 現有合作：坪林採集人團隊
 - 尋求合作意願：NGO（均一 shareclass、螢光教育協會、放伴協會）...（求補充）

品佳:
 - 商轉可能性？擋書商財路？

### 前端設計
1. 每個plan開頭有個固定的info table，table欄位有下拉式選單可以選擇。例如: `年紀受眾`欄位中可以選擇`高中一年級`、`高中二年級`、`高中三年級`。
2. 使用者可以在每個可拖動的自訂div下面開issue

### 訪綱
已搬移至 https://g0v.hackmd.io/FUCSFS5kTguSX7F9OsOT-g


### 搜尋
:::info
這裡不急
:::
1. 整理現有教案 [metadata](https://docs.google.com/spreadsheets/d/1pQ0AlcU0UU4dzpSz58UOhTOj7dan_Zi7E4qUm1bMjFc)
2. PDF需要人工解析
3. [arte](https://github.com/coteach/server/blob/nesl/services/scraper/scrapers/arte_scraper.py) 爬蟲需要更加細緻

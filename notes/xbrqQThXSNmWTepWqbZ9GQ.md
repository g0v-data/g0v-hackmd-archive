---
tags: g0vernance
---
g0v slack app 登記
=================
根據 [g0v slack 治理機制討論](/rHe3Lfh_S3yhtRawnliSIg)，因為 g0v slack app 只能安裝 5 個，這邊記錄現有 app 的治理機制以及相關開源程式碼。

範本
---
- 申請人：
- 申請目的：
- 預計申請期間：（可為限期或永久）
- 相關程式碼（若為自行開發 app ，需要開放原始碼）
- 若開發中，預計開發多少：
- 使用資料範圍：

現有App
------

### 揪松小幫手
- 申請人： Ronny Wang
- 申請目的： 供 [g0v slack archive](https://g0v-slack-archive.g0v.ronny.tw/) 和 [線上揪松](https://meet.jothon.online/) 使用
    - g0v slack archive
        - 完整對話備份
        - 提供 slack 人數、頻道數、訊息數資訊給 [g0v dashboard](https://g0v.tw/dashboard/) ([API](http://g0v-slack-archive.g0v.ronny.tw/index/count))
        - 提供公開頻道內容 API ，並供線上揪松[彈幕](https://meet.jothon.online/message/barrage/CGU1SLHNH)使用 ([API](https://g0v-slack-archive.g0v.ronny.tw/index/getmessage?channel=CGU1SLHNH))
    - 線上揪松
        - [自我介紹](https://meet.jothon.online/event/show/g0v-hackath38n)
        - [線上大松](https://meet.jothon.online/meet/show/g0v-hackath38n)
        - [彈幕](https://meet.jothon.online/message/barrage/CGU1SLHNH)
- 預計申請期間：永久
- 相關程式碼：
    - [g0v slack archive](https://github.com/ronnywang/g0v-slack-archive)
    - [線上揪松](https://github.com/g0v/g0v-intro)
- 使用資料範圍：
    - g0v slack archive
        - 完整公開頻道聊天對話記錄
        - 登入使用者驗證同意後，備份非公開頻道
    - 線上揪松
        - 使用者頭像、暱稱、使用者登入驗證

### Matterbridge 橋接

- 申請人： pm5
- 申請目的： 供 matterbridge 橋接使用
- 預計申請期間： 永久
- 相關程式碼/文件：
    - [matterbridge](https://github.com/42wim/matterbridge)
    - [Matterbridge Slack bot setup](https://g0v.hackmd.io/IsyNmVDnTySE-OfVhEcQMg)
    - [g0v/bridge](https://github.com/g0v/bridge)
- 使用資料範圍：
    - 申請橋接的頻道的完整公開頻道聊天對話記錄與使用者暱稱
    - 頻道
        - #facing-the-ocean
        - #herstory 申請中

歷史App
------

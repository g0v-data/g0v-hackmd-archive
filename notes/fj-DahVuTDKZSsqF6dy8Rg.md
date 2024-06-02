---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240603 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## 小聚檢討
https://g0v.hackmd.io/9yeDnDJqQTe7CklA7pwuEA

- 照片內擺放方式：
  - 桌子 3x3、平行於長邊
  - 一個桌子放 4 人，9x4=36 椅子
- 實際出席：最多 17 人 + 工作人員
- 只有三條延長線，但要電的人會自己找邊邊坐，中間的人不插電但仍可參與

## RightsCon
https://docs.google.com/document/d/1ed8_p90gjxEp12Ce6PqjWh2FCVT0Pd-rkzPY5eBCVHk/edit

## DDoS 紀錄

### 6/1

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9c33c75e95cccf15066192fdf647e5c7.png)
https://drive.google.com/file/d/184sPI3OpZWuQf3KSfOetp0eL10W9WAJG/view?usp=drive_link

- 16:17 ~ 16:40 攻擊 /article/2t9fyk7wka3e4 觸發 HTTP requests from known botnet (signature #1)
  - 小聚期間，無人回報問題 XD
  - 14:18 monitor 有回報 site 短暫 520
- 17:54 ~ 17:57 針對 /article/2cawqaqh128pl 攻擊
  - 17:55 monitor 回報 site 短暫 520
- 18:01 ~ 18:12 針對 /article/2cawqaqh128pl 攻擊兩波
- 18:20 好像有一波隱形攻擊，僅部分被 Cloudflare 辨識，彈導致倒站 https://drive.google.com/file/d/1ZziuFMJQ_xah2kJL_MygF5qBG-Kuo-0P/view?usp=drive_link
- 18:27 API, LINE bot, site down
- 19:10 Recover by manually restart web server

### 6/2

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_933c2fc3b4f6ab6c8755430c15400a30.png)

https://drive.google.com/file/d/1JTSzIpO_f79fd1wUJhyfaJiS-x94wN8J/view

都是攻擊 `/article/2cawqaqh128pl`

- 18:32 ~ 18:38：觸發 Cloudflare HTTP DDoS - known bot net (signature #1).
- 18:59 ~ 19:03：觸發 Cloudflare HTTP DDoS - HTTP requests with unusual HTTP headers or URI path (signature #55)
- 19:03 ~ 19:18：觸發 HTTP requests from known botnet (signature #1).
- 19:04：API, chatbot, website 下線
- 19:30 補上 Cloudflare rule [name=nonumpa]++
- 20:04 發現網站已好，但 LINE bot 需要手動開啟

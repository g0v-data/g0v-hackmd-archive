---
tags: Rep0rter - g0v 零時記者
---

# 第壹次 Rep0rter 專案開會

[ToC]

https://g0v.hackmd.io/@Hawks/rJ2aJTetT

https://docs.google.com/document/d/1g4unx-__fvCc6tPLeniPd_jb5EoIDALXOYkROWyVaTo/edit

## Hawks 試做 Email

[g0v 社群重要更新 🌟](/vVsIRxJbTu6Io1Ag1MdxDQ)

- Ronny
    - 將頻道範圍跨張至整個 Slack (不局限於 General)
    - 加上 Slack 頻道連結以便討論
- Sky
    - 信件主旨可以根據內容寫出一個更好
    - 每個標題文不及義
    - 時間可以放在後面，把空間留給內文發揮
    - 順序可以不用按照時間，而是該資訊對於所有人的重要程度，或是閱讀的順暢程度 etc...
- Hawks
    - 要讓信件內容在讀者不需要點進出處連結的情況下，就可以知道發生了什麼事情
    - HTML 排版
- Wolf
    - 時間可以改成週一，週二等
    - 圖片嵌入電子報的可能性
        - [Ronny 寫的 Archive](https://g0v-slack-archive.g0v.ronny.tw/index/file?url=https%3A%2F%2Ffiles.slack.com%2Ffiles-tmb%2FT02G2SXKM-F0HJWFZ32-09a1db7d0f%2Fpasted_image_at_2016_01_02_11_46_pm_360.png%3Ft%3Dxoxe-2546915667-1169225759360-1144009992869-25c68316e444e38e4422a73da5595e43) 直接把 [Slack](https://files.slack.com/files-tmb/T02G2SXKM-F0HJWFZ32-09a1db7d0f/pasted_image_at_2016_01_02_11_46_pm_360.png?t=xoxe-2546915667-1169225759360-1144009992869-25c68316e444e38e4422a73da5595e43) 圖片拉進來了
        - 可能需要 Serverless 
        - Cloudflare Worker 應該可以解決
    - 發信的郵件是要使用郵件伺服器還是使用 Mailing list

## Wolf 建立 g0v 動態庫

- 本來想要用 TS 但看起來想改回 JS

## 零時先輩資訊共筆：

https://g0v.hackmd.io/@jothon/rydvIDluT/https%3A%2F%2Fg0v.hackmd.io%2F%40jothon%2FHJJecPgOp

## 電子郵件用途

- rep0rter@googlegroups.com
- rep0rter@gmail.com
    send to rep0rter@googlegroups.com
- rep0rter@g0v.tw

## 信件內容

- 人
- 時間
- 超連結
- 文章內容

## 電子報渲染

```md
<!--
請遵守以下格式

# 標題
內文 150 字                       |
- avatar: ![](image link)        | 可選
- name: chewei                   |
- time: Now                      | Monday ~ Sunday
- reference: https://google.com  | Website, Slack etc.
-->

# 今天天氣很好
我是內容我是內容我是內容  
- avatar: ![avatar text](https://xxx.yyy/aaa.png)
- name: chewei
- time: Now 
- reference: https://google.com
```

## 自動化方式

1. 把資料整理好發出 init 版本
2. 同步到 GitHub 上
<!--3. 發消息請大家 Review
4. 引導到全前端發 PR 的網頁
5. 直接編輯儲存後發 PR
    - 兩個人同時編輯會不會有問題？ [name=Wolf]
        - 如果用 HackMD 當後端能解決衝突 [name=Ronny]
    - 不小心打錯字如何回溯？
-->

## Ronny 出品ㄉ酷工具

https://github.com/g0v-data/g0v-hackmd-archive
https://api.search.g0v.io/

## 信件排版藍圖

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_adae08cc2babd31504d47effa27f5d53.png)

## Call to Action

1. [這裡](#自動化方式)ㄉ
2. 格式 GitHub Action
3. 寄信 (使用 GitHub Action?)
    - 新建立 Google 帳號
        - 開啓 2FA (?)
        - 使用 App password
        - Google SMTP

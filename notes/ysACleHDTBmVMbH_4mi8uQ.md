---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220928 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis: bil, mrorz
- 線上出席：4000, nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: rumors-line-bot
https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20220922

### :rocket: Staging

#### :robot_face: rumors-line-bot

https://github.com/cofacts/rumors-line-bot/compare/release/20220922...master

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [ ] LIFF 測試
    - [x] 傳送有 reply 的訊息，點開 Feedback LIFF 可切換正負評、儲存理由等正常運作
    - [ ] 傳送尚未回覆的訊息，點開 Comment LIFF 可儲存理由等正常運作

- [ ] Rich menu 測試
    - [x] 「設定」更改後再次打開，應該會保留原本設定
    - [x] 「教學」可以觸發教學流程
    - [x] 可以點開看過的訊息

##### ⛔️ Release Blockers

送出理由後會有空的 alert
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cc891cb69719053679adb50b4a686ca9.png =x400)

- https://github.com/cofacts/rumors-line-bot/pull/329
- Tenary operator's precedance problem
- [name=mrorz] will fix and PR

## 小聚檢討
https://hackmd.io/otpwqMFzTI6KQIXgQwncQg

- 3:30 開始自我介紹
    - 人多 + 比較投入 [name=bil]
    - 大家願意多聊是好事情 [name=bil]
    - 結束後的志工參與也比較好，有建立關係 [name=bil]
    - 想要留 email [name=bil]
        - 可以直接用 kktix 選參與者寄信
- 4:00 自我介紹完成
- 4:28 介紹完「回應」，開始練習回應
- 4:45 結束練習回應
    - 縮短為 15min，預留時間講 RSS / g0v slack
    - 也有人成功進來 slack [name=mrorz]

## Image support follow-ups

> https://github.com/orgs/cofacts/projects/9

何時宣布正式上線？

- 可以收 video & audio？ https://g0v.hackmd.io/IqCOZMZLRe-JPMSJIV3yRQ#Audio-amp-Video
- LIFF article & articles 支援圖片？ https://github.com/cofacts/rumors-line-bot/issues/319 [name=mrorz]
- 修好圖片「找不到」case？ https://github.com/cofacts/rumors-line-bot/issues/326 [name=nonumpa]

## 10/23 十週年

30min workshop 內容
"LINE 傳來的圖是真的假的？網傳圖片查核工作坊"
- 加 chatbot
- 蒐集可疑圖片
- 放補充資訊：在哪裡看到的、搭配什麼文字⋯⋯等
- 用手機就可以
- 另外加碼 Google 智慧鏡頭、以圖找圖

投影片連結 (最晚 10/22 23:59 提供)
- 表演 & 工作坊

## Nctex 來信要求下架

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_de453d746f6b4d09a50ec579d181dfa6.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6b8bbc20091896b8b056513527bb9abb.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bd8261da1e21d09c4fcfc64977138e68.png)

----

遭申訴網址：https://cofacts.tw/article/64p58ej8hpum
提到的文件：內文有 https://www.coloradosos.gov/biz/CertificateSearchCriteria.do
搜尋該 Confirmation number 確實有結果 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f91625e5e510b5c6812b66bc813d1d71.png)
https://www.coloradosos.gov/biz/BusinessEntityDetail.do?quitButtonDestination=BusinessEntityResults&nameTyp=ENT&masterFileId=20221675690&entityId2=20221675690&fileId=20221675690&srchTyp=ENTITY

[網路文章](https://vocus.cc/article/632d8608fd8978000171637a)號稱從 2018 年開始活動，但是上述文件是 2022 年 7 月送出的。

但根本找不到官網，只能找到可以自己上稿的平台發稿。
發信使用的也都是 gmail。

全球反詐騙查詢結果
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e030dc8ef5c9625d5a73b9ea61e9d3d5.png)
(冒名的也會在資料庫裡面)

## 下周會議暫停

- Orz: family trip
- bil: activity

---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20230823 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz
- 線上出席：nonumpa, 4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
https://github.com/cofacts/rumors-api/releases/tag/release%2F20230817
- Cooccurrences [name=LY++]
- Log cost saving

#### :robot_face: rumors-line-bot

https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20230817

- Increase typescript type coverage [name=LY++]
- highlight transcripts when searching text


## CCPRIP

### [Comm layer] 逐字稿
> https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ
> [name=nonumpa]

#### History
> [name=nonumpa]
> 
- 還在改 get version api
- collab server 儲存結束，網站要從 API 拿 versions

#### Auth
> [name=mrorz]

No progress yet


#### AI

##### LINE bot: Merging `processImage` & `processMedia`

- PR: https://github.com/cofacts/rumors-line-bot/pull/361
- Refactor 順便拿掉 `otherFields`
- 實測時發現 [ListArticles API](https://github.com/cofacts/rumors-api/pull/309) 會噴 error (reading `id` from null)，要另外修在 [API PR](https://github.com/cofacts/rumors-api/pull/309)

##### API 寫入 ydoc
> [name=mrorz]

No progress yet

### [Infra] Log cost saving

8/17 深夜上線
1.7G/day --> 1.1G/day

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7fe39ffd407752069a2c7ff15c844bc0.png)

另考慮換 Google cloud logging
- https://docs.docker.com/config/containers/logging/gcplogs/
- https://cloud.google.com/stackdriver/pricing
  - GCP Log ingestion fee: $0.5 per GB, 50G/project/mo free
  - AWS Cloudwatch ingestion fee: 0.76 per GB, 5G/mo free
  - 換到 Google cloud 好像不用錢，因為 < 50G / project / mo

## 11 月小聚場勘

- 有投影機、麥克風
- 11/18 訂金已付
- 可提供材料讓曬書店宣傳

場勘
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4c1a0a31a8b46a209f41882ee14627cf.jpg)

插座們
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_270e57163c84600a681cb1e0526e6d21.png)

簽到桌與廁所
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1bf69b91aebf748f89b8a1928ba1a0bc.png)


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_27c2273b89ec2c0d67d5f377ed7532b0.png)

:::success
提供海報 （relab 設計）:

https://www.figma.com/file/WbirxHjwl76NzorCaIGzBZ/Cofacts-%E6%96%87%E5%AE%A3%E6%AA%94?node-id=0%3A1&t=m5Xa4dr4doHICOim-1

下面的資訊換成活動資訊
200 張 A4

:::

5摺頁摺頁
https://www.figma.com/file/WbirxHjwl76NzorCaIGzBZ/Cofacts-%E6%96%87%E5%AE%A3%E6%AA%94?node-id=25%3A2&t=w3zkOQAFZDYLUjJU-1

## 檢舉處理：中二

https://cofacts.github.io/community-builder/#/editorworks?type=2&day=365&userId=j4S8C_UGoyBvoeIT1ATe1Wz02jFh_IsMOKLf7lqR3k2UpZqGk&showAll=1

- 檢舉人：「同一個帳號有70則訊息回報，多半為無意義訊息」
- 希望可以 block LINE user，他還是可以查，只是送訊息寄來沒人看到 [name=bil]
  - 看起來加了半年，還是不會用這個 LINE bot
- 確實有[抱怨](https://cofacts.tw/article/2qp6lyxy926zn)、[無用內容](https://cofacts.tw/article/j38tuptc4lq6) [name=mrorz]
- 在單日發送數則無意義內容；應該是手動發送。[name=mrorz]
- 但同一帳號又有回報真的詐騙，如 https://cofacts.tw/article/mlt1z7ppjmdl https://cofacts.tw/article/1qm3yjb002hkx  https://cofacts.tw/article/2ls4kijpl3k4b [name=mrorz]
- 這是 LINE 使用者，看起來沒有直接違反 [Cofacts 聊天機器人使用者條款](https://github.com/cofacts/rumors-line-bot/blob/master/LEGAL.md) [name=mrorz]
  - [過往案例](https://github.com/cofacts/takedowns/blob/master/2022/1221-swear-word.md)是針對有相近條款的網站使用者，且有公告社群討論後才執行
  - 因此若要介入資料庫進行處理，至少會需要在社群公告
- 針對訊息的封鎖，目前功能並不完備 [name=mrorz]
  - 目前 LINE 使用者的操作只有針對「人」的「封鎖」，一封下去就會影響過去以及未來該使用者所送出的訊息、回應、feedback 等等
  - 即使他現在送了很多垃圾，但看起來也是會轉傳實際詐騙的人。如果現在封鎖他，未來他又剛好是一篇熱門的詐騙的第一個傳進來的人，那系統會不會把熱門度算在這篇（被封鎖的人所發出的）訊息上、然後查核協作者又看不到（因為作者已被封鎖），也是個問題。
- 從被檢舉人傳的內容看起來，他像是中二 [name=mrorz]
  - 原神 https://cofacts.tw/article/2l5l83qbetjwc https://cofacts.tw/article/2gqn5dr5s1kr9 https://cofacts.tw/article/c_lAP4cBn6k8q-JUrn-Q
  - Roblox https://cofacts.tw/article/1wjxjadbzx9ep https://cofacts.tw/article/1qofqhd63fzg5 
  - 無聊的性玩笑 https://cofacts.tw/article/3oq9eyjk7704s
  - 朋友間還會有人傳連鎖詛咒信 https://cofacts.tw/article/bfkxah8tp5t5
  - 看起來像九年級教室的公告 https://cofacts.tw/article/2do9k8arogpzw
- 小弟弟喔⋯⋯好吧 [name=bil]
  - 不會計較，因為是正太控。 [name=bil]

## 下周會議時間

- 週三有事情，是否可以週四 [name=bil]



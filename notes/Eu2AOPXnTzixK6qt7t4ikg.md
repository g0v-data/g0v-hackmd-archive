---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20230927 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz, nonumpa, cai
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :electric_plug: API

- https://github.com/cofacts/rumors-api/pull/317
- https://github.com/cofacts/rumors-api/pull/318

#### :robot_face: rumors-line-bot

- https://github.com/cofacts/rumors-line-bot/pull/363

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 群組訊息可以運作
- [x] 1:1 可送出全新影片、圖片、聲音
- [x] 點到網站，可以看到 AI 逐字稿自動填入


#### :globe_with_meridians: Site
##### Testing checklist
http://dev.cofacts.tw/

登入自有帳號後檢測：
- [x] AI 逐字稿填入後，edit history 正常運作

##### ⛔️ Release Blockers

##### 未竟項目

- User unknown: 在 ydoc 那裡呼叫 `setUser`  https://github.com/cofacts/rumors-site/blob/63c03a7c1753d61fb95b3ec9d6cf9e6f2ec43095/components/Collaborate/CollabEditor.js#L93-L101
  - `permanentUserData.setUserMapping` 會 mutate `ydoc`，後面不用 `permanentUserData` 也無所謂
- 尚無歷史紀錄
  - 重新整理之後就會有 Unknown，timestamp 會是重新整理的時間
  - 可能需要手動塞 snapshot
    - https://github.com/cofacts/collab-server/blob/master/src/snapshot.ts#L35C9-L39
- WhisperAPI hallucination https://dev.cofacts.tw/article/FpSR1ooBXtQmmeronHkr

### :eye: Under review

## CCPRIP

### [Comm] Transcript

> https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ
> [name=nonumpa]

#### AI: API 寫入 ydoc
> Design doc https://g0v.hackmd.io/wkx286lmTDaFUpgRhnUawQ#CreateMediaArticle
> Related discussion on 2023/8/2: https://g0v.hackmd.io/0tPABSZ6SRKswBYqAc1vZw#API
> [name=mrorz] 
> 

https://github.com/cofacts/rumors-api/pull/318

遇到 ydoc 下的 lib0 無法跑 jest 問題
- `transformIgnorePatterns` 無用 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d40fa8cfba9e27c7facb3bcada0fa23d.png)
- 加 type: module 的話會死在 TestSequencer 而且改 import 也說有 require


### [Op] Explicit content filtering

> https://g0v.hackmd.io/@cofacts/rd/https%3A%2F%2Fg0v.hackmd.io%2FBRsJOevWSbyUMBSZEVVWrA


Avoid account being busted with explicit content
  - Safesearch annotation https://cloud.google.com/vision/docs/detecting-safe-search
  - Pricing: free


### [Comm] Topic labeling
- Supervised learning of Cofacts topics with Vertex AI AutoML
  - [Pricing](https://cloud.google.com/vertex-ai/pricing): prediction USD5 / 1000 text records (1,000 unicode characters each)
  - Batch processing does not need to deploy endpoints
- Cloud natural language API's classifier
  - All categories https://cloud.google.com/natural-language/docs/categories contains COVID-19, etc
  - Pricing: by unicode characters ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_aa481bf2c2cc2968f95ed2f279f92035.png)


### [Comm] Reverse image search with CloudVision API
- https://cloud.google.com/vision/docs/detecting-web
- Takes image or screenshot of video
- Search on horizontal flips
- Pricing
  - free for first 1000 unit / mo
  - 3.5 per 1000 unit afterwards


## 11 月小聚

海報已更新： https://www.figma.com/file/WbirxHjwl76NzorCaIGzBZ/Cofacts-文宣檔?node-id=0%3A1&t=m5Xa4dr4doHICOim-1

- TODO: 傳到 google drive 再傳到曬書店粉絲頁

KKTIX Prompt: 不同年紀的人的在上課的背影

## 檢舉處理

### 多重帳號

CIB 處理公告
- https://github.com/cofacts/rumors-site/pull/547
- https://github.com/cofacts/rumors-line-bot/pull/362

討論
[Facebook](https://www.facebook.com/groups/cofacts/posts/3656817661216703/), Slack & discord: 無回音

- 邀請 NX 來小聚 [name=cai]


### 不認真回應

https://www.facebook.com/groups/cofacts/posts/3656870847878051/

無討論

:::info
先放著
:::

## 來信

喬治亞

- data from civic society
- bil contact, 內容交換與互助、協助

:::success
Forward 給 hi
:::

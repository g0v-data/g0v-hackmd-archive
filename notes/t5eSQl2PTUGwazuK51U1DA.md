---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240208 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## Release

API https://github.com/cofacts/rumors-api/releases/tag/release%2F20240205
但 Facebook 需要 Business account 認證，與 Google workspace 一起進行好了
> https://g0v.hackmd.io/joEUsABVRr2aMQqD-Z8ixQ#Facebook-apps

## 小聚籌備

- [x] 日期：2/18 (日)
- [ ] 食物：現場點
- [x] 場地：[蘭燈空間](https://linteng.org.tw/lanternspace/) 
  - 尾款當天付
- [x] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Slido 暖身
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [x] 投放目標：
  - 推播日: 農曆年間 / 前（提早）
    - 除夕以前：大家可能在移動，收不到地點為「宜蘭/花蓮」的推播 [name=nonumpa]
    - 初一：應該都在所在地了，可以推
  - 目標：宜蘭、花蓮
  - 宜蘭媽媽朋友
  - 海報貼在宜蘭農會 [name=bil]
    - 改海報 [name=johnson]
    - Figma: https://www.figma.com/file/WbirxHjwl76NzorCaIGzBZ/Cofacts-%E6%96%87%E5%AE%A3%E6%AA%94?type=design&node-id=338-2955&mode=design&t=V0MEyPXIvAQnLZDl-4
    - PDF: https://drive.google.com/file/d/17hAV4qJSQeAz27844Tb28MVZiEL4bTl2/view?usp=drive_link
    - 放 ibon 要印 A3
- [x] KKTIX:https://cofacts.kktix.cc/events/cofactseditor40
  - 配圖：玄武 = 龜（山島）+ 龍
- [x] 誰會來呢：bil, mrorz, nonumpa
- [x] 記得帶：貼紙、環保杯
- [x] LINE 文案（初一）
  - 甲辰年新年快樂。
  「這裡是宜蘭南方澳漁港，滿載新鮮鮪魚，但漁民卻笑不出來。核廢水是輻射性的，人類沒辦法把它從水裡排除掉。到了人體癌症的機率就會提高。」這是一則假訊息，現在你有機會幫助家人破解這些難題囉！Cofacts 真的假的 要到宜蘭舉辦免費的查核志工培訓工作坊啦，能回到家鄉真的超級開心，這次我們要到宜蘭市，用一個周日下午的時間幫助親朋好友抵禦網路上的假新聞與不實訊息唷！
時間：02月18日（日）14:00-17:00(活動免費，會準時開始)
地點：蘭燈空間 LANtern SPACE / 260宜蘭縣宜蘭市中山路一段662號3樓
請自行攜帶筆記型電腦與電源，當天會準時開始唷！
請先報名 https://cofacts.kktix.cc/events/cofactseditor40
- [x] VOOM 發文


## MyGoPen 謠言惑眾獎

- MyGoPen 有撈出他們的，需要另外 map article ID
  - 初步觀察：很多舊的
- TODO: 撈出 https://colab.research.google.com/drive/1mBWULiyKTBLRMvX8Un4mBQdJEBJkeF3I#scrollTo=Z_ta9fA2KCAa 裡面有 reference MyGoPen / TFC 的那些
  - 計算 Popular 與否

## CCPRIP & TODO planning

### [Op] Transcript spam
> nonumpa
> https://g0v.hackmd.io/vKCvrqSQTlm7GEx9MAXGaw?view#op-Transcript-spam-處理

### [Comm] article group 收尾

> nonumpa

- 補 unit test [name=nonumpa]
- 更新 chatbot state diagram [name=mrorz]
  - Before: ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e38866d6dd1f9952c711572861375459.png)
  - After: ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2b75c4085789972883d3bede5094cbd8.png)
    - Remove `__INIT__` at the bottom, change to looped arrows
    - Add `__PROCESS__BATCH__` and `ASKING_COOCCURRENCE` from the bottom
    - Recolor entry states
    - Reference in the design doc: https://docs.google.com/drawings/d/1HVjAacHCt7UJWINJ9hekvYmWZ2V62CStHgZeXu8_dj4/edit
  - 發現 `processBatch` 忘記埋 ga 了，應該埋個 `__PROCESS_BATCH__` 才能計算送了 batch 之後，有回報是否為 cooccurrence 的比例
  - MrOrz 發 PR 補
- 在 tutorial 加字 [name=mrorz]
  - 不知道放哪，先不要？
  - 可以看看 ga 使用狀況 [name=nonumpa]
- VOOM 宣傳 [name=mrorz] ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2f4bc9ddbbce94a44e60ebe2eab13af5.png)

### [infra][op] API key
> Previous research: https://g0v.hackmd.io/51wwLHgvSUqtBDaP-yAVnA#Alternative-Implement-using-Cloudflare-Zero-Trust

community-builder 改 server-side render
- https://github.com/cofacts/dashboard
- Deploy to: https://dash.cofacts.tw

TODO
- prettier + CI workflow
- shadcn
- stats
- editor works

### [Comm] AI assisted reply authoring

> Previous proposal: https://g0v.hackmd.io/oz-49rOSSPW3J8AbG0yRSA#Comm-ChatGPT-aid-fact-checking
> 

Design doc: https://g0v.hackmd.io/@cofacts/rd/%2FmU8qi721RZeAQ9PDfj7XRA

- 覺得酷，覺得需要時間 [name=bil]
  - Improve writing 的實作比較快，而且比較能想像效果應該還行；另外其他的部分較具開創性，不確定效果如何，而且比較花時間。 [name=mrorz]




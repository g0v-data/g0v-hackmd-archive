---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240311 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz, hsin-tzu, nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site
https://github.com/cofacts/rumors-site/releases/tag/release%2F20240311

## CCPRIP
### [Op] Transcript spam
> nonumpa
> https://g0v.hackmd.io/vKCvrqSQTlm7GEx9MAXGaw?view#op-Transcript-spam-處理

 - 發現有很多 history 都只有名字（舊版）沒有 userid，要把這些 case 撈出來再用名字 mapping 回 userId，怕使用者在這期間改了名字 mapping 不回來
 - update contributors
     - 要先 get 再 update
     - 或每次都從 ydoc 拿一次 contributors
     - 可以理解從 ydoc 拿可以確保 single source of truth，不過這樣要等 plugin 做完 [name=mrorz]
     - 也可以做在 plugin 裡 [name=nonumpa]
     - 但 plugin 應該只處理 ydoc。如果要紀錄 `articles.contributors` 或許在 collab-server index 裡做比較恰當 [name=mrorz]
- 要在 GraphQL 做一個可以讀的 filter? [name=nonumpa]
    - `ListArticles` 要可以 filter by contributor，這樣 user page 能列出使用者貢獻過逐字稿的 articles 讓使用者點回去，也能計算總數


### [Comm] article group 收尾
> nonumpa


### [Comm] Whisper hallucination

> https://github.com/cofacts/rumors-api/issues/326
> [name=mrorz]

Design doc: 
- https://g0v.hackmd.io/wkx286lmTDaFUpgRhnUawQ#Whisper
- https://g0v.hackmd.io/65JMCYDEQCeCYSAkBwJNTA#Better-multimedia-support


新點子：除了用 VAD 之外，也可以⋯⋯
- 先 OCR 首幀影像，然後把裡面的文字放進 whisper prompt
- Whisper 跟 Google 的 transcript 同時做，然後交給 LLM 改寫
    - 要跟 LLM 說，請參考 Google transcript 來移除 Whisper 裡面的 hallucination
    - 可以把第一幀影像傳給 multimodal LLM 同時進行判斷
    - 這個應該會很慢，不適合即時檢索，但適合用來加工要送到資料庫的影片逐字稿
        

### [Op] Google 非營利
- 回信後尚無回音


## User organization and CoC
> https://g0v.hackmd.io/ucUXvnqbRBmsD6YGkmdYvg?both#User-organization-and-CoC
> bil

N/A

## 小聚籌備

- [ ] 日期：3/24 (日)
- [ ] 食物：要自己清，垃圾桶不能丟
- [ ] 場地：新北青職基地 1F
    - 一定要 20 人以上，最多坐 60
    - 6 個桌子、20 張椅子、麥克風、投影幕、筆電
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
  - 推播日：3/18 (一)推播
  - 推播日之前：新北志工優先報名
  - 目標：雙北、桃園？
      - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_aff7fe2b732675b4b90f1e90a56fd071.png)
    - 14 萬人收到、萬分之2報名率 --> 開 30~40 人、預期 20 人到場？
    - Ref: [past click through rates](https://docs.google.com/spreadsheets/d/1XjEQZ9esNKfkGd8XYd1p3E8DTgB0f5QPDl5ghf-JxE0/edit#gid=0)
- [x] KKTIX:https://cofacts.kktix.cc/events/cofactseditor41
- [x] 誰會來呢：bil, mrorz, nonumpa
- [ ] 記得帶：貼紙、環保杯
- [x] LINE 文案
Cofacts 要來到新北市舉辦志工培訓啦，三鐵共構板橋站，交通超級方便唷！
地址：新北市青職基地 / 新北市板橋區民權路170號1樓
時間：03月24日（日）14:00-17:00(會很準時開始)請記得攜帶筆記型電腦喔！
活動報名：https://cofacts.kktix.cc/events/cofactseditor41
- [x] VOOM 發文


## 2024 TODO

> API & DB enhancements: https://g0v.hackmd.io/@cofacts/rd/%2F65JMCYDEQCeCYSAkBwJNTA

讓更多在意假訊息的人加 Cofacts LINE bot
- 下 google / FB 關鍵字廣告，投放廣告使更多注意到假訊息問題的人使用 cofacts
- 用熱門的謠言、美玉姨、趨勢科技防詐達人、LINE 訊息查證等名字，或 debunk, 查核 等作為關鍵字
    - 有考慮找 KOL 嗎 [name=hsin-tzu]
    - 怕 KOL 炎上 (或 Cofacts 炎上燒到他 (?)) [name=mrorz]

更多人知道如何使用 cofacts 協作
- 網站改版：https://www.figma.com/file/nFFi6c8ennXV8CxeF58Asl/Confact?type=design&node-id=0-1&mode=design&t=r3aPm6FzJfFgsQMT-0
    - Optional: 增加教學與說明？
    - 問題：server rendering 與目前 API 的 web authentication 不合，需要在 Cofacts site 上重新進行 authentication (NextAuth.js) -- https://g0v.hackmd.io/51wwLHgvSUqtBDaP-yAVnA#Alternative-Treating-all-apps-equal
        - 或是用 proxy 做 https://g0v.hackmd.io/51wwLHgvSUqtBDaP-yAVnA#Proxy-issue-passing-login-cookie-around
- 編輯逐字稿的 contribution 與 visualization (斌綸正在做的那個)
- 野生查核協作小聚：培養查核協作者培訓講師 train the trainer
    - 包含事後 QC
- 讓網傳影片，能更有效率地被查核協作者處理。包含：用 LLM + 首幀截圖來改善 indexed 逐字稿、Thumbnails 等讓查核者可以一目了然的輔助功能那

持續貢獻
- Optional: achievement badge?
- 維繫現有查核者的關係 (寄信)


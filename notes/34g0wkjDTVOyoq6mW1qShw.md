---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240201 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, orz
- 線上出席：nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :globe_with_meridians: Site

Upgrade Facebook Graph API https://github.com/cofacts/rumors-api/pull/333

##### Testing checklist
http://dev.cofacts.tw/

- [x] Can login with Facebook

遇到這個
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bae88d6b08fbacaed6ba2162e0304a8c.png)

網址是：
https://www.facebook.com/v19.0/dialog/oauth?response_type=code&redirect_uri=https%3A%2F%2Fdev-api.cofacts.tw%2Fcallback%2Ffacebook&scope=email&client_id=719656818195367

- 會是[進階存取權限](https://developers.facebook.com/docs/graph-api/overview/access-levels#advanced-access)的關係嗎 [name=mrorz]
  - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e3510cf84a991961849000b3b2fe84a0.png)
  - 需要 business acount

- Staging & production 都不行 [name=nonumpa]
  - 所以不是這次 API 升級導致的

##### ⛔️ Release Blockers
無

##### 未竟項目

FB 驗證 public_profile 與 email 送審

## 小聚籌備

- [x] 日期：2/18 (日)
- [ ] 食物：現場點
- [x] 場地：[蘭燈空間](https://linteng.org.tw/lanternspace/) 
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
- [ ] 投放目標：
  - 推播日: 農曆年間 / 前（提早）
    - 除夕以前：大家可能在移動，收不到地點為「宜蘭/花蓮」的推播 [name=nonumpa]
    - 初一：應該都在所在地了，可以推
  - 目標：宜蘭、花蓮
  - 宜蘭媽媽朋友
  - 海報貼在宜蘭農會 [name=bil]
    - 改海報 [name=johnson]
- [ ] KKTIX:https://cofacts.kktix.cc/events/cofactseditor40
  - 配圖：玄武 = 龜（山島）+ 龍
- [ ] 誰會來呢：bil, mrorz, nonumpa
- [ ] 記得帶：貼紙、環保杯
- [ ] LINE 文案（初一）
  - 甲辰年新年快樂。
  「這裡是宜蘭南方澳漁港，滿載新鮮鮪魚，但漁民卻笑不出來。核廢水是輻射性的，人類沒辦法把它從水裡排除掉。到了人體癌症的機率就會提高。」這是一則假訊息，現在你有機會幫助家人破解這些難題囉！Cofacts 真的假的 要到宜蘭舉辦免費的查核志工培訓工作坊啦，能回到家鄉真的超級開心，這次我們要到宜蘭市，用一個周日下午的時間幫助親朋好友抵禦網路上的假新聞與不實訊息唷！
時間：02月18日（日）14:00-17:00(活動免費，會準時開始)
地點：蘭燈空間 LANtern SPACE / 260宜蘭縣宜蘭市中山路一段662號3樓
請自行攜帶筆記型電腦與電源，當天會準時開始唷！
請先報名https://cofacts.kktix.cc/events/cofactseditor40
- [ ] VOOM 發文

:::success
明天會有 kktix
海報 --> PDF 在 7-11 印成 A3
:::

## MyGoPen 謠言惑眾獎

> [20231018 會議記錄](https://g0v.hackmd.io/v4taAFAtRt6EOMGGMa7Btw#%E4%B8%80%E8%B5%B7%E8%BE%A6%E8%AC%A0%E8%A8%80%E6%83%91%E7%9C%BE%E7%8D%8E)

整理 Cofacts Analytics 排名
https://colab.research.google.com/drive/1mBWULiyKTBLRMvX8Un4mBQdJEBJkeF3I#scrollTo=jD4Z2J_NvtHA

- Text 明顯較多，因為使用者都會 google 文字而無法 google 圖片或影片
  - 可能要另外做 LINE + LIFF 的 ranking
- 會有 similar article 分開計算的問題（數字會分散）

## CCPRIP & TODO planning

### [Op] Transcript spam
> nonumpa
> https://g0v.hackmd.io/vKCvrqSQTlm7GEx9MAXGaw?view#op-Transcript-spam-處理

這禮拜沒進度

### [infra][op] API key
> Previous research: https://g0v.hackmd.io/51wwLHgvSUqtBDaP-yAVnA#Alternative-Implement-using-Cloudflare-Zero-Trust

- community-builder 改 server-side render
  - `dashboard` repo
  - nextjs + tailwind + shadcn (也是新 rumors-site 預計的 tech stack)
  - server component --> 不會 expose API
- rumors-site 重構
- 設定 Cloudflare key 與 API
- 發信告知第三方：
  - 停用 api.cofacts.g0v.tw
  - 需要帶 key
  - 詳見 https://g0v.hackmd.io/65JMCYDEQCeCYSAkBwJNTA#API-access-amp-client-management

### [Comm] AI assisted reply authoring

> Previous proposal: https://g0v.hackmd.io/oz-49rOSSPW3J8AbG0yRSA#Comm-ChatGPT-aid-fact-checking
> Not in cofacts/rd doc yet

- RAG analysis
- AI 共編討論

### [Comm] article group 收尾

- 補 unit test
    - unit test 需要幫忙補嗎？ Johnson 可以專心改網站 [name=nonumpa]
    - 要！感謝 m(_ _)m [name=mrorz]
- 傳單一圖影音時不用再問是否有其他訊息
  - 看起來已經自然有人會這樣傳了
    - TODO: 更新 chatbot 的 state diagram [name=mrorz]
  - 在 tutorial 加字嗎？
    - OK [name=bil]
  - 要推播宣傳嗎？
    - 推播有點多，放 voom [name=bil]

### [Op] cofacts.tw google workspace

- 揭露協會與 Cofacts 社群的支持關係 https://g0v.hackmd.io/4HVFW0ivS-e9QfArzzOFiA#%E5%AF%A6%E7%A7%91%E5%8D%94%E6%9C%83
- 自行申請 google 非營利或跟 OCF 談
  - 自行申請 [name=bil]

### [Infra] API & DB enhancements

See https://g0v.hackmd.io/@cofacts/rd/%2F65JMCYDEQCeCYSAkBwJNTA

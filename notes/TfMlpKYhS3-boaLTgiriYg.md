---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20200520 會議紀錄
=====

Workis
> 線上開會： https://tico.chat/powercall?room=cofactshack&type=timeFirst
> 上次開會紀錄：https://g0v.hackmd.io/@mrorz/BJ2GzyK9L

## 5/23 在家大松

> :bulb: 報名頁面 Register for participants：https://bit.ly/g0v39thregister
> :bulb: 活動共筆 Note：https://g0v.hackmd.io/@jothon/g0v-hackath39n （新手必看！！）
> [name=ichieh, g0v#general]


### 誰會來

在家組
- nonumpa

Workis 組
- mrorz
- bil

食物
- 3 份貓下去涼麵

:::success
5/21 就要下訂，最晚 5/22
:::

### 怎麼進行

https://meet.jothon.online/meet/show/g0v-hackath39n

- 沒有「聲音近大遠小」
- 沒有「區域地投影螢幕」 
- 考慮用 https://theonline.town/ ？ (no screen-sharing)
- breakouts https://github.com/jitsi/jitsi-meet/issues/4787

編輯用私訊
code 直接用主頻 (jitsi)

### Good first issue

https://github.com/cofacts/rumors-line-bot/labels/good%20first%20issue
https://github.com/cofacts/rumors-site/labels/good%20first%20issue
https://github.com/cofacts/rumors-api/labels/Good%20first%20issue

### 標記作業

> 上了的話 @darkbtf 就可以把我們現在標的好的資料含若水標記的資料全部打回去哩
> 
> [name=ggm, [g0v#cofacts](https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1588662781.346900)]
> 

確實已有介面，但可以不用在大松呼籲人用 Cofacts 分類介面

因為還不是最新的樣子

## 台南

### 2020/05/31

:::success
2020/5/31 (日) 1:30pm ~ 5:30pm
:::

第二十次台南小聚

僅 1 人報名：https://cofacts.kktix.cc/events/cofacteditor20

- [x] 主題：
    - 好想在台南小聚喔
        - 主視覺：孔廟 牛肉湯
- [x] 時間：5/31 (日) 2:00pm ~ 5:00pm
- [x] KKTIX(https://cofacts.kktix.cc/events/cofacteditor20)
- [x] 攜帶貼紙 - bil
- [x] 場地：會是[好想工作室](https://goo.gl/maps/MBd7jz6gDK3J3fJV9)（含場佈：1:30 ~ 5:30）
    - [x] 水
        - [ ] 自備水杯
        - [ ] 紙杯
    - [x] 麥克風+插座+網路
    - [x] 投影機
    - [x] 延長線
    - [ ] 食物 - Rosalind
        - [ ] budget: <2000NTD (NTD80 / 人)
    - [x] 垃圾桶
    - [ ] ~~Talk~~
    - [ ] 路標、黏土 - mrorz
    - [ ] wifi（現場有）
        - [ ] 小松 25 人不是問題
        - [ ] Nighthawk M1 + 4G sim
        - [ ] ASUS RT-N12 Wireless N300 (2x 5dbi高增益天線)
- [x] 誰會來呢：mrorz, bil, 文武, RR, lucien
- [ ] LINE 文案

bil
當週週三再推播嘉義台南高雄
已經放主頁

orz
可能放個 rich menu

bil
因為這個活動的 priority 沒有那麼高
提早的話大家也會臨時有事
不如當週才宣傳，這樣只有真的沒事的人再來

orz
平常小聚觸及是 50K
嘉義台南高雄是 20K

:::success
rich menu - orz
需要推播台南
:::

### 2020/06/01 台南大學

型式：同政大

:::warning
TODO: 需要 O/X 的 instant
https://github.com/cofacts/community-builder
:::

## Production Release Plan

Discussion: https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1589252345.423700

### Versions / release scope

- API - master branch, on production now
- [Website](https://cofacts.hacktabl.org) - https://github.com/cofacts/rumors-site/pull/249/
  :::danger
  **Release blocker**
  - [ ] Google analytics component tracking - https://github.com/cofacts/rumors-site/pull/254
  - [ ] PR249 rebased to include GA
  :::
- Chatbot - master branch, on production now
  :::danger
  Fix iOS `isInClient` issue
  https://github.com/cofacts/rumors-line-bot/blob/dev/src/liff/index.js#L11-L19
  Maybe try [`getOS`](https://developers.line.biz/en/reference/liff/#get-os) instead?
  
  https://liff.line.me/1654201315-ElNako7b
  
  Fix: https://github.com/cofacts/rumors-line-bot/pull/189
  :::

### Progress

- [x] Deploy API
- [ ] Deploy production english version
  - [x] [English Chatbot](https://lin.ee/2Ox46aqyW): Deploy `dev` branch
    - [x] LIFF app & env
      - [x] env: `ROLLBAR_CLIENT_TOKEN`, `JWT_SECRET`, `MONGODB_URI`, `LIFF_URL`
      - [x] Fix LIFF issue
  - [ ] Website: `site-en` image label 改 `pr249-en` in docker-compose file
- [x] Translate to TC
  - [x] Chatbot PR: https://github.com/cofacts/rumors-line-bot/pull/187
  - [x] Website PR: https://github.com/cofacts/rumors-site/pull/253
- [ ] Introduction text
  > TBA
- [ ] Deploy production TC version
  - [x] Chatbot: 
    - [x] env: `ROLLBAR_CLIENT_TOKEN`, `JWT_SECRET`, `MONGODB_URI`, `LIFF_URL`
    - [x] merge to `master` and push
  - [ ] Website: `site-zh` image 改 `pr249-tw` in docker-compose file


## Youtube API audit

回信內容：
Google 回信說
如果我們不是直接儲存 title, description，而是儲存被處理過的資料，例如說 keyword 之類的分析，就不受 30 天限制

> Cofacts這邊可以多做一層parsing 和 ranking的機制
> 或許這個機制可以解決:
Cofacts got YouTube's link as a search query -> use this query as a parameter in YouTube Data API to get title/description -> Do some linguistic parsing/natual language parsing and store results to Cofacts' database (instead of storing YouTube's link and title/description) -> Search within Cofacts' database and get ranking/confidence score 


這是 youtube 全球皆然的規定，無法變更

處理方式：

orz:
我們做的是 archive，若內容下線之後，編輯還是要可以看到原文
只存 result 或許有助於 search 但效果比較差（編輯無法看到原文）

不知道可不可以不靠 API 而用爬的（archive，不針對 youtube 處理）或許就能繞過？

:::success
g0v #cofacts 討論
:::

### Terms & Privacy review

As-is
- [網站 Cofacts TOS](https://hackmd.io/mFSlWs4IQke_9RnFAOWlfQ)
- [Chatbot TOS](https://hackmd.io/t2DSbtU9RsS8cNTi-uLtSQ)

5/8 寄信來
5/29 為 15 工作天後

:::warning
- 要改什麼
  - III.A.1 state in their own terms of use that, by using those API Clients, users are agreeing to be bound by the YouTube Terms of Service + link
  - III.A.2.a. be prominently displayed and easily accessible to users at all times
- 如何公布: 放網站 footer
- 時程: 下週
:::



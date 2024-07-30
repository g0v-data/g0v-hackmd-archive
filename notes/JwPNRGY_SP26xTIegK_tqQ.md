---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20230208 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- workis 出席：bil, mrorz
- 線上出席： nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
https://github.com/cofacts/rumors-api/releases/tag/release%2F20230203
- block spammer articles

Currently rolled back to 12/13 version to see if errors decrease (more on this later)

#### :globe_with_meridians: Site

https://github.com/cofacts/rumors-site/releases/tag/release%2F20230203 
- block spam
- don't show reply requests <= 0 score for aanonymous
- Typescript support


#### :robot_face: rumors-line-bot

https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20230203
https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20230207
- Better logging to track errors & if group messages work


## Crowd-source transcript update

> 還在研究 hocuspocus 的 db extension 和 Y 的 document class (history)
> [name=nonumpa]


## Group message tracking

- 2023/2/3 2am deploy logging 時重開 chatbot server，group 恢復運作
- 2023/2/7 2am 印出 chatbot group 判斷 log
- 不穩的情形？
- 可能是 docker container --> concurrency = 3
  - 有些 instance 的 queue 斷掉 （？）但有一些好的 [name=mrorz]
  - 因為 redis 很貴，在考慮日後會把 line bot 拆到其他服務（google cloud run 等）跑的狀況下，會希望減少 dependency
    - bull.js depend on redis
    - 但還是應該要有 queue 比較好
    - 可能找其他不是 depend on redis 的 queue
    - RabbitMQ? Kafka?
    - Google event pub/sub?

:::success
每 1hr 重開？
pm2 reload all
:::

- 調降比對 % 數？
  - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6030337ed61c9c8a2148d03a5af60ab9.png)
  - 目前都不太回話，不確定多話的狀況是如何 [name=bil]

:::success
調 0.7 之後追蹤回應是否合理
:::

- 大多還是健康類、會中的通常 similarity 都很高，很少調降 0.7 之後加回的

## 色情 mitigation

### Legal update

- Chatbot: https://github.com/cofacts/rumors-line-bot/pull/340
- Site: https://github.com/cofacts/rumors-site/pull/527/files?short_path=da8a0fe#diff-da8a0fecbbc84fd9b0f9efad9d4ce8f9b15928c35161498c6161f4f8f3506c5c

### Takedown candidates

:::info
From: https://g0v.hackmd.io/6c3CpKXhQwOtFX8kf31ePA#%E8%89%B2%E6%83%85%E5%9C%96%E7%89%87
:::

- https://cofacts.tw/article/f_pDPIUBC7Q3lHuUGOh8
    - LINE bot user `j4S8C_BLFHD5oU73AduwXzBBeEqOZ52spoyUjfCJpR87fDWMA`
    - 所傳進來的其他訊息：
        - https://cofacts.tw/article/h_sIBoYBC7Q3lHuUSaLT
        - https://cofacts.tw/article/WPue1oUBC7Q3lHuUbn_N
        - https://cofacts.tw/article/3prnyzh4f9dsi
        - https://cofacts.tw/article/36cwqs4he2mzf
        - https://cofacts.tw/article/2l4rvj1yllr2j
        - https://cofacts.tw/article/212c38ng672dq
        - https://cofacts.tw/article/-PtFeYUBC7Q3lHuU-SWZ
- https://cofacts.tw/article/O_qIMYUBC7Q3lHuUod0J
    - LINE bot user `j4S8C_P73G2TtM6FqW7rsDp6JOv3L5g6koVO8jgMVmkXeSRE0`
    - 傳進來的東西僅此一份

:::success
- 公告使用者條款變更
- 上面這兩篇當範例
- 大家覺得 OK 就刪文
:::

## CCPRIP

### [Infra] Chatbot stability

:::info
- [20230131 discussion](https://g0v.hackmd.io/iGqCnbuoQfKlZLTNEyM3dw#Infra-Chatbot-%E7%A9%A9%E5%AE%9A%E5%BA%A6)
- Analsis doc: https://g0v.hackmd.io/mkb9Wr_2SrCbbiLCv_7-EQ
:::

- 排除 2023/1/23 API deploy，將會把版本換回來
- 還沒找到原因⋯⋯

### [Op] Anti-SEO spam

:::info
Previous cases https://g0v.hackmd.io/XBJS-KEtScWyVCuQ9P_iNQ#Cases
:::

Account to delete
- `j4S8C_LO8hbMHXx2JJGkLhlrJFIE3eilJW0mu2SGJScX1D1cE`
    - 明顯是 SEO spammer：在不同網站發布後，來 Cofacts 送出
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4075c648dcad2a571eb645420aff7e07.png) ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1cbeba463e54edcfb05d46db1a16c2ba.png)
- `j4S8C_PM1BJIZ1acF-VZZPmA9Zm8AZUZC7Va2k1uN5p8CK23k`
    - 文章發表當日就送進來 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c2b25ebc2cee2e310135465b51f8bbfa.png)
- 需要 community builder for articles 比較能一口氣列出違規狀況⋯⋯ [name=mrorz]
    - 用 comment 就可以啦，送訊息進資料庫一定會有 reply request

:::success
- 先做 community builder
- 寫 takedown，PR 貼 FB
:::


## GA4 breakdown

https://g0v.hackmd.io/@cofacts/rd/%2FcJFFXVzgT4OFT6bBLtulGg


## Twitter birdwatch / Community notes

:::info
- Previous discussion: https://g0v.hackmd.io/LpBtA5-CT-m0XmlqpsdWEQ#Case-study-Twitter-birdwatch
- Updated research doc: https://g0v.hackmd.io/@cofacts/rd/%2FoK1F5q4eRV2IhGM-8ULTdQ
:::

- 網站資訊結構調整？ https://g0v.hackmd.io/@cofacts/HJ_O1Xhhs
- 大家一起 join community notes
    - 對 CBBWorld1 寫 community notes?
      - 存檔 https://web.archive.org/web/20230208052951/https://twitter.com/CBBWorld1
    - 但我的申請也還沒過⋯⋯
    - Admit by country https://twitter.github.io/communitynotes/join/
        - 今年 1 月才剛開某些國家 https://techcrunch.com/2023/01/22/twitter-is-now-accepting-community-notes-contributions-from-four-more-countries/
    - 還要累積 rating impact 才能解鎖撰寫 note 功能
        - https://twitter.github.io/communitynotes/writing-ability/#unlocking-writing-ability-for-the-first-time

## Website preview

:::info
Previous discussion: https://g0v.hackmd.io/@cofacts/meetings/%2FiGqCnbuoQfKlZLTNEyM3dw
:::

https://g0v.hackmd.io/@cofacts/rd/%2Fgu_hAI6tTeaeBuNUgGpq-g

## 大松籌備

- Good first issue
- Announce discord channel
- Other things?
  - Media indexing? Website Preview?
  - 更新網站 / impact report

## 下週開會 / 提案
- 想到週二 [name=bil]
- OK

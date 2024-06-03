---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240603 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO hub 出席： bil, mrorz, nonumpa
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## 小聚檢討
小松果：https://g0v.hackmd.io/9yeDnDJqQTe7CklA7pwuEA

- 椅子架不能放超過數量的椅子
  - 一邊 8 張，架子只能放 16 張
  - **剩下的靠牆**
- 杯子洗好可以放外面
- 桌椅擺放方式：
  - 見小松果照片
  - 桌子 3x3、平行於長邊
  - 一個桌子放 4 人，9x4=36 椅子
- 直接用 Airplay 很順
  - 一開始請大家連到 Cofacts，所以場地 wifi 很順
  - 不知道為啥變慢，以前應該可以撐比較多人
  - 額度也沒爆
- 上限 36 人，報名 35 人，事前有寄信不能來的 3~4 人
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
  - 16:18 monitor 有回報 site 短暫 520
- 17:54 ~ 17:57 針對 /article/2cawqaqh128pl 攻擊
  - 17:55 monitor 回報 site 短暫 520
- 18:01 ~ 18:12 針對 /article/2cawqaqh128pl 攻擊兩波
- 18:20 好像有一波隱形攻擊，僅部分被 Cloudflare 辨識，彈導致倒站
  - https://drive.google.com/file/d/1ZziuFMJQ_xah2kJL_MygF5qBG-Kuo-0P/view?usp=drive_link
  - Traffic https://drive.google.com/file/d/1BOKc_1BeozePrPQpUtmm0VOiYpGDCpNy/view?usp=drive_link
  - 都不是在台灣 [name=nonumpa]
  - 一台電腦同時打好幾次 [name=nonumpa]
    - https://drive.google.com/file/d/1O9gLbOYY3Pov8LGQ13-wtP1gqXs1fbJL/view?usp=drive_link
  - 一次 web request 會觸發好多 API [name=nonumpa]
    - 可能是用真的瀏覽器打的 [name=mrorz]
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

### Mitigation

把 site-zh 也改用 CloudRun?
- 不會因為 site 吃滿 linode 記憶體而倒站
- 用 Cloudrun 內建 domain mapping
  - 據說有 [latency issue](https://cloud.google.com/run/docs/issues#latency-domains)
  - 但 site-ja 好像還好？
- 切換 DNS 需要數小時
- 放一週看 $$ 花多少

新增 country rule? rate limit?
- 通過 waf 的 case https://drive.google.com/file/d/1ruhBxCAdz_jF30p3FFdp1cTLXsrmdxLJ/view?usp=sharing [name=nonumpa]
- 攻擊者 1 秒打 10 次
- 我們開 10 秒打 10 次，1/10 速率 [name=mrorz]
  - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8a8fcc8d0b96a5f21f58f8dbe4dbf057.png)
  - 手動測試，沒有觸發
  - 小聚的時候可能觸發，但也就是 managed challenge 而已


## CCPRIP

### [Infra] Migrate to Cloudrun
> https://g0v.hackmd.io/BRsJOevWSbyUMBSZEVVWrA#Phase-1-rumors-site-amp-rumors-line-bot-%E4%B8%8A-Google-cloud-run

- 202309: Staging & Production EN, JA sites migrated to Cloudrun https://g0v.hackmd.io/ulv1SGtBRWmhxnE9Lpv9TQ#Infra-Migrate-to-Cloudrun

#### Cost analysis

##### By SKU
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8907f9649db946c337c1905e4138057f.png)

- 80% of cost from CPU allocation time
- 10% of cost from outbounding traffic

##### By component
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9bfaaa4103da7e63937f5629f401e52a.png)

- Mostly by site
- In 2024 Jan I put the min instnace of line bot to 1

##### By env

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dab790c16aaa1c57159dfa05901bdccc.png)
- 80% production
- 20% staging

##### By language
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e5a0ec2f47263ac0367afc6f7da6fcdd.png)
- 50% EN
- 25% JA
- Not sure where the tw traffic comes from, zh.cofacts.tw is not used anywhere......

#### Prediction


Traffic: https://drive.google.com/file/d/1jC0GwXzZj5HTfVNwVQa1rIA16v_Ci6Ap/view

- EN: $30 USD / mo
- PV to cofacts.tw is roughly 2.6x of en.cofacts.tw
- Assume TW cost: 30*2.6 = 78 USD / mo

### [Comm layer] 逐字稿 API

Ronny API results https://docs.google.com/spreadsheets/d/10xfkOZpGJ-9vIvoYziEkD1lZETWMbBLDT-NABdQ8H_g/edit#gid=69740903
- May need tuning language
- 排隊可以到 4 分鐘
- https://g0v.hackmd.io/wkx286lmTDaFUpgRhnUawQ#WhisperX-by-Ronny-Wang
- Maybe can use to reduce hallucination https://g0v.hackmd.io/aUgKwPUaTPeVLZbcpyxe3A#Comm-Whisper-hallucination
- Dify workflow for fixing Whisper hallucination
  - Index 文章時，應已有 whisper 結果
  - Input: whisper 結果、URL
  - Ronny's WhisperX --> 把兩者丟去 chatgpt 合併 --> 打 API 更新逐字稿


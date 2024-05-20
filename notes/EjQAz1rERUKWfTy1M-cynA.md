---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240520 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO hub 出席：bil, mrorz
- 線上出席：nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## CCPRIP
### [Op] Transcript spam

Removed cases [last week](https://g0v.hackmd.io/fSJ-OU9cRKSLxENOi9Z4VQ#Op-Transcript-spam) - https://github.com/cofacts/takedowns/blob/master/2024/0520-transcript-spam.md

### [Op] 垃圾訊息反制
> https://g0v.hackmd.io/um7DyY_ESbu2LL78kLw3pg?view

本週沒有進度

## 20240514, 20240519 DDoS 攻擊

> Recorded to: https://hackmd.io/i0GcWSSVQNeDQ_OBebyk6Q?both#20240519-DDoS-attack
>

### Before 5/14

5/9、5/12 Received same emails twice from the same address
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a7bbf9af3b10238ea0f91b4e77c7c3a7.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_208ad6d8f70106d00be1c00f11d82985.png)

> 這次被攻擊的網頁，前幾天我們有收到來信檢舉二次詐騙
剛才一查 email 發現，根本就是詐騙集團寄來的信。
> [name=mrorz]

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_48d5d01aa2a215d3b71f6a27b7a17ad1.png)

> 結果我幾天前有回那個 zhenghe18168 Cofacts 這裡的處理方式
> 等於是把 honeypot 跟他們說了 ._.
> [name=mrorz]

### 5/14 DDoS

Time
- 17:08 health check report: all services offline (API, line bot, website)
- 17:20 attack stopped
- 17:26 recveived another email from different address but using the same terms, thus should from the same person
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d62a6d62495b97f6603c54a11075669f.png)

Cloudflare report
https://drive.google.com/file/d/1XkD4o4l95iqUKf8AVHzeODlK8MhAMJBa/view?usp=drivesdk
- DDoS requests: 12.82M
    - 1M req / min, QPS = 16K
- Attack method: rapidly accessing the same page using different IPs: cofacts.tw/article/2v60p2lt2jmdx
-  攻擊可以判斷為寄信者，希望將此網頁下架

### 5/15 Cofacts FB fan page received messages

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_12d037c419030954f1a922d04ff62b99.png)

[Sender profile](https://www.facebook.com/profile.php?id=61554300789951) ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d98f9885692387bfc19bd583efe87c22.png)

### 5/18 DDoS

Time
- 17:16 Attack start, Cloudflare starts blocking requests
- 17:30 health check: all service timeout (API, website, line bot)
- 17:32 MrOrz acknowledge downtime, investigating Cloudflare, found that it's an attack
- 17:47 Setup Cloudflare WAF rule:
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f72e2baccf1f1772dc61f81b2e240761.png)
    - If incoming requests match…
 `http.request.uri.path contains "/article/2v60p2lt2jmdx"`, take action: [Managed challenge](https://developers.cloudflare.com/waf/reference/cloudflare-challenges/#managed-challenge-recommended)
- 17:54 Website starts working
- 18:24 health check: all services response 520
- 19:09 MrOrz acknowledge downtime; found that the attack target switched to cofacts.tw/article/1rfvth8iy4fnc
- 19:16 MrOrz turns on I'm under attack mode
- 20:06 MrOrz finds out that service gets back by itself
    - Probably because site-zh restarts itself every 30 minutes at 0 & 30 min of every hour?

Cloudflare report
- Full https://drive.google.com/file/d/10bx6J1HD_IHi3rC_x0ckNDUOK_KFYI53/view?usp=sharing ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_674745a445d9d5ac4a932d2a636e4069.png)
- 17:00 ~ 17:40 https://drive.google.com/file/d/11ZqlfDKftAWi96szEW1UhNJdaeoIdDbQ/view?usp=sharing ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_80782806ec401a849a10ff6263627e37.png)

    - Managed by Cloudflare DDoS detection 
    - DDoS requests: 15.32M, 24min; QPS=10.6K
    - Attack target: `/article/2v60p2lt2jmdx`
- 17:45 ~ 18:15 https://drive.google.com/file/d/1vozVBEwMhJlEz2kVf_h2ICx_om8yDCf_/view?usp=drive_link ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_34a60dc5da94847681a05bb6e480be9d.png)

    - Contained by Managed challenges + DDoS block 
- 18:15 ~ 19:15 https://drive.google.com/file/d/1RVGjViKQiu45BCzWoRaHbaiTrGzXNtmo/view?usp=drive_link ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3fd99dfcc18aefb8a7369fa2ae5bad64.png)
    - Attack switched gear to attack `/article/1rfvth8iy4fnc`, Service down 
- 20:13 ~ 20:20 https://drive.google.com/file/d/1QMTrK9gM4nLGQKCVHCXCcFkeBx3aGrOT/view?usp=drive_link ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_50cd5d2589a0f4302932716c2d4d27db.png)
    - Peak 1.5M / min; QPS: 25K (highest today)
    - No downtime triggered

### Mitigation

- Go to Security > Event to see what page is under attack
- If a single page is under attack, go to WAF > "Visiting certian page" action > add link
- Let's add all articles in scammer's email

## 5 月開會時間

- 5/27 線上 only, 時間相同

## 小聚籌備

- 確定是 6/1

----

- [x] 日期：6/1（六）
- [ ] 食物：馬來西亞土產
- [x] 場地：NPO Hub Foundry（大的那間）
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
  - 推播日：5/21 推播
  - 推播日之前：新北志工優先報名
  - 目標：雙北
- [x] KKTIX: https://cofacts.kktix.cc/events/cofactseditor42
- [ ] 誰會來呢：bil, mrorz, nonumpa
- [ ] 記得帶：貼紙、環保杯
- [ ] LINE 文案：
台灣中央山脈龍脈要毀風水了嗎？老百姓或私人公司會被定罪藐視國會嗎？社會紛紛擾擾，看到可疑訊息從四方湧入，動手破解假資訊的機會來了，Cofacts志工培訓與查核工作坊就在週六，你就是改變社會的正能量。
時間 06月01日 （六）14:00-17:00
地點：台北NPO聚落 / 台北市中正區重慶南路三段2號2樓
免費活動，會很準時開始，請記得攜帶筆記型電腦或是平板方便作業。
- [ ] VOOM 發文


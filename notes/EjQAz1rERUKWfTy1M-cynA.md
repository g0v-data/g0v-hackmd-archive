---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240520 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## CCPRIP
### [Op] Transcript spam

Removed cases [last week](https://g0v.hackmd.io/fSJ-OU9cRKSLxENOi9Z4VQ#Op-Transcript-spam) - https://github.com/cofacts/takedowns/blob/master/2024/0520-transcript-spam.md

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
- 17:10 Attack start, Cloudflare starts blocking requests
    - 
- 17:30 health check report: all service timeout (API, website, line bot)
- 17:32 MrOrz  acknowledge downtime, investigating Cloudflare, found that it's an attack
- 

Cloudflare report
https://drive.google.com/file/d/10bx6J1HD_IHi3rC_x0ckNDUOK_KFYI53/view?usp=sharing


### Mitigation

## 5 月開會時間

- 5/27 線上 only, 時間相同
---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240617 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

### :eye: Under review

## CCPRIP

### [Infra] DDoS defense

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_757feb026f122c0f63663a8417e8c6da.png)

- 6/11 13:00~14:00 https://drive.google.com/file/d/1u3raRyP3wdqYdyyvPLVRRk5qXWQY18oi/view?usp=drive_link
    - 5.66M actions
        - 2.86M to /article/cipt3xcuvg7v
        - 2.76M to /article/8r58v48gkly1
    - 5M by HTTP requests from known botnet (signature #1)
    - 0.3M by Challenge foreign non-bot access
- 6/12 17:00~18:20 https://drive.google.com/file/d/1XM491u8yaf4i4RJZF6Wg5-kIiGYSOIAE/view?usp=drive_link
    - 14.77M actions
        - 10M to /article/CYLTyY8B3RbBUEe29Ws9
        - 3M to /article/8r58v48gkly1
        - 1M to `/` ==注意== ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d7596ff8199444a5dcadf62ee0cfae1d.png)
            - Block by HTTP DDoS
    - 9.65M by HTTP requests from known botnet (signature #1).
    - 3.77M by HTTP requests with unusual HTTP headers or URI path (signature #55). 
    - 0.88M by Challenge foreign non-bot access
- 6/14 17:00~17:30 https://drive.google.com/file/d/1du37sCTH2huouDBZsHdhC8t0er06-bIT/view
    - 5.64M actions
        - 2.6M to /article/sm4w33x13eri
        - 2.26M to /article/1hzn0t7mn2eq4
        - 0.8M to /article/CYLTyY8B3RbBUEe29Ws9
    - 2.78M by HTTP requests from known botnet
    - 2M by HTTP requests with unusual HTTP headers or URI
    - 0.65M by Challenge foreign non-bot access

#### Current rule CSR
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ea45533d8269e3d1ba681870ea903941.png)


### [Comm] AI assisted reply

Dify

### [Comm] Rewrite transcript

Dify

## 聯絡事項

### 訛稱是同樣帳號

> https://docs.google.com/spreadsheets/d/1q-iMJ9tZtoyHNfwInAb3z-eIg2x4-w1yp7XGTiaLB-w/edit?resourcekey=&gid=1583640334#gid=1583640334&range=K1235:K1237
> （workspace only) 

過往 CIB 調查：https://g0v.hackmd.io/ndNDmEkiSHyTRMOEIy2q2Q （workspace only)

### 下架
https://cofacts.tw/article/JPe4WI0BAjOeMOkl4Lpz
https://cofacts.tw/article/mvZ_fYwBAjOeMOklVKvx


### 詭異
https://cofacts.tw/article/19xo84c6ndn1k
https://cofacts.tw/article/sm4w33x13eri (被 DDoS)
https://cofacts.tw/article/1hzn0t7mn2eq4 （被 DDoS）

Related replies: https://cofacts.tw/reply/uXFAG5ABd3gcY0LpuUCp

### 165?

> Last discussion https://g0v.hackmd.io/DSuREu46QbWI38ITq9IlrQ#Honeypot-to-165
> 忘記結論⋯⋯

- 有很多二次詐騙會來打廣告
- 165 窗口？
- 有 dify 可能可以比較簡單？

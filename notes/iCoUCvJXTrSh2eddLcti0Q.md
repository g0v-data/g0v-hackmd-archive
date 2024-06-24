---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240617 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz, nonumpa, 4000
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

:::success
Can disable "visiting certain page"
:::

### [Comm] AI assisted reply

Dify

--> https://udify.app/chat/GPP7KgwM8cn778yO

Next steps
- get related article & reply
- 放進 prompt 當成 few-shot examples
    - Example: https://cofacts.tw/article/tII3zY8B3RbBUEe2gG-J 這篇有人回過，說不定 LLM 會採用

### [Comm] Rewrite transcript

Dify
Blocked by accessing media

### [Op] 訛稱是同樣帳號

> https://docs.google.com/spreadsheets/d/1q-iMJ9tZtoyHNfwInAb3z-eIg2x4-w1yp7XGTiaLB-w/edit?resourcekey=&gid=1583640334#gid=1583640334&range=K1235:K1237
> （workspace only) 

過往 CIB 調查：https://g0v.hackmd.io/ndNDmEkiSHyTRMOEIy2q2Q （workspace only)


:::success
修改過往信件重寄 --> Done
:::

### 下架
https://cofacts.tw/article/JPe4WI0BAjOeMOkl4Lpz
https://cofacts.tw/article/mvZ_fYwBAjOeMOklVKvx


:::success
1. 先聯繫[對方](https://esubank.com.tw/e%e9%80%9f%e8%b2%b8%e5%8f%8d%e8%a9%90%e9%a8%99%e8%81%b2%e6%98%8e/) 詢問是否是假冒的
2. 撰寫回應
碼掉名字、聯絡方式
回應：新型債務風暴 https://www.youtube.com/watch?v=Reiq4UmXtHg
https://www.mirrormedia.mg/story/20230515pol002 需謹慎理財

--> https://github.com/cofacts/takedowns/blob/master/2024/0618-privacy.md
:::

### 詭異
https://cofacts.tw/article/19xo84c6ndn1k
https://cofacts.tw/article/sm4w33x13eri (被 DDoS)
https://cofacts.tw/article/1hzn0t7mn2eq4 （被 DDoS）

Related replies: https://cofacts.tw/reply/uXFAG5ABd3gcY0LpuUCp

- 0 人回報，已經被刪過 [name=bil]
- 網站：把 blocked message 的 title 也拿掉
- 網站針對 blocked 訊息，相似可疑訊息也只給登入的人看
- 0 人回報的訊息 --> 不應該回應 [name=bil]
    - 會導致其他人無法蓋掉怪怪的訊息嗎 [name=mrorz]
    - 先放著不改好了
- 被 block 的訊息有 AI 回應會被搜尋到 [name=nonumpa]
    - 詐團用關鍵字搜尋到，就進來亂 [name=nonumpa]
    - 但 AI 回應會讓人更小心
    - 也是可以藏起來，只有登入的人看 [name=mrorz]

:::success
1. CIB，用回應內文撈肉粽，通通 block --> https://github.com/cofacts/takedowns/blob/master/2024/0621-cib.md
2. 改網站 title
3. 改網站，blocked article 的 related article 只有登入者看得到
:::

### 165?

> Last discussion https://g0v.hackmd.io/DSuREu46QbWI38ITq9IlrQ#Honeypot-to-165
> 忘記結論⋯⋯

- 有很多二次詐騙會來打廣告
- 165 窗口？
    - 需要有能力決策的單位 [name=bil]
    - 165 好像沒有與 LINE 合作，他們 ID 都搜尋得到 [name=nonumpa]
        - 詐騙 LINE ID open data 是警政署放的 https://data.gov.tw/dataset/78432
    - 數發部好像有要做整合 [name=nonumpa]
- 有 dify 可能可以比較簡單？

:::success
MrOrz 問數發部＆警政署
:::


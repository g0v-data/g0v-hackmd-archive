---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210512 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz
:::

## :potable_water: Release pipeline

### :star: Released to production

https://github.com/cofacts/rumors-site/releases/tag/release%2F20210507

- Tico integration
- Japanese version https://ja.cofacts.tw

### :rocket: Staging

#### :robot_face: rumors-line-bot

- [ ] [Ask user not to trust the message just yet when no reply is available #252](https://github.com/cofacts/rumors-line-bot/pull/252)
- [ ] [Dockerize LINE bot](https://github.com/cofacts/rumors-line-bot/pull/253)
    - 缺 README, automatic build 與 log drain

## [LIFF article page](https://g0v.hackmd.io/0RX4MsjRRJmBqJSKVilWMA#article-amp-reply-LIFF)

1. [x] Article LIFF 設計 https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/?node-id=3004%3A224
2. [ ] 實作 article & reply
3. [ ] 實作 feedback form
4. [ ] 實作 reply request list & form
5. [ ] 實作 related article


> 調整了一下 Article LIFF feedback form
upvote / downvote 與 reason text input 會放一起填
> 送出後會進入 summary，可回到編輯模式或展開其他人的 feedback
> Summary 高度最矮，僅用刷淡底色標注使用者的選擇。這是希望使用者繼續往下捲到其他回應 or 下面的內容，以不干擾使用者繼續往下讀為主。
> 之前討論的「分頁」形式我覺得還是太複雜，會不知道點下去會是編輯還是看其他人回應還怎樣，而且會干擾使用者繼續往下讀。
> 其他人的 feedback 是 upvote / downvote 人混排
> https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/Cofacts-website-MrOrz?node-id=3042%3A2
> [name=mrorz]

## LINE bot to Docker

> 未來打算搬進跟 API、site、elasticsearch 同樣的一台主機。如果試跑起來沒問題的話，之後就能擺脫 Heroku 的 512MB / 1024MB RAM、每天抱怨 memory quota exceed、以及每個月約 45 鎂的使用費囉。
>
> 現在 Docker 版 LINE bot 已經放到 staging https://lin.ee/1QUzEX4nI 大家可以測測。
> [name=mrorz]

預計將 rumors-line-bot 從 Heroku 轉移到現有 Linode。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fd9e3b1ab508e316232719d1be5186dc.png)


### Chatbot error rate baseline

2021/4/26 - 30
202 errors, mostly `Request Timeout`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_492ca147a71a2c1102cd5c64612b282e.png)

2021/5/8 - 12: 37 errors
mostly still `Request Timeout`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9e2bf31db1706a91c7a984dcec1d07fc.png)

- 綠盾牌 Response time > 1 sec 就算 request timeout [name=mrorz]

### Linode server load baseline

Peak: 5/3, 使用者較多時
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5d1800e09cbc9667f776164d1131b62e.png)

Sampled date: 5/12 20:07

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fdc82759194b6f31853a73ef18a5cce6.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f9ad3c9dc5913c0238817bbde7e78837.png)

RAM ups & down probably triggered by site-zh periodic restart, which happens every hour at :00
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_62bce97a2a86bfd33eb6ed666e745ecb.png)

### Heroku LINE bot load baseline

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a411f8fb70f62bad33fc2e64b1bc5a81.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d63c8aa6670823ed7fde773ccf7b5cee.png)



### Target
0 errors after migration!

### Migration check

:::info
Moved to [20210526 會議記錄](/8VGFKx-cR8yEdKlAQ3vv5A)
:::

- [ ] `linebot.cofacts.tw` up and running
    - [ ] AWS credential for cloudwatch is working; `awslogs` is sending output to cloudwatch
    - [ ] `/` returns
    - [ ] `/liff/index.html?p=article&articleId=fq3hn0gn4z4e` works
    - [ ] log drain setup complete
    - [ ] notification cronjob added
        - [ ] `lastScannedAt` should be in Redis and available
    - [ ] long term token and all other ENV vars are done
- [ ] LINE developer
    - [ ] Switch webhook URL to `linebot.cofacts.tw`
    - [ ] Switch LIFF endpoint URL
- [ ] LINE business
    - [ ] Update rich menu cache busting

## 新的 Dialogflow 自動回覆

https://www.facebook.com/groups/cofacts/permalink/2992380564327086/

Input:

「資料庫裡有幾篇訊息，跟你傳給我的 有些接近」
「不實訊息常常會被人修改重發。請選擇比較接近的版本」

Output:
「不要學我說話。」

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cccccdda75283582ab83e822474d2a5c.png)

- Repeat chatbot phrases
- 超過 10 個字，confidence 要是 1 才行 QQ [name=mrorz]

- 下面這個就可以  [name=mrorz]
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cffcc309fb28e2ca0f2bdb65ad3b1541.png)


----

Input:
「不要學你說話？」

Output:
「你是笨蛋嗎？」

-----

Input:
「我是老虎」

Output:
https://www.youtube.com/watch?v=AvsId84Guyc

-----

### Question intent

使用者問真的假的

https://cofacts.tw/search?type=messages&q=真的還假的

https://cofacts.tw/search?type=messages&q=真的嗎？

https://cofacts.tw/search?type=messages&q=幫我查

https://cofacts.tw/search?type=messages&q=請問

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e65982aff93ed0a4fdc404c14a7ca333.png)


## 確診訊息太極鍵譜

> hackmd: https://hackmd.io/@cofacts/r1EUpWTdu

壱ノ型「足跡無用」
比對時間後發現根本不可能感染 https://cofacts.tw/reply/S6l-T3kB9w1KR1Ikb5fA
可遇不可求，但效果顯著（27 upvote, 0 downvote）

弐ノ型「不用知道」
指出足跡太囉唆，給出更簡單的圖請他看這個就好
https://cofacts.tw/reply/ralSLXkB9w1KR1IkkYnq

参ノ型「不如基本功」
通常會有 1/3 的人不滿意，但至少有 2/3 會滿意 (?)
https://cofacts.tw/reply/UKljOnkB9w1KR1IkD5DR


跟公告足跡完全反白 - 當成假的、來亂的
https://cofacts.g0v.tw/article/159qco3doxrxe

「南方澳1人.冬山1人.羅東2人.壯圍1人」
https://cofacts.g0v.tw/article/2z6shkjujo932

OOO 不要去 - 如果是真的也消毒了啦
https://cofacts.tw/article/1rttomwy5ttsx

（調整語氣：因為不是說「不要去」而是說「去過了要小心」，觀念正確）
https://cofacts.tw/article/156v6hkwdstg0




## Good design award
https://www.g-mark.org/about/?locale=zh_TW

https://www.g-mark.org/guide/2021/guide2.html#guide2-2

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1a5165855e2efe17d174b942daec521a.png)

※ 報名開始至獲獎為止所需費用的估算參考：
一次評審費 11,000日圓＋ 二次評審費 58,300日圓＋ 獲獎推廣費88,000日圓＝ 合計 157,300日圓（以小型且不使用電源的展示作品為例。）

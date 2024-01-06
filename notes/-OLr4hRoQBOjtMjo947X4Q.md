---
tags: cofacts, meeting note
---
20200226 會議紀錄
=====

> bil, mrorz, 文武, lucien, 志超
> 上次開會紀錄：https://g0v.hackmd.io/@MODl5abnQpKy6ifB4DPGcQ/Byr84JK7I
>

## 4 月台南小聚（第19次編輯小聚）

- [x] 主題：
    - 我:heart:台南
        - 主視覺：孔廟 牛肉湯
- [ ] 時間：4/18 (六) 2:00pm ~ 5:00pm
- [ ] KKTIX
- [ ] 攜帶貼紙
- [ ] 場地：會是[好想工作室](https://goo.gl/maps/MBd7jz6gDK3J3fJV9)（含場佈：1:00 ~ 6:00）
    - [ ] 茶水
    - [ ] 麥克風+插座+網路
    - [ ] 投影機
    - [ ] 延長線
    - [ ] 食物
    - [ ] 垃圾
    - [ ] Talk
    - [ ] wifi
        - [ ] Nighthawk M1 + 4G sim
        - [ ] ASUS RT-N12 Wireless N300 (2x 5dbi高增益天線)
- [ ] 誰會來呢？
- [ ] 誰不會來：
- [ ] LINE 文案

[1/29「嚴重特殊傳染性肺炎(武漢肺炎)」因應指引：公眾集會](https://www.cdc.gov.tw/File/Get/fVFJsQkfIBresjZxRxOWTA) from: https://www.cdc.gov.tw/Category/MPage/V6Xe4EItDW3NdGTgC5PtKA

:::info
已經在 g0v slack 問 Howard

- 洗手用具
- 額溫槍或類似道具
- 應變機制
    - 誰量體溫、> 幾度怎麼做、< 幾度怎麼做 etc
- 會前宣傳：透過多元管道(如邀請函、簡訊及活動網站等)向參加者進行衛教溝通
- 會中宣導：加強防範嚴重特殊傳染性肺炎與維持個人衛生習慣之衛教溝通並透過明顯告示
:::

:::success
Howard 回應說會有，三月底也會辦活動～
:::

## LINE chatbot 換 logo

檔案：https://drive.google.com/drive/folders/1nnOFuxW70m7OgGfAI3fVcB8ri2ugODki

bil
對方還沒給新的約

:::success
志超排排
:::

## 名片
orz: 明天拿貨

## 提交社群討論

與訊息毫無相關的廣告
https://cofacts.g0v.tw/article/mnq35yxixe0v#_=_


## 開發
GitHub activities
https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/WSQFB


### Invalid reply token
https://github.com/cofacts/rumors-line-bot/issues/154

PR: https://github.com/cofacts/rumors-line-bot/pull/156
要討論 Wording
Reference（疾管家）：
`非常不好意思！系統目前忙碌中，稍待幾分鐘後可以再次要求我幫你查詢`

### Polyfill
https://github.com/cofacts/rumors-site/pull/221
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b40b477db666210cd2f6879e2294075d)


### Upvote, downvote for ppl not logged in
https://github.com/cofacts/rumors-site/issues/209

> 另外，關於另一個每天會被觸發快 50 次的 error，找到原因了：應該是使用者在沒有登入的狀況下，對 reply 或 reply request upvote 或 downvote。
https://github.com/cofacts/rumors-site/issues/209
我覺得現階段就直接跳一個 alert  說請先登入就好，之後怎麼做就再看設計師如何設計？

### 新上線：Sort by latest reply

> 現在 most recently replied 已經上 production
https://cofacts.g0v.tw/articles?orderBy=lastRepliedAt&filter=solved
不過顯示上還不會有 latest reply，這個部分請跟 @lucien 討論現階段可以先怎麼做唷

### Browser stats
https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/1M

可以 filter by referrer, device & category

> 左上角兩張深藍色的表，可以點按，圖表的其他數字會更新。
例如說，如果想看 mobile, organic search (代表在手機 google 搜尋到 Cofacts 進來) 的數據
可以點 mobile, organic search 那格，等個幾十秒讓他 load，最後會得到這張圖
解讀就是
手機上透過 organic search 點進來的人，大多都是 google 進來，landing page 也大多是特定文章頁面，大概是 google 訊息關鍵字然後找到 Cofacts 的。
手機搜尋使用者的瀏覽器寬度方面，大多為 360px ~ 380px 寬，但也有 320px 的。
Organic search 使用者 Android vs iOS 約 1:1，前者大多用 Google chrome
>
> 我覺得這個表最重大的意義是
> 我們應該要採取 mobile first design⋯⋯ XD
> 至於已經登入的編輯都用什麼，這個部分要另外埋 code QQ

### Linode RAM 調整

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8687d75fecfd90215fe8dea04e006bb4)

- java: elasticsearch, with JVM set to `ES_JAVA_OPTS=-Xms4g -Xmx4g`
- https://facinating.tech/2020/02/22/in-depth-guide-to-running-elasticsearch-in-production/
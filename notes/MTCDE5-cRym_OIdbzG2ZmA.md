---
tags: cofacts, meeting note
---
20200108 會議紀錄
=====
orz, bil, 文武, darkbtf
+2 NDI (沒飲料)
+5 BBC中國 (沒飲料)

> 上次開會紀錄：https://g0v.hackmd.io/@mrorz/rkHAFzKJL
> 

## 開發相關

### Rumors-site 升級 next9
1. [x] Article list --> PR to dev
2. [x] Article page （見 API 更新）
3. [x] Reply list
4. [x] reply page
5. [x] docker build
6. [x] landing page
7. [x] 上 staging
8. [x] 上 production --> 新台幣升級
9. [x] google analytics (w/ gtag)
10. [ ] All i18n (including levels...)
11. [x] RSS feed


### RSS

PR: https://github.com/cofacts/rumors-site/pull/210

問題：大家會用嗎⋯⋯ XD 闔各言爾志？

ggm
訂閱特定關鍵字
想要訂閱我有回過的訊息的更新

orz
article reply list + filter: 我曾回過的文章
照 article-reply 時間排序

但 articleReply 是 article 下的 nested object
elasticsearch 好像做不出來

btf
說不定 aggregate 得出來
但不知道
可能可以用這個
https://www.elastic.co/guide/en/elasticsearch/reference/7.5/search-request-body.html#request-body-search-sort

:::success
Code Review!!!
:::


### 網站 performance issue

目前網站已經設定每天 12:30 會重新啟動 site-zh 與 site-en 的 docker container，但今天早上 7am ~ 11am 又是 CPU 滿載的狀況，在 11am 的時候手動重新啟動。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b9490f73da865ab2a805110f7d9eb445)

好像滿多時間花在 render `_error` 上面，原因不明⋯⋯

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_89631e21672e91cf47199ae6e0843ee6)

文武
會不會跟 rollbar 上面回報的一堆 error 有關

orz
有可能
但看起來有些好像是特定手機瀏覽器或 extension 觸發

現在回應列表會壞掉  但這是在 client side
stack trace 下有 renderToString 代表吐出去的 html 就是 error

ggm
看一下 rollbar


orz
是 production nodejs 的 ｅｒｒｏｒ：
https://github.com/cofacts/rumors-site/issues/196

:::success
先修 Rollbar 再說
https://github.com/cofacts/rumors-site/issues/196
:::


### TODOs
- 從其他頁面點進 `/replies` 會壞掉 - https://github.com/cofacts/rumors-site/issues/193
- API server & url-resolver protobuf update
- API server + highlight
- API server article reply list
- API server dockerfile revamp
- LINE bot Typescript
- LINE bot [xstate](https://xstate.js.org/docs/)

### server served LIFF 
LINE bot LIFF under same server (simpler deploy); LIFF URL + nonce (so that we can SSR sensitive data when nonce are correct)
    - ggm: 使用者不會拿到對方的 ID 吧？
    - orz: 有點難說
    - orz: nonce / csrf 每個 liff 都不一樣，這樣可以防止它點到舊的 LIFF
    - ggm：這樣之後用 server-side rendering 嗎
    - orz: 都可以。其實 liff 會帶 userid 在 query 裡，但還是要帶個 nonce 不然會被 curl 到


### 2~6 月 focus (funded items)
- Cofacts 網站：幫助編輯找出需要複查的回應與訊息
- Cofacts 網站：整合自動與協作議題標記，幫助編輯找出自己有意願回覆的訊息
- Cofacts Chatbot：告知 Chatbot 使用者新回應
- Cofacts 網站：調整網站視覺、視覺化呈現編輯貢獻


### Chatbot Token 過期

> 文武：自動更新
> 
這兩個禮拜事情比較多，預計下下次開會 update 進度


## Takedown

- 維護 takedown: http://github.com/cofacts/takedowns
- 執行刪除作業
- 相關討論：
  - slack: https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1578051717.051200
  - facebook: https://www.facebook.com/groups/cofacts/permalink/2580532028845277/

## 選舉期使用率下降問題

### 2020 大選
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_218c07a4558557a7cc75424295b90794)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0b688a6010765b30838e92dd83e4899d)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c956a07c28a841c718b619b751649278)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d13292119b105b51b9f266b9b7b6cb1d)


### 2018 大選
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0ac0aa202fd15cfc4c7a65148f5ddb35)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_073cb7846068b44b8fcfa079cf832bb8)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_73c8b7485a95c04181a4084a00e298bb)


### 觀察

- Chatbot 有效好友數是 2 倍
- 實際傳進來的訊息數差不多、找到的比率差不多、繼續選擇的比率差不多
- 使用者選擇一篇訊息之後，沒有回應的比例少一半
- 使用者選擇送出訊息的比例少近一半
    - 2018/12 LIFF 版的理由
    - 2019/? 詢問訊息來源
        - 詢問來源次數 = article not found + user selected article has no reply ~= 5300 次
        - 實際有選擇選項的 = 3125 次
        - 多一步「詢問來源」--> 60% click through
        - match 觀察到的訊息送出比例下降問題
- 提供 Feedback 的使用者減少 20%
- 2018選前一個月使用者數比前一個月 +27.9%, 但 2020 選前一個月使用者數比前一個月 -10%
    - 2018 選前有介紹
    - 2020 也有媒體曝光
- 用 google analytics "User explorer" 分析2018選前一個月使用者 user ID、與 2020 選前一個月使用者 userId
    - 2018: 7876人 (超過5次：600多人)
    - 2020: 8412人（超過5次：400多人）
    - 交集(兩次都有用 bot)：3547人
    - --> 2020 使用者裡，去年沒用過的人數：`8412-3547=4865` 人 （57.83%）
    - 可能是大家這次比較有概念，查詢次數變少

bil
因為有不同 chatbot 分流

文武
年齡性別比呢
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9dbbe3fb8e0da23540f37832f2b05eec)

2017 --> 2020
- 男多 --> 女多
- 50+ 老人變多
    - 假新聞清潔劑

:::success
問來源的步驟應該盡快改善（選後）
https://github.com/cofacts/rumors-line-bot/issues/145
:::

### 討論




## 外賓接待

### 今天：BBC interview

### 今天：NDI Victoria

### Done：半島電視台
> Subject: Al Jazeera 線上媒體採訪
 

### 未回：環球郵報
> Subject: 選舉假訊息
 

### 未回：瑞士公視
> Subject: 【代轉採訪聯繫】



## 二月小聚(第18次編輯小聚)

NPO hub - (jothon同意了key holder ronny)
2/8 (六) 1:30 ~ 5:30，廚房那間，可以小組討論，也有投影機

- 可以：MrOrz, bil, 文武, 蝴蝶
- 不行：GGM

主題：元宵

平平安安慶元宵，看著滿月，年節也終於到尾聲了。
2020，Cofacts 第一次的編輯小聚，就在02月08日星期六下午。
這次換了一個新的場地，NPO HUB！！


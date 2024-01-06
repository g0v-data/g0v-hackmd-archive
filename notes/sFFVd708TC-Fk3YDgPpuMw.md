---
tags: cofacts, meeting note
---
20200115 會議紀錄
=====

orz, bil,文武(有飲料),ci,ggm,lucien(nono)

> 上次開會紀錄：https://g0v.hackmd.io/@mrorz/HJt2rymxL
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

 https://github.com/cofacts/rumors-site/pull/210
今晚上 production?

Lucien: [GraphQL module](https://graphql-modules.com/) 不錯

### 2 月前 focus

- 從其他頁面點進 `/replies` 會壞掉 - https://github.com/cofacts/rumors-site/issues/193
- API server & url-resolver protobuf update
    - Conflict solved by HC
    - url-resolver 會加上 https://github.com/uw-labs/bloomrpc 開發教學、API 接取教學
    - 上 staging 1 week
- ~~API server + highlight~~
    - ~~https://github.com/answerfamily/answerfamily-api/blob/master/src/resolvers/Query.js#L107-L120~~
- 問來源改善 https://github.com/cofacts/rumors-line-bot/issues/145
    - 是否需要先處理 LIFF？


### 2~6 月 focus (funded items)
- Cofacts 網站：幫助編輯找出需要複查的回應與訊息
- Cofacts 網站：整合自動與協作議題標記，幫助編輯找出自己有意願回覆的訊息
- Cofacts Chatbot：告知 Chatbot 使用者新回應
- Cofacts 網站：調整網站視覺、視覺化呈現編輯貢獻

> 先把 user story & task breakdown 貼去 github？可幫助招募？

ggm
招進來再貼吧

lucien
開票跟給文件是一樣的效果

:::success
招募後討論之後再貼
:::

### Chatbot Token 過期

> 文武：自動更新
> 

我剛剛寫得差不多了
PR: https://github.com/cofacts/rumors-deploy/pull/11
~~再看看 heroku config:set 要怎麼處理~~ done
剩 cron job


## Takedown

已經完成 takedown: http://github.com/cofacts/takedowns

## 外賓接待

### 環球郵報
> Subject: 選舉假訊息
 
 done by phone

### 瑞士公視
> Subject: 【代轉採訪聯繫】

已經來過囉


## 二月小聚(第18次編輯小聚)

NPO hub
2/8 (六) 1:30 ~ 5:30，廚房那間，可以小組討論，也有投影機

- [x] 主題：
    - 元宵
        - 平平安安慶元宵。
        - 看著滿月，年節也終於到尾聲了。
        - 2020，Cofacts 第一次的編輯小聚，就在02月08日星期六下午。
        - 這次換了一個新的場地，NPO HUB！！
- [x] 時間：2/8 (六) 14:00-17:00 
- [ ] KKTIX(bil上班寫)
- [ ] 攜帶貼紙
- [ ] 場地：NPO hub 2/8 (六) 1:30 ~ 5:30
    - [x] 茶水
    - [x] 麥克風+插座+網路
    - [x] 投影機
    - [x] 延長線 (jothon 4條)
    - [ ] 食物
    - [x] 垃圾
    - [ ] Talk
    - [ ] wifi
        - [ ] Nighthawk M1 + 4G sim
        - [ ] ASUS RT-N12 Wireless N300 (2x 5dbi高增益天線)
- [x] 誰會來呢？ MrOrz, bil, 文武, 蝴蝶, ci, lucien
- [ ] 誰不會來：ggm
- [ ] LINE 文案

:::success
Lucien 出出圖
:::

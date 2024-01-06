---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210609 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20210606

Migrate to Linode!
Release SOP: https://g0v.hackmd.io/8VGFKx-cR8yEdKlAQ3vv5A#Deploy-SOP
Release 時間：6/7 1:52AM

Release 過程中發現的問題：
- 更新 Heroku 上的 production 時，遇到[新 redis client 與 REDIS_URL 不合的問題](https://github.com/go-redis/redis/issues/1343) 導致有 downtime
- 忘記設定 CORS origin for line-bot.cofacts.tw
- `JOB_QUEUE_CONCURRENCY` 若設定會使 group chat 失效 https://github.com/cofacts/rumors-line-bot/issues/260

2021/06/07 2:00AM 調整為 1 standard dyno ($25/mo)
2021/06/09 19:22 調整為 Free dyno ($0/mo)，刪除 process scheduler，但仍然與 master branch 連動，作為備援

:::success
GGM 注意帳單

- 預計 Heroku 6 月份帳單：(40*9/30) ~= 12USD 
- 預計 Heroku 7 月份帳單：0 USD
:::

## 流量 error 紀錄

### LINE

使用人數也沒有在尖峰，可能無法直接跟過去的尖峰比較
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_94a540aeb9b4919766537b620639e5c1.png)

6/7 1:52AM 切換到 Linode
6/8 00:52 `WEB_CONCURRENCY` 2 --> 3

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_eb9959ce61e7f6a0f56f242013f4259e.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_87015120402d6980d4bf6ba64394d852.png)

### Linode

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_75f515182c3eacebb9245f8a0e30fc89.png)

Sampled date: 2021/6/9 19:30
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bb6c4c3dcb02cba7a413a8d699570a4c.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_14b1b0e339f7fed847a777dba45d1798.png)

### Heroku
新的 [H31 - Misdirected Request](https://devcenter.heroku.com/changelog-items/2100)，原因不明。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1a53c783f919c23297784b64b33b6e0a.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e8175c409a664dcb3c96d80afb921741.png)

關成 free dyno 之後就沒有 metric report 可以看囉～


## Notification count issue

- 5/30 發現 notification 怪怪
    - 「當某一天有收到，之後就會一直收到 (?」「redis 裡的 lastScannedAt 被清掉了」
    - Fix: https://g0v.hackmd.io/yCJkaJJiSQmApACcVWkVNg#-Under-review pending (要改 mongodb)
- 5/31 起手動設定 lastScannedAt 並派送 notification
- 6/8 起設定 cronjob 自動跑

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e3d8cf2230545743772126ed3218196a.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_855f777f6cae11ff8f63af66af3bc9ff.png)

## Dev

### Article LIFF

https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/?node-id=3004%3A224
1. [ ] 實作 common component storybook
2. [ ] 實作 feedback form + 使用在目前的按鈕上
3. [ ] 實作 reply request form + 使用在目前的按鈕上
4. [ ] 實作 article & reply
5. [ ] 實作 reply request list
6. [ ] 實作 related article

### 實作新 profile contribution / 升級

討論：https://g0v.hackmd.io/8VGFKx-cR8yEdKlAQ3vv5A#%E7%AD%89%E7%B4%9A%E8%A8%88%E7%AE%97%E7%9A%84%E8%A8%8E%E8%AB%96

- 「使用他人回應」「按評價」還沒算分數，先算成 +1 看如何，加權以後再說 [name=bil]
    - 「使用他人回應」寫回應的人與使用回應的人都 +1
    - 「按評價」寫回應的人、使用回應的人 +1

:::success
以上面的公道值計算方式，來撰寫技術文件
預留未來計算 badge / contribution graph 所需 activity 的空間
:::

## 亂回與通知

https://cofacts.tw/article/3a68xz85ennsd

- 如果持續亂回，使用者也會一直收到通知，我覺得不是好現象欸 [name=bil]
- 這篇文章不能特別處理嗎，他有確實非協作者的群眾在維護散佈假訊息 [name=bil]
- 目標跟手段 [name=lucien]
    - 比如說目標是摺疊惡意攻擊的回覆
    - 手段是用社群投票的方式寫下此決議
- 理論上那個文章看起來是手打的對話，應該不太會被  line 使用者詢問到才對。如果其實沒人在問，只是有奇怪的人自 high 亂送回應，那似乎不用特別做太多處理 [name=mrorz]
- 如果有評價的話才通知使用者？[name=bil]
    - 正評 2 or 3 不計負評，排除按到的人 [name=bil]
        - 新的回應要比舊得更好，查的人才會收到通知，否則就不會收到通知
    - 總評價是 >= 0
        - 幫助正常回應但回的是冷門的訊息被評價 [name=mrorz]
        - 明顯來亂的狀況，也只要有一個負評就會被擋下 [name=mrorz]
        - 如果是查核組織一次回很多已經被其他組織闢謠過的舊訊息，但看起來沒有什麼不同的話呢 [name=bil]
            - 我覺得這個狀況還是可以通知使用者，不同組織的回應面向、使用的闢謠手法可能不同，讓使用者接觸新回應來判斷是好事情 [name=mrorz]

:::success
掃描要回的訊息時，過濾掉「新回應是負分」的狀況 -- 開票 https://github.com/cofacts/rumors-line-bot/issues/265
:::

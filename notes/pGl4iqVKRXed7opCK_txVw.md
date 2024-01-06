---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220420 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz, nonumpa
- 線上出席：cai
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API

- https://github.com/cofacts/rumors-api/releases/tag/release%2F20220414

#### :robot_face: rumors-line-bot

- https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20220414

## 新 comment page 流量

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6d63b1ff69e072700b5737ba9cde15cd.png)


## 送出訊息流程是否使用 quick reply

原訂 wording: https://g0v.hackmd.io/eo8NM1VGQ7qxaamBZXRPtA#%E9%80%81%E5%87%BA%E8%A8%8A%E6%81%AF-wording

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c5256a816e5d22bb172e03e875b911f2.png =x500)

優點
- 比按鈕不佔空間
- 按了之後就消失，繼續流程
- 簡化處理邏輯
    - 不過現況所有 button postback 也都會檢查 sessionId，如果新傳了訊息進來，舊的按鈕也會失效，不會有太大問題

問題
- 「回報此訊息」還是按鈕形式，使用者還是有可能按到失效按鈕
- 電腦版不會顯示 quick reply
- 手機版跳出對話後再進入對話視窗，quick reply 不會自動出現，要稍微捲動才行
- 沒看到 quick reply 時使用者有可能會想要用鍵盤打字回覆，反而要處理鍵盤打字回覆的事件

---

- 疾管家：輸入的不是 quick reply 就再問一次 [name=nonumpa]
    - 等於放棄桌面版 [name=mrorz]
    - handleInput 也會需要修改才能做類似的行為 [name=mrorz]
- 用按鈕多佔點空間有什麼問題嗎 [name=mrorz]
    - 捨棄桌面版 cost 有點高 [name=nomumpa]

:::success
Conclusion: 改回按鈕
:::

## 廣告貼文者登入方式

> 感覺可以看一下這些廣告商是用什麼方式登入的
> 「Google 登入」門檻好像比較低，如果大部分是 Google，也許可以考慮把它移除或隱藏？
> 之前有拿一些廣告訊息 google 過，發現奇摩新聞、方格子都有同一人的足跡，但看起來是 email 被盜，不肖人士拿去利用了 [name=nonumpa]

- 拿被舉報的文字去 google 發現同一人足跡 [name=nonumpa]
- 奇摩只有 google 登入，google nickname 完全一致，名字看起來是老人，像是被盜

https://docs.google.com/spreadsheets/d/1TE9PSNGDPGhNV04FG44Z_qnXMJ6RHXFTwlzIZzmdzRI/edit#gid=0

- Google 最多詐騙，但學生只有 google [name=mrorz]
- 如果我們藏起來，放到秘密網址，現場跟大家說這個秘密，或許可以 [name=nonumpa]
- leak?
    - 試了幾個都沒被 pwned
    - 應該是詐騙集團自己創的 google 帳號
- 整體的創帳號使用的是？[name=bil]
    - 要另外處理
- honeypot 數據
    - lastActiveAt 比 blockedReason 日期晚，應該是有作用 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3446bfa37ce5a5f05e7407a64753c241.png)
- spam 頻率
    - 先把 google 藏起來? [name=bil]
    - 之前每天都有 report，最近一個禮拜一次就還好 [name=mrorz]

:::success
先找出整體創帳號的使用數據
要考慮日期
如果 google 不多 --> 可考慮藏到特殊 URL 後
:::

## Multimedia migration 事項

- Migration https://github.com/cofacts/rumors-api/pull/273
    - 先在 staging 測
- Image migration: 到時候一個檔案一個檔案用 curl 呼叫 `CreateMediaArticle`
    - Image URL: ngrok + local 起一個 simple http server 來 serve image file

## 5 月小聚籌備

- [x] 時間:
    - 5/7 母親節前大家可能有節目
    - 5/15 (日) 大家可以
    - 第二志願 5/21 (六)
- [ ] 主題：
    - ？？？
- [ ] 場地：
    - [NPO Hub 2F 影響力工場（30人）](https://g0v.hackmd.io/@jothon/NPOHub-rules)?
- [ ] 食物 
    - 疫情期間不鼓勵
- [ ] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Keyholder 介紹場地
        - 2:20 - 2:40 介紹 mission 1 -幫其他查核者評審回應
        - 2:40 - 3:00 進行評價 (20則)
        - 3:00 - 3:30 休息、自我介紹、交流 
        - 3:30 - 3:50 介紹 mission 2 - 寫回應
        - 3:50 - 4:30 進行回應（1則）
        - 4:30 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：北北基桃
- [ ] 事前產生 spreadsheet 25 人分工
- [ ] KKTIX：
- [ ] 誰會來呢：mrorz, bil, nonumpa
- [ ] 無法來：
- [ ] 做圖：用 Figma 做 [name=mrorz]
- [ ] LINE 文案


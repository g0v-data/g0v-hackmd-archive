---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220302 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz, nonumpa
- 線上出席：kukka
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: rumors-line-bot

- https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20220224

## 群組功能檢討

### 群組使用率

加入狀況
2021/11/15 故障前
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4c3909f01a13de0a5b7f3081b1e09062.png)

2022/2/24 修復後
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_22ffea3108d91af805d88c52d9751015.png)

Queue 數字 / 2022/3/2 中午
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_efe717ccd57dee188ccc84db4400da14.png)

### 回應與紀錄邏輯

https://github.com/cofacts/rumors-line-bot/blob/master/src/webhook/handlers/groupMessage.js


- Document title = 文字
- Custom dimension 1: message sounrce 'user' | 'group' | 'room'
- 字數需要大於 10
- 只要有 article found:
    1. 📡 Search hit: `UserInput` / `ArticleSearch` / `ArticleFound`
    2. 📡 每一篇 Event：`Article` / `Search` / article ID
    3. 最像那篇的 string similarity 須大於 0.95
    4. 最像的那篇必須有 valid category
    5. 📡 Top article valid: `Article` / `Selected` / article ID
        - 這個也會被 API 的 [GA 數據 pickup](https://github.com/cofacts/rumors-api/blob/master/src/scripts/fetchStatsFromGA.js#L68)，算在 LINE 查詢次數裡
    6. 過濾是否有 valid reply (replycount <= 2 || rumorCount >= 2/3 replyCount、標記為謠言的那篇回應讚數要大過標記為不是謠言的)
    7. 📡 Has valid reply: `Reply` / `Selected` / reply ID

### Event 數字

https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/Fuy6B

2021/11/15 故障前
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a4dda9106a869a57e206aa79f0b817f5.png)
- Valid article rate = 21772/108908 = 20%
- Valid reply rate = 3394/21772 = 16%

2022/2/24 修復後
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_963cf5a93556e00e19ed1b228f87bfe0.png)

- Valid article rate = 546/2348 = 23%
- Valid reply rate = 72/546 = 13% 

### Wording

列出相似文章？
- 「說到「⋯⋯」，之前有長得滿像的訊息在 LINE 上流傳，或許會帶給大家不一樣的想法唷！」
- 選擇文章後打開 Article LIFF，不在發話佔用群組的討論空間
    - 不會把回應文字 show 出來，沒辦法直接看是個問題，但也比較省空間 [name=mrorz]
- 跳 LIFF 會有人有疑慮，也有人會覺得複雜 [name=bil]
- 如果 95% 以上的話 chatbot 跟現在一樣插話，但如果是 60% 這種，chatbot 因為不確定所以就讓使用者可以選文章 show LIFF，這樣如何 [name=mrorz]
    - 有說服我，但還是把 95% 往下一點比較好 [name=bil]
- 先拉 search hit 的使用者傳送文字，來計算 threshold 如何？[name=mrorz]
    - 看數據很好，但現在非常時期（俄國侵略）還是先調整如何 [name=bil]
    - 「跨國互動」不是 valid category [name=mrorz]
    - 但還是有疫情 [name=bil]
- 為啥是 95% [name=mrorz]
    - 他也是 1:1 下自動選擇的 threshold [name=nonumpa]
- 80%? [name=bil]
    - 怕 `https://www.youtube.com/watch?v=xxxxxxxx` 的亂碼部分就佔不到 1/5 之類 [name=mrorz]
    - 要把 URL 獨立算嗎？ [name=nonumpa]
    - 但也同時有 https://cofacts.tw/article/1r72n9bh4yxp3 這種根本是同個網頁的 case [name=mrorz]
    - 群組 case:
        - 連結比對問題 https://www.facebook.com/groups/2034059996670763/posts/2260959403980820/
        - 連結比對問題 https://www.facebook.com/groups/2034059996670763/posts/2134007683342660
        - 似乎沒有因為「80% 太低」而觸發的問題回報 [name=bil]
        - 真的假的的第二層 filter 也會把 false positive 降到很低 [name=bil]
     - 之前的[討論](https://g0v.hackmd.io/Svt6MCd5T76hjDJ8UsKBnQ#Group-chatbot)

:::success
Short term: 先調降到 80%
Related ticket:
https://github.com/cofacts/rumors-line-bot/issues/245

Long term:
- 研究兩段 filter 濾掉的東西長怎樣
- Maybe 再往更不像的訊息實作 article list carousel 機制 
:::


## 送出訊息 state diagram

https://docs.google.com/drawings/d/1jnrRJG8zs8HZTjgey0FbNQjo5FpylE47_-jiPiuD3iY/edit

- Creation flow 都使用 quick reply 避免使用者捲回來按舊按鈕
- 把 `ASKING_ARTICLE_SOURCE` state 加回來
- 移除 Source LIFF
- Reason LIFF 送出理由之後，直接在 LIFF 裡道謝，不會再 sendMessage 回訊息視窗
    - 仍有舊的 upvote/downvote LIFF 與「看過的訊息」會 sendMessage

:::success
Flow: checked!
下週：對 wording
:::

## 小聚籌備

- [x] 3/12 (六) 下午 2~5
- [x] 主題
    - 戰爭與資訊
- [x] 場地：
    - [NPO Hub 2F 影響力工場（30人）](https://g0v.hackmd.io/@jothon/NPOHub-rules) 13:30 ~ 17:30
    - 旁邊（論壇、16~20 人）有基礎松
    - 走樓梯直上二樓不被門禁卡住
- [x] 食物 
    - 疫情期間不鼓勵
- [x] 時間：
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
- [x] 投放目標：北北基桃
- [x] 事前產生 spreadsheet 25 人分工
- [x] KKTIX：[29次編輯小聚](https://cofacts.kktix.cc/events/cofacteditor29)[name=bil]
- [x] 誰會來呢：mrorz, bil, nonumpa
- [ ] 無法來：
- [ ] 做圖：用 Figma 做 [name=mrorz]
    - ~~底圖直接用影響力工廠的圖 XD?~~
    - 用其他圖？ex: 這段時間的粉專用圖
- [ ] LINE 文案


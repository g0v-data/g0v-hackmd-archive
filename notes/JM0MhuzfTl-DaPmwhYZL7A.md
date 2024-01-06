---
tags: cofacts, meeting note
---

20190424 會議記錄
=====
ttcat, orz, bil, 文武, ggm


> 上次開會紀錄：https://g0v.hackmd.io/s/rJB1nENcN
> 
## 小聚檢討

:::info
當日闢謠後討論：https://hackmd.io/ZQKsam5sT4yDf0yOoduxfw
:::

### 貼紙補償
名單看KKtix 人都有報到
 * 小狗小豬各50張 (Lucien給圖?)
Caroline 
Lillian
Paul 
文武
Lucien （我說那個小貼貼啊）
Cindy 
Andy 
嘟嘟
慈
韋婷 
Michael 
ggm 
bil 
orz
4000

### 闢謠送貼圖
 * 是時候檢查檢查有沒有新的200了

（已經發文）

## 新功能貼文

### Downvote 理由
- 顯示 Downvote 理由：https://github.com/cofacts/rumors-site/pull/159 by leanne
- 詢問 Downvote 理由：https://github.com/cofacts/rumors-site/pull/158 by jihchi

:::success
待寫文案 + 出圖
:::

## 理由檢討

From https://g0v.hackmd.io/s/rJB1nENcN#%E4%BB%8A%E6%97%A5%E8%A8%8E%E8%AB%96%E7%B4%80%E9%8C%84

1. 文武提案：隱藏只送一次且沒填寫理由的訊息
2. bil 提案：提供方法來標記個別使用者「不用傳理由」，用於線下活動，降低高濃度浸潤假訊息的人傳訊息進來的門檻

MrOrz:
小孩才做選擇，大人就是兩個都做。
bil 提案也會需要文武提案「讓每個人都能不填理由」增加回報率，才能讓訊息更快進入大眾視野（盡快達成有 2 人以上回報）

## 能推播的新功能

:::info
上次討論：
https://g0v.hackmd.io/s/rJB1nENcN#%E8%83%BD%E6%8E%A8%E6%92%AD%E7%9A%84%E6%96%B0%E5%8A%9F%E8%83%BD

- LINE bot server connect to database, 獨立於 cofacts API，保持 client 獨立性
- 一個 LIFF: 列出所有這個 user id 傳過、有建檔的訊息，以及回應狀況，還有已讀未讀狀況
- trigger menu
- cron job 產生 push notification
  1. 知道哪些 article id 要查
  2. 跟 cofacts API 要資料
  3. 實際去 push message
- nice to have: 任何新回應都通知
:::

### cronjob 邏輯

1. 從 redis 取得上次 cronjob 啟動的 timestamp
2. 去 Cofacts API 列出所有在該 timestamp 以後才新建立、且未刪除的 `ArticleReply`
3. 由 2 整理出 list of unique, updated article ids
4. 從 user <> selected article 關聯表，找出要通知的對象 (list of unique users to update)
5. 使用 [multicast API](https://developers.line.biz/en/reference/messaging-api/#send-multicast-message) 告知使用者「之前的訊息有回應囉」導引使用者點開 LIFF
6. redis 紀錄這次執行的 timestamp 

### LIFF 顯示邏輯

- 從 LIFF API 取得 user id；持 user id 向 LINE bot server 查詢新的 API，得到自己查詢過的文章列表
- 文章列表，包含：
    - 時間
    - 文章內文節錄（點擊時進入 cofacts、紀錄「已讀」）
    - 回應數（新的數量）
- 點按 LIFF 會傳訊息進 Cofacts chatbot，chatbot 列出回應列表供使用者點按，進入 `CHOOSING_REPLY`；若只有一則回應，自動 `skipUser`
    - 這樣使用者才能在 LINE bot 內按「有用沒用」回應
    - 在 LINE bot 內比在 LIFF 內方便轉傳
    - 回應內仍然有文章連結，使用者如果真的要進網站，也不會沒門路
- 顯示上次 cron job 執行日期（redis 內 timestamp）

### user <> selected article 關聯表 insert 時機

- 傳訊息、資料庫沒有、填寫理由送出後
- 傳訊息、選擇一則資料庫訊息，但該訊息沒有回應。 (沒填理由也算)
- 傳訊息、選擇一則資料庫訊息，有回應。


### 相關 API quota

Send multicast message, LINE official accounts

- 100,000 requests per minute
- 2,000,000 recipients per minute

### DB schema

#### userArticleLink

紀錄 user <> selected article 關聯

- `userId`: LINE user ID
- `articleId`: Cofacts article ID
- `createdAt`: 關聯建立之時間
- `timing`: 第一次送出 or 尚無回應 or 已有回應
- `readAt`: 使用者已讀此訊息的時間。LIFF 內用此計算新回應篇數。在使用者點擊 LIFF 時更新。

#### Redis 新欄位：`scannedAt`

紀錄上次執行 cron job 的時間。




## GEC (deadline: 4/29)

送出前改改討論。

## Tech4Democracy case study (deadline: 5/3)

## coscup 社群軌投稿 (deadline: 5/6)
https://blog.coscup.org/2019/04/2019-cfp-open.html#g0v

> 哈囉，g0v 今年也參加了COSCUP 的社群議程，今年 g0v 社群議程原則上包含下列主題—「開放政府」、「新媒體」、「公共服務」、「開放資料」、「社會參與」和「基礎建設」這幾個大方向。歡迎各位投稿分享你今年的專案吧！
> 


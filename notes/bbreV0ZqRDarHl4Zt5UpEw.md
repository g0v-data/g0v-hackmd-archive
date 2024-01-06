---
tags: cofacts
---
[Spec] 個人資訊
=====

## 前情提要

給編輯能看到自己的成果與展示個人成果，目的讓使用者感受到切實的貢獻感與給與成長目標。


## 功能列表

https://www.figma.com/file/ajFwwef2wqv5z4ydl0PgTZ/Wireframe-Dubious-Messages?node-id=0%3A1


## 使用者分類

Cofacts 有兩種不同的使用者： Line 上的回報者、網站上的查核編輯。
為了統一全站使用者顯示方式，統一使用個人 profile 形象頁處理。

但 Line 上的回報者只有以下功能：

- 我回報過的訊息
- 我評價過的回應

並且由於 Line 無法取得使用者名稱與頭像 Profile ，所以需要使用 [假名生成系統](https://g0v.hackmd.io/7ERem43XREWJPOjjdE28SQ)，生成頭像及名字。


## 卡牌設計 

個人簡介區塊，外觀上設計成遊戲卡牌，把使用者經營成一個個成長的角色，並且在卡牌外框、底圖裝飾、用字顏色上給高階用戶可選外觀，讓使用者感受到自己的努力，可以在 Cofacts 社群與眾不同。

:::info
外觀可參考爐石、寶可夢等等對戰卡牌遊戲，同時可以考慮有可愛版風格，給跟遊戲陌生的編輯有另一種非競技風格。
:::

卡牌上需要呈現

- 個人等級
- 個人頭像
- 個人簡介
- 特殊成就 （Ex: <分類>的<年份>優秀回答者 ）
- 組織認證
- 公道值
- 查證數
- 評價他人數
- 查核被好評數
- 追蹤者數
- 編輯 ／ 追蹤功能

:::info
等級名字 https://github.com/cofacts/rumors-site/blob/dev/constants/levelNames.js
:::

另外 Line 的 user 要給一個最普通但跟編輯不一樣的卡牌設計

### 經驗值

TBD: 暫時一篇文章一點公道值。

https://github.com/cofacts/rumors-api/issues/124


陰德值XDDDD


## 成就

特殊成就

- 我是<分類>的<年份>優秀回答者
- 重要指標排名
    - 回應數第一名
    - 評價查核數第一名
    - 被好評數第一名


一般成就

使用 ｎ 值者作為門檻的成就，例如闢謠數 > n，可以做成多段成就，另如 n = 8, 13, 21...


|   成就   |   英文   |   條件   |
| ----------- | ----------- | ----------- |
| Text     | Text     | 首次闢謠    |
| Text     | Text     | 首次引用別人的回應    |
| Text     | Text     | 首次被 upvote    |
| Text     | Text     | 收到贊同的回應數量 > n   |
| Text     | Text     | 關注你的人數 > n     |
| Text     | Text     | 關注他人的數量 > n    |
| Text     | Text     | 連續回應的天數 > n     |
| Text     | Text     | 連續上站的天數 > n     |
| Text     | Text     | 曾經獲得過優秀回答者   |
| Text     | Text     | 收到的總贊同數 > n    |
| Text     | Text     | 個人總 reply Request > n    |
| Text     | Text     | 被引用的回應數量 > n    |
| Text     | Text     | 引用別人的回應數量 > n    |
| Text     | Text     | 查核回應數量 > n    |
| Text     | Text     | 為第一個人查核回應數量 > n    |

成就區塊會同時顯示：

- 已達成成就（如果是 n 值，只顯示最強的數值）
- 還未達成成就，但會告知進度

點擊更多展開成就 Modal ，列表展示所有已完成/未完成的成就列表定義及進度。


## 統計數字


被瀏覽主頁的總次數

- 查核在 Line 的被查看數
- 查核在 Line 的每日被查看數 （今天幫助多少迷茫的人）
- 每種類型的可疑訊息的查核數/比例
- 被瀏覽主頁每日次數曲線
- 追蹤者的每日成長曲線
- 被好評的查核回應排行榜
- 被引用數
- 被負評數



## 自己的回應列表 / 查核回應

自己回應的謠言與回應
```
article.articleReplies.userId == 'me'  
```

### 排序選項：

*預設

| 中文 | English | Elastic Search 定義 |
| -------- | -------- | -------- |
| *最近被查核 |  Most Recently replied     |  max(articleReply.createdTime)     |
| 最多好評   |  Most upvoted | article.articleReplies.positiveFeedbackCount     |
| 最近被詢問     |  Most Recently Asked     |  article.lastRequestedAt     |
| 最多人想知道     |  Most People want to know | article.replyRequestCount     |
| 最少人查核   |  Least fact-checked | article.normalArticleReplyCount     |

### 過濾選項：

| 中文 | English | Elastic Search 定義 |
| -------- | -------- | -------- |
| 時間區間  |  Time Range  |  article.articleReplies.createdAt     |
| 還未有有效查核  |  have yet to have a useful reply |  **filter** <br/> 沒有任何 normal articleReply 符合「正feedback>負feedback && status」  |
| 熱門回報  | Asked many times  | **filter** <br/> `article.replyRequestCount >= N (default N = 2)`  |
| 熱門討論  | Relied many times  | **filter** <br/> `article.normalArticleReplyCount >= N (default N = 3)`  |
| 回應中有「含有真實資訊」and「含有不實資訊」and「非文章」 (多選)   | ... | `article.articleReplies.replyType == ...`   |
| 主題   | Topic | https://docs.google.com/spreadsheets/d/1rw3Dzpmec-6lHgAgMPhW7ccPFzNlPp9YqpUJVxnYezw/edit#gid=484232713     |

## 自己的回報列表 / 回報補充 

自己有回報補充的列表


### 排序選項：

*預設

| 中文 | English | Elastic Search 定義 |
| -------- | -------- | -------- |
| \*最近回報 |  Most Recently asked     |  max(replyRequest.createdTime)     |
| 最多好評     |       |  replyRequest.positiveFeedbackCount     |


### 過濾選項：

| 中文 | English | Elastic Search 定義 |
| -------- | -------- | -------- |
| 時間區間  |  Time Range  |  article.articleReplies.createdAt     |


## 關注可疑訊息列表 / 關注訊息

我也想知道的謠言與回應

TBD: out of scope

## 我評價過的回應 ／ 我讚或是踩過的回應

sort article reply 最近跟最遠

### 排序選項：

*預設

| 中文 | English | Elastic Search 定義 |
| -------- | -------- | -------- |
| \*最近被查核 |  Most Recently replied     |  max(articleReply.createdTime)     |
| 最以前被查核     |  Most anciently replied     |  min(articleReply.createdTime)     |


### 過濾選項：


| 中文 | English | Elastic Search 定義 |
| -------- | -------- | -------- |
| 時間區間  |  Time Range  |  article.articleReplies.createdAt     |
| 我讚過的回應  |   |    |
| 我踩過的回應  |   |    |


## 關注使用者列表 / 追蹤中

使用者
- 頭像姓名
- 回應數
- 最近回應



## 通知 （遊戲化設計）

顯示 Banner 告知你今天拯救多少迷茫的羔羊：對應到你的查核在 Line 上被搜尋查看幾次。
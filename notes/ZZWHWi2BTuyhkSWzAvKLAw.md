---
tags: cofacts
---
[Spec] 最新查核訊息(需複查列表)
=====

## Updated
// 可能可以用點擊一次展開，第二次進入的方式 （quora）

## 前情提要

討論： https://hackmd.io/dfAkGHLCShacnOoruGxr0w?view

## 功能列表

https://www.figma.com/file/5qegqv1g0fxCYkzNz3jVA6/Wireframe-Need-to-Review-Page?node-id=0%3A1


### Query 定義

顯示已有查核的可疑訊息及對應查核回應列表，預設依照最新的查核時間排序。

Elastic Search
```
filter articles  
    WHERE article.articleReplies.counts > 0
    SORT by max(articleReply.createdTime)
```

:::info
Elastic Search DB map
https://hackmd.io/@mrorz/SyinqvMQL

Related Issue
https://github.com/cofacts/rumors-api/issues/35
:::


### 排序選項：

*預設

| 中文 | English | Elastic Search 定義 |
| -------- | -------- | -------- |
| *最近被查核 |  Most Recently replied     |  max(articleReply.createdTime)     |
| 最近被詢問     |  Most Recently Asked     |  article.lastRequestedAt     |
| 最多人想知道     |  Most People want to know | article.replyRequestCount     |
| 最少人查核   |  Least fact-checked | article.normalArticleReplyCount     |

### 過濾選項：

| 中文 | English | Elastic Search 定義 |
| -------- | -------- | -------- |
| 時間區間  |  Time Range  |  article.articleReplies.createdAt     |
| 我查核過  |  replied by me  | article.articleReplies.userId == 'me'   |
| 還未有有效查核  |  have yet to have a useful reply |  **filter** <br/> 沒有任何 normal articleReply 符合「正feedback>負feedback && status」  |
| 熱門回報  | Asked many times  | **filter** <br/> `article.replyRequestCount >= N (default N = 2)`  |
| 熱門討論  | Relied many times  | **filter** <br/> `article.normalArticleReplyCount >= N (default N = 3)`  |
| 回應中有「含有真實資訊」and「含有不實資訊」and「非文章」 (多選)   | ... | `article.articleReplies.replyType == ...`   |
| 主題   | Topic | https://docs.google.com/spreadsheets/d/1rw3Dzpmec-6lHgAgMPhW7ccPFzNlPp9YqpUJVxnYezw/edit#gid=484232713     |


--- 

And in graphql resolver

```
# in filtered aritcles 
articles.map(article => ({
    article,
    replies: article.articleReplies.filter(
        articleReply => date.now() - articleReply.createdTime < N 
    ).slice(0, K)
}))
```

目前先以 N = 3 days, K = 5 開始。


:::info
Elasticsearch 的 script in nested 可以用於 filter, 但不能 sorted，導致我們只能在 resolver 做 replies 處理
:::


## 列表介面註解

- 可疑訊息希望能做能顯示 __2__ 行，最後 ellipsis。
- 對應回應希望能做能顯示 __3__ 行，最後 ellipsis。
- 可疑訊息原文能被展開，被展開前將斷行換成全形空格，緊縮排在一起。
- 對應回應能被展開
- 對應回應能直接被展開後（如果能被展開），能直接被 upvote/ downvote 
- 點擊 downvote 跳出輸入框 modal，讓使用者填理由
- 列表使用 infinite scroll 去讀取下一頁內容

> [color=#ff728c] CSS 上可能有點麻煩
> 

- 從最新查核訊息點擊到訊息頁的排版會 highlight 相關回覆，詳細待詳情頁設計，但請在 url 帶 query string 指定哪些 replies 要 highlight。
- 每一頁顯示 15 條訊息
- 回報時間 Hover 規範 https://www.figma.com/file/Hvx0OId2kGdX3ldvb0MUJY/Component-Time-Tooltip?node-id=1%3A6

### 回應標頭文案

針對回應的原案或是引用，分別用

- A 認為含有真實訊息
- B 引用 A 的查核認為認為含有真實訊息

## 成效追蹤

多少瀏覽量比例 UV / All UV

多少人直接對回應 upvote/downvote

各 Sort 被使用次數

各 Filter 被使用次數

從此頁去到詳情頁添加回覆的數量
---
tags: cofacts
---
# [Spec] 等你來答

## 前情提要

討論： https://g0v.hackmd.io/xLlqGYLoQmO9Ri-r5-w2xw?view

## 功能列表

https://www.figma.com/file/ajFwwef2wqv5z4ydl0PgTZ/%5BWireframe%5D-Pages?node-id=31%3A0

## Query

－列表使用 infinite scroll 去讀取下一頁內容


### Filter
熱門回報 && 還未有有效查核
 
```
article.replyRequestCount >= N (default N = 2)

and 

沒有任何 normal articleReply 符合「正feedback>負feedback && status == "NORMAL"」
```

(注意：「尚無articleReply」應符合上面的第二項條件)

### Sort

最近被詢問

```
max(article.lastRequestedAt)
```

### Complete body

```json
{
  "query": {
    "bool": {
      "must": [
        {
          /* 現有「replyRequestCount」filter 邏輯 */
          "range": {
            "replyRequestCount": {
              "gte": 2,
            }
          }
        }
      ],
      "must_not": {
        /* NEW: 「任何 articleReply 是 NORMAL 且正 feedback 多於負 feedback」 */
        "nested": {
          "path": "articleReplies",
          "bool": {
            "must": [
              {
                "term": {
                  "articleReplies.status": "NORMAL"
                }
              },
              {
                "script": {"script": "doc['articleReplies.positiveFeedbackCount'] > doc['articleReplies.negativeFeedbackCount']"},  
              },
            ]
          }
       }
    }  
  },
  "sort": {
    /* 現有「lastRepliedAt」排序邏輯 */
    "lastRequestedAt": {
      "order": "DESC"
    }
  }
}

```



### 過濾選項：

| 中文 | English | Elastic Search 定義 |
| -------- | -------- | -------- |
| 時間區間  |  Time Range  |  article.createdAt     |
| 主題   | Topic | https://docs.google.com/spreadsheets/d/1rw3Dzpmec-6lHgAgMPhW7ccPFzNlPp9YqpUJVxnYezw/edit#gid=484232713     |


## 成效追蹤

多少瀏覽量比例 UV / All UV

從此頁去到詳情頁添加回覆的數量
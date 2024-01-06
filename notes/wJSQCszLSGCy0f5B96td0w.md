---
tags: cofacts
---
[Spec] 篩選排序
===

Cofacts 使用 Elastic Search 作為主要資料庫，因此所有搜尋排序在還沒有導入其他預處理的機制前，只能基於 Elastic Search 做設計，此篇整理所有 Cofacts **排序**及**過濾**相關定義與介面。

:::info
Elastic Search DB map
https://hackmd.io/@mrorz/SyinqvMQL

Related Issue
https://github.com/cofacts/rumors-api/issues/35
:::


## 排序
| 中文         	| English                  	| Elastic Search 定義                   	|
|--------------	|--------------------------	|---------------------------------------	|
| 最近被詢問   	| Most Recently Asked      	| article.lastRequestedAt               	|
| 最近被查核   	| Most Recently replied    	| max(article.articleReply.createdTime) 	|
| 最多人想知道 	| Most People want to know 	| article.replyRequestCount             	|
| 最少人查核   	| Least fact-checked       	| article.normalArticleReplyCount       	|

## 過濾

| 中文 	| English 	| Elastic Search 定義 	|
|-------	|-------	|-----------------------	|
| 我查核過 	| replied by me 	| article.articleReplies.userId == 自己的ID 	|
| 還未有有效查核 	| no useful reply yet	|  no article.articleReply has(positiveFeedbackCount > negativeFeedbackCount && status == "NORMAL") 	|
| 熱門回報 	| Asked many times 	| article.replyRequestCount >= N (default N = 2) 	|
| 熱門討論 	| Relied many times 	| article.normalArticleReplyCount >= N (default N = 3) 	|
| 查核爭議 	| fact-checked controversial 	|  article.normalArticleReplyCount > N (default N = 5) && ABS(article.articleReplies.replyType[has truth] - article.articleReplies.replyType[has false]) < K (default K = 3) 	|
| 回應中含有「含有真實資訊」or「含有不實資訊」or「非文章」 	| ... 	| article.articleReplies.replyType == ... 	|
| 主題 	| Topic 	| ... 	|




### 時間區間

時間區間在不同頁面會針對不同欄位 Query

| 頁面  	| Elastic Search 定義 	|
|-------	|-----------------------	|
| 可疑訊息 	| article.createdAt 	|
| 最新查核  |  article.articleReplies.createdAt     |
| 等你來查 	| article.createdAt 	|



### 主題 / Topic

文章將會標記上主題，一篇文章對於每個主題都會標記上 true/false。
因此一篇文章可明確標記出符合哪些主題。


目前所有主題：
https://docs.google.com/spreadsheets/d/1rw3Dzpmec-6lHgAgMPhW7ccPFzNlPp9YqpUJVxnYezw/edit#gid=484232713 

## Elastic Search Syntax


### 有有效查核

```json
{
  "query": {
    "bool": {
      "should": {
        /* 「任一 articleReply 是 NORMAL 且正 feedback 多於負 feedback」 */
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
  }
}
```

### 沒有有效查核

```json
{
  "query": {
    "bool": {
      "must_not": {
        /* 「任何 articleReply 是 NORMAL 且正 feedback 多於負 feedback」 */
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
  }
}

```

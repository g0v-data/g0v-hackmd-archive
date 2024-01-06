---
tags: cofacts
---
[Spec] 可疑轉傳訊息
=====


## 功能列表

https://www.figma.com/file/ajFwwef2wqv5z4ydl0PgTZ/Wireframe-Dubious-Messages?node-id=0%3A1


### 排序選項：


| 中文 | English | Elastic Search 定義 |
| -------- | -------- | -------- |
| *最近被詢問     |  Most Recently Asked     |  article.lastRequestedAt     |
| 最多人想知道     |  Most People want to know | article.replyRequestCount     |
| 最少人查核   |  Least fact-checked | article.normalArticleReplyCount     |

### 過濾選項：

| 中文 | English | Elastic Search 定義 |
| -------- | -------- | -------- |
| 時間區間  |  Time Range  |  article.createdAt     |
| 我查核過  |  replied by me  | article.articleReplies.userId == 'me'   |
| 還未有有效查核 	| no useful reply yet 	|  no article.articleReply has(positiveFeedbackCount > negativeFeedbackCount && status == "NORMAL") 	|
| 熱門回報  | Asked many times  | **filter** <br/> `article.replyRequestCount >= N (default N = 2)`  |
| 熱門討論  | Relied many times  | **filter** <br/> `article.normalArticleReplyCount >= N (default N = 3)`  |
| 查核爭議  | fact-checked controversial  | **sort -> filter -> script** <br/> `article.normalArticleReplyCount > N (default N = 5) && ABS(article.articleReplies.positiveFeedbackCount - article.articleReplies.negativeFeedbackCount) < K (default K = 3)`   |
| 回應中有「含有真實資訊」or「含有不實資訊」or「非文章」  | ... | article.articleReplies.replyType == ...   |
| 主題   | Topic | https://docs.google.com/spreadsheets/d/1rw3Dzpmec-6lHgAgMPhW7ccPFzNlPp9YqpUJVxnYezw/edit#gid=484232713     |



## 列表介面註解

- 可疑訊息希望能做能顯示 __3__ 行，最後 ellipsis。
- 點擊條目進入詳情頁
- 列表使用 infinite scroll 去讀取下一頁內容
- Hover 時間請參考 https://www.figma.com/file/YikWPPauMnukDH0U2Nq4YS/Components?node-id=1%3A284 
- Hover 已查核Ｎ篇請參考 https://www.figma.com/file/YikWPPauMnukDH0U2Nq4YS/Components?node-id=1%3A284



## 成效追蹤

多少瀏覽量比例 UV / All UV

各 Sort 被使用次數

各 Filter 被使用次數

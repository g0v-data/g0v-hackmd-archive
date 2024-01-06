---
tags: cofacts
---
# [Spec] 搜尋結果

搜尋全站結果頁，從導航列搜尋框搜尋後進入，可以搜尋可疑訊息及查核回應中內容。

對應搜尋網址為：

```
cofacts.g0v.tw/search?type=<messages|replies>&q=<search content>
```

當 `q` 為空時，請 redirect to  `/articles`。

## 功能列表

### Wireframe
https://www.figma.com/file/ajFwwef2wqv5z4ydl0PgTZ/%5BWireframe%5D-Pages?node-id=44%3A71

### Design
https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=432%3A2019

### 搜尋內容

搜尋結果同時為輸入框，但不是單行 input ，而是可以多行輸入的 textarea，最高高度為十行。
選中 textarea 時， `Enter` 會進行搜尋； `Shift + Enter` 會進行換行。

Tab 可以切換搜尋的 scope ，同時url query string 中的 type 一起改變 messages or replies

### 可疑訊息

搜尋出現結果中會高亮標示搜尋內容，搜尋目標會有以下三種

- 可疑訊息內文
- 可疑訊息中連結標題
- 可疑訊息中連結總結（crawler 利用 [readability](https://github.com/mozilla/readability) 抓到的正文）

介面上同時對以上三個做關鍵字高亮標註。

#### 排序選項：

預設依照搜尋相關度 score 排序，欄位權重分別為：


|   Field  |  articles.text    | articles.hyperlinks.title | articles.hyperlinks.summary | 
| -------- | -------- | -------- | -------- | 
| Weigh    |    2     |   1       |     1     |


#### 過濾選項：

| 中文 | English | Elastic Search 定義 |
| -------- | -------- | -------- |
| 時間區間  |  Time Range  |  article.createdAt     |
| 我查核過  |  replied by me  | article.articleReplies.userId == 'me'   |
| 主題   | Topic | https://docs.google.com/spreadsheets/d/1rw3Dzpmec-6lHgAgMPhW7ccPFzNlPp9YqpUJVxnYezw/edit#gid=484232713     |



### 查核回應


搜尋出現結果中會高亮標示搜尋內容，搜尋目標會有以下三種

- 查核回應內文
- 查核回應中連結標題
- 查核回應中連結總結（crawler 利用 [readability](https://github.com/mozilla/readability) 抓到的正文）

介面上同時對以上三個做關鍵字高亮標註。


每一個搜尋的查核回應上，顯示超連結「被使用於幾則回應」，點擊跳出 modal 顯示所有被回應在的可疑訊息的前 200 字。

#### 排序選項：

預設依照搜尋相關度 score 排序，欄位權重分別為：


|   Field  |  replies.text    | replies.hyperlinks.title | replies.hyperlinks.summary | 
| -------- | -------- | -------- | -------- | 
| Weigh    |    2     |   1       |     1     |

#### 過濾選項：

| 中文 | English | Elastic Search 定義 |
| -------- | -------- | -------- |
| 時間區間  |  Time Range  |  article.createdAt     |
| 我查核過  |  replied by me  | article.articleReplies.userId == 'me'   |
| 回應中有「含有真實資訊」or「含有不實資訊」or「非文章」  | ... | replies.replyType == ...   |



### 空白狀態

當沒有搜尋結果時，需要顯示還任何結果，請試試其他關鍵字。

### 分頁

- 列表使用 infinite scroll 去讀取下一頁內容


## 分析 Metrics 

使用者 / 
---
tags: cofacts
---
# 訊息詳情

## 後續增改

- [已刪除回應](/dYT7zCPGQiKsTne7-kkybw)
- [最近每日被查詢次數圖表](/0kjaVlFASSyddkltqGR6Nw)


## 前情提要

https://github.com/cofacts/rumors-site/issues/243
https://g0v.hackmd.io/fRDzVwdqSduSlI-BBBK3Jg

## 功能列表

https://www.figma.com/file/ajFwwef2wqv5z4ydl0PgTZ/%5BWireframe%5D-Pages?node-id=104%3A342&viewport=-729%2C671%2C1.1285957098007202



## 可疑訊息原文

最上面顯示
> 有 N 人想知道以下訊息的真實性 (N people wants to know if the following is true)

用於給使用者明白此頁的上下文是謠言內容。

接下來，依照原本傳進來的格式顯示內文，並且有 micro browser，顯示連結內容。

### 使用者可用操作

- 我要查核 reply 
- 我要補充 / 回報給編輯 <= TBD
- 關注 follow 
- 分享 share

### 可疑訊息 Meta

- 被回報次數
- 被回報時間
- 總瀏覽次數
- 最近每日被查詢次數圖表

Spec: [最近每日被查詢次數圖表](/0kjaVlFASSyddkltqGR6Nw)

## 可疑訊息標籤

顯示 ai 標注的標籤，使用者可以建議增加或是反對

顯示同意反對比例

[訊息 Label 列表與定義](https://docs.google.com/spreadsheets/d/1rw3Dzpmec-6lHgAgMPhW7ccPFzNlPp9YqpUJVxnYezw/edit#gid=484232713) 

- Hover 標籤會使用 tooltip 告知標籤的定義


## 訊息補充留言

幫助編輯了解
- 可疑訊息的爭議點
- 可疑訊息的查核線索，包含其他人的已經查到的進度

簡稱
> 給編輯留言

--- 

提示資訊：

- 搜尋臉書或Google後，你發現了什麼可疑的地方，想給其他編輯參考呢
- 請分享你覺得訊息中的爭議點或是你查核到的相關圖片、影片以及報導資訊

#### 呈現資訊形式

- 頭像姓名
- 認為為什麼是謠言的原因/我自己的查核到的線索


從 line 回報的使用者，我們不能拿到真實頭像與姓名，因此我們會對 line 使用者用 id 創造一致性的假頭像與假名。
假名規則:
- <地名> <形容詞> <名字>
- 萬華 勤奮 金城武

同時編輯也可以對已收錄的文章寫上可疑的原因，可以當作查核接力的紀錄分享。


## 查核回應


### 撰寫新回應

1. 選擇回應類別，並提供類別檢視

- 含有真實訊息
- 含有虛假訊息
- 個人意見
- 不再查核範圍

2. 查核內容 

考慮到 Line 訊息的呈現方式，只提供以下三種輔助輸入編輯功能，並非 markdown or WYSWYG editor。

- 無序列表
  快速輸入 •
- 有序列表 
  1.
  2. 
- Emoji Picker 
  https://github.com/missive/emoji-mart

##### Question from @johnson
>如果編輯沒有框文字，按下ordered list / unordered list 按鈕，要幫他斷行然後加 • 在前面嗎? >>> Yes
如果使用者在 1. XXXXXX  後面斷行，要幫他加 2.  嗎？ >>> Yes
如果編輯框起數個段落後按下 ordered list / unordered list 按鈕，是要幫每個段落前面加 1, 2, 3 嗎？>>> No，還是只加第一個
>
> [reference]: https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP/2020-04#ts-1588142825.286100 "Slack 討論紀錄"

##### 2020/6/22 討論

- 在按下 enter 後針對 text area 內容做處理
- 邏輯可以封裝成 (`text`, `cursorPos`) => `{ updatedText, updatedCursorPos }`
  - 好寫 unit test
  - 開發較方便

#### 根據不同類別，會給於快速模板

個人意見：陰謀論、滑坡謬誤、尚無共識、個人價值
不再查核範圍：長度太短、商業促銷、聊天、意見回饋．．．

#### 搜尋

能快速搜尋使用現有回應，點擊延伸會將查核附加到尾端
搜尋有一個 filter ，能在「全部可疑訊息」、「全部查核回應」、「自己查核回應」中搜尋。

:::info

> Johnson:
>  @lucien
>  ListArticle 目前無法過濾出「我回報的可疑訊息」，但 ListReply 有 selfOnly  可以用，所以「我查核過的回應」可以做。我建議在 API 不支援的現在，暫時先拿掉「我回報的可疑訊息」這個選項。

:::

預設顯示： 我最近 10 篇回應

#### 快捷鍵
希望能有 undo 快速鍵功能



3. 參考來源

考慮到 Line 訊息的呈現方式，placeholder 提供建議，並給一個快速輸入方法


例如：點加號快速輸入

```
來源說明
» 連結網址

```

### 使用現有回應

會顯示相似度高的可疑訊息的回應，另有搜尋能查詢其他現有回應，點擊使用是將回應加到此可疑訊息


## 現有回應

### 顯示內容

<編輯者> 認為含有真實訊息

<引用者> 引用 <編輯者> 的查核 認為含有真實訊息



- 查核內容
- 參考資料
- Meta
    - 回應時間
    - 被引用

### 操作

- upvote 
- downvote 
- 複製回應跟分享

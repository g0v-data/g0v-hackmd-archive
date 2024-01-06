---
tags: cofacts, meeting note
---
20200212 會議紀錄
=====

> mrorz, bil, 文武, Lucien
>
> 上次開會紀錄：https://g0v.hackmd.io/@mrorz/r11fK2DGI
>

## 小聚檢討

bil: 超級成功沒有什麼好檢討的

小松果列表：https://g0v.hackmd.io/Yef7YTSZS5q52nLPdNgz2A
Cofacts 編輯小聚松果：https://hackmd.io/B2uBOj7HT8C1tgWuRzyoNQ

orz: 提早一個小時到場比較從容，這次太趕了
架網路＋wifi 需要 30min

## 個資事件
https://www.facebook.com/groups/cofacts/permalink/2611730099058803/

ttcat: 加上昨天的例子，聽起來如果有一個 moderate 機制，其實資料庫內還是有原始資料，只是讓前端與 API 輸出資料前會先針對特定紀錄，隱藏某些「不想在平台上公開顯示的敏感資料，但拿掉又無法搜尋比對，無助降低傳播與教育使用者」的特殊情況。

orz: 看起來是 API 輸出的時候的一層 rule-based 的過濾機制，其他不動

lucien:
可是這樣好處是什麼

orz
可以用來處理這些 complaint

lucien
可以做成一個 article --> censored text 的 mapping 簡單地替換掉

orz
如果我們以後再收兩個 complaint 而這種機制都可以適用的話
我們再實作

:::success
放置
:::

## 開發

### Carry-over
從其他頁面點進 /replies 會壞掉 - https://github.com/cofacts/rumors-site/issues/193

Corresponding tickets
https://github.com/cofacts/rumors-site/issues/209
???

https://github.com/cofacts/rumors-site/issues/208
理論上 nextjs 有 babel-preset-env --> corejs --> 應該要有 polyfill???

back button issue https://github.com/cofacts/rumors-site/issues/211

### New issues

#### "Invalid reply token" 成因
replyToken 似乎 30 秒會到期 - https://github.com/cofacts/rumors-line-bot/issues/154

Orz
終於找到可靠的重現方式：傳 OCR 字很多的文件 讓OCR處理很久

這個很麻煩，可能要自己有個 timeout 在快要到期的時候趕快用 reply token 回說
抱歉無法即時完成你的 request
之類

因為一但 timeout 發生，就再也無法回應使用者

文武
LINE timeout 的信也是這個嗎

Orz
那個好像是綠盾牌（business connect 帳號）回應 postback 的速度
如果 memory 爆炸，server 回 postback 就會慢
超過一秒還是什麼的就會噴 error

但我們應該可以超過一秒再使用 reply token 回訊息回去

:::success
文武：試著解看看
（加上 timeout 機制）
:::

#### CreateReply 不要等 url resolving，有時候還會出錯

希望 reply, articleReply 插入完之後就先 return

hyperlinks 欄位先是空的，
resolve 完再填入

client 可能透過 polling 把 hyperlinks 填回去（如果編輯還在該文章頁面）

:::success
MrOrz 明天做
:::

### Merged

- rumors-api, rumors-db, rumors-site renovate merge
    - babel 更新到 7

### 已部署

Rumors-site 轉 cluster mode - https://github.com/cofacts/rumors-site/pull/214
- site-zh: 2 instances
- site-en: 1 instance


Orz:
elasticseaerch.js (NodeJS client)
https://www.elastic.co/cn/blog/new-elasticsearch-javascript-client-released
好像有 breaking change，以後再另開 PR


### LINE bot memory issue
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d57dc19c14c35c0e65d06a0cc8253278)

Standard-1X 與 Standard-2X 一台互相切換後，
Standard-2X 上線時再也沒有 memory issue~

### 想做

#### API + UI: 編輯 Reply 功能
1. 前提：該則 reply 還沒被按任何 feedback (因為 feedback 是針對當下版本) 
    - 若被用在其他 article 則無法修改
    - 若所有 aritcleReply 與 reply 作者都是當下 current user 才能修改 reply 內文
        - 文武：這樣很複雜 UI 也要判斷
        - bil: 把回應用在其他文章的功能很少使用
3. 增加 mutation API 讓 author 修改 Reply 內文

:::success
Orz 做成
1. 被 feedback 就不能編輯內文
2. 被用在超過一個 article 也不能編輯內文
:::

#### ListArticles, ListReplies filter 增加 time range

UI 可搜尋 createdAt 或 updatedAt 或 lastRequestedAt 在某個 time range 以內的訊息 / 回應

## 設計討論
https://hackmd.io/dfAkGHLCShacnOoruGxr0w
---
tags: cofacts, meeting note
---

20190417 會議記錄
=====
am:ttcat, ggm, rock, bil
pm:lucien/文武/orz/bil
> 上次開會紀錄：https://g0v.hackmd.io/s/ryMWp8otV
> 

## 4/20 小聚

- [x] 邀請人：不會有邀請人。
- [x] kktix 
- 散佈
    - [x] Facebook fanpage
    - [x] Facebook group
    - [x] LINE bot 貼文
    - [x] LINE bot richmenu
    - [ ] 發小聚資訊的推播（等 4/11 LINE OA 整合後）--> 場地僅能 16 人，這次不推。等場地比較固定之後再推播。
- [x] 場地 - [小樹屋](https://www.treerful.com/space/15)
    - [x] 茶水（ggm 會帶水杯，另外訂大的寶特瓶的茶水）
    - [x] 沒有麥克風（小樹屋禁止使用麥克風）
    - [x] 食物（買餅乾，帶家裡剩的餅乾）

### 當日 rundown

會到的人：ggm, mrorz, bil, 文武

- 幾點到：13:00 使用密碼開門
- 桌椅：見網站 https://www.treerful.com/space/15 含工作人員共 16 人
- 延長線：場地有


### 新貼紙
 * 小狗小豬各50張 (Lucien給圖?)

:::danger
天窗囉
:::

## 新功能貼文

### Downvote 理由
- 顯示 Downvote 理由：https://github.com/cofacts/rumors-site/pull/159 by leanne
- 詢問 Downvote 理由：https://github.com/cofacts/rumors-site/pull/158 by jihchi

### 新 demography

Line bot analytics
https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/Cy2P 最下面

- 需要手動更新到 spreadsheet
- 需要標註最後更新日期

## 理由檢討

課題：放寬理由為選擇題？

註：「理由需 15 字以上」為 1/18 上線。


### Chatbot log「是否要送出？」出現次數與訊息統計

2019/1 ~ 2019/4 bot 對話記錄弄下來整理了這張表：
https://docs.google.com/spreadsheets/d/1WDVfmi5DoaIqpxJRn8URdzWE-GRD-KK2VLyitu984vg/edit#gid=1445472702 （註：對話記錄屬個資，僅內參）

表格欄位為：
1. 訊息內文
2. bot 問該訊息「是否要送出」的次數
3. 第一次詢問「是否要送出」的時間
4. 與最後一次詢問的時間
5. 最後被送出的 article id, 時間, 理由（若從未送出，則留空）

note: 理由字數 15 字以上的限制，是在 2019/1/16 左右上線

觀察：
- 最多次的訊息（ [17po8p5bc4yaa](https://cofacts.g0v.tw/article/17po8p5bc4yaa) ）第一次詢問為 2/9，但到 2/23 才進入資料庫，途中有 35 人詢問
- 有則健康相關訊息被傳了 22 次，但仍然沒有人沒有人想送進資料庫。
- 確實有擋住一些不該進來的文字
- 798 則訊息被傳進來 2 次；實際送出文章者僅 58 則（7.2%）
- 1245 則訊息被傳進來 2 次(含)以上；實際送出文章者僅 168 則（13.5%）


### 過去的相關討論
1/2 決議禁止送太短的理由 + 選擇：https://g0v.hackmd.io/s/SyN-sb8b4#LIFF-%E4%B8%8A%E7%B7%9A%E5%BE%8C%E6%AA%A2%E8%A8%8E
1/16 PR：https://g0v.hackmd.io/s/S1D8FVqf4#%E7%90%86%E7%94%B1%E9%95%B7%E5%BA%A6%E9%99%90%E5%88%B6
1/23 檢討：覺得效果不錯 https://g0v.hackmd.io/s/B1uUy3VQ4#%E5%B7%B2%E4%B8%8A%E7%B7%9A
4/3 重開討論：好像文章太少 https://g0v.hackmd.io/s/SyA8YtlKE#%E6%94%BE%E5%AF%AC%E7%90%86%E7%94%B1%E7%82%BA%E9%81%B8%E6%93%87%E9%A1%8C

### 今日討論紀錄

文武
我看 1/16 有提到說第二個就不用讓他填理由的事情。

如果改成理由可以 skip，只是講說 skip 就會送不進來。
後面偷偷做說兩個就會顯示，一個就不會顯示這樣子。

orz
如果有一個有填理由呢

文武
那就傳進來
主要就是要擋掉亂傳的

orz
那就做成，如果
- 只有一人傳進來
- 又沒有填理由
- 也沒有回應 （for old articles，避免舊資料也被濾掉）

的話就不要出現在任何文章列表裡面，即使勾選了「包含僅有一則的回應」。

lucien
所以是要調鬆嗎

bil
如果是對部分的人調鬆呢？
例如說在理由填一個固定的
之後這個人傳進來都不用填理由

例如說我在這個人面前，我就填一個固定的理由。
例如說樂齡中心、假新聞清潔劑
我覺得這個人是謠言的大戶，又沒有能力填理由
就讓這個用戶永遠不需要填理由
因為對於填理由，對於20幾歲與 6、70 歲的人來說會有不同的標準

orz
所以不需要放寬 20 幾歲的部分

bil
會覺得需要老人更多的愛與關懷
因為不想打字所以都用轉傳
這些人我不會勉強他一定要打字

bil
這種人不用多，50 個就夠了

文武
其實他還是可以送進來，只是要不要顯示給編輯看而已

orz
如果讓他可以 skip，會不會讓年輕人也不想填

文武
所以就要在 skip 時說「有可能不會送進來」

orz
如果讓老人按 skip，然後請他按確定要跳過，會很 demanding 嗎

bil
老人會覺得光是問理由就很討厭
第一次填理由會有授權的頁面，也有點嚇人
第一次加 bot 好友，也會有授權頁面

orz
如果是比鄰這個，目前還沒有想到好的實作方式

文武的提案的話，感覺要改 API 跟 line bot
API 方面可以用 flag 做，他是個 flip 過去之後就不會再 flip 回來的 flag

:::success
做 flag 提案
:::


## 能推播的新功能

ttcat
OA 只有一年，所以 pushMessage 要在一年內做出來

orz
我不確定現在這個階段是幫編輯好，還是幫使用者做功能好
像現在是選前

編輯：網站外觀、等級、profile 頁面等等，提升編輯樂趣
使用者：chatbot pushMessage

bil
幫編輯做了兩年大概就是這樣了呢
可以幫使用者

文武
如果選前有推播，感覺比較好

orz
實作的時候可以溯及既往，爬 log 判斷哪些訊息要通知
然後上線的時候發推播請他們點開 LIFF
在 LIFF 裡面列出這個人過去傳過的訊息以及回應狀況

文武
如果是以你說功能，我們不用推播就做得到
就送個訊息說我要之前的訊息

orz
menu 就好
重點是要叫使用者去點那個 menu / 傳一個按鈕給他按

- LINE bot server connect to database, 獨立於 cofacts API，保持 client 獨立性
- 一個 LIFF: 列出所有這個 user id 傳過、有建檔的訊息，以及回應狀況，還有已讀未讀狀況
- trigger menu
- cron job 產生 push notification
    1. 知道哪些 article id 要查
    2. 跟 cofacts API 要資料
    3. 實際去 push message

lucien
- redis queue (OptimalBits/bull)
- 一個 worker 定時目標去掃是不是有 push notification，把東西丟進 job queue
- worker 用 job 
跑在 k8s 上

orz
可是我們放 heroku，想說用 heroku scheduler 就好

文武
如果有新增回應的話要 push 嗎

orz
我覺得是 nice to have，可以做

但因為大部分訊息都只有一個回應，所以先做第一則回應，就能處理 80%

剛才的 LIFF 的已讀 flag 可以做成 timestamp
如果有新回應，那就更新「最新一則回應的 timestamp」

可以用掃所有 article 來實作，掃的頻率可以不用像第一個回應那麼頻繁

文武
送進來就可以有 aritcle id
只問這些 article id

orz
這個要有作用的話就是，如果掃到有回應就要把 aritcle id 剔除。
不過如果要做「已回應的文章有新回應也要 notify」可能就要靠掃文章來做

:::success
結論：
先做 push message
我先開 ticket

因為 OA 比較貴
:::

## 對外

### GEC (deadline: 4/19)
Bil -> OCF Rock -> AIT (4/19)
書懷 ->

美玉姨的提案：
- 特點：source checking 的實踐
- 需要注意：此實踐是否能被複製

### Tech4Democracy case study (deadline: 5/3)

### coscup 社群軌投稿 (deadline: 5/6)
https://blog.coscup.org/2019/04/2019-cfp-open.html#g0v

> 哈囉，g0v 今年也參加了COSCUP 的社群議程，今年 g0v 社群議程原則上包含下列主題—「開放政府」、「新媒體」、「公共服務」、「開放資料」、「社會參與」和「基礎建設」這幾個大方向。歡迎各位投稿分享你今年的專案吧！
> 


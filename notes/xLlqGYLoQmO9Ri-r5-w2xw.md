---
tags: cofacts, meeting note
---
20200311 會議紀錄
=====

> 黑卡 mrorz, bil
> ggm、Lucien、蝴蝶、志超
>
> 上次開會紀錄：https://g0v.hackmd.io/@johnson/ByAb_n24U
>

## 3/14 大松籌備

活動共筆 Note：https://g0v.hackmd.io/@jothon/g0v-hackath38n
要買很多口味的 Lays

### 誰會來

在家組
- ggm
- 文武

Workis 組
- bil
- mrorz
- darkbtf
- lucien (下午)

### 大松頁面
https://g0v.hackmd.io/@johnson/HyXMDVLBI

### Good first issue

- https://github.com/cofacts/rumors-line-bot/labels/good%20first%20issue
- https://github.com/cofacts/rumors-site/labels/good%20first%20issue
- https://github.com/cofacts/rumors-api/labels/Good%20first%20issue

### 標記作業 - postponed

- DB ready? No
- API PR review 中
- UI PR review 中

:::danger
先不要
大松那天上 staging
:::


## LINE chatbot downtime

- 3/18 移轉為 OA 2.0
- Logo LINE 還沒回說會換頭像，也不確定具體時間

### FB group / Slack 文案

### LINE bot 自動回覆

:::danger
大松寫文案
:::

【Cofacts 真的假的 LINE 帳號升級公告】

Cofacts 的 LINE 官方帳號「Cofacts 真的假的｜轉傳查證」將在 3/18 (三) 進行官方帳號升級作業，升級作業時將無法自動回應。在升級之後，功能維持不變，但我們會用新頭像與大家見面唷 :)





## Incidents

### 3/9 Disk full, website & line bot "index is read only" error

https://www.facebook.com/groups/cofacts/permalink/2634161976815615/

- 8:02 的時候硬碟已滿，資料庫唯讀
- 13:20 暫時關閉 API server 來 debug
- 最後 13:46 修復完畢。

#### 調查結果

`docker system df` 顯示各個 container 正常

```
root@debian:/var/lib# docker system df
TYPE                TOTAL               ACTIVE              SIZE                RECLAIMABLE
Images              27                  7                   7.903GB             5.63GB (71%)
Containers          7                   6                   5.344GB             151B (0%)
Local Volumes       122                 0                   45.4MB              45.4MB (100%)
Build Cache         0                   0                   0B                  0B
```

但實際上有單一 container 在 `/var/lib/docker/containers` 使用了 94GB—— Elasticsearch 的 docker container。

https://stackoverflow.com/questions/59507037/elasticsearch-docker-container-taking-all-my-disk-space-cannot-find-where

有人說是資料亂存（但發問者跟我一樣是把整個 data 資料夾 bind mount）
有人說是 swap 問題

ggm
我們不是用 docker 直接跑在機器上
這感覺跟 docker 有關

:::danger
放著
:::

#### Aftermath

- 我們的 error logger 超過免費額度，接下來到 4/5 之前如果有 bug，要仰賴大家回報才能提早發現 bug 了 QQ

#### Other issue

這個 error 每一秒會噴好幾次：

```
db_1            | [2020-03-09T05:34:52,969][WARN ][r.suppressed             ] path: /_msearch, params: {}
db_1            | java.lang.IllegalStateException: No matching token for number_type [BIG_INTEGER]
db_1            | 	at org.elasticsearch.common.xcontent.json.JsonXContentParser.convertNumberType(JsonXContentParser.java:210) ~[elasticsearch-x-content-6.3.2.jar:6.3.2]
db_1            | 	at org.elasticsearch.common.xcontent.json.JsonXContentParser.numberType(JsonXContentParser.java:68) ~[elasticsearch-x-content-6.3.2.jar:6.3.2]
(下略很深的 stacok trace)
```

:::info
Root cause 依舊不明

現在不噴了 (?)
:::

### 3/11 Website down due to high server load

> 4000 回報剛才網站進不去
> ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6d3f57ce9b7079ae9116f1af158340e2)

> Linode 報表顯示 9:40 ~ 10:05 的時候 server load 超載，原本 load 大概是 2~5 (>1 就是很忙了)
> 那段時間衝到 100

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f0c3eb76f138fe31da59ba641b7a5d71)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_63306cdd77d9443ddeaffa158790e001)

- `Java`: Elasticsearch
- `node /srv/www/b`(uild/index.js): API server, 2 instances
- `node /srv/www/s`(erver.js): Web server, 2 TW instances, 1 EN instance


:::success
Linode 升級到 16GB plan (80USD / month)
6 CPU, 16GB Ram, 320GB Storage
Do 升級
:::

### LINE bot RAM issue

3/7 6:30PM: Deploy 0d05fa47 (最新版)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2eed59aff8a9e46fd9ce73f2cb3e7fa9)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5e107a5d0fbc26025b5468e9199f18e6)

Logs: https://drive.google.com/file/d/1LoErUwFIVHRB-cYlxIeJ439_QdamAORg/view?usp=sharing


Orz: 看起來一次可以傳 6 張圖，平行處理 6 張圖，導致 Memory 超標
但 ssh 進去 dyno 看，確實是最新的 code
而且 staging 正常
```
09 Mar 2020 11:27:45.724309 <158>1 2020-03-09T03:27:45.206870+00:00 heroku router - - at=info method=POST path="/callback" host=rumors-line-bot.herokuapp.com request_id=f987e6a4-ce3e-4533-a2a1-320996511c8c fwd="147.92.150.196" dyno=web.1 connect=1ms service=5ms status=200 bytes=137 protocol=https
09 Mar 2020 11:27:46.952309 <158>1 2020-03-09T03:27:46.400480+00:00 heroku router - - at=info method=POST path="/callback" host=rumors-line-bot.herokuapp.com request_id=5eccf80a-be9b-4a2d-be8c-7f54dbda7eb1 fwd="147.92.150.196" dyno=web.1 connect=1ms service=4ms status=200 bytes=137 protocol=https
09 Mar 2020 11:27:47.849309 <158>1 2020-03-09T03:27:45.398598+00:00 heroku router - - at=info method=POST path="/callback" host=rumors-line-bot.herokuapp.com request_id=6c1b5a69-031b-41cf-bb07-81064ac80c4f fwd="147.92.150.196" dyno=web.1 connect=1ms service=3ms status=200 bytes=137 protocol=https
09 Mar 2020 11:27:47.967239 <45>1 2020-03-09T03:27:47.798721+00:00 heroku web.1 - - source=web.1 dyno=heroku.57521933.95b18a95-11e0-466d-92db-81b09bdcb0bd sample#load_avg_1m=0.93 sample#load_avg_5m=0.25 sample#load_avg_15m=0.09
09 Mar 2020 11:27:48.033374 <45>1 2020-03-09T03:27:47.798721+00:00 heroku web.1 - - source=web.1 dyno=heroku.57521933.95b18a95-11e0-466d-92db-81b09bdcb0bd sample#memory_total=585.84MB sample#memory_rss=579.59MB sample#memory_cache=6.25MB sample#memory_swap=0.00MB sample#memory_pgpgin=2838649pages sample#memory_pgpgout=2708090pages sample#memory_quota=1024.00MB
09 Mar 2020 11:27:48.358309 <158>1 2020-03-09T03:27:47.735478+00:00 heroku router - - at=info method=POST path="/callback" host=rumors-line-bot.herokuapp.com request_id=076aa867-952a-4ddb-95ca-b1f786740fae fwd="147.92.150.196" dyno=web.1 connect=0ms service=4ms status=200 bytes=137 protocol=https
09 Mar 2020 11:27:48.801309 <158>1 2020-03-09T03:27:48.145231+00:00 heroku router - - at=info method=POST path="/callback" host=rumors-line-bot.herokuapp.com request_id=a2d72a41-9b59-479e-a634-a4e6d48a9133 fwd="147.92.150.196" dyno=web.1 connect=0ms service=3ms status=200 bytes=137 protocol=https
09 Mar 2020 11:27:48.985146 <190>1 2020-03-09T03:27:48.333077+00:00 app web.1 - - Uploaded File Id: 1XIt7xKPTQpAHkmNZ0BTeZjpVdw0r4urb
09 Mar 2020 11:27:49.104146 <190>1 2020-03-09T03:27:48.445722+00:00 app web.1 - - Uploaded File Id: 1zSdno0goVEkvGahsf6Vhc7nVRdJ1dsc6
09 Mar 2020 11:27:50.518146 <190>1 2020-03-09T03:27:47.886422+00:00 app web.1 - - Uploaded File Id: 1jHVDnVvLbl2M95iyn4XDrBViJEfql31x
09 Mar 2020 11:27:51.601310 <158>1 2020-03-09T03:27:49.139194+00:00 heroku router - - at=info method=POST path="/callback" host=rumors-line-bot.herokuapp.com request_id=fedbd9a0-8b8b-4a21-90ad-c86ba7e189f6 fwd="147.92.150.196" dyno=web.1 connect=0ms service=11ms status=200 bytes=137 protocol=https
09 Mar 2020 11:27:53.718146 <190>1 2020-03-09T03:27:53.069648+00:00 app web.1 - - Uploaded File Id: 1iyTCQjOkGB3qgtJUtJYfCQlI0qOLe51v
09 Mar 2020 11:27:53.844146 <190>1 2020-03-09T03:27:53.072061+00:00 app web.1 - - Uploaded File Id: 1btnRENaGvI8mH9XGh8b39OQxaDYJLIQF
09 Mar 2020 11:27:53.844146 <190>1 2020-03-09T03:27:53.097199+00:00 app web.1 - - Uploaded File Id: 190NEtMJGUtLc-2H1OABuzEPNZFUJg4j7

09 Mar 2020 11:28:09.511239 <45>1 2020-03-09T03:28:09.080861+00:00 heroku web.1 - - source=web.1 dyno=heroku.57521933.95b18a95-11e0-466d-92db-81b09bdcb0bd sample#load_avg_1m=7.52 sample#load_avg_5m=1.81 sample#load_avg_15m=0.63
09 Mar 2020 11:28:09.629377 <45>1 2020-03-09T03:28:09.080947+00:00 heroku web.1 - - source=web.1 dyno=heroku.57521933.95b18a95-11e0-466d-92db-81b09bdcb0bd sample#memory_total=1132.49MB sample#memory_rss=872.88MB sample#memory_cache=1.29MB sample#memory_swap=258.32MB sample#memory_pgpgin=3192992pages sample#memory_pgpgout=2981469pages sample#memory_quota=1024.00MB
09 Mar 2020 11:28:09.629129 <45>1 2020-03-09T03:28:09.081396+00:00 heroku web.1 - - Process running mem=1132M(110.5%)
09 Mar 2020 11:28:09.629129 <45>1 2020-03-09T03:28:09.081517+00:00 heroku web.1 - - Error R14 (Memory quota exceeded)

09 Mar 2020 11:28:13.819296 <190>1 2020-03-09T03:28:13.208233+00:00 app web.1 - - [LOG] Timeout {"type":"message","userId":"U_7","timestamp":1583724463957,"mode":"active","message":{"type":"image","id":"11565161151380","contentProvider":{"type":"line"}}}
09 Mar 2020 11:28:13.929296 <190>1 2020-03-09T03:28:13.401540+00:00 app web.1 - - [LOG] Timeout {"type":"message","userId":"U_7","timestamp":1583724464832,"mode":"active","message":{"type":"image","id":"11565161218468","contentProvider":{"type":"line"}}}
09 Mar 2020 11:28:15.046296 <190>1 2020-03-09T03:28:14.399782+00:00 app web.1 - - [LOG] Timeout {"type":"message","userId":"U_7","timestamp":1583724465683,"mode":"active","message":{"type":"image","id":"11565161285310","contentProvider":{"type":"line"}}}
09 Mar 2020 11:28:16.767296 <190>1 2020-03-09T03:28:16.150057+00:00 app web.1 - - [LOG] Timeout {"type":"message","userId":"U_7","timestamp":1583724467598,"mode":"active","message":{"type":"image","id":"11565161448716","contentProvider":{"type":"line"}}}
09 Mar 2020 11:28:17.433296 <190>1 2020-03-09T03:28:17.144000+00:00 app web.1 - - [LOG] Timeout {"type":"message","userId":"U_7","timestamp":1583724468437,"mode":"active","message":{"type":"image","id":"11565161518092","contentProvider":{"type":"line"}}}
09 Mar 2020 11:28:24.374296 <190>1 2020-03-09T03:28:15.739733+00:00 app web.1 - - [LOG] Timeout {"type":"message","userId":"U_7","timestamp":1583724466718,"mode":"active","message":{"type":"image","id":"11565161377196","contentProvider":{"type":"line"}}}
09 Mar 2020 11:33:06.338129 <190>1 2020-03-09T03:33:05.982228+00:00 app web.1 - - [LOG] reply & context setup aborted
09 Mar 2020 11:33:22.765129 <190>1 2020-03-09T03:33:22.411547+00:00 app web.1 - - [LOG] reply & context setup aborted
09 Mar 2020 11:33:27.189129 <190>1 2020-03-09T03:33:26.493499+00:00 app web.1 - - [LOG] reply & context setup aborted
09 Mar 2020 11:33:28.769129 <190>1 2020-03-09T03:33:28.410305+00:00 app web.1 - - [LOG] reply & context setup aborted
09 Mar 2020 11:33:32.219129 <190>1 2020-03-09T03:33:29.487442+00:00 app web.1 - - [LOG] reply & context setup aborted
09 Mar 2020 11:33:32.453129 <190>1 2020-03-09T03:33:27.735900+00:00 app web.1 - - [LOG] reply & context setup aborted
```

:::info
再看看，不知道為什麼
:::

## 開發
GitHub activities
https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/WSQFB

### Polyfill size

禮拜三的時候有聊過我把 polyfill 塞進 webpack bundle 這件事
( https://g0v.hackmd.io/-x5qyf_ER-mTiECYx0GX6g#Polyfill )
我剛才用 next-bundle-analyzer 測了一下，結果在這裡：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_87111c3bd6d351969c66b9a087ea9a37)

:::success
Issue: https://github.com/cofacts/rumors-site/issues/233
:::


### Subscription w/ IFTTT Applets

- RSS <> Slack: https://ifttt.com/applets/110762028d-cofacts-replies-to-slack
- RSS <> LINE: https://ifttt.com/applets/110758381d-latest-reply-line
- RSS <> Email: https://ifttt.com/applets/26887139d-rss-feed-to-email
- RSS <> Telegram: https://ifttt.com/applets/110762597d-cofacts-reply-to-telegram

問題：pubDate 不對，無法觸發 RSS feed run
https://github.com/cofacts/rumors-site/tree/rss-pubdate-fix (缺
 API route unit tests)

### Tracking

:::success
- 埋 hotjar: https://github.com/cofacts/rumors-site/issues/236
- 先設定 displayName of important component: https://github.com/cofacts/rumors-site/issues/237
- 以後再看看要不要 react-tracking
:::

### LINE bot notification
https://g0v.hackmd.io/eIeU2g86Tfu5VnLazNfUvQ

## New analytics: 已登入使用者
https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/zJpHB
看起來已登入的編輯們，8 成的 session 用的是桌機，2 成是用手機，沒人用平板。螢幕解析度方面 1280, 1150 佔大宗

## 設計：最新回應列表
https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=0%3A1

### 最新回應列表
Mockup
https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=0%3A1

### Icons 與錊者

超
現在多了形狀，視覺上比較分得開
八角形要再微調不然會有點凹陷

「不在查證範圍」原本用黃色，但 Cofacts 主色就黃色，覺得主色用在這有點怪
所以改紫色

orz

現在還少了作者
作者會有兩種（訊息作者、連結人）
我覺得可以放右下角

另外，chatbot 上是刻意把編輯判斷放最後面，淡化編輯判斷，讓使用者閱讀內文

lucien
目前 icon 比較尷尬，會讓人覺得「這就是錯的」而不是「含有不實訊息」
比較沒有原本那種小心的感覺

超
我覺得看到「含有不實訊息」跟看到叉叉是一樣的
要小心的話，要看到「某某人覺得含有不實訊息」這種「某某人說」比較好

lucien
icon 可以放大但是可以放去背景呢
可以感受到這個是「含有不實訊息」但是可以一眼看到「誰覺得」的

超
那做成緞帶/便利貼的感覺呢

### 區分訊息與回應（回應為重點）

超
麻煩的是，這頁的主角是回應，但你又會想把回應放在第二層
會比較亂

lucien
所以想說回應的顏色比較深等等

超
可以試試看，浮水印不是很討喜，會看起來很亂
便利貼/帶子可以是紅色然後寫「XXX 覺得含有不實訊息」
是長型的
但如果要縮排的話比較難排

orz
如果是聊天視窗的「回應」呢
不縮排但用不同方匡，也能看出是回應

超
但這是列表不是聊天視窗
整齊滿重要的

lucien
顏色與緞帶都可以試試看

### 展開系列

Lucien:
閱讀全文是 for 回應，不是訊息。

超：
我覺得都要，訊息與回應都可以

L:
我覺得訊息 2 行，回應 3 行，超過就放「閱讀全文」

詳情頁面才有 reference，然後詳情頁面才有 copy button

orz
回應展開後會有 reference 嗎

bil
沒有 reference 我覺得沒有不好

lucien
我覺得放 reference 有點太多

回報幾次那些 Meta 還可以調整

超：
回報幾次與時間的部分，跟內文比誰比較重要？
現在是重要性分三層
不然會很亂

orz
啊 看回報數是「可疑訊息」（還沒有回應）的時候比較重要一些
如果是「最新查核」我會看回應文字沒錯

lucien
我的「可疑訊息」 wireframe，時間擺得不太一樣
https://www.figma.com/file/ajFwwef2wqv5z4ydl0PgTZ/Wireframe-Dubious-Messages?node-id=0%3A1

先回去「最新查核」

訊息與回應都可能有斷行，原本可能有排版，現在會吃掉

我想把空白換成全形空格
點「閱讀全文」的時候才會變回原本排版的樣子

現在那個 upvote / downvote 有點太重
icon 與數字比例有點不一樣


### Upvote / Downvote 理由

orz
我們要顯示 downvote 理由唷
ex: https://cofacts.g0v.tw/article/2e3iohcfzpgv 這裏的理由大戰 (?)

這等於回應的回應

lucien
理由要顯示在 list page 嗎 會不會太多

超
如果是 dialog 我覺得還行
"(why)" 的呈現也 ok

lucien
中文寫什麼

orz
"Why"

超
「不認同理由」或「反對理由」

orz
也可以做成 detail dialog
顯示 upvote 的人、與 downvote 的人
和理由

API 的 upvote 可以送理由，只是現在沒送

lucien
那我可以再出一個 dialog

超
但如果又一個專門的資訊頁面
會不會在列表拖太多東西

現在只呈現 downvote 的話，呈現比較輕快一些

lucien
不過這是點擊之後的細節，可以呈現多一點

超
大家會很 care 誰贊同嗎

lucien
像 FB 我們會去看 like / dislike
例如說這篇被某個厲害的編輯 upvote 了，會讓作者覺得有一種社交地位的感覺

超
那作法應該會像 FB app 這樣，數字不會顯示在 like button 旁邊
button 與數字放不同地方，顯示與操作分開

### CTA「查核闢謠」按鈕

lucien
現在「查核闢謠」有點空
或許可以把 upvote, downvote, 查核闢謠放在同一排

超
可以
但「查核闢謠」是針對整個訊息，upvote / downvote 是針對個別回應

(還在調)

## 設計：Filter wireframe
https://www.figma.com/file/5qegqv1g0fxCYkzNz3jVA6/Wireframe-Need-to-Review-Page?node-id=0%3A1


### type filter

超
app 裡面有兩種複選機制很奇怪
"回應含有" 應該拉出來跟其他三項一樣
mobile 就多一行

況且 wireframe 現況，如果你四項都選，一樣也會佔一整行

orz
手機怎麼辦

### Date filter
orz
如果要 native date picker 的話，按下「自訂」之後應該只會有兩個 date input

:::info
下次討論
:::

### 主題 filter

超
collapse 底下，點擊主題之後會跳到左邊很討厭

orz
要不要把「展開」改成「設定」，主題預設就只寫「全部主題」？

lucien
這樣就減少主題的曝光

超
如果主題的排序是有依據的（例如總篇數）那順序就沒啥問題

lucien
到底要不要複選
沒有複選就沒問題

超
可以複選，但應該用 button 叫出來
之後還能做「添加主題」、也能處理主題變多的狀況

orz
我們要顯示主題的定義嗎
article page add category 的時候會顯示在 dialog 裡

lucien
不希望太濫用 modal

orz
那如果一樣列出主題，點到灰色（沒 highlight）的主題都是展開
收起的時候才把他排到第一個呢

lucien
可以考慮
他就是假的然後不能捲
可以只用純文字表達有哪些主題，不用都做成按鈕

超
可以就放「全部主題」純文字，不會是 tag 樣式
一整排就是一個按鈕
然後添加的時候通常是跳窗

lucien
不能用展開嗎

超
下滑的展開也可以啦

orz
可能要注意 tag 有點長，mobile 上面一行可能只有一個 tag

lucien
mobile 可能就直接開全頁了吧
mobile 比較常有這樣的互動

超
mobile 就直列然後一行一項吧

## 設計：priority = navbar

orz
list page 做完後先做 search result
因為工程會先做

lucien
search result 就是多個「搜回應」與「搜訊息」的 tab

orz
下週開始會先做 nav bar
logout 怎麼辦 改名字怎麼辦

lucien
點擊頭像可以 logout 或改名字

超
做了一個新的（右邊 drawer）
沒登入就點頭像的地方登入

footer 的東西塞進 drawer，原本 footer 可以只放 g0v logo

## 設計：「熱門訊息」

orz
「熱門訊息」感覺像是「可疑訊息」加一個 filter

我們會希望使用者先看 2 人以上回報的訊息

lucien
如果 sort by 最多人問呢

orz
最多人問的可能很久了，我就是不知道怎麼回所以才會放著，但他只會越來愈多人問 = 越來越上面
而且這種很多人問卻沒人回答的一定很難
會嚇跑新手編輯

所以現況是 filter 掉 1 人以上回報的，但還是按照時間排

lucien
但如果不先幫弄個頁面選好 filter，他就不知道要這樣選

其實當初「熱門訊息」是希望用 cron job 跑的

orz
那可能可以先拿掉

然後可疑訊息 default 成 2 人以上回報、未查核？

lucien
要先選好這麼多嗎

是可以加上「熱門回報」這個選項，加入 replyRequestCount > N 

orz
當初做 replyRequestCount > N 是因為如果很多的話壓力會很大
所以預設會希望他 focus 在 replyRequest > N 的那種
只是現在剛好是 0 篇

lucien
但還是希望新使用者進來之後可以看得到東西，知道這裡是做什麼

orz
那或許可以
如果 1 則的篇數太多，就預設開啟「熱門回報」filter 然後有個 bubble 說「篇數太多了，希望大家專注在多人回報的訊息ㄛ」這樣

實作上就是 query 兩份表與 totalCount 放進 apollo cache
UI 再決定要顯示哪個

其實就是現在這個 UI，但在數字太少的時候自動勾選 include messages reported only 1 time 這樣

lucien
filter 太自由會很像工具，而現在是用 filter 會搞到 query 不出東西來

你那個需求比較像是要有個 tab「等待你闢謠」

article list 想說做給編輯以外，也可以知道這是什麼的人

orz
但來 article list 的應該都是想幫忙回應的人，想找答案的人幾乎都在 article detail 看答案
如果幫忙回應的人被數字嚇跑了也不太好

lucien
不過現在不會顯示數字
應該就還好？

所以理想上是
filter 是「還未有效查核」+「熱門詢問」
排序是「最近被詢問」

把這三個選項框起來出一頁「熱門回報」如何？
裡面就是只能篩主題跟時間

原本沒有用熱門回報是因為他是 sort 的一個選項，但考量到這些，確實很 tricky

orz
可以呀～
還可以有 badge 顯示數字

lucien
但是有時候會是 0

還是「熱門未查核訊息」獨立一頁，帶有 badge

orz

有數字的時候顯眼一點，新手鼓勵去那一頁之類的

Lucien

知乎:
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_efcad88b9ff1b2a34494fad48d7db9d5)
「等你來答」，裡面會猜你擅長什麼來回
另外還有你被邀請回答的問題

另外還是有個首頁

Quora:
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_555f64187a4b185f25e2d96af238d405)
「要 Answer 就點這」，有 questions for you

orz

- (由定義命名) Recent urgent requests
- (由定義命名) Asked by many recently
- (由定義命名) Latest popular hoax
- (我們希望傳達的 / 抄 quora) Hoaxes for you / You can reply this / Hoax to reply / Reply
- (我們希望傳達的) Needs fact-check now

- (由定義命名) 最新熱門回報
- (我們希望傳達的 / 騙人有個人化，總之快請進！) 猜你想回
- (我們希望傳達的 / 抄知乎) 等你來答
- (我們希望傳達的) 急需回覆 / 急需闢謠
- (我們希望傳達的) 優先處理 / 優先回應 / 優先闢謠

lucien
這樣列表空掉是不是編輯就會覺得都回完了

orz
可以呀，一人回報的本來就沒有什麼營養
可以等到有兩人回報再回

lucien
也可以在這一頁 load 到 0 筆資料的時候
自動放鬆 filter 成一篇就撈出來之類的
畢竟這一頁本來就不給他設定，所以可以自動

---
tags: cofacts, meeting note
---

20200318 會議紀錄
=====

> 黑卡 mrorz, bil, ggm, lucien, 文武
> 志超 蝴蝶
>
> 上次開會紀錄：https://g0v.hackmd.io/@johnson/BkjIIk8B8
>

## 3/14 大松檢討

https://g0v.hackmd.io/@johnson/HyXMDVLBI

rumors-site

1. 開發時如果要做有登入的東西
要先登入 staging
https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1584175335.196700
沒在 README 裡寫

2. 使用
https://cofacts-api.hacktabl.org/graphql 時，要記得點開設定
把 "request.credentials": "omit" 改成 "include" 不然不會送 cookie

3. 有遇到奇怪的 samesite issue，可能跟 cookie 沒有 http 有關，但無法重現 https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1584177199.204800

ggm: 試試看這個 chrome://net-internals/#hsts

:::info
之後補正到 rumors-site README.md
:::

bil:
Lays 的水蜜桃塔洋芋片跟湖池屋的草莓蛋糕洋芋片太有挑戰性。

但下次可以試試看焦糖布丁洋芋片。



## 4/18 編輯小聚

:::info
什麼時候要決定是否舉辦?
標準？
[備案](https://medium.com/mozilla-related/virtual-community-meetup-at-the-mozilla-hubs-6fdfd269a81d)？
:::

4/1(三)決定

bil:
本週好想工作室的就停了
之前有提會在台南辦
可以暫緩公布日期

近期不會發出會在台南辦的風聲

g0v summit （12 月上旬） 也可能會延期

orz
所以 4/1 如果決定不行，就延期
判斷標準： 4/1 前連續 3 日 0 新確診

- 案1: 照常
- 案2: 延期
- 案3: 不去台南

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_14bfc756e0fab680fe7a58b4fb639c48)

ggm:
這太超前了

## LINE chatbot 升級

- [x] 換頭像
  - [x] FB page
  - [x] LINE bot
  - [x] 改 LINE 顏色
  - [ ] Cover photo: 1080 x 878
- [ ] Rich menu
  - 選項：教學、專案簡介、討論區？
  - 按下去之後：![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e9614df0db223e1f4333071a608a899d)

- [x] 公告說已經完成



## Downtimes
3/13 凌晨 1:54 升級後依然有 downtime

### [升級前] 3/6
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0c70e87e820d5f4664c042dff7ce4d21)

### [升級前] 3/10
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e1395d9314f5e637486c0320c412e95a)

```
# nginx error log

2020/03/09 22:42:52 [error] 8#8: *885292 recv() failed (104: Connection reset by peer) while reading response header from upstream, client: 3.84.42.143, server: cofacts-api.g0v.tw, request: "POST /graphql? HTTP/1.1", upstream: "http://172.18.0.5:5000/graphql", host: "cofacts-api.g0v.tw"
2020/03/09 22:42:52 [error] 8#8: *885201 upstream prematurely closed connection while reading response header from upstream, client: 118.163.94.30, server: cofacts-api.g0v.tw, request: "POST /graphql HTTP/1.1", upstream: "http://172.18.0.5:5000/graphql", host: "cofacts-api.g0v.tw"
2020/03/09 22:43:47 [error] 8#8: *885663 upstream prematurely closed connection while reading response header from upstream, client: 3.84.42.143, server: cofacts-api.g0v.tw, request: "POST /graphql? HTTP/1.1", upstream: "http://172.18.0.5:5000/graphql", host: "cofacts-api.g0v.tw"
2020/03/09 22:43:47 [error] 8#8: *885653 upstream prematurely closed connection while reading response header from upstream, client: 3.84.42.143, server: cofacts-api.g0v.tw, request: "POST /graphql? HTTP/1.1", upstream: "http://172.18.0.5:5000/graphql", host: "cofacts-api.g0v.tw"
2020/03/09 22:43:47 [error] 8#8: *885684 upstream prematurely closed connection while reading response header from upstream, client: 3.84.42.143, server: cofacts-api.g0v.tw, request: "POST /graphql? HTTP/1.1", upstream: "http://172.18.0.5:5000/graphql", host: "cofacts-api.g0v.tw"
2020/03/09 22:43:47 [error] 8#8: *885599 upstream prematurely closed connection while reading response header from upstream, client: 118.163.94.30, server: cofacts-api.g0v.tw, request: "POST /graphql HTTP/1.1", upstream: "http://172.18.0.5:5000/graphql", host: "cofacts-api.g0v.tw"
2020/03/09 22:43:49 [warn] 8#8: *885994 a client request body is buffered to a temporary file /var/cache/nginx/client_temp/0000000616, client: 172.18.0.1, server: cofacts-api.g0v.tw, request: "POST /graphql HTTP/1.1", host: "cofacts-api.g0v.tw"
2020/03/09 22:44:43 [error] 8#8: *886113 upstream prematurely closed connection while reading response header from upstream, client: 118.163.94.30, server: cofacts-api.g0v.tw, request: "POST /graphql HTTP/1.1", upstream: "http://172.18.0.5:5000/graphql", host: "cofacts-api.g0v.tw"
2020/03/09 22:45:24 [error] 8#8: *886641 upstream prematurely closed connection while reading response header from upstream, client: 118.163.94.30, server: cofacts-api.g0v.tw, request: "POST /graphql HTTP/1.1", upstream: "http://172.18.0.5:5000/graphql", host: "cofacts-api.g0v.tw"
2020/03/09 22:45:36 [warn] 8#8: *886973 an upstream response is buffered to a temporary file /var/cache/nginx/proxy_temp/7/61/0000000617 while reading upstream, client: 27.246.230.25, server: cofacts.g0v.tw, request: "GET /_next/static/images/5-eb47244f98fda02e06fa617d77f8ef25.jpg HTTP/1.1", upstream: "http://172.18.0.6:3000/_next/static/images/5-eb47244f98fda02e06fa617d77f8ef25.jpg", host: "cofacts.g0v.tw", referrer: "https://cofacts.g0v.tw/"
2020/03/09 23:06:17 [error] 8#8: *887015 upstream timed out (110: Connection timed out) while reading response header from upstream, client: 118.163.94.30, server: cofacts-api.g0v.tw, request: "POST /graphql HTTP/1.1", upstream: "http://172.18.0.5:5000/graphql", host: "cofacts-api.g0v.tw"
```

### [升級前] 3/11
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_86d0d8c7699599ba133e2c5ef36091a3)


### [升級前] 3/12
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fc4e7cc6b035202ebdf18b3f0c979718)

### [升級後] 3/16
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d7741fa2b26d4e8b390a73340134b710)

### nginx logs
https://drive.google.com/drive/u/0/folders/1rsSJ9TNry6roElCqqxsJXI9b3DWxn0eE

raw log --> fluentd --> elasticsearch ---> kibana (time series 有 visualize + 下 query)

## rumors-line-bot memory issue

文武:
看 log 跟自己傳，發現其實是有擋的
但是是要同時傳 6 張圖，才會有一張擋住（上限 = 5）
超過 memory 的 log 也是在那個時候噴的

ggm
那要不要弄個 job queue

文武
但這樣可能後面的都要 drop 掉
因為有 30 秒回應限制

orz
如果有做很久的擋在前面 timeout，後面排隊的人也白等了

信件「Messaging API: Webhook transmission failed - Cofacts 真的假的 | 轉傳查證」的發生時間
會跟 Heroku dyno memory 超過的時間一致
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0b675cb19e44fddef443b4544d1010e7)

## 開發
GitHub activities
https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/WSQFB

### LINE bot notification
Tickets: https://github.com/orgs/cofacts/projects/4
LIFF redesign: https://g0v.hackmd.io/860RnxUGTi6z2Kca6ojAbg

### `CreateCategory` 與 `CreateArticleReply` 討論
https://github.com/cofacts/rumors-api/issues/158


### 許願
> MrOrz: 最近回訊息的時候，發現自己其實很常搜尋自己過去寫過的來重複使用
> 覺得可以做下面的功能
> - 回應訊息區可以有個 tab 列出「自己過去的回應」
> - 「把此回應加到這則文章」按鈕可以多個次功能 (收在下拉 dropdown 裡) 是「使用此回應撰寫新回應」，按下去的話會把回應 + 出處（但不含 type 判斷）append 到「回應」與「出處」的輸入框

## Likecoin validator
> Likecoin 估算：
> 1 core 2GB RAM 的機器應該夠用
儲存空間方面，之前的估算是每年增加 40GB，目前運行了約 4 個月，空間用了約 8GB，所以大約是每年 25GB
考慮到將來升級後功能增加，交易量可能會相應增加，按每年增加 40GB 空間估算似乎比較穩妥
linode 的話，我看到他們有 1 core 2GB 的機器，10 USD / month
不過儲存空間只有 50GB，加到 100GB 的話應該額外再多出 5 USD / month
>
> 另外保險起見，會建議額外運行一兩臺非 validator 的普通節點，以便平時存取 API，並在 validator 節點出問題時快速切換恢復，以免被 slash
這個模式下費用會相應加倍
> 

lucien
likecoin 通過了第一個 proposal

POS 記憶體與 CPU 應該都不吃重，硬碟開好開滿就好
結點用 docker 直接起就好

slash 是有 downtime 的話，卡著大家會有懲罰
怕機器有問題所以要開兩台
要有個簡單的 load balance

orz
硬碟兩個要 sync 嗎

lucien
不用，會自己 sync

ggm
沒驗證不是只是拿不到獎勵嗎

lucien
slash 是懲罰，會砍錢

https://likecoin.bigdipper.live/validators

ggm
可以在自己的地方友情幫跑

:::success
GGM <> Likecoin
跑在 GGM 用來跑節點的地方
:::

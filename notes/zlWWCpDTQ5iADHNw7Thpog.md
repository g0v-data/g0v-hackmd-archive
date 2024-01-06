---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20211006 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz, nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production
#### :globe_with_meridians: Site
https://github.com/cofacts/rumors-site/releases/tag/release%2F20210930

- #451 Block sending empty replies
- #448 Fix typo in impact report

### :rocket: Staging

#### :robot_face: rumors-line-bot

- [Redirect LIFF](https://github.com/cofacts/rumors-line-bot/pull/292)

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] Rediret LIFF 測試
    - [x] iOS 打開此連結：https://dev-line-bot.cofacts.tw/liff/redirect.html?articleId=3tu9btf8s50sm
        - [x] 可不用登入就正常點開
        - [x] 按「前往閱讀查核回應」無須登入就能看到訊息與回應
        - [x] 可 upvote / downvote」
    - [x] Android 打開此連結：https://dev-line-bot.cofacts.tw/liff/redirect.html?articleId=3tu9btf8s50sm
        - [x] 可不用登入就正常點開
        - [x] 按「前往閱讀查核回應」無須登入就能看到訊息與回應
        - [x] 可 upvote / downvote
    - [x] Google analytics 可收到 pageview
- [x] Rich menu 測試
    - [x] 「設定」更改後再次打開，應該會保留原本設定

##### ⛔️ Release Blockers

無

##### 未竟項目

右上角「在真的假的開啟」 iOS 下沒有作用（production 上也是）

#### :globe_with_meridians: Site

- [#452](https://github.com/cofacts/rumors-site/pull/452) Move added categories forward
    - Move categories that has been added to the front
    - Then list out categories that is also marked in similar articles
    - Then the rest of the categories.

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：
- [x] Article detail
  - [x] Can see similar messages
  - [x] Can see categories

登入自有帳號後檢測：
- [x] Article detail
  - [x] 觀察「類似訊息」的分類，相關分類應該會排在 Add category dialog 的前面
  - [x] Can add, remove, upvote, downvote category

##### ⛔️ Release Blockers

##### 未竟項目

- 如果 related article 的 category 的評分是負的，這個 category 仍然會優先出現
    - 新需求，另外開票

## Delete reply requests

:::info
**2021/12/01 Update**
A dedicated doc is opened to track its development - https://g0v.hackmd.io/hk1v8Ka5TCmIZinQ6zKU9Q
:::

https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1633251643.0785

### 帳號與內容

- 3 個帳號、59 篇，幫 2 個 LINE ID 打廣告
- https://docs.google.com/spreadsheets/d/1Ytd69YU6z7Fgra81_79XrsPwQYV1Clh0yp5OZlk5Psg/edit

### 影響

- 不斷觸發等你來答 RSS，但訊息其實很冷門
- 增加 reply request count

### 處理方式

- 同刪除 reply 做法：放進 [spreadsheet](https://docs.google.com/spreadsheets/d/1BBObfTO7bLWERQ3nq3S1iBs3xt2o2TgOxikXqixOdYI/edit)，根據黑名單定時自動列出廣告，產生刪除指令後手動刪除
  - 不用改動系統，在 spreadsheet appscript 透過現有 API 偵測與進行公告
  - 但仍然需要仿照 [delete reply 的 script](https://github.com/cofacts/rumors-api#removing-article-reply-from-database)，在 rumors-api 增加刪除 reply request 的指令 script
  - 無法解決 RSS 問題，除非對方發現沒有廣告效益後消失
- 增加「回報濫用」/「檢舉」按鈕，檢舉違反使用者條款的廣告行為
  - 全新系統，但可以套用到訊息、回應、補充、feedback 等
  - 需要公告檢舉列表與回應進度嗎？爭議處理如何做？
  - 公告與刪除仍然是手動，亦無法解決 RSS 問題
- ~~刪帳號~~
  - 登入時秒重註冊，完全沒有擋到
- 允許黑名單使用者寫入新補充、回應與 feedback，但也全自動刪除
  - 公告 spreadsheet 與 cronjob 連動，進行自動公告與刪除
  - 太快刪會被黑名單使用者發現，太晚刪又無法解決 RSS 
- 帳號增加黑名單 flag，若為黑名單，則禁止發表補充、回應與 feedback
  - 如果一直阻擋寫入，他應該會發現，然後直接蓋新帳號
      - 除非包裝成一種錯誤，跳出視窗說「遇到問題所以送出失敗、若問題持續請主動來信」？
  - 可以暫時解決 RSS 問題，直到他開新帳號
  - 變化型：UI 做 [optimistic update](https://www.apollographql.com/docs/react/v2/performance/optimistic-ui/), 發現是黑名單使用者的話就阻擋 mutation 但不顯示錯誤、也不重繪 UI
      - 不確定是否能簡單地實作成功
- 隱藏黑名單的產出，但本人看不到被隱藏這件事情 [name=nonumpa]
    - 新 state: 其他人看不到、但自己看得到的 state
    - 改 comment & reply 的顯示邏輯
    - 登出就看不到了 XD
    - replyrequest / reply count 計數要避開被折疊的項目
    - 可以紀錄被隱藏的內容是什麼，作為「為什麼要藏」的依據
    - downvote 比較多就藏 [name=nonumpa]
        - 但有些比較極端的狀況例如天ㄗㄜˊ集團那篇

:::info
先試試看隱藏 solution
1. user 建立黑名單
2. 黑名單使用者的產出會被標上隱藏 state
3. API 預設不顯示隱藏的東西；UI 會 request 隱藏的東西，並且在隱藏物的作者登入下顯示
:::


## LINE bot event 送不進 Google Analytics

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_36992d581b1446bdc2fade3daa8f3600.png)

- 日期範圍：10/3, 10/4, 10/5。10/6 凌晨恢復。
- 影響 event：rumors-line-bot [GA Events](https://github.com/cofacts/rumors-line-bot#google-analytics-events-table) 中，除了 LIFF event 與 LIFF pageview 之外的所有 event
- Root cause
    1. Linode 指定給我的機器的 name server，把 www.google-analytics.com 導向到失效的 IP「203.208.50.65」
    2. 機器的 docker container 會沿用 host machine 的 DNS 設定
    3. LINE bot server docker container 使用 [universal-analytics](https://www.npmjs.com/package/universal-analytics) library 發送 GA event 時，會把 event 送去 www.google-analytics.com
    4. 由於 www.google-analytics.com 被 name server 錯誤的解析成錯誤的 IP，因而無法建立連線，導致所有 chatbot server 往 GA 送的 event 無法送達
- 資料送往中國的疑慮
    - 錯誤 IP 203.208.50.65 位於中國
    - LINE bot 送給 GA 的 event，會包含使用者在 chatbot 查詢的文字內容（在 document title 欄位，用來顯示在 [message trend](https://datastudio.google.com/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/NrUQ)）；另外也會送 LINE 給該使用者的 id  (`U` 開頭的亂碼) 作為給 google analytics 的 user ID
    - 但既然 curl 會是回報 “Failed to connect”，代表 TCP 連線根本無法建立，所以以上資訊應該是完全沒送出去。
- 後續處理
    - 已在 2021/10/6 2am 回報 Linode 開立 support ticket “Linode DNS points www.google-analytics.com to wrong IP in China” 並提供解析錯誤 IP 的 name server
    - 是否要有個地方列出會影響 analytics 與 opendata 的 incidents 供使用數據的人參考？

:::success
放個 hackmd 紀錄 incident
hackmd URL 貼到每個表
:::

:::spoiler 分析細節
- Staging GA property：沒有問題，正常運作，staging bot 可正常發送 event
- Production GA property：
    - 在 Mac 自家電腦開啟 node CLI 可以使用 `ga()` lib 發送 custom event 並在 GA realtime event report 收到 :heavy_check_mark: 
    - 在 rumors-line-bot 的 docker container 內 (利用 docker-compose exec) 開啟 node CLI 可以正常呼叫 `ga()` 與 `.send()` 但 GA realtime event report 無反應 ❌
        - 昨天開始沒有 hit 流量
        - 但 line bot container 已經開兩個禮拜
    - 從 production 機器直接打 curl & pageview hit from [hit builder](https://ga-dev-tools.web.app/hit-builder/)： GA realtime event report 可以收到 :heavy_check_mark:
    - 在 rumors-line-bot 的 docker container 打 curl & pageview hit from [hit builder](https://ga-dev-tools.web.app/hit-builder/)： ❌：
        - `curl: (28) Failed to connect to www.google-analytics.com port 443 after 130281 ms: Operation timed out`
        - 被 Google analytics 防火牆擋住？ [name=mrorz]

---

感謝 kevinho84 +++++

### Docker host machine
```
$ ping www.google-analytics.com
PING www-google-analytics.l.google.com (142.251.42.142) 56(84) > bytes of data.
64 bytes from … (略) …
--- www-google-analytics.l.google.com ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7077ms
rtt min/avg/max/mdev = 0.540/0.597/0.644/0.041 ms
```

```
$ nslookup www.google-analytics.com
Server:		<some-ip-under-same-subnet>
Address:	<some-ip-under-same-subnet>#53

Non-authoritative answer:
www.google-analytics.com	canonical name = www-google-> analytics.l.google.com.
Name:	www-google-analytics.l.google.com
Address: 203.208.50.65
```

(`A`, `B`, `C` and `D` are under same subnet of my machine’s IP address)
```
docker@debian:~/rumors-deploy$ traceroute www.google-analytics.com
traceroute to www.google-analytics.com (142.251.42.142), 30 hops max, 60 byte packets
 1  A (A)  0.578 ms B (B)  0.709 ms  0.848 ms
 2  if-11-1-5-0.gw2.shg1.jp.linode.com (C)  0.462 ms if-0-1-5-0.gw2.shg1.jp.linode.com (D)  0.485 ms  0.458 ms
 3  72.14.196.114 (72.14.196.114)  2.102 ms 72.14.223.216 (72.14.223.216)  0.404 ms  0.408 ms
 4  108.170.242.97 (108.170.242.97)  0.552 ms  0.595 ms 108.170.242.129 (108.170.242.129)  1.615 ms
 5  108.170.236.127 (108.170.236.127)  0.542 ms  0.550 ms  0.561 ms
 6  nrt12s45-in-f14.1e100.net (142.251.42.142)  0.583 ms  0.567 ms  0.532 ms
 ```

### LINE bot docker container

```
PING www.google-analytics.com (203.208.50.65): 56 data bytes
64 bytes from … (略) …
--- www.google-analytics.com ping statistics ---
16 packets transmitted, 4 packets received, 75% packet loss
round-trip min/avg/max = 105.746/190.202/228.356 ms
```

```
/srv/www # nslookup www.google-analytics.com
Server:		127.0.0.11
Address:	127.0.0.11:53
Non-authoritative answer:
www.google-analytics.com	canonical name = www-google-> analytics.l.google.com
Name:	www-google-analytics.l.google.com
Address: 203.208.50.65

Non-authoritative answer:
www.google-analytics.com	canonical name = www-google-analytics.l.google.com
```

`DOCKER_GATEWAY`: IP address used by docker (172.18.x.x); `E` and `F` are under same subnet of my machine’s IP address)
```
/srv/www # traceroute www.google-analytics.com
traceroute to www.google-analytics.com (203.208.50.65), 30 hops max, 46 byte packets
 1  DOCKER_GATEWAY (DOCKER_GATEWAY)  0.007 ms  0.006 ms  0.004 ms
 2  A (A)  0.560 ms  0.519 ms  B (B)  0.806 ms
 3  if-11-0-0-0.gw2.shg1.jp.linode.com (E)  0.471 ms  if-11-1-5-0.gw1.shg1.jp.linode.com (F)  0.638 ms  0.314 ms
 4  ae-9.a00.tokyjp05.jp.bb.gin.ntt.net (192.80.16.5)  0.833 ms  1.315 ms  1.074 ms
 5  ae-22.r02.tokyjp05.jp.bb.gin.ntt.net (129.250.4.7)  1.594 ms  1.793 ms  1.209 ms
 6  202.97.94.13 (202.97.94.13)  90.094 ms  xe-0.chinanet.tokyjp05.jp.bb.gin.ntt.net (129.250.66.10)  204.861 ms  ae-22.r02.tokyjp05.jp.bb.gin.ntt.net (129.250.4.7)  1.411 ms
 7  *  xe-3.chinanet.tokyjp05.jp.bb.gin.ntt.net (129.250.66.90)  161.073 ms  *
 8  202.97.74.2 (202.97.74.2)  80.426 ms  202.97.74.34 (202.97.74.34)  52.750 ms  202.97.91.25 (202.97.91.25)  56.915 ms
 9  202.97.62.73 (202.97.62.73)  54.355 ms  202.97.94.141 (202.97.94.141)  205.894 ms  *
10  202.97.19.53 (202.97.19.53)  90.569 ms  202.97.13.157 (202.97.13.157)  86.509 ms  *
11  101.95.88.133 (101.95.88.133)  55.874 ms  61.152.24.105 (61.152.24.105)  87.906 ms  61.152.25.109 (61.152.25.109)  95.932 ms
12  *  101.95.95.162 (101.95.95.162)  112.589 ms  101.95.116.138 (101.95.116.138)  96.343 ms
13  *  *  101.95.116.138 (101.95.116.138)  95.539 ms
14  *  203.208.62.221 (203.208.62.221)  96.958 ms  203.208.62.2 (203.208.62.2)  225.663 ms
15  203.208.62.55 (203.208.62.55)  220.407 ms  203.208.62.2 (203.208.62.2)  229.029 ms  203.208.62.16 (203.208.62.16)  224.079 ms
16  *  203.208.50.65 (203.208.50.65)  220.497 ms  203.208.62.55 (203.208.62.55)  238.744 ms
```

### 分析

我的 linode 的 network 是有開 network helper （ https://www.linode.com/docs/guides/network-helper/ ） 的。所以，Linode 會幫我管理 `/etc/resolv.conf`

所以我的 /etc/resolve.conf 長這樣
```
# Generated by Linode Network Helper
# Thu Sep 16 18:08:49 2021 UTC
#
# This file is automatically generated on each boot with your Linode's
# current network configuration. If you need to modify this file, please
# first disable the 'Auto-configure Networking' setting within your Linode's
# configuration profile:
#  - https://cloud.linode.com/linodes/2569620/advanced
#
# For more information on Network Helper:
#  - https://www.linode.com/docs/platform/network-helper
#
# A backup of the previous config is at /etc/.resolv.conf.linode-last
# A backup of the original config is at /etc/.resolv.conf.linode-orig
#
domain members.linode.com
search members.linode.com
nameserver 第一台
nameserver 第二台
nameserver 第三台
options rotate
```

而下面分別是我的 hostmachine 使用 8.8.8.8 以及這三台 linode name server resolve 出來的結果：
```
host-machine:~# nslookup www.google-analytics.com 8.8.8.8
Server:		8.8.8.8
Address:	8.8.8.8#53

Non-authoritative answer:
www.google-analytics.com	canonical name = www-google-analytics.l.google.com.
Name:	www-google-analytics.l.google.com
Address: 172.217.160.78

host-machine:~# nslookup www.google-analytics.com 第一台
Server:		第一台
Address:	第一台#53

Non-authoritative answer:
www.google-analytics.com	canonical name = www-google-analytics.l.google.com.
Name:	www-google-analytics.l.google.com
Address: 203.208.50.65

host-machine:~# nslookup www.google-analytics.com 第二台
Server:		第二台
Address:	第二台#53

Non-authoritative answer:
www.google-analytics.com	canonical name = www-google-analytics.l.google.com.
Name:	www-google-analytics.l.google.com
Address: 142.251.42.142

host-machine:~# nslookup www.google-analytics.com 第三台
Server:		第三台
Address:	第三台#53

Non-authoritative answer:
www.google-analytics.com	canonical name = www-google-analytics.l.google.com.
Name:	www-google-analytics.l.google.com
Address: 216.58.197.238
```

三台 name server 說的 www.google-analytics.com 位置都不同，但第一台 name server 回傳的 IP 「203.208.50.65」指向中國

然後又因為 docker container 會取用 host machine 的 /etc/resolv.conf ( https://docs.docker.com/config/containers/container-networking/#dns-services )
所以我的 line bot docker container somehow 就把 `www.google-analytics.com` 解析成了 googlecn `203.208.50.65`

我把 host machine 上的 /etc/resolv.conf 的第一台 name server comment 掉之後重開 line bot 的 container
line bot container 就能連到 www.google-analytics.com ，資料也就能正常的送進 google analytics 了⋯⋯

:::


## rumors-ai

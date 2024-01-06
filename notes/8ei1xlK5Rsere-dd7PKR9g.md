---
tags: cofacts, meeting note
---
20191211 會議記錄
=====

orz,bil,JC,文武（慈慈沒飲料）,(上午：4貓,Lora, bil)
> 上次開會紀錄：https://g0v.hackmd.io/@mrorz/r1wIjGVaS
> 

## Google Trusted Media Summit

### Tempo.cc
- 200 journalists
- 10 fact-checkers
- 

### Mafindo

- 現在做影片 > 10 full-time fact-checker
- 1 FC per day
- many volunteers
- 大學查核志工比賽，贏的人帶來新加坡參加 Trusted media summit

Bot:
Whatsapp 輸入關鍵字，噴出相關訊息
「總統」「總統的名字」etc

### Full fact
- https://fullfact.org/about/funding/
- open-source
- 

### Meedan

開源上稿平台，像無名小站後台

### 媒體產業心靈健康
爭議
媒體可能採訪新疆等題目然後心靈很難承受


## 拜訪
- JC (疾管家)
- 路透社採訪 https://docs.google.com/document/d/1BszQQIsXHTBZXvsIUKE1RwshSscNGeMoC5z6Oi8GnCo/edit?usp=sharing

## BOT
可能會有兩個TA（一個是回報假訊息的人另一個是？）
Line 現在提供兩種主選單，可以針對不同使用者顯示
實作初心者教學

如果用computer design 來套用RD的開發
其實Johnson已經開發好一個版本了

所以接下來想要考慮到長輩的使用
優化line bot的清單

標題字跟內文字可以再考慮

可以怎麼樣鼓勵志工？

billion 去教
查核促進大家熱烈對話
對話千層派：鼓勵對話
串聯很快，用很多大學生
特點是對議題有想法的人，但沒辦法複製
規格化

一些跨國的小經驗
（假新聞清潔劑）免費小禮物  美陸坦盒子 （但是因為獎勵差不多所以可能拿過一次就不會想要拿了）

視覺化
badge
實體獎盃
長輩使用時，長輩被闢謠會尷尬啊啊（美玉姨）
(正確的回應提供更多的正向回饋)


Johnson
chatbot 可能主要還是想知道回應的人在用
不過我們會希望 chatbot 使用者覺得回應可以改進的時候，把他們轉化成撰寫回應的人

目前單一文章頁面的教學不太好，所以有一些回應是謾罵的，我覺得可能是從 chatbot 轉過來的人
或許可以改進文章頁面，讓他們知道如何寫出好回應

JC
目前主要的優化方向
bot onboarding
bot 主選單
bot 查詢結果的呈現方式
從bot轉化查核者的流程優化
網站 onboarding


## 其他採訪
- New York Times

:::success
MrOrz 回信
:::

## Rumors-site 升級 next9
1. [x] Article list --> PR to dev
2. [x] Article page （見 API 更新）
3. [x] Reply list
4. [x] reply page
5. [x] docker build
6. [x] landing page
7. [x] 上 staging
8. [ ] 上 production --> GG
9. [x] google analytics (w/ gtag)
10. [ ] All i18n (including levels...)
11. [ ] RSS feed



### PRs
- 補做「這個回應也用在」功能 https://github.com/cofacts/rumors-site/pull/182
- 「這個使用者也回報其他訊息」列表標題 https://github.com/cofacts/rumors-site/pull/183
- Rollbar 整合 https://github.com/cofacts/rumors-site/pull/187
- `/analytics` & `/hack` route: https://github.com/cofacts/rumors-site/pull/188 (還是做在 nginx 好?)

### TODOs
- 從其他頁面點進 `/replies` 會壞掉
- 字太小
- performance issue (可能沒救，加大機器ㄅ)


### Performance issue

#### CPU Snapshots
https://drive.google.com/drive/folders/1sDwEe2dc1SLorZN7jM2UuoMG3px14AO5

#### Setup

local 的 API server, local 的 elasticsearch (全空)
development mode React + 開啟 --inspect flag 的 node.js

- 舊網站：`d3d24342`
- 新網站：`ea405bac`


#### Result

##### 舊網站
```
$ ab -n 10000 -c 20 http://localhost:3000/articles
This is ApacheBench, Version 2.3 <$Revision: 1826891 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking localhost (be patient)
Completed 1000 requests
Completed 2000 requests
Completed 3000 requests
Completed 4000 requests
Completed 5000 requests
Completed 6000 requests
Completed 7000 requests
Completed 8000 requests
Completed 9000 requests
Completed 10000 requests
Finished 10000 requests


Server Software:
Server Hostname:        localhost
Server Port:            3000

Document Path:          /articles
Document Length:        6677 bytes

Concurrency Level:      20
Time taken for tests:   117.871 seconds
Complete requests:      10000
Failed requests:        0
Total transferred:      69270000 bytes
HTML transferred:       66770000 bytes
Requests per second:    84.84 [#/sec] (mean)
Time per request:       235.742 [ms] (mean)
Time per request:       11.787 [ms] (mean, across all concurrent requests)
Transfer rate:          573.90 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0    0   0.2      0       9
Processing:    33  235 113.5    206    1853
Waiting:       31  231 109.9    204    1800
Total:         33  236 113.5    206    1853

Percentage of the requests served within a certain time (ms)
  50%    206
  66%    235
  75%    260
  80%    282
  90%    352
  95%    415
  98%    507
  99%    606
 100%   1853 (longest request)
```

##### 新網站

```
$ ab -n 10000 -c 20 http://localhost:3000/articles
This is ApacheBench, Version 2.3 <$Revision: 1826891 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/
Benchmarking localhost (be patient)
Completed 1000 requests
Completed 2000 requests
Completed 3000 requests
Completed 4000 requests
Completed 5000 requests
Completed 6000 requests
Completed 7000 requests
Completed 8000 requests
Completed 9000 requests
Completed 10000 requests
Finished 10000 requests
Server Software:        
Server Hostname:        localhost
Server Port:            3000
Document Path:          /articles
Document Length:        66747 bytes
Concurrency Level:      20
Time taken for tests:   265.422 seconds
Complete requests:      10000
Failed requests:        7514
   (Connect: 0, Receive: 0, Length: 7514, Exceptions: 0)
Total transferred:      484474032 bytes
HTML transferred:       481791546 bytes
Requests per second:    37.68 [#/sec] (mean)
Time per request:       530.845 [ms] (mean)
Time per request:       26.542 [ms] (mean, across all concurrent requests)
Transfer rate:          1782.51 [Kbytes/sec] received
Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0    0   0.2      0       7
Processing:    85  530 417.9    465    8792
Waiting:       83  418 420.3    378    8789
Total:         85  530 417.9    465    8792
Percentage of the requests served within a certain time (ms)
  50%    465
  66%    503
  75%    540
  80%    574
  90%    662
  95%    771
  98%    948
  99%   1289
 100%   8792 (longest request)
```

:::success
1. 拔掉 material UI SSR 再上上看狀況
2. 機器還是升
:::

## OCR

PR: https://github.com/cofacts/rumors-line-bot/pull/147 待 review
TODO: Deploy to staging w/ new buildpack

## VI

https://drive.google.com/drive/u/0/folders/1nnOFuxW70m7OgGfAI3fVcB8ri2ugODki

Cofacts 中文 chatbot - LINE 官方帳號不給換
Cofacts 主頁 cover photo: 貼圖大小建議為1080x878px，且在3MB以內。

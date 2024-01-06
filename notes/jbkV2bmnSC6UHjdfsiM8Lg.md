---
title: "g0v X Watchout SoC 期中報告檢討"
tags: hackpad
---

# g0v X Watchout SoC 期中報告檢討

> [點此觀看原始內容](https://g0v.hackpad.tw/NpkgP263Y78)


### 開場及串場

    下次可以記得做投影片放上Logo當背景，因為都在忙直播所以串場都是大家自由發揮。

### 直播

    youtube有一臺機器掛掉，必須要換帳號，對應的url才會改變。本來想換hangout但是hangouts也抓不到HDTV CAM的畫面(可能有地方沒調好)
    畫面問題(因為截取卡和錄像設備，採480p streaming)
    收音問題

### 投影機

    給大家測試投影機的時間沒預估進去，並且中途機器有掛掉過，浪費了開始的時間。
    下次準備一檯專門報告用的筆電，加上詢問大家報告的需求。

### 立委投票指南android app

    可能要做好測試系統，之後就可以做些程式上的修正或新增功能


### ly.g0v.tw(國會大代誌)

    clkao 在我 demo 時抓到進度條上的錯誤，我跟 clkao 在會後討論時把問題釐清了，之後我會再發 pull request 解決這個 bug。
    demo 時出問題的提案：[http://ly.g0v.tw/bills/1374L15430](http://ly.g0v.tw/bills/1374L15430)
    這個問題發生在「複議」上，目前如果議程是「複議」的話，程式就會直接當作「三讀通過」。
    但這是錯的，「複議」在不同情況下，有不同含意：
1.  如果在「一讀」後「複議」，有可能：
    1.  沒有付委，還停留在「一讀」階段
    2.  已付委，進入「付委」階段，委員會查詢系統會有該筆議程
    3.  逕付二讀，進入「二讀」階段
2.  如果在「三讀」後「複議」，那麼會保持在「三讀」階段


### 我說錯了嗎 (politwoops.tw)

    clkao建議可以先做個小的MVP讓大家看到目前有那些人的臉書有刪除記錄。
    討論後預計先做這部分(使用nodejs) + 截圖部分(只截第一次發文當作證據)
> 嗚嗚我還在想到底要不要用nodejs....(angular 還沒看囧
> [name=lanfon]

> btw, MVP是指 Model View Presenter 嗎XD?
> [name=lanfon]

> 我剛查到這篇：[https://plus.google.com/+AngularJS/posts/aZNVhj355G2](https://plus.google.com/+AngularJS/posts/aZNVhj355G2)，所以你說的應該沒錯
> [name=強 廉]

> 村長一開口，立馬有深坑.......(逼死人QAQQQ
> [name=lanfon]

> MVP 是minimum viable product XDD
> [name=Yuan C]

> 完全誤會啊....btw 問獎金是一起發嗎XD
> [name=lanfon]

> 好問題！有人急著需要獎金的嗎？ 
> [name=Yuan C]

> ((其實快斷糧XD
> [name=lanfon]

> ok 我跟上頭請示一下，不過大概最快要下週才給你回復 :smile:
> [name=Yuan C]

> ok :+1:
> [name=lanfon]




---
title: "法院判決書資料探勘"
tags: 判決書,司改會,hackpad
---

# 法院判決書資料探勘

> [點此觀看原始內容](https://g0v.hackpad.tw/jzBYLYjZ2J4)


## 目的

1.  讓法院的判決可以用  Google 做全文搜尋
2.  透過 data mining 回答以下問題 (請增加):
    1.  一年之中哪個月處理的案子最多？
    2.  月初還是月底是結案高峰？
    3.  哪個法官勝訴機率最大？
    4.  誰告人最多？
    5.  誰被告最多？
    6.  誰一直告誰？
    7.  哪個銀行發的的支付命令最多，平均多少錢？
    8.  刑法某個法條平均刑期、標準差等
3.  爬出以下結構化資料
    1.  人名 { 原告、被告、法官、書記官、律師 }
    2.  適用法條
    3.  刑期
4.  等等等請自行增加


## 架構

- 判決本文放在 gh-pages
    - Google 可以依此做全文搜尋 -- 反正我們自己做，也不可能做得比 Google 好
    - 命名規則和判決字號做 1:1 mapping 如:
        - [http://miaoski.github.io/jrf/86/鑑/8226.html](http://miaoski.github.io/jrf/86/鑑/8226.html)
        - 為了增加 git push 的效率，分成幾個 repo ，請以 *.html 為準
- 判決案由另開 gh-pages
    - Google 可以依此做全文搜尋
- metadata 放在 EC2 上的 ElasticSearch / Kibana
    - 為了省錢，只存 metadata 做 visualization 和分析
    - 找到東西後就連回
- Graph 放在 A-tsioh 的 padagraph.io


## 資料來源

爬資料的方法放在 [jrf_data](https://g0v.hackpad.tw/BlLdzEsImuv) 。


## 待處理

- 每天 get_schedules.rb


## 解釋

庭期表：
庭期表是法院開庭的時程，通常過期就會砍掉了。而公布的時程只有今明兩天比較穩（因為先公布的有可能會改時間）。

庭期表內容有開庭的案號、時間、法官股別（搭配股別分配表可找到法官，不過有時候有三個法官，股別分配表只能找到一個法官）。

分析庭期表，可了解法院案子審理進度。不過，有些案子如果和解，就會沒有判決，但從此再也不開庭；送鑑定也可能一年以上沒開庭。


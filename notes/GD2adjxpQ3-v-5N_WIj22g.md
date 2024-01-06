---
title: "g0v shadowcat 影子政府網站"
tags: hackpad
---

# g0v shadowcat 影子政府網站

> [點此觀看原始內容](https://g0v.hackpad.tw/ta138sdLdND)


## 專案簡介

- 將任何政府網站的 domain gov.tw 的 "o" 改成 0 都可以連到一個 shadow website
- 系統會自動分析原始的網站的關鍵字，並立刻建立一個頁面：
    - 訂閱此網頁功能：
        - 每天/小時會把更新寄給訂閱者
        - 網頁更新監控：
            - [http://sitealerts.com/](http://sitealerts.com/)
            - [https://versionista.com/](https://versionista.com/)
    - 連結所有政府 / 民間相關的 Open Data
        - 使用者可以增加自己在爬的相關資料
        - 增加 Kimono-like 的功能，使用者可以用 web tool 直接抓取該頁面的資料，成為新的 api 並加入到 shadow site
        - ref: [https://wrapapi.com/](https://wrapapi.com/)
        - ref: [https://scrapinghub.com/scrapy-cloud](https://scrapinghub.com/scrapy-cloud)
        - ref: Portia
        - open data set 可以增加 comment, 5 star ranks
    - 所有與此關鍵字有關的 g0v/civic tech project**（再也不用去記那麼多 project 的宅名與網址）**
        - 使用者也可以自由新增與上述 open data 有關的 project, github repos..
    - 所有與此政府機構有關的 pol.is 討論
    - Crowd-sourcing keywords/tags => 這個政府機構跟哪些關鍵字有關（例如，勞動部自己的官網可能沒有「過勞」、「超時工作」這類的標籤）
    - 每個類別使用者都可以透過新增功能，加入新的內容

- g0v.tw dashboard
    - 首頁可以看到所有連結的 Open data
    - 首頁可以看到哪些頁面有多少人訂閱
    - 史上最後一個 project hub

### 未來

- g0v conquer the world 未來可以推到全世界其他國家（快買 domain!）
- 付費的話訂閱的頁面可增加或是設定用 twillo text message


## 問題

1.  如果有人新增廣告或不相干的 project 連結該怎麼處理？
2.  如果一個網是政府 host 但是 domain 不是以 gov.tw 怎麼辦
3.  全球政府關聯 Keyword 標準：
    1.  用 SDGs 永續發展目標當成其中一種 keyword 類別來 mapping




## 徵求

- [ ] 電腦螢幕是好的人
- [ ] Coolest name
    - [ ] gov-mirror (sounds like gov-zero by @wildjcrt) /// gov-zero present g0v-mirror
    - [ ] YAGOV (yet another gov by @widjcrt)
- [ ] 工程師
    - [x] 關鍵字分析 yuting
    - [x] 網站 diff 分析 chihao
> sitediff [https://github.com/evolvingweb/sitediff](https://github.com/evolvingweb/sitediff)
> [name=chihao y]

    - [x] kimono-like 抓資料的簡易工具 poga
- [ ] 設計師
- [ ] UI designer
- [ ] ideas


## Github & Slack

- [https://github.com/g0v/g0v-shadow](https://github.com/g0v/g0v-shadow)
- g0v-tw.slack.com [**#g0v**](https://g0v.hackpad.tw/ep/search/?q=%23g0v&via=ta138sdLdND)**-shadow**

## UI ref


change this to dark/hacker style


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d0f432a35df4c893165c289086917435)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6f9bc6a35fc3e676dd760102c0339673)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b5b9342f64294289ef3b3a2564676d08)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_000e2516bbd295a64b3818ce93277550)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bbc9addfda449428b1a9755aead28b42)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fe88b9ee5135de05345b162f2e9c0f01)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9a91697a894ba6c0ae051fb9e88ba4ea)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_828d913c7e0fa5759a93630b9d9105a5)

## Prototype

將任何 *.gov.tw 的網址改為 *.devpoga.org 即會看到頁面。

相關連結後台：[https://airtable.com/invite/l?inviteId=invJCGbCJYgxxsXxc&inviteToken=413e4009250b1f845f7396bdc3e6cb4aee9c344a1dc9ef757d7f81139537bf9c](https://airtable.com/invite/l?inviteId=invJCGbCJYgxxsXxc&inviteToken=413e4009250b1f845f7396bdc3e6cb4aee9c344a1dc9ef757d7f81139537bf9c)


---
title: Rentea 第 0 次小聚
tags: Rentea
---
# Rentea 第 0 次小聚

Rentea 的首次小聚來啦～這次小聚以專案開發為主題，無論你是設計師、工程師，或是對專案有興趣，是否已經跳坑，都歡迎來參加！

- 時間：2019-08-21 （三） 19:00 - 21:00
  - ddio 18:30 就會先到，想要先來吃吃喝喝聊聊天也沒問題
  - 活動 19:00 正式開始，會晚到或早走都歡迎
- 地點：由你咖啡 Union Kaffe
   - 地址：台北市松山區八德路四段245巷52弄29號
   - 交通：捷運南京三民站 2 號出口，[步行三分鐘](https://goo.gl/maps/hGEU1MbRgmUt7wXJ8)
   - 低消：一杯飲料，[菜單請見官方臉書](https://www.facebook.com/pg/unionkaffe/photos/?tab=album&album_id=2217593481858013)
- 專案資訊：
   - [Hackfoldr](https://beta.hackfoldr.org/rentea) / [Slack](https://g0v-tw.slack.com/messages/CJTBP7YRK/details/)
   - [Figma Wireframe](https://www.figma.com/file/Z0Wsc63DYpXLouSC7vvpw5aR/rental?node-id=0%3A1)
   - [程式開發指南](https://g0v.hackmd.io/jg_TRTEbRxyV-osQptSqwQ) / [爬蟲設計](https://g0v.hackmd.io/Bv_1JeHoT1O8gIjFBEJROg?view#%E8%A8%8E%E8%AB%96%E7%B4%80%E9%8C%84%E3%80%81%E7%B5%90%E8%AB%96%E3%80%81%E5%BE%85%E4%BD%9C) / [資料庫設計](https://g0v.hackmd.io/BFd56MJAQqu242x_oqYP2w)

## 參加者打卡區

想要參加的人請先在這裡打卡，方便確定人數，也記得寫一下想來作什麼，可以是開發東西、學程式、幫忙紀錄，或是任何想做的事情都可以～

- ddio - Rentea 專業打雜 - 想把爬蟲和資料庫弄到會動 + 想收集有趣的小聚地點！
- York - Rentea 專業推坑人 
- pTau - Rentea 專業~~被推坑~~ 
- Yukai - 花式開坑~~棄坑~~
- chriske - 確認需求、瞭解具體資料欄位與資料結構、詢問資料重複等等相關問題
- Steven - 協助開發爬蟲與資料庫
- Moojing - 協助前端開發
- Brody PM 幫忙弄UI UX（臨時可以來，可坐地上）
- Chloe - 了解目前設計的狀況


### 任務認領

1. [x] 現場小記 @chloe && @Mooji
2. [x] Rentea Monthly @york - 2019-08 - 範例：https://g0v.hackmd.io/KM6GyMh8SgCdUTjoFxWFXw

:::info
<i class="fa fa-home fa-lg fa-fw"></i> [回到 Hackfoldr](https://beta.hackfoldr.org/rentea/https%253A%252F%252Fhackmd.io%252Fs%252FSJbOIFHpE)
:::

### Rentea Weekly

- 徵求 Rentea Weekly 八月小幫手，整理每個人每個月在 Project 裡面做的事情。 
    - Ｙork認領，ddio需要開權限

- 目前的[爬蟲 Server 版本](https://github.com/rentea-tw/rentea-crawler)是版主之前專案用的爬蟲，用來抓全 591 網站的資料，想跳坑的人可以加入 Github org.
    - docker base
- 目前有一些[issues](https://github.com/rentea-tw/rentea-crawler/issues)待解：
    - Verify crawler performance and find best 
        -  決定爬蟲的頻率（多久爬一次）  
    - Enable Sentry i crawler
        -  檢查591是新的防爬蟲並驗證目前的爬蟲是否依然有效
    - Create unit test for periodic591 spider
        -  爬蟲的Unit test

- 需要知道有哪些資料筆數的狀態有改變 （Update Detection)，但應該可以拿之前開放台灣租屋資料的專案來Merge 。 (https://github.com/g0v/tw-rental-house-data)


- 說明目前schema 
- ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_76a119891ea1c9a115aa4e64706fb508)


- DB建議支援GIS(用於搜尋地圖)
- DB與爬蟲中間需要介面
    - Raw House 和 Unique House 塞的時候要怎麼處裡


- 社會住宅包租代管
- 固定欄位

- microservice

- [Sentry 坑](https://github.com/rentea-tw/rentea-crawler/issues/3)：順便知道 Scrapy 怎麽寫
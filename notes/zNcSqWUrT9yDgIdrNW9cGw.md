---
title: Taiwan ADIZ Records
description: Collect open records about Taiwan ADIZ(防空識別區) reports around the world.
image: https://upload.wikimedia.org/wikipedia/commons/thumb/7/72/Taiwan_location_map.svg/200px-Taiwan_location_map.svg.png
tags: Taiwan, ADIZ, 防空識別區, 軍機擾台
---

# Taiwan ADIZ Records

![](https://upload.wikimedia.org/wikipedia/commons/thumb/7/72/Taiwan_location_map.svg/399px-Taiwan_location_map.svg.png)
Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Taiwan_location_map.svg)
Author: [NordNordWest](https://commons.wikimedia.org/wiki/User:NordNordWest)
License: Creative Commons Attribution-Share Alike 3.0 Unported

## 計畫緣起
- 自 2020 年 9 月起，中共軍機開始頻繁的侵犯台灣的防空識別區（ADIZ），根據[中央社的新聞（2020-10-11）](https://www.cna.com.tw/news/firstnews/202010110133.aspx)，台灣截至同年 10 月 7 日已花了 312 億因應。為了能夠更全盤的了解台灣的軍事現況，希望能透過**爬梳即時軍事動態資料**，提供**簡易的統計數據**及**資料視覺化呈現**，讓關心台灣的鄉民快速得了解台灣國安的現況。

## GitHub 原始碼
- [爬蟲程式](https://github.com/felixshai/mnd_ADIZ_news_crawler)
- [資料視覺化網站](https://github.com/felixshai/Taiwan_ADIZ_alerts)
- pm5> 幫解放軍空軍建了個 GitHub 帳號 https://github.com/pla-air-force 

## To-Do List
### 資料下載
- [x] [中華民國國防部即時軍事動態](https://www.mnd.gov.tw/PublishTable.aspx?Types=%E5%8D%B3%E6%99%82%E8%BB%8D%E4%BA%8B%E5%8B%95%E6%85%8B&title=%E5%9C%8B%E9%98%B2%E6%B6%88%E6%81%AF)
    - [x] 下載每則即時軍事動態
    - [x] 從每則 PDF 檔拉出第 2 頁所提供的地圖示意圖
    - [x] 儲存資料在資料庫、地圖上傳 AWS S3
    - [x] 建立工作排程系統（Job Scheduler）每天自動完成以上的工作

- [ ] [Plane Finder](https://planefinder.net/)
- [ ] [日本航空自衛隊](https://www.mod.go.jp/js/Activity/Scramble/Scramble2021.htm)

### 資料視覺化網站

- [ ] 首頁提供簡易的統計數據（本月、本季、今年累積多少次共軍擾台）
- [ ] 首頁底下提供最新的單日報告
- [ ] 以日期做固定連結，單頁呈現文字及圖片報告
- [ ] 網站架構符合[開放資料的五顆星](https://5stardata.info/zh-TW/)

### 遠程目標
- [ ] RWD(Responsive Web Design)
- [ ] PWA(Progressive Web App)


### 其他

- 戰機來自於哪些軍事基地？
    - 網友有整理一份地理資料：中國人民解放軍基地及設施 (海軍、空軍、戰略支援部隊、重要戰訓基地及核心軍事機關) https://goo.gl/maps/QXXWAE7PjJoqRmmN6
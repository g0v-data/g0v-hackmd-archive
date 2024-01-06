---
title: "新聞連連看 story-tracer"
tags: hackpad
---

# 新聞連連看 story-tracer

> [點此觀看原始內容](https://g0v.hackpad.tw/0oYeM9wOR0L)

視覺化呈現新聞與新聞間的關聯

## 來龍去脈（想解決什麼問題）

### 起源

    最初是從 Muser 與 ETBlue 的 [討論](https://twitter.com/caasih/status/342112581051379712) 中得到靈感。

### 主旨

    希望能藉由使用者自己建立的，文章與文章間的關係，表現該使用者的思考脈絡。並讓他能將此脈絡與討論分享給其他人。

    有鑑於自己相信程式爬文建出來的網路，多少會有錯誤或是不完善，我認為如果想表現閱讀一則文章時，聯想到的其他主題，最後還是將「建立連結」這件事情，交給人們手動處理，才能保證成果可以表現建立該關聯的人的思考脈絡。

    加上純粹 HTML 超連結在一般情況下，沒有被視覺化，也無法協作，故開始此專案。

### 牽涉領域

- 新聞

### 現有類似專案

- [人物關係圖](https://github.com/zbryikt/ppllink)（連線部份）
- [Microsoft Live Labs Pivot](http://www.youtube.com/watch?v=BZuFUZpEZ-A)（操作部份）

### 相關組織單位

- 無

### 相關專案

- [news-diff](https://github.com/clifflu/news-diff)：希望未來可以以其當文章來源

### 授權方式

- 程式碼：MIT
- 資料來源：按來源的規定

### 使用資料

- MoreText

### 專案目前狀態

- 雛型：[http://story-tracer.herokuapp.com/](http://story-tracer.herokuapp.com/)


## 目標與功能（要如何解決）

### 預定使用者

    看文章時，希望把聯想到的事情記起來的人。

### 預定功能

- 加入新文章
- 分析並呈現新聞文章
    - 表現版本差異
- 選取文字
- 製造連結
- 描述連結關係
- 調整文章大小
- 縮放整個關係圖
- 註解與留言

### 使用方式

- 製作自己的文章關係圖
- 修改別人的關係圖
- 對別人的關係圖發表意見


## 實做細節（非技術背景可跳填）

### 使用技術

- node
    - express
    - LiveScript
    - request
    - entities
    - cheerio
    - bower
- web
    - ember
    - font-awesome

### 協作工具

- github repo：[https://github.com/caasi/story-tracer](https://github.com/caasi/story-tracer)
- hackfoldr 工作資料夾網址：尚無
- google drive 共用資料夾網址：尚無

### 進度與 TODO

> 僅供參考
> [name=ET B]

- [ ] product planning（recommanded procedure from justin lee / 李易修）
    - [ ] strategy
    - [ ] scope
    - [ ] structure
    - [ ] wireframe
    - [ ] visual
- [ ] web front-end
- [ ] web back-end
- [ ] ui / visual design

### 技術問題

- 如何取得一個字的 bounding-box
- 如何縮放各個 story 與整個 board 又不影響效能
- ember.js v.s. canvas v.s. WebGL

## 開發者

### 分工與成員

- [x] NeedsDesigner: 需要介面設計
> 現在只套了個 Flat 的配色。
> [name=caasi H]

- [x] NeedsData: 需要資料
> 從來源得到文章 html 後，我還得處理過才行。
> [name=caasi H]

- [x] NeedsTech: 需要技術支援
> 如上節的**技術問題**。
> [name=caasi H]

- [ ] NeedsProcess: 需要幫忙設計作業流程
> 設定成 project registry 中的 tags，需要幫忙的會自動 promote 到 g0v project hub
> [name=ET B]



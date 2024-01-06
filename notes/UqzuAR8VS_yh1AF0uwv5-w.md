---
title: "投票指南系列-設計共筆"
tags: Design,hackpad
---

# 投票指南系列-設計共筆

> [點此觀看原始內容](https://g0v.hackpad.tw/iRTizrchwng)

立委網站：[http](https://vote.ly.g0v.tw/)[s](https://vote.ly.g0v.tw/)[://vote.ly.g0v.tw/](https://vote.ly.g0v.tw/)
議員網站：[https://councils.g0v.tw/](https://councils.g0v.tw/)

專門討論優化投票指南設計的地方
如果這是你覺得好的設計，那可以投身到其他專案
如果這是你覺得需要改進的設計，歡迎跳坑救救投票指南

## Review with OCF

2017-11-07

選區的列表
- [ ] 增加議員配合款內容的連結
- [ ] 各欄可排序的功能
- [ ] 名字增加連結到個人頁面

選民互動功能
- [x] 議案、表決，列出已被、尚未被標籤的搜尋功能
- [x] 下標籤的位置不要放左上
- [x] 首頁有隨機的議員提案，可下標籤、投票
- [x] 下完標籤後可分享，og需要改圖片和文字，要有可擴散性
- [ ] 寫政見，增加政見的分類標籤

## 找子龍看醫生

### 2017-08-11討論內容

1.  Johnny先介紹網站功能
    1.  四大功能：表決、提案、議員配合款、可能參選人
2.  以下分各個功能檢討：候選人、表決、議員配合款／工程建議款、議員個人頁面

#### 現階段的調整指南

- 讓色彩、元件樣式統一，不要使用過多的色彩或是文字大小
- user的許願需要整體評估再投入進去做，不需要有求必應
- 釐清網站的重點功能：投票指南的資訊呈現，之後才是更深入的資料或是互動
- 手機版本的畫面和功能必須加以測試

#### 首頁

- [x] 改回選縣市，這是一般使用投票指南的最重要入門功能，必須在首頁做呈現與引導
- [x] 「可能參選人」或是未來有任何需要推廣的活動可能改用 banner 放在選縣市上方
- [ ] 「可能參選人」的用字，改更好懂一點（辦投票）
- [x] nav bar 改成跟 footer 同色
> 有收到關於「可能參選人」的意見：現在表單是要大家填完整的議員參選資料，但這可能對一般大眾門檻有點高，是否提出「單一一條政見」會來的參與度高一些呢？
> [name=Moon C]

> 只發表政見的話是匿名嗎？匿名會產生的問題我還想不到怎麼解決
> [name=ly t]


#### 候選人

- [x] 當選註記和得票數合併，名字排第一欄，醒目一點
- [x] 政治獻金 icon 拿掉
- [x] 游標有手勢出現，卻沒有連結可按
- [x] <bug>沒有政治獻金的議員出現 error
> 沒有該年競選資料的議員，在個人頁不顯示政治獻金選項
> [name=ly t]

- [ ] 各屆表現總覽放個人頁面
- [ ] 競選政見的用字（年度不統一難懂）
- [ ] icon 代表的意思有統一的解釋區（例如表格上方）

#### 表決

- [x] 該縣市如沒有表決要標註

#### 提案

- [x] 選區搜尋框改沒有圓角，跟其他統一

#### 議員配合款／工程建議款

- [x] 統一用字
- [ ] 個別工程款項怎麼讓使用者參與？
- [x] 南投下方有多條靈異<hr>

#### 議員個人頁面

- [ ] ~表決、提案的 tab 收進左邊，像 hackfoldr~
> 直接改設計了
> [name=ly t]

- [x] 表決、提案等選單字體大小降級，不要超過名字
- [x] 往上滑的時候，留第二層 menu 在 top
- [x] 立場統整頁面，把標籤和次數分不同行，表決1變成按鈕，向左切齊下方內容，下方內容字體降級縮小
- [x] 立場統整頁面框跟框對齊
- [x] 個人表決總覽頁面，大面積色塊改色小點
- [x] 以贊成、反對搜尋的按鈕移到搜尋按鈕右邊，改成同顏色
- [x] 按鈕的字都有陰影影響閱讀，把陰影拿掉
- [x] 下拉選單底色改成和按紐同色、同寬，字的顏色統一
- [ ] 表決看要不要做跟其他黨籍的圓餅圖
- [ ] 和其他黨籍的圓餅圖抽出成為獨立的 tab
- [x] 只看第一提案人的按鈕移到搜尋框右邊，和搜尋按鈕同一行
- [x] <bug> 提案總覽頁面往右shift了（連footer都是）
- [x] 工程建議款的廠商圓餅圖拿掉
- [x] 工程建議款的細目展開，直接連到搜尋完的suggestions/lists/ 頁面
- [x] 政見頁面，標題和內容分開，避開 mac 字體粗細問題
- [x] 政治獻金也拿掉 icon

#### 搜尋

- [x] 搜尋的 summary 字體降級縮小
- [x] 熱門搜尋、熱門議題統一顏色

討論圖、過程
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_df18a2b878cf9a8a47b1502f995ffa22)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_80a8b0b8ed9fe45109705c60880980a8)

## 專案連結

[立委投票指南](https://vote.ly.g0v.tw/)
[議員投票指南](https://councils.g0v.tw/)

### UI：

[Mockup](https://invis.io/6G5EW3XP5)

### UX:

[架構圖：](https://g0v.hackpad.tw/UU3SnmXugVZ#架構圖：)
[Card Sorting](https://g0v.hackpad.tw/QzWpgXhtRCK#Card-Sorting)

### Feedback:

[意見回饋](https://g0v.hackpad.tw/--dMc3UYvwTjT)
[開issue](https://github.com/g0v/twly-voter-guide/issues?q=is%3Aopen)
[易用性測試 Usability test](https://g0v.hackpad.com/yxrIYtdhyzF#易用性測試-Usability-test)


[2015/4/18 黑客松：立法院表決資料分析](https://g0v.hackpad.tw/76CBR5VkIQn#:h=使用者要什麼東西)


Github:[https://github.com/g0v/twly-voter-guide](https://github.com/g0v/twly-voter-guide)
網站圖檔連結：[https://drive.google.com/folderview?id=0B0NsS2a-Qx8ZNm45V0hBR3Jhb2M&usp=sharing](https://drive.google.com/folderview?id=0B0NsS2a-Qx8ZNm45V0hBR3Jhb2M&usp=sharing)

相關產品分析：
[誰是立委大聲公？ 候選人社群聲量大搜查](http://p.udn.com.tw/upf/newmedia/2015_data/20151208_udnlegislatorsocialmedia/udnlegislatorsocialmedia/index.html)
[立委在衝啥毀](http://legislator.thenewslens.com/index.html)
[立委做設麼](http://2016legislators.tumblr.com/)
[選戰溫度計](https:// http://vote2016.dailyview.tw/Legislator)
[網路國會](http://capitol.tw/)

## 問題整理

### 待解任務：

目前功能健全，缺整體性的整理與規劃
希望跳坑的設計師可以在大系統下維持一致性！
以下任務歡迎隨時更新

- [ ] 整體統一的視覺
    - [ ] 色系規劃、字體大小等等
    - [ ] 細節（像是文字的可讀性
    - [ ] 首頁地圖的呈現
    - [ ]
- [ ] 更佳的使用引導
    - [ ] 動線引導
    - [ ] 資訊層級規劃
    - [ ] 卡牌的呈現
    - [ ] 按鈕互動規劃
- [ ] 手機版 UI 規劃

一些明顯問題說明：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_14ec2aea3b786b3fc88b39eb61794e66)

## 徵求

挖坑工人：
- [ ] 挑毛病開任務的設計師（找到問題，填到hackpad中開啟任務）
填坑工人：
- [ ] 視覺設計師（規劃logo\\整體視覺系統）
- [ ] UI介面設計師
- [ ] UX使用者經驗設計師

嘗試跳坑：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_40f91c1dbfebc039aa644576177c2dc0)

## Logo redesign

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7c7c996c4dcb1d33b408030bf00bb779)


## web redesign

2015.10.18
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_37ab8a6e7ff244c791b5c688ae0e4aaf)


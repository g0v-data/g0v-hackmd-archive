---
title: "[PPT] RoadMap"
tags: Promise Tracker,hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/BL7M4HtxYTk)


#### ＊專案上層 Hackfoldr：[http://beta.hackfoldr.org/ppt](http://beta.hackfoldr.org/ppt) ＊


## g0v-hackath15n TODO

先把桃園的歷史資料處理好，將網站功能完整呈現。

- [ ] 整理 [PDF 存檔區](https://drive.google.com/drive/folders/0B1tiWyU4jeiofjJoQ29RRVN5VDlKVnJYQWJSV183bl9vdGFwVHV1YTdPaDJ1LVhsLTFxWXc) 成下列結構：`地區資料夾 / 日期.pdf` 並且更新連結。
- 處理歷史承諾步驟：
    - 初步人工排除機器處理承諾的錯誤
    - [取 feature 產生 similarity matrix](https://github.com/MrOrz/ppt-commitment-matcher)  並且放在 spreadsheet 上
    - [編輯 similarity matrix](http://beta.hackfoldr.org/ppt/https%253A%252F%252Fdocs.google.com%252Fspreadsheets%252Fd%252F13VnIEo-yvm0nfbG7saUx60Zhd50Q_rwHCMILAMyu7wQ%252Fedit%2523gid%253D36188101) ，把配對的 commitment 的 similarity 設成 1
    - 人工處理承諾，把「進度」與「承諾」分開，並且評定完成度
- 「similarity matrix 放進 spreadsheet」處理進度
    - [x] 1040417-1030804
    - [ ] 1030804-1030331
    - [ ] 1030331-1021001
    - [ ] 1021001-1020401
    - [ ] 1020401-1011005
    - [ ] 1011005-1010529
- 「人工處理承諾，把「進度」與「承諾」分開，並且評定完成度」進度
    - [x] 1040417
    - [ ] 1030804
    - [ ] 1030331
    - [ ] 1021001
    - [ ] 1020401
    - [ ] 1011005
    - [ ] 1010529
- [ ] 將 spreadsheet 內容處理進資料庫


## 歷程

### 2015/8/2 以前


先用[自動工具](http://github.com/g0v/ppt-commitment-parser)處理承諾文檔，放在 [7 月萌典松工作區](https://docs.google.com/spreadsheets/d/1EefGM7p3xlSMOcTFo5i8WkWbiZhwoBFv0rezFLIwUDo/edit#gid=1016570619)，並且將此 Google spreadsheet 與過去的[承諾資料表](http://beta.hackfoldr.org/ppt/https%253A%252F%252Fdocs.google.com%252Fspreadsheets%252Fd%252F11Owh0XvHIqrLil4y9wvwq0f9VGBJueijbUSm5qCJch0%252Fedit%2523gid%253D1810583590)做匯整。

目前 104 年桃園承諾放上網站看起來像這樣：
[https://promisetw.herokuapp.com/governor/%E6%A1%83%E5%9C%92%E5%B8%82%E6%94%BF%E5%BA%9C](https://promisetw.herokuapp.com/governor/%E6%A1%83%E5%9C%92%E5%B8%82%E6%94%BF%E5%BA%9C)

目前先試著將桃園的歷史施政資料一併做個整理，這樣就能看出哪些承諾是新加的，哪些承諾一年都沒有進度，又或者可能會發現有些承諾默默地再某一年的施政報告中消失了。

接下來 [Johnson Liang](https://g0v.hackpad.tw/ep/profile/z4JarLrJBea) 會處理 103 年度的桃園承諾，並且心寫程式來比對 103 年的承諾與 104 年的承諾。


### 2015/7/18 moedi11ct 以前


主要分為「承諾資料」（TXT 組徵求中）、「進度資料」以及「程式」兩塊。
資料來源請見左欄「資料來源」
有意願認領的人請在項目後 tag 自己簽名 m(_ _)m

#### 承諾資料

先集中火力，將六個直轄政府的承諾寫進[「承諾」資料表](http://beta.hackfoldr.org/ppt/https%253A%252F%252Fdocs.google.com%252Fspreadsheets%252Fd%252F11Owh0XvHIqrLil4y9wvwq0f9VGBJueijbUSm5qCJch0%252Fedit%2523gid%253D1810583590)。

- [ ] 台北市 \- 可直接整理自[市長承諾一覽表](http://hacktabl.org/taipei-mayoral-election-2014)
- [ ] 新北市 \- from [市長施政報告](https://wedid.ntpc.gov.tw/Content/eBooks/book1-1/index.html) \- by [Johnson Liang](https://g0v.hackpad.tw/ep/profile/z4JarLrJBea)
- [x] 桃園市 \- by [Yi Sheng Wang ](https://g0v.hackpad.tw/tFssEKNFyrW#Yi-Sheng-Wang-)
> [Yi Sheng Wang](https://g0v.hackpad.tw/tFssEKNFyrW) 我們將你所整理的承諾，跟後來匯整的資料一起放到 [https://promisetw.herokuapp.com/governor/%E6%A1%83%E5%9C%92%E5%B8%82%E6%94%BF%E5%BA%9C](https://promisetw.herokuapp.com/governor/%E6%A1%83%E5%9C%92%E5%B8%82%E6%94%BF%E5%BA%9C)  囉！
> [name=Johnson L]

> 我們會在 [Facebook 社團討論](https://www.facebook.com/groups/1603577519893717/)，歡迎一起加入 :)
> [name=Johnson L]

- [ ] 台中市 \- from [林佳龍官網](http://hope2014.citylove.org.tw/pdf_files/bigtaichung.PDF) \- by 宏圖
- [ ] 臺南市
- [ ] 高雄市
> 不好意思！對g0v很少接觸，很多部份都不熟悉，但我對這個專案很有興趣，也從發起時一路潛水至今，不知是否可以協助桃園市部份的政策彙整呢？
> [name=Yi W]

> 當然可以！在上面簽名打勾就對了 XD
> [name=Audrey T]

> 有看到相關網址也請貼上。
> [name=Audrey T]

> [Yi Sheng Wang](https://g0v.hackpad.tw/ep/profile/vbZcLmAu501) 謝謝你的關注 :)  看到您從市議會施政報告截取的資訊了！！
> [name=Johnson L]



#### 進度資料

預計從新聞以及 2015/4 六都的市長施政報告來截取。目前尚未開始。

#### 程式

- [ ] Google spreadsheet --> Mock data parser (見 \`server/boot/seed-mock-data.js\`)
- [ ] 用 Material-UI 取代 Semantic UI - by 宏圖

### 2015/4/18 g0v-hackath13n 以前

- [x] Livereload to make developing a happy process
- [x] Combine React.js mockup with mock data directly in React
- [x] Add React.router
- [x] Add Flux
- [x] Move mock data into in-memory database, serve from API.
- [x] flux actions that fetch data from api and put data in stores -- 改成用 React-transmit，已可以從 DB 撈資料顯示。


## 徵求協作者


發起人/拋磚人：  [Johnson Liang](https://g0v.hackpad.com/ep/profile/z4JarLrJBea)
分工與成員
- [x] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
- [x] NeedsDesigner: 需要介面設計
- [x] NeedsData: 需要資料（擷取、清理）
- [ ] NeedsTech: 需要技術支援（程式、架站 etc)
> My turn
> [name=Shelling F]

> 如果有 entity extraction 等 NLP 技術人的話，可以減少更多的資料處理人力！
> [name=Johnson L]

- [x] NeedsProcess: 需要幫忙設計作業流程
- [x] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡
> 設定成 project registry 中的 tags，需要幫忙的會自動 promote 到 g0v project hub
> [name=ET B]

> 需要界面流程設計的部分我可以幫忙
> [name=Obelai c]




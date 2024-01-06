---
title: "社會議題追蹤網"
tags: hackpad
---

# 社會議題追蹤網

> [點此觀看原始內容](https://g0v.hackpad.tw/8OJGjMMTItF)

專案介紹 | Project Readme / Meta

做一個類似 issue tracker 的系統，來追蹤各種社會議題，避免太多新聞事件導致有些重要的事情被轉移目標（例如林益世貪污案被另一件事給救了）。不過八卦事件原則 上不追蹤（例如某大爺酒駕撞死人），這個系統只整理政治、人權、社會公益等等的事件。

## 來龍去脈


### 主旨

> 怎麼想到要做這個東西/想達成什麼... etc.
> [name=ET B]


### 牽涉領域

> e.g.教育 / 環保 / 醫療 / 社福 / 核電 / 都市計畫 / 勞工權益 / 食品安全 ...（會變成專案 tag）
> [name=ET B]


### 相關組織單位

> e.g.公督盟/綠盟/司改會/苦勞網/泛科學...（會變成專案 tag）
> [name=ET B]


### 相關專案

> 衍生自某專案/衍生出某專案/API串接自某專案...etc.
> [name=ET B]


### 授權方式

- Code: MIT License
- Content: CC (?)

### 使用資料


初期先全部由使用者自己貼，之後再來想接別站的資料

### 專案目前狀態

> 構想 / 規劃 / 雛形 / 實作
> [name=ET B]

規劃功能中

## 目標與功能


### 預定使用者


一般大眾

### 預定功能


- 開票
- 指票給負責的單位/負責的人
- 更新票的進度
- 關聯票
- 票打 tag
- Milestone (大事紀)

### 使用方式


- 參考軟體開發的 issue tracker 的操作方式，但要簡化到沒有軟體專業的人也會用
- Facebook 登入
- //TODO

> 從 [https://g0v.hackpad.com/ZhayTz2Om0n](https://g0v.hackpad.com/ZhayTz2Om0n) 轉貼來的，待整理
> [name=&#33674;&#32946;&#25215;]


> 初步的構想是像 Redmine 這種東西，每個議題 (issue) 有自己的頁面，每個議題可以更新當前的狀態，介面像是 Facebook 動態時報，最新的消息放在上面。
> [name=&#33674;&#32946;&#25215;]

> **comments:** 剛剛討論想到另外一個類比是 twitter ，每個議題相當於是一個帳號，帳號的 tweets 就是該議題的更新（含新聞、blog 看法……）。進入該議題的頁面（twitter 個人頁）會顯示出所有的新聞、blog文章等等（更新）。自己可以去 follow 帳號，也就是可以 關注議題，所以在自己的  timeline 上會看到所有關注議題的更新。
> [name=&#23567;&#34809; &]


> 議題可以 assign 給負責人，例如智財局要推鎖網法，就把這事 assign 給智財局長。當然系統裡不會內建他的帳號，要找個方法表現出這是他要負責的。 assignee 可以多個人。
> [name=&#33674;&#32946;&#25215;]


> 貼新聞或引用他人在 blog / Facebook 的評論，可能會有著作權的問題？當然超連結一定要附上。
> [name=&#33674;&#32946;&#25215;]


> 若要自動抓新聞的話或許可以接「社會議題懶人包」？ Google 電子快訊？
> [name=&#33674;&#32946;&#25215;]

> 可以去接[http://www.news-pac.com/](http://www.news-pac.com/), 已經有RestAPI, VCS: [https://github.com/radjan/newspac](https://github.com/radjan/newspac)
> [name=HisnYi C]

> 例如去對方 API 抓相關新聞，推薦使用者將它加入這張票。
> [name=&#33674;&#32946;&#25215;]



### 關於更新議題


更新議題是要手動進行的。

要維護每個議題也很累的，萬一沒人維護的話漏掉新聞就糟了。或許有些可以讓關心這件事情的人來當志工認養？例如樂生事件，可以請樂生青年的朋友來維護。

誰來把改票的狀態 (state) ？例如誰可以 confirm / reject / mark as duplicated / close 票。一開始一定是少數人才能改 state ，要開放誰可以改？又，有哪些狀態可以用？

議題是否成案 (confirmed) 可以透過投票方式？但這樣會 slowdown 整個流程。

### 關於議題的 tagging


誰可以改 tag ? （我傾向每個人都可以改）

防亂改？ rollback 機制？

福利請聽的做法是大家都可以 propose tag ，由站務來審核。

另外又想到一個方法是大家都可以加 tag ，但可以提 abuse 。

### 關於共同關注議題


1.  大家要可以共同關注議題。相同的議題盡量不要有重複的票出現。所以議題應該都是 public ，然後大家都可以都可以 follow （比較接近 twiiter follow）。最新議題和熱門議題，應該要放在首頁，讓新使用者可以輕鬆的關注，不會產生重複的議題。
2.  議題應該要有管理員，因為議題的 state 會變化，要設定 milestone ，要新增/移除 tags 等等。其他人都應該只是 follower，只能關注和留言。管理員還要可以允許其他人加入管理員，接收新增/移除 tag 建議等等。
3.  議題的更新來源是 社會議題專案的爬新聞的來源 api ，所以爬新聞專案的規劃裡面，本身就有 tags ，因此議題專案應該只要透過 api 去問有哪些 tags 可以下。

> 要有方法來把熱門事件給放在首頁顯眼的地方。
> [name=&#33674;&#32946;&#25215;]


### 關於懶人包


更新事件的時候可以設 milestone ，例如林益世貪污案宣判結果出來了，就設一個 milestone。瀏覽 timeline 的時候以 milestone 為主，在 milestone 下面再貼新聞、參考資料、評論等等。

單一議題#show 的頁面會長得像是懶人包，一次顯示出所有的 milestones ，然後會像 wikipedia 手機版介面，可以收合。

> 要開放 API ，讓別的程式可以直接抓到這個網站上的資料，動態時報也可以開放 RSS 。
> [name=&#33674;&#32946;&#25215;]



## 實做細節


### 使用技術與工具


- Ruby on Rails
- 使用的 vagrant box 版本 / 網址：
- hackfoldr 工作資料夾網址：

### 產出檔案格式


- 會提供 JSON API
- 會提供 RSS

### 進度與 to-do


- [ ] product planning（recommanded procedure from justin lee / 李易修）
    - [ ] strategy
    - [ ] scope
    - [ ] structure
    - [ ] wireframe
    - [ ] visual
- [ ] web front-end
- [ ] web back-end
- [ ] ui / visual design
    - [ ] based on Bootstrap

細節的票開在 GitHub: [https://github.com/chitsaou/twbug/issues](https://github.com/chitsaou/twbug/issues)

### 現有成果


- Repository: [https://github.com/chitsaou/twbug](https://github.com/chitsaou/twbug)

## 開發者


- 鴨七 @yorkxin

### 技術指導


### 分工與成員

- [ ] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
- [ ] NeedsDesigner: 需要介面設計
- [ ] NeedsData: 需要資料（擷取、清理）
- [ ] NeedsTech: 需要技術支援（程式、架站 etc)
- [ ] NeedsProcess: 需要幫忙設計作業流程
- [ ] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡
> 設定成 project registry 中的 tags，需要幫忙的會自動 promote 到 g0v project hub
> [name=ET B]





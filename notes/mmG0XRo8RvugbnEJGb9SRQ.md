---
title: "#選舉宣傳回報系統 專案介紹"
tags: hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/E9X1LqXJZz9)


## 專案簡介


### 緣由

柯文哲跟連勝文的選舉支出數字不相上下，你相信嗎？柯文哲說用膝蓋想也知道不可能，那我們是否可以做出一套流程跟工具，讓我們不用去問膝蓋，而可以做出一些合理的估計呢？

### 要解決的問題

每次大選候選人花了多少錢在宣傳曝光，包括實體大型看板、公車車廂內外廣告、報紙、雜誌、宣傳車、造勢活動（晚會等）、宣傳單、宣傳小物（如扇子、面紙）、旗幟、語音廣告等，這些經費怎麼估

### 預定使用者

台灣每兩年就有一次大型的選舉，這套流程跟工作現在可能是針對 2016 年的立委選舉所設計，之後可以針對不同的選舉作調整，讓社會大眾有效監督每次的選舉宣傳支出

### 預定功能

回報系統，針對不同的實體宣傳設計不同問題，以選單呈現，希望可以在三個問題內蒐集所需資料

### 預定工作

行銷推廣，如何擴大參與
整理估價方式、蒐集相關價目表, 例如 LINE 企業帳號收費標準 [http://www.applealmond.com/news/line3](http://www.applealmond.com/news/line3)

### 現有類似專案

- [https://roadkill.tw/download/app](https://roadkill.tw/download/app) \- 群眾提交內容與照片的平台
- [http://openstreetview.org/](http://openstreetview.org/)  [https://www.mapillary.com/osm.html](https://www.mapillary.com/osm.html) \- 開放的 openstreetview, 可 geotag 照片位置與角度，精確定位看板與推估尺寸
- [https://github.com/markaspot/mark-a-spot](https://github.com/markaspot/mark-a-spot)
- [https://github.com/ushahidi/platform](https://github.com/ushahidi/platform)
- [http://wiki.open311.org/GeoReport_v2/Resources/](http://wiki.open311.org/GeoReport_v2/Resources/)

### 相關專案



### 授權方式

程式碼部分視原始回報程式授權方式而定
照片、描述 CC0

### 監測範圍

＃大型戶外競選看板
＃報紙廣告
＃雜誌廣告
＃其他平面文宣(單張)
＃宣傳小物(扇子, 面紙之類)
公車內、外廣告
宣傳車
造勢晚會
網路廣告(手機版/PC版)
> 手機截圖沒有必要的metadata資訊, 如網站名稱等, 可能要額外問用戶一些問題。PC版廣告的監控必須要另外做瀏覽器外掛
> [name=Trevor H]

語音廣告
> App要有另外針對語音廣告回報時間地點等資訊的能力，但這種資料完全靠使用者自行回報，也不必提供其它佐證資料，恐怕很難驗證其真實性
> [name=Trevor H]

SMS、LINE短信廣告
旗幟

有#為優先監測項目

### 使用資料

回報人提供照片、網站截圖、手機截圖與其他和資料相關的metadata，如時間、地點
拜票語音 \- 回報時間、地點、受話的電話種類 （住家、公司、手機）
手機截圖可能不會顯示 url，需要手動填充

### 取得資料的管道：

手機拍照與上傳 App
瀏覽器截圖外掛
> Ronny的建議: 由於App的製作與上架需要花比較長的時間, 特別是iOS的App上架前需要通過Apple審核, 時間可能會拉得非常長(繼寬的個人經驗是公司的App上架審核前前後後就花了2個多月), 等App上架後, 選舉已經進行一大半了. 
> [name=Trevor H]

> 為了爭取時效, 不如讓計劃參與者直接把照片上傳到FB的社團頁, 再由志工做進一步資料清理, 這樣才能快速取得資料, 進行下一步分析作業.
> [name=Trevor H]


### 專案目前狀態

規劃中
手機App的規格需求: 報紙、雜誌廣告要額外問一些問題
pilot版先開放優先監測項目：
拍看板: 直接上傳到open street view來做資料校正補強
拍報紙: 問哪個報紙?  日期?  留版面欄位，可能需要人工補
拍雜誌: 雜誌名? 期數? 留頁數欄位，可能需要人工補
平面文宣: 直接上傳
宣傳小物: 直接上傳

PC瀏覽器外掛規格需求
截圖功能：理想目標是可以支援滾動截圖，不然可能會截不到廣告所在位置
網址記錄功能：直接紀錄該網頁url
上傳資料到後台資料庫
參考對象: Evernote的網站截圖外掛

後端資料庫?

行銷計畫:
成立FB社團
在PTT, G0V, FB等平台上進行宣傳, 吸引志願者加入我們的行列
行銷素材草稿
[https://docs.google.com/presentation/d/1C9PGXmxVAj\_8jNX43D3Z1q9eOzcNvl8-FybWNxL-A\_Y/edit#slide=id.p](https://docs.google.com/presentation/d/1C9PGXmxVAj_8jNX43D3Z1q9eOzcNvl8-FybWNxL-A_Y/edit#slide=id.p)
這份簡報還沒完成, 大家先點點看能不能讀
前台呈現?

### 功能設計上的疑慮

為避免觸及個資法，如何盡可能避免取得使用者個資，必須納入考量
verification 或舉發錯誤，制度如何設計防弊

### 利益揭露

（牽涉到哪些組織團體、有哪些已知的或潛在的金錢或物質或無形利益報酬）

### 其他參考資料

- LINE企業帳號收費標準 [http://www.applealmond.com/news/line3](http://www.applealmond.com/news/line3)
- [https://www.newschallenge.org/challenge/elections/evaluation/2016-political-ad-tracker-making-tv-ads-viewable-and-accountable-with-fact-checking-citizens-can-trust](https://www.newschallenge.org/challenge/elections/evaluation/2016-political-ad-tracker-making-tv-ads-viewable-and-accountable-with-fact-checking-citizens-can-trust)

## 徵求協作者

發起人/拋磚人：
- [ ] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
- [ ] NeedsDesigner: 需要介面設計
- [ ] NeedsData: 需要資料（擷取、清理）
- [ ] NeedsTech: 需要技術支援（程式、架站 etc)
- [ ] NeedsProcess: 需要幫忙設計作業流程
- [ ] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡


> 您好  [S Chen](https://g0v.hackpad.tw/ep/profile/E4G7fRJZRw8)  [Finjon Kiang](https://g0v.hackpad.tw/ep/profile/G4yGGowBe3x)  [Charles Chuang](https://g0v.hackpad.tw/ep/profile/qJOzQZUKo4m)我很有興趣，請問你們現在還有進行嗎？我的email：alan7492@yahoo.com.tw
> [name=Alan l]


## 實作細節（非技術背景可跳填）


### 協作工具

- github repo：
- hackfoldr 工作資料夾網址：
- google drive 共用資料夾網址：

### 進度與 to-do

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


## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_04de045fbde44ee84a4d8443d8aa2b2c)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_eb29073f92020a1bb9fa770f73cf07bd)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b042845978b64c6b389766ac01ecd457)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_623d21a9a34007e6913d52eeb3569aac)






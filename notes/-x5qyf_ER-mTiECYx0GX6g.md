---
tags: cofacts, meeting note
---
20200304 會議紀錄
=====

> 黑卡 ggm, 文武, mrorz, bil, darkbtf, lucien
> Norman, yang, 志超
>
> 上次開會紀錄：https://g0v.hackmd.io/@MODl5abnQpKy6ifB4DPGcQ/Syx9t9dXNL
>

## 網站設計
https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=0%3A1

- Date picker 外面統一，裡面看裝置（native input），開始、結束分成兩個 input 比較好做
    - native input 沒辦法點一下開兩個
- Menu: drawer 型態
    - 橫向設計會擺不下英文
- 「查核闢謠」需再確認

:::warning
需要有 wireframe 才能估程式設計時程
:::

## 3/14 大松籌備

活動共筆 Note：https://g0v.hackmd.io/@jothon/g0v-hackath38n

上次大松協作頁面：https://beta.hackfoldr.org/cofacts/https%253A%252F%252Fg0v.hackmd.io%252F%2540mrorz%252FHkvX_cP0S

ggm
category 那個時候做好了嗎

orz
UI + API 3/9 應該要好
DB migration：
1. + tag
2. 灌 flow 的資料 (每篇至多 3 label)

ggm
flow 要 3/13 給 7,500 篇標好的
應該來不及灌進去

我想到的是放在 google sheet 讓大家標
給 2/1X 之後的，那些 flow 不會標到

orz
理論上 UI 當時應該要可以運作
但直接上 production 不確定大家是否知道每個標籤的定義
大松的時候可以透過視訊確認

ggm
確實 flow 在標記之前也是有很多面對面討論

orz
那大松前暫時把 category UI 上線
大松後拿掉，等 flow 資料一起進來

大松時跟參與者討論標記定義是否清楚，該如何呈現才能有用 & 讓大家不要標錯

或者是 rumors-site 用 env var 控制是否可以 crowd-source label

---

orz
workis 組食物當天再看有多少好了～

- - -

在家組
- ggm 

Workis 組
- bil
- mrorz

:::success
3/14 前先拼 category 能上線
用 env vars 控制是否可以送出新標記
大松期間允許送出
:::

## 4 月台南小聚（第19次編輯小聚）

- [x] 主題：
    - 我:heart:台南
        - 主視覺：孔廟 牛肉湯
- [ ] 時間：4/18 (六) 2:00pm ~ 5:00pm
- [ ] KKTIX
- [ ] 攜帶貼紙
- [ ] 場地：會是[好想工作室](https://goo.gl/maps/MBd7jz6gDK3J3fJV9)（含場佈：1:00 ~ 6:00）
    - [ ] 茶水
    - [ ] 麥克風+插座+網路
    - [ ] 投影機
    - [ ] 延長線
    - [ ] 食物
    - [ ] 垃圾
    - [ ] Talk
    - [ ] wifi
        - [ ] Nighthawk M1 + 4G sim
        - [ ] ASUS RT-N12 Wireless N300 (2x 5dbi高增益天線)
- [ ] 誰會來呢？
- [ ] 誰不會來：
- [ ] LINE 文案

[1/29「嚴重特殊傳染性肺炎(武漢肺炎)」因應指引：公眾集會](https://www.cdc.gov.tw/File/Get/fVFJsQkfIBresjZxRxOWTA) from: https://www.cdc.gov.tw/Category/MPage/V6Xe4EItDW3NdGTgC5PtKA 

- 應變機制
    - 誰量體溫、> 幾度怎麼做、< 幾度怎麼做 etc
- 會前宣傳：透過多元管道(如邀請函、簡訊及活動網站等)向參加者進行衛教溝通
- 會中宣導：加強防範嚴重特殊傳染性肺炎與維持個人衛生習慣之衛教溝通並透過明顯告示

:::success
Howard 回應說會有
- 洗手用具
- 額溫槍或類似道具

三月底也會辦活動～
:::

## LINE chatbot 換 logo

檔案：https://drive.google.com/drive/folders/1nnOFuxW70m7OgGfAI3fVcB8ri2ugODki

bil
對方還沒給新的約


## 開發
GitHub activities
https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/WSQFB


### Invalid reply token
Deployed, very effective


### Polyfill
Deployed, very effective.

Bundle size 的影響未知。若大很多，可以考慮 `<script nomodules />` https://3perf.com/blog/polyfills/#modulenomodule

### RSS feed 調整
https://github.com/cofacts/rumors-site/pull/229
實作了：
- [Include latest replies in RSS](https://github.com/cofacts/rumors-site/issues/225)
- [Provide RSS options](https://github.com/cofacts/rumors-site/issues/223)

TODO: [Tracking RSS usage](https://github.com/cofacts/rumors-site/issues/222)

志超：哪一個是比較常用的

yang:
感覺 ifttt 跟 RSS 都比較進階
一般使用者只要知道用 email 訂閱或送到 LINE 就好
(或許可以分不同介面，給進階的藏深一點，給一般 user 的顯眼一點)

orz:
不過可能還是要讓使用者知道他會被導向到什麼服務
因為他要到該服務的網頁完成設定
之後寄信 / notification 的會是那個服務

IFTTT Applet 可以設計成讓使用者填某些欄位就好

先 merge https://github.com/cofacts/rumors-site/pull/229 才能繼續測 IFTTT Applet

:::info
先 merge
https://github.com/cofacts/rumors-site/pull/229

再 survey IFTTT applet
:::

### Tracking

Track usage on Cofacts website!

- [User ID](https://github.com/cofacts/rumors-site/pull/224)
- 不會觸發換頁的動作：voting reason, voting replies, submitting replies, 點開 subscription, etc --> 可能要用 [generic event tag](https://www.simoahava.com/analytics/create-a-generic-event-tag/) 處理
  - 或者用 nytimes 的 [react-tracking](https://open.nytimes.com/introducing-react-tracking-declarative-tracking-for-react-apps-2c76706bb79a)，但他其實也只是 [push to `window.dataLayer`](https://github.com/nytimes/react-tracking#custom-optionsdispatch-for-tracking-data)
  - https://www.npmtrends.com/react-metrics-vs-react-tracker-vs-react-tracking-vs-treacker
- Google Tag Manager 可以抓到哪些？
  - 手動給定 `displayName` 可[讓 production 保留 component name](https://github.com/facebook/create-react-app/issues/4081#issuecomment-427197629)
  - 可以透過 DOM 取得 component name

yang:
hotjar https://www.hotjar.com/pricing/6mqa0
UX 分析

orz
量化 --> analytics
值化 --> hotjar

yang
設定 displayName 可能不會讓人理解到這跟 analytics 相關，更像是 debug 用

orz
可以在 README 裡面提及
這些是 component of interest
production debug 的時候可以用，也能讓 GTM 追蹤被點擊的重要 component

:::success
- 埋 hotjar
- 先設定 displayName of important component
- 以後再看看要不要 react-tracking
:::

### Upvote, downvote for ppl not logged in
https://github.com/cofacts/rumors-site/issues/209

On staging now

### Show latest reply
https://github.com/cofacts/rumors-site/pull/230
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_838cf320e52e8606dbc21c85c1b45d5f)


### New issue: JS heap out of memory
https://github.com/cofacts/rumors-api/issues/151

### Fix image message bug
PR : https://github.com/cofacts/rumors-line-bot/pull/160

文武：
1. 有些 image 字很少
但我們有檢查 length > 3
如果圖只有 1~2 個字，就會一直回傳「請輸入 1~4 的數字，選擇訊息來源」

2. 同時傳 10 張有字的圖，就會很容易觸發 timeout
所以先用 global count
超過 3 張正在處理的圖
就會直接回 timeout 訊息
也不會下載圖


---
tags: cofacts, meeting note
---

20180926 會議記錄
=====

> Previous meeting note: https://g0v.hackmd.io/7GfT5p0MSVmoWrwgNEft8g?both
> 

## Dev updates

### Title available in reports!
- https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/NrUQ
- 21 號之後的資料不知道發生什麼事 QAQ
- 目前只有舊文章有 title，新文章不會
- 要讓新文章也有 title，需要等到這個 bug resolve: 
https://issuetracker.google.com/issues/111465522 (幫忙按 star，希望可以加速實作 XD)

:::warning
【問題】
發現 9/21 ~ 9/25 之間的 Article/Select 都壞掉了，~~好像是因為多送 document title `dt` 的關係，應該要盡快拔掉。~~ 因為 [function call 錯](https://github.com/cofacts/rumors-line-bot/commit/c2c59e4db34936c4ad1bd27ad9a95810f37c5ca2)，所以 hit 結構送錯了（event category 變成 user id, event label 變成一個 object⋯⋯）。

目前[已修復](https://github.com/cofacts/rumors-line-bot/commit/c2c59e4db34936c4ad1bd27ad9a95810f37c5ca2)。
:::

:::danger
【公告】

9/21~9/25 之間的 Article / Select event 因為實作錯誤，所以都沒有收到。這導致[報表中的 event 數歸零](https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/NrUQ)，相當嚴重 :weary: 。

9/26 之後應該就恢復了。
:::

### URL preview
- Scrapping script: https://github.com/cofacts/rumors-api/pull/104
- Scrapper: https://github.com/cofacts/url-resolver
    > 如果大家想架一個會自己做 text summarization 的爬蟲，可以直接載這個 cofacts url resolver 的 docker image 來玩玩看～

#### 問題：`urls` 大小太大！
- 預估會有 30000 URLs，總大小可能會到 2GB
- 最大的部分是我存了 raw html 來做頁庫存檔，純儲存不會 index。
- 會影響到 elasticsearch 備份作業

:::success
【結論】

把 backup script 改寫成：
1. 刪掉本機過去的備份
2. 把 tar 檔案丟到 google cloud storage 上去 [(coldline storage)](https://cloud.google.com/storage/docs/storage-classes?hl=zh-tw#coldline)
3. 用 cron 處理每日備份，用 [gsutil 上傳](https://cloud.google.com/storage/docs/gsutil/commands/cp)
4. 要抓檔案就去 google cloud storage 上來載

備案：unlimited space google drive (但 authorization 稍煩)
:::

### Tagging

> 大平台有闢謠組，在徵求謠言
> 覺得需要 classifier
> 


## 翻譯
https://drive.google.com/drive/folders/1BOLmshrx1gOWWJsU7m1Yi4NVnu96PN4b

## 送貼圖

- 換了頭圖
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5af93fa1e038bdd5a068987e2c10236f)

已經把貼圖送給了 4 人，並且寄信通知已經寄出的消息。

感謝文武花錢購買點數，請跟 @ggm 請款。

## g0v summit Rundown

### annotation 

### 連連看

## 對外

### 上完 9/18 有話好說之後

加好友人數：三天內增加 1000 人。但此漲幅並非前所未見。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ca1be66271fbf4ee3acea11026344ccf)


實際使用人數：似乎沒有太大差別

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ba83dd6c4105e1018a98094a3ea9bd5f)




### 沃草公民之夜
10/1 or 10/2
- Billion
- MrOrz

with Jason

### [IADA panel](http://iada-taiwan2018.pccu.edu.tw/files/90-1160-9.php?Lang=en)
- 9/27 10:45-12:00
- 地點：[中國文化大學 大夏館](http://future.sce.pccu.edu.tw/service/service01_01.asp) 大安森林公園東南方 / 建國南路和平東路口
- Panel 題目：Dialogues in Rogue Nation: What is the Answer to Social-Mediated Fake News and How Technology Can Redeem Itself to Foster Meaningful Public Dialogue?
- 主持人：台大新聞所 林麗雲老師
- 另外 2 位講者
    - 媒觀 福岳老師 講題：Media Literacy and Journalism Education
    - 蘋果日報 鄭副總編 講題：Fact-Checking and Reality Checking

投影片：http://bit.ly/cofacts-iada

### SEAPA panel
> Lucien

Need any help? (flyers? slides?)


# 正體中文語料收集計劃

目前 AI 訓練資料需要大量正體中文資源，但是因為缺少資料來源，目前有一個 [Common Crawl](https://commoncrawl.org/) 多年來持續利用爬蟲，每月持續釋出數百TB爬蟲收集的全球網路文字資料，其中包含一定比例的正體中文文字資料，因為資料量過大，只靠單一家用電腦可能需要花數個月才可以處理一個月的資料，只有大公司有資源可以加速處理。為了降低資料使用門檻，打算規劃一個群眾外包機制，讓大眾可以在電腦閒置時在背景協助下載檔案並且篩選出正體中文資料，讓正體中文 AI 研究者可以簡單的拿到純粹的中文文本資料。

## 相關連結
- [Common Crawl](https://commoncrawl.org/)
- [Common Crawl 資料抓取方式](https://commoncrawl.org/get-started#WARC-Format)

## 資料狀況
- 最新一筆資料是 September 2024，是 2024-09-07 - 2024-09-21 之間爬蟲收集的資料，解壓縮後約 410TB (壓縮後約 110TB)，內含 28 億的全球網頁內容。
    - 打包代號：CC-MAIN-2024-38
    - 資料層級
        - WARC: 包含原始資料，完整的 HTML
        - WAT: 只有 metadata
        - WET: 只保留純文字的部份
    - [WARC 列表路徑](https://data.commoncrawl.org/crawl-data/CC-MAIN-2024-38/warc.paths.gz)
        - WARC 一個 segment 約 1GB ，一包約有 90000 個 segment
        - WET 一個 segment 約 90MB，一包約有 90000 個 segment
        - 


## 資料處理流程
- 需要建置一台伺服器，裡面需要索引目前 Common Crawl 的打包索引，以及需要記錄哪些 segment 已經有人處理過了
- 沒人處理過的 segment ，可以在參與群包的人電腦進行下載整理並且上傳到伺服器
- 伺服器會再根據處理結果打包上傳至 huggingface

## 授權
- 待研究？
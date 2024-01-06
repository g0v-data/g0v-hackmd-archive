---
tags: 0archive, disinfo
---
# 0archive 營運管理 Operation Management

## 如何營運管理自己的 0archive？
> [name=chihao] 待整理

## 目標
- 更有效運用雲端空間
- 確實備份資料

## Action items
- [x] 刪除 40G middle2 dump 的檔案 [name=ronny]
    - 現有 79G 可用空間
- [x] ArticleSnapshot202002 -> jsonl -> bzip2 -> m2 disinfo db [name=pm5]
- [x] ArticleSnapshot202002 -> jsonl -> bzip2 -> objstorage  [name=pm5]
- [x] ArticleSnapshot202003 -> jsonl -> bzip2 -> objstorage  [name=pm5]
- [x] 每天把 snapshot 以外的 table sql dump -> bzip2 -> objstorage [name=pm5]
- [x] 每天把新的 snapshot -> jsonl -> bzip2 -> objstorage [name=pm5]
- [x] 開 linode objstorage 1TB [name=ronny]
- [x] 手動處理 Ptt 舊文章不再 snapshot [name=wenyi]
    - 按照「2 個月前的文章不再 update」的原則，2/2 以前的文章不再 update
    - 可以從 url 知道發佈時間 
- [x] 實作 - 增加 policy：first snapshot 在 2 個月以前的 Article 不再 update [name=wenyi]
- [x] 實作 - update freq - 第 1、2、3 天各一次，第 7 天第 4 次，1 Article = 4 ArticleSnapshot [name=wenyi]
- [ ] ~~實作 - 第一次之後的 snapshot 都存 diff~~
- [ ] ~~實作 - parser 要把 snapshot 拼起來~~
- [ ] ~~實作 - parser 要在 first snapshot 兩個月內 parse 完該 Article~~

## 備份
- 除了 snapshot 之外的 table
    - 每天 sql dump -> objstorage
- snapshot 呢？
    - 每天新的 ArticleSnapshot -> jsonl -> objstorage

## 實作
- 320G db
    - ArticleSnapshot202003: 129G
    - ArticleSnapshot202002: 42G
    - ArticleSnapshot: 16G
    - binlog: 49G (只保留三天，寫入記錄，應該是壓縮後)
    - taoyuan-chu: 16G
    - 還有些零零碎碎的
    - 2020/4/2 12:40 現況

| 檔案系統 | 容量 | 已用 | 可用 | 已用% | 掛載點 |
| --- | --- | --- |  --- |  --- |  --- | 
| /dev/sdc | 314G | 253G | 46G | 85% | /mnt/m2-disinfo-mysql-320g-1 |
> 容量 > 已用 + 可用？因為 df 指令會留 buffer 以防萬一
> 80% 就是需要因應處理了 [name=ronny]

- 160G 原生
    - 40G middle2 dump 的檔案 - 刪！
    - 70G 誤刪的檔案
- snapshot archive: snapshot table 超過 2 個月就 archive 到 offline storage
- take fewer snapshots?
    - 目前 - 7 - daily for a week
    - 改 - 3？ - once every 2 days
    - 改 - 前三天一天一次、第七天再一次，總共四次
    - 分 site 類型用不同的 snapshot freq?
        - 內容農場
        - 官媒
        - 新聞網站
        - Fb 專頁
        - Fb 公開社團
        - 討論區看板
        - YouTube 頻道
        - YouTube 帳號
- ~~沒有不一樣就不存 snapshot？~~
- 每次 snapshot 存 diff 就好
    - 比 readability 快
    - 但是 snapshot archive 可能會把第 1 篇刪掉
    - 是對第 1 篇 diff 還是前 1 篇？
        - 偷懶：都對第一篇 :p [name=chihao]
    - 方案一：我們 2 個月 archive 一次，只追蹤 update 1 個禮拜，所以在目前的 scheme 底下應該沒有問題
        - 增加 policy：first snapshot 在 2 個月以前的 Article 不再 update
    - 方案二：Snapshot 和 SnapshotDiff 分開存，Snapshot 只存第 1 個 snapshot

### Snapshot archive
- 儲存到哪裡？
    - Linode Object Storage
        - 1 TB = $20/mo
            - 1 TB Outbound Transfer
            - Up to 50 Million Objects per Cluster
            - $.02/GB Additional Storage
            - $.01/GB Additional Outbound Transferred
    - NAS
    - B2 Cloud Storage
    - AWS Glacier
    - AWS S3
    - GCP Storage
    - GCP Storage Nearline
- 用什麼格式儲存？
    - JSONLines
        - 缺點 - 要自己刻、多佔一些空間
        - 優點 - 使用上比較彈性
        - script 完成 [name=pm5]
        - encoding
            - unicode -> utf8
        - 寫好了

## 討論
> 比較治本應該是把 202002 搬出來，然後盡快實作內容沒變就不要 snapshot 和超過兩個月就 archive ，這樣子現在硬碟空間應該很夠
>
> - 把 202002 搬出來
> - 省空間機制
>    - 實作「內容不變就不要 snapshot」
>    - 超過兩個月的 snapshot 就 archive
>    
> [name=ronny]
> 之前是以 5 年用量來估計硬碟的？顯然十分不準 XD [name=pm5]
> 「內容不變就不要 snapshot」要用 raw HTML？用 parse 過的內文？Readability 跑起來也有點花時間所以這可能會讓 crawling 的速度變慢 [name=pm5]
> 而且 parser 更新也會影響「內容不變」的判斷 [name=chihao]
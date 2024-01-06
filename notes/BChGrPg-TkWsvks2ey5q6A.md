---
tags: disinfo, 0archive
---
# disinfoRG Meeting Notes (2019-2020/3/16)

## 2020/3/16 Mo [devs]

### 近況分享
### 進度報告
- wenyi
    - ZeroScraper的Airtable
        - sitesAirtable spider 的 airtable base id -> 環境變數
        - 增加 [AIRTABLE.md](https://github.com/disinfoRG/ZeroScraper/blob/master/AIRTABLE.md) for setting up airtable Sites
    - 用HPC跑PTT
    - [SiteStats table](https://github.com/disinfoRG/ZeroScraper/pull/89)
        - db schema
        - 什麼時候跑
- pm5
    - 更新[零時資訊傳播資料標準](/0Mt45bP_TQ2g0jRFP0tfTA)，調整欄位與增加 PTT 資料欄位
    - 更新 ArticleParser 配合新的資料標準 ([#17](https://github.com/disinfoRG/ArticleParser/pull/17))
- chihao
    - 大松提案、當坑主、成果報告
    - 開始了[簡單的資料統計](https://github.com/chihaoyo/disinfo-playground)
- bruce
    - 整理 helper 到 facebook [PR38](https://github.com/disinfoRG/FbScraper/pull/38)
    - 新增 fb-site 能 update 一個 site 所有的 article [PR35](https://github.com/disinfoRG/FbScraper/pull/35), [PR36](https://github.com/disinfoRG/FbScraper/pull/36)
    - 整合 click 以及處理 reference error [PR38](https://github.com/disinfoRG/FbScraper/pull/38)
    - 拿掉 max try times、 timeout 換成 limit sec [PR34](https://github.com/disinfoRG/FbScraper/pull/34)
    - Dockerfile for quick start [PR39](https://github.com/disinfoRG/FbScraper/pull/39)

### 討論
- SiteStats
    - [schema](https://github.com/disinfoRG/ZeroScraper/pull/89/commits/2db511b7ec1c024da29dee2765ca7e9658eee51e)
    - discover_count / update_count ?
    - use `new_article_count` / `updated_article_count` ?
    - date -> 維持字串
- SiteStats 什麼時候跑
    - 維持當天跑昨天的資料
- SiteStats: Site沒有update or discover count 要不要輸入
    - 不要
    - 用前端解決
- 有缺一些資料？
    - 大新聞網站好像有缺，例如武漢肺炎的相關報導
    - 如果tainan有但publications jsonl沒有，有可能是published_at 沒有被parse出來
- [0archive google drive](https://drive.google.com/drive/folders/18uDOhXBoxuiA0gyEy4U-i0ccpN-DN0bN)
- middle2
    - export file
    - cronjob log 無法及時
    - FbScraper 測試時遇到無法在本機重現 m2 狀況的問題
    - wenyi 那個「跑很久」的那個問題
- 租個 Linode？
    - remote write m2 db
    - 鎖 ip
- 成果發表？？？

### 本週工作
- chihao
    - 協助大家簽約
    - 建立好上手的資料分析 kit，為下次 community event 做準備
- wenyi
    - [ ] deploy Stats table
        - 做一些 monitor 圖
    - [ ] 研究新聞網站是否有少爬 & why
        - 列一個共筆追蹤文章是否有爬到、是否有被parsed
    - 雪花新聞
    - scrapy-splash
- pm5
    - [x] deploy new parser
    - [x] re-run PTT article parser
    - [x] publish new datasets
- bruce
    - [ ] test gcp write fb to m2 db

## 2020/3/14 Sa g0v-hackath38n 在家松

## 2020/3/9 Mo [devs]

### 近況分享
### 進度報告
- bruce
    - 整理 FbScraper 的程式碼
        - 取消 `facebook.Facebook` class ([this PR](https://github.com/disinfoRG/FbScraping/pull/26))，抽出 security check 的邏輯 ([this PR](https://github.com/disinfoRG/FbScraper/pull/31))
        - 有些 `try...except` 是重複的，應該移除到一些。 ([this PR](https://github.com/disinfoRG/FbScraping/pull/23))
        - 設定檔合成一個 `settings.py`。([this PR](https://github.com/disinfoRG/FbScraper/pull/30))
        - 單一使用的`fb-site.py` 與 `fb-post.py`([this PR](https://github.com/disinfoRG/FbScraper/pull/32))
- wenyi
    - 開源 FbScraper & ZeroScraper
    - 整合fb 原有的 Crawler, Pipeline, Parser and Spider 四支程式 -> fbscraper.actions.discover / fbscraper.actions.update
    - 修ZeroScraper update: dcard missing snapshots
    - PTT:
        - 發現scrapy的crawl邏輯
        - 把depth-first search (LIFO) 改成 breadth-first seearch (FIFO)
        - 要不要全部改？
- pm5
    - opened ArticleParser source
    - 改良 ArticleParser datetime & metadata parsing
    - 跟 bruce & wenyi 討論 fbscraper 調整，改了 logging
    - review some of the fbscraper codebase
- chihao
    - Masashi Nishihata, Citizen Lab
        - https://citizenlab.ca/2020/03/censored-contagion-how-information-on-the-coronavirus-is-managed-on-chinese-social-media/
    - TeamT5

### 討論
- FbScraper
    - `fbscraper.helper.*` 關於 facebook 的 function 可以搬進 `fbscraper.facebook` 了
    - `SITE_DEFAULT_TIMEOUT`、`POST_DEFAULT_TIMEOUT` 改個名字？加到 CLI arguments
        - timeout 通常表示失敗
        - discover - 最多可以跑多久 - `--limit-sec`
            - [name=bruce] ~1hr 可 discover 1000+ article
        - update - 最多可以跑多久 - `--limit-sec`
            - [name=bruce] 1000+ comment 展開 ~10min
    - `DEFAULT_MAX_TRY_TIMES`
        - discover
            - 改成 `DEFAULT_MAX_SCROLL_TIMES`
        - update
            - 載入更多留言 - 尋找「載入更多」dom element 的次數？
            - selenium 有「等某個 element 的功能」，所以不需要在另外設定變數。
                - timeout 之前看到，就會按下去
                - 否則就當作沒有了
    - 另外 - `def load_comment(self, depth, clicked_max_times=50):`
        - 拿掉 `clicked_max_times`
    - update 要不要抓所有留言？
        - 因為有 limit-sec，所以是「在時間限制內抓到最多留言」
    - 討論一下 `fbscraper.actions.update.UpdateCrawler.crawl_and_save` 的邏輯
        - [name=pm5] 了解！不過目前看起來有點難，可能可以改一下讓他更容易看懂一些
            - 但需要 test case
    - helper `click_without_move` / `click_with_move` / `click`
        - https://github.com/disinfoRG/FbScraper/blob/master/fbscraper/helper.py#L164
        - difference?
        - 是不是要移到 `facebook.py`
        - actions: 
            - 要合成一個
            - https://github.com/disinfoRG/FbScraper/issues/29
            - 移到 facebook.py
    - fb-site update?
        - 加！
        - for loop
- ZeroScraper Airtable
    - Add instructions for Airtable in ZeroScraper/README
    - Move Airtable link to env
- depth-first / breadth-first search?
    - 跟網站結構有關的話之後可能要改成 site 的 config
    - https://doc.scrapy.org/en/latest/faq.html#does-scrapy-crawl-in-breadth-first-or-depth-first-order
        - `DEPTH_PRIORITY = 1`
        - `SCHEDULER_DISK_QUEUE = 'scrapy.squeues.PickleFifoDiskQueue'`
        - `SCHEDULER_MEMORY_QUEUE = 'scrapy.squeues.FifoMemoryQueue'`
- PTT
    - 試試看 `nohup`
    - cronjob 開完後立刻關掉
    - 短期內大概只有以上這些方法
    - 去 #middle2 問 ronny 好了
- Nick
    - https://docs.google.com/document/d/1WDhuFWwUFrO3Drx5DqXyLdhvXy_UgBuJtvMma_qmqpM/edit
    - IP 
    - Completeness
    - snapshot 消失的要不要直接從 publication text parse?
        - 舊的 parser 不會 parse 純 publication text 與 comments 所以那些 text field 都有完整的 post html，可以 parse 出 published_at 與 comments
        - 這樣就不用重抓一次，而且有些 post 已經 404 了
    - how to reply nick?
- 和 Nick 提議合作？
    - PTT
    - 之後？
- [大松提案](https://docs.google.com/spreadsheets/d/1RsUGPSchbHWuosKsyH0wELCepNRTkEWAHI_OI6R5d4g/edit#gid=1)嗎？
    - COVID-19 相關資料分析？

### 本週工作
- [x] [name=pm5] reply to nick
- [x] [name=pm5] release 2nd version of data standard
    - include article author field
    - include fields for GA and other tracking code identifiers
    - include author IP address fields
- [ ] [name=pm5] re-run parser on PTT articles and release datasets.
    - parse data from >= 2 upstreams including backup tables
    - fix article urls extract code
    - monitor CPU usage during parsing
    - 特別處理舊 parser 所留下的 publication text ^^^^
- [ ] [name=chihao] 準備大松提案
- [name=wenyi] 
    - [x] ZeroScraper Airtable
    - [x] 在#middle2 問 ronny 可不可以不用一直ssh讓middle2跑程式
    - [x] 報名 hackath38n
    - [ ] 想一下大松的時候可以做什麼
    - [ ] scrapy splash
        - https://splash.readthedocs.io/en/stable/
        - maybe 合用：不需要操作 UI、不需要登入
        - 詳細測試
    - [name=chihao] 不知道做什麼了嗎？
        - https://g0v.hackmd.io/L1l9m6joRhCWhmGFZYAO5A
    - [ ] 每天晚上跑一個統計的 .py，存進 db
        - 開 db schema
        - 實作 .py
    - [x] 把台南db中Fb相關table拿掉
- [x] [name=bruce]
    - 整理 helper 到 facebook
    - 新增 fb-site 能 update 一個 site 所有的 article
    - 整合 click 以及處理 reference error
    - 拿掉 max try times、 timeout 換成 limit sec 

### 下次會議
3/14 大松 http://bit.ly/hackath38nrigester
3/16

## 2020/3/6 Fr [devs]

## 2020/3/2 Mo [devs]

### 近況分享
- chihao
    - 韓式炸雞

### 進度報告
- chihao
    - ...
- wenyi
    - ptt: Gossiping (153338/779K), HatePolitics (84258/80k)
        - 大概抓了 4 天
        - 總數比較少因為 ptt 前幾天有刪減頁面（頁面總數變少）
    - changhua Article.created_at
    - FbScraping PR [#20](https://github.com/disinfoRG/FbScraping/pull/20)
- pm5
    - fixed mysql unicode collation (haven't check is the problem is resolved yet)
    - dumped current datasets with partial text
    - fixed a db performance issue reported by ronny
    - made a minial example to reproduce chrome zombie process problem on middle2
        - 不確定是 chrome driver linux 版的問題還是 m2 的問題
        - 要再繼續查下去
    - fixed a "too many aborted connections" problem
- bruce
    - [整理程式碼和說明文件](https://g0v.hackmd.io/0MGGecVSSkunT5DWAHFC9Q?view#%E7%A8%8B%E5%BC%8F%E7%A2%BC%E6%9E%B6%E6%A7%8B)
    - 將 timeout 的規則，從 multiprocessing 移到 child process 的 discover 和 update 裡面
    - 還在解決 zombie 的狀況

### 討論
- tainan ArticleSnapshots 消失
    - now: 264543
- tainan ArticleSnapshot (update) 最後是 2/28 13:51 
    - dcard 的問題
    - 可以有個推論，就是資料是 2/28 左右才消失的？有點奇妙
- [NewsScraping](https://github.com/disinfoRG/NewsScraping) 開源
    - ZeroScraper
- [datasets](https://github.com/disinfoRG/datasets) 開源
    - + LICENSE
- zombie
    - 用了 docker file from ronny + scripts from pm5 但錯誤難重現
- wenyi PR
- ptt
    - 3/2 12:20 UTC
    - 2/28 1:00 UTC

### 本週工作
- ArticleSnapshot 的問題 + 有沒有備份
    - 磁碟用量和 phpMyAdmin 顯示 264k (4.xGB) 不符？
- wenyi
    - [x] NewsScraping -> ZeroScraper [by 3/2] 
    - [x] private -> public
    - [x] ping @chihao at #disinfo
    - [x] update `runner/update.py` to accommodate missing dcard snapshots.
- pm5
    - [x] dump new datasets with ptt articles crawled last week
    - ~~[ ] fix parser and check progress~~
    - ~~[ ] work /w ronny on db recovery (might also need to implement [snapshot table rotation](https://github.com/disinfoRG/NewsScraping/issues/81))~~
    - [x] help fix fbscraping
- bruce
    - [x] 3/3 前 merge PR #20

## 2020/2/24 Mo [devs]
### 近況分享
- chihao
    - 自主健康管理解除
- pm5
    - Pixel 3a
- wenyi
    - Melancholia

### 進度報告
- wenyi
    - data migration
        - airtable site update
    - monitor api
        - publication
            - 跟pm5討論後目前保留使用LIKE syntax
            - 然後把所有publication store in memory
            - 一個小時更新
        - 加了一個 `GET /sites/[site_id]/article_count?discoverFrom=[unix_time]&discoverUntil=[unix_time]`
    - cli 
        - update: middle2 `sh: 1: python3: not found`
        - discover: `sqlalchemy.exc.InternalError: (pymysql.err.InternalError) (1366, "Incorrect string value: '\\xF0\\x9F\\x8E\\xB6\\xE5\\xAE...' for column `user_tainan-sun-500796`.`ArticleSnapshot`.`raw_data` at row 1")`
    - 抓 ptt
        - disabled for 1 day
        - 會亂跳
- chihao
    - 報告交出去了覺得開心
    - 小松有點⋯
        - 我忘記事先貼文了⋯
        - ...
- bruce 
    - Add sql overview discover and update progress
        - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_76927ddef8a32aa0602225be78cd2c95)
        > 這個 sql 在哪？ [name=chihao]
        ```sql
        select
            Integrated_Site_1.*,
            (select count(ArticleSnapshot.article_id) from ArticleSnapshot, Article, Site where ArticleSnapshot.raw_data<>'' and ArticleSnapshot.article_id=Article.article_id and Article.site_id=Site.site_id and Site.type='fb_page') / (select count(Article.article_id) from Article, Site where  Article.site_id=Site.site_id and Site.type='fb_page') as total_updated_ratio,
            Integrated_Site_1.discovered_count / (select count(Article.article_id) from Article, Site where  Article.site_id=Site.site_id and Site.type='fb_page') as discovered_ratio,
            Integrated_Site_1.updated_count / (select count(ArticleSnapshot.article_id) from ArticleSnapshot, Article, Site where ArticleSnapshot.raw_data<>'' and ArticleSnapshot.article_id=Article.article_id and Article.site_id=Site.site_id and Site.type='fb_page') as updated_ratio,
            sum(Integrated_Site_2.discovered_count) as discovered_cumulated,
            sum(Integrated_Site_2.discovered_count) / (select count(Article.article_id) from Article, Site where  Article.site_id=Site.site_id and Site.type='fb_page') as discovered_cumulated_ratio,
            sum(Integrated_Site_2.updated_count) as updated_cumulated,
            sum(Integrated_Site_2.updated_count) / (select count(ArticleSnapshot.article_id) from ArticleSnapshot, Article, Site where ArticleSnapshot.raw_data<>'' and ArticleSnapshot.article_id=Article.article_id and Article.site_id=Site.site_id and Site.type='fb_page') as updated_cumulated_ratio
        from
            (
                select
                    Discovered_Site.site_id, 
                    Discovered_Site.name,
                    Discovered_Site.url,
                    Discovered_Site.last_crawl_at,            
                    Discovered_Site.discovered_count,
                    count(ArticleSnapshot.article_id) as updated_count, 
                    (count(ArticleSnapshot.article_id)/Discovered_Site.discovered_count) as self_updated_ratio
                from 
                    ArticleSnapshot, 
                    Article, 
                    (
                        select 
                            Site.site_id,
                            Site.name,
                            Site.url,
                            Site.last_crawl_at,
                            count(Article.article_id) as discovered_count 
                        from 
                            Article, 
                            Site 
                        where 
                            Article.site_id=Site.site_id and 
                            Site.type='fb_page' 
                        group by 
                            Site.site_id
                    ) as Discovered_Site 
                where 
                    ArticleSnapshot.raw_data<>'' and 
                    ArticleSnapshot.article_id=Article.article_id and 
                    Article.site_id=Discovered_Site.site_id 
                group by
                    Discovered_Site.site_id
            ) as Integrated_Site_1,
            (
                select
                    Discovered_Site.site_id, 
                    Discovered_Site.name,
                    Discovered_Site.url,
                    Discovered_Site.last_crawl_at,            
                    Discovered_Site.discovered_count,
                    count(ArticleSnapshot.article_id) as updated_count, 
                    (count(ArticleSnapshot.article_id)/Discovered_Site.discovered_count) as self_updated_ratio
                from 
                    ArticleSnapshot, 
                    Article, 
                    (
                        select 
                            Site.site_id,
                            Site.name,
                            Site.url,
                            Site.last_crawl_at,
                            count(Article.article_id) as discovered_count 
                        from 
                            Article, 
                            Site 
                        where 
                            Article.site_id=Site.site_id and 
                            Site.type='fb_page' 
                        group by 
                            Site.site_id
                    ) as Discovered_Site 
                where 
                    ArticleSnapshot.raw_data<>'' and 
                    ArticleSnapshot.article_id=Article.article_id and 
                    Article.site_id=Discovered_Site.site_id and 
                group by
                    Discovered_Site.site_id
            ) as Integrated_Site_2
        where
            Integrated_Site_1.discovered_count<=Integrated_Site_2.discovered_count or 
            (
                Integrated_Site_1.discovered_count=Integrated_Site_2.discovered_count and 
                Integrated_Site_1.site_id=Integrated_Site_2.site_id
            )
        group by
            Integrated_Site_1.site_id,
            Integrated_Site_1.discovered_count
        order by
            Integrated_Site_1.discovered_count desc,
            Integrated_Site_1.site_id desc;
        ```
    - Found insertion error of utf8(mb4)
    - cli add supports
        - 指定site
        - 間隔時間 0-120s random
        - 自動切換登入或不登入
    - [ ] 統計 fbscraping discover / update 一天可以跑多少
        - discover: 130/day
        - update: 18/day
        > 這個統計區間是？如果是從剛開始到現在，這個統計是無效的，應該要每天 count，看趨勢。 [name=chihao]
        > 
    - [x] 小松提案
    - [x] Parallel discover page and update group
    - [ ] Automatically switch accounts for login mode for discover and update
    - [x] Figure out more about security check
        - different break time between process can avoid
        > 關於 security check 可以有一份內部文件嗎？[name=chihao]
    - [ ] README for open source
- pm5
    - 處理 db & server 的事情
    - 修了 [#69](https://github.com/disinfoRG/NewsScraping/issues/69) 404 handling
    - 修了 [#41](https://github.com/disinfoRG/NewsScraping/issues/41) 減少 dedup 的 db queries
    - 修了 [#26](https://github.com/disinfoRG/NewsScraping/issues/26) site_id 用太快的問題

### 討論
- cli error
    - column collation
    - python3 not found
- ptt crawling 會亂跳⋯解法
    - 至少有兩個數字
    - 拒絕 index1.html `index([2-9]|(\d\d+))`
    - https://regexr.com/
    - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d21172a3ec0b0e29700bf9c6d0a7d92c =50%x)
- dataset release
    - ptt 優先？
    - 這週釋出部份內文資料？
    - 3/5 大松
- ocf 簽約
    - remote
- ArticleSnapshot 分 table？
    - 可能的作法：先把一年份的 table 都開好，用 article ID 切換 table
    - dump 的規則？
    - `SELECT MIN(article_id) FROM Article WHERE snapshot_count < 7`
- 討論一下 fb crawler 的用量
    - 最近有幾次 cpu 用量蠻高的
    - defunct: 應該是 cronjob 結束 container 被砍掉，所以 defunct 的都砍掉了
    - bruce：目前會開 4 個
    - 這禮拜來測試
- 想加 Article 的 discovered_at
    - 叫 created_at

### 資源協調
- Linode 6 core 24G

### 工作項目
- [x] pm5: collation -> table: utf8mb4, column: utf8mb4_unicode_ci
    - taoyuan publication, producer
    - tainan ArticleSnapshot 
- wenyi: 
    - [x] fix ptt crawling
    - [x] 開一個 Article.created_at 的 column
        - type INT
            - (value provided by FbScraping)
        - 研究一下 Timestamp -> Int
- [x] pm5: 這週內釋出目前所有 publication (~890k) 「部份內文」publication_text 前 280 char 資料集，repo datasets 開源
    - 用之前寫好的工具釋出了「有 parse 出 published_at」的 ~550k 筆資料
    - ptt 的有 ~27k 筆，集中在 2020/1~2。更早以前的資料要再查查是沒抓到還是沒 parse 到。
- [x] pm5 /w help from everyone: ArticleSnapshot 分 table 這件事開 issue: [#81](https://github.com/disinfoRG/NewsScraping/issues/81)
- [ ] bruce: FbScraping 測試
    - 目標：讓 fb handler 自動跑，可以穩穩地一直跑下去
    - bruce 開少一點 cpu
    - 跟 pm5 / ronny 協調
    - [關於 FbScraping 的 cpu 測試](https://g0v.hackmd.io/J_9XAF9MTu6qAeyolsomUQ)
        - [目前結果](https://docs.google.com/spreadsheets/d/1SvZ3xRfU-RA5S6fi_hblScW-YqcGT1sGzzeQAdKb96I/edit#gid=1417334576)
- chihao
    - [ ] 協助大家簽約
    - [ ] 開 NewsScraping / FbScraping 比較技術分析共筆

## 2020/2/23 Su 2-6pm disinf1thon

## 2020/2/17 Mo [devs]
### 近況分享
- chihao
    - 從日本回來，自主健康管理中
- pm5
    - 覺得疫情有點緊張
    - 最近開始追 The X-Files（完成小時候的願望？）
    - Ted Chiang 的短篇集 Exhalation 出[中譯本](https://www.books.com.tw/products/0010847496?loc=P_0002_050)，推推
        - 軟體物件生命週期 The Lifecycle of Software Object
        - 呼吸 Exhalation
- wenyi
    - \jojo rabbit/
- bruce
    - 小樹屋月租方案

### 進度報告
- wenyi
    - db api: publication
        - 目前用Like，和pm5討論測試full-text search中
            - [#65](https://github.com/disinfoRG/NewsScraping/pull/65) query「台灣」2min
    - NewsScraping CLI
        - article
            - discover, update by article 用request, selenium
            - discover \<url\>
        - site
            - discover
            - update
        - ns
            - discover -- 原本的 batch_discover
            - update -- 有問題 [#70](https://github.com/disinfoRG/NewsScraping/issues/70)
- pm5
    - 跟 bruce 討論了 FbScraping
    - 改了 NewsScraping update 的平行處理，今天開始跑，正在跑
        - per-site
    - 測試了 parser db MySQL full-text indexing，要再想個辦法 migrate production db
- bruce
    - parallelly update fb_page article and discover fb_public_group without login from same file ([code](https://github.com/disinfoRG/FbScraping/tree/update_without_login))
    - discuss FbScraping with pm5
    - 不登入也可以抓
    - 但大概 90 分鐘就會遇到安全驗證
        - 遇到安全驗證，目前的處理方法
            - css selector 偵測遇到安全驗證，就自己 quit
            - quit 之後，
        - 安全驗證是不是 fb 在電腦端存了什麼
            - 如果是，那是什麼？
        - 4 個 chrome 是否 share 這些東西
            - 如果是，那是不是清理一次就可以避免安全驗證？
            - 如果不是，那？
    - dom
        - parsing 需要先判斷這個是登入狀況下抓到的 or 不登入狀況下抓到的
    - 要避免不同地方抓同一個 url
    - 登入 / 不登入；discover / update；page / group
    - 釐清一下
        - NewsScraping
            - prod server: tainan
            - prod db: tainan
        - FbScraping
            - prod server: changhua
            - prod db: 目前是 tainan，但希望 changhua
        - FbScraping 測試
            - server: local
            - db: local! 不能寫 chuanghua
    - action plan
        - 更改 parser db schema
            - 可以 map 到兩個以上不同的 scraping db 來源；producer 跟 publication 都要處理
            - +column
                - producer_mapping.scraper_db
                - publication_mapping.scraper_db
        - changhua db 清空
        - migrate fb 相關的資料 tainan db -> changhua
- chihao
    - first payment from both funder have arrived (fucking finally)
    - report (1) draft done \o/

### 討論
- [System report (1)](https://docs.google.com/document/d/1sdzbmMn6ztbjJWodIkGtx7A_sMeIqw8DhtBjja9Vtis/edit#)
    - [stats](https://docs.google.com/spreadsheets/d/1zYaN4-pSu-sja81XcK5ecPQaFDn8JU-Ti9iffiYH20U/edit#gid=1365137482)
    - scraper frequency
        - NewsScraping
            - discover 1h
                - 平行跑所有 site
                    - TODO：偵測哪些 site 一小時內跑不完 discover
                        - 自然死亡就是跑完惹
            - update 24h
                - 平行跑所有 site 之下所有需要 update 的 article
                    - 用 last_snapshot_at ASC
                    - 已有紀錄：哪些 article 兩次 update > 24h
                    - 現在的問題：之前一段時間 update 跑得很慢
                        - 因為 pm5 把平行處理寫完了，正在跑
                        - 要先抓個 2 weeks，然後用數據來調整系統
                        - 目前的 update 速度約 2500 snapshots/hour
                - stats:
                    - 1m articles
                    - ~800k 1 snapshot
                        ```
                        COUNT(*) 	snapshot_count 	
                        52419 	0
                        825410 	1
                        60173 	2
                        7749 	3
                        8801 	4
                        14358 	5
                        6674 	6
                        69705 	7
                        ```
        - FbScraping
            - https://g0v.hackmd.io/BChGrPg-TkWsvks2ey5q6A?both#2020130-Th
            - discover
                - 24h
                    - 已知：跑不完
                - 測試 discover: 4.23 article/min (607/143.58)
            - update
                - 24h
                    - 已知：跑不完
                - 測試 update: 2.39 article_snapshot/min (327/136.18)
    - parser freq
        - producer
            - 1h
        - publication
            - 1h
            - 10000 max
    - Ptt scraping before 2020/1/13 (16)
    - db snapshot (public data set)
        - 目前 https://github.com/disinfoRG/datasets
    - data scehma
        - public dataset 就會按照這個格式
        - https://g0v.hackmd.io/@chihao/0archive/%2F0Mt45bP_TQ2g0jRFP0tfTA
- [Nick](https://docs.google.com/document/d/1WDhuFWwUFrO3Drx5DqXyLdhvXy_UgBuJtvMma_qmqpM/edit)
- [小松](https://g0v.hackmd.io/@chihao/0archive/%2FDvoeZunbSqK4UBq8AUg4VA)
- [ns\.py](https://github.com/disinfoRG/NewsScraping/blob/master/ns.py) twisted connection error [#70](https://github.com/disinfoRG/NewsScraping/issues/70)
    - pm5: 好我會看一下

### 一些工作項目
- migration
    - [x] (1) changhua stop cron; stop local jobs until migration done (bruce)
    - [ ] (2) parser schema (pm5)
    - [x] (3) changhua clear (wenyi)
        - site 清空
        - article 清空
        - article snapshot 清空
    - [x] (4) data migration – .py 讀 tainan 寫 changhua (wenyi)
        - site:fb的部分從台南移除，放入彰化，保留site_id
        - article: fb的從台南移除，放入彰化，未保留site_id
        - article snapshot: fb的從台南移除，放入彰化
    - [x] (5) 更改 airtable update 至 site table 的邏輯 
- NewsScraping 偵測一篇文章 update 區間
- 大家：小松先提案

### 本週工作規劃
- pm5
    - [ ] 開新 dataset repo 放部分內文資料集
    - [ ] 小松提案
- bruce
    - [ ] 統計 fbscraping discover / update 一天可以跑多少
    - [ ] 小松提案
    - [x] Parallel discover page and update group
    - [ ] Automatically switch accounts for login mode for discover and update
    - [x] Automatically switch to without-login mode for discover and update
    - [ ] Figure out more about security check
    - [ ] README for open source
- chihao
    - [x] Set up meeting with Nick (Thur ET / Fri TW)
    - [x] Report by Thursday
    - [ ] 小松提案
- wenyi 
    - db migration
        - [x] 台南 -> 彰化
        - [x] airtable update
        - [x] 清掉在台南的空的update & 調整article中的snapshot_count, snapshot_time （等ronny）
    - [x] 小松提案
    - [ ] ns.py update 
    - [ ] 測試full-text search
    - [ ] ptt 跑一個完整的 (--depth 0)
        - chihao 建議：如果無法一次跑完，建議分階段
            - 先備份選前三個月 2019/11-2020/1
            - 再備份更之前

### 下次會議
- 2/21 8:30am +Nick
- 2/23 小松
- 2/24 dev meeting pending

## 2020/2/13 Th [pm5 bruce sync]
* 一些討論
    * 為什麼需要用 RemoteWebDriver？
    * 管理 process 的方法
    * 需要儲存全部的 crawler log 嗎？
    * 解釋一下 fb_controller.FbController.control 的邏輯
    * discover 與 update 的優先度與佔比
    * 目前的 fb_controller 會只有一部份的 site 有跑到 discover
    * 用 threading 還是 multiprocessing
    * release hanging browser 的作法
    * 需要存 login cookies
    * group 應該不要 copy 整套 page 的程式來改，會比較好
    * 需要開更多 fb 帳號的話要說

## 2020/2/10 Mo [devs]
### 近況分享
- chihao
    - JAL 的機上餐是薑燒豬肉好香但不能吃
    - 東京好冷
- wenyi
    - [factfulness](https://www.amazon.com/Factfulness-Reasons-World-Things-Better/dp/1250107814)
        - https://www.youtube.com/watch?v=hVimVzgtD6w
- pm5
    - 把 MacBook 和 iPhone 改成法語語系
- bruce
    - 靈魂不歸法律管
    - 春山出版
### 進度報告
- wenyi
    - db api
        - GET /articles/[id]
        - GET /articles?url=[url]
        - GET /sites/[site_id]/article_count
        - GET /sites/[site_id]/latest_article
    - dcard 404
        - 終止next snapshot at
        - 送一篇 snapshot 進 db
        ```json
        {'post': {'error': 1202, 'message': 'Post not found', 'reason': 'wash', 'reasonText': '惡意洗板、重複張貼'}, 'comments': {'error': 1202, 'message': 'Post not found', 'reason': 'wash', 'reasonText': '惡意洗板、重複張貼'}}
        ```
    - 完成 update site-wise 
        - update README
        - `python3 execute_spider.py -u --site_id xxx`
        - 若不指定site_id則為update all
        - update all的時候dcard會出現403的文章，但若指定dcard site則不會
        - 需要時才會開selenium
    - closed [issue #58](https://github.com/disinfoRG/NewsScraping/issues/58): add site_id to crawler stats
- pm5
    - 跟 wenyi 討論 CLI 改進
    - 改進 parser CLI 工具 [#10](https://github.com/disinfoRG/ArticleParser/issues/10)
    - Closed parser issues [#2](https://github.com/disinfoRG/ArticleParser/issues/2) (GA ID), [#8](https://github.com/disinfoRG/ArticleParser/issues/8) (PTT parser)
- bruce
    - fb_page 跑完 update 一次
        - 963727 https://www.facebook.com/1006889099430655/posts/2725157240937157
        - update 10675 篇 ArticleSnapshot，涵蓋 18 個 site
        ```sql
        select count(Article.article_id) from Article, ArticleSnapshot where Article.article_id=ArticleSnapshot.article_id and Article.article_type='FBPost';
        select distinct Article.site_id from Article, ArticleSnapshot where Article.article_id=ArticleSnapshot.article_id and Article.article_type='FBPost';
        ```
        - [x] [遇到安全驗證會抓不到文章就跳出](https://github.com/disinfoRG/FbScraping/commit/848a0276eeef39097efc1609895e8fbd7d49e50c)
        - [ ] 換不同帳密繼續抓
    - 可以用 fb_controller 跑 discover 和 update
        - [x] [discover](https://github.com/disinfoRG/FbScraping/commit/17881cc35871c31fbd323a1a7580d507eb6ddb87)
        - [ ] update
    - [x] 可以跑 fb_group 的 discover 和 update 的[程式](https://github.com/disinfoRG/FbScraping/commit/134a6e6605165f96b46f63abac92af88cd7f4c57)
    - crawl (discover & update) single url
        - [x] [single site id](https://github.com/disinfoRG/FbScraping/commit/e76c61a17165d2a3f3631adfe3a637b4683f9bf3)
        - [x] [single article id](https://github.com/disinfoRG/FbScraping/commit/2075b319cb3da591b2ad27ede977bd2f3eb0c298)

### 系統現況
- [tainan] Article
    - Article 866037
    - FBPost 65917
    - PTT 46090
    - Dcard 2456
- update 跑的比 discover 慢
    - Article
        - 多工比較慢
        - 這週要改進
    - FBPost
        - 留言很多，要展開
### 討論
- $$$
    - 收到！
- 小松是不是要改成線上呢？
    - 改！
    - 作法
        - Slack channel #disinfo 討論
        - 線上 code review
- db api: publication
    - GET /publications?q=[string]
        - MySQL match 標題、內文
            - LIKE '%something%'
            - [match 標題 OR 內文](https://dev.mysql.com/doc/refman/5.7/en/fulltext-search.html)
        - 要分頁
            - "paging": page=1, page=2...要處理排序
- api deploy
    - code 目前在這
        - https://github.com/disinfoRG/NewsScraping/tree/master/newsSpiders/webapi
        - https://github.com/disinfoRG/NewsScraping/blob/master/application.py
    - gunicorn + WSGI + application.py on middle2
    - custom domain
    - https://api.0archive.tw/v0/... ?
- 其他種類 article 404 的處理方法
- 關於 fb
    - 目前都在本機上跑，直接寫 tainan
        - bruce: middle2 上看不到 log
        - cron job 跑完都看不到 log
    - raw html 需要什麼樣的 parsing
    - udpate 怎麼加快

### 下次進度確認
- pm5
    - [x] 解決 NewsScraping update 多工不良時間過長的問題
    - [ ] review and fix data exchange standard to add publication comments and other missing things
    - [x] sync FBScraping /w bruce
- bruce
    - fb_page 跑完 update
    - update 自動換不同帳密繼續抓
    - fb_group 跑完 discover 和 update 一次
    - 對 fb_page 跑完 update 得到的 ArticleSnapshot 去 pares 出 comment 寫入到 db
    - 對 fb_page 和 fb_group 會任何情形（例如：有些文章會跳出影片自動播放的畫面）而導致原本 update 方法抓不到文章的情形做處理
    - 跟 pm5 討論 fb_controller
- wenyi
    - [ ] db api: publication
    - [ ] NewsScraping CLI
    - [ ] dashboard for monitoring daily process (本機)
- chihao
    - OCF $$$ tracking
    - reporting

## 2020/2/7 Fr
4pm
bruce, chihao
### 完成事項
- upate 了 6687 篇 ArticleSnapshot 涵蓋 7 個粉絲頁
- discover 了 2089 篇 Article 涵蓋之前失敗的 4 個粉絲頁
### 進行中
- discover fb_group
- 執行 fb_controller 時，應該再呼叫 discover 或 update 去執行後，就可以結束 fb_controller 的主程式
- 將 fb_controller 判斷 hangout 的方式，從本機端的 log 轉移到雲端或db

## 2020/2/5 We
4pm
bruce, chihao
### 完成事項
- update 跑 site_id=69 寫入台南 ArticleSnapshot 1094 篇
- 增加 update 的 next_snapshot_at 的 interval https://github.com/disinfoRG/FbScraping/issues
- 更新本月工作計畫
- fb_controller 可以同時用不同的 fb 帳號跑 2+ 個 site 的 disocver （1 個 site 用 1 個 fb 帳號）https://github.com/disinfoRG/FbScraping/blob/fb_controller/fb_controller.py

## 2020/2/3 Mo [devs]
### 近況分享
- chihao
    - 今天一天很紮實地做了很多事感覺很棒
    - 週末去了九份
    - 日本
- pm5
    - 很宅
- wenyi
    - 想分享坐飛機時95%都有戴口罩 ++
    - 過年去太平山做嘣嘣車 & 鳩之澤溫泉超棒 \++/
- bruce
    - 過年回台南
    - 漫畫
    - 撲克牌

### 進度報告
- chihao
    - $
- wenyi 
    - 人工跑fb sites \++/
    - FBScraping discover 有加了argument for max_try_times = 1000
    - NewsScraping 的 update 可以指定 site
    - 修 dcard 的 bug
        - 只有excerpt --> 抓到content
        - 每一個snapshot都至少會有一則留言（上一個snapshot的最後一則留言）
        - [尚未解決] dcard 的文章許多都被移除了，需要對這些被移除的文章做處理。
- bruce
    - 在彰化跑 discover, update，資料寫到台南
    - 加 log 到 discover 和 update
    - 加入關閉然後重啟 browser 的機制來面對 page crashed
    - 本機跑 fb_controller 原型執行 discover
- pm5
    - 整理需求
        - 希望四月之後，程式可以放著自己跑，不要花太多力氣，可以自己運作
        - 爬蟲時不時一定會有問題，所以如果要減少維護
            - 要能很快看到有問題
            - 能很快修改、測試爬蟲
        - 列在 Roadmap 裡了
    - 改架構
    - 推了資料集到 GitHub
        - 每天 50-80MB；github 每個檔案限制 <100MB
    - 看程式跑的狀況

### 討論
- [Roadmap & Task Tracker](https://g0v.hackmd.io/@chihao/0archive/%2FL1l9m6joRhCWhmGFZYAO5A)
    - Fb、Ptt、Dcard 第一次跑 discover 可能可以在開發者的電腦自己跑，比較有彈性
- Memory problems on middle2
    - 無法同時跑太多 selenium
- disinf1thon 2/23 (Sunday) ok?
    - 2/15...
    - 2/22 是 sch001 開學日
- Site 註記上次 discover 的結果？
    - 加在 site_info
    - FbScraping crashing... why?
        - more than 1000 posts 就很有可能 crash
        - +RAM
- logging
    - 進 db？
        - 會很快爆炸
    - 能即時看到 log
        - 應該在 dev 解決
    - 能夠回去查以前的 log
        - 在 production 需要
        - 提出需求看 ronny 怎麼回應

### 本月工作計畫
這個月的分工與目標
- chihao
    - week 1 (2/3)
        - [x] 合約
        - [x] 跟 ronny 討論加記憶體 XD
        - [x] 付 ronny 錢
        - [x] jothon disinf1thon
        - [x] 小松場地
        - [ ] ~~小松報名~~
        - [x] 小松共筆
        - [x] 2/5 週三 check monthly plan
    - week 2 (2/10)
        - [ ] 報告
        - [ ] 查以前的 log：提出需求看 ronny 怎麼回應
    - week 3 (2/17)
    - week 4 (2/24)
- bruce
    - week 1 (2/3)
        - fb_page 跑完 update 一次
            - [x] [遇到安全驗證會抓不到文章就跳出](https://github.com/disinfoRG/FbScraping/commit/848a0276eeef39097efc1609895e8fbd7d49e50c)
            - [ ] 換不同帳密繼續抓
        - 可以用 fb_controller 跑 discover 和 update
            - [x] [disocover](https://github.com/disinfoRG/FbScraping/commit/17881cc35871c31fbd323a1a7580d507eb6ddb87)
            - [ ] update
        - [x] 可以跑 fb_group 的 discover 和 update 的[程式](https://github.com/disinfoRG/FbScraping/commit/134a6e6605165f96b46f63abac92af88cd7f4c57)
        - crawl (discover & update) single url
            - [x] [single site id](https://github.com/disinfoRG/FbScraping/commit/e76c61a17165d2a3f3631adfe3a637b4683f9bf3)
            - [x] [single article id](https://github.com/disinfoRG/FbScraping/commit/2075b319cb3da591b2ad27ede977bd2f3eb0c298)
    - week 2 (2/10)
        - fb_group 跑完 discover 和 update 一次
        - parse single article
        - 對 fb_page 跑完 update 得到的 ArticleSnapshot 去 pares 出 comment 寫入到 db
        - 對 fb_page 和 fb_group 會任何情形（例如：有些文章會跳出影片自動播放的畫面）而導致原本 update 方法抓不到文章的情形做處理
    - week 3 (2/17)
        - 對 fb_page 和 fb_group 得到的 ArticleSnapshot 去 parse 出 po 文者和留言者的 id 和照片寫入到 db
        - 對 fb_page 和 fb_group 去 crawl 基本資訊（管理員、粉絲、關於我們等）寫入到 db
    - week 4 (2/24)
        - fb_page 和 fb_group 簡易版的進度監控儀表板（ex. 串流 middle2 上 cron 執行 fb_page 和 fb_group 的 stdout 和 stderr 到其他雲服務來做作為監控的資料來源）
- wenyi
    - week 1 (2/3)
        - NS: Monitoring API [issues #59](https://github.com/disinfoRG/NewsScraping/issues/59)
            - [x] GET /articles/[id]
            - [x] GET /articles?url=[url]
            - [x] GET /sites/[site_id]/article_count
            - [x] GET /sites/[site_id]/latest_article
            - [ ] GET /publications?q=[string]
        - NS: update site-wise [issues #49](https://github.com/disinfoRG/NewsScraping/issues/49)
            - [x] `python3 execusite_spiders.py -u --site_id xxx`
            - [x] 需要時才會開selenium
            - [x] update README
            - [ ] parallel 執行檔 --> (做CLI時一起寫)
        - dcard 已移除處理 [issues #55](https://github.com/disinfoRG/NewsScraping/issues/55)
            - [x] next_snapshot_at = 0 
            - [x] 送一個最後的snapshot w/ error message
        - [x] add site_id to crawler stats [issue #58](https://github.com/disinfoRG/NewsScraping/issues/58)
    - week 2 (2/10)
        - NS: CLI [issues #57](https://github.com/disinfoRG/NewsScraping/issues/57)
        - simple web interface for crawling stats
        - 開始整理其他人做過的相關data exploration 產出
    - week 3 (2/17)
        - 修 issue #39, #43, #44, #26
        - 初步 data explore
    - week 4 (2/24)
        - data exploration
- pm5
    - week 1 (2/3)
        - [x] 改進 parser CLI 工具 [#10](https://github.com/disinfoRG/ArticleParser/issues/10)
        - [x] 解決 parser issues [#2](https://github.com/disinfoRG/ArticleParser/issues/2) [#8](https://github.com/disinfoRG/ArticleParser/issues/8)
    - week 2 (2/10
        - [x] 解決 update 時間過長問題
        - [ ] review and fix data exchange standard to add publication comments and other missing things
    - week 3 (2/17)
        - 測試 Google Drive、Linode、Amazon S3 for datasets export
        - 完成自動 export
    - week 4 (2/24)
        - build some basic tools to handle datasets using the standard

### 下次會議

## 2020/2/1 Sa
4pm
bruce, chihao
### 完成事項
- discover 寫入到台南
    - 爬了 13 個 site(69, 70, 71, 73, 74, 77, 79, 80, 87, 88, 89, 90, 91)
    - 總共 8655 篇文章
- 當 discover 在一個 site 讀進 1000 篇以上文章容易 crashed，決定 crashed 發生時關掉原本的chrome，重開新的 chrome 跑下一個 site
    - [site_id in  [69, 70, 71, 73, 77] ](https://docs.google.com/spreadsheets/d/1SvZ3xRfU-RA5S6fi_hblScW-YqcGT1sGzzeQAdKb96I/edit#gid=0) 都有發生 session deleted because of page crash 可見下方的 log 在 viewed 1039 posts 時發生此情形
        ```
        crawler_timestamp_1580527323: viewed 1039 posts, add 8 new posts, existing 1039 posts in database, empty response count #0 
        727888 723175
        handler_timestamp_1580527339: failed crawling site, {'site_id': 70, 'type': 'fb_page', 'name': '旅行．美景．看世界！', 'url': 'https://www.facebook.com/traveltheworld168/', 'config': '{}', 'is_active': 1, 'airtable_id': 'recSdwgOnLSFlZajU', 'site_info': '{}', 'last_crawl_at': None}, result is Exception of type <class 'selenium.common.exceptions.WebDriverException'> occurred in file "/usr/local/lib/python3.7/dist-packages/selenium/webdriver/remote/errorhandler.py", line 242, in check_response: [WebDriverException] unknown error: session deleted because of page crash
        from unknown error: cannot determine loading status
        from tab crashed
          (Session info: headless chrome=79.0.3945.130) 
        ```
    - 程式
        ```python
        def discover_all(site_ids, browser, logfile):
            sites = db_manager.get_sites_need_to_crawl_by_ids(site_ids)
            total = len(sites)

            has_error = False
            running_browser = browser
            with tqdm(total=total) as pbar:
                for s in sites:
                    logfile.write('\n')

                    if has_error:
                        log_handler(logfile, '<create a new facebook browser> start', s)

                        try:
                            running_browser.quit()
                            helper.wait(120)

                            from facebook import Facebook
                            from settings import FB_EMAIL, FB_PASSWORD, CHROMEDRIVER_BIN
                            fb = Facebook(FB_EMAIL, FB_PASSWORD, 'Chrome', CHROMEDRIVER_BIN, True, False)
                            fb.start()
                            running_browser = fb.driver
                            has_error = False
                            log_handler(logfile, '<create a new facebook browser> done', 'SUCCESS')
                        except Exception as e:
                            log_handler(logfile, '<create a new facebook browser> failed', helper.print_error(e))
                            break

                    log_handler(logfile, 'start crawling site', s)

                    try:
                        discover_one(s, running_browser, logfile)
                        log_handler(logfile, 'complete crawling site', s, 'SUCCESS')
                    except Exception as e:
                        log_handler(logfile, 'failed crawling site', s, helper.print_error(e))
                        has_error = True
                    pbar.update(1)

        ```
> 依照我們的演算法，這些 sites 下一次跑 discover 的時候就不會再超過 1000 篇了，是嗎？[name=Pomin Wu]

### 未完成事項
- update 的 log
- 將 fb_controller 的原型跑起來
    ```python
    sites = db_manager.get_sites_tagged_need_to_crawl()
    articles = db_manager.get_articles_tagged_need_to_update()

    if len(sites) == 0 and len(articles) == 0:
        return

    self.release_hanging_chromes()
    available_cookies = self.get_available_cookies()

    worker_type = self.WORKER_TYPE_DISCOVER
    site_tasks = []
    article_tasks = []
    for c in available_cookies:
        if worker_type == self.WORKER_TYPE_DISCOVER and len(sites) > 0:
            s = sites.pop()
            site_tasks.append(s)
            worker_type = self.WORKER_TYPE_UPDATE
        elif worker_type == self.WORKER_TYPE_UPDATE and len(articles) > 0:
            a = articles.pop()
            article_tasks.append(a)
            worker_type = self.WORKER_TYPE_DISCOVER
        else:
            break

    with Pool(5) as p:
        p.map(self.discover_site, site_tasks)

    with Pool(5) as p:
        p.map(self.update_article, article_tasks)
    ```
> 這個應該要再討論一下設計。這樣跑主機記憶體會不足 [name=Pomin Wu]

## 2020/1/30 Th
4pm
bruce, chihao
### 完成事項
- 解決 discover 之前無法繼續爬到上次停下來的進度([見此連結](https://github.com/disinfoRG/FbScraping/blob/3a1dcb9ee0088976fd608c697b6957332182baab/page_crawler.py#L52-L55))
- 完成 fb_controller pseudo code([見此連結](https://github.com/disinfoRG/FbScraping/blob/feature_fb_controller/fb_controller.py))
> 居然已經不是 pseudo 直接是 code 了嗎 XD [name=chihao]
- 測試 discover: 4.23 article/min (607/143.58)
- 測試 update: 2.39 article_snapshot/min (327/136.18)

## 2020/1/28 Tu
4pm
bruce, chihao
### 完成事項
- 解決 discover 執行緒過多的問題
    - 每隔固定時間（目前是 10 分鐘），去看 discover 有沒有掛掉或已經跑完ㄧ段時間，掛掉會重開 Chrome（[詳細可見此連結](https://github.com/disinfoRG/FbScraping/issues/5#issuecomment-579111990)）
    - 解決三個問題：
        - discover 根本跑不起來
        - discover 跑起來但沒有在爬
        - discover 跑起來有在爬，但爬的進度沒有進展
    - 邏輯
        - if 沒 discover 的log（discover 開始運行會產生 log）
            - 重開 discover
        - else
            - if 有 crawler 的時間戳
                - if crawler 最近一次的時間戳已經超過 timeout (ex. 60*10)
                    - 重開 discover
            - else
                - if 有 scheduler 的時間戳（scheduler = cron = ex. 60*10 就跑一次）
                    - if 最近的 timeout(ex. 60*60) 已經出現三個以上
                        - 重開 discover
                - else
                    - 新增 scheduler 的時間戳
            - 
        - 以上都通過，判斷 discover 是運行成功的，回傳 200
    - 範例
```python
pipeline_timestamp_1580193490: insert to database, table = Article, id = [19], data = {'first_snapshot_at': 0, 'last_snapshot_at': 0, 'next_snapshot_at': -1, 'snapshot_count': 0, 'url_hash': 3188593434, 'url': 'https://www.facebook.com/1063653903655415/posts/2813836228637165', 'site_id': 45, 'article_type': 'FBPost', 'redirect_to': None} 
crawler_timestamp_1580193490: viewed 15 posts, add 15 new posts, existing 15 posts in database, empty response count #0 
9089 9089
handler_timestamp_1580193500: complete crawling site, {'site_id': 45, 'name': '天南地北', 'url': 'https://www.facebook.com/%E5%A4%A9%E5%8D%97%E5%9C%B0%E5%8C%97-1063653903655415/'}, result is SUCCESS 
scheduler_timestamp_1580192419: main-process-hanging-checkpoint
scheduler_timestamp_1580192430: main-process-hanging-checkpoint
scheduler_timestamp_1580192432: main-process-hanging-checkpoint

  1%|▏         | 1/71 [00:31<36:36, 31.38s/it]
handler_timestamp_1580193500: start crawling site, {'site_id': 46, 'name': '杏仁哥', 'url': 'https://www.facebook.com/almondbrother/'} 

crawler_timestamp_1580193515: viewed 0 posts, add 0 new posts, existing 0 posts in database, empty response count #None 
7544 7544
handler_timestamp_1580193525: complete crawling site, {'site_id': 46, 'name': '杏仁哥', 'url': 'https://www.facebook.com/almondbrother/'}, result is SUCCESS 

```
- discover 加 log
    - page_scheduler：discover 運行的狀態、重開discover的動作
    - discover：目前抓到第幾個 site
    - page_crawler：目前抓了幾篇新文章
    - page_pipeline：寫入後db返回的id、寫入的資料、時間戳
- 解決 discover 和 update 共用一個視窗的問題
- 修正 empty_count 的邏輯，讓 discover 在同一個 site 爬第二次時可以抓到新的文章

### 待完成事項
- 解決 update 執行緒過多的問題
    - 目前偵測網頁視窗高度是否有變化，容易因為網路或顯示較慢而誤判

### 討論 - fb_controller
- db 裡既有的 Sites
- db 裡既有的 Articles
- N(=10?) Chrome instances
    - N 組 fb login cookie
- 一個 dashboard（應該可以是個 JSON file）
    - 會顯示每個 Chrome 跟 cookie 的對應關係
    - 會顯示每個 Chrome 正在執行的工作
        - 哪些 Site 正在被哪個 Chrome discover
        - 哪些 Article 正在被哪個 Chrome update
        - 就可以從這裡知道哪些 Chrome 沒事做
- 每 M(=10?) 分鐘，fb_controller 會被 cron 叫醒
    - check 是不是有當機的 Chrome
        - ... // TODO: 怎麼確定 Chrome 當機了？
        - 把當機的 Chrome 重開機
    - check 有沒有 Site 需要 discover。
        - 如果有⋯
            - check 是不是有沒事做的 Chrome。如果有⋯
                - 叫他跑 discover_one 某個 Site
            - 如果沒有⋯
        - 如果沒有⋯
    - check 有沒有 Article 需要 update。
        - 如果有⋯
            - check 是不是有沒事做的 Chrome。如果有⋯
                - 叫他跑 update 某些 Articles // TODO: 誰決定哪些 Article 怎麼分配？
            - 如果沒有⋯
        - 如果沒有⋯

## 2020/1/24 Fr
4pm
bruce, chihao
### 處理中
- 避免 discover 或 update 的執行緒過多（ex. 超過設定的最多數字6）
- 目前打算設定一個最高執行緒數ex. 6，每次新的cron會先看執行緒是不是滿了，沒滿才跑，然後每個執行緒是一個新的tab但同一個window，跑完就關掉tab但一樣不關window

### 完成事項

## 2020/1/22 We
4pm
bruce, chihao

### 完成事項
- 這兩天成功用 cronjob 跑 discover 和 update 在彰化上，寫入的資料是正確
- 有 discover 和 update 加入 progress bar 可以知道跑的進度
### 待完成事項
- 針對 discover 和 update error 的 log 做處理

discover
```python
Exception of type <class 'selenium.common.exceptions.WebDriverException'> occurred in file "/usr/local/lib/python3.7/dist-packages/selenium/webdriver/remote/errorhandler.py", line 242, in check_response: [WebDriverException] unknown error: session deleted because of page crash
from unknown error: cannot determine loading status
from tab crashed
(Session info: headless chrome=79.0.3945.130)
Exception of type <class 'selenium.common.exceptions.InvalidSessionIdException'> occurred in file "/usr/local/lib/python3.7/dist-packages/selenium/webdriver/remote/errorhandler.py", line 242, in check_response: [InvalidSessionIdException] invalid session id
```

update
```python
Exception of type <class 'AttributeError'> occurred in file "/srv/web/post_crawler.py", line 29, in turn_off_comment_filter: [AttributeError] 'NoneType' object has no attribute 'find_elements_by_css_selector'
```

- 偵測 scroll 到底

### 想討論
- 是不是像 wenyi 一樣可以來寫入到 tainan 的 db

## 2020/1/20 Mo
4pm
bruce, chihao

### 完成事項
- 更新了 [README](https://github.com/disinfoRG/FbScraping/blob/master/README.md)，說明執行方式和程式架構
- 模擬 cron 跑 discover, update 在本機，寫資料到彰化的 db，然後寫入的資料是正確的
- 修了 wenyi 今天在 [repo 提到的 bug](https://github.com/disinfoRG/FbScraping/issues/1)
### 待完成事項
- 要將 discover, update 成功跑在彰化上
    - 2020/1/20 18:25 已成功在彰化上用 cronjob 執行 discover, update
### 請求支援
- 遇到的問題： chrome 在彰化的 middle2 上跑不起來（但本機可以）
- 追蹤後發現是這個錯誤：unknown error: DevToolsActivePort file doesn't exist
- 參考可能的解決辦法：
    - [NewsScraping 中使用到 selenium 的程式碼](https://github.com/disinfoRG/NewsScraping/blob/415347c470dd1ca0e5360b3cd1b8f8181f075aad/newsSpiders/middlewares.py#L114-L124)
    - [Stackoverflow 上相關的解法](https://stackoverflow.com/questions/50642308/webdriverexception-unknown-error-devtoolsactiveport-file-doesnt-exist-while-t)
- 嘗試改用以下參數設定後再開啟 chrome：
```python
    def configure_headless_options(self, options):
        options.headless = True
        options.add_argument("start-maximized"); # open Browser in maximized mode
        options.add_argument("disable-infobars"); # disabling infobars
        options.add_argument("--disable-extensions"); # disabling extensions
        options.add_argument("--disable-gpu"); # applicable to windows os only
        options.add_argument("--disable-dev-shm-usage"); # overcome limited resource problems
        options.add_argument("--no-sandbox"); # Bypass OS security model
```
- 嘗試進度：
    - 15:00 - 16:00 原本的錯誤訊息沒有再出現，接著停在登入 facebook 帳號的步驟，然後便無法再度連線上彰化的 middle2 來驗證嘗試的解法。
    - 16:47 ronny 協助重開彰化的機器，bruce 重新嘗試連線上去，但尚未連上
    - 18:25 重新連線上去，成功在彰化上用 cronjob 執行 discover, update

## 2020/1/18 St [devs]
11:00 in jothon’s office
15:20 meeting

### 近況分享
- chihao
    - 不知道要分享什麼（好像也是好事）
    - 選後回歸工作，感覺蠻好的
- pm5
- bruce
    - 公車司機
        - 今天建國花市開始，一直到過年
- wenyi

### 進度報告
- wenyi
   - replace `ptt_board` with `discussion_board` on airtable and Site db, `discussion_board` includes ptt and dcard websites
   - add `discussion_board` to get_sites_to_crawl.sql
   - update_content_spider updates article where `article_type == "PTT" or "Article"`
   - Dcard
       - 目前只能用在 forum（不能用在 user）
       - 每個 snapshot 只會抓（從上次最新開始）新的 comment
       - 每個 forum 只能抓到 newest 100 posts
       - discover / update 各有一隻 spider
       - discover
       - update
           - `python3 execute_spider.py -u` 多開一支spider
   - 工人 fb_controller discover 42-55
       - 幾乎都有「跑完」、跑到一兩年前
       - 有時候斷線
       - 11am-3pm - 3 pages
- chihao
    - 團隊協調
    - FS、funder 聯繫、合約、整體工作計畫調整
    - 整理 HackMD book、[專案定義](/1q2T7WWbRCS837oT68uPmA)
    - 寫報告
    - 工人 fb_controller 沒跑到
- pm5
    - NewsScraper discover spider /w twisted 上線
        - \o/
        - 應該不會再出現吃光記憶體的狀況
        - 速度也還可以
    - 測試 fb crawler
- bruce
    - 工人 fb_controller 沒跑到
    - 去除掉參雜著的第三方源碼，放到新的 repo - [FbScraping](https://github.com/disinfoRG/FbScraping)
        - README 還沒
    - 本地端 cron 跑 post 的 discover 和 update 寫入 m2 上彰化的資料庫
        - 目前：本地可跑，m2 有問題，正在 debug
        - 只抓 post raw HTML
        - article url 正規化 https://www.facebook.com/{page_id or page_name}/posts/{post_id}

### 討論
- fb post discover
    - 原本 scroll 三次就不抓，可能會跟以下情形重疊
        - 應該要處理 db 斷線的情形
        - 應該要處理網路斷線或 timeout 的情形
        - 處理
            - 要有 log
            - 一次跑到底 max_try_time: 1000000
            - 每個 site 要有一個「在這之前都好了」的標註 checkpoint，就不用再繼續 scroll
- fb_controller
    - 易付卡
    - 申請全新的 email
    - 申請全新的 fb 帳號
- [x] 開獨立專案、獨立 db 給 fb crawler + parser
    - 要通知 ronny
- ~~check dependency (fb crawler 塞進 newsScraping???)~~
- [pending] fb parser
- [US-Taiwan Tech Challenge](https://disinfocloud.com/taiwan-tech-challenge)
- [(Maybe) 0archive @ RightsCon](/PgCc8ehjSp6pamNVDvnv6g)
    - also 玄彬
    - RightsCon
        - June 9-12 @ San Jose, Costa Rica https://www.rightscon.org/
        - Access Now 舉辦的數位人權大會
        - Call for Proposal: Dued on 21th Jan. 2020
- Task Tracker - YES
- Fb, Ptt, Dcard post + comment 這種，parser db 要怎麼存？
    - post
    - comments???

### 月計畫更新
- chihao
    - week 1 (1/6-10)
        - ~~推進 data explorer，目標：從《怒吼》發現一些有趣的事情，寫進 monthly report~~
        - fb 發佈 monthly report（預定：用 g0v 粉專發文）
        - 處理專案行政、撥款
        - ~~寫 1/15 的報告~~
    - week 2 (1/13-17)
        - ~~export data for 1/15 報告~~
        - 寫 1/15 的報告
        - 1/15 交報告
        - 處理專案行政、撥款
        - ~~預先來寫一些 node-edge (graph-like) 的 data explorer web UI，倒一點資料進去試試看~~
            - ~~用 ronny 在小松跑的那個~~
    - week 3 (1/20-24)
        - 推進 data explorer
            - 目標：從《怒吼》發現一些有趣的事情，寫進 report
        - 寫報告
    - week 4 (1/27-31)
        - 推進 data explorer
            - 目標：從數個網站發現一些有趣的連結
        - 寫報告
    - FEB
        - 來寫一些 node-edge (graph-like) 的 data explorer web UI，倒一點資料進去試試看
        - video/image (?)
        - 準備小松
- bruce
    - week 1
        - crawl every page for 100 posts
            > [name=chihao] 有再往更舊的 post 爬的打算嗎？
            - https://github.com/disinfoRG/facebook-nbs/blob/enhancement_page_return_url/page.py
    - week 2
        - crawl every group for 100 posts
            > [name=wenyi] I think fb group & page are pretty similar except for post author 
    - week 3
        - summarize and improve facebook crawler and parser
    - week 4
        - do auto-backtesting for crawled data
- pm5
    - week 1: cleanly manage scrapy & twisted process
    - week 2: ~~setup auto-export process for datasets~~ deploy and test
    - week 3: setup auto-export process for datasets; add web api for pipeline monitoring
    - week 4: manage data pipeline with long-standing server process
- wenyi
    - week 1
        - ptt & dcard
        - help fb parser
    - week 2
        - ~~develop tools/dashboard for monitoring crawling process~~ dcard spider & fb first discover
    - week 3
        - 研究 Dcard 登入
        - parser
    - week 4
        - be able to monitor crawling results

### 下次會議
2/3 8pm remote?

### 本週工作計畫
- bruce
    - trace facebook-nbs 上的 issue
    - batch 改目前台南 db 裡的 Article.url
    - deploy fb post cralwer
        - 不重複資料
        - 不會漏掉資料
- pm5
    - 開個 log format spec 與計劃 log monitoring
- chihao
    - fb_controller
    - email tech challenge
    - 
- wenyi 
    - PR Dcard
    - 把fb discover跑完 （use FbScraping)
    - 更改fb urls on Article

## 2020/1/16 Th
4pm
bruce, chihao

### 完成事項
- 把整理好的 code 推上 GitHub 新 repo
    - 刪除沒用到的檔案
    - 重寫 facebook.py
    - 重寫util.py
- changhua as staging

## 2020/1/16 Th
isabel, 0archive
關於專案產出、資料集釋出、授權、合約

### 整個專案的授權
- MIT 2020 0archive project
    - 在 hackmd 上開文件：定義 0archive project、處理授權的治理機制、遵守 g0v 宣言

### 專案產出
- 資料集
    - 釋出什麼？
        - 蒐集的內容，有些有著作權人，有些不知道是誰，不太可能一個一個確認
        - 不是著作權人，不能開放授權
        - 每個國家規定不一樣
        - 結論：
            - 所有 publication 以「metadata + 內容小部分」釋出
            - 完整資料採開放申請
    - 怎麼授權？
        - 授權：MIT 2020 0archive project
- 程式碼、技術文件
    - MIT 2020 0archive project
- 資料交換格式
    - MIT 2020 0archive project
- 月報
    - CC BY 4.0 International by 0archive project in accordance with g0v Manifesto
- 資料分析成果、資訊視覺化
    - CC BY 4.0 International by g0v contributors in accordance with g0v Manifesto

## 2020/1/15 We
chihao, bruce
https://github.com/Charleswyt/crawler/blob/master/LICENSE

## 2020/1/14 Tu [devs]
9am-5pm, bruce + wenyi + chihao

### 討論
- clean split between fb crawler / parser
- possible deprecation of FB*Snapshot tables in db
- fb_controller as deamon
- 在 fb_controller 上線前：建立一個手動 discover 的流程
    - 參考 facebook-nbs README 建立環境
        - env 放 fb 帳號密碼
        - db url 放 middle2 db
    - 組成「工人 fb_controller」
        - https://docs.google.com/spreadsheets/d/1SvZ3xRfU-RA5S6fi_hblScW-YqcGT1sGzzeQAdKb96I/edit#gid=0
    - 手動跑 discover

### 本週工作計畫
- wenyi
    - [ ] db migration: Article.artic_type = ptt, dcard
        - [x] new version
        - [x] to middle2 db 
        - [ ] `alembic upgrade head` on db
    - [ ] Dcard
        - [x] dcard discover 可以自己執行 (spider crawl)
        - [x] dcard discover 可以用execute_spider and batch 執行
        - [x] dcard update spider
        - [x] dcard update 加入 runner
    - [ ] see if selenium on middle2 is parsing right amount of articles
    - [x] make ptt article has article_type = "PTT"
        - [x] 更新已經在db的 -> chihao
        - [x] 更改 code for future ptt
    - [x] line & linkedin 連結要從 spider 中 filter 掉，應該直接改rules 
    - [ ] 工人 fb_controller
        - [ ] 跑 discover 寫入 middle2 (tainan)
        - [ ] discover 完成後 #disinfo 回報
        - [ ] 跑 update 寫入 middle2
- chihao
    - [x] 跟 jothon 溝通 1/14 早上的場地
    - [x] 改既有 article article_type = "PTT"
    - [x] 開新 repo for Fb scraping
    - [ ] 寫 1/15 報告
    - [x] 在 hackmd 上開文件：定義 0archive project、處理授權的治理機制、遵守 g0v 宣言
    - [ ] 開完整資料申請表
    - [ ] 工人 fb_controller
        - [ ] 跑 discover 寫入 middle2 (tainan)
        - [ ] discover 完成後 #disinfo 回報
        - [ ] 跑 update 寫入 middle2
- bruce: fb crawler (+wenyi +chihao)
    - [x] 1/14 寫新的 discover + update
        - [x] discover.py 針對一個 site
        - [x] update.py 針對一個 article
            - [x] 可以在 local 跑
            - [x] 資料可以進 local db
        - [x] update.py update_all
            - [x] 可以在 local 跑
            - [x] 資料可以進 local db
        - [x] 更新 facebook-nbs README
    - [x] 更新 update.py
        - 測試存完整網頁 raw HTML <-> 只有 post raw HTML 的容量差距
        - 提供測試結果
            - for https://www.facebook.com/185537762220181/posts/2426555417632575
                - raw HTML - whole_page_html
                    - 2.1 MB
                - post (+ comments) raw HTML
                    - 38 KB
            - for https://www.facebook.com/znk168/posts/412649276099554
                - raw HTML will casue (pymysql.err.OperationalError) (2006, "MySQL server has gone away (BrokenPipeError(32, 'Broken pipe'))")
                - post raw HTML
                    - can work
        - 做決定
            - 只抓 post raw HTML
    - [x] 重寫 facebook.py, util.py
    - [x] 刪除沒用到的檔案
    - [ ] 更新 README
        - 怎麼在本地跑
        - 說明程式結構
        - 目標：可以讓完全不會的人馬上上手
    - [x] 把整理好的 code 推上 [GitHub 新 repo](https://github.com/disinfoRG/FbScraping)
    - [x] 在本機盡量模擬 middle2 的實際情況
        - cronjob 可以在本地分別跑 discover, update
        - 可寫入本地 db，寫入的資料是正確的
    - [ ] 工人 fb_controller
        - [ ] 跑 discover 寫入 middle2 (tainan)
        - [ ] discover 完成後 #disinfo 回報
        - [ ] 跑 update 寫入 middle2
- pm5: dataset export process
    - [x] deploy twisted crawler

## 2020/1/13 Mo [devs]
3pm at jothon-HQ

### 近況分享
- pm5
    - 第一次去文化部
    - 聽說年中會有 workshop
- chihao
    - 今天早上遇到滅火器
    - 中午做瑜伽覺得無力
- wenyi
    - 秦味館 +++ 一定要點炸鮮奶
- bruce
    - 回台南投票
    - 看開票

### 上週進度
- ronny
    - 好像做了很多事
- chihao
    - fb 發佈 monthly report
        - https://www.facebook.com/g0v.tw/posts/3395349920506270
        - isabel++ bess++
        - 「備份」
    - data explorer 沒進度
    - 處理孔劉的臨時要求 isabel++ pm5++
    - 跟 FS 開會 isabel++
    - 1/15 簽約看來沒問題，延遲支薪，謝謝各位開發者的容忍
- pm5 
    - `new_discover.py` 改用 twisted 做多工，正在測試中。遇到一些問題：
        - 好像還是會抓到一些舊文章（可以討論要不要抓）
        - 有一些 line 與 linkedin 的連結應該不要抓
        - 可以討論要多一種爬蟲的類型
        - db connection 的關係，目前的做法會爬的比較慢，可以再研究怎麼加快一點
- wenyi
    - ptt 成功跑 (cookies middleware)
        - crawler 可以加 cookie 了
    - dcard: 
        - 還正在測試，看起來是需要selenium
        - dcard本身的架構好像會讓discover複雜化 https://g0v.hackmd.io/@chihao/0archive/https%3A%2F%2Fg0v.hackmd.io%2FlMQO37z6SbWNWo3R4-X_EA#Dcard-Crawler
        - 需要測試新的改動會不會影響其他網站的爬蟲
    - 看了一下 selenium 在 middle2 抓到太少網站的問題，應該是因為proxy掛掉了所以很多天都沒有抓任何東西，今早補跑
- bruce
    - 進度落後
    - 實作只抓 page 的架構到一半，希望可以討論

### 討論
- [wenyi] 希望可以把 PTT & Dcard加入 `article_type` in db 因為他們的parse邏輯應該與 article 不同
    - migration 修改 ENUM
    - op alter column or see [here](https://alembic.sqlalchemy.org/en/latest/ops.html)
- FbPostSnapshot - [希望可以討論 fb_page_snapshot 的可行性](https://g0v.hackmd.io/lMQO37z6SbWNWo3R4-X_EA?both#Facebook-Crawler)
- ronny
    - 分散式 proxy as g0v infra
- spider 好像有點複雜
    - Dcard API
        - Single post https://www.dcard.tw/_api/posts/232845717
        - Comments https://www.dcard.tw/_api/posts/232877594/comments?limit=50
    - 寫一個新的好像比較省事
- 第一次加新的 site 的時候，需不需要跑一個「不限 depth 全部抓完」的 spider
    - 有需要
    - 應該用現在的 `execute_spiders.py --discover` 設定 depth 為 0 就可以了？
        - 需要人 supervise
        - spider 有時候會跑進死胡同

### 本週計畫
來不及確定

### 下次會議
- 1/14 (Tu) 9am [Kafemera](https://goo.gl/maps/HjpMJkztWJep6Fmf8)
- 1/18 (Sa) 11am (same place) co-work
- 1/20 (Mo) 8pm (remote) dev meeting

## 2020/1/6 Mo [devs]
### Personal updates
- chihao
    - 好久沒好好運動啦⋯
    - https://watchout.tw/projects/fc-2020/
    - 不要再喝酒吃麻辣鍋了
- pm5
    - 好久沒抱石了⋯⋯今天去爬覺得變弱很多（嗚）
        - QQ
- wenyi
    - 潮境公園美！！！
- bruce
    - 跨年看了董事長樂團⋯⋯的一本書《最後一杯酒：董事長樂團的年少輕狂》

### Last week’s outcomes
- chihao
    - monthly report
    - started a nodejs data explorer... nothing interesting yet...
    - logo
    - website https://0archive.tw/
    - meeting with 1/2 Korean Stars
- pm5
    - made parser streamline
    - tested fb crawler
    - added some code to extract published_at from RDFa and a few more JSON-LD classes.
    - working on lingering subprocess problems on parser db, might need a some more time to fix it
- wenyi
    - NewsScraping: 
        - crawl site based on last_crawl_time
        - filter sites based on type for batch crawl
    - FB:
        - write a post parser
    - Add more sites to db
- bruce
    - upload crawled fb data to [this airtable link with password: 0archive](https://airtable.com/shrCK48np6MkjEtSf)
        - Article: 9781 (有些可能重複到QQ 需要檢查) 
            - FBPostSnapshot: 2457
            - FBCommentSnapshot: 6661
        - Site: 69
    - facebook-nbs (see [PRs](https://github.com/disinfoRG/facebook-nbs/pulls?q=is%3Apr+is%3Aclosed+author%3Adieface))
        - Use the correct structure to parse comment in comment
        - Bug no such element comment
        - Reuse existing logged-in browser window to crawl
        - Add instructions to fetch site list for crawling
        - Fixed getting displayed name for post's author
        - Add more information for id to site_info, post_info, comment_info, author_info
        - Script to upload local database to Airtable
        - Refactor page.py to return in view all urls of posts and comments

### Discussions
- USD / TWD
    - TWD
- 1 月工作內容
    - 資料分析
    - 工程
        - wenyi: 監控 scraper / parser 執行結果是否正確
            - 因應某些網站改結構就抓不到的情形
        - pm5: 讓 scraper & parser 都更穩定，可以放著不用管
            - 執行效率
            - process / 硬碟容量 / memory monitoring???
        - 自動釋出 dataset 的流程
        - 【抓】image/video 的獨立流程
            - 新的 db table
                - url
                - downloaded?
            - 偵測
                - fb post: fb_post_info 的 type = photo / video
                - webpage: youtube embed / fb embed / url 會顯示是 video
            - 儲存方式
                - linode / s3
                - 圖片: imgur?
        - 【抓】bruce: 把 facebook page 和 facebook group 的 crawler 做好抓完，然後 parser 至少有第一版
        - 【抓】ptt
            - 一個看板一個 Site
            - 先套用 Article / ArticleSnapshot 的模型
            - article discovery 除了「年滿 18 歲」應該可以用現在的機制
        - 【抓】dcard
            - 看板是一個 Site
                - 先看板
                - 時事板 https://www.dcard.tw/f/trending
            - 帳號也是一個 Site
                - https://www.dcard.tw/@young1632054129
            - 技術
                - https://github.com/leVirve/dcard-spider- 
                - 可能要用 selenium
                - 帳號的 api
                    - https://www.dcard.tw/_api/personas/young1632054129/posts?before=232209466
                - [看板的 api](https://github.com/leVirve/dcard-spider/blob/588913a5a77e8035147192db429da09b75db4f97/dcard/api.py#L92-L104)
                    - _api/forums
                    - _api/forums/{forum}/posts
                    - ex. https://www.dcard.tw/_api/forums/trending
- 台大新聞所在組 roundtable 討論計算方法研究媒體、社群媒體、假新聞、資訊站
    - https://docs.google.com/forms/d/e/1FAIpQLSd8X7bLJNyTlE02FMUwHZvRG2Nl-UIf0-xw2x3eKUKH1nTO4Q/viewform
- 小松大家覺得如何？
    - chihao: 不喜歡那個場地
        - 下一次想換場地
    - people?
    - pm5: 產出好像沒有預期的多
    - chihao: 可能下次 team 自己多準備一點、在報名前訂出一些具體的目標

### This month’s plan
- chihao
    - week 1 (1/6-10)
        - 推進 data explorer，目標：從《怒吼》發現一些有趣的事情，寫進 monthly report
        - fb 發佈 monthly report（預定：用 g0v 粉專發文）
        - 處理專案行政、撥款
        - 寫 1/15 的報告
    - week 2 (1/13-17)
        - export data for 1/15 報告
        - 寫 1/15 的報告
        - 1/15 交報告
        - 處理專案行政、撥款
        - 預先來寫一些 node-edge (graph-like) 的 data explorer web UI，倒一點資料進去試試看
            - 用 ronny 在小松跑的那個
    - 1/18 cowork
    - week 3 (1/20-24)
        - video/image (?)
    - week 4 (1/27-31)
        - ...
- bruce
    - week 1
        - convert into url scraping structure (thank you wenyi's advice)
            - [詳情請參考檔案局的 Facebook Crawler](https://g0v.hackmd.io/lMQO37z6SbWNWo3R4-X_EA?both#Facebook-Crawler)
        - crawl every page for 100 posts
            > [name=chihao] 有再往更舊的 post 爬的打算嗎？
            - https://github.com/disinfoRG/facebook-nbs/blob/enhancement_page_return_url/page.py
        - work for any need of 1/15's report on facebook side
    - week 2
        - facebook group crawler
            > [name=wenyi] I think fb group & page are pretty similar except for post author
        - facebook group parser
        - crawl every group for 100 posts
    - week 3
        - summarize and improve facebook crawler and parser
    - week 4
        - do auto-backtesting for crawled data
- pm5
    - week 1: cleanly manage scrapy & twisted process
    - week 2: setup auto-export process for datasets
    - week 3: separate parser from scarper db with api
    - week 4: completely manage data pipeline with twisted & asyncio & long-standing server process
- wenyi
    - week 1
        - ptt & dcard
        - help fb parser
    - week 2
        - develop tools/dashboard for monitoring crawling process
    - week 3
        - video/image (?)
    - week 4
        - be able to monitor crawling results

### Next meeting’s confirmation
- 1/13 Mon. 3pm 孔劉 + team meeting + beer
- 1/18 Sat. 1pm NPO Hub cowork

## 2020/1/4 Sa disinf0thon
https://g0v.hackmd.io/v_3RGE87S4KClrd-0ue9qw

## 2019/12/30 Mo [devs]
### Personal updates
- chihao
    - 即時事實查核總統辯論會
        - 沃草
        - 另一個：https://www.readr.tw/project/fact-check-debate-2020
- pm5
    - 吃壞肚子
        - QQ
    - 聽總統辯論會
    - 監票？
- bruce
    - 聽總統辯論會
- wenyi
    - 聽總統辯論會，推薦媽媽看沃草即時fact check
    - 腳底按摩阿姨說蔡英文額頭凹一塊一定會輸(?)
        - li joy https://www.youtube.com/user/kittyb16

### Last week’s outcomes
- bruce
    - 轉成 script，撈 post、comment 到本地資料庫
    - 41 site, 1264 post, 7679 comment
    - 寫到可以測試了！
- pm5
    - merged wenyi's JSON-LD parser & add facebook columns to db
    - made some analysis to the data we have now
    - helped bruce sort out his tasks before mini-hackathon
    - collected some ideas about roadmap
- chihao
    - news from funders
    - fake stored procedure (in Tech Spec)
        - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_da20c6eb6dc8f80dd769f6acbbeb037b)
- wenyi
    - 將新網站加入site table
    - 研究selenium怎麼用proxy
        - 密碼的問題
    - 稍微研究text diff
        - text similarity by python library `Levenshtein`
        - article snapshot <-> snapshot
        - article <-> article???
### Discussions
- Hard deadlines
    - https://g0v.hackmd.io/@chihao/0archive/
- disinf0thon plan
    - https://g0v.hackmd.io/v_3RGE87S4KClrd-0ue9qw
    - 1/4-1/11 公眾宣傳
- fb
    - 先傳資料上去？
        - 不易 merge，需要另開 db
    - 3 hr 20 min = 5156 則
    - https://github.com/disinfoRG/facebook-nbs/issues
    - snapshot 的 raw_data 額外存文字內容
        - issue
    - Article 的 redirect_to 要存
        - issue
    - 存fb的id，還是url就好
        - page
            - 顯示id
            - 顯示名稱
        - post
        - comment
        - author
            - 顯示id
            - 顯示名稱
    - Site 存 page 的資訊，例如：粉絲名單
    - 存 Reactions, Shares 裡面的人（author）
    - FBPostSnapshot 的 shared_url = Article 的 url?
        - 縮圖
    - 結論：一不二沒有
        - 不要在小松以前改
        - 沒有要整進 NewsScraping
        - 沒有要開新的 db
        - post meta -> FBPostSnapshot.fb_post_info
        - comment meta -> FBCommentSnapshot.fb_comment_info
        - deploy: pm5 can help to setup
- proxy
    - ask ronny if possible to whitelist middle2 ip
- export from db
- 1/16-2/28 work?

### This week’s plan
- bruce
    - 將撈的資料傳到雲端上的資料庫
    - 整合到 NewsScraping
        > [name=chihao] 也許還不急
    - facebook-nbs bugs 開 issue
- wenyi
    - [x] use proxy on middle2
    - [ ] try FB code
    - [ ] parser: extract complete links 
- chihao
    - [x] disinf0thon #general、後勤中心
    - [x] disinf0thon 個人推坑
    - [ ] 問 ronny 有關 export
    - [ ] elasticsearch
    - [ ] 架一個 https://openrefine.org/
    - [ ] 備份
    - [ ] daily export to S3? Linode?
    - [x] email to team on disinf0thon location
    - [x] email to participants disinf0thon location
- pm5
    - [x] add fb_post_info [JSON], fb_comment_info [JSON] to fbpostsnapshot & fbcommentsnapshot
    - [x] add site_info [JSON] column site table
    - [ ] deploy fb crawler
    - [ ] think about export datasets

### Next meeting’s confirmation

## 2019/12/28 Sa [devs]
- cowork

## 2019/12/23 Mo [devs]
### Personal updates
- chihao
    - FtO Tainan 2019 (community is “stronger” and “bigger”)
    - rode a bike
    - “otobai” is Taiwanese, Japanese && Korean!
    - 週日晚上的牛肉湯⋯
        - 鴻牛溫體牛肉
- pm5
    - 第一次用食物當 3 個關鍵字
        - <3 牛肉湯！？
    - 被幾個人建議政黨票要投給小黨，還在考慮中
- wenyi
    - 買了一台Rakuten kobo e-reader, 還滿好用的推推
    - flying on Thursday, anyone wants anything from NYC?
        - chihao: 不用！行李應該很滿吧 XD
- bruce
    - 推了8個第一次認識的朋友上台分享
    - 仙女棒
    - 第一次吃冬至菜包
    - 陪爸媽吃湯圓和香菇雞湯

### Last week’s outcomes
- chihao
    - Did not have any time to work on code
    - Met with fiscal sponsor staff Tuesday, updated them with info, sorted out details
- bruce
    - 整理好目前可以爬到的資料，輸出成json
    - 整理了一個架構
- andrea
    - pitch
    - adding selenium to middle2 -- but couldn't get anything??
        - [ ] extend wait time
        - [ ] networking issues (lower possibility...)
        - [ ] ...
- pm5
    - incorporated wenyi's parser into ArticleParser
    - export datasets in json and csv, released in hackathon
    - checked a few articles about their [traceabilities](https://g0v.hackmd.io/hDTzhxxfRqyDaiqWdL4baQ)
        - pm5++!
        - 發現《中時》文章抓得不完整
    - there is json-ld metadata in quite a few of the web sites that we can utilize
        - we parse datePublished from there

### Discussions
- 孔劉、玄彬
    - pm5: 我比較喜歡孔劉
    - 親朋好友問我在哪裏工作？「g0v 的一個專案」「幫孔劉工作」
    - g0v 的朋友問？「在 0archive」
- 投保
    - 姓名、身分證字號、出生年月日
    - 每月薪資（於薪資清冊提供）
    - 如果有眷屬需要依附投保健保
- 1/4 disinfoRG 第零次小松 disinf0thon
    - Keyholder: chihao
    - Time: 1/4 10:30-17:30
    - 是否要事先報名？
        - [x] 要
        - [ ] 不要
    - 地點資訊
        - [x] 只公佈區域
        - [ ] 公布完整資訊
    - 是否篩選參與者？
        - [x] 是
            - [x] 總人數
            - [x] 問問題
                - [ ] 請舉一個內容農場
                - [ ] 請舉一個你聽過的假訊息事件
                - [ ] 你想來幹嘛？
        - [ ] 不是
- page 要不要有另一個table，或是說怎麼跟 airtable 的合在一起
    - 投放的廣告（ad library）
    - 管理員
    - 建立時間、名稱改革歷史
    - chihao: 覺得先以目前 project scope 為主，ad lib 的資訊 maybe out of scope
- post 需要有page_id的欄位，comment需要有post_id的欄位
- facebook 用的id，跟 db 存的 index 的 id 要怎麼區別
- NewsScraping 和 Article Parser 的不同之處？
    - NewsScraping: 爬網站存入 db
        - 用 scrapy
    - ArticleParser: 把 html -> title, contents, etc
        - 不是用 scrapy 所以執行方法不一樣
- 怎麼知道某網站有用 json-ld？
    - ``<script type="application/ld+json">``
    - "@type": "NewsArticle"
        - https://schema.org/NewsArticle 
        - schema.org 想統一網路上資料的規格
- qiqi
    - is_active
- ArticleSnapshot 裡找到 url 連結可能可以成為未來的 Site

### This week’s plan
- pm5
    - [x] add post and comment id on Facebook
    - [x] FBCommentSnapshot add post_id
    - [x] FBPostSnapshot add page_id
    - [x] merge wenyi's JSON-LD-capable parser
- pm5 + bruce co-work
    - 12/28 2pm 不會在礁溪
- chihao
    - [x] email to connect FS with 0archive task force
    - [x] update email to GY & HB
    - [x] update roadmap + events + deadlines
    - [ ] fiscal sponsor USD/TWD
    - [x] budget sheet + schedule [執行計畫](https://docs.google.com/spreadsheets/d/1GYZ_s16-qa7iczB-ClMemsfDtI3hNA6aGILNrFEOX2E/edit#gid=2052037572)
    - [x] disinf0thon Google Form / TypeForm...
    - [ ] disinf0thon promotion
- wenyi
    - [x] 放新的 site 進去
    - [ ] 需要 selenium 的網站加進去跑，monitor 一下
        - pm5: 有問題 slack 問一下
    - [ ] 看資料集
        - 抓到內容對不對、有沒有漏、需不需要加什麼欄位
            - e.g. 連結有沒有都找出來？
                - nooho: readability doc.summary() 遺漏了一些文章來源，因為被包在``<div class=article-source>`` 中
            - 連結有沒有待爬網頁列表
        - 簡單分析 （下一步要做什麼？）
            - e.g. textdiff
    - [ ] check issue
- bruce
    - [ ] 將 notebook 轉成 .py 的 script
    - [ ] 串接 site 的 table 上的 fb 粉絲頁，存爬到的資料到資料庫

### Next meeting confirmation
- dev meeting 12/30
- community hangout 1/2???
- disinf0thon 1/4

## 2019/12/16 Mo [devs]
- personal updates
    - chihao: 進度 delay 大家對不起 QQ
    - wenyi: 切到手了....打字變很慢
    - pm5: 福岡的湯布院不錯。有柚子辣椒口味的洋芋片，名產。
    - bruce: 房東重新裝地板；幫忙選舉大補帖
- last week’s outcomes
    - chihao
        - taoyuan-chu-975484
        - compensation
            - still need a couple of days
        - budget
            - personnel + insurances + retirement...
        - comm w/ fiscal sponsor (isabel++)
            - encoding
            - pending contract review
        - comm w/ funders
            - different progress
    - pm5
        - update [architecture](https://g0v.hackmd.io/lMQO37z6SbWNWo3R4-X_EA?view#%E7%A8%8B%E5%BC%8F%E6%9E%B6%E6%A7%8B)
        - update [data standard](https://g0v.hackmd.io/0Mt45bP_TQ2g0jRFP0tfTA)
            - hope to unify web articles / fb posts / LINE messages
        - merged facebook db tables
        - test wenyi's selenium branch and deploy it (but not finished yet)
            - 迷樣頭條（？）
                - 還有兩個 iframe!?!?!?
        - set up parser project
            - chihao: delay so sorry m(_ _)m
        - wrote a very simple data export script on parser db
    - wenyi
        - update airtable (selenium add to config)
        - selenium scrapy
            - [ ] 今日頭條
        - parser
            - meta tag
            - logging
    - bruce
        - 問題
            - 展開全部留言，比較花時間
            - 留言的互動數，只看得到圖片，沒有明顯的html特徵值
            - 還沒接到專案的資料庫
        - 完成
            - 展開留言中的留言
            - 文章
                - 永久網址
                - 文字內容
                - 發布時間
                - 互動情形
                    - 各互動類別的數字
                    - 互動總數
            - 留言
                - 永久網址
                - 文字內容
                - 發布時間
                - 互動情形
                    - 互動總數
                - 留言者的fb用戶id
                - 回應哪一則留言(永久網址)
- discussions
    - payment plan
        - 詢問美國帳號
        - 付款日期：每月 5 日前
    - community hangout scheduling
        - bi-weekly? tri-weekly?
        - 進度報告（已經有在做）
        - developers’ opinion on community hangout?
            - 了解對於使用專案產出的想法
    - 決定（一、二月）小松行程
        - 1/4
            - 一整天
            - chihao 場地、食物
                - wenyi: 想吃炸雞腿飯（雞腿 *2）
            - pm5, bruce, wenyi++++
            - mg
            - 1/11 大選
        - 1/18?
        - 2/15
            - pm5, bruce
        - 3/14? g0v 大松月
        - 4/11
        - 5/16? g0v 大松月
            - 5/20 就職
    - 大松上台提案
        - chihao: 不太想要我一直講
        - pm5: 覺得我也講很多了
        - https://g0v.hackmd.io/VS8C89GxQS68nWdNlAnqkg
        - 當天提案列表： https://docs.google.com/spreadsheets/d/1W7m11EOosq2n-gc0w4SBht2CuwoYr5L6ZbuBaKyZ2RA/edit#gid=1
        - 前一次大松： https://docs.google.com/spreadsheets/d/1RPuEYKVTyNqjEyHCE-HqIgZguGIBbBKzrFnkyCoxkzM/edit#gid=1
        - 提案內容
            - 簡短介紹（五句話？）
            - 今天釋出哪些資料？
                - 什麼資料集？？？
                    - 哪些網站
                    - 刊登了什麼文章
            - 大松當天要找什麼人
                - 來一起玩資料的人
                    - article content 處理、（半）自動分析
                - 可以做資料視覺化的人
                - 來畫插畫？設計 logo？
                - 法律顧問！？
            - disclosure
                - funding
                    - 這個專案是有資金的
                    - 專案團隊還在評量公開資金來源的風險，並不是不公開。
                - 法律
                    - 備份的資料都是別人的哦
            - 如果有興趣加入團隊，可以先來參與、聊聊
            - 宣傳小松 1/4
- this week’s goal
    - bruce
        - [x] 記下文章和留言的爬蟲時間、raw data
        - [ ] 抓文章的分享情形
        - [x] 抓留言各互動類別的數字
        - [x] push 到 [github repo](https://github.com/disinfoRG/facebook-nbs) 上
        - [ ] 單純分享沒文字的post，應該抓什麼作為content，ex. https://www.facebook.com/verachen.taiwan/posts/2790994537617842?__tn__=-R
    - wenyi
        - [x] TW Thursday morning: 提案第一版
        - [ ] 今日頭條
        - [ ] kknews 有時候可以有時候不行 -- monitor
        `您的訪問請求未能通過驗證 非常遺憾！由於您訪問請求未能通過我們的驗證，我們暫時無法爲你提供服務。請嘗試使用其它瀏覽器或稍後再訪問。`
        - [ ] CTWant: weird website...網頁沒有連結 但可找到文章網址，重點是每次開網頁都關不起來....
        - [x] 測試 selenium on middle2 (chromedriver install on m2-build.sh)
    - pm5
        - [ ] 把 parser 接起來，用最新的 snapshot 生出 dataset
        - [ ] 寫一個快速生出 snapshot diff 工具
    - chihao
        - [ ] ~~elasticsearch~~
        - [ ] 與 fiscal sponsor 建立良好關係
            - [ ] 12/17 meeting
        - [ ] 12/17 寄信警告 funder
        - [ ] finish budgeting
        - [ ] 開 schedule
        - [ ] 開看板（？）
    - 想做還不確定有沒有時間做的
        - fabric
            - fab db-migrate
            - fab build deploy
            - fab test
            - fab discover 跑 discover spider
        - chrome drive on middle2
- chihao 追加事項： 大家目前有做 work log 嗎？
    - pm5: 我有一個 tgif folder weekly planning
        ```
           $
          1 This Week (2019/12/15-21): week 51$
          2 ---$
          3 $
          4 * g0v: disinfo, publish 1st batch of datasets. (0%)$
          5 * g0v: disinfo, talks & issues & on boarding & diagrams for hackathon. (0%)$
          6 $
          7 Next Week (2019/12/22-28): week 52$
          8 ---$
          9 $
         10 * g0v: disinfo, prepare for the 1st meetup.$

        ```
    - pm5: daily planning...
        ```
        - [X] disinfo: write basic data publishing code.
          - [X] setup new project for parser.
          - [X] deploy new parser project.
          - [X] write JSON export code.
        - [ ] disinfo: documenting project structure.
        - [X] disinfo: join dev meeting.
        ```
- wenyi: 目前 Parser output
```json
{
  "article_id": 1,
  "snapshot_at": 1576094962,
  "meta_property": {
    "og:title": "五十歲新加坡大叔，同齡人在給子女帶娃，他在秀顏值身材！",
    "og:type": "article",
    "og:locale": "zh_tw",
    "article:author": "https://www.facebook.com/read01.tw",
    "article:publisher": "https://www.facebook.com/read01.tw",
    "fb:pages": "138044993314451",
    "fb:app_id": "1953515198281701",
    "og:url": "https://read01.com/8zz4JJg.html",
    "og:description": "帥哥是什麼樣的？小鮮肉？雅痞大叔？還是肌肉潮男？如果這些都集於一身那豈不是帥翻很多迷妹了？他就是這樣時而鮮肉萌一臉▼留著鬍子就是雅痞大叔▼脫掉衣服變身肌肉潮男▼他叫陳宇飛，是新加坡一名攝影師如果不說年齡，大家應該覺得他三十幾歲最多四十歲吧，可現實是他已經50歲",
    "og:image": "https://i1.read01.com/SIG=21pb92u/30477454326468517357.jpg",
    "og:image:width": "640",
    "og:image:height": "640"
  },
  "meta_name": {
    "viewport": "width=device-width,initial-scale=1,maximum-scale=1,user-scalable=0",
    "generator": "WordPress 4.8",
    "robots": "noarchive",
    "google": "notranslate",
    "description": "帥哥是什麼樣的？小鮮肉？雅痞大叔？還是肌肉潮男？如果這些都集於一身那豈不是帥翻很多迷妹了？他就是這樣時而鮮肉萌一臉▼留著鬍子就是雅痞大叔▼脫掉衣服變身肌肉潮男▼他叫陳宇飛，是新加坡一名攝影師如果不說年齡，大家應該覺得他三十幾歲最多四十歲吧，可現實是他已經50歲",
    "twitter:card": "summary_large_image"
  },
  "title": "五十歲新加坡大叔，同齡人在給子女帶娃，他在秀顏值身材！ - 壹讀",
  "main_text": "免責聲明：本文內容來源于 ，文章觀點不代表壹讀立場，如若侵犯到您的權益，或涉不實謠言，敬請向我們提出 。",
  "external_links": [
    "mailto:webmaster@read01.com"
  ],
  "image_links": []
}
```
```json
{
  "article_id": 2,
  "snapshot_at": 1576094962,
  "meta_property": {
    "og:title": "遭遇整容選秀風波，為上位當小三，然而這並不影響她成為豪門闊太",
    "og:type": "article",
    "og:locale": "zh_tw",
    "article:author": "https://www.facebook.com/read01.tw",
    "article:publisher": "https://www.facebook.com/read01.tw",
    "fb:pages": "138044993314451",
    "fb:app_id": "1953515198281701",
    "og:url": "https://read01.com/RnnKogG.html",
    "og:description": "出道就遇整容選秀風波、為上位插足導演婚姻當小三、全港男人都看光過她的身體……這些都沒能影響她成為豪門闊太，婚後老公也多年疼愛不改，孩子也遺傳到了她的高顏值，有著故事一般的人生，到現在她的顏值還保持著最佳狀態。",
    "og:image": "https://i3.read01.com/SIG=2tjq3b/30477068466143356974.jpg",
    "og:image:width": "372",
    "og:image:height": "400"
  },
  "meta_name": {
    "viewport": "width=device-width,initial-scale=1,maximum-scale=1,user-scalable=0",
    "generator": "WordPress 4.8",
    "robots": "noarchive",
    "google": "notranslate",
    "description": "出道就遇整容選秀風波、為上位插足導演婚姻當小三、全港男人都看光過她的身體……這些都沒能影響她成為豪門闊太，婚後老公也多年疼愛不改，孩子也遺傳到了她的高顏值，有著故事一般的人生，到現在她的顏值還保持著最佳狀態。",
    "twitter:card": "summary_large_image"
  },
  "title": "遭遇整容選秀風波，為上位當小三，然而這並不影響她成為豪門闊太 - 壹讀",
  "main_text": "出道就遇整容選秀風波、為上位插足導演婚姻當小三、全港男人都看光過她的身體……這些都沒能影響她成為豪門闊太，婚後老公也多年疼愛不改，孩子也遺傳到了她的高顏值，有著故事一般的人生，到現在她的顏值還保持著最佳狀態。     曾經一襲紅衣、黑髮紅唇的邱淑貞，驚艷了多少寂寞少年郎的心。   上個月是邱淑貞49歲的生日，淑貞曬出三個女兒和乾媽上山詩鈉為她慶祝49歲生日的照片，女兒罕見同框，照片立刻引發了網友的熱烈討論。   尤其是大女兒沈月，很多人都在她的身上找到了媽媽邱淑貞的影子，更是被封為「最美星二代」。   每看到倆母女同框，目光依然會不自覺的停留在邱淑貞身上。   一是因為邱淑貞確實保養的好，女兒15歲，她49歲，但是單從照片看，真的看不出34歲的年齡差。不止是臉，連身材也絲毫沒有年齡差。另一方面是因為喜歡邱淑貞身上那種被歲月打磨後的氣質，這可是青春朝氣的女兒們身上沒有的一種美。   難道美人，連歲月都會對她溫柔以待？19歲和49歲的邱淑貞看不出大的差別，青澀褪去僅是平添了幾分成熟優雅。  闖入港姐12強、被質疑整容退賽  邱淑貞19歲的時候參加了87年的港姐選美，是當時的大熱門選手。當年港姐的水準比現在可是高出許多的，能成為熱門人選的都是實力美女。透過差到不行的畫質，也能看到她俏麗的五官。眼睛亮亮的，鼻子又小又挺，而且笑起來很甜。 她本來人氣極高，卻被同行的選手背後捅刀子，說她下巴曾經整過容，一時間議論紛紛，最後她無奈退賽。   塞翁失馬，焉知非福？就在她心灰意冷的時候，影視公司看中了她優秀的外形條件，把她簽了下來。幸運的是，邱淑貞的第一部戲就是和當時已經聲名鵲起的梁朝偉合作，在《新紮師兄1988》中飾演機敏可愛的小秘書，人設好，演得又清新自然，邱淑貞就這樣走進了大眾視線。   邱淑貞的事業仿佛登上了快車道，一路狂奔，她先後和周潤發、周星馳、張國榮等一眾大牌明星合作，留下了很多經典角色。她演戲演得痛快淋漓，人們也記住了這個長相精緻、演技靈動的女孩。   《鹿鼎記》里，她是那個刁蠻任性的建寧公主，你說她惡毒吧？她愛上韋小寶的時候卻失去了驕傲，甚至很可憐；你說她善良嗎？她施虐成狂，做的事情荒唐殘忍。她明面上身份尊貴，卻擁有虛假的親情和身份，周圍人暗地裡都瞧不起她，這個角色性格複雜，邱淑貞卻把她塑造得生動可愛。   她清純起來，可以像一頭睜著眼睛看著你的小鹿。她是《倚天屠龍記》里的小昭，而且小昭的人設加成，讓邱淑貞在直男心目中更加完美。邱淑貞演的這幾個金庸筆下的女性角色備受好評，她自己也火了起來。   當你以為邱淑貞是個可愛的小妹妹時，她性感起來又能撩你一臉。注意她的眼神依舊勾人，所以人們都說她是「天使的面孔，魔鬼的身材」，她的性感不是肉慾，而是性感到骨子裡。 八九十年代香港女神備出，邱淑貞不僅靠顏值，演技也是相當棒、戲路很寬，無論什麼扮相都毫無違和感。   拍三級片，轉身嫁給英俊總裁 1988邱淑貞年遇到伯樂王晶後，一改往日清純形象，徹底被送上性感女神的神壇。王晶為她打造了多部釋放性感的限制級電影，也讓她的名字打上了性感的標籤，邱淑貞三個字，就是行走的性魅力教科書。   可以說「王晶造就了她，也是她成就了王晶」，因此兩人傳出了緋聞。而導演王晶是有妻子的，在1978年已經結婚，為此邱淑貞承擔了近十年的小三之名。   1997年邱淑貞認識了如今的丈夫，香港I.T時裝集團主席沈嘉偉，兩人很快相戀。因為邱淑貞曾參演過三級片，有朋友對沈嘉偉說：「邱淑貞，很墮落啊！」沈嘉偉只答：「墮落？但我快樂啊」。只靠這麼一句話就堵住了悠悠眾口。這個男人讓邱淑貞滿滿的全是感動，認定了這個人就是自己值得一生相伴的男人。 在邱淑貞30歲生日那一天，沈嘉偉向邱淑貞求了婚。1999年31歲的邱淑貞嫁給了沈嘉偉。   嫁為人婦後，邱淑貞便退出了演藝圈，再沒接過戲，婚後，沈嘉偉主動將公司股份分給了邱淑貞，邱淑貞成為了名副其實的老闆娘。 婚姻生活頗為甜蜜，還經常全家人出外遊玩，沈嘉偉對邱淑貞寵愛有加，有趣的是，二人婚後，沈嘉偉身價直線上漲，生意越做越大，她被冠以香港第一旺夫相。接著，他們陸續生下了3個女兒，一家人更全是幸福的模樣。   在媒體拍到的照片中，她和老公總是手牽著手，帶著孩子去看演唱會、去逛街，一家人其樂融融，眼裡心裡都是愛。   很多富豪找了女明星之後都會反對在演藝圈的發展，不過對於沈嘉偉來說，十分尊重她的想法，他覺得邱淑貞愛她的工作，他就會支持她，從來不關心別人的想法。 而且生活中，丈夫也會為她分擔。全家一起出遊時，老公還各種負責打下手、抱孩子。   擁有年輕的心態 女人\"修內\"夠不夠，通常會體現在面對變老這件事的心態上。 良好健康的心態是需要通過不斷閱讀、看電影、體驗不同的人生而收穫的，當眼界開闊了，看事物也會更客觀一些，看問題的高度會更高一些。   47歲，她本該是一副中年婦儒的樣子，但看著她與自己14歲的女兒出街，依然光彩照人，像極了姐妹。  ",
  "external_links": [],
  "image_links": [
    "https://i3.read01.com/SIG=1qddjui/30477068466135316544.jpg",
    "https://i2.read01.com/SIG=ujsif8/30477068466148493552.jpg",
    "https://i2.read01.com/SIG=4c9i2d/30477068466171634431.jpg",
    "https://i1.read01.com/SIG=37hr1n2/30477068466166587066.jpg",
    "https://i3.read01.com/SIG=1pq9f8g/30477068466156593668.jpg",
    "https://i1.read01.com/SIG=2jaf2pm/3047706846614365324b.jpg",
    "https://i3.read01.com/SIG=v2it2k/30477068466176647177.jpg",
    "https://i1.read01.com/SIG=1bq26gh/304770684661427a5433.jpg",
    "https://i3.read01.com/SIG=2vaujbp/30477068466165505641.jpg",
    "https://i3.read01.com/SIG=2ujtppr/304770684661654f5674.jpg",
    "https://i1.read01.com/SIG=5v24aa/30477068466131474457.jpg",
    "https://i1.read01.com/SIG=2b6lol6/30477068466173796530.jpg",
    "https://i3.read01.com/SIG=38idf1o/30477068466155584865.jpg",
    "https://i2.read01.com/SIG=8suh28/304770684661544b3643.jpg",
    "https://i1.read01.com/SIG=19cq5r8/3047706846616c516254.jpg",
    "https://i3.read01.com/SIG=p7arct/304770684661694e5553.jpg",
    "https://i3.read01.com/SIG=302sk47/304770684661314b4b32.jpg",
    "https://i3.read01.com/SIG=3j0pc4o/30477068466144784447.jpg",
    "https://i3.read01.com/SIG=2tjq3b/30477068466143356974.jpg"
  ]
}
```

## 2019/12/12 Th

Time: 12/12 8-9pm
URL: https://meet.jit.si/disinfoRG

### Agenda
- 零時檔案局 0archive 進度報告 [chihao]
- 爬資料 / data mining 的法律問題
    - 「合理使用」
    - EU 比較進步
    - 台灣沒判例
    - 自己用 vs 爬下來之後公開 不一樣
    - metadata 通常都是 ok 的
    - 在台灣會牽涉到的問題
        - 隱私權
        - 著作權
        - 各網站的使用者規範
    - 資料庫遷到⋯（？）
- https://islander.ailabs.tw/
    - API?
    - 別重工
    - 看是不是 dump 一份出來看島民衛星有沒有興趣
- 1/4 小聚
    - mg +1

### Action items
- 今天 hangout 之後，會想要做什麼嗎？

## 2019/12/9 Mo [devs]
### Agenda
- personal updates
    - chihao: woke up every early so sleepy now
    - pm5: dinner @ 7-11 now; hot spring in Fukuoka 
    - wenyi: woke up every early so sleepy too
    - bruce: dealing with rental apartment issues
- last week’s outcomes
    - chihao
        - documents
        - meeting with Adam
        - pseudonames
    - pm5
        - db schema -> bruce
            - 已開 branch 已開 PR 等一下應該可以 merge
            - db 要跑 migration 心臟停一拍但應該可以順利完成
        - data exchange spec
            - 確定 scope：資料集涉及的對象
                - 從爬蟲角度：Site / Article / ArticleSnapshot
                - 從資料交換的角度：組織、人
                - 從 FC 角度：claim
            - 讀 schema.org / frictionless 相關 spec / 其他比較不相關的 spec
        - 測試了 readability (XD) 修了一個 unicode bug
    - wenyi
        - 寫 parser pm5++ 結果還不錯
        - 可以拿到
            - title
            - content
            - links
            - image url
        - 還沒想到
            - 日期
            - 作者
        - 問題：parser 分開，不要放進 Scrapy
        - 發現：kknews 兩個網站，文章會卡在 loading
        - 結合 selenium + scrapy
            - 解決上面的問題了 wenyi++++
        - 問題：怎麼決定 loading complete？
            - 目前：每篇等 5 sec
            - OK
        - 目前：哪些 site 需要用 selenium
            - airtable 開 column
            - [x]寫進 config
        - 問題：parse 以後的資料要去哪裡？
            - mysql
                - 另一個 db
                - parser 記得上次 parse 到哪個時間點
            - elastic search
        - 問題：定期清理 snapshot
            - pm5: 大松之後再來處理
    - bruce
        - 用 cookie 登入
        - 往下滑動 n 次，抓更多文章
        - 還沒
            - 有找到「所有文章都抓完的」的那個 css selector
            - 每次滾動停 2-3 秒
            - 更多、更多留言
            - 抓留言
            - 抓文章 permalink
        - 有找到另一個抓 fb 的
- 關於中國
- 大松的 dataset
- committment
    - bruce: full-time until end-of-May
    - pm5: full-time until end-of-March
    - wenyi: full-time until end-of-May
    - full-time = 65 hours / 2 weeks
    - Rate
        - negotiate
- next meeting
    - 12/12 Th. 8pm (TW) community hangout; devs optional
    - 12/16 Mo. 8pm (TW) dev meeting
- 小松
    - 1/4
- this week’s plan
    - chihao
        - [x] 問 ronny 開另一個 db 存 parsedText
        - [ ] 問 ronny 開 elasticsearch
    - wenyi
        - [x] 清理無意義 snapshot
        - parse 後的資料去 new db (wait for chihao)
        - [x] selenium 設定放進 site config
        - new site CTWant
        - [x] meta-tag
        - add back 'active' sites after selenium-scrapy merge and deploy to middle2
    - bruce
        - push code to GitHub/disinfoRG
    - pm5
        - [x] move author out of Article into FBFooBarSnapshot
        - format and tools for published data [0.0.1???]
            - 要先清理 snapshot
            - 是 parsed text

## 2019/12/5 Th

Time: 12/5 8-9pm
URL: https://meet.jit.si/disinfoRG

### Agenda
- 自我介紹一番
- 有什麼想要聊的可以加在這裡
    - 最近不實訊息的新聞？
    - 生活中遇到不實訊息的例子？
    - 與其他人溝通、澄清不實訊息的障礙？
    - ...

### Action items
- 今天 hangout 之後，會想要做什麼嗎？

## 2019/12/2 Mo [devs]
### Agenda
- last week’s outcomes
    - pm5
        - done airtable pull script
            - 只要有 is_approved 就會抓
            - config / is_active 要自己改資料庫
        - fixed deployment problems
        - drew an architecture
            - \o/ 不是確定版本，幫助討論
        - done a simple GraphQL api at `api` branch but not merged yet
    - wenyi
        - batch_discover.py
            - 會抓 is_active Sites
        - logging to file 到 .log directory 中
        - 幾個網站抓不太到東西，稍微研究了一下
            - 今日頭條
                - 版本過低，要升級瀏覽器
            - KKnews 每日頭條
                - 會抓到 "loading" 的頁面
            - 目前還不太確定 scrapy
    - chihao
        - worked on required docs
        - 如果順利，兩週後第一筆 $$$
    - bruce
        - 用了 selenium 模擬瀏覽網頁抓 fb post，存成 csv
            - 漏了網址
            - 「更多」
            - 抓不到留言
            - 文章裡引用的其他連結
            - 最後應該可以抓的資料格式，參考：https://github.com/rugantio/fbcrawl
        - scrapy 遇到 fb 要求驗證
        - Graph API 有免費額度限制，也遇到 redirect URI 失敗的問題
        - 改善
            - 通用
            - 改善方式，參考：https://github.com/Charleswyt/crawler
            - 用 cache 登入，就不用一直重複登入，被fb 擋
            - 抓每次滾動網頁完整刷新完以後的訊號值來判斷
            - chihao: CrowdTangle?
                - 必須先討論 governance
- discussions
    - 這週要修 crawler，還是要準備釋出資料集？
        - wenyi: 有 capacity 可以準備資料
        - pm5: 傾向先產出一個可以用的資料集
            - HTML => TXT
            - HTML => links
            - 有資料集就可以有 feedback
            - wenyi 也可以開始試試看 data analysis
        - selenium
            - 要不要整合到 NewsScraping (scrapy 有 middleware)
            - scrapy selenium middleware 
                - http://mroseman.com/scraping-dynamic-pages/
                - https://stackoverflow.com/questions/31390569/integrating-selenium-with-scrapy
    - 如果這週朝著一個可用的資料集？
        - Readability and ElasticSearch
        - 資料格式
        - 文章裡的 links
    - wenyi 可以先來試試看可以做到什麼
        - 文字內容
        - 假如很順利的話，想研究 selenium + scrapy
    - bruce 繼續改進 selenium
        - 完整內文
        - like/reactions
        - comments
        - 暫時是個分開的工具，也沒問題，資料格式一致就好
        - 參考的
        - db schema 提案 => [tech spec](https://g0v.hackmd.io/lMQO37z6SbWNWo3R4-X_EA)
    - pm5
        - 會開 db schema 給 bruce
        - data set schema
        - 如果有涉及 architecture 再跟大家討論
    - db migration: +Article.type +FbPostSnapshot???
        - pm5 + bruce 確定 schema 之後 migrate
    - after meeting: pipenv & black party! led by @pm5
        - pm5 + wenyi 先繼續討論、發展
        - bruce 目前的工作暫時用不到
        - chihao 暫時無法加入開發 (cry)
    - some [problems](https://middle2.com/project/cronlog/tainan-sun-500796#log-2019-12-01T18:37:33+08:00-53) with duplicated article url hash? 
        > [name=wenyi] 已經加到 github issue
    - kknews and toutiao problem?
    - Facebook crawling: how is it going?
    - What will we do on December g0v hackathon?
        - release some data sets?
        - 大松提案 https://g0v.hackmd.io/VS8C89GxQS68nWdNlAnqkg
        - 新 project idea
            - 是好的，因為 0archive 就是要產出資料集支援其他的專案
    - [Architecture](https://g0v.hackmd.io/lMQO37z6SbWNWo3R4-X_EA#Architectural-data-flow)
        - 處理過的資料和現在的 raw data mysql db 分開？
    - [PuqSQL](https://pugsql.org/tutorial) is quite nice actually.
        - pm5: 覺得比寫 SQLAlchemy 簡單
- things we could do this week
    - [Fabric](http://docs.fabfile.org/en/2.5/) for maintenance scripts.
    - Readability and ElasticSearch
    - hackath37n project pitch
    - config
        - article (required, dtype string)
        - following (required, dtype string)
        - depth (optional, default 0, dtype int)
        - delay (optional, default 1.5, dtype int)
        - ua (optiona, default "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.108 Safari/537.36", dtype string)
    - 怎麼拿錢
        - 大家自己決定
        - 需不需要針對居住地調整薪資？
    - [ ] pm5
        - [ ] data schema & standard; picture of final output of the project in terms of datasets.
        - [ ] db schema for FB posts.
        - [x] clean up Site table in db.
        - [x] add config options to airtable that are synced to db.
    - [ ] wenyi: 
        - [x] extract 文章內容, url連結, 發布日期等有用資訊from html (try readability)
            >[name=wenyi]
            >1. should parser be in the itempipeline? (don't think so)
            >2. date/author parsing not done
        - [x] scrapy selenium middleware
            >[name=wenyi]
            >1. ideal way of determining the page has loaded
            >2. ideal way of storing which website needs selenium
    - [ ] bruce
        - [ ] 多次登入不被fb擋、點擊文章的更多、滾動頁面更新（參考：https://github.com/Charleswyt/crawler）
        - [ ] 文章網址、抓留言、文章中出現的連結和其他資料欄位（參考：https://github.com/rugantio/fbcrawl）

## 2019/11/25 Mo [devs]

### Agenda
- intro. bruce (and any newcomers)
    - Welcome @bruce \o/
- last week’s outcomes
    - chihao
        - work plan: https://docs.google.com/document/d/1g4Tf2q6lMX8-DelxRhhR6pBNGk42Jae76AjMMvbiZQk/edit#
        - will sign a contract
    - wenyi
        - news sites / content farms 抓完了
            - 「今日頭條」抓不到
            - 「KKnews」也抓不太到
            - 「中國時報」不是非常好抓
    - pm5
        - middle2 deployed!
        - release workflow
            - pm5: 希望大家想 release 就 release
        - last weeks’ todo all done
- discussions
    - crawling algorithm and schedule tuning
        - 「抓不太到」的狀況？
        - 今日頭條: maybe 回應的內文都沒有 link？maybe 是 JS load 內容？or iframe
        - KKNews: 有分頁，看起來後面的頁數沒抓到
        - Site table 加 delay etc. 參數、加 `active` column 讓已經失效的網站不需要跑
    - airtable
        - periodically pull new sites from airtable to MySQL
        - need engineers' approval before pushing to MySQL
    - [github flow](https://guides.github.com/introduction/flow/), db migration /w [alembic](https://alembic.sqlalchemy.org/en/latest/), release flow
        - 自己覺得需要 reviewer 比較安心的話就自己隨機加 reviewer，不然就自己 merge to master
        - merge master 之後儘快 deploy by push middle2
        - 順手在 #disinfo 通知大家
    - [pipenv](https://pipenv.kennethreitz.org/en/latest/) & [black](https://github.com/psf/black)?
        - pipenv = 管理 python 套件
        - 暫訂拜四會議結束後來一起弄一下安裝與使用
    - db backup plan
        - script auto dump?
        - Google drive upload api
    - chihao: start crawling fb pages & groups?
        - too soon?
            - 工程上負擔太大？
            - 期待儘早開始爬爬
        - https://github.com/ronnywang/fb-post-crawler
        - https://github.com/FalseChord/fbcrawl
        - bruce 先跑一跑🏃🏻‍♂️，好的話來討論 FBPostSnapshot db schema，然後改一改把資料餵進去
    - bruce: 怎麼偵測有沒有新的網址？
        - wenyi: 從 db 拉出所有網址，scrapy Link Extractor 'deny'
    - bruce: 怎麼決定哪個 Site 是不是 active
        - wenyi: 點進去看連不連得到？
        - 偵測很久沒有新網址？
    - meeting time???
        - dev meeting 和 community hangout 分開
        - dev meeting: Monday 8pm TPE / 7am NYC -> dev 務必參加
        - community hangout: Thu 8pm TPE -> 自由參加
- things we could do this week
    - monitoring spiders: dashboard API and UI
    - speed up crawling
    - elasticsearch
    - readability
    - scaling spiders
    - export data
- 

### TODOs
- [x] bruce: give chihao email (GitHub + Google)
- [x] chihao 修改 gcal
- [x] chihao: add bruce to GitHub org & middle2 & gcal events
- [ ] bruce: 跑跑看 FalseChord/fbcrawl
- [x] pm5: airtable pull
- [ ] pm5: basic dashboard API as in [here](https://g0v.hackmd.io/lMQO37z6SbWNWo3R4-X_EA?view#Monitor) (we use GraphQL)
- [x] wenyi: 包每隻discover spider的程式 (asychronous) + monitor
- [x] wenyi: site config (depth, crawl delay...) + column "active"

## 2019/11/20 We [devs]
- Payment
    - Has approval
    - 20% up-front payment with software
    - Not attached to the work plan
    - 2 weeks for funds go to through
- Contract OR Grant
    - Contract: lumpsum payment attached to deliverable
        - for their goal
        - much less paperwork for us
        - advice: easiest way to go forward
    - Grant: report on interim progress towards agreed goals
        - for g0v’s goal
- [maybe] Delegation in March
- [maybe] A new idea
    - Raise visibility of people / government’s work in TW
    - Doing a (kind of) documentary
    - Through the cfall network (perhaps)

## 2019/11/18 Mo [devs]
- first/last/next_snapshot_at use unix timestamp (to seconds)

### issues?
- 各網站的 parser
- fail-safe
- 自動化
- headless chrome?
- dashboard
- 整體 achitecture

### pm5 + wenyi
- 2 repos
    - https://github.com/disinfoRG/NewsScraping
    - https://github.com/pm5/0ar
- use env to store secret
- db migration
    - https://github.com/pm5/0ar/blob/master/migrations/versions/95de751e529c_initialize_db.py
    - `alembic upgrade head`
- Python dependency management
- 合起來的話感覺可以互補
    - wenyi 的 spider 比較完整
    - pm5 repo db schema, py 套件管理
    - 理論上花個 1、2 天

### TODO this week
- [wenyi] snapshot all sites
    - wait 4 hours for chihao
- [pm5] 合併 repo，目標可以上 middle2
    - 把 0ar 先放到 NewsScraping 的一個 directory
    - 再用幾個 commit 移動、合併 code
    - 使用文件，建測試資料庫的文件
- [chihao] To be done **today (11/18 TW time)**
    - [x] add all sites to `Site` table
    - [ ] provide new `url_map.csv` to `NewsScraping`
    - [x] 改 timestamp
    - [x] 開 gcal events

### Bonus!!! ⭐️🌟✨
- item_pattern / page_pattern 怎麼進 db？
    - 感覺上可以 cancel SiteEntry & SiteArticleURLMatch，把所有 site 相關的參數寫成一個大 JSON 塞進 Site.config 之類的欄位

### next meetings
- 11/21 cancel
- 11/25 8pm TW time dev meeting
- 11/28 9am TW time meetup

## 2019/11/14 Th [devs]
- OCF fiscal sponsorship
    - isabel + pofeng 初步討論完成
- wenyi
    - NewsScraping
        - discover article
        - update content
    - scheduling
    - db
    - healthy check?
        - /10mins discover
        - /1min update content
    - python + mysql
        - https://middle2.hackpad.tw/-MySQL-17UVqbgRcZw
- 計算報酬的方式
    - ???
- 公眾討論
    - 媒體
    - 自發組織地面部隊
        - 行動山棧花
    - 媒體識讀
        - 教育部
        - 基金會
    - 假新聞路徑的遊戲
- 群眾參與
    - tagging
    - 要把任務做得夠簡單
        - 政治獻金夠簡單
        - cofacts 有點難
        - 鄉民看電視太難了
- project proposal update
- bil: cofacts 正在開始來進行查圖片的事

## 2019/10/31 Th [devs]

wenyi: Scrapy!

url match
https://docs.google.com/spreadsheets/d/1-RVRRe6pfsPNTudGEY1HlOypLOJ9rWhKPVsOkMv3SNo/edit?usp=sharing

Project proposal
https://docs.google.com/document/d/1g4Tf2q6lMX8-DelxRhhR6pBNGk42Jae76AjMMvbiZQk/edit#
> [name=chihao] ronny++ ddio++ wenyi++

Todos
- chihao
    - [ ] set up middle2
    - [x] add ronny to middle 2 project admin
- wenyi: work with scrapy
- ddio: 旁聽中

## 2019/10/24 Th
### 自我介紹
- Charlie
    - 沃草工程師 ~ (之前負責BackEnd相關)
    - 偶爾會支援社群的錄影直播 (Taipei Ethereum Meetup)
    - 最近想要開始回歸到很久很久很有以前拍照寫些文章QQ
- Johnson
    - FE at Appier
    - Cofacts founder
    - Cofacts 的 URL preview + index 超連結文章的 crawler: https://github.com/cofacts/url-resolver
        - 是一個 GraphQL / GRPC server，戳 endpoint 給網址，可以回傳網頁 HTML 與 [Readibility](https://github.com/mozilla/readability) 解析的「內文」
            - README 還沒更新
        - Cofacts production 在用
        - 包成 docker image 可以直接架
            - ``
        - 每天都會收到 url cralwer 的 exception QQ
        - 用 Puppeteer 所以有點笨重
            - 一個網頁大概 5 秒
        - 偵測到 youtube 會直接用 API 拿 description（我是鄰鄰）
- Ronny
    - 程式設計師 (PHP + JS)
    - newsdiff https://newsdiff.g0v.ronny.tw/
    - 爬蟲經驗主要用 curl + DOMParser
- chihao
    - 全職 Tech Lead at 沃草
    - Nuxt.js (Vue.js), Node.js
    - g0v-intl member
    - 0archive funding contact
- wenyi
    - NYU MS in Data Science (NLP)
    - DS @ NYU Public Safety Lab 寫US prison jails的scrapers (requests, selenium) 最近開始試用scrapy
    - 主要使用 Python (不會JS, 大概看得懂)
    - 美東時區：11月中之後+13小時現在還+12
- ddio
  - 前端工程師
  - 去年開始寫 scrapy ，目前在維護[開放台灣租屋資料](https://rentalhouse.g0v.ddio.io) + 參加 [Rentea](https://beta.hackfoldr.org/rentea)
    - [Scrapy Spider](https://pypi.org/project/scrapy-tw-rental-house/)
- pm5
    - 目前跟這個專案無關
    - 去年做了選舉投票數據資料視覺化
    - Python PERL OCaml
    - 我想要制定一個資料交換的標準
        - (Charlie)喔喔！ 這個很棒 
- Isabel
    - 語言：BASIC、繁體中文、台語
    - 不確定可以貢獻什麼
    - 想學 python
    - proposal
    > [name=mrorz] 程式親子共學蠻酷的
    > [name=isabel] 我只想要子學，不想要親學

### 專案技術架構
https://g0v.hackmd.io/lMQO37z6SbWNWo3R4-X_EA

Johnson:
其實或許可以把 archive 順便建檔到 wayback machine
- 建檔只要用 URL 就好: `http://web.archive.org/save/${URL}`
- 抓 snapshot 有 API: `https://archive.org/help/wayback_api.php`
- 我們抓到 url，拿去戳，讓 wayback machine 也備份一份，直接有可信第三方的 permalink
- 要做資料分析一定要有自建資料庫
- readability (JS) 對 fb 和一些新聞網站不太 work

:::info
cofacts-url-resolver:
```
$ docker run -p 4000:4000 --rm mrorz/cofacts-url-resolver:graphql
```

Sample query:
```
{
  resolvedUrls(urls: 
    ["https://mobileai.net/2019/10/20/line-me/"]
  ) {
    title
    summary
  }
}
```

跑起來的樣子 （`summary`）是 Readability.js 抽取的內容
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_308290de2938b5750e3c939e9d5e010d)

跑一頁要 7 秒的原因：
- 要等「網頁 load 完」
- 「load 完」的定義是[網路連線數 = 0](https://github.com/cofacts/url-resolver/blob/master/src/lib/scrap.js#L128)
- 但現在部落格、新聞的都會有廣告版位 load 很久，網路連線數一直連著
- 所以幾乎都是 [timeout 之後](https://github.com/cofacts/url-resolver/blob/master/src/lib/scrap.js#L129)才會開始分析
:::

ddio:
- ronnny pseudocode 跟 scrapy 類似
- scrapy 可以設定 N 層
- scrapy 注意事項
    - 預設看到同樣網址會跳過
    - 所以刪除的文章 redirect 到同一個網址的話，這份文章會像是從來沒爬過
   > [name=wenyi] 好像可以調整這個參數 [DUPEFILTER_CLASS](https://docs.scrapy.org/en/latest/topics/settings.html#std:setting-DUPEFILTER_CLASS)

Static HTML / JS web app
- cofacts url resolver 會執行 js
    - tradeoff: 一個網址五秒

chihao: 目前有的 Sites https://airtable.com/shrKvjXMO7GaUg1vd

Data research?
chihao: 同樣或類似 post 跨 site 的傳遞

johnson: 有看過一個 GDELT project
https://www.gdeltproject.org/
> GDELT monitors print, broadcast, and web news media in over 100 languages from across every country in the world to keep continually updated on breaking developments anywhere on the planet. Its historical archives stretch back to January 1, 1979 and update every 15 minutes. Through its ability to leverage the world's collective news media, GDELT moves beyond the focus of the Western media towards a far more global perspective on what's happening and how the world is feeling about it.

2.5TB /year

從[《大数据告诉你外媒是否热衷于报道中国负面新闻？》](http://web.archive.org/web/20190905074236/https://mp.weixin.qq.com/s/rNkSTtdvVZxNZathAgGj_w)看來的 (原文已被和諧)

ronny: https://nccur.lib.nccu.edu.tw/bitstream/140.119/119629/1/150201.pdf 有政大研究生用 newsdiff 資料做分析寫論文

wenyi: db 可以拿來 train model

文章裡的 image？
Cofacts 會存在 google drive 學術版免費

### 初步分工

- charlie: 想寫 dashboard
- andrea: crawler
- pm5: data exchange standard、幫忙研究其他人坑裡的小議題
- isabel: 備份又公開的法律問題
-  

### Next meeting: 2019/10/31
- Charlie PASS 一次～ (在日本)

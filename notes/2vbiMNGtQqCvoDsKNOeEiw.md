---
tags: disinfo, 0archive
---
# disinfoRG Meeting Notes (2020/3/23+)
## Quick links
- [Community Report](https://docs.google.com/document/d/1r_oP8ojk0P7MSJWqyQUa71EjrAudZCg4SAn19oOndNk/edit#)
- [Final Report](https://docs.google.com/document/d/1EklepVCwuOH-hBw9-rArS9py606jOB6JTxGv1iE8fj0/edit)

## 2020/7/31 Fr 10am - Final final meeting?
### Lessons
- Lacking behind on text-analysis tech for Taiwanese Mandarin
    - Need human annotated datasets
    - 0archive has the edge to be that (given sufficient human resources)
- Most fact-checked rumors is not present in 0archive
    - 0archive is web pages
    - rumors live in LINE groups, ...
    - need to keep monitoring what we can
    - not much we can do on private chat
        - info lit ed
        - how were these rumors composed?
        - providing tools to spread truthful info
### Make 0archive more useful
- Lowering barrier to use this data
- Talk to more people
- Find partner to do data journalism / research projects

### What to highlight?
- It’s useful
    - IORG
    - Nick Monaco

## 2020/7/13 Mo 8pm - Final meeting
- pm5
    - report on PTT users https://www.overleaf.com/read/kwdzjnhyjzhn
- wenyi
    - report https://www.overleaf.com/4266441429tbmnzmqqthwx
- chihao
    - final report
        - 7/15 23:00 (TW Time) 寄出
        - 請上傳 pdf 到 https://drive.google.com/drive/folders/1bLqfXUV2bLqL_21C2CHAhD60X4pAcJzU
    - ticket
        - 請 wenyi 買好之後直接回信
    - 餘款
        - middle2
        - summit
- summit 投稿討論
    - 7/28 10am (TW Time) 討論

## 2020/7/6 Mo 8pm
- wenyi - ticket 有記得就好
- Final Report - https://docs.google.com/document/d/1EklepVCwuOH-hBw9-rArS9py606jOB6JTxGv1iE8fj0/edit

## 2020/6/29 Mo 8pm

### Checklist
- [x] Confirm compliance with f1 [name=chihao]
    - Fri morning meeting
- [ ] Process contract completion with f2 [name=chihao]
    - Sent email to f2 & OCF
- [ ] Update [architecture](https://docs.google.com/presentation/d/1RPRAGsHJWNR87AW_L2v-GHCc4S5eFUPNFwcmCz0_eSw/edit#slide=id.g8aa6e343ef_4_0) [name=chihao]
- [x] sitesAirtable: `airtable base id` -> .env [name=wenyi]

### g0v summit 2020?
wenyi :clap:

### webinar?
August 10-14 choose one day

## 2020/6/26

### Content farm / wenyi
- credible
- political
- creator/aggregator
- questions
    - source of political statements
    - issues appear more often
    - tendency of narrative OR chaos?
    - aggregator: where content from?
- wenyi
    - 2 largest aggregators: xuehua / mission
    - xuehua - anything, no particular political inclination
    - mission - chinatimes
        - tries to formulate itself as a news website
        - has news/opinion
    - qiqi - huffpo & political
- process of identification?
    - PTS video teaching how to identify content farm
    - info on website / author
- attribution?
    - text comparison need more time
    - via image
- motivation?
- any interference?
- Never force the data
- Why?
    - Feels like we are chasing them
    - Long term: nutrition label for website
- Other data sources?
    - disinfo identified by TFC, not on websites

### PTT / pm5 (chihao)

### Future
- Bring researchers in to use 0archive data
- Restriction: 9/30



## 2020/6/23 Tu 8pm
### 行動
- architecture
    - https://docs.google.com/presentation/d/1RPRAGsHJWNR87AW_L2v-GHCc4S5eFUPNFwcmCz0_eSw/edit#slide=id.g8aa6e343ef_4_0

- 永續經營
    - Linode
    - Google Drive
    - Airtable
    - middle2
    - proxy
    - Google service account

- pm5
    - [PTT 使用者分析](https://gist.github.com/pm5/05b990c02e15a1adf89d4c3a6bfd57db)
        - 基本步驟
            1. 用 < 16 小時同一個 IP 不同使用者的發文記錄，建一個 graph
            2. 算出 connected components
            3. 列出 compenent 內的所有使用者的發文
        - 結果
            - 用在 HatePolitics 可以找到疑似故意爭吵、製造話題的事件
            - Gossiping 能找到的分身比較少，從發文內容也比較難確認這類事件的意圖
        - 下一階段發想
            - 配合 IPInfo 可以篩選出使用 VPN 的使用者（需付費）
            - 如果有 sentiment analysis 可以分析不同版的疑似分身帳號的發文傾向彼此附和或是反對
        - 關於 16 hours
            - 做過 >24h
            - 8h 就會有一些不見
            - LAPDSWAT... 0.5h
            
- wenyi
    - FbScraper
        - update documentation
        - 整理 script，修了一個 script 無法在指定時間結束的bug
    - Content Producer Classification
        - https://www.overleaf.com/read/zrqhdxzykpjg
        - 從三個角度去看 Content Producer:
            - [x] Credibility (by the information revealed in website) 
            - [x] % of political contents (use keywords to tag each article)
            - [ ] % of contents that are from other producers

## 2020/6/16 Tu 8pm

### 進度
- wenyi
    - qiqi 看新聞
        - https://airtable.com/tblsr4JHkr2FXW09X/viwhG7U12IpkqKjQI?blocks=hide
        - https://hackmd.io/_wTH4_drR3GvPfwpr5_jag
        - https://docs.google.com/document/d/17UJab-ZC47lCi3gF1gKlfCOc3Z7JEi6qpNn96GeJst4/edit
- chihao
    - talked about weibo scraping with an IORG engineer
        - will start collect accounts on 0archive airtable
    - Nick’s report
    - handed out comm. report
    - will start final report
- pm5
    - 幫 ben 解了一個安裝的問題，自動 upload to gdrive
    - 維護自動跑 parser
        - currently at 5/27
    - PTT 使用者來源 IP 分析行為模式 -ing
        - https://g0v.hackmd.io/@chihao/0archive/%2F0dgzUnjSSo-iKV7I8j6yIg
        - `結果我們發想發想就做完了！？` [name=chihao]
### 玄彬
- Last email
    1. 嗯⋯ -- Scratch this.
    2. Site types. Currently...
        - https://github.com/disinfoRG/ZeroScraper/blob/master/.env.default#L8
        - https://github.com/disinfoRG/ZeroScraper/blob/master/sitesAirtable/items.py
        - https://github.com/disinfoRG/ZeroScraper/blob/master/sitesAirtable/pipelines.py#L24-L30
        - [x] if not found, use as is
        - add comments (in English) to explain a bit more
        - also FbScraper
    3. what? data standard? -- Scratch this.
- FbScraper documentation
- Eastern Europe & Nigeria
    - demo
- pegabot
    - demo
- communications
    - [ ] upload logo [name=chihao]

### Chris
- [ ] email [name=chihao]

### 討論
- wenyi ✈️ && $$$
    - [x] email with OCF [name=chihao]
- final report
- 永續經營 (maybe next time?)
- IORG?
- 台權會
    - 粉專數量：約莫 10 個左右就足夠了。
    - 為期多久：大約 2-3 個月
    - 每篇發文包含的內容：留言、圖片、影片 url (optional)、按讚與分享數
    - 單篇文章追蹤次數：2 次，間隔時間還要想一下
    - clarify
        - [ ] after 6/30 = community project
        - [ ] no image archive (only url if parser recognizes)
        - [x] fb no parsing

## 2020/6/9 Tu 8pm
### 進度及討論
- pm5
    - Wrote an installation guide
    - Merged a pull request from ben
    - 二月以前要重跑的 publication 跑完了，只跑第一個抓到的版本。現在接著五月抓到的繼續跑
    - 用 social network 的 cluster coefficient 分析了一下政黑版帳號有相同的來源 IP 的情況。計算方式還有一些問題沒有回答清楚，目前只能加減參考。目前的分析有抓出到一個有點名氣的跳板使用者，在大選前我們抓資料的期間還被版友發文點名一直出國玩。文章已刪但我們有抓到。但另外抓出來的帳號，根據一些 IP 資料庫，多半只是用台灣 ISP 的浮動 IP。
- wenyi
    - airtable + 華僑的網站 & new content farms discovered on facebook
    - [facebook tags](https://airtable.com/tbl3DrYs5mXgl0EV9/viwCJtLy5jRVqr84H)
    - https://hackmd.io/_wTH4_drR3GvPfwpr5_jag
- chihao
    - contract
    - need help with last paragraph of the [community report](https://docs.google.com/document/d/1r_oP8ojk0P7MSJWqyQUa71EjrAudZCg4SAn19oOndNk/edit#) re: NLP
    - https://iorg.tw/
    - Google Big Query + Metabase
    - Chris

## 2020/6/2 Tu 8pm
### 進度及討論
- pm5
    - 重跑 2020/2 月底之前抓到的 snapshots
    - 現在先只跑第一個版本的 snapshot
    - 修掉 datapublisher bug 現在東西都會 publish 到 google drive 上了
        - published_at IS NULL 的文章會被存到 `no_date.zip` 裡的 `no_date.jsonl`
- chihao
    - drinking a American pilsner
    - [Community Report](https://docs.google.com/document/d/1r_oP8ojk0P7MSJWqyQUa71EjrAudZCg4SAn19oOndNk/edit#)
- wenyi
    - search similar articles w/ text distance
        - use "敦睦艦隊" as keyword cause the dataset is smaller
        - https://observablehq.com/@andrea-w-wang/arc-diagram
        - https://drive.google.com/drive/u/0/folders/1ezIYejx2iTrPTNa5R-XAWCYGzncH4ely
    - Dec, Jan news websites keywords
        - rate: # of publications tagged with this keyword/# of total pubs
        - [with election](https://drive.google.com/drive/u/0/folders/1ezIYejx2iTrPTNa5R-XAWCYGzncH4ely)
        - [without election](https://drive.google.com/drive/u/0/folders/1ezIYejx2iTrPTNa5R-XAWCYGzncH4ely)
        - some visualization: https://g0v.hackmd.io/0dgzUnjSSo-iKV7I8j6yIg?both#keywords
    - api /health -> 60 minutes
    - 雪花新聞 & 琦琦新聞有提到「起源」、「來自」、「源頭」的文章：https://drive.google.com/drive/u/0/folders/1ezIYejx2iTrPTNa5R-XAWCYGzncH4ely
- 合約
    - [x] 請 pm5 wenyi 簽署後回傳
- 香港 - 備份網站（以防下架）
    - [ ] explore :)
- 台權會 - 關於 Fb censorship
    - 2 months, 1-2 people
    - 如果不考慮開源與長久維護，也許 1 人可以
    - [x] 聯繫 [name=wenyi] ++ \o/
- bot
    - Telegram
    - ...?
- 玄彬
    - [ ] email chain [name=chihao]
- tiktok
    - [ ] ???
    - [ ] https://medium.com/dfrlab/popular-hashtag-hidden-from-tiktok-during-anti-police-protests-in-the-united-states-2065f1bdf031
- disinfoRG / 0archive
    - [x] no action needed
- Feng
    - [ ] [name=pm5] engage!
- 華僑的網站
    - [x] [name=wenyi] activate

### How to use 0archive?
0archive has built up an archive of websites and social media platforms, including content of posts and comments. People can use it can run their own research question against the archive.

Archiving info is the easy part. Asking question is the hard part.

### Outreach in June
- graphic design / branding / refining documentation
- pilot implementations
- translation to Spanish

### Tech review
- Works pretty well (some hickups)
- Storage
    - middle2 (Linode)
- Deployment documentation
    - cronjobs :)
- Export some problems
    - ArticleParser is working, doc is lacking behind
    - export scripts -> compress -> Google Drive daily
        - not documented now
    - backup scripts -> S3 daily

## 2020/5/25 Mo 8pm
### 進度及討論
- pm5
    - fixed articleparser performance problems /w dateparser.
        - 好用但很慢
        - 常見格式自己 parse => 變快 ler
    - fixed articleparser db publication id bug.  only now do we actually parse multiple versions for a single publication.
        - version => part of id
    - did a ptt user behaviour analysis and a ptt user ip analysis (copied i'analyseur)
    - wrote a scenario in the get started document.
    - joined g0v hackathon.
- chihao
    - pitched & presented results at g0v hackathon
    - worked with a designer during g0v hackathon for a mockup of 0archive’s landing page.
- wenyi
    - fixed tokenizer "broken pipe" issue for large jsonl
    - add some analysis in here https://g0v.hackmd.io/@chihao/0archive/%2F0dgzUnjSSo-iKV7I8j6yIg
        - 聯合報抄中央社（用武漢肺炎）過幾天之後改標，但內容不會變
        - sentiment analysis 目前覺得效果不好
            - 好像需要找 training data
    - provided a tutorial for doing topic clustering & another for plotting 肺炎使用名稱
- 6 個 Site publication 更完整？
    - 有！
- 還是有看到分身帳號
- 發現了 1 個 id 有多篇文章被中時記者引用？
    - 拿 ptt id 到 google news 搜⋯
- 發文行為規律
    - 再進一步看發文內容，也許會有一點結論
- 追蹤文章誰抄誰
    - url
    - 內容比對

## 2020/5/18 Mo 8pm
### 進度及討論
- pm5
    - Explored [favorite sources](https://g0v.hackmd.io/@chihao/0archive/https%3A%2F%2Fg0v.hackmd.io%2F0dgzUnjSSo-iKV7I8j6yIg)
    - Fixed a db migration running
- wenyi
    - redirect_to db migration
    - 整理斷詞的code -> cli，大概80%的jsonl都有斷詞檔了
    - 生成一個月一個json & 整理目前資料格式 https://g0v.hackmd.io/MuBbS3NkSXa7pNTFdX4MKw#%E5%85%AC%E9%96%8B%E8%B3%87%E6%96%99%E9%9B%86
    - 比較了一下琦琦看新聞&自由時報的標題長度
- chihao
    - 小松
    - 政黑版
        - 週六看了[政黑版的公開資料集](https://g0v.hackmd.io/8MUR3mk4SiWEvSjJX-p7gA)
        - 剛剛看了一下，在那之後 2019/11,12,2020/1,2,3 月有更新
    - 八卦版
        - 目前有 1,4,5 月
- 引用來源資料分析
    - 同樣 domain 的好像應該要去除？
        - 我覺得留著好像也蠻有趣的 XD 可以看到喜歡自己連自己的網站
        > [name=wenyi] 但相同domain很多時候是來自於文章的tag連結，以我們目前extract urls的方法無法區分是來自於tag或是cite自己的網站
    - 要看看每個網站的 publication 數目
    - [dependency diagram](https://observablehq.com/@d3/chord-dependency-diagram)
- articles per site?
    - 八卦 90k publication 53w (publications 6/2 81w)
    - coco 77w
    - 雪花 61w (publications 6/2 xuehua.us 20w, xuehua.tw 18.8w)
    - ... <10w
    - 政黑 ~10w
- 大松之前
    - Parser
        - Ptt 政黑
            - Article = 11w
            - Publication = 13w (6/2 15w)
        - 中時電子報
            - 10/24 前 published 的還沒有 (6/2 都有了)
            - Article = 96392
            - Publication = 43157 (6/2 9.1w)
        - Dcard 時事
            - Article = 9711
            - Publication = 4203 (6/2 4395)
        - 人民网
            - Article = 19069
            - Publication = 15723 (6/2 1.6w)
        - 观察者
            - Article = 50947
            - Publication = 5745 (6/2 3.6w)
        - 中評網
            - Article = 18w
            - Publication = 12w (6/2 17w)
        - 6 Sites
            - A = 466119
            - P = 318828 = 68%
            - (6/2) P = 467395 = 100.2%(??)
    - 資料分析
        - 基礎的統計
        - 已知武漢肺炎相關謠言在 0archive 資料集出現的狀況
            - 「美國流感死亡人數」
            - 「美國是武漢肺炎病毒來源」
        - 已知選舉相關謠言
            - 「中選會做票」
    - 宣傳
        - [文案、配圖](https://g0v.hackmd.io/@chihao/0archive/%2FPgCc8ehjSp6pamNVDvnv6g)
        - 自己來發社團
        - #sns 發 g0v 粉專
- 五月最後一週
    - 資料分析
        - 「武漢肺炎」、「新冠肺炎」、「covid-19」
            - Quantify 各個政治人物使用三者的比例

### 行動
- 試用 snownlp [name=wenyi]

## 2020/5/16 Sa 10:30am

## 2020/5/13 We 8pm

## 2020/5/11 Mo 8pm
### 進度及討論
- wenyi
    - parser for appledaily and toutiao
        - toutiao
    - [斷詞](https://github.com/disinfoRG/TextPreprocessor)
        - remove punctuations & numbers
        - tokenization:
        `jieba`: 
            - speed: very fast: 3 minutes for 3500 ptt titles & texts
            - can use self determined dictionary. Now include [`民國104年常用語詞調查語料統計分析詞頻表-附錄19_多音節詞頻統計`](https://github.com/irvin/moe-common-phrases-of-zhtw/blob/master/2011-2015/csv/%E6%B0%91%E5%9C%8B104%E5%B9%B4%E5%B8%B8%E7%94%A8%E8%AA%9E%E8%A9%9E%E8%AA%BF%E6%9F%A5%E8%AA%9E%E6%96%99%E7%B5%B1%E8%A8%88%E5%88%86%E6%9E%90%E8%A9%9E%E9%A0%BB%E8%A1%A8-%E9%99%84%E9%8C%8419_%E5%A4%9A%E9%9F%B3%E7%AF%80%E8%A9%9E%E9%A0%BB%E7%B5%B1%E8%A8%88.csv)
        - pos tagging
        `ckipnlp`: tagged very well however is slow. 
            - 10 sec for 1 ptt titles+texts
            - gpu
- pm5
    - changed fulltext dataset files to one file per month for each producer.
    - uploaded datasets for April.
    - did parser db stats: publication_stats and parser_db are automatically updated everyday.
    - traced server memory usage problem but couldn't find the cause; rebooted
    - started running parser on March snapshots; some problems remain.
- chihao
    - started reading the guide & half-way through
- 公開資料集 - 目前 solution
    - [ ] 松前 - 三 OR 五
    - [ ] 重跑？
    - [ ] 自動上傳 google drive https://drive.google.com/drive/folders/1ckDs03tdXhLdeF0N2St5OP0EeqxFC1bm
    - [ ] 寫 py script (OAuth?) 下載所有公開資料集檔案
        - 有些現成的
            - https://github.com/gdrive-org/gdrive
            - https://github.com/nurdtechie98/drive-cli
            - https://github.com/prahladyeri/tuxdrive
            - https://github.com/ndrplz/google-drive-downloader
        - 是大家都過不了 Google 審核還是都不想送表單？🤔
    - [ ] 斷詞資料集
        - [ ] ptt + 斷 comments
    - [ ] gen 一個武漢肺炎資料集
    - [ ] 自動（手動？）上傳武漢肺炎資料集？

```
[x] /公開資料集/{producer-name}-{producer-id}/{year}-{month}.zip
[ ] /斷詞資料集/...
[ ] /公開資料集/{producer-name}-{producer-id}-tokenized/...
[x] /公開資料集/{producer-name}-{producer-id}/{year}-{month}-tokenized.zip
```

- URL hash
    - 可以用 `UNHEX(MD5(<url>))` 存成 `BINARY(32)` index 速度會快一點
    - FIXME `url_hash` should be passed in as a string (`str(zlib.crc32(some_url))`) otherwise MySQL wouldn't use the index
    - ```SELECT article_id FROM `Article` WHERE url = "https://www.ptt.cc/bbs/Gossiping/M.1587456014.A.2F7.html" AND url_hash = 3356748719``` takes ~12 seconds
    - ```SELECT article_id FROM `Article` WHERE url = "https://www.ptt.cc/bbs/Gossiping/M.1587456014.A.2F7.html" AND url_hash = "3356748719"``` takes <1 second
- 5/13 OR 15 松前
    - 自我介紹
    - 0archive 目前有的東西
    - 大家的意見
    - 一起做點什麼
- 5/16 小松
- project extension

### 行動
- tainan db url_hash [name=wenyi]: 
    - + redirect_to hash + 建 redirect_to hash index & 跑 migration 
    - 檢查有用到url_hash的queries 要把url_hash -> str
- stats table on web [name=wenyi]
## 2020/5/4 Mo 8pm
`May the 4th be with you`
### 進度及討論
- chihao
    - Next payment on the way
    - [0archive base presentation](https://docs.google.com/presentation/d/1kqTS7QHhlBGL6LdRZR24IRA5jxevy0pxUK1kQdtYEOs/edit)
- wenyi
    - api
        - update [documentation](https://github.com/disinfoRG/ZeroScraper/blob/master/API.md)
        - add tests
        - GET `/publication?q=`
    - health
        - `/health` -> discover & update 分開
        - [sql](https://github.com/disinfoRG/ZeroScraper/blob/master/queries/count_recent_articles_by_process.sql)
        - health metric
            - 目前 - 30 分鐘沒有新 ArticleSnapshot
        - 「收到 not okay 但其實有在跑」-> 站方 error
    - ptt
        - [ptt.py](https://github.com/disinfoRG/ZeroScraper/blob/master/newsSpiders/ptt.py)
        - 加入 [`newsspider.runner.discover`](https://github.com/disinfoRG/ZeroScraper/blob/master/newsSpiders/runner/discover.py#L63-L64)
        - 用 `zs-site.py discover xxx` call，但是Ctrl+C無法結束process
            - 被 Ctrl+C 被 CrawlerProcess擋下來，要到`process.start`才開始
            - ptt.DiscoverSite.run 設定成twisted process，不要真正跑
            - blocking `requests` -> non-blocking `axios`
            - discover runner 建立 reactor
        - 沒有加入 [`zs.py discover`](https://github.com/disinfoRG/ZeroScraper/blob/master/zs.py#L40-L43)，會卡住其他的spiders
            - 混用滿麻煩的
            - requests自己另外一個process
            - 在Site裡面加一個 `spider_name`
    - 資料分析發想 doc
- pm5
    - publish datasets
        - full text datasets 每天自動上傳到 google drive
        - public datasets 其實也可以比照辦理，弄 github 比較麻煩
    - job queue for parser: 進行到一半
    - publication 不太對耶⋯⋯要再調查一下
- public data set
    - https://docs.google.com/uc?id=1QP4ihK1pjB5e97cUEOI5QVhVGYhIt4uh
    - [pyDrive](https://pypi.org/project/PyDrive/) (python package communicating w/ GoogleDrive)

### 行動
- [ ] 改網站 [name=chihao]
- [x] google drive publish 改成每個月一個檔案 [name=pm5]
- [x] 查 parser 的問題：為什麼跑完的資料這麼少？ [name=pm5]
- [x] 蘋果 & 頭條的parser [name=wenyi]
- [ ] 設計 monitor dashboard [name=wenyi]
- [ ] 整理 public data set use case / 需求 [name=chihao]
- [ ] Read the guide [name=chihao]
- [x] 嘗試斷詞 w/ ptt [name=wenyi]
- [ ] 整理 documentation? [name=chihao]

## 2020/4/27 Mo 8pm [devs]
### 進度及討論
- chihao
    - YtScraper 沒有進度
    - 使用 0archive public datasets
        - https://docs.google.com/spreadsheets/d/1GnVa0OevwmxhgLn-2JdImUdyQdsZo1ERDILOcLWmH7s/edit#gid=1664807922
- wenyi
    - api
        - add header `Authorization: Bearer xxx`，api 會檢查cookies or header for access tokens
        - enabled CORS
        - add rate limit (10/sec)
        - add 2 endpoints
            - `GET /playground/random`
            - `POST /playground/add_record`
    - 更改 appledaily mechanism [#111](https://github.com/disinfoRG/ZeroScraper/issues/111)
    - Playground
        - 開了新 [repo](https://github.com/disinfoRG/Playground)，目前只有從 publication db 拿資料然後 dump 到 taichung 的 queries
        - 畫 UI
    - PTT
- pm5
    - fixed ZeroScraper backup duplicated data
    - fixed parser db schema and performance issues
    - start dumping published datasets to elasticsearch automatically everyday
- 
- 5/16 小松

### 四月底（這週）要完成什麼？
- pm5
    - [x] 自動丟 datasets 上 google drive...
    - [ ] 開始用 job queue 管理 parser tasks
    - [ ] 三月份的 snapshots 都沒有 parse，要丟進去跑
- wenyi
    - 把 api 建構完成 (publication & tests)
    - 設計一下 monitor dashboard

### 五月預計要完成什麼？
> 3 hackathons
- [x] 1/4 
- [x] 2/23
- 5/16 小松之前要做的事
    - 邀請樁腳
        - [ ] a-chioh
        - [ ] gugod
        - [ ] tkirby
            > [name=chihao] #disinfo 問了 \o/
        - [x] Li Cheng En
        - [x] chihao 同事
        - [ ] Linda or Linda 的朋友 [name=wenyi]
    - 設定小松主題
        - 了解內容農場：內容農場的內容分析
        - 武漢肺炎
            - 設定時間區間：2019/12/29-2020/5/16
            - 每週前十大報導主題
            - 口罩政策報導演變
            - 「武漢肺炎病毒發源自美國」？
                > [name=pm5] 找「武漢肺炎發源」的資料，看「美國」什麼時候開始多起來
    - 改網站 0archive.tw [name=chihao]
        - dataset 連結
    - 更新 `datasets` [name=pm5]
    - elasticsearch???
        - 搜尋是全文，好像不行
    - kibana?
    - `datasets` `publication.title` & `publication.text` 做好斷詞
    - `datasets/publications/<producer_id>-<producer_name>/YYYY-MM-DD.jsonl` 資料本人
    - `datasets/publications-tokenized/<producer_id>-<producer_name>/YYYY-MM-DD.jsonl` 資料本人
    - YYYY-MM-DD-tokenized.jsonl
- 5/16 小松當天要做的事
    - ...
- [ ] 0archive basic presentation [name=chihao]
- 1 report on event summary [name=chihao]
- 1 report on chinese disinfo during election (or COVID-19 - to be confirmed) (data analysis) [name=chihao]
- 2 presentations
    - 5/23 大松報告
    - 6/x 0archive 自己 host 線上 event？
- 分身伐樹
    - 5/23 大松一定要發表
    - [ ] 做一個簡單web介面 [name=wenyi]
- extension
    - -> 7/31?
    - [ ] 算錢 [name=chihao]
- [x] wenyi: 整理一份討論過的所有 data analysis 主題
- [ ] pm5: data standard

## 2020/4/21 Tu 8pm [devs]
- https://github.com/disinfoRG/datasets
- elasticsearch
- [0archive 公開資料集](https://drive.google.com/drive/folders/1ezIYejx2iTrPTNa5R-XAWCYGzncH4ely)
- 理解內容農場經營
- 關於斷詞的作法
    - ckip？會搞一陣子
    - 先塞進 elasticsearch 看一下
- 武肺為主題的內容分析
    - data export
        - 0archive team
    - 斷詞
        - ckip
        - jieba
        - elasticsearch 內建
        - elasticsearch plug-in
        - [教育部常用字詞](https://github.com/irvin/moe-common-phrases-of-zhtw/tree/master/2011-2015/csv)
    - 詞性 tagging
        - https://www.moedict.tw/raw/%E8%90%8C
        - ...?
    - 找主題
        - 自己看名詞
            - 找職業或特定主題（e.g. 藥局、藥師、口罩、WHO...）
            - 幫助找主題
        - 自動看 - topic modeling
            - ...
    - 情感分析
        - 自己看標題中的形容詞
        - 先把標題放到人家做好的 model 跑跑看（可以先做看看model合不合用）
        - chinese sentiment analysis 
            - https://github.com/Tony607/Chinese_sentiment_analysis
            - others...

## 2020/4/20 Mo 8pm [devs]
### 進度及討論
- wenyi - ptt makeup script

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0af8c22f36b74c4385c69d2010674394.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b9737f94b2bf9e0de40a3cb1a2566bc5.png)

- wenyi
    - ptt makeup script
        - run at 0:23
        - X:20-X:50 文章會 lost
        - discover starts at X:20
        - [ ] 星期二 deactivate ptt 八卦版，一小時跑一次makeup script，看看跑的情形如何。主要觀察是每一個cronjob有沒有在一小時內結束（不會同時跑很多隻），還有有沒有全部抓到（隔天的makeup script)。
    - [今日頭條](https://www.toutiao.com/) spider
        - 用 https://www.toutiao.com/api/pc/realtime_news/
    - pttread parser
        - 19 篇 404 XD
    - stats
        - [zeroscraper](https://github.com/disinfoRG/ZeroScraper/blob/master/queries/count_site_stats.sql)
        - [fbscraper](https://github.com/disinfoRG/FbScraper/blob/master/queries/count_site_stats.sql)
    - stats visualization
        - [axios](https://www.npmjs.com/package/axios)
    - 不過通常 API 會用 Authorization header
        - [x] `POST /login?user=XXX&pass=XXX`
        - [x] `Authorization: Bear <token>` header
        - [x] login response 回傳 jwt token
        - [x] api 檢查 cookies 或檢查 header
- chihao
    - Watchou RG uses 0archive public data
    - writing another report... (due tonight!)
    - YtScraper
        - 406377 Articles with (some) metadata (no statistics)
            - 中天 = 99732 (all)
            - 東森 = 83278 (~33.6%)
            - 三立 = 79867 (~87.2%)
        - 還沒加 comments
    - 中華電信 not yet
    - 王銘宏 Tony
- pm5
    - 追思會
    - publication and producer id in UUID
    - datasets file structure
        - `<32-char producer ID> - <producer name>/YYYY-MM-DD.jsonl`
        - `50309CA081FE11EA8627F23C92E71BAD - 中国台湾网/2020-03-20.jsonl`
        - producer name 再研究一下
        - full text datasets 會 gzipped 起來
    - PTT author parsing 暱稱
- review backup & storage management
    - https://g0v.hackmd.io/@chihao/0archive/%2FI8_OwNM5SI2YYfRrdjvUfg
- g0v summit
    - https://g0v.hackmd.io/LEARby4wRJi_H6VN6jWkHg

## 2020/4/13 Mo [devs]
### 進度及討論
- wenyi
    - recover lost ptt [issue #105](https://github.com/disinfoRG/ZeroScraper/issues/105)
        - use pttread, e.g. https://pttread.com/gossiping/m-1582100863-a-FFF
        - 4000+ articles (wenyi ++ ++)
        - 有更新 last_snapshot_at 但沒有更新 snapshot_count
        - 不同的 parser - YES
    - improve api
        - [doc](https://github.com/disinfoRG/ZeroScraper#api)
        - /health -> [content tracker](https://contenttrack.ronny.tw/?id=45#track-log)
            - if `max(snapshot_at)>15 minutes` -> not okay
    - ptt makeup script
        - https://github.com/disinfoRG/ZeroScraper/blob/makeup-ptt/makeup-ptt.py
        - 一天跑一次，但加上一個『超過兩百頁之後如果接下來 10 頁都沒有新文章就結束，如果有就繼續』以防有一天突然文章爆量。
        - 紀錄每一天makeup的時候抓的url，有助於debug原本的spider的問題
        - 上次跑了整個 4 月 (10天) - 14247 - 1900
        - 針對八卦版
        - 凌晨跑
        - few suggestions
            - 只抓url讓他每個小時跑，snapshot讓update spider去補
        - 線索：parse 出來 ptt 的文章的 published_at 的分佈
        - 另一種解法 `save_url` rule - spider 碰到這種 url 就 create Article save url (roll credit) 就好不存 snapshot
    - a new ptt scraper? [pending]
        - 針對 ptt.cc
        - should still run hourly
    - fb
        - stats table
            - update 部分尚需更新
            - how to set up TZ on linode?
                - linode .bashrc or shell script 跑程式 + 環境變數 TZ
        - set up cronjob on linode for fb 
            - db connection tunnel 會斷掉
                - 1. 問 ronny: mysql 鎖 linode ip
                - 2. db 搬到 linode
        - 現況
            - discover 1 hr + update 1 hr
                - discover 1 hr 跑的完
                - update 1 hr 內會被擋
            - 沒有接到 parser
        - NEED
            - 穩定的 db connection
            - 多個 Fb 帳號
            - 改 FbScraper
                - 切換帳號
                - chrome process 管理
                - 平行處理
- chihao
    - youtube
        - 99 Sites
        - 133424 Articles
        - 4567 ArticleSnapshot
    - YouTube “CommentThread”
        - comment / reply
    - ref from secret source: https://docs.google.com/spreadsheets/d/1GnVa0OevwmxhgLn-2JdImUdyQdsZo1ERDILOcLWmH7s/edit#gid=0
    - Fb - 我還沒去中華電信 QQ
    - $$$
    - extension to be finalized
- pm5
    - fixed many published_at parsing
        - published_at 超重要 der [name=pm5] paraphrased by chihao
        - 問題：會有完全束手無策找不到 published_at 的狀況嗎？
    - need to re-parse old publications; in progress
    - 1 day’s backup left for 2020-03
    - some work in progress: design parallel implementation for parsers, test elasticsearch
    - 討論：parser 速度趕不上了，需要做平行處理 [name=pm5]
    - parser 120k/day 追不上了 QQ
- 四、五月
    - 滿足合約的要求
        - 3 小松
        - 2 大松提案 + 成果發表
        - 大選相關不實訊息資料分析
    - 收尾
        - 「好維持」的 api
        - system dashboard visualization (using that api)
        - 定期自動更新部分內文資料集
        - 維持 linode
        - 維持 middle2
        - 定期自動更新完整內文資料集
    - 其他 Data analysis
        - 肺炎
    - Fb

> **MS3A** - ... will host three hackathons and give two presentations over their findings. An interim update of the workshops will be submitted. To submit detailed reports of the topics covered, how many people attended, any successes and/or challenges encountered during the planning and implementation of the hackathons/presentations. Depending on the sensitivity of workshop content and the security circumstances in- country, the partner may include photographs and an attendance sheet if appropriate.
> 
> ... will host three hackathons focused on analyzing and interpreting the data sets.
> 
> ... will publish and interim report about the hackathons and other media content produced by the workshop groups using the data sets from stage one.
> 
> Output: Hackathon participants will have raised awaremness about misinformation campaigns in Taiwan.
> 
> **MS3B** - A final report covering the usage of the data sets by the community groups and any other content published.
> 
> ... will produce a final report covering the usage of the data sets by the community groups and any other content published.
> 
> ... will become informed on the use of Chinese propaganda tactics and statistics surrounding and immediately following the Taiwanese 2020 elections. This report will contribute towards the goal of analyzing data related to misinformation targeted at Taiwan’s democratic institutions and public opinion and raising public awareness about misinformation campaigns.

### 行動
- yt yt yt [name=chihao]
    - [x] add more channels
    - [ ] add Comment/CommentSnapshot
        - comment_id (AUTO_INC)
        - article_id
        - parent_comment_id
        - ...
    - [x] url => youtube ID
- ptt make up script [name=wenyi]
    - [x] 增加邏輯
    - [x] 產出更多 log、幫助調查 
    - [x] deploy
- stats
    - [x] 不要用snapshot_at_date (MySQL實作細節) [name=wenyi]
    - [ ] visualization
- fb 
    - [x] 問 ronny: mysql 鎖 linode ip（tunnel 會斷）[name=wenyi]
    - [x] stats [name=wenyi]
    - [ ] 去中華電信 [name=chihao]
- [ ] parser 趕快 [name=pm5]
- [ ] elasticsearch 弄起來 [name=pm5]
- data research
    - tutorial [name=chihao?]
    - 想想人選？
    - 先自己來一次資料小松

## 2020/4/6 Mo [devs]
### 進度
- chihao
    - report will be done tonight
        - https://docs.google.com/document/d/1PjRMaDYA-thg1ePGkqHsvYUmD-AHC2mRyFEEZKIpI8Y/edit
    - all contracts signed
    - funding extension
    - Nick says thanks!
        - 應該是公開資料的 meta data
    - YouTube
- pm5
    - db 備份
        - Done: pre-2020-02, 2020-04-* daily
            - 自動 m2 cronjob
        - In progress: 2020-03-* daily
        - Snapshots in JSONLines bzipped
        - Articles, Sites /w mysqldump bzipped
        - Db schema /w mysqldump bzipped
        - 有一個 spreadsheet 記錄下載備份檔的地方
        - `ns-dump` dumps snapshots; `ns-load` loads snapshots
    - db partitioning: done。以後可以用 exchange 把舊的 snapshot 移除
    - 繼續調查二月的 data loss 事件的復原情形 [#94](https://github.com/disinfoRG/ZeroScraper/issues/94): 應該可以結案了
- wenyi
    - API authentication
        - ns.py login
        - 更新 README
    - ptt
        - 補舊的資料
        - 可是 4/4 整天沒抓
        - 可能需要一個「補充資料」的 script
    - snapshot 調整
        - ptt 2/2 以前 next_snapshot_at -> 0
        - 所有文章調整成前三天一天一次，然後第七天再一次
        - first_snapshot_at 兩個月以前-> next_snapshot_at=0
    - fb
        - discover - ok
        - update - security check
        - 現在沒有平行處理

### 討論
- API 要放在 ns.py 裡面嗎？
    - https://github.com/disinfoRG/ZeroScraper/blob/master/ns.py#L127-L146
    - [API doc](https://github.com/disinfoRG/ZeroScraper/blob/master/README.md)
    - use case: 
        - 自己電腦開發的時候用 ns.py 直接看到stats如何，可以直接 print 出來即可
        - stats 的結果可以把它pipe到其他地方，或是存出表格之類的 ( `python ns.py stats -o output.json` )
    - 很常用的指令或需要很多的requests才需要去戳api
        - 不用 ssh 進 db
        - 其他 repo 透過 API 而不是直接讀 tainan db
    - 列一下經常需要查的東西，放到 cli 中
        - site stats
        - variables (discover & update PID) （之後會加上 process 跑的時間 [name=pm5]）
        - MAYBE: active sites
- Publication api / api 效率
    - elasticsearch on m2?
        - middle2 有支援但有 bug，ronny 要改，但 5 月底前應該不會動
    - 啟動時間
- 4/3 & 4/5 的 update & discover 都劇烈減少
    - pm5:「昨天（4/4）又遇到 discover 與 update processes 不明原因掛掉因此 PID table 沒有清掉所以一整天沒有跑 discover & update 的問題」
    - pm5 - pid table + start time
    - threadhold 2 hr / 3 hr
    - ronny - 最近可能沒空
    - ronny - 我覺得怪怪的
    - GET /health
        - return okay 的條件？
            - 看 variable table (加了時間之後)
            - or 看 ArticleSnapshot table 的 snapshot_at 最近十分鐘有沒有新snapshot (這應該比較快)
        - return notOkay
- fb
    - 邊跑邊改
    - 新帳號
- YouTube
    - 資料架構
        - Site(channel)
        - List(playlist)
        - Article(video)
        - ???(comment)
        - comment 先不要獨立出來好了
    - multi account
- data loss 要不要結案？
    - [x] 好
    - [x] 開 issue 研究 ptt 補回來
    - [x] 壹讀、每日頭條 -> active
- funding extension
    - 六月？七月？
- 四月、五月重點
    - 下一次大松是 5/16
    - community outreach / researcher collab / data analysis
        - 準備工作
            - elasticsearch + api
            - pre-defined datasets ("肺炎")
            - jupyter
        - 我們自己開 data analysis 的坑
            - explorer web-based UI
        - 找人開他們的坑（0archive team 支援）
            - a-chioh and text mining?
            - text distance /w elasticsearch and ronny?
            - nick?
        - [research reference](https://docs.google.com/document/d/1-CUdqLVbfMd7MfUgPkAzfpOcI2WiBA871iX-4xcUdjk/edit?usp=sharing)
    - fb?
- publications -匯入-> es
    - ArticleParser 5000/hr
    - script 定期 select from publication & POST POST POST

### 行動
- admin
    - [ ] 完成 report (2) [name=chihao]
- infra
    - [x] GET /health (no auth) [name=wenyi]
        - [x] 串 ronny 的 [tracker](https://github.com/ronnywang/contenttrack)
    - [x] data loss follow-up: 開 issue 研究 ptt 補回來 [name=wenyi]
    - [x] ns.py api improvements [name=wenyi]
        - [x] -o option
        - [x] add site stats & variables look up
- 看資料 get fu
    - [ ] wenyi
    - [ ] pm5 [name=pm5]
    - [ ] chihao [name=chihao]
- community / data analysis
    - [ ] publications -匯入-> es -串-> api
        - [ ] script 定期 select from publication & POST POST POST [name=pm5]
        - [ ] 修改 GET /publications 改串 elasticsearch [name=wenyi]
- fb
    - [ ] 買預付卡先 [name=chihao]
    - [ ] set up phones [name=chihao]
    - [ ] text msg fowarding [name=chihao]
    - [ ] accounts [name=chihao]
    - [ ] changhua stats table [name=wenyi]
    - [ ] fbscraper linode cronjob discover => changhua [name=wenyi]
- ptt 如何跟上發文速度 [name=wenyi]

## 2020/3/30 Mo [devs]
### 進度
- chihao
    - youtube scraping prototype
        - https://github.com/chihaoyo/YtScraper
    - $$
- wenyi
    - site.py add arguments `url`, `article`, `following`
        - making up PTT Gossiping
    - [login spider](https://github.com/disinfoRG/ZeroScraper/blob/master/newsSpiders/spiders/login_discover_spider.py) for appledaily
    - api deploy
        - [authentication](https://github.com/disinfoRG/ZeroScraper/pull/101/files)
    - remove duplicates for `udn` and `appledaily`
        - Article && ArticleSnapshot
- pm5
    - copied backup snapshot data to production db
    - designed snapshot table archive scheme; test partition
        - monthly, partition according to snapshot_at
    - wrote multiple upstream feature for parser
        - from multiple scraperDB && multiple tablew
    - parsed qiqi (sites 6, 8) snapshot in backup with new parser
    - 順便發現了更多琦琦（？？？）
    - uploaded 2019-11 to 2020-03 datasets for sites 6, 8, 98 99 to google drive
        - jsonl daily
        - zip monthly
### 討論
- google drive upload
    - 還沒做自動上傳
    - parser 速度跟不上 scraper
    - 最多的八卦版大概 150MB/month
    - 每份 zip 放個 LICENSE
- restore
    - 2/21 之前回復完成
    - 2/21-28 復原很困難
- ArticleSnapshot rotation / partition https://g0v.hackmd.io/@chihao/0archive/%2FlMQO37z6SbWNWo3R4-X_EA
    - parse 完的 articlesnapshot 離線備份
    - parser 怎麼知道已經 parse 了？parser 要做，還沒想到
    - ArticleSnapshot.snapshot_at_date 裡面可以存台灣時區的日期，這樣備份檔的 YYYYMM 就會是台灣時間（吧？）
    - 三月底 pm5 會
        1. 關掉所有 scraper & parser
        2. rename ArticleSnapshot -> ArticleSnapshot202003
        3. 重開一個 ArticleSnapshot table with partition
        4. 開始跑 scraper & parser
        5. ArticleSnapshot202003 再慢慢去跑 parsing 與 archive
- 一些 parse 出來可以幫助追蹤與分析的資料
    - ga-id
    - facebook publisher
        - 在這裡：taoyuan db -> producer.identifiers
    - facebook app id
        - 暫時在 publication.metadata
        - 還沒存到 producer.identifiers
- 發現新 qiqi
    - qiqi facebook 帳號⋯
- snapshot archiving
    - 要問 ronny 之後 table 的檔案要怎麼備份
- Article 的 ArticleSnapshot(s) -> publication
    - 每個 snapshot 都會 parse
    - 內容 / 標題 / metadata 不一樣就會 create new publication
    - 四個 timestamp
        - published_at
        - first_seen_at
        - last_updated_at
        - version
- [api auth](https://github.com/disinfoRG/ZeroScraper/pull/101/files)
    - wenyi
        - login page -> JWT as cookie
        - 30mins
    - 申請帳密
        - 先不用
        - 之後要實作：帳號可以直接存 tainan db，密碼要hash 過(+ salt) 再存 (look up mysql 的 hash method)
    - pm5 建議流程
        - `> ns.py login`
            - `ns.py` POST request to login endpoint
        - 輸入帳號密碼，獲得 secret
        - 把 secret 存起來在 credentials.json (secrets.json?)，檔案名稱要寫在文件裡面，告訴使用者這個檔案不要給別人看
        - 不會過期（暫時這樣）
- middle2 / gcp? / linode / gsuite 帳號等等
    - 0archive.tw g-suite
    - Linode
    - AWS Glacier / Azure Storage / GCP Nearline
    - 結論：還是 google drive 好了 
- PTT 資料還沒 parse 完
    - wenyi 再確認一次
    - pm5 繼續關心 parser 跑的情況
- PTT scraper 好散漫⋯
    - Ptt discover?
    - 比對哪些 url 有抓到 Article?
        - 不要一個一個 query
        - 整個倒進進 db 用 JOIN 算 diff
        - diff 直接 insert Article
- production db 備份
    - 權限
    - 開備份的空間
    - 備份頻率：一天一次
- yt
    - Site - YouTube channel
    - SiteSnapshot
        - site_id
        - snapshot_at
        - raw_data
        - title
        - description
        - custom_url
        - published_at
        - thumbnail_url
        - view_count
        - comment_count
        - subscriber_count
        - video_count
        - uploads_playlist_id
    - Article - YouTube video
    - ArticleSnapshot
- fb

### 本週工作
- [ ] parser stats? producer stats? [name=pm5] 有空的話
- [ ] publication timestamp 解說 [name=pm5]
- [x] 確定 partition 是否能用 TW time [name=pm5]
- [ ] 檢查 publication publish_at 是否是台灣時區（在輸出時）[name=pm5]
- [x] snapshot table rotation [name=pm5]
- [ ] parse site 120 （閃文聯盟） dataset [name=pm5]
- [ ] 報告 [name=chihao]
- [ ] 將 login info 加入 Airtable config - [name=wenyi]
- [x] finish api auth - [name=wenyi]
    - [x] 更新readme 
- [x] 確認政黑版 & 八卦版的文章都抓下來了沒有 - [name=wenyi]
    - [x] 先把八卦版的 url 全部抓下來 (政黑版已經抓好了)，用python set算網頁的url 和db url 的差集
    - [x] 把缺漏的抓完 (2019-2020) 
- [ ] 0archive google account - [name=chihao]
- [ ] linode snapshot - [name=chihao]
- [x] fb 在 linode 跑起來 - [name=wenyi]

### 下次會議
- 4/1 0:00 TW time beer pa?
- 4/6 8pm TW time OK.

## 2020/3/23 Mo [devs]
### 近況分享
- chihao
    - 台南 \o/
- bruce
    - 買了拼圖

### 進度報告
- chihao
    - (very slowly progressing) more keywords matching [Data Playground](https://docs.google.com/spreadsheets/d/1aHlR0Xku0r4l2mQBDT7B7yU-dQpqEW8NMj_65LoUsMM/edit#gid=0)
- pm5
    - 改好 parser 可以 parse 出 PTT 的作者、來源 IP 等等
    - 改動 parser db 欄位，加了幾個 index
        - 現有 1M+ rows
    - 把 PTT 文章重新 parse 一遍
    - 倒出資料集 (ing)
        - ~2h
- wenyi
    - [新聞網站](https://g0v.hackmd.io/ktWzAepfTB-uJ3zGDt-l9A)
        - 大新聞網站應該都沒有缺漏的問題
        - 但有重複抓到不同url但同一個文章的問題
            - 正在緩慢清理 udn news 重複的文章
            - chinatimes 已經清理完
        - 蘋果即時新聞需要登入
            - 只有 metadata
    - SiteStats 已經開始每天跑了，正在緩慢的寫web based viz...（第一次寫QQ）
    - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bd74a802bf96230915b4b9c01482f935)
    - [StandardizePipeline](https://github.com/disinfoRG/ZeroScraper/blob/master/newsSpiders/pipelines.py#L11-L28)
- bruce
    - 測試 gcp 可以 discover 和 update 文章到 m2 的資料庫，沒有看到 zombie process
        - 彰化寫入中
    - dockerfile 編輯
    - gcp 試用 $$ 還有大概 9000

### 討論
- data loss
    - 2020-02-21~26 data loss？
    - 2/28 之前 ptt
    - 先來算 snapshot_count > 0 但沒有 snapshot 的 article 有多少
- PTT
    - Gossiping 版沒有抓 2019-11-11 之前的文章
        - wenyi: 問題
            - 不太確定跑一跑就停了
            - 另外指定 start url、禁止它走下一頁
    - PTT 資料集怎麼釋出
        - site / day
        - e.g. Sites / 98 PTT Gossping / 2020-01-11.jsonl
> 那個 path 要是可以從資料庫或 airtable 欄位值拼出來的 [name=Pomin Wu]
- API server
    - middle2
- 同一篇文章多個 url
    - 移除重複的工作
        - url search 很慢
        - 根據 snapshot count 排序很慢
    - https://github.com/disinfoRG/ZeroScraper/issues/44
    - 經過 parser 的 publication，偵測重複
    - customized url normalizer 加入 StandardizePipeline
    - https://github.com/disinfoRG/ZeroScraper/issues/91
- appledaily
- 上次提到的 middle2 + tmux
    - 開個很小的 linode
    - [mosh](https://mosh.org/) 進去 linode，再 ssh 到 middle2
- data analysis
    - 先請 pierre 自行探索 \o/
    - wenyi 的提案：https://g0v.hackmd.io/@chihao/0archive/%2FDvoeZunbSqK4UBq8AUg4VA
- fb gcp 雲端架構
    - 有腳本，試試看怎麼開源

### 本週工作
- progress summary for report (2)
    - article 2M
    - article snapshot ??M
    - publications ...
    - 2 sites 完整資料集
    - 建立研究者的合作
    - 更新 zeroscraper
        - command line 工具
    - fbscraper refactor
    - cloud
        - fb scrapping on gcp
        - linode instance
    - site stats
    - data standard 更新
    - api server
    - community
        - 更新 book
        - 更新 gdrive...
        - 更好上手？
- data loss
    - [x] chihao: 寫 sql + explain
> Something like `SELECT article_id, site_id, snapshot_count, (SELECT COUNT(*) FROM ArticleSnapshot WHERE article_id = Article.article_id) AS actual_count FROM Article HAVING snapshot_count > 0 AND actual_count = 0`[name=pm5]
> Made a `LossArticle` table out of the query. Made an [issues](https://github.com/disinfoRG/ZeroScraper/issues/94) for follow-up works. [name=pm5]
- 琦琦
    - [x] chihao: 開 gdrive folders
    > 目前開了 3,4,5,6,7,8 六個琦琦 [name=chihao]
    - [ ] pm5: 輸出資料集、（手動）上傳
- PTT
    - [x] chihao: 開 gdrive folders
    > 開了 98,99 [name=chihao]
    - [ ] pm5: 輸出資料集、（手動）上傳
    - [x] wenyi: 
        - [x] 改 site.py
        - [x] 跑 Gossiping 2019/11/11 以前的posts
- appledaily
    - [x] chihao: 帳號
    - [x] wenyi: 使用spider 登入appledaily
- 跑長時間的
    - [x] chihao: Linode
- API server
    - [x] wenyi: study Heroku
    - [x] sitestats 加入 api
    - [x] deploy api
    - [ ] add authentication
- facebook: bruce
    - 減少每次開一個新爬蟲機器的 image build 的時間（目前推測應該可以利用 [Cloud Build](https://cloud.google.com/cloud-build)）
    - 設定 cron 腳本讓他可以自動每隔固定時間跑（目前推測應該可以利用 [Cloud Scheduler](https://cloud.google.com/scheduler)）
    - 設定 credentials 自動從有權限的帳號載入(目前推測應該可以利用 [Service Accounts](https://cloud.google.com/kubernetes-engine/docs/tutorials/authenticating-to-cloud-platform))
    - 設計 monitor 爬蟲機器，如果遇到 security check 就關掉舊的機器，開新 ip 的機器，或更換登入 facebook 的帳號密碼（目前推測應該可以利用 [Credential rotation](https://cloud.google.com/kubernetes-engine/docs/how-to/credential-rotation), [Prometheus](https://cloud.google.com/monitoring/kubernetes-engine/prometheus) 或 [Stackdriver Kubernetes Engine Monitoring](https://cloud.google.com/kubernetes-engine-monitoring)）
    - 整理 gcp 設定成腳本，供 repo 其他人也可以馬上使用

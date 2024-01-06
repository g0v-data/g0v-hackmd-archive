---
tags: disinfo
image: https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_76117781fda5f5de955a0c29111008f5
---
# 0archive 藍圖 Roadmap

## 許願池 Wishing well


## 2019/10-2020/6 時間表 Timeline
> 詳細可參考[專案行事曆 Project calendar](https://docs.google.com/spreadsheets/d/1yvcwQ4Qx4ZqsFNscsrL1anrZQhU6-8J7j3ufXUb1RYo/edit#gid=317836919)

🌲 - Public event
👋 - Public engagement
✅ - Milestone

- [x] 🌲 12/23 g0v hackathon
    - Data sets release
    - Presentation
- [x] 🌲 1/4 disinf0thon
- [x] 👋 1/5-1/11 public engagement
- [x] ✅ 2/20 sys report (1)
- [x] 🌲 2/23 disinf1thon (remote)
- [x] 🌲 3/14 g0v hackath38n
    - Data sets release
    - Presentation
- [x] ✅ 4/17 sys report (2)
    - Sys status
    - Data archive
    - Data storage schema
    - Data exchange standards
- [ ] 🌲 5/16 disinf2thon
- [ ] 👋 5/18-5/22 public engagement
- [ ] 🌲 5/23 g0v hackath39n
- [ ] 👋 5/25-5/29 public engagement
- [ ] ✅ 5/29 community report (1)
    - Hackathons & presentations
- [ ] ✅ community report (2)
    - Data set usage by community
    - Content published

## Milestones

### 1/15

Expecting:

* A dataset of content from 10 major content farm web sites?
* Report on these content farms
    * Their sources? 以目前的資料集涵蓋範圍，可能單一內容農場的分析比較容易進行，例如以下（示意圖）
    * Credibility? 

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5711749a233bae2dfdc2bfaef2d8ff34)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e2f56a3b6b5df59331b0d916731c00f4)

### 2/28

## Pending features

* 爬 PTT：資料集裡需要 PTT 的發文、推文、作者等等資料，才能有效分析出訊息傳播路徑
    - 不一定要自己寫，也可以透過 scraper db 或 API 整合已有的好多 [PTT crawler](https://github.com/ocftw/PttCrawler)
* 爬 FB 專頁、社團：working on it
* [x] 抓 DCard
* Data pipeline
    - Goal: 要做到可以放置 play 靠 middle2 的支援一直生資訊集出來
    - Requirements
        * Accurate: data is not garbled, mis-attributed, with correct metadata to ease exploration.
        * Complete: all contents should be acquired; nothing should be left out once we put a node under monitor.
    - To those ends, the data pipeline should have the following features:
        * Crawl fast: when possible, crawlers should work in parallel to quickly acquire contents once they start circulating.
        * Re-doable parsing: the parsing of raw data should be repeatable.  If we developed a better parser, we should be able to re-run the archive to provide better results.
        * Can handle large volume: the archive will be huge.  If we make a change to the data or the process, we shouldn't have to go through the whole archive to produce the newer results.
        * Problems in the pipeline are traceable
            - We can easily check the progress on a single piece of data (a single URL), see if it went through the pipeline, and if it landed correctly on the resulting datasets.
            - If there were problems, we should be able to re-run that single URL after we fixed the pipeline.
            - An exception on the pipeline should be reported.
      - 可能會遇到的問題和解法
          - 假設有人丟了中時電子報的一篇文章，發現資料集裡面沒有這篇文章，然後怎麼辦？
              - [x] 可以輸入 url 馬上重爬或新增任務到 discover 和 update
          - middle2 掛掉的 alert
          - [x] 需要先找出這篇文章是在哪一個環節漏掉（e.g. 從沒有被discover? 或是有discover但沒有parse、或parse掛掉...）
* Data standard toolkits
    - linter & validator
    - visualization and exploration tools
    - select and export to good data formats
    - data import tools, for ppl who wants to merge all datasets into one db for further analysis
* YouTube 頻道
    - 用 RSS/Atom crawler 可以爬到一些基本資訊
        - 例如[這些影片](https://www.youtube.com/channel/UC2VegJxIx8PlnMozak9jslA/videos)可以從[這裡](https://www.youtube.com/feeds/videos.xml?channel_id=UC2VegJxIx8PlnMozak9jslA)爬到
    - 有現成工具可以把影片存下來，或是跟 ronny 的電視松合作
    - 要抓出文字內容就需要 OCR 字幕，或是跟 ronny 的電視松合作
* Ask questions and find answers
    - 「內容農場的文章都是哪裡來的？」「內容農場成份分析」
    - 「內容農場最喜歡轉哪種文章？」
* Tools to do cross-project search of disinfo pieces and related claim reviews
    - pm5: Once we have a way to merge disinfo and claim reviews from various projects into one archive, we can start providing tools to help fact checkers.
* Dynamic IP / distributed cloud infra for crawlers
    - crawlers on known cloud services can be easily blocked
    - raspberry pi round robin? (via ronny + pm5)
    - 分散式 proxy
* Good UI for journalists

- ptt
    - [x] [ptt.py](https://github.com/disinfoRG/ZeroScraper/blob/master/newsSpiders/ptt.py)
    - [x] 加入 [`newsspider.runner.discover`](https://github.com/disinfoRG/ZeroScraper/blob/master/newsSpiders/runner/discover.py#L63-L64)
    - [ ] 用 `zs-site.py discover xxx` call，但是Ctrl+C無法結束process
        - 被 Ctrl+C 被 CrawlerProcess擋下來，要到`process.start`才開始
        - ptt.DiscoverSite.run 設定成twisted process，不要真正跑
        - blocking `requests` -> non-blocking `axios`
        - discover runner 建立 reactor

### Monitoring
- API
    - single url status check
        - input: url
        - output: 這個 url (normalized) 在系統內部的現況
    - GET API endpoints
        - GET /articles/[id]
        - GET /articles?url=[url]
            - 需要內建 url normalizer :heart:
            - Exact match
        - GET /publications?q=[string]
            - MySQL match 標題、內文
            - 要分頁
        - GET /sites/[site_id]/article_count
        - GET /sites/[site_id]/latest_article
    - scripts
        - crawl (discover & update) single url
        - parse single article
        - cron

- Dashboard
    - a table showing today's stats, compared with 3-day, 7-day, 30-day comparison?
    - order by today's stats asc

---
tags: disinfo, 0archive
---
# On FbScraper...

## 已經有的 PR
> [name=bruce] 目前 (2020.3.6 14:04 [commit at that time](https://github.com/disinfoRG/FbScraping/commit/1ee095686a56cf62fa38e1d27a3037fb8bf57269)) 送 PR 前可以用以下的 script 先跑過一次，然後看 db 有增加 Article 和 ArticleSnapshot 的資料代表程式碼是可執行的
```shell=
# discover article urls of site 90 without login
python3 fb_handler.py --discover --page --max 1 --chunk-size 1 --cpu 1  --timeout 60 --between 0 --site 90
# discover article urls of site 20 as logined
python3 fb_handler.py --discover --page --max 1 --chunk-size 1 --cpu 1  --timeout 60 --between 0 --site 20 --login
# update one article of all sites without login
python3 fb_handler.py --update --page --max 1 --chunk-size 1 --cpu 1  --timeout 60 --between 0
# update one article of all sites as logined
python3 fb_handler.py --update --page --max 1 --chunk-size 1 --cpu 1  --timeout 60 --between 0 --login
```

### PR #20
- 3/3 完成 merge by [this commit link](https://github.com/disinfoRG/FbScraping/commit/ec61d0cbf1fc0d89ce7a95528903beb09775e391)
- 後續討論

## 一些問題
- update 多個 url 用同一個 chrome 會怎麼樣？
- 現在使用了許多進度序列, e.g. `Item Process Countdown`, `Take A Break Countdown`, `update fb_page`, `discover fb_page`，每一個進度序列是代表什麼？程式主要會放在middle2上面跑，使用這些進度序列是否有幫助？
- chunk 是為了減少一個 pool 跑的工作，這樣做是為了應付 fb security check，不用到一個 pool 跑完才處理。之後應該改成平行處理的方式。

## 一些希望
- console 的 message & logfile 上的訊息可以有個呼應
    - 實際遇到的問題：遇到insert error 的時候，console有重複的print error，但是log上面看不出來有問題，而且code是正常繼續執行。
        - **console**: `line 109, in raise_mysql_exception: [InternalError] (pymysql.err.InternalError) (1364, "Field 'created_at' doesn't have a default value"), note: NoneException of type <class 'sqlalchemy.exc.InternalError'> occurred in file "/Users/wyw/.local/share/virtualenvs/FbScraping-ZxQqmDhN/lib/python3.7/site-packages/pymysql/err.py", line 109, in raise_mysql_exception: [InternalError] (pymysql.err.InternalError) (1364, "Field 'created_at' doesn't have a default value"), note: NoneException of type <class 'sqlalchemy.exc.InternalError'> occurred in file "/Users/wyw/.local/share/virtualenvs/FbScraping-ZxQqmDhN/lib/python3.7/site-packages/pymysql/err.py"`,
        - **log**: `pipeline_timestamp_1582927141: insert to database, table = Article, id = None, data = {'first_snapshot_at': 0, 'last_snapshot_at': 0, 'next_snapshot_at': -1, 'snapshot_count': 0, 'url_hash': 4264407347, 'url': 'https://www.facebook.com/1063653903655415/posts/2884068654947255', 'site_id': 54, 'article_type': 'FBPost', 'created_at': 1582927141, 'redirect_to': None}`
- 一個process一支logfile，現在會遇到的情況是一個process update N 篇文章的話產生N logfiles (1 for each post)。

### 程式碼架構

共識：

1. [x] [name=wenyi] 建立 `fbscraper.actions.update` & `fbscraper.actions.discover` 模組，把它們的 Crawler, Pipeline, Parser and Spider 搬進去。
2. [ ] 建立 `fb.py`、`fb-site.py`、`fb-post.py` 三個指令。`fb.py <cmd>` 如果遇到不認識的 `cmd` 就會去執行 `fb-<cmd>.py`，例如 `fb.py site discover 123` 實際上會執行 `fb-site.py discover 123`。`fb-site.py` 與 `fb-post.py` 先 break down 到 8. 去做。
    - `fb-site.py` & `fb-post.py` 不用做 multiprocessing。只有 `fb.py` 會做 multiprocessing。
    - 【待議】要用 post 還是用 article？用 article 符合 db 與內部程式的用法（但 fbscraper 的 db 也不一定要與 zeroscraper 完全一致），用 post 符合社群 developers 的理解。
3. [x] [name=pm5] 用 Python standard library 的 `logging`。可以同時 log 到 stderr 與檔案。 log 到的檔案時，一個工作（job）產生一個 log file。
    - [ ] Log filename 是一個 option，`--log <filename>` 或是其它。這個等 `fb_handler.py` 裡的邏輯都搬到 module 裡面以後再做。
4. [x] [name=bruce] [resolve by this PR](https://github.com/disinfoRG/FbScraping/pull/26)  取消 `facebook.Facebook` class，把用不到的 method 移除，用得到的 method 改成 `facebook.some_func(driver, ...)` function。也把 `helper` 裡關於臉書的特定的 selenium 操作移過來，例如 `helper.click(node, driver, ...)` 變成 `facebook.click(driver, ...)`。
    - 這樣之後 `facebook.py` 裡就不會再有 `facebook.Facebook` class，而且裡面的 function 應該大部份是以 `(driver, ...)` 為參數。
    - 可能需要增加 `facebook.create_driver()` function（但這不一定要放在 `facebook` module 可以再看看），使用上就會是
      ```python
      import facebook as fb
      driver = fb.create_driver(...)
      fb.login(driver, ...)
      fb.do_somthing(driver, ...)
      driver.close()
      driver.quit()
      
      # 以後覺得太多操作的話，也許再改成這樣會比較容易讀
      #
      # fb.login(driver)
      #    .do_something()
      #    .and_do_something_more()
      ```
    - `facebook` module 裡可能會增加一些 class 例如 `facebook.UserProfile`，但也有可能這些包裝好的資料都會存到 db，那到時候就跟著 db schema 的格式就好了，不需要特別建一個 class。
5. [x] [name=bruce] [resolve by this PR](https://github.com/disinfoRG/FbScraping/pull/23)有些 `try...except` 是重複的，應該移除到一些。
    - 例如 `fb_handler` 裡一些 `try..except` 但其實裡面 call 的程式碼本來就已經有 `try...except` 了
    - 或是有些 `try...except` 應該要停止程式，但只有 log 但沒有再 `raise`，程式就繼續跑
    - 初步來說 pipeline 可以不會處理任何 db exception。有需要 retry 的情況，再處理（有時候沒有 retry 其實也沒有太大關係）。
6. [x] [name=bruce]([resolve by this PR](https://github.com/disinfoRG/FbScraper/pull/30)) 設定檔合成一個 `settings.py`。現在有 `config.py` 和 `settings.py`，還有從 `.env` 讀設定進來。
    - 跟 ZeroScraper 一致的用法，目前的設定搬到 `settings.py`，是屬於整個專案的設定與預設值；config 保留給不同臉書 page 或 site 有各自的設定（例如 page 需要不同的 delay）的時候再用。
7. [x] [name=wenyi] `fbscraper.actions.discover` 與 `fbscraper.actions.update` 都是一個 Python file 就可以了，裡面包含 `DiscoverCrawler` 與 `UpdateCrawler`，包含目前 Crawl 與 Spider 的功能。會有一個 `DiscoverCrawler.crawl_and_save` 與 `UpdateCrawler.crawl_and_save` method 做目前的 Spider 的 `work` method 的工作。
8. [x] [name=bruce]([resolve by this PR](https://github.com/disinfoRG/FbScraper/pull/32)) 先寫 `fb-site.py` 與 `fb-post.py`（不用 multiprocessing）確定程式碼架構夠好。
9. [x] 安裝 pre-commit 然後設定好。
10. [x] [name=bruce]([resolve by this PR](https://github.com/disinfoRG/FbScraper/pull/31)) 把處理（包含偵測與應對） facebook security check 的邏輯搬出來到 `facebook` module。
11. [x]  [name=bruce]([resolve by this PR](https://github.com/disinfoRG/FbScraper/pull/38))把 `fbscraper.helper` 裡關於 facebook 處理的 function 移到 `fbscraper.facebook`。

> The followings are mine. [name=Pomin Wu]
- `facebook.Facebook` 不是個好封裝，不應該寫成 class；有 `facebook.*` function 就可以了。沒有再用到的 function 應該都移除。
- `helper.Helper` 裡有關 Facebook webdriver 操作的 method 全部應該移到 `facebook.*` 做為 function。
- `update_spider.UpdateSpider` 與 `discover_spider.DiscoverSpider` 沒有實際作為，應該移除後以 `UpdateCrawler` 與 `DiscoverCrawler` 取代。
- 用 Python standard library 的 `logging`
- `update_crawler` & `update_pipeline` & `update_parser` 應該合併成一個 `update` module；`discover_*` 也是。


> [name=wenyi]
- `discover_spider.py`, `discover_crawler.py`, `discover_pipeline.py`, `discover_parser.py`
    - [`spider`](https://github.com/disinfoRG/FbScraping/blob/master/discover_spider.py) is a thin wrapper, [`crawler`](https://github.com/disinfoRG/FbScraping/blob/master/discover_crawler.py) is the main function, [`pipeline`](https://github.com/disinfoRG/FbScraping/blob/master/discover_pipeline.py) handles db insertion, [`parser`](https://github.com/disinfoRG/FbScraping/blob/master/discover_parser.py) handles extracting post urls (doesn't really need a class for it...). 
    - 目前的結構是：[`fb_handler` 呼叫 `spider`](https://github.com/disinfoRG/FbScraping/blob/master/fb_handler.py#L66)
    -> [`spider` 將`pipeline` & `parser` 輸入進`crawler`](https://github.com/disinfoRG/FbScraping/blob/master/discover_spider.py#L18-L20)，並呼叫`discover_crawler.py`工作。

    - 應該整合四支程式為一支
[`pipeline` 中只有一個method在`crawler`中被使用](https://github.com/disinfoRG/FbScraping/blob/master/discover_crawler.py#L64)，[`parser`也是](https://github.com/disinfoRG/FbScraping/blob/master/discover_crawler.py#L74)。`crawler.py` 才是主程式，應該可以把 `spider`, `pipeline`, `parser` 刪除，把`pipeline` 和 `parser` 中有被使用的(先)放進`crawler`中，然後讓`fb_handler`直接呼叫`crawler`。

- `update_spider.py`, `update_crawler.py`, `update_pipeline.py`, `update_parser.py`: 同上

- fb_handler拆成三支：site.py, post.py, fb.py，因為fb_handler目前太雜，讓管理起來非常困難
    - e.g. FB Handler arguments 過多。
        - 哪些是必要、哪些為optional不清, 且optional argument的default值未妥善記錄，目前只有在`fb_handler.py` 的[`argparser`](https://github.com/disinfoRG/FbScraping/blob/master/fb_handler.py#L217-L229)中有提到（但並不完全正確）
        - 若arguments組合輸入不符期待也沒有跳出任何訊息，就直接什麼都沒做結束了(e.g. `python3 fb_handler.py --update --site_id 53`)
        - `--page` and `--group` 這兩個arguments是要幹嘛，為何一定要指定一個？
        - 不是很清楚update是不是一定要指定一個site （目前經驗好像：是）

- `helpers.py` 的Functions 應該要回歸在適當之處（e.g. scroll）
- `settings.py` & `config.py` & `.env` 三個檔案可否合併或減少？

> [name=bruce]
- 減少重複的 try-except
- log: [timestamp]-[file-method]-[parameters][error]
- 一個檔案負責一個工作，檔案可以寫單元測試負責的工作
- Handler > Spider > Crawler, Parser, Pipeline（目前寫在 https://github.com/disinfoRG/FbScraping#architecture）
# Architecture
## Handler (Main Function, aka. called by cronjob on Middle2)
- xxx_handler.py
    - decide the target url list for spider to crawl and parse
    - decide how different spiders to work together
## Spider (xxx now can be: discover or update)
- xxx_spider.py
    - temporary center for all arguments later used to feed in crawler, parser, and pipeline
    - decide how crawler, parser, and pipeline work together
- xxx_crawler.py
    - input: url, output: html
    - principle: output be maximum html of a url with minimum parsing
    - process
        - enter site by url
        - scroll, click and expand the webpage if in need
        - save whole page's html, but sometimes save only part of the html for whole page's html may too much and broke the database pipeline (especially async-loaded posts in sinlge page website)
    - note: may add callbacks to use parser or pipeline, or a totally independent instance
- xxx_parser.py
    - input: html, output: interesting data
    - principle: output be mostly structured than analogy
    - process
        - load html into beautifulsoup (called it soup)
        - apply css selector on soup to get interesting data
    - note: may be used as a callback function in crawler, or a totally independent instance
- xxx_pipeline.py
    - input: html or data, output: write input into database
    - principle: output be minimum modification of input when writing into database
    - process
        - load input from parser or crawler
        - write input with specified id from spider into database
    - note: may be used as a callback function in crawler, or a totally independent instance
## Database
- queries
    - implement the details to CRUD with database
## Browser
- facebook.py
    - based on webdriver and specialized for facebook
    - cookie_path for reusage to login without reentering email and password
    - session_path for reusage of running browser without reopening a new window
## Utils
- helper.py
    - concentration area of convenient functions and should be independent from any other files
## Configuration
- config.py
    - configure default arguments for CLI
- settings.py
    - configure required arguments for browser and database


## Programming style

### 個人意見

我個人偏好是減少程式碼中的 "code smell": https://www.amazon.com/Refactoring-Improving-Existing-Addison-Wesley-Signature-ebook/dp/B07LCM8RG2

* method and function 長度不要超過 45 行
* 一個 class 做一件事
* method, function, class names 要看得出來它負責做什麼

「一直變來變去」是常態的話，好的 programming style 就是要讓你能快速改來改去

technical issue 在改變架構之後通常就會很容易解決 SO 調整架構優先於修 bug


## Technical issues

- multiprocessing / threading?
    - update 時都會遇到這個error `/Users/wyw/anaconda3/envs/watchout/lib/python3.7/multiprocessing/semaphore_tracker.py:144: UserWarning: semaphore_tracker: There appear to be 1 leaked semaphores to clean up at shutdown len(cache))`

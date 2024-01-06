---
title: "g0v tasks queue 整合"
tags: hackpad
---

# g0v tasks queue 整合

> [點此觀看原始內容](https://g0v.hackpad.tw/1ngNLPX3mLr)

Updated: 現在這頁已經爆炸了，有各種討論與實作 XD 我們慢慢把它整理出來到不同頁面吧:
    [http://hack.g0v.tw/g0v-issue-tracking/1ngNLPX3mLr](http://hack.g0v.tw/g0v-issue-tracking/1ngNLPX3mLr)


## 原始討論：

**拋磚人:** kcwu
**狀態：**已經運作專案 (邊討論邊實作中)
**專案簡介**: 許多人想幫忙但不知如何下手, 需要簡單的 task. 本專案希望讓各 project 的 easy task 更容易被找到
**工作目標**:
關於 Label 定義的內容，已切到新頁面 [g0v issue label ](https://g0v.hackpad.tw/L23ntanWnv7)

1.  [寫一個 script 把 github project 加上這些 tag](https://github.com/g0v/dev/issues/16) \- 也需要這些 tag 的 github 顯示顏色
2.  寫一個 page 把 project hub 上的 github issue 中有特定 tag 的 task 撈出來
    1.  猜測應有現成的可以改, 不然也可以自己 call github api
> g0v member 可以先在 dashboard 看到 [https://github.c](https://github.cwwom/organizations/g0v/dashboard/issues)[ww](https://github.cwwom/organizations/g0v/dashboard/issues)[om/organizations/g0v/dashboard/issues](https://github.cwwom/organizations/g0v/dashboard/issues)
> [name=Chia-liang K]

    2.  可以在搭配各 repo 的 language summary 顯示
3.  推廣給各 project
    1.  標上 easy tag 的 task, 希望把內容寫清楚一點, 譬如要什麼技能
4.  在新手的文件上(ex新手村)請他們來認領工作

使用資料: github issue api

## IRC 上的一些討論

記錄一下以免忘掉，同時也需要有人整理一下，log 好多。XD

### August 15, 2013


14:07 < billy3321> clkao: g0v的404不適合放這個
14:07 < billy3321> 應該要放issue list
14:07 < billy3321> "您要找的網頁看起來不存在，不過您要找的工作應該在這裡。"

### August 12, 2013

18:00 < kcwu> isacl: 我原本想的是新做出來的只是 search/filter 系統(read only). 操作還是讓大家自己回 github. 自己作 issue tracking 太              累了
18:31 < isacl> kcwu: yeah 大致上是 readonly 沒錯。但是沒 github 帳號���人，如果想開始處理這個 issue. 我們要想辦法標示。
18:31 < isacl> kcwu: source of truth 必須是 github
18:32 < isacl> kcwu: g0v 自己的 db 可能會有些額外的 flag.
18:33 < isacl> kcwu: 目前主要是 jeffhung 在處理實作，可以彼此 sync 一下想法。
21:42 < ETBlue> isacl_:  請問 g0v tasks queue 整合跟 [http://miau715.github.io/eo4/related_job.html](http://miau715.github.io/eo4/related_job.html) 需要串起來嗎？
21:42 < kcwu> ETBlue's url: \[eo4 人力銀行\]
21:43 < isacl> ETBlue: 我覺得要
21:43 < ETBlue> isacl: 不曉得要怎麼弄，沒概念中...
21:44 < isacl> ETBlue: 請問目前 eo4 開寫寫後端抓 github issue 的 code 了嗎？
21:44 < isacl> s/開寫/開始/
21:44  * ETBlue 受 eo4 人力銀行作者黃米奧指示幫忙橋事
21:44 < clkao> 應該還沒，不過 jeffhung 的 widget 好像弄的差不多了
21:45 < hcchien> 喬事!!
21:45 < isacl> 不確定 jeff 有沒有做獨立頁面。 如果要做，可能也是後端用同一份，頂多前端 CSS 不同，分別是 eo4 跟 widget.
21:46 < clkao> right
21:46 < clkao> 目前應該沒做 但是 controller 重用應該相當容易
21:46 < isacl> [http://utcr.org/g0v-issue-tracker/](http://utcr.org/g0v-issue-tracker/) 至於這醜東西，我最近會把它下掉 XD
21:46 < kcwu> isacl's url: \[g0v Tasks Queue Viewer for Github\]
21:47 < ETBlue> 好一頁坑坑洞洞的網頁... 每行都是坑
21:48 < isacl> ETBlue: 嗯，那後端應該就實作一份 storage 跟 github issue client. 看要不要一起到某一頁 hackpad 橋一下
21:48 < isacl> ETBlue: eo4 有 hackpad 討論頁嗎
21:49 < ETBlue> isacl: 目前只有在這串討論... XD [https://groups.google.com/forum/?hl=zh-TW%E3%80%82#!topic/g0v-moc/6uG5L6jY9fQ](https://groups.google.com/forum/?hl=zh-TW%E3%80%82#!topic/g0v-moc/6uG5L6jY9fQ)
21:49 < kcwu> ETBlue's url: \[Google 網上論壇\]
21:50 < isacl> ETBlue: jeff 的現在都在這邊 [http://hack.g0v.tw/g0v-issue-tracking/1ngNLPX3mLr](http://hack.g0v.tw/g0v-issue-tracking/1ngNLPX3mLr)
21:52 < ETBlue> miau715: hooray! isacl: 就是這位
21:52 < superbil> miau715: 請直接發問即可
21:52 < isacl> jeffhung: ping
21:53 < ETBlue> miau715: 剛才對話 isacl> ETBlue: 嗯，那後端應該就實作一份 storage 跟 github issue client. 看要不要一起到某一頁
                hackpad 橋一下
21:54 < isacl> miau715: Hi, 我目前也只是起頭實驗一下 github API 的使用，沒有另外做什麼了。而 jeffhung 那邊做了一個 widget, 我們的討
論都在: [http://hack.g0v.tw/g0v-issue-tracking/1ngNLPX3mLr](http://hack.g0v.tw/g0v-issue-tracking/1ngNLPX3mLr) (有點凌亂)
21:54 < miau715> 我現在做的 eo4 因為主要是想讓自閉人比較容易參加，所以專案的主要成員可能會需要多費點心..
21:55 < miau715> 主要問題是預期每個專案會有負責人或管理人
21:55 < miau715> 也有每個專案的參與者
21:55 < miau715> 不知道目前有沒有哪裡已經整合了這種資料，沒有的話要怎麼生出來我也沒概念...
21:58 < isacl> miau715: 我們之後會訂一個資料存取 API 給你抓。並且可以用 label 名稱作 filter. 可以抓出需要特定專長的 task, 或是適合新               手的 task 等等。
21:58 < jeffhung> kcwu, isacl: 我這兩天人在醫院剛好可以開工，明天開始上班就沒那麼多時間了，所以我選擇了直接就先開幹，想說有東西可以
動之後，大家應該就會有更清晰的想法。建議大家先把想法 dump 到 [http://hack.g0v.tw/g0v-issue-tracking/1ngNLPX3mLr](http://hack.g0v.tw/g0v-issue-tracking/1ngNLPX3mLr) ，
                  irc 東西太多追不完。XDD  # 18:33 < isacl> kcwu: 目前主要是 jeffhung 在處理實作，可以彼此 sync 一下想法。
21:58 < isacl> miau715: 可能會在這幾天吧，還不需要實作，但 web API 先訂出來，較容易接軌
21:59 < lanfon72> miau715:暫時...沒有
21:59 < isacl> jeffhung: 嗯我也是平日在上班，不過我可以先訂個 restful API, 然後 document 起來 ok 嗎？
22:00 < miau715> 我也想過要不要做媒合配對或是新手專用一類的，但後來想一想覺得...太複雜了 XD 還是大家上去看看有沒有可以撿的工作就好
22:00 < miau715> 況且哪些工作適合「新手」實在是每個領域都不一樣阿 Orz
22:01 < isacl> miau715: 嗯沒錯，可能領域的 label 先訂出來吧。 hackpad 上有個 label 表格看似是之前 clkao 整理的。
22:03 < isacl> miau715: [http://miau715.github.io/eo4/related_job.html](http://miau715.github.io/eo4/related_job.html) 這頁裡面的東西, API 都會提供資料。
22:03 < kcwu> isacl's url: \[eo4 人力銀行\]
22:03 < jeffhung> isacl: 我比較傾向不要訂 restful api，再怎樣訂大概都跟 github 的差不多。
22:03 < isacl> miau715: 王小明是 github user 還是？
22:04 < isacl> jeffhung: 嗯是會差不多。那你本來預計用什麼方式存取我們的 issue cache?
22:04 < jeffhung> miau715: 我目前的想法是，每個 issue 可以標 easy/medium/hard 或 programmer/designer/writer 之類的 labels
22:05 < miau715> @isacl 我沒有預設用什麼方式登入耶，只是總要有個方式判定使用者的身分這樣＠＠
22:05 < isacl> miau715: hmm. facebook XD?
22:05 < jeffhung> 請大家分頭進 github 為每個 issue 標 label，這樣前端 filter 完之後，就可以依據瀏覽者的屬性，顯示適合跳的坑。
22:06 < miau715> @jeffhung 我沒有期望要標困難度，因為大部分人應該都遇過別人說「這很簡單阿你怎麼做那麼慢..」之類的不爽事情XD
22:07 < miau715> 總之我覺得難度應該是接工作的人自己感覺的而不是發工作的人說的...
22:07 < jeffhung> miau715: 這樣講好像也對。
22:08 < miau715> 所以我理想中的發工作方式是大工作也許比較活躍的人接下來，然後他可以再開單下包
22:08 < jeffhung> 總之，我想像中的 filtering 大概可以就分幾個維度。可以是能力特性、難易度、專案類型... 等等，whatever。
22:08 < isacl> jeffhung: 嗯那 cache 想存在哪邊嗎？
22:08 < miau715> 或直接發「需要分配工作」的工作讓擅長溝通的人來接
22:08 < jeffhung> isacl: 我還在想。多一層 cache 要處理 consistency 也挺麻煩的。
22:09 < miau715> 工作可以是任何形式，只是目標要清楚，不需要猜測要幹嘛的時候比較容易參與
22:09 < miau715> （理想狀況 = =;;;）
22:09 < jeffhung> isacl: 有點想偷懶先完全沒有 cache，完全沒有 cache，完全沒有 cache，等有人抱怨太慢再來看哪邊慢。
22:10 < jeffhung> isacl: 另外剛剛想到的一個噁濫招數，現在會慢是因為每個 repo 都要個別呼叫拿資料。乾脆我們拿 github 當 cache。
22:10 < isacl> jeffhung: yes, 但如果你指得是用前端撈 issue. 沒 github 帳號的人，沒辦法過 OAuth 抓 github 的 issue.
22:10 < jeffhung> isacl: 開一個 repo 專門 aggregate issues，這樣前端只要撈這個 repo 就好，一個 api call 搞定。
22:11 < jeffhung> isacl: 我直接用 curl 不加帳號也可以撈資料啊。應該是不需要 login 也能抓的。
22:11 < scourgen> 可以架一个proxy，没有账号的请求走proxy，proxy再用某个内置账号去捞数据？
22:11 < isacl> jeffhung: 沒過 OAuth, 一小時撈超過 60 次會被擋住。 :P
22:12 < scourgen> 带了token就可以很多了
22:12 < isacl> scourgen: 沒錯.
22:12 < scourgen> 没有token很多api都限制一小时60次
22:13 < jeffhung> isacl: 咦？是 per hour 不是 per minute 喔？這樣就搞笑了。XDD 那走 OAuth 有其他 rate limit 嗎？
22:13 < scourgen> For requests using Basic Authentication or OAuth, you can make up to 5,000 requests per hour. For unauthenticated
                  requests, the rate limit allows you to make up to 60 requests per hour. (The Search API has custom rate limit
                  rules.)
22:13 < jeffhung> 可見我寫程式不夠快，測試時撞不到 60 req/hr 的限制。XDD
22:13 < isacl> 因此中間可能需要加一層。另外，沒有 github 帳號的人，想要關注或是標明說「我要參與某 task」這資料有可能也必須另外存
22:14 < jeffhung> isacl: 那我現在傾向於這個 cache 基本上用起來跟
22:14 < jeffhung> isacl: 原來的 github api 很像，只是多了我們想要外加的 annotation 欄位。
22:15 < scourgen> jeffhung,说明你不是 reflush driven development
22:15 < isacl> 另外，若又需要自己做出 issue 跨 repo 的關聯，也可能需要另外存資料。（當然也有可能在 github issue 的 description 偷加
               自己的 tag）
22:15 < scourgen> 这是好事
22:15 < isacl> jeffhung: 嗯同意
22:16 < isacl> jeffhung: [http://developer.github.com/v3/](http://developer.github.com/v3/#rate-limiting)[#rate](https://g0v.hackpad.tw/ep/search/?q=%23rate&via=1ngNLPX3mLr)[-limiting](http://developer.github.com/v3/#rate-limiting) 就是 60 跟 5000 request per hour 的差別
22:16 < kcwu> isacl's url: \[GitHub API v3\]
22:17 < jeffhung> isacl: 原始 github 上的 issue 怎樣跟存在 external storage/cache 的連動，還需要再多想想。
22:17 < isacl> 因此我才有提出說，如果有想換 issue tracking 平台，要趁早說 :P 不然我們要被埋進坑裡面了
22:18 < isacl> jeffhung: yeah. 但如果想提前串前端，API 可以先開出來。不見得 web/restful, 但先開一下可能會比較容易接下來進行
22:19 < scourgen> jura 如果是 for open source project的话是free的
22:19 < scourgen> 强烈推荐一下
22:19 < scourgen> jira
22:19 < tuiry> pofeng 可以麻煩你，在圖片/文案沒有成熟前，不要發布在公開宣傳頁面嗎?
22:20 < isacl> scourgen: 嗯 jira 真的很強大。不過後來大家昨天覺得還是用 github, 單純好用，而且 source 也都在 github, 整合方便。
22:20 < jeffhung> isacl: 我的想法比較 decentralized，強迫大家統一到某平台使用 issue tracking，這樣會不 work。我們該做的是，大家喜歡
                  用什麼平台，我們就盡量去支援。
22:20 < isacl> jeffhung: hmm. cache 我也還沒有特別的想法
22:21 < scourgen> source到不是什么问题，现在各个project manage系统都支持的很好
22:22 < isacl> jeffhung: 若 decentralized ，未來 task 可能會分散在不同的平台，那我們就更需要自己 own 一份了。
22:23 < jeffhung> isacl: 我們可不可以這麼說，我們缺的是 OpenID for Github，如果大家不管用哪邊的帳號，都可以參與 issues 的討論，這樣
                  cache 的問題就可以解決了？！
22:23 < isacl> jeffhung, miau715: 抱歉得先暫離一下，晚點回來追討論 :)
22:24 < jeffhung> isacl: 或是 mash up 就好，cache 就只是單純的 cache，不牽涉 logic。
22:24 < isacl> jeffhung: 嗯不要做 logic
22:26 < jeffhung> isacl: cache 不做 logic 的話，那選擇就多了，切來切去也可以。(就算有過 OAuth 還是有 rate limit，所以可以大家一起來
                  貢獻 cache/fetcher \[誤\])
22:26 < isacl> jeffhung: 大致應該是兩個目標: 1. 沒 github 帳號的人要能參與。2. 要能跨 repo 的集中管理 task.
22:27  * isacl &
22:27 < jeffhung> 2. 集中「管理」 task 還是
22:27 < jeffhung> isacl: 2. 「集中{管理」 task 還是
22:28 < jeffhung> isacl: 2. 「集中『管理』 task 」還是「集中『呈現』task」就好？
22:28 < isacl> jeffhung: 對本來有想讓每個人看網頁時，ajax 去 update cache XD 但這樣有點危險
22:28 < superbil> 感覺呈現就夠了
22:29 < superbil> 管理的話權限又會集中(?)，然後會要處理，純粹讓人快速找到再回到該專案就很夠
22:29 < isacl> 嗯 sorry, 管理改成呈現，之後再看怎麼加上簡單的「關注」之類的功能吧
22:30 < jeffhung> 2. 集中「呈現」的話，那我現在弄得大概就是這樣做 (除了 rate limit 問題)
22:31 < jeffhung> 基本想法就是 filter 有若干 dimension，歡迎大家幫忙發想，但基本上都是用 label 來過濾。
22:32 < jeffhung> 另外排序若 issue 很多時就會有幫助，可以用哪些屬性來排序，也歡迎大家幫忙發想。
22:33 < jeffhung> 排序的話就不限於 label，但必須是 github api 裡面有的欄位 (或未來外加的 annotations)
22:33 < isacl> jeffhung++
22:33 < jeffhung> filter 可以有 pseudo label，如 repo name as label 就是一例。這個要特殊處理，也歡迎大家一起發想。
22:34 < isacl> 前端 widget 跟 eo4 要怎���不重複工，也可以討論一下
22:34 < jeffhung> 基本上「呈現」的問題，假設 scope 設定成以上，程式方面就可以快速進行，大家的發想結果，以後再改進去很快。
22:35 < jeffhung> 1. 沒 github 的人怎麼參與暨迴避 rate limit 問題
22:35 < jeffhung> 假設我們目標只設定在「呈現」，那就可以是只靠 cache 解決。
22:36 < jeffhung> cache 可以有兩種做法：1) 被動 cache: 當有人瀏覽時，自動 cache 住 2) 主動 cache: 用 crontab 主動「爬」github api 放                  進 cache 裡。
22:37 < jeffhung> 2) 比較簡單，request rate 也好控制。但是情況 cache 是舊得機率還算大。
22:38 < superbil> jeffhung: github 有提供 server hook ，這個是否可以提供為「主動」的更新來源?
22:39 < jeffhung> superbil: 這也是個好辦法。
22:40 < jeffhung> 總之，我建議 cache 的 spec 跟 github api 要 compatible，未來切過去就很快，現在也可以先假裝沒 cache 這回事。
22:41 < jeffhung> 而 cache 要 behave like a proxy 用 1) 的做法，還是 behave like a simple storage 用 2) 的做法來更新，都可以。
22:52 < isacl_> jeffhung: 對耶 rate limit 只要架個 proxy 就解決了，而且又簡單。API 就完全跟 github 一樣。很棒的想法。
22:52 < isacl_> 我明天應該可以用
22:53 < superbil> isacl_ jeffhung ++
22:59 < jeffhung> 我現在的做法是，用 jquery plug-in 寫 dao 存取 github api or cache，然後寫 angularjs controller 把 presentation 跟
                  dao 接起來。
23:00 < jeffhung> 首先，jquery plug-in 那部分還不怎麼 jquery，我準備等 interface 比較確定要長怎樣時再來弄。但基本上都會是靠
                  callback 把內容送出去。
23:01 < jeffhung> 這樣的做法，以後 jquery plugin as the dao 與 angularjs controller 的部分，理論上可以 reuse。
23:02 < jeffhung> 若 reuse 時是 angular，那就跟 controller 接，若 reuse 是其他東西，那就跟 jquery plug-in 接。
23:02 < jeffhung> hmm.. jquery plug-in 這邊可能根本不需要是個 jquery plugin。Anyway 再說。

## Full Site Mockup


[Chia-liang Kao](https://g0v.hackpad.tw/ep/profile/AHlg3ouwI8g) 提到 [https://github.com/miau715/eo4](https://github.com/miau715/eo4) 有個 full site 的 mock up。
miau715 放到 github pages 上了： [http://miau715.github.io/eo4/](http://miau715.github.io/eo4/)

## Task Queue Service


1.  整個 task queue 應該可以視作一個超大 table，裡面每個 row 是一個 github issue
2.  所有 issues 是 g0v 這個 github organization 於 github 相關專案的 issues 聯集
    1.  但應該也要可以額外指定其他 repo (not user/org) 加入
3.  取得內容時，可以指定 filter 與 ordering 當參數。
4.  Filter
    1.  可以是 issue 的:
        1.  label (tag)
        2.  所屬的 project
    2.
5.  ordering
    1.  可以被拿來排序的有：
        1.  最後更新/回應日期
        2.  發 issue 日期
        3.  comment 數
        4.  關注人數? (how)
        5.  reopen 次數 XD
    2.
> 用google app script 丟到 google spreadsheet?
> [name=HisnYi C]

> 不錯的主意，所以可以分成前、後端。後端把資料從 github 拉到 google spreadsheet 裡，前端則由 jquery-plugin/angularjs-controller 從 google spreadsheet 拉資料。
> [name=Jeff H]

> 不過目前我只有「單向」的想法：github -> (cache storage) -> library (jquery/angularjs) -> frontend；「雙向」怎麼做還不敢深入去想。
> [name=Jeff H]


後端 API 架構：
- client (不帶 auth 資訊) <=> g0v github API proxy (帶 client\_id 與 client\_secret) <=> github API
    - 這樣 proxy 實際可以存取到 github 的限制是 5000 request / per hour
    - client 的存取無限制 (前提是 proxy 有啟用 cache, 並設定好可負擔的 expire time)
    - ATS 的 remap.config 設定
> 請教一下 ATS 是什麼？？
> [name=Jeff H]

> Apache Traffic Server
> [name=isacl]

        - map [http://](http://issue-api.g0v.tw/)[i](http://issue-api.g0v.tw/)[s](http://issue-api.g0v.tw/)[s](http://issue-api.g0v.tw/)[u](http://issue-api.g0v.tw/)[e](http://issue-api.g0v.tw/)[-](http://issue-api.g0v.tw/)[a](http://issue-api.g0v.tw/)[p](http://issue-api.g0v.tw/)[i](http://issue-api.g0v.tw/)[.g](http://issue-api.g0v.tw/)[0](http://issue-api.g0v.tw/)[v](http://issue-api.g0v.tw/)[.t](http://issue-api.g0v.tw/)[w](http://issue-api.g0v.tw/)[/](http://issue-api.g0v.tw/)  [http](https://api.github.com/)[s](https://api.github.com/)[://a](https://api.github.com/)[p](https://api.github.com/)[i](https://api.github.com/)[.g](https://api.github.com/)[i](https://api.github.com/)[t](https://api.github.com/)[h](https://api.github.com/)[u](https://api.github.com/)[b](https://api.github.com/)[.c](https://api.github.com/)[o](https://api.github.com/)[m](https://api.github.com/)[/](https://api.github.com/)
> map [http://h](http://hack.g0v.tw/issues-api/github/)[a](http://hack.g0v.tw/issues-api/github/)[c](http://hack.g0v.tw/issues-api/github/)[k](http://hack.g0v.tw/issues-api/github/)[.g](http://hack.g0v.tw/issues-api/github/)[0](http://hack.g0v.tw/issues-api/github/)[v](http://hack.g0v.tw/issues-api/github/)[.t](http://hack.g0v.tw/issues-api/github/)[w](http://hack.g0v.tw/issues-api/github/)[/](http://hack.g0v.tw/issues-api/github/)[i](http://hack.g0v.tw/issues-api/github/)[s](http://hack.g0v.tw/issues-api/github/)[s](http://hack.g0v.tw/issues-api/github/)[u](http://hack.g0v.tw/issues-api/github/)[e](http://hack.g0v.tw/issues-api/github/)[s](http://hack.g0v.tw/issues-api/github/)[-](http://hack.g0v.tw/issues-api/github/)[a](http://hack.g0v.tw/issues-api/github/)[p](http://hack.g0v.tw/issues-api/github/)[i](http://hack.g0v.tw/issues-api/github/)[/](http://hack.g0v.tw/issues-api/github/)[g](http://hack.g0v.tw/issues-api/github/)[i](http://hack.g0v.tw/issues-api/github/)[t](http://hack.g0v.tw/issues-api/github/)[h](http://hack.g0v.tw/issues-api/github/)[u](http://hack.g0v.tw/issues-api/github/)[b](http://hack.g0v.tw/issues-api/github/)[/](http://hack.g0v.tw/issues-api/github/)  [https://a](https://api.github.com/)[p](https://api.github.com/)[i](https://api.github.com/)[.g](https://api.github.com/)[i](https://api.github.com/)[t](https://api.github.com/)[h](https://api.github.com/)[u](https://api.github.com/)[b](https://api.github.com/)[.c](https://api.github.com/)[o](https://api.github.com/)[m](https://api.github.com/)[/](https://api.github.com/)
> [name=Jeff H]

> 要注意 same-origin policy，同樣放在 hack.g0v.tw 比較方便
> [name=Jeff H]

> 目前 hack.g0v.tw 是 gh-pages 上的純 static 頁面，所以 api endpoint header 記得上 CORS 就可以了
> [name=Chia-liang K]

> 未來可能會有其他 issues backend，所以要多一層 /github/
> [name=Jeff H]

> 在 irc 上的討論有提到，目前主要會慢的地方在於多個 repo 必須發多個 api requests 才能拿到資料，所以單純的 proxy 仍然沒辦法解決這個速度的問題。我現在仍傾向建議做一個特殊的 repo 負責 aggregate 所有 repo 的 issues 這個方法。這個方法可以跟 proxy 機制 decouple 開，沒有 proxy 仍然可以運作。
> [name=Jeff H]

> 我可以嘗試看看用 proxy 做到這個功能 (也許得寫 ATS plugin.)
> [name=isacl]


### proxy settings

ATS (Apache Traffic Server) 的設定初步搞定，關於上面討論的 hostname 與路徑，都是小改，隨時可以調整。現在這台可以暫時先給大家開發實驗用。
現在 ATS 的設定如下：
- **in remap.config**
    map [http://utcr.org:8080/](http://utcr.org:8080/)  [https://api.github.com:443/](https://api.github.com:443/) @plugin=regex\_remap.so @pparam=/etc/regex\_remap.conf
- **in /etc/regex_remap.conf** (強制將 request 利用 proxy 帶 github application id 與 secret)
    ^/.*$ [https://api.github.com/$P?client_id=](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[X](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[X](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[X](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[&](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[c](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[l](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[i](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[e](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[n](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[t](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[_](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[s](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[e](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[c](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[r](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[e](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[t](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[=](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[Y](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[Y](https://api.github.com/$P?client_id=XXX&client_secret=YYY)[Y](https://api.github.com/$P?client_id=XXX&client_secret=YYY)
- **in record.conf**
    - CONFIG proxy.config.http.server_ports STRING 8080
    - CONFIG proxy.config.reverse_proxy.enabled INT 1
    - CONFIG proxy.config.url\_remap.pristine\_host_hdr INT 0 # 這設定是讓 http header Host 要改用 api.github.com (不要用原始 request 的 host), 否則會被 github API server 吐 404
- **in plugin.config**
    - header_filter.so @pparam=/etc/hdr_filters.conf
- **in /etc/hdr_filters.conf**
        \# 在 response 加上 Access-Control-Allow-Origin: *
        \[SEND\_RESPONSE\_HDR\]
        Access-Control-Allow-Origin =*=

註：尚未設定 cache, (目前 browser 看到的 302 Not Modified 是來自 github ) 但利用 proxy 去 append query string, 帶上 client\_id 與 client\_secret, 因此可以達到 5000 request per hour 了。（如果還是不夠用，再來設 cache）

Demo server: [http://u](http://utcr.org:8080/)[t](http://utcr.org:8080/)[c](http://utcr.org:8080/)[r.o](http://utcr.org:8080/)[r](http://utcr.org:8080/)[g](http://utcr.org:8080/)[:8](http://utcr.org:8080/)[0](http://utcr.org:8080/)[8](http://utcr.org:8080/)[0](http://utcr.org:8080/)[/](http://utcr.org:8080/)
- 看目前的 rate_limit  [http://utcr.org:8080/r](http://utcr.org:8080/rate_limit)[a](http://utcr.org:8080/rate_limit)[t](http://utcr.org:8080/rate_limit)[e](http://utcr.org:8080/rate_limit)[_](http://utcr.org:8080/rate_limit)[l](http://utcr.org:8080/rate_limit)[i](http://utcr.org:8080/rate_limit)[m](http://utcr.org:8080/rate_limit)[i](http://utcr.org:8080/rate_limit)[t](http://utcr.org:8080/rate_limit)
- 撈 issue [http://utcr.org:8080/repos/g0v/hack.g0v.tw/issues](http://utcr.org:8080/repos/g0v/hack.g0v.tw/issues)
- 看共有哪些 API (hostname 要自己改掉，並加 :8080): [http://utcr.org:8080/](http://utcr.org:8080/)
> 回報：成功使用，速度還不錯。(該頁慢的東西多的是。:-p) 
> [name=Jeff H]

> Cool! (這台 ram 只有 256 MB, 萬一開發階段爛掉請再 ping 我吧)
> [name=isacl]

> 跨 repo 一次拿全部 issues 的 API 我再想想辦法.
> [name=isacl]

> 因為做了分頁，再加上 incremental 一個 repo 一個 repo 拿，所以就算個別抓比較慢，其實也看不出來。所以跨 repo 一次拿全部 issues 這件事我覺得可以不急著做。
> [name=Jeff H]

> Got it.
> [name=isacl]

## 整理目前 github issue 遇到的問題：

- Also affect
    - 22:40 < hychen> 沒有also affect 這種功能
    - 22:40 < hychen> github上的issue 只有一層, 他沒有辦法做一個bug also affect to multiple projects
> 若有需要，我們可以約定某些特殊格式，寫在 issue body 裡。例如：see:kuansim#16、affects:kuansim。
> [name=Jeff H]

> 另一種做法是，約定好 project name 當 tag 時，即代表 bug also affects。這樣剛好跟上面的設計符合，project name 亦是 tag 的一種。
> [name=Jeff H]

> 這邊有一些有用的東西，也許可以幫助做跨 project link [https://help.github.com/articles/github-flavored-markdown#references](https://help.github.com/articles/github-flavored-markdown#references)
> [name=isacl]

> 看起來不錯，若 github 有規定的 syntax 我們應盡量遵循。
> [name=Jeff H]

> [https://github.com/rauhryan/huboard](https://github.com/rauhryan/huboard) 這好酷，似乎可以 link 不同 repo 的 issue 到同一個 kanban board 上。但我不是 g0v owner, 剛剛讀 g0v 時，是空的。暫時無法測試效果。
> [name=isacl]

> clkao: 我稍微用過.. cross repo 還是不大好用
> [name=isacl]



##    TODOs

- 功能補全
    - ~Github OAuth. (for updating issues) =>~ 暫時不做
    - 關注 (users with github account)
    - 回覆「我要做這個」(users with/without github account.)
    - Filter by labels
    - IndexedDB (不需要每次重新 parse json.) / Or use backend to cache issues.
    - Move pages into hack.g0v.tw
    - ~Fetch issues from backend and store to DB~ =\> Use proxy instead
- 其他加值功能
    - ircbot 有新的特定 label issue, 發到 irc.

##    資料呈現:

- Prototype demo (純用前端 js 抓 issue 下來): [http://utcr.org/g0v-issue-tracker/](http://utcr.org/g0v-issue-tracker/)
> 抱歉因為最新的版本在測 github 的 oauth, 因此會被導到 github 輸入帳號密碼。不是釣魚 XD
> [name=isacl]


##    Code (Prototype)

- 純用前端 fetch github API (oAuth supported)
    - [https://github.com/youchenlee/g0v-issue-tracker](https://github.com/youchenlee/g0v-issue-tracker)
- 未來為了有更多應用，應該要用後端抓 issue

##    使用情境:   (暫定)

-    Scenario 1: User 無 github 帳號，為翻譯人員
    - 新手在「如何參與 g0v」頁面，看到 tasks 列表
    - 以 「新手」+「翻譯」做 filter
    - 選定一個 task, 點入查看內容
    - 點選「我要參與」並留言
    - Update 回 github 的 project issue (? How)
        - 以 github  bot 回 comment (user 沒 github account)




##    Reference:

- Github API: [http://developer.github.com/v3/issues/](http://developer.github.com/v3/issues/)
- 取得所有 g0v repository
    - curl  [https://api.github.com/orgs/g0v/repos](https://api.github.com/orgs/g0v/repos)
- 取得單一 repository 的 issues
    - curl  [https://api.github.com/repos/g0v/hack.g0v.tw/issues](https://api.github.com/repos/g0v/hack.g0v.tw/issues)  (以 hack.g0v.tw 為例)
- API Clients:
    - [http://developer.github.com/v3/libraries/](http://developer.github.com/v3/libraries/)
- 註：Github API 限制
    - [http://developer.github.com/v3/](http://developer.github.com/v3/#rate-limiting)[#rate](https://g0v.hackpad.tw/ep/search/?q=%23rate&via=1ngNLPX3mLr)[-limiting](http://developer.github.com/v3/#rate-limiting)
    - 沒有過 oAuth, 一小時只能打 60 次




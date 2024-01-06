---
title: "\"選票成份分析 - g0v.hackpad.tw\""
tags: hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/YpOT9vjLthf)

選票成份分析

- 6/21 第九次黑客松issue
    - 個人對議題的評分紀錄與首頁與議題頁的評分結果不一致
    - 立委列表由大頭照改為接近列表表示
    - [個人議題頁](http://dev-congress-vote-analytics.herokuapp.com/me/issue-score) 連結到議題失效
    - 議題內頁下方的政治人物列表不應可以評分
    - 議題頁下方政治人物超連結可到
        - 該政治人物頁
        - 該政治人物與這個議題相關的新聞頁，此處才可決定此立委的立場
    - 新聞列表增加議題或政治人物TAG，可以根據TAG篩選新聞
    - 政治人物列表改列表示，排序加上立場排序


- 相關專案
    - 選票成分分析 [http://congress-vote-analytics.herokuapp.com/](http://congress-vote-analytics.herokuapp.com/)
    - 立法院風雲榜
    - 立委投票指南 [http://twly.herokuapp.com/legislator/about/](http://twly.herokuapp.com/legislator/about/)
    - 零時政府立院報你知 [http://ly.g0v.tw/debates](http://ly.g0v.tw/debates)
- 平台
    - Web - [http://congress-vote-analytics.herokuapp.com/](http://congress-vote-analytics.herokuapp.com/)
    - FB Club - [https://www.facebook.com/groups/VAgroups/](https://www.facebook.com/groups/VAgroups/)
    - FB Fans - [https://www.facebook.com/VotesAnalysis](https://www.facebook.com/VotesAnalysis)
    - Hackpadfoldr - [http://hack.g0v.tw/VotesAnalysis](http://hack.g0v.tw/VotesAnalysis)
    - Github
        - Organize - [https://github.com/g0v-tw-congress-vote-analytics](https://github.com/g0v-tw-congress-vote-analytics)
        - (NEW)laravel [https://github.com/g0v/congress-vote-analytics](https://github.com/g0v/congress-vote-analytics)
        - Reop
            - [Alpha](https://github.com/g0v-tw-congress-vote-analytics/congress-vote-analytics-alpha) \- bater所製DEMO版
            - [Beta](https://github.com/g0v-tw-congress-vote-analytics/congress-vote-analytics-beta) \- Fntsrlike用Framework所重製的版本。
            - [laravel](https://github.com/g0v/congress-vote-analytics) \- fukuball用laravel所重構的版本。
    - 樣式\- [http://dl.dropboxusercontent.com/u/66596502/VA/next.html](http://dl.dropboxusercontent.com/u/66596502/VA/next.html)
- 參考資料
    - Google Folder - [https://drive.google.com/?authuser=0#folders/0B56l5cDN19BhX280TkhoaEtKTUU](https://drive.google.com/?authuser=0#folders/0B56l5cDN19BhX280TkhoaEtKTUU)
    - 中研院斷詞系統：
        - 帳號: VotesAnalysis
        - 密碼: votesanalysis
        - Server IP: 140.109.19.104
        - Port: 1501
        - 此為簡單版本！
- 分工
    - Jimmy - 爬新聞。Source: 各大新聞網站。
    - [Fntsrlike（若虛）](https://github.com/fntsrlike) \- PHP Framework, Facebook Login
    - bater 補功能 SQL





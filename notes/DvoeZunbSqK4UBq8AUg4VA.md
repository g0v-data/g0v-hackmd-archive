---
tags: disinfo, disinfothon
---
# disinf1thon 第壹次不實訊息松

- 時間：2020/2/23 (Sunday) 2-6pm?
- 地點：線上協作
- Hangout: https://hangouts.google.com/call/hlyOQ7-icWBVu58MnoUkAEEM

## 2pm 提案
:::info
歡迎偷跑 :raised_hands: 在這裡加上自己的提案嘿
:::

### 【提案範例】web-based data explorer
提案人：chihao
提案簡介：我想用 0archive 目前爬到的一些資料，用 vue.js / nuxt.js 寫一個簡單的 web-based 資料探索介面。

### 【提案】mobile-based facebook article reporter
提案人：bruce
提案簡介：我想利用 iOS 的捷徑功能，寫一個能擷取 iphone 上當前瀏覽的 facebook 文章的url 到雲端的捷徑工具。

### 【提案】a dashboard to monitor daily crawling process 
提案人：wenyi
提案簡介：我想要寫一個可以監測crawling process過去『一小時&一天』每一個site新增的文章數。希望可以有歷史線圖(e.g. 過去30天內每天所新增的文章數，可以分成各site & 總數）、還有當有site有遠低於歷史數據時的顏色提醒。

### 【提案】不實訊息傳播
提案人：wenyi
提案簡介：我想要拿一些已知的不實訊息（從事實查核基金會、Cofacts、蘭姆酒吐司等來源），去我們的db找看看有沒有，試圖在我們有的資料內建立其中一或多則不實訊息傳播的方向。

### 【提案】標題的分析嘗試 - 壹
提案人：wenyi
提案簡介：我想要使用n-grams做現有db內新聞標題的topic modeling，看效果如何。理想是可以做一個像這樣的[報導](https://pudding.cool/2018/12/countries/)，國旗可以改成人物、事件，在較短的時間間隔內（一天、一週）。

### 【提案】標題的分析嘗試 - 貳
提案人：wenyi
提案簡介：我想要做一個可以把標題拆解成名詞、動詞、形容詞的工具作為未來分析的基石。可能可以用來輔助的資料 https://github.com/irvin/moe-common-phrases-of-zhtw/tree/master/2011-2015/csv

Ronny
- ElasticSearch
- snapshot 一個月一個 table？
- 最新版本自己一個 table？

## 2:30pm 自我介紹
:::info
在這裡簽到 :raised_hands: 
:::

| 暱稱 | 介紹 |
| --- | --- |
| chihao | 我不是 PM、0archive、g0v 社群國際交流 |
| ronny | 工程師、蠻喜歡爬資料的、健身環是好物已經瘦了 10kg |
| bruce | fb 爬蟲 |
| A-Bow | 來自內地南投、平面設計師、想轉職前端，學了 7-8 月，最近開始比較多線上參與的小松，就來試試看 |
| pm5 | ... |

## 3pm Hacking
:::info
歡迎加入 g0v Slack #disinfo 頻道，一邊討論一邊 hacking！
由此加入 →→→ https://join.g0v.tw ←←← 由此加入
:::

可以用這裡記錄，或者開新的 HackMD，記得把連結貼到這裡。

## 5:30pm 成果報告
- pm5
    - run update snapshot 1500/hr
    - now
        - 60k article 1 snapshot
        - 30k articles 2 snapshots
        - 10k articles 3+ snapshots
- bruce
    - shortcut: https://www.icloud.com/shortcuts/68ef27c43cea4f1c89d87e47f6a225d7
    - reported: https://airtable.com/shrkHkTOjiggYlhJs
    - 最佳化
        - 可選填理由
        - 補自動截圖
        - 網頁上傳後自己關掉網頁
    - 問題
        - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_46a4385e41db023da51f641434e8f6c4 =50%x)
    - ronny 建議考慮 fb messenger bot
- ronny
    - alter 40+GB table
    - compress 設定從 phpmyadmin 消失了！？
    - tainan 除了 ArticleSnapshot 以外都已經 mb4 了
    - taoyuan 還沒

---
title: "g1v work items"
tags: hackpad
---

# g1v work items

> [點此觀看原始內容](https://g0v.hackpad.tw/ewwARXN8iyi)


repo: [https://github.com/g0v/ivod.ly.g0v.tw](https://github.com/g0v/ivod.ly.g0v.tw)
demo site: [http://ivod.ly.g0v.tw/](http://ivod.ly.g0v.tw/)


### 留言板


先去睡了，看大家收工做到哪再來接，有空順便想一下下面的 demo plan - clkao
我最後將render-stats 接上實際的data queue, 不過還沒做到實際live的狀況
另外offset還是有些要搞清楚的地方, 要把live 跟影片都可以用彈幕, 要去睡了commit還輸高村長兩個commit數, 扼腕 orz..

## 功能

danmaku
- player integration
    - calculate offset
- aggregated analysis

live broadcast integration
- status flag
- stream offset
- seekable stream

player enhancement
- permalink for timecoded clips
- context for individual clip

video browse, search
- by committee

Featured Actor


gamification
- live score
- rank


nice to have:

context reference link
- debates metadata
    - [http://api.ly.g0v.tw/v0/collections/debates?q=](http://api.ly.g0v.tw/v0/collections/debates?q=){%22date_asked%22:%222012-11-9%22}
Yahoo DEMO 登記頁面:
[http://hacks.developer.yahoo.com/hacks/yahoo-hack-taiwan/event_17](http://hacks.developer.yahoo.com/hacks/yahoo-hack-taiwan/event_17)



## demo plan

- ivod api, improved usability for both archived and live streams
    - quickly seek to where things are happening
    - view related info (bills, reports, debates topic)
    - view all committees at a glance

- sometimes you get bored watching them talking nonsenses, you can turn on danmaku and special items
    - how it looks like
    - stats

firebase usage
- timed comment on firebase
    - per video room
        - meta data
            - video id
        - content entry
            - timestamp
            - text
            - created_by
            - created_at
            - style-info
        - action entry
            - timestamp
            - type
            - for_whom
            - {x,y}
            - created_by
            - created_at
        / videos / :vid ...
        danmaku\[\]
        metadata
        stats
```
                        total
```
    shoe  egg melon raise-net: white-banner: flower: boat duck
```
                        queue

```
    / stats / by\_xxx\_rank
```
            /legistor/:lid

```
報告腳本

1min
立法院議程有錄影、有即時轉播、有公開影音檔，但沒人要看…等新聞出來再罵也沒用了
立院影城使用前 \- 播放一段枯燥無味的影片
立院影城使用後 \- live demo
- 講解如何即時表達自己的不滿 \- demo 丟東西
- 講解可以丟什麼東西 \- demo 各種被丟出的垃圾類型
- 不只可以自己丟，還可以跟大家一起丟 \- demo social 功能，多人同時丟東西
- 看到自己支持的立委被丟，可以和酸民對戰 \- demo 護航防禦功能
- 戰完以後可以看對戰成果，還可以找其他熱門影片來戰
為什麼要做這麼多有的沒的功能呢？其實 kuso 的背後有我們的用心良苦，透過互動電影院，立法院會議議程變得比正規電影還好看，在不知不覺間，引導公民看完超長時間立院議事過程，促使更多人關心重大的議題，提升台灣人的公民素養～～～～
- 影片頁可以連結到 ly.g0v.tw 上的會議頁來看議案資訊還有法案 diff (正經)
> 到時看看能否有個多人線上遊戲的視覺模式，呈現出公民們組團打怪（怪=立委）的情況。<--簡單說，但背後其實有些比較嚴肅的研究--
> [name=Michael_Li]


1min
這個偉大的專案是如何做到的呢？（技術說明）
- 立院影音資料從哪來 \- demo 立院官網影音頁面
- 官網影片的問題 \- 只有三個月、格式 blahblah、瀏覽器 blahblah
- 所以我們做了… blahblah
- 後端 blahblah

20 sec
未來可以延伸出：
- 影音 timestamp 與公報紀錄對應，找出被丟的立委，以便進一步做巨星排行榜，當作選民投票的參考
- 辨識質詢分割畫面左右半的出演人員，以便根據準星位置判斷被丟的人到底是誰
- 建立玩家的成就系統，增加影城的黏力
- 更豐富的彈幕特效，提供付費管道讓使用者購買特殊道具來丟
    - 道具舉例：丟紅蛋、丟皮蛋、丟壞蛋、丟臉、丟人
    - 被丟特殊道具後，該影片/立委/官員可以解開新的成就


### 登錄資訊

[http://hacks.developer.yahoo.com/hack/yahoo-hack-tai](http://hacks.developer.yahoo.com/hack/yahoo-hack-taixwan/congr)[x](http://hacks.developer.yahoo.com/hack/yahoo-hack-taixwan/congr)[wan/congr](http://hacks.developer.yahoo.com/hack/yahoo-hack-taixwan/congr)
[ess-cinema-/event\_17/hack\_995](http://hacks.developer.yahoo.com/hack/yahoo-hack-taiwan/congress-cinema-/event_17/hack_995)

> Name of Hack*
> [name=ET B]

Congress Cinema 立院影城

> Description*
> [name=ET B]

Video records of congress used to be boring. Yet they are not anymore-- with congress cinema, watching over our congress will be funner than ever.
立法院的影音紀錄既枯燥、又冗長。現在，有了立院影城，在家監督國會比出門看電影有趣萬倍。

> Event*
> [name=ET B]

Yahoo Hack Taiwan

> Category*
> [name=ET B]

Media / Social

> Hack URL
> [name=ET B]

[ivod.ly.g0v.tw](https://github.com/g0v/ivod.ly.g0v.tw)

> Hack Screenshot/Picture
> [name=ET B]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_11d714b674775ea0c5d0a869d7ea8f81)
[http://i.imgur.com/GMHsUXp.jpg](http://i.imgur.com/GMHsUXp.jpg)
> Hack Screencast
> [name=ET B]


> Technologies Used
> [name=ET B]

Youtube API, api-beta.ly.g0v.tw, firebase, raphaeljs, semantic-ui, angularjs

> Tags (Separate each tag with a comma)
> [name=ET B]

open congress, open data, firebase, danmaku,

> Source code URL
> [name=ET B]

[https://github.com/g0v/ivod.ly.g0v.tw](https://github.com/g0v/ivod.ly.g0v.tw)



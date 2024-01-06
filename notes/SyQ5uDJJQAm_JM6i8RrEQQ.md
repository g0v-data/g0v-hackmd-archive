---
title: "動民主 2.0 殘而不廢敏捷開發計畫"
tags: hackpad
---

# 動民主 2.0 殘而不廢敏捷開發計畫

> [點此觀看原始內容](https://g0v.hackpad.tw/A8UlpEbKfK2)


tkirby, ETBlue @ 12/25 hackad0n

目標：讓動民主 2.0 快速上線
> 有沒有可能比 airesis 中文版快呢？讓我們繼續看下去… XD
> [name=ET B]

作法：第一階段只挑最常用功能——提案來實做
架構： [https://docs.google.com/drawings/d/1bT0YU73SmM0eIReod5Gmhv30l8TN74v8-WYv69hVoCg/edit](https://docs.google.com/drawings/d/1bT0YU73SmM0eIReod5Gmhv30l8TN74v8-WYv69hVoCg/edit)
[http://g0v.github.io/don-republic/public/index.html](http://g0v.github.io/don-republic/public/index.html)

to-do
- [ ] 完成架構圖
- [ ] UI 改成只有提案功能版
    - [ ] 註冊頁
        - 以 twitter/github/google/facebook登入
        - ~選擇所屬社群~
> 請各社群/團體的人自己上來開groups
> [name=ET B]

        - 選擇專長標籤
        - 選擇興趣標籤
> 內建標籤要去哪兒砍木材好？ans: 列清單給神斧榮尼
> [name=ET B]

        - 選擇追蹤對象
    - [ ] 導覽列
        - 首頁（時間軸）
        - 提案列表
        - 標籤列表
        - 搜尋
        - 通知
        - 帳號與設定
    - [ ] 首頁（=個人化時間軸）
        - 版面組成
            - 側邊欄
                - 我
                - 時間軸
                - 我的訂閱
                    - 標籤
                    - 提案
                - 我的追蹤對象
                - 我的群組
            - 主要區塊
                - 時間軸
        - 顯示內容
            - 簡介 in 提案
            - 便利貼 in 提案
            - 方案 in 提案
            - 決議 in 提案
        - 顯示規則
            - 符合你的專長…
            - 符合你訂閱/收藏的標籤…
            - 你正在追蹤的人也對這個感興趣…
            - 和你屬於同群組的人也對這個感興趣…
> 優先顯示以上範圍中交集較多的
> [name=ET B]

    - [ ] 提案列表/使用者列表/群組列表…暫時不管 lol
    - [ ] 新提案
        - 設定選項
            - 是否包括便利貼系統
                - 需要腦力激盪的複雜大型提案可以包含便利貼
                - 小型提案可以單純用 etherpad 共筆
            - 是否需要投票表決
                - 參與人數多時可以開啟投票功能以利統計
                    - 開啟投票功能時，需設定成案門檻，門檻有預設值，見下面套餐
                - 參與人數少時可以不開啟投票功能，單純在討論過程中形成決議
> 就是比較方便寫共筆的 loomio…XD
> [name=ET B]

> 這種時候其實大概用 hackpad 就好惹，動民主原本不是設計來這樣用的…（抓頭）不過搞不好用一用會有意外發現（？）
> [name=ET B]

            - 時程
                - 指定時程
                    - 討論期 _ 天
                    - 底定期 _ 天、投票期 _ 天（如果有投票的話）
                    - deadline  _ 月 _ 日
                - 排入每月定期表決
                - 無時程，it's done when it's done
            - 協作權限
                - 誰可以瀏覽
                    - 所有人
                    - 我選擇的人 (指定個人 / 群組)
                - 誰可以留言提出建議
                    - 所有合格公民 (level1 以上)
                    - 我選擇的人 (指定個人 / 群組)
                - 誰可以參與
                    - 所有合格公民 (level1 以上)
                    - 我選擇的人 (指定個人 / 群組)
                - 誰可以管理提案
                    - 所有合格公民 (level1 以上)
                    - 我選擇的人 (指定個人 / 群組)
                    - 只有我
        - [ ] 設定套餐
            - 正式，適合群眾參與、需要同時做民意調查的大型提案，例如「能源政策規劃」「都市更新政策規劃」等
                - 有 etherpad
                - 有便利貼
                - 要投票，預設值：
                    - 便利貼的贊同率 5% 才算有效
                    - 方案的有效便利貼覆蓋率 30% 才算成案
                    - 表決的有效投票率 30% 才算通過
> _以上預設數字亂抓的可以改_
> [name=ET B]

                - 不指定時程，待通過門檻後排入下次定期投票
                - public（所有合格公民皆可瀏覽、留言、投票、管理）
            - 非正式，適合多人參與、但不需要民意統計的中型提案，例如「政府 IT 委外計畫採用 open source 模式建議案」
                - 有 etherpad
                - 有便利貼
                - 不用投票
                    - 便利貼仍可打勾或打叉，但統計數字僅供參考，沒有正式效力
                - 不指定時程
                - public（所有合格公民皆可瀏覽、留言、投票、管理）
            - 簡易，適合少人參與的小型提案，例如「歪來歪去婚友跨年派對」等
                - 有 etherpad
                - 沒有便利貼
                - 不用投票
                - 不指定時程
                - public（所有合格公民皆可瀏覽、留言、投票、管理）
            - 自訂：隨便選上面一套來改
    - [ ] 新方案
        - 設定
            - 協作權限
                - 誰可以共同編輯方案
                    - 所有可參與提案的人
                    - 在所有可參與提案的人之中，指定我選擇的人 (指定個人 / 群組)
                    - 只有我
                - 誰可以修改方案權限
                    - 在所有可參與提案的人之中，指定我選擇的人 (指定個人 / 群組)
                    - 只有我
    - [ ] 提案頁
        - 管理者畫面
            -
        - 使用者畫面
            - 引言/簡介 intro (etherpad)
                - 這整件事情是怎麼來的、要往哪去
                - 這個提案想要達到的願景是什麼
                    - 可引入便利貼
                - 現在有哪些方案了
                    - 系統自動列出
                    - 可直接快速投票
                    - 可點進去看細節
                - 現在進行到哪裡了
                    - pchome 送貨 progress bar
                - 問題與建議
                    - 留言板
            - 腦力激盪 (stickers)
                - 想實現的願景
                - 為了實現願景所要解決的問題
                - 問題的成因
                - 針對問題成因的對策
            - 規劃
                - 方案
                    - 章節
                        - 內容

### temp

use case:
- 議題 issue - 收集資料、探索
    - 健康與醫療資料的加值應用公民論壇
    - 服貿協議公聽會
- 提案 proposal - 分析、規劃
    - 政策性
        - hychen 的 政府 IT 委外 open source 建議案
    - 法規性
        - 多元成家修法案

ui:
- reference 方式
    - [http://synapse.koreamed.org/DOIx.php?id=10.4111/kju.2013.54.4.244&vmode=PUBREADER](http://synapse.koreamed.org/DOIx.php?id=10.4111/kju.2013.54.4.244&vmode=PUBREADER)
    - [http://www.readcube.com/articles/10.1038/nrurol.2011.78](http://www.readcube.com/articles/10.1038/nrurol.2011.78)

\-\-\-\-
彈性

管理員決定是否有便利貼門檻、是否需要投票…etc.
config
哪些便利貼要納入評分
多少算valid
管理員第一個畫面：dashboard（給管理員）
1.列出方案
2.有地方可以問問題
3.stickers佔一個區塊

給一般人：
1.這是幹嘛的-引言、來龍去脈、問問題
2.我能幹嘛？-弄幾個方案，可以發問或提起方案
方案跟引言可以放在一起、想要達到的願景可引入intro
可以直接投票
細看：提案
從方案的話會倒過來

如果提案有時程，要用ui step標註現在在哪裡…

user timeline
註冊時選擇社群、該社群熱門類別、塞入timeline
用顏色標分類、時間排序

一般人可以看所有提案
一般人看單一提案
管理員看單一提案
提案發起、編輯頁面

指令
```
node_modules\\.bin\\lsc server.ls

```
排名式投票計算方式: _schulze method_
    [http://en.wikipedia.org/wiki/Schulze_method](http://en.wikipedia.org/wiki/Schulze_method)
javascript example:
    [http://bram.gotink.me/Schulze/](http://bram.gotink.me/Schulze/)
    [https://](https://github.com/bgotink/Schulze/blob/gh-pages/js/schulze.js)  [hub.com/bgotink/Schulze/blob/gh-pages/js/schulze.js](https://github.com/bgotink/Schulze/blob/gh-pages/js/schulze.js)

firebase 資料關連討論
    [http://logbot.g0v.tw/channel/g0v.tw/2014-01-11#315](http://logbot.g0v.tw/channel/g0v.tw/2014-01-11#315)
    [au](http://logbot.g0v.tw/channel/g0v.tw/2014-01-11/321)ETBlue: 對 firebase 因為沒有 join 的關係，所以需要超展開。術語叫 denormalization
    [au](http://logbot.g0v.tw/channel/g0v.tw/2014-01-11/323)cf.: [https://www.firebase.com/blog/2013-04-12-denormalizing-is-normal.html](https://www.firebase.com/blog/2013-04-12-denormalizing-is-normal.html)
    [**au**](https://www.irccloud.com/#!/ircs://irc.freenode.net:6697/au)\> 如果要很講究, 可以用 [https://www.firebase.com/docs/javascript/firebase/transaction.html](https://www.firebase.com/docs/javascript/firebase/transaction.html)
    [au](http://logbot.g0v.tw/channel/g0v.tw/2014-01-11/354)ETBlue: 之後有時間 polish 時再換到 poga clkao 等人寫的 firebase clone 並且敦促他們加上自動 normalize 的功能就好了 XD

共筆：firepad [http://www.firepad.io/](http://www.firepad.io/)


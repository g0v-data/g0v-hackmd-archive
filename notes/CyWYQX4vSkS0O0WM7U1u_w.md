---
title: "使用者回饋自動化，暨 QAbot 養成技能樹"
tags: 廣宣團,hackpad
---

# 使用者回饋自動化，暨 QAbot 養成技能樹

> [點此觀看原始內容](https://g0v.hackpad.tw/T1sSifx2RvA)

> 肚子好餓，先把相關的 [IRC log](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06#319) 貼過來再整理
> [name=venev]


## IRC 會議記錄（待整理）

[Bropheus_](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/319)
- venev 讓我看了昨天粉絲專頁小幫手的討論，關於網友提建議（幫 pm2.5、pm10 加上意義說明）這點...
- 有沒有可以**把開 github issue 的功能，整合到專案成果網頁裡的方法**啊？類似scrollback 把 irc channel 嵌到網頁右下方那樣...
- 我剛剛從 [http://g0v.github.io/twgeojson/air.html](http://g0v.github.io/twgeojson/air.html) 開始去找，根本找不到 github 或其它建議回報處
- 想說這應該要有個好解法，所有專案都可以用
[jimyhuang](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/323) Bropheus: 意思是說，多一個button，按下去就去開issue?
[Bropheus](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/324)（是說從網頁畫面找，看網址列去 github page 再進 issue，對 end user 來說不太可能 XD）
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/325) 因為即使已經進到 g0v 的 github 想發 issue，但各專案入口名稱並不直覺。像這次是因為網址內有 twgeojson，所以我才找得到
[Bropheus](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/326) jimmyhuang: 對，類似這樣的東西。像 Bookshow.tw 是直接掛 zopim 線上客服，再人工處理
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/328) jimyhuang: 也不一定要人工處理啦，**在專案網頁，點下「回報、建議」按鈕，直接連到該 github new issue，也是好方法**
[Bropheus](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/331) jimyhuang: 我自己覺得，**要盡量鼓勵人參與的話，右下角有個「下一步改進清單」之類的標示，一點就彈出所有 issue 和加 issue 的介面**，效果應該比較好
[jimyhuang](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/332) venev: Bropheus 其實是看各專案耶～**每個專案的「客服」程度不同** XD
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/334) 其實每次專案成果公布在臉書/G+後，都會有一些很好的回饋建議，但未必每次小幫手都有辦法人工處理
[Bropheus](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/335) jimyhuang: 對，不過 github issue 應該是公約數？如果是這樣的話，右下角直接彈開 issue 應該可行
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/337) jimyhuang: 所以最懶惰的方式應該是你一開始說的，按鈕按下去，直接連到該 github new issue 頁
[jimyhuang](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/338) Bropheus: venev 政誌前天改README後，今天就有人回報日期錯誤了... 但其實埋在右上角得「?」>「關於」>「link」
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/340) 好奇一下：各位專案開發者，**除了看 github issue 之外，最常能夠取得使用者回饋的管道是？**
[au](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/341) 萌典是 **twitter 最多，email 次之，然後 google play / ios store 有評分 review**
[yhsiang](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/342) 我也覺得 **email** 會是比較多的
[jimyhuang](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/344) 其實用 **github回報，之前有人反應過好宅... （看不懂、不想註冊、不想登入）**
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/345) jimyhuang: 我找到了 # 政誌回報錯誤新功能。因為在客服前台跟粉絲溝通久了，所以在思考如何將這種糾錯回報機制更自動化
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/347) jimyhuang: 對齁，差點忘記 github 還要註冊（原來我還是不夠不宅）
[Bropheus](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/348) 那**各專案的開發者群，習慣從哪裡找 issue 開始作呢？**剛剛說 email 是所有開發者都可以看到？還是有人丟進 github issue 再讓開發者群看？諸如此類
[yhsiang](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/349)  [**https://zapier.com/zapbook/github/uservoice/**](https://zapier.com/zapbook/github/uservoice/) # 有人用過嗎 XD
[au](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/351) Bropheus: **twitter/email/review 來的回應會經過 triage (檢錯分類) 流程，再分門別類丟進 github issues，並把 issue URL 提供給提交者 (就是 venev 在 fb 上做的程序)。開發者群的討論是在 github issues，如此比較不致處理重複、已修正，或不擬修正的問題。**
[yhsiang](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/353)  **也有 Create GitHub Issue from an Email**
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/354) au: 我看到萌典除了明顯的 twitter、google play / ios store 圖示，左下還有推文給萌典的捷徑文字框。這其實就很像直覺的客服系統了
[Bropheus](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/360) au++: 瞭解了，這是千手觀音工人智慧處理法 XD 但 jimyhuang 剛剛講到每個專案的客服程度不同也是關鍵，如果意見量還不大，純自動化有好的解法嗎？
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/362) yhsiang 講的 zapier 或許有方便解？
[jimyhuang](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/363) yhsiang: oh!!! 原來是**自動從 uservoice至github ...**
[au](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/364) 所以我負責**前台 (見** [**https://twitter.com/moedict**](https://twitter.com/moedict) **紀錄)，往 github issues 後台如果有重複或需要交叉索引時，kcwu 小精靈會默默完成** XD
[yhsiang](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/366) 就**阿宅依舊看github issue**
[au](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/367) uservoice -> github 感覺挺不錯，可以試試
[yhsiang](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/369) 然後看**做個範例 讓其他的project可以輕鬆套用 XD**
[yhsiang](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/370) 其實我昨天在洗澡的時候就是想弄github with trello XD
[yhsiang](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/371) zapier也有
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/375) 作為總舵門前掃地僧，如果使用者可以直接追到開發者家門口發 request，當然最好（翹腳）
[au](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/377) yhsiang: **common frontend utility script... 感覺可以和之前提的 Tabzilla 併坑**
[yhsiang](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/378) au: :D
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/380) 或許下次黑客松小講 yhsiang or kcwu 等可以**分享如何善用線上客服工具，取得專案 end user 回饋**？ # 推很大推不用錢
[Bropheus](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/381) 補充一下：我自己**作為提意見者，如果從網頁上要回報時，可以順便讓我看到別人的意見、處理狀況，參與動力會因此提高、持續**（丟完這次比較願意繼續關注）
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/386)（思考如何**由內向外推廣成果 \- 由外而內撈取回饋**，好像也算廣宣團使命之一 # communi-kon ）
[ETBlue](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/401) 同意專案網頁上可以加 github issue 頁的link，或許之後請 evenwu 直接做到 g0v tabzilla 裡面？就不用大家各自弄了
[ETBlue](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/404)不然要我另外找個地方塞那按鈕還真傷腦筋
[Bropheus](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/405) g0v tabzilla 是什麼？哪裡可以看~~
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/406) 感謝 evenwu 大大 # g0v tabzilla
[ETBlue](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/407) Bropheus: venev 是個還沒做的東西，**模仿這個** [**http://www.mozilla.org/en-US/**](http://www.mozilla.org/en-US/)
[ETBlue](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/409) Bropheus: venev 上面那個 mozilla 按下去會有整個 moz 的東西
[Bropheus](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/410) ETBlue: 原來如此~
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/411) ETBlue: 這個好！！
[ETBlue](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/412) 嗯不過話說回來………**最通用的客服管道應該還是 email 吧 XD 我自己則喜歡 twitter** ……雖然我沒啥東西可以客服的哈哈
[kcwu](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/416) venev: 我沒有在取得 end user 回饋耶 XD 我自己是萌典 end user, 自己發 issue 到 github XD
[kcwu](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/418) venev: 只是我有**在萌典的 github project 按 star, 所以別人發 issue 我會看到(email)**, 若我見過也許就去多嘴幾句
[ETBlue](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/419) 原來 kcwu 默默完成這麼多事情，真是低調的背景程式…… # 人形QA bot
[kcwu](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/428)  **uservoice 似乎比 github 容易讓人想發 request**
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/429) kcwu: 同意！
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/430) 剛看了一下萌典 twitter 和 github issue, 客服部的前端後勤做得真好 au kcwu++
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/432) 但有個小問題：我是 github user 也會發 issue，想對萌典提建議時，要發去 g0v 還是 audreyt 底下的萌典 repo ？ **\# 迷路**
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/433) 目前看起來是 audreyt 底下的 repo 有較多 issue. 還是其實沒差、都可以？
[au](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/435) venev: g0v/moedict-data-* 是資料上的 issue
[au](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/436) audreyt/moedict-webkit 是界面呈現上的 issue
[au](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/437) 兩邊都可以，**QAbot 會轉發**
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/438) 可惡！害我好想發起 QAbot 團購~
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/440)下次碰面來詢問 kcwu，有沒有**變身 QAbot 的相關技能樹**（例如熟悉專案功能架構......？）好了
[au](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/441)  **Triage skill tree** 可以參考 [https://wiki.mozilla.org/QA/Triage](https://wiki.mozilla.org/QA/Triage)
[au](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/442) (bbiab)
[venev](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/444) au++ 零時的學習不能等又有新內容了
[kcwu](http://logbot.g0v.tw/channel/g0v.tw/2014-01-06/447) 比較正式的 triage 會看 ticket description 決定是不是 bug,priority,assignee 之類的. 可是在 g0v, 沒有人負責修, 沒有人決定 priority... 所以其實 triage 沒什麼事做

## 動機

20140105 粉絲專頁小幫手討論，[網友對專案提改進建議](https://www.facebook.com/photo.php?fbid=650597644981525&set=a.456791061028852.107377.454607821247176&type=1&comment_id=2083968&offset=0&total_comments=12)（幫空污指標 pm2.5、pm10 加上意義說明）該如何回覆處理？
- 過去多半是「開發者或小幫手路過順便開 issue」，但......
    - 常有漏網之魚
    - 使用者無法產生協作參與感
    - 工人每次手動很累
- 要求使用者直接去 github 提 issue 太宅，要註冊、登入，對 end user 門檻高


## 可能解法

- 套用 zapier 功能 uservoice -> github？
- common frontend utility script 與 Tabzilla 併坑，讓各專案套用
- 培養 QAbots 作專案後勤：參考萌典客服系統前後台合作經驗
    - QAbot 可以從活躍 enduser 拉人
    - 前台負責真人回應建議，自開或引導使用者開 issue
    - use github star feature to follow project issues，跨 repos 作 triage

## feedback 介面符合使用者心理



## QAbot 養成參考

活體：諮詢 kcwu 實作流程撇步
文件：[https://wiki.mozilla.org/QA/Triage](https://wiki.mozilla.org/QA/Triage)


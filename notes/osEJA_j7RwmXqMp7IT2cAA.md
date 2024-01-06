---
title: "g0v irc  robot (by hubot)"
tags: hackpad
---

# g0v irc  robot (by hubot)

> [點此觀看原始內容](https://g0v.hackpad.tw/IBmzHC20wBb)

Repo: [https://github.com/g0v/b0t-hubot](https://github.com/g0v/b0t-hubot)
## Preface

g0v  irc channel 上現在已經有 logbot 和 kcwu 網站 title bot (人機一體)，然而當需要一個新的自動化功能時，大家往往重寫一隻新的 robot，並無一個共用的 robot framework。而且寫一個 irc bot 對於手邊沒有現成工具的人來說很花時間。

##  Why hubot?

###  1\. 架構完整

hubot  最初由 GitHub 開發而成（[http://hubot.github.com/](http://hubot.github.com/)），為 GitHub 公司內部使用的自動化 robot。

hubot 本身是一個以 node.js + coffeescript 寫成的 robot engine，架起來後，可以使用 command line 直接與 bot 互動。若再輔以各種網路通訊的 adaptor，則可透過網路將 robot 掛在線上。如 hubot-irc 即是 hubot 的 IRC adaptor，用來將 hubot  掛在 IRC。

### 2\. 功能擴充容易

開發 hubot 的功能，不需要知道 hubot 怎麼運作，只要在 scripts/ 資料夾內，使用 coffeescript (or livescript，需額外 plugin) 寫 nodejs 的 script，即可擴充 hubot 的功能。

例如以下的簡單範例：
```
module.exports = (robot) ->
  robot.respond /ping/i, (msg) ->
    msg.reply "pong"

```
### 3\. 已經有一大堆的 scripts 可擴充 robot 功能

[https://github.com/github/hubot-scripts](https://github.com/github/hubot-scripts)  #  hubot scripts 專案
[http://hubot-script-catalog.herokuapp.com/](http://hubot-script-catalog.herokuapp.com/)  \# 各種 scripts 的說明


## 功能發想 (挖坑)

- [**isacloud_**](https://www.irccloud.com/#!/ircs://irc.freenode.net:6697/isacloud_)\> 個人覺得現在資料夾分兩層(install 後把 scripts copy 進內層執行) 有點會讓人混淆，如果可以改成更簡單 run 也很不錯
- 隨意發想，g0v irc robot 想要些什麼功能呢？
> 自動查萌典、公司關係、執行範例 LiveScript XD
> [name=caasi H]

> (Y) 萌典+1
> [name=isacl]

> 執行範例 LiveScript 現在有什麼線上有 API 的服務嗎？
> [name=isacl]

> 靈感來源是 ECMABot: [https://github.com/oftn/oftn-bot/wiki/Guide-to-Ecmabot](https://github.com/oftn/oftn-bot/wiki/Guide-to-Ecmabot)
> [name=caasi H]

> 正在查有無 API 。
> [name=caasi H]

- 查詢萌典
- 查詢公司關係
- 隨機 g0v 語錄
- \[DONE\] 用 {user}/{repo}#{issue-id}  顯示 github issue.
- [x] 查詢 g0v 各專案條目簡介，[條目的API](http://g0v-communique-api.herokuapp.com/api/1.0/tags)，條目內容來自[這份文件](https://g0v.hackpad.com/Fe3VpeN42w9)，可以讓大家快速了解各專案進度或者跟新手介紹專案使用。
> +1
> [name=isacl]

- bot: give me a job => 就 random 推坑給他
> 不過很少人會講 give me a job <<<這句吧XDDD
> [name=lanfon]

> 也許 give somebody a job (me replace somebody)，再由bot reply(?
> [name=lanfon]

> good idea!
> [name=isacl]

- logbot 保母 - 偵測 logbot 動向，如果 logbot 離開頻道 10 分鐘還沒回來，就在頻道發出提醒「天這麼黑，風這麼大...」
- 在哪 bot
    - 15:14 <[tkirby](https://www.irccloud.com/#%21/chat.freenode.net:6667/tkirby)\> 從去年六月開始, 搜尋 "在哪" 一共有 293 個人講過... 應該來弄個 bot 看到"在哪"就撈撈看 log
    - 15:16 <[clkao](https://www.irccloud.com/#%21/chat.freenode.net:6667/clkao)\> tkirby 在哪？
    - 15:17 <[tkirby](https://www.irccloud.com/#%21/chat.freenode.net:6667/tkirby)\> 『< clkao> 上次那個 multiplayer 炸彈超人在哪裡？好想玩喔』
> 大家好我是 tkirbyW
> [name=Kirby W]

> hi
> [name=isacl]


## How To Start

hubot  與 hubot IRC Adaptor 所需的 packages 已經整理在 packages.json 內。

執行辦法：
1.  安裝並執行 redis-server (這個步驟可省略，請參考 [Pre-requirement](https://github.com/g0v/b0t-hubot/blob/master/README.md#pre-requirement)  )
2.  `git clone [https://github.com/g0v/b0t-hubot](https://github.com/g0v/b0t-hubot)[`](https://github.com/g0v/b0t-hubot)
3.  修改 \`env.sh\` 改掉 \`HUBOT\_IRC\_NICK\`，避免 IRC  上 nickname 重複
4.  `./install.sh && ./run.sh`

 跑起來之後，機器人預設會進到 freenode 的 #  g0v-b0t-test 這個頻道中，方便測試。
 p.s. 測試時建議將 scripts/ 裡面用不到的 script 移除，避免同個 channel 內，相同功能的 robot  互相打架搶生意。

 詳細說明可見：[README](https://github.com/g0v/b0t-hubot/blob/master/README.md)

##



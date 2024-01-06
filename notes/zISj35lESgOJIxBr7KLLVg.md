g0v slack app 申請機制
==============
Slack 免費版一個 workspace 只能裝 10 個 app ，雖然 slack 在 2020/3 起提供給 NGO 三個月免費專業版可以無上限，但是六月後仍會遇到 10 個 app 限制，這共筆主要想討論管理機制。

目前有的 App
-----------
* 已安裝
    * [GitHub Enterprise Server](https://g0v-tw.slack.com/apps/A0F7YS2SX-github-enterprise-server?next_id=0)
        * 目前好像是 summit 和 2020voting-guide 有用到
    * [Google Drive](https://g0v-tw.slack.com/services/BG7376L0Y)
        * 用在當有人分享 Google drive 連結時，透過某個帳號下載預覽
    * [Matterbridge](https://g0v-tw.slack.com/apps/AUZLG1D5G-matterbridge)
        * 2020/3/13 superbil 加的？
          pm5 在 #infras 提的「把 #hello-world 跟 Code for Japan Slack 的 #helloworld_ 串起來」，目前還在服務串接中的狀態
        * 結果是 patcon 用來做 general 頻道翻譯、 irc bridge 用的 app ， GitHub [在此](https://github.com/42wim/matterbridge)
        * 目前 IRC bridge 繼續用 [slack-irc-bridge](https://github.com/g0v/slack-irc-plugin) ，走 webhook ，和此 app 無關
    * [揪松小幫手 Jothon Helper](https://g0v-tw.slack.com/apps/ACSTZR2TB--jothon-helper)
        * https://intro.g0v.ronny.tw 和 https://g0v-slack-archive.g0v.ronny.tw 都是透過這隻 App 更新
* 等待同意中
    * [Pingdom](https://g0v-tw.slack.com/apps/A0F814AV7-pingdom) by k6-2  2020/3/30
        * “您好我是鄉民王敬豐 ，有用 pingdown 監控了幾個網站，可以申請 PINGDOWN 告警嗎 (我不會寫code QQ ，剛剛測試 https://zapier.com/ 也是要安裝 slack apps ) ”
    * [Github](https://g0v-tw.slack.com/apps/A8GBNUWU8-github) by mrorz 2020/3/27
        * “想要把 Cofacts 的 github activity 接到 #cofacts”
    * [Google calendar](https://g0v-tw.slack.com/apps/ADZ494LHY-google-calendar) by gaga 2020/3/21
        * Please
* 已關閉
    * [Geekbot](https://g0v-tw.slack.com/apps/A0H67RAG0-geekbot)
    * [Miro Feed](https://g0v-tw.slack.com/apps/A8VK125AS-miro-feed)
    * [Outline](https://g0v-tw.slack.com/apps/A0W3UMKBQ-outline)
    * [Quip](https://g0v-tw.slack.com/apps/A0M22HR1P-quip)
    * [Trello](https://g0v-tw.slack.com/apps/A074YH40Z-trello)
    * [Trello Alerts](https://g0v-tw.slack.com/apps/A0F814C4R-trello-alerts?next_id=0)

### 基礎松討論 2020/4/5

- 先同意申請中的（沒有違反宣言和COC的狀況下），慢慢討論機制，三個月後就會刪除
- 建立中繼 app，就需要投入開發資源 !
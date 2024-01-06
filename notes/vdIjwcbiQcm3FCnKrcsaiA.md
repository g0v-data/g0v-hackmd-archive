---
tags: bridge
---

# Adding Discord to g0v bridge

作為 Discord 管理員，要做的事情是

1. 在 Discord 照著 https://github.com/42wim/matterbridge/wiki/Discord-bot-setup 建立好 discord bot、拿到 token、設定 Privileged Gateway Intents、邀請 bot 進自己的 discord
    - 文中壞掉的圖可參考 https://github.com/reactiflux/discord-irc/wiki/Creating-a-discord-bot-&-getting-a-token ，申請 bot 的步驟一樣
2. 到 https://github.com/g0v/bridge/blob/fun/matterbridge.toml.template 發 PR 修改之，例子：https://github.com/g0v/bridge/pull/3/files
    1. 在 `[discord]` 下新增自己的 discord 區塊。
        - **Token 記得不要直接貼裡面**！取一個 variable 名字，另外到 `#bridge` 問 @pm5 要怎麼 pass 給他。
        - Server ID 就是自己 discord 的 `https://discord.com/channels/<這裡是 ID>/<這裡是 channel ID 不要管他>`
        - 其他諸如 `PreserveThreading` 等選項見 https://github.com/42wim/matterbridge/wiki/Section-Discord-%28basic%29 
    2. 在最下面，每一組要連在一起的 channel 就新增一個 ``[[gateway]]`` entry，設定連在一起的 ``[[gateway.inout]]``。
3. 在 g0v Slack 把 `@HelloWorld bot` 邀請到你要連動的 channel 中
4. `@pm5` merge PR 並放好 token 後，就連起來囉～
5. 歡迎至 g0v slakc #bridge 頻道討論執行細節

## 已連結案例

Cofacts
- Discord: https://discord.gg/mmZS9sZuau
    - #general
- g0v slack 
    - #cofacts
- 啟用時間：2023.01
- 維護者：Mrorz

零時小學校
- Discord: https://discord.gg/csDjWBbhvf
    - #零時小學校交誼廳
- g0v slack 
    - #edu
- 啟用時間：2023.03
- 維護者：Ronny

UniCourse
- Discord: https://discord.gg/aDUjjDf3yZ
    - #閒聊
    - #edu-open-coscup-2023
- g0v slack
    - #edu-unicourse
    - #edu-open-coscup-2023
- 啟用時間：2023.03
- 維護者：Sky Hong


## 針對雙邊訊息編修動作，測試結果 

以下內容時間點：2023.03

### 發訊息

- ✅ 文字
- ✅ emoji
- ✅ 圖片

### 回覆

- ✅👀 Discord 的「回覆」，可以顯示在 slack，不過！顯示位置會在「對話串之中」，而非主頻道的新訊息
- ✅👀 在 slack 回覆 Discord 過來的訊息，回覆內容，可以同步到 Discord
    - 2023.03 不行
    - 2023.07.12 可以
    - 其他參考: Linking Slack threads to Discord threads https://github.com/42wim/matterbridge/issues/1558#issue-955418564

### 轉貼至頻道

- 👀 Slack：從另一個 slack 頻道，轉貼內容 (Share Message) 至 slack 頻道
    - 轉貼的內容，不會完整顯示至 Discord
        - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6a4116aeb6acaf06777c60eae1d2859f.png)
        - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_32c4af6ff2514ab2fed351ff37207c90.png)
    - 轉貼過程中，Add a message，這個則是可以同步於 Discord
- Discord：似乎沒有「頻道之間轉貼」這個功能

### 編輯
- ✅ Discord 編輯後的內容，也會同步更新至 slack
- ✅👀 slack 編輯後的內容，也會同步至 Discord，但是！Discord 那邊會把「新的訊息，整篇」再顯示一次，而非置換

### 刪除
- ✅ Discord 發出的訊息，在 Discord 刪除後，slack 會同步刪除
- 👀 slack 發出的訊息，在 slack 刪除後，Discord 這邊不會同步刪除，所以！要記得前往 Discord 手動刪除

### 圖片
- ✅ Discord 張貼圖片，可以同步至 slack
- ✅ slack 張貼圖片，可以同步至 Discord

### 備份 (slack archive)
- 👀 slack archive 似乎不會紀錄 Discord 傳過來的訊息，以下是 3/5 slack #edu 頻道對話紀錄網址中，查無本則訊息
    - https://g0v-slack-archive.g0v.ronny.tw/index/channel/CN64A1FHA#ts-1677997542.5826
- 不過，如果把訊息轉傳到另一個 slack 頻道，則可以記錄於 Archive，例如 把本則訊息，從 #edu 轉至 #bridge 可被紀錄，但是篇幅受限制，基於 slack 轉貼訊息預覽長度的字數限制 
    - https://g0v-slack-archive.g0v.ronny.tw/index/channel/C01SHPD80UD/2023-03#ts-1678002258.3854 
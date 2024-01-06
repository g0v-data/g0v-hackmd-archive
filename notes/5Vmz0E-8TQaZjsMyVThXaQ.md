---
title: "live.g0v.tw 立院影城特別版"
tags: hackpad
---

# live.g0v.tw 立院影城特別版

> [點此觀看原始內容](https://g0v.hackpad.tw/4tGJf2h69t4)

[https://www.youtube.com/watch?v=cygd0tvbk50](https://www.youtube.com/watch?v=cygd0tvbk50)

### 要解決的問題

- 現有的聯播網無法 cover 所有直播
- 新上架的直播網址需要一直更新
- g0v.today 工人 24 小時隨時待命放最新網址會很累
- 過期的直播網址需要保存、可以回頭查詢
- 過期的直播需要連到對應的文字轉播，讓網友可以邊看邊幫忙補完文字
需要功能完整的直播專用網頁，可內嵌在 g0v.today 中，也可單獨瀏覽。網址為 live.g0v.tw

### mockup

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8cbb504f70818da63c5b357772422b0d)

### 功能

> 前端完成在行首加 :ballot\_box\_with_check: ( : 後接 ballot\_box\_with_check)，後端完成加 :heavy\_check\_mark: ( : 後接 heavy\_check\_mark)，驗收完成整行打勾
> [name=ET B]

- [ ] 使用者從 g0v.today 左側選單，按下其中一個選項，打開內嵌的 live.g0v.tw 頁面…
    - [ ] …看到一個影片清單
        - [ ] 每個影片有時間、地點、主題等 metadata
        - [ ] 影片下面可以連到相關的文字稿
        - [ ] 使用桌機的話，一列可以有好幾個影片
        - [ ] 使用手機或平板的話，影片會自動變成上下疊起來
        - [ ] 預設只會看到目前 on air 的影片
            - [ ] 在大螢幕上可能可以全部自動開播，桌機應該跑得動？
            - [ ] 在手機等小螢幕上不會自動開播
                - [ ] 看到感興趣的直播主題，點下去會連到該直播的 youtube / ustream / justin 頁面
        - [ ] 想找過去的影片，按下某個連結後可以…
            - [ ] 用搜尋的
            - [ ] 用設定過濾條件的
- [ ] 使用者直接打開 live.g0v.tw
    - [ ] 按下某個連結，可以回到 g0v.today 的 hackfoldr 內嵌頁面
- [ ] 維護人員想更新直播網址時，進入 github repo 或某後台…
    - [ ] 直接加一筆新的 item 並附上 meta data
    - [ ] 把舊的 off air 的 item 標上某個 class，使它 display: none 之類的
    - [ ] 設定好後…
        - [ ] 前台會自動更新
        - [ ] off air 的影片會自動抓取結束時間，標註在 metadata 欄位

### 技術實做

[https://github.com/g0v/ivod.ly.g0v.tw/](https://github.com/g0v/ivod.ly.g0v.tw/) (= [http://ivod.ly.g0v.tw/](http://ivod.ly.g0v.tw/) ) 也許可以參考
> 連不上[http://ivod.ly.g0v.tw/](http://ivod.ly.g0v.tw/) 了
> [name=Bestian T]


簡單一點的話就是掛上 [http://mediaelementjs.com/](http://mediaelementjs.com/) 即可




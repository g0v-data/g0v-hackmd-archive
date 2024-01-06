---
title: "vTaiwan 介面 2.0"
tags: vTaiwan.tw, hackpad
---

# vTaiwan 介面 2.0

> [點此觀看原始內容](https://g0v.hackpad.tw/5Rpzv7bxLlw)

demo：[https://react.vtaiwan.tw/](https://react.vtaiwan.tw/)
repo：[https://github.com/g0v/react.vtaiwan.tw](https://github.com/g0v/react.vtaiwan.tw)
ref：[廣宣組意見彙整](https://g0v.hackpad.tw/vTaiwan.tw-mockup-v1-cJSDzZRro6W)

6/5 小松
    - [x] 左上 toggle 在桌面應該變得比較不明顯 \[soidid\]
    - [x] 最底下的 menu item 會被吃掉
    - [x] 「各階段」在 Category 層，加上 <，暗示可以回上層。首頁連結也要加 Home 符號 \[soidid\]
    - [ ] Post paging 無法多頁 \[soidid\]
    - [x] Discuss paging 應顯示最舊、最新，而不是最舊的兩個 \[soidid\]
    - [x] 首頁會出橫向捲軸 \[pm5\]
    - [x] 手機版的 Nav 顯示時，樣式調整 \[soidid\]
    - [x] 手機版預設不顯示 Nav
    - [x] 首頁各階段加上介紹文字 \[soidid\]
    - [x] Zombie 應該要不使用 paths.js 而是用 scraping (follow href) \[au\]
    - [x] 靜態頁面：/how 、 /tutorial 、 /about \[au\]
    - [x] locationHandler 在 dev mode 換回 Router.HistoryLocation，把 server.js 做成可以處理 /path/ \[ly\]
        - [rackt/react router#676](https://github.com/rackt/react-router/issues/676)
    - [x] Transmit 的後端加上 cache（如 superagent-cache or caching-fetch） \[ly\]
        - immutable-request
    - [x] 整個畫面多了一個 scrollbar \[pm5\]
    - [ ] NavList 符合 router.getCurrentPath() 的項目要 highlight，另外 hover 時也要 high/light
    - [x] post item 裡原本 talk.vtaiwan.tw 的連結會壞掉 \[pm5\]
    - [x] 使用 localStorage 做 request cache

5/30 線上設計松 + 6/2 au clkao 討論筆記
- 桌面模式時，左上角的 toggle 取消
    - 「回首頁」和「回上層」用圖示表示
    - 「各階段」在 Category 層可以用 menu 裡的 sub-tab icon 切換，而不是回上層再下來
- 議題形成區
    - 用時事作為 motivating example，不預設正反方
        - 例如「施明德以網路收集總統選舉連署正本」
        - 第零階段：在 pol.is 上建立個案討論，將網址貼上
            - 公開 review，需滿足三個構成要件：
                - 以網路使用者為主要利益相關者
                - 與法規調適有直接關聯
                - 不預設特定解決方案
            - 取得一定參與度，即可開始尋找合適之提案部會。

4/24 小松，討論介面目前需要修改的地方，以下==從需要優先修改的列起==

- 不知道左上角可以按。四行改三行。預設展開不要擋到。
    - [x] 這個改好了~ 已上線。

- 「金管會群眾募資」的定案快要出來了，目前沒有放定案的地方（5/1 前要出現）
    - 在 talk 裡面，把草案變成定案？（改了六七個地方）
    - 或者某個可以 diff 的機制


- 討論主題列表的地方，有很多不同的 stage，顯示方式不清楚 & 看不到過去討論的資料
    - 相較起來，talk 還比較清楚：[https://talk.vtaiwan.tw/](https://talk.vtaiwan.tw/)
        - 同一個顏色的就是同一個討論主題


- 在某個討論主題底下，各個階段的資料，可以用時間軸的方式呈現
    - 左邊是資料，右邊是討論
    - 也可以參考 udn 的 debate

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_de6b0ad4526c60a8fe3d655b5866f7e6)

- 首頁直接把各個討論主題列出來（目前有九個），圖片用提案時候的簡報封面當作圖片，不要只用部會的 icon，感覺太官樣。
    - 例如這裡的簡報：[https://talk.vtaiwan.tw/t/topic/148](https://talk.vtaiwan.tw/t/topic/148)
    - gitbook 的第一頁
    - 或是直接放 slideshare 的網址（或 thumbnail 圖片？）在 .json 裡

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1f829532f65bd6338e4677e8ba02cbc2)


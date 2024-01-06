---
tags: g0v-summit, 2020
---

# Grantdash 筆記

## 會議記錄

### 2020/05/14

#### summit 2020 grantdash(?) 時程

- 5/19 stage server - 給行銷組
    - 能夠清楚的表述需要提供的文字、圖片需求

- 5/27 production server - 開始提案
    - Static pages
    - 註冊登入帳號(g0v slack)
    - 提案 (二個月 or 一個半月)
        - CRUD
        - 歷史紀錄
        - markdown editor
    
- 接續一個月後？ 提案結束進入討論 2 週至一個月
    - 串接 https://discuss.grants.g0v.tw/
    - 追蹤功能
    - 搜尋功能

- 接續一個月後？ 討論結束，進入審議結果
    - 審議結果列表

#### Grandash 使用流程

1. 三階段（依日期分）
   1. 提案階段，大家可自由報名
   2. 修改階段，不可報名，但已報名的還可修改
   3. 評審階段，都不可改
1. 目前 config 裡的日期，沒有和邏輯連動，
   1. 請自行把 html 編輯的按鈕拿掉
1. 哪些需要手動改東西
   1. 要注意有些欄位會出現在多個檔案裡，請參考 Ronny `修改需求欄位`
   2. 其他請參考 Ronny `一些動作`
1. 需要自架 [discourse](https://www.discourse.org/) ，塞到 grantdash config 裡
   1. 要測試是否需要兩邊都 login 才能留言

## 暫定六月中上線前的規劃：

1. 建立 stage server
2. 了解頁面時間點的邏輯，哪個時間邏輯控制頁面的呈現
3. 提供 stage 頁面給行銷組
4. 剪法修改網站
5. Production 上線

## 讀書心得

1. init setting
   1. copy conig/config.json + key.json 
   2. copy metrics/config.json
   3. Docker node:6.11-onbuild not work on Ubuntu XD
2. tech stack: 
   1. node 0.10.x + with ES6 support over babel
   2. express with http + socket.io (0.9.14 使用 process.EventEmitter ，綁 node 0.10)
      - view: jade + less
      - route 
      - session store [over Mongo](https://www.npmjs.com/package/connect-mongo)
   3. backbone 1.1.2 - load by express in most of routes
3. routes / features:
   1. api
      - `/api/v2/dashboard` - flat CRUD
      - `/api/v2/collections` - flat CRUD
      - `/api/v2/projects` - depth = 2 CRUD + socket.io (unsure)
        - `/:pid/followers`
        - `/:pid/contributors`
      - user.js - not CRUD, collection of multiple endpoint XD
        - `/:domain/draft`
        - `/:domain/admins/:uid`
        - `/users/:id`
        - `/users/team`
        - `/profiles/:uid`
   3. site (non API related route)
      - whole bunch of redirection, apply view data (`meta.js`), and render view
   4. admin
      - just for first installation check
   5. metrics
      - cronjob that count user, project, dashboard, and collection periodically
4. socket.io
   - listen to `post`, and ?
6. data schema (lib/models) `請參見 Ronny 筆記 / monbodb 結構`
   1. collection - list of dashboards that belong to a user
   1. dashboard - 
   1. draft
   1. project - 提案 with revision history
   1. user
6. Backbone UI - WIP
   - in `client` directory
   - Use Grunt to build + copy file to `../public`
8. Pure Jade loaded by Express directly
   - `/`
   - `/2018`
   - `/power/` && `/power/en`
   - `/issue/`
   - `/news/`

## Ronny 筆記
* mongodb 結構
    * dashboards:
        * 表示一個活動，裡面可以有很多提案，以 grants 為例是 2017a, 2017s, 2018, 2019 等活動
        * 主要 key 是 domain
        * 欄位：
            * open: 是否在開放提案階段
            * showcase: list
        * 在 summit 的話，一個 dashboard 可以當成一軌議程
    * projects:
        * 表示一個提案
        * 欄位：
            * finalist: 入圍
            * awarded: 得獎 
    * draft
        * 草稿，會在頁面上隨時做儲存動作
* 一些動作
    * 新增 dashboard
        1. 改 grantdash/data 下的 dashboards.json
        2. 進到 grants.g0v.tw 主機內
            * docker-compose -f docker-compose.yml -f docker-compose.prod.yml  run --rm mongodb mongoimport --host mongodb --db hackdash --collection dashboards --file /dev/stdin
            * 貼上 dashboards.json 上的內容
        * 
    * 中止新增提案
    * 停止提案修改
    * 修改需求欄位
        * https://github.com/g0v/grantdash/commit/38c308d787021547d26d65d6623c42d0e81d7873   有三個地方要改

## 待解問題

1. 網站資訊、頁面架構
2. 提案相關情境們的流程圖
3. letsencrypt-nginx docker
4. 


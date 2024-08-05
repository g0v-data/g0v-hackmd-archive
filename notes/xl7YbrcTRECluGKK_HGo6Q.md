---
tags: cofacts, 詐騙, 165, open data, SEO
---

# Open165 反詐騙 - 假網站公告搜尋引擎最佳化

## 看到的問題

165 每週都會公告「[民眾通報假投資(博弈)詐騙網站](https://165.npa.gov.tw/#/article/9/1541)」。

然而，實際在 Google 搜尋公告裡的網站，會發現出現的不是 165 公告，而是大量的「[二次詐騙](https://www.vac.gov.tw/vac_home/changhua/cp-1228-113572-105.html)」

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7aaf7c45ae619a69b4ddb4d1d8e7876f.png)
（左邊的 "nexus" 搜尋結果都是二次詐騙，而右邊的詐騙公告都沒有在 Google 上）

## 想到的解法

- 用 165 開放資料做一個網站，讓每一個 scam site 有自己的一頁
- SEO: 網址、標題、內容
- 讓 Google 到的人得到有用的資訊，如：簡單好懂的 165 處理方式、過往報案的經驗分享等等

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_161a97856a8fdecd46f44942802849ae.png)

### Target audience

會透過搜尋引擎裡進到網域 (host) detail 或網站名稱（name）detail 的人，應有兩種

- 與詐騙有接觸，半信半疑者
- 前一波已被完詐，搜尋資料時容易踩進二次詐騙陷阱者

由於兩者需求不同（前者需要資訊與被說服說是詐騙；後者剛被完詐，已知詐騙，重點是把握黃金報案時間），需要的資訊與 wording 也都會不一樣。

### 可以放的東西

兩個 detail 頁面都可以這樣放：
- 網域/網站名作為標題
- Summary：根據 ＯＯＯ（165 通報案例）來看，它確定 / 可能（僅有類似名字 or 網域但本身不在 165）是詐騙
- Tab: 分成「OO 是詐騙嗎」跟「被 OO 騙怎麼辦」對應到兩種 TA，預設顯示前者 tab
  - Tab 視為一種分頁，有自己的 route 與頁面標題，以供最佳化
  - Tab 最末尾有按鈕可以換 tab

Host detail 「OO 是詐騙嗎」tab 中可以放：
- 165 公告列表（點擊名字可以連到 name detail），蓋棺論定是詐騙
- WHOIS record - 分析網域多新
- 列出類似網域
  - fake.idv, fake.xyz, fa0ke 算是「相似」

name detail 「OO 是詐騙嗎」tab 中可以放：
- 165 網域與公告次數（點擊網域可以連到 host detail）
- 列出類似名字
  - 「富達」、「富達投資」算是相似

找不到的 case（網址、名稱）時，「OO 是詐騙嗎」tab 中可以放：
> 找不到的 case 仍須顯示以下，方便 Fact checker 引用
> 真的很可疑、但 165 還沒有的 case，有這個 open165 permalink 可以用在查核裡

- 坦承說 165 反詐騙還沒收到這個，無法確認
- 若為網域，做 DNS record
- 列出類似內容，若有，則明確請讀者小心

每個 case 的「被 OO 騙怎麼辦」tab 內容都一樣：
- 網頁標題放「被 OO 騙怎麼拿回錢」之類
- 說明「二次詐騙」與小心所有會幫你拿回款項的人
- 撥打或前往 165 官網，提供保存的證據
- 赴警局完成報案程序
- 一些 youtube 上的成功案例，但也說明這是比較幸運的狀況
- 說明調查接下來會怎麼進行
  - 也說明：無論有沒有拿回來，赴警局交付證物也是有幫助的

### Brainstorming
- 「類似名字」、「類似網域」的 retrieval：
    :::success
    Already implemented in https://github.com/cofacts/open165/pull/9
    :::
  - 因為一定很多「投資」等常用字，用向量做或只用 term frequency 做效果一定爛。搜尋一定要用 TF-IDF 來避開常用字。
  - D1 supports virtual tables for full-text search using SQLite’s FTS5 module [source](https://developers.cloudflare.com/d1/build-with-d1/import-export-data/); [discussion](https://community.cloudflare.com/t/d1-support-for-virtual-tables/607277)
  - 其他支援 TF-IDF 的有：
    - Zinc https://github.com/zincsearch/zincsearch?tab=readme-ov-file
    - Quickwit https://github.com/quickwit-oss/quickwit
      - 介紹人：https://grafbase.com/blog/serverless-search-in-rust
    - Edgesearch https://github.com/wilsonzlin/edgesearch
    - Comparisons: https://prabhatsharma.in/blog/in-search-of-a-search-engine-beyond-elasticsearch-introducing-zinc/
- 紀錄詐騙網站截圖：某種網站外觀可能是詐騙常用的，所以會長很像
  - 若要做使用者站內搜尋功能（可能產生 not found case），也可以用截圖外觀比對
- 紀錄詐騙網站原始碼：可能詐騙集團抄來抄去，用的都是同一套 library 組合等等
    - 很多都 SPA，或許可以用 headless browser 抓 JS 啟動完成後的 HTML，用全文檢索處理
- 官方澄清：某些網站名稱是被冒用，如果他們有官方澄清，那麼可以放在「OO 是詐騙嗎」分頁裡
    - 可能需要 crowd source
- 詐騙網站 server header fingerprint - 可能不同網域都連到同一台機器
- WHOIS / OSINT recon solutions
  - [whoiser](https://github.com/LayeredStudio/whoiser) 與[似乎能在 Cloudflare Worker 上跑的 hack](https://www.pudn.com/Download/item/id/1699851202973721.html)
  - FinalRecon's [whois command](https://github.com/thewhiteh4t/FinalRecon/blob/master/modules/whois.py#L39-L58)

### 其他內容

- 政府 open data license
- 本專案 license
- about 本專案
- 想一個不會被誤會成政府的 site name 擺在左上角。如 Open165 民間反詐騙？

## 目前進度

### 2024/8/04 COSCUP
- Designers in Tech - Open Source Design Workshop
    - [最靠近門的那一組的共筆](https://hackmd.io/dMR3n42xSYy2P4EzVP-SeQ?view#%E6%9C%80%E9%9D%A0%E8%BF%91%E9%96%80%E7%9A%84%E9%82%A3%E4%B8%80%E7%B5%84%E7%9A%84%E5%85%B1%E7%AD%86)
    - https://github.com/cofacts/open165/issues/13

### 2024/7/20 大松

> 初次提案

- [📊 提案投影片](https://docs.google.com/presentation/d/1ivYoq6-urRHUYQw92Rm1Y2tIM4F98NTS1EMGXbcs6z4/edit#slide=id.g2787f2273ce_0_0)
- [📝 共筆](https://g0v.hackmd.io/roo-89pnR6iouhm-xgLL3A)
- [💻 開發](https://github.com/cofacts/open165)
  - Finished data flow: [Open data](https://data.gov.tw/dataset/160055) --> Cloudflare D1 DB --> website display
  - Continuous deployment on Cloudflare Pages
  - 申請 [165.g0v.tw](https://github.com/g0v/domain/pull/82)

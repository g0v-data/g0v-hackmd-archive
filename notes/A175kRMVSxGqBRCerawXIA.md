---
tags: hackfoldr 2.0
---

Hackfoldr 快取計畫
=================

最近因為 ethercalc 好像有些不太穩定，又時間接近大松，希望 hackfoldr 能穩一點，我最近想把 cache 機制作好，預計會弄個  ethercalc-cache.g0v.io 來做這件事，目前想法規格如下：
1. ethercalc-cache.g0v.io　只會 cache 網址符合 ethtercalc.net/_/([^/]*)/csv 的內容，其他網址不 cache 直接 404
2. cache 規則如下：
    a. cache miss: 去 ethercalc 抓內容存進 db 後並顯示出來 
    b. cache hit 而且 cache 在五分鐘內: 直接從 db 抓資料顯示，不去戳 ethercalc
    c. cache hit 但是 cache 超過五分鐘: 去 ethercalc 抓來更新
    d. cache hit 但需要更新時，連 ethercalc 超過 3 秒：暫時標記　ethercalc 異常，五分鐘內都不會去 ethercalc 抓新資料，統一都用 db 內資料為主 
    e. cache miss 時，去 ethercalc 抓資料時間為 20 秒 
    
3. db 規格如下：
    a. id VARCHAR(32): 記錄網址中 csv 前面的字
    b. cache_at INT: 記錄 cache 時間，用 UNIX Timestamp 存
    c. content: TEXT: cache 內容
4. 支援 curl https://ethercalc-cache.g0v.io/_/hello/csv?purge=1 ，會將 cache_at 歸零，讓下次讀取時會重抓
5. 修改 beta.hackfoldr.org 程式碼，讓抓取 csv 改從 ethercalc-cache.g0v.io 抓（但 edit 仍保持從 ethercalc.net

note
----
* SQL:
``
CREATE TABLE cache (
    id VARCHAR(32),
    cache_at INT,
    content TEXT,
    PRIMARY KEY (id)
);
``
---
title: "國會大代誌復活計劃"
tags: hackpad
---

# 國會大代誌復活計劃

> [點此觀看原始內容](https://g0v.hackpad.tw/ZJ5iE1uLD8Y)


我想要把國會大代誌復活，這邊記錄一下復活的流程
> ++
> [name=chihao y]


## 問題與解決方式

- pgrest 在現在的 postgresql 比較難運作起來，因此 API server 無法跑起來
    - 計劃用 PHP 重新寫一個 pgrest 模擬器，不需要依賴在 postgresql 裝外掛，這樣可以存活久一點
- ly.g0v.tw 放在 node jitsu ，現在好像也跑的怪怪的（應該是 dependency 的問題）
    - 把 package.json 的版本設好後，也推到 middle2 上

## 流程

- ly.g0v.tw
    - package.json 改版本
        - karma 版本從 ">= 0.11.13" 改成 "0.11.13"
        - "karma-mocha" 版本從  "~0.1.0" 改成 "0.1.0"
    - gulpfile.ls 把 port 從寫死 3000 改掉
- api.ly.g0v.tw
    - 從 srv/index.ls 前面註解有寫到的 CREATE TABLE 相關指令，在資料庫建立 table
        - 其中 stats.analytics 改成 analytics ，不用再多建一個 schema

## 變殭屍了

- 後端新程式碼
    - [https://github.com/g0v/api.ly-php](https://github.com/g0v/api.ly-php)
- 展示
    - [http://ly.g0v.tw/bills/1150L15359](http://ly.g0v.tw/bills/1150L15359)
[https://greenparty-net.kktix.cc/events/greenparty-net-201405](https://greenparty-net.kktix.cc/events/greenparty-net-201405)




---
title: "使用 PostgreSQL"
tags: hackpad, middle2
---

# 使用 PostgreSQL

這裡會一步一步教你如何在 Middle2 使用 PostgreSQL 資料庫

## 需要基礎知識
* PostgreSQL 基本連線使用方式
* 會在程式內引用環境變數

## 步驟

### 為專案新增資料庫
* 在已經開好的專案頁中，拉到 Addon 區塊，並點選 Add: PgSQL
* * ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6a6830386408de2cb806bce8d5c8d19c.png)
* 新增完後，就會看到有新增了 PgSQL 資料庫可以使用
* * ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_eb3d7befba266cc184c6da386462185f.png)
* 並且在 Variable 區塊可以看到資料庫的帳號、密碼、IP等資訊
* * ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7e8d1c44218cf12bfc7b2f52f7723c04.png)

### 透過 phpPgAdmin 管理資料庫
* 可以在上方看到有 phpPgAdmin 頁籤
* * ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8168c215fa0288284fcbfe50ec6c915d.png)
* 在 phpPgAdmin 內就可以看到全部有開資料庫的專案列表了
* * ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9ddbbbb41da07a30ac7be09043dfc2a5.png)


### 透過 SSH Tunnel 從外部連到 PostgreSQL
* 目前 PostgreSQL 放置在內網中，無法從網際網路直接連到 PostgreSQL ，但是 middle2 有提供 SSH Tunnel 可以從外部連入的功能，以方便讓專案第一次建立或匯入資料庫時可以使用
* 可以先拉到專案資訊頁的 Addon 區塊，可以看到 Tunnel 指令資訊
* * ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3a78ced9cf17bec61792b69cbfd68816.png)
* 在主控台環境下，輸入Tunnel 指令後，就可以建立起來 Tunnel 了
* * ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d7d2021501c80d3b0cb8934cd16817c2.png)
* * 可以看到 tunnel is up ，會建立起來能連線一小時的 tunnel
* 也可以透過 psql 指令進去
* * ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ad12c84b994877bb2b8aca48b80fa307.png)
* * 其中 DATABASE_URL 中的格式是 pgsql://[帳號]:[密碼]@[IP]/[資料庫] ，要連線時指令就用 psql -U [帳號] -W -h 127.0.0.1 [資料庫] ，並且輸入密碼
* 在測試開發環境中，也可以用 env DATABASE_URL=pgsql://[帳號]:[密碼]@127.0.0.1/[資料庫] ，在本機環境中連到線上資料庫
* * 可以用 「cat dump.sql | psql -U [帳號] -W -h 127.0.0.1 [資料庫]」 的方式將匯出檔倒進資料庫中
* * 在 rails 要做 migrate 也可以用 「env DATABASE_URL=pgsql://[帳號]:[密碼]@127.0.0.1/[資料庫] rake db:migrate」

---
title: "使用 MySQL"
tags: hackpad, middle2
---

# 使用 MySQL

這裡會一步一步教你如何在 Middle2 使用 MySQL 資料庫

需要基礎知識
MySQL 基本連線使用方式
會在程式內引用環境變數

步驟

為專案新增資料庫
在已經開好的專案頁中，拉到 Addon 區塊，並點選 Add: MySQL

新增完後，就會看到有新增了 MySQL 資料庫可以使用

並且在 Variable 區塊可以看到資料庫的帳號、密碼、IP等資訊


透過 PHPMyAdmin 管理資料庫
可以在上方看到有 PHPMyAdmin 頁籤

在 PHPMyAdmin 內就可以看到全部有開資料庫的專案列表了


透過 SSH Tunnel 從外部連到 MySQL
目前 MySQL 放置在內網中，無法從網際網路直接連到 MySQL ，但是 middle2 有提供 SSH Tunnel 可以從外部連入的功能，以方便讓專案第一次建立或匯入資料庫時可以使用
可以先拉到專案資訊頁的 Addon 區塊，可以看到 Tunnel 指令資訊

在主控台環境下，輸入Tunnel 指令後，就可以建立起來 Tunnel 了

可以看到 tunnel is up ，會建立起來能連線一小時的 tunnel
也可以透過 mysql 指令進去

其中 DATABASE_URL 中的格式是 mysql://[帳號]:[密碼]@[IP]/[資料庫] ，要連線時指令就用 mysql -u [帳號] -p -h 127.0.0.1 [資料庫] ，並且輸入密碼
在測試開發環境中，也可以用 env DATABASE_URL=mysql://[帳號]:[密碼]@127.0.0.1/[資料庫] ，在本機環境中連到線上資料庫
可以用 「cat dump.sql | mysql -u [帳號] -p -h 127.0.0.1 [資料庫]」 的方式將匯出檔倒進資料庫中
在 rails 要做 migrate 也可以用 「env DATABASE_URL=mysql://[帳號]:[密碼]@127.0.0.1/[資料庫] rake db:migrate」

---
tags: g0vernance
---

g0v slack 備份
==============

https://jothon-public-files.s3.ap-northeast-1.amazonaws.com/g0v-export-20140816-20210618.zip

- 線上版：https://g0v-slack-archive.g0v.ronny.tw/
- 時間範圍：2014-08-16 ~ 2022-06-18
- 所有公開頻道的公開發言
- 有做去個資處理：https://github.com/g0v/slack-export-cleaner/blob/main/clean.php
    - email 去識別化： g0ver@g0v.tw => -----@---.--
    - 電話去識別化： 0912-345-678 => \****-***-***
    - 使用者資料只保留必要欄位
- 檔案大小：62MB
- 檔案說明
    - users.json 所有成員資料(11647人)
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e608e4d6b866d2fa5a11f9c4b33b3873.png)
    - channels.json 所有頻道資料（712個頻道）
    - (頻道名)/YYYY-MM-DD.json 單一頻道某一天的對話記錄


分析研究成果可回報在下面
=========
- [g0v成就系統](https://badge.g0v.tw/)
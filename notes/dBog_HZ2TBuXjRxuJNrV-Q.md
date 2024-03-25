---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240325 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :eye: Under review
- https://github.com/cofacts/collab-server

## 小聚檢討

小松果：https://g0v.hackmd.io/agmmCdDLQEmon7BYG-kSIQ

## 2024/3/24 Downtime

3/23 誤報（？）
- 08:30 回報下線，但實際上是好的 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c9deb0552680ab4fed6b01f0034747d9.png)


3/24 爆炸
- 20:00 Cloudflare 回報 HTTP timeout occurred ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6ee376beeee21ebe0573d0e3e19a3ccc.png)
- 20:59 Ronny 提醒倒站
- 21:30 `top` ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_19324d71b9dc7476a56cf746f4a87b09.png)
    - 狀態跟 2/17 一樣 https://g0v.hackmd.io/R06Z7EflRYqAC-R8zO6FqA#2024217-Downtime
    - 但這次 `echo 1 > /proc/sys/vm/drop_caches` 沒用
- 21:42 使用 `docker-compose restart db`
    - 指令要過數十秒才生效，但的確有執行

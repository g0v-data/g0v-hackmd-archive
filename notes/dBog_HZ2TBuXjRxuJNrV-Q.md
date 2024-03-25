---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240325 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：orz,bil, 4000, nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :robot_face: rumors-line-bot

- 謠言惑眾獎 LIFF https://github.com/cofacts/rumors-line-bot/pull/388

##### Testing checklist

測試 Staging 問卷 URL: https://liff.line.me/1563196602-X6mLdDkW?p=mgp (非正式站網址)

- [ ] 應可直接使用瀏覽器進入上述網頁
    - [ ] 會要求登入 LINE
    - [ ] 沒有加 Cofacts 好友，會請使用者允許 Cofacts
    - [ ] 使用者應可直接分享「不帶有 user ID」的 URL 給他人
- [ ] 網址放進 LINE，在 LINE 點時也可以直接使用
    - [ ] 不用登入 LINE，直接檢查是否有加 Cofacts 好友
    - [ ] 使用者應可直接分享「不帶有 user ID」的 URL 給他人



### :eye: Under review
- https://github.com/cofacts/collab-server

## CCPRIP
### [Op] Transcript spam
> nonumpa
> https://g0v.hackmd.io/vKCvrqSQTlm7GEx9MAXGaw?view#op-Transcript-spam-處理
> 

https://github.com/cofacts/rumors-api/pull/335
- Question: why implement as plugin; why not just implement in `onStoreDocument`?


## 謠言惑眾獎

4/2 開催
- Cofacts LINE voom 露出
- Cofacts 粉專幫推
    - Meta 贊助廣告 --> LIFF URL
- Cofacts 專屬問卷網址
    - LIFF 讓使用者登入 LINE 並加 Cofacts 好友
        - 目前 bot prompt Normal https://developers.line.biz/en/docs/line-login/link-a-bot/#redirect-users
    - LIFF 帶入使用者 ID 到 surveycake 網址中
        - 僅是 dedup
        - 沒有想要防假的使用者 ID，因為
            - 這是趣味投票，選哪個選項不會影響中籤機率
            - 灌假 ID 只會降低自己中籤的機率
    - 受眾可在 Cofacts 投一票、MyGoPen 投一票，會有兩倍中獎機率
    - 中籤後若為 Cofacts 使用者，Johnson 會幫忙發送推播給該使用者
- TODO
    - 問卷最後請讀者加好友
    - 問卷尾端要大家在活動期間維持好友狀態，否則會收不到中籤推播

## 小聚檢討

小松果：https://g0v.hackmd.io/agmmCdDLQEmon7BYG-kSIQ

- 桌子
- 插座與延長線佈置法
- 場地 OK?

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
- TODO:
    - 想不到還能做啥。

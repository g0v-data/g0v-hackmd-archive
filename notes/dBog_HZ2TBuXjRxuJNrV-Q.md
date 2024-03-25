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

- [x] 應可直接使用瀏覽器進入上述網頁
    - [x] 會要求登入 LINE
    - [x] 沒有加 Cofacts 好友，會請使用者允許 Cofacts
    - [ ] 使用者應可直接分享「不帶有 user ID」的 URL 給他人
- [ ] 網址放進 LINE，在 LINE 點時也可以直接使用
    - [ ] 不用登入 LINE，直接檢查是否有加 Cofacts 好友
    - [ ] 使用者應可直接分享「不帶有 user ID」的 URL 給他人

#### 問題

- ios safari 登入 LINE 如果沒做過就不知道怎麼用


### :eye: Under review
- https://github.com/cofacts/collab-server

## CCPRIP
### [Op] Transcript spam
> nonumpa
> https://g0v.hackmd.io/vKCvrqSQTlm7GEx9MAXGaw?view#op-Transcript-spam-處理
> 

- 有兩個 user 查不到，有一個在 snapshot 查到，另一個找不到，但貢獻只有一次 [name=nonumpa]
  - 可以放成 AI transcript 
- ydoc 有時候 user 會不見，被 gc，只要被 gc 就不會拿出來。硬拿可以，但還是有東西被刪掉。
  - 只有在 migration 比較以前的 doc 發生 [name=nonumpa]
  - 不確定之後是否還會發生
  - 本週 migration 寫完就可以放 staging 
    - 先 reindex db
    - 再跑 migration
    - 會寫在 PR

https://github.com/cofacts/rumors-api/pull/335
- Question: why implement as plugin; why not just implement in `onStoreDocument`?
  - 問題：只加空白，snapshot 會是沒有變動的，但還是會被放上去
  - 如果跟 snapshot 邏輯放在一起，disconnect 時再去計算，如果 snapshot 沒有變動就不記。contribution
  - 因為 contributor 會要讀之前的 snapshot 所以必須在 snapshot plugin 之前執行


## 謠言惑眾獎

4/2 開催 同步mygopen 宣傳
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
    - 字體大小、錯字 [name=bil]

## 小聚檢討

小松果：https://g0v.hackmd.io/agmmCdDLQEmon7BYG-kSIQ

- 檢查行前通知的地址
- 交通方便（略輸行天宮/北車/雙連小樹屋）
- 窗明几淨，廁所乾淨
- 唯一的缺點是不能丟垃圾
- 網路還可以 new taipei
- 桌子太重
- 桌子排成東大的做法很好
  - 一桌 5 人左右，4 桌，高腳椅座位也有人
- 插座與延長線佈置法
  - 2x 三插頭，插在高腳椅下的插座
  - 從高腳椅下延長到後排座位
  - 前排坐位: tbd
- 場地 OK?
  - ok [name=bil]

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
    - 再發生就課金加大伺服器


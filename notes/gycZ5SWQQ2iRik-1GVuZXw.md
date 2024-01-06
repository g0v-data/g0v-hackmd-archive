---
tags: cofacts, meeting note
---

20190814 會議記錄
=====
lucien, bil, ggm, mrorz
> 上次開會紀錄：https://g0v.hackmd.io/s/r1yKZAPXr
> 

## 小聚準備

:::danger
今天要處理完！
:::

- [x] 主題：鬼門關（鬼差、搶孤、勇闖鬼門關 = 資料庫）
    - 勇闖謠言鬼門關
    - 用回應消口業、渡眾生
    - 西洋人怕鬼、台灣人也怕鬼
    - 在鬼月的尾聲，一起與好兄弟、好姐妹、回學校的小朋友、以及與資料庫裡的鬼話連篇說再見
- [x] 時間：8/31 14:00-17:00（青平台已經確認）
- [x] 人數：25
    - bil: 不要超過 25, 超過會認識不到人, wifi 會爆
- [ ] Banner 改舊的圖 - lucien
- [x] KKTIX
- [ ] LINE 推播（不要提到 g0v 否則會爆量，造成困擾）
- [x] 攜帶貼紙: bil - 殭屍
- [x] 場地：青平台
    - [x] 茶水
    - [x] 麥克風+插座+網路
    - [x] 投影機
    - [x] 延長線
    - [ ] 食物
    - [x] 垃圾的話大樓有垃圾車
    - [x] Talk - maybe coscup by mrorz
    - [ ] 青平台說樓下門禁變嚴格，需要簽到單 --> KKTIX 可列印
- [ ] 誰會來呢？orz, bil, ggm
- [ ] 開場使用材料更新：https://docs.google.com/presentation/d/1QCAPtwkxreQ4EUtIWsOgR4c8h4tkRs22Qvv7jBFNrfI/edit#slide=id.g1ffc87ef17_0_23

:::warning
TODO
Banner 圖
LINE 推播文案
:::

## Dev

:::danger
db_1              | [2019-07-31T15:21:04,163][WARN ][o.e.d.z.ZenDiscovery     ] [new-cofacts] failed to connect to master [{VxKgRte}{...}{...}{172.19.0.9}{172.19.0.9:9300}], retrying...

Root cause: elasticsearch docker container 內，Elasticsearch 對於 new-cofacts host 的 IP resolve 結果，跟 ping 結果完全不同
- Ping 得到的 IP 可以進行 TCP 連線，是對的
- Elasticsearch 不知道哪來的 IP 是錯的
:::

cofacts.org --> answerfamily 時有交換 master name 與 master 認為自己的 publish address
但後來會改用 master 傳的 publish address 來溝通，然後就壞了。

- host 問題 https://discuss.elastic.co/t/the-publish-address-1-2-3-4-9300-is-not-the-real-ip-address/173126/2
- bind_host & publish_host https://stackoverflow.com/a/40315558

## TFD 問答
> Subject: Questions From TFD

https://hackmd.io/@mrorz/Hyw4eSh-B

:::success
Done by bil
:::

## 10/5 2019年亞洲事實查核專業論壇
事實查核中心10月5日（六）下午約3:00到5:00邀請在亞洲論壇提供約15分鐘的專案分享（mygopen, rumortoast和華視小組也都各有自己的時間）

投影片截稿日：9/20 (五)

:::success
bil講講
會回信
:::

## NDI infotegrity workshops, Sept. 10-12 in Taiwan

> 9/10(二)  ~ 9/12(四)
> bil 會去

:::success
bil 已回信
:::

## 台灣記協邀稿

:::warning
等信中
:::

---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20211124 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 實體出席：mrorz, bil, nonumpa
- 線上出席：cai
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline


### :rocket: Staging

#### :globe_with_meridians: Site
##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [ ] Article list
  - [ ] Filter works
  - [ ] Sorting works
  - [ ] Can go to article page

article detail with spams
- https://dev.cofacts.tw/article/wo41wy34iome
- https://dev.cofacts.tw/article/lr82tw5c8iam
- https://dev.cofacts.tw/article/kk2d56p3jtw5
- https://dev.cofacts.tw/article/iiy86mg2fppc
- https://dev.cofacts.tw/article/AWEdLURhhutQxxU6tqLk


##### ⛔️ Release Blockers

##### 未竟項目

### :eye: Under review

### :electric_plug: API

- https://github.com/cofacts/rumors-api/pull/268
- https://github.com/cofacts/rumors-api/pull/267

## 小聚檢討

- No show 太多，其他很好 [name=bil]
    - 出席 10~12 人 （報到率 45%）
    - 一個告知有事、一個重複報名
    - NPO hub 約 15 人，只有一次 20 人 [name=bil]
        - 因為跟朋友一起來，相揪出席率較高
        - 這次都個人戶
    - 提醒說不能來的話要取消
- 場地非常棒，數一數二好 [name=bil]
    - 擺設不用動
    - 沒有杯子，可以自己準備紙杯
    - 有冰箱，其實可以準備小東西
    - 交通方便，適合叫東西
    - 便利商店 300m 內
- 有一個參與者剛好有看到重複的文章，是否可以合併 [name=nonumpa]
    - 感覺不太需要，數量不多問題不大，花時間開發 cp 值太低
    - 微變形的變體應該要保留

:::success
下一次注意
- 提醒說不能來的話要取消
- 若還在小樹屋，則準備紙杯
:::

## 新增 spammer
> cai++

https://docs.google.com/spreadsheets/d/1Ytd69YU6z7Fgra81_79XrsPwQYV1Clh0yp5OZlk5Psg/edit#gid=0

## Server 遭受攻擊紀錄

- 時間：2021/11/19 11:00 左右開始
- 紀錄：https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1637297982.089500
- 13:54: 在 cloudflare 打開 I'm under attack mode、用 page rule 排除 api.cofacts.tw
    - 在社團發公告： https://www.facebook.com/groups/cofacts/posts/3136811743217300
- 14:13 block  `116.204.211.21` 讓 API spam 也消失
- 14:42:19 對方停止攻擊
- Suggestion: set rate limit on nginx: https://www.nginx.com/blog/rate-limiting-nginx/

:::success
已寫入 incident report: https://hackmd.io/@cofacts/incidents
:::

### 12:50 左右 server load
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2cd0a3fe99c2d6958571173ffd422692.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_df648baae052f87c8e04ce93a9764d5a.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9d275f62b32a8389b1ad1d2bbf3241b8.png)
https://files.slack.com/files-pri/T02G2SXKM-F02MY5B827L/image.png

### 攻擊狀況（使用指令與 log）
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6f1c9ac8bce6a716e424c458a9a407ae.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b9f4344b009091603a142bbbc9c32413.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cec536320d86e89ed80303aca0a2a5a0.png)

### 調高安全等級後狀況

設定
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_050525c331878e304623de60f647cd65.png)

Cloudflare 阻擋網站的攻擊，但似乎並非全面
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_aa143c2bf6ae6331545abf0675157a70.png)

load 仍有 10 左右

### 開啟 Under attack mode 後

在 website URL 亂 inject 成功阻擋，但 API 仍有 400
> （圖中回傳 400 者，代表有 GraphQL syntax error。第三方 chatbot 不可能會有 GraphQL syntax error）

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ddb2f7364d02553e91c0bc8796d5843f.png)

### 後續監測

- Cloudflare 顯示來自 116.204.211.21 的攻擊在當日 14:42:19 後就不再出現
- 11/17 19:00 ~ 19:30 時其實就曾有一波攻擊 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_045c3108d33178d04603d6e94b3dbc74.png)
- 擋完 IP 後，request 回到正常的 2k req/min 以下（nginx log，包含 website, chatbot access）
    - 攻擊發生的期間高峰是 10k req/min
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_297a4bedaa61332277d85998816727e5.png)

## 詐騙 with 個資
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4a0d2858eaf5e3f0a56f0489b12f4cb2.png =x300)
明顯是詐騙訊息卻有個資(身分證字號、地址)

討論：https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1637667382.1084

https://cofacts.tw/article/1ambr7sq4vkge

- 技術上拿掉名字與身分證字號也不會影響搜尋，因為旁邊的文字足夠多 [name=mrorz]
- [之前](https://github.com/cofacts/takedowns/blob/master/2020/0610-privacy.md)的情形是本人或相關人士提出修改需求，我們公告在 [takedown](https://github.com/cofacts/takedowns) 進行修改 [name=bil]

:::success
處理完成 :tada: 
:::


## rumors-ai

https://github.com/cofacts/ground-truth

## 問題回報

- 天澤集團 https://cofacts.tw/article/3a68xz85ennsd
    - 因為已經有 165 所以應該可以蓋棺論定是詐騙
    - 可能要針對此文章做鎖定
    - 可以去 facebook 討論
- 似乎有人人工在刷「中國影響力」tag，很新的文章也有，似乎跟「政治、政黨」tag搞混，可能是新手編輯。


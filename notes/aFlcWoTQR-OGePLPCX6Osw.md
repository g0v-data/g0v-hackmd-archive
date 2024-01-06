---
tags: cofacts, meeting note
---

20191002 會議記錄
=====
bil, orz, 文武
ggm (沒飲料)
NPOst 記者 (沒飲料)

:::danger
20191009 開會暫停一次
:::

> 上次開會紀錄：https://g0v.hackmd.io/oOEz-UpNQOS-n7isB45MNg
> 

## 小聚rundown

https://cofacts.kktix.cc/events/cofacteditor15

- 誰會來呢？bil, mrorz, 文武
- 攜帶
    - [x] 貼紙 - bil
    - [x] 簽到單 --> KKTIX 可列印 - mrorz
    - [x] Wifi 機 - mrorz
        - [ ] Netgear 本體
            - [ ] usb type-c 充電線與插座
            - [ ] 電池
            - [ ] 4G 天線 - 忘記了！！！
        - [ ] Asus RT-N12
            - [ ] 電源線
            - [ ] 5dBi 天線
            - [ ] RJ45 線
    - [ ] Router
- 場地：青平台
    - [x] 食物 - 當天決定，2:10pm 下訂單, include 青平台
- 13:30 - 場佈, 在樓下帶人
  - [x] 拿著編輯小聚牌子在樓下等 - bil
  - [x] 排桌子椅子
  - [x] 麥克風
  - [x] 電梯間引導牌子
  - [x] WIFI
      - [ ] 佈機x2
      - [ ] 連結 netgear 與 asus WAN port
      - [ ] 白板寫 SSID Cofacts meetup(_5G) + wifi password
      - [ ] 192.168.2.1 進入 netgear admin 看 asus 的 IP
      - [ ] 開好兩台 router admin 監測連網狀態
      - [ ] (optional) netgear 換成 5GHz only?
  - [x] Slido - 白板寫 slido number
  - [x] 產生本日 spreadsheet - 文武
    - [x] 貼社團
    - [x] 生短網址貼 slide
    - [x] [產生 QR code](http://www.quickmark.com.tw/cht/qrcode-datamatrix-generator/default.asp?qrLink) 貼 slide
  - [x] 投影的電腦開好：
    - [x] browser tab: [投影片]((https://docs.google.com/presentation/d/1QCAPtwkxreQ4EUtIWsOgR4c8h4tkRs22Qvv7jBFNrfI/edit#slide=id.p))
    - [x] browser tab: [Instant](http://cofacts.g0v.tw/instant)
    - [x] browser tab: [KKTIX](https://cofacts.kktix.cc/events/cofacteditor16)
    - [x] browser tab: [Slido](https://wall.sli.do/event/orysnkjm?section=288aa08c-69c3-4469-8b14-c213a90fc921&info_modal_version=v1)
    - [x] BGM
- 14:00 - 14:20 自我介紹＆真的假的闢謠簡介
- 14:20 - 16:00 很有效率光速闢謠100分
- 16:10 - 16:40 闢謠也聊聊時間 / slido 大哉問
- 16:40 - 17:00 自由交流 & 大合照

:::danger
- [x] 開場使用材料更新：https://docs.google.com/presentation/d/1QCAPtwkxreQ4EUtIWsOgR4c8h4tkRs22Qvv7jBFNrfI/edit#slide=id.g1ffc87ef17_0_23
- [x] 改[instant文案](https://github.com/cofacts/rumors-site/blob/master/pages/instant.js#L9-L87) - https://github.com/cofacts/rumors-site/issues/167
:::

## 宜蘭社大
> 活動主題：「讀」新聞？「毒」新聞？
> 討論議題：拒絕被動接受假消息！理性判斷很重要！ 
> 活動日期：108年10月29日（二）
> 活動時間：晚上7：00～9：10

> bil: 如果是在有電腦的地方，不嫌棄的話可以線上與談

:::success
GGM 會去
:::

## 敬邀真的假的Cofacts團隊　擔任11/16(六)「新聞與言論自由論壇－假新聞的起源、目的與產出結構」與談人事宜

:::success
MrOrz 參加完 g0v 忘年會之後出席與談
:::

## 分析「請問您在哪裡看到這個訊息」

### 「在哪裡看到此訊息」能否擋住亂傳

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9c4f6800b268d7ce4e7ab54e40fa239c)

「自己輸入的」的數量:

- 即時資料： https://datastudio.google.com/reporting/8b715296-0032-4c46-bb2e-9da8db6c19c3
- Raw Log (2019/9/01~2019/9/30) - 非公開: https://datastudio.google.com/reporting/9e3389be-a839-44bd-9d23-c3e4460a5be4
    - 顯示「在哪裡看到的」選項: 2,811 (100%)
    - 使用者選擇「自己輸入的」: 174 (6%)
    - 使用者選擇其他選項: 1,169 (42%)
    - 使用者沒有後續選擇: 1,468 (52%)

「自己輸入的」的文句，與其他選項的文句


ggm:
讓他選有個意義是可以知道從哪裡來的
但那個官方帳號的不知道要不要多一個分類
寫 LINE@ 給他選好像也不錯

mrorz
可是現在是不是不叫 LINE@


【方案1】
之前想的分類：https://github.com/cofacts/rumors-line-bot/issues/121#issuecomment-507626233

但是會重複
例如說永和教堂 是地方還是宗教

ggm
這樣大家就會不知道要選哪一個

orz
還是就 5 個選項

【方案2】

1. 有人在 LINE 群組裡分享的
2. 有人用 LINE 傳給我的
3. LINE 官方帳號廣播
4. 我在 LINE 外頭看到的
5. 我自己寫的

4, 5 --> 陷阱

- - -

【方案3】
LIFF 版
1. LINE 裡面看到的：（輸入框）(選填)
2. 我在 LINE 外頭看到的
3. 我自己寫的

orz: 但 LIFF 要用按鈕請他點開然後再點擊或輸入，
填完之後直接在裡頭完成填理由送出

ggm 這樣似乎會看不出來群組跟官方
其實滿多人會問「你知道謠言是哪裡來的嗎」

- - -

【方案4】
LIFF 版
1. LINE 群組裡看到的：（輸入框）(選填)
2. LINE 官方帳號廣播的：（輸入框）(選填)
3. 有人私下用 LINE 傳給我的
4. 我在 LINE 外頭看到的
5. 我自己寫的

orz: 但 LIFF 要用按鈕請他點開然後再點擊或輸入，
填完之後直接在裡頭完成填理由送出

bil
可以慢慢改，不要一開始就放輸入框，讓大家練習(在 LIFF 裡)選 radio button
讓大家練習

orz
先看官方帳號多不多 還是群組多 還是私訊多
再決定要不要 input 也可以

:::success
- 【現狀】親戚 同事 朋友 自己 : 
- 【方案1】自己 家族 宗教 地方 公共議題 官方 私訊 其他 : 
- 【方案2】群組 私訊 官方 外面 自己 : bil
- 【方案3】LINE裡(輸入框) 外面 自己 (整合理由發送) : 
- 【方案4】群組(輸入框) 官方(輸入框) 私訊 外面 自己 (整合理由發送) : ggm, bil(無選填，只有選項)

- - -

--> 【方案4】但是是沒有輸入框的版本
仍然使用 LIFF，未來保留彈性
Ticket: https://github.com/cofacts/rumors-line-bot/issues/145
:::

### 目前資料是否有用（選項鑑別度）

> 來自官方帳號的訊息要選哪個？「官方帳號推播」選項？

:::success
見上述討論，改選項。
Ticket: https://github.com/cofacts/rumors-line-bot/issues/145
:::

## Facebook bot

> Last discussion: https://g0v.hackmd.io/@GuJ5fZ3uR-O09mlTi1w2UQ/rJUCYp2SB#Facebook-chatbot

> Github issue: https://github.com/cofacts/rumors-fb-bot/issues/4

### 公告 FB bot 上線文案
:::info
粉絲頁、社團、LINE 主頁、LINE bot 公告
:::


## Rumors-site 升級 next9

PR:
- New reply form: https://github.com/cofacts/rumors-site/pull/168
- Connect reply: TBA

1. [x] Article list --> PR to dev
2. [ ] Article page （見 API 更新）
3. [ ] Reply list
4. [ ] reply page


### 主機轉移

ES 對外

:::success
下一次來做
:::


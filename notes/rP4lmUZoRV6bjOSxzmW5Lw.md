---
tags: cofacts, meeting note
---
20200205 會議紀錄
=====

> mrorz, bil, 文武, Lucien
>
> 上次開會紀錄：https://g0v.hackmd.io/@mrorz/ryMFmcC-I
>

## 小聚 rundown
- 誰會來呢？ MrOrz, bil, 文武, 蝴蝶, ci, lucien
- 週三會議
    - [x] 開場使用材料更新：https://docs.google.com/presentation/d/1QCAPtwkxreQ4EUtIWsOgR4c8h4tkRs22Qvv7jBFNrfI/edit#slide=id.g1ffc87ef17_0_23
    - [x] 行前通知：提醒時間、地點、電腦、電源、杯子，不來的話請退訂
:::info
Cofacts 編輯小聚行前通知

編輯小聚就在這個週六（2/8）2:00PM，在 NPO Hub（ https://g.page/NPOHUBTaipei 4樓）舉行唷！

當天活動會用到 💻 筆記型電腦、🔌 電源，現場備有茶水 🚰 歡迎攜帶環保杯。

若不克出席，也可以盡快取消訂單，將位子讓給有興趣的朋友 :)

期待在週六看到大家～～
:::


- 週五
    - [x] 看有沒有退訂後多的位子，有的話在 FB 發文
- 攜帶
    - [x] 貼紙 - bil
    - [x] 簽到單 --> KKTIX 可列印 - mrorz (  )
    - [x] 黏土
    - [x] 編輯小聚的牌子、電梯間引導牌子 - mrorz https://drive.google.com/drive/folders/1n22lrzMQ4MJCE8CeLhINDxLR2FppQtHZ / ibon 列印：4023625327
    - [x] Wifi 機 - mrorz
        - [x] Netgear 本體
            - [x] usb type-c 充電線與插座
            - [x] 電池
            - [x] 4G 天線
        - [x] Asus RT-N12
            - [x] 電源線
            - [x] 5dBi 天線
            - [x] RJ45 線
- 13:30 - 場佈, 在樓下帶人
  - [x] 引導牌 (https://drive.google.com/drive/folders/1n22lrzMQ4MJCE8CeLhINDxLR2FppQtHZ)
  - [x] 排桌子椅子
  - [x] 麥克風
  - [x] ~~WIFI~~ 好想 built-in~
      - [ ] 佈機x2
      - [ ] 連結 netgear 與 asus WAN port
      - [ ] 白紙寫 SSID Cofacts meetup(_5G) + wifi password 貼牆上
      - [ ] 192.168.2.1 進入 netgear admin 看 asus 的 IP
      - [ ] 開好兩台 router admin 監測連網狀態
      - [ ] (optional) netgear 換成 5GHz only?
  - [ ] Slido - 白紙寫 slido room number `#cofacts18`
  - [ ] 產生本日 spreadsheet - 文武
    - [x] 貼社團
    - [ ] 生短網址貼 slide https://bit.ly/COFACTS-20
    - [ ] 生短網址貼 slido
    - [ ] 產生 QR code 貼 slide
  - [ ] 投影的電腦開好：
    - [ ] browser tab: [投影片](https://docs.google.com/presentation/d/1QCAPtwkxreQ4EUtIWsOgR4c8h4tkRs22Qvv7jBFNrfI/edit#slide=id.p)
    - [ ] browser tab: [BigNum](https://cofacts.github.io/community-builder/#/bignum?start=2020-05-31T14%3A00&panels=replied&panels=feedback)
    - [ ] browser tab: [KKTIX](https://cofacts.kktix.cc/events/cofacteditor20)
    - [ ] browser tab: [Slido]()
    - [ ] BGM
- 14:00 - 14:20 自我介紹＆真的假的闢謠簡介
    - [ ] 食物
        - [ ] 建中黑糖冰的熱食？
        - [ ] 仙草 https://deliveroo.tw/zh-tw/menu/taipei/nanjichang-night-market/fairy-grass-brothers-home
        - [ ] 豆花 https://deliveroo.tw/zh-tw/menu/taipei/section-2-tingzhou-road-nearby/yu-chen-douhua-shop

- 14:20 - 16:00 很有效率光速闢謠100分
- 16:10 - 16:40 闢謠也聊聊時間 / slido 大哉問
- 16:40 - 17:00 自由交流 & 大合照

## 開發相關

### Rollbar quota exceeded QQ

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6d40e649ae77335ad2bd44200991fa62)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9f4f38a2dc63c4538392db88446fa8dd)

#### Corresponding tickets
https://github.com/cofacts/rumors-site/issues/209
?????

https://github.com/cofacts/rumors-site/issues/208
理論上 nextjs 有 babel-preset-env --> corejs --> 應該要有 polyfill????

### New issues
- back button issue https://github.com/cofacts/rumors-site/issues/211

### 開發中

Rumors-site 轉 cluster mode
- site-zh: 2 instances
- site-en: 1 instance

### PRs

- 修正 rumors-api Hyperlink resolve 錯置問題：https://github.com/cofacts/rumors-api/pull/140 (先上 production 了)

- Rumors-line-bot 轉 cluster mode： https://github.com/cofacts/rumors-line-bot/pull/153

:::warning
TODO: 分析有多少 URL 被錯置。
時間區間：
url-resolver 新版上線～2020/2/1 為止
:::

### Rescaled Dynos
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a55ec2ec4917573cd4fba844d59bccaa)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0ce6e5a9eba20f1a105f541c6ab66274)

其實還是會爆記憶體（其中一台）：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7f0138875fe371097029ade7e0f8f0fb)


## Access rules to resources
- 專案主：最早期投入、有持續產出、了解專案、有最多貢獻、花最多時間
- 核心團隊
    - 核心團隊的定義：固定開會、聯絡得到人、持續有大量貢獻受專案主協調理解、有貢獻/工作承諾、喪失一點點自由
    - 一個月開會3次以上(線上 or 實體)
- 來開會的人：核心團隊工作成員(邀請制)限定邀請
    - 類似 jothon, g0v-talks

- cofacts mailing list：核心團隊
- Facebook Public Group：管理員為有意願的核心成員
- KKtix：管理員為有意願的核心成員
- LINE 後台：管理員為有意願的核心成員
- Medium：投稿制，對社群開放。核心團隊成員負責管理。

- 伺服器root：管理員為有可以登入權限，有意願的核心成員可登入。

---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20241125 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO Hub 出席：bil, mrorz, nonumpa
- 線上出席：T
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API

Admin API scaffold release https://github.com/cofacts/rumors-api/releases/tag/release%2F20241125
- https://admin-api.cofacts.tw/ with `/ping` now available

### :rocket: Staging

#### :globe_with_meridians: Site

- https://github.com/cofacts/rumors-site/pull/581 & https://github.com/cofacts/rumors-site/pull/583 belong112

##### Testing checklist
http://dev.cofacts.tw/

檢查 feedback 是否為
- [x] 有文字的在前面，沒文字的在後面
- [x] 都有文字 or 都沒文字：新的在前面，舊的在後面

### :eye: Under review

- Badge schema https://github.com/cofacts/rumors-db/pull/74
- blockUser admin API https://github.com/cofacts/rumors-api/pull/352
    - Unit test: broken after order switch

## 大松檢討

> https://g0v.hackmd.io/@cofacts/meetings/%2FXSpjp40-QEGVAPeTrvxZeQ

## CCPRIP

### [Op] Automated spam removal

> Design doc: https://g0v.hackmd.io/@cofacts/rd/%2Fum7DyY_ESbu2LL78kLw3pg


#### Phase 1: Script execution automation
> MrOrz

https://github.com/cofacts/rumors-api/pull/352
- Still debugging
- 可以穩定重現、每次都死在相同的 test
- PR 之外的 master 不會有此問題

#### Phase 3: Automated detection
> nonumpa

- gemini usage 要傳到 langfuse 才能算 token

https://langfuse.cofacts.tw/project/cm3n1h0xu000mfdgamwhs63t2/traces/0c51f6d8-7146-4a2f-8d3a-3a3d4ae6d5ec?observation=518cc920-4cf4-4240-a30d-22f946c9c463
- few shot reason 放在判斷前面，可以把為何是 or 不是的理由交代清楚一些，幫助 LLM 思考（chain of thought）
- 格式：few shot 可以考慮直接使用 user / assistant。user 放 sample input, assistant 放 sample output
- 如果真的不行，考慮放棄 JSON mode 看會不會變好 https://arxiv.org/abs/2408.02442
- 先處理單則 OK

### [Infra] Downtime

- 2024/11/24 17:23~18:50 疑似倒站 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e236f0a5cdf5065d4f7e16d654a95fc1.png)
- 2024/11/24 17:00 ~ 11/25 14:27 台灣 LINE bot 下線 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8fa43bd45c7b9cf4a11e3fe2b1d00ebd.png)
- 2024/11/24 17:00~18:00 CPU & disk IO 很高 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_14551a3f290f76a90da425f0bbb53481.png)，應該是 memory ＆ swap 滿了

:::info
Record to https://hackmd.io/@cofacts/incidents
:::

### [Infra] DDoS 帳單攻擊預防

[鬼故事 by ihower](https://www.facebook.com/share/p/18HpYzXc1Q/)：

> 大約半年前，我客戶網站上的一張放在 Google Cloud Storage (台灣 asia-east1 區) 的圖片，被 DDoS 攻擊，持續下載同一張圖片(500MiB/s，每秒 8k requests 來自歐美的七個 IP 位址) 持續了兩天。雖然發現後立即加上 Cloudflare 防火牆 (還是免費版即可，早知道就..... 哎) 就擋住了，但仍造成了約 USD 11,000 的鉅額 GCP 帳單，而這平常一個月的流量只需要 USD 15 元。
>
> 後續透過代理商 i 社多次和 GCP 爭取退款或流量費減免，在經歷長達半年的焦慮等待，包括無數次的客服聯繫、反覆確認攻擊細節、通知X部門審查、確認我身份、申請至Y部門、再等待Z部門確認、被拒絕後重送工單 N 次(感謝代理商持續跟進)。最終 Google Cloud Billing Support 的回覆仍是申請失敗，僅爭取到 Google 業務給予的 USD 2000 補助 credits。

Lessons learned by iHower: https://www.facebook.com/ihower/posts/pfbid02NSGjkquioV7TEq5GpTCRnK9uT38NDTqEgzT31x2w8hmTgF5GLZFKWXy3zPzT66sBl

- ✅ 設定帳單提醒
- [在 GCS bucket 前擋 Cloudflare](https://stackoverflow.com/a/35895422/1582110)：好像要[設定 load balancer](https://cloud.google.com/load-balancing/docs/https) 或把[整個 bucket 改名字](https://cloud.google.com/storage/docs/hosting-static-website-http)才能綁網域
    - 直接把 GCS 的網址對外，即使是 signed URL 也是可能被攻擊 

---

#### Possible Solution: GCS bucket --> Cloudflare R2

Thanks to @alex for proposing the idea!

Pros
- [No egress fee](https://developers.cloudflare.com/r2/pricing) 而且 class A & B operation 比 GCS 的便宜
- [Sippy](https://developers.cloudflare.com/r2/data-migration/sippy/) incremental migration
    - 可以先只改 rumors-api 輸出 URL 的部分，讓它輸出 R2 URL

Cons
- 未來開發 Gemini transcript 時，傳檔給 Vertex AI 似乎一定要用 GCS，因此 GCS 上傳還是不可少
- Cloudflare 無法開發票（好像要企業版），需走墊款流程
- by bucket 只能設定 [location hint](https://developers.cloudflare.com/r2/reference/data-location/#location-hints)，精確度到「APAC」--> 代表可能會被放到[日本、新加坡、甚至⋯⋯中國？](https://www.cloudflare.com/network/)
- 如果只用 sippy 而不是整個搬去 Cloudflare R2，會有以下兩個問題
    - Double 資料存放費用 (GCS & Cloudflare) --> 但 cost 很少，即使乘二也不貴
    - 如果要下架圖片，要記得改 Cloudflare 這端的圖
      - 下架是否即時？[name=nonumpa]
        - 不確定是否有 cache，但他都做成 R2 服務了，應該知道我想更新某檔案 [name=mrorz]

:::success
記錄到 CCPRIP 的 infra layer
:::

## 檢舉怪象

- 「磨告」
- 目前沒有搜集檢舉人 Email ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_695b3f7e97398b4508d893292f166598.png)
- 是否有從 LINE 開 cofacts 網站檢舉的人？有的話，那瀏覽器不會有 google 帳號
  - 網站 URL 檢舉可以加 `openExternalBrowser=1` 確認大家都是用瀏覽器檢舉 [name=mrorz]

:::success
已開啟 collect email addresses: Verified
現在檢舉要先登入 Google
:::

## Langfuse

Design doc: https://g0v.hackmd.io/@cofacts/rd/%2FccwZjCTnQ4-I5sPO1tuvFg

## 小聚籌備

- [ ] 日期：01/05 (日)   - 2025 skedda 還沒有被借走
- [ ] 食物：
- [ ] 場地：NPO Hub Foundry（大的那間)
- [ ] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Slido 暖身
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：
  - 推播日：12/27 or 12/22
  - 目標：雙北
- [ ] KKTIX: https://cofacts.kktix.cc/events/cofactseditor45
- [ ] 誰會來呢：bil,orz,nonumpa
- [ ] 記得帶：貼紙、環保杯
- [ ] LINE 文案： TikTok 上熱門到轉傳給 LINE 的影片說皮蛋在顯微鏡下都是會四處蠕動的寄生蟲，真的假的呀？這其實是一個合成過的影片，前半段雖然真的是把皮蛋切片放在載玻片並用顯微鏡觀察，但後半部有蟲蟲危機的片段卻是合成剪接後的結果。顯然眼見為憑並不為真。網路上許多影片圖片需要你的查證公開，就能幫助更多身邊的人。 Cofacts 真的假的 第 45 次志工查核工作坊需要你的加入，活動完全免費，（請自備電腦）最近的捷運站是中正紀念堂站，連結內報名：https://cofacts.kktix.cc/events/cofactseditor45
- [ ] VOOM 發文
- [ ] FB 發文

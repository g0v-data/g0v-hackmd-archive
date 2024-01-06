---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20230511 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis: Bil, MrOrz
- 線上出席：nonumpa, 4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: rumors-line-bot

Chatbot connects to GCP with Application Default Credentials
- https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20230504
- https://github.com/cofacts/rumors-deploy/pull/23


## CCPRIP

### [Comm] Transcript
> https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ
> nonumpa

改個 repo 名字
https://github.com/cofacts/collab-server

目前是直接用 node+env 啟動，不知道要不要改成 pm2+ecosystem.config

[`Prettier` end of line](https://prettier.io/docs/en/options.html#end-of-line) 問題
> default value changed from auto to lf in v2.0.0

- test, CI 不知道要不要 [name=nonumpa]
- rollbar 監控 error [name=nonumpa]
- Push built image to docker-hub
  - Github action that pushes docker image
  - or to [Github container registry](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry)
- Elasticsearch mapping
  - Ex: https://github.com/cofacts/rumors-db/blob/master/schema/airesponses.js
  - 因為是丟 blob 所以 elasticsearch 自動判斷為 data [name=nonumpa]
  - 那就不用 mapping 了 [name=orz]
- Send PR to change docker-compose: https://github.com/cofacts/rumors-deploy/blob/master/docker-compose.sample.yml

:::success
目標：下週可以 deploy built docker image 到 staging
:::

### [Comm] LLM-aid fact checking
> https://g0v.hackmd.io/@cofacts/rd/%2FmU8qi721RZeAQ9PDfj7XRA

New scenarios
- Claim extraction
- Automatic groundness checking with Auto-GPT

---

- 可以 google 這件事情值得一試 [name=bil]
- 入班教學也是判斷爭點找資料，機器人可以做也不錯

:::success
研究 Auto-GPT 的 prompt 與 memory 的取捨設計
:::

### [Op] 分身帳號處理

https://g0v.hackmd.io/ndNDmEkiSHyTRMOEIy2q2Q (非公開)

## Access of open data

>  目前 Cofacts dataset 是靠使用者填寫 Google form 加上 Apps script 自動 share Google drive access to CSV files 來分享的，以確保每個下載者都有讀過 license。但我的 apps script 美 7 天會被 revoke access 要重新 authorize，過去幾年來每週都要重新 authorize 然後檢查有沒有漏掉的使用者，真的是滿煩的。
> 我最近才發現原來 huggingface 可以放 data set 而且可以設定 gated access，就是要留下 email 申稱自己有讀過 license 才能 access：
> https://huggingface.co/docs/hub/datasets-gated
> 我希望這麼做可以
> - 提升 Cofacts dataset visibility & usage
> - 維持追蹤 Cofacts dataset 的 user
> - 追蹤 Cofacts dataset use case (做得到嗎？)
> [name=mrorz]
> 
> 我自己是沒有在HF 上面用 datasets 過，不過這個使用場景的話在 HF 上應該是比較方便追蹤的沒錯
> 追蹤 use case 我猜在 additional customization 那邊要他們加上 citation 或是附上他們 github repo 搞不好也行？（就可能 optional 不是 required 的欄位這樣）
> 注意的地方我目前有想到的就是說明用的語言，中文英文都要有之類的？
> [name=cheng-hung pai]

## GA4

- BigQuery script that generates a table https://github.com/cofacts/rumors-db/pull/62/files#diff-1ed164d31676d310c37469dad892e1a676cd6ccbe2c3e501805b1d46e84d2a1d
- Write chatbot events to BQ https://github.com/cofacts/rumors-line-bot/pull/351/files

## Facebook apps

> https://developers.facebook.com/blog/post/2023/02/01/developer-platform-requiring-business-verification-for-advanced-access/
> 剛發現 FB 在 2/1 有改了 FB 登入的 advaneced access 權限的規定，改成一定要商家認證才能使用，針對舊的 App 也有說 7/1 之後也有強制認證，否則 8/1 就會失效
> [name=ronny]
> 

- 不做會怎樣
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_81d0f97c39cc08fbf2d1bd7d5aaec104.png)
    - `email` & `public_profile` 是 Advanced access，不做驗證的話就會拿不到
- [Business verification](https://www.facebook.com/business/help/1095661473946872?id=180505742745347) 對象：「商家或組織」
- 要提供[正式聯繫方式](https://www.facebook.com/business/help/2058515294227817?id=180505742745347)
    - Email 必須要在網站 domain 下
    - 電話號碼 / 簡訊要上傳帳單證明這是 business phone number
- 需要[政府文件](https://www.facebook.com/business/help/159334372093366)
    - 須確認這些文件尚未失效，且由相關機關核發
    - 語言：支援 Mandarin
    - 接受的文件類型
        - 公司登記執照／公司組織章程
        - 營利事業登記證或許可文件
        - 政府核發的營業稅務文件：這包括扣繳憑單。我們不接受自行填寫的文件。
        - 企業銀行對帳單
        - 水電帳單：水電帳單僅適用於驗證**商家地址**和**電話號碼**。水電帳單上必須包含**法定企業商家名稱**。若要驗證企業商家名稱，水電帳單並非可接受的文件

## 小聚籌備

### 台南新芽

- [x] 地點：
  - 2023/5/27 2pm - 5pm
  - 台南新芽 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_467d6f751c9c90edbde9615261ce0983.png)
三張大桌子，坐15人以內舒適，有延長線跟飲水機和廁所，開門即會場。當天會有新芽工作人員陪伴
- [ ] 食物？統編？
    - Maybe 双生綠豆沙？
- [x] 場地費：轉帳新芽
- [x] 時間：
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
- [x] 投放目標：台南、高雄、嘉義 57,000 人
- [x] KKTIX:https://cofacts.kktix.cc/events/cofactseditor37
- [x] 誰會來呢：bil, mrorz, nonumpa
- [ ] bil要記得帶的：杯子、貼紙、粉粉文宣
    - 需使用實體車票
- [x] LINE 文案: 
「台南市被列入全台10大疫情危險縣市？」假的！！中央流行疫情指揮中心並沒有列出10大疫情危險縣市。
活動不該只辦在台北，Cofacts 真的假的要到台南舉辦志工培訓活動啦！！5月27日(六)14:00-17:00 歡迎沒有經驗的你，用一個下午的時間當鍵盤志工，一起對抗假新聞！請自備水杯、筆記型電腦與充電線唷！
台南新芽地址：台南市中西區成功路29號4樓(賀聲助聽器樓上，一樓有電梯）

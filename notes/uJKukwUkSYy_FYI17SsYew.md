---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20201216 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, hsiao, nonumpa, lucien, cathy
:::

## 開放授權變更

Follow-up 已經更新：https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2FNqPf1SfPQEGOZ3Z6h7Q7wA

### 執行方式

> 需確認下面作法是否具有效力

- CC BY-SA 的姓名標示方式請見 https://github.com/cofacts/opendata/pull/19
- Cofacts opendata 檔案庫台灣時間 2021/1/1 0 點以前所發布的 commit 將維持 CC0 授權開放到公眾領域，但 2021/1/1 0點之後發布的 commit 的資料，都將以新授權發布。
- Cofacts API 在 2021/1/1 0 點起所提供資料，都將視為以 CC BY-SA 發布。屆時，發往 Cofacts API 的 request 都需要加上 x-accept-license header，否則API server 將會以 412 Precondition Failed 拒絕連線（見 https://github.com/cofacts/rumors-api/pull/240 ）


### UI 要改的部分

https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/Cofacts-website-MrOrz-s-copy?node-id=2807%3A220

> 點擊發布變更後，表示您同意我們的使用條款。
> 同時您同意依據CC-BY-SA-3.0和GFDL條款授權您的貢獻，並在CC-BY-SA-3.0的條款下以超連結或URL的方式進行署名。
>
> -- Wikipedia

> 登入或註冊即表示您同意使用者條款，以 Cofacts 社群的名義，將您在本網站輸入的內容以 CC BY-SA 4.0 條款釋出為開放資料。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a3dc56510304ecf966e865d99fba493a.png)

> 其他地方（輸入 reply request, reply, article reply feedback）還要重複嗎？

- 登入時說就可以了 [name=bil]

### Attribution
見：https://github.com/cofacts/opendata/pull/19/files#diff-b335630551682c19a781afebcf4d07bf978fb1f8ac04c6bf87428ed5106870f5

:::success
無論寫訊息的人是誰，都用下面的名字
- Cofacts 群眾查核社群
- Cofacts crowd-sourced fact-checking community
:::

### API、網站與 chatbot

- 確保所有 API 使用者知情：https://github.com/cofacts/rumors-api/pull/240
- rumors-line-bot、rumors-site 一樣要給 `x-accept-license`
- 網站與 LINE bot 也要示範 attribution？
    - nice to have, 因為管理者都在這邊 [name=bil]
    - 是否要放一下，作為示範作用，因為網站也會送 x-accept-license，可能會有人抱怨說為什麼這個網站可以自己違反 license (?) [name=mrorz]
    - 示範也是自己對自己的要求，本身非必要 [name=bil]

:::success
【action item】
mrorz:
發 line-bot 跟 rumors-site 的 PR
加送 x-accept-license 以及加上 consent 字串

bil:
使用者條款
:::

## Dialogflow

### Intent 回應統計
https://datastudio.google.com/reporting/1be09256-0931-4d3a-8e6b-8256fbce5ea3/page/2ZRtB
- 使用者說「謝謝」之後是否要請他幫忙轉傳回應？
    - 要先抓說他上一步是不是在查 [name=nonumpa]
    - 送 context 進 dialogflow 來設定 [name=mrorz]

:::success
先放著，下週看數據與 review 需求
:::

### Best practices
https://cloud.google.com/dialogflow/es/docs/agents-design
- fallback intent 的 training phrase = negative example


- 朋友發現可以跟 bot 對話之後就開始亂玩 [name=nonumpa]
    - 試了其他 bot 可以接受的
    - 發現很多都不能 match 到
- small talk?
    - 英文翻過來的，沒有太多參考價值

:::info
研究看看怎麼過濾出出現多次、沒 match 到、字數也短的訊息
:::

## TWB

> Subject: Fwd: 【臺灣吧】Cofacts真的假的機器人場物修改版

確定物件稿

- cut 20 改「我想補充」--> OK
    - please provide more info 按鈕之後會改中文
    - 40 字以上才會變成「送出」按鈕
    - 可以改 (?)
- cut 24 送出流程保持原樣 --> OK
- cut 27 右下角新發現 --> 改「我想補充」or 寫新回應？

## AI4SG

bil 已經填完在 Google doc，請 ggm 補技術的部分

## :potable_water: Release pipeline

### :star: Released to production
#### :robot_face: LINE bot
https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20201211

### :rocket: Staging

#### :globe_with_meridians: Site

- #358 Fix reference in "add this reply"

確認無誤即可上 fix

### :eye: Under review

#### :globe_with_meridians: Site
- #357 Openpeeps avatar
- #356 landing page
    - Check what will a spider see
    - og-image 要用哪張？
        - `line-banner-mobile@2x.png`


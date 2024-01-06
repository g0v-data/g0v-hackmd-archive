---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20230817 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz
- 線上出席：nonumpa, cai
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

- feat: record less bytes in GraphQL request [#312](https://github.com/cofacts/rumors-api/pull/312)

#### :robot_face: rumors-line-bot

- [fix(initState): typing gql and initState API response #355
](https://github.com/cofacts/rumors-line-bot/pull/355)
- [fix(webhook): typing webhook request handler #356](https://github.com/cofacts/rumors-line-bot/pull/356) LY++
- [fix(tutorial): typing functions in tutorial #358](https://github.com/cofacts/rumors-line-bot/pull/358) LY++
- Searching text will highlight transcripts in article list [#359](https://github.com/cofacts/rumors-line-bot/pull/359/files)

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 應可送出「全新訊息」
    - [x] 選擇「轉傳訊息」後會詢問是否要送出訊息。
    - [x] 同意送出訊息後就會送出訊息，並得到：
        - [x] Cofacts article page 按鈕
        - [x] 寫理由的按鈕

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應
    - [x] 選擇回應之後可以幫回應 upvote
    - [x] 可以再次選擇 downvote
    - [x] 選完回應之後，還可以捲回去選其他回應

- [x] Rich menu 測試
    - [x] 「設定」更改後再次打開，應該會保留原本設定
    - [x] 「教學」可以觸發教學流程
    - [x] 可點入「查過的訊息」、點擊查過的訊息可以在 chatbot 列出

##### ⛔️ Release Blockers

##### 未竟項目

- 傳 100% match 的逐字稿，會直接說已經送進資料庫，不會要求送出 [name=nonumpa]
  - 如果是資料庫已有圖或影片，那 100% 相似的文字我覺得不用送。
  - 但如果使用者傳圖片，資料庫有 100% 相似的文字的話，我還是會想要收錄圖片。
  - 這會在下一個 PR 處理 [name=mrorz]

### :eye: Under review

- https://github.com/cofacts/rumors-api/pull/312
- https://github.com/cofacts/rumors-line-bot/pull/359/files

## CCPRIP

### [Comm layer] 逐字稿
> https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ
> [name=nonumpa]

#### History
> [name=nonumpa]
> PR review 還沒改完

#### Auth
> [name=mrorz]

No progress yet

#### AI

[API merge](https://github.com/cofacts/rumors-api/pull/309#issuecomment-1681643548) blocked by LINE bot similarity display
- 用文字搜到 trancript - https://github.com/cofacts/rumors-line-bot/pull/359
- 用圖（的 transcript）搜到 transcript -- 還沒做
    - Merge `processImage` & `processMedia`
        - 加入逐字稿之後，是否為圖都一樣可能會有各種 response，故不再區分 image 與 video / audio
        - 但跟文字還是不太一樣；GraphQL 不太相同，且文字才會去 dialogflow
    - 因為還沒作截圖影片，所以不會顯示 transcript 的影片，只會放逐字稿
    - [relevance score >= 100](https://github.com/cofacts/rumors-api/pull/309/files#diff-4167517a97e190b8c0c392b1f3ea2fe257b9d5a07302b37f1816217ed3e03879R1015) 視為 identical？

- API 直接寫入 ydoc：not yet

### [Infra] Log cost saving

- 6 月起 AWS 帳單暴增 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ea6ed5afb483b7835d7672c06b8eb121.png)
- Breakdown: 7 月帳單裡，Cloud watch log ingestion 56GB，花費 43 USD ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9ed6ac30c996eabbccf71d14e9a0fb6f.png)
    - 與傳輸相比，儲存便宜很多。一方面是單價低，另一方面是他會再壓縮（56G transferred, 16G stored）
    - Log retention = 1 month
- Cloudwatch metrics 計算 incoming bytes per day ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c17db967f38d4be38575a5f0058e762b.png)
    - 絕大多數都是 rumors-api 的流量
    - 5 月底時為了實作 [IP logging](https://g0v.hackmd.io/luIa-z9HToC2zlFpD9yK3w#Op-%E5%88%86%E8%BA%AB%E5%B8%B3%E8%99%9F%E8%99%95%E7%90%86) 而開啟 API log
    - [6/7 release](https://github.com/cofacts/rumors-api/releases/tag/release%2F20230607) 讓 log 變得 compact 一些，但每天仍有 1.5GB ~ 2GB 的 API log
- 分析 API log 組成 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_474033ad5245bf45c979e16b40e3ab72.png)
    - 網站的 header 會一直重複，又很長 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7b2e1606815ab4736ad77d32307fe19e.png)
    - 第三方 bot 內容可能會含有私人聊天內容 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f97734cf186ad1e25fbcfbeaf71cc5b4.png)
- 改善方向
    - GraphQL server log header 只放 IP 節省空間
        - pino 的 request logging 仍會紀錄完整 header，比對 IP 即可找到完整 http header
    - 減少 GraphQl query 長度：把空白、斷行壓縮，增加資訊密度，減少總長度
    - log 不要紀錄 variables
- PR: https://github.com/cofacts/rumors-api/pull/312

## 檢舉處理

詐騙集團辯解 https://cofacts.github.io/community-builder/#/editorworks?type=2&day=365&userId=l88gyIkBrkRFoI6roVBt&showAll=1

- ＴＢＡ：分析

:::success
- 公告並移除 reply request 作者
- 其餘 CIB 帳號先放著
:::

### 無關的篇幅太長
https://cofacts.tw/reply/Cs9B_4kBrkRFoI6rqIww

:::success
- 提供 bil 聯絡方式 [name=mrorz]
- 寄信溝通 [name=bil]
:::

## 小聚

- 場地已確認（好民）
- 想另外辦社區推廣活動 [name=bil]
  - 小聚是陪青年一起查核
  - 推廣活動是理解樣態

## Design

[Figma design system](https://g0v.hackmd.io/EfM4Xqn4TA-nIXF8Njjovg#Cofacts-design-system-on-Figma)：月底有機會完成
- 技術 NextJS 13 + TailwindCSS + Typescript https://g0v.hackmd.io/@cofacts/rd/%2F%40cofacts%2FHJ_O1Xhhs
- 可能要明年才有 bandwidth 做 [name=mrorz]

## 彰化場地推薦
- 孔廟（彰化縣政府青年發展處）[name=cai]++

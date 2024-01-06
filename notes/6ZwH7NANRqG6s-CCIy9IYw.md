---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210428 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, lucien
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :robot_face: rumors-line-bot

- #248 Cofacts GraphQL
- #250 Article LIFF Proof of concept

發現 iPad 版 LINE 沒有 rich menu QQ
但 iPad 版 LINE 可以開 LIFF XD

#### Deploy 注意

要記得改 rich menu 的 LIFF URL cache busting

### 還在做

#### :globe_with_meridians: Site

- Tico integration

## 防詐顯名

Cofacts 提議停止接取 API，並提出兩方案
一、趨勢實作機制送資料回 Cofacts API
二、Cofacts 實作 Article LIFF

結論

1. 趨勢 4/29 停止接取 Cofacts
2. 趨勢科技預計採方案一

## [LIFF article page](https://g0v.hackmd.io/0RX4MsjRRJmBqJSKVilWMA#article-amp-reply-LIFF)

1. [x] LINE bot LIFF 可呼叫 Cofacts API https://github.com/cofacts/rumors-line-bot/pull/248
2. [x] Proof of concept implementation https://github.com/cofacts/rumors-line-bot/pull/250
3. [x] Article LIFF 設計 https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/?node-id=3004%3A224
    - 是否在 vote 前顯示 vote 數？
        - 可以不顯示，不要影響使用者 [name=lucien]
    - Vote 完之後怎麼顯示？如何編輯？
        - vote 完之後可以放在按鈕上
        - button 相當於 tab，reason form 放在下面
        - 可以有個編輯按鈕 [name=lucien]
        - 整塊淺綠或淺紅表示之前輸入的狀態，淺色代表已經做過了所以不用那麼顯眼 [name=mrorz]
        - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1b68fbb2e18de041e7328b1f8aa8de76.jpg =x400)
        :::success
        先畫 feedback 後的設計
        :::
4. [ ] 實作 article & reply
5. [ ] 實作 feedback form
6. [ ] 實作 reply request list & form
7. [ ] 實作 related article


> Design considerations [name=mrorz]
> - 內文字至少 16px，且避免橫向排版，給調大系統字體的使用者預留空間。
>   - LINE 使用者有回報，當網站傳給長輩的時候，長輩看不到。
>   - 其他 Fact checker 網站的內文字體，有些甚至到 18。
> - 由於字要大，所以目前的版本把 card 左右與螢幕貼邊，省下橫向空間放更多字。
>   - 目前作法參考 FB mobile app 的外觀。
>   - 不過其實像 snope 網站在 mobile 上其實還是 card view 的樣子，所以如果有需要，還是可以試排一個更接近目前網站外觀的 card view。
> - 資訊架構，按照 LINE 使用者需求來重構：
>   - 網站同時要滿足 fact checker 需求與查謠言的人的需求，而且有較大揮灑空間，所以資訊呈現上可以較豐富；但 LINE 使用者在認知能力上可能較為受限、更容易被其他東西 distract，所以設計上會拿掉網站有呈現的一些資料。
>   - 使用情境是，使用者看到一個謠言回應之後，下面有個「看詳細」按鈕。若訊息有回過，重點在 (1) 確認在問的訊息（但沒很重要） (2) 看回應、看出處 (3) 確保使用者會按 feedback
>

## 「評價過的回應」列表

- 設計 OK：
https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/Cofacts-website-MrOrz?node-id=2923%3A402
- 使用者要可以控制是否列出此分頁給他人
    - 自己看沒問題
    - 要可以控制說要不要公開整頁 [name=bil]
    - 不用做到單篇的控制沒關係
    - 可以擋在 ListArticleReplyFeedback 上，但允許從其他方式撈 [name=lucien]
    - 這樣大松前做不完 [name=mrorz]

## yegogo 處理

https://docs.google.com/spreadsheets/d/1BBObfTO7bLWERQ3nq3S1iBs3xt2o2TgOxikXqixOdYI/edit

- 每小時自動計算已知 spammer 的新回應
- 有新回應時在 cofacts-next slack #random 回報
- 已經提供 spreadsheet 連結在 cofacts/takedown，所以不用再公布
- 仍然需要手動 ssh 進主機，執行刪除指令
- 若有新 spammer 帳號，仍須仰賴人工回報
    - 跟 g0v slack 的參與者講說可以回報廣告帳號

提案：自動修掉回應中的超連結？
- 移除超連結讓搜尋引擎完全不會 index
- 已在 spreadsheet 保留原文

:::success
刪起來 --> https://github.com/cofacts/rumors-api/issues/258
:::

## Visit PDIS

問題與 solution：

1. 我們希望透過科技來做媒體識讀教育以及查核社群，因此我們期待生態系能有更多「社群經營」、「查核內容產生」的角色產生，但此預想的競爭沒有發生，取而代之的是單方面的資源取用，也就是整個生態系只有 Cofacts 輸入回應但沒有而沒有得到正向的反饋。
2. 因為沒有良性的生態系誕生，我們嘗試使用贊助資源來激勵更多人參與，像是物質獎勵優秀的查核組織與個人（例如：台灣事實查核中心），以及外包部分平台功能開發⋯⋯等等，實際上有看到其獎勵成效，但後續我們找不到一個適當切入點去跟企業與大眾募集資源，我們近期有積極與企業 CSR 洽談並同時開啟小額募捐的方式，但收效甚微，還找不到一個能引起大家願意資助專案永續的敘事方法。

---

- 生態系單向取用：
    - CC BY & Article LIFF 是試著把 Cofacts 貢獻的功能，嵌入到取用 Cofacts 的產品 [name=mrorz]
    - 查詢＆回應的人不夠多
    - 其他想法？
- 激勵內容產生者
    - 例如志工時數？
    - 政策相關的澄清？




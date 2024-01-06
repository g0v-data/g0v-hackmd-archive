---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240103 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis: bil, mrorz, nonumpa, 導演
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :electric_plug: API

- [Fix `createOrUpdateCooccurrence`](https://github.com/cofacts/rumors-api/pull/327)

#### :robot_face: rumors-line-bot

- [Refactor bubbles](https://github.com/cofacts/rumors-line-bot/pull/378)
- [Multiple msg handling](https://github.com/cofacts/rumors-line-bot/pull/379)

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 應可送出單則「全新圖片影片」
    - [x] 會詢問是否要送出訊息。
    - [x] 不同意送出訊息後可以收到感謝。
    - [x] 同意送出訊息後就會送出訊息，並得到：
        - [x] Cofacts article page 按鈕
        - [x] AI reply (依照逐字稿內容)
        - [x] 寫理由的按鈕
        - [x] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面
        - [x] 「分享到 Facebook」、「分享到 LINE」且可以正常運作
    - [x] 剛才送出的訊息應該要在「查過的訊息」列表

- [ ] 送出多則訊息（圖文）
    - [ ] 全部訊息都不在資料庫
        - [x] 詢問是否要送進資料庫
        - [x] 拒絕的話就全數停止
        - [ ] 確定的話就會送出訊息，顯示查詢結果
            - [ ] 查詢結果會包含剛才送出的訊息
            - [ ] 選擇剛才送出的訊息（還沒回應）會顯示 AI reply
            - 已知：只有 text messasge 會顯示 AI reply --> 未盡項目
        - [ ] 剛才送出的訊息應該要在「查過的訊息」列表
    - [x] 部分訊息不在資料庫
        - [x] 詢問是否要送進資料庫
        - [x] 確定的話就會送出訊息，顯示查詢結果
        - [x] 剛才送出的新訊息會出現在「查過的訊息」列表
        - [x] 從點擊現有訊息後，現有的訊息也會出現在「查過的訊息」列表
          - 不會。

    - [x] 全數訊息都在資料庫
        - [x] 直接顯示查詢結果
        - [x] 剛才查的訊息，無論是否有在資料庫，都應該要在「查過的訊息」列表

- [x] 送出「資料庫內有多則相似」的單則舊訊息，會列出相似訊息
    - [x] 若為圖片，會顯示圖片
    - [x] 如果目前查詢的不在茲料庫，會列出相似訊息、「沒有我查的訊息」選項
    - [x] 選擇「沒有我查的訊息」選項會詢問是否要送進資料庫





##### ⛔️ Release Blockers

###### Wording 怪怪
新送完之後會寫說
- 「資料庫裡有幾篇訊息接近」但一開始說沒有
- 有 100% 相似的但還是會說會「修改重發」
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_293c681d623e076fecf235017714be45.jpg)

若有送出，就改成：
「謝謝您！現在資料庫裡有這些訊息囉。」
「請選擇要查的訊息 (finger down)」

###### index 露出
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6dc8bd015388137d1433968f7ee98958.png)

0, 3 --> 應為「2 則」

###### 查過的訊息
- 現有的訊息，即使選擇了也不會跑到前面
  - (sorting?)
  - 是 sorting 問題，時間有更新
- 「查看這篇的回應」目前故障
  - 會 timeout
  - Production 也是

##### 未竟項目

- Select text article --> createAIReply
  - 變成所有都去 createAIReply, 或者是
  - 無論是哪種 article，只讀取現有的 aiReply，不要去呼叫 createAIReply
- Staging can't handle large files  https://github.com/cofacts/rumors-line-bot/issues/380

### :eye: Under review

- [Fix `createOrUpdateCooccurrence`](https://github.com/cofacts/rumors-api/pull/327)
- [Refactor bubbles](https://github.com/cofacts/rumors-line-bot/pull/378)
- [Multiple msg handling](https://github.com/cofacts/rumors-line-bot/pull/379)


## 放大視野 follow-up
https://youtu.be/11Hqe5rjA7I 放哪

文案：bil 跟 chatgpt 協作，寫出影片標題與 description 

AI Features with Cofacts chatbot
Cofacts is an open-source non-profit initiative dedicated to assisting the public in embracing a vigilant, pro-democracy attitude and actively confronting disinformation.
This video will introduce three essential features: multimedia factchecking, automatic classification, and media literacy training.

## CCPRIP

### [comm] Transcript
> nonumpa
> 

- Test updated

### [op] Transcript spam 處理
> nonumpa
> https://g0v.hackmd.io/vKCvrqSQTlm7GEx9MAXGaw?view#op-Transcript-spam-%E8%99%95%E7%90%86

- Not yet

### [comm] Cooccurrence

順序
- Fix blocker & bugs
- Implement website display cooccurrences
- 大松
- 下週週會 test & release (如果沒問題)
- 選舉
- 實作 `ASKING_CONTEXT` (Optional?)

## 實科協會

- Google 非營利
    - 初次申請失敗
    - 擇日再申請


## Microsoft Research

9:00 am, 國泰置地, 19F

## 大松籌備

> - 報名：https://g0v-jothon.kktix.cc/events/g0v-hackath60n
> - 上次共筆 https://g0v.hackmd.io/@cofacts/meetings/%2FI7J17SoFRvWyxRuAecoS1w
> - 上次籌備 https://g0v.hackmd.io/DSht8xFqRN-XXbhwE64k9Q#%E5%A4%A7%E6%9D%BE
> - 本次投影片 https://docs.google.com/presentation/d/1vCi5IpGvNEuNE7OP9o8shEiU0LYTjG_B6EX68-tY_A4/edit

- 報告：bil
- 台灣選務謠言筆記 + ~~試用 Cofacts 送出多則訊息~~？


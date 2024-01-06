---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20221207 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：mrorz, bil
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

https://github.com/cofacts/rumors-api/pull/293
- Migration flow: https://github.com/cofacts/rumors-api/pull/293#issuecomment-1339816673
- Design doc: https://g0v.hackmd.io/@mrorz/cofacts-rd/%2FXBJS-KEtScWyVCuQ9P_iNQ


#### :robot_face: rumors-line-bot

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 應可送出「全新訊息」
    - [x] 同意送出訊息後就會送出訊息，並得到：
        - [x] Cofacts article page 按鈕
        - [x] 送出的訊息可以呈現在網站上

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應

##### ⛔️ Release Blockers
##### 未竟項目

#### :globe_with_meridians: Site
##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] Article list
  - [x] Filter works
  - [x] Can go to article page

### :eye: Under review
- https://github.com/cofacts/rumors-api/pull/293
- Migration flow: https://github.com/cofacts/rumors-api/pull/293#issuecomment-1339816673
- Design doc: https://g0v.hackmd.io/@mrorz/cofacts-rd/%2FXBJS-KEtScWyVCuQ9P_iNQ

## community builder 改版

- 顯示不同數字
  - 不同 category 的總數
  - 勾選了才顯示如何？
    - OK [name=bil]
- 不同時間區段

:::success
改這頁：
https://cofacts.github.io/community-builder/#/stats

Spec
- 數字上加入 filter
  - 每個 category 一張 card
  - Article type: image / video / text / audio
  - 建立時間
- 均呈現 all messages, replied messages, has useful replies 三個數字
- 一次呈現多個 filter，跟沒有 filter 的比較
  - 按加號 add row
  - Remove row / move rows
  - compare between rows: 選擇 base row (100%)
:::

## 檢舉處理

[Penn Peng](https://cofacts.tw/article/gvpi2IQBC7Q3lHuUlote)
- 前例：[謹慎的西屯綺莉](https://cofacts.github.io/community-builder/#/editorworks?type=1&day=365&userId=j4S8C_IzEWhzF_3uk6hdEnJZrrJxnin-AGz8wDaj1iZwHVgxY&showAll=1)
> 前次判例：[name=mrorz]
> 
> 從該使用者的使用紀錄看起來，該 LINE 使用者應是一名無法理性表達「不同意」的使用者，隨意謾罵足見其水準低下，使編輯蒙受不必要之負面情緒，應可考慮對此內容或使用者進行處理。不過，Cofacts WG 目前尚無法循 LINE 使用者條款、網站使用者條款尚未含括此狀況，故如何處理仍需討論。

- 不是累犯，可以再觀察 [name=bil]
- 數量沒有回太多 [name=bil]
- 攻擊可以考慮拿掉 [name=bil]

:::success
- 清掉 "SHIT" 攻擊語句
  - 保留 downvote 本身
  - 不會 block 使用者
- 公開在 FB 問大家想法
  - OK 的話執行文字清理、在 [takedown](https://github.com/cofacts/takedowns) 紀錄
  - 未來循此例，不會在 FB 公告，但若有修改資料庫仍然會記錄在 takedown
:::

## 來信：「本人對話不實, 懇請下架」
https://cofacts.tw/article/3450r46jeit6

- 寄信人姓管（by LINE ID / google search） 但看起來與投訴文無關 [name=nonumpa]
- 看不懂被投訴的訊息跟投訴者的關聯，信裡也沒說 [name=mrorz]

:::success
無聲卡
:::

## 2023 年一月小聚
- [ ] 時間：1/14 (六) or 1/15 (日)
  - 1/7 (六) 補工作
  - 1/21, 22 除夕、春節
  - 28, 29 春節連假期間
- [ ] 場地：
- [ ] 食物？統編？
- [ ] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：
- [ ] KKTIX：
- [ ] 誰會來呢：
- [ ] 無法來：

## 網站許願

- 捐款連結
  - 放「聯繫我們」
  - Impact report 放「關於」
- 搜尋 filter
  - 未含有有效查核 / 0 則回應

:::success
Tickets:
- https://github.com/cofacts/rumors-site/issues/520
- https://github.com/cofacts/rumors-site/issues/521
:::


---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220126 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz
- 線上出席：kukka, nonumpa, cai
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### Community builder

- `userId` and `showAll` URL param for editor works page

### :rocket: Staging

#### :globe_with_meridians: Site

- https://github.com/cofacts/rumors-site/pull/470
- https://github.com/cofacts/rumors-site/pull/471
- https://github.com/cofacts/rumors-site/pull/472

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] Replies list
  - [x] Can see vote reasons
  - [x] Cannot see report abuse button
- [x] Article detail
  - [x] Cannot see report abuse button

登入自有帳號後檢測：
- [x] Replies search page
  - [x] can upvote / downvote replies
  - [x] can see and click report abuse button on other's feedback
  - [x] cannot see report abuse button on yourselve's feedback
- [x] Replies list
  - [x] can upvote / downvote replies
  - [x] can see and click report abuse button on other's feedback
  - [x] cannot see report abuse button on yourselve's feedback
  - [x] can submit abuse report for feedback
- [x] Article detail
  - [x] Can submit reply request
  - [x] Can report abuse on other's reply requests
  - [x] Cannot see report abuse button on yourselve's reply request
  - [x] Can report abuse on other's replies
  - [x] can submit abuse report for reply

##### ⛔️ Release Blockers

N/A

##### 未竟項目

N/A

## 檢舉違規處理流程

:::info
檢舉處理的網頁（公開）
https://docs.google.com/spreadsheets/d/e/2PACX-1vRdcwXdC36xfgXfSMSk527Zbel9A-__vwRXkQ0NjkzSXoSPETCFc7sI7SoaAFdPCfskugtQL-Md8JgH/pubhtml

Spreadsheet（檢舉違規內容 (回覆)，不公開）
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_50a7c5a23de66d94820a62eadaf93779.png)
:::

1. 使用者在真的假的網站按 report abuse
    - 一定要用 email 嗎 [name=kukka]
        - 本來想說可以聯絡他 [name=mrorz]
        - 拿掉好了 [name=bil]
        - 反正原本 email 也可以亂填 [name=nonumpa]
    - 機填欄位看以網後嗎 [name=kukka]
        - replyType 沒辦法，一定要在最前面，才能設定跳頁；既然有一個一定要在第一頁，就想說通通放在第一頁 [name=mrorz]
        - 把機器填的部分變成用google app script 送如何? [name=cai]
        - 對耶好像可以把 replyType 之類的欄位合併成一個，用 AppsScript 拆出資料來 [name=mrorz]
3. 使用者填寫完畢後送出
4. Google sheet 的 apps script 按照使用者輸入內容，從 Cofacts API 拉資料
    - 若使用者擅自修改 userId, itemId, itemType 等欄位，這裡就會拉不到資料，檢舉無效
5. Cofacts WG: 判斷該檢舉是否應公開。
    - 每一則檢舉送出後，預設自動公開。
    - 不公開的情形：
        - 測試用、但不方便刪掉
        - 惡意檢舉
6. 判斷其違規樣態、處置
    - `判定之違規樣態`：純文字
    - `處置`：對被檢舉內容或被檢舉人的處置。
		- noop: 判定沒有違規，不做任何事情。
		- block: 封鎖「被檢舉人」、隱藏該被檢舉人的所有內容
		- deleteReply: 僅刪除單篇回應
		- modify: 手動修改被檢舉的內容
    - `Takedown announcement`: 在 takedown 發 PR 然後 merge 後的公告 URL。一開始是空的
7. 產生 takedown 公告並發 PR
    - TBD: 發文樣板、框起要處理的對象之後，自動生成公告供複製貼上
    - 框到重複的使用者或內容的話需要 dedup
8. PR review
9. Merge PR
    - 把 merge 後的公告 URL 貼到處理完的 `takedown announcement` 處
10. 產生 CLI 指令並執行
    - TBD: 框起要處理的對象之後，自動生成 CLI 腳本指令，供複製貼上
    - 框到重複的使用者或內容的話需要 dedup

:::success
欄位改成一個 payload (JSON) + 一個 itemType 即可
:::

## 3 月小聚

- [x] 3/12 (六) 下午 2~5
- [ ] 主題：
- [x] 場地：
    - NPO Hub 2F 影響力工場（30人） 13:30 ~ 17:30
    - 旁邊（論壇、16~20 人）有基礎松
    - 走樓梯直上二樓不被門禁卡住
- [ ] 食物 
    - 疫情期間不鼓勵
- [ ] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Keyholder 介紹場地
        - 2:20 - 2:40 介紹 mission 1 - 按讚 
        - 2:40 - 3:00 進行評價 (20則)
        - 3:00 - 3:30 休息、自我介紹、交流 
        - 3:30 - 3:50 介紹 mission 2 - 寫回應
        - 3:50 - 4:30 進行回應（1則）
        - 4:30 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：北北基桃
- [ ] 事前產生 spreadsheet 25 人分工
- [ ] KKTIX：[name=bil]
- [ ] 誰會來呢：mrorz, bil, nonumpa
- [ ] 無法來：
- [ ] 做圖：用 Figma 做 [name=mrorz]
- [ ] LINE 文案

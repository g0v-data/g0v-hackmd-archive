---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240125 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
#### :globe_with_meridians: Site
#### :robot_face: rumors-line-bot

### :rocket: Staging

#### :robot_face: rumors-line-bot

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [ ] 應可送出「全新訊息」
    - [ ] 問訊息來源時選擇「我自己打的」會被擋下。
    - [ ] 選擇「整篇轉傳」後會詢問是否要送出訊息。
    - [ ] 不同意送出訊息後可以收到感謝。
    - [ ] 同意送出訊息後就會送出訊息，並得到：
        - [ ] Cofacts article page 按鈕
        - [ ] 寫理由的按鈕
        - [ ] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面
        - [ ] 「分享到 Facebook」、「分享到 LINE」且可以正常運作
    - [ ] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [ ] 可以再打開理由視窗，此時會載入上次填寫的理由。修改理由送出後，查看 article page 看理由是否有被送出。

- [ ] 送出「沒回應」的舊訊息，應可送出新理由
    - [ ] 文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。
    - [ ] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [ ] 可以修改理由送出。查看 article page 看理由是否有被送出。
    - [ ] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [ ] 送出「有回應」的舊訊息，應自動回傳回應
    - [ ] 應列出訊息所有的回應
    - [ ] 選擇回應之後可以幫回應 upvote
    - [ ] 可以再次選擇 downvote
    - [ ] 選完回應之後，還可以捲回去選其他回應
    - [ ] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [ ] Rich menu 測試
    - [ ] 「設定」更改後再次打開，應該會保留原本設定
    - [ ] 「教學」可以觸發教學流程

##### ⛔️ Release Blockers
##### 未竟項目

#### :globe_with_meridians: Site
##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [ ] Article list
  - [ ] Filter works
  - [ ] Sorting works
  - [ ] Can go to article page
- [ ] Replies list
  - [ ] Filter works
    - [ ] 不允許選擇 Replied by me
  - [ ] Sorting works
  - [ ] Can go to article page
  - [ ] 不允許 upvote / downvote replies
  - [ ] Can see vote reasons
- [ ] Hoax for you
  - [ ] Filter works
  - [ ] Can go to article page
- [ ] Article detail
  - [ ] Can see similar messages
  - [ ] Cannot submit, upvote, downvote reply request
  - [ ] Cannot submit, upvote, downvote reply
  - [ ] Cannot add, remove, upvote, downvote category
- [ ] Search
  - [ ] Can use global search to perform search
  - [ ] Can use textarea in header to perform searchs
     - Known issue: firefox 無法
  - [ ] Can list searched articles
    - [ ] Filter works
    - [ ] Can go to article page
  - [ ] Can list searched replies

登入自有帳號後檢測：
- [ ] Replies search page
  - [ ] can upvote / downvote replies
- [ ] Replies list
  - [ ] 可選擇 Replied by me
  - [ ] can upvote / downvote replies
- [ ] Article detail
  - [ ] Can submit, upvote, downvote reply request
  - [ ] Can submit, remove own reply
  - [ ] Can upvote, downvote other's article reply
  - [ ] Can add, remove, upvote, downvote category
- [ ] Can go to profile page on menu
    - [ ] Can edit own name, bio, URL
    - [ ] Can see own replies
- [ ] Can logout

##### ⛔️ Release Blockers

##### 未竟項目


### :eye: Under review

## MyGoPen 謠言惑眾獎

> [20231018 會議記錄](https://g0v.hackmd.io/v4taAFAtRt6EOMGGMa7Btw#%E4%B8%80%E8%B5%B7%E8%BE%A6%E8%AC%A0%E8%A8%80%E6%83%91%E7%9C%BE%E7%8D%8E)

- 活動建議、改善之處
- 11 個獎項重新定義？https://www.mygopen.com/p/award.html
- 整理 Cofacts Analytics 排名

## 實科協會

- NPO Hub
    - 開會？
- Reveal on cofacts.tw
    - 更改會址後、申請 Google 非營利前用
    - Cofacts 開源專案開始於 2016 年。2023 年，Cofacts 工作小組成立社團法人台灣實科協會，持續營運 Cofacts 社群。
- 帳務
    - 綜合活存帳戶
    - Spreadsheet with the following sheets
        - 流水帳 on OCF
        - 流水帳 on 協會帳戶
        - 請款紀錄，紀錄代墊款項、發票連結、誰代墊、最後用那個帳號在什麼時候支出墊付款
        - 設備資產

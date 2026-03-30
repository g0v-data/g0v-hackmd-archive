---
tags: cofacts,
---

# 20260331 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 上次會議待辦事項

### Cofacts.ai 開發

https://github.com/orgs/cofacts/projects/12

- [ ] React-markdown --> 回應編輯器
- [ ] 資料關聯整理：準備 source list 然後掃 messages
- [ ] Session list
- [ ] Deploy to production w/ Claudelare
- [ ] 整理 header (logo、menu、搜尋⋯⋯ etc)
- [ ] landing page focus issue
- [ ] input 在組字時 enter 會直接送出
- [ ] tool call 細節調整
- [ ] Langfuse feedback buttons
- [ ] ADK 升級到可以看到 openapi.json
- [ ] 直接用 ADK type 來 render events 而非轉成 messages
- [ ] 在 tool call 中間關掉瀏覽器視窗再打開同一個 session page，要可以繼續串流結果

### :potable_water: Release pipeline

#### :rocket: Staging

##### :robot_face: LINE bot

- [ ] 應可送出「全新訊息」
    - [ ] 問訊息來源時選擇「我自己打的」或「LINE 外面看到的」，應該會被擋下。
    - [ ] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，訊息應該還是有被送出。
    - [ ] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [ ] 可以修改理由送出。查看 article page 看理由是否有被送出。
    - [ ] 「分享到 Facebook」、「分享到 LINE」可以正常運作

- [ ] 送出「沒回應」的舊訊息，應可送出新理由
    - [ ] 跳出來源視窗後關閉，文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。
    - [ ] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，可以看到「提供更多資訊」按鈕，按下去可以再打開「理由」視窗
    - [ ] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [ ] 可以修改理由送出。查看 article page 看理由是否有被送出。

- [ ] 送出「有回應」的舊訊息，應自動回傳回應
    - [ ] 應列出訊息所有的回應
    - [ ] 選擇回應之後可以幫回應 upvote
    - [ ] 可以再次選擇 downvote
    - [ ] 選完回應之後，還可以捲回去選其他回應

- [ ] 送出跟舊訊息相似的訊息，應提供選項選擇最像的訊息
    - [ ] 按下任一訊息應該會列出回應
    - [ ] 選了一個訊息之後，還可以捲回去按其他訊息
    - [ ] 捲回去按下「這裡都沒有我要的」應該要跳出詢問來源視窗 (選項中不能有 100% 相似的，否則會找不到按鈕)

- [ ] Rich menu 測試
    - [ ] 「設定」更改後再次打開，應該會保留原本設定
    - [ ] 「查過的訊息」應該要列出之前查過的訊息

- [ ] Group chat test

##### :globe_with_meridians: Site

**未登入下檢測：**
- [ ] Article list
  - [ ] Filter works (Replied by me: known issue)
  - [ ] Sorting works
  - [ ] Can go to article page
- [ ] Replies list
  - [ ] Filter works (Replied by me: known issue)
  - [ ] Sorting works
  - [ ] Can go to article page
  - [ ] 無法 upvote / downvote replies
  - [ ] Can see vote reasons
- [ ] Hoax for you
  - [ ] Filter works
  - [ ] Sorting works
  - [ ] Can go to article page
- [ ] Article detail
  - [ ] Can see similar messages
  - [ ] Can see deleted replies
  - [ ] Cannot submit, upvote, downvote reply request
  - [ ] Cannot submit, upvote, downvote reply
  - [ ] Cannot add, remove, upvote, downvote category
- [ ] Search
  - [ ] Can use global search to perform search
  - [ ] Can use textarea in header to perform searches
  - [ ] Can list searched articles
    - [ ] Filter works
    - [ ] Sorting works
    - [ ] Can go to article page
  - [ ] Can list searched replies
    - [ ] Can go to reply page

**登入自有帳號後檢測：**
- [ ] Replies search page
  - [ ] can upvote / downvote replies
- [ ] Replies list
  - [ ] can upvote / downvote replies
- [ ] Article detail
  - [ ] Can submit, upvote, downvote reply request
  - [ ] Can submit, remove own reply
  - [ ] Can upvote, downvote other's article reply
  - [ ] Can add, remove, upvote, downvote category
- [ ] Can logout

### ES6 --> ES9

Reindex time spend = 2hr
- Start time: 2026年 3月31日 星期二 00時52分36秒 CST
- Article 搞定：大概在 01:19 (30min 內)
- Reindex 期間 Load 會飆到 > 15，RAM 會用掉 24GB + 8GB buffer ~= 32 GB
- Process time: 2hr (7437 秒)


### 小聚籌備
- [ ] VOOM 發文
- [ ] FB 發文
- [ ] 記得帶：貼紙、不太環保杯 (bil)

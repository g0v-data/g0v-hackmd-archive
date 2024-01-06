---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20211027 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production
#### :globe_with_meridians: Site

[10/21 ~ 10/22 release](https://github.com/cofacts/rumors-site/releases)
Contribution charts

### :rocket: Staging

#### :electric_plug: API
See below

#### :globe_with_meridians: Site
##### Testing checklist
http://dev.cofacts.tw/

登入自有帳號後檢測：
- [x] Replies list
  - [x] 可選擇 Replied by me
  - [x] can upvote / downvote replies
- [x] Article detail
  - [ ] Can submit, upvote, downvote reply request
      - 無法送出「我想補充」
      - upvote / downvote OK
  - [x] Can submit, remove own reply
  - [x] Can upvote, downvote other's article reply
  - [x] Can add, remove, upvote, downvote category

##### ⛔️ Release Blockers

需修復「我想補充」功能的送出

##### 未竟項目

### :eye: Under review

- API: https://github.com/cofacts/rumors-api/pull/263
- DB: https://github.com/cofacts/rumors-db/pull/55

## User Blocking

:::info
**2021/12/01 Update**
A dedicated doc is opened to track its development - https://g0v.hackmd.io/hk1v8Ka5TCmIZinQ6zKU9Q
:::

### 1st milestone: data prep

#### Schema
- [x] WIP add status field & “BLOCKED” state https://github.com/cofacts/rumors-db/pull/55/
- [x] Add migration script to fill in status for `articleReplyFeedback`, `replyRequest`, `articleCategoryFeedback`
    - Unlike `articleReply` and `articleCategory` under `articles` index, those are individual indexes.
    - `articleReplyFeedback`, `replyRequest`, `articleCategoryFeedback`  can be listed out in separate API using ElasticSearch `terms` filter

#### API

- [x]  Update mutation APIs for `ArticleReply`, `ArticleReplyFeedback`, `ReplyRequest`, `ArticleCategory`, `ArticleCategoryFeedback` so that statuses can be filled in according to currently logged-in user is blocked or not

#### Release

- Working schema
- Existing document fields are properly filled
- New document fields are properly filled
- Hidden reply rquests does not increase replyRequestCount
- Hidden article reply feedback does not increase feedbackCount

Not yet
- API still gives hidden items as before

### 2nd milestone: blocking mechanism

#### API
- [ ] Implement manual script that blocks a user (given a userId and blockedReason) and marks all their existing  `ArticleReply`, `ArticleReplyFeedback`, `ReplyRequest`, `ArticleCategory`, `ArticleCategoryFeedback` as `BLOCKED`
    - Leave `DELETED` article replies intact so that the contents we previously deleted won't come out
    - Should also update counting fields
- [ ] Expose `blockedReason` in `User` type

#### Website

- [ ] In website, writes `blockedUserIds` to cookie (website domain) if the current user is blocked
- [ ] load if the user is blocked from cookie and make this info available for all components (through react context or global variable)
    - The value should be available during SSR and in browser
    - The value should be availble even after logout

#### Release

- Block known violating users after release
    - Blocked user will start having `blockedUserIds` cookie in their browser
- API & website still gives hidden items as before

### 3rd milestone: remove blocked content from sight

#### API

- [ ] `WIP` add `statuses` filter to all listing APIs for `ArticleReply`, `ArticleReplyFeedback`, `ReplyRequest`, `ArticleCategory`, `ArticleCategoryFeedback` https://github.com/cofacts/rumors-api/pull/262/
    - filter out DELETED / BLOCKED items by default 

#### Website

- [ ] Query for `BLOCKED` items from API by default
- [ ] Filter out `BLOCKED` items if the their `userId` not in `blockedUserIds`

#### Community builder
- List out latest blocked items


#### Release
- Should display `BLOCKED` items even after blocked user logout!

## 大松檢討

https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2F6iSR4tW3Qv-nXFsKOf127w

- 研討會大桌子 + 工程師比較少，能參與協作的工程師相對少 [name=bil]
- 高中生有回應，但需要可以再加強 [name=nonumpa]
    - 可能是因為用手機，沒有帶電腦 [name=bil]
    - 小聚有投影片慢慢教，大松沒有；其他人從網站進來闢謠，沒有經過小聚，如果放在網站某個地方較好 [name=nonumpa]
    - https://cofacts.tw/tutorial?tab=bust-hoaxes
    - Added to TODO below

## 小聚籌備

[前次小聚檢討](https://g0v.hackmd.io/5VRwpbcJSlSPFtISaNBJ8g?view#%E5%B0%8F%E8%81%9A%E6%AA%A2%E8%A8%8E)

- 三人交集：11/21 > 27 > 28
- [ ] 主題：
    - 現場不太可能只處理公投訊息 [name=bil]
    - 公共議題小聚？ [name=mrorz]
    - 重返實體小聚 [name=mrorz]
- [ ] 場地：NPO hub [name=bil]
- [ ] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
        - 2:20 - 2:40 介紹 mission 1 - 按讚 
        - 2:40 - 3:00 進行評價 (20則)
        - 3:00 - 3:30 休息、自我介紹、交流 
        - 3:30 - 3:50 介紹 mission 2 - 寫回應
        - 3:50 - 4:30 進行回應（1則）
        - 4:30 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：北北基桃
- [ ] 事前產生 spreadsheet 25 人分工
- [ ] KKTIX：
- [ ] 誰會來呢：
- [ ] 做圖：
- [ ] LINE 文案：


## TODO items

- Categories 整理
    - "Hidden" 與 "New"
    - 如何顯示 category 定義
- 宣傳 RSS 訂閱主題 for 公投 [name=nonumpa] +1
    - 2018 時還沒這功能，但現在可以推
        - 在意特定議題的人
        - FB page
    - 主題 mapping
        - 反萊豬 --> 農林漁牧 or 跨國互動 or 食品安全 (看訊息種類)
        - 藻礁 --> 環保生態
        - 公投綁大選 --> 政治政黨
        - 重啟核四 --> 電力、能源
    - 推廣 email 訂閱 or 教學 RSS feed
        - RSS feed 大家比較少用 [name=bil]
        - 那可能主推「IFTTT 進階設定」![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bfbf8a04fe4bc7b4a534cb9bf07d7468.png)
    - 1. 產出 FB page 圖文 --> 介紹主題與公投的關係 & 訂閱步驟
    - 2. 散佈該圖文

:::success
開共筆寫 FB 圖文文案
- Cofacts 主題功能
- 公投與主題的關聯
- 訂閱特定主題
:::

公投 LINE 訊息來襲！

訂閱真的假的・掌握最新回報

「過濾」--> 「訂閱」

（文字）
2018 年公投期間，Cofacts 真的假的搜集了 N 篇公投主題相關的訊息

這次的公投，真的假的有「主題」分類與訂閱功能，讓大家可以在特定主題有新回報訊息時的第一時間就收到通知唷！

---

「主題」分類

按照設定的受眾，將網友回報訊息按照「議題」分類
（過濾 & 主題下拉列表）

AI 標記與群眾協作標記
AI 分類：每天午夜會有神奇小精靈，針對當天新回報的訊息，自動進行主題分類
人工標記：任何編輯志工都能在網站上，替訊息增加或刪除主題分類
（示意步驟圖：按鈕 --> 視窗 --> 標註分類）

訂閱

---

藻礁：環保生態

---

核四重啟：能源議題

---

公投綁大選：政治政黨

---

萊豬：農林漁牧 or 跨國互動 or 食品安全
（各自的定義、截圖）

---

有新訊息通知我

LINE

進階



- - -

- [常見錯誤回應樣態](https://g0v.hackmd.io/6mTYVWhLSTWfDcyaxYLaXA#%E5%B8%B8%E8%A6%8B%E9%8C%AF%E8%AA%A4%E5%9B%9E%E6%87%89%E6%A8%A3%E6%85%8B)
- 初次進入的教學
    - 偵測使用者 < Level 1 且按下「闢謠」時跳出 dialog 邀請去看[教學](https://cofacts.tw/tutorial?tab=bust-hoaxes) [name=mrorz]
    - 更多的教學連結 in editor

## rumors-ai

Q_Q


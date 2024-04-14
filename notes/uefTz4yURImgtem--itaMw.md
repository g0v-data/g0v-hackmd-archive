---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240414 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

- https://github.com/cofacts/rumors-site/releases/tag/release%2F20240408
- https://github.com/cofacts/rumors-site/releases/tag/release%2F20240412


#### :robot_face: rumors-line-bot

- https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20240406
- https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20240412

### :rocket: Staging

#### :globe_with_meridians: Site

https://github.com/cofacts/rumors-site/pull/569

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] 各訊息 URL 自動處理是否正常
- [x] 長 URL 的刪節號處理是否正常
  - [x] 複製貼上具有刪節號的 URL 是否能不受刪節號影響

##### ⛔️ Release Blockers
無

##### 未竟項目
無

### :eye: Under review


## CCPRIP
### [Op] Transcript spam
> https://github.com/cofacts/rumors-api/pull/335


### [Op] 垃圾訊息反制

- 過去一週非常頻繁 https://github.com/cofacts/takedowns/blob/master/2024/0123-spam.md
- 目前：有人看到並回報 --> 判斷是詐騙 --> 在 google sheet 生成公告、指令 --> 更新公告、執行指令
  - 必須要有電腦才能在 google sheet 用 script 生成公告與指令
  - 必須要 SSH 登入主機才能執行指令

### 提案
1. 自動偵測 or 檢舉
2. 產生帶有指令的 Github PR（takedown announcement），有權限的人都能編輯公告、approve & merge
    - (More) human in the loop
    - 手機亦可操作
    - 有 audit log
    - 能在 PR 上公開討論
    - 可在 github repo 指定誰能 merge
3. API 偵測到有 Merged PR 就執行指令

### 技術細節
- API 執行指令不希望 API 開 endpoint
  - Option 1: subscribe 到 Google cloud pubsub?
    - 每月 10GB 免費，沒有問題 https://cloud.google.com/pubsub#pricing
    - 跟 Option 2 比的優點：
      - 直接寫在 Github action，執行有 log 可以看
      - 不用 polling，按下 merge 後立即執行
      - API 端只要接收訊息並執行就好
  - Option 2: API 寫 cronjob 掃 PR?
    - 跟 Option 1 比的優點：
      - 不用多整合 pubsub
- 檢舉 --> Github PR 怎麼做
  - 把目前 google sheet 的 script 裡的公告，加入指令
  - 但不希望每個檢舉都發 Github PR。可能還是先手動在電腦上執行 script。
- 自動偵測 --> Github PR 怎麼做
  - Option 1: 直接做在 API CreateArticle / CreateReply / etc，遇到了就呼叫 Github API 發 PR
  - Option 2: API CreateArticle / CreateReply / etc 只會 publish event to Google pubsub，processing 另外做
    - 跟 Option 1 比的優點：
      - 無論偵測怎麼實作，都跟 API 無關，不會有影響
      - 還能擴增更多東西，如 URL 存檔、加強逐字稿、判斷色情訊息等等
    - 跟 option 1 比好像不會多太多時間，但彈性多很多 [name=MrOrz]
  - Option 3: 直接做成 `cofacts/takedowns` 的 scheduled Github action
    - 反正偵測也不用很及時，每 10 分鐘批次處理亦可
    - 直接呼叫現有 ListArticle / ListReply 等進行處理
    - 跟 Option 2 比的優點：
      - 不用多整合 pubsub、Github action 也有權限直接建立 PR
      - processing 直接做在 github action 不用另外 deploy
    - 缺點：要注意 [Github workflow 2000min / mo](https://docs.github.com/en/billing/managing-billing-for-github-actions/about-billing-for-github-actions) 的限制 --> 每天只有 66min 的 quota。
Detection 如果要跑 5min，那一天只能跑 13 次。寫錯 code 導致 workflow 停不下來的話，更是會大量吃光 quota。
    - 實作速度最快最簡單，但那個缺點會導致此選項感覺不合用⋯⋯ [name=MrOrz]

:::success
API 執行指令：Option 1
自動偵測：Option 2

--> MrOrz 寫 design doc
:::

## missing 逐字稿
> 還沒補 [name=mrorz]
> 先做垃圾訊息反制

## 謠言惑眾獎

### 推播成效

超出[預期](https://g0v.hackmd.io/cyOfGs88TROLTF1bKeAyAg?both#%E8%AC%A0%E8%A8%80%E6%83%91%E7%9C%BE%E7%8D%8E) 2 倍

- Click / Impression = 3% (預測為 1%)
- Cofacts 2931 + MyGoPen 2636

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f41a5d888e16ab37a4f1b270dab0687a.png)


### 後續作業

通知得獎者：
- 透過 LINE 推播給特定 LINE ID 列表（Cofacts 帳號的 ID）
- LIFF + Surveycake 收 LINE ID 與地址資訊
  - LINE ID 假造問題：我們不會公告完整 LINE ID，而且獎很小

:::info
跟 MyGoPen 討論要不要切斷 MyGoPen 真人查證的部分
因為民眾反應下架會找 MyGoPen、使用者又搞混兩者，變得有點像是客服勞務外包給 MyGoPen，有點不好意思 [name=bil]
:::


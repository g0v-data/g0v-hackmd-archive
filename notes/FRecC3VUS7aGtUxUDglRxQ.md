---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20241031 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：mrorz, bil, nonumpa, 4000, T, Conrad
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
- 今天風災影響會稍微晚點
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: rumors-line-bot

- Cooccurrence replyrequest and consent https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20241022

### :rocket: Staging

#### :electric_plug: DB & API

Make schema strict

- https://github.com/cofacts/rumors-db/pull/70
- https://github.com/cofacts/rumors-db/pull/71
- https://github.com/cofacts/rumors-db/pull/72
- https://github.com/cofacts/rumors-api/pull/342 (Including migration script)

Need a thorough test to see if anything is broken

#### :robot_face: rumors-line-bot

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 應可送出「全新訊息」
    - [x] 問訊息來源時選擇「我自己打的」會被擋下。
    - [x] 選擇「整篇轉傳」後會詢問是否要送出訊息。
    - [x] 不同意送出訊息後可以收到感謝。
    - [x] 同意送出訊息後就會送出訊息，並得到：
        - [x] Cofacts article page 按鈕
        - [x] 寫理由的按鈕
        - [x] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面
        - [x] 「分享到 Facebook」、「分享到 LINE」且可以正常運作
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以再打開理由視窗，此時會載入上次填寫的理由。修改理由送出後，查看 article page 看理由是否有被送出。

- [x] 送出「沒回應」的舊訊息，應可送出新理由
    - [x] 文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以修改理由送出。查看 article page 看理由是否有被送出。
    - [x] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應
    - [x] 選擇回應之後可以幫回應 upvote
    - [x] 可以再次選擇 downvote
    - [x] 選完回應之後，還可以捲回去選其他回應
    - [x] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [x] Rich menu 測試
    - [x] 「設定」更改後再次打開，應該會保留原本設定
    - [x] 「教學」可以觸發教學流程

##### ⛔️ Release Blockers
##### 未竟項目

#### :globe_with_meridians: Site
##### Testing checklist
http://dev.cofacts.tw/


登入自有帳號後檢測：
- [x] Replies search page
  - [x] can upvote / downvote replies
- [x] Replies list
  - [x] 可選擇 Replied by me
  - [x] can upvote / downvote replies
- [x] Article detail
  - [x] Can submit, upvote, downvote reply request
  - [x] Can submit, remove own reply
  - [x] Can upvote, downvote other's article reply
  - [x] Can add, remove, upvote, downvote category
- [x] Can go to profile page on menu
    - [x] Can edit own name, bio, URL
    - [x] Can see own replies
- [x] Can logout

##### ⛔️ Release Blockers
No

##### 未竟項目
No

:::success
找個深夜 release
:::

### :eye: Under review

## 小聚檢討

> 小松果 https://g0v.hackmd.io/mjJOZkQ0TQqO1FzyucVfZA?view

- 整袋忘記帶 orz
  - 標語：立刻印了
  - 黏土：有存一些 (?)
  - 網路：那天人不多，不卡
- 記者寫「我要查核闢謠」時，99 則回應 = 0 則回應
  :::info
  開票
  沒有類似訊息的 0 = 99  
  :::

## Open165
- cronjob 壞掉 https://github.com/Open165/site/issues/33
- Internet Archive Wayback machine 壞掉 https://blog.archive.org/2024/10/21/internet-archive-services-update-2024-10-21/

## Badge 功能

- 實作方向：badge ( https://g0v.hackmd.io/6tCmrXsyS3WEGgC_bMcd9w?#User-organization--badge )
  - 認證該使用者有參與過課程
  - 無須追蹤 badge 擁有者成效等等
  - 顯示上會較為顯眼
  - 使用者若獲得多個 badge，可自選要呈現哪個 badge
  - 直接改資料庫加入新 badge 資訊
  - 由第三方打 Cofacts API 把人加進 badge，發 badge 時也提供 metadata
- 過往討論整理：https://hackmd.io/ktxqGDX4S4iuBd1MoZqDmQ?#Cofacts-Editor-Organization-%E6%A9%9F%E5%88%B6

## Automatic spam removal

> @nonumpa
> Design doc:  https://g0v.hackmd.io/@cofacts/rd/%2Fum7DyY_ESbu2LL78kLw3pg

> 最近 Spam 太誇張，一天可以有好幾個不同帳號產生 https://github.com/cofacts/takedowns/blob/master/2024/0123-spam.md ，讓檢舉人也疲於奔命
> 之前自動 spam 移除 ( https://g0v.hackmd.io/@cofacts/rd/%2Fum7DyY_ESbu2LL78kLw3pg )，是想解決自動執行一定要 ssh 的部分，目前推進卡在前面的 refactor
> 我現在想要先跳過自動執行（phase 1, 2）的實作，直接做自動檢舉（原定計劃中的 phase 3）。執行下架還是手動沒關係，至少能：
> - 自動發 PR
> - PR 裡附上要執行的指令讓我 copy & paste 到 terminal
>
> 目前用 `ListBlockedUsers` + `ListReplies` API 觀察到已經封鎖的使用者行為：
> - 有的註冊後 10 分鐘內會開始動作，但也有可能會放一陣子；另外，我們也沒開 ListUser API，因此無法掃使用者偵測
> - 開始貼文後，每篇間隔約 25 秒，可能手動也可能用瀏覽器自動化工具，因此就算上 captcha 可能也沒用（如果對方是手動 or browser automation with headed browser）
> - 可能會被有幾種文案交互貼，不會每個都貼一樣的，但都是廣告無誤
>
> 我的構想是：
> - 直接在要發 PR 的 https://github.com/cofacts/takedowns 寫 Github action workflow 寫 script，跑在 github action 上比較省事
> - 每 10 分鐘跑個 script 打 `ListReplies` API 掃過去 10 分鐘的回應（先以回應為主，未來可以再擴充到 reply request 等）
> - 把這些回應丟給 LLM 看是否是詐騙
> - 是的話，先檢查是否已經發過 PR；否則，就發 PR 在該年度 directory 下建立 <date>-<userid>.md  公告該使用者違反廣告條款，PR 附上可以複製貼上的 CLI 指令
> - 我看到後覺得是詐騙無誤，就 merge + 手動執行該指令；若是冤枉的，就 close PR。因為前面發 PR 前會先檢查的緣故，script 不會再針對此使用者自動發 PR。
> 
> 這個設計未來在自動 spam 移除計畫原訂的 pubsub（phase 1）自動指令執行（phase 2）完成後應該可以無痛接軌，變成任何能 merge PR 的人按下 merge 之後都能觸發 spam removal，擴大 spam 處理量能。
>
> [name=mrorz]

- article 丟進 GPT [name=nonumpa]
  - 很難控制說只回 true / false
  - OpenAI structured output or Gemini function calling [name=mrorz]
  - [few-shot prompting](https://www.promptingguide.ai/techniques/fewshot), 但就是 prompt 很多 [name=mrorz]
- 想先串起來，之後再弄 prompt
- PR：一個違規使用者開一個 PR [name=mrorz]
  - 開 PR 之前檢查，開過的不要再開，close 掉的也不要再開（可能不是 spam 被我們 close 掉）[name=mrorz]

## Langfuse

- 可以觀察 prompt
- Langfuse 架在 staging [name=mrorz]
- 想要把 LLM feedback 直接用 Langfuse 做，但就是 rumors-api 要打 langfuse API 拿到 vote，不確定增加這個 dependency 有沒有比較好



---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250224 會議記錄
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

## LLM Transcript update

Errors can come from:
- Cloudflare
    - 
- nginx proxy
    - `proxy_read_timeout`: Default 60s; production already at 240s
        - Moved staging timeout from default to also 240s: 
    - `proxy_send_timeout`: Defualt 60s; already bigger than Cloudflare's
- rumors-api: ListArticles with transcript creation turned on
    - 

- 


### :eye: Under review

## RightsCon & Satelite Events


- 2/22 (Sat) 大松：https://g0v-jothon.kktix.cc/events/g0v-hackath65n 
- ~~2/24 (一) Side-event 17:00~18:00 比鄰演講~~ 取消
- 2/25 (二) 9:00~10:00 NDI Panel
- 2/25 (二) 14:00 ~ 15:00 Cofacts 自己的 talk - ID # 23894 – “Crowd-sourced fact-checking in AI era - Lessons learned by Cofacts
  - 地點：South Lobby of the 2nd floor
  - 投影片：https://docs.google.com/presentation/d/1_FGSKvgP2jh9o_22FhKSuDWLI-cu4lY3u95PL5lVb9o/edit
- 2/26 (三) **早上**擺攤
- 2/26 (三) 12:45-13:45 大平台 ~~(Promote 攤位)~~
- 2/27 (四) 11:30~12:30
  - NiemanLab / Panel Discussion / Challenge around deepfake detection
- 2/27 (四) 12:45~13:45 ID # 25017 - Global Giants, Local Influence: The Role of International Social Media in Shaping National Discourse
  - 地點：201E

### Sessions we may participate

- [2/23 (日) OCF sattlelite event](https://ooni-research.ocf.tw/docs/blog/2025/02/rightscon25-tor-tails-ooni/)
  - 活動日期：2025/02/23
  - 工作坊 14:00 – 17:30 如何使用 Tor 避開審查並匿名瀏覽
  - 工作坊 18:00 – 19:00 如何使用 OONI 偵測與觀察網路審查狀況
  - 演講座 19:30 – 21:00 Tor 在網路監控的世界中捍衛個人線上隱私權
- 2/23 (日) 3pm-6pm[【工作坊】打造韌性網路：動手實作「不需海纜」的網路](https://airtable.com/appWd48vvxh0VJS1D/shrLERQDlmu6j3jMz)
- 2/26 (三) DWeb panel 10:15~11:15 (Promote 攤位)
- 2/24~2/27 OCF＆司改會一起擺攤

### 2/26 (三) 09:00~13:00 擺攤

人
- Johnson & Bil
- Stella & Yutin

時間
- 8:30 ~ 9:00 設攤
- 9:00 ~ 13:00 擺攤

空間
- 3F Networking Lounge https://www.rightscon.org/venue2025/#floor3 / https://www.ticc.com.tw/wSite/vr360/index.html
- 先在 1F Help Desk 報到，才知道在哪個 booth
- 180 cm x 60 cm 桌子
- 2 張折疊椅
- 牆上不能貼東西
- 不一定有電，延長線自備
- 沒有推車與幫手，進場撤場都是手搬

材料

https://drive.google.com/drive/folders/1U-etbZSOiFzpXgOr0GtBxkwYKk666nni

- [ ] CCC 的 Cofacts 遊戲
- [x] 局部上光 bil 名片
  - [x] 加中文「比鄰」小字
- [x] 更新英文版網站 news
- [x] 文宣更新與印刷
  - [x] 英文（achoo）
    - 250 張起跳 http://www.soho8d.com.tw/Form2/F102.aspx?csubid=73
    - 要更新 QR code
    - 背面有疊影，需處理掉四色黑
  - [ ] 豆腐版
  - 借放在 OCF 攤位 & 自己攤位上
- [x] 宣傳用：Logo 貼紙（透明 or 長的）
- [ ] 投影片放在多頁的透明資料夾


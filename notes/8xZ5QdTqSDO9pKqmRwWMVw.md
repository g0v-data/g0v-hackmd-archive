---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20241007 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
https://github.com/cofacts/rumors-api/releases/tag/release%2F20241007

    fix(graphql): ListCooccurrences API error by @MrOrz in #346
    fix: add refresh when inserting media article by @MrOrz in #347
    Add status field to Reply by @MrOrz in #349


#### :globe_with_meridians: Site
https://github.com/cofacts/rumors-site/releases/tag/release%2F20241001

    Fix type for codegen by @MrOrz in #578
    Reply detail and article detail revamp for blocked content by @MrOrz in #579

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


## CCPRIP

### Cloudflare 設定
> https://g0v.hackmd.io/i1XNmK5_ShuBrkf3KHabcQ?view#Cloudflare-%E8%A8%AD%E5%AE%9A

- Cloudflare 設定導致 downtime: https://hackmd.io/@cofacts/incidents?_gl=1*nx60y4*_ga*MTg0MzUwMzI5Ni4xNjAzMzkyNTAx*_ga_NGVZMM6DR6*MTcyODIzMzY4My4xMjA2LjEuMTcyODIzNTM2Mi41OC4xLjIwMzE2ODA5MDc.#20241001-1301---2121-LINE-bot-not-accesible

> 有 `@A` 的就是 Alex 的 rule

#### Analytics
- Enabled Web analytics for Cofacts 

#### Security > WAF > Custom rules

- 將CF驗證過的Bots排除WAF@A：Verified bot category (去除 AI crawler 們)
- 擋已知有威脅的國家@A
- Challenge未列入白名單的國家@A（目前 disable 中）--> 由原本的 challenge foreign non-bot access 處理
- 尋找Bot API Probing的Fallthrough Rule@A：skip，只是 log

#### Security > WAF > Rate limiting rules
- Prevent fast access --> 10 秒 10 requests --> 10 秒 7 requests
- 擋已知惡意graphql DOS@A：特定 user agent 的 request，十秒內超過 25 request 就做 managed challenge

#### Security > WAF > Managed rules
==TBA==

#### Security > WAF > Tools
- Allow Cofacts Linode & LINE corp (whitelist)
  - 有討論到為啥 Linode 內流量還要過 Cloudflare。主因是現在有部分服務在 Linode 內/外，而且未來會往外搬，要細部設定不划算。 [name=mrorz]

#### Security > Page Shield
==TBA==

#### Security > API Shield

設定 `/graphql` 為 endpoint 做 logging

#### Security > Settings

- Challenge Passage: 5min -> 15min

#### Speed > Optimization

- Enabled [Speed Brain](https://developers.cloudflare.com/speed/optimization/content/speed-brain/)
- Enabled [Enhanced HTTP/2 Prioritization](https://blog.cloudflare.com/better-http-2-prioritization-for-a-faster-web/)
- Enabled [Mirage](https://developers.cloudflare.com/speed/optimization/images/mirage/)
- Enabled QUIC (HTTP/3)
- Enabled [Early Hints](https://developers.cloudflare.com/cache/advanced-configuration/early-hints/)
- Enabled [Cloudflare Fonts](https://developers.cloudflare.com/speed/optimization/content/fonts/)

#### Caching > Configuration
- Browser cache TTL: 1 month --> 2 days

#### SSL/TLS > Edge Certificates
- Ordered Universal Certificate
- Enabled [Encrypted Client Hello (ECH)](https://developers.cloudflare.com/ssl/edge-certificates/ech/)
- 開啟 Automatic HTTPS Rewrites
- 開啟 TLS 1.3

#### Rules > Transform Rules > Managed Transforms

==TBA==

#### Rules > Cached rules
- 測試把Origin動態HTML來源Override成Static@A：==TBA==
- 測試把Home PNG Cache Miss Override成Hit@A：==TBA==

#### Rules > [Compression rules](https://developers.cloudflare.com/rules/compression-rules/)
- ZTSD compression on Default Content Types @A

## Takedowns

- 20240625 明確為二次詐騙 https://github.com/cofacts/takedowns/pull/128/files
  - 以 CofactsWG 信箱聯繫
  - 有填寫下架表單
  - 連續寄信來拜託刪除整篇文，聲稱「明天開庭會被偵查到」、「不想有麻煩」等語，並要求「把律師事務所的名字刪除」
- 20241006 用語與過往吸金案例有相同之處 https://github.com/cofacts/takedowns/pull/136
  - 以 CofactsWG 信箱聯繫
  - 兩人填寫下架表單，一人自稱傳訊息的使用者，另一人自稱委任人的助理
  - 後者應是真人，聲稱受任人得知合約公開非常生氣並揚言提告
  - 傳訊息進來的人表示對方「找上他」不希望「節外生枝」

過去做法


考量點
- 公共性：確實有詐騙疑慮
- （自稱是傳訊息的人）來信

### Action items

- [ ] 優先實作 https://github.com/cofacts/rumors-line-bot/issues/394

## 小聚籌備

- [ ] 日期：10/27 (日)
- [ ] 食物：
- [ ] 場地：NPO Hub Foundry（大的那間)
- [ ] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Slido 暖身
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：
  - 推播日：
  - 目標：雙北
- [ ] KKTIX: https://cofacts.kktix.cc/events/cofactseditor44
- [ ] 誰會來呢：bil,orz,nonumpa
- [ ] 記得帶：貼紙、環保杯
- [ ] LINE 文案：唯恐天下不亂的老牌假訊息又出現了，聲稱「美國聯邦調查局在麥當勞肉類中發現人類遺骸」十年前的假訊息歷久彌新。假訊息說「以為進入了火化程序，卻進入了食物鏈成為了別人的食物。」這種破壞食品安全與社會信任的假訊息惡意又瘋狂，還好有查核志工協助把關。邀請你的參與，10月27日(日)14:00-17:00，在台北NPO聚落二樓。第44次查核志工培訓工作坊期待你一起來加入協作＝Ｄ
地址：台北市中正區重慶南路三段2號二樓（最近的捷運站是中正紀念堂站2號出口）
- [ ] VOOM 發文
- [ ] FB 發文

## 十月開會

- 10/14 取消
- 10/21 線上開會，同一時間

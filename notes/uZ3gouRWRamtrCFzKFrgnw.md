---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220810 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz
- 線上出席：4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
https://github.com/cofacts/rumors-api/releases/tag/release%2F20220807

Fix number inaccuracy caused by [GA sampling in #290](https://github.com/cofacts/rumors-api/releases/tag/release%2F20220807)

- 上線後發現網站上美玉姨、防詐達人的 hit 數與 GA 上對不起來
- 在本機端發現：如果只取小範圍的資料，數據就會一致；但如果一口氣從 2021-09-01 取到現在，那數字就會跟 production 上完全一樣
- 判斷是 GA [sampling](https://support.google.com/analytics/answer/2637192#zippy=%2Cin-this-article) 在搞鬼，因此加入[偵測 sampling 的機制](https://developers.google.com/analytics/devguides/reporting/core/v4/basics#sampling)
- 手動的每 15 天為一個區間；熱門的日子（疫情期間）區間數還要下降到 8 天一區間，才能維持不 sampling
- 現象：只有有回應過的訊息，會有美玉姨 / 趨勢科技的數據
    - 因為這兩個 bot 不會把沒回過的 article 吐出去⋯⋯

#### :globe_with_meridians: Site
https://github.com/cofacts/rumors-site/releases/tag/release%2F20220806

#### 🖼️ Media Manager

Documentation: https://github.com/cofacts/media-manager

### :rocket: Staging

#### :robot_face: rumors-line-bot

https://github.com/cofacts/rumors-line-bot/pull/316

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 應可送出「全新訊息」
    - [x] 問訊息來源時選擇「我自己打的」會被擋下。
    - [x] 選擇「整篇轉傳」後會詢問是否要送出訊息。
    - [x] 不同意送出訊息後可以收到感謝。
    - [x] 同意送出訊息後就會送出訊息，並得到：
        - [x] Cofacts article page 按鈕
        - [x] 寫理由的按鈕
        - [ ] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面
        - [x] 「分享到 Facebook」、「分享到 LINE」且可以正常運作
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以再打開理由視窗，此時會載入上次填寫的理由。修改理由送出後，查看 article page 看理由是否有被送出。

- [x] 送出「沒回應」的舊訊息，應可送出新理由
    - [x] 文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以修改理由送出。查看 article page 看理由是否有被送出。
    - [ ] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應
    - [x] 選擇回應之後可以幫回應 upvote
    - [x] 可以再次選擇 downvote
    - [x] 選完回應之後，還可以捲回去選其他回應
    - [ ] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [x] 送出 staging 上有的圖，應能回應
    - [x] 有回應者，會回傳回應
    - [x] 無回應者，會回傳「請先不要相信這個訊息唷」

- [x] Rich menu 測試
    - [x] 「設定」更改後再次打開，應該會保留原本設定
    - [x] 「教學」可以觸發教學流程

##### ⛔️ Release Blockers

等圖片送出流程

##### 未竟項目

- bug: LIFF 裡修改回應，如果只有一人 reply request，會顯示「有 0 人跟你一起期待這則訊息被回應」 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9ca5803dba1b797a6088bde239004337.png =x400)
- LIFF articles list 尚未支援圖片 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ac63d8a2ee8a67d50ca37e1d8d2b345b.png =x400)

:::info
另外開票處理
- https://github.com/cofacts/rumors-line-bot/issues/320
- https://github.com/cofacts/rumors-line-bot/issues/319
:::


## Image support
> https://github.com/orgs/cofacts/projects/9

### Documentation
- README & typedoc site done
- Wiki 待補


### Chatbot

New diagram? 
- 目前 https://docs.google.com/drawings/d/1sSzI0PSggkA3PPP99Nl18H4zMO4lk-2y5s7dGRNJwAE/edit
- search image PR + 未來的送出實作後 https://docs.google.com/drawings/d/1N6RYK3KYlSzLDu6SClNwz57U0QfakIrat5sG5uUhovU/edit 
    - 因為圖的部分不會自己做圖放進來，所以可以直接問 consent [name=nonumpa]


### Process existing images
1. chatbot 上線，圖檔往 GCS 送，Google drive 不再有新圖 (8/20)
2. 用 [rclone](https://rclone.org/) 把所有圖下載到本機端
3. 計算 hash，找出有重複 hash 的圖檔們（預計約 8000 個 unique hash 有多張圖）
4. 用 Google drive API 找到 3 的每張圖的建立時間
5. 把 3 的每個 unique hash 的一張圖用 media-manager 上傳，紀錄 Media entry ID
6. 用 5 的 media entry 與 4 的 metadata 蓋出 aritcle & reply-request object with correct createdAt
   - replyrequest 的 userId 是個挑戰
8. 把 6 的資料輸入 staging 進行回應 (staging 先更新到最新 snapshot)
9. 網站支援 filter by article type
10. 把 staging 上的 ariticle, reply, replyrequest 移植到 production

### Extended goal
- 協作圖片上的文字、OCR：協作機制、衝突管理
    - 回退防亂、三回退衝突處理(wiki 作法)？
    - crowd-source 作法：多人標記正確性/校正
- 跟圖片一起傳的文字如何處理
    - [0525 article group](https://g0v.hackmd.io/3_jgVd9vQreCsgADOdF25w#%E6%96%87%E5%AD%97%E9%85%8D%E5%9C%96%E9%85%8D%E5%BD%B1%E7%89%87%E5%95%8F%E9%A1%8C-article-group)

## Trend and contribution
> https://github.com/orgs/cofacts/projects/10

全數開發並 deploy 完畢。

## CCPRIP

> Cofacts Chatbot Platform Resiliency Improvement Plan, CCPRIP

長期方向
https://g0v.hackmd.io/BRsJOevWSbyUMBSZEVVWrA

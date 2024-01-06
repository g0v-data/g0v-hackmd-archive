---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20210707 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz, nonumpa, Kai, lucien
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site
Fix "Similar Replies"
https://github.com/cofacts/rumors-site/releases/tag/release%2F20210701

### :rocket: Staging

#### :robot_face: rumors-line-bot

- #267 Common LIFF components
- #268, #270 Replace svelte-material-ui with common components
- #271, #272 Testing env improvement
- #273 Introduce persistent AppVariable and use it to store `lastScannedAt`
- #274 Fix postback redis error

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 應可送出「全新訊息」
    - [x] 問訊息來源時選擇「我自己打的」或「LINE 外面看到的」，應該會被擋下。
    - [x] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，訊息應該還是有被送出。
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 選擇回應之後可以幫回應 upvote
    - [x] 可以再次選擇 downvote

- [x] Rich menu 測試
    - [x] 「設定」更改後再次打開，應該會保留原本設定

##### ⛔️ Release Blockers


##### 未竟項目

轉介 MyGoPen 時應該轉到一對一查詢的那個版本

#### :globe_with_meridians: Site

- #438 Fix avatar in Landing page - kudos to ulayab 

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] Landing page
  - [x] Shows "Login" on top right corner


登入自有帳號後檢測：
- [x] Landing page
  - [x] If user uses gravatar, shows on top right corner
  - [x] If user uses openpeens, shows open peeps on top right corner

##### ⛔️ Release Blockers

##### 未竟項目

### :eye: Under review

## Case study: Twitter birdwatch

[Twitter Birdwatch 研究](/oK1F5q4eRV2IhGM-8ULTdQ)

> note 接近我想補充
> 回報的人要寫 note，像是新聞小幫手檢舉新聞要回報內容。
> cofacts 仰賴回報確認熱門度，如果回報必須寫 note，回報率下降。
>
> twitter 本來就有轉貼的功能，比複製貼上快，所以不容易重複。

- Birdwatch Note = Cofacts reply request（補充） + reply（回應）[name=mrorz]
    - Birdwatch 回報者負責寫 note
        - Twitter 每個 tweet 本來就有 like count
        - Twitter 有 retweet，比起複製貼上，retweet 更快，所以重複問題較小
        - Cofacts 仰賴輕量的回報來搜集回報、判斷「熱門度」，沒辦法讓「回報」與「查證」合一，不然沒人要回報⋯⋯
    - Reply request 或許可以朝 note 邁進
        - 回報時先送出空白 reply request 使數字 +1
        - 提供類似 note 的選項，以及相同的 text area
        :::success
        可以考慮跟進類似的選擇題
        ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b592d29449722d2d339e6f6451e51df7.png)

        或訊息分類
        :::
    - 「好的 reply request」與「一則 reply」的邊界？「回報者」與「查證者」的邊界？
        - 目前的機制有試著讓使用者 pivot 成回應者，例如「覺得回應不夠好嗎」的問句 [name=bil]
        - 只是撰寫能力或時間的不同 [name=bil]
        - 目前也有使用者會在補充放查到的東西，只是人比較少而已，只是機制是有的 [name=bil]
        - 訊息分類可以做進回報系統 [name=nonumpa]

- Birdwatch contributor 每票不等值 [name=mrorz]
    - 每個人都有分數，投的 rating 會有不同權重
    - 目前想到可以防止網軍攻擊，不知道還有沒有其他作用？ [name=nonumpa]
        - 鼓勵 be helpful、約束不要亂 rate 亂寫 note，因為行為都會影響自己的 helpfulness score [name=mrorz]

- UI wording [name=mrorz]
    - "Needs Your Help" 取代 "Hoax for you"
    - "Helpful / unhelpful" 取代 "useful / not useful"

:::success
Needs Your Help / Help Needed
:::

## 2021 2H Roadmap

### Article LIFF

Target: receive input (feedback, reply requests) from outside of Cofacts chatbot

https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/?node-id=3004%3A224
1. [x] 實作 common component storybook
2. [ ] 實作 feedback form + 使用在目前的按鈕上 - ongoing [name=mrorz]
3. [ ] 實作 reply request form + 使用在目前的按鈕上
4. [ ] 實作 article & reply
5. [ ] 實作 reply request list
6. [ ] 實作 related article

### Contribution calculation

- Discussion: [20210526 會議記錄](/8VGFKx-cR8yEdKlAQ3vv5A)
- Conclusion: https://g0v.hackmd.io/giYWfM8yRkKghtPOG1EBig?both#%E5%AF%A6%E4%BD%9C%E6%96%B0-profile-contribution--%E5%8D%87%E7%B4%9A
- Status: Needs design doc
    - Sample: [Cofacts LIFF redesign](/860RnxUGTi6z2Kca6ojAbg), [Rumors-api userId & appId management proposal](/ZcoUOX_-RQSkJyl5xz4_Zg), [rumors-line-bot 過去傳過訊息 implementation](/eIeU2g86Tfu5VnLazNfUvQ))

### 「評價過的回應」列表

- Design: https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/Cofacts-website-MrOrz?node-id=2923%3A402
- Postponed due to [privacy concern](https://g0v.hackmd.io/6ZwH7NANRqG6s-CCIy9IYw#%E3%80%8C%E8%A9%95%E5%83%B9%E9%81%8E%E7%9A%84%E5%9B%9E%E6%87%89%E3%80%8D%E5%88%97%E8%A1%A8)
    - 個人頁面外連還沒做，似乎還是可以先有這個 tab，之後要把個人頁面外連時才去控制公開與否 [name=mrorz]
  
### 鼓勵 linebot 使用者評價

- 綁定 cofacts 帳號 [name=nonumpa]
    - 身份認證用
    - 鼓勵 LINE 使用者註冊 Cofacts 網站登入 https://engineering.linecorp.com/zh-hant/blog/how-to-use-account-link/
- 評價 500 送貼圖 
    - 數量可以再討論（可以先看看大部分使用者的評價數量是多少）
    - 可能有人為了拿貼圖亂評價
- community-builder 或 spreadsheet：最多評價 / 回應的人
    - 程式更新
    - 定期去看 --> 聯絡、送貼圖

## 25th 小聚

- 時間
    - 7/24 (六) 2pm - 4pm
    - ~~7/10 (六) 2pm - 4pm 解封前~~
- 規劃 
    - Default 線上，即使管制放鬆，也沒有必要把人約出來 [name=bil]
    - 線上活動 3hr 有點累 [name=bil]
    - 休息 10min

----

- [ ] 主題：
- [ ] 時間：7/24
	- **活動時間：14:00 - 16:00**
- [ ] Jitsi
    - 可以[到 75 人](https://community.jitsi.org/t/maximum-number-of-participants-on-a-meeting-on-meet-jit-si-server/22273) [name=kai]
- [ ] KKTIX
- [ ] 誰會來呢？
- [ ] 誰不會來
- [ ] 做圖：
- [ ] LINE 文案：

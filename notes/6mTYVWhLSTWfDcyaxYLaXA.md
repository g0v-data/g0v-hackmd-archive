---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20210908 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: rumors-line-bot
https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20210907

### :rocket: Staging

#### :robot_face: rumors-line-bot

- #286 Cache-control for assets
- #288 Google analytics title for LIFF article page
- #287 Update translation for 真的假的
- #289 Add AppBar and link to website


檢查 GA blocker 是否已經解除
https://g0v.hackmd.io/E1-ajzinSwCyacGG228VsQ?both#TODO-before-GA

- [x] Link to website (article page & tutorial)
- [x] Cofacts闢謠志工 --> 「真的假的」闢謠志工
- [x] 「這則 cofacts 回應」--> 「真的假的回應」
- [x] Google analytics + `utm_source` (影響到 URL 整合，要先說) 

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 送出「有多則回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應，且指導語的「Cofacts」已經換成「真的假的」
    - [x] 選擇回應之後可以幫回應 upvote
    - [x] 可以再次選擇 downvote
    - [x] 選完回應之後，還可以捲回去選其他回應
- [x] 用 LINE 造訪 article LIFF（多回應）- https://liff.line.me/1563196602-X6mLdDkW?p=article&articleId=2gvs0nu9ynjo7&utm_source=rumors-line-bot
    - [x] 可以 upvote 沒 vote 過的回應
        - [x] 用桌機看[同一 article](https://dev.cofacts.tw/article/2gvs0nu9ynjo7) 可以看到自己的回應
    - [x] 可以 downvote 沒 vote 過的回應
        - [x] 用桌機看[同一 article](https://dev.cofacts.tw/article/2gvs0nu9ynjo7) 可以看到自己的回應
    - [x] 可以把 upvote 的回應改成 downvote 的
- [x] 用 LINE 造訪 article LIFF（單回應） - https://liff.line.me/1563196602-X6mLdDkW?p=article&articleId=3tu9btf8s50sm&replyId=ArnghHkBpYB_rtUxsxtQ&utm_source=rumors-line-bot
    - [x] 可以正確顯示單一回應
    - [x] 可以展開看其他回應

##### ⛔️ Release Blockers

N/A

##### 未竟項目

- Volunteer editors --> 編輯志工、闢謠志工、查證志工

> 闢謠/查證/查核  志工>編輯志工，「編輯」太籠統不知道實際做的事情

:::success
「查證志工」
:::

- 有遭遇從 chatbot 詢問是否有用，點開「是」卻跳出否的 LIFF
    - 但清 cache 之後就不會這樣了

### :eye: Under review

- #287 Update translation for 真的假的
- #289 Add AppBar and link to website

## Article LIFF

Target: receive input (feedback, reply requests) from outside of Cofacts chatbot

https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/?node-id=3004%3A224
1. [x] 實作 common component storybook
2. [x] 實作 feedback form + 使用在目前的按鈕上
3. [x] 實作 article page 的 article 部分
4. [x] 實作 article page 的 reply
5. [x] 實作 article page 的其他回應連結、cofacts 網站連結 `Before GA`
6. [x] Google analytics + `utm_source` (影響到 URL 整合，要先說) `Before GA`
7. [ ] 載入使用者自己的 feedback
8. [ ] 列出其他人的 feedback
9. [ ] 實作 article page 的 reply request form + 使用在目前的按鈕上
10. [ ] 實作 article page 的 reply request list
11. [ ] 實作 article page 的 related article

本週開發：見 staging 待測事項

## 常見錯誤回應樣態

直接在送出回應的時候偵測以下樣態，出現的話就跳出框框告知此事，詢問是否確定要送出。

- （來自[上週](https://g0v.hackmd.io/E1-ajzinSwCyacGG228VsQ?both#%E5%9C%A8%E5%90%8C%E4%B8%80%E7%AF%87%E9%87%8D%E8%A4%87%E5%BC%95%E7%94%A8%E5%B7%B2%E7%B6%93%E5%9B%9E%E9%81%8E%E7%9A%84%E5%9B%9E%E6%87%89)）複製貼上同樣的回應
- 出處沒有超連結
- 有多人詢問但使用「不在查證範圍」回應
    - 例：https://cofacts.tw/reply/PvS-vnsBqH8xU4AwxbN7
    - 提醒查證範圍：有在 LINE 上轉傳的訊息
    - 附上小聚內「找回脈絡」的教學：去 Facebook 搜尋看看 etc

直接阻擋（無法按送出）：
- 空的查核
    - 例：https://cofacts.tw/reply/J_S6vXsBqH8xU4AwC7Lz 、 https://cofacts.tw/reply/UkJBtHoBgBgcuemX5aeB
    - 會造成 chatbot bug：https://github.com/cofacts/rumors-line-bot/issues/285

:::success
1. 草擬 dialog 中的文案，下週討論
2. 阻擋空查核 --> good first issue 直接在 #285 下寫需求 - 改發在 https://github.com/cofacts/rumors-site/issues/449
:::

## 26th 小聚籌備

[前次小聚檢討](https://g0v.hackmd.io/ie1Ymj_3SlmHp0jAIy6mJw#%E5%B0%8F%E8%81%9A%E6%AA%A2%E8%A8%8E)

- [ ] 主題：26th 柚子、優酪乳與香蕉編輯小聚
    - 中秋節前後
    - 經典謠言
- [ ] 時間：9/25
	- **活動時間：14:00 - 16:00**
	- 時間分配
        - 2:00 - 2:20 開場
        - 2:20 - 3:00 進行評價 (20則)
        - 3:00 - 3:20 介紹工具
        - 3:20 - 4:00 進行回應（1則）
- [ ] Jitsi 50 人
- [ ] 投放目標： All - 北北基桃 約 10 萬人
- [ ] 事前產生 spreadsheet 50 人分工
- [ ] KKTIX：
- [ ] 誰會來呢：mrorz, bil, nonumpa, Lucien
- [ ] 做圖：Lucien (?)
- [ ] LINE 文案：


## 採訪共筆

9/15 前交

https://docs.google.com/document/d/1J8EVhWkJxHkRkRuoatfQRTQF_ZAPkCkf/edit

## 真的假的 <> downstream bots

- Update 開發進度
- 正式網址：`https://liff.line.me/1563196602-R1zEXaDB?p=article&articleId=<Article ID>&replyId=<Reply ID>&utm_source=<Source>`
    - 美玉姨: `meiyu`
    - 防詐達人: `drmessage` or `tmcheck`
    - Cofacts: `rumors-line-bot`
    - 例：
        - https://liff.line.me/1563196602-R1zEXaDB?p=article&articleId=1mpleu7bspv6j&utm_source=rumors-line-bot
        - https://liff.line.me/1563196602-R1zEXaDB?p=article&articleId=1mpleu7bspv6j&replyId=T_RKqnsBqH8xU4Aw6aYA&utm_source=rumors-line-bot
    - 網址參數
        - `p`（必填）：頁面，文章頁面固定為 `article`
        - `articleId`（必填）：Cofacts article ID，對應到官網個別文章頁面 `cofacts.tw/article/<articleId>`
        - `replyId`（選填）：Cofacts reply ID，對應到官網個別回應頁面 `cofacts.tw/reply/<replyId>`。若不提供，則會列出該訊息的所有回應。
        - `utm_source`（選填）：Google Analytics 紀錄流量來源用。請使用 `xxx`。
- LIFF 統計：https://datastudio.google.com/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/p_44cex908mc

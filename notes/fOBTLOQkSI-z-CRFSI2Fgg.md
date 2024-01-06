---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220427 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz, nonumpa, cai
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

- Revise English translation #307
- Remove additional flex alt text #308
- Revamp submission flow #303
- Removes unused code and add translation #309


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
無

##### 未竟項目
無

### :eye: Under review
- https://github.com/cofacts/rumors-line-bot/pull/303
- https://github.com/cofacts/rumors-line-bot/pull/309

## 流量與貢獻資訊開發

- Article reply feedback 紀錄 article reply 作者與 reply 文字作者
    - [Community builder](https://cofacts.github.io/community-builder/#/editorworks?type=1&day=7) 可以列出特定作者「收到」的 feedback 列表
        - 列出原文的 category
    - ETA: before the end of 2022/06
    - 未來可以用來[算 level](https://g0v.hackmd.io/8VGFKx-cR8yEdKlAQ3vv5A#%E7%AD%89%E7%B4%9A%E8%A8%88%E7%AE%97%E7%9A%84%E8%A8%8E%E8%AB%96)
- Article LIFF 流量加入資料庫
    - 呈現在 article page 圖表
    - ETA: before the end of 2022/07
- 修好 website add category - https://github.com/cofacts/rumors-site/issues/481
    - add text filter

## Multimedia 開發
- [Progress update](https://github.com/orgs/cofacts/projects/9)
    - API rebase 完了
    - 可以先測 staging 做 migration (in PR) [name=mrorz]
    - [Image-M1] Manually onboard ~10 images on Cofacts website for POC [name=mrorz] 
    - 先把圖放上 staging
- Mockup for image display: https://github.com/cofacts/design/issues/1 [name=mrorz]

## 小聚籌備

- 防疫：
    - 要求疫苗狀態 / 採檢狀態？
    - 提供線上參與選項（因應匡列） / 全部線上參與？
- 很可能全部線上參與
    - 發通知給非台北的人
    - 上次 [rundown](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2FvcKai2DNQYeZKjY8oe6O9w)
    - 可以用 big blue button by OCF
    - 有主持人功能
    - 可以先上傳簡報，不用分享 tab / 螢幕
    - 可以同時觀看影片，但線上不用播影片
    - 線上不會自我介紹
    - 線上有個缺點是不知道現在在幹嘛 [name=cai]
        - 重心要放在推廣而非工作 [name=bil]
        - 把 bot 加入群組等等
        - 主題：新疫情、兒童疫苗等
    - 主題還可以加過時訊息拿出來 [name=cai]
    - 教平常怎麼找資料 [name=cai]
        - 線上的會議會比較接近展示 [name=bil]
        - 以前[小聚簡報](https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit#slide=id.gcf39f45d47_0_807)有，但是太平面了 [name=cai]
    - 線上版：教按讚、補充意見，跳過查證 [name=bil]
        - 「線上版」的小聚開場投影片
        - ~~分類？~~ 太難 [name=bil] 手機版難用 [name=cai]
        - 專分 COVID 就好～ [name=bil]

:::success
五月上旬來改投影片
1. 現有的按讚
1. mission 2 改留補充資訊
1. 幫 COVID 訊息標 category
:::

----

- [x] 時間:
    - 5/15 (日) &  第二志願 5/21 (六)
    - 尚無回音
- [ ] 主題：
    - ？？？
- [ ] 場地：
    - [NPO Hub 2F 影響力工場（30人）](https://g0v.hackmd.io/@jothon/NPOHub-rules)?
- [ ] 食物 
    - 疫情期間不鼓勵
- [ ] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Keyholder 介紹場地
        - 2:20 - 2:40 介紹 mission 1 -幫其他查核者評審回應
        - 2:40 - 3:00 進行評價 (20則)
        - 3:00 - 3:30 休息、自我介紹、交流 
        - 3:30 - 3:50 介紹 mission 2 - 寫回應
        - 3:50 - 4:30 進行回應（1則）
        - 4:30 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：北北基桃
- [ ] 事前產生 spreadsheet 25 人分工
- [ ] KKTIX：https://cofacts.kktix.cc/events/cofacteditor30
- [ ] 誰會來呢：mrorz, bil, nonumpa
- [ ] 無法來：
- [ ] 做圖：用 Figma 做 [name=mrorz]
- [ ] LINE 文案

## 最近的謠言
- 跨境易購 完整對話話術 - https://howardyang2012.pixnet.net/blog/post/562276886 [name=cai]
    - Cofacts 上出現的名稱：SK購物、ebuy
    - https://cofacts.g0v.tw/article/3lrs0ge4qcbuf
    - https://cofacts.g0v.tw/article/3kox8kn882kyy
- 以前是對的訊息，現在是錯的 [name=cai]
    - 可以養成在回應裡面寫時間的習慣 [name=bil]

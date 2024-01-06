---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20210714 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：orz, bil, nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site
https://github.com/cofacts/rumors-site/releases/tag/release%2F20210708

- #438 Fix avatar in Landing page 

#### :robot_face: rumors-line-bot
https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20210708
- #267 Common LIFF components
- #268, #270 Replace svelte-material-ui with common components
- #271, #272 Testing env improvement
- #273 Introduce persistent AppVariable and use it to store lastScannedAt
- #274 Fix postback redis error

### :rocket: Staging

#### :robot_face: rumors-line-bot

- #275 Feedback form

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應
    - [x] 選擇回應之後可以幫回應 upvote
    - [x] 可以再次選擇 downvote
    - [x] 選完回應之後，還可以捲回去選其他回應

##### ⛔️ Release Blockers
無
##### 未竟項目
無

## 25th 小聚

- [x] 主題：Cofacts 真的假的 第25次線上疫苗關注編輯小聚
- [x] 時間：7/24
	- **活動時間：14:00 - 16:00**
	- 時間分配
        - 2:00 - 2:20 開場
            - 放影片可，但要
                - 開麥克風才有聲音
                - 只分享一個視窗且拉小一點，否則畫面會有一塊不動
        - 2:20 - 3:00 進行評價 (20則)
        - 3:00 - 3:20 介紹工具
        - 3:20 - 4:00 進行回應（1則）
    - 小聚前先給小學校的教學影片
        - 第二集評價
        - 第三集寫回應
- [x] Jitsi 50 人
- [x] 投放目標
    - 60% 報到率，預計到場 30 人
    - 過去推播：投放 27,750 人，最後 18 人報名
    - 故若想要有 50 人報名，應投放給 77,000 人
    - All - 北北基桃：![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9c0f8daf18742a31ca6fc0218e55337a.png =x200)
        - 優點：無法來實體小聚的人優先報名
    - 25~40歲青年 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_886d894ae99a1ee74ce89b1897c61d9a.png =x200)
        - 優點：這個年齡層比較會用 jitsi 與 slido
    - 結論：All - 北北基桃
- [x] 如何 50 人分工：
    - 提供 spreadsheet
    - 用 kktix 的名字來取 sheet 名
        - [need-to-check-list-generator](https://github.com/cofacts/need-to-check-list-generator) 可以吃名單生 sheet, nonumpa做
    - 一兩個人不小心做到同一個 tab or 想要多做/沒報名直接到場，就隨便找個 tab 直接做
        - 屬於少數情況
        - 若無法操作 spreadsheet（如手機使用者）就請他們點開最新查核 https://cofacts.tw/replies 下「還未有有效回覆」
- [x] 如何幫個別使用者 troubleshoot
    - 文字的私人訊息，送出還會問你要回應私人訊息還是傳給大家
    - 如果需要分享螢幕，就請對方分享螢幕（如果不介意的話）
    - 投影 Slido 問題 + 會議代碼、community builder big number
    - 在 jitsi 對話窗提醒大家也可以去 slido 匿名問問題
    - 想出聲問問題，可以先在 jitsi 舉手 :hand: 
- [x] KKTIX：https://cofacts.kktix.cc/events/cofacteditor25
- [x] 誰會來呢：mrorz, bil, nonumpa
- [ ] 誰不會來
- [ ] 做圖：https://unsplash.com/s/photos/covid-19
- [ ] LINE 文案：

大家都還好嗎？

真的假的 聊天機器人在 2021 年查了前所未有的大量可疑訊息
編輯小聚一直以來都以志工貢獻的方式，簡易而快速的幫助被不實訊息欺騙的朋友。
本次小聚將以最新疫苗情報與疫情不實訊息為討論主題，歡迎參加真的假的 線上編輯小聚，週六下午在家裡開電腦就能當志工！

## Figma 發文樣板

MrOrz 做
底圖用 fill 填

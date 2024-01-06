---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20201104 會議記錄
:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：nonumpa, 宇彤, 志超, bil, mrorz, lucien
:::

## Cofacts Next 追蹤

- 需要 FB 教學
    - Highlight: LINE bot 搜尋時會標記
    - RSS 教學: Email / IFTTT / IFTTT 進階版
    - 推播
    :::warning
    沒空做⋯⋯
    :::

## 2020 Q4 ~ 2021 Q1 Execution

> [20200923 初次提出](https://g0v.hackmd.io/-j-fAX0tS62amv9LejshOg#2020-Q4--2021-Q1-Directions)後的更新

### 已經在進行 / 已經分配
- LINE tutorial - https://github.com/cofacts/rumors-line-bot/pull/231
- Dialogflow - https://github.com/cofacts/rumors-line-bot/issues/222
- Landing page
- User profile page (列出貢獻、數字)

### TODO

- Tutorial page https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=2011%3A0
- LINE 群組訊息 
    - [原始提案](https://g0v.hackmd.io/-j-fAX0tS62amv9LejshOg#%E7%BE%A4%E7%B5%84%E8%A8%8A%E6%81%AF)：私訊看到訊息的人、在群組裡不會說話
    - 目的
        - 建立「Cofacts 會如何在群組裡對話」的示範
        - more *accurate* view count
    - 功能
        - 還是會在群組裡自動回話，但只限於：
            - 訊息相似度幾乎完全命中
            - Category: 醫藥保健、COVID-19、資訊安全
            - 狀態：has useful reply 且標為「含有錯誤訊息」、「含有個人意見」 
                > 過去收到的 feedback 是在群組裡回話會中斷討論流程，尤其是「不在查證範圍」
        - 針對群組內「已經有人回報」的訊息 (不限於會自動回話的)：
            - 送 google analytics viewed 數
                - 若群組內有 5 人，一次要加幾個 view count？
                    - 算是一個人、一次 view count [name=bil]
                - view 過 article 不代表有 view 過 reply
                    - 還是算一次 view article [name=bil]
            - 自動送出 reply request (?)
                - 在群組裡被送入，不要送 reply request，因為這與「發問」不同 [name=bil]
                - 增加 google analytics count 就好 [name=bil] 
            - 幫群組裡有加 cofacts 的人建立 `userArticleLink`
                - 放的話他可以收到新回應推播 [name=mrorz]
                - 「看過的訊息」是私人的體驗，放了會有點破壞。先不要 [name=bil]
    - 先不要功能
        - 私訊群組裡有加 cofacts 的人
        - 原始提案中的「hash 保存」
    - 技術
        - Job queue (open-source 版美玉姨的做法)
            - delay: reply token 到期之前能回就好
    - 材料
        - 自介 wording
            - 被 tag 時再自我介紹即可 [name=bil]
        - 回應時的 wording
        - ＦＡＱ：隱私疑慮、bot 誰做的、跟美玉姨的差別
            - 放主頁置頂即可 [name=bil] 
- Facebook bot
    - Deploy https://github.com/cofacts/rumors-fb-bot
    - 11 月底之前決定是否要做，屆時再去問人力
- Gamification
    - github-like contribution: https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2Fn74W64y4RiWIKt1Noxn-Mg
        - Profile page 新 tab
        - 按照時間的 visualization
        - 按照時間的 contribution (=reply, add feedback, add category, add reply request, etc)
    - 升級特效動畫
        - 回完一篇訊息之後如果有升級就會有
        - (optional) 每回一篇訊息之後，顯示進度
    - Badge 成就系統
    - badge 特效動畫
        - badge: 做完一個動作、拿到 badge 時
    - 新的公道值計算方式
        - 用於每日任務 [name=mrorz]
        - 回 200 篇送貼圖 --> 用公道值計算 [name=nonumpa]
            - 需要買一些點數
    - 每日任務
        - 任務
            - 幫 10 個回應評分
            - 回一則訊息
            - 標記 5 則訊息的 category
        - 完成獎勵
            - 完成 --> N 公道值
            - 連續 M 天完成 --> `fib(M mod 7) * N` 公道值（每週重設）[name=bil
        - 技術上跟 badge 類似，都是做完一件事情之後要計算各個成就 / 達成條件的進度；可能做完 badge 系統之後再來實作？ [name=mrorz]

## 第 22 次小聚

- [ ] 主題：訊息真的很多來闢謠吧
- [ ] 時間：11/29 (日) 14:00-17:00 (借13:30-17:30)
- [ ] KKTIX
- [ ] 準備貼紙
- 場地：NPO Hub 4 樓廚房 （台北市中正區重慶南路三段 2 號 4 樓）
    - Keyholder: Ronny
    - [ ] 場地單
    - [ ] 食物
    - [ ] 延長線 (場地有)
    - [ ] wifi
        - [ ] Nighthawk M1 + 4G sim
        - [ ] ASUS RT-N12 Wireless N300 (2x 5dbi高增益天線)
- [ ] 誰會來呢？ bil, mrorz
- [ ] 誰不會來
- [ ] 志超做圖
- [ ] LINE 文案：

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: LINE bot
https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20201030

#### :globe_with_meridians: Site

### :rocket: Staging

#### :robot_face: LINE bot

##### Feature
- [#231](https://github.com/cofacts/rumors-line-bot/pull/231) On-boarding tutorial

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應
    - [x] 選擇回應之後可以幫回應 upvote
    - [x] 可以再次選擇 downvote
    - [x] 選完回應之後，還可以捲回去選其他回應

- [x] Rich menu 測試
    - [x] 「設定」更改後再次打開，應該會保留原本設定
    - [x] 「教學」可以觸發教學流程

##### 未竟項目
- 字的位置
    - 字要放在圖的上面還下面 [name=mrorz]
    - 因為視窗會被捲到底，所以放下面比較好 [name=nonumpa]
- 「模擬傳訊息進 Cofacts」按鈕
    - 無法改字體大小，就先這樣
- Wording 更新 --> https://github.com/cofacts/rumors-line-bot/issues/216
- 圖壓縮 PNG8, 1024x1024, tinypng

### :eye: Under review

#### :electric_plug: API

Merge 後需要 migration：

- Cleanup tests #231
- Index user if not existed and log last active time for user accessing apis via backend apps #227

---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220223 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis: Bil, mrorz, nonumpa
- 線上出席：kukka, cai
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :eye: Under review

Queue monitor APIs - https://github.com/cofacts/rumors-line-bot/pull/297

Deploy 時要 clean up production redis

- https://nyogjtrc.github.io/posts/2019/12/delete-keys-matching-a-pattern-in-redis/
- `redis-cli --scan --pattern bull:expiredGroupEventQueue:*` 會有 80000 多筆

## 大松檢討

- 還是覺得實體比較好 [name=bil]

## 小聚籌備

- [x] 3/12 (六) 下午 2~5
- [x] 主題
    - 隔壁是 g0v 基礎松ㄛ小聚 :+1:
    - 白色情人節要到了小聚
    - 驚蟄（Actually 3/5）
- [x] 場地：
    - [NPO Hub 2F 影響力工場（30人）](https://g0v.hackmd.io/@jothon/NPOHub-rules) 13:30 ~ 17:30
    - 旁邊（論壇、16~20 人）有基礎松
    - 走樓梯直上二樓不被門禁卡住
- [x] 食物 
    - 疫情期間不鼓勵
- [x] 時間：
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
- [x] 投放目標：北北基桃
- [x] 事前產生 spreadsheet 25 人分工
- [ ] KKTIX：[29次編輯小聚](https://cofacts.kktix.cc/events/cofacteditor29)[name=bil]
- [x] 誰會來呢：mrorz, bil, nonumpa
- [ ] 無法來：
- [ ] 做圖：用 Figma 做 [name=mrorz]
    - 底圖直接用影響力工廠的圖 XD?
- [ ] LINE 文案


## TODO 排序

- 前次排序結果：https://g0v.hackmd.io/SETMQ8DaQDu3a5ZYnrvfpA#TODO-%E6%8E%92%E5%BA%8F
- 2021 H2 TODO: https://g0v.hackmd.io/LpBtA5-CT-m0XmlqpsdWEQ#2021-2H-Roadmap

### Chatbot
- [群組回文門檻](https://g0v.hackmd.io/SETMQ8DaQDu3a5ZYnrvfpA#%E5%B0%8F%E8%81%9A%E6%AA%A2%E8%A8%8E) :one: 
    - 讓使用者自訂門檻？
    - 有點想做私訊說群組有人傳假訊息 [name=mrorz]
        - 覺得封鎖率會上升，像是私訊打小報告 [name=bil]
- 群組 bot 自我介紹 ==:information_desk_person: 需要文案==
    - 在針對群組功能投入更多開發(自訂門檻等等)之前，應該先把自我介紹想好 [name=mrorz]
    - 除了 hi cofacts 之外，也用 @ tag 觸發？
    - 幫助大家破解詐騙、辨別錯誤的健康資訊 [name=bil]
- revamp LINE bot 送出文章 :two: 
    - https://github.com/cofacts/rumors-line-bot/issues/214
    - 方案二
    - 如何不讓使用者送自己的問句？[name=mrorz]
        - ex:「烏東打起來是真的還假的」 --> 自然語言，不會有人用相同的方式問第二次，沒有送進資料庫的價值
        - 「請問這個訊息是 LINE 或網路上看到的嗎」--> 使用者會理解成「烏東打起來」是不是在網路上看到的，他會覺得 Yes --> 阻擋失敗 [name=mrorz]
        - 「請問這個問題是你自己問的嗎」 --> 使用者會理解成「對，是我問的」--> 阻擋失敗 [name=bil]
        - 「請問這個訊息是你從 LINE 群組裡整篇轉傳分享 / 複製貼上的嗎」
            - 有「整篇」的概念不錯
    - 如果被擋住，要解釋真的假的是個機器人的概念、只接受網路上分享轉傳的訊息，沒辦法直接回答疑問、引介真人查證
    - blocks LIFF token 機制
- Deprecate LIFF token 機制
    - blocks 拔掉「傳送到聊天室」LIFF 權限
- 拔掉「傳送到聊天室」LIFF 權限
- 改掉「識別資訊」權限，換成 profile https://github.com/cofacts/rumors-line-bot/issues/293
    - 還是要改些 code (ID token 機制換成 access token)
- [Article LIFF 做完](https://g0v.hackmd.io/6mTYVWhLSTWfDcyaxYLaXA#Article-LIFF)
    - 編輯 feedback
    - 列出其他人的 feedback
    - 實作我想補充
    - 實作 related article
- Typescript
- [Article LIFF sharing 機制](https://g0v.hackmd.io/0RX4MsjRRJmBqJSKVilWMA#Share-%E5%8D%A1%E7%89%87) ==:information_desk_person: 需要 sharing card UI 設計==

### Website

- [編輯的「搜尋現有回應」難用](https://g0v.hackmd.io/NqPf1SfPQEGOZ3Z6h7Q7wA#%E6%90%9C%E5%B0%8B%E6%94%B9%E9%80%B2)
- 整合 LIFF 的瀏覽數進圖表
- 編輯教學 https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2F-G9Md9IyQauRoalIXJgenQ

:::success
Priority: 隨緣～
:::

### API

- 分配 App ID
    - 土炮的用個 YAML 檔案來管理 API clients
	- https://g0v.hackmd.io/51wwLHgvSUqtBDaP-yAVnA
	- https://github.com/cofacts/rumors-api/pull/270




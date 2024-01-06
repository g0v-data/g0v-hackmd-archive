---
tags: web3
---
# da0 Shoutout 5/23 會議

## 會議記錄
- Shoutout bot 開發文件：
https://g0v.hackmd.io/@_rTAcCrLS7W71XaFfUyIMg/r1CW3Wmf2/https%3A%2F%2Fg0v.hackmd.io%2Fc%2Fr1CW3Wmf2%2Fedit%3Fedit

#### 開發 action items
- 豆腐前端功能需要列進開發文件中 
- 下週確認前端功能需求 > Status? What's practical?
- 昶惟持續修 bug > Status?
- 昶惟開始重組後端基礎 > Status? Was there a discussion about IPFS and SBT?
- 前後端開發文件需要 PM 重整 > List of features & upgrads

## Spec list till early July hackathon

#### 公共版
- Dashboard
    1. 最頻繁使用 Shoutout 的頻道（weekly, check with 昶惟）（v）
    2. 總 Shoutout 數量（放大 Numbers 小方塊）（v）
    3. 總 Shoutout 使用人數（放大 Numbers 小方塊）（v）
    4. 使用 Shoutout 頻道數（放大 Numbers 小方塊）（v）
    5. Shoutout 時間戳記（Matt 自由發揮）

#### 個人版
- General
    - Build menu bar (v)
        - Dashboard
        - Shoutouts sent
        - Shoutouts received
    - Mobile (v)
- Dashboard
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a9efa3c48664b9fc4803395834076845.png)
- Confirmed
    - 送出 Shoutout 給多少不同的人- total different ppl sent(v)
    - 從多少不同的人獲得 Shoutout- total different ppl received(v)
    - 我送出 Shoutout 的總數量- total shoutout you've sent (v)
    - 我獲得 Shoutout 的總數量- total shoutout you've received (v)
    - 排名- Ppl who shoutout you the most (v)
    - 排名- Ppl who recieve your shoutout the most (v)
    - 時間軸- Shoutout you've received in last 7 days (v)
    - 時間軸- How much you shoutout in last 7 days (v)
- Shoutout private list
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ee5a11d7bfdd2a529c08bac391a4201d.png)

- 介面優化
    - 列的問題 Decision > 一行（之後改 RWD）(v)
    - Visual optimization of sender, time (local time zone) and channel
    - Collapse (v)
- 送出 Shoutout
    - 新頁面
- Search (postponed)
    - auto-refresh (to be confirmed with Matt)
- 可選擇看某個坑/專案 (postponed)
    - Filter (?) > 公版是否有可以使用的script
        - Channel 

- Backend
    - bot被安裝的log
    - 弄到 database 那邊，有跟 Tim 討論
- Bug fixes
    - 目前無正在修的 bug

#### 文件後續
- 指定 PM：Peixing

#### 創意回饋確認

#### TBD action items
- discussion - @3Q or @SO (pending)
- discussion - 超越性是否加入(放最後文件的rephrase)
- discussion - 使用SO的儀式性 (放最後再做討論，可先忽略)
- Peixing 確認Tofus下週二會不會上線？

## Reminder : Priorities before July Hackathon
P1 : Debug：code team keep going (from last code meeting)
P2 : Documentation
P3 : UIUX（Tofus & Bens？on build ShouOuts頁面）
P4 : API & SOB
P5 : Opensource

#### team feedback to Tofus
* Lucky sort的情境如果是日期的話可以選擇特定區間或進行A-Z排序蠻好的
* Peixing @維人 可以確認工作量，或許可以先用figma確認這兩個功能的操作流程。
* Matt 技術可執行，可以討論。UI以手機、直式來想像會比較通用，實際上的狀況每個SO的文字內容多寡不一，用一欄來設計視覺比較順暢
* 昶惟 誰發送、誰收到、內容、在哪個channel、時間、url（可抓）資訊是可以運用的

#### 公共版 archived specs

    4. 使用人數（?）
    5. 使用頻道數 (?)
    6. 頻道排行（v）
    7. 整體獲得與送出的SO數量、趨勢
        - 時間、哪個坑、哪個場合(大活動highlight? 例如各種松)
    8. 排行：獲得與送出者
    9. 可以去看任何坑的坑內版，看每個坑的互動與紀錄 (filter)
        - Shoutout public list
            - 介面優化
            - Search
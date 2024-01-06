---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20201028 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：宇彤, bil, nonumpa, mrorz, lucien, 志超
:::

## Cofacts Next 追蹤

- 需要 FB 教學 
    - Highlight
    - RSS 教學
    - 推播
- Editor contribution
    > 突然想到，elasticsearch 可以跨 index 做 search / aggregate 的特性，其實很適合拿來做類似 github 那樣的 contribution chart
    > 可以畫出使用者哪一天做了多少貢獻（= reply, article-reply feedback, replyrequest, etc）
    > 但問題是編輯會想要有類似 github 的 contribution graph 嗎
    > https://github.com/MrOrz
    > ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1d347462d295b1b25b2cb9bc4e117571.png)
    > [name=mrorz]
    >
    > github contribution 的雷達圖也很有趣，可以做 category 雷達圖，看這是一個專攻醫療健康的編輯還是全方面型的編輯
    > 你說的貢獻分類也可以畫（ reply, article-reply feedback, replyrequest, etc）
    > github 的圖使用者是不能選擇要不要顯示，還滿多人抱怨這件事情，但這感覺是可以讓使用者在 user profile 決定的事情
    > [name=zoe]
    >
    > 我們有想過
    > 讓等級高的使用者可以設定要不要隱藏
    > 但等級低的通通顯示
    > 隱私作為誘因 + 新編輯確實比較需要觀察 xd
    > [name=mrorz]
    >
    > 是一種 visualization
    > 對使用者跟對專案本身都不錯
    > 可以用 github 的
    > [name=bil]
    > 
    :::success
    Do
    - profile page 新分頁 （contribution）其他 tab 就是細節
    :::

## 萌典松

https://moe.kktix.cc/events/moed24ct

## 大松檢討

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b9646470cac95eac1c74e9373f605d8e.png)

:::success
Lucien 跟志超討論一下

結論：將選中邊框改成 primary 黃色
https://github.com/cofacts/rumors-site/issues/309
:::

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

## Google analytics for 教學

orz:
GA 報表的 goal 多步驟的要使用 screenview 或 pageview
但我們用的是 google data studio 直接顯示各個步驟的 event count 
所以也可以直接用 event 

文武:
要在 context 紀錄是從 Rich menu 來還是 join event 來的嗎

orz:
應該不用
我們只要知道第一步是哪裡
後面的步驟就不管是哪裡來的了

文武:
要細到使用者層級嗎
紀錄 session id 之類

orz:
我覺得不用
就是每一步有多少次數我覺得就很好


## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

- [10/22 release](https://github.com/cofacts/rumors-site/releases/tag/release%2F20201022): Reply page, RSS UI
- [10/23 release](https://github.com/cofacts/rumors-site/releases/tag/release%2F20201023): Makeshift edit name UI

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

- [ ] Rich menu 測試
    - [ ] 「設定」更改後再次打開，應該會保留原本設定
    - [ ] 「教學」可以觸發教學流程
        
##### Release blockers

- 中文翻譯
- 圖片

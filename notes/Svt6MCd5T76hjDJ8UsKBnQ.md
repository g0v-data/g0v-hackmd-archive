---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210224 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil,orz,zoe,文武,hsiao
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site
https://github.com/cofacts/rumors-site/releases/tag/release%2F20210218

#### :robot_face: LINE bot
https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20210218

#### :electric_plug: API

[DIFF](https://github.com/cofacts/rumors-api/compare/c2ff8f2c8f7221bf431fb760438d09b01a8e6608...d679bc118185a4df2dcc5dbda464b548a82629c8)
- #245, #246 Legal & display

### :rocket: Staging

#### :robot_face: LINE bot
- Fix group issues https://github.com/cofacts/rumors-line-bot/pull/244
- LIFF redirect https://github.com/cofacts/rumors-line-bot/pull/243

#### :globe_with_meridians: Site

- #391, #392, #394 impact report
- #393 Landing page links to tutorial
- #395 edit avatar

##### Issues
- 比鄰 iOS 無法登入 dev site
    - disable iOS safari "prevent cross-site tracking" 就可以了
    - production 沒有這個問題（不知道為啥）
    - 桌機版沒有這個問題（瀏覽器不同吧）
    - Follow-up [name=zoe]
        > production 是 cofacts-api.g0v.tw -> cofacts.g0v.tw
        > staging 是cofacts-api.hacktabl.org -> dev.cofacts.org
        > 所以 prod 不會有登入的問題
- random (票)
- open peep button anchor (票)
    - material-ui 會抱怨「不能同時設定 `anchorElem` 與 `transformOrigin`」[name=zoe]

### :eye: Under review

#### :globe_with_meridians: Site
- #395 edit avatar

#### :electric_plug: API
- https://github.com/cofacts/rumors-api/pull/247

## 2021 二月三月計畫

- 2 月底：Cofacts 影響力報告網站
- 2 月底：chatbot LIFF redirect 設定 by 斌
- 2 月底：給金控的 pitch deck
- 3/1：零時小學校＠台南
- 3/5 簡訊設計影片完成
- 4 月初：enforce API header

## 小聚檢討

[小聚紀錄](https://hackmd.io/6ecDqPqYRE-uUzo6dzUmCg)

- 人數太多，可以只推台北市就好。上上次就是只推台北市，來 10+ 人，比較舒適 [name=mrorz]
    - 也可以調低人數然後推雙北 [name=nonumpa]
    - 但受眾多的話會比較容易被封鎖 [name=orz]
    - 會變成受眾只有在台北 [name=nonumpa]
    - 或是台北或新北輪流推 [name=orz]
    - +桃園、新竹、基隆，組合可以是其他縣市一組，或是新北台北分別搭配幾個 [name=nonumpa]
    - 可以看推哪裡被封鎖率比較高 [name=nonumpa]
- 小聚流程更動 [name=bil]
    - 2:00 - 2:10 先放影片，然後介紹 Cofacts 專案。這個時間點會很多人到場，不要 cue keyholder、讓 keyholder 繼續開門比較好
    - keyholder 大概 2:30 再來介紹 [name=bil]
    - 也可以協調一個人幫忙開門 [name=mrorz]
        - 可是就會沒人量體溫簽到發號碼牌 [name=bil]
    - 自我介紹放在中間休息時間（mission 1 之後）很不錯。因為看過了回應，也有革命情感，有更多東西分享 [name=bil]
        - 遲到的也可以分享 [name=nonumpa]

## 二月底開發進度

- 影響力報告網頁 https://dev.cofacts.org/impact
- LIFF redirect https://github.com/cofacts/rumors-line-bot/pull/243
- Edit avatar https://github.com/cofacts/rumors-site/pull/395
- Github contribution [name=zoe]

## Group chatbot

- 目前狀態 analytics

### 無法回應問題

- threshold 問題：
    - 訊息 100%，但 url 不一樣或是沒有，導致相似度太低而不回應
        - 可能的解法是，把有文字 + url 訊息，url 濾掉/不要比對
    - 美玉姨傳進來的文章會被裁到 300(中文字因為編碼問題字數會變成 100) 字以內
        - 完整原文 https://cofacts.org/article/1uxerms774nca
            > 學蜂蜜的知識
            > 01：
            > 純蜂蜜不用冰冰箱，冰在冰箱會壞掉，放在室溫可以放十年不壞。
            > 02：
            > 純蜂蜜是單糖，不會長螞蟻，螞蟻只吃雙糖。
            > 03：
            > 純蜂蜜不可以和茶葉一起喝，會造成心血管拴塞，所以蜂蜜紅茶、蜂蜜綠茶等，都不能喝
        - 相似度 91%
        - 解法是送一篇完整的進資料庫 [name=nomumpa]
        - 或許有種 workaround 是可以在搜尋完之後，比對相似度時，只比對前 N 個字（N = 找到的文章的長度） [name=mrorz]
        - 但如果原始文字上千，很可能在 elasticsearch 就找不到。應該處理「文章被截斷」問題本身 [name=nonumpa]
        - 至少可以先處理相似度 7 8 成的那些囉 [name=mrorz]
- 可以有一個分類是一定會在群組回嗎 [name=bil]
    - 例子： https://cofacts.org/article/3kg93yfepgmfg 
    - 但這個相信了也沒有害 [name=nonumpa]
    - 信了這篇的後果，跟相信跟其他中國影響力一樣，所以如果這篇要回，那其他中國影響力的訊息也應該被放進群組 [name=mrorz]
    - 但 (1)他很熱門 (2) 確定事實有誤 此時應該考慮要回應 [name=bil]
    - 那變成要「有人說的算」例如說事實查核中心 [name=mrorz]
    - 或許可以用 upvote [name=bil]
    - 群組裡面回應不能選，1-1 可以選。用 upvote 可能有被操作空間，例如說天澤集團那篇 [name=nonumpa]
- 應該還是要跟使用者解釋為什麼在群組裡不會動 [name=nonumpa]
    - LINE 主頁有人問、假清亦有回報，認為 threshold 太高 [name=bil]
    - 有個 Q&A [name=nonumpa]
        - bot 為什麼不回應？
        - 隱私相關問題
        - room 無法移除 bot
        - (出現贊助後) xxx 贊助是在幫打廣告嗎？回答時又可以再感謝贊助一次(計畫通👍😃)
    - 可以自己設定嗎 [name=zoe]
        - 會變成要讓 bot 回一個按鈕之類的 [name=orz]

---

- 還沒有人建議自我介紹 [name=orz]
    - 好像大家比較在意有用程度 [name=orz]
    - 我會自己放個謠言進去觸發他的回話 [name=bil] 
    - 我在等自我介紹好再加進群組 [name=nonumpa]

:::success
1. Workaround 開票 --> https://github.com/cofacts/rumors-line-bot/issues/245
2. 「一定要回的分類」再觀察，蒐集覺得一定要回的那種，再來想辦法
3. 觀察 event input & article found 之間的相似度，計算 threshold
:::

## Pitch deck
40p

## 零時小學校

- 海報
- 傳單
- 貼紙

## Chatbot 圖片 or 影片

「我們還不支援文字以外的訊息唷！」
- 鼓勵使用者輸入文字，例如說「獅子」「蜜蜂」[name=bil]
- 但這樣會讓使用者送出「獅子」「蜜蜂」這種查詢語句進資料庫 [name=mrorz]
- 目前 OCR 不到才會回上面的訊息。可以明確說「如果這是含有文字的圖片，請手動輸入文字試試看」[name=mrorz]

:::success
開票 https://github.com/cofacts/rumors-line-bot/issues/246
決定 wording

:::

## Profile page upvote / downvote

- 編輯會希望看到自己的回應的 upvote / downvote
- 但有編輯回報，不希望 profile page 「被人攻擊 = 連續 downvote」
- 看要不要等級高的 or 簽編輯公約的，就能讓 profile page 的 voting 便成唯讀，要 downvote 必須點進回應頁面 [name=mrorz]
- 看得到卻不能點，會有點像 bug [name=zoe]
    - 唯讀時外觀可能要改一下，不要有按鈕外框 [name=mrorz]

:::success
Ticket: https://github.com/cofacts/rumors-site/issues/401
:::
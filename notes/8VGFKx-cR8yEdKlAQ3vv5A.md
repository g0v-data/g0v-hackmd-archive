---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210526 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, 4000, mrorz, nonumpa, lucien
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::


## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: LINE bot

https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20210520

- 5/15 ~ 5/19 Notification 故障
- 5/20 上線，推播校正回歸到 5/14 日起的所有有新回應的訊息
- 本週推播量與因此開啟「看過的訊息」量 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_45e36ac937ef4e4370daf091b996b942.png)





### :rocket: Staging

#### :robot_face: rumors-line-bot

- [Dockerize](https://github.com/cofacts/rumors-line-bot/pull/253) ([deploy script](https://github.com/cofacts/rumors-deploy/pull/20))

流量評估見[20210519 會議記錄](/EzCMaHOrRN--GGArbZHYrg)

##### Deploy SOP

- [x] Update `master` to latest branch
    - [x] Syncs Heroku production, so that when we want to switch back, it still works
- [x] `line-bot.cofacts.tw` up and running
    - [x] AWS credential for cloudwatch is working; `awslogs` is sending output to cloudwatch
    - [x] `/` returns
    - [ ] `/liff/index.html?p=article&articleId=fq3hn0gn4z4e` works
        - 會被 LIFF 自動登入 redirect 走⋯⋯
    - [x] log drain setup complete
    - [ ] notification cronjob added
        - [ ] `lastScannedAt` should be in Redis and available
        - Postponed to Monday, when we run the daily notification
    - [x] long term token and all other ENV vars are done
- [x] LINE developer
    - [x] Switch webhook URL to `line-bot.cofacts.tw`
    - [x] Switch LIFF endpoint URL
- [x] LINE business
    - [x] Update rich menu cache busting

-----

- [ ] 應可送出「全新訊息」
    - [ ] 問訊息來源時選擇「我自己打的」或「LINE 外面看到的」，應該會被擋下。
    - [ ] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，訊息應該還是有被送出。
    - [ ] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [ ] 可以修改理由送出。查看 article page 看理由是否有被送出。
    - [ ] 「分享到 Facebook」、「分享到 LINE」可以正常運作

- [ ] 送出「沒回應」的舊訊息，應可送出新理由
    - [x] 跳出來源視窗後關閉，文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。
    - [x] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，可以看到「提供更多資訊」按鈕，按下去可以再打開「理由」視窗
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [ ] 可以修改理由送出。查看 article page 看理由是否有被送出。

- [ ] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應
    - [x] 選擇回應之後可以幫回應 upvote
    - [x] 可以再次選擇 downvote
    - [x] 選完回應之後，還可以捲回去選其他回應

- [ ] 送出跟舊訊息相似的訊息，應提供選項選擇最像的訊息
    - [x] 按下任一訊息應該會列出回應
    - [x] 選了一個訊息之後，還可以捲回去按其他訊息
    - [x] 捲回去按下「這裡都沒有我要的」應該要跳出詢問來源視窗 (選項中不能有 100% 相似的，否則會找不到按鈕)

- [ ] Rich menu 測試
    - [ ] 「設定」更改後再次打開，應該會保留原本設定
    - [x] 「查過的訊息」應該要列出之前查過的訊息

- [x] Group chat test

##### Github action

- 分環境使用不同 ENV
    - `if github_event`
    - 研究 matrix https://docs.github.com/en/actions/learn-github-actions/managing-complex-workflows#using-a-build-matrix

## 六月小聚 @ gather?

> 本來大松在五月的話，小聚會安排在六月，不過大松延期了
>
> 不確定小聚會改在五月、或是一樣在六月，抑或是延至7月
> [name=bil]


> 疫情底下可能會有很多人想要線上聚聚？雖然延期教學比較方便呢 [name=lucien]


> 如果對象是連一般的視訊會議都會忘記關麥克風、講話會忘記開麥克風的人
> 那 gather 會很有障礙
>
> 但如果是經過這兩週 WFH 的年輕人，那應該滿適合
> 所以我覺得如果要辦的話，可以推播 50 歲以下的人
> （可以選擇所有雙北以外的人）
> 人數一樣控制在 25 ( Gather 免費版可以超過 x 人，但超過之後會比較吃力 )
> [name=mrorz]
> 

bil: 6 月已經有大松（Gather）
基礎松 50 人，一樣可以討論

mrorz: 6 月跟著大松
bil: 不推播

Gather 大松：6/ 3rd week

:::info
不辦六月小聚，跟著 g0v 大松
:::

## Article detail 調整設計

lucien:
1. au 提到「我想補充」不太明顯
    Context: 當時在討論 +1,-1 這種 peripheral 參與與「寫回應」這種 core 參與之間，是否有中間難度的參與
    orz 回說有「我想補充」，但設計目前跟 LINE 不太一樣
    au 表示看不太出來
    - Lucien: 大家可能比較習慣只有「一個回應輸入框」的網頁
2. 另外有個人把暫存檔當成回應回 https://cofacts.g0v.tw/article/r58o53xp08zt

4000:
- 「我想補充」已經比較習慣
- FB 明確說是在對誰回應
- 現在的補充好像看不見
    - orz: 對

:::warning
再想看看 [name=lucien]
:::

## 等級計算的討論

- 回應如果按讚會增加積分 [name=4000]
- orz: 目前不會
- 寫到後面會覺得重質不重量，少少的也是一分、+100 也是一分的話差異滿大的(可以鼓勵回應有質的提升)  [name=4000]
- 按了 -1 要不要扣分就另當別論 [name=4000]
- orz: https://github.com/cofacts/rumors-api/issues/124
- orz: 之前是去做個人頁面，所以就沒有繼續做等級
- orz: 技術上可能要做成，每一個經驗點都是一個 DB record，這樣不只可以算等級，也可以算每日貢獻圖 / activity log / badge 等等

### 什麼算是貢獻

- 寫回應
- 登入網站認真寫「我想補充」（chatbot 不算）
- 評價別的回應
- 分類標籤

### 什麼東西應該算公道值
- 寫回應
    - 如果複製貼上得分，寫原本回應的人會不開心嗎 [name=mrorz]
    - 回應 CC0，而且複製貼上的人也有付出時間成本，代表他比較有空，應該得分 [name=4000]
    - 我花了 3 個小時寫某篇回應，如果有人複製算他的分數那可能會不開心。但這是針對那一篇。同意複製的人也有時間成本。 [name=4000]
    - 如果寫回應跟連結回應都是一分，應該就不會有人想要抄襲（複製貼上）[name=4000]
    - 如果寫回應與連結回應分開、使得原創回應+連結的人會有兩分的話（鼓勵原創），可能就會有動機去複製貼上別人的回應 [name=mrorz]
        - 連結一則回應 = 1 分
            - 回應的作者若與連結的人不同，則回應原作者也 +1 分
        - 寫回應本身不算分
- 自己撰寫的 / 連結回應的有用程度
    - 如果寫回應的人與連結回應的人不同，兩人都會加相同的分數
- 登入網站認真寫「我想補充」（chatbot 不算）+1 分
    - 用字數判斷？[name=mrorz]
        - 有 chatbot user 會 repeat 一次謠言衝過字數，所以字數不太準確 [name=bil]
    - 用 user 判斷 [name=mrorz]
        - 可用 replyrequest 的 appId 是不是網站來判斷 
        - 這個比較可靠 [name=lucien]
    - 用有人覺得補充有用來判斷？[name=mrorz]

加公道值的幅度
- 上面都 +1 [name=mrorz]
- 寫回應 +5 [name=bil]

#### 技術

- 有個 activity 的 table 紀錄
    - 所有會算貢獻、算公道值的動作過後會記錄一筆
    - 計算等級時，撈出算等級的 activity 計算等級
    - 繪製貢獻表時，撈出算貢獻的 activity 做 aggregation

:::success
實作的 Design doc - ?
:::

## 下架個資轉傳訊息

> 您好：
>
> https://cofacts.tw/article/1t2nff4vaf372
>
>本篇文章內有家人的個資，依個資法規範，請貴單位協助刪除此篇文章。
並請轉告發文者，本人已截圖取證，若再次觸犯個資洩漏，將訴諸法律行為。
>
>謝謝
>
- 整篇移除 https://github.com/cofacts/takedowns/blob/master/2020/0610-privacy.md
- 遮除個資 https://github.com/cofacts/takedowns/blob/master/2020/0904-privacy.md
- 移除個資 https://github.com/cofacts/takedowns/blob/master/2020/1103-privacy.md

:::info
【結論】
參考 https://github.com/cofacts/takedowns/blob/master/2020/0610-privacy.md 全篇移除

https://github.com/cofacts/takedowns/pull/12/files?short_path=0324876#diff-03248763c55663da73c936f21b09fc6ca79f628d3c82c4d507c7731e62ae5a6d
:::

------

takedown 草稿

# 0526 含個資且不具查證價值之訊息遭公開

## 說明
2021/05/26 Cofacts WG 信箱接獲通知，告知下面文章具有其家人的個資：

https://cofacts.tw/article/1t2nff4vaf372

經 Cofacts WG 審議，該篇回報訊息屬為私有社團事務訊息，被送入公開資料庫。其與公共利益無關，也無關事實查核，因此決議刪除全文。

Cofacts 不會移除具有公共利益可能性的文章，如果片段刪除或隱去個人資料的情況，而內文仍然適合事實查核或者具公共利益效果，將視實際發生情況特別處理。

## 處理
2021-05-26 Cofacts 團隊修改資料庫，將https://cofacts.g0v.tw/article/3enhvccv7hnud 的內文替換為「內文含有隱私資訊」等語。

[內文含有隱私資訊，經申訴後下架，請見 https://github.com/cofacts/takedowns/blob/master/2021/0526-privacy.md ]

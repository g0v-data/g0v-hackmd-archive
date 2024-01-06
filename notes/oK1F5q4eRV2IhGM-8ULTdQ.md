---
tags: Twitter, Community Notes, Birdwatch
---

# Twitter Birdwatch / Community Notes 研究

- 2021 年初運作影片：https://twitter.com/birdwatch/status/1353774171684106243
- 2023 年改名 Community Notes
    - https://twitter.com/i/communitynotes 進入
    - 文件：https://twitter.github.io/communitynotes/
- 使用者可以回報一則 tweet ("contribute to birdwatch")
- Notes：針對 tweet 補足脈絡的東西。
- Ratings：看到 Note 的 Twitter 使用者，可以給該篇 note feedback。

## Birdwatch contributors

[![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_527eaf34a944e415525262fd80a78f35.png)](https://www.popularmechanics.com/technology/apps/a34575259/twitter-birdwatch-explained/)

### 身份認證

https://twitter.github.io/birdwatch/contributing/signing-up/

目前 Birdwatch 僅為 pilot program，參與者需符合：

- 驗證過的手機號碼與 email
- ~~美國門號~~
    - 2023 年更新：只要有驗證都行，無地域限制
- 2FA
- 在 Twitter 上沒有違規紀錄

### 註冊需同意「三大核心價值」

核心價值全文：https://twitter.github.io/birdwatch/contributing/values/

- 僅三點，簡短易讀
    1. Provide context, not insults
    2. Please be good
    3. Be helpful even to thouse who disagree
- 提醒（催眠暗示？）使用者要自我約束
- 桌面版上，隨時顯示在側邊欄 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_77b61a8c937c7bb473f7500f2457ad05.png)


### 匿名性 [^FAQ]

- Note 撰寫者的 twitter handle 在外面不會顯示，但會放在 "Note detail" 中
    - 但使用者可以使用任何 display name，與一般 twitter 帳號相同
    - 可使用分身帳號與假名
- 受試者表示「看到 note 是誰寫的」會讓他覺得該 note 更有幫助

[![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_72664d282ab9f95dfe94025c1a382b85.png)](https://twitter.com/birdwatch/status/1373033059470045185)


### 違規處理 [^FAQ]

https://twitter.github.io/birdwatch/about/faq/

使用者可以針對單篇 note 回報違規，或者手動填寫[表格](https://help.twitter.com/en/forms/birdwatch)。

若違規的話 Twitter 可以將參與者踢出 Birdwarch pilot。

## Notes

### 將 Tweet 送入 Birdwatch

https://twitter.github.io/birdwatch/about/overview/
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_20d473b80e1375b3435eda221e5fc92d.png)

- 每一則 tweet 都能被標 Birdwatch note [^FAQ]


### Selecting reported tweet to write note

好像沒這功能？似乎 “Contribute to Birdwatch” 的人，就同時要撰寫 note。

### Creating notes

[![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b89da0a339acb6e5992f197f23ff5100.png)](https://twitter.com/birdwatch/status/1366520313777897475)

- 會顯示一次 [Birdwatch Value](https://twitter.github.io/birdwatch/values)
- 勾選為何這個 Tweet 是 misleading (或不 misleading) 的理由
- 1 open text field
    - 280 字數限制
    - 一個 URL 算一個字
    - 內文會公開
- 沒附說明文字或沒付 URL 的話[會提醒說「付了比較好喔」](https://twitter.com/birdwatch/status/1382788138351857669)

### [Note status](https://twitter.github.io/birdwatch/about/ranking-notes/#note-status)

根據 note 搜集 rating 的情形，一個 note 會有[以下三種狀態](https://twitter.com/birdwatch/status/1373033026515439618)：
- “Currently rated helpful”
- “Needs more ratings”
- “Currently not rated helpful.”

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ac04544cad2af86cfa1965a513e56542.png)


### Displaying notes

Note 會在 Twitter 主站內、與 Birdwatch Timeline 內顯示。

#### Twitter 內

直接顯示在該則 tweet 下方，Pilot 期間只有參與者看得到。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0d2f84fe578c7128d86bc40fc8a6bf59.png)

- 若有 note 被標為 helpful 則[直接顯示 Note 且可以協助 rating](https://twitter.com/birdwatch/status/1400150154557202432)
    - 若有多則 note 都被標為 helpful，則會[輪換](https://twitter.com/birdwatch/status/1400150156142596109)
- 若有 note 但尚未被標為 helpful，則[僅顯示 note 數量，點擊後導到 Birdwatch site](https://twitter.com/birdwatch/status/1400150162736091143)
- 若所有 note 都被標成 not helpful，就[連卡片都沒有，只會顯示一個 Birdwatch icon](https://twitter.com/birdwatch/status/1400150168075489283)  ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5d7e8465e1d6377641f844c65c9bb6af.png)

[順序方面](https://twitter.github.io/birdwatch/about/ranking-notes/#note-status)，Needs More Ratings 的 note 以時間排序（新的在前）；Currently Rated / Not Rated Helpful 的以其 Helpfulness Score 排序。

#### Birdwatch Timeline 內

https://twitter.github.io/birdwatch/about/ranking-notes/#birdwatch-timelines

只有 like + 轉推超過 100 的 Tweet 會被列在這。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5a15dd7779f35f345b45c5ad74bd0f29.png)

- "New" tab
    - 按照最新 note 建立順序排列
    - 列表超長，跟 timeline 一樣無限捲動
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d462cfcdb14c1a018bc384b4dbb0b036.png)
    - 最末尾：![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1667773270cb546de85dc5983108eb82.png)
- "Rated Helpful" tab
    - 至少有一個 note 是 currently rated helpful
    - 至少有一個上述 note 標為 misinformed or potentially misleading
    - 大多數標為 currently rated helpful 的 note 都沒把它標成 satire
- "Needs Your Help" tab
    - 讓新 contributor 立即上路的設計
    - 展示 ~~5~~ 2 個 tweet
        - 有 note 的 status 是 need more rating
        - 自己還沒 rate 過任何此 tweet 的 note
        - 如果自己的 rating history 跟 rate 過某 tweet 的 rater 很像，那此 tweet 就比較不會出現（確保 diversity）
    - 每幾小時更新一次

#### UI 分析

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_81bfe1d3ddcf47a35e2f45456e3beef9.png)

- 加入後 Needs your help 放第一個，會直接看到
- 有明確指示：tweets need more diverse range of feedback，不會無所適從

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_267c8ca21cb882b9bcc293744e960188.png)
- UI 接近推特，推文本身 UI 無需學習
    - Community note 插入在內文與數據條之間
- 下方顯示  Community Note，title 稍囉唆但很中性 "Added context they thought people might want to know"
    - 與「查核回應」帶有「我比較有知識」相比，這個說明中性很多
    - 但同時也比較難說明一點。
    - 不過整個產品改名 community note 的話，其實頗有共筆的 Fu，這樣的標題與產品整個調性也跟著明確了起來。
    - Do you find this helpful 按下去之後才進入 Rating dialog（見下）
    - 最後再加入 Find out more 的說明

#### 一則推文可以有[多則 community note](https://twitter.com/i/birdwatch/t/1620507509688774659)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_68fb4b9c6fefa841e988fc70f5227c58.png)
- 原推 --> 明顯區隔 + 要做什麼 --> 標題與 Help icon --> Notes with 明顯區隔
- 都不放是誰寫的 note
- 用整塊標記自己的反應，哪些回過很清楚

如果 note 評分不夠，就不會直接顯示，需要手動點入「See all notes on this Tweet」
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_602393740ff479bb1331a7865131ff84.png)

#### 不同意見：「需要 context」v.s.「不用 context」
例子：https://twitter.com/i/birdwatch/t/1621691186019991553
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_557785690876031dcdc0bca4367bbd8e.png)

## Ratings

### Finding notes to rate

https://twitter.github.io/birdwatch/contributing/rating-notes/

- Twitter：顯示完 note 之後就會有 "Rate it" 按鈕（同上 "Displaying notes" 所示）
- 按下去之後顯示 dialog

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_69a423e7b294710ad8cf825f21174fb7.png)

Currently rated helpful 那塊點下去，會有 Note details

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fc377a6131094d0cf4be229aed318912.png)

#### UI 分析

- 跳窗中重點反轉，原文變小，作為評價主體的 Note 全文變大
- 顯示目前 rating
    - Note detail 再顯示完整的，告知目前 status
- 顯示最多人勾選的選項

### Content of a Rating

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_82a8d588738568e4112a2509d6288c43.png)

[20210701 設計歷程](https://twitter.com/birdwatch/status/1410288711921766401)

### "Helpful" & "Unhelpful" note & rating examples

#### Helpful
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ccc1789f50fbb30bc313adc0a546a1b8.png)

#### Not helpful
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6b163508af1b8d5723a0b98b88cae80b.png)

#### Somewhat
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ee661caf1bc915e99c3b53456e4c47f5.png)

#### 分析
- feedback 給複選很不錯，可用於統計
- Somewhat 可以正向負向都選，很有趣
- Other 勾下去時沒有自由輸入的框
- 最後再次有個 learn more

#### 送出後
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4da810e151eebae4b6fdd9aebdbf1ae6.png)

可刪改
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bb64cfac4fac0bbf2991b06dca52e34c.png)


### Ranking multiple notes using rating

https://twitter.github.io/birdwatch/about/ranking-notes/

#### Note Helpfulness Score 與 Note Status

Rating 對應到 `helpful score`：
- Yes = `1.0`
- Somewhat = `0.5`
- No = `0`

Note Helpfulness Score 是把每個 Rating 的 helpful score，用該 Rater 的 Combined Helpfulness Score 加權後的平均。

Note Helpfulness Score 對應到 Note Status:
- `<= 0.29`: Currently Not Rated Helpful
- `>= 0.84`: Currently Rated Helpful
- In between: Needs more Ratings

週期性更新

顯示 helpful / unfelpful 理由：
1. 選擇最多人投的選項
2. 若平手，則選平台上比較不常見的那個選項

#### Combined Helpfulness Score

Combined helpfulness score 跟在人（contributor）身上，範圍 0~1，是下面兩者的平均：
- [Author Helpfulness Score](https://twitter.github.io/birdwatch/about/ranking-notes/#author-helpfulness-score)
    - 類似 Pagerank 演算法，假設寫過較多 helpful note 的 contributor 給的 rating 也準
    - 一開始每個 contributor 的 Author Helpfulness Score 是 1 ($a_0(u) = 1 \forall u$)
    - 不斷 iterate 直到 converge: ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0cd9e8dec7b8d5637ad80b08dcad7b0a.png)

- [Rater Helpfulness Score](https://twitter.github.io/birdwatch/about/ranking-notes/#rater-helpfulness-score)
    - 如果你的 rating 與最終社群 rating 結果常常一致，那你的 rating 會有更高的權重
    - 只有 48 小時內的前 5 筆 rating（稱作 "valid ratings"）會用來計算 Rater Helpfulness Score，用以獎勵 early rater，也避免有人照著 rating 結果來 rate 舊的 note 刷分數。
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1c6f85a59df8492906879276b93830b4.png)


### Rater contribution

進行 rating 後，會用 notification [告知使用者 rating 的 impact](https://twitter.com/birdwatch/status/1387867559945457666)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3a5df9ed24c57bdb233d81644a0a9338.png)


## 其他

### 如何避免 Birdwatch 被操弄

https://twitter.github.io/birdwatch/about/challenges/


#### 參與者層次：避免協同操弄

第一層：Eligibility criteria 要求有手機門號與驗證過的 email
第二層：pilot 階段會優先採用與現在 participant 所 follow 的帳號不同的人，讓參與者趨近多元、減少來自同一意識型態、背景、利益空間的人。

#### 內容層次：反映多元、避免偏見

- contribution 被不同觀點的人覺得有幫助，才會給予鼓勵
- 系統可以主動邀請不同觀點的參與者來提供 rating
- 設置聲譽系統

### 相關學術研究

Birdwatch 之所以選用 crowdsource approach 且不做 background check，參考自下面三份研究：

- [Pennycook and Rand 2019](https://www.pnas.org/content/116/7/2521)
- [Allen, Arechar, Pennycook, and Rand 2020](https://psyarxiv.com/9qdza)
- [Micallef, He, Kumar, Ahamad, and Memon 2020](https://arxiv.org/abs/2011.05773)

### 與現有 Twitter 機制的關係

Twitter 本身就有[資訊操弄防治機制](https://help.twitter.com/en/rules-and-policies/platform-manipulation)，過去也有[移除帳號的紀錄](https://blog.twitter.com/en_us/topics/company/2019/information_operations_directed_at_Hong_Kong)。

Birdwatch 不會取代上述機制，而是希望與之互補。 [^FAQ]

## 外界評價

### 新聞
- Forbes: [20210125](https://www.forbes.com/sites/rachelsandler/2021/01/25/twitter-launches-birdwatch-a-wikipedia-style-approach-to-fight-misinformation/?sh=7b7332746e5f) 比做 Wikiepdia，著重在貢獻門檻
- TechCrunch: [20210603](https://techcrunch.com/2021/06/02/twitter-starts-rolling-out-birdwatch-fact-checks-inside-tweets/) 與 FB 相比，並表示比較 messy
    > Twitter is clearly aiming to decentralize this effort as much as it can and put power in the hands of Birdwatch contributors, but with audiences of individual tweeters currently responsible for deeming the helpfulness and visibility of fact checks, it’s clear this is going to be a pretty messy solution at times.
- Popular Mechanics [20210610](https://www.popularmechanics.com/technology/apps/a34575259/twitter-birdwatch-explained/) 簡介介面如 Twitter

### Skeptism feedback

針對 [Birdwatch 2021/1/26 推文](https://twitter.com/birdwatch/status/1353774171684106243)的部分回應：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e782d718e0c027c06bc9ec45ea4ba7eb.png)

其中一個不同立場網友的對話串 - https://twitter.com/_emilbergdahl/status/1353810185912016896

[^FAQ]: https://twitter.github.io/birdwatch/about/faq/
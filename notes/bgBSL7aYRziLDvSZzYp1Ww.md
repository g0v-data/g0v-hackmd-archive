---
tags: cofacts, meeting note
---

20181017 會議記錄
=====
hazel/慈/文武/orz/Bil/ggm

> 前次會議記錄：https://g0v.hackmd.io/AzZMgKyeRLGhckfvxsg0bA

## Dev

### 解禁 URL

過去討論：https://beta.hackfoldr.org/cofacts/https%253A%252F%252Fhackmd.io%252Fs%252FBJRJxopTb

:::success
新作法：只判斷總字數，`< 20` 就不讓他送出文章（但還是可以查詢現有文章）

參考：被編輯標成「長度太短」、「在跟機器人聊天」的文章：
https://docs.google.com/spreadsheets/d/1AN0YNiUWdkrOXT6NNfDvTMKpUpLTs9BF_LkABs1GZX8/edit#gid=1958593018
:::


PR:
https://github.com/cofacts/rumors-line-bot/pull/107

Hazel:
有些好像是新聞標題，其實可以查

Orz:
但新聞標題如果再 LINE 上面轉，
應該會服 ＵＲＬ

文武
可能是有人看到這個標題，手動打的

我覺得會送出理由，也可以不用擋

orz:
所以贊成事都不要有嗎

Lucien:
但送出理由認真填得好像很少
他可以擋嗎

文武：
還是有怪怪的文章傳進來嗎

orz:
36歲⋯⋯
這很短 １８字
好像是影片？

Hazel:
沒有辦法完全根絕
而且現在也沒辦法處理

文武：
就算有擋，想故意鬧的還次是可以穿過吧

只要有理由應該就會擋住想聊天的吧

因為現在會擋所以觀察不到長度
可以先拔掉觀察看看

Lucien
我們無法收圖片飲片所以有些是標題就無法進來

如果可以收圖片影片就能限制長度，因為代表那個標題不是要查證的內容

還不能收的話，就先拔掉試試看會不會造成問題

bil
換一個制度試試看

:::success
【結論】
先拔掉長度限制觀察看看
isNonsenseText -> return false
:::

### Tagging
> 請蝴蝶更新進度
> 倒數 38 天囉

### New bug: URL preview on mobile
https://github.com/cofacts/rumors-site/issues/144

### Next dev items

> 請依照年底大選使用率(both editor & LINE user)排序

#### 平權公投相關訊息列表

> 如果想做 list of 平權公投相關訊息，我們這裡需要做些什麼？
> - 先弄個分開的一頁？
> - 標記與信心水準要寫進資料庫的哪裡？什麼時候寫？
> - 是否要收集 [relevance feedback](https://nlp.stanford.edu/IR-book/html/htmledition/relevance-feedback-and-pseudo-relevance-feedback-1.html) ?
> - 用 RSS / atom 做 notification / 訂閱是否可行？

#### Bug: Github & Twitter 註冊是壞的

issue: https://github.com/cofacts/rumors-api/issues/93

> 文武 

#### Bug: 覺得有用 / 沒用的分數最多只有 10

> MrOrz

issue: https://github.com/cofacts/rumors-api/issues/77

#### 顯示覺得 article reply 沒用的理由；使用者在網站上按 Ｘ 時也詢問理由

> MrOrz

issue: https://github.com/cofacts/rumors-site/issues/97

#### 讓 LINE 使用者可以回頭按按鈕，讀其他則文章或回應

issue: https://github.com/cofacts/rumors-line-bot/issues/49

> GGM

MrOrz:
讀完一個回應之後想看另一則，兩種做法
1. 加一個「看更多回應」，按下去再顯示一次回應列表
2. 支援讓使用者回頭選擇
3. 以上皆支援

文武
1 有點洗版，使用者會想看他傳過什麼

GGM:
使用者可能被我們訓練成不會往前按

文武：
他是設計成看起來按多則，先點開看一下再決定要不要回來


## 對外

### NTU interview

> 請大家填填

https://docs.google.com/document/d/1tdysg3_bj291D1rS2fJAxZa5yuMT6jbqHzaYHZ2A8_k/edit?usp=sharing

### The Dilopmat interview


> Email Subject: [g0v-talks] Request for Interview on Fact Checking Research
> 

https://docs.google.com/document/d/112floc_56IaTe5J5s6hu8GFifkt5DgReLZU_e4bv80k/edit?usp=sharing

### I4C Campaign Accelerator Training
> Letter subject: You are invited! Campaign Accelerator Training, Annual Strategy Meeting
> 

Location: Malaysia

Expected arrival / departure: 11/3 (六)~ 11/11(日)
1. 11/4(日)~11/6(二) Campaign Accelerator Training (CAT)
--action-based learning, team building exercises, campaign planning approaches in aid of campaign and advocacy work
2. 11/8(四)~11/10 East Asia Annual Strategy Meeting
--East Asia community will identify its top priorities, goals, and outcome setting for 2019-2020; conversations on I4C-East Asia’s governance


## Latest slides available
- 20180927 bit.ly/cofacts-iada
- 20180815 bit.ly/cofacts-ayld
- 20180929 bit.ly/cofacts-seapa

## 11/11 小聚

> https://goo.gl/images/FwsmKQ
> 2018真的假的雙11全球闢謠節
> 24:00:00
> 2018.11.11
> 破解9487則謠言

iChef 2f
banner: 呃啊
禮拜天好了
崩潰

### 文案
> 鼓勵大家闢謠換購物金（誤
> 謠言闢一則送一則
> 謠言翻倍送

各種優惠名稱：
https://www.youtube.com/watch?v=Tst5oz1vi5s

## 貼圖

貼圖重審還是不給過。

## 工具包翻譯

> Hazel

準備結案

## 匡列預算

- 小聚：
    - 一次 1,500
    - 一年 9,000
- 貼紙：
    - 一組 1,000，24 組
    - 一年 30,000
- 開會：
    - 一月 4,500
    - 一年 5,4000
- 伺服器
    - Heroku 一年 210 * 12 = 2,520
    - Linode 一年 600 * 12 = 7,200

Bil
補助出國報告的機票錢，這個好像公共事務比較沒有關係

Hazel
要定義說帶回來的東西是什麼

GGM
可以決定回來之後要分享會之類

Hazel
向馬來西亞這個就是要提一個改善的案子之類的

GGM
一時想不到要做什麼

Bil:
議員投票指南做 t-shirt 跟紅包袋，行銷他們的專案
如果做行銷，錢就會噴很快

GGM
可以編列行銷預算

Lucien
之前有想要把這個投紅點 communitation design
~~cobinhood 也拿 honorable mention~~

如果有明確的目標就能做
但是我太多事情了
我拔牙也超意外是受不了 ｏｎｂｏａｒｄ第二天去拔牙耶
我被 appier reject 了耶好傷心喔
雖然他 reject 的時候已經 ｏｎｂｏａｒｄ 了

- - -

出國補助？


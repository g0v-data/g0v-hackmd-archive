---
tags: cofacts, meeting note
---

20181024 會議記錄
=====

> 前次會議記錄：https://g0v.hackmd.io/bgBSL7aYRziLDvSZzYp1Ww

## Dev

### 2018/10/21 Incident:

1. LINE bot does not respond when URL is attached
2. LINE bot does not remember the context after user submitted content

See [incident report](/xd8i1oR-Q9OEFQjOCPOplQ).

### 解禁 URL

Done。現在不會再檢查長度。

### Tagging
> 需要更多的同婚樣本

### Bug: Github & Twitter 註冊是壞的

PR: https://github.com/cofacts/rumors-api/pull/107

> 文武 

上 production，已經修好了，PR 最下面有流程

不過這個好像還沒修好

https://rollbar.com/mrorz/rumors-api/items/58

### Bug: 覺得有用 / 沒用的分數最多只有 10

> MrOrz

issue: https://github.com/cofacts/rumors-api/issues/77

### 顯示覺得 article reply 沒用的理由；使用者在網站上按 Ｘ 時也詢問理由

> MrOrz

issue: https://github.com/cofacts/rumors-site/issues/97

### 讓 LINE 使用者可以回頭按按鈕，讀其他則文章或回應

issue: https://github.com/cofacts/rumors-line-bot/issues/49

> GGM

這個禮拜或下禮拜吧

### New bug: 文章數字是壞的
https://github.com/cofacts/rumors-site/issues/145

`replyRequestCount: {GT: 0}` 會使得整個 query 回傳所有數量。
之前有做過 elasticsearch 升版（升小版號），不確定是不是這個原因。

## 對外

### NHK 出機採訪

> Email subject: `日本媒體ＮＨＫ（電視，廣播）諮詢－關於＂真的假的＂群組`

需要聯絡對口 --> bil

大家有空的時間：
- MrOrz: 平日晚上、假日
- 文武 : 同上
- Lucien: 基本同上

### NTU interview

> 請大家填填

https://docs.google.com/document/d/1tdysg3_bj291D1rS2fJAxZa5yuMT6jbqHzaYHZ2A8_k/edit?usp=sharing

### GTI talk & meeting with NDI at Washington DC

GTI talk: https://www.eventbrite.com/e/october-26-combating-fake-news-and-disinformation-in-taiwan-tickets-51088880216 with Nickmon

主要以介紹為主。但 NDI 一直在跟我們問說有沒有收 funding 的計畫。這次會面滿可能會被問到相關問題的，所以可以討論一下：

1. 收 funding 的話要有人全職工作嗎？ （參考：Mafindo & El Poder de Elegir ？）
2. funding 要拿來做什麼？（full-time worker salary? 噴錢錢宣傳？）
3. funding plan 是怎麼煉成的？

Orz:
沒有的話，我也可以用 g0v summit 時的說法，就是說我們沒準備好。

如果要拿 funding，那感覺要有明確的 KPI、宣傳計畫、要做到的東西，以及預算的分配等等。

Bil
這感覺就跟 g0v grant 很像

Orz:
嗯對，然後這個確實也是 GGM 擅長的部分，所以等他的書面答覆 (?)

bil:
如果做成每個功能都外包、一個功能一次錢呢？

Orz:
那就變成那種對外的才有錢，例如 FB bot or WhatsApp bot（選後研究）

Bil
覺得一個禮拜會花多少時間在 Cofacts 上？可以用來評估。

Orz:
要注意的是大家不會為了最低薪資放棄原本的工作，給了錢大家會有不得不做的壓力，會更累。

文武
平均 4hr/week 吧。追 bug 的話就會比較多。

bil
開源專案大家會花多少時間在裡面，每個人都不太一樣、也不是比較長就比較辛苦，所以可以每一個人都分開問


## 11/11 小聚

> https://goo.gl/images/FwsmKQ
> 2018真的假的雙11全球闢謠節
> 24:00:00
> 2018.11.11
> 破解9487則謠言


### 文案
https://cofacts.kktix.cc/events/cofacteditor11?preview_token=a19b791e380c5490fc2bc18803d51f55

## 平權社會對話工程

需要人 QAQ

https://g0v.hackmd.io/c/B1iHBvVPQ

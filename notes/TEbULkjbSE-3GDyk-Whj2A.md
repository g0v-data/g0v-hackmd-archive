---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20211201 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz, nonumpa
- 線上出席：cai
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API

Spam blocker reason setting script
https://github.com/cofacts/rumors-api/releases/tag/release%2F20211126

### :eye: Under review

- Expose user blockedReason https://github.com/cofacts/rumors-api/pull/269
- Mark blocked user browser cookies https://github.com/cofacts/rumors-site/pull/457
- Category review script 1 https://github.com/cofacts/rumors-api/pull/265
- App ID management mechanism https://github.com/cofacts/rumors-api/pull/270
    - Can be used to insert reviewer feedbacks (Script 2 in [design doc](https://g0v.hackmd.io/EcrdwfZrQOSTGX7yK6nn4w?view))
    - Can be used to [manage 3rd party apps](https://github.com/cofacts/rumors-api/pull/270) in the future

## Category review milestones

Design doc: https://g0v.hackmd.io/EcrdwfZrQOSTGX7yK6nn4w?view
Executes the script on date: 2020-07-22 (https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2F9qp8dE7dReK2q8FTeP9Feg)
```
node_modules/.bin/babel-node src/scripts/genCategoryReview.js -f 2020-07-22
Scanning 223 valid article category feedbacks...
progress [========================================] 100% | ETA: 0s | 223/223
Scanning 66931 categorized articles...
progress [========================================] 100% | ETA: 0s | 66931/66931
Result written to: review.xlsx
```
Spreadsheet: https://docs.google.com/spreadsheets/d/1Y9FrI01in2hz5eiveGknH0HE081sr7gVuk0a7hqqKuc/edit

- 2990 items;
- Can review 60 items in 12 mins; 300 items per hour

---

- 可以 crowdsource 嗎 [name=bil]
    - 近期不太行，看起來有編輯認為所有東西都是中國影響力，但這對訂閱「中國影響力」標籤的人來說是垃圾 or 他沒興趣的東西 [name=mrorz]
    - 這個 category review 機制本身就是在 review crowdsource 的東西了
    - 或許未來找到方法讓 crowdsource 的人不太標注，
- URL 不處理嗎 [name=bil]
    - 先不處理好了 [name=mrorz]
    - 這次的 script 不會把 URL title 納入 train data，AI 只會看到內文，所以確實不適合處理
- 有編輯會把公投會放分類到連署 [name=cai]
    - 有在寫回應，比較簡短 [name=bil]
    - 針對該編輯撰寫 deny reason [name=mrorz]
    - 寫信解釋 [name=mrorz]
        - 但應該只有發生嚴重的事情才用 email 聯繫比較好 [name=nonumpa]
    - 寫一篇教學分享比較好 [name=cai]
        - 教學公投應該如何分類 [name=cai]
        - https://g0v.hackmd.io/rf0A7MRfTOC613QZmFehQA#TODO-items
    - 很少人知道分類是給 AI 學習的 [name=cai]
        > 我們需要您協助調整分類，讓人工智慧可以吸收您的智慧，做出更好的判斷。
        > [UI 現有 12px 灰色小文字]
    - 中國的事件不知道要不要丟到「中國影響力」 [name=cai]
        - 如果中國影響力的讀者都對中國發生什麼事情滿有理解的話，這類訊息標成「中國影響力」或許確實有助於回應 [name=mrorz]
        - 可以改名「中國大外宣」。當時想要比較隱晦，但現在「中國大外宣」大家比較一望即知。另外還可以開新的分類「綠營大外宣」 XD [name=bil]
- 「免費訊息詐騙」放大
    - TA = 「詐騙受害者、警政署 165 反詐騙等主管機關」相同
    - 「假優惠、假投資、假工作、網路詐騙」

## User blocking mechanism

Progress moved to: https://g0v.hackmd.io/hk1v8Ka5TCmIZinQ6zKU9Q

## 未來大人物 follow-up?

網站教學文（撰寫回應）
事實查核你我做起
https://cofacts.tw/tutorial?tab=bust-hoaxes

## 網站教學的問題

> cai++

- 一開始會不知道如何下筆
- 搜尋引用會搜到很早的（超連結失效）
- 教學沒有提到 LINE 與網站顯示不同、須注意排版

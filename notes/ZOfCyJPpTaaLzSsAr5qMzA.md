---
title: "g0v 闇黑心法：用最少的力氣讓大家一起跳坑"
tags: hackpad
---

# g0v 闇黑心法：用最少的力氣讓大家一起跳坑

> [點此觀看原始內容](https://g0v.hackpad.tw/zdF0J8A10pq)

2017.11.06 小班

上週揪松團跟最近一期 g0v 獎助金的獲獎專案聊聊，一個下午跟五個專案討論其開發進度，超級燒腦。我從中歸納了一些讓社群參與協作的建議和方法，希望可以分享給開發公民科技專案的大家，大家有好用的經驗也歡迎加上。

```
警語：以下這些點不是唯一的專案運作方式，也不是說全部做到就會拿到 g0v 獎助金，請自行斟酌服用。

```
## 自動化

g0v 公民科技獎助金主要是獎助公民科技的開發，讓大家不必重複打造輪子。因此，步驟中如果有很需要人力的部分，可以試著思考是不是能夠自動化，也比較容易規模化，然後自動化不足的地方再由人工校正、輔助。

例子一：
caasi 要打造 g0v 機器人大使，但目前的開發方向，實際上需要 caasi 親自去看一個專案的每一個 commits 和訪問團隊成員，然後為討論的 log 紀錄加上 tag，以有限的人力和時間，無法規模化。
> 最妙的是，最近才說明清楚， YA0H 主要是要做 dashboard 而不是機器人 XDDD
> [name=caasi H]


討論中的建議：
- 先釐清最後要產出的結構是什麼，回頭設定要搜集的結構化資料。
- 先可以用關鍵字搜尋到專案，再請大家幫忙標示 tag。
- 機器人可以做哪些取代人力的事？例如，有沒有可能讓機器人主動吐資訊給新手，新手表示自己會 python 就直接傳有哪些 python 專案。

例子二：
美國國會台灣觀測站目前由志工協助在 Dropbox Paper 上標示台灣相關法案和下 tag。

建議：
- 可以使用 Google Spreadsheet，到時候網站系統架設好之後，可以直接餵進去，不需要請志工再搬一次。

## Release early, release often

開源名言，但真的很好用，也可以公開讓大家知道專案目前的進度。

例如推動剩食分享的 foodsharing.tw 正在進行網站首頁改版和後台分配系統的建設，但同時網站首頁可以先顯示已經有多少餐廳和麵包店加入，已經減少每天多少的食物浪費。

## Showcase

有時候，功能還沒開發完，還不能跑，但是可以先手動 showcase 如果開發完可以做到什麼程度，讓想參與協作的人和使用者可以想像，並且提供回饋。

例如名字超長的「台灣企業集團母子公司關係與環境社會責任」專案，目前進行到整理 2013-2016 年的台灣母子公司財報。虹文說：「想要做到，可以查到 A、B 兩公司的母集團，然後發現 A 公司因重大污染不斷被環保局開罰，B 公司卻形象超好，每年可以拿到政府的稅賦減免。公民就可以拿這筆資料向該集團和政府施壓。」

「這是個實際的例子嗎？」clkao 問。
「是。」虹文回答。
「那就可以先釋出來讓大家看到資料可以這樣用。」

## 成功不必在我：去中心化的社群參與

雖然拿了 g0v 獎助金，一定會有核心開發者，但有沒有辦法更去中心化的社群參與？如果核心團隊不幹了，其他人也可以撿起來做，流程也不會卡在特定幾個人。

例如，數位化翻拍歷史檔案的國家寶藏選擇使用手機翻拍，而不是專業翻拍機。任何人只要有 iPhone 和下載了 app，自行前往美國國家檔案館就可以翻拍，而不需要找人搬專業的翻拍機。

例如，真的假的 Line Bot 專案，讓任何人都可以加入查證不實資訊，而不是核心團隊每天查證查到死。

## 清楚公開的文件

要能夠讓大家去中心化參與，很重要的就是清楚公開的文件。這邊指的不只是開放原始碼，而是如何讓其他人參與、複製你的模式的文件。

例如，LostSAR 就被建議可以讓全台各地的無人機、登山、搜救社群自發加入測試無人機與 beacon 的搜救測試，不然要親自跟每個社群合作入山測試會累死。

建議：
- 撰寫測試 SOP，與測試記錄範本，以表單的形式回報，例如地形、天候、beacon 型號、beacon 功率、beacon 放置位置。

例如， foodsharing.tw 希望全台各地都有自發的食物分享社群，雖然目前後台系統還沒建置好，但可以先提供目前與麵包店簽的合約範本和如何用 Facebook 社團進行食物分享的 SOP。

## 切小坑，讓大家掉坑無負擔

要去中心化的社群參與，除了清楚的文件之外，就是要讓大家覺得這是舉手之勞，不知不覺就陷入無底洞的坑。

例如，上一期的真的假的 Line Bot 和阿龜微氣候天眼通都會舉辦實體小聚，先用貼紙、食物讓人先來輕度參與，然後再想辦法長期推坑。

例如，我在晚餐的時候發表了一下歸納的結論，就被推坑寫這篇文章。

---
分隔線
---

另外，除了社群參與的部分，揪松團這次使用德國 Prototype Fund 的一句話模板和 innovateAfrica 的四個策略去討論公民科技專案開發，也分享給大家。

### 一句話定義清楚目標使用者和解決問題的方式

針對________\[我的目標使用者\]面臨______\[什麼樣具體的問題\]，我的專案______\[專案名\]可以提供_________\[平台、APP、網站、服務之類的分類\]，以____________\[具體解決問題的方法和做的事情\]。相對於____________\[目前已經有的方案\]，我的專案_____________\[提供具體不同的解法比舊有方案更好。\]

英文原版：
For__________ (my target group), which_________ (faces a specific problem), my project
_________\[name\] provides a ___________(category like platform, service, …), which \[does
something in order to solve the problem\]. Opposed to __________ \[existing
solutions\], my project \[provides something specific that sets it apart\].

### 4 個策略：技術、資料、UI/UX、參與

- 技術策略：
    你執行專案所需要用到的技術細節，想要達成的技術目標以及技術上會遇到的挑戰。
    Tell us what technology you’re going to built, and how you’ll do it, with sufficient detail that our in-house tech team can understand your ambitions / challenges and possible synergies with other grantees or existing tech solutions.
- 資料策略
    你專案所需的資料如何取得，你會如何管理這些資料，你會如何分析使用這些資料到你的專案上。
    Tell us what data you project will require, whether you’ll acquire this data externally or whether you will generate it yourself, how you’ll do this, and how you’ll manage the resulting data resources.
- UI / UX 策略
    你會如何設計使用者經驗和介面，讓你的目標使用者可以順暢使用你的服務，你需要什麼樣的支援？
    Tell us how you will ensure that the user experience – the UX – will be calibrated to your target audience and how you’ll design the user interface – the UI – for your project in sufficient detail that our in-house experts can gauge appropriate milestones and now best best to leverage support for you.
- 參與策略（ENGAGEMENT STRATEGY）
    你有什麼策略/機制讓更多使用者使用你的服務，並且會長久使用下去？怎麼讓社群加入協作？
    Tell us what mechanisms or strategies you will put in place for your project to win maximum sustained adoption by your target audience, and how you intend doing this, in sufficient detail that our in-house experts can support your efforts.



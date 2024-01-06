---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20231220 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, nonumpa, orz
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :robot_face: rumors-line-bot

- Context revamp https://github.com/cofacts/rumors-line-bot/pull/377

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 應可送出「全新訊息」
    - [x] 問訊息來源時選擇「我自己打的」會被擋下。
    - [x] 選擇「整篇轉傳」後會詢問是否要送出訊息。
    - [x] 不同意送出訊息後可以收到感謝。
    - [x] 同意送出訊息後就會送出訊息

- [x] 送出「沒回應」的舊訊息，應可送出新理由
    - [x] 文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應
    - [x] 選擇回應之後可以幫回應 upvote
    - [x] 可以再次選擇 downvote
    - [x] 選完回應之後，還可以捲回去選其他回應

### :eye: Under review

- https://github.com/cofacts/rumors-line-bot/pull/377/files

## CCPRIP

### [comm] Transcript
> nonumpa
> 

- `detectOpenHandle` 沒東西，但 test 不會停 [name=nonumpa]
- 加了 disconnect 就好了  [name=nonumpa]

### [comm] Cooccurrence

> https://g0v.hackmd.io/@cofacts/rd/%2Ff_Ze19PhQuqx_fzOAOkohQ

PR #1 --> In review
PR #2: handlers for new states
- `processMedia` --> `askingContext`
    - Do the same thing when use chose `No`
- Implement `askingCooccurrence`
- `askingArticleSubmissionsConsent`: 2+ msg in batch route


## Bridging g0v #cofacts to other fact checking orgs

- 讓 MyGoPen 與 TFC 可以在自己工作常用的管道就看到 Cofacts channel 上的討論
- 或許有機會增加閒聊互動

## 發新聞稿經驗

> @bil

:::spoiler 原文
親愛的媒體朋友您好，

公民科技社群 Cofacts 的比鄰有一則新聞稿分享。

選前假新聞達高峰！Cofacts 真的假的調查：逾八成認為身邊親友被假新聞所害

【12 月 14 日】台灣近年對於不實資訊的關注提升，而為了了解網路社群當中實際的狀況，公民科技社群 Cofacts 真的假的 發出【假新聞與不實資訊認知大調查】問卷，試圖理解民眾對於假資訊的看法。並在 2023 年11月隨機發布的調查當中，回收超過 2,000 份問卷。資料顯示，超過 95% 的民眾認為假新聞與不實資訊的影響嚴重，且逾八成認為親友會被不實資訊或假新聞所傷害。

問卷結果也有趣地發現，近八成民眾會將假訊息跟詐騙畫上等號，但其實，假訊息背後有更深刻的操作意涵。辨識假訊息與防堵詐騙不是同一件事情，詐騙會基於金錢或是其他利益而透過誘騙、社交工程、與你建立關係的方式取得信任，並且騙取珍貴的財富與社會資產。然而假訊息除了會讓你損失金錢，還有政治上的意義，受到假訊息影響或是改變偏好，都會造成許多嚴重的後果，甚至可能會影響到民主。

從回收的結果顯示，有超過 86% 的民眾認為假訊息來自於中國，是所有國家選項的第一名。而排在這之後的則是台灣自己，有三成的人認為假資訊是自產自造，由此可以窺見台灣部分社會的極化，不同的人在同溫層當中，強化自己的偏見與想法，進而較難看見其他人的聲音。Cofacts 真的假的從 2016年開始關注假新聞與不實資訊的問題，並持續透過開發開放原始碼的聊天機器人，用守護言論自由的形式協助民眾面對不實資訊。這次的問卷回收，是一次與使用者的積極對話，並思考如何透過群眾參與與協作，創造更有韌性與民主的言論空間。

在民眾的調查回應中，我們可以看到對民眾而言，假訊息的平台前三名分別是 LINE、Facebook 與抖音（TikTok）。有許多錯誤資訊在網路上散佈，進而影響台灣的資訊環境與和諧。LINE 做為封閉群組，影像或圖片被傳到群組空間之後，就只有群組中的朋友可以看見，由於群組中不願意批判親友與避免社交衝突，使得錯誤的訊息鮮少有被指正的機會。與 Facebook 或 Blog、X不同，公開的言論場域中，錯誤的訊息比較有機會被提出來討論並且受到反駁。而私人群組當中，錯誤的資訊卻會長時間存在，大量的曝光效應造成的閱聽效果是超乎想像的。因此 Cofacts 真的假的 也鼓勵使用者把 ＠cofacts 機器人加入群組，讓他自動查證並保障資訊安全。

從 Cofacts 真的假的 的開放資料中隨機觀察有哪些具有渲染力的文字，「選舉靠中共，治國靠謊言，貪污靠政權」， 「台灣經濟是亞洲四小龍之首，台灣無知的年輕人竟然也會相信。由此可見，這些台灣的年輕人毫無獨自思考與判斷的能力，實在太可怕了。」、「台軍送反艦導彈配件去瑞士維修，結果竟然送到了山東，你看看讓你不回家，修個家電還要被老外賺差價」，尤其是在選舉之前一個月，不實訊息增加的幅度都會達到高峰，較前一個月超出 40 ％。

錯誤的資訊會造成的負面影響也包含傷害民主，在台灣的資訊環境之下，常常在社群論壇、實體活動中聽到一些民眾言論，包含：「台灣很亂」、「台灣不適合民主」、「台灣不需要民主」，就能進而讓民眾自己對民主感到失望，而用言論、制度、甚至投票放棄民主的權利，也因此在避免極化的風險擴大，會需要透過群眾協作，去找到不同年齡層與背景能一起看見的民主願景，讓和諧回到我們的社會。這些都是公民科技期待達成的社會共好與公益成果，開放與透明像是一種信仰，讓更大的對話空間，保護身邊的孩子與長輩。

社群介紹：Cofacts 真的假的
於 2016 年在 g0v 零時政府 公民科技社群提案發起，致力於做沒有人做過的事，開發資訊科技工具面對不實訊息。透過 ＡＩ 工具的建立，創造透明與公民的協作平台與第一個事實查核機器人，收到任何可疑資訊、圖片影片，都可以轉傳給機器人查證。LINE 搜尋 ＠cofacts

新聞聯絡人：
:::

發的媒體有：80 間

刊出後的樣子：
- 中央社 [媒體識讀2 / 95%民眾指假新聞影響嚴重 Cofacts：錯誤資訊傷民主](https://www.cna.com.tw/news/ahel/202312150040.aspx)
  - UDN 轉 [95%民眾指假新聞影響重 Cofacts：錯誤資訊傷民主](https://udn.com/news/story/6656/7642725)
  - PCHome 轉 https://news.m.pchome.com.tw/living/cna/20231215/index-17026065670365218009.html
  - Yahoo 轉  https://tw.news.yahoo.com/95-%E6%B0%91%E7%9C%BE%E6%8C%87%E5%81%87%E6%96%B0%E8%81%9E%E5%BD%B1%E9%9F%BF%E9%87%8D-cofacts-%E9%8C%AF%E8%AA%A4%E8%B3%87%E8%A8%8A%E5%82%B7%E6%B0%91%E4%B8%BB-021607847.html
  - 華視新聞網轉  https://news.cts.com.tw/cna/life/202312/202312152264126.html
  - 更生新聞網轉  https://www.ksnews.com.tw/20231215006-2/
- 央廣 [Cofacts調查： 95%民眾認為假新聞影響嚴重 ](https://www.rti.org.tw/news/view/id/2189890)
  - Yahoo 轉 https://tw.news.yahoo.com/cofacts%E8%AA%BF%E6%9F%A5-95-%E6%B0%91%E7%9C%BE%E8%AA%8D%E7%82%BA%E5%81%87%E6%96%B0%E8%81%9E%E5%BD%B1%E9%9F%BF%E5%9A%B4%E9%87%8D-164149638.html
- 基督教論壇報 [【假新聞充斥恐影響大選】媒體及政治人物是釋出亂源？ 學者提醒勿被下意識洗腦](https://ct.org.tw/html/news/3-3.php?cat=10&article=1397479)
- 社企流 [選前假新聞達高峰！調查指出：逾 8 成民眾認為親友被假新聞所害](https://www.seinsights.asia/article/9395)

---

- 「因此 Cofacts 真的假的 也鼓勵使用者把 ＠cofacts 機器人加入群組，讓他自動查證並保障資訊安全」像是廣告就不會被露出
- 未來如果觀察到什麼詐騙趨勢之類的，是不是可以發新聞稿，然後拿來當出處⋯⋯XD" [name=mrorz]
    - 有些不挑來源的新聞稿發表平台就會被詐騙拿來利用，如 https://cofacts.tw/article/36k1gj1gq4njn [name=mrorz]

## Checkmate.sg
https://checkmate.sg

Categories
- Scams (Messages intended to obtain money/personal information via deception)
- Suspicious Activity (Messages representing potential illicit activity, e.g. moneylending/prostitution)
- News/Information/Opinion (Messages intended to inform/convince a broad base of people)
- Spam (Unsolicited spam, such as marketing messages)
- Trivial (Trivial/banal messages with nothing to assess)
- Legitimate (Message has a legitimate source but doesn't contain claims that can be assessed, e.g. transactional messages)
- Unsure (Our checkers are unsure how to categorise this message)


想法 / 觀察
- 需要報名才能投票 [name=mrorz]
- Voting 感覺需要很多社群參與 [name=bil]
- 不需要寫回應跟出處嗎 [name=mrorz]
- 每票等值，跟 cofacts 類似；community note 會以貢獻度決定票的權重 [name=mrorz]
- 看不到幾個人投 [name=nonumpa]
- 含有不實訊息的社論，好像只能分在 opinion? [name=mrorz]
  - 例：號稱起訴書說宜蘭縣長無罪，但其實是誤讀的社論
  - 例：邱彰批評美國國籍放棄公告的英文不好的例子
  - 或許是想要 focus 在反詐騙，所以政治訊息就通通 opinion 不想分太細？ [name=mrorz]

## Hypercert

- 已向參與者告知 hypercert 怎麼拿
- 所有參與者都希望提領新台幣，也已經蒐集到所有參與者的銀行帳號
- USDC 已經轉入 Cofacts 錢包
- 接下來會轉到 Johnson 的 Max、提領成新台幣，之後轉帳給上述參與者
- Johnson 吸收所有 gas fee

## 胸針進度
- 會進行打樣
- 設計稿：![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d34b93d2c29dc8961e1fdd048087ddeb.jpg)
  - 好像還是跟我給的稿不太一樣 lol

## 實科協會

> https://g0v.hackmd.io/0Ta4gitcTJCY2Lnwll0qrw#%E5%AF%A6%E7%A7%91%E5%8D%94%E6%9C%83

- 稅籍登記 done
  - 但換地址之後還會再換
- 開協會帳戶
  - 玉山
  - 國泰世華
- 遷去 NPO hub（2024Q1）
  - 申請租一個位子
  - 通過的話可以用 NPO hub 的會議空間與廚房
- 可能接應援的服務
- 需要改章程細節
  - 協會解散後的財產，預設會被政府沒收
  - 有些 funder 無法接受上面這種規定
  - 可以改成經會員大會後，捐贈給性質相近的公益團體
  - 政府無法接受不收會費，但榮譽會員不收會費是可以的

## 下次開會

- 改到週四12/28 20:00開始 [name=bil]

## TODO

- [宣傳選務謠言筆記：隱形墨水文](https://g0v.hackmd.io/0Ta4gitcTJCY2Lnwll0qrw#%E9%81%B8%E5%8B%99%E8%AC%A0%E8%A8%80%E7%AD%86%E8%A8%98)
- [擬稿徵詢講者](https://g0v.hackmd.io/9eG8d4HgT6KSPHN58SJgFA#Comm-%E6%9F%A5%E6%A0%B8%E5%8D%94%E4%BD%9C%E8%80%85%E5%9F%B9%E8%A8%93%EF%BC%9A%E5%BE%B5%E8%A9%A2%E8%AC%9B%E8%80%85)

## OCF 資安陪伴計畫

- 解決被攻擊這件事

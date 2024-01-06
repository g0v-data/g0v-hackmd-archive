---
tags: cofacts, meeting note
--- 

20190724 會議紀錄
====
orz,文武,bil
>
> 上次開會紀錄：https://g0v.hackmd.io/s/H1V55IoWB
> 

## 小聚準備

:::danger
今天要處理完！
:::

- [ ] 主題：TBD：父親節、中元節嗎、鬼門關（鬼差、搶孤、勇闖鬼門關 = 資料庫）喔、人比鬼更可怕、返校
    - 勇闖謠言鬼門關
    - 用回應消口業、渡眾生
    - 西洋人怕鬼、台灣人也怕鬼
    - 在鬼月的尾聲，一起與好兄弟、好姐妹、回學校的小朋友、以及與資料庫裡的鬼話連篇說再見
- [ ] 時間：TBD 14:00-17:00
- [ ] KKTIX
- [x] 攜帶貼紙: bil 
- [ ] 場地：TBD
    - [ ] 茶水
    - [ ] 麥克風+插座+網路
    - [ ] 投影機
    - [ ] 延長線
    - [ ] 食物
    - [ ] 垃圾的話大樓有垃圾車
    - [ ] Talk
- [ ] 誰會來呢？
- [ ] 開場使用材料更新：https://docs.google.com/presentation/d/1QCAPtwkxreQ4EUtIWsOgR4c8h4tkRs22Qvv7jBFNrfI/edit#slide=id.g1ffc87ef17_0_23

## Logo
:::success
進行中～
:::

## 大松狀況
MrOrz：已與 BBC 傳送 analytics 等資料；另有認識 Luminate group 成員

文武：
發現不知道是不是 bug: 刪掉之後還是會出現在回應列表

orz:
因為 `normalArticleReplyCount` 不是 reply 的欄位，所以有困難

文武：
引用別人的回應也不會出現

orz：
之後想要做一個 article reply 列表，比較能反映大家的 contribution
要 notify 使用者來看的話，有這樣的列表也是好事
另外還可以加上有用 / 沒用程度 filter

> https://github.com/cofacts/rumors-api/issues/129

## 主機轉移

:::danger
要先問 g0v 這裏
:::

目標主機（ cofacts.org ）已經備齊。

先轉移 Linode 上的服務（API, DB, Site, URL resolver. resource intensive），chatbot 之後再說

- [ ] 公告下線時間（12hr）
    - [ ] LINE bot 公告
    - [ ] LINE bot 自動回應
    - [ ] FB page 公告，轉到 FB group
- [ ] 下線
    - [ ] 更換 cofacts-api.g0v.tw 與 cofacts.g0v.tw 網域到新的 IP
    - [ ] 舊機器 API server 關閉、確認服務無法存取
    - [ ] 關閉舊機器 DB 自動備份
    - [ ] 新機器 API 關閉
    - [ ] 轉移 SSL cert
    - [ ] 執行 database 備份
    - [ ] 在新機器下載備份
    - [ ] 開啟新機器 API
    - [ ] 測試 Cofacts 網站運作
    - [ ] 開啟新機器 DB 自動備份
- [ ] 上線

:::success
1. 演練一次備份的部分
3. 敲定時間，與 g0v 方確認可否執行
4. Run it! (7/31)
:::

## 活動與訪談

### 合作：專板專帳號

:::success
目前進度：暫緩。
:::

### TFD 問答
> Subject: Questions From TFD

https://hackmd.io/@mrorz/Hyw4eSh-B

:::success
orz 寫
:::

### 7/26 FB / IG 工作坊
> Subject: [g0v 揪松團] 分享工作坊資訊：7/26 Facebook 及 Instagram 工具應用工作坊

https://fbtrainingforngo.splashthat.com/

:::success
Bil 會去
:::
收到確認信了

### 8/13(二) 電視台訪談
:::success
Bil 正詢問時間
:::
對方還沒回啊啊

### 8/17 COSCUP talk

粉專幫推廣：https://www.facebook.com/story.php?story_fbid=2871354082905859&id=454607821247176

:::info
粉專貼文

❓10萬人使用的 Cofacts 是怎麼煉成的❓

「真的假的 LINE bot」從 2016 年 10 月 g0v 黑客松第一次提案走到現在，即將邁入第三個年頭囉！這三年來，網站外觀看起來一點長進都沒有，但其實從 chatbot 端訊息蒐集機制、背後的系統，到給編輯的資訊，其實鴨子划水地前進了不少。

今年 COSCUP 第一天早上，Cofacts 真的假的專案的共同發起人想用 30 分鐘的時間，與大家聊聊這一路走來我們做了哪些設計選擇、遭遇了哪些挑戰、又有哪些成果。

如果沒有搶到 COSCUP 的票也沒關係，8/17 (六) 10:40 會在在下面的 YouTube 頻道直播這場演講，之後也會放上錄影唷！

📹 直播連結： https://www.youtube.com/channel/UCeGbBclLIMoK8wzq2Mzsl8Q
🕥 時間：8/17(六) 10:40

:::


- Day1 8/17 10:40~11:20 在教室 E2-102

:::warning
MrOrz 從無到有生投影片 時間：30min / 10min QA?
Topic: 全民追真假 —— 設計開放群眾參與的即時訊息查證系統 Cofacts

Reference: 
https://medium.com/cofacts
:::

mrorz
要不要把講到「闢謠」的詞換成「回應」之類的？但我想不到更簡潔的解釋

bil
「回應」太廣泛，而且如果裡面做 counter-narrative 會更容易被說是誰的網軍

mrorz
不過「含有個人意見」確實只佔了回應的 20%
還是先不要換好了

:::info
## Abstract

隨川普創造「Alternative facts」一詞以來，事實查核 (fact-check) 在國際社會漸成顯學。分析訊息、查證來源、並且撰寫嚴謹的查證報告，都是一門專業，世界各國民間紛紛成立專業的事實查核組織，針對各種訊息進行闢謠。然而，闢謠結果的散播力往往不如原始謠言，而且也遭美國保守派質疑報告公正性。

如果高度專業的「事實查核」這麼難，那麼沒那麼專業但還是很有用的「提供不同觀點的連結」這件事情，有沒有辦法透過群眾協作來達到、然後直接在謠言流通的平台進行傳播呢？

「Cofacts 真的假的」是一個開放原始碼的群眾協作查核專案，以 LINE chatbot 蒐集 LINE 網友回報的留言、設立資料庫讓群眾一起來寫 chatbot 的回應，並且鼓勵 LINE 使用者將 chatbot 的回覆轉傳回去謠言所在的聊天室，希望能降低大家取得不同意見的門檻，並且讓謠言止於 Cofacts 使用者。專案自 2016 年啟動以來，在獲得 2017 年春季公民科技創新獎助金計畫之後，已經累積超過 90,000 名 LINE 使用者、並且回應上萬篇的 LINE 轉傳訊息。

在專案運作的 2 年半，我們走過了大選、經歷媒體報導、民間團體間的合作、也有來自陰謀論者的質疑；而專案也從最一開始的 chatbot，透過志願編輯的熱血參與、CC0 開放數據資料、開放 API、熱心工程師與研究者的響應，逐漸成長為 Cofacts ecosystem。近半年來，資訊戰與假訊息的議題不斷進入公共視野，就讓我們一起探討事實查核與開放參與應該如何設計、有哪些取捨、又有哪些成效吧。
:::

### 8/25 高雄
> 6pm
> 內容：網站如何使用與心得分享
> 現場供餐

:::success
GGM 會去
:::

### 9/13 OFF in 華山擺攤

:::success
FNC 2人
Cofacts (ggm or bil), johnson
:::



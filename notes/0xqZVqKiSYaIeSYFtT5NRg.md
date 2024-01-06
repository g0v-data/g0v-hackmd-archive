---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20200513 會議紀錄
=====
orz,bil,文武
Workis
> 線上開會： https://tico.chat/powercall?room=cofactshack&type=timeFirst
> 上次開會紀錄：https://g0v.hackmd.io/@mrorz/B1X4EkJcU

## 5/24 在家大松

> 「g0v 零時政府又在家黑客松 Stay Home Hackath39n」開始報名囉！
> 在疫情警報解除前，黑客松仍然維持線上參與的形式，歡迎大家在各自舒適的沙發或床上一起參與 Hacking～
> 【g0v 第參拾玖次又在家黑客松 Stay Home Hackath39n】
> :bulb: 時間 Date：2020/5/23 Sat. 9:20 - 18:00 GMT+8
> :bulb: 給參與者的直播 Livesteam channel for general participants：https://youtu.be/Ub9B1MidV3k
> :bulb: 討論地點 Online Chat：g0v Slack https://join.g0v.tw/
> :bulb: 報名頁面 Register for participants：https://bit.ly/g0v39thregister
> :bulb: 活動共筆 Note：https://g0v.hackmd.io/@jothon/g0v-hackath39n （新手必看！！）
> :bulb: 捐款支持 g0v 黑客松永續發展 Donate to g0v Hackathon：http://bit.ly/moneyg0v
> 
> [name=ichieh, g0v#general]


### 誰會來

在家組
- nonumpa

Workis 組
- mrorz
- bil

### Good first issue
:::danger
下週處理
:::

https://github.com/cofacts/rumors-line-bot/labels/good first issue
https://github.com/cofacts/rumors-site/labels/good first issue
https://github.com/cofacts/rumors-api/labels/Good first issue

### 標記作業？

> 上了的話 @darkbtf 就可以把我們現在標的好的資料含若水標記的資料全部打回去哩
> 
> [name=ggm, [g0v#cofacts](https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1588662781.346900)]

## 台南

### 2020/05/31

:::success
2020/5/31 (日) 1:30pm ~ 5:30pm
:::


~~方案 1：mrorz 講 coscup + bil 講案例~~
方案 2：第二十次台南小聚
我兩個月前超前部署！！！！！KKtix已經好了欸打開還嚇一跳XDDD
- [x] 主題：
    - 好想在台南小聚喔
        - 主視覺：孔廟 牛肉湯
- [x] 時間：5/31 (日) 2:00pm ~ 5:00pm
- [x] KKTIX(https://cofacts.kktix.cc/events/cofacteditor20)
- [x] 攜帶貼紙 - bil
- [x] 場地：會是[好想工作室](https://goo.gl/maps/MBd7jz6gDK3J3fJV9)（含場佈：1:30 ~ 5:30）
    - [x] 水
        - [ ] 自備水杯
        - [ ] 紙杯
    - [x] 麥克風+插座+網路
    - [x] 投影機
    - [x] 延長線
    - [ ] 食物 - Rosalind
        - [ ] budget: <2000NTD (NTD80 / 人)
    - [x] 垃圾桶
    - [ ] ~~Talk~~
    - [ ] 路標、黏土 - mrorz
    - [ ] wifi（現場有）
        - [ ] 小松 25 人不是問題
        - [ ] Nighthawk M1 + 4G sim
        - [ ] ASUS RT-N12 Wireless N300 (2x 5dbi高增益天線)
- [x] 誰會來呢：mrorz, bil, 文武,RR
- [ ] 誰不會來：
- [ ] LINE 文案

Rosalind
可以透過台南地方社群擴散
kktix done 時通知

週末

:::success
需要加印貼紙：LINE 貼圖的圖
:::

### 2020/06/01 台南大學

型式：同政大

:::warning
TODO: 需要 O/X 的 instant
:::

## Production Release Plan

Discussion: https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1589252345.423700

### Versions / release scope

- [API](https://cofacts-api.hacktabl.org) - https://github.com/cofacts/rumors-api/pull/153
  - staging article page load 不完會不會是這個造成的？
- [Website](https://cofacts.hacktabl.org) - https://github.com/cofacts/rumors-site/pull/249/
  :::danger
  **Release blocker**
  - [x] ~~Reply upvote / downvote is borken in Detail page~~ Done in [PR#249](https://github.com/cofacts/rumors-site/pull/249/files), review pending
  - [x] article page load 不完 ([討論](https://g0v-tw.slack.com/archives/C2PPMRQGP/p1588665581350300))
  - [x] No "熱門回報" in article list ([Mockup](https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=428%3A37), [Spec](https://g0v.hackmd.io/@NFi0czulSemxCM8RNSlz8Q/HJ8xT3QVU/%2FahtI6xsFRQyxktrIlc1VcQ))
  - [x] Correct "For you" filter ([Spec](https://g0v.hackmd.io/@NFi0czulSemxCM8RNSlz8Q/HJ8xT3QVU/%2FN8I2-zkJTaS35BP8VH8ZQA))
  - [x] Google Tag Manager setup (see 成效追蹤 in [Spec](https://g0v.hackmd.io/@NFi0czulSemxCM8RNSlz8Q/HJ8xT3QVU/%2FahtI6xsFRQyxktrIlc1VcQ))
  :::
- [Chatbot](https://lin.ee/1QUzEX4nI) - https://github.com/cofacts/rumors-line-bot/pull/184

文武：
load more 以前有 7~8 頁，以前可以切到第七頁去看，現在你要按很多次

orz
現在有日期 filter

但 custom date 好像一定要 start, end 都給才有作用
(好像只有 for you 的是壞的？？article list 的好像可以)

文武
有日期就還好

### Progress

- [x] Deploy API: `api` image label 改 `pr153`
- [ ] Deploy production english version
  - [x] [English Chatbot](https://lin.ee/2Ox46aqyW): Deploy `dev` branch
    - [x] LIFF app & env
      - [x] env: `ROLLBAR_CLIENT_TOKEN`, `JWT_SECRET`, `MONGODB_URI`, `LIFF_URL`
      - [x] Fix LIFF issue
  - [ ] Website: `site-en` image label 改 `pr249-en` in docker-compose file
- [x] Translate to TC
  - [x] Chatbot PR: https://github.com/cofacts/rumors-line-bot/pull/187
  - [x] Website PR: https://github.com/cofacts/rumors-site/pull/253
- [ ] Introduction text
  > TBA
- [ ] Deploy production TC version
  - [x] Chatbot: 
    - [x] env: `ROLLBAR_CLIENT_TOKEN`, `JWT_SECRET`, `MONGODB_URI`, `LIFF_URL`
    - [x] merge to `master` and push
  - [ ] Website: `site-zh` image 改 `tbd` in docker-compose file

### Rollbar quota available

:::spoiler Rumors-line-bot + rumors-site

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_77ed2efcd125790032a11d139787f519.png)

:::

:::spoiler rumors-api + url-resolver

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a24cdf325d7e5b89fedc84083eeb1f5a.png)

:::

## Youtube API audit

Discussion: https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1589175218.421000

> 上週 Cofacts 配合 Youtube API Services Team 的 audit 調查，對方表示 Cofacts 在下面兩點不合格：
> 
> 1. 沒有在 Privacy 與 ToS 中提及 Youtube ToS - Policy #: https://developers.google.com/youtube/terms/developer-policies#a.-api-client-terms-of-use-and-privacy-policies|III.A.1,2
> 2. 沒有每 30 天就重新更新爬到的 non-authorized 資料 - Policy #: https://developers.google.com/youtube/terms/developer-policies#e.-handling-youtube-data-and-content|III.E.4.a-g
> 

> 2 的部分就就滿討厭的，不只技術上很煩，也會影響 Cofacts 的使用——一但原始謠言影片被下架，30 天內資料庫被強制更新，那個影片的 title 與 description 就會被洗掉。
> 
> 我在 audit 時給的例子就很明顯，謠言本體剛好是個被下架的影片，拿另一個被重新上架的影片去查，還能查到對應的訊息：https://docs.google.com/document/d/1hlFszsLV9uUJl17L40o6AGZVtyAEoTcLA76wSz969QI/edit
> （註: 步驟裡的那個 query 影片之前還活著，大概最近幾天也下架了⋯⋯）
> 
> Cofacts 之所以製作 URL preview，其中一個目的就是為了保存訊息被回報的當下，連結裡面的內容，以供未來查詢比對。如果要求我們每 30 天要更新，效果會大打折扣，以上面這個 COVID-19 陰謀論的例子來說，甚至會影響到 COVID-19 的防疫。

### Data retention 問題

bil：google 會先了解狀況

### Terms & Privacy review

As-is
- [網站 Cofacts TOS](https://hackmd.io/mFSlWs4IQke_9RnFAOWlfQ)
- [Chatbot TOS](https://hackmd.io/t2DSbtU9RsS8cNTi-uLtSQ)

:::warning
- 要改什麼
  - III.A.1 state in their own terms of use that, by using those API Clients, users are agreeing to be bound by the YouTube Terms of Service + link
  - III.A.2.a. be prominently displayed and easily accessible to users at all times
- 如何公布
- 時程
:::

bil: 等 google 回信

## Chatbot 「過去傳過訊息」 實作

https://g0v.hackmd.io/eIeU2g86Tfu5VnLazNfUvQ?view#Implementation-detail-2020510

## userId / appId 管理

https://g0v.hackmd.io/ZcoUOX_-RQSkJyl5xz4_Zg?view

## 組織化
:::info
Comparison: see [20200506](https://g0v.hackmd.io/@mrorz/B1X4EkJcU)

Cofacts 業務為維護產品、單一社群的經營與營造，有較單一的目標；與社群行政工作較為不同，因此對外的機會也不同（grant）。

而 Cofacts 在進行 funded project 時，很可能會排擠到 OCF 服務其他國內社群的資源。因此若 Cofacts 本身能有法人、可以自理的話，就不用佔用 OCF 有限的服務社群的資源。
:::

公司 v.s. 非營利組織

bil

差別：

- 非營利組織對會員大會負責，公司監督比較少
- 沒有獲利模式的話要自己養公司。雖然還是可以接贊助，但不確定是否適合。

會費？
組織章程會寫收入來源，其中一個是會費。

bil 不希望請求會員繳交會費，i.e. 章程寫會費是 0。

所以可能就只靠 grant 剩餘款

lucien
靠募捐的話可以不用收會費嗎

bil
一定要收，但是可以多可以少

lucien
要給會員什麼東西嗎

bil
最少會有大會的選舉投票權，改選理事長（四年一次）與董事

lucien
Cofacts 提供的查核服務還滿具體的

bil
組織會有財報、會計師簽核
租用募捐系統 etc。


## Gamification

Lucien
每日任務
看系統的目標是什麼
例如說是增加回應的話，
那妹個人回來做的前幾個事情就是回新訊息
然後第一、二個任務給予高回饋，或更明確的效果，讓他想要回來

登入後的「等你來查」會有本日任務

要先討論 metrics 要訂哪一個

再來是要不要鼓勵跟謠言互動，而是鼓勵人跟人互動
例如現在回報的時候有討論
查核討論

orz
我想到的 metric 是維持現在 9:1 的有用沒用比例

lucien
可以訂一些像是一篇回應要有 10 人 review 之類的

feedback 一個是經驗值，另一個是遊戲特效 micro-interaction
導入 global toast 進去

文武
遊戲有些是畫個框框
使用者就會想要把它填滿

lucien
現在有一排洞了
如果是展示目的性的話，假設有 10 個洞，有 5 個完成，個人頁面會顯示 5 個東西，點進去才會看到 10 個洞

看會不會要把展示跟自己看的頁面分開

orz
如果 hoax for you 那一頁要放每日任務
那感覺好像還可以放在那裡

lucien
變成成就的東西可能會在那一頁出現


（聊遊戲）

orz
為什麼遊戲可以創造一種回饋
又沒有發錢

lucien
遊戲會給的是一種在社群之間的影響力的虛擬的貨幣
年輕人因為時間比較便宜所以會願意花時間獲得這種貨幣
而比較有影響力的人則會尋求把現有的影響力 convert 到這種獲益的東西

對 cofacts 來說，查訊息的人不是要關注的點
而是要創造出讓查核者覺得有價值的東西

如果能做一些營運
例如說今日排行、熱門文章的排行
讓使用者知道，自己的回應是被很多人傳誦的，知道自己的回應有影響力
後面就是看要不要燒錢用 email 寄送

orz
熱門文章的排行 --> [community builder for 小編](https://g0v.hackmd.io/@mrorz/B1X4EkJcU#New-idea-Social-media-toolkit)
不過那個是進 facebook group，對網站來說是一種外掛，跟網站整個是平行的系統
但也可以視為一種 MVP


## Hackfoldr 整理

- 新文件
  - [Dev doc](https://hackmd.io/@mrorz/r1nfwTrgM) + [ER model](https://g0v.hackmd.io/@mrorz/S1caurZq8)
  - Updated [database relation graph](https://g0v.hackmd.io/@mrorz/S1caurZq8)
- hackmd book mode 替代 hackfoldr?
  - beta.hackfoldr.org/cofacts --> ethercalc.org/cofacts --> Google spreadsheet --> display，載入在很差的網路下要數十秒，且 ethercalc 回應速度不穩定
  - Hackmd book mode: https://hackmd.io/@cofacts/HkvKIkO9U
    - 可[自訂 URL](https://hackmd.io/c/tutorials-tw/%2Fs%2Fhow-to-share-note-tw): `/home` ? `/index` ?
    - 可[自訂 CSS](https://hackmd.io/c/tutorials-tw/%2F%40docs%2Fcustomize-font-color-zh) 甚至做出 [dark mode](https://hackmd.io/c/tutorials-tw/%2Fs%2Fhow-to-embed-note-tw#%E9%80%B2%E9%9A%8E%E9%81%8B%E7%94%A8%EF%BC%9A%E5%B5%8C%E5%85%A5%E8%83%8C%E6%99%AF%E4%B8%BB%E9%A1%8C)
  - Hackmd 主站 team space
    - https://hackmd.io/team/cofacts?nav=overview
    - 但新的會議紀錄仍然應該放在 g0v hackmd，因為主站免費版的圖會放在 imgur，[放久了會消失](https://hackmd.io/c/tutorials-tw/%2F%40docs%2Fhow-to-upload-images-in-team-tw)
  - Backward Compatibility
    - cofacts.g0v.tw/hack --> 直接換成新的
    - 所有文件保留，以免 break 過去的超連結 (email 裡面應該有不少⋯⋯)
    - bit.ly/cofacts-quickstart --> 同上，繼續放著
      - 但裡面的 URL 可以通通換成 book mode
    - 首頁放上新 hackmd book mode 說明，並且鎖定 hackfoldr spreadsheet 編輯權限



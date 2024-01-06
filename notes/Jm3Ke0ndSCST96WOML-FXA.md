---
tags: cofacts, meeting note
---

20190821 會議記錄
=====
> 上次開會紀錄：https://g0v.hackmd.io/@GuJ5fZ3uR-O09mlTi1w2UQ/B1pOYXZVB
> 
orz,文武.bil
## 小聚準備

:::danger
今天要處理完！
:::

- [x] 主題：鬼門關（鬼差、搶孤、勇闖鬼門關 = 資料庫）
    - 勇闖謠言鬼門關
    - 用回應消口業、渡眾生
    - 西洋人怕鬼、台灣人也怕鬼
    - 在鬼月的尾聲，一起與好兄弟、好姐妹、回學校的小朋友、以及與資料庫裡的鬼話連篇說再見
- [x] 時間：8/31 14:00-17:00（青平台已經確認）
- [x] 人數：25
    - bil: 不要超過 25, 超過會認識不到人, wifi 會爆
- [x] Banner 改舊的圖 - lucien
- [x] KKTIX
- [x] LINE 推播（不要提到 g0v 否則會爆量，造成困擾）
- [x] 攜帶貼紙: bil - 殭屍
- [x] 場地：青平台
    - [x] 茶水
    - [x] 麥克風+插座+網路
    - [x] 投影機
    - [x] 延長線
    - [ ] 食物 - 當天看人數與報名決定，如果人數爆滿的話就先訂二號出口的仙草冰，bil 已經觀察很久了
    - [x] 垃圾的話大樓有垃圾車
    - [x] Talk - maybe coscup by mrorz
    - [ ] 青平台說樓下門禁變嚴格，需要簽到單 --> KKTIX 可列印
- [x] 誰會來呢？orz, bil, ggm, 文武
- [ ] 開場使用材料更新：https://docs.google.com/presentation/d/1QCAPtwkxreQ4EUtIWsOgR4c8h4tkRs22Qvv7jBFNrfI/edit#slide=id.g1ffc87ef17_0_23

:::info
## LINE 推播文案

(clock)「Cofacts 編輯小聚」就在下週六囉 (clock)

機器人為什麼可以精準地陪你查證 LINE 的謠言，都是因為每兩個月有一群義工無私的付出——也就是讀到這行無私的你 (moon wink)

一起加入把手上的燈提高一點就能照亮更多朋友的行列。參加小聚活動，瞭解更多媒體識讀的資訊，並且一起把不實訊息的澄清送進資料庫，你的回應就會出現在「Cofacts 真的假的」、「美玉姨」、與「趨勢科技防詐達人」唷！(clap)(clap)(clap)

不管你是從一開始就支持「Cofacts 真的假的」的好朋友，或者是聽到「美玉姨」才認識的好朋友，都歡迎一起來替 LINE 上的轉傳訊息，撰寫回應。沒有現場的大家一筆一筆回應，機器人就很難動啊，所以真的萬事拜託了，缺你不可 (please!)

（當天要查很多資料，記得要帶電腦 💻 來唷！！！)

時間：2019/8/31(六) 2pm ~ 5pm 
地點： 台北市中正區中華路一段77號6樓之1 (最近的捷運站是西門捷運站)
線上報名： https://cofacts.kktix.cc/events/cofacteditor15
:::

## Dev

### cofacts-url-resolver migrate 到 gRPC
> 桓誠

### rumors-site
https://github.com/cofacts/rumors-site/tree/next

- No FOUC
- Material UI (CSS 內建 `withStyle` / `useStyle`)
- apollo-client (local state 取代 redux)
- next-i18next

### 搬主機
沒解，訂一個 downtime 吧。

Domain change: https://logbot.g0v.tw/channel/g0v.tw/2019-07-29
    > 發個 PR 並且寫有沒有希望明確切換的時間，然後看看 domain team 有沒有人該時間能配合？
SOP: https://g0v.hackmd.io/@GuJ5fZ3uR-O09mlTi1w2UQ/ryxpCDrfB?type=view#%E4%B8%BB%E6%A9%9F%E8%BD%89%E7%A7%BB

:::warning
小聚後再處理
:::

## （未雨綢繆）CIB 處理

Ref: [Cofacts 真的假的網路平台編輯使用者規範](https://hackmd.io/mFSlWs4IQke_9RnFAOWlfQ)

Should we handle [CIB (Coordinated inauthentic behavior)](https://newsroom.fb.com/news/2018/12/inside-feed-coordinated-inauthentic-behavior/)?

Rules
- coordinated: 多帳號、註冊時間接近
- inauthentic behavior: 洗版等貼的東西類似

反應
- 公布在 Cofacts 上的貼文？
- 回報給 FB？

- - -

bil:
如果有人充滿熱誠，回了幾十篇，那是不是要先聯絡這個人
而不是先放在上面公審

orz:
一個人的話不會是 CIB，比較像帝吧出征，一次 10 個 20 個人

bil
還是要聯絡到這些人

orz
如果這些人不回呢

inauthentic: 背後的不是真人，一人操作很多帳號等等
coordinated: 一群人說好要來做一個 behavior 

FB 會處理 CIB 是因為這樣的東西在平台上一天，都會降低平台的可信度。

bil
我會希望可以先聯絡到他
如果有 email 或 fb 或來過小聚的話

文武
網軍通常都是躲在背後，會露臉的會現場挑戰你

mrorz
twitter 是公開之後刪掉一堆
FB 是不公開然後刪掉

bil
所以 FB 刪得有點少

文武
我覺得 Facebook 這樣做會有爭議

bil
所以中國抗議說侵犯言論自由

mrorz
Facebook 與 twitter 都是依照「行為」違反「社群守則」而刪文。
CIB 是「行為」，不管內容是什麼立場，做了 CIB 違反社群守則就會被刪文。
這跟中國用文章內容「立場」來刪文非常不一樣。

我覺得可以回報給 FB

文武
但回報給 FB 也只能幫到 FB
像之前有個俄國註冊的 email 好像就被 FB 砍了

mrorz
那我們可以像 twitter 包成一包公佈出來
然後下架？

bil
PTT 也是公佈出來然後下架？
是清除帳號：https://disp.cc/b/163-bxVA

文武
下架是比較簡單的做法，也可以做成標記為垃圾 etc

mrorz
ptt 好像沒有公開說他是怎麼判斷的

bil
因為實名制跟站務資料吧，認證信箱之類的

mrorz
感覺是個資
若是用 IP 判斷，好像也不好公開
那他會刪掉過去的文章會推文嗎

bil
好像不會

mrorz
另外我有在想的機制是
如果量太大但又一直來
要不要先把資料庫鎖定（elasticsearch 可以把 index 鎖成唯獨）
等到我們調查完、清理完之後再解除

bil
可以發在社團裡面建檔

mrorz
可以
處理的過程 = 把這段時間大量異常的回應整理在 spreadsheet 裡面公開給大家看

這段時間要不要鎖定資料庫其實滿 minor

鎖定的優點是新的搗亂不會來
缺點是社群如果想要幫你寫新回應，會做不到

要不要鎖定感覺是多做的

文武
可以只鎖一篇？

mrorz
這跟所全部的優點跟缺點一樣，不過範圍限縮在一篇訊息
那還要聯絡嗎

bil
有公開在社團的話，他（們）應該會自己看到，不用聯絡

mrorz
公開之後要做什麼呢

bil
先詢問請教
「有人認識這群人嗎」

mrorz
所以處置的部分交由社群討論再處理囉

那要公開我們為什麼覺得這些訊息屬於 ＣＩＢ 嗎

bil
是要阻絕有人帶風向嗎

mrorz
其實我想抓的比較接近無意義洗版
例如說過去一個小時新註冊的 10 人，在很多篇文章洗類似的回應之類的

那其實好像只要公布回應，大家一看就知道這是洗的
也不用多解釋什麼

bil
跟過去有人用程式灌訊息進來一樣

:::success
處理方式：
1. 先針對 CIB 回應建檔
2. 在編輯社團公布 1 的檔案。其為 CIB 應為一望即知，無需解釋。
3. 在社團中形成如何處理這群訊息的共識。
:::

## 台灣駐曼谷代表處跟朱拉隆功大學預計在10/21舉辦論壇
> RE: [cofacts] 真的假的專案簡介

:::success
MrOrz 要回
:::

## NPOst
> 【 NPOst ＸNPOwer 公益行動家 】入選通知
http://npower.npost.tw/#_4

- NPOwer 將於 8/27-9/15 舉行網路投票，我們將以團隊所提供的簡介資料與簡報整理後上傳，網路投票獲得票數將會計入最終評選分數中，占比為20% 。
- 若您要抽換介紹簡報，請於8/23 中午 12:00 前提供，總篇幅需維持在 5 頁以內，提醒您，若您的簡報圖片較多、缺少清楚的說明文字，建議您斟酌修改。 


日期：9/17 （二）14:00-17:00 （14:00 報到）

地點：紀州庵文學森林三樓人文講堂（100台北市中正區同安街107號）

進行方式：簡報時間為 6 分鐘，評審問答 4 分鐘（確切時間順序將於決選前夕通知）

當日發表之簡報檔案繳交：請於 9/11（三）12:00 前轉成 PDF 檔傳送至 pennypan-at-adct.org.tw，並不得於現場抽換內容。

備註：請向專業評審介紹貴團隊的公益計畫，也以此作為年會分享的發表試講。當日發表之簡報篇幅不限，但請務必注意，您的發表時間只有 6 分鐘。

2019 NPOst 年會「撐起一個地球的好事：公益的數位動員」，請於8/31 前填妥貴賓表單，我們將優先為您保留席次。年會相關資訊如下： 

·  日期：2019 年 10 月 18 日

## OpenUP Summit
> Hi,OpenUP Summit敬邀真的假的設計團隊擔任講者

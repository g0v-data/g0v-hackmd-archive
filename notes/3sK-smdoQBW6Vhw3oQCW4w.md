---
tags: cofacts, meeting note
---

20190911 會議記錄
=====
bil.文武.orz
Lucien (沒喝到飲料)
> 上次開會紀錄：https://g0v.hackmd.io/@GuJ5fZ3uR-O09mlTi1w2UQ/rJUCYp2SB
> 

## 10/6 小聚

- [x] 主題：國慶
- [x] 時間：10/6 14:00-17:00  (時間已經跟青平台訂下   )
- [x] KKTIX
- [ ] 攜帶貼紙
- [ ] 場地：TBD
    - [ ] 茶水
    - [ ] 麥克風+插座+網路
    - [ ] 投影機
    - [ ] 延長線
    - [ ] 食物
    - [ ] 垃圾
    - [ ] Talk
    - [ ] wifi 不夠力
- [ ] 誰會來呢？ bil, mrorz, 文武,
- [ ] 開場使用材料更新：https://docs.google.com/presentation/d/1QCAPtwkxreQ4EUtIWsOgR4c8h4tkRs22Qvv7jBFNrfI/edit#slide=id.g1ffc87ef17_0_23

bil 好想做國慶 XD
我們是假的中國 真的中華民國
可以做 8 logo diff

真的假的中華民國

mrorz
主題是光輝十月嗎 w

lucien
要寫什麼 slogan

bil
就放青天白日滿地紅旗、時間、地點
「愛國闢謠救中國」
「真的假的愛台灣」

orz
用貼在走廊的標語的格式

蹭返校熱度 (?)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b11f6192d010d354699ed9e16cc88231)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fa727d843f962b7f841d1147b67c0d14)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3d2116b10ea26e2b67143e0d7cc90ce8)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_174501d00c3035347b0ecec3b0a4e10f)



## 9/13 Oslo Freedom Forum 擺攤
> 準備什麼帶去 demo?

- 把 oslo 謠言印成 A3 （中/英）
- 筆電 + 充電器

:::warning
- [x] 把 [oslo 謠言](https://cofacts.g0v.tw/article/255l6zk2l9qsx
)做成 A3 圖檔
- [ ] 去 7-11 印出圖檔
- [x] 紙膠帶 or 黏土
- [x] 筆電 + 充電器 - youtube 連播 + 網頁
- [ ] iPad + 充電器
- [x] 延長線
- [ ] 名片
:::


## 9/12 NDI workshop

Added to calendar with details.

## [update] 9/7 黑客松

:::success
拿到的名片都已寄信
:::

文武
參與者想要追來源
透過回報時間序來找 pattern
或許有固定路線

但 Cofacts 沒有這樣的東西提供

bil
OCF 有 demo ptt 上站時間
但是這種 pattern
例如說公關公司，其實可以分配好混淆

文武
像是大家都知道要抓 IP 但就是有人不知道
然後就可以抓

參與者有提一個不太可行的需求
想問能不能幫忙發菸害的訊息

bil
沒辦法，他身份的關係所以會是 propaganda
我們跟 LINE 的合約不能幫他這樣推
但歡迎個人來闢謠

文武
有解釋說我們推播最多是做到 popular 謠言，沒辦法幫特別 topic 推

未來可能也會有人來問能不能幫推

也有人問訊息是不是來自中國
感覺大家想問的都很像 

還有鄰居推薦斷詞工具：卓騰語言中文斷詞
可以免費試用
Api https://api.droidtown.co/document/

只有邊緣人在闢謠，闢了多則謠言（三代表很多）
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a061a05ad40a8cd55f1aaee4b4d81043)


希望可以用 google analytics 回報數來做排序
也許有人傳進來，只有一個人

mrorz
1. ReplyRequest 變簡單 --> 下面的討論項目
2. 回應過後仍然可以在文章頁面求回應：https://github.com/cofacts/rumors-site/issues/13 --> good first issue!

文武
參與者自己覺得，最近一直在罰散播謠言的人，這不是很好
畢竟情節沒有到很嚴重，覺得沒有必要

## [update] 9/9, 9/10 NDI 拜訪
> NDI滿關心fb bot的狀況，例如是在comment tag cofacts啟動bot或是可以直接對messenger bot講話

## Dev Items

### LINE bot

- 送出新訊息時問來源：https://github.com/cofacts/rumors-line-bot/pull/135
- 放寬 LINE bot 理由字數限制：https://github.com/cofacts/rumors-line-bot/pull/142
  - Ref：「mrorz UI 設計是還是希望他寫 40 字，只是不會擋 15 字以下」 from https://g0v.hackmd.io/@GuJ5fZ3uR-O09mlTi1w2UQ/rk3KFOUo4?type=view#%E7%90%86%E7%94%B1%E6%AA%A2%E8%A8%8E
- 選文章、選回應 wording update
  - Discussion: https://g0v.hackmd.io/@GuJ5fZ3uR-O09mlTi1w2UQ/rJUCYp2SB#LINE-bot-%E4%B8%8D%E5%A5%BD%E7%94%A8---%E6%B5%81%E7%A8%8B-or-Wording-%E6%AA%A2%E8%A8%8E
  - Github:
    - https://github.com/cofacts/rumors-line-bot/issues/141
    - https://github.com/cofacts/rumors-line-bot/issues/140
  - bil: 列出有幫助沒幫助很好，但是會影響選擇
  - mrorz: 原本就有列出，而且放在最上面
- 針對第 2~N 名回報者，chatbot 可以先送 reply request 再提供理由，加速 reply request 從 1 -> 2 的狀況
  - issue: https://github.com/cofacts/rumors-api/issues/100
  - 其實送出文章流程裡，也可以在使用者按下「送進資料庫」的時候就等同拿到公開的 user consent、去背後 submit article，但 bot 這裏 button 是觸發 LIFF URL，要按按鈕的同時觸發送文章，有一些技術難度要克服，所以先處理「沒回應過的現有文章」。

### API

- 提供「`CreateOrUpdateReplyRequest`」  
  - https://github.com/cofacts/rumors-api/issues/100
- API 藏起「查證價值低」的文章：https://github.com/cofacts/rumors-api/issues/127
  - Discussion:
    - 20190501 https://g0v.hackmd.io/@GuJ5fZ3uR-O09mlTi1w2UQ/rk3KFOUo4?type=view#%E7%90%86%E7%94%B1%E6%AA%A2%E8%A8%8E
    - 20190424 https://g0v.hackmd.io/@GuJ5fZ3uR-O09mlTi1w2UQ/rkEn4TtqE?type=view#%E7%90%86%E7%94%B1%E6%AA%A2%E8%A8%8E
    - 20190417 https://g0v.hackmd.io/@MODl5abnQpKy6ifB4DPGcQ/rJB1nENcN?type=view#%E7%90%86%E7%94%B1%E6%AA%A2%E8%A8%8E
  - 邏輯：
    - By default, show only ReplyRequest count > 1 or sum(ReplyRequest reason length) >= 40
    - Show all only under a certain flag in `ListArticle`
  - 實作方式：
    - 在 mutate 到 ReplyRequest 的 API 手動更新 article 的某個 flag
      - Related code: [CreateReplyRequest](https://github.com/cofacts/rumors-api/blob/master/src/graphql/mutations/CreateReplyRequest.js)
      - 可以跟這個 https://github.com/cofacts/rumors-api/issues/100 一起實作
    - ingest node?

### Rumors-site 升級 next9

https://github.com/cofacts/rumors-site/compare/next9

Progress

1. [x] Article list --> PR to dev
2. [ ] Article page
3. [ ] Reply list
4. [ ] reply page


### Facebook chatbot
> by 桓

> Last discussion: https://g0v.hackmd.io/@GuJ5fZ3uR-O09mlTi1w2UQ/rJUCYp2SB#Facebook-chatbot

> Github issue: https://github.com/cofacts/rumors-fb-bot/issues/4
> 
文武
臺灣吧的做法參考 [可以去玩玩](https://m.me/348320745336110?ref=ObN4rRZzF)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_360b294c548e6d2020f28b30f3874626)


#### 公告 FB bot 上線文案
:::info
粉絲頁、社團、LINE 主頁、LINE bot 公告
:::



### 主機轉移

> 我突然想到，既然現在我們轉移主機卡住，是資料庫的問題
> 而我們想整碗轉去 GCP
> 
> 那換成 GCP hosted elasticsearch 如何？
https://www.elastic.co/products/elasticsearch/service
>
> 先把資料庫轉過去 (有downtime)
舊機與新機都同時連到同一個 elasticsearch
然後再換網域名

orz
另一種做法是，cofacts.org 上的 elasticsearch 先暫時對外
讓舊 production 可以連接到新的 elasticsearch


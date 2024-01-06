---
tags: cofacts, meeting note
---

20190918 會議記錄
=====
orz.文武,bil
> 上次開會紀錄：https://g0v.hackmd.io/3sK-smdoQBW6Vhw3oQCW4w?both
> 

## 10/6 (日) 小聚

- [x] 主題：國慶
    - slogan：
        - 小心！匪謠就在你身邊
        - 回應謠言人人有責
- [x] 時間：10/6 14:00-17:00  (時間已經跟青平台訂下)
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
    - [x] wifi 不夠力 -> 已經買了 [Netgear Nighthawk M1](https://shopee.tw/%E6%BE%B3%E6%B4%B2%E7%89%88-Netgear-M1-4CA-4G-%E8%A1%8C%E5%8B%95Wifi-%E7%B6%B2%E5%8D%A1%E8%B7%AF%E7%94%B1%E5%99%A8-790s-810s-e5788-%E8%8F%AF%E7%82%BA-b525-i.5320736.314685253) 會帶
- [ ] 誰會來呢？ bil, mrorz, 文武
- [ ] 開場使用材料更新：https://docs.google.com/presentation/d/1QCAPtwkxreQ4EUtIWsOgR4c8h4tkRs22Qvv7jBFNrfI/edit#slide=id.g1ffc87ef17_0_23
- [ ] 加slido
    - 連結寫白板上
- 改[instant文案](https://github.com/cofacts/rumors-site/blob/master/pages/instant.js#L9-L87)
    - 21~44 中間加一個（3X）
        - 24個英文字母
        - 30而立
        - 37個注音符號
        - 38婦女節
        - 40不惑
        - 50知天命
        - 60耳順，在非洲每過60秒，就過了1分鐘
        - 70隨心所欲而不踰矩
    - 104 查號台
    - 衛福部 113 保護專線
    - 112 緊急救援專線
    - 125 普通重型機車
    - 128 2的7次方
    - 12*12=144=fib(12)
    - 
    - ~~133 最低時薪~~ 刪掉
    - ~~mini158~~ 刪掉
    - ~~說好不提261~~ 刪掉

bil:
2pm 來的人就定食物 2:10
之後來的就沒有

## Logo 標準字（中文）選擇

### 20190819

GGM: 我覺得這個的粗細適中，另外兩個在白色的背景看起來有點胖

文武：黑底選 8/19，白底 8/19 看起來太細

### A

Orz: 粗細與 logo 一致，看起來比較勻稱
剛黑有社運感是比較俐落，但個人比較喜歡圓圓的樣子，之後 UI 也可以走親民風格

過去[割闌尾計畫](https://www.flyingv.cc/projects/3080)就是走這個風格，但這個計畫本身就是比較往前衝的風格，Cofacts 希望圓滑一點

文武：白底選 A，黑底 A 看起來太粗

lucien:
線條感覺比 glyph 粗很多

### B

bil:
覺得「的」右下角的直角很萌

## Dev Items

### 針對第 2~N 名回報者，chatbot 可以先送 reply request 再提供理由
加速 reply request 從 1 -> 2 的狀況
  - Issue: https://github.com/cofacts/rumors-api/issues/100
  - API PR (`CreateOrUpdateReplyRequest`): https://github.com/cofacts/rumors-api/pull/131
  - LINE bot PR: https://github.com/cofacts/rumors-line-bot/pull/143 (depend on API change)

### 藏起「查證價值低」的文章

- API 藏起「查證價值低」的文章：https://github.com/cofacts/rumors-api/issues/127
  - Discussion:
    - 20190501 https://g0v.hackmd.io/@GuJ5fZ3uR-O09mlTi1w2UQ/rk3KFOUo4?type=view#%E7%90%86%E7%94%B1%E6%AA%A2%E8%A8%8E
    - 20190424 https://g0v.hackmd.io/@GuJ5fZ3uR-O09mlTi1w2UQ/rkEn4TtqE?type=view#%E7%90%86%E7%94%B1%E6%AA%A2%E8%A8%8E
    - 20190417 https://g0v.hackmd.io/@MODl5abnQpKy6ifB4DPGcQ/rJB1nENcN?type=view#%E7%90%86%E7%94%B1%E6%AA%A2%E8%A8%8E
  - Orz: 先讓「放寬標準」+「加速 reply request」上線，說不定現在的「」


### Rumors-site 升級 next9

https://github.com/cofacts/rumors-site/compare/next9

#### Progress

1. [x] Article list --> PR to dev
2. [ ] Article page （見 API 更新）
3. [ ] Reply list
4. [ ] reply page

#### 相對應 API 更新

https://github.com/cofacts/rumors-api/pull/132

- `ownVote` field for UI: 當下使用者是否已經 upvote / downvote `ReplyRequest` or `ArticleReply`

- `CreateOrUpdateReplyRequest` 回傳 article ([PR#131](https://github.com/cofacts/rumors-api/pull/131)), `CreateOrUpdateReplyRequestFeedback` 回傳 `ReplyRequest`,
`CreateOrUpdateArticleReplyFeedback` 回傳 `ArticleReply`


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

ggm
好像只有跟 k8s 一起一鍵部署
不如把原本的對外
同步完關掉

既然都要對外，那就在舊的 production 對外然後開 cluster mode

之前會失敗是因為過 tunnel

:::success
下一次來做
:::

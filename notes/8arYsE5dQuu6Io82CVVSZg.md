---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240715 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO hub 出席：bil, mrorz
- 線上出席：nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## CCPRIP

### [Op] 垃圾訊息反制
> https://g0v.hackmd.io/uefTz4yURImgtem--itaMw?both#Op-%E5%9E%83%E5%9C%BE%E8%A8%8A%E6%81%AF%E5%8F%8D%E5%88%B6
> Design doc: https://g0v.hackmd.io/um7DyY_ESbu2LL78kLw3pg?both

1. Schema fix: https://github.com/cofacts/rumors-db/pull/70
    - 補漏掉的欄位
    - 所有 table 都關閉 [dynamic field mapping](https://www.elastic.co/guide/en/elasticsearch/reference/current/dynamic-field-mapping.html) 確保不會有 mapping 外的欄位
2. API update [WIP] https://github.com/cofacts/rumors-api/pull/342
    - 確保 API 不會寫入 mapping 外的欄位
    - test 要 pass
3. API script with type https://github.com/cofacts/rumors-api/pull/338
    - Pending on #2 

## 小聚籌備

- [x] 日期：08/03（六）
- [ ] 食物：
- [x] 場地：NPO Hub Foundry（大的那間）- 借好了
- [x] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Slido 暖身
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：
  - 推播日：07/24 推播
  - 推播日之前： 
  - 目標：雙北
- [x] KKTIX: https://cofacts.kktix.cc/events/cofactseditor43
- [x] 誰會來呢：bil, mrorz, nonumpa
- [ ] 記得帶：貼紙、環保杯
- [ ] LINE 文案：「川普陣營曾經要求增加維安保護川普的人員卻被拒絕」、「杀手是極左成员,日前在油管上发视频说正义即将到来」網路上可疑訊息太多了，而 Cofacts 要成為你抵禦假資訊的小幫手，08/03（六）14:00-17:00 Cofacts 第43次查核志工培訓工作坊期待你一起來參與協作＝Ｄ
地址：台北市中正區重慶南路三段2號二樓（最近的捷運站是中正紀念堂站2號出口）
- [ ] VOOM 發文

:::success
bil: LINE 文案換川普
:::


## 大松籌備
中研院
- 我們在旁邊修issue 跟查核假資訊 by bil
- 提案：bil
- 報告：by 貢獻者 or orz
- 誰會去：bil, mrorz

Good first issue
- LINE bot 公開訊息 consent https://github.com/cofacts/rumors-line-bot/issues/394
- Website enhancements https://github.com/cofacts/rumors-site/issues?q=is%3Aopen+is%3Aissue+label%3A%22good+first+issue%22

## Talks
- 反詐
  - Honeypot 機制與裡面的東西（二次詐騙）--> 結構化資料，未驗證
  - 與詐騙集團的對話
  - 其他樣態
    - 偽裝來二次詐騙（CIB：我真的有拿到錢）
    - 改名字為 165、查證、反詐之類
    - 改逐字稿、補充、回應
    - 詐騙業者要求下架未果，跑來 DDoS
- 大松
- TWIGF
  - 大松時再 sync


## COSCUP
開源設計工作坊
地點 RB-101
時間：08/04 10am-4pm

Designers in Tech- Open Source Design Workshop
https://blog.coscup.org/2024/06/designers-in-tech-open-source-design.html
We'd like to focus on two aspects of CoFacts in the contribution event:
1. How can users looking at long texts and references get a clear picture of the thread and specifically differentiate two references
https://github.com/cofacts/rumors-site/issues/360
2. How to improve analyics views of CoFacts for understanding and comprehension of what the 'viewership' of resaders are?
https://github.com/cofacts/rumors-site/issues/332
https://g0v.hackmd.io/yEp9JJtHSyK18bxCQV4dUg#Analytics"

提供了這個 Figma https://www.figma.com/design/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=0-1&t=mkxL4v7iQWlbwvPS-0



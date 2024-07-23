---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240722 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO Hub 出席：bil, mrorz
- 線上出席：nonumpa, T
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

https://165.g0v.tw

### :rocket: Staging

#### :globe_with_meridians: Site

* Enhance display of many link previews by @jiru in https://github.com/cofacts/rumors-site/pull/571
* Adding header by @mojoee in https://github.com/cofacts/rumors-site/pull/572

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] Article detail
  - [x] Can list multiple hyperlinks correctly

登入自有帳號後檢測：
- [x] Article detail
  - [x] Can show reply requests with author and correct time

##### ⛔️ Release Blockers

N/A

##### 未竟項目
- 一些 visual quirk (例如 reply request 在 mobile 頭像應該要在上方而非左邊、preview 顏色跟外面一樣等) 之後再修就好

## Cofacts API Schema Bug

graphql-playground 有一段時間沒人維護了，大家建議換到 graphiql
https://github.com/graphql/graphql-playground/issues/1366

- 直接使用
https://github.com/graphql/graphiql/blob/main/packages/graphiql/README.md
- 使用 apollo-server 內建
稍微試了一下，好像 apollo-server-koa 要升級到 v3 才可以用，目前的版本是 [v2.11.0](https://github.com/cofacts/rumors-api/blob/8a1bffbef9dbd78e1de76232dd897cc85fa8f2a2/package.json#L34)
但是 apollo-server v4 把 apollo-server-koa [移除](https://github.com/apollographql/apollo-server/blob/79dacd01114c1596a2646a3458b984944fedb109/packages/server/CHANGELOG.md#removed-web-framework-integrations)了，如果要升級可能就直接升到 apollo-server v4
    - 但 dependency 滿多，graphql 要升、啟動 script 要改 [name=nonumpa]

:::success
nonumpa try graphiql
:::

## 大松檢討

> https://g0v.hackmd.io/@cofacts/meetings/%2Froo-89pnR6iouhm-xgLL3A

## Open165

> 專案共筆：
> https://g0v.hackmd.io/xl7YbrcTRECluGKK_HGo6Q

跟 Cofacts 的關係
- 「被 OO 騙怎麼辦」的文案可以參考 Cofacts 上反應比較好的回應
- 站名與 URL 的獨立頁面：可以作為 LLM 自動輸出的資料來源
- 就算 165 裡沒有還是可以放類似名字的搜尋結果

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
- [x] 投放目標：
  - 推播日：07/24 推播
  - 推播日之前： 
  - 目標：雙北
- [x] KKTIX: https://cofacts.kktix.cc/events/cofactseditor43
- [x] 誰會來呢：bil, mrorz, nonumpa
- [ ] 記得帶：貼紙、環保杯
- [x] LINE 文案：你有收到這些訊息嗎：「川普陣營曾經要求增加維安保護川普的人員卻被拒絕」、「杀手是極左成员,日前在油管上发视频说正义即将到来」，這些訊息的回應都是Cofacts 志工一筆一筆整理的。網路上可疑訊息太多，而 Cofacts 要成為你抵禦假資訊的小幫手，08/03（六）14:00-17:00 Cofacts 第43次查核志工培訓工作坊期待你一起來參與協作＝Ｄ
地址：台北市中正區重慶南路三段2號二樓（最近的捷運站是中正紀念堂站2號出口）
- [ ] VOOM 發文


## COSCUP
開源設計工作坊
地點 RB-101
時間：08/04 10am-4pm

有沒有什麼希望設計的頁面或是東西呢？工作坊想要成果是可以直接有用的
Designers in Tech- Open Source Design Workshop
https://blog.coscup.org/2024/06/designers-in-tech-open-source-design.html
We'd like to focus on two aspects of CoFacts in the contribution event:
1. How can users looking at long texts and references get a clear picture of the thread and specifically differentiate two references
https://github.com/cofacts/rumors-site/issues/360
2. How to improve analyics views of CoFacts for understanding and comprehension of what the 'viewership' of resaders are?
https://github.com/cofacts/rumors-site/issues/332
https://g0v.hackmd.io/yEp9JJtHSyK18bxCQV4dUg#Analytics"

提供了這個 Figma https://www.figma.com/design/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=0-1&t=mkxL4v7iQWlbwvPS-0

https://miro.com/app/board/uXjVK7S_xCQ=/
寫了個persona

:::success
告知說 Cofacts 有個相關網站需要設計
反詐騙資訊站，給快被騙或已經被騙的人有幫助的資訊
未來可以用在 Cofacts 裡回應用
:::

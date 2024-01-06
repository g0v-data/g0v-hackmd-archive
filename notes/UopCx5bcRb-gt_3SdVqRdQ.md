---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220706 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, nonumpa, mrorz, cai
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API

> https://github.com/cofacts/rumors-api/releases/tag/release%2F20220701

- `MEDIA_ARTICLE_SUPPORT` env
- Media manager & `CreateMediaArticle`
- `articleReply` filter in articles
- record feedback target ([migration result](https://github.com/cofacts/rumors-api/pull/285#issuecomment-1171485812))
    - Now can see feedback of an author in [community-builder](https://cofacts.github.io/community-builder/#/editorworks?type=1&day=7&articleReplyUserId=AVqVwjqQyrDaTqlmmp_a)

#### :robot_face: rumors-line-bot

> https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20220701

New (correct) feedback flow

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_42315e729516101448fcde184ca8e13d.png)

Signigicantly more user giving feedback (?) after release
- Dashboard counts `Feedback-Vote` event
- It's submitted whenever
    - user opens feedback LIFF
    - user switches upvote / downvote in LIFF
    - user clicks close or submit in LIFF

### :eye: Under review
- https://github.com/cofacts/media-manager/pull/4
  - integration test implementing on [rumors-api](https://github.com/cofacts/rumors-api/pull/288)
  - Test work on rumors-api --> merge [media-manager#4](https://github.com/cofacts/media-manager/pull/4) --> publish 0.1.0 --> [rumors-api#288](https://github.com/cofacts/rumors-api/pull/288) review
- https://github.com/cofacts/rumors-line-bot/pull/311

## Image support
> https://github.com/orgs/cofacts/projects/9

- 過圖片的 Wording / 流程 [name=nonumpa]
- Media Manager wiki & README
    - 分 usage 跟 development
    - https://github.com/cofacts/media-manager/issues/5

## Trend and contribution
> https://github.com/orgs/cofacts/projects/10

- Feedback list for fact checkers
- spreadsheets

## 小聚籌備

- [revamp 第二階段介紹](https://g0v.hackmd.i]o/_HXxDu6OQPaK08WFwOshtg#%E5%B0%8F%E8%81%9A%E6%AA%A2%E8%A8%8E)
- [不用 spreadsheet，直接用主題分](https://g0v.hackmd.io/_HXxDu6OQPaK08WFwOshtg#%E5%B0%8F%E8%81%9A%E6%AA%A2%E8%A8%8E)
    - 展示 Google analytics 目前大家在哪一頁
    - [User-ID view](https://analytics.google.com/analytics/web/#/realtime/rt-content/a98468513w144848466p149494611/)
    - User-id is broken...... ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c485ac9310ae02d4265342c8c8f56fb0.png)

:::warning
Fix user id view
:::

----

- [x] 時間:
    - [7/24 (日) 13:30-17:30](https://g0v-slack-archive.g0v.ronny.tw/index/channel/C0385B90D/2022-06#ts-1656553121.3964)
    - 四樓廚房
    - keyholder Ronny
- [ ] 主題：
- [x] 場地：
    - [NPO Hub 四樓廚房](https://g0v.hackmd.io/@jothon/NPOHub-rules)
- [ ] 食物 
- [x] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Keyholder 介紹場地
        - 2:20 - 2:40 介紹 mission 1 -幫其他查核者評審回應
        - 2:40 - 3:00 進行評價 (20則)
        - 3:00 - 3:30 休息、自我介紹、交流 
        - 3:30 - 3:50 介紹 mission 2 - 寫回應
        - 3:50 - 4:30 進行回應（1則）
        - 4:30 - 5:00 介紹分類、RSS、合照
- [x] 投放目標：新北市 only
    - 介紹青年局志工活動
- [x] KKTIX：https://cofacts.kktix.cc/events/cofactseditor31
- [ ] 誰會來呢：mrorz, bil, nonumpa
- [ ] 無法來：
- [ ] LINE 文案
台灣疫情每日本土確診人數兩萬人，小孩子到底可不可以施打疫苗？快篩買不到、確診怎麼照顧？
7月24日（日）14:00-17:00 在ＮＰＯ ＨＵＢ 4樓廚房，（最近的捷運站是中正紀念堂站）鍵盤志工活動，完全免費，歡迎從未參加過的您，幫助不擅長查證訊息的親戚朋友。
（請自行攜帶筆記型電腦與水杯）
請先報名：KKtix

## 「編輯」一詞

> 上週討論 https://g0v.hackmd.io/UP6DRljfTciCSv_mUtB7wQ?view#%E3%80%8C%E7%B7%A8%E8%BC%AF%E3%80%8D%E4%B8%80%E8%A9%9E

- 沿用「編輯小聚」，編輯作為動詞 [name=bil]
- 協作者 collaborator、「查核協作者 / fact-checker」 [name=bil]

## Moderation

> 同上週 https://g0v.hackmd.io/UP6DRljfTciCSv_mUtB7wQ#Moderation

## 搜尋圖片 wording 

> 🔍There are some messages that looks similar to {inputSummary} you have sent to me.
> 🔍資料庫裡有幾篇訊息，跟您傳給我的「{ inputSummary }」有些接近。

🔍There are some messages that looks similar to the one you have sent to me.
🔍資料庫裡有幾則訊息，可能跟您傳給我的有些接近

> Internet rumors are often mutated and shared.
  Please choose the version that looks the most similar👇
> 不實訊息常常會被人修改重發。
> 請選擇比較接近的版本👇

> ![](https://i.imgur.com/hfZBEGg.png)
> Header「第 1 張：87% 像」「Image 1: 87% similar」[name=mrorz]
> None of these messages matches mine :(
> 找不到我想查的訊息 QQ
None of these images matches mine :(
找不到我想查的訊息

> I choose 「xxx」
> 我要選「xxx」
I choose image 1
我要選第 1 張


### 無回應
> This message has already published on Cofacts, and will soon be fact-checked by volunteers.
> Don’t trust the message just yet!
> 此訊息已經被收錄至 Cofacts 有待好心人來查證。
> 請先不要相信這個訊息唷！

此訊息還沒有好心人回應
請先不要相信這個訊息唷！

<!-- 
> 接下來您可以...
> 提供更多情報／遠親不如近鄰，問問親友
 -->

### 有回應

-> (舊流程) 顯示回應


### 搜尋不到，送進資料庫

> 對訊息保持懷疑很好唷！
> 不過我目前還不認得「xxx訊息．．．」。可以請你幫我一個忙嗎？

對訊息保持懷疑很好唷！
不過我目前還不認得這張圖片，可以請你幫我一個忙嗎？

<!-- 
> 成為全球首位回報此訊息的人
 -->

### State reuse?
- text 與 image 會在外面就拆開，還不會進到 event handler [name=nonumpa]
- Postback handling 可能往外面拉(現在似乎在 handleText 後面) [name=nonumpa]
- event postback value 被塞進 event.input 可能也要改？[name=mrorz]
  - 看怎樣比較好改 [name=mrorz]


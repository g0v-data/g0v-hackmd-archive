---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220713 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz, nonumpa
- 線上出席：4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :electric_plug: API
- Image variant processing https://github.com/cofacts/rumors-api/pull/288
    - Media manager v0.2.0 variant support

#### :robot_face: rumors-line-bot

- Image proxy https://github.com/cofacts/rumors-line-bot/pull/311

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 傳圖片不會壞
- [x] collected images 會有圖進 google drive

##### ⛔️ Release Blockers
##### 未竟項目

#### :globe_with_meridians: Site

- Image variant & signed URLs https://github.com/cofacts/rumors-site/pull/493
- Fix filter in profile page https://github.com/cofacts/rumors-site/pull/494
- Fix Google analytics user ID view https://github.com/cofacts/rumors-site/pull/495

##### Testing checklist
http://dev.cofacts.tw/

項目同 [0518 時測的](https://g0v.hackmd.io/_HXxDu6OQPaK08WFwOshtg?both#-Site1)。

**未登入**下檢測：

- [x] Article list
  - [x] Can go to article page
- [x] Replies list
  - [x] Can go to article page
- [x] Hoax for you
  - [x] Can go to article page
- [x] Article detail
  - [x] Can see similar messages - no similar images yet
- [ ] Search
  - [ ] Can list searched articles 沒有圖的可以
  - [x] Can list searched replies

登入自有帳號後檢測：
- [x] Article detail
  - [x] Can submit, upvote, downvote reply request
  - [x] Can submit, remove own reply
  - [x] Can upvote, downvote other's article reply


##### ⛔️ Release Blockers

##### 未竟項目


### :eye: Under review

## Image support
> https://github.com/orgs/cofacts/projects/9

- Image variant on API & website; test article with images on staging now
    - cache 是後來加的所以現在 staging 上的都沒 cache header
- Chatbot file proxy on staging now
- Chatbot image search is under development [name=nonumpa]
    - Image 會過期：staging 上的圖還沒有設 metadata `Cache-Control: public, max-age=31536000, immutable`
        - 手動設了幾張試試看: https://storage.cloud.google.com/cofacts-media-collection/image/vDph4g/__-AD6SDgAebG8cbwifBB-Dj0yPjo8ETgAOAA4P_8_8/original
    - 圖片解析度問題 [name=nonumpa]
        - 不要放大；(shrink-to-)fit 在高度 240px 的地方
        - background color: pick from https://www.figma.com/file/Xr80rEWwCrNks1uFIrGCG4/Cofacts-Colors?node-id=22%3A34
    - check if score is 1~2
        - 1: comes from `match_all` query
        - 0~1: MediaManager similarity

## Trend and contribution
> https://github.com/orgs/cofacts/projects/10

- No progress this week


## Moderation

### 已處理
#### 政治立場不同者的檢舉

> https://g0v.hackmd.io/Gf45qq-9T9GLMkSrsfXG1A#針對-Lopi-的檢舉

回應：https://docs.google.com/spreadsheets/d/1q-iMJ9tZtoyHNfwInAb3z-eIg2x4-w1yp7XGTiaLB-w/edit?resourcekey#gid=1583640334&range=P218


- 「含有個人意見」其實不是「正確」 [name=mrorz]
- 多元性 [name=bil]
- 審查 -> 會砍的人的樣態跟他檢舉的並不一樣 [name=mrorz]
    - 除了詐騙、惡意廣告等狀況之外，不會因為政治立場或懷疑某人的意圖而直接下架他人
- 可以寫一個新回應
    - 我們有注意到一位查核協作者 NF 有回應，這就符合我們多元並陳的精神
- DTL, IORG 都有在密切關注此專案上的內容，但他們作為研究者或許有其他考量，我們無法要求他們積極回應。
- 禮拜三晚上來聊天？

#### 疫苗陰謀論遭檢舉
> https://g0v.hackmd.io/UP6DRljfTciCSv_mUtB7wQ#%E7%96%AB%E8%8B%97%E9%99%B0%E8%AC%80%E8%AB%96%E9%81%AD%E6%AA%A2%E8%88%89

回應：https://docs.google.com/spreadsheets/d/1q-iMJ9tZtoyHNfwInAb3z-eIg2x4-w1yp7XGTiaLB-w/edit?resourcekey#gid=1583640334&range=P236

### HCR 腦控
- 決議：至 FB group 發文討論 https://g0v.hackmd.io/Gf45qq-9T9GLMkSrsfXG1A#ＨＣＲ-腦控
- 尚未貼文

### 某些詐騙相關

- Hopoo
- stock broker views --> 除了廣告之外沒有其他互動，是為廣告帳號
- Naomi -->
    - 讓人覺得有個正版，應該鎖 [name=bil]
    - 但他讓其他人知道 hopoo.plus 這個也是詐騙，也不像其他二次詐騙會導向到另一個 LINE，像是群組裡的人叫大家不要加入 [name=mrorz]
    - noop，再觀察
- 韩巧莲 --> block


## 小聚籌備

新投影片：https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit#slide=id.gc4cef832ac_0_124
- Go through 預定的 edit [name=mrorz]
- 內容農場辨別
- 個人意見要好好講解
    - 分別事實與意見

---

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

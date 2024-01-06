---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220504 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis: bil, mrorz
- 線上出席：4000, nonumpa, cai
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: rumors-line-bot

- https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20220502
    - 需要貼文說明更新

:::info
TODO
- 送出流程 funnel --> https://datastudio.google.com/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/Cy2P
:::


### :rocket: Staging

#### :electric_plug: API
- [Multimedia support phase 0 #273](https://github.com/cofacts/rumors-api/pull/273)
- [Fix build by upgrade Node.JS #278](https://github.com/cofacts/rumors-api/pull/278)
- [Use buffer instead of cloned stream #279](https://github.com/cofacts/rumors-api/pull/279)

Note when migrating: https://github.com/cofacts/rumors-api/pull/273#issuecomment-1111858300

#### :globe_with_meridians: Site

- https://github.com/cofacts/rumors-site/pull/484

##### Testing checklist

僅升版沒動 feature，所以僅挑選部分 CRUD 做測試
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] Article list
  - [x] Filter works
  - [x] Sorting works
  - [x] Can go to article page
- [x] Article detail
  - [x] Can see similar messages
- [x] Search
  - [x] Can use global search to perform search

登入自有帳號後檢測：
- [x] Article detail
  - [x] Can submit, upvote, downvote reply request
  - [x] Can submit, remove own reply
  - [x] Can upvote, downvote other's article reply
  - [x] Can add, remove, upvote, downvote category
- [x] Can logout

##### ⛔️ Release Blockers

##### 未竟項目

- Downvote article category 時偶爾會有： ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0189a8771d971503119ac6075c3c55ab.png)
  - https://dev.cofacts.tw/article/2wknj1pk2pk58
  - 針對醫藥分類按「downvote」
  - 最近常遇到，有時候重開就會好 [name=bil]


:::info
可 release，開票追蹤 downvote 時 unexpected error issue


:::

## Cofacts Media Manager

- Design doc: [Cofacts media manager implementation](/C8dW2cFiR1-N5Z0wcOefuA?both)
- Research article: [Cofacts multimedia support design doc](/aJqHn8f5QGuBDLSMH_EinA), [Cofacts research on image-hash](/LHhF_VQ1RdS12C0k0ESQ_Q)

## 其他 Multimedia 更新

https://github.com/orgs/cofacts/projects/9

- Manually onboard 10 images: done
    ```graphql
    {
      ListArticles(filter: {articleTypes: [IMAGE]}) {
        totalCount
        edges {
          node {
            id
            attachmentHash
            attachmentUrl
          }
        }
      }
    }
    ```

## 流量與貢獻資訊開發

Previous list: https://g0v.hackmd.io/fOBTLOQkSI-z-CRFSI2Fgg#%E6%B5%81%E9%87%8F%E8%88%87%E8%B2%A2%E7%8D%BB%E8%B3%87%E8%A8%8A%E9%96%8B%E7%99%BC

Need project tracking?
- Yes [name=bil]
- "Trend and Contribution"

:::info
- Create project
- Create 4 tickets across different repositories

--> https://github.com/orgs/cofacts/projects/10/views/1
:::

## 洗版處理

https://github.com/cofacts/takedowns/pull/63/files?short_path=90d7e35#diff-90d7e3533a6ba0ae0a48b19bcfded5c6af275f52d087b14edc60c0b6810f8254

- 像是張爸 [name=mrorz]
- 他現在篇數少，我比較懷疑是不會操作 [name=cai]
- Community builder https://cofacts.github.io/community-builder/#/editorworks
- NF

## LINE bot 更新說明

- 標題：「簡化送出流程」？「送出流程更新」？
  - 機器人變懂事啦 [name=4000]
- 文字+截圖？
- 主題
    - 確認是否為轉傳訊息
    - 詢問意願後隨即送出
    - 鼓勵補充資訊

## 小聚籌備

[前一週討論線上版本](https://g0v.hackmd.io/fOBTLOQkSI-z-CRFSI2Fgg#%E5%B0%8F%E8%81%9A%E7%B1%8C%E5%82%99)

:::success
五月上旬來改投影片
1. 現有的按讚
1. mission 2 改留補充資訊
1. 幫 COVID 訊息標 category
:::

- [x] 時間:
    - 5/15 (日) keyholder Ronny
- [ ] 主題：
    - 疫情爆發群聚闢謠 (?)
    - 疫起來闢謠 <--- 公部門覺得讚的名字
- [ ] 場地：
    - [NPO Hub 2F 影響力工場（30人）](https://g0v.hackmd.io/@jothon/NPOHub-rules)
- [ ] 食物 
    - 疫情期間不鼓勵
- [ ] 時間：
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
- [ ] 投放目標：北北基桃
- [ ] 事前產生 spreadsheet 25 人分工
- [ ] KKTIX：https://cofacts.kktix.cc/events/cofacteditor30
- [ ] 誰會來呢：mrorz, bil, nonumpa
- [ ] 無法來：
- [ ] 做圖：用 Figma 做 [name=mrorz]
- [ ] LINE 文案
台灣疫情每日本土確診人數兩萬人，小孩子到底可不可以施打疫苗？快篩買不到、確診怎麼照顧？
5月15日（日）14:00-17:00 在ＮＰＯ ＨＵＢ 2樓影響力工場，（最近的捷運站是中正紀念堂站）鍵盤志工活動，完全免費，歡迎從未參加過的您，幫助不擅長查證訊息的親戚朋友。
（請自行攜帶筆記型電腦與水杯）
請先報名：KKtix

## 新北青年局合作

- 促進公共參與
  - 讓志工開始知道公眾事務的複雜性
  - 第一階段可以先專注在 COVID 相關訊息，也可以支援政策相關資訊
- 署名「Cofacts 真的假的訊息回報機器人與查證協作社群」/「Cofacts 真的假的」
- 需要可以列出時間內的回應
  - 現在的列表即可使用： https://cofacts.tw/user/mrorz?slug=mrorz&start=2022-04-24&end=2022-04-30
    - community builder + excel output?
  - Spreadsheet of user ID 拼出 URL
- 時數認證
  - 篇數、覺得有用數
  - 用到的 reply 數？
- 使用者條款：https://github.com/cofacts/rumors-site/blob/master/LEGAL.md
- 新北訊息
  - https://cofacts.tw/article/sllw5lobnfmp
  - https://cofacts.tw/article/2xv1rilj7je55
  - https://cofacts.tw/article/e9rboiv2a5go
  - https://cofacts.tw/search?type=messages&q=%E6%96%B0%E5%8C%97&start=now-1M%2Fd

---
tags: cofacts, meeting note
---

20191023 會議記錄
=====
orz, 文武, ggm（沒有飲料）

> 上次開會紀錄：https://g0v.hackmd.io/VE7wEXXSTQ245jqjwMu1_g
> 

## 活動出席/採訪

### 10/21 CALD
> Subject: Invitation to Speak in an International Seminar-Workshop on Disinformation

RR 的禮物在 Workis XD
bil:瓶瓶～～～😘

### ITS Rio
> Subject: CoFacts and ITS Rio :)

採訪共筆：https://docs.google.com/document/d/1bkGBKTYxm7mHIErzKystxM-8PkwBADQoLgxbDELokUk/edit
回應格式：(暱稱) 想說的話

### 泰國 Conference on Social Innovation and Civic Participation

投影片：https://bit.ly/2My0ptb
Slido: https://app.sli.do/event/4l86jelp

不確定會不會有錄影

orz: slido 很讚
不用怕聽不懂發問者的英文

slido google slides chrome extension 也不錯


### 11/30 (六) 國際志工日 青年志工論壇 技能專長服務
subject: 敬邀參與國際志工日系列活動-系列 1. 青年志工論壇

> Track III: 技能專長服務 （13:30 ~ 15:00）
> 討論重點
> 青年如何運用專長進行志願服務，將專長結合受服務者需要規劃服務方案(待講者確定再調整)

鄰鄰姊姊故事日、有時間ㄇ

orz:
前後有願景工程，所以會找上我們
我們有三個選項
- 轉介 Wikimedia Taiwan 更符合「用專長進行志願服務」
- 轉介至 g0v-talks / g0v-jothon
- 轉介假新聞清潔劑
- 我們自己出人

ggm: NPOst 跟我們一起的其他講者好像也可以被推薦
都是廣招志工來完成事情

orz:
那要不要推 readr 2020總統候選人事實查核計畫

:::success
Orz 10/25 前回覆：
目前 cofacts 沒有人可以出席
是否考慮 g0v community、Wikimedia Taiwan、假新聞清潔劑、readr or etc
:::

### 12/6 ~ 11 - Google Trusted News Summit APAC
> The weeklong event is divided into three parts: a one-day product working group (Dec 6), two-day main conference (Dec 7-8) and optional workshops (Dec 9-11).
>
> #### Product Working Group (Dec 6)
> The product working group will allow members of the verification community to speak directly with product teams, share case studies and discuss tools and product features.
>
> #### Main Summit (Dec 7-8)
> The main summit will follow a traditional conference format, featuring:
>
> - Updates from First Draft, IFCN, Google, YouTube and Facebook
> - Lightning talks about fact-checking and verification initiatives in APAC and around the world
> - Panels to discuss challenges and opportunities faced by the verification community
> - Office hours / 1:1 sessions
> - Breakout sessions by country, topic (elections, health, crowdsourcing verification etc.), challenges (tech, standards, etc.), media literacy, researching misinformation, evaluating success
> - Workshops on topics such as online safety and digital security, fact-checking, verification, disseminating fact-checks and tools!
> - Verification CSI: We'll break up into small groups and tackle real-world case studies (alleged voter fraud in Indonesia, the Nancy Pelosi video), discuss best-practices and standards
> - Train-the-trainer Parallel Sessions & Design Sprint (Dec 9-11)
> - For three days following the summit, there will be optional workshops on the following topics:
> 
> #### December 9: Misinformation in Medicine Forum: A  one-day event to build collaboration between journalists, doctors and technologists to combat the misinformation epidemic in health in Asia.
> December 9: Responsible Reporting Workshop: Standards and best practices for creating and disseminating verifications/ fact-checks in multiple mediums (text, photo, video), led by First Draft
> Dec 10-11: Taking Verification to the Next Level: For experienced fact-checkers/ verification experts, led by OSINT expert Eoghan Sweeney
> December 9-11: Media Literacy Bootcamp: A three-day meeting for journalists, community groups and educators focused on building a network of media literacy practioners in Asia-Pacific, evidence-based best practices and measurement.
> We have arranged for a group discount at M Social hotel and will provide transportation between this hotel and the Google office. Once you have confirmed your attendance, a member of our event planning team will reach out to answer any questions you may have about logistics.

:::success
等 Irene 回信

ggm, orz, 文武不行
:::


## LINE bot rewording

依照[上週討論](https://g0v.hackmd.io/VE7wEXXSTQ245jqjwMu1_g#Facebook-bot)，github issue 正在改寫：
https://github.com/cofacts/rumors-line-bot/issues/145

- 按鈕跟 LIFF 結合的問題：可以設定選項按鈕直接接 LIFF，不過這會跟桌機 LINE 衝突

:::success
拔掉 `ASKING_ARTICLE_SOURCE` state
照這個影片：https://drive.google.com/open?id=1QGuPFsNj9DtL65VFUez-Hk8M4YtrQtew


:::


## ~~Facebook bot~~
> discussion with HC

> Last discussion: https://g0v.hackmd.io/@GuJ5fZ3uR-O09mlTi1w2UQ/rJUCYp2SB#Facebook-chatbot

> Github issue: https://github.com/cofacts/rumors-fb-bot/issues/4


:::info
TODO
- Production deployment
- testing app
:::

### ~~公告 FB bot 上線文案~~
:::info
粉絲頁、社團、LINE 主頁、LINE bot 公告
:::

## Rumors-site 升級 next9
1. [x] Article list --> PR to dev
2. [x] Article page （見 API 更新）
3. [ ] Reply list
4. [ ] reply page
5. [ ] RSS feed

## 主機轉移

- ES 對外
- 
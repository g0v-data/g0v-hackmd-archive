---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20200506 會議紀錄
=====

Workis
> 線上開會： https://tico.chat/powercall?room=cofactshack&type=timeFirst
> 上次開會紀錄：https://g0v.hackmd.io/@mrorz/BksBf58KI

## 組織化

### 社群（w/ 全職員工）

例子：
- g0v jothon - 合作專案
  - full-time employee hired by OCF
  - 任何合作案（funding, human resource, ...etc）都要有 OCF 參與
  - 捐款徵信 https://jothon.g0v.tw/transaction/

:::info
Cofacts 業務為維護產品、單一社群的經營與營造，有較單一的目標；與社群行政工作較為不同，因此對外的機會也不同（grant）。

而 Cofacts 在進行 funded project 時，很可能會排擠到 OCF 服務其他國內社群的資源。因此若 Cofacts 本身能有法人、可以自理的話，就不用佔用 OCF 有限的服務社群的資源。
:::

### 公司

- MyGoPen: 識實數據有限公司 https://www.mygopen.com/p/blog-page_58.html / http://company.g0v.ronny.tw/id/83561111
- 沃草: 沃草有限公司 https://watchout.tw/transparency/2014 / http://company.g0v.ronny.tw/id/54648384
- 科斯高科斯高有限公司 http://company.g0v.ronny.tw/id/53216009
- Snopes: Snopes Media Group Inc. (SMG), a California-based S Corporation. https://www.snopes.com/disclosures/
- 蘭姆酒吐司：安民網路多媒體科技股份有限公司 http://company.g0v.ronny.tw/id/24956308
- LINE, Facebook, Google, Twitter, Plurk 等社群網路平台

:::info
專案若有需要，可以選擇「募資」 https://watchout.tw/transparency/2014
:::


### NPO

- 假新聞清潔劑: 協會
- 台灣民主實驗室 https://doublethinklab.org/
- 台灣維基媒體協會 (非營利全國性社會團體) https://zh.wikipedia.org/zh-tw/%E5%8F%B0%E7%81%A3%E7%B6%AD%E5%9F%BA%E5%AA%92%E9%AB%94%E5%8D%94%E6%9C%83

---

- Mafindo (協會 association) https://www.mafindo.or.id/about/
- Meedan (501(c)3 non-profit) https://meedan.com/about
- Politifact (501(c)(3) part of nonprofit Poynter Institute) https://www.politifact.com/who-pays-for-politifact/

:::info
`>= 9` 人理事
`>= 3` 人監事
均有任期限制，一任不得超過 4 年
理事長至多連任一次，理監事得連選連任

一般來說，執行團隊（hired）有
- 秘書長
- 會計

章程、發起人會議 (30 人)、籌配會議、成立大會、年度大會、年度預算表。
可以進行「公益勸募」，須送主管機關備查（地區性=社會局、全國性=衛福部）。
:::

orz
協會的設計與門檻，感覺就是設計給這種社團型式、人很多的團體成為法人用的
好像跟我們不太一樣

bil
我們就新創size

協會還要辦年度募款餐會請大家吃飯然後收捐款
壓力山大

15人（盤點朋友ing 集合啦！闢謠朋友會）

網路上說說協會會凋零，就是只找朋友
協會有點害羞，要跟大家要錢

orz
新創size 但我們不像社會企業能養活自己（至少可以打平）

## 0601 演講

型式：同政大

政大場在超過 60 人時發現會無法編輯
若超過人數，則需要分不同表格

需要 O/X 的 instant

## New idea: Social media toolkit

by mrorz

產出可以貼去 Facebook 編輯群組的文章，手動或自動貼文

- 本週感謝編輯
  - 目前已有
  - Query: `ListAritcle` filter by `repliedAt` 時間區段後，aggregate user name
- 本週 / 本日最多 feedback count 的 reply
  - negative 多不一定代表查證不好、positive 多也不一定跟你想得一樣，唯一確定的是很多人看到了這些回應，希望讓大家一起來檢查（或觀摩）
  - 鼓勵大家對回應按 O 或按 X，按 X 的話可以到討論串討論切磋，或者是回一個新的。
  - Query: `ListAritcle` filter by `repliedAt` 時間區段後，（在程式端）照 feedback count 排列
- 本月最邊緣排行 (?)
  - 讓默默耕耘、不求點閱 (?) 的編輯可以曝光。鼓勵大家對回應按 O 或按 X。
  - 列出本月回應最多「只有一個 reply request」的編輯，附上他的 reply 們
  - Query: `ListAritcle` filter by `repliedAt` 時間區段、`replyRequestCount` = 1、`replyCount` >= 1 之後統計編輯名字。
  - Reply 列表可以另外輸出到 google spreadsheet
- 發文用底圖 （其實可以用 figma）
- LINE 登入後使用電腦直接上稿 article + reply

----

orz
獨立在網站之外
做完之後換 API endpoint 就可以變成泰國的 social media toolkit 惹
只要是 Cofacts API 都能接

Instant 頁面其實也屬於這種性質（社群用 + 大多只有 query），應該放在這個專案下。

:::success
可以開個 cofacts/community-builder repo
:::

## Staging API

升級 elasticsearch client，fix breaking change

變更太大所以直接放上 staging 跑跑看
https://github.com/cofacts/rumors-api/pull/153


## Staging site

目前上的版本是[PR-247](https://github.com/cofacts/rumors-site/pull/247)，內有所有 list page UI。

## Staging LINE bot

Staging: https://lin.ee/1QUzEX4nI

### 桌面版可以打開 ＬＩＦＦ
sendMessage 看起來無解：https://github.com/line/line-liff-starter/issues/9

- 桌面版 LINE 開 LIFF 一定是 external browser
- external browser 就會不支援 sendMessage (Ref: https://developers.line.biz/en/reference/liff/#send-messages )


使用 `liff.isInClient()` 處理
https://developers.line.biz/en/reference/liff/#is-in-client

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2520476574891d2307bd114532ae2277.gif)

### 送出 source 與 reason 後的訊息重複問題

> 第二個 provide more info 其實不用是 highlight 色
> 因為他已經提供過理由了
> 這樣的話上兩個是灰色，兩個 bubble 可以合併成一個
> 但填了ｓｏｕｒｃｅ還沒填 reason 的可以不用 merge 成一個 bubble
> [name=Lucien, [20200429 會議記錄](https://g0v.hackmd.io/@mrorz/BksBf58KI#%E9%80%81%E5%87%BA-source-%E8%88%87-reason-%E5%BE%8C%E7%9A%84%E8%A8%8A%E6%81%AF%E9%87%8D%E8%A4%87%E5%95%8F%E9%A1%8C)]

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_44bbc4718c130674369e6d9c88a456f8.png)


![](https://user-images.githubusercontent.com/108608/81098815-790e2000-8f3c-11ea-8c1d-d2917421ab65.png)
- In response to source (first carousel), both bubble are all call-to-actions (we want user to both provide more info and share)
- In response to reason (2nd carousel), not many people updates their own reason, thus use gray color instead; also, the update bubble is moved to the right (2nd bubble).

PR: https://github.com/cofacts/rumors-line-bot/pull/184


### Feedback yes/no wording
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b10a03ee5f30ab4321c2478aa1f4f754.png)


## Landing page 討論

> from 志超

Discussion: https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1588067286.270900

https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=994%3A111

## 假名討論

Lucien 已經取得作者大大同意使用
https://github.com/PlatoForum/PlatoForum/tree/2cdc807a6ec54f68e0479787ccb865f0e89aed50/utils/pseudonym_gen

From 上週：https://g0v.hackmd.io/ynQn2LmoQSmQQpwidirI6g?both
> random 生成存起來
> API server 產生
> 存在 users index, id: `app_id:user_id`, app_id 來源是 https://github.com/cofacts/rumors-api/blob/master/src/checkHeaders.js#L7

- 何時生成新的 user document
- 是否需要 DB migration

## url-resolver 輕量化？

url-resolver 有時會 not responding......

https://github.com/cofacts/url-resolver/issues/69


---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220413 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis: bil, mrorz, nonumpa
- Guest: jiahe
- 線上出席：4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

Forgot to release last week......


### :rocket: Staging

#### :electric_plug: API
- [Changes from last week](https://g0v.hackmd.io/gyIJXbTqRnySbfeaPJcJew#-API)

#### :robot_face: rumors-line-bot

- [Changes from last week - LIFF](https://github.com/cofacts/rumors-line-bot/pull/300)
- [Revamp no reply flow #302](https://github.com/cofacts/rumors-line-bot/pull/302)

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 送出「沒回應」的舊訊息，應可送出新理由
    - [x] 文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以修改理由送出。查看 article page 看理由是否有被送出。
    - [x] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應
    - [x] 選擇回應之後可以幫回應 upvote
    - [x] 可以再次選擇 downvote
    - [x] 選完回應之後，還可以捲回去選其他回應
    - [x] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

##### ⛔️ Release Blockers
n/a

##### 未竟項目
n/a

## 大松檢討

活動頁面：https://hackmd.io/@mrorz/ByE9tPRQc

- 網路不好用 [name=bil]
- 工程師比較少、新參者工程師也少 [name=bil]
- 疫情下食物比較少
- 在大松送禮物給貢獻者很好
    - 讓第一次參與專案的人報告，會讓人覺得是他們的專案，下一次比較可能進行貢獻 [name=bil]
    - 送口罩不錯，上面就印 g0v logo
        - 戴出去廣告效益
        - 單價低
- 傳單被帶走一些
    - 新參者旅行團時發放很多 [name=mrorz]
    - 大家都趁旅行團問問題 [name=bil]
- 感謝 review 翻譯
- 大松的字幕翻譯上了 1min [name=bil]
- 交際比較多、貢獻稍少

## 十週年嘉年華徵件

https://g0v.hackmd.io/@chihao/g10v-book/%2FWEyWrVuvTcO6FgE6X8GBTg

- 4/9-5/9 投稿 活動介紹
- g0v 相關謠言的闢謠？
- Cofacts 上沒有，要去外面查

https://www.viewpointtaiwan.com/columnist/真的假的？唐鳳在搞輿論勞改營？/

https://www.ettoday.net/news/20160825/762311.htm

- 回應：https://medium.com/cofacts/%E6%91%98%E6%8E%89-%E5%85%AC%E6%AD%A3%E7%AC%AC%E4%B8%89%E6%96%B9-%E7%9A%84%E9%AB%98%E5%B8%BD%E5%AD%90-cofacts-%E5%B0%8D%E9%99%B0%E8%AC%80%E8%AB%96%E7%9A%84%E5%9B%9E%E6%87%89-bd948d128d6c

https://cofacts.tw/article/AVs8QULBtKp96s659DqC

## OCF 春季派對

https://ocftw.kktix.cc/events/ocf-spring-2022

mrorz + bil

## Multimedia 開發分票

- github tickets?
- github projects?

:::success
https://github.com/orgs/cofacts/projects/9/views/1
:::

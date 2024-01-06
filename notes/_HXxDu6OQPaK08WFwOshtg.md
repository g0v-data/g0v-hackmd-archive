---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220518 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz, nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

https://github.com/cofacts/rumors-site/releases/tag/release%2F20220514

> 我發現這個修法有個副作用
> 就是如果我在 article page 從旁邊的相似可疑訊息裡面點選一篇
> 他在 load 新訊息的時候，不會進入 loading state
> [name=mrorz]

### :rocket: Staging
#### :electric_plug: API
https://github.com/cofacts/rumors-api/pull/282

#### :globe_with_meridians: Site
https://github.com/cofacts/rumors-site/pull/490

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] Article list
  - [x] Can go to article page
- [ ] Replies list
  - [ ] Can go to article page  只有第一個有圖圖
- [ ] Hoax for you 有兩個圖
  - [ ] Can go to article page
- [x] Article detail
  - [ ] Can see similar messages 看到的不是圖圖
- [ ] Search
  - [ ] Can use global search to perform search 不確定要測試什麼
  - [x] Can use textarea in header to perform searchs
  - [ ] Can list searched articles 沒有圖的可以
  - [ ] Can list searched replies 沒有圖的可以

登入自有帳號後檢測：
- [ ] Article detail
  - [x] Can submit, upvote, downvote reply request
  - [x] Can submit, remove own reply
  - [x] Can upvote, downvote other's article reply

##### ⛔️ Release Blockers

##### 未竟項目

- mobile 上 article list / hoax-for-you 爆版
  - Detail, reply list, reply search 沒事
  - 用最簡單的修法即可：圖片窄一點
- reply detail 的 article list item 不會顯示圖 XD
- profile page 的查核回應列表也不會顯示圖 XD

### :eye: Under review

- https://github.com/cofacts/rumors-site/pull/490

## Media support

> https://github.com/orgs/cofacts/projects/9

- Determined rough ETA
- Currently opened https://github.com/cofacts/media-manager
  - main branch: bootstrapped with tsdx
  - [WIP] MediaManager class implementation https://github.com/cofacts/media-manager/pull/1/files

## Trend and Contribution

> https://github.com/orgs/cofacts/projects/10

- Added ETA
- Jun/E = feedbacks a user received on community builder
- Jul/E = LIFF trend

## 小聚檢討

> [小松果](https://g0v.hackmd.io/q2AjbzezR8SsMoozvnNCzA?view)

- 場地相關 [name=mrorz]
    - 通風 setup 問題：門沒有門擋、遙控窗簾無法拉起
    - 要填 https://www.surveycake.com/s/DzyWD
    - 網路 OK，不自架也行
- Time control? [name=mrorz]
  - 3:30 ~ 4:00 第二階段
  - 回答 8 題，30 min
  - 也介紹了回報檢舉
- Revamp 第二階段介紹 - 案例取代比較空泛的內容
  1. 複習 Cofacts 頁面內容，加講 trend 與數字
  2. 判斷撇步 1：要不要處理
  3. 判斷撇步 2：找內容（刪掉訊息不完整那個，現在不會有此 case） 
  4. 寫回應：教學！
      - 其他三種查核回應、「含有」
          - 編輯有不同判讀例子
          - 可查核的「事實」
          - 不可查核的「意見」
      - 畫重點：哪個有把握就回哪個
          - 行有餘力，觀察情緒，決定回哪個
      - 特別的「含有個人意見」
      - 送出後會在 chatbot 怎麼呈現
  5. 查到一半而已 --> 補充
- 不用 spreadsheet，直接用主題分？ [name=mrorz]
  - 流程是設計給電腦的，Pad 與手機比較難
  - 沒回的訊息變多了，不太會重工，不用 spreadsheet 可能也 OK
    - 「還未有有效查核」filter [name=bil]
    - 但大家會從列表從上做到下，比較久以前的就沒有什麼機會 [name=mrorz]
  - 把 cofacts.tw 作為第一印象

:::success
1. 重構第二階段的教學
2. 思考不用 spreadsheet 讓大家一起做的方式
:::

## Moderation discussion

### 簡化二次詐騙公告流程

- 直接改現有公告 [(Example)](https://github.com/cofacts/takedowns/commit/fc77198791525a16d85067fa7628bb6b318249e8?diff=unified#diff-34893516a53b8b910e6dcb6377108f01eb195998a15702d346a5594cf6580a21) ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_790480dd306ff9e90d4fa01317c15f5e.png)
- 主動偵測
    > 這次被檢舉的兩位都在 10 多分鐘內貼了 40 多篇
    > 我看了一下 replyrequest 的 appId ，是正常的 WEBSITE （代表有用 cookie 登入）
    > 我猜是寫了 sikuli 或 selenium 這類的 e2e script 做的
    > [name=mrorz]
    - 找出二次詐騙必回 article list
    - 定時掃這些 article 看
    - 需要新 API filter 來掃 articleReply: https://github.com/cofacts/rumors-api/pull/283
        - Also helps in profile page, when listing article replies of current user

:::success
- Bypass code review for 二次詐騙：OK
- 改 ListArticles API
:::

### 單人操控兩帳號 case

https://cofacts.g0v.tw/article/AV2HK6GOyCdS-nWhudKS by cai

- CIB 參與者
    - https://cofacts.github.io/community-builder/#/editorworks?type=1&day=7&userId=iCZiwYABvUvLpBdg593j&showAll=1
    - https://cofacts.github.io/community-builder/#/editorworks?type=0&day=7&userId=GSYJw4ABvUvLpBdgxuA-&showAll=1
- Alan 與 Mango 在同一天先後註冊，均使用 Twitter 註冊
- 兩個帳號的 email 前 7 字雷同，使用同一個免費 email 服務
- 一個帳號用 Android 手機、另一個帳號用 iOS 手機，IP 不同

:::success
先去社團貼文問，類似 
https://www.facebook.com/groups/cofacts/posts/3273891186176021/
:::

### 呼朋引伴 case

https://cofacts.g0v.tw/article/s8n7zllc0py1 by cai

- 這四個 upvote 的帳號都是 Google 登入
- 也都是 5/6 上午註冊
- 只有按這篇讚，沒其他活動
- 回應者與按讚者 5 人的 IP 均不同，看起來比較像是呼朋引伴
    - 回應者：https://cofacts.github.io/community-builder/#/editorworks?type=0&day=365&userId=kkZ6zIABLBWbhK-vg-b5&showAll=1
    - 按讚者：
        - https://cofacts.github.io/community-builder/#/editorworks?type=1&day=365&userId=rEaLzIABLBWbhK-vrubm&showAll=1
        - https://cofacts.github.io/community-builder/#/editorworks?type=1&day=365&userId=z0aczIABLBWbhK-vOebJ&showAll=1
        - https://cofacts.github.io/community-builder/#/editorworks?type=1&day=365&userId=mkZ_zIABLBWbhK-vg-bY&showAll=1
        - https://cofacts.github.io/community-builder/#/editorworks?type=1&day=365&userId=nUaAzIABLBWbhK-vguZx&showAll=1


---

- [CIB](https://g0v.hackmd.io/@johnson/HykZ8rq4H#%EF%BC%88%E6%9C%AA%E9%9B%A8%E7%B6%A2%E7%B9%86%EF%BC%89CIB-%E8%99%95%E7%90%86) 跟呼朋引伴都是破壞遊戲規則，不該存在 [name=bil]
  - 按讚的又不闢謠，不是一個人帶下線來處理
  - [TrustGlobal 也是，互捧彼此回應](https://www.facebook.com/groups/cofacts/posts/3066647213567087)
  - Trust global 也應該一併處理 [name=bil]
    - block 協同的按讚，因為他們不是真實的機器人使用者，而是協同效應來的 [name=bil]
    - 帶一群人來按讚不是正常的使用
- 去社團公告說 block 按讚的 4 人 [name=mrorz]

:::success
- 去社團公告處理：block 按讚 4 人、溯及既往至 trust global 的按讚者
- 羅列按讚帳號
:::

## Open data in spreadsheets

- 165 公告 (CC0)
    - Spreadsheet: https://docs.google.com/spreadsheets/d/1qKSwF7lAtZEOvz7ksgoG3jShd0nNjAsA0aaV6fmBzEo/edit#gid=0
    - 每天從 165 網站（每週更新）爬公告，沒有做什麼轉譯，故 CC0
- 檢舉表單
    - Spreadsheet: https://docs.google.com/spreadsheets/d/1q-iMJ9tZtoyHNfwInAb3z-eIg2x4-w1yp7XGTiaLB-w/edit#gid=462534108 (非公開)
        - 含操作用表單與程式碼
    - 公開網址：https://docs.google.com/spreadsheets/d/1q-iMJ9tZtoyHNfwInAb3z-eIg2x4-w1yp7XGTiaLB-w/edit#gid=462534108
    - 僅為公告用途，並無標註 license
- 新：blocked users & contents
    - Spreadsheet: https://docs.google.com/spreadsheets/d/1F3NSAVuBQdJfdaywL01GLI_wd_ejf9PulLGuBlwiGvQ/edit (非公開)
    - 定期打 Cofacts API 拿 blocked user & blocked content (TBA)
    - 未來想要開放成 CC BY-SA 資料集 ([同 opendata](https://github.com/cofacts/opendata/blob/master/LEGAL.md))

:::success
有空就做
隨喜
放去 https://github.com/cofacts/opendata
:::


## Universal analytics to GA4

> Cofacts 網站跟 chatbot 都仰賴 google 的 universal analytics
> 結果 ua 明年 7 月就不能用了囧
> https://support.google.com/analytics/answer/11583528
> 
> 先盤點了一下
> 目前用到 GA 的東西
> 升級 GA4 時要考慮的 mapping
> 放在共筆裡
> https://g0v.hackmd.io/QRRlVa_URk-wT0QqahLN-w?view
> 目前是連到底要開幾個 GA4 property、幾個 data stream、chatbot 資料流怎麼接，都還沒有決定⋯⋯
> [name=mrorz]
> 

:::info
求有 GA4 經驗的人 QAQ
:::
https://jothon.g0v.tw/

## 6/18 大松

提案已滿 https://beta.hackfoldr.org/g0v-hackath50n/https%253A%252F%252Fdocs.google.com%252Fspreadsheets%252Fd%252F1ijhY4aQfv02SmTLeAP4kwXIp6H3GQzJ-YMSeb83NPg8%252Fedit%2523gid%253D1
報名也快滿ㄌ https://jothon.g0v.tw/

> Email subject: [OSCVPass] WorkShop 活動：將與 OSCVPass 合作社群：SITCON、COSCUP x g0v jothon，分別舉辦兩場次開源貢獻

## 自然醫學陳俊旭

- 雙掛號給 Cofacts 真的假的，但沒有人叫這個名字也沒這個法人，所以就退回去ㄌ

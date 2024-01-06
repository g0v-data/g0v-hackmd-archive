---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20210623 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production
N/A

### :rocket: Staging

#### :robot_face: rumors-line-bot

- #269 Fix highlight issue
- #262 Storybook
- #263 Include GraphQL schema in code base
- #261 chagne main brain to master

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 送出[會有 bug 的舊訊息](https://github.com/cofacts/rumors-line-bot/issues/220)，應自動回傳回應
    - [x] 應列出訊息所有的回應
    - [x] 選擇回應之後可以幫回應 upvote
    - [x] 可以再次選擇 downvote
    - [x] 選完回應之後，還可以捲回去選其他回應
    - [x] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

> 小心囉，北農18名新冠確診，四樓營業部重災區，每天包20-30萬包蔬菜給全聯，前幾天就有了，但因為蔬果是民生必需品，故沒公佈，今天爆18人，大概是瞞不住了，暫時不要去全聯！
> https://udn.com/news/story/120940/5537424?from=udnamp_storysns_line

> 陳培哲說這1年多來參加了約50多次疫情會議，如果篩檢出新冠肺炎的高齡患者、糖尿病、腎臟病等慢性病者，立刻打新冠單株抗體，可以減少5到6成死亡率。「這我很早就講過了，他們充耳不聞，那些生命是可以挽救的，你就知道我的挫折有多深。這代表這個指揮中心的科學判斷與能力不足。」
>
> 陳培哲指出，另一個疫情中心不夠科學專業的地方是「核酸檢測方式」。美國食藥局（FDA）有一套檢測系統，但台灣的病管局（CDC）卻自己弄另外一套，沒自動化、量能少又不凖，專家建議應採FDA的系充，但指揮中心根本不聽。「這次中國廣州疫情爆發，1000多萬人1個禮拜做完採檢，用我們手動方式要做到哪一年？」
> https://www.storm.mg/new7/article/3740414?fbclid=IwAR3KtouSJVdWjFM0VVA3dj7J-0kWBxxObEw0jNjpy87LpQil0fmMYrm0OzE

##### ⛔️ Release Blockers
##### 未竟項目

### :eye: Under review

#### :robot_face: rumors-line-bot

- [#267 common components in LIFF](https://github.com/cofacts/rumors-line-bot/pull/267)
- [#268 Remove svelte-material-ui](https://github.com/cofacts/rumors-line-bot/pull/268)

## 大松籌備

- 誰會到
    - bil 提案
    - mrorz
    - nonumpa 直播
- 禮拜五 8pm 坑主測試
    > 嗨嗨 hackath44n 坑主們，感謝這次來線上大松提案，揪松團跟主持人們會在 6/25(五) 20:00 GMT+8 進行彩排跟演練，如果坑主們有空一起上線測試操作一下 gather town 也歡迎加入，若這個時段無法加入但仍想測試請私訊我約時間，感謝大家！（請注意螢幕分享時若想同時分享音訊，Mac 有機率會失敗，希望大家報告的時候盡可能避開撥放影片） [name=ichieh]
- 投影與場地佈置 (?)
    - community builder - 其中一人一直投影 community builder，投影特定視窗而非螢幕即可
    - 週五問：是否可以放 NPC 進來一直投影（佔一個名額）
- 線上活動的差別
    - 導覽團不確定怎麼進行
    - 會一直盯著螢幕，不像大松可以休息
    - 每小時跟 fly 一起做運動 (?)
    - 要訂一個吃東西／自由活動的時間，不然會尷尬
        - 吃飯：12:30 - 13:30
- Good first issues
    - 網站為主

## Server 觀測

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b9f9558ceabe17b3e41f4fef1d62f979.png)

- 6/17: 北農確診，「不要去全聯」瘋傳 [name=nonumpa]

### Error 爆大量
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9fa27c77630a74e64f943b77fd3f1103.png)

6/17 4AM - 6AM
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_16e7d1eb21a4ba0b87bb9ad1237cea3d.png)

6/15-6/19 170 errors
- 48 request timeout
- 3 Session protocol negotiation failure: https://line-bot.cofacts.tw/callback 
- 2 Connection timeout: https://line-bot.cofacts.tw/callback
- Others: "502"

> 看起來 container 活得好好的，nginx 也沒死翹翹
> nginx access log 與 error log 相對應的時間也都沒有 502 log
> [name=mrorz]

---

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8f62e9013c7db0c1ed1ab2ccca773687.png)

- Connection timeout 2
- Request timeout 2

### lastScannedAt 問題
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7c36cfd42160a0ebd20b4c75b54466ed.png)
> 針對 lastScannedAt 一直被刪掉
> 我做了個爛招
> 就是加一筆 cronjob 每一小時去讀一次 lastScannedAt
> 希望這樣他就不會被 LRU 掃到⋯⋯囧
> [name=mrorz 2021/6/22]


## Reply request 觀察
- 有使用者吵起來 https://cofacts.tw/article/14qezlzjtt9ej
- 有使用者以為 reply request 就是回應 https://cofacts.tw/article/3jbfecc2s95mr ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_66e911da1e77b3fba13b282318b27af8.png)
    - 看要不要折疊？[name=mrorz]
    - 沒有回應之前不要折疊，但查了而且很多人按覺得有用，就可以想成是結案，可以折疊 or 放在後面 [name=bil]
    - 折疊的時候只把 LINE bot 使用者的折疊起來，網站使用者輸入的 comment 不會被折到 [name=mrorz]
        - 因為我們有教使用者，不確定怎麼回就先放 comment，網站使用者的 comment 參考性較高
        - 有人按覺得有用的 comment，也可以考慮不折疊 (?)
        - 有回應之後放後面也可以


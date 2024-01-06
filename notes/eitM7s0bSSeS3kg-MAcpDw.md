---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20200812 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil.orz.文武. Lucien
:::

## Cofacts Next! 追蹤

- [收尾] Chatbot notification
    - 過去對話紀錄轉 `userArticleLink`
        - ~ 2020-07-31 23:57:29.000Z 共 358,098 筆
            - 這個數量若不建 index 直接 sort 會觸發 memory error
            - 不建 index 直接 `COLSCAN` 動輒 100ms
        - 需要增加 index:
            - list 與 insert 用：`{ "userId" : 1, "articleId" : 1, "createdAt" : -1 }`
            - 查看用：`{ "lastViewedAt" : -1 }`
        - [x] 跑 [script](https://github.com/cofacts/rumors-line-bot/blob/dev/src/database/backtrack.js) 但有下述修改
            - `UserSettings` 底下 `allowNewReplyUpdate` 先全部填 `false`
                - 因為按照下面的 Progress，只想先讓部分使用者有通知
            - `UserArticleLink` 的 `createdAt` 原本是真正的 insertion time，但改成與第一次的 `lastViewedAt` 同
                - 因為 LIFF 裡面的瀏覽紀錄係按照 createdAt 反向
                - `createdAt` 當順序會比 `viewedAt` 固定，比較不會嚇到使用者
                - backtrack.js 執行的時間對使用者
沒有意義
                - 確實存在不少同一個訊息查兩次的現象，`createdAt` 與 `lastViewedAt` 不同 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_32ae77663cc57109e483fb65d2521e45.png)
        - [x] 放進自己電腦的 local mongodb 後 mongodump
        ```
        $ mongodump --uri="mongodb://root:root-test-password@localhost:27017/cofacts?authSource=admin" --collection="userArticleLink" --out="userArticleLink-staging-dump" 
        $ mongodump --uri="mongodb://root:root-test-password@localhost:27017/cofacts?authSource=admin" --collection="userSettings" --out="userSettings-dump"
        ```
        - [x] 把所有的 `UserSettings` 跟 [2019/12/12](https://cofacts.org/article/3ngpjephqmn7g) 以前的 `UserArticleLink` 的 dump 放進 staging DB
        ```
        $ mongorestore --uri=$MONGODB_URI userArticleLink-staging-dump
        $ mongorestore --uri=$MONGODB_URI userSettings-dump
        ```
        - `mongorestore` 會跳過造成 unique index error 的項目
            - 共 1441 個 usersetting
            - 大概一半已經 unfollow 所以 `allowNewReplyUpdate` 已經是 false
        
        > 如果預設都關閉，我們都準備好之後再發個推播說有這個選項可以設定
        > 想說預設開啟的話，使用者可能會不知道如何關閉，就把我們封鎖了
        > [name=mrorz]
        > 商業產品的話我會考慮預設開啟，但調整推播頻率
        > 我們這裡可以預設關閉，然後如果使用者送新訊息進來後，沒有得到回應，使用者又沒有開啟推播的話，可以多問一句要不要開啟
        > [name=lucien]
        > 
        :::success
        1. 今晚的 migration 會把所有人的推播關掉，然後我們自己把自己的打開，測個一週
        2. 開一張票做「如果使用者送新訊息進來後，沒有得到回應，使用者又沒有開啟推播的話，可以多問一句要不要開啟」
        :::
        
    - Progress
        - 8/12 討論 rich menu
        - 8/13 凌晨：
            - 把舊資料放進資料庫
            - release rich menu
            - 啟動推播 cron job 但預設不把使用者通知啟動（只啟動部分人的通知）
        - 8/19 看看通知的狀況（頻率、cron job 執行狀況、使用者回應）
    - MongoDB backup mechanism
        - owner: GGM
        - 是否需要 read-only user?
        - Mongodump --> 到哪裡？GCS?
        - Plan

- Article analytics from GA
    - Owner: Zoe
    - Tracking board: https://github.com/orgs/cofacts/projects/7
    - Plan: API done :rocket: , 9/7 for UI

- `ArticlePageLayout` refactor
    - Owner: MrOrz
    - Spec: https://g0v.hackmd.io/h8rP0TOGTh2Clxi_Oi_QKw
    - Plan
      - 2nd PR:
        - 節外生枝：`ArticleReplyFeedbackControl`⋯⋯
        - 主 PR: https://github.com/cofacts/rumors-site/pull/288 8/15 [萌典松](https://g0v.hackmd.io/-KiPYTO3T96V-KJM_dRdyw) 做做看⋯⋯
      - 3rd PR: 8/15 [萌典松](https://g0v.hackmd.io/-KiPYTO3T96V-KJM_dRdyw) 做做看⋯⋯

- User ID refactor
    - Owner: MrOrz
    - Spec: https://g0v.hackmd.io/ZcoUOX_-RQSkJyl5xz4_Zg?view#%E6%96%B9%E5%90%91-2-%E9%87%9D%E5%B0%8D%E6%AF%8F%E5%80%8B-backend-user-%E9%83%BD%E7%94%A2%E7%94%9F%E4%B8%80%E5%80%8B-user-document
    - Plan: GG

- 教學頁 spec
    - owner: Lucien
    - https://g0v.hackmd.io/sB_zayWjTo-W0R7xe_U34w
    - ETA：

## 討論事項

### RSS 訂閱教學影片

腳本：見 [20200805 會議記錄](/rEtx-47bRHeW2aM05DINDQ)
用 Keynote 做：https://www.icloud.com/keynote/0uSJhzhXm6ti2ua9frzQuqubw#Cofacts_subscribe_tutorial

需要：
- 設定 IFTTT Applet
- 步驟截圖
- 錄音

> 中英文 [name=lucien]
> 先中文吧
> youtube id 是 runtime env variable [name=mrorz]


UI:

> icon 要重畫嗎
> 「下載成 svg」好像會變成點陣 [name=nonumpa]
> 可以切 figma [name=lucien]
:::success
icon 先不動
:::

> 手機版？現在 width 寫固定的[name=nonumpa]
> dialog 應該用 material-ui 自己的寬度
> video 用 100% width + percentage bottom-padding 做 16:9 


### chatbot 不問來源

放進 https://github.com/cofacts/rumors-line-bot/issues/214


### 誤認 Cofacts 為訊息來源的 case

- 有人把 Cofacts 當成謠言來源：https://www.facebook.com/100004743373440/videos/1661616297339800/
- 3 個人把 Cofacts 當成主辦單位：https://cofacts.g0v.tw/article/2ic0n2moc0ppy
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_be85b0359450b581c2f3a513e7b08b1f.png)
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4250ec14eb4ba71bb88726f62a4014c4.png)
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_147c30edfd00616923683fb4a3810a35.png)


> 覺得可能是因為沒中文，把中文翻好或許就可以 [name=mrorz]
> ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ee04999182b993939aa793d876943655.png =x300)
>
> 今天又收到催 cofacts cite 他們網站的信
> 覺得可以不理 [name=bil]
> 感覺是在做自己網站的 SEO 的人，所以不想管他們 XD [name=mrorz]

### LINE bot onboarding UX

> 過去的討論：https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2F%40mrorz%2FS1cpqgCpr
> 後來沒有留下成果圖 QQ
> 

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b875d6ca30afbb259c1c8f59006973ec.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_27609bb865e00c8127ee064b9476a2d4.jpg)

> 需要志超出插圖嗎
> 會有角色插圖
> 狗狗或許可以變成 loading gif
> [name=lucien]

> chatbot 這裏是呈現 lookup 情境，比較單純
> 網站的教學則是會呈現到「第一次送出」＋「網站編輯」的部分
> 有重疊不過不太一樣
> [name=mrorz] 

> 會有 edge case 是
> 被朋友推薦，沒走完流程就轉傳進來，會發生什麼事情 [name=lucien]
> 會直接中斷 onboarding 流程，開始跑 state diagram
> 但或許可以在 rich menu 做一個按鈕重跑 onboarding [name=mrorz]
> 「權限設定」按鈕是為了讓使用者第一次開啟 LIFF 按下 user consent 這樣
> 除了「設好囉」之外也可以考慮把推播 toggle 也放進去 [name=mrorz]

:::success
以上開票追蹤
行銷之前做完
:::

### LINE bot menu 討論
> - [20200325](https://g0v.hackmd.io/@mrorz/HkqrDEOLI#LINE-chatbot-rich-menu) Rich menu 選項討論
> - [2018](https://hackmd.io/@mrorz/SyivqlIrf?type=view#Rich-menu) 初次討論 menu
> - [2019](https://g0v.hackmd.io/@mrorz/S1D8FVqf4?type=view#rich-menu-%E8%A3%A1%E9%99%84%E4%B8%8A%E7%AF%84%E4%BE%8B) 討論附上範例的做法（失敗）

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6f5582ad38e1020d364e38e53d56084c.png)


功能：

```
1 2 3 
4 5 6
```
> Image sizes: 2500 × 1686, 2500 × 843, 1200 × 810, 1200 × 405, 800 × 540, 800 × 270

1. 教學 - 重新觸發 on boarding UX？ （暫時跟「分享」合併）
2. 小聚 --> 近期活動 - https://cofacts.kktix.cc
3. Cofacts 官網 - https://cofacts.g0v.tw
4. 分享 chatbot - https://line.me/R/nv/recommendOA/@cofacts
5. 推播設定 `https://liff.line.me/1563196602-R1zEXaDB/liff/index.html?p=settings`
6. 我問過的訊息 `https://liff.line.me/1563196602-R1zEXaDB/liff/index.html?p=articles`

:::success
志超做圖
:::

### Reply search 相關討論

- Related issue: https://github.com/cofacts/rumors-site/issues/295
- Discussion item see [20200729 meeting note](https://g0v.hackmd.io/r3NK7xssSwCNPFxthlw7tA#Reply-search-%E7%9B%B8%E9%97%9C%E8%A8%8E%E8%AB%96)


> 「取消」按鈕有「清除搜尋字串」與「拿掉搜尋結果」兩個意思 [name=lucien]
> 「卡片設計更 compact」「浮動搜尋結果視窗」之後有 figma 再處理

:::success
除待 figma 處理的項目之外，都放進 https://github.com/cofacts/rumors-site/issues/295 了
:::

## 編輯小聚
> 前次討論 https://g0v.hackmd.io/9qp8dE7dReK2q8FTeP9Feg#8%E6%9C%88%E7%B7%A8%E8%BC%AF%E5%B0%8F%E8%81%9A%EF%BC%9F
> NPO Hub 小松填單 - https://g0v.hackmd.io/@jothon/hsiaothon/

bil: 8 月萌典松的話，可以改辦在 9 月
https://moe.kktix.cc/events/moed23ct-20200815  @ NPO HUB Taipei 廚房

9/27 (日)
主題：孔子媽媽待產日

> 9/26 (六) 要上班 [name=mrorz]
> 我們公司不用 [name=lucien]
> 這樣台北工作的人就都會留在台北所以很好 [name=bil]

:::success
麻煩 bil 填單：
https://docs.google.com/forms/d/e/1FAIpQLSee5Y9AX_uLjGpGwt3afsDJyrPJ_IHZnyMWggHgGMU05YHo-Q/viewform
:::

## :potable_water: Release pipeline

### :star: Released to production

Nope

### :rocket: Staging

#### :globe_with_meridians: Site

(TBA, 目前成果上 staging 沒上 production)

#### :electric_plug: API

##### Feature

- #180 #188 #189 #190 #191 #194 #195 #206 # Google analytics related changes

##### Bugfix

- #187 load more than 10 reply requests at once

:::success
20200815 deployed to production
:::

##### DB migration

- schema: https://github.com/cofacts/rumors-db/blob/master/schema/analytics.js
- migration
```
$ ELASTICSEARCH_URL=http://<DB URL> npx babel-node db/migrations/202008-add-analytics.js
```

:::success
Staging, production done
:::

##### Server setup
0. Setup
    - `GOOGLE_OAUTH_KEY_PATH`, `GA_WEB_VIEW_ID` and `GA_LINE_VIEW_ID` in docker-compose and restart server
    - Insert stored script in database
        Staging
        ```bash
        $ ./compose-all exec cofacts-api-staging node build/scripts/fetchStatsFromGA --loadScript
        ```
        Production
        ```bash
        $ docker-compose exec api node build/scripts/fetchStatsFromGA --loadScript
        ```
2. Try out cron job in one-off script 
    Staging
    ```bash
    $ ./compose-all exec cofacts-api-staging node build/scripts/fetchStatsFromGA --startDate=yesterday --endDate=yesterday
    Production
    ```bash
    $ docker-compose exec api node build/scripts/fetchStatsFromGA --startDate=yesterday --endDate=yesterday
    ```
2. See result
    Curl
    ```
    curl <ES_URL>/analytics/doc/_search -H 'Content-Type: application/json' -d '{"query": {"match_all": {}}}'
    ```
    GraphQL
    ```graphql
    {
      GetArticle(id: "3fczhzr31y8ap") {
        id
        stats {
          date
          webUser
          webVisit
          lineUser
          lineVisit
        }
      }
    }
    ```
3. Setup cron-job (ensure on-going data works)
    Staging
    ```bash
    # hourly update
    0 * * * * cd answerfamily-deploy; ./compose-all exec -T cofacts-api-staging node build/scripts/fetchStatsFromGA.js >> cron.log 2>&1
    # daily update yesterday's last hour number (UTC+8)
    15 16 * * * cd answerfamily-deploy; ./compose-all exec -T cofacts-api-staging node build/scripts/fetchStatsFromGA.js --startDate=yesterday --endDate=yesterday >> cron.log 2>&1
    ```
    Production
    ```bash
    0 * * * * cd /home/docker/rumors-deploy; /usr/local/bin/docker-compose exec -T api node build/scripts/fetchStatsFromGA >> /var/log/cron.log 2>&1
    # daily update yesterday's last hour number (UTC+8)
    15 16 * * * cd /home/docker/rumors-deploy; /usr/local/bin/docker-compose exec -T api node build/scripts/fetchStatsFromGA --startDate=yesterday --endDate=yesterday >> /var/log/cron.log 2>&1
    ```
4. Peform migration script
    Staging
    ```bash
    $ docker-compose exec api node build/scripts/fetchStatsFromGA --useContentGroup=false --startDate= --endDate=
    ```
    Production
    ```
    $ ./compose-all exec cofacts-api-staging node build/scripts/fetchStatsFromGA --useContentGroup=false --startDate= --endDate=
    ```
5. See result using GraphQL
    Command see 2.


If staging OK, perform identical operation on production

#### :robot_face: Chatbot

無 code change，主要是資料庫與設定的變更

##### Feature

- 推播 deployment
  - 設定 env vars
      - Staging:
          - `NOTIFY_METHOD=LINE_NOTIFY`
          - `LINE_NOTIFY_CLIENT_ID=<paste LINE Notify Client ID here>`
          - `LINE_NOTIFY_CLIENT_SECRET=<paste LINE Notify Client Secret here>`
          - `RUMORS_LINE_BOT_URL=<line bot server url>`
          - `LINE_FRIEND_URL=https://line.me/R/ti/p/@nkq3195z`
          - `REVIEW_REPLY_BUFFER={"seconds":0,"minutes":-1,"hours":0,"days":0}` 1 分鐘 buffer
      - Production:
          - `NOTIFY_METHOD=PUSH_MESSAGE`
          - `REVIEW_REPLY_BUFFER={"seconds":0,"minutes":0,"hours":-12,"days":0}` 12 小時 buffer
  - 重新佈屬 heroku app
      - 因為 `NOTIFY_METHOD` 在 LIFF 是 build-time constant，所以改了之後必須重新 build
- 啟動 Cron job
    - `node build/scripts/scanRepliesAndNotify.js` in Heroku scheduler, or
    - `heroku run -r staging node build/scripts/scanRepliesAndNotify.js`

    :::spoiler
    Staging 有跑成功
    ```
    15 Aug 2020 12:01:18.601201 <45>1 2020-08-15T04:01:15.794790+00:00 app api - - Starting process with command `node build/scripts/scanRepliesAndNotify.js` by user scheduler@addons.heroku.com
    15 Aug 2020 12:01:34.473178 <45>1 2020-08-15T04:01:33.92109+00:00 heroku scheduler.3161 - - Starting process with command `node build/scripts/scanRepliesAndNotify.js`
    15 Aug 2020 12:01:34.811139 <134>1 2020-08-15T04:01:34.460759+00:00 heroku scheduler.3161 - - State changed from starting to up
    15 Aug 2020 12:01:36.433125 <190>1 2020-08-15T04:01:35.727127+00:00 app scheduler.3161 - - [heroku-exec] Starting
    15 Aug 2020 12:01:37.336132 <190>1 2020-08-15T04:01:36.720754+00:00 app scheduler.3161 - - [notify] notificationList :{}
    15 Aug 2020 12:01:37.491133 <45>1 2020-08-15T04:01:36.956209+00:00 heroku scheduler.3161 - - Process exited with status 0
    ```
    :::
##### Bugfixes

無

##### Others
無

##### Testing checklist

- [x] 可以打開查過的訊息列表
- [x] 可以打開推播設定
    - [x] 可以開關設定
- [x] 進行回應、執行 cronjob 應該可以收到 LINE notify 通知

##### ⛔️ Release Blockers

- `node build/scripts/scanRepliesAndNotify.js` 好像不會自己結束？

:::success
PR: https://github.com/cofacts/rumors-line-bot/pull/215

Verified on staging:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e13cdfd727a773c9d7f9fe34b354fcea.png)

Deployed binary to prodcution as release/20200815
:::

:::danger
1. 就算把所有人 UserSettings 的推播設定調成 false，在 rich menu 做好、引導 onboarding 流程做好之前，新加入的使用者還是會預設被打開推播、然後被 LIFF 的 consent screen 擋住囧
2. LIFF 設定應該會需要更多 description，且應該要翻譯成中文

--> cronjob 設定的部分至少要等到 rich menu 做好⋯⋯
:::

##### 未竟項目

- staging 預設開啟 notification 的話，會造成有人有開 notification 但卻還沒設定 LINE notify token 的情形。
--> 見上面的討論，會全部預設關閉。

### :eye: Under review

- [Upgrade to Apollo Client 3](https://github.com/cofacts/rumors-site/pull/312)
- [RSS UI](https://github.com/cofacts/rumors-site/pull/305) Change requested
- [`ArticleReplyFeedbackControl` revamp](https://github.com/cofacts/rumors-site/pull/311)


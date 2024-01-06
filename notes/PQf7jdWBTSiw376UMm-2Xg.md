---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20200826 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, nonumpa
:::

## Cofacts Next! 追蹤

- [收尾] Chatbot notification
    - Migration: Blocked by rich menu
        - `UserSettings` 還沒放進 production
        - Cronjob 還沒設定與啟動
    - MongoDB backup mechanism
        - owner: GGM
        - progress?
- Article analytics from GA
    - API & migration all done
    - UI: will PR in Sunday
- `ArticlePageLayout` refactor
    - `ArticleReplyFeedbackControl`: 50% complete
    - 2nd PR https://github.com/cofacts/rumors-site/pull/288 not ready yet
    - 3rd PR Remove ArticlePageLayout 遙遙無期 orz
- User ID refactor
    - Owner: TBD
    - 還沒估時間～
- 教學頁 spec
    - owner: Lucien
    - https://g0v.hackmd.io/sB_zayWjTo-W0R7xe_U34w

## 討論事項

### RSS 訂閱教學影片

- 腳本：見 [20200805 會議記錄](/rEtx-47bRHeW2aM05DINDQ)
- [影片用 Keynote](https://www.icloud.com/keynote/0uSJhzhXm6ti2ua9frzQuqubw#Cofacts_subscribe_tutorial) 

> （Cofacts -- IFTTT -- LINE 示意圖、以及 IFTTT 在 LINE 回報的截圖）
> 透過 IFTTT，您可以在 LINE 上收到最新的 Cofacts 回報訊息。
> 
> （zoom in 到 IFTTT）
> 首先，您要先免費註冊 IFTTT 帳號。
> 
> （轉到 Cofacts，hoax for you 設定 filter，按下訂閱、選擇 IFTTT 訂閱）
> 在 Cofacts 找到您想訂閱的訊息列表、設定好您想要訂閱的主題，然後選擇透過 IFTTT 訂閱。
> 
> （複製 Feed URL、按下訂閱）
> 在視窗中複製 Feed URL 並按下「訂閱」
> 
> （IFTTT 巨大 switch UI）
> 這會帶你到 IFTTT、按下 Connect。
> 
> （LINE login）
> 它會跳轉到 LINE 讓您登入
> 
> （LINE Notify 頁面）
> 在同意 IFTTT 與 LINE Notify 連動之後
>
> （Connect to LINE 設定頁面）
> 您會再次回到 IFTTT，在「Feed URL」的地方貼上剛才複製的 Feed URL。
> 
> （LINE RSS 設定頁面）
> 最後，選擇您要接收訊息的聊天室，或使用 LINE Notify 一對一聊天，按下 Save，就完成訂閱囉！
>
> （Cofacts -- IFTTT -- LINE 示意圖、以及 IFTTT 在 LINE 回報的截圖）
> 之後 Cofacts 的這個列表有新的訊息時，IFTTT 就會將這些訊息傳到你指定的 LINE 聊天室。
> 一起來回應這些被回報的可疑訊息吧！

## 編輯小聚
上週討論：https://g0v.hackmd.io/DjY6dVLxQFG6moNlM98_OQ?both#%E7%B7%A8%E8%BC%AF%E5%B0%8F%E8%81%9A

- [x] 主題：
    - 孔子媽媽待產日
    :::success
    放課本孔子圖
    「明天我生日ㄛ」
    :::
- [x] 時間：9/27 (日) 14:00-17:00 Ronny keyholder(借13:30-17:30)
    - 備選：9/13 (日) (9/12 比鄰要演講所以不行)
- [ ] KKTIX
- [ ] 準備貼紙
- 場地：NPO Hub 廚房
    - [ ] 借用場地單 - bil
    - [ ] 食物
    - [ ] 延長線 (揪松有 3~4 條，但可以再帶)
        - [ ] MrOrz 一條
    - [ ] wifi
        - [ ] Nighthawk M1 + 4G sim
        - [ ] ASUS RT-N12 Wireless N300 (2x 5dbi高增益天線)
- [ ] 誰會來呢？
    - mrorz, bil, lucien, nonumpa, zoe (maybe)
- [ ] 誰不會來
- [ ] LINE 文案

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API

https://github.com/cofacts/rumors-api/compare/60d671509d2fa70e0a2bd733742818c34ba2dc44...master

##### Bugfix
- #211 Support SameSite=None to fix cross-site requests
- #214 Timestamp with correct timezone
- #215 Hyperlink cleanup script fix

##### Env vars
- [x] GOOGLE_OAUTH_KEY_PATH
- [x] GA_WEB_VIEW_ID
- [x] GA_WEB_TIMEZONE
- [x] GA_LINE_VIEW_ID
- [x] GA_LINE_TIMEZONE
- [x] TRUST_PROXY_HEADERS
- [x] COOKIE_SAMESITE_NONE

##### Migration

Google analytics migration finished on 8/25

:::spoiler
0. Delete all previously fetched analytics
    ```bash
    curl $ES_URL/analytics/doc/_delete_by_query -H 'Content-Type: application/json' -d '{"query": {"match_all": {}}}'
    ```
    
1. Try out cron job in one-off script 
    Staging
    ```bash
    $ ./compose-all exec cofacts-api-staging node build/scripts/fetchStatsFromGA --startDate=yesterday --endDate=yesterday
    ```
    Production
    ```bash
    $ docker-compose exec api node build/scripts/fetchStatsFromGA --startDate=yesterday --endDate=yesterday
    ```
2. See result
    Curl
    ```
    curl $ES_URL/analytics/doc/_search -H 'Content-Type: application/json' -d '{"query": {"match_all": {}}}'
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

3. Make sure cron job is properly set
4. Migrate old GA data
    Staging
    ```bash
    $ ./compose-all exec cofacts-api-staging node build/scripts/fetchStatsFromGA --useContentGroup=false --startDate=A --endDate=B
    ```
    Production
    ```bash
    $ docker-compose exec api node build/scripts/fetchStatsFromGA --useContentGroup=false --startDate=A --endDate=B
    ```
:::


### :rocket: Staging

#### :globe_with_meridians: Site

https://github.com/cofacts/rumors-site/compare/master...dev

##### Features
- #305 New RSS UI

##### Bugfixes
- #302 Security fix
- #304 RSS related fixes; RSS should start working again!
- #316 iOS polyfill
- #318 Fix search page static build
- #320 Fix "Asked many times"

##### Others
- #301 `<Infos>` time & metadata display component
- #311 Revamp article reply feedback component (50% complete); reorganize article reply related component props
- #312 Upgrade apollo-client to 3
- #317 Google translate now no longer blocks mobile UI

##### Testing checklist

http://dev.cofacts.org/

**未登入**下檢測：

- [x] Article list
  - [x] Filter works
  - [x] Sorting works
  - [x] Can go to article page

- [x] Replies list
  - [x] Filter works
    - [x] 不允許選擇 Replied by me
  - [x] Sorting works
  - [x] Can go to article page
  - [x] 不允許 upvote / downvote replies
  - [x] Can see vote reasons

- [x] Hoax for you
  - [x] Filter by topic works
  - [x] Sorting works
  - [x] Can go to article page

- [ ] Article detail
  - [x] Can see similar messages ( https://dev.cofacts.org/article/1fi7dla9wtwjn )
  - [x] Cannot submit, upvote, downvote reply request
  - [x] Cannot submit, upvote, downvote reply
  - [ ] Cannot add, remove, upvote, downvote category
      - downvote category broken

- [ ] Search
  - [x] Can use global search to perform search
  - [ ] Can use textarea in header to perform searchs
      - Firefox 沒辦法點擊搜尋按鈕
  - [x] Can list searched articles
    - [x] Filter works
    - [x] Sorting works
    - [x] Can go to article page
  - [x] Can list searched replies
    - [ ] Can go to reply page
        - 手機版完全不能進
        - 桌面版必須點按時間才行 @@ ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b7374857df9c6460488059d495febab1.png)

登入自有帳號後檢測：

- [x] Replies search page
  - [x] can upvote / downvote replies
- [x] Replies list
  - [x] 可選擇 Replied by me
  - [x] can upvote / downvote replies
- [x] Article detail
  - [x] Can submit, upvote, downvote reply request
  - [x] Can submit, remove own reply
  - [x] Can upvote, downvote other's article reply
      - (會整頁更新有點可怕)
  - [ ] Can add, remove, upvote, downvote category
      - 可以 upvote, 但 downvote 會 500

- [x] Can logout

##### ⛔️ Release Blockers

N/A

##### 未竟項目

- [ ] 搜尋回應的結果不能點
    - 但 production 現狀也是如此
    - 已經詢問設計師 https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO?node-id=432:2727#38351332
- downvote category 會 500 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f70c338e7b99191099ea8d94fa32ad20.gif)
- Firefox 沒辦法點擊搜尋畫面的橘色搜尋按鈕

## Rich menu

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5d6731fbdec524c9f914088f88067386.jpg)

（大小要調整）

:::success
Deployed to staging 試按～
:::
---
tags: cofacts
---

# 最近每日被查詢次數圖表

- Github tickets
    - [API](https://github.com/cofacts/rumors-api/issues/166)
- [Mockup](https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=889%3A306)
- Parent spec - [訊息詳情](/@NFi0czulSemxCM8RNSlz8Q/HJ8xT3QVU/%2FCx7dQo3YTQS4KwYmYCBY8w)

## Data definition

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4eb507a47399c0e4434e13c830969d5c.png)

X-axis
- Dimension: Date `ga:date`
- 區間
    - `start-date`: ~~`30daysAgo`~~ `today` (default when running cron)
    - `end-date`: `today` (default when running cron)

Y-axis
- 網頁瀏覽次數
    - id: Cofacts website's tracker
    - Metrics:
        - Hits `ga:pageviews`
        - Users `ga:users` (extra)
    - Dimensions
        - Article id `ga:pagePathLevel2` (when requesting stats for multiple articles)
    - Filter:
        - `ga:pagePathLevel1==/article/`
        - ~~`ga:pagePathLevel2==/<articleId1>[,ga:pagePathLevel2==/<articleId1>,...]` (when requesting stats for specified article IDs)~~ not applicable when implementing cron jobs

- LINE 詢問
    - id: Cofacts chatbot's tracker
    - Metrics:
        - Hits `ga:hits`
        - Users `ga:users` (extra)
    - Dimensions
        - Article ID `ga:eventLabel` (when requesting stats for multiple articles)
    - Filter:
        - `ga:eventCategory==Article`
        - `ga:eventAction==Selected`
        - ~~`ga:eventLabel==<articleId1>[,ga:eventLabel==<articleId2>,...]` (when requesting stats for specified article IDs)~~ not applicable when implementing cron jobs

右上角 toggle
- 網頁瀏覽次數 + LINE 詢問次數

### Core reporting API documentations
- [Query Parameters Summary](https://developers.google.com/analytics/devguides/reporting/core/v3/reference#q_summary)
- [Dimensions & Metrics Explorer](https://ga-dev-tools.appspot.com/dimensions-metrics-explorer/)

## Elasticsearch index spec

Index name: `analytics`

Document's ID encoding: `${type}_${docId}_${date in YYYY-MM-DD}`

Properties:
- `type`: string (`article` only. Maybe adding `reply` in the future?)
- `docId`: string (Article ID when `type` is `article`)
- `date`: Date 
- `fetchedAt`: Date - the timestamp that fetched this data
- `stats`: Object - groups the following properties together
    - `stats.lineUser`: number
    - `stats.lineVisit`: number
    - `stats.webUser`: number
    - `stats.webVisit`: number

:::spoiler Consideration in this design

設計此 index 時，應考慮未來可能會需要實作「找出某時間區段內，最多人造訪的 article 的排名」之類的需求。

Property 編排應該要能支援用 elasticsearch aggregation 達成上述需求。

:::

## Integration with Cofacts API

- [rumors-api ticket](https://github.com/cofacts/rumors-api/issues/166)

1. Cronjob run every hour updating data with hits / pageviews
    - 可以 [sort](https://developers.google.com/analytics/devguides/reporting/core/v3/reference#sort) by `ga:hit` 把當天內有 hit 的 article 都抓下來
    - upsert Elasticsearch
3. Data loader that loads data from Elasticsearch index above

## Interaction

- 右上角 toggle 圖表收合。
- Desktop Hover/ Mobile Touch 出現切線，並顯示選取日期及對應數據 (TD: 設計稿) 

## Others

### Design alternatives

直接使用 [Embed API](https://developers.google.com/analytics/devguides/reporting/embed/v1)
- Example: https://ga-dev-tools.appspot.com/embed-api/multiple-views/
- 在瀏覽器 load 資料 + 畫圖，不用與 Cofacts API 整合
- 使用 [server-side authorization](https://ga-dev-tools.appspot.com/embed-api/server-side-authorization/) 取得能存取特定 view 的 access token
- Pros
    - 簡單好實作，不用碰到 Cofacts API 與 elasticsearch
    - 可以用它內建的 chart，好像也可以直接接資料進 custom component
- Cons
    - 不確定是否可以把 LINE bot 與 website 兩個不同 view（且不同 filter）的資料畫在同一張圖裡
      - [文件](https://developers.google.com/analytics/devguides/reporting/embed/v1)號稱可以提供「Full access to run your own queries, allowing you to use third-party visualization tools like d3.js and chart.js.」
    - 無 cache 所以 quota 可能會爆（[見下](#API-Quotas)）
      - 因為 filter 不同，畫 line bot 的趨勢與 website 的趨勢，各需要一次 API request
      - 2020 年網站瀏覽高峰：單日 pageview 95K；平常約在 10K 左右
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a0803a5940d21dc1ef0c4567e0740662.png)

:::info
由於 Quota 問題，最後不選擇 Embed API，直接 core reporting API 收入 elasticsearch
:::

### API Quotas

Google analytics [quota & limits](https://developers.google.com/analytics/devguides/reporting/core/v4/limits-quotas)

- 50,000 requests per day
    - 10,000 per view (profile) per day
    - 10 concurrent requests per view (profile)
- 2,000 requests per 100 seconds
- 100 requests per 100 seconds per IP
- 10 requests per second per user
(IP & user can be forwarded via `userIP` or `quotaUser`  parameter)

Quota reset: 0:00 Pacific Standard Time (UTC-8)

https://developers.google.com/analytics/devguides/reporting/core/v3/reference#reducing_dimensions

- The API allows specifying up to 7 dimensions in any one request


Request quota: 10,000 rows per request

> The Analytics Core Reporting API returns a maximum of 10,000 rows per request, no matter how many you ask for. It can also return fewer rows than requested
> [https://developers.google.com/analytics/devguides/reporting/core/v3/reference#maxResults]
> 

### API terms of use

似乎沒有 Youtube API 那麼嚴格
https://developers.google.com/terms

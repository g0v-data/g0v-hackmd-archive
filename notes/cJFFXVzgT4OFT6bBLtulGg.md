---
tags: cofacts, google analytics, GA, GA4, universal analytics, UA
GA: UA-98468513-3
---

# Cofacts GA4 Migration design doc

## :globe_with_meridians: Site

Goal:
- Migrate from Universal analytics to GA4 (with Google Tag Manager)

Tasks:
- [x] Simplify GA integration
    - Remove BE ga tracking RSS endpoint calls, use nginx log instead
    - Remove GA tracking ID, it can be hard coded on tagmanager side; update README and `.env.sample`
- [x] investigate difference in UA and GA4 stats
    - Within error range (<5%)
- [ ] investigate if RSS's `utm_source` still work in GA4
- [x] investigate if article ID in page views can be tracked correctly
  - Leverage [recommended event](https://developers.google.com/analytics/devguides/collection/ga4/reference/events?hl=en&client_type=gtm#view_item)
    - Article detail --> `view_item` w/ article ID + each reply IDs.
    - Reply detail --> `view_item` w/ reply ID only.

### `view_item` event and parameters

When viewing article or reply detail page, [`view_item` event](https://developers.google.com/analytics/devguides/collection/ga4/reference/events?hl=en&client_type=gtm#view_item) will be triggered when the datail page's data is loaded.

When visiting an article page, `view_item` event is fired with the following event fields:

| BigQuery field | Description | Sample |
| -------- | -------- | -------- |
| `items[].item_id` | Viewed article ID or reply ID in the article detail | `IfvpToYBC7Q3lHuUI-c0` |
| `items[].item_category` | type for `item_id`, can be `Article` or `Reply` | `Article` |
| `items[].item_list_name` |  | `article detail` |
| `items[].item_list_id` | The article id of this detail page | `3c8bmf2taopxw` |
| `items[].item_list_index` | Only for replies in article page. Records the position of this reply at the moment, start with 0. | `0` |

When visiting a reply page, `view_item` event is fired with the following event fields:

| BigQuery field | Description | Sample |
| -------- | -------- | -------- |
| `items[].item_id` | Viewed reply ID of the reply detail | `IfvpToYBC7Q3lHuUI-c0` |
| `items[].item_category` | Reply detail only list reply itself | `Reply` |
| `items[].item_list_name` |  | `reply detail` |
| `items[].item_list_id` | The reply id of this detail page | `IfvpToYBC7Q3lHuUI-c0` |

## :robot_face: rumors-line-bot

Goals:
- LIFF: Migrate from Universal analytics to GA4 (with Google Tag Manager)
- Webhook: send events directly to BigQuery

Tasks:
- [x] integrate [BigQuery insert](https://cloud.google.com/bigquery/docs/streaming-data-into-bigquery)
- [x] replace universal-analytics occurrences with own functions
  - inside these functions we still call ua() so that we send to both BQ and GA in the sake time to verify implementation 
- [x] implement tag manager for LIFF
  - send both GA and GA4 using tag manager
      - Same GA4 property for website
  - compare GA & GA4 stats
- [ ] Monitor cost

### `view_item` event and parameters
Identical to website's article detail page.

When viewing article LIFF page, [`view_item` event](https://developers.google.com/analytics/devguides/collection/ga4/reference/events?hl=en&client_type=gtm#view_item) will be triggered when the datail page's data is loaded.

When visiting an article LIFF, `view_item` event is fired with the following event fields:

| BigQuery field | Description | Sample |
| -------- | -------- | -------- |
| `items[].item_id` | Viewed article ID, or ID of replies shown in the article detail | `IfvpToYBC7Q3lHuUI-c0` |
| `items[].item_category` | type for `item_id`, can be `Article` or `Reply` | `Article` |
| `items[].item_list_name` |  | `article liff` |
| `items[].item_list_id` | The article id of this detail page | `3c8bmf2taopxw` |
| `items[].item_list_index` | Only for replies in article page. Records the position of this reply at the moment, start with 0. | `0` |

## :electric_plug: API
Goal: Retireve analytics from BigQuery
- [x] rewrite cron job tp read from BQ instead of GA reporting API

### Details of web

In universal analytics, we extract article ID from URL and content grouping. They are actually not reliable and can [cause weird stuff entering `analytics` index](https://github.com/cofacts/rumors-api/issues/298).

In GA4, rumors-site now leverages [`view_item` event](#view_item-event-and-parameters) with article ID and exposed reply IDs right from GraphQL.

This gives us:

1. Accurate view count for articles
2. Ability to calculate reply view count under each article views


:::spoiler Previous attempt
#### SQL
```sql
SELECT
    event_timestamp,
    event_name,
    items.item_id,
    items.item_category,
    items.item_list_id,
    items.item_list_name,
    items.item_list_index
FROM `..._intraday_...`, UNNEST(items) AS items WHERE event_name = "view_item" LIMIT 1000
```


#### Result
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8a4f257d924bd34db864a3f626f20753.png)
:::

#### `webVisit`, `webUser`

For analytics, we can just count `item_id` to get the view count of that specific article / reply.

In addition, we can also list the view count of a specific reply (in `item_id`, `item_cateogry` being `Reply`), and the view count distribution (can come from reply detail, or from different article details).

##### SQL

```sql
SELECT event_date, item_category, item_id,
  count(*) as webVisit,COUNT(DISTINCT user_pseudo_id) as webUser
FROM `${GA4_DATASET}.events_*`, UNNEST (items)
WHERE event_name = 'view_item'
  AND stream_id = '${GA_WEB_STREAM_ID}'
  AND ${event_date condition}
group by event_date, item_category, item_id
```

##### Verification
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1977e83d8ee27a07f4aec6376a432065.png)

Web visit & web user of SQL result matches looker studio.

Note: we cannot verify reply count because Looker Studio do not allow us to calculate event count under a certain `item_id` (we use "page path" on the screenshot above, which works foraritcle detail page).

#### `liff`
##### SQL
```sql
WITH t AS (
  SELECT 
    event_date, item_category, item_id,
    struct(
      collected_traffic_source.manual_source as source,
      count(*) as visit, COUNT(DISTINCT user_pseudo_id) as user
    ) as liffObj
  FROM `${GA4_DATASET}.events_*`, UNNEST (items)
  WHERE event_name = 'view_item'
    AND stream_id = '${GA_LIFF_STREAM_ID}' -- LIFF stream
  GROUP BY event_date, item_category, item_id, collected_traffic_source.manual_source
)
SELECT event_date, item_category, item_id, ARRAY_AGG(liffObj) AS liff FROM t
GROUP BY event_date, item_category, item_id
```

- We should use `collected_traffic_source.manual_source` to match UA stat
  - The field `collected_traffic_source` is newly added  on 2023/06/05 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b34454736ef95118473a6d06162e438b.png). [Its documentation](https://support.google.com/analytics/answer/7029846?hl=en#zippy=%2Ctraffic-source%2Ccollected-traffic-source) was [not there in 2023 May](https://web.archive.org/web/20230521012849/https://support.google.com/analytics/answer/7029846?hl=en).
  - If we use `traffic_source.source` (cross-channel source), we will include an extra "(direct)" for `tmcheck` with exactly 1 user & 1 view count. Also, it is not populated in intra-day tables.
- To create liff array with counts inside, we must 
  1. first group by (event_date, item_category, item_id, source) to calculate count
  2. then merge liff objects of same (event_date, item_category, item_id) into array `liff`


##### Verification
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_778cb09e4543218bc9375c4052c45da7.png)


### Details of LINE bot

#### `lineUser`, `lineVisit`
##### SQL

```sql
SELECT
  DATE(evt.time, "${TIMEZONE}") as event_date, evt.category AS item_category, evt.label AS item_id,
  count(*) as lineVisit, COUNT(DISTINCT userId) as lineUser
FROM `${LINE_BOT_EVENT_DATASET}.events`, UNNEST (events) as evt
WHERE evt.action = 'Selected'
GROUP BY event_date, item_category, item_id
```

##### Verification

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_39aaf0763d1653ee1f744de1d5f02b7f.png)

Note that UA contains JA bot's group usage, thus has more users. But for less popular messages the view count is somewhat consistent.



### Combined SQL

Constants
- LINE_BOT_EVENT_DATASET
- GA4_DATASET
- GA_WEB_STREAM_ID
- GA_LIFF_STREAM_ID

Parameters
- startDate
- endDate

```sql
WITH
  lineStats AS (
    SELECT
      FORMAT_DATE("%Y%m%d", DATE(createdAt, "+08:00")) AS event_date,
      evt.category AS item_category,
      evt.label AS item_id,
      COUNT(*) AS lineVisit,
      COUNT(DISTINCT userId) AS lineUser
    FROM `industrious-eye-145611.line_bot.events`, UNNEST (events) AS evt
    WHERE evt.action = 'Selected'
      -- Use createdAt so that BQ can select correct partition
      AND createdAt >= TIMESTAMP("2023-05-10T00:00:00.000+08:00")
      AND createdAt <= TIMESTAMP("2023-05-20T23:59:59.999+08:00")
    GROUP BY event_date, item_category, item_id
  ),
  webStats AS (
    SELECT
      event_date,
      item_category,
      item_id,
      COUNT(*) AS webVisit,
      COUNT(DISTINCT user_pseudo_id) AS webUser
    FROM `industrious-eye-145611.analytics_315002472.events_*`, UNNEST (items)
    WHERE event_name = 'view_item' AND stream_id = '3561738274'
      -- Optimize BQ table selection
      AND (_table_suffix between '20230510' and '20230520' OR _table_suffix between 'intraday_20230510' and 'intraday_20230520')
    GROUP BY event_date, item_category, item_id
  ),
  liffStats AS (
    WITH t AS (
      SELECT 
        event_date, item_category, item_id,
        struct(
          collected_traffic_source.manual_source as source,
          count(*) as visit, COUNT(DISTINCT user_pseudo_id) as user
        ) as liffObj
      FROM `industrious-eye-145611.analytics_315002472.events_*`, UNNEST (items)
      WHERE event_name = 'view_item'
        AND stream_id = '4697477273' -- LIFF stream
        -- Optimize BQ table selection
        AND (_table_suffix between '20230510' and '20230520' OR _table_suffix between 'intraday_20230510' and 'intraday_20230520')
      GROUP BY event_date, item_category, item_id, collected_traffic_source.manual_source
    )
    SELECT event_date, item_category, item_id, ARRAY_AGG(liffObj) AS liff FROM t
    GROUP BY event_date, item_category, item_id
  )
SELECT
  event_date AS dateStr,
  LOWER(item_category) AS type,
  item_id AS docId,
  STRUCT(lineUser, lineVisit, webUser, webVisit, liff) AS stat
FROM lineStats
FULL JOIN webStats USING (event_date, item_category, item_id)
FULL JOIN liffStats USING (event_date, item_category, item_id)
```

#### Notes on `_table_suffix`

It is possible that intraday tables contain 2 days.
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_25d3204b869ae50224ee502b7b3509ad.png)

Therefore when we do `_table_suffix` filter, we should handle both the case that has `intraday_` and no `intraday_` together.

## Analysis of LINE bot number drop

### 2203-6-16~22

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a2413b8c758a40f81a7961b441b3b290.png)

Event / category that drops:
- Article / Search
- UserInput / ArticleSearch
- UserInput / MessageType
- Article / Selected
- Reply / Selected
- Group / Leave
- Group / Join

Event / category that does not drop:
- Reply / Type
- ContextProxy / Forward
- Reply / Search
- Tutorial / Step
- Article / NoReply
- Article / Create
- UserInput / IsForwarded
- UserInput / ChatWithBot
- Cronjob / Send Notification

Obsolete: UserInput/Feedback-Vote (LIFF via Tag Manager)


### 2203-5-20~6-22

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_029a6c5b7b24f06d09fd6c8be65425e4.png)

Event / category that drops:

- Article / Search (15% drop)
- UserInput / ArticleSearch (11% drop)
- UserInput / MessageType (1% drop)
- Article / Selected (6% drop)
- Reply / Selected (2% drop)
- Tutorial / Step (Just by 1, omitable)
- Article / NoReply (Just by 1, omitable)
- Group / Join
- Group / Leave

Event / category that does not drop

- Reply / Search
- Reply / Type (Actually BQ has +1 more)
- ContentProxy / Forward (Actually BQ has +1 more)
- UserInput / IsForwarded (BQ Has 1% more...)
- Article / Create (BQ has 1% more...)
- UserInput / ChatWithBot
- Cronjob / Send Notification

Segment by category & message source:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_972833217554ccfc92aa0db94247825a.png)

Dropping combinations
- UserInput / user (just by 0.04%)
- Article / group (by 33%)
- UserInput / group (by 49%)
- Tutorial / user (just by 1)
- Reply / group (by 50%)
- Group / group (by 62%)
- Article / room (by 62%)
- UserInput / room (by 72%)

Not dropping combinations
- Article / user (BQ has 0.04% more)
- Reply / user (BQ has +2 more)
- Cronjob / user

### Focus on 6/10

Check filter alignment: if message source is user, the numbers are accurate
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7e393583c18a77e9e4e5fe299e01f4fb.png)

Group: UA > BQ
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2269d736bc3e0934d311451725fa07ff.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_11a476ae0e988ee14b902957e40c60ec.png)

Even when category / action / label are the same, the count is still missing.
- For the same line of code, sometimes it works, but some times it's not sent.
- Only happens for group chat.

#### Matching logs

One `UserInput / ArticleSearch / ArticleFound` should match to one `console.debug('[GROUP]')`

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4de4a5c71f5d3e50d6516e0d7e158ac7.png)


zh log stream: 127 records
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_583ea8a4f236cdda27e7ce37915eeb8d.png)

zh, en log stream: 261 records (BQ result)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_eb953deb3a43d6661040c3a8129b21e1.png)

zh, en, ja log stream: 401 records (UA result)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_14b5cce9413871986826a8c60277d3bc.png)

:::success
#### Conclusion
The number difference of UA and BQ is due to JA bots not updated to latest version.
- Users of EN & JA bot users almost do not use 1-1; groups are used instead
- We do remember to update EN bot to latest, but not JA bots. JA bots are not connected to BQ at all, hence the difference.
:::
---
tags: cofacts, google analytics, GA, GA4, universal analytics, UA
GA: UA-98468513-3
---

Cofacts Google Analytics 4 migration research
=====

On July 1, 2023, standard Universal Analytics properties will [stop processing new hits](https://support.google.com/analytics/answer/11583528). We should migrate all Cofacts' existing Universal Analytics properties to Google Analytics 4. 

## Existing properties

- website
- website (dev)
- LINE bot
- LINE bot (staging)
- Hackfoldr
- Analytics
- kktix

## Existing integrations

- cofacts.tw/analytics reports - website & LINE
  - Data studio pulls historical data on the fly
- article website trend & chatbot trend
  - website trend uses content grouping to extract article ID
  - pulled data is stored in `analytics` collection
- [Search console integration](https://support.google.com/analytics/answer/10737381?hl=en&ref_topic=12154236)

## Migration of integrations

### Account structure

:::info
[[GA4] Structure your Analytics account](https://support.google.com/analytics/answer/9679158)
:::

- 1 Account
- 1 Property (shares same user base in `rumors-api`) for chatbot & website?
- Data streams
  - 1 stream for all?
    - Separate by host [Hostname dimension](https://support.google.com/analytics/answer/9143382#zippy=%2Cpage-screen)?
  - 1 web stream for website & 1 web stream for chatbot?

Need to consider:
- [GA4 limits](https://support.google.com/analytics/answer/9267744?hl=en&ref_topic=9756175)
- [GA4 dimensions & metrics](https://support.google.com/analytics/answer/9143382)

Event parameter unification across chatbot & website?
  - event name: `select_content`
  - parameters: `item_id` = article or reply ID, `item_category` = article or reply or ...

> Each event name is not necessarily unique (in fact, it’s best practice to reuse the same event name many times, differentiating the event by the parameter values collected). For example, a sign-up might have an event name of sign_up with parameters page_location, product, form_id, and so on. The same event name could (and should) be used on every sign up button across the site (whereas in UA, you would want to use unique event naming for each button).
> -- https://support.google.com/analytics/answer/11986666#event_count&zippy=%2Cin-this-article

### Website
- [Recommended events](https://support.google.com/analytics/answer/9267735): `login`, `search`, `share`, `select_content`, `level_up`
- [No content grouping](https://support.google.com/analytics/answer/10845666?hl=en&ref_topic=10737980), must come up with other way to specify article ID

#### Integration

Datalayer variables and GA [user properties](https://support.google.com/analytics/answer/11396839?hl=en&ref_topic=9756175#user-properties)

#### Parameters

Page view from RSS - manual utm tagging still works https://support.google.com/analytics/answer/11242870

### LINE bot webhook

- [Recommended events](https://support.google.com/analytics/answer/9267735): `tutorial_begin`, `tutorial_complete`

#### Integration

- [Measurement protocol](https://taichunmin.idv.tw/blog/2020-11-21-linebot-google-analytics.html) does not support customized `client_id`
- Use Firebase API? https://firebase.google.com/docs/analytics/events?hl=en&platform=web

#### Parameters

- event category / action / label: change to name & custom params
- Article LIFF traffic source dimensions - manual utm tagging still works https://support.google.com/analytics/answer/11242870

### LIFF

- A web app that already uses `gtag()`
- Uses `gtag('event', 'ViewArticle', {event_category: 'LIFF', event_label: 'articleId'})`
  - action --> GA4 event name
  - category and label --> GA4 event parameters
- Custom event names
  - `ChooseArticle`
  - `ViewArticle`
  - `Comment`
  - `ViewReply`
- UA event names
  - `page_redirect`: tracking LIFF redirect, probably not used by anyone......
  - `page_view`

### Integration

- [UA --> GA4 dimension & metric equivalence](https://developers.google.com/analytics/devguides/migration/api/reporting-ua-to-ga4-dims-mets)
- [Export to BigQuery](https://support.google.com/analytics/answer/9358801?hl=en&ref_topic=12154236) to combine with old data (transformed to bigquery format)?
  - then rewire all analytics charts to BigQuery?

# Alternative: Woopra

## Pros
- Down-to-event reports
- Down-to-user funnel
- Easy tracking API https://docs.woopra.com/reference/intro-http-tracking
- Super clear reporting API https://docs.woopra.com/reference/intro-http-apis


## Cons
- Free quota: 500,000 actions/month
- Free data retention: 90 days
- No ready-made datastudio connector
- No filtering param in reporting APIs
    - Filter are done using UI in reports; reporting API gets data of a specific report ID

# Alternative: Google BigQuery


## Pros
- GA4 also exports to BQ, so that API cronjob can work on BQ only
- Manual 1-time setup for Google BigQuery dataset and tables
  - (Can create a script instead)

## Cons
- Cost?


## Usage

- [Streaming ingestion](https://cloud.google.com/blog/topics/developers-practitioners/bigquery-explained-data-ingestion#:~:text=scan%20partial%20data.-,Streaming%20Ingestion,-Streaming%20ingestion%20supports)
- [Storage write API](https://cloud.google.com/bigquery/docs/write-api#default_stream)
- [NodeJS client lib](https://googleapis.dev/nodejs/bigquery/latest/index.html)
  - [Insert row as stream](https://github.com/googleapis/nodejs-bigquery/blob/main/samples/insertRowsAsStream.js)
  - [createWriteStream](https://cloud.google.com/nodejs/docs/reference/bigquery/latest/bigquery/table#_google_cloud_bigquery_Table_createWriteStream_member_1_)
- [NodeJS client lib for storage APIs](https://cloud.google.com/nodejs/docs/reference/bigquery-storage/latest/bigquery-storage/v1.bigquerywriteclient)

## Pricing
Estimate: 每日 20,000 次 insert，每個 50 byte --> 1MB / day
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0a985be843a6941b2fc50c1b34bdd85f.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b48e3c16809bfa54cfc5082812e17cba.png)

似乎不用擔心價錢。

## Bigquery tables by GA

### Comparison with GA

### `events_*` table
- Data retention: ?


### `events_intradays_*` table
- Data retention: 2 days


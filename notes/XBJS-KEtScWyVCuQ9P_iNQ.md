---
tags: cofacts
GA: UA-98468513-3
---

Cofacts anti SEO-spam mechanism
======

## Previous discussion
- 20221019 [First found](https://g0v.hackmd.io/JPUb9EMATwGLBhgeECAskA#%E6%9C%AC%E9%80%B1%E9%81%95%E8%A6%8F%E6%AA%A2%E8%88%89)
- 20221026 Initial proposal of anti SEO-spam: [CIB processing](https://g0v.hackmd.io/G8JKqoW6T-SpCa704awGsw#CIB-%E8%99%95%E7%90%86)

## Cases

- Note: reporting conversation in spam group is not a SEO spam.
- 同一人一直推交易所相關 https://old.cofacts.tw/articles?searchUserByArticleId=1lgis9b8sl5gp&filter=all&replyRequestCount=1
- https://old.cofacts.tw/articles?searchUserByArticleId=2ker4s3fv5rv2&filter=all&replyRequestCount=1
- https://cofacts.tw/article/pjagx6j66egg

## Milestones and progress
### M1: data prep 

### Schema

- [x] add blocked status for articles
- [x] add migration script to fill in status for existing articles

### API
https://github.com/cofacts/rumors-api/pull/293
- [x] mutation API for articles should fill in status correctly
- [x] can list article by status

### M2: Script for setting article status

### API

https://github.com/cofacts/rumors-api/pull/295
- [x] blocking user also turns their article to blocked status
    - List blocked article URLs so that we can [remove those pages from Google](https://support.google.com/webmasters/answer/9689846?hl=en)
- [ ] able to block individual article (optional, need reason)
    - 先不做 [name=bil]

### M3: Hide blocked article for non logged-in users

### Website
- [x] Show "Login to see text" for blocked articles if the user is not authenticated
  - Page title would be just "Suspecious message"
  - This should stop server from rendering text, thus no SEO for the spammer
  - Show blocked reason ? (Optional)
    - 先不用 [name=bil]
- [x] Do not list blocked articles in article list
    - Already done from API side
- [x] Implement [Robots meta tag](https://developers.google.com/search/docs/crawling-indexing/block-indexing) on blocked articles to prevent Google Search from indexing the article (`noindex` specifically)
- [x] Add [`rel="ugc"`](https://developers.google.com/search/docs/crawling-indexing/qualify-outbound-links) to all article hyperlinks
    - So that content farms don't get their rank boosted due to Cofacts referring to their site

### M4: Allow reporting SEO spammer articles

### Website
- [x] Add flag button to article
  - 「⋯」button on the right of "Share"

### Report form and spreadsheet
- [x] Make the form support article

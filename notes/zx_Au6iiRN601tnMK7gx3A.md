---
tags: cofacts
GA: UA-98468513-3
---

Badge System
======

## Previous discussion
https://docs.google.com/presentation/d/1ZmQyeSRv_cY3NXtDPrz1IQDUT-C-EGbi/edit#slide=id.p1

## Milestones and progress

### M1: data prep 

#### Schema
- [ ] add badges for user  https://github.com/cofacts/rumors-db/pull/55/

#### Release

Not yet
- Working schema
- Existing document fields are properly filled
- New document fields are properly filled
- Hidden reply rquests does not increase replyRequestCount
- Hidden article reply feedback does not increase feedbackCount



### M2: API for receive certification 

#### API

- [ ]  add certification APIs for `/badge` for 3rd party orgnization to push update the badge holder's information
control with Cloudflare zero trust 
https://github.com/cofacts/rumors-api/pull/263



#### Release

- Block known violating users after release
    - Blocked user will start having `isUserBlocked` cookie in their browser
- API & website still gives hidden items as before

### M3: Frontend display


#### Website

- [ ] User page badge display
- [ ] User page badge list
- [ ] rumor page user icon border


#### Release
- Should display `BLOCKED` items only for blocked users, even after they logout!


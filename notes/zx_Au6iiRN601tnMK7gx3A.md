---
tags: cofacts
GA: UA-98468513-3
---

Badge System
======

## Previous discussion
https://docs.google.com/presentation/d/1YkJ76WEANq-SopKfgY8KQfLuNBVYKJp_/edit#slide=id.g317f579cd8a_0_0

## Milestones and progress

### M1: data prep 

#### Schema
- [x] add `badges` table for badges information (cofacts maintain)
- [x] add `badges` in `users` table
https://github.com/cofacts/rumors-db/pull/74
- use `bordaerImage` instead of `color`


#### Release


- Working schema



### M2: API for receive certification 

#### API


Implement the following endpoint using feTS & OpenAPI. The path hierarchy is designed for easier management using Cloudflare.

- `/badge` series: 
    - POST `/badge/award`: for external source (i.e. TFC) to award a badge to a user through API.
        - `userId`
        - `badgeId`
        - verify `requeat-user-id` vs issuer in `badges`

- add `issuers` to `badges` for verify if the source match the authorized issuer.
    - `issuers` should be array of string , for OpenAPI or feTS will using different `request-user-id`. 
    - change cofacts.cloudflare.com login id for EJ (to jhk482001@gmail.com)

- badge image -> 200x200px is enough.

#### Release

Not yet
- TBD


### M3: Frontend display


#### Website

- [ ] User page badge display - components/ProfilePages/ProfilePages.js
- [ ] rumor page user icon border - 
- [ ] 改成用background with radius, allow to configure background image url 


#### Release
- Should display `BLOCKED` items only for blocked users, even after they logout!


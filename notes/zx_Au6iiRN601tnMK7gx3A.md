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
        - verify `request.userId` vs issuer in `badges`

- add `issuers` to `badges` for verify if the source match the authorized issuer.
    - Get currently logged in user or service token with `request.userId`
      - Each handler function in feTS gets a `request` object
      - On staging & production environment, `useAuth` middleware under `src/adm/util` reads the access token from Cloudflare Access and populates `request.userId`
      - If the admin user is logged in as a user, email is set to `request.userId`
      - If the admin API is accessed via service token, the ID of the service token is used as `request.userId`
    - On each Badge, `issuers` should be array of string , for OpenAPI or feTS will using different `request.userId`. 
    - change cofacts.cloudflare.com login id for EJ (to jhk482001@gmail.com)

- badge image -> 200x200px is enough.

#### Release


- TBD


### M3: Frontend display


#### Website

- [ ] User page badge display - components/ProfilePages/ProfilePages.js
- [ ] rumor page user icon border - AppLayout/Widgets/Avatar.js
- [ ] 改成用background with radius, allow to configure background image url 
- [ ] showBadgeDialog.js


#### Release
- Should display `BLOCKED` items only for blocked users, even after they logout!


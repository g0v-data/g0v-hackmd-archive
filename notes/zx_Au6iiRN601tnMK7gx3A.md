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

#### Release


- Working schema



### M2: API for receive certification 

#### API


Implement the following endpoint using feTS & OpenAPI. The path hierarchy is designed for easier management using Cloudflare.

- `/badge` series: designed for Cofacts automations, including
    - POST `/badge/award`: for external source (i.e. TFC) to award a badge to a user through API.
        - userId
        - badgeId
    - GET `/badges`: get badge list and it's information for front-end display.
    - POST `/moderation/aiReply`: regenerate AI reply. Map to current `genAIReply` script.
- `/badge` series: reserved for Badge operations (TBA)
- Others: feTS provides `/docs` for Swagger UI, and `/openapi.json` for OpenAPI spec file.

We log all access to the API to console. Fields to be included:
- The invoked endpoint
- `user` - who initiated the request. Can be:
  - email, when [identity-based authentication](https://developers.cloudflare.com/cloudflare-one/identity/authorization-cookie/application-token/#identity-based-authentication) is used
  - [Client ID of the service token](https://developers.cloudflare.com/cloudflare-one/identity/authorization-cookie/application-token/#service-token-authentication)
- request payload

- [ ]  add certification APIs for `/badge` for 3rd party orgnization to push update the badge holder's information
control with Cloudflare zero trust 


#### Release

Not yet
- TBD


### M3: Frontend display


#### Website

- [ ] User page badge display
- [ ] User page badge list
- [ ] rumor page user icon border


#### Release
- Should display `BLOCKED` items only for blocked users, even after they logout!


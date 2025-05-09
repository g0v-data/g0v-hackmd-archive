---
tags: cofacts
GA: UA-98468513-3
---

# Cofacts API access management

:::info
Related doc: [userId & appId management proposal](https://g0v.hackmd.io/ZcoUOX_-RQSkJyl5xz4_Zg)
:::

In order to ensure the capacity of Cofacts API server is provided to known services (including Cofacts' own websites, chatbots, and 3rd party services), we should limit the access of anonymous requests to the API server.

However, this is not an easy task -- given the fact that we do have public client-side services like Cofacts website, API must be exposed to these services. However, we can take measures to limit the exposure.

## Connections among apps

(圖: rumors-api <> app server <> browser / LINE server / scripts, etc)

Existing 1st party apps / clients
- ~~rumors-ai: secret~~
- rumors-site: id + domain
- community-builder: (id + domain)
- rumors-line-bot: secret, proxied GraphQL (LIFF), analytics Google sheet script
- ~~rumors-fb-bot: secret~~
- 檢舉表單: (can use secret)

To be added:
- meiyu: secret
- drmessage: secret

Traffic can go from
- cofacts-api.g0v.tw: Go through A record, NOT defended by Cloudflare
- api.cofacts.tw: Go through and defended by Cloudflare
- Directly within docker network: Production LINE bot, for better file transfer

## Server-to-server communication

### Traffic management

Redirect all traffic from `cofacts-api.g0v.tw` to `api.cofacts.tw`; and `cofacts.g0v.tw` to `cofacts.tw`
- don't need to manage g0v domains
- all traffic on Cloudflare
- can hide IP

### Service token

Cloudflare has a upper limit of 50 service tokens.

Dispatch Cloudflare Service tokens to:
- Cofacts automation (takedown) --> already there
- Cofacts site
- Cofacts LINE bot
- 3rd party applications
  - Meiyu
  - Dr.Message
  - LINE 訊息查證
  - TFC: 已經有了一把 service token，可重複使用

Other researchers: can [use snapshot on HuggingFace](https://github.com/cofacts/opendata/issues/24)

Servers need to use service token to access:
- api.cofacts.tw/graphql
- dev-api.cofacts.tw/graphql

We can still allow direct browser access to GraphQL (GraphiQL) after then "login"
- This is achieved by setting an "allowed" Cloudflare policy for "everyone"
- User will be prompted a login screen, but anyone can access
    - each successful login takes up one of 50 user seat; seat expire in 1 month


### Mapping to `appId`

- Cofacts API translates [`cf-access-jwt-assertion` header](https://developers.cloudflare.com/cloudflare-one/identity/authorization-cookie/validating-json/#verify-the-jwt-manually) from Cloudflare to corresponding `appId`.
- The header is [a JWT](https://developers.cloudflare.com/cloudflare-one/identity/authorization-cookie/application-token/) whose `common_name` is the Client ID of the service token.
- We can maintain a JSON or YAML config to map these service token Client ID to appId in Cofacts DB.
- We can refer to https://github.com/cofacts/rumors-api/blob/master/src/adm/util.ts for service JWT decode logic.
- On staging environment where we allow requests with no service tokens, we map the activity to the same special appId `DEVELOPMENT_BACKEND`

:::spoiler Old proposal

(圖：backend apps <> rumors-api)

Block requests with no `x-app-id`, `x-app-secret` or values not in the whitelist above.

### App management

- Lookup is per API request, must be fast and efficient
- Can generate app credentials by hand
    - As long as we don't want to go as far as X.509 key generation...
- Not many app, can tolerate server restart
    - Can consider using file instead of DB
    - Just read file once at app start

Consider simple YAML:

Refactor [checkHeader](https://github.com/cofacts/rumors-api/blob/master/src/checkHeaders.js)

- As-is: hard-coded if-else and environment variables
- To-be: loop through a config YAML file that is bind-mounted to the container.


```
---
- headerAppId: ""
  headerAppSecrets: [""]
  dbAppId: DEV # merge DEVELOPMENT_FRONTEND and DEVELOPMENT_BACKEND
  domains:
  - "http://localhost:3000"
  enableMutation: true
```

Use YAML + json schema

```
---
type: object
required:
- appId
properties:
  appId:
    type: string
  appSecret:
    type: string
  enableMutation

```

### Identifying apps

- Use API keys

### [Optional] Avoid token leakage

The above method will send API keys (secret) in every request. Therefore this is more likely to be leaked.

We can consider tech like request signing so that the secret is not send on the wire for every request; but is used in signing the content.

#### Simple [request signing](https://blog.andrewhoang.me/how-api-request-signing-works-and-how-to-implement-it-in-nodejs-2/)
- client ID + secret
- Server holds all pair of client ID + secret
- Client: Provide client ID + signed request
- Server: find secret w/ client ID and try recreating the signature



Example: [LINE messaging API's signature](https://developers.line.biz/en/docs/messaging-api/receiving-messages/#verifying-signatures)
- Fixed algorithm
- No safe headers
- Don't base64 lots of stuff
- Does not defend replay attacks
- Problem: user ID is not part of signed payload, so it is still possible that the request is spoofed
    - This should be as difficult as a replay attack, though

#### Advanded: HTTP signature spec
- HTTP signatures - https://datatracker.ietf.org/doc/html/draft-ietf-httpbis-message-signatures
    - Flexible algorithm and header design
    - Medium: https://technospace.medium.com/ensuring-message-integrity-with-http-signatures-86f121ac9823

#### Defending replay attacks
- Attack only feasible in MITM attacks; not easy in HTTPs environments and server-server scenario.
- Add timestamp / nonce to the header to avoid [replay attacks](https://github.com/apache/apisix/issues/5784)

### Alternative: Implement using Cloudflare Zero Trust

- A function under an account, not under a domain
- Define Cofacts API as a (self-hosted) [application](https://developers.cloudflare.com/cloudflare-one/applications/configure-apps/) to be protected
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5186422240d549136be1b975553c6f2c.png =x300)
    - Can only setup domain under the account
        - Needs GGM's help on setting this up, because cofacts.tw is under his Cloudflare account
    - Sets [access policy](https://developers.cloudflare.com/cloudflare-one/policies/access/#actions) to block access without service tokens ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_08d9c58e50edc53b4c3979684c966e74.png)

- Create service tokens and send them to downstream (downstream bots, researchers, etc)
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_53a5cbbe3dd358ebe33d522969fd6919.png =x300)
    - [Max 50 service tokens](https://developers.cloudflare.com/cloudflare-one/account-limits/#:~:text=Service%20tokens%20count)
    - Token duration: min 1 year, max non-expiring
- Access without service token: ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d36a8362a98c2fc155e2632e744342e8.png =x300)
- Protected application (rumors-api) gets an [application token](https://developers.cloudflare.com/cloudflare-one/identity/authorization-cookie/application-token/#service-token-authentication) with `common_name` being the access client ID.
:::

## Browser <> API

### Problem of APIs exposed to browsers

- 防君子不防小人，因為爬蟲可以假冒來自 community builder / website 的 request [name=orz]
- 可以看 IP，太集中就是 bot [name=nonumpa]
    - 即使不擋也可以觀察狀況 [name=bil]
    - 用 bot 爬網站之類的違反使用者條款 [name=orz]
- 可以看 query? 因為網站只會做某些 query [name=orz]

:::spoiler Previous proposals

### Limiting exposed API

Cofacts website proxies API server and perform server-to-server communication using app secret. No API connections without app secret is allowed.

Cofacts website can limit the access of exposed API with React server components or GraphQL persisted operations.

- rumors-site talk to rumors-api using app-secret 
        - rumors-site use React server component to do all server-side communication
        - GraphQL not directly exposed, only rendered server components
        - no client side apollo-client anymore
        - Alternative: use [persisted operations](https://the-guild.dev/graphql/yoga-server/docs/features/persisted-operations) + block non-persistent queries on rumors-site GraphQL proxy to rumors-api.
- community builder
    - Rewrite API fetching using persisted operations or server components
    - Login mechanism? https://www.cloudflare.com/products/zero-trust/access/

#### Blocker of React server components

- Material-UI is not compatible with Next.JS 13 app directory: https://github.com/mui/material-ui/issues/34905
    - Can mark Material UI as client-side, but have FOUC
- Not sure if GraphQL requests are properly [deduped on server components](https://beta.nextjs.org/docs/data-fetching/fundamentals#automatic-fetch-request-deduping)

### Proxy issue: passing login cookie around

- Similar to option 3 in [Google Firebase doc](https://firebase.google.com/docs/auth/web/redirect-best-practices?hl=zh-tw#proxy-requests)
- proxy GraphQL API under site domain
    - first request to site can also have login cookie
    - cookie from browser will be proxied to API server under proxy
    - set-cookie from API server will be proxied to the browser
- change redirect URI from api.cofacts.tw to `cofacts.tw/api/`

:::

### No more "browser apps"

We will remove the concept of [browser apps](https://g0v.hackmd.io/ZcoUOX_-RQSkJyl5xz4_Zg#Identifying-the-app-and-user) -- at the end of the day, only "backend apps" (with service token auth) are allowed.

For rumors-site:
- Cofacts website manages its own user
    - Cofacts API login / registration endpoints moved to rumors-site
    - Cofacts website needs a database (MongoDB or CloudSQL) for users
    - Social login related keys should be removed from rumors-db
- Cofacts website users are treated also as [backend app users](https://g0v.hackmd.io/ZcoUOX_-RQSkJyl5xz4_Zg#Backend-app-user-%E7%9A%84%E9%9C%80%E6%B1%82).
    - `cofacts.tw/users?id=xxx` can still use app user id; it searches database and resolve to real id
- Cofacts website talks to API using service token.
    - Short term: spin up an rumors-api proxy under `/api`, the proxy talks to rumors-api via service token
    - Long term: use server action to do GraphQL, so no public access to full GraphQL server --> eliminates GraphQL complex query attack

For community builder:
- cofacts.github.io/community-builder should redirect user (with javascript) to a new Cloudflare domain
  - host the static site on Cloudflare workers?
- Directly apply auth policy that allows anyone (it takes up Cloudflare zero trust user seats, but seats expire in 1 month) to access
  - rumors-api can allow authenticated people

:::spoiler Auth service choice
- rumors-site
    - Nextauth
    - Ory kratos endpoints for login session (cookie) and social logins
        - endpoint should be under website's domain for cookie session
    - userId: kratos ID
    - New website users:
        - register on kratos
        - get kratos ID and send to rumors-api
        - rumors-api generates `_id` for new users
        - set social profile if applicable on kratos
    - Existing website users: don't change ID
        - so that they can still be accesible via `?userId=xxx` (possibly?)
    - Other authentication as a service
        - Auth0
            - Free plan: 7,000 active users, 2 social connections
            - Essential: USD 23/month
            - Social covers Goolgle, facebook, twitter, github; as well as LINE
            - Non-profit offers: 50% savings https://auth0.com/nonprofits
        - Firebase authentication
            - [Free](https://firebase.google.com/docs/auth#no_cost_spark):  3,000 daily active users (24hr)
            - Social covers Google, [Facebook](https://firebase.google.com/docs/auth/web/facebook-login), Twitter, Github
            - [FirebaseUI Auth (with UI)](https://firebase.google.com/docs/auth/where-to-start#new-apps) or Firebase Authentication SDK
            - ID token based authentication
                - Client gets ID token before making requests https://firebase.google.com/docs/reference/js/v8/firebase.User#getidtoken
                    - 如果到期好像要整頁 refresh?
                - API server verify ID tokens https://firebase.google.com/docs/auth/admin/verify-id-tokens
                - [ID token 一次一個小時](https://firebase.google.com/docs/auth/admin/manage-sessions)
                - UI 一定要先啟動、拿到 ID token 之後才能打 auth related API
                - Need [additional handling](https://firebase.google.com/docs/auth/web/redirect-best-practices#proxy-requests) for browsers blocking 3rd-party cookies
            - [Session cookie based authentication](https://firebase.google.com/docs/auth/admin/manage-cookies)
                - ID token 在 client gen 完之後傳給後端，傳完後 client side 立即登出 client app
                - 後端用 Firebase admin SDK 呼叫 `createSessionCookie()` 產出 session cookie 設給 UI (httpOnly)
                - 每次 API 呼叫時驗證 session cookie
                - cookie 到期：5min ~ 2weeks
        - AWS Cognito
            - JS SDK - https://github.com/aws-amplify/amplify-js/tree/main/packages/amazon-cognito-identity-js
        - [Cloudflare Zero Trust Identity](https://developers.cloudflare.com/cloudflare-one/identity/)
            - 同時允許 One-time pin, 各種 IdPs, 以及 service token (limited)
            - 50-user free
- rumors-api
    - remove passport.js and social login
    - remove app-id related logic
:::

## Rollout plan

1. Traffic management
    - Announce change to 301 redirect `cofacts-api.g0v.tw` and `cofacts.g0v.tw` to `cofacts.tw` domains
    - Apply 301 redirect ([sample](https://github.com/g0v/domain/blob/8890ddde14f49e83addd79bdf0c5c4288fdf6eec/g0v.dev/g0v.dev.json#L6))
    - 至此，所有流量均可由 cloudflare 掌控

2. Implement service token ID --> appId logic
    - Apply to Cofacts services first
    - Then send to downstream and ask them to change
    - We still allow people to bypass service token for now
    - 至此，當匿名流量過高，我們可以暫時拒絕無 service token 的 traffic，網站無法使用但 LINE bot 仍然可查詢

3. Migrate social login to rumors-site and its DB
    - 大工程（可能只比重寫網站小）
    - 可合併 user query 與一般 query，減少 request 數
    - API auth logic 簡化
    - 可實作較為安全的登入後才連結其他 social platform 之功能

4. Setup API proxy for rumors-site and community-builder
    - 至此，所有 client 應該都用 token 與 API 溝通了

5. Remove service token bypass
    - API 很難被打壞，因為根本沒辦法直連 API
    - 但即使如此，DDoS 網站本身應該還是會爛掉

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

existing 1st party apps / clients
- rumors-ai: secret
- rumors-site: id + domain
- community-builder: (id + domain)
- rumors-line-bot: secret, proxied GraphQL (LIFF), analytics Google sheet script
- rumors-fb-bot: secret
- 檢舉表單: (can use secret)

to be added:
- meiyu: secret
- drmessage: secret

## Server-to-server communication

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

:::info
TBA:
- Usage logging
- Detailed access control on service tokens
:::


## Rollout

Implement & deploy w/ "development frontend" & "development backend" fallback: ASAP
Remove "development *end" fallback on production: end of Feb 2021


## Browser <> API

### Problem of APIs exposed to browsers

- 防君子不防小人，因為爬蟲可以假冒來自 community builder / website 的 request [name=orz]
- 可以看 IP，太集中就是 bot [name=nonumpa]
    - 即使不擋也可以觀察狀況 [name=bil]
    - 用 bot 爬網站之類的違反使用者條款 [name=orz]
- 可以看 query? 因為網站只會做某些 query [name=orz]

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

:::danger
Blocker of React server components

- Material-UI is not compatible with Next.JS 13 app directory: https://github.com/mui/material-ui/issues/34905
    - Can mark Material UI as client-side, but have FOUC
- Not sure if GraphQL requests are properly [deduped on server components](https://beta.nextjs.org/docs/data-fetching/fundamentals#automatic-fetch-request-deduping)
:::

### Proxy issue: passing login cookie around

- Similar to option 3 in [Google Firebase doc](https://firebase.google.com/docs/auth/web/redirect-best-practices?hl=zh-tw#proxy-requests)
- proxy GraphQL API under site domain
    - first request to site can also have login cookie
    - cookie from browser will be proxied to API server under proxy
    - set-cookie from API server will be proxied to the browser
- change redirect URI from api.cofacts.tw to `cofacts.tw/api/`


### Alternative: Treating all apps equal

Another topic would be if we should treat [browser apps and backend apps](https://g0v.hackmd.io/ZcoUOX_-RQSkJyl5xz4_Zg#Identifying-the-app-and-user) equally -- that is, 
- Cofacts website manages its own user
    - Cofacts API login / registration endpoints can be removed
- Cofacts website users are treated also as [backend app users](https://g0v.hackmd.io/ZcoUOX_-RQSkJyl5xz4_Zg#Backend-app-user-%E7%9A%84%E9%9C%80%E6%B1%82).
    - `cofacts.tw/users?id=xxx` can still use app user id; it searches database and resolve to real id ()
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

---
tags: cofacts
---

# Cofacts LIFF redesign

## Implementation

LIFF 實作為一 SPA：
- 使 HTML 最簡化，加速 server --> LINE initial payload 的 loading
- Hosting: line bot server `/liff` 
  - [Proxies to svelte dev server](https://github.com/vagusX/koa-proxies) on dev; use [koa-static](https://github.com/koajs/static) to serve built file.
  - change package.json to include [build](https://devcenter.heroku.com/articles/nodejs-support#customizing-the-build-process) script that runs both LIFF build scripts and server-side babel script.
- (optional) 使用 cloudflare CDN cache deliver JS & CSS assets

## LIFF <> Chatbot server communication

結合 liff.js 的 server 資料（user id）與 chatbot server 資料 (nonce in URL param) 來驗證使用者資料。

0. In user's redis session, generate a `nonce` for current session and change `nonce` as new session starts (`issueAt` changes)
1. User clicks LIFF URL with [URL path](https://speakerdeck.com/line_devday2019/whats-new-in-line-front-end-framework?slide=22) and `nonce` param, LIFF pops up
2. LIFF invokes GraphQL APIs with `userId` in `liff.init()` response and the `nonce` in AJAX headers and get required data / perform mutation
3. When user perform action that brings themselves back to chatbot, LIFF will invoke `liff.sendMessage` with special pattern (Readable prefix, or flex message ([???](https://developers.line.biz/en/reference/liff/#send-messages))) --> 因為要有 text message 才能 reply

:::danger
nonce 打算用 JWT 取代掉。JWT 每次產生 LIFF 按鈕時會蓋一個新的，裡面有：
- `exp`: 每次產生 LIFF 按鈕的時候產生，擋住太久以前的 LIFF，控制 JWT leak 的 impact
- `sessionId`: server 可跟當下 redis `context.data.sessionId` 比對是否屬於同一個 session
- `sub`: user Id，API 將以此判斷是哪一位使用者。LIFF 會拿 `sub` 與 `liff.getProfile()` 結果比對。
:::

## LIFF UI

- Tech stack: try Svelte first, use CRA as escape hatch
  - [Material UI library]()
  - Typescript support: [within components & within ts lib files](https://github.com/sveltejs/svelte/issues/1639), but no typecheck in UI libraries though.
- Svelte with its own package.json under `/liff` folder
- Routes:
  - `/liff/source`: asking message source (LIFF asking source)
  - `/liff/reason`: asking submission reason for new messages (Reason LIFF)
  - `/liff/feedback`: submitting feedback for article-reply (Feedback LIFF)
  - `/liff/sent`: list of messages previously sent to chatbot (Messages LIFF)
- ~~Use CRA + Typescript! (LIFF v2 SDK [supports Typescript](https://speakerdeck.com/line_devday2019/whats-new-in-line-front-end-framework?slide=25) as well)~~
- During development, we may need to setup `PUBLIC_URL` and/or `WDS_SOCKET_PATH` so that `/liff` can be properly hot-reloaded 
- In production, we need to [configure it](https://create-react-app.dev/docs/deployment#building-for-relative-paths) so that it can serve under `/liff`

## LIFF 互動 & state diagram

- [#144 Revamp LIFF with FE framework](https://github.com/cofacts/rumors-line-bot/issues/144)
- [#145 Update article source wordings](https://github.com/cofacts/rumors-line-bot/issues/145)

https://docs.google.com/drawings/d/1sSzI0PSggkA3PPP99Nl18H4zMO4lk-2y5s7dGRNJwAE/edit

<img src="https://docs.google.com/drawings/d/e/2PACX-1vTeXGMSaPQadbe7kXay6n0vWWKHbLrMWtNB1xWuuH7SEO9KlPjDSML_TZgcuk6_kpsGLwM6YlosB1MI/pub?w=1428&amp;h=1057">

https://g0v.hackmd.io/6f12uznTQjCDRAKRyPOSxw?both#LINE-bot-%E4%BA%92%E5%8B%95%E4%BF%AE%E6%94%B9


## LIFF API

- Endpoint: `/graphql`
- Requires `Authorization` header with `basic <base64 of "user id:nonce">`; returns 401 if not nonce not match

:::danger
想改成 `Authorization: bearer <JWT>`
:::

```graphql=
type Query {
  # Current user's chatbot context
  context: Context
  
  # TODO: Implement after database is established
  readArticleIds(skip: Int, limit: Int): [String]
}

type Context {
  state: String
  issuedAt: Int
  data: StateData
}

type StateData {
  searchedText: String
  selectedArticleId: String
  selectedArticleText: String
  selectedReplyId: String
}

type Mutation {
  # Submits searchedText in context, then store articleId to context.
  # Returns created article ID.
  submitArticle: ID
  
  # Submit empty reply request to the articleId in context.
  submitReplyRequest: boolean
  
  voteReply(vote: FeedbackVote): boolean  
  
  # TODO: Implement after database is established
  setViewed(articleId: String!): boolean
}

enum FeedbackVote {
  UPVOTE
  DOWNVOTE
}
```



## Project folder restructure

現在有點亂，加上 LIFF ＆ chatbot 共用的 file 之後，可能會更亂。
因此做下面的改動：

- `/liff`: 資料夾位置不變，但裡頭改成 svelte client-side app config w/ Webpack
- `/i18n`: 資料夾位置不變。
- `/src`: Chatbot server 本體。
  - `index`: koa server 進入點。
  - `handleInput`, `handlers/`, `checkSignagureAndParse`, `lineClinet`: 移動到 `/src/webhook`，亦即 LINE messaging API webhook。`/src/webhook/index` 擺放目前在 `src/index` 裡的 `singleUserHandler()`、`groupHandler()`、`processText()` 邏輯，使 koa server 進入點不要放太複雜的 middleware logic.
  - 新增 `src/graphql` 放 Apollo server 相關 typedefs。`src/graphql/index` 為 GraphQL API request handling middleware。
  - `ga`, `gql`, `redisClient`, `rollbar`: 是 `graphql` 與 `webhook` 共用的東西，移動到 `/src/lib`

## Setup on LINE side

LIFF 2.0 w/ LINE login-capable channels


## Design alternatives - 沒採用的設計

### LIFF as server-rendered pages

Pros:
- Minimal network requests when server load is low

Cons:
- In article list, we still need to combine API data with the list from server. However, server-rendered pages are hard to "bootstrap" with javascript, not to mention re-render and combine AJAX data.
- If we go for full server-side (i.e. read article data through API on chatbot server) we will put too much burden on chatbot server. Chatbot server is already busy...

CSRF: 不是用來防偽造身份打 api 的
只能防跨網域
nonce = 暫時性密碼是正解

### Deploy LIFF elsewhere

現況就是 LIFF 在 github pages, chatbot 在 Heorku。

優點：打開 LIFF 不佔 chatbot 資源（但 API 還是會）
缺點：
- LIFF 與 chatbot 要分開 deploy，忘記的話版本會對不起來
- API 要開 CORS 才能讓 LIFF 讀到
- 開發時要另外開 static server 且還要加掛 https（LIFF 需要 https）

### CRA instead of Svelte

Pros
- We all know how to set it up
- Typescript support
- We have experience handling React's browser compatibility on old mobile browsers

Cons
- Bundle size is expected to be larger
- More code
- CRA proxy 有點複雜（見下）

### During development, use CRA's built-in web server + proxy

一樣是要同時開 CRA 與 chatbot server，CRA 也有[內建 proxy](https://create-react-app.dev/docs/proxying-api-requests-in-development/)，由 CRA webpack-dev-server 的 express 來主導。

但這樣一來，`/` 也會是 CRA host 的 index.html，而且這樣的行為與 production 下，server & LIFF 的主客關係相反，讓開發變得有些複雜。

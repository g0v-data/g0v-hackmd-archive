---
tags: cofacts
---

[Rumors-api](https://github.com/cofacts/rumors-api) `userId` & `appId` management proposal
=====

This document explains the machanism of `userId` & `appId` in rumors-api codebase, and proposes a change to the status quo.


[TOC]

## Background

[rumors-api](https://github.com/cofacts/rumors-api) is designed to support multiple *apps*, or "clients" in clinet/server model. The LINE bot server, [rumors-line-bot](https://github.com/cofacts/rumors-line-bot), is one of the app; [rumors-site](https://github.com/cofacts/rumors-site), the reply-editing application, is another.

When different apps invoke mutative rumors-api APIs to create object entities (articles, replies, feedbacks, etc), the API records the corresponding `appId` and the `userId` provided by the app to the created entities. In [the database schema](https://g0v.hackmd.io/@mrorz/S1caurZq8), you can see that almost every index has `userId` and `appId` fields; they can be also seen in nested objects as well, such as `replyrequests.feedbacks`, `articles.articleReplies`, etc.
 
### Identifying the app and user

`rumors-api` provides 2 ways for apps to identify themselves and the current user when making requests to its GraphQL API:

| App type  | Browser apps<br><small>(rumors-site)</small>  | Backend apps<br><small>(rumors-line-bot)</small> |
| --- | --- | --- |
| [Identifying App](https://github.com/cofacts/rumors-api/blob/master/src/checkHeaders.js)  | HTTP header `x-app-id`  | HTTP header `x-app-secret` |
| [Specifying user](https://github.com/cofacts/rumors-api/blob/master/src/index.js#L86-L88) | Login cookie in `cofacts-api.g0v.tw` domain, managed by rumors-api | `?userId=xxx` query param |
| Forgery protection | CORS origin & appId mapping | Shared secret between the app and rumors-api |

:::info
Lucien:
直接用 domain 就好，這樣應該就不用 x-app-id

orz
對耶

Lucien
啊你是 for CSRF 嗎

orz
喔對齁。對對。

Lucien
了解，這樣確實要 HTTP header。
:::

#### For Backend Apps

When backend apps (like rumors-line-bot) talk to rumors-api, it should
- Attach HTTP header `x-app-secret` with specified value
- Specify desired `userId` denoting the current user performing the action

The `x-app-secret` acts like an secret API key. If the given `x-app-secret` maps any known app secret, rumors-api will set `appId` corresponding to the secret, and take whatever `userId` the backend app provides in `/api/graphql` URL path.

#### For Browser Apps

When browser apps (like client-side render part of rumors-site) talk to rumors-api, it should provide `x-app-id` HTTP header.

When receiving `OPTION` request with `x-app-id`, rumors-api will set `access-control-allow-origin` to the domain corresponding to that `appId`, allowing subsequent cross-origin AJAX calls from the browser app.

##### Security aspect: is it possible to forge `appId`?

Although `rumors-api` takes in the public, unencrypted `x-app-id` directly from the client side, `appId` forgery can still be prevented by combining HTTP header `x-app-id` and CORS origin together. The HTTP header limits the attacker to use AJAX, and the CORS origin blocks the attack from any domain other than the one that corresponds to the `appId`.

##### Authentication of Browser Apps

On the contrary to backend apps, `userId` of browser apps are **managed by rumors-api**. This is designed so that browser apps don't need to implement their own authentication.

Rumors-api expect browser apps redirect the user to one of its [login endpoints](https://github.com/cofacts/rumors-api/blob/master/src/auth.js#L237-L239) (`/login/facebook`, `/login/twitter`, `/login/github`), finish OAuth login flow, and redirect back to the browser app. After that, whenever the browser app makes request to rumors-api, it uses the login session to determine the `userId` of current API call. The login session cookie is managed by rumors-api itself.

### Resolving user in `user` field

Many object type from rumors-api, including `Article`, `ArticleReply`, `ArticleReplyFeedback`, has a `user` field indicating the author of that object.

The [user field resolver](https://github.com/cofacts/rumors-api/blob/master/src/graphql/models/User.js#L103-L120) is designed so that:

- If the object's `appId` is from a *browser app*, it resolves to the  corresponding document in `users` Elasticsearch index.
- If the object's `appId` is from a *backend app* and has the same `appId` currently accessing the API,  it resolves to `{ id: <userId of the app> }`.
- Otherwise, resolve to `null`.

This ensures that
1. Users managed by rumors-api (i.e. users used by browser apps) can be accessed openly by any app (even when no `appId` is specified at all), since they are physically stored in the database under our control, and we leak no personal data in users' ID and any public fields.
2. For user managed by backend apps, rumors-api has nothing but the user ID stored on the object. Since each backend app manages their own `userId`, we want to prevent `userId` from one backend app leaks to other apps, just in cast that any backend app uses personal data (such as plaintext email) directly as user ID. We still expose `userId` to the backend app that created the object, so that the backend app can still bridge between the objects in rumors-api database and the owner entities in the app's own user database.

## Current implementation

Instead of managing all `appId`s and their configuration in a centralized place, currently rumors-api directly hard-code the following `appId` throughout the codebase [[1]](https://github.com/cofacts/rumors-api/blob/master/src/checkHeaders.js), [[2]](https://github.com/cofacts/rumors-api/blob/master/src/auth.js#L189), [[3]](https://github.com/cofacts/rumors-api/blob/master/src/graphql/models/User.js#L110):

- `RUMORS_LINE_BOT`: the **backend** app representing rumors-line-bot. Set when `x-app-secret` matches `process.env.RUMORS_LINE_BOT_SECRET`.
- `BOT_LEGACY`: Not present in codebase, but presents in very old objects in the database, denoting that this data is collected by the legacy chatbot before Feb 2017.
- `DEVELOPMENT_BACKEND`: the fallback **backend** app for wrong `x-app-secret`, used when 
- `WEBSITE`:
- `DEVELOPMENT_FRONTEND`:

These code are introduced into the codebase for faster development when we kick-start the product. They are subject to change, as we are currently facing the following challenges.

## Challenges we are facing now

### Emerging clients

- [rumors-fb-bot](https://github.com/cofacts/rumors-fb-bot/)
- [AI model](https://github.com/cofacts/rumors-ai)
- [community builder](https://g0v.hackmd.io/@mrorz/B1X4EkJcU#New-idea-Social-media-toolkit)

### Naming backend app users
https://g0v.hackmd.io/KVzYgGsARZuyd3AJjJtxlA#%E5%81%87%E5%90%8D%E8%A8%8E%E8%AB%96

## Proposed implementation to overcome the challenges

storage
specify dev-only secret (.env.sample), only available on staging DB
block all other usage

----

## Representation of backend app users

I.e. rumors-line-bot 的使用者在 rumors-api 如何表示。

### Backend app user 的需求

User IDs from backend app 的性質是：

- **sensitive**: 可能含有 PII (email)，因此若不是同一個 app，不該直接輸出 userId
- **not safe**: 可能含有特殊字元，無法直接當成 Elasticsearch document `_id`
- **long**: 長度可能會超過 [elasticsearch 上限 512 byte](https://blog.joshmlwood.com/elasticsearch-ids-are-hard/)

因此，設計上需要考慮：

- 若 user ID from backend app 需要放進 Elasticsearch key 時應該要使用 `sha256(userId)` 而不能直接使用 `userId`，同時考慮到 sensitive、not-safe 與 long 這三個特性。
- 因為 sensitive 的關係，user Id from backend app 不應被其他 app 直接存取；但進行 query 的 app 可以存取自己寫入的 entity 的 userId (i.e. query 的 app id 若與 entity app Id 相同，才能拿出 user id)，這樣此 app 才有機會將 rumors-api 的 entity 與自己的 user id 對在一起。

:::danger
雖說 backend app user ID 因為 *sensitive* 所以不該露出、因為 *not-safe* 且 *long* 所以不該用來拼接 entity ID，但事實上現在 production API 的某些欄位，並沒有遵循上面的原則，應當修正：

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b0d42f7d823c5023e08e993e615b3bea.png)
:::

---

另外，API 在 Cofacts Next 時，會面對以下「指涉特定 backend user」的需求：

- **display author of an entity**: 需要顯示特定 entity 的 user 資訊，如顯示 reply request 使用者的假名。此時 entity 帶有 `userId`、`appId`。
- **ensure entity uniqueness**: 有些 entity 組合，一個使用者只能有一個。如一個 user 只能對一個 article 送出一次 reply request。由於 Elasticsearch 沒有 unique key 機制，只能將 user ID、article ID 一併放在
- **user page**: 需要從 URL segment 讀出使用者 ID 然後顯示 user page。
- **fetch entities related to the user**: 「顯示此使用者的所有 reply request」、「列出此使用者所回報的文章列表」等等。

### Implementation

下面兩種實作方向，均能滿足上列需求。

#### 方向 #1: backend 無實體 user

此解法在 elasticsearch 中，仍然需要一個 index 紀錄 backend user 的：
- `_id: sha(appId + userId)` 確保同一個 appId / userId 組合不會產生兩個 doc
- random generated name
- random generated avatar

上面的 index 可以在 resolve user 時存取，若不存在則即時產生。

此實作的重點是在「`userId` 保密、又沒有相對應的 user entity」的限制下滿足「指稱 user」的需求。上述需求可以這樣實作：

- **fetch entities related to the user**: query 時，用 `authorOf: {entityId, entityType}` 避開 userId，而是用「什麼東西的作者」來在 query 中指稱該使用者。API 會先在 resolver 中從資料庫找出相對應的 `userId` & `appId`，再使用 `userId` & `appId` 去撈相關 entity。
  :::info
  其實現在 `ListArticleFilter` 中的 [`fromUserOfArticleId`](https://github.com/cofacts/rumors-api/blob/master/src/graphql/queries/ListArticles.js#L98-L104) 就是一種「用別的 entity 指稱某個 LINE 使用者」的設計。
  
  上面的 `authorOf` 就是將 `fromUserOfArticleId` 從指稱「單一 article 的 author」推廣到指稱「任何 entity 的 author」。
  :::
- **user page**: 同理，URL 中放 `entityId`, `entityType`，在 API 中找出相對的 userId & appId
- **display author of an entity**: user resolver 讀取 entity (如 replyrequests) 的 `appId` 與 `userId`，取得該 index 中儲存的 random name & avatar
- **ensure entity uniqueness**: 將 `sha(appId + userId)` 放入 entity ID 以確保同一個使用者的限制。

:::warning
**需要 migration script**

- 重新生成 _id 裡有原始 app `userId` 的 entity：所有 `replyrequest`、`articlereplyfeedback` 的 `_id` 裡，`appId` + `userId` 的部分都要改用 `sha(appId + userId)` 重新生成。
:::

#### 方向 #2: 針對每個 backend user 都產生一個 user document

與其把 backend app user 與 browser app user 分開處理，不如統一處理：

- 兩者的 user 都一樣在 `users` index 下產生 user entity。
- 資料庫內所有 entity (`articles`, `articlereplies`, `replyrequests` 等等) 通通都使用 `users` 的 `_id`~~；刪除 `appId` 欄位。~~
- backend app 的 `user` entity ，與 browser app 的相比有下列特性：
  - `_id`： `sha256(appId + userId)` 確保 (appId, userId) 對應到唯一一個 user。（browser app user 的 `_id` 則維持由 Elasticsearch 自動生成）
  - 新增 `appUserId` 欄位，存放 backend app 送給 rumors-api 的原始 user Id。 `appUserId` 欄位，只有原 app 可存取（request 時 `x-app-secret` 須符合該 app）。
    - 至此，有 *sensitive*、*long*、*not safe* 特性的東西被收進 `appUserId`，`users._id` 則是公開也沒關係的 `sha(appId + userId)`，因此可以與 browser app 的 user id 一樣外顯在 URL 裡，也可以編進 replyrequest、articlereplyfeedback 等 entity 的 `_id` 裡確保 uniqueness。
    :::info
    `User` object type 要 expose `appUserId` 的話，需要檢查 `appId`
    可以先不做，畢竟目前沒有 client 要讀
    :::
  - `name`, `avatarUrl`：[隨機產生](https://g0v.hackmd.io/7ERem43XREWJPOjjdE28SQ)
  - 新增 `appId` 欄位，存放是哪一個 backend app。（browser app 則無，畢竟所有 browser app 都共用由 rumors-api 統一管理的 user）
- 新增 backend user 時機：[graphql server 取用 user 時](https://github.com/cofacts/rumors-api/blob/master/src/index.js#L79-L90)。流程如下：
  1. 取 GraphQL call URL 中的 `userId` 與 `checkHeader` middleware 解出的 appId，~~產出 `sha(appId, userId)` 去 users index 撈出 user instance~~ term query 去撈該 (appId, appUserId) 的使用者
  2. 若撈不到該 user，則就地產生一個 backend app user，插入 `users` DB （check collision）

:::warning
**需要 migration script**

- 把現在所有 entity (`articles`, `replyrequests`, `articlereplyfeedbacks` 等等) 裡的 user 都蓋出 user instance
- 把所有 entity 的 `userId` 都從 backend app 給的原始 `userId`，更新成新的 ID （從資料庫撈）
- 重新生成 `_id` 裡有原始 app `userId` 的 entity：所有 `replyrequest`、`articlereplyfeedback` 的 `_id` 裡，`appId` + `userId` 的部分都要改用 `sha(appId + userId)` 重新生成。

**需要變更 DB schema**
- `users` 新增上面提到的欄位
- ~~各 `entity` 移除 `appId` 欄位。~~ Lucien: 還是保留 appId 紀錄這個 entity 是哪個 app 做的，方便用來做 filter。
:::

如此一來，上面列出的需求的實作就會變得非常單純，且與指涉 browser app user 的邏輯一致：

- **display author of an entity**: 拿 entity 的 `userId` 去 users index 撈出該 user 的資訊。行為與 browser app users 一致。
- **ensure entity uniqueness**: ~~直接把 entity 的 `userId` encode 進該 entity 的 ID 方可確保 uniqueness。~~ graphql context 層會 find or insert uesr，取用 `_id` 拿來放進 entity id 中 （如 replyrequest, articlereplyfeedback）
- **user page**: URL 裡直接使用 users index 裡的 `_id` （`sha(appId + userId)`）。行為與 browser app users 一致。
- **fetch entities related to the user**: 直接使用 users index 裡的 `_id` （`sha(appId + userId)`） 去比對資料庫裡各 entity 的 `userId` 欄位。行為與 browser app users 的一致。

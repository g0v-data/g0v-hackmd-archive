# 20200831 release thrashing issue

> 0831 release 應該是發生在 8/31 凌晨 3 點（UTC 08/30 19:00）
> 0731 release 上線時間：8/31 下午 5 點（UTC 8/31 09:00）

## 經過

0831 release 之後，8/31(一) 伺服器非常忙碌，網站、chatbot、API 都受影響，不時會會倒站。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_531c0d4519f05cf710f6ff55442506ec.png)

在 8/31 下午 5 點的時候，rollback 到 0731 release 的版本。

9/2 凌晨，陸續嘗試了另外的兩個版本，目前版本為 [8514e26b](https://github.com/cofacts/rumors-site/tree/article-stats-feature-branch)。

## 比較版本

目前已經在 production 上測試了 4 種 rumors-site 的 image，最舊到最新的版本依序為：

1. 0731 release
   -（此為前一版上線版本）

2. [8514e26b](https://github.com/cofacts/rumors-site/compare/release/20200731...article-stats-feature-branch) **目前上線版本**
   - #301 <Infos> time & metadata display component
   - #302 Security fix
   - #304 RSS related fixes; RSS should start working again!

3. [test/apollo3](https://github.com/cofacts/rumors-site/compare/article-stats-feature-branch...test-apollo3)
   - #312 Apollo client 3

4. [0831 release](https://github.com/cofacts/rumors-site/compare/test-apollo3...release/20200831)
   - #311 Revamp article reply feedback component (50% complete); reorganize article reply related component props
   - #316 iOS polyfill
   - #318 Fix search page static build
   - #305 #325 New RSS UI
   - #317 Google translate now no longer blocks mobile UI
   - #320 Fix "Asked many times"
   - Translation

## 各版本 deploy 後的表現

0731 release 版本的 nginx log（瞬時）：
可以看到來自不同 IP 的 request，相隔數秒，為正常瀏覽或第三方爬蟲行為所致。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_90cb6917c8c21e636a5b4305009cde54.png)

0731 release 版本的一日 apollo studio 使用觀測：
平均 rpm 為 546。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4393d6e0705ecc91cc0d7c87505abbb2.png)

:::info
若改為 deploy 8514e26b，nginx 觀測到的流量與 apollo studio 觀測到的流量，與 0731 release 沒有顯著差異。
:::

0831 與 test/apollo3 在 deploy 之後nginx 會觀測到非常多來自 172.18.0.1 (docker-compose network gateway) 往 `/graphql` 的 request，時間戳記在同一秒、referer 是 node-fetch，應該是 rumors-site server-side render。

0831 release 的 nginx log （瞬時）
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9f5d065082d5ca015d5e65319ba59c7f.png)

0831 版本 deploy 後的 apollo studio 使用觀測：
雖然 deploy 後的時間沒有超過 12 小時，日均 RPM 就已經飆到 900。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e52807004ea8c9427cdc7ea55d712433.png)

:::info
若改為 deploy test/apollo3，也一樣可以在 nginx 與 apollo studio 觀測到一樣的情況，因此 test/apollo3 與 20200831 release 也沒有顯著差異。
:::

## 分析

實際在 production deploy 8514e26b 與 test/apollo3 這兩個 image 的差異相當顯著，
root cause 確實就在[升級 apollo-client 3 的 PR 中](https://github.com/cofacts/rumors-site/pull/312)

但實際造成 Apollo client 3 request thrashing 的原因不明。

## Proposed solution

將 apollo-client 3 降級回 apollo-client 2 再繼續開發。

:::spoiler Previous investigations

## Investigate what is being navigated
- [x] Google analytics
- [x] nginx log

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_835a6aac908a9971170a93020ce0acb9.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5a2fb3d62024049f67d76f6a0b9e22b0.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6c8df146623c55533822353fb06d44c9.png)

> 使用者較少、但 hit 更多
> 未達上週一的 usage，用量正常（含 /graphql requests）
> 

## `LoadArticlePage` Before release

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_742e3850767213a0aad5f1d8b03e0648.png)


### All operations
> ## SERVER SIDE RENDER
> FETCH [ 'LoadArticlePage' ]
> FETCH [
>   'ListUnresolvedArticles',
>   'ListCategoryForSelect',
>   'ListUnresolvedArticles',
>   'ListCategoryForSelect'
> ]
> ## CLIENT
> FETCH ["ListUnresolvedArticles", "ListCategoryForSelect", "LoadArticlePageForUser", "CurrentUserQuery", "UserLevelQuery"]
> FETCH ["LoadArticlePageForUser"]
> 

### LoadArticlePage

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_93ee3c0b52939824e28bea10ce636bc9.png)

Operation signature

```graphql
fragment AddCategoryDialogData on ArticleCategory {
  __typename
  articleId
  category {
    __typename
    description
    title
  }
  categoryId
  negativeFeedbackCount
  ownVote
  positiveFeedbackCount
  user {
    __typename
    id
  }
}
fragment ArticleCategoryData on ArticleCategory {
  __typename
  articleId
  canUpdateStatus
  category {
    __typename
    description
    title
  }
  categoryId
  negativeFeedbackCount
  ownVote
  positiveFeedbackCount
  status
}
fragment ArticleInfo on Article {
  __typename
  articleReplies(status: NORMAL) {
    __typename
    reply {
      __typename
      type
    }
  }
  createdAt
  replyCount
  replyRequestCount
}
fragment ArticleReplyData on ArticleReply {
  __typename
  articleId
  canUpdateStatus
  createdAt
  reply {
    __typename
    hyperlinks {
      __typename
      ...HyperlinkData
    }
    id
    reference
    text
    type
    user {
      __typename
      avatarUrl
      id
      level
      name
    }
    ...ReplyInfo
  }
  replyId
  user {
    __typename
    avatarUrl
    id
    level
    name
  }
  ...ArticleReplyFeedbackData
}
fragment ArticleReplyFeedbackData on ArticleReply {
  __typename
  feedbacks {
    __typename
    comment
    id
    user {
      __typename
      avatarUrl
      id
      name
    }
    vote
  }
  negativeFeedbackCount
  ownVote
  positiveFeedbackCount
  ...ArticleReplyFeedbackForUser
}
fragment ArticleReplyFeedbackForUser on ArticleReply {
  __typename
  articleId
  ownVote
  replyId
}
fragment CurrentRepliesData on ArticleReply {
  __typename
  articleId
  replyId
  status
  ...ArticleReplyData
}
fragment HyperlinkData on Hyperlink {
  __typename
  error
  summary
  title
  topImageUrl
  url
}
fragment RelatedArticleData on Article {
  __typename
  relatedArticles(filter: {}) {
    __typename
    edges {
      __typename
      node {
        __typename
        articleReplies {
          __typename
          ...RelatedArticleReplyData
        }
        id
      }
    }
  }
}
fragment RelatedArticleReplyData on ArticleReply {
  __typename
  article {
    __typename
    id
    text
  }
  articleId
  reply {
    __typename
    createdAt
    id
    text
    type
  }
  replyId
  user {
    __typename
    id
  }
}
fragment ReplyInfo on Reply {
  __typename
  createdAt
  id
  user {
    __typename
    id
    name
  }
}
fragment ReplyRequestInfo on ReplyRequest {
  __typename
  negativeFeedbackCount
  positiveFeedbackCount
  reason
  ...ReplyRequestInfoForUser
}
fragment ReplyRequestInfoForUser on ReplyRequest {
  __typename
  id
  ownVote
}
query LoadArticlePage($id: String!) {
  GetArticle(id: $id) {
    __typename
    articleCategories {
      __typename
      ...AddCategoryDialogData
      ...ArticleCategoryData
    }
    articleReplies {
      __typename
      ...CurrentRepliesData
    }
    createdAt
    hyperlinks {
      __typename
      ...HyperlinkData
    }
    id
    references {
      __typename
      type
    }
    relatedArticles {
      __typename
      edges {
        __typename
        node {
          __typename
          id
          text
          ...ArticleInfo
        }
      }
    }
    replyCount
    replyRequestCount
    replyRequests {
      __typename
      ...ReplyRequestInfo
    }
    requestedForReply
    text
    ...RelatedArticleData
  }
}

```


## `LoadArticlePage` After release

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_80525949d0456f6aa5084a733076e8a3.png)

### All operations
> ## SERVER-SIDE RENDER
> FETCH [ 'LoadArticlePage' ]
> FETCH [ 'ListUnresolvedArticles', 'ListCategoryForSelect' ]
> ## CLIENT
> FETCH ["ListUnresolvedArticles", "ListCategoryForSelect", "CurrentUserQuery", "UserLevelQuery", "LoadArticlePageForUser"]
> FETCH ["LoadArticlePageForUser"]

### LoadArticlePage

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_430b71ab207f8cb0515fbe8f88e34326.png)


Operation signature

```graphql=
fragment AddCategoryDialogData on ArticleCategory {
  __typename
  articleId
  category {
    __typename
    description
    title
  }
  categoryId
  negativeFeedbackCount
  ownVote
  positiveFeedbackCount
  user {
    __typename
    id
  }
}
fragment ArticleCategoryData on ArticleCategory {
  __typename
  articleId
  canUpdateStatus
  category {
    __typename
    description
    title
  }
  categoryId
  negativeFeedbackCount
  ownVote
  positiveFeedbackCount
  status
}
fragment ArticleInfo on Article {
  __typename
  articleReplies(status: NORMAL) {
    __typename
    reply {
      __typename
      type
    }
  }
  createdAt
  replyCount
  replyRequestCount
}
fragment ArticleReplyData on ArticleReply {
  __typename
  articleId
  canUpdateStatus
  createdAt
  reply {
    __typename
    hyperlinks {
      __typename
      ...HyperlinkData
    }
    id
    reference
    text
    type
    user {
      __typename
      id
      level
      name
      ...AvatarData
    }
    ...ReplyInfo
  }
  replyId
  user {
    __typename
    id
    level
    name
    ...AvatarData
  }
  ...ArticleReplyFeedbackControlData
}
fragment ArticleReplyFeedbackControlData on ArticleReply {
  __typename
  feedbacks {
    __typename
    comment
    id
    user {
      __typename
      id
      name
      ...AvatarData
    }
    vote
  }
  negativeFeedbackCount
  ownVote
  positiveFeedbackCount
  ...ArticleReplyFeedbackControlDataForUser
  ...ButtonGroupDisplayArticleReply
}
fragment ArticleReplyFeedbackControlDataForUser on ArticleReply {
  __typename
  articleId
  ownVote
  replyId
  ...ButtonGroupDisplayArticleReplyForUser
}
fragment AvatarData on User {
  __typename
  avatarUrl
  id
  level
}
fragment ButtonGroupDisplayArticleReply on ArticleReply {
  __typename
  articleId
  negativeFeedbackCount
  positiveFeedbackCount
  replyId
  user {
    __typename
    id
  }
  ...ButtonGroupDisplayArticleReplyForUser
}
fragment ButtonGroupDisplayArticleReplyForUser on ArticleReply {
  __typename
  articleId
  ownVote
  replyId
}
fragment CurrentRepliesData on ArticleReply {
  __typename
  articleId
  replyId
  status
  ...ArticleReplyData
}
fragment HyperlinkData on Hyperlink {
  __typename
  error
  summary
  title
  topImageUrl
  url
}
fragment RelatedArticleData on Article {
  __typename
  relatedArticles(filter: {}) {
    __typename
    edges {
      __typename
      node {
        __typename
        articleReplies {
          __typename
          ...RelatedArticleReplyData
        }
        id
      }
    }
  }
}
fragment RelatedArticleReplyData on ArticleReply {
  __typename
  article {
    __typename
    id
    text
  }
  articleId
  reply {
    __typename
    createdAt
    id
    text
    type
  }
  replyId
  user {
    __typename
    id
  }
}
fragment ReplyInfo on Reply {
  __typename
  createdAt
  id
  user {
    __typename
    id
    name
  }
}
fragment ReplyRequestInfo on ReplyRequest {
  __typename
  negativeFeedbackCount
  positiveFeedbackCount
  reason
  ...ReplyRequestInfoForUser
}
fragment ReplyRequestInfoForUser on ReplyRequest {
  __typename
  id
  ownVote
}
query LoadArticlePage($id: String!) {
  GetArticle(id: $id) {
    __typename
    articleCategories {
      __typename
      ...AddCategoryDialogData
      ...ArticleCategoryData
    }
    articleReplies {
      __typename
      ...CurrentRepliesData
    }
    createdAt
    hyperlinks {
      __typename
      ...HyperlinkData
    }
    id
    references {
      __typename
      type
    }
    relatedArticles {
      __typename
      edges {
        __typename
        node {
          __typename
          id
          text
          ...ArticleInfo
        }
      }
    }
    replyCount
    replyRequestCount
    replyRequests {
      __typename
      ...ReplyRequestInfo
    }
    requestedForReply
    text
    ...RelatedArticleData
  }
}
```

:::
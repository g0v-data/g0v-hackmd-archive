---
tags: cofacts
---

# Cofacts Next list pages TODO items

## Release blocker

### Message list filter

文章列表至少應該要有「熱門回報」filter，亦即現在 production 上的「僅顯示兩個回報以上」的功能。

因為這是原本 production 上有的重要功能，因此希望可以先有這個。

#### As-is
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d0622de8a8c191168d0543325b8c06e7.png)

#### To-be

* 增加「熱門回報」選項（ `ListArticleFilter` 的 `replyRequestCount >= 2` ）

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c54506e917c572c231dc3ca1395856f6.png)

:::info
- Github Project Card: https://github.com/orgs/cofacts/projects/5#card-37494391
- Spec: https://g0v.hackmd.io/@NFi0czulSemxCM8RNSlz8Q/HJ8xT3QVU/%2FahtI6xsFRQyxktrIlc1VcQ
- Mockup: https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=428%3A37
:::


### For-You 等你來答

「等你來答」目前 filter 跟 spec 不符。由於我們需要評估此新功能的效果，因此希望可以實作之。

#### As-is

For-You filter 跟 article list 預設目前一致。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2e2c1d900293ee07033092c4c3a633d6.png)

#### To-be

1. 列表的 `ListArticleFilter`，根據 [spec](https://g0v.hackmd.io/@NFi0czulSemxCM8RNSlz8Q/HJ8xT3QVU/%2FN8I2-zkJTaS35BP8VH8ZQA) 應使用 `replyRequestCount >= 2` 且 `hasArticleReplyWithMorePositiveFeedback = false`。
2. 導覽列數字的`ListArticleFilter`，根據 [spec](https://g0v.hackmd.io/@NFi0czulSemxCM8RNSlz8Q/HJ8xT3QVU/%2FN8I2-zkJTaS35BP8VH8ZQA) 應使用`replyRequestCount >= 2` 且 `hasArticleReplyWithMorePositiveFeedback = false`。
    - spec 中「自己沒有送過任何 normal articleReply」尚無可用 API，因此先跳過，僅使用上面條件顯示數字。另在 [rumors-api#165](https://github.com/cofacts/rumors-api/issues/165) 追蹤 API 進度。

:::info
- Issue:
- Github Project Card: https://github.com/orgs/cofacts/projects/5#card-37456782
- Spec:
  - 列表內容 https://g0v.hackmd.io/@NFi0czulSemxCM8RNSlz8Q/HJ8xT3QVU/%2FN8I2-zkJTaS35BP8VH8ZQA
  - 導覽列數字 https://g0v.hackmd.io/iJm9_nZaTA2GyInn7ycxoA#%E7%AD%89%E4%BD%A0%E4%BE%86%E7%AD%94-Query
- Mockup: https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=436%3A1
:::

## Enhancements

### Reply list 過濾日期功能

#### As-is

目前左上角過濾日期功能是使用 `createdAt` 進行過濾，因此即使訊息最近有被回過，也無法正確顯示。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f7c7c2ba7dffdba816ca74baf423913f.png)

#### To-Be

根據 Spec，應使用 `ListArticleFilter` 中的 `repliedAt`。[`repliedAt` 使用的](https://github.com/cofacts/rumors-api/blob/master/src/graphql/queries/ListArticles.js#L291-L311)才是 spec 裡規定的 `article.articleReplies.createdAt`。

:::info
- Issue:
- Github Project Card: 
- Spec: https://g0v.hackmd.io/@NFi0czulSemxCM8RNSlz8Q/HJ8xT3QVU/%2FZZWHWi2BTuyhkSWzAvKLAw
- Mockup: 
:::

### Other message list filters implementation

#### As-is
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d0622de8a8c191168d0543325b8c06e7.png)

#### To-be
* 拿掉 unsolved / solved / all filter
* 增加下面選項:
  - 還未有效查核（`ListArticleFilter` 的 `hasArticleReplyWithMorePositiveFeedback = false`）
  - 熱門討論（`ListArticleFilter` 的 `replyCount >= 3`）

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c54506e917c572c231dc3ca1395856f6.png)

:::info
- Github Project Card: https://github.com/orgs/cofacts/projects/5#card-37494391
- Spec: https://g0v.hackmd.io/@NFi0czulSemxCM8RNSlz8Q/HJ8xT3QVU/%2FahtI6xsFRQyxktrIlc1VcQ
- Mockup: https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=428%3A37
:::

### Reply list filters implementation

#### As-is
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_be6f431bb498ef86dbd5bd3f6f0f35ea.png)

#### To-be
* 拿掉 unsolved / solved / all filter
* 增加下面選項:
  - 還未有效查核（`ListArticleFilter` 的 `hasArticleReplyWithMorePositiveFeedback = false`）
  - 熱門討論（`ListArticleFilter` 的 `replyCount >= 3`）
  - 熱門回報（ `ListArticleFilter` 的 `replyRequestCount >= 2` ）

![](https://user-images.githubusercontent.com/108608/80923827-88646080-8db8-11ea-8dea-faf365456f67.png)

:::info
- Github Project Card: https://github.com/orgs/cofacts/projects/5#card-37494391
- Spec: https://g0v.hackmd.io/@NFi0czulSemxCM8RNSlz8Q/HJ8xT3QVU/%2FZZWHWi2BTuyhkSWzAvKLAw
- Mockup: https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=79%3A9
:::

### Alignment of date filter and sorting

#### As-is

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1bca97104add2bd0c6df61dbca708763.png)


#### To-Be

Desktop
左右 control 高度一致
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_882c8d3a16a7a9f31e4b6bfe2f133bdf.png)

Mobile
注意 control 高度與 desktop 不同，但左右高度一致
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6016392c20cb63a2775d7b5b9dfdb977.png)

:::info
- Mockup: https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=304%3A138
:::


### Subscribe button alignment

#### As-is

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d72ead9c1d7eee3a7e3a375e26a7be3d.png)


#### To-Be

Desktop: 在標題右邊、垂直擲中

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_91f272bea5ac942e5776703f2e950352.png)

Mobile: 在標題下面、跟標題一起置中

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6847e6f04d8667813460fe44f6499513.png)


:::info
- Mockup: https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=304%3A138
:::

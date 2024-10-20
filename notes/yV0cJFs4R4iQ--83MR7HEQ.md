---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240923 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, orz
- 線上出席：Conrad, T, nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :female-police-officer: Open165

Summary + accordion + 165 官方公告連結
https://165.g0v.tw/name/%E4%B8%8A%E6%B5%B7%E6%9C%9F%E8%B2%A8%E4%BA%A4%E6%98%93%E6%89%80

- [Direct hit display in detail pages #26](https://github.com/Open165/site/pull/26)
- [Sync announcements in 165 to DB #27](https://github.com/Open165/site/pull/27)
- [Name detail page summary and refactor #28](https://github.com/Open165/site/pull/28)

#### :globe_with_meridians: Site
#### :robot_face: rumors-line-bot

#### :electric_plug: API

- https://github.com/cofacts/rumors-api/pull/347

### :rocket: Staging

- https://github.com/cofacts/rumors-line-bot/pull/398

#### :robot_face: rumors-line-bot

##### Testing checklist

:::info
上週發生什麼事：https://g0v.hackmd.io/UHKMm7h_QIe5EB4Z0cGQ3g?view#%E2%9B%94%EF%B8%8F-Release-Blockers
:::

https://lin.ee/1QUzEX4nI

- [ ] A 回報一組圖文
- [ ] A 在網站上回覆其中一個 article
- [ ] B 把同一組圖文 + 一個多的文字，回報成新的 cooccurrence
- [ ] 觀察現有 article 的 reply request count

##### ⛔️ Release Blockers
- 這組好像還是壞的 https://dev.cofacts.tw/article/0RG7-pEBUOXjqM1AKBOd
  - 多了雲之聲，少了二手菸
  - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_76ca4bb5c891c82acae9349c33b4e12e.png =x400)
- https://dev.cofacts.tw/article/7BHNHpIBUOXjqM1ADxMn
  - 應有 https://dev.cofacts.tw/article/6RHNHpIBUOXjqM1ABRPZ
  - 有 group 但「雲之聲」也是錯的 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_32733fc98031808a4da3739108196c96.JPG =x400)
- https://dev.cofacts.tw/article/8xHSHpIBUOXjqM1AvRND
  - 一樣有 group 但「雲之聲」是錯的 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0f8656a69e6164ee1ef7f980eb7cfa4a.png =x400)

##### Analysis

Debugging Google Cloud Logs Explorer query
```
(resource.type="cloud_run_revision" AND resource.labels.service_name="dev-line-bot") OR (resource.labels.instance_id="rumors-api-staging" AND jsonPayload.message: "Apollo#requestDidStart")
```

###### 2024-09-23 20:13
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_76ca4bb5c891c82acae9349c33b4e12e.png =x400)
訊息之一：https://dev.cofacts.tw/article/0RG7-pEBUOXjqM1AKBOd

- 比對截圖時間，操作之使用者應為 `j4S8C_3WKC9KPW2pJr1iEx-vaIYoQJJ8rLGCy5PGYhlQQT44o` (`Uaddc74df8a3a176b901d9d648b0fc4fe`)
- 20:13:23 時，詢問使用者是否要把 1 則新訊息送進資料庫
- 20:13:30 時 server 報錯 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4fabaa776422017f1d6edc4b6fa3ae08.png)
  - 應是 article version conflict 導致`SubmitMediaArticleUnderConsent` 失敗
  - 應是 https://dev.cofacts.tw/article/6RHNHpIBUOXjqM1ABRPZ 這張圖，當時唯一的新訊息
  - 12:13:26 & 12:13:31 分別有兩人送出 reply request（收到 error 的是後者），應是此原因無誤 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c76b4eeb62b281f23d75771beecfbf1f.png)
  - 但判斷不出來是哪個 LINE 帳號收到 “[askingArticleSubmissionConsent] article is not created successfully”。本案例的使用者最後還是有拿到 LINE bot 回應，看起來不是 throw error 的人。
- 20:13:34 五次 `ListArticlesInProcessMedia`
- 20:13:40 建立 Cooccurrence，article ids:
  - 0RG7-pEBUOXjqM1AKBOd
  - 2BHJ-pEBUOXjqM1AkhMW
  - oP_g_-AB4DHgA-D_4E_gD-AP6FfoV-AH4AfgV-ip4J8
  - yRGx-pEBUOXjqM1ArxO7
  - yhGx-pEBUOXjqM1AsxP0
- 沒有半次 `AddReplyRequestForUnrepliedArticle`
- 20:13:41 選擇要查看的訊息：
  - https://dev.cofacts.tw/article/yRGx-pEBUOXjqM1ArxO7 ① 看起來 100% 像, 逐字稿內的字
  - https://dev.cofacts.tw/article/yhGx-pEBUOXjqM1AsxP0 ② 看起來 100% 像, 逐字稿內的字
  - https://dev.cofacts.tw/article/0RG7-pEBUOXjqM1AKBOd ③ 看起來 100% 像, 逐字稿內的字
  - https://dev.cofacts.tw/article/2BHJ-pEBUOXjqM1AkhMW ④ 看起來 100% 像, 逐字稿內的字
  - https://dev.cofacts.tw/article/6RHNHpIBUOXjqM1ABRPZ ⑤ 看起來 100% 像, 逐字稿內的字, 二手菸的傷害，卻沒有進 occurrence
  - https://dev.cofacts.tw/article/oP_g_-AB4DHgA-D_4E_gD-AP6FfoV-AH4AfgV-ip4J8 ⑥ 看起來 67% 像, 逐字稿內的字：醫師，使用多年，推薦用次氯酸水洗手，次氯酸水的爭論非常，使用次氯酸水的醫師 --> 錯的
- 判斷
  - 5 messages 有成功 query 出來，代表新訊息其實有在資料庫中
  - `createSearchResultCarouselContents` 會以圖片（有 `mediaSimilarity` 者）優先排序，所以會放在前面
  - `ListArticlesInProcessMedia` 是用 `_score` 排序，但這不保證「圖一樣」的會被排在前面；而`addReplyRequestForUnrepliedCooccurredArticles` 或 `setMostSimilarArticlesAsCooccurrence` 都是直接拿 `ListArticlesInProcessMedia` 的順序，因此雲之聲可能就是這樣被抓進來

###### 2024-09-23 20:14
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_32733fc98031808a4da3739108196c96.JPG =x400)

訊息之一：https://dev.cofacts.tw/article/7BHNHpIBUOXjqM1ADxMn

- 文字的部分似乎被 dialogflow 捕捉，觸發「你是在問哪一篇呢」回應
- 比對截圖時間，操作之使用者應為 j4S8C_0yPmaqiWIOQrPOWbjVUlGEhujR63JHNmn8kqPPPZUsM (Uafb8e4d9464c1dea58a01c34871993ba)
- 20:14:55 詢問 consent
- 20:15:01 `SubmitMediaArticleUnderConsent`
- 20:15:05 6 次 `ListArticlesInProcessMedia
- 20:15:10 建立 cooccurrence
- 20:15:14 選擇要查看的訊息：
  - https://dev.cofacts.tw/article/6BHMHpIBUOXjqM1A_xM_ : ① 看起來 100% 像, 逐字稿內的字
  - https://dev.cofacts.tw/article/7BHNHpIBUOXjqM1ADxMn : ② 看起來 100% 像, 逐字稿內的字
  - https://dev.cofacts.tw/article/-dtpSpABoURTSGJKIgLM : ③ 看起來 100% 像, 逐字稿內的字
  - https://dev.cofacts.tw/article/6hHNHpIBUOXjqM1ACRPG : ④ 看起來 100% 像, 逐字稿內的字
  - https://dev.cofacts.tw/article/popa0oIBv5it-Cx_-lKR : ⑤ 看起來 100% 像, 逐字稿內的字
  - https://dev.cofacts.tw/article/6RHNHpIBUOXjqM1ABRPZ : ⑥ 看起來 100% 像 <--- 應該要在 cooccurrence 但卻沒有
  - https://dev.cofacts.tw/article/oP_g_-AB4DHgA-D_4E_gD-AP6FfoV-AH4AfgV-ip4J8 : ⑦ 看起來 67% 像, 逐字稿內的字 <--- 不應該要在 cooccurrence 但卻有
- 判斷：同上

##### 未竟項目

### :eye: Under review

## Open165

- Wayback machine 方面：
  - 其實很多 165 回報的網址都已經被 Wayback machine 存檔 [name=mrorz]
  - 除了少數部落格型態的會被正常存檔外，其他 SPA 很容易壞掉
  - 可能自己存比較好
- New discoveries: https://g0v.hackmd.io/xl7YbrcTRECluGKK_HGo6Q#%E7%B6%B2%E7%AB%99%E5%85%A7%E6%96%87
  - 可以比外觀、code、IP
  - 針對 165 沒有收錄的網址，也能爬一下外觀、code、IP，與已知詐騙比對 --> 能及早發現換湯不換藥的詐騙！
- 需要 [browser rendering worker](https://developers.cloudflare.com/browser-rendering/)
- 網站移動到 github.com/Open165/site ，recon worker 放 github.com/Open165/worker
- 之後打算 recon endpoint 用 turnstile (Cloudflare 的 captcha) 保護

## Community

### 廣播：科技社群敲敲門
> 訪綱？

### 大松
> Cofacts + Open165

- 13:30 幫新手導覽團拍照 [name=Conrad]
  - 在導覽團抵達 Cofacts 的位置時拍照，畫面裡要有導覽團、正在解說的 Johnson 與 nonumpa 與 Johnson 的螢幕

Cofacts
- 協助闢謠
- good first issue
- AI classifier?

Open165
- 被騙後的文案
- 設計

### RightsCon
- 比鄰會是別場的講者
- Tech demo 可以有兩個講者

### 小聚
Fork 了一個在 oen
還沒有確定日期、還沒有借場地
https://cofacts.oen.tw/events/2mTCSkn6M3fCHW5wpVFPxwXRIkh
票在這裡
https://cofacts.oen.tw/events/2mTCSkn6M3fCHW5wpVFPxwXRIkh?shearTicket=2mTMGn8t0dIHh7KVKp2h8kSFPrW
- 發現一定要登入才能拿票

:::success
決定不用 oen，還是kktix吧
:::


- 大松可能會在二月 --> 9 月大松後可能還是 11 月
- 12, 1 月可能沒有大松
- 農曆年 = 1 月
- --> 10/27(日) 借 NPO Hub 二樓


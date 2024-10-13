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

https://dev.cofacts.tw/article/0RG7-pEBUOXjqM1AKBOd

有問題的 cooccurrence 在 2024-09-23T12:13:40.214Z 時建立, 5 messages
- ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a767f26e67e36df0f981658358055b1e.png)
- ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b13ced3bccfde295ba83935d2b3aca85.png)
- 選擇要查看的訊息：
  - yRGx-pEBUOXjqM1ArxO7 逐字稿內的字, 100% 像
  - 



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


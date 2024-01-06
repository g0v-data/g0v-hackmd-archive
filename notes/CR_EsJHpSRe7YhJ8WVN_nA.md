---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20210818 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：4000, orz, bil, paul, leo
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

[2021/08/13 Release](https://github.com/cofacts/rumors-site/releases/tag/release%2F20210813)

- #441 Fix "replied by me" in search pages and improves search highlight
- #442 Ellipsis in URL will no longer break URL when copied & pasted

#### :robot_face: rumors-line-bot

[2021/08/13 Release](https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20210813)

- #276 Relative & absolute time string in viewed article list
- #277 Collapsible article display
- #278 Revamp viewed article list UI and extract common components

### :rocket: Staging

Travis.org 不會幫我們跑測試、Docker hub 也不會幫我們 build

#### :electric_plug: API

- [#261 Build images & run CI on Github](https://github.com/cofacts/rumors-api/pull/261)

#### :globe_with_meridians: Site

- [#444 Build images & run CI on Github](https://github.com/cofacts/rumors-site/pull/444)

## 商標狀態

2021-08-18 0:00:00 已送出至[智財局](https://twtmsearch.tipo.gov.tw/OS0/OS0201.jsp?l6=zh_TW&isReadBulletinen_US=&isReadBulletinzh_TW=true)
- 「Cofacts 真的假的」申請號：110059474、110059475
- 「標章圖」申請號：110059476、110059477

> 由於智財局官網案件並非即時更新, 因此, 如您查詢時尚未找到您的商標案件, AIPLUX建議您可於2天後, 再重新查詢一次, 如有任何問題, 歡迎聯繫AIPLUX詢問。

## 大松

- 報名：https://g0v-jothon.kktix.cc/events/g0v-hackath45n
- 共筆：https://beta.hackfoldr.org/g0v-hackath45n
- Good first issues
- 進度 + 背景音樂
- 按 x 看影片
- 誰會來：bil, 4000, mrorz

:::danger
Google drive XML feed 有問題，網址疑似有更換，不能直接用 spreadsheet ID 了⋯⋯
https://beta.hackfoldr.org/cofacts/
:::

## 廣告 spammer

https://cofacts.tw/user?id=7EMgU3sBgBgcuemXXRfD

- 雖然與訊息有關，但沒有公開的出處，要求「私聊」，更接近廣告行為 [name=mrorz]

:::success
符合[使用者條款 一、6](https://github.com/cofacts/rumors-site/blob/github-actions/LEGAL.md) 的「廣告投放」樣態，可逕行公告刪除

> 如果網站協作者有廣告投放或是惡意的文章散布、違法情形，Cofacts WG 得直接終止與刪除網站使用者的帳號與其廣告內容、或是違法行為所留下之文字並將相關處理資訊紀錄於 https://github.com/cofacts/takedowns 
:::

https://cofacts.tw/article/35s3oqkdq8qys
號召網友來回應與評價的 case

## Article LIFF

Target: receive input (feedback, reply requests) from outside of Cofacts chatbot

https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/?node-id=3004%3A224
1. [x] 實作 common component storybook
2. [x] 實作 feedback form + 使用在目前的按鈕上
3. [x] 實作 article page 的 article 部分
4. [ ] 實作 article page 的 reply - ongoing
5. [ ] 實作 article page 的 reply request form + 使用在目前的按鈕上
6. [ ] 實作 article page 的 reply request list
7. [ ] 實作 article page 的 related article

本週開發：卡在 reply 的頭像
- 想說從 API render openpeeps 頭像
- 但 runtime efficiency 考量（見下）可能需要 refactor

### Openpeeps data-url

- react-peeps + react 的 SSR
- 可以加 svgo 把小數點去掉 (`cleanupNumericValues` with `floatPrecision = 0`), 31kB --> 7kB 
- https://github.com/cofacts/rumors-api/pull/260/files
- 蓋 user 時一律寫進 `avatarUrl` 比較好
- 但我們是每個 request 都會 upsert user（見下）

改成不放頭像
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f46aadb62a01adeabd4ce72dae8439ff.png)

### User upsert per request
每個 request 都會 `createOrUpdateUser` https://github.com/cofacts/rumors-api/blob/master/src/index.js#L95
- 會 upsert https://github.com/cofacts/rumors-api/blob/5e1fbd126ffc46a0f6b0e54009599b6321e81ab7/src/util/user.js#L188


- 若沒登入，下面的 bash script 可以正常運作:
    ```
    for VARIABLE in 1 2 3 4 5 6 7 8 9 10
    do
      curl 'https://dev-api.cofacts.tw/graphql' \
        -H 'x-app-id: RUMORS_SITE' \
        -H 'content-type: application/json' \
        --data-raw '[{"operationName":"GetArticlesList","variables":{},"query":"query GetArticlesList {\n  GetArticle(id: \"2agyninzg397r\") {id} }"}]' \
        --compressed &
    done
    ```
    執行結果：印出 10 次 `[{"data":{"GetArticle":{"id":"2agyninzg397r"}}}]`
- 但若加入 login cookie，則會有 conflict
    ```
    for VARIABLE in 1 2 3 4 5 6 7 8 9 10
    do
      curl 'https://dev-api.cofacts.tw/graphql' \
        -H 'x-app-id: RUMORS_SITE' \
        -H 'content-type: application/json' \
        -H 'cookie: koa:sess=...; koa:sess.sig=...' \
        --data-raw '[{"operationName":"GetArticlesList","variables":{},"query":"query GetArticlesList {\n  GetArticle(id: \"2agyninzg397r\") {id} }"}]' \
        --compressed &
    done
    ```
    會有數筆 `{"errors":[{"message":"Context creation failed: version_conflict_engine_exception","extensions":{"code":"INTERNAL_SERVER_ERROR"},"authError":false}]}`

:::info
- 可能改成先讀取，讓已經 create 過 user 的使用者不會遇到問題
- 但對於要新建 user 的使用者來說，同時打兩個含有 userId + secret 的 API 還是會出錯
:::

## Remove `hyperlinks` for chatbot messages

> 感覺回應跟出處之外的訊息，我們都可以改用 flex message，這樣大家就不會把這類東西送進來
他送進來麻煩的點在於，因為它付有 Cofacts URL，crawler 會針對文章訊息再次建檔，導致詢問原始訊息時會找到這種訊息
https://cofacts.tw/article/aayr2qaurvsv
> 針對這種已經送進來的訊息，我們要刪除 hyperlinks 嗎
不然因為他有 cofacts article hyperlink 所以一直會被找到囧

實測：似乎不會因為 hyperlink 內容就把該選項 show 出來，為何會一直被查詢的原因不明
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5ed780d93e08f7a7e14569e51ac901d9.png)

:::warning
因為 root cause 不明，所以先不動資料庫
:::

## Preload CSS & JS for websites in cloudflare

> 我發現原來 cloudflare 只要有指定 Link: </css/style.css>; rel=preload;
> cloudflare 自動升級 HTTP2 的同時還會做 HTTP2 push
> https://www.cloudflare.com/zh-tw/website-optimization/http2/serverpush/
> 這樣瀏覽器在拿到一開始的 html response 的時候，就同時會收到這些 asset 的 http2 push
> 省去瀏覽器 parse + 發 request 去拿 asset 的一個 RTT
感覺值得一試

- LIFF & Website 把 CSS & JS 加上 Link header?
    - 只會對第一次有影響，其實之後有 cache 就沒差太多

## 真的假的 <> 防詐達人

幫助此文章的選項（wording 再改）--> LIFF 免責 --> Cofacts LIFF

- 可以直接放在第一個按鈕「到 cofacts 看」 
    - 原本那個按鈕就是開網頁，所以跳一個 consent LIFF 應該也可以 [name=mrorz]
    - 但其他來源的卡片，點同一個按鈕是直接開網頁，有這樣的 concern [name=paul]
    - 可能只有第一次會開 consent，之後應該不會有 [name=yb]
- URL: https://liff.line.me/1563196602-X6mLdDkW?p=article&articleId=19yffzgl9w0xu
- TODO: 不確定 LIFF 裡面 `<a href="https://liff.line.me/1563196602-X6mLdDkW?p=article&articleId=19yffzgl9w0xu"></a>` 是否可以正確，再 POC
- 之後也會讓美玉姨用 LIFF 取代現在的 LINE URL scheme [name=mrorz]


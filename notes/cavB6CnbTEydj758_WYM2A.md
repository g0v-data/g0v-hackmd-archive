---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20200610 會議紀錄
=====
- Workis
- MrOrz, bil,


## Youtube API audit

> Subject: YouTube API Services Form
> 目前進度：6/18 回覆狀況


> https://github.com/cofacts/url-resolver/pull/70
> 這份 PR 在呼叫 puppeteer (scrap()) 之前，先用 unfurl 爬 metadata，如果 metadata 的東西不完整，才會呼叫 scrap() 。
> 在此前提下，這個 PR 也因此能安全拔掉 Youtube API。因回覆 Youtube API audit request 有時效性，請大家 review 此 PR～

- 2020/6/10 16:55 deployed to production!
- No more API calls:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_480abd2cf13c5ea7aeadef997fec52c4.png)
- 已經把 Youtube API 從此 app disable 掉


:::info
Deployed to production
已經回信，應可視為結案
:::

## Devs

### Pending review
- Category UI https://github.com/cofacts/rumors-site/pull/261
- LINE login https://github.com/cofacts/rumors-line-bot/pull/193
  - 遇到 ID token 會 expire 但沒有 update API 的問題
  - 在 expire 後呼叫 `liff.login()` 會拿到一樣的 expired token
  - 若 expire 就呼叫 `liff.logout()` 強迫重新登入，或者重新呼叫 `liff.init()` ([getIDToken 文件](https://developers.line.biz/en/reference/liff/#get-id-token))
- 「我回過的」API (12 day no review) https://github.com/cofacts/rumors-api/pull/172


### Deployed to Staging
- React hooks fix ([導致 search bar 壞掉](https://g0v-tw.slack.com/archives/C2PPMRQGP/p1591672395140900?thread_ts=1591671477.140100&cid=C2PPMRQGP))
- 網站側欄破版 fix
- `TimeRange` storybook: https://dev.cofacts.org/storybook/index.html?path=/story/timerange--no-range-given

### Deployed to production :rocket: 
- 嚴格的 CORS: https://github.com/cofacts/rumors-api/pull/175
  - http://cofacts.org 這些非 https 連線不在白名單內，故會觸發 CORS
  - http://localhost:3000 只有在 staging 的白名單內，故現在無法直連 production
- 新 cofacts url-resolver: https://github.com/cofacts/url-resolver/pull/70
  - 觀察 errors: https://rollbar.com/Cofacts/url-resolver/
  - 不知道為什麼沒被 `parseMeta` 擋下：
    - https://m.facebook.com/128269288214/posts/10157557180993215/?d=n
    - https://pets.ettoday.net/amp/amp_news.php?news_id=1734329&from=ampshare-line-fixed
    - https://kknews.cc/zh-tw/entertainment/44rv9v.html
    - https://kknews.cc/home/qvraa8y.amp
    - https://m.facebook.com/ceenceenco/posts/3053396154756225?__xts__%5B0%5D=68.ARCoNcS3-ppPAojL-yQhyEuGc4pRj_tAkqI0LQfE3nn1hUjESS_zuJawmxO0KiDZdAPyRJCbGq7P8L8Oe0OgkG0m6zz1Hf_C5TdWu9ROo0cO7-gBJYUGPSMPmYjlUX0lrvptmIWa7qI7RuClAa8MgZeuIhlsMYkiuXJkmsnyPXXJzqImUNMNvN5KuyuQ-IsmYweEDl14rNLG9hczta1HZskvOjF-UzkgfEtibNseBEOg15Plk10sJ37ywWsB1BugF8pgOI_oBqzVMthiVkxEhc5rSrAWT8542Zp4XgTnRTdxnzZH6z2VigHE1FsDjyfJDNToyGTIdH_EYi5ROrvkxb4yogm9TJ0tZGZGay3f9FmljUDBuKsQbU3ROP4&__tn__=H-R
    - https://a5717543.pixnet.net/blog/post/285059444
- More robust `CreateArticleCategory`: https://github.com/cofacts/rumors-api/pull/174
  - AI 輸入 article category 時應該更不會觸發 error

### New domains

- 新 domain 短很多
- [Staging] 支援多 domain；登入時會被導向到按下登入時的 domain

:::warning
需要設定 google search console
(domain 使用 DNS 設定)
:::

#### To production
- https://cofacts.org
- https://www.cofacts.org
- https://api.cofacts.org
- https://zh.cofacts.org
	- 無視瀏覽器設定，中文
- https://en.cofacts.org
	- 無視瀏覽器設定，英文
- https://old.cofacts.org
    - 升級至 next.js v9 之前的舊舊版，可以一直開著沒有 v9 的效能問題

#### To staging
- https://dev.cofacts.org
- https://dev-api.cofacts.org
- https://dev-zh.cofacts.org
    - 無視瀏覽器設定，中文
- https://dev-en.cofacts.org
	- 無視瀏覽器設定，英文


## Cofacts Next! blocking items

- Article page analytics API: https://github.com/cofacts/rumors-api/issues/166
- Archiving all hyperlinks in data archiving services
  - ~~Mitigate Youtube API audit: https://g0v.hackmd.io/6f87Zwo7QAOGx7rYK-QRfw~~
  - ~~Increase url-resolver's throughput:  https://github.com/cofacts/url-resolver/issues/69~~
  - Provide more robust archive: https://github.com/cofacts/rumors-api/issues/136
- (斌) Fix RSS: old RSS is broken by new list page, needs fixing
  - Also track its usage https://github.com/cofacts/rumors-site/issues/222
  > 作為編輯，我希望我有興趣的議題有新訊息時可以通知我，讓我可以即時回到 Cofacts 網站進行回應。
- Cofacts official website
  - Landing page
  - Profile page
  - RSS subscription dialog
- Cofacts new production usability enhancement items (a.k.a. bug fixes)
  - (斌) highlight search snippet (searched text) https://github.com/cofacts/rumors-api/issues/51
  - (斌) "我在 LINE 外頭看到的" trap bug https://github.com/cofacts/rumors-line-bot/issues/190
  - (斌) chatbot "sessionId of undefined" bug https://github.com/cofacts/rumors-line-bot/issues/192
  - (斌) Handle chatbot user did not grant send message permission https://rollbar.com/mrorz/rumors-line-bot/items/216/
  - (斌) optimize chatbot states https://github.com/cofacts/rumors-line-bot/issues/177

## 會議記錄移動

- 從 hackfoldr 收入 https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/
- 可以在 hackmd 裡完成所有整理作業，不用另外開 spreadsheet

## Communications

### 講師邀請
> Subject: 2020 COol Conference講師邀請
> https://www.facebook.com/events/255769419004815
>
> AIESEC NTLC
> 全台高中職生籌辦的四天三夜全英語營隊
> 暫定日期為7月20日星期一下午約一到一個半小時
> 主題針對分辨真假訊息及媒體識讀
> 地點暫定為國立台灣大學
> 


### Takedown
https://github.com/cofacts/takedowns/pull/1

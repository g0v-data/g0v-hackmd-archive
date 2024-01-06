---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20200603 會議紀錄
=====
orz, bil, 文武, Lucien ,darkbtf, ggm
Workis
> 上次開會紀錄：https://g0v.hackmd.io/@mrorz/SJD9LwoiL

## 台南小聚、講座檢討

文武：更新了偵測尚未領取的 tab 的 script
orz: 已同步更新到樣板檔 https://docs.google.com/spreadsheets/d/1Oijd-RfLOZGVhyhE4h-Sw8PxcyJ9oy7VL82Jxf_wD7c/edit#gid=2128743333

Before:
- 圖片無法ctrl-c + ctrl-p，必須整 sheet 複製
- 程式要分開複製

After
1. clone https://docs.google.com/spreadsheets/d/1Oijd-RfLOZGVhyhE4h-Sw8PxcyJ9oy7VL82Jxf_wD7c/edit#gid=2128743333
2. import need-to-check xlsx to cloned 分配表
3. 設定 trigger (但程式應該已經就位)

bil
台南人都很誠懇

台南大學共 12 人，一人分 2 tab，處理了 400 多篇

好想工作室的環境

- 記得先申請 iRent
- 廁所在對角線
- 飲水機的水滿冰
- 交通方便也有電梯
- 高雄人不少，可以一起經營


## Youtube API audit (Deadline: 5/29)

> Subject: YouTube API Services Form


寫了信說
- ombed 拿 title
- 把所有連結丟去第三方 archiver
- 無法趕上 5/29

Youtube 回說
> 1. Please confirm that the API Client is completely removing the YouTube API services from the API Client website
> 2. Kindly confirm, whether you want us to close this Audit request ?

我回問「close audit request」是什麼意思惹。

## Google analytics
[![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8cee75784749874883234c0f5676516a.png)](https://analytics.google.com/analytics/web/#/report/content-event-events/a98468513w144848466p149536672/explorer-table.secSegmentId=analytics.eventLabel&explorer-table.plotKeys=%5B%5D&explorer-table.rowStart=0&explorer-table.rowCount=100)

- Article reply 顯示的字數真的太少了，導致「閱讀全文」一直被按

## Devs

:rocket: Production launch

### Website
- Search page PR: https://github.com/cofacts/rumors-site/pull/256
- Hooks: https://github.com/cofacts/rumors-site/pull/258

### API
- Fix `ArticleReplyFeedback` filter bug: https://github.com/cofacts/rumors-api/pull/171
- `articleRepliesFrom` for `ListArticles` https://github.com/cofacts/rumors-api/pull/172

### Chatbot
- Cannot read property 'sessionId' of undefined: https://github.com/cofacts/rumors-line-bot/issues/192 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d9088f68feea779161585f8d1be7b729.png)


## 開發計畫

MrOrz
- rumors-api + rumors-db: userId & appId ( https://g0v.hackmd.io/ZcoUOX_-RQSkJyl5xz4_Zg )
- rumors-line-bot: line ID token processing ( https://g0v.hackmd.io/eIeU2g86Tfu5VnLazNfUvQ#Implementation-detail-2020510 )

orz: 6/4 做 rumors-api + rumors-db
文武: 6/4 整理 LINE login PR

### Cofacts Next! blocking items

- Article page analytics API: https://github.com/cofacts/rumors-api/issues/166
- Archiving all hyperlinks in data archiving services
  - Mitigate Youtube API audit: https://g0v.hackmd.io/6f87Zwo7QAOGx7rYK-QRfw
  - Increase url-resolver's throughput:  https://github.com/cofacts/url-resolver/issues/69
  - Provide more robust archive: https://github.com/cofacts/rumors-api/issues/136
- Fix RSS: old RSS is broken by new list page, needs fixing
  - Also track its usage https://github.com/cofacts/rumors-site/issues/222
  > 作為編輯，我希望我有興趣的議題有新訊息時可以通知我，讓我可以即時回到 Cofacts 網站進行回應。
- Cofacts official website
  - Landing page
  - Profile page
  - RSS subscription dialog
- Cofacts new production usability enhancement items (a.k.a. bug fixes)
  - highlight search snippet (searched text) https://github.com/cofacts/rumors-api/issues/51
  - "我在 LINE 外頭看到的" trap bug https://github.com/cofacts/rumors-line-bot/issues/190
  - chatbot "sessionId of undefined" bug https://github.com/cofacts/rumors-line-bot/issues/192
  - Handle chatbot user did not grant send message permission https://rollbar.com/mrorz/rumors-line-bot/items/216/
  - optimize chatbot states https://github.com/cofacts/rumors-line-bot/issues/177
  - 

## 非營利組織：申請「科技濃湯」

- 免費非營利組織 Google Apps + 每個月一萬塊美金的 Google 關鍵字廣告贊助，用來推廣組織網站 https://www.techsoup-taiwan.org.tw/faq/google
- 一年 2000 USD 的 AWS 點數 https://www.techsoup-taiwan.org.tw/node/6290

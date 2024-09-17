---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240916 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：orz, bil, Conrad, nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :robot_face: rumors-line-bot

- https://github.com/cofacts/rumors-line-bot/pull/397
- https://github.com/cofacts/rumors-line-bot/pull/398

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] A 回報一組圖文
- [x] A 在網站上回覆其中一個 article
- [x] B 把同一組圖文 + 一個多的文字，回報成新的 cooccurrence
- [x] 觀察現有 article 的 reply request count
  - 三人回報搭配 + reply request，符合預期 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_461a442adc44a8942b19571f6f3a0033.png)
##### ⛔️ Release Blockers
- nonumpa 傳的
  ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a01fb89a30051dabde6c3ba3935af9de.png)
  - https://dev.cofacts.tw/article/1RG8-pEBUOXjqM1A4xO9 應該要跟別人 group 但好像沒 Group 到
- bil 沒傳這張，但有傳這張旁邊的 cooccurrence
  https://dev.cofacts.tw/article/EynRB4kBFLWd9xY2Ohxi
  - 有傳 https://dev.cofacts.tw/article/265pyrpr2lix6 與其他搭配，但 cooccurrence 沒增加

----

Debugging Google Cloud Logs Explorer query
```
(resource.type="cloud_run_revision" AND resource.labels.service_name="dev-line-bot") OR (resource.labels.instance_id="rumors-api-staging" AND jsonPayload.message: "Apollo#requestDidStart")
```

###### nonumpa 的 grouping issue
一起傳但沒 group 到：
- https://dev.cofacts.tw/article/1RG8-pEBUOXjqM1A4xO9 沒 group 到
- https://dev.cofacts.tw/article/1BG8-pEBUOXjqM1A4RMD 沒 group 到
- https://dev.cofacts.tw/article/yRGx-pEBUOXjqM1ArxO7 與 https://dev.cofacts.tw/article/2BHJ-pEBUOXjqM1AkhMW 有 group 到

Log:
- 2024-09-16 20:08:27.480 LINE bot 收到 4 則訊息，詢問是否一起
- 2024-09-16 20:09:16.986 詢問是否送進資料庫
- 2024-09-16 20:09:26.485 收到答覆
  - 呼叫 2 次 SubmitMediaArticleUnderConsent、CreateAIReply
  - 呼叫 4 次 ListArticlesInProcessMedia
  - 呼叫 4 次 AddReplyRequestForUnrepliedArticle
  - 呼叫 1 次 SetCooccurrences 
    - 比照時間，cooccurrence ID 為，包含：
- 2024-09-16 20:09:37.661 完成送進資料庫，提供文章列表：
	- https://dev.cofacts.tw/article/yRGx-pEBUOXjqM1ArxO7 (v)
	- https://dev.cofacts.tw/article/yhGx-pEBUOXjqM1AsxP0 (100% 像，Match by 逐字稿內的字: 科技征, 無硝煙的自由戰, 開源運動在臺灣, OCF, 十週年特展, 槎地公民基金會)
	- https://dev.cofacts.tw/article/1RG8-pEBUOXjqM1A4xO9 (v, 沒 group 到)
	- https://dev.cofacts.tw/article/1BG8-pEBUOXjqM1A4RMD (v, 沒 group 到)
	- https://dev.cofacts.tw/article/EynRB4kBFLWd9xY2Ohxi (77% 像，逐字稿的字但明明無關 - 台灣大罪了, 民進黨飽了, 飽暖思淫毯嗎)
	- https://dev.cofacts.tw/article/AAFD6W_6L_EP8A_wD_APcA_wDPAP8I_wD_AH8Af3AD8 (76% 像，但明明無關)
	- https://dev.cofacts.tw/article/A8A_vAfgP9gEID_8P_w9AP_5P_g_AAAA__8AAAAAAAA (67% 像，逐字稿內的字但明明無關 - 同樣, 連勝文, 臺灣人接, 疫苗, 你們有沒, 仲介, Otto, 灣人民力量, 哪位, 發國難財⋯⋯)

分析：
- 關鍵應是「4 次 ListArticlesInProcessMedia」是否有找到對的文章，但 log 裡沒有
- 當時建立的 `SetCooccurrences` ， 

疑似是 submit 後 search again 沒有找到剛送進去的
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dac9d6a75988c2ff51da21cf8ed47b9a.png)




##### 未竟項目

### :eye: Under review

- https://github.com/cofacts/rumors-line-bot/pull/397
- https://github.com/cofacts/rumors-line-bot/pull/398


## CCPRIP

### [Infra] Logging & Observabilty

> CCPRIP doc
> https://g0v.hackmd.io/BRsJOevWSbyUMBSZEVVWrA#Logging-and-monitoring

Logging pricing
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f87c88290415e7c2fb3d0addbc8f38c4.png)

- Before: only rumors-api log is sent to Google Cloud; cloud run services are already in Google Cloud.
- After 2024/09/15 change: All services (nginx, api, site, line-bot-tw) are sent to Google Cloud.
  - 每個月月中的時候超過 free quota 50GB 後開始算錢
    > Ref: https://www.finout.io/blog/reducing-gcp-logging-costs
  - 6 月可能被 DDoS 所以特別多？
  - 太貴的話考慮設定 log retention 與 GCS log sink
    > Ref: https://mile.cloud/zh/resources/blog/cloud-logging-pricing_701
    > Ref2: https://www.finout.io/blog/reducing-gcp-logging-costs

## 開源祭

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c8b504fbbc94cf77892ae8e45522e7b0.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_74176193601291a39b7171fa2de7ba08.png)

- 擺攤的東西可以放在固定的紙袋，比較容易出門 [name=bil]
- 感謝 OCF 調整場地，十二點的時候雨還很大，不確定如何處理 [name=bil]
- 大活動人力吃緊 [name=bil]

## Open165
- 還在做 detail 頁面 https://github.com/cofacts/open165/pull/26
- HTML content of 165 reported sites; HTML similarity

## 交流

波蘭
有 https://demagog.org.pl/en/lets-introduce-ourselves/ 參與
投影片：https://docs.google.com/presentation/d/1MHVuA80ZC-9-vlWAwBw-xnBzPo-hxwlH42BNyzVnXoI/edit?usp=drive_web&ouid=100298319366825427383


## Conrad
翻譯了橘色海報跟恐龍塗鴉牆

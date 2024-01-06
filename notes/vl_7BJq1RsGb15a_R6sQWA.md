---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220914 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：noah, 4000, cai, nonumpa
- Workis 出席：bil, mrorz
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
- https://github.com/cofacts/rumors-api/releases/tag/release%2F20220908 Similar article for images

#### :globe_with_meridians: Site

- https://github.com/cofacts/rumors-site/releases/tag/release%2F20220908 Similar article for images

#### :robot_face: rumors-line-bot

- https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20220908 Return image search result for chatbot

### :rocket: Staging

Legacy image migration on staging now.


#### :globe_with_meridians: Site
- https://github.com/cofacts/rumors-site/pull/504/files


##### Testing checklist
https://dev.cofacts.tw/articles?articleTypes=IMAGE,TEXT

- [x] 可列出舊圖片
    - [x] 透過不同方式排序、篩選，可以看到舊的熱門圖片
- [x] 可以點開舊圖片的 article
- [x] staging 現有 article 會加入過去的 reply request
    - [x] 例：https://cofacts.tw/article/kYop34IBv5it-Cx_JGBq --> migrate 後：https://dev.cofacts.tw/article/kYop34IBv5it-Cx_JGBq
    - [x] 例：https://cofacts.tw/article/iIra0oIBv5it-Cx_olMW --> migrate 後：https://dev.cofacts.tw/article/iIra0oIBv5it-Cx_olMW
        ```
        {
            GetArticle(id: "iIra0oIBv5it-Cx_olMW") {
            text
            attachmentHash
            createdAt
            lastRequestedAt
            user {
              id
              name
              createdAt
            }
            stats(dateRange: {GT: "2018-01-01"}) {
              date
              lineVisit
              lineUser
            }
          }
        }
        ```
#### :robot_face: rumors-line-bot

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 可查詢舊圖片

##### ⛔️ Release Blockers
##### 未竟項目


## Image support
> https://github.com/orgs/cofacts/projects/9

### Existing image migration

1. [x] 公告 LINE bot、網站將要下線 15 分鐘
2. [x] 確保 drive，production 存放資料的目標資料夾淨空
3. [x] 把 LINE bot server 與網站們下線
   - 杜絕新 media article, replyrequest 生成
4. [x] 備份 production 資料
5. [x] colab 跟 runtime 連線，確定 setup 正確，執行 setup step
6. [x] 執行 colab "Generate Elasticsearch Docs"
7. [x] 執行 curl script and main script
8. [x] 確認 API 可回傳更新後資料
9. [x] Line bot、api server 上線

### Media entry 上傳 GCS 後分析

- Uploaded to GCS
- 但有些 upload.js 算出來的 `gcsKey` 跟當時 hash.js 的 media entry 不太一樣（[分析](https://docs.google.com/spreadsheets/d/1SLRNf3hq26jJunWRvgE1VdeohUVMS_Mlvd-TrsL6b3g/edit#gid=0)）
- TODO
    - 查看原始檔案與 GCS
    - hash 不一的 root cause？
    - 修正 script 填入正確的 hash？
    

### Increasing chatbot server errors
- 現況
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7e2340d94a2a842d70cc695386928142.png)
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6fc3be241793af05e8da746b8484b969.png)
- 過去類似情形處理 https://g0v.hackmd.io/hakuJY45QWe5xb7Csr-gsw#Error-%E7%88%86%E5%A4%A7%E9%87%8F
    - 看 user count
    - 看 nginx log
    - 看 line bot server log

### LIFF image support
- 查過的訊息 articles LIFF 不支援圖片
- article LIFF 亦尚未支援圖片

### audio & video
- 類似 image LINE bot 流程，但加註說還沒完成
- 先上 LINE bot，article 顯示先不管

## Chatbot 上 URL 都是 cofacts.org
- 嘗試調整 `SITE_URLS` 的順序，把 https://cofacts.tw 放第一個
- 調整前：
    ```
    # Cofacts web page URL base, separate by comma.
    # First one will be used to generate article URLs, others will be used to detect article page.
    SITE_URLS=https://cofacts.org,http://cofacts.org,https://cofacts.tw,https://cofacts.g0v.tw
    ```
- 已調整完畢，待深夜重開 line bot server

## 小聚籌備

> 上次檢討 https://g0v.hackmd.io/JfQ03mRCTWiREv2PKWhfDQ#%E5%B0%8F%E8%81%9A%E6%AA%A2%E8%A8%8E

- [ ] 時間:
    - 9/25 (日) 13:30-17:30
- [ ] 場地：台北市中山區民權東路二段46號4樓-401房
    - 小樹屋
        - [巒大衫101](https://thehapp.com/space/267)被訂走了
        - 訂 https://thehapp.com/space/375
        - 需要帶網路、延長線越多越好
    - 打統編
- [ ] 食物？
- [ ] 時間：2022/09/25
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：雙北 + 基隆
- [ ] KKTIX：https://cofacts.kktix.cc/events/cofactseditor32
- [ ] 誰會來呢：bil, mrorz, nonumpa
- [ ] 無法來：
- [ ] LINE 文案 
假新聞四處亂竄，對於厭煩吵架與對立的你，如果用一個下午的時間，參與本次志工活動，將可以對社會創造偉大的貢獻！
Cofacts 真的假的 在9月25日本週日下午 2 點- 5點  ，徵求新的查核協作志工，活動完全免費，現場供應點心，邀請你的到訪與參與！用鍵盤與智慧，為周圍的朋友與大家帶來和諧的力量。
(記得帶筆記型電腦與充電線唷！)
時間：9月25日(日) 下午 2 點- 5點
地點：台北市中山區民權東路二段46號4樓-401房
最近的捷運站是中山國小站 
- [ ] [投影片更新](https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit#slide=id.g13dfd29df0b_0_322)
    - [ ] 有提到個人貢獻圖，但可以加講列表，回來看其他人對自己回應的評價
    - [ ] community builder 增加「我想補充」的數字

---

- 自我介紹引導提問：為什麼來、平常遇到什麼問題、印象最深刻的謠言 [name=cai]
  - 剛才有沒有看到奇怪的訊息或回應可以分享 [name=mrorz]
  - 寫在投影片上 [name=bil]

## g0v 十週年

活動日期：10/23 @ 社創
9/15 截止徵件，抽籤決定，10/10 公佈議程

已報名：
- 表演：沒有人會拿 LINE 謠言講 Stand-up comedy 啦！ [name=mrorz]
    - 單口喜劇。
    - 需要投影機
- 表演：1:30 跳舞 [name=bil]
- 30min 開放工作坊：LINE 傳來的圖是真的假的？網傳圖片查核工作坊 [name=mrorz]
    - Cofacts 真的假的聊天機器人支援圖片囉！在 LINE 上面將圖片分享給 Cofacts 真的假的（ID: @cofacts） 就能看看資料庫裡，是不是有查核協作者已經針對該圖片撰寫查核回應。這個工作坊中，會邀請大家一起成為查核協作者，學習圖片查證技巧。



## LINE 訊息查證

https://fact-checker.line.me/
- 已更新 logo
- 希望修改成 article LIFF - 提案中
- Usage data in 後台


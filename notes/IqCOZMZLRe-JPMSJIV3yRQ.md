---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220921 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz, nonumpa
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

- Matters link hotfix https://github.com/cofacts/rumors-site/releases/tag/release%2F20220915

### :rocket: Staging

#### :robot_face: rumors-line-bot

https://github.com/cofacts/rumors-line-bot/pull/324

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [ ] 應可送出「全新訊息」
- [x] 可應對 100% match、有多則回應的文字訊息
  - [x] 應可顯示回應列表
  - [x] 選擇一個回應之後，可以捲回去選其他回應
- [x] 可應對 100% match、僅有一則回應的文字訊息
  - [x] 應可直接顯示回應
- [x] 可應對 match 到多篇現有文章的文字訊息
  - [x] 若點選的文章只有一個回應，就會直接顯示回應
  - [x] 顯示完回應之後，可以捲回去選其他文章
- [x] 可應對 100% match、有多則回應的圖片
  - [x] 應可顯示回應列表
  - [x] 選擇一個回應之後，可以捲回去選其他回應
- [x] 可應對 100% metch、僅有一則回應的圖片
  - [x] 應可直接顯示回應
- [x] 可應對 match 到多個現有圖片的圖片
  - [x] 若點選的圖片只有一個回應，就會直接顯示回應
  - [x] 顯示完回應之後，可以捲回去選其他圖片

##### ⛔️ Release Blockers
N/A

##### 未竟項目

###### Feedback 無法紀錄

1. 給一圖，觸發兩則圖 A, B
2. 先選一個有多個回應的圖 A，但不選回應
3. 捲回去選單一回應的圖 B，觸發回應
4. 捲回去挑一個 A 的回應顯示
5. 對該回應按「有用」或「沒用」
6. 按關閉，會出現「無法紀錄您的評價」

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4e3523290472d282d074c70c448b5f53.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c4c62d4f5d7ae9523e04dfc77dd4836c.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3d98a03de09c69d104c7ad84959a8ea7.png)
:::info
另開票處理 https://github.com/cofacts/rumors-line-bot/issues/327
:::

###### 沒有實作「找不到我想查的訊息」
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0c6b7309dd626e4abbea154105c3ce08.png)
:::info
另開票處理 https://github.com/cofacts/rumors-line-bot/issues/326
:::

### :eye: Under review
- https://github.com/cofacts/rumors-line-bot/pull/324

## Image support follow-ups

### Media hash mismatch
https://docs.google.com/spreadsheets/d/1SLRNf3hq26jJunWRvgE1VdeohUVMS_Mlvd-TrsL6b3g/edit#gid=0

Root cause:
- 計算 file spreadsheet 時是使用 google drive 的原檔 (mount drive)
- 上傳時是使用 `lh3.googleusercontent.com` 的檔案
- 兩者的 binary 其實不一定一樣！
  - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_04b14d5d8d87134e0458b07cfbef315a.png)
  - 上圖中有兩組圖 hash 一致，另外兩組圖 hash 不一致。hash 不一致的，lh3 與 drive 原檔都不同（lh3 不知為何比較大⋯⋯）
  - `https://drive.google.com/uc?id=<id>` 會與 google drive 一樣，但跑一跑會被 ban
- 解法
  - 準備另一個 entries sheet，用 `https://drive.google.com/uc?id=<id>` 重新上傳
    - Exponential back-off after getting banned
  - 刪掉 hash 不同的 lh3 檔案 (optional)
    - 約 700 多個 hash 不同，應該永遠用不到的檔案

:::success
Proceed with production migration
:::

### Increasing chatbot server errors

- Could not connect
    - LINE ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_76b26e063099550895b7169dceed40aa.png)
    - nginx - 該秒有非常多 API request，只有一個往 webhook 送 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bb83c6102035c33db284ee7c013ab146.png) 
    - 周邊 nginx (line webhook) ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1d719c65bc143d07d78792266d556861.png)
    - chatbot： 沒有記錄到這個 request。
        - 有 20:44:11、20:44:26、20:45:53、20:45:59 的 log
    - Rollbar: 該期間沒有 error
    - 可能是加好友 event 這類不會 log 的 [name=nonumpa]
    - group 裡的 chat event 應該也不會 log [name=mrorz]
    - LINE bot 可能還是有個 request log? (不要有 sensitive content 即可) [name=mrorz]
      - 不然很難 debug 這種 could not connect / request timeout
- Request timeout
    - TBA


### Audio & Video

Wording
- "Checking audio and video is still under construction. But I would still like to help."
- 查詢錄音與影片的功能仍在開發中。不過，我還是想幫你查查看。

Implementation
- `processMedia(): {context, replies}`: search for hash.
  - Tell user that the function is experimental and not finished yet
  - Choose article if match
  - Ask article submission consent if not match
  - (No artcile selection here)
- `webhook/index` otherFields.message.type 是 video 或 audio 時呼叫 `processMedia()`

Observation：今年至今的 message type
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_43ae0a29edbc9f635a4fd188276283ef.png)
- video 遠多過 audio 多，甚至比 image 多
- 似乎可以做個 sticker response

## 小聚 rundown

- [x] 時間:
    - 9/25 (日) 訂13:00-17:30，活動 14:00 ~ 17:00
- [x] 場地：台北市中山區民權東路二段46號4樓-401房
    - 小樹屋
        - 訂 https://thehapp.com/space/375
        - 需要帶網路、延長線越多越好
          - MrOrz 一條
          - nonumpa 2條
        - 延長線：
            - 家用、4.5m、插座角度正確、三孔 https://24h.pchome.com.tw/prod/DSAO10-A82680282?fq=/S/DSAO05
            - 動力延長線？![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c49d4261c04f3d14c4c24b4da803c36c.png) [3m](https://24h.pchome.com.tw/prod/DSAO16-A9009IVOF#Go) [5m](https://24h.pchome.com.tw/prod/DSAO16-A900A9KXY)

    - 打統編
- [ ] 食物
  - [ ] - [在室甜點｜En vie Pâtisserie](https://goo.gl/maps/fin8eCZUcEhcgWpe6)
  - [ ] [阿草的店-錦州店 ](https://goo.gl/maps/HpjUCsasnQ28BFcx8)
- [x] 時間：2022/09/25
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
- [x] 投放目標：雙北 + 基隆
- [x] KKTIX：https://cofacts.kktix.cc/events/cofactseditor32
- [x] 誰會來呢：bil, mrorz, nonumpa
- [x] 無法來：
- [x] LINE 文案 
假新聞四處亂竄，對於厭煩吵架與對立的你，如果用一個下午的時間，參與本次志工活動，將可以對社會創造偉大的貢獻！
Cofacts 真的假的 在9月25日本週日下午 2 點- 5點，徵求新的查核協作志工，活動完全免費，現場供應點心，邀請你的到訪與參與！用鍵盤與智慧，為周圍的朋友與大家帶來和諧的力量。
(記得帶筆記型電腦與充電線唷！)
時間：9月25日(日) 下午 2 點- 5點
地點：台北市中山區民權東路二段46號4樓-401房
最近的捷運站是中山國小站 
- [x] [投影片更新](https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit#slide=id.g13dfd29df0b_0_322)
    - [x] 有提到個人貢獻圖，但可以加講列表，回來看其他人對自己回應的評價
    - [x] community builder 增加「我想補充」的數字

--- 

- 週三會議
    - [x] 週四 8 pm schedule
    > 查核機器人所回應的查證資訊，都是善良的志工一筆一筆新增的。
    >
    > (PC) 在這裡邀請您，即使只是對查證資訊好奇，不限年齡、無論經驗，都能參與本次的查核工作坊。只需要攜帶筆記型電腦，花一個下午的時間，就能習得查核技巧幫助其他的朋友喔！
    >
    > 9月25日（日）14:00-17:00 在臺北市中山區民權東路二段46號4樓-401房，鍵盤志工活動，完全免費，歡迎從未參加過的您，幫助不擅長查證訊息的親戚朋友。
    > 
    > 🔰 這是免費的實體志工聚會，超級歡迎沒有參加過的新手，會在活動中提供查核技巧教學。
    > 
    > 座位有限，請記得報名 👇
    > https://cofacts.kktix.cc/events/cofactseditor32
    > 
    > 📍 地點：小樹屋 楓香分館 / 臺北市中山區民權東路二段46號4樓-401房
    > 🚇 最近的捷運站：中和新蘆線 中山國小站
    >
    - 目標：新北市
    - [x] 換 rich menu
- 週六早上
    - [x] KKTIX 行前通知：提醒時間、使用電腦而非手機
    > Hello 你好，
	>
	> 明天就是 9 月 25 日的志工培訓囉！
	>
	> 志工培訓需要大量查詢資料，請自備筆電 💻 與充電器 🔌 並帶著愉快的心情來參加。帶順手的平板也可以的！
	> 
	> 😷 疫情期間，參與培訓須佩戴口罩。場地備有飲水機，請攜帶自己的杯子或水瓶取用唷 🚰 ！
	>
	> 時間：9/25（日）14:00
	> 地點： Happ. 小樹屋｜楓香分館 401 室（臺北市中山區民權東路二段46號4樓-401房）
	> 
	> 費用全免，會很準時開始。
	> 
	> Cofacts 真的假的 查核協作 VIP 臉書社團在這裡 👉 https://www.facebook.com/groups/cofacts
	> 說你會來查核小聚優先加入 ＝Ｄ
	> 
    > 🤒 最後，如果這幾天成為了密切接觸者、不幸確診、或是自覺有染疫風險而希望減少接觸，請記得要取消報名唷！小聚每兩個月就有一次，還是歡迎參與未來的活動。 
	>
	> 感謝你的閱讀。
	>
	> 那麼明天見囉😊
	>
	> 比鄰敬上
    - [x] 開場使用材料更新：https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit [name=mrorz]
	- [x] 準備 Slido `#cofacts32`
		- [x] 放投影片網址
    - [x] 幫 Netgear 充電
- 當日準備 / 攜帶
    - [x] 樓下用的標語
    - [ ] 貼紙 - bil
    - [x] 黏土 - orz
    - [x] 延長線 x 1 - mrorz
    - [ ] 延長線 x 2 - nonumpa
    - [x] 編輯小聚的牌子 - orz
    - [x] Wifi 機 - mrorz
        - [x] Netgear 本體
            - [x] usb type-c 充電線與插座 （已充飽電，無需插座）
            - [x] 電池
            - [x] 4G 天線
        - [x] Asus RT-N12
            - [x] 電源線
            - [x] 5dBi 天線
            - [x] RJ45 線
- 13:00 - 場佈
  - [x] 簽到、噴酒精、量體溫
  - [x] 排桌子椅子
  - [ ] 麥克風
  - [x] 延長線佈置
  - [x] 門口黏引導牌
  - [x] Slido - 白紙寫 slido room number `#cofacts32`
  - [x] WIFI
      - [x] 佈機x2
      - [x] 連結 netgear 與 asus WAN port
      - [x] 白紙寫 SSID Cofacts meetup(_5G) + wifi password 貼牆上
      - [x] 192.168.2.1 進入 netgear admin 看 asus 的 IP
      - [x] 開好兩台 router admin 監測連網狀態
      - [x] (optional) netgear 換成 5GHz only?
  - [x] 投影的電腦用 google chrome 開好
    - [x] Google Chrome tab: [投影片](https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit)
    - [x] Google Chrome tab: [Bignum](https://cofacts.github.io/community-builder/#/bignum/setup)
    - [x] Google Chrome tab: [KKTIX](https://cofacts.kktix.cc/events/cofactseditor32)
    - [x] Google Chrome tab: [Slido admin](https://admin.sli.do/event/kKaauw9TMs5EbDq9fdVD6J/)
    - [x] Google Chrome tab: [Slido]()
    - [x] Google Chrome tab: [開場影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNVuJ9S-In4k93trnO_D2s6R)
    - [x] BGM
    - [ ] Analytics
- 14:00 - 14:20 開場
    - 放[影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs) 8min
    - 場地、Slido、Cofacts 機器人系統簡介
- 14:20 - 14:40：引導註冊網站、介紹評價現有回應
- 14:40 - 14:50：實作評價
    - 讓大家從網站找訊息按讚
    - 提醒 15:00 結束時會問大家有沒有想要分享的心得
- 14:50 - 15:10 介紹補充資訊
- 15:10 - 15:40 實作補充資訊、自我介紹、休息
    - 閒聊「看到覺得最好的回應、覺得哪裡好」
- 15:40 - 16:10：介紹撰寫新回應
- 16:10 - 16:40：實作撰寫新回應
    - 大家從網站挑選「一篇」覺得最有興趣的回
- 16:40 - 17:00 介紹 RSS、社群、合照

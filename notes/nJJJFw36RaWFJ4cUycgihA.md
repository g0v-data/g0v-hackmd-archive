---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240318 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO hub: bil, nonumpa, mrorz
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## CCPRIP
### [Op] Transcript spam
> nonumpa
> https://g0v.hackmd.io/vKCvrqSQTlm7GEx9MAXGaw?view#op-Transcript-spam-處理
> 

https://github.com/cofacts/rumors-api/pull/335
- ai reply test snapshot 不知道要怎麼更新
  - 真的有去打 openai 的話，可能要 mock 掉他 [name=mrorz]
- appId 要設定成 'WEBSITE' 才能拿得到 `user`
  - 直接寫入 elasticsearch 的話 ok [name=mrorz]
- migration 還要修一下，反向 query userid
  - 要即時生成查詢還是存下來？這樣比較不會又變 [name=orz]
  - 即時生成比較簡單
- 有 ydoc 沒逐字稿的狀況，逐字稿是空的
  - 應該是沒有講話的 [name=nonumpa]
- contributor fields 沒有要寫 createdAt, 只有 lastUpdatedAt --> 改成 updatedAt
  - 加上 createdAt 比較麻煩 [name=nonumpa]
  - 使用者應該會對 updatedAt（最後改過的時間）比較有印象 [name=orz]
  - 只放 updatedAt [name=nonumpa]
  - 要 reindex articles table

### [Comm] article group 收尾
> nonumpa

### [Op] Google 非營利
- 2/28 Percent: 沒有辦法確認我跟非營利的關聯性。來信要求 (1) Voided bank deposit slip, (2) Officially approved governing documents, or (3) Confirmation of your association with the nonprofit e.g contract, ID card. 
- 2/29: 回信交付當選證明書、護照
- 3/9: Follow up
- 3/14: Percent:
	> We are just reviewing your application and will update you as soon as possible. 
	> Please note the review process can take up to 5 business days to complete. 
	> Thanks for your patience, it's really appreciated.

## 小聚 rundown

- [ ] 日期：3/24 (日)
- [ ] 食物：要自己清，垃圾桶不能丟
- [ ] 場地：新北青職基地 1F
    - 一定要 20 人以上，最多坐 60
    - 6 個桌子、20 張椅子、麥克風、投影幕、筆電
- [x] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Slido 暖身
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [x] 投放目標：
  - 推播日：3/18 (一)推播
  - 推播日之前：新北志工優先報名
  - 目標：雙北、桃園？
      - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_aff7fe2b732675b4b90f1e90a56fd071.png)
    - 14 萬人收到、萬分之2報名率 --> 開 30~40 人、預期 20 人到場？
    - Ref: [past click through rates](https://docs.google.com/spreadsheets/d/1XjEQZ9esNKfkGd8XYd1p3E8DTgB0f5QPDl5ghf-JxE0/edit#gid=0)
- [x] KKTIX:https://cofacts.kktix.cc/events/cofactseditor41
- [x] 誰會來呢：bil, mrorz, nonumpa
- [ ] 記得帶：貼紙、環保杯
- [x] LINE 文案
Cofacts 要來到新北市舉辦免費的志工培訓啦，三鐵共構板橋站，交通超級方便唷！
地址：新北市青職基地 / 新北市板橋區民權路170號1樓
時間：03月24日（日）14:00-17:00(會很準時開始)請記得攜帶筆記型電腦喔！
活動報名：https://cofacts.kktix.cc/events/cofactseditor41
- [x] VOOM 發文

----

## 小聚 Rundown

- 週一會議
    - [x] 週一 19:00 pm schedule
    - [x] 換 rich menu
- 週五早上
    - [ ] KKTIX 行前通知：提醒時間、使用電腦而非手機
    > Hello 你好，
	>
	> 本週日就是 3 月 24 日的志工培訓囉！
	>
	> 志工培訓需要大量查詢資料，請自備筆電 💻 與充電器 🔌 並帶著愉快的心情來參加。帶順手的平板也可以的！如果願意協助編修影片逐字稿，請自備耳機唷🎧！
	>
	> 🕒 時間：3/24（日）14:00
	> 📍 地點：新北市青年局青職基地 / 新北市板橋區中山路一段 166 號 1 樓
	> 
	> 費用全免，會很準時開始。若不克前往，記得取消報名 :)
	> 
	> Cofacts 真的假的 查核協作 VIP 臉書社團在這裡 👉 https://www.facebook.com/groups/cofacts
	> Cofacts 真的假的 查核協作 Discord 在這裡 👉  https://cofacts.tw/discord
	> 說你會來查核小聚優先加入 ＝Ｄ
	> 
	> 感謝你的閱讀。
	>
	> 那麼後天見囉😊
	>
	> 比鄰敬上
    - [ ] 開場使用材料更新：https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit [name=mrorz]
	- [ ] 準備 Slido `#cofacts41`
		- [ ] 放投影片網址
    - [ ] 幫 Netgear 充電
- 當日準備 / 攜帶
    - [ ] 樓下用的標語 - orz
    - [ ] 貼紙 - orz, bil
    - [ ] 黏土 - orz
    - [ ] 手板 - bil
    - [ ] 一次性杯子 - bil
    - [ ] 延長線
    - [ ] 編輯小聚的牌子 - orz
    - [ ] Wifi 機 - mrorz
        - [ ] Netgear 本體
            - [ ] usb type-c 充電線與插座 （已充飽電，無需插座）
            - [ ] 電池
            - [ ] 4G 天線
        - [ ] Asus RT-N12
            - [ ] 電源線
            - [ ] 5dBi 天線
            - [ ] RJ45 線
- 13:30 - 場佈
  - [ ] 簽到（問飲料）
  - [ ] 排桌子椅子
  - [ ] 麥克風
  - [ ] 延長線佈置
  - [ ] 門口黏引導牌
  - [ ] Slido - 白板寫 slido room number `#cofacts41`
  - [ ] WIFI
      - [ ] 佈機x2
      - [ ] 連結 netgear 與 asus WAN port
      - [ ] 白紙寫 SSID Cofacts meetup(_5G) + wifi password 貼牆上
      - [ ] 192.168.2.1 進入 netgear admin 看 asus 的 IP
      - [ ] 開好兩台 router admin 監測連網狀態
      - [ ] (optional) netgear 換成 5GHz only?
  - [ ] 投影的電腦用 google chrome 開好
    - [ ] Google Chrome tab: [投影片](https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit)
    - [ ] Google Chrome tab: [Bignum](https://cofacts.github.io/community-builder/#/bignum/setup)
    - [ ] Google Chrome tab: [KKTIX](https://cofacts.kktix.cc/events/cofactseditor40)
    - [ ] Google Chrome tab: [Slido admin](https://admin.sli.do/event/nm76YwhjPaWEMvAgvELMLp/home)
    - [ ] Google Chrome tab: [Slido](https://wall.sli.do/event/nm76YwhjPaWEMvAgvELMLp?section=1b43b8ac-95c8-4b6a-8b21-1f92464b0c21)
    - [ ] Google Chrome tab: [開場影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs)
    - [ ] BGM
    - [ ] Analytics
- 14:00 - 14:20 開場
    - 放[長影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs) 8min
    - 場地、Slido、Cofacts 機器人系統簡介
- 14:20 - 14:40：引導註冊網站、介紹評價現有回應
- 14:40 - 14:50：實作評價
    - 讓大家從網站找訊息按讚
- 14:50 - 15:10 介紹補充資訊
- 15:10 - 15:40 實作補充資訊、自我介紹、休息
    - 閒聊「看到覺得最好的回應、覺得哪裡好」
- 15:40 - 16:10：介紹撰寫新回應
- 16:10 - 16:40：實作撰寫新回應
    - 大家從網站挑選「一篇」覺得最有興趣的回
- 16:40 - 17:00 介紹 RSS、社群、合照

:::success
- 比鄰問場地是否有延長線
  - 可能有飲料或小點心
:::

## 健保

bil 研究一下

## 下架

- 移置，文字會跑進 takedown，原文會修改為「應要求後修改」並附上 takedowns 連結
- 窗口有來信跟來電
- 詢問句，並非網傳訊息本身
- 不會修改回應 - 跟來信人無關
- 不會修改 reply request - 沒 upvote 不會顯示、他們也確實有查
  - reply request 內容無法查

本日金句：
- 辣椒醬與本次的例子：大家想要自己的言論自由，然後 sensor 別人 [name=bil]

## 四月開會
- 4/1 實體開會
- 4/8 比鄰在美國東岸 --> 線上
- 4/15 --> 不確定，要的話也是線上
- 4/22 可以，實體開會可
- 4/29 --> 換到 5/2 (四)


---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220720 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
- Image variants https://github.com/cofacts/rumors-api/releases/tag/release%2F20220714

#### :globe_with_meridians: Site
- attachment variant & filter in profile https://github.com/cofacts/rumors-site/releases/tag/release%2F20220714

#### :robot_face: rumors-line-bot
- LINE proxy https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20220714

### :eye: Under review

## Image support
> https://github.com/orgs/cofacts/projects/9

- Cache 問題 follow-up ([上週](https://g0v.hackmd.io/AqvBLZNmS4uAGMmuNQSgVg?view#Image-support))
  - Cache header works [name=nonumpa]
- hero 旁邊背景用白色比較好 [name=nonumpa]
  - 若為 pillar box 可以與上下融合 [name=mrorz]
- 選第幾張 / 選 reply：handle postback 的 image & text 可以共用 [name=nonumpa]
  - 選 article & reply 都有 ID，應該不會過期
  - 所以應該可以支援捲回去選過去的 article carousel & reply carousel (?) [name=mrorz]

## Trend and contribution
> https://github.com/orgs/cofacts/projects/10

- No progress this week

## Moderation

### 回信

> 前情提要：https://g0v.hackmd.io/AqvBLZNmS4uAGMmuNQSgVg?both#%E6%94%BF%E6%B2%BB%E7%AB%8B%E5%A0%B4%E4%B8%8D%E5%90%8C%E8%80%85%E7%9A%84%E6%AA%A2%E8%88%89

:::success
bil 回信
:::

## 小聚 rundown

新投影片：https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit#slide=id.gc4cef832ac_0_124

任務二新順序

1. 介紹列表、挑訊息
2. 不在查證範圍
3. 找脈絡
   - 介紹「我想補充」
   - 提供「我想補充」案例
   - 進階：介紹以圖找圖
:::info 
Q: 是否要放練習時間（？）
或者把自我介紹移動到這裡
--> 自我介紹移動

- 挪動放影片時間？ [name=bil]
  - 影片是為了讓大家進場，在 4F 的話可能還是需要影片
  - 只放 simpleinfo & 第一次小聚的影片
:::
4. 介紹撰寫新回應功能
   - 要填的欄位
   - 呈現方式
5. 事實陳述 v.s. 意見表達
   - 與「我認為」欄位的對應
   - 用事實回應「事實陳述」
     - 驗證人事時地物
     - 進階 google 技巧：時間
   - 回應「意見表達」
     - 訊息框架
     - 陰謀論
6. 撰寫回應
   - 文字編排技巧
   - 選擇好出處
     - Wikipedia
     - 避開內容農場

### Rundown

- [x] 時間:
    - [7/24 (日) 13:30-17:30](https://g0v-slack-archive.g0v.ronny.tw/index/channel/C0385B90D/2022-06#ts-1656553121.3964)
    - 四樓廚房
    - keyholder Ronny
- [ ] 主題：
- [x] 場地：
    - [NPO Hub 四樓廚房](https://g0v.hackmd.io/@jothon/NPOHub-rules)
- [ ] 食物 ：[提案仙草](https://teddy0411.pixnet.net/blog/post/467502608-屋琥甜冰品｜陳皮的日常-懷舊綜合冰-中正紀)
- [x] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Keyholder 介紹場地
        - 2:20 - 2:40 介紹 mission 1 -幫其他查核者評審回應
        - 2:40 - 3:00 進行評價 (10則)、介紹 mission 2 part 1
        - 3:00 - 3:30 自我介紹、交流、寫 comment(?)
        - 3:30 - 3:50 介紹 mission 2 - 寫回應
        - 3:50 - 4:30 進行回應（1則）
        - 4:30 - 5:00 介紹分類、RSS、合照
- [x] 投放目標：新北市 only
    - 介紹青年局志工活動: 要寫青年局協辦
- [x] KKTIX：https://cofacts.kktix.cc/events/cofactseditor31
- [ ] 誰會來呢：mrorz, bil, nonumpa, lucien
- [ ] 無法來：
- [ ] LINE 文案
真的假的？？？安倍的保安人員在奈良醫院前切腹？美國來的疫苗會改變基因讓小孩生出來不像自己？假訊息太多了，需要志工投入！幫助自己也幫助別人。
7月24日（日）14:00-17:00 在ＮＰＯ ＨＵＢ 4樓廚房，（最近的捷運站是中正紀念堂站）鍵盤志工實體活動，完全免費，歡迎從未參加過的您，一起幫助不擅長查證訊息的親戚朋友。
（請自行攜帶筆記型電腦、充電線與水杯）
請先報名：KKtix


--- 

- 週三會議
    - [x] 週四 8 pm schedule
    > 查核機器人所回應的查證資訊，都是善良的志工一筆一筆新增的。
    >
    > (PC) 在這裡邀請您，即使只是對查證資訊好奇，不限年齡、無論經驗，都能參與本次的查核工作坊。只需要攜帶筆記型電腦，花一個下午的時間，就能習得查核技巧幫助其他的朋友喔！
    >
    > 7月24日（日）14:00-17:00 在ＮＰＯ ＨＵＢ 4樓廚房，（最近的捷運站是中正紀念堂站）鍵盤志工活動，完全免費，歡迎從未參加過的您，幫助不擅長查證訊息的親戚朋友。
    > 
    > 🔰 這是免費的實體志工聚會，超級歡迎沒有參加過的新手，會在活動中提供查核技巧教學。
    > 
    > 座位有限，請記得報名 👇
    > https://cofacts.kktix.cc/events/cofactseditor31
    > 
    > 📍 地點：NPO Hub Taipei 4 樓 / 100台北市中正區重慶南路三段2號 4 樓
    > 🚇 最近的捷運站：中正紀念堂站2號出口
    >
    - 目標：新北市
    - [x] 換 rich menu
- 週六早上
    - [x] KKTIX 行前通知：jitsi 網址、提醒時間、使用電腦而非手機
    > Hello 你好，
	>
	> 明天就是 7 月 24 日的志工培訓囉！
	>
	> 志工培訓需要大量查詢資料，請自備筆電 💻 與充電器 🔌 並帶著愉快的心情來參加。帶順手的平板也可以的！
	> 
	> 😷 疫情期間，參與培訓須佩戴口罩。場地在半室外的空間備有飲水機，請攜帶自己的杯子或水瓶取用唷 🚰 ！
	>
	> 時間：07/24（日）14:00
	> 地點：NPO Hub Taipei 4 樓 （台北市中正區重慶南路三段2號4樓，請在自動門前按門鈴）
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
	- [x] 準備 Slido `#cofacts31`
		- [x] 放投影片網址
    - [ ] 幫 Netgear 充電ㄉ
- 當日準備 / 攜帶
    - [x] 樓下用的標語
    - [ ] 貼紙 - bil
    - [x] 黏土 - orz
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
  - [ ] 簽到、實聯制、噴酒精、量體溫
  - [ ] 排桌子椅子
  - [ ] 麥克風
  - [ ] 門口黏引導牌
  - [ ] Slido - 白紙寫 slido room number `#cofacts31`
  - [x] WIFI
      - [x] 佈機x2
      - [x] 連結 netgear 與 asus WAN port
      - [x] 白紙寫 SSID Cofacts meetup(_5G) + wifi password 貼牆上
      - [ ] 192.168.2.1 進入 netgear admin 看 asus 的 IP
      - [ ] 開好兩台 router admin 監測連網狀態
      - [ ] (optional) netgear 換成 5GHz only?
  - [x] 投影的電腦用 google chrome 開好
    - [x] Google Chrome tab: [投影片](https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit)
    - [x] Google Chrome tab: [Instant](https://cofacts.github.io/community-builder/#/bignum?start=2022-07-24T14%3A00&panels=replied&panels=feedback)
    - [x] Google Chrome tab: [KKTIX](https://cofacts.kktix.cc/events/cofactseditor31)
    - [x] Google Chrome tab: [Slido admin](https://admin.sli.do/event/ovxkey63TiVQWjg85TNKeS/questions)
    - [x] Google Chrome tab: [Slido]()
    - [x] Google Chrome tab: [開場影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNVuJ9S-In4k93trnO_D2s6R)
    - [ ] BGM
    - [ ] Analytics
- 14:00 - 14:20 開場
    - 放[影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs) 8min
    - 場地、Slido、Cofacts 機器人系統簡介
- 14:20 - 14:40：介紹 mission 1 - 按讚
    - 介紹「幫回應按讚」的用途，以及怎麼做；什麼樣的回應可以按「有用」、哪些可以跳過、哪些真的母湯要按「沒用」，如何就事論事的給 feedback
- 14:40 - 14:50：按讚時間 10 min
    - 讓大家從網站找訊息按讚
    - 提醒 15:00 結束時會問大家有沒有想要分享的心得
- 14:50 - 15:10 介紹 mission 2 part 1
    - 介紹我想補充、以圖找圖
- 15:10 - 15:40 自我介紹、交流、寫 comment
    - 閒聊「看到覺得最好的回應、覺得哪裡好」
- 15:40 - 16:00：介紹 mission 2 - 寫新回應
    - 如何找全文、拆解回應、附出處
- 16:00 - 16:30：挑回應來回
    - 大家從網站挑選「一篇」覺得最有興趣的回
    - 回完之後如果行有餘力，再挑一篇
- 16:30 - 17:00
    - 介紹 RSS、社群、合照

---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220511 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz, nonumpa, cai
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
- Multimedia phase 0 https://github.com/cofacts/rumors-api/releases/tag/release%2F20220505

#### :globe_with_meridians: Site
- Update node & npm package https://github.com/cofacts/rumors-site/releases/tag/release%2F20220505

## 送出流程 funnel

- 5/2

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7017ca275553c1d0b6749f613f30ef2c.png)

- 詢問是否轉傳 4,243
- 有回應是否轉傳（是+否） 2,045 (Response rate: 48%)
  - 是轉傳訊息、詢問公開意願 1,676 (82% of responses; 40% of asked)
- 有回應公開意願（是+否）1,224 (Response rate: 73%)
  - 願意公開 1,118 (91% of responses, 67% of asked)
- 送出後（或訊息沒回應後）另外點開 comment LIFF: 374

對比：[2020 年 8 月數字](https://g0v.hackmd.io/r3NK7xssSwCNPFxthlw7tA?view#chatbot-%E4%B8%8D%E5%95%8F%E4%BE%86%E6%BA%90)（當時[尚未上線 onboarding 教學](https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20201105)）
- 顯示按鈕：644 + 12 + 120 = 776
- 成功打開 LIFF：181 (Conversion rate: 23%)
- 點按 LIFF 按鈕（含陷阱）：152（Conversion rate: 84%）

---

- 有看到一兩個把新訊息當成補充貼進來的狀況 [name=mrorz]
  - 可能因為他 LINE bot 停留在上一次送出，就點開補充按鈕
  - 可以再觀察

## Media manager
https://github.com/orgs/cofacts/projects/9

- No progress on my side [name=mrorz]
- Website display image (list / article page) [name=nonumpa]
  - PR on Saturday

本週預計：
- 先修 website [category downvote bug](https://github.com/cofacts/rumors-site/issues/486) QQ [name=mrorz]
- [cofacts/design#1](https://github.com/cofacts/design/issues/1) image / text in article list 混排 v.s. 分開排 figma [name=mrorz]
- [cofacts/rumors-api#277](https://github.com/cofacts/rumors-api/issues/277) Kick-off cofacts media manager repo [name=mrorz]

## Trend and Contribution
https://github.com/orgs/cofacts/projects/10

本週預計
- Design fields for LIFF trend, comment in [cofacts/rumors-api#281](https://github.com/cofacts/rumors-api/issues/281)
- [cofacts/rumors-db#57](https://github.com/cofacts/rumors-db/issues/57), [cofacts/rumors-db#58](https://github.com/cofacts/rumors-db/issues/58)

## 違規檢舉案例

https://cofacts.github.io/community-builder/#/editorworks?type=1&day=365&userId=6CbfdYABvUvLpBdg_Hz_&showAll=1

> 這個好難喔
到底是受害者還是詐騙集團
從看他回應、對其他人的 feedback (有在拉人加自己 ID) 與 comment 看不出來⋯⋯
> [name=mrorz]
> https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1652070487.332199

- 露出自己 ID 是一種打廣告，處理才能回應檢舉人 [name=bil]

:::success
- 提及 fu760913(二次詐騙)者：清除 fu760913 ID
- 廣告：ohje0310 --> 被檢舉後刪除
:::

鹽水漱口 CIB：
https://www.facebook.com/groups/cofacts/posts/3270473376517802/

- [過去針對 CIB 的討論](https://g0v.hackmd.io/@johnson/HykZ8rq4H#%EF%BC%88%E6%9C%AA%E9%9B%A8%E7%B6%A2%E7%B9%86%EF%BC%89CIB-%E8%99%95%E7%90%86)
  - 使用者條款裡沒有說 CIB 怎麼處理
  - FB group 公開事證後討論
- 針對此案
  - 回應已經用現有方式（downvote / 回新的更好的回應）處理
  - feedback 明顯有協同（連續時間、不重複；可以再檢查註冊時間）

:::success
- 預計處理方式：
  - block 3 名按讚者
  - 回應均保留
- 公開以上資訊與預計的處理方式，若無異議就執行
:::

## 自然醫學陳俊旭要求下架

2022/5/10 OCF 通知收到來自陳俊旭的存證信函
要求 Cofacts 下架「不實言論」
但沒有附上 Cofacts URL、或要求下架之內容等等，不知所指何物

- 所附之「妨害名譽」附件均為其他部落格的內容
- 附上規範指出「保健食品」不該聲稱療效 [name=bil]
- 回應時可以贊同增加免疫力，但指出資訊與 COVID 的關聯未經實證，使用上仍應配合有實證資料之疫苗或抗病毒藥物 [name=mrorz]


## 小聚 rundown

Q: 防疫相關
- 建議自己帶杯子、不提供食物
- 要求疫苗狀態 / 採檢狀態？
  - 請大家斟酌自己的狀態
- 提供線上參與選項（因應匡列） / 全部線上參與？
  - 不會開線上參與
- 掌握參與者聯絡方式？
  - 明確說明 email 會用於防疫聯繫
  - 參與活動後三日內（～週三）若確診，請聯繫 cofacts@googlegroups.com
- 減少人數，加大距離？
  - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9fa71bc255d78cffdc2f64b9c6af82d2.png =x300)
  - 一張桌子坐 2 人，坐斜對角
  - 3x3 排放，18 個位子
  - 開放報名 20 人，抓 6 成報到率?
    - 目前開 25
    - 應該是不會超過 18
  - 可以理解缺席（行前通知信提醒）

---

- 週三會議
    - [x] 週四 8 pm schedule
    > 查核機器人所回應的查證資訊，都是善良的志工一筆一筆新增的。
    >
    > (PC) 在這裡邀請您，即使只是對查證資訊好奇，不限年齡、無論經驗，都能參與本次的查核工作坊。只需要攜帶筆記型電腦，花一個下午的時間，就能習得查核技巧幫助其他的朋友喔！
    >
    > 2022年真的假的編輯志工教學聚會，就在2022年05月15日(星期日)下午2:00-5:00
    > 在 NPO Hub Taipei（台北市中正區重慶南路三段2號2樓），活動完全免費。
    > 
    > 🔰 這是免費的實體志工聚會，超級歡迎沒有參加過的新手，會在活動中提供查核技巧教學。
    > 
    > 座位有限，請記得報名 👇
    > https://cofacts.kktix.cc/events/cofacteditor30
    > 
    > 📍 地點：NPO Hub Taipei 2 樓 / 100台北市中正區重慶南路三段2號 2 樓
    > 🚇 最近的捷運站：中正紀念堂站2號出口
    >
    - 圖：https://www.figma.com/file/zwThV99c4dHkFdIPg3Ii0T/Cofacts-%E7%99%BC%E6%96%87%E7%94%A8%E5%9C%96?node-id=978%3A19
    - 目標：北北基桃
    - [x] 換 rich menu
- 週六早上
    - [x] KKTIX 行前通知：jitsi 網址、提醒時間、使用電腦而非手機
    > Hello 你好，
	>
	> 明天就是 5 月 15 日的編輯小聚囉！
	>
	> 編輯小聚需要大量查詢資料，請自備筆電 💻 與充電器 🔌 並帶著愉快的心情來參加。帶順手的平板也可以的！
	> 
	> 😷 疫情期間，參與小聚必須全程佩戴口罩，也不開放飲食。場地在半室外的空間備有飲水機，請攜帶自己的杯子或水瓶取用唷 🚰 ！
	>
	> 時間：05/15（日）14:00
	> 地點：NPO Hub Taipei 2 樓 （台北市中正區重慶南路三段2號2樓，沿著樓梯走）
	> 
	> 費用全免，會很準時開始。
	> 
	> Cofacts 真的假的 查核協作 VIP 臉書社團在這裡 👉 https://www.facebook.com/groups/cofacts
	> 說你會來編輯小聚優先加入 ＝Ｄ
	> 
    > 🤒 最後，如果這幾天成為了密切接觸者、不幸確診、或是自覺有染疫風險而希望減少接觸，請記得要取消報名唷！小聚每兩個月就有一次，還是歡迎參與未來的活動。 
	>
	> 感謝你的閱讀。
	>
	> 那麼明天見囉😊
	>
	> 比鄰敬上
    - [x] 開場使用材料更新：https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit [name=mrorz]
    - [x] 準備空 Spreadsheet + 上 bit.ly 短網址
    	- [x] https://bit.ly/cofacts30-1 （[樣板檔](https://docs.google.com/spreadsheets/d/1K_2WYW-yZ2gbQbFteJxNfrx9xKHBtKbq6ejsuZ2B8OU/edit#gid=0)）
    	- [x] https://bit.ly/cofacts30-2 （[樣板檔](https://docs.google.com/spreadsheets/d/1j75M_qh7s1JE0hUx3YQHN6-ncL6u2gMCdoHfm1sweeI/edit#gid=0)）
	- [x] 準備 Slido `#cofacts30`
		- [x] 放投影片網址 + spreadsheet 1
    - [x] 幫 Netgear 充電
- 當日準備 / 攜帶
    - [x] 樓下用的標語
    - [x] 產生「有回過、沒 feedback」 spreadsheet [name=nonumpa]
        - 每人 20 篇
        - 25 人
        - 只產出 `repliedButNotEnoughFeedback` 的網址
        - [x] 匯入進 https://bit.ly/cofacts30-1
    - [x] 產生「沒回過」spreadsheet
        - 每人 5 篇
        - 25 人
        - 只產出 `newest, mostAsked` 的網址
        - [x] 匯入進 https://bit.ly/cofacts30-2
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
  - [x] 排桌子椅子
  - [x] 麥克風
  - [ ] 門口黏引導牌
  - [ ] Slido - 白紙寫 slido room number `#cofacts30`
  - [ ] WIFI
      - [ ] 佈機x2
      - [ ] 連結 netgear 與 asus WAN port
      - [ ] 白紙寫 SSID Cofacts meetup(_5G) + wifi password 貼牆上
      - [ ] 192.168.2.1 進入 netgear admin 看 asus 的 IP
      - [ ] 開好兩台 router admin 監測連網狀態
      - [ ] (optional) netgear 換成 5GHz only?
  - [ ] 投影的電腦用 google chrome 開好
    - [ ] Google Chrome tab: [投影片](https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit)
    - [ ] Google Chrome tab: [Instant](https://cofacts.github.io/community-builder/#/bignum?start=2022-05-15T14%3A00&panels=replied&panels=feedback)
    - [ ] Google Chrome tab: [KKTIX](https://cofacts.kktix.cc/events/cofacteditor28)
    - [ ] Google Chrome tab: [Slido admin]()
    - [ ] Google Chrome tab: [Slido]()
    - [ ] Google Chrome tab: [開場影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs)
    - [ ] BGM
- 14:00 - 14:20 開場
    - 放[影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs) 8min
    - 場地、Slido、Cofacts 機器人系統簡介
- 14:20 - 14:40：介紹 mission 1 - 按讚
    - 介紹「幫回應按讚」的用途，以及怎麼做；什麼樣的回應可以按「有用」、哪些可以跳過、哪些真的母湯要按「沒用」，如何就事論事的給 feedback
- 14:40 - 15:00：按讚時間
    - 讓大家從 Slido 打開 spreadsheet 1，直接點進自己名字的那個 sheet
    - 然後幫每一篇按有用或沒用
    - 提醒 15:00 結束時會問大家有沒有想要分享的心得
- 15:00 - 15:30 休息、自我介紹、交流
    - 閒聊「看到覺得最好的回應、覺得哪裡好」
- 15:30 - 15:50：介紹 mission 2 - 寫新回應
    - 如何找全文、拆解回應、附出處
- 15:50 - 16:30：挑回應來回
    - 大家從 Slido 打開 spreadsheet 2，直接點進自己名字的那個 sheet
    - 先挑選「一篇」覺得最有興趣的回
    - 回完之後如果行有餘力，再挑一篇
    - 如果都覺得不想回，去「等你來答」挑，不要硬回 XDDD
- 16:30 - 17:00
    - 讓大家講感想
    - 介紹 RSS、文章列表、filter 功能、合照



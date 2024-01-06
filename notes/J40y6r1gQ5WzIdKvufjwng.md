---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220309 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz, nonumpa
- 線上出席：kukka
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: rumors-line-bot

https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20220304

## 群組 threshold 變更後狀況

- 2/24 修復
- 3/4 修改 Threshold

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1e8e516615ea67e253ecb1156b975355.png)

3/4 ~ 3/8
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dd24aab2406fe2ed504446e39a1ed104.png)

- Identical doc rate = 455/1745 = 26%
- Valid category & reply rate = 66/455 = 14%

---

- 調降門檻檻起來沒有影響太多 ~~valid article rate~~
    - ~~可能大多數都是 category 在擋~~
    - 可能本來就很像的才會觸發
- 實際被濾掉什麼？
    - https://datastudio.google.com/reporting/56235ef2-b283-4dcf-a771-160c0c295aa7/page/wZanC
    - 非公開，最左邊可能有些群組內訊息，只是有 search hit 但沒有很像


## 小聚 rundown

- 週三會議
    - [x] 週四 8 pm schedule
    > 查核機器人所回應的查證資訊，都是善良的志工一筆一筆新增的。
    >
    > (PC) 在這裡邀請您，即使只是對查證資訊好奇，不限年齡、無論經驗，都能參與本次的查核工作坊。只需要攜帶筆記型電腦，花一個下午的時間，就能習得查核技巧幫助其他的朋友喔！
    >
    > 2022年真的假的編輯志工教學聚會，就在2022年03月12日(星期六)下午2:00-5:00
    > 在 NPO Hub Taipei（台北市中正區重慶南路三段2號 2樓），活動完全免費。
    > 
    > 🔰 這是免費的實體志工聚會，超級歡迎沒有參加過的新手，會在活動中提供查核技巧教學。
    > 
    > 座位有限，請記得報名 👇
    > https://cofacts.kktix.cc/events/cofacteditor29
    > 
    > 📍 地點：NPO Hub Taipei 2 樓 / 100台北市中正區重慶南路三段2號 2 樓
    > 🚇 最近的捷運站：中正紀念堂站2號出口
    >
    - 圖：https://www.figma.com/file/zwThV99c4dHkFdIPg3Ii0T/Cofacts-%E7%99%BC%E6%96%87%E7%94%A8%E5%9C%96?node-id=978%3A19
    - 目標：北北基桃
    - [x] 換 rich menu
- 週五早上
    - [x] KKTIX 行前通知：jitsi 網址、提醒時間、使用電腦而非手機
    > Hello 你好，
	>
	> 明天就是 3 月 12 日的編輯小聚囉！
	> 編輯小聚需要大量查詢資料，請自備筆電 💻 與充電器 🔌 並帶著愉快的心情來參加。帶順手的平板也可以的！
	>
	> 時間：03/12（六）14:00
	> 地點：NPO Hub Taipei 2 樓 （台北市中正區重慶南路三段2號2樓，沿著樓梯走）
	> 當天 2 樓有兩場活動——「g0v 基礎松」與這個「Cofacts 編輯小聚」。如果怕走錯場，可以開口問人唷！
	> 
	> 費用全免，會很準時開始。
	> 
	> Cofacts 真的假的 查核協作 VIP 臉書社團在這裡 👉 https://www.facebook.com/groups/cofacts
	> 請先加入吧＝Ｄ說你會來編輯小聚優先加入（真的）
	> 
    > 另外，如果不克出席，也請記得取消報名唷！也歡迎參與未來的小聚。
	>
	> 感謝你的閱讀。
	>
	> 那麼明天見囉😊
	>
	> 比鄰敬上
    - [x] 開場使用材料更新：https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit [name=mrorz]
    - [x] 準備空 Spreadsheet + 上 bit.ly 短網址
    	- [x] https://bit.ly/cofacts29-1 （[樣板檔](https://docs.google.com/spreadsheets/d/1K_2WYW-yZ2gbQbFteJxNfrx9xKHBtKbq6ejsuZ2B8OU/edit#gid=0)）
    	- [x] https://bit.ly/cofacts29-2 （[樣板檔](https://docs.google.com/spreadsheets/d/1j75M_qh7s1JE0hUx3YQHN6-ncL6u2gMCdoHfm1sweeI/edit#gid=0)）
	- [x] 準備 Slido `#cofacts29`
		- [x] 放投影片網址 + spreadsheet 1
    - [x] 幫 Netgear 充電
- 當日準備 / 攜帶
    - [x] 產生「有回過、沒 feedback」 spreadsheet [name=nonumpa]
        - 每人 20 篇
        - 25 人
        - 只產出 `repliedButNotEnoughFeedback` 的網址
        - [x] 匯入進 https://bit.ly/cofacts29-1
    - [x] 產生「沒回過」spreadsheet
        - 每人 5 篇
        - 25 人
        - 只產出 `newest, mostAsked` 的網址
        - [x] 匯入進 https://bit.ly/cofacts29-2
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
  - [x] 簽到、實聯制、噴酒精、量體溫
  - [x] 排桌子椅子
  - [x] 麥克風
  - [x] 門口黏引導牌
  - [ ] Slido - 白紙寫 slido room number `#cofacts29`
  - [x] WIFI
      - [x] 佈機x2
      - [x] 連結 netgear 與 asus WAN port
      - [x] 白紙寫 SSID Cofacts meetup(_5G) + wifi password 貼牆上
      - [x] 192.168.2.1 進入 netgear admin 看 asus 的 IP
      - [x] 開好兩台 router admin 監測連網狀態
      - [x] (optional) netgear 換成 5GHz only?
  - [x] 投影的電腦用 google chrome 開好
    - [x] Google Chrome tab: [投影片](https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit)
    - [x] Google Chrome tab: [Instant](https://cofacts.github.io/community-builder/#/bignum?start=2022-01-09T14%3A00&panels=replied&panels=feedback)
    - [x] Google Chrome tab: [KKTIX](https://cofacts.kktix.cc/events/cofacteditor28)
    - [x] Google Chrome tab: [Slido admin](https://admin.sli.do/event/pGvrqQcZPmTXgBNRoW7Etb/polls)
    - [x] Google Chrome tab: [Slido](https://wall.sli.do/event/pGvrqQcZPmTXgBNRoW7Etb?section=a8ba9a02-1750-4ef0-aa61-1d2d1df50598)
    - [x] Google Chrome tab: [開場影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs)
    - [x] BGM
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


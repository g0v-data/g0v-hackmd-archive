---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220105 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz, nonumpa
- 線上出席：cai
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :family: Community builder

https://cofacts.github.io/community-builder/

- Fix Editor Works pagination
- Add Github actions auto-build


### :rocket: Staging

需測試新的 API 是否會影響現有 chatbot & website 功能
https://g0v.hackmd.io/hk1v8Ka5TCmIZinQ6zKU9Q

#### :robot_face: rumors-line-bot

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [ ] 查詢後可以列出回應
- [ ] Article LIFF 可以正常列出回應

##### ⛔️ Release Blockers
##### 未竟項目

#### :globe_with_meridians: Site

中文 search snippet 更新 - https://github.com/cofacts/rumors-site/pull/466
##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] Article detail
  - [x] Can see replies
  - [x] Can see comments
      - [x] Do not see blocked comments (find them in [spammer report](https://docs.google.com/spreadsheets/d/1Ytd69YU6z7Fgra81_79XrsPwQYV1Clh0yp5OZlk5Psg/edit#gid=267346713))
      - [x] ex: https://dev.cofacts.tw/article/1ob47xb1ngs9i

#### 發現漏 block 的 spammer
https://dev.cofacts.org/article/101zeo3auiite

##### ⛔️ Release Blockers
N/A

##### 未竟項目
N/A

### :eye: Under review

- Hide blocked content API - https://github.com/cofacts/rumors-api/pull/262
- Show blocked content for specific users - https://github.com/cofacts/rumors-site/pull/467
- Multimedia support phase 0

## 小聚 rundown

- 週三會議
    - [x] 週四 8 pm schedule
    > 查核機器人所回應的查證資訊，都是善良的志工一筆一筆新增的。
    >
    > (PC) 在這裡邀請您，即使只是對查證資訊好奇，不限年齡、無論經驗，都能參與本次的查核工作坊。只需要攜帶筆記型電腦，花一個下午的時間，就能習得查核技巧幫助其他的朋友喔！
    >
    > 2022年的第一次真的假的編輯志工教學聚會，就在2022年01月09日下午2:00-5:00
    > 在 NPO Hub Taipei（台北市中正區重慶南路三段2號 4樓廚房），活動完全免費。
    > 
    > 🔰 這是免費的實體志工聚會，超級歡迎沒有參加過的新手，會在活動中提供查核技巧教學。
    > 
    > 座位有限，請記得報名 👇
    > https://cofacts.kktix.cc/events/cofacteditor28
    > 
    > 📍 地點：NPO Hub Taipei 4 樓 / 100台北市中正區重慶南路三段2號 4 樓
    > 🚇 最近的捷運站：中正紀念堂站2號出口
    >
    - 圖：https://www.figma.com/file/zwThV99c4dHkFdIPg3Ii0T/Cofacts-%E7%99%BC%E6%96%87%E7%94%A8%E5%9C%96?node-id=978%3A19
    - 目標：北北基桃
    - [x] 換 rich menu
- 週六早上
    - [x] KKTIX 行前通知：jitsi 網址、提醒時間、使用電腦而非手機
    > Hello 你好，
	>
	> 明天就是 1 月 9 日的編輯小聚囉！
	> 編輯小聚需要大量查詢資料，請自備筆電 💻 與充電器 🔌 並帶著愉快的心情來參加。帶順手的平板也可以的！
	>
	> 時間：1/9（日）14:00
	> 地點：NPO Hub Taipei 4 樓廚房 （台北市中正區重慶南路三段2號4樓，出電梯左轉）
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
    	- [x] https://bit.ly/cofacts28-1 （[樣板檔](https://docs.google.com/spreadsheets/d/1K_2WYW-yZ2gbQbFteJxNfrx9xKHBtKbq6ejsuZ2B8OU/edit#gid=0)）
    	- [x] https://bit.ly/cofacts28-2 （[樣板檔](https://docs.google.com/spreadsheets/d/1j75M_qh7s1JE0hUx3YQHN6-ncL6u2gMCdoHfm1sweeI/edit#gid=0)）
	- [x] 準備 Slido `#cofacts28`
		- [x] 放投影片網址 + spreadsheet 1
    - [x] 幫 Netgear 充電
- 當日準備 / 攜帶
    - [x] 產生「有回過、沒 feedback」 spreadsheet [name=nonumpa]
        - 每人 20 篇
        - 25 人
        - 只產出 `repliedButNotEnoughFeedback` 的網址
        - [x] 匯入進 https://bit.ly/cofacts28-1
    - [x] 產生「沒回過」spreadsheet
        - 每人 5 篇
        - 25 人
        - 只產出 `newest, mostAsked` 的網址
        - [x] 匯入進 https://bit.ly/cofacts28-2
    - [ ] 貼紙 - bil
    - [ ] 食物 - 提醒 ggm 來叫 ubereats
    - [ ] 簽到單 - orz
        - [ ] pen
    - [x] 黏土 - orz
    - [x] 編輯小聚的牌子 - orz
    - [x] Wifi 機 - mrorz
        - [x] Netgear 本體
            - [ ] usb type-c 充電線與插座 （已充飽電，無需插座）
            - [x] 電池
            - [x] 4G 天線
        - [x] Asus RT-N12
            - [x] 電源線
            - [x] 5dBi 天線
            - [x] RJ45 線
- 13:30 - 場佈
  - [x] 簽到、實聯制、噴酒精、量體溫
  - [ ] 排桌子椅子
  - [x] 麥克風
  - [x] 門口黏引導牌
  - [x] Slido - 白紙寫 slido room number `#cofacts28`
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
    - GGM 統計仙草，買買：https://www.ubereats.com/tw/store/%E5%85%AB%E6%99%82%E7%A5%9E%E4%BB%99%E8%8D%89-%E4%B8%AD%E5%B1%B1%E5%BA%97/2DqZm69iRA-_IRfwQ3AfRw
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

## 詐騙型態介紹文

### 二次詐騙

案例：https://docs.google.com/spreadsheets/d/1Ytd69YU6z7Fgra81_79XrsPwQYV1Clh0yp5OZlk5Psg/edit#gid=267346713

假律師：
https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP/2021-10#ts-1635829762.0419

實際會怎樣
- [防詐達人 二次詐騙](https://getdr.com/%E4%BD%A0%E6%9C%89%E8%81%BD%E9%81%8E%E3%80%8C%E4%BA%8C%E6%AC%A1%E8%A9%90%E9%A8%99%E3%80%8D%E5%97%8E%EF%BC%9F%E6%83%B3%E8%A6%81%E8%BF%BD%E5%9B%9E%E8%A2%AB%E9%A8%99%E7%9A%84%E9%8C%A2%E4%B9%9F%E5%88%A5/)

### 聲稱療效產品

文章案例
- 請問是你本人 https://cofacts.tw/search?type=messages&q=%E6%82%A8%E5%A5%BD%E8%AB%8B%E5%95%8F%E6%98%AF%E6%9C%AC%E4%BA%BA
- 封鎖還會收到號稱的訴訟 XD
    - https://cofacts.tw/article/2zr9skucanz9y
    - https://cofacts.tw/article/3lznmyutirlzi
    - https://cofacts.tw/article/2ftu9wuf3md7j

實際會怎樣
- https://www.dcard.tw/f/ask/p/236542859
- https://meteor.today/article/WgtUI6

Reply points
- 易生消費糾紛
- 營造量身打造產品、墊高退款門檻
- 不肖業者會透過 LINE 一對一訊息進行問答、推銷「療程」並宣稱療效；但是由於對話都在不公開的聊天視窗，若受害者不主動檢舉，衛生局也無法針對這些誇大不實的療效進行調查。
- 有醫師被冒用的案例

https://cofacts.tw/reply/JqTUfn0BnX5-aOa4EG3A

### 試吃員、試住員

文章案例：
- https://cofacts.tw/article/2vflekpevr9e2 與 related articles

實際會怎樣
- 要求加入群組 https://www.dcard.tw/f/talk/p/237756039
- 會給錢、之後要求「預付」 https://www.facebook.com/vic.wang/posts/10158560988041717

根據收到此訊息的網友經驗分享，加入該帳號好友之後會被推薦加入其他線上社群，隨後推送其他廣告；目前尚無人實際在加入該 LINE ID 後，有接到訊息裡聲稱的工作。

https://cofacts.tw/reply/v6SU_30BnX5-aOa4A5p4

### 車手：收集帳戶註冊綁定交易所，完成入金的提領工作

文章案例
- https://cofacts.tw/article/3mmczh4159bkn
- https://cofacts.tw/article/2w6g9sk37gshe

實際會怎樣
[臺灣高等法院 臺南分院 109 年度上訴字第 1481 號刑事判決](https://law.judicial.gov.tw/FJUD/data.aspx?ro=2&q=148c6069bca8c2c9b13e11e2bd29001c&sort=DS&ot=in)

### 代操金融

文章案例
- 「我本身有在做金融平台的投資 目前在⋯⋯」「所以需要請人幫我顧」
    https://cofacts.tw/article/2hliscsstl4cy 與旁邊的相似可疑訊息
- 「工作內容是 我會給你我的個人外幣帳號」「會有人親自指導你」「不用擔心沒有經驗」
    https://cofacts.tw/article/22repgc8bltjp
- https://cofacts.tw/article/vagfgfyhlj2v 喔喔喔這裡有人在我想補充把完整話術與平台與帳號密碼都貼出來了 XDD

實際會怎樣
TBA

### 財富自由
https://cofacts.tw/search?type=messages&q=%E8%B2%A1%E5%AF%8C%E8%87%AA%E7%94%B1&categoryIds=nD2n7nEBrIRcahlYwQoW

BEEWiN Mining
- https://cofacts.tw/article/sldy7r3eeaot
- https://cofacts.tw/article/3vbtdc9r4joc5
- https://cofacts.tw/article/2wxqikdljfa75

## 防禦性商標申請

- 圖片：過ㄌ
- 文字：需要提供使用資料
    - 「真的假的」提案
    - 新舊版網站（都有使用「真的假的」或「Cofacts 真的假的」）
    - 每年 PV
    - LINE 使用者數（「Cofacts 真的假的」）

## Multimedia support

- Spec: https://g0v.hackmd.io/aJqHn8f5QGuBDLSMH_EinA
- 先前分 phase 討論：https://g0v.hackmd.io/1WADYBY0TH27ZqOaVMjqUg#Overall-discussion
- Q: 現有 article 要填入 articleType='TEXT' 嗎？ListArticle 看起來會自帶 `articleType` filter [name=mrorz]
    - A: 寫 updateByQuery, query 沒有 articleType 的文章，設 doc [name=mrorz]
- 網站、LINE bot 也要改 [name=nonumpa]
    - 送圖片需要加一個 consent [name=nonumpa]
    - 用跟文字一樣的 wording（成為世界第一個⋯⋯）[name=mrorz]
    - state 可以跟文字共用，在 handler 裡面判斷 event type [name=mrorz]
- 如果像衛武營那種文字相同，圖片不同要怎麼算? [name=cai]
    - [狀況一：國外藝人表演](https://tw.news.yahoo.com/轉傳不雅片還註記-衛武營純台灣味-男子吃官司-045140987.html)
    - [狀況二：學校表演](https://cofacts.tw/reply/WMMxGn0BucwAqrba0YSv)
    - [狀況三：勸世三姊妹](https://cofacts.tw/reply/hkIzSHoBgBgcuemXmFSV)
    - phase 0 的圖片與所附文字視為分開的訊息，就是請使用者傳圖進來，Cofacts 按照圖片內容進行回應 [name=mrorz]
    - 圖與其圖說在 Cofacts 資料庫會是分開的 article，未來([Phase 1](https://g0v.hackmd.io/1WADYBY0TH27ZqOaVMjqUg#Overall-discussion))會導入新的 article group 概念，紀錄「這兩個 article 會一起傳」這件事情。
    - 這樣也能處理「一個文字會被配上不同圖片來傳」的狀況
        - Cofacts Articles: 圖 A, 圖 B, 文 A
        - article group A = (圖 A + 文 A)
        - article group B = (圖 B + 文 A)
    - 可能在 aritcle detail 會顯示「這個東西會跟哪些訊息/圖片一起傳」
    - 尚未決定：是否要有針對「article group」的 reply
        - 但能分開 reply 的話，要做 article group 的 reply 時，就能讓使用者選擇從現有 reply mix & match [name=mrorz]


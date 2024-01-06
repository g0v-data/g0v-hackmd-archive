---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210217 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, hsiao, 文武, lucien
:::

## :potable_water: Release pipeline

### :star: Released to production

New `LEGAL.md` merged to master.
`LEGAL.md` 為主，過去的 3 份 Google doc 留存作為歷史文件之用。

- [API](https://github.com/cofacts/rumors-api/pull/245)
- [rumors-site](https://github.com/cofacts/rumors-site/pull/387)
- [rumors-line-bot](https://github.com/cofacts/rumors-line-bot/pull/240)
- [opendata](https://github.com/cofacts/opendata/pull/21)
    - 新的申請 opendata 的方式：[google form](https://docs.google.com/forms/d/1w4urJqDnZ9tI4Bn0d25KDqrwgwjD3eIZw4a3ahqmJJY/edit) --> 自動加使用者進 cofacts data folder
    - google form 確保所有申請者都同意 user agreement
    - 問題：[「自動加 viewer」每隔一段時間會過期](https://stackoverflow.com/questions/65316819/unable-to-open-google-xlsx-spreadsheet-also-google-drive-permission-blocked)
        - Mitigation: 每天會戳一次程式，如果 fail 的話就手動 run 一次 [name=mrorz]

### :rocket: Staging

#### :electric_plug: API

[DIFF](https://github.com/cofacts/rumors-api/compare/c2ff8f2c8f7221bf431fb760438d09b01a8e6608...d679bc118185a4df2dcc5dbda464b548a82629c8)
- #245, #246 Legal & display

#### :robot_face: LINE bot
- #238 handle group messages
- #241, #242 Cofacts article URL can trigger reply list (Simplify forward from 3rd party chatbots)

##### 未竟項目
- Items in https://github.com/cofacts/rumors-line-bot/pull/238#pullrequestreview-592054109

#### :globe_with_meridians: Site

- #372, #380 urljs, immer security upgrade
- #387, #389 Legal notice update

##### Testing checklist

http://dev.cofacts.org/

**未登入**下檢測：

- [x] Article list
  - [x] Filter works
  - [x] Sorting works
  - [x] Can go to article page
- [x] Replies list
  - [x] Filter works
    - [x] 不允許選擇 Replied by me
  - [x] Sorting works
  - [x] Can go to article page
  - [x] 不允許 upvote / downvote replies
  - [x] Can see vote reasons
- [x] Hoax for you
  - [x] Filter works
  - [x] Can go to article page
- [x] Article detail
  - [x] Can see similar messages
  - [x] Cannot submit, upvote, downvote reply request
  - [x] Cannot submit, upvote, downvote reply
  - [x] Cannot add, remove, upvote, downvote category
- [x] Search
  - [x] Can use global search to perform search
  - [x] Can use textarea in header to perform searchs
     - Known issue: firefox 無法
  - [x] Can list searched articles
    - [x] Filter works
    - [x] Can go to article page
  - [x] Can list searched replies

登入自有帳號後檢測：
- [x] Replies search page
  - [x] can upvote / downvote replies
- [x] Replies list
  - [x] 可選擇 Replied by me
  - [x] can upvote / downvote replies
- [x] Article detail
  - [x] Can submit, upvote, downvote reply request
  - [x] Can submit, remove own reply
  - [x] Can upvote, downvote other's article reply
  - [x] Can add, remove, upvote, downvote category
- [x] Can go to profile page on menu
    - [x] Can edit own name, bio, URL
    - [x] Can see own replies
- [x] Can logout

##### ⛔️ Release Blockers
N/A

##### 未竟項目
- Items listed in https://github.com/cofacts/rumors-site/pull/388#issuecomment-780328449
- 翻譯：user agreement, login dialog 下面的 notice

### :eye: Under review

#### :robot_face: LINE bot
- [#238](https://github.com/cofacts/rumors-line-bot/pull/238) group messages
    - TODO: custom metric v.s. dimension [name=mrorz]
    - 擱置，先不設定 dimension2
     
#### :globe_with_meridians: Site
- [#388](https://github.com/cofacts/rumors-site/pull/388) tutorial page
    - Need clarification of `<Slider>`'s `useEffect`s [name=mrorz]
    - 放進未竟項目

## 2021 二月三月計畫

- 2/21 編輯小聚
- 2 月底：Cofacts 影響力報告網站
- 2 月底：chatbot LIFF redirect 設定 by 斌
- 2 月底：給金控的 pitch deck
- 3/1：零時小學校＠台南
- 3 月初：enforce API header
- 3/5 簡訊設計影片完成

### 第 23 次小聚

#### 小聚 rundown

- 週三會議
    - [x] 發布 LINE 推播 --> 週四 8 pm schedule
    - [x] 換 rich menu
- 週六早上
    - [x] KKTIX 行前通知：提醒時間、筆電
    > Hello 你好，
	>
	> 明天就是 2 月 21 日的編輯小聚囉！
	> 編輯小聚需要大量查詢資料，請自備筆電 💻 與充電器 🔌。
	>
	> 時間：2/21（日）14:00
	> 地點：100台北市中正區重慶南路三段2號4樓（NPO Hub）
	> 可以從中正紀念堂站 2 號出口出站，沿寧波西街走 7 分鐘。
	> 
	> 費用全免，會很準時開始。
	> https://www.facebook.com/groups/cofacts
	> Cofacts 編輯 VIP 臉書社團在這裡，請先加入吧＝Ｄ說你會來編輯小聚優先加入（真的）
	>
	> 感謝你的閱讀。
	>
	> 那麼明天見囉😊
	>
	> 比鄰敬上
    - [x] 開場使用材料更新：https://docs.google.com/presentation/d/1QCAPtwkxreQ4EUtIWsOgR4c8h4tkRs22Qvv7jBFNrfI/edit#slide=id.g1ffc87ef17_0_23
    - [x] 準備空 Spreadsheet + 上 bit.ly 短網址
    	- [x] https://bit.ly/cofacts23-1 （[樣板檔](https://docs.google.com/spreadsheets/d/1K_2WYW-yZ2gbQbFteJxNfrx9xKHBtKbq6ejsuZ2B8OU/edit#gid=0)）
    	- [x] https://bit.ly/cofacts23-2 （[樣板檔](https://docs.google.com/spreadsheets/d/1j75M_qh7s1JE0hUx3YQHN6-ncL6u2gMCdoHfm1sweeI/edit#gid=0)）
	- [x] 準備 Slido `#cofacts23`
		- [x] 放投影片網址 + spreadsheet 1
- 攜帶
	- [x] 貼紙 - orz, bil
    - [x] 食物 - (wait for 週六)
    - [ ] 簽到單 - orz
    	- [ ] sticky note
    	- [ ] pen
	- [x] 黏土 - orz
    - [x] 編輯小聚的牌子 - orz
    - [x] Wifi 機 - mrorz
        - [x] Netgear 本體
            - [x] usb type-c 充電線與插座
            - [x] 電池
            - [x] 4G 天線
        - [x] Asus RT-N12
            - [x] 電源線
            - [x] 5dBi 天線
            - [x] RJ45 線
- 13:00 - 場佈
  - [x] 樓下貼好按開門的 sticky note
  - [x] 簽到
      - 要給每個人指定一個 **1 ~ 25 的號碼，分工要用**
  - [x] 排桌子椅子
  - [x] 麥克風
  - [x] 引導牌
  - [x] Slido - 白紙寫 slido room number `#cofacts23`
  - [x] WIFI
      - [x] 貼 SSID
  - [x] 產生「有回過、沒 feedback」 spreadsheet
      - 每人 20 篇
      - 25 人
      - 只產出 `repliedButNotEnoughFeedback` 的網址
    - [x] 匯入進 https://bit.ly/cofacts23-1
  - [x] 產生「沒回過」spreadsheet
      - 每人 10 篇
      - 25 人
      - 只產出 `newest, mostAsked` 的網址
    - [x] 匯入進 https://bit.ly/cofacts23-2
  - [x] WIFI
      - [x] 佈機x2
      - [x] 連結 netgear 與 asus WAN port
      - [x] 白紙寫 SSID Cofacts meetup(_5G) + wifi password 貼牆上
      - [x] 192.168.2.1 進入 netgear admin 看 asus 的 IP
      - [x] 開好兩台 router admin 監測連網狀態
      - [x] (optional) netgear 換成 5GHz only?
  - [x] 投影的電腦開好：
    - [x] browser tab: [投影片](https://docs.google.com/presentation/d/1QCAPtwkxreQ4EUtIWsOgR4c8h4tkRs22Qvv7jBFNrfI/edit#slide=id.p)
    - [x] browser tab: [Instant](https://cofacts.github.io/community-builder/#/bignum?start=2021-02-21T14%3A00&panels=replied&panels=feedback)
    - [x] browser tab: [KKTIX](https://cofacts.kktix.cc/events/cofacteditor23)
    - [x] browser tab: [Slido](https://wall.sli.do/event/1wucl8p2?section=fef8bbc0-424d-4c78-9d88-6a9ad5a20214)
    - [x] browser tab: [Slido admin](https://admin.sli.do/event/1wucl8p2/)
    - [x] BGM
- 14:00 - 14:20 開場
    - 場地介紹、Slido 破冰、Cofacts 機器人系統簡介，大家自我介紹
- 14:20 - 14:40：介紹 mission 1 - 按讚
    - 介紹「幫回應按讚」的用途，以及怎麼做；什麼樣的回應可以按「有用」、哪些可以跳過、哪些真的母湯要按「沒用」，如何就事論事的給 feedback
- 14:40 - 15:00：按讚時間
    - 讓大家從 Slido 打開 spreadsheet 1，直接點進自己號碼的那個 sheet
    - 然後幫每一篇按有用或沒用
- 15:00 - 15:10：休息時間
    - 閒聊「看到覺得最好的回應、覺得哪裡好」
- 15:10 - 15:30：介紹 mission 2 - 寫新回應
    - 如何找全文、拆解回應、附出處
- 15:30 - 16:30：挑回應來回
    - 大家從 Slido 打開 spreadsheet 2，直接點進自己號碼牌的那個 sheet
    - 先挑選「一篇」覺得最有興趣的回
    - 回完之後如果行有餘力，再挑一篇
    - 如果都覺得不想回，去「等你來答」挑，不要硬回 XDDD
- 16:30 - 17:00：閒聊時間
    - 讓大家講感想
    - 介紹 RSS、文章列表、filter 功能
    - 最後拍合照

---


- [x] 主題：大過年的來闢謠
	- [2020](https://cofacts.kktix.cc/events/cofacteditor18)
	- [2019](https://cofacts.kktix.cc/events/cofacteditor12)
	- [2018](https://cofacts.kktix.cc/events/cofacteditor7)
- [x] 時間：2/21（日）
	- **活動時間：14:00 - 17:00**
	- 場地借用 13:30 - 17:30 （上限 4hr）
- [x] KKTIX  https://cofacts.kktix.cc/events/cofacteditor23
- [x] 準備貼紙
- 場地：NPO Hub 4 樓廚房 （台北市中正區重慶南路三段 2 號 4 樓）
    - [x] Keyholder: ronny
    - [x] 場地單
    - [ ] 食物
        - 看禮拜六有沒有剩 XD
    - [x] 延長線 (場地有)
    - [ ] wifi
        - [ ] Nighthawk M1 + 4G sim
        - [ ] ASUS RT-N12 Wireless N300 (2x 5dbi高增益天線)
- [x] 誰會來呢？bil, mrorz, 文武, hsiao
- [ ] 誰不會來
- [x] 志超做圖
- [x] LINE 文案：貼文串有了，推播還沒有
(圖文訊息)
https://cofacts.kktix.cc/events/cofacteditor23
第23次聊天機器人開發之查核志工編輯小聚就在2月21日(星期天)下午，請帶筆記型電腦，免費參加。有新手教學，歡迎舊雨新知參加！

座位有限，請記得報名～
(最近的捷運站是捷運中正紀念堂站)

- 484 要強調新手可以參加呀 [name=mrorz]
    - [上次有人](https://g0v.hackmd.io/PUXRtdC2SNak8VYUSAb-Gg)提說「編輯小聚」這個名字像是 for 已經認識的編輯們的聚會，是看到「義工」或「志工」才來的 [name=mrorz]

### 影響力報告網站

report branch --> merge --> 各自從 dev fork 出來做

### LIFF redirect
> 相關討論：https://g0v.hackmd.io/U-KmeEYJTVmtCFB-bqWfGg#LIFF

https://github.com/cofacts/rumors-line-bot/pull/243 nonumpa++

### pitch deck

- 複製一些去小聚開場投影片 [name=mrorz]
- 跟 LINE 確認 [name=bil]

### 零時小學校籌備

- 週六去 [name=bil]
- 3hr，小聚模式

### 新 terms & API header
> Owner: MrOrz

- [x] 開發者溝通
- [x] Prepare pull requests for license change
- [x] 社群溝通: FB group
- [x] opendata 表單 https://forms.gle/nYaaVSLDX5i5vScT7
- [x] 2/17 第一版公布
- [ ] 開發[API client application 管理機制](https://github.com/cofacts/rumors-api/issues/244)
    - backward compatible: 沒送 app-secret 的也會 match 到某個開發用 app
    - --> postponed to March, app-secret 會再往後延 [name=orz]
- [ ] 4 月：enforce API 管理
    - 保留 staging 上的開發用 app
    - 移除 production 上的開發用 app

## AOB

### 時間顯示
> 周三討論到網站日期顯示
讓我想到最近遇到兩個也是跟日期有關，但是是跟闢謠有關的
第一個是過時的回應
https://cofacts.g0v.tw/article/3lnetvzfdkm62
這個 2019的訊息，在 2021 年又在傳，導致困擾
另一個是在醫院工作的親戚，前幾天知道北部確診醫師的醫院門診照常，但今天聽到別人指稱該院封院時，還是來問我。即使他在幾天前就知道正確資訊，但第一次接觸謠言時，還是會覺得是不是有什麼「更新的資訊」自己沒 catch 到。
我覺得上面兩種狀況，都可以透過 chatbot 加註這個回應「多久以前回的」、訊息「多久以前就在傳」，增加大眾意識到時序的重要性
> [name=mrorz]

Facebook: 當下是 1/27 2:00PM 的時候 --
5m, 2h, 18h, 2d (for January 25 9:40 AM, comment)
Yesterday at 11:06 AM
January 25 at 1:25 AM
January 25 11:27PM
July 10, 2020

:::success
差異 24hr 內：hour
> 24hr 但落在昨天：yesterday、時間
昨天以前：月、日、時間
其他：年、月、日

Or use https://date-fns.org/v2.16.1/docs/formatRelative for time difference within 48hr

--> https://github.com/cofacts/rumors-site/issues/396
:::

### 推薦標籤

> Idea: 利用「相似可疑訊息」的分類來推薦分類。可以在「分類建議」按鈕後面做一鍵增加的鈕。
> 例如說 COVID-19 的新訊息 https://cofacts.tw/article/j1al35fna5au ，進來的時候還滿常有已經標過分類的相似可疑訊息，但每次點開「分類建議」按鈕都要找好久的分類。
由於分類未來只會越來越多、手機螢幕大小依然有限，list traversal 本身無法改進太多（最有用的可能是加個搜尋框），不如直接用「相似可疑訊息」的分類來推薦。
> [name=mrorz]

- 直接在「分類建議」按鈕後面列舉建議的標籤，讓使用者直接點選 [name=mrorz]
- 增加標籤的話，只有名字是否足夠？若不夠的話，還是有 description 比較好 [name=lucien]
- 那還是做在 dialog 裡面。要分區嗎 [name=mrorz]
- 好像會有重複 [name=lucien]
- 有標過的也應該往上放 [name=nonumpa]

:::success
分三區，不重複

第一區：標過的，讓使用者可以同意或反對
第二區：類似文章的標記
第三區：其他

--> https://github.com/cofacts/rumors-site/issues/397
:::

### SEO & nginx 設定
https://github.com/cofacts/rumors-deploy/pull/15

想要把 cofacts.tw 當成 canonical URL
- 比較短
- 可以把打錯字的 cofact.tw 也導向去 cofacts.tw


:::success
執行之
:::
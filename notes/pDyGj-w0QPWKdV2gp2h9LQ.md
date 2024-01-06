---
tags: cofacts, meeting note
---

20200408 會議紀錄
=====

> Workis: MrOrz, bil, lucien
> 線上：志超
> 線上開會：https://tico.chat/powercall?room=cofactshack&type=timeFirst
> 上次開會紀錄：https://g0v.hackmd.io/@mrorz/rk3w8oWwI
>

## Design
> by 志超

Landing page
- 與 Lucien
- 需要照片
  - 不要有時代感的東西，例如 m8
  - 有什麼給什麼，志超再挑
    - 2K / full hd，可以放全版的圖
  - 長頸鹿

Badges
- 確定的等級中英文
- https://g0v.hackmd.io/@NFi0czulSemxCM8RNSlz8Q/HJ8xT3QVU


---

- lv0: 從零開始的主人公
- lv1: 鄉民
- lv2: 站得前面一點的鄉民
- lv3: 好心人
- lv4: 很好心的人
- lv5: 好人
- lv6: 大好人
- lv7: 謠民 Fact checker
- lv8: 童貞魔法師 Magician
- lv9: 老司機 On the road
- lv10: 闢謠天行者 Rumor the skywalker
- lv11: 魔法少女 Magica
- lv12: 闢謠天師
- lv13: 謠言大覺者
- lv14: 謠言終結者
- lv15: 滅謠師太
- lv16: 闢謠小女警
- lv17: 闢謠小飛俠
- lv18: 闢謠鐵金剛
- lv19: 從零開始的魔法旋轉花花
- lv20: 變態的好人
- lv21: 超能孟獲
- lv22: 熱血傲嬌律師
- lv23: 初號機
- lv24: 貳號機
- lv25: 好心神

orz
英文與中文要一致好難
但如果要照意思畫圖的話中英文就要一致

bil
迪士尼翻譯也會在地化

可以等級不同用顏色分就好嗎

orz
金銀銅
藍鑽 (?)

lucien
當時是覺得等級 25 已經是天文數字 所以可以設計
badge 則是給成就的。

等級名字一種是讓社群去討論
另一個是就不要名字

orz
我覺得等級太難了

lucien
但我有 1X 個成就也要取名字

orz
但 badge 圖可以用達成條件來畫
例如說大家覺的有用 10 個、20 個、50 個

lucien
之前淡化編輯
但如果等級很高，是不是可以加回來

例如說可以填資料、職位認證之類

orz
我是覺得可以用等級

lucien
希望可以增加欄位
可能需要人工審核認證

頭像可以存嗎

orz
要做的話就是接 [Google picker](https://developers.google.com/picker)
丟 GCS 然後存 ＵＲＬ

lucien
職業認證呢
他跟 organization 有什麼不一樣
organizaition 是誰審核

bil
organization 是公開資訊
但職業是個人資訊

orz
我本來是打算用網域擁有與否
然後組織就是「擁有這個網域的人」(可用 [google search console API 認證](https://developers.google.com/webmaster-tools/search-console-api-original/v3/sites/get))

組織下的人可以選擇用個人身份回應，或用組織身份回應
用組織的話分數就會算在組織
組織也有 score 跟 badge

組織可以在 chatbot 上顯名


## 小聚

上週討論： https://g0v.hackmd.io/@mrorz/rk3w8oWwI#%E5%B0%8F%E8%81%9A%E6%80%8E%E9%BA%BC%E8%BE%A6

### 基礎松觀察

用的是跟大松一樣的工具
https://intro.g0v.ronny.tw/
- 需要 g0v slack 帳號
- 「大廳」https://intro.g0v.ronny.tw/meet/show/g0v-infrath16n

### 我們怎麼辦

orz
上週提到用直播 + slido
不過沒辦法重現私下問問題的部分
分享螢幕也麻煩

bil
LINE 可以直撥

orz
Facebook group 開直播
發問直接在直播下面
發問怎麼辦

bil
1. 私訊給粉專，這樣可以保密，但也可以公開回
2. 留訊息，大家可以一起回答

orz
那他們查到一半的東西要怎麼回

bil
用「我也想知道」功能，請他們把查到一半的東西放上去

:::success
- 粉專開直播
- FB group, page, LINE 都會通知
:::

orz
不會有自我介紹了
認領工作怎麼處理

bil
置頂工作分配

orz
工作分配的 sheet:
第一個分頁放教學
請大家認領分頁

OBS 放資訊
1. 工作分配
2. 發問：comment or 私訊 Cofacts 粉專
3. 目前活動進行到哪
    1. 介紹 Cofacts 編輯
    2. 介紹今天如何工作
    3. 直播比鄰吃飯（冠軍薯條、涼麵）

bil
認領 tab 之後
做 3 個之後
可以私訊我們請我們叫食物

orz
上次說前三天再宣傳嗎
那就是下週三 4/15
4/18 開直播
4/18 早上測試 “publish as a test broadcast”

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3f929604ce473a035e8e0352b7e7dc9b)


bil
直播通知抄指揮中心快訊的格式 lol

「小聚直播快訊」

- [x] 主題：
    - 首次防疫雲端直播小聚
- [x] 時間：4/18 (六) 14:00-17:00 
- [ ] ~~KKTIX~~
- [ ] ~~攜帶貼紙~~
- [x] 場地：Workis (早上測試)
    - [ ] 食物給比鄰直播吃。
    - [ ] 直播用筆電
      - [ ] OBS 設定
      - [ ] 字卡素材
      - [ ] 投影（不要把直播設定也直播出去惹）
    - [ ] BOSE 藍芽喇叭麥克風
    - [x] 延長線
    - [ ] 新功能介紹
    - [ ] wifi
        - [ ] Nighthawk M1 + 4G sim
        - [ ] ASUS RT-N12 Wireless N300 (2x 5dbi高增益天線)
- [x] 誰會來呢？
  - Bil
  - MrOrz
  - Howie
- [ ] 誰不會來
- [ ] LINE 文案

## Category 上線缺什麼

### UI PR review

article page 的互動
https://github.com/cofacts/rumors-site/pull/234

### Elasticsearch mappings migration

否則 article page UI 會無法顯示⋯⋯

### 顯示 Category 的定義

否則大家會不知道要標成什麼

lucien
description 應該就足夠？

orz
好像有新的分類
政治
慈善相關

bil
tag 是給研究者
urban legends
free 可以分成免費跟詐騙
IFCN 也有做這樣的標記

orz
但我想要做真的有人想訂閱的
給「編輯用」的標籤

lucien
訂閱有點難
但主要是讓人可以 filter 

orz
那也是要有人想要「只看這種分類」
我們做分類才有意義

lucien
burst 類的 event 

-----

### 訂閱

lucien
RSS 類 / 個人 user page 可以看到內容

orz
那等於要記 activity log 耶
就是所有人的所有動作都會記在一個表
然後大家的訂閱設定也是一個表

在看關注列表時，就是讀取設定，然後去 activity log 撈要顯示的東西

lucien
限定可以訂閱的東西
例如說看到關注的使用者回應什麼

## rumors-line-bot memory issue
 前週討論：https://g0v.hackmd.io/IS6_Qg6pQFK6uorTtatZ7w#rumors-line-bot-memory-issue

## 開發
GitHub activities
https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/WSQFB

### 感謝送出理由功能

Stimim++

orz
我想要感謝 stimim
然後說請大家把查到一半東西放進去「增加回報理由」

### LINE bot 互動修改

Chatbot PR 求 review:
1. 改目錄結構: https://github.com/cofacts/rumors-line-bot/pull/167
2. 加簡單 GraphQL API (無需 auth): https://github.com/cofacts/rumors-line-bot/pull/168
3. 加需要 auth 的 GraphQL query API: https://github.com/cofacts/rumors-line-bot/pull/169
4. 加需要 auth 的 GraphQL mutation API: https://github.com/cofacts/rumors-line-bot/pull/170

還沒好的ＰＲ：LIFF 初始設定 https://github.com/cofacts/rumors-line-bot/pull/171


UX 定稿：
https://g0v.hackmd.io/860RnxUGTi6z2Kca6ojAbg

State diagram 設計：

> * 共有三種 LIFF： LIFF asking source (詢問文章來源)、reason LIFF (送出文章理由)、feedback LIFF (覺得回應有用的建議或沒用的理由)
> * 送出 article, reply request 與 feedback 的流程思維改變：從先問理由(選填)才送出，改成先送出、才問理由。回到 __INIT__ state 時，也能叫出 LIFF 修改 reason / feedback。這也導致了 state diagram 的簡化。
> * 在 LIFF 裡的動作（選擇選項、送出文字）都會透過 LIFF send message API 傳回聊天視窗做紀錄；同時 chatbot server 也會把握這個機會拿到新的 reply token 送新東西（也就是 state diagram action 裡的 “reply with” 敘述）
> * 光是顯示 LIFF 是無法回應使用者的，但可以在 LIFF 載入時打 API 進行動作（如 create feedback）
> * 設計時需考量到使用者跳出 LIFF 之後怎麼回來接關。

> 使用者選到一則沒回應的訊息有兩種情形：
> 1. 有複數篇訊息符合搜尋，而使用者點到沒有回應的那篇
> 2. 只有一篇訊息符合搜尋
>
> 2 的行為，現在是直接跳到「沒有回應噎，請按『我也想知道』」這一步。
> 
> 我思考了一下，原本 （3/25 會議時提出的） 1 直接打開 LIFF 的設計，其實也要處理「把使用者選了這一則訊息（selectedArticleId）存進 context」這件事。但是，目前 chatbot webhook 的設計都是「回應時一併 mutate state 與 context」，但這個設計會需要在不改 state 的情形之下修改 context，我覺得設計上不是很好。況且，2 「只有一篇訊息符合」的 case 也無法解決，因為我們沒辦法在回應訊息時直接打開 LIFF，無論如何都要吐一個按鈕出去讓使用者點才行。
> 
> 因此我還是把 `ASKING_REPLY_REQUEST_REASON` 這個 state 加回來了：
> https://docs.google.com/drawings/d/1sSzI0PSggkA3PPP99Nl18H4zMO4lk-2y5s7dGRNJwAE/edit
> - `CHOOSING_ARTICLE` 下，不管是上面 1 還是 2 的狀況，都會轉移到 `ASKING_REPLY_REQUEST_REASON` state 並且設定 `selectedArticleId`
> - state 轉移的當下就會送出 reply request。
> - 作為 reply，我們會告訴使用者「抱歉『ooooo』這一篇還沒有回應，已經幫你提交需求」、並且問使用者願不願意提供更多資訊幫助編輯闢謠（一個按鈕）；按鈕會展開 LIFF asking source。
> - 續上，使用者在 `CHOOSING_ARTICLE` 下到底選了「哪一篇」在對話視窗裡面就會有個紀錄（LIFF 下比較麻煩還要 `sendMessage`）
>
> 這樣一來，整個流程也會與流程圖右邊的 `ASKING_ARTICLE_SUBMISSION_CONSENT` 更為接近，但差異是 reply request 會在進入 `ASKING_REPLY_REQUEST_REASON` 之前就會觸發（加速 1 人回報 --> N 人回報的過程，反應實際流傳度 ），而送出文章是在離開 `ASKING_ARTICLE_SUBMISSION_CONSENT` state 的時候才會觸發。 

### LIFF compatibility

https://github.com/sveltejs/svelte/issues/558

從 mobile browser, direct 來猜, 時間分佈 this year to date

瀏覽器分佈：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ad815304463eb99864974c51e547c092)

版本分析：
https://docs.google.com/spreadsheets/d/121Jql1JIF-fC8-uIgcLlK-PyofC2GMnqu6W1EO_dJ0o/edit#gid=0

:::info
Android: Chrome mobile `52.0.2743.98` to cover 99% of sessions
iOS: iOS version `10.3` to cover 99% of sessions
:::

寬度分佈：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c1c59576b9b834e4f7575418866c37b6)

:::info
可用 320 寬的手機進行測試
:::

高度分佈：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1bdd7477019c2a8ea1e3ca7df8c54201)

:::info
參考就好，[LIFF 不一定要蓋滿整個螢幕](https://developers.line.biz/en/docs/liff/overview/#screen-size)
:::


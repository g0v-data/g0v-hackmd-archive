---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20210811 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：mrorz, bil, nonumpa, 4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :robot_face: rumors-line-bot

- [#276](https://github.com/cofacts/rumors-line-bot/pull/276) Relative & absolute time string in viewed article list
- [#277](https://github.com/cofacts/rumors-line-bot/pull/277) Collapsible article display
- [#278](https://github.com/cofacts/rumors-line-bot/pull/278) Revamp viewed article list UI and extract common components

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 送出「沒回應」的舊訊息，應可送出新理由
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應
    - [x] 選擇回應之後可以幫回應 upvote
    - [x] 可以再次選擇 downvote

- [x] Rich menu 測試
    - [x] 「設定」更改後再次打開，應該會保留原本設定
    - [x] 「教學」可以觸發教學流程
    - [x] 「看過的訊息」可以載入並且顯示順利

##### ⛔️ Release Blockers
無

##### 未竟項目
- LIFF 反白「是」「否」按鈕讓人不確定是不是有按到
    - 可以考慮改成「感謝你選擇：有幫助  (修改)」

#### :globe_with_meridians: Site

- [cofacts/rumors-site#441](https://github.com/cofacts/rumors-site/pull/441) 修復「我查核過」搜尋功能，並且改進關鍵字 highlight。
    - 「搜尋自己的回應」功能實在太重要，但它是壞的。 [name=mrorz]
- [cofacts/rumors-site#442](https://github.com/cofacts/rumors-site/pull/442) 讓有「⋯」的 URL ，在複製貼上時不受影響，也就是貼上的時候會得到的是完整的 URL
    - 我們會針對過長的 URL 做 ellipsis（中間用⋯省略），讓出處等有很長網址的地方的顯示較為簡潔。但是這會讓人無法直接複製貼上出處（會複製到「⋯」所以出處會壞掉），我又超級常複製貼上自己的舊出處的，每次都要用 share > copy 然後刪掉多的字真的很痛苦，還常常漏刪 :woman-facepalming: [name=mrorz]

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] Article list
  - [x] 觀察是否有長網址破版
- [x] Replies list
  - [x] 觀察是否有長網址破版
  - 其實這頁根本不會縮網址 XD ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0831e8f795b4809ab32ac27b471a6bca.png)
- [x] Hoax for you
  - [x] 觀察是否有長網址破版
- [x] Article detail
  - [x] 觀察是否有長網址破版
  - [x] 從頁面上複製有網址的文字到其他地方貼上，網址應該完整呈現（不含「⋯⋯」）且可正確連到目標網頁
- [x] Search
  - [x] Can use global search to perform search
  - [x] Searched words are highlighted
  - [x] Can use textarea in header to perform searchs
     - Known issue: firefox 無法
  - [x] Can list searched articles
    - [x] 「我查核過」filter is disabled when not logged in
    - [x] Can go to article page
  - [x] Can list searched replies

登入自有帳號後檢測：
- [x] Search
    - [x] 「我查核過」filter works for both article & reply search

##### ⛔️ Release Blockers

##### 未竟項目
- 在搜尋狀態登入會出現 500 internal server error
- 「我查核過」在 article search 是指「我加過自己或他人回應」的文章，但在 reply search 時會列出「自己撰寫」的、由自己或他人加入的訊息們
- https://dev.cofacts.tw/article/2omoc6t82eqvo
    - 框全文的話，不會 highlight 全部
    - https://github.com/cofacts/rumors-api/issues/229


### :eye: Under review

以上都是 under review 的東西，只是先 deploy 到 staging 讓大家玩玩看

## 商標申請
:::info
前言: https://g0v.hackmd.io/Nhc9MnskSsGvUqntz0z7Dg#%E5%95%86%E6%A8%99%E7%94%B3%E8%AB%8B
:::

諮詢 Vincent & Alfred from AIPLUX

- 是否可個人申請
    - 沒有盈利沒有開公司可以申請商標。
    - 個人持續持有商標，可以往後簽授權協議，把商標給基金會或是協會使用。
    - 個人先申請，未來只要準備一些文件就可以轉移。
- 商標元素
    - 圖：顏色申請墨色，形狀作為申請，黑白稿就好，之後要換顏色都可以
    - Logo 是元件、cofacts 是元件、真的假的 是元件
        - 因為目前只是防衛性的，Cofacts 真的假的 放在一起申請就可以
        - Cofacts 真的假的放在一起申請會提高辨識度，比只送「真的假的」容易通過
        - 但是 LOGO + 名字一起申請就會保護效力最弱，被人"真的假的"、"Cofacts"單獨拿來用會沒有保護力
- 「真的假的」流行語與識別性
    - 流行語不能註冊，因為沒有識別性
    - 建議策略：持續使用、大量使用、大量曝光
        > 如果你使用夠久，識別性就會增加
        > 例如說「多喝水」以前沒有任何人可以申請過
        > 味丹申請的時候有 6~7 年都沒有通過
        > 但因為「沒事多喝水 多喝水沒事」的廣告不斷使用
        > 讓消費者能夠辨識（頻次破百萬是個很好的標準）
    - 「真的假的」70% 會遭核駁，一定會答辯
    - 「真的假的」在事實查證上，這領域是慣用詞，所以在這個領域上特別困難
- 選擇商標類別
    - 商標保護是十年，看 10 年會發展到什麼樣，會一併作保護
    -  用名稱做講座會是 41 類，API 提供資料要再確認，網路存取服務 38 類，35 資料庫存取建立資料庫
- 建議類別
    - 第 35 類
        - (3501) 網路廣告設計;電腦網路線上廣告;為商業或廣告目的編網頁索引;為商業或廣告目的彙編資訊索引;廣告傳播策略諮詢;為商業或廣告目的提供使用者評論;為商業或廣告目的提供使用者排名;為商業或廣告目的提供使用者評分
        - (3504) 建立電腦資訊系統資料庫;電腦資料庫資訊編輯;電腦資料庫管理;為他人提供電腦資料庫檢索;電腦資料庫資料更新和維護;登錄資料的更新和維護;建立電腦資訊系統資料庫;文字處理
        - (3512) 網路廣告看板租賃
    - 第 38 類
        - (3801) 通訊社服務;新聞社
        - (3804) 網際網路之電信連結;全球電腦資訊網路之電信連結;線上資訊傳輸;提供電子佈告欄之訊息傳送;電子佈告欄(電信通訊服務);訊息和影像的電腦傳輸;聊天室資訊傳輸;提供資料庫存取;提供電子連線網路資料存取服務;資料串流傳輸;數位檔案傳送
    - 第 41 類
        - (4101) 提供電子刊物線上瀏覽服務;提供不可下載之線上電子刊物;提供電子圖片線上瀏覽服務;各種書刊雜誌文獻之查詢;書刊之查詢;雜誌之查詢;文獻之翻譯;代理雜誌之訂閱。
    - 第 42 類
        - (4210) 電腦資料處理;電腦資料復原;將實體資料或文件轉換成電子載體;線上資料儲存服務;電子資料儲存服務;電腦資料備份服務;遠距資料備份;電腦資料加密服務;平台即服務(PaaS);電腦平台的開發;軟體即服務(SaaS)

---

- bil: 35 類、38 類
    - 因為裡面的資料與資訊是事實，但資料庫、資料集本身有創意，
所以 3504
    - 資料庫存取 所以 38
- MrOrz
    - 未來申請商標的類別會是[公開](https://twtmsearch.tipo.gov.tw/SS0/SS0201.jsp?showType=2&caseNo=XpJ13RyT4YzJ3Tm4yUWNyM2VSeDhldmVtT1F3QT09&caseType=1&l6=zh_TW&isReadBulletinen_US=&isReadBulletinzh_TW=true)
    - 如果選了「為商業或廣告目的編網頁索引」之類的類別，未來會不會有人拿這個做惡意解讀，如「你們說這是公益，但選了這個類別，是不是要拿志工的 effort 賣錢」
        - 如果真能有商業利益，那就可以回饋志工 [name=bil]
    - 商標是保護的概念，申請這個類別是希望如果有「其他人」任意拿這個商標做奇怪的事情的時候，我們可以主張一些權利，請他不要用這個名字作這些「為商業或廣告目的提供使用者評論;為商業或廣告目的提供使用者排名;為商業或廣告目的提供使用者評分」的事情，來保護此專案與志工做的東西。

---

- bil: logo 以及「cofacts 真的假的」共兩個
    - 已經委託第三方的話，就直接做完整即可
    - total: 4W
mrorz: 如果是防禦性的話，其實 logo + cofacts 真的假的 一起申請，一個也 ok
    - total: 2W

:::success
1. 元件：logo 以及「cofacts 真的假的」，共兩個
2. 類別：35 & 38，按照建議的子項目申請

加 安心方案，共 4W
:::

## Cofacts <> 防詐達人

> ( a ) 向使用者詢問現有回應「是否有用」，並詢問理由
> ( b ) 若訊息在資料庫卻沒有人回過，請使用者補充「為何認為此是謠言、或提供找到的資料」
> ( c ) 導引使用者撰寫新回應
> ( d ) 教育防詐達人的使用者「協作」的概念，前面的這些功能都是「協作」的一環。

- 防詐達人提出，在現有卡片中直接加上「有幫助」「沒幫助」「給意見」三個按鈕
    - MrOrz: 在使用者無法看完整回應的狀況下就給「有幫助」「沒幫助」，對編輯來說沒有太大參考性
    - bil: 「給意見」是針對個別回應，不會需要收「給 Cofacts 的意見」這件事情
    - 防詐達人不會採取按鈕方案，而是另尋方式完整呈現回應之後再給「有幫助」「沒幫助」按鈕
- Cofacts present LIFF
    - Paul: 防詐達人的使用者對 LIFF 疑慮甚深，連防詐達人自己的 LIFF 都會被使用者質疑
    - Paul 希望導向到 cofacts 網站的 reply page，MrOrz 表示會卡在 authentication 所以收不到 feedback 等東西；LIFF 反而可以解決 authentication 問題。
    - 趨勢科技要符合 ISO 相關規定，需要一個步驟明確告知使用者即將離開趨勢科技產品
    - MrOrz 可以接受多一個步驟，或許可以在這個步驟教使用者說接下來會有個 LIFF （無論是趨勢科技自己開發，還是直接用 Cofacts article LIFF）
    - 趨勢科技會再評估 LIFF solution
- Cofacts API
    - 如果要直接打 Cofacts API，需要另外傳送 hash 過的 user id。未來 Cofacts `GetArticle` 等 API 也會回傳這個 hased user id 是否之前有 upvote 或 downvote 過一則回應 
- 下週三 9pm 再 follow-up
    - 趨勢科技會再 update

---

- bil: 因為開放資料的是 Cofacts WG，所以可以希望是以 Cofacts 可以接受的方式來開放
- nonumpa: 導向到 LIFF 有內部規範，那導向到網站就可以符合規範嗎？
    - orz 好像跟是否內嵌、使用者是否可以知道自己「離開趨勢科技產品」有關


## Article LIFF

Target: receive input (feedback, reply requests) from outside of Cofacts chatbot

https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/?node-id=3004%3A224
1. [x] 實作 common component storybook
2. [x] 實作 feedback form + 使用在目前的按鈕上
3. [x] 實作 article page 的 article 部分
4. [ ] 實作 article page 的 reply - ongoing
5. [ ] 實作 article page 的 reply request form + 使用在目前的按鈕上
6. [ ] 實作 article page 的 reply request list
7. [ ] 實作 article page 的 related article

## Spammers

PR: https://github.com/cofacts/takedowns/pull/16/files?short_path=ca8bcce#diff-ca8bcce2907b4a8e70ea08606b9272e782d43cbb35aa6a79fea697fcca5afcc6

- https://cofacts.tw/user/SUOLEMEN
    - 用 hackmd 賣威而鋼
    - 一、6 如果網站協作者有廣告投放或是惡意的文章散布、違法情形，Cofacts WG 得直接終止與刪除網站使用者的帳號與其廣告內容
- https://cofacts.tw/user?id=YUOoNHsBgBgcuemXIQMD
    - 賣 VPN
    - 一、6 如果網站協作者有廣告投放或是惡意的文章散布、違法情形，Cofacts WG 得直接終止與刪除網站使用者的帳號與其廣告內容
- https://cofacts.tw/user?id=tKklhXkB9w1KR1IkVrks
    - spam
- https://cofacts.tw/user?id=YEIJLnsBgBgcuemXkv7J
    - 虛擬貨幣廣告
    - 一、6 如果網站協作者有廣告投放或是惡意的文章散布、違法情形，Cofacts WG 得直接終止與刪除網站使用者的帳號與其廣告內容
- Trust Global
    - https://cofacts.tw/article/35s3oqkdq8qys
    - 要麵麵不要辣辣的回應還在第二個，大家應該還是看得到 [name=mrorz]
    - 165 反詐騙目前還沒收錄，目前不太方便回 [name=mrorz]


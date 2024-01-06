---
tags: g0v-summit, 2020
---
# 新 Grantdash 許願池
目前的正式網站：https://propose.summit2020.g0v.tw/
目前的測試網站：https://propose.summit2020.pre-stage.cc/

## !!! 2020/06/07 War Room (上線前所有的建議都可以列在這邊)

- [x] `Lai` 依照[此文件](https://g0v.hackmd.io/@ddio/summit-2020-articles/%2FSphmcJemS5CyIuwa1KtN2w)修改中英文社群與summit簡介
- [x] `Lai` [議程委員英文](https://g0v.hackmd.io/@ODrkl-1rScWpK6S1uQCQDw/g0v-summit-2020-marketing/https%3A%2F%2Fg0v.hackmd.io%2F%40summit2020%2Fsummit-2020-cfp-wg)需要附上
    - [x] `議程委員英文缺翻譯` 台南新芽秘書長職稱翻譯、Hsinyi 委員翻譯
- [ ] `總籌組先審閱後` 修補一下[所有文案中英文部分](https://g0v.hackmd.io/iqKSTK42QXu3iRB2vGnLFw?both)
- [x] `RR` 補上徵件辦法英文（RR努力翻譯中）
- [x] 修理消失的討論區
- [x] `ddio` 講者的照片好像沒有上傳管道？  `by 熊`
    - 目前先由 third party 提供，日後再增加功能 - [name=Howard]
    - 這是 bug ， ddio 會修～ [name=ddio]
    - 看到這裡已經有一樣的 bug report 所以下面的我就刪掉了 [name=hkazami]
- [x] `howard` 刪除測試用的資料
- [x] `議程組` 填寫 sample
- [x] `ddio` 提案內容強制 CC
- [ ] `???` 需要臉書可用的圖片（也需要協助貼到sns編輯台）
- [x] `Howard` menu 加上「討論區」(forum)，連結至 https://discuss.summit2020.g0v.tw/ `by howard`
- [x] `Bess` 我有改個資同意書的機關單位名稱 >> g0v Summit 2020 Working Group 工作小組
- [x] `熊` 錯字：大島開放的Makers’ movemen->movement
- [x] `ddio` 形式希望能每個時間都變成一個選項（workshop 60 mins, workshop 90 mins etc.） `by hkazami`
- [x] `ddio` 講者資訊 url 是 optional `by hkazami`
- [x] `ddio` 摘要目前沒有辦法分行 or 分段（會很阿雜！） `by hkazami`
- [x] `hkazami` 「g0v summit 2020 特色」＆「投稿方法」的內容希望可以分段（每個特色之間空一行或間距拉大）
- [x] `ddio` 投稿頁面裡沒有寫說星號代表的意思是必填欄位（雖然他送不出去的時候就知道了） `by hkazami`
    - 就先當作共識XD - [name=Howard]
    - 改為若是選填欄位，則在說明裡提示 - [name=ddio]
- [x] `ddio` sample 提案列表 「假新聞在不同國家的樣貌與跨國合作」破版 `by howard`
- [x] `Lai` owner pic 若會顯示，可能要提供破版時的預設圖片 `by howard` -> 暫時的破版，等修好頭像相關的 issue 後就會恢復正常
- [x] `howard` 標題 "Call for Proposal" 的 proposal 應該要加 s（至少大多其他 conference 的 CFP 是這樣寫的） `by hkazami` 
- [x] FAQ 的按鈕和標題可以補上中文「常見問題」 `by hkazami` 
- [ ] 討論區的粗體在投稿網頁上不會顯示為粗體，可能還有其他東西也是兩邊顯示不一樣的，不過基本上不影響功能所以可以再看要不要做。 `by hkazami`
- [ ] 議程委員的簡介裡有用到中英夾雜的地方，在英文前後各加一個半形空白（強迫症發作）`by hkazami`
- [ ] 「通知投稿結果 Notification of accepted proposals：八月底」的後面加上英文 "End of August" `by hkazami`

## 亂入區
- 想要趕快取一個新名字～ [name=hkazami]
- 叫他 proposal 如何？ [name=Howard]
- 投稿大平台(好爛) [name=pipi]
- 反對 proposal，因為到時候會出現 「那個 proposal 上面的 proposal 怎樣怎樣～」這種奇怪的句子，有點難溝通ＸＤ，但改成 prop 或是 propo 之類的就沒問題（欸 propo 聽起來像波波好可愛😂） [name=hkazami]
 
## 後端：資料庫存取介面
- 要能依照使用者身份（組別、是否為組長等）劃分可以 access 和不能的欄位
- 要可以讓（不會寫 code 的）使用者編輯欄位
- 這個資料庫要跟 summit 主網站是同一個
    - User story：議程組員要幫某講者改 title，他就進這個介面更改然後儲存。然後 summit 主網站會定期去撈資料庫的資料，這樣講者的 title 就能被自動更新。
      - Acceptance Criteria: 
        1. 一個 API 下載所有可公開顯示的資料的 json 檔，因為只抓公開資訊，可考慮做成不須認證，或只做簡單認證的 API (ddio 提議)
        > 所以自動更新的 workflow 會是 summit 主網站定期去 call API 抓公開資訊的 json 檔回來放在自己的 database 上再 show 在主網站上這樣嗎？ [name=hkazami]
        > 會有 project list 和 project API，只要在主網站 ajax 就能取得，不用寫 cron 自動更新 [name=Howard]

## 前端：投稿頁面
- 送出前要給他們看[g0v summit 2020 個人資料蒐集、處理及利用同意書](https://g0v.hackmd.io/iqKSTK42QXu3iRB2vGnLFw?view#g0v-summit-2020-%E5%80%8B%E4%BA%BA%E8%B3%87%E6%96%99%E8%92%90%E9%9B%86%E3%80%81%E8%99%95%E7%90%86%E5%8F%8A%E5%88%A9%E7%94%A8%E5%90%8C%E6%84%8F%E6%9B%B8)（還沒 finalize）並同意才能送出
- 欄位[在這](https://g0v.hackmd.io/iqKSTK42QXu3iRB2vGnLFw?view#%E6%8A%95%E7%A8%BF%E6%96%B9%E6%B3%95)（還沒 finalize）
- 改稿介面：讓每個欄位都允許修改，然後每次改完稿按 save 都把舊的保留起來新的另外存，不要 overwrite
    > 目前的設計是照 grantdash 的方式，每次 blur 欄位都會存 draft，然後每次 save 都會是一個 version [name=Howard]

## 前端：討論區
「討論區」指的是這東西：https://discuss.grants.g0v.tw/
- 聲望制度可以關掉嗎？
    - Howard 已在 Slack 回答：可以
- 若有登入投稿系統就會自動在討論區建立帳號
    > 我的想法：投稿者應該先建帳號，然後用同一個帳號投稿、改稿、留言討論，這樣的話想投複數個稿件的人就用一個帳號就好；一般使用者就直接在討論區建帳號。但技術上不知道會不會變很繁雜？舊 grantdash 的處理方式是？ [name=hkazami]
    > 我比較頃向跟目前 grantdash 的方式一樣，統一由 proposal 登入，所以若是在 discuss 點擊登入，就連結回 discuss 的登入頁面，這樣比較不會有多個入口，可以統一管理 [name=Howard]
    > 應該來列一下投稿者在第一次投稿時、修改稿件時、投第二份 or 第n份提案（雖然可能不太會有人這麼做？ＸＤ）會走的 workflow 各是什麼。
- 投稿成功的時候就自動為這個專案建立一個討論串
    - 在「各投稿討論區」底下
    - 討論串的第一篇文是系統自動發的模板式歡迎文，並附上稿件連結
        - 舊的 grant 有連結，只是沒有模板式歡迎文
    - 那區除管理員外無法 po 文只能回文
        > 權限已經設好 [name=hkazami]
- 討論區要分哪些區塊？
    - 目前有公告區、提案討論區和一般 feedback 區
- 有問題的留言可以讓管理員一鍵送真的假的資料庫
    - 如何回傳查證結果?

## 前端：提案內容瀏覽頁面
「看提案頁面」指的是這東西：https://grants.g0v.tw/dashboards/2019a?sort=showcase
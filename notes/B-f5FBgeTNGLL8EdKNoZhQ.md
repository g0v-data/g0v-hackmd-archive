---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210203 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, 超, hsiao, 斌綸, lucien
:::

:::info
2/10 不開會～～～
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

https://github.com/cofacts/rumors-site/releases/tag/release%2F20210122

- #381 #382 #383 Editor hint -- kudos to ulayab
    - Fixes: [#362](https://github.com/cofacts/rumors-site/issues/362) Provide better text for reference input
    - Fixes [#361](https://github.com/cofacts/rumors-site/issues/361) Provide better placeholder for editors
- #385 Avoid attaching text for logged in users
- [#384](https://github.com/cofacts/rumors-site/pull/384) Update terms to match suggestion from Lucien

### :rocket: Staging

#### :robot_face: LINE bot

- #238 handle group messages

### :eye: Under review

#### :robot_face: LINE bot

- #238 handle group messages
   - hi cofacts 跟 cofacts 的相似度是 0.8
     hi cofacts 跟 hi confacts 的相似度是 0.82
     為了讓比對更嚴謹一點(只允許使用者少打一個s之類的錯誤)，特別把 hi confacts放進比對列表，而不是把 hi cofacts 的比對相似度調成 0.82 或 0.8
     
     
- 一次噴四個有點多，尤其是出處，所以會很可怕，會有人覺得是危險連結。希望可以不要放出處。另外，CC BY SA 也可以不用。只回第一個、第二個比較符合邏輯。 [name=bil]
    - 在群組的對話脈絡，一直放連結好像不太好，也有可能有危險。
- 換成橫向 carousel [name=斌] 
    - +1 [name=lucien] [name=mrorz]
    - 可以先 release 現在的版本，然後再討論要如何放 carousel [name=mrorz]
    - 但 carousel 不太像人對話的感覺，不太親切。群組的對話感是重要的 [name=bil]
    - 如果是 carousel 的話，反而比較清楚，不會跟對話混在一起 [name=斌]
    - 可以第一句話打招呼是對話，放資訊的部分用 carousel [name=mrorz]
- test 不會停，可能是 bull 的問題，但 localhost 無法重現 [name=斌]
     
#### :globe_with_meridians: Site

- Openpeeps avatar https://github.com/cofacts/rumors-site/pull/357

## 2021 二月三月計畫

- 2 月：公布新 terms 與 API header
- 2/4 AI4SG
- 2/5 授權諮詢
- 2/14 趨勢 Forward Thinker Award
- 2/21 編輯小聚
- 2 月底：Cofacts 影響力報告網站
- 2 月底：chatbot LIFF redirect 設定
- 2 月底：給金控的 pitch deck
- 3 月初：enforce API header
- 3/5 簡訊設計影片完成

### 新 terms & API header
> Owner: MrOrz

- [x] 開發者溝通
    - [x] carol
    - [x] kalin
    - [x] 來寄信問過的
- [x] Prepare pull requests for license change
    - [x] API: https://github.com/cofacts/rumors-api/pull/245
    - [x] opendata https://github.com/cofacts/opendata/pull/21
    - [x] rumors-site https://github.com/cofacts/rumors-site/pull/387
    - [x] rumors-line-bot https://github.com/cofacts/rumors-line-bot/pull/240
- [x] 社群溝通: FB group
- [x] opendata 表單 https://forms.gle/nYaaVSLDX5i5vScT7
- [ ] 2/17 第一版公布
- [ ] 開發[API client application 管理機制](https://github.com/cofacts/rumors-api/issues/244)
    - backward compatible: 沒送 app-secret 的也會 match 到某個開發用 app
- [ ] 3 月：enforce API 管理
    - 保留 staging 上的開發用 app
    - 移除 production 上的開發用 app

### 2021 AI4SG Award
> bil & lucien

### 跟新芽協會了解與金控募捐的方法

對方有跟銀行金控募資的豐富經驗，分享了幾個重點：

- 對於有資源的企業 CSR 部門，做不同主題 NPO 並不會競爭同一塊資源，所以不用擔心我們去競爭
- 對於金控來說，我們必須找到一個能幫助企業宣傳 CSR 的故事來說服對方。
- Cofacts 的 chatbot 以及網站已經有不少流量，如果在查詢過程中顯示這些贊助商資料，其實是很有機會的
- Ex. 此查核訊息服務由XX所贊助。 放在 chatbot 查核回應跟網站查核回應頁面上。
- Todo ：
    - 詢問能不能在 line chatbot 上提及贊助
    - 整理能曝光位置的流量
    - 整理 CSR 的故事


### 商業授權諮詢
> bil & lucien

### 2/14 趨勢 Forward Thinker Award

- [官網](https://www.trendforward.com/forward-thinker.html)
- [報名表](https://docs.google.com/forms/d/e/1FAIpQLSf0yJBDxDVoE0MBrbiQbDBchJI8dJeZ8gl7DTPlJ0BNss6N1Q/viewform)
    - 看重「人」而不是「公司」
- [Full rules](www.trendforward.com/forward-thinker.html?modal=official-rules-2d3afa)



### 第 23 次小聚
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
    - Keyholder: ronny
    - [ ] 場地單
    - [ ] 食物
    - [ ] 延長線 (場地有)
    - [ ] wifi
        - [ ] Nighthawk M1 + 4G sim
        - [ ] ASUS RT-N12 Wireless N300 (2x 5dbi高增益天線)
- [ ] 誰會來呢？bil
- [ ] 誰不會來
- [x] 志超做圖
- [ ] LINE 文案：


### 二月開發項目
> zoe, 宇彤

### LIFF redirect
LIFF legacy redirect 看來還是得趕快改掉，3 月會失效囧
https://taichunmin.idv.tw/blog/2021-01-19-line-liff-v2-replace-deprecated.html 

相關討論：https://g0v.hackmd.io/U-KmeEYJTVmtCFB-bqWfGg#LIFF
> 我可以幫忙 [name=nonumpa]
## Editor 相關 UI idea

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
> 24hr 但落在昨天：yesterday
昨天以前：月、日
其他：年、月、日

Or use https://date-fns.org/v2.16.1/docs/formatRelative for time difference within 48hr
:::

### 推薦標籤

> Idea: 利用「相似可疑訊息」的分類來推薦分類。可以在「分類建議」按鈕後面做一鍵增加的鈕。
> 例如說 COVID-19 的新訊息 https://cofacts.tw/article/j1al35fna5au ，進來的時候還滿常有已經標過分類的相似可疑訊息，但每次點開「分類建議」按鈕都要找好久的分類。
由於分類未來只會越來越多、手機螢幕大小依然有限，list traversal 本身無法改進太多（最有用的可能是加個搜尋框），不如直接用「相似可疑訊息」的分類來推薦。
> [name=mrorz]


## 其他變更

### SEO & nginx 設定
https://github.com/cofacts/rumors-deploy/pull/15

想要把 cofacts.tw 當成 canonical URL
- 比較短
- 可以把打錯字的 cofact.tw 也導向去 cofacts.tw

---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210120 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, lucien, 文武, hsiao, nick, mrorz, zoe
:::

## :potable_water: Release pipeline

### :star: Released to production

https://github.com/cofacts/rumors-site/releases/tag/release%2F20210120

- [#376 landing page fix](https://github.com/cofacts/rumors-site/pull/376)
    - Fix「landing page header 多了底線」
    - Fix 「landing page menu 變白的時機太晚 」

### :rocket: Staging

#### :globe_with_meridians: Site
- profile page PRs #367, #374, #368, #369, #375, #373
    - merged due to inactivity
- [#378](https://github.com/cofacts/rumors-site/pull/378) profile page for editor themselve

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
    - [ ] ~~Sorting works~~ 無此功能，已經按照相關度排序
    - [x] Can go to article page
  - [x] Can list searched replies
    - [ ] Can go to reply page - 手機版無法

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

- 長內容破版 https://github.com/cofacts/rumors-site/issues/390

### :eye: Under review

#### :globe_with_meridians: Site

- [#378](https://github.com/cofacts/rumors-site/pull/378) profile page for editor themselve

## 2021 一月二月計畫

- 1/18 (一) license 會議
- 1/20 (三) 決定 license attribution & terms
- 1/21 (四) Pitch deck
- 1/22 (五) TWB 影片上線
- 1/23 (六) g0v 大松、演講
- 1/31 COVID-19 Open fund close
- 2 月：公布新 terms 與 API header
- 2/21 編輯小聚
- 2 月底：enforce API header

### 1/21 Pitch deck
> 1/21 11:00AM 
- One pager appendix
- MrOrz 開頭 10p 內 impact
    - 2020 年的 input / output
    - 先問對專案的興趣
    - 2021 年的計畫 = 重現 2020 狀態
    - 最低：固定支出
    - 中間：專案執行
    - 最高：基金會

### 1/23 大松
- 誰會來：MrOrz
- 協作頁面
- good first issues

MrOrz: 錄影剪輯

### 1/23 演講

需要多少份傳單？（剩下40份 + N 份）

### 1/31 GNI COVID-19 Open fund

- [Google Keyword blog post](https://www.blog.google/outreach-initiatives/google-news-initiative/open-fund-projects-debunking-vaccine-misinformation)
- [Program website](https://newsinitiative.withgoogle.com/covid-vaccine-counter-misinfo-fund/)
- [Frequently Asked Questions](https://newsinitiative.withgoogle.com/covid-vaccine-counter-misinfo-fund/how-to-apply#faqs)

See [google doc](https://docs.google.com/document/d/14cctKsNTAUXO__ThbhWf0kseqx_T0LzpXDEQmVFzYgQ/edit#).

:::success
billion 找 ivy、TFC summar 問。
mrorz 用 FB 問 Charles 是否有興趣。
:::

### 2 月 License

https://hackmd.io/YwmDbZiOTViswZYFRDj_NQ
https://hackmd.io/1DsLg4T6SdGpBBHebHogbw
https://hackmd.io/U_OK5FOvQ_-Fiju_OOYO6w

:::info
See [CC BY-SA 授權法律確認事項](https://docs.google.com/document/d/1cABQrJHPjsnJ6401Y60JLF3tZ6FGtpggvjd2V179FEw/edit?usp=sharing)
:::

Action items
- 分成「網站」「chatbot」「開放資料」三份條款
- [網站條款](https://docs.google.com/document/d/1JvKQFnkmH75jR9QUfkEnUi_Gro12TmEcdb5thQFpJng/edit)、[chatbot條款](https://docs.google.com/document/d/1Mfz2Av17cXqf01QHFlOL8AY5kBA9kn2dYxqyNni5Hg8/edit)要加入「只限於自然人使用，禁止機器人」的敘述
- 網站條款：
    - 「提交時當明確標示該等資料權利歸屬於第三方之狀態。」太嚴格，應該改成「提交時應提供原創作出處」即可
    - 「若提報資料的著作權利歸屬於第三方，則敦請LINEBot 使用者協助標示其歸屬狀態。」LINE bot 使用者沒這個能力，建議只要免責說不保證資料裡沒有侵權，使用者要注意。
- 開放資料條款：https://docs.google.com/document/d/1ptywehV7VLKeXADsCuqx0klVyRmnxhnon92p6xSD1zg/edit
	- 確認顯名規範
	- 要把 LINE 內（要求 @cofacts）與非 chatbot 分開寫嗎？
	    - 一律寫成 LINE bot 版本為預設，其他為例外 [name=bil]
	- API 的 app ID 管理實作 https://g0v.hackmd.io/51wwLHgvSUqtBDaP-yAVnA
	:::success
    Implement ASAP
    :::
- 改網站內文
    > 以上內容由「Cofacts 真的假的」訊息回報機器人與查證協作社群提供，以 CC授權 姓名標示-相同方式分享 4.0(CC BY-SA 4.0) 釋出，於後續重製或散布時，原社群顯名及每一則查證的出處連結皆必須被完整引用。 
    > The content above by "Cofacts crowd-sourced fact-checking community" is provided under CC BY-SA 4.0, the community name and the provenance link for each item shall be fully cited for further reproduction or redistribution. 
    - chatbot 要改嗎？
        - 不要 [name=bil]

### 二月開發項目

- Profile page contributor chart 與相關 API
	- 需要類似 github 的這種外觀 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d7e49c39a2d28c82dca9388c4ca67923.png)
- ListArticle articleReply filter: https://github.com/cofacts/rumors-api/issues/243
- ListArticleReplyFeedback 增加 `articleReplyOrReplyFrom` filter？
	- 用「自己的回應最近被評價」來排序
	- 計算 profile page「查核好評」數
	- 需要在 article reply feedback 上增加 articleReplyAuthorId 與 replyAuthorId
	> 如果沒有要算「自己回應有多少讚」，好像不太需要做，因為可以用 ListArticle nested filter⋯⋯
- badge 系統 API

### 2/21 第 23 次小聚
- [ ] 主題：大過年的來闢謠
- [ ] 時間：2/21（日）
	- **活動時間：14:00 - 17:00**
	- 場地借用 13:30 - 17:30 （上限 4hr）
- [ ] KKTIX
- [ ] 準備貼紙
- 場地：NPO Hub 4 樓廚房 （台北市中正區重慶南路三段 2 號 4 樓）
    - Keyholder: ronny
    - [ ] 場地單
    - [ ] 食物
    - [ ] 延長線 (場地有)
    - [ ] wifi
        - [ ] Nighthawk M1 + 4G sim
        - [ ] ASUS RT-N12 Wireless N300 (2x 5dbi高增益天線)
- [ ] 誰會來呢？
- [ ] 誰不會來
- [x] 志超做圖
- [ ] LINE 文案：

## 影片 60 秒


## Profile page pilot study results 

成果：https://g0v.hackmd.io/lIedGsQWTeScBTWfr4Zq0w

- 增加 Lv.17 (ㄇ), Lv.16 (魔人啾啾)
- 增加顯示「何時加入 cofacts」[name=一-4]

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
> 
### 登入鼓勵

> 是說 etoro 每天第一次登入的時候，都會說「恭喜！您最近 N 天賺了 OO 」或「報酬率 OO%」
> 發現那個天數常常會變，感覺像是他準備了幾個數字，然後 show 一個正最多的數字這樣。
> 如果一日報酬率是負的，就試試 7 天報酬率之類的 XDDD
> Cofacts 如果也實作這個大家覺得如何？ XDDDD
> 網站第一次登入的時候利用現在的 API 拿到不同區間的各種數字，然後挑一個棒的來顯示之類的
>「你的回應最近 7 天超熱門，有 42 人看過」
>「最近 30 天有 690 人覺得你寫的回應很棒！」
>「24 小時內對你的回應說讚的人增加了 300%！」
>「最近 7 天你寫的回應被其他編輯引用了 9 次唷！」
> [name=mrorz]

## 其他變更

### SEO & nginx 設定
https://github.com/cofacts/rumors-deploy/pull/15

想要把 cofacts.tw 當成 canonical URL
- 比較短
- 可以把打錯字的 cofact.tw 也導向去 cofacts.tw
- Cofacts LINE bot 也換成 cofacts.tw？

### LINE LIFF redirect

LIFF legacy redirect 看來還是得趕快改掉，3 月會失效囧
https://taichunmin.idv.tw/blog/2021-01-19-line-liff-v2-replace-deprecated.html 

## Downstream bot 數據彙整

趨勢科技有：
- 任意時間範圍的「偵測到有謠言的次數」（無論 Cofacts 是否有回過）
- 2020/10/16 起的每週 Cofacts 結果卡點擊數（referral count）


美玉姨有：
- 2020 年 LINE bot reply message count by 月、週、日
- 2020 年 LINE bot 增加好友數 by 月、週、日
- 2020/11/20 起的個別 article 詢問次數 by 日

交集：無⋯⋯囧

## Line bot 群組功能
- 需要自介文，輸入 'Hi Cofacts' 時回應的
- 要處理其他 case 嗎 : Hi cofact | Hi, cofacts | Hi confacts | Hi, confact
    > 可以不處理，因為打錯不回應，使用者馬上就知道打錯
    > 要處理的話，把 "," 去掉轉小寫，再用 string-similarity?
- job queue 用 `Bull`，它[自己說](https://github.com/OptimalBits/bull#feature-comparison)它很厲害
    - rate limit: 每幾毫秒要處理多少 job，好像沒辦法知道達到限制了
      > 要設多大?
    - process concurrency
      > 要設多大?
    - timeout: Bull 的 timeout 會在 job 開始跑才會計時，不適合用在這裡，要自己處理 
      > `Date.now() - event.timestamp` 
      > 可以順便紀錄花多長時間處理 request
    - 把 image 也改用 Bull 處理？
- 被加入多少群組：可以用 join/leave event，不知道有沒有其他的方式可以看
- 新增一個 category : 免費訊息詐騙


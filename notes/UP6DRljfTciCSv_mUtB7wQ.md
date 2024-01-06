---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220629 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：mrorz, nonumpa, bil, 4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :robot_face: rumors-line-bot

- New feedback sending mechanism https://github.com/cofacts/rumors-line-bot/pull/312
- Batch GraphQL sending from LINE bot to API https://github.com/cofacts/rumors-line-bot/pull/313
- Remove unused handler state & "URL token" authentication logic https://github.com/cofacts/rumors-line-bot/pull/315

雖然主要是改 feedback flow（左側），但因為有拿掉一些 fundamental 的東西（如把 JWT token 放在 LIFF URL 裡）所以還是都測測看。

![New flow](https://camo.githubusercontent.com/51f6df16cbcc26bff96d7a812f1d5d5a1b3e0b9a70427a3958c46310862c6089/68747470733a2f2f646f63732e676f6f676c652e636f6d2f64726177696e67732f642f652f32504143582d317652756a5974545273536e48337873755230424d72374b4a346f5950393077427759556533365075456548704f6368684543566a7178305251467a785751544c6148346b7661634837633662385a662f7075623f773d3134343326683d383830)

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 應可送出「全新訊息」
    - [x] 問訊息來源時選擇「我自己打的」會被擋下。
    - [x] 選擇「整篇轉傳」後會詢問是否要送出訊息。
    - [x] 不同意送出訊息後可以收到感謝。
    - [x] 同意送出訊息後就會送出訊息，並得到：
        - [x] Cofacts article page 按鈕
        - [x] 寫理由的按鈕
        - [x] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面
        - [x] 「分享到 Facebook」、「分享到 LINE」且可以正常運作
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以再打開理由視窗，此時會載入上次填寫的理由。修改理由送出後，查看 article page 看理由是否有被送出。

- [x] 送出「沒回應」的舊訊息，應可送出新理由
    - [x] 文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以修改理由送出。查看 article page 看理由是否有被送出。
    - [x] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面

- [x] 送出「有多則回應回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應
    - [x] 選擇回應之後可以幫回應 upvote
    - [x] 可以再次選擇 downvote
    - [x] 選完回應之後，還可以捲回去選其他回應
    - [x] （若沒開啟推播）應該要看到「開啟小鈴鐺」泡泡，且可打開 setting 頁面
    - [x] 選其他回應之後，**捲回去前一則回應 upvote 或 downvote**，評價應該會落在正確的那則回應上，而不是在最新的回應

- [x] Rich menu 測試
    - [x] 「設定」更改後再次打開，應該會保留原本設定
    - [x] 「教學」可以觸發教學流程

##### ⛔️ Release Blockers
N/A

- 口氣很溫和的機器人，請謝謝對不起，好的抱歉不好意思，很有禮貌 [name=bil]

#### :globe_with_meridians: Site

透過網站檢測一下 master --> release/20220505 之間進的功能
https://github.com/cofacts/rumors-api/compare/release/20220505...master


##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] Article list
  - [x] Filter works
  - [x] Sorting works
  - [x] Can go to article page
- [x] Hoax for you
  - [x] Filter works
  - [x] Can go to article page
- [x] Article detail
  - [x] Can see similar messages
  - [x] Cannot submit, upvote, downvote reply

登入自有帳號後檢測：

- [x] Replies list
  - [x] 可選擇 Replied by me
  - [x] can upvote / downvote replies
- [x] Article detail
  - [x] Can submit, remove own reply
  - [x] Can upvote, downvote other's article reply

##### ⛔️ Release Blockers

##### 未竟項目

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0ef43e10cabac8df9af88c19d2ec8a28.png)
- 「一個月內」filter 不是 for 這個使用者的 article reply 而是文章的最新 reply，導致 filter 不準確
- tab 裡的計數應該要跟 filter 連動，比較有用；tab 裡目前的數字跟最上面重複。
  - filter 可能要移到 tab 上面，比較能呈現 filter 會影響 tab 這件事

:::success
另外開票處理 profile page filter fix
https://github.com/cofacts/rumors-site/issues/492
:::

### :eye: Under review

- LINE bot image proxy [name=nonumpa]
    - https://github.com/cofacts/rumors-line-bot/pull/311
    - 改成 stream proxy + forward headers?
- (On staging) LINE chatbot feedback mechanism revamp [name=mrorz]
    - New feedback sending mechanism https://github.com/cofacts/rumors-line-bot/pull/312
    - Batch GraphQL sending from LINE bot to API https://github.com/cofacts/rumors-line-bot/pull/313
    - Remove unused handler state & "URL token" authentication logic https://github.com/cofacts/rumors-line-bot/pull/315
- (On staging) API bugfix [name=mrorz]
    - https://github.com/cofacts/rumors-api/pull/286
- Community builder revamp [name=mrorz]
    - https://github.com/cofacts/community-builder/pull/12
    - Depends on API deployment
- File variant support in media manager
    - https://github.com/cofacts/media-manager/pull/4

### Migration
Feedback author 欄位 https://github.com/cofacts/rumors-api/pull/285#issuecomment-1159399583
- Reindex takes 10 minutes
- Migrating 318K feedbacks in 16 minutes

## Image support
> https://github.com/orgs/cofacts/projects/9

New tickets
- File variants ([cofacts/media-amanger#4](https://github.com/cofacts/media-manager/pull/4)) & its application to rumors-api ([cofacts/rumors-api#287](https://github.com/cofacts/rumors-api/issues/287))
- MediaManager documentation ([cofacts/media-manager#5](https://github.com/cofacts/media-manager/issues/5))

### Image proxy
https://github.com/cofacts/rumors-line-bot/pull/311/files#

- `downloadFile` 回傳的是 response object 不是 file，body 是 ReadableStream [name=nonumpa]
- `ctx.body = result.body` 就是 stream proxy 了

### Chatbot image search

- API & flow 都不一樣
  - 會寫新的 handler for 圖片 [name=nonumpa]
  - 即使 search hash 一樣，也可能圖片不一樣，所以還是要顯示 [name=nonumpa]
- Wording
  - 先比照 https://g0v.hackmd.io/eo8NM1VGQ7qxaamBZXRPtA#%E9%80%81%E5%87%BA%E8%A8%8A%E6%81%AF-wording 出個 hackmd 下週大家一起過 [name=nonumpa]

### File variant support
https://github.com/cofacts/media-manager/pull/4

:::success
6/30 PR review :pray:
:::

### Design

- https://github.com/cofacts/design/issues/1
- Where is 調整字體大小的 Figma?
  - https://www.figma.com/file/6yJZnwNYJciyH7mrhPvyZs/Cofacts-website-(Interview)?node-id=5081%3A1216

:::success
bil 幫找 figma link :pray: 
:::


### GCS 圖片對外

- 希望 original 原始圖檔 / 影片 / 檔案只有登入後才拿得到
    - Original variant 全部 private，只透過 signed URL 對外
- GCS bucket 直出 traffic 有點貴
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9198e297ad7ffbb005834cfb75bf5f07.png)
    - 這是以原檔 200KB 計算
    - 如果 preview 圖檔控制在 50KB 的話，就是 1/4 的錢 (50usd/mo)
- Cloudflare images
    - Variant 直接由 cloudflare 管理
    - request 比較便宜 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_752cfa4346b474858da5c8e8faf2c3cc.png)
    - 但還沒研究 Cloudflare images API，且目前 MediaManager 實作與 GCS 耦合，較難拆開
    - Cloudflare images 無法處理影片與聲音，仍需另外實作
- 直接在 GCS 的縮圖 variant 前面擋 Cloudflare CDN 減少 GCS traffic？
    - https://community.cloudflare.com/t/using-cloudflare-cdn-https-with-google-cloud-storage/15602
    - https://stackoverflow.com/questions/35116278/use-cloudflare-to-cdn-a-google-cloud-storage-bucket
    - CNAME to storage.googleapis.com (GCS public URL) https://medium.com/@pablo.delvalle.cr/cloudflare-and-google-cloud-for-hosting-a-static-site-fd2e1a97aa9b

## Trend and contribution
> https://github.com/orgs/cofacts/projects/10

- Feedback enhancement done
- LIFF trend ETA end of July

## Moderation

### 腦控洗版
- 決議：至 FB group 發文討論 https://g0v.hackmd.io/Gf45qq-9T9GLMkSrsfXG1A#%EF%BC%A8%EF%BC%A3%EF%BC%B2-%E8%85%A6%E6%8E%A7
- 尚未貼文

### 政治立場不同者的檢舉 

- 決議：不修改資料庫 https://g0v.hackmd.io/Gf45qq-9T9GLMkSrsfXG1A#%E9%87%9D%E5%B0%8D-Lopi-%E7%9A%84%E6%AA%A2%E8%88%89
- 尚未撰寫 Cofacts WG 判斷

### 疫苗陰謀論遭檢舉

- 被檢舉人資訊 https://cofacts.github.io/community-builder/#/editorworks?showAll=1&day=365&userId=cyWkqn4BvUvLpBdgXhV_
- 不用封鎖
- 尚未撰寫 Cofacts WG 判斷

## 「編輯」一詞

- 查核者/查核員 [name=bil]
    - 英文下 fact-checker 最好理解
- 不建議 fact-checker 的理由是 [name=mrorz]
    - 一般 fact-checker 不處理個人意見
    - 因為那不是客觀上要去 fact-check 的東西
    - 但 fact-checker 也是可以處理個人意見 [name=bil]
- 編輯：新聞室那個主管？ [name=bil]
    - 英文問題比較大
    - 中文裡「編輯」同時是動詞跟名詞，很麻煩
    - 相較於 news room 只有一個主編，我們讓真的假的網站上面的每個人都可以是獨立的編輯 [name=mrorz]
    - 當時可能是刻意去貼近編輯室現有名詞的[name=mrorz]
    - 「編輯」跟「查核員」，感覺查核員會在編輯之下 [name=mrorz]
- OSINT 領域：investigator
    - https://www.bellingcat.com/contributors/
    - Open-Source Investigator 是個職缺 https://www.indeed.com/q-Osint-Investigator-jobs.html?vjk=37db1056c4d6688e 
- 查核協作者 [name=bil]
    - collaborator
    - https://github.com/cofacts/rumors-site/blob/master/LEGAL.md 是用網站協作者 [name=mrorz]
- 要改的 effort
    - 更新[使用者條款們](https://github.com/cofacts/rumors-site/blob/master/LEGAL.md)
    - 網站到處的地方
    - 編輯小聚
        - 編輯可以視為動詞 [name=bil]
        - 「編輯協作者小聚」[name=mrorz]
    - https://www.youtube.com/watch?v=LkwOLicel4A
        - 編輯還是視為動詞 [name=bil]
- 「協作者」會有 fact checker, designer, developer, etc [name=bil]
- 「編輯協作者」比較可以承先啟後 [name=mrorz]

:::success
大家回去想想
下週再定案
:::

## 商標

- 商標名稱：Cofacts 真的假的
- 附註：本件商標不就「真的假的」文字主張商標權
- 今天處理 [name=ggm]

## 小聚籌備

7/2 新北市政府

【7/24, 7/16】

新嘗試
- [revamp 第二階段介紹](https://g0v.hackmd.io/_HXxDu6OQPaK08WFwOshtg#%E5%B0%8F%E8%81%9A%E6%AA%A2%E8%A8%8E)
- [不用 spreadsheet，直接用主題分](https://g0v.hackmd.io/_HXxDu6OQPaK08WFwOshtg#%E5%B0%8F%E8%81%9A%E6%AA%A2%E8%A8%8E)

:::success
bil 借 impact hub
:::

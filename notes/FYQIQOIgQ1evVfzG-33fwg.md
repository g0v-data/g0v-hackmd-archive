---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220907 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis: mrorz, bil, ben
- 線上出席：nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

- Site article list `articleTypes` arg: https://github.com/cofacts/rumors-site/releases/tag/release%2F20220825

#### :robot_face: rumors-line-bot

- Image search and submission https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20220825

### :rocket: Staging

#### :robot_face: rumors-line-bot
https://github.com/cofacts/rumors-line-bot/pull/321

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 送出圖片查詢，可以回傳類似圖片

#### :globe_with_meridians: Site

- API: related image article https://github.com/cofacts/rumors-api/pull/291
- Site: related image article https://github.com/cofacts/rumors-site/pull/502

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] Article list
  - [x] Filter works
  - [x] Sorting works
  - [x] Can go to article page
- [x] Article detail
  - [x] Can see similar messages

##### ⛔️ Release Blockers

##### 未竟項目

上線後可以測試傳這張圖
https://cofacts.tw/article/j4pZ7IIBv5it-Cx_Smz0

會不會拿到 reply

### :eye: Under review
- API https://github.com/cofacts/rumors-api/pull/291
- Site https://github.com/cofacts/rumors-site/pull/502

## Image support
> https://github.com/orgs/cofacts/projects/9

### 上線後追蹤：主機繁忙程度

上線時間：8/25 2:04AM

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d8e1c03011b3dee04860b256f1880f33.png)

### 上線後追蹤：重複圖片

#### Case: [白蝙蝠](https://dev.cofacts.tw/article/q4oK1YIBv5it-Cx_b1ZI)

- Article ID: `q4oK1YIBv5it-Cx_b1ZI`, `rYoK1YIBv5it-Cx_b1bl`, `rIoK1YIBv5it-Cx_b1Z4`
- Hash 都是 `HIeeOA.YOUA9wD_Af8AOgPgD-D__hwIP7g_4B_gH_xH_w_hAAA`
- 使用者都是 `j4S8C_LZoGB2VN0N7xIu_3ebkFEfhxqMBDFx8VJ8DCRiiamzM`, 建立時間都是 `2022-08-25T12:46:47.XXXZ`
- 應是手抖，連按了三下送出⋯⋯
    - Article 有針對文字內容計算 ID，所以連點也都會算成同一個 article
    - 考慮送出文章改成 quick reply?
- 但是 postback 應該有 expire 檢查 [name=nonumpa]
  - 可以先看看能不能重現手抖，可以重現就代表 expire 機制沒有擋住 [name=mrorz]
  - 開票追蹤

| Log Time | Input | Response |
| -------- | -------- | -------- |
| 2022-08-25T12:46:14.741Z     | Image     | 抱歉沒有找到你想要查詢的訊息。<br>你要請人查查這則訊息嗎？<br>（送出選項）|
| 2022-08-25T12:46:16.365Z | `__POSTBACK_YES__` (ts=1661431573835) | 收錄至 https://cofacts.org/article/pYpI1IIBv5it-Cx_hFVE |
| 2022-08-25T12:46:47.552Z | `__POSTBACK_YES__` (ts=1661431605828) | 收錄至 https://cofacts.org/article/q4oK1YIBv5it-Cx_b1ZI |
| 2022-08-25T12:46:47.575Z | `__POSTBACK_YES__` (ts=1661431605907) |  收錄至 https://cofacts.org/article/rIoK1YIBv5it-Cx_b1Z4 | 

:::info
開票追蹤 - https://github.com/cofacts/rumors-line-bot/issues/322
:::

#### Case: 65歲免費領一份5劑

- 65歲免費領一份5劑快篩這圖片有重複 [name=cai]
- https://cofacts.tw/article/o4pH1IIBv5it-Cx_fFUp
- https://cofacts.tw/article/pYpI1IIBv5it-Cx_hFVE
- https://cofacts.tw/article/PIq81IIBv5it-Cx_HVbc
- https://cofacts.tw/article/gIow1IIBv5it-Cx_x1UF

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d2c17d2196aee41234e44e93c8d12788.png)

> 快篩那 4 張非常奇怪，時間間隔滿久的
> 理論上後送進來的應該都可以在選項裡看到高度相似的圖才對
> 還有一個 search hash 不同但 id hash 卻相同的
> 整個見鬼不知道發生什麼事情

| Log Time | User ID | Input | Response |
| -------- | -------- | -------- | ---- |
| 2022-08-25T08:24:53.897Z | `U02c...b80c` | 傳圖 | 沒查到，詢問送出 |
| 2022-08-25T09:13:51.271Z | `U02c...b80c` | `__POSTBACK_YES__` | 收錄至 `o4pH1IIBv5it-Cx_fFUp` |
| 2022-08-25T09:14:39.291Z | `U863...666b` | 傳圖 | 沒查到，詢問送出 :question: | 
| 2022-08-25T09:14:58.916Z | `U863...666b` | `__POSTBACK_YES__` | 收錄至 `pYpI1IIBv5it-Cx_hFVE` |
| 2022-08-25T11:20:47.165Z |`Ua8a...a2f1` | 傳圖 | 沒查到，詢問送出 :question: |
| 2022-08-25T11:21:14.876Z | `Ua8a...a2f1` | `__POSTBACK_YES__` | 收錄至 `PIq81IIBv5it-Cx_HVbc` |

- `ListArticles` 沒有回傳相同 search hash 的 article
    - 即使提供[原圖 URL](https://drive.google.com/uc?id=1oUHDvybgVP-gh3Afbo0buUT3_O43bMlQ) 好像也都沒有結果 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8f141e31c82620495463d6f48b36f4b8.png)
    - root cause: production 沒開 media article support，query 者需要指定 article types ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d1f483fb71c8aef348931ec05a02f32d.png)

- ID hash 不同，所以 `CreateMediaArticle` API 會建立新的 article


#### Case: [moda 預算](https://dev.cofacts.tw/article/EYqC34IBv5it-Cx_MGFB)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_67f59f2ff345b8e420da7c67e0e2aa7e.png)

- 類似上面的狀況，不知為何 `ListArticles` 沒有回傳相同 search hash 的 article

#### Cache-control of new images

- Service account 忘記開 update 權限，導致所有新圖的 cache-control 都沒有設進去⋯⋯
- 已經更新權限 + migrate 現有圖片的 cache-control

### Migration status

- Script: https://colab.research.google.com/drive/1EmCgNtPVr_U3PZ-HDSn1OzjlPRVC0jqh
- Files stylesheet: https://docs.google.com/spreadsheets/d/1nlDVGSl1IYazbQSna1ObZtYfpABxmD96vHJQXaiXekI/edit?usp=sharing
    - 126,535 files
- Media Entry stylesheet: https://docs.google.com/spreadsheets/d/14e-cYpgvvGHGXf3KK4aatPjZvBUw-X81PAVzxSXAXTw/edit#gid=259272385
    - 8909 files with occurrence >= 2
    - 超過 3, 4, 5, 6 次的分別為 4276, 2855, 2262, 1858
- TODO
    > 關於把之前蒐集到的圖片放上去，我在想要不要直接 deploy 到 production 耶
    > 畢竟現在 production 上已經有人在傳圖了，有些圖其實是直接有重複的。
    > 直接 deploy 上去就可以省去從 staging --> production 的圖片們 merge 的這一步 merge 的部分，如果有人上傳舊圖，也會直接使用舊圖 [name=mrorz]
    > 
    - [x] Upload images to GCS
    - [ ] Generate batch script from media entry stylesheet
    - [ ] Run batch on staging as test
    - [ ] Run batch on production
    - [ ] Choose a day to show images in website

### Transcript

> 我覺得接下來的重點應該是讓編輯可以共編圖上的文字，像國家寶藏那樣
能共編文字之後，「相似的訊息」就能運作，也能夠用文字搜尋，即使 hash 不同，在回了一篇之後，也能快速套用回應。
作業系統有 OCR 功能編輯（如新版 iPad）的，也能輕鬆把文字放進去
> [name=mrorz]

> 接續「讓編輯可以共編圖上的文字」的話題
> 我寫了共編圖中文字 / 文字辨識 / 逐字稿的 design doc
> https://g0v.hackmd.io/OhGIQzoxR5eF6audQuS_FQ
> 裡面包含：
> - UI design Figma
> - UX flow 試玩（建議用手機玩玩看，看建立逐字稿流程是否直覺）
>     - 有考慮到「在儲存逐字稿時，如果有人搶先儲存逐字稿，那要怎麼處理衝突」的流程！
> - 資料庫欄位
> - API 設計
> 
> 請大家看看～～提出一些需要討論的點
> 共編「圖上文字」英文這裡用 transcript，中文目前有「圖中文字」、「文字辨識」、「逐字稿」等命名，可以想一個好名字
> 之後支援影片跟聲音的時候，如何支援很長的影片與聲音共編逐字稿（hackmd 裡面有塊紅色背景的區塊在討論此議題）

## 小聚＆十週年黑客松
> https://10th.g0v.tw/
> 9/15 截止徵件
> - 開放工作坊（30min）for 圖片查核
> - ABC 體操表演 by bil

9/25? https://thehapp.com/space/267 ?
1:30pm~5:30pm

## 二次詐騙貼文

- 0 reply requests
    - 2zeg7nknvppyd
	- 1c6jl5fq7plsw
	- 20j7tov2pwi6u
	- yjhr09b8h0mo
	- 3q1zucbbrobxa
	- 2f7ujanyqo1vr
	- 312jz2odp1xwd
	- 2o1ycthbdatar
	- n6cr2rlwndvz
	- 3ps8oul9x114a
	- 1pe9fq93m6oez
	- 2dlvj7t517ogr
	- zfykyif3b2sq
	- l1k7sptlglo3
	- 2mqe16ahhtrg
- 回應價值低
- 但會被 google 搜尋到⋯⋯
- 用一個 Reply 處理？
  - OK

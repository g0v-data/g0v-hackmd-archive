---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20231004 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, orz, nonumpa, 4000, cai
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
- `GetYdoc` fix https://github.com/cofacts/rumors-api/releases/tag/release%2F20230929

#### :robot_face: rumors-line-bot

- Group bug https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20230928

### :rocket: Staging

#### :electric_plug: API

- https://github.com/cofacts/rumors-api/pull/318

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 1:1 可送出全新影片、圖片、聲音
- [x] 點到網站，可以看到 AI 逐字稿自動填入


#### :globe_with_meridians: Site
##### Testing checklist
> 主攻[上週未竟項目](https://g0v.hackmd.io/Eu2AOPXnTzixK6qt7t4ikg#%E6%9C%AA%E7%AB%9F%E9%A0%85%E7%9B%AE)
> - 有歷史紀錄
> - 時間、作者資訊均有

http://dev.cofacts.tw/

登入自有帳號後檢測：
- [x] AI 逐字稿填入後，edit history 有呈現送出訊息的時間，作者為「AI Transcript」

##### ⛔️ Release Blockers
##### 未竟項目

- 有影片 （7/1 不禮讓行人）送入 chatbot always 會 busy

### :eye: Under review

#### :electric_plug: API

- Upgrade jest https://github.com/cofacts/rumors-api/pull/319
  - Fix 上週提到的 [lib0 問題](https://g0v.hackmd.io/Eu2AOPXnTzixK6qt7t4ikg#AI-API-%E5%AF%AB%E5%85%A5-ydoc)
- https://github.com/cofacts/rumors-api/pull/318

## CCPRIP

### [Comm] Transcript

> https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ
> [name=nonumpa]

計畫：補 test、弄 monorepo
網站補提示

#### AI: API 寫入 ydoc

> Design doc https://g0v.hackmd.io/wkx286lmTDaFUpgRhnUawQ#CreateMediaArticle

##### Migration plan
Summary from https://g0v.hackmd.io/wkx286lmTDaFUpgRhnUawQ#Migration-of-exisitng-media-articles :
1. Use open data to put articles to transcribe in [Google sheet](https://docs.google.com/spreadsheets/d/1ZNNySVATxjGp-L4WJh9MgqzGnEVXaH7QLOKuCoHZ6BU/edit#gid=0)
2. Run Whisper / OCR using [Colab](https://colab.research.google.com/drive/1oorZ1B1XTDV6Ngw0dW4YkaLbumDw8W7p#scrollTo=EJ9mSDWQF6Cd) and store back to Google sheet
3. Call [`writeAITranscript(articleId, text)`](https://github.com/cofacts/rumors-api/pull/318/files#diff-f4f56dad07f0ad69f9bf3e8d7055aa437be72efb27d5404c35d4257982da43c2R176) for all transcribed items

Note: No `airesponses` doc is created in this process

##### Execution
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6ce3ac19dc296f5b2d1988c3cb842f70.png)

Estimated 20,000 articles to transcribe.

0. Sort 20,000 articles to transcribe by creation date, latest first
1. Process first 1,000 articles, calculate time needed
2. Plan for the rest 19,000 migration

#### Other issues

> OCR的偵測敏感度（？）可以調比較低嗎
傳疾管署那種宣導圖卡，OCR都會把沒有文字的變成文字 
> [name=cai]

### [Comm] Article group / cooccurrence implementation

> 我在思考 [article group 處理多則訊息](https://g0v.hackmd.io/@cofacts/rd/%2Ff_Ze19PhQuqx_fzOAOkohQ) 時，跟現有 chatbot context 裡面的某些欄位（尤其是 `selectedArticleId` ）會有衝突的問題
> 正在思考「先整理 chatbot context 把東西移到 postback action」的方向時，發現現在把 `selectedArticleId` 記在 context 會有這個 bug:
> https://github.com/cofacts/rumors-line-bot/issues/327
` 我想要先把 `selectedArticleId`  移動到 postback action 來修好這個 bug
> 再來逐步移除不需要的 context
> 最後再回頭思考 article group 與 chatbot context 的問題，說不定清完之後發現就沒有那些不 compatible 的 context field 了
> [name=mrorz]

> [postback.data](https://developers.line.biz/en/reference/messaging-api/#postback-action)有長度限制
>[name=nonumpa]


### [Infra] Migrate to Cloudrun

> https://g0v.hackmd.io/BRsJOevWSbyUMBSZEVVWrA#Phase-1-rumors-site-amp-rumors-line-bot-%E4%B8%8A-Google-cloud-run
> 

#### Website

> Previous TODO: https://g0v.hackmd.io/ulv1SGtBRWmhxnE9Lpv9TQ?both#TODO
> 

- Github image build triggers deploy: https://github.com/cofacts/rumors-site/pull/549
- Service account:
  - `rumors-site` service account runs container, has no permission
  - `rumors-site-deploy` is used on Github actions
    - Shared across `rumors-site` and `rumors-line-bot` (see below)
    - Went through [Workload Identity Federation](https://github.com/google-github-actions/auth#setting-up-workload-identity-federation) setup
      - Authenticates to Google via [Github's token](https://github.com/google-github-actions/auth#github-token-format)
      - No need to generate and maintain JSON keys
    - It has [enough permission](https://github.com/google-github-actions/deploy-cloudrun#authorization) to create Cloud run deployments and impersonate as individual service accounts

#### Chatbot

##### Original

- Chatbot on Linode
  - Notification job in Crontab
- Redis on Linode
- MongoDB on MongoDB Atlas

##### Now (Staging only)

- Chatbot on Cloud Run as a *service*
  - Notification job on Cloud Run as a *job*
  - Automatic deploy after Github action build https://github.com/cofacts/rumors-line-bot/pull/364
  - Reuse service account `line-bot` to run the cloud run containers
    - Already used in Linode to access Dialogflow
    - Will remove its key after all line-bot is running on Cloud Run
- Redis on Redis Cloud
  - Free for now
  - Production grade: 8usd / mo for 100MB ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_117fc787e5ca76299168204adb091af3.png)

- MongoDB on MongoDB Atlas
  - Still free XD

##### TODO

- Apply to en, ja production, observe 1 month
- Apply to tw production


## Hugging Face

> Hugging Face dataset page:
https://huggingface.co/datasets/Cofacts/line-msg-fact-check-tw
> Example Colab (含有如何 join table 做一個 classifier 需要的 train data)
https://colab.research.google.com/drive/1qdE-OMJTi6ZO68J6KdzGdxNdheW4ct6T
> [name=mrorz]
> 相較多數資料集 是詳細了很多 但我覺得詳細說明還蠻不錯的
> example 的話算是蠻簡單的，可以很直接地讀進資料（不過這應該是用 HF 這套蠻常見的就是），能想到的就是有個圖輔助你要 join tables 之間的概念可以錦上添花一些
> [name=pai]

https://github.com/cofacts/opendata
- 關閉 google form
- Github 上只會把使用者導向到 HuggingFace
  - 如何生檔案的部分換寫在 `CONTRIBUTING.md`


## MozTW 服務學習

> 徵求「交大資工服務學習課程自由軟體組」的參與專案
大家好，我跟軟自協的 @frank
、前教育部自由軟體中心的 Eric Sun 及維基社群的 @s8321414
> 每學期都會去交大資工協助服務學習自由軟體組。由於今年系上想要擴大舉辦，因此想要徵求一些有興趣帶領大一同學:beginner::beginner::beginner:的坑主來加入。
有興趣提供貢獻機會，請把專案資料填寫到此份投影片：https://docs.google.com/presentation/d/1ZnbJy5_qpjOYPtkoH88v3X8IGVQ6yNVEloRipg_MVzc/edit?usp=sharing
>（參與項目不限寫 code）
我們將會在 10/13 去學校舉辦說明會，到時會將投影片提供給同學參考，我也會快速介紹一輪。會後供他們自由選擇有興趣的項目，再直接按照投影片上的資訊聯絡各專案坑主。
>（另外，系上也希望額外邀請參與者來系上演講，分享自己的開源及程式貢獻社會的經驗等（此項有演講費）。時間可安排在十一月或十二月下午或晚上，有興趣也請舉手一下。）
> [name=irvin]

- Code: Good first issue
- 闢謠

:::success
Johnson 寫
:::

## 大松籌備

報名

2023/10/15
- https://github.com/cofacts/rumors-site/issues
- https://github.com/cofacts/rumors-line-bot/issues

:::success
Johnson 報
:::

## 來信處理

- 喬治亞
- 直銷

## 回溯性投資

月底出計算的 spreadsheet
12 月底結案
需要錢包的解釋 Zoey
線上說明會 / 另外辦一個實體的

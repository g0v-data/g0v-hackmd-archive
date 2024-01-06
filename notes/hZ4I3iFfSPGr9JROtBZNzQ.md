---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20230712 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：Dennis, bil, mrorz
- 線上出席：nonumpa, cai
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :globe_with_meridians: Site

- https://github.com/cofacts/rumors-site/pull/542
- ~~https://github.com/cofacts/rumors-site/pull/543~~ Fix storybook build first

##### Testing checklist
http://dev.cofacts.tw/

- [x] Article list
- [x] Article detail
  
##### ⛔️ Release Blockers

##### 未竟項目

## 小聚檢討

- 小松果 https://g0v.hackmd.io/DACiWe7XQnS4fo7v0OX4pg
- 人少的時候有良好的討論氣氛 [name=bil]
- 有安全感（15 人內）、記得住人，就會談話 [name=bil]
  - 太多的話會覺得談話不是自己的責任
- 拍好的影片素材放在 Cofacts photos
- 金豆咖啡老闆娘很善良 [name=bil]
  - 三樓 somehow 滿好找的 [name=bil]
  - 有貼導引在 1F 的門，2F 沒貼
- 這次沒有人發問，提早 10min 結束 [name=mrorz]
  - 這次都是協作者，比較少不做事來發問的人 [name=bil]

## CCPRIP

### [Comm layer] 逐字稿

> https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ
> [name=nonumpa]

#### History
> [name=nonumpa]

- 遇到 y.js 問題還在看。用到 crypto 判斷如果是 browser 切換 browser / nodejs 版本

#### API
> [name=nonumpa]

#### 逐字稿 spam

> https://cofacts.tw/article/3ikuQIkBFLWd9xY2rVZf
> https://cofacts.tw/article/mynuOYkBFLWd9xY2HE-8
> 為什麼詐騙類的逐字稿欄位會出現不是逐字稿內容？
> 代表他在 LINE 送進資料庫後，又特地登入網站輸入文字？
> [name=cai]
> LINE 沒辦法送出逐字稿
> 好怪喔，像是詐騙集團的行為
> 我覺得先檢舉起來好了
> [name=mrorz]

- 歷史紀錄做出來就會知道是誰打的 [name=nonumpa]
- 遇到先用逐字稿蓋掉？可以回溯嗎 [name=mrorz]
- 還沒做 snapshot，不確定 history 是否看得到所有的紀錄 [name=nonumpa]
- https://cofacts.tw/article/aynkP4kBFLWd9xY2clZq 同一個人又用錯 [name=mrorz]
  - 感覺像是想要讓自己的字比較上面 [name=nonumpa]
  - 可能是鉛筆讓人很想按。可能把按鈕移動到「逐字稿」下面而非較顯眼的右邊？ [name=bil]
  - 那不要放鉛筆 [name=mrorz]
  - 按鈕改成「輸入逐字稿」/「編輯逐字稿」[name=cai]
  - placeholder 說明「請輸入圖片內的文字」「請輸入影片內顯示的文字，或所聽到的逐字稿」[name=cai]
  - https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/Cofacts-LIFF-and-new-designs?type=design&node-id=4516-3020&mode=design&t=BLromckuq07EWU68-4 [name=nonumpa]
    - (i) 「請勿輸入不在影片中顯示的文字或聽到的內容」
    - (i) 「請勿輸入不在圖片中顯示的文字」

:::success
開票
:::

#### AI

- PR: https://github.com/cofacts/rumors-api/pull/309
- 圖片：呼叫 Google Vision API 的 document text detection
  - 直書跟橫書混合似乎也沒問題
  - 表格比較微妙
- Whisper prompt engineering: https://docs.google.com/spreadsheets/d/10xfkOZpGJ-9vIvoYziEkD1lZETWMbBLDT-NABdQ8H_g/edit#gid=0
  - 中文 prompt 在法文內容上會 hallucinate
  - 沒聲音時可能會重複 prompt 內容
- Whisper hallucination 解方
  - Also added to [design doc](https://g0v.hackmd.io/wkx286lmTDaFUpgRhnUawQ?both#Whisper)
  - ffmpeg silence removal (但這是用寫死的 loudness 來做) - https://community.openai.com/t/whisper-api-hallucinating-on-empty-sections/93646/5
  - 提及 whisperX 等會用 voice activity detection (VAD) 只取有人聲的前處理： https://github.com/openai/whisper/discussions/1369 ；或用 VAD 的 timestamp 來過濾 Whisper 的結果（回傳 type 為 `verbose_json` 時，會帶有 timestamp）
  - 用 prompt 指定 accent 等等：https://community.openai.com/t/how-to-avoid-hallucinations-in-whisper-transcriptions/125300/17
  - 嘗試設定一些細節參數 (`condition_on_previous_text` , whisper API 調不到) 與計算 chunk size https://github.com/openai/whisper/discussions/679
    - 也有人提到一個 VAD 實作 silero vad model，且有 nodeJS API：https://www.vad.ricky0123.com/docs/node/

---

- 想要謠言兩倍速 [name=bil]
- 但打逐字稿時也會想要 0.5 倍速，瀏覽器也可以調 [name=mrorz]
- 瀏覽器會記得上一次的設定，有點煩，沒關係我自己調 [name=bil]


## 招募開發人員

- Article group / 相關圖文功能 https://g0v.hackmd.io/@cofacts/rd/%2Ff_Ze19PhQuqx_fzOAOkohQ
  - scope 相對明確
  - 緊急（希望選前可以有）、重要、且已經設計完成（Figma、API 一應俱全）
  - 會動到比較 fundamental 的訊息處理機制，加上 typescript 保護比較好
- [OP layer] API management https://g0v.hackmd.io/@cofacts/rd/%2Fj27XFAQ0R0Cuqi2jDLJuWw
  - 想要 focus 在網站 https://g0v.hackmd.io/LxNqtaRhQbqkSFMsLShAiQ?view#Op-layer-API-management
  - 但會跟網站改寫有點重疊
- 網站改寫 https://g0v.hackmd.io/@cofacts/rd/%2F%40cofacts%2FHJ_O1Xhhs
  - 目標
    - Tailwind CSS (efficient on server render, fast development)
    - React server-side components (enables API protection) instead of Apollo-client
  - 路徑
    - 將 Material UI component 用 Tailwind CSS 改寫
      - Installation of TailwindCSS is blocked by PostCSS 8 -- introduced in ==Next.12==
    - 所以要先升級 Next.JS
    - 等 [server action](https://nextjs.org/docs/app/building-your-application/data-fetching/server-actions) (mutation solution) stable 後，把 Apollo-client 換掉，改成 server side component + server action
- [Infra layer] API 改寫 Typescript, monorepo
  - Mentioned in https://g0v.hackmd.io/BRsJOevWSbyUMBSZEVVWrA#Phase-2-move-API-sub-services-into-Cloud-Run
  - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_668e086ac3f451478078b30f8d3508bf.png)

----

不會外包的東西
- transcript: 快做完了
- AI chatbot: 理想的 AI 查核形狀在我們的腦海裡，spec 變動，不適合外包

## 檢舉處理

- 貼 FB https://cofacts.github.io/community-builder/#/editorworks?type=2&day=365&userId=j4S8C_aLDBZJEJGJ3Lomo6A8o19GrR6GUdFQCvgDYGuuvVirc&showAll=1
- 暴力 https://cofacts.tw/article/8ykRRIkBFLWd9xY2d1rV
- 血腥 https://cofacts.tw/article/RikrBYkBFLWd9xY2cBd4
- 阿拉伯行刑 https://cofacts.tw/article/DmoupYgBvEj1WkaUjfvL
- 回報詐騙？ https://cofacts.tw/reply/8Gp8UIgBvEj1WkaUOp25 https://cofacts.github.io/community-builder/#/editorworks?showAll=1&day=365&userId=52p6UIgBvEj1WkaUk53f

:::info
下週再討論
:::

## 台南新營小聚

- 曬書店 / 市民學堂 11/12
- 過往大多是講座，沒有看過有桌子的活動 [name=bil]
  - 還是有桌子跟白板 https://www.facebook.com/2booksite/posts/pfbid0hCVXNzFm8TN8Hmzvr8VdAFcRaytkomHakzjwYJCRNrNfjsuk3UgLmD7ZXa4nEuBMl
  - 桌子跟新芽、青平台一樣
  - 照片裡有 15 人，都有桌子
- 會不會辦講座比較好？ [name=bil]
- 小聚比較習慣，只是小聚會怕沒有人來

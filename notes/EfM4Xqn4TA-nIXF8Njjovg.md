---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20230719 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis: bil, dennis, mrorz
- 線上出席：nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site
https://github.com/cofacts/rumors-site/releases/tag/release%2F20230719

## CCPRIP

### [Comm layer] 逐字稿

> https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ
> [name=nonumpa]

#### History
> [name=nonumpa]

- 目前只能看到新增的紀錄，還在看為什麼刪除的紀錄無法顯示，會顯示每一行是誰新增的
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c767816e3dcdb37f90f844dc20fa203e.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c4d81820323d97415d322da91a4c7086.png)

- 比較目前預設跟上一版比，參考 hackmd，未來也可以做成選擇兩版本做比較
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7937ddc85dfb0a24586e56d0ed471bdc.png)

:::info
紀錄 userid & username
:::


#### API
> [name=nonumpa]

#### 逐字稿 spam
票：https://github.com/cofacts/rumors-site/issues/544
- 過去亂打逐字稿的兩個案例 [A](https://cofacts.github.io/community-builder/#/editorworks?type=2&day=365&userId=j4S8C_ziPcE8xmmAQdmxX8ZvRh3-lFQoJBUsODQGSbmpvs-CE&showAll=1), [B](https://cofacts.github.io/community-builder/#/editorworks?showAll=1&day=365&userId=j4S8C_nuxUjWLx2vP4NdCUo8qhyJCgmzq6fLriwt38GOxJq_g)，看起來都是正常使用 [name=mrorz]
  - 沒有短時間大量貼
  - 看起來是自然的不會用

#### AI
- 尚無進度 [name=mrorz]

## 招募人員

### Article group / 相關圖文功能
https://g0v.hackmd.io/@cofacts/rd/%2Ff_Ze19PhQuqx_fzOAOkohQ

> LINE 上的網傳訊息常常以文字搭配圖片或影片的方式傳播。有時候這兩個材料各自沒有問題，但搭在一起就是錯的，
> 為解決 Cofacts 真的假的無法紀錄「搭配」的問題，我們希望徵求 Node.JS 工程師完成我們所設計的變更。
> 
> 專案中希望進行的變更包含：
> - 在現有 ElasticSearch 資料庫新增資料表
> - 新資料表的 CRUD API（含 unit test）
> - 改寫 chatbot server 處理訊息的機制，使其能處理「一起傳送」的訊息。（此部分改寫建議以 Typescript 為之）
> - 修改網頁來顯示「一起傳送」的訊息。
>
> 技術細節、UX 請見 Design doc：https://g0v.hackmd.io/@cofacts/rd/%2Ff_Ze19PhQuqx_fzOAOkohQ
> 
> 專案總酬勞：8W~10W
> 專案完成時間 2023 年 10 月底以前。
> 變更可以分段，如：資料表與 CRUD API、Chatbot 處理訊息的機制改寫、網站更新等，分段給予酬勞。
> 需線上或實體出席週三晚間 8pm 的開發者會議 sync 進度

- Recruiting priorities
  - 之前接案過的人
  - Cofacts repo 貢獻者

### Cofacts design system on Figma
- 目前 Figma: https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/Cofacts-LIFF-and-new-designs?type=design&node-id=0-1&mode=design&t=pGf5toQABSrAKKIa-0
- 基本字體放大到 16px
  - 重新建立 font 級距、搭配的 line height
  - 調整 padding、框線區塊等
  - 未來會使用 TailwindCSS 改寫網站，可參考其值 https://tailwindcss.com/docs/padding
- 以 Auto layout、components 排版四大功能頁面；包含 mobile & desktop
  - latest replies
  - Dubious messages
  - Article detail
  - Reply detail 
- 排版支援長寬比不一的圖片與影片
- Site navigation 調整（[例](https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/Cofacts-LIFF-and-new-designs?type=design&node-id=5209-544&mode=design&t=pGf5toQABSrAKKIa-4)）
  - 如：登入、footer 收進 hamburger
  - 調整順序：最新回應、可疑訊息、請支援協作
- 需線上或實體出席週三晚間 8pm 的開發者會議 sync 進度

### Impact report
TBA

## 檢舉處理

- 貼 ~~FB~~ https://cofacts.github.io/community-builder/#/editorworks?type=2&day=365&userId=j4S8C_aLDBZJEJGJ3Lomo6A8o19GrR6GUdFQCvgDYGuuvVirc&showAll=1
  - 複製貼上 youtube。可能是想備份 comment。沒有回報過 LINE 轉傳訊息。 [name=bil]
  - 問協作者社群。偏向：先移除訊息。若累犯則考慮 block。如果社群覺得直接封鎖，就封鎖 XD
- 暴力 https://cofacts.tw/article/8ykRRIkBFLWd9xY2d1rV
  - 只有一個 LINE 使用者問
  - 血腥 + 人臉清楚，因此移除 [name=mrorz]
- 血腥 https://cofacts.tw/article/RikrBYkBFLWd9xY2cBd4
  - 熱門，回掉就好 [name=bil]
  - 雖然確實殘忍，但不會從影片 identify 這個人是誰；也有很多人查，未來可能還會再被查，因此保留。 [name=mrorz]
- 阿拉伯行刑 https://cofacts.tw/article/DmoupYgBvEj1WkaUjfvL
  - 真假不明、無法 identify 到人、很多人查（刪掉也會再被送進來）。保留。[name=mrorz]
- 回報詐騙？ https://cofacts.tw/reply/8Gp8UIgBvEj1WkaUOp25 https://cofacts.github.io/community-builder/#/editorworks?showAll=1&day=365&userId=52p6UIgBvEj1WkaUk53f
  - 刪除單一篇。為自己的 LINE 帳號打廣告。
- 色情
  - 沒人傳的就下架
  - 有人傳的另外處理

## 台南新營小聚
- 場勘：曬書店×新營市民學堂
- 距離台南約半小時到一小時。

## 大松
記得報名 

https://g0v-jothon.kktix.cc/events/g0v-hackath57n




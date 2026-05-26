---
tags: cofacts
---

# 20260526 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：mrorz, nonumpa, bil
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 上週待辦

### GCE Migration
- [ ] 跑幾週看穩定度，決定是否要再把 tw site 也搬進 GCE
- [ ] 跑幾個月看實際用到的運算量，決定 GCP committed use discount 怎麼買比較划算

### 主機維運
- [ ] （高優先）清除 Swap：在離峰時段執行 `swapoff -a && swapon -a`，確認 Swap 能正常回收。若無法清除，需排查是否有 memory leak。
- [ ] （中優先）site-tw 記憶體：容器持續在 1 GB 邊緣，建議評估是否需調高 Cloud Run memory limit 或優化 SSR 記憶體用量。
- [ ] （持續追蹤）Cloudflare One token 導入：作為防火牆誤擋的根本解法，取代 Bot Fight Mode 作為 API 存取控制。

### Kaggle
- [ ] 先手動在 johnson 個人帳號上傳
    - [ ] 沿用開放資料授權條款
    - [ ] 是不是能「同意條款」之後再下載
- [ ] 之後再看看自動化
- [ ] 申請 Org 帳號

## cofacts.ai

> https://github.com/orgs/cofacts/projects/12

- [cofacts/ai] MrOrz 發布了一個新的 release [release/20260522](https://github.com/cofacts/ai/releases/tag/release/20260522)
- [cofacts/ai] nonumpa 建立了一個 Pull request [[codex] Fix Langfuse score read fields](https://github.com/cofacts/ai/pull/67)
- [cofacts/ai] MrOrz 關閉了一個 Pull request [Add Langfuse env to ingress container](https://github.com/cofacts/ai/pull/66)
- MrOrz 正在處理 Youtube --> LLM https://github.com/cofacts/ai/pull/68
- MrOrz 下一個想處理：多媒體
    - Cofacts article 本身是圖片、影片、聲音
        - GCS URL --> ADK artifact (以 GCS URI 的形式) --> ADK 內建 load_artifacts tool 就會轉成 File Parts
        - 另外開張票 --> https://github.com/cofacts/ai/issues/70
    - 使用者貼截圖時傳給 LLM https://github.com/cofacts/ai/issues/39

## 小聚籌備
- [ ] 日期：6/7 (日)
- [ ] 場地：新北市青年局青職基地
- [ ] 時間：13:00 擺桌子場佈
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：
  - 推播日：5/28
  - 目標：雙北
- [ ] 記得帶：貼紙、不太環保杯 (bil)
- [ ] LINE 文案：假訊息聲稱：「微波爐斷電後一定要等10分鐘，讓微波爐裡的高壓電容慢慢放電，把殘留的高壓電全部放完。」但這是利用民眾擔心健康與安全的心理，而刻意製作半真半假容易引起恐慌的內容。06月07日(日)下午，
- [ ] VOOM 發文
- [ ] FB 發文

## 數發部網路爬蟲治理利害關係人政策溝通交流會議

- 參與者：手上有資料，會被 AI 爬取的利害關係人
    - Cofacts 也會在 URL 也算的時候抓取網頁內容
- 數發部：三階段治理
    1. 整理共識，做出範本 / 指引（會議重點）
    2. 協議沙盒
    3. 修法 
- [內容業者網路爬蟲治理受影響狀況調查表](https://docs.google.com/document/d/1pvaaqFBeYUZwl0GIXvpn64aFP0BsqGDXcFURVusNkNg/edit?tab=t.0)

## 大松

> 5/31 週日台灣零時政府第柒拾參次動手自造黑客松 | g0v Braiding our Future Hackath73n

https://g0v-jothon.kktix.cc/events/g0v-hackath73n

- bil 講
- 可以讓參與者試用 cofacts.ai

## g0v summit 擺攤檢討

![](https://g0v.hackmd.io/_uploads/Byg7enZXlMe.png)

![](https://g0v.hackmd.io/_uploads/rygAehbXxGl.png)

![](https://g0v.hackmd.io/_uploads/ryzyn-mxMg.png)

- 說明板放在影片下面，介紹完 LINE 的狀況可以直接接 cofacts.tw 網站上的資料庫 [name=mrorz]
- 有人靠攤時，使用祈使句讓參與者掃 QR code [name=mrorz]
- X 展架很專業但好大 [name=bil]
- 必備電風扇、喉糖 [name=mrorz]

## Discord

### server-alerts

- `cofacts.tw` 在 2026-05-25 19:15:00 回報為 Unhealthy，原詳細資訊如下：
  > Health Check Name: cofacts.tw
  > Health Check ID: 26c31cd565ee9448e8cff64528205cd3
  > Time : 2026-05-25 19:15:00 +0000 UTC
  > Status: Unhealthy
  > Failure reason: HTTP timeout occurred

## GitHub

- [cofacts/takedowns] nonumpa 關閉了一個 Pull request [Takedown spam user Dubaidddd JoAxTZ4BYvv2RuZLAkqI](https://github.com/cofacts/takedowns/pull/302)
- [cofacts/takedowns] cofacts-takedown[bot] 建立了一個 Pull request [Takedown spam user Dubaidddd JoAxTZ4BYvv2RuZLAkqI](https://github.com/cofacts/takedowns/pull/302)
- [cofacts/takedowns] nonumpa 關閉了一個 Pull request [Takedown spam user desiredubai zYCvSZ4BYvv2RuZL-kXq](httpss://github.com/cofacts/takedowns/pull/301)
- [cofacts/takedowns] cofacts-takedown[bot] 建立了一個 Pull request [Takedown spam user desiredubai zYCvSZ4BYvv2RuZL-kXq](httpss://github.com/cofacts/takedowns/pull/301)
- [cofacts/takedowns] nonumpa 關閉了一個 Pull request [Takedown spam user Zainia AHAHAHAHAHAHAH dIBIUJ4BYvv2RuZLrU-i](httpss://github.com/cofacts/takedowns/pull/300)
- [cofacts/takedowns] cofacts-takedown[bot] 建立了一個 Pull request [Takedown spam user Zainia AHAHAHAHAHAHAH dIBIUJ4BYvv2RuZLrU-i](httpss://github.com/cofacts/takedowns/pull/300)

## 下次開會

回到週二 8pm

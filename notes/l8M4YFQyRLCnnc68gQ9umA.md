---
tags: cofacts
---

# 20260331 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::


## 會前資訊

### 綜合討論 (General)

- **主機遷移至 Google Compute Engine (GCE)**
  - mrorz 於 3/27 晚間進行了主機遷移，將服務從 Linode 搬遷至 GCE，預計停機一小時。遷移完成後，服務恢復正常。
  - 討論中提及 GCE 的流量計費方式，以及對 AI 爬蟲可能導致帳單爆增的擔憂。
  - mrorz 考慮使用 Cloudflare 的 HTML 快取及 AI 爬蟲防禦功能，以降低費用。

- **Elasticsearch 升級**
  - Staging 環境的 Elasticsearch 已升級至 9.3 版本，預計在清明連假期間將 Production 環境也升級。

- **API Server Build 失敗**
  - mrorz 於 3/30 晚間回報新版 API server build 失敗，並由 nonumpa 協助修復。

- **服務短暫中斷**
  - 3/25 `cofacts.tw` 網站曾短暫無法連線，後來自行恢復。

### 開發相關 (Github)

- **rumors-api**
  - [New release release/20260331](https://github.com/cofacts/rumors-api/releases/tag/release/20260331)
  - [PR #383: fix: include babel.config.js in Docker build and exclude test files](https://github.com/cofacts/rumors-api/pull/383) (已合併)
  - [PR #382: Fix build](https://github.com/cofacts/rumors-api/pull/382) (已關閉)
  - [PR #381: refactor: migrate from Elasticsearch 6.8 to 9.2 and Node 18 to 24](https://github.com/cofacts/rumors-api/pull/381) (已合併)

- **rumors-db**
  - [New release release/20260328](https://github.com/cofacts/rumors-db/releases/tag/release/20260328)
  - [PR #77: Upgrade to Elasticsearch 9.2 and Node 24](https://github.com/cofacts/rumors-db/pull/77) (已合併)

- **devops**
  - [PR #1: docs: Add GCE.md with instance setup instructions](https://github.com/cofacts/devops/pull/1) (審核中)

### 系統狀況 (Server Alerts)

- 3/30: `cofacts.tw` 及 `line-bot.cofacts.tw` 服務不穩定。
- 3/27: `line-bot.cofacts.tw` 及 `api.cofacts.tw` 服務不穩定。
- 3/25: `cofacts.tw` 服務不穩定。

## :potable_water: Release pipeline

### :rocket: Production


### :rocket: Staging

Now on staging:

- ES 9.3.2
- New API that connects to ES 9.3.2


#### :robot_face: LINE bot

- [ ] 應可送出「全新訊息」
    - [ ] 問訊息來源時選擇「我自己打的」或「LINE 外面看到的」，應該會被擋下。
    - [ ] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，訊息應該還是有被送出。
    - [ ] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [ ] 可以修改理由送出。查看 article page 看理由是否有被送出。
    - [ ] 「分享到 Facebook」、「分享到 LINE」可以正常運作

- [ ] 送出「沒回應」的舊訊息，應可送出新理由
    - [ ] 跳出來源視窗後關閉，文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。
    - [ ] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，可以看到「提供更多資訊」按鈕，按下去可以再打開「理由」視窗
    - [ ] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [ ] 可以修改理由送出。查看 article page 看理由是否有被送出。

- [ ] 送出「有回應」的舊訊息，應自動回傳回應
    - [ ] 應列出訊息所有的回應
    - [ ] 選擇回應之後可以幫回應 upvote
    - [ ] 可以再次選擇 downvote
    - [ ] 選完回應之後，還可以捲回去選其他回應

- [ ] 送出跟舊訊息相似的訊息，應提供選項選擇最像的訊息
    - [ ] 按下任一訊息應該會列出回應
    - [ ] 選了一個訊息之後，還可以捲回去按其他訊息
    - [ ] 捲回去按下「這裡都沒有我要的」應該要跳出詢問來源視窗 (選項中不能有 100% 相似的，否則會找不到按鈕)

- [ ] Rich menu 測試
    - [ ] 「設定」更改後再次打開，應該會保留原本設定
    - [ ] 「查過的訊息」應該要列出之前查過的訊息

- [ ] Group chat test

#### :globe_with_meridians: Site

**未登入下檢測：**
- [ ] Article list
  - [ ] Filter works (Replied by me: known issue)
  - [ ] Sorting works
  - [ ] Can go to article page
- [ ] Replies list
  - [ ] Filter works (Replied by me: known issue)
  - [ ] Sorting works
  - [ ] Can go to article page
  - [ ] 無法 upvote / downvote replies
  - [ ] Can see vote reasons
- [ ] Hoax for you
  - [ ] Filter works
  - [ ] Sorting works
  - [ ] Can go to article page
- [ ] Article detail
  - [ ] Can see similar messages
  - [ ] Can see deleted replies
  - [ ] Cannot submit, upvote, downvote reply request
  - [ ] Cannot submit, upvote, downvote reply
  - [ ] Cannot add, remove, upvote, downvote category
- [ ] Search
  - [ ] Can use global search to perform search
  - [ ] Can use textarea in header to perform searches
  - [ ] Can list searched articles
    - [ ] Filter works
    - [ ] Sorting works
    - [ ] Can go to article page
  - [ ] Can list searched replies
    - [ ] Can go to reply page

**登入自有帳號後檢測：**
- [ ] Replies search page
  - [ ] can upvote / downvote replies
- [ ] Replies list
  - [ ] can upvote / downvote replies
- [ ] Article detail
  - [ ] Can submit, upvote, downvote reply request
  - [ ] Can submit, remove own reply
  - [ ] Can upvote, downvote other's article reply
  - [ ] Can add, remove, upvote, downvote category
- [ ] Can logout


## Cofacts.ai 開發

https://github.com/orgs/cofacts/projects/12

### Elasticsearch 升級


Reindex time spend = 2hr
- Start time: 2026年 3月31日 星期二 00時52分36秒 CST
- Article 搞定：大概在 01:19 (30min 內)
- Reindex 期間 Load 會飆到 > 15，RAM 會用掉 24GB + 8GB buffer ~= 32 GB
- Process time: 2hr (7437 秒)


目前進度與現狀：


1. Production (GCE: 9209)：
   * ES v9 已經就緒。
   * 資料搬遷 (Reindex) 完成。
   * GCS Snapshot Repository 註冊並通過驗證。
   * 完整備份 (Snapshot) 已建立成功。


2. Staging (Vultr: 62222)：
   * ES v9 已經就緒。
   * 已成功從 GCS 完整恢復資料。
   * 驗證成功：Staging API 已成功透過別名讀取 ES v9 的資料。

---

下一個階段：正式切換 (Final Cutover & Phase 4)


既然 Staging 的驗證已經完美通關，我們準備好要進行 Production 的正式切換 了。


Production 切換計畫：
1. 停止 Production 的 v6 舊服務（db）。
2. 修改 Production 的 docker-compose.yml：
   * 將 db 改為 v9 鏡像（或是將原本的 elasticsearch-v9 改為 db 並設回正確的 port）。
   * 移除 elasticsearch-v9 臨時服務。
   * 將 api 的 ELASTICSEARCH_URL 從 http://db:9200 指向新 db。
3. 啟動 Production 服務。

### Hybrid search infrastructure

[針對 Cofacts 多模態查核資料庫之 Gemini Embedding 2 與 Elasticsearch 9 混合搜尋架構評估報告](https://docs.google.com/document/d/1sZ4jOsrZPvbJv4QjlMxgbqFsh_pTZNBRs-NbG-HU0rM/edit?pli=1&tab=t.tmt65uvfpaek#heading=h.50am5vq07luy)




## 小聚籌備
- [ ] VOOM 發文
- [ ] FB 發文
- [ ] 記得帶：貼紙、不太環保杯 (bil)

---
tags: cofacts
---

# 20260331 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, lahna, mrorz, nonumpa
- 線上出席：Alfred
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

Cofacts production on GCE
https://github.com/cofacts/devops/blob/main/GCE.md


### :rocket: Staging

Now on staging:

- ES 9.3.2
- New API that connects to ES 9.3.2

#### :robot_face: LINE bot

- [x] 應可送出「全新訊息」
    - [x] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，訊息應該還是有被送出。
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以修改理由送出。查看 article page 看理由是否有被送出。

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應
    - [x] 選擇回應之後可以幫回應 upvote
    - [x] 可以再次選擇 downvote
    - [x] 選完回應之後，還可以捲回去選其他回應

##### Release blocker
- Investigate staging bot - 文字也很慢，卡在 AI 生成回應
![](https://g0v.hackmd.io/_uploads/Syn72NKsZx.png =300x)

- 查詢舊的也不行
  - ![](https://g0v.hackmd.io/_uploads/BywiaNKjbg.png =300x)
  - ![](https://g0v.hackmd.io/_uploads/B1gh6VtoWx.png =300x)

:::success
Resolved: 單純是因為 staging mongodb 太久沒用所以被 suspend orz
啟動 mongodb 之後就正常了
:::


#### :globe_with_meridians: Site

https://dev.cofacts.tw

**登入狀態下檢測：**
- [x] Replies list
  - [x] Filter works
  - [x] Sorting works
  - [x] Can go to article page
  - [x] Can upvote / downvote replies
  - [x] Can see vote reasons
- [x] Article detail
  - [x] Can see similar messages
  - [x] Can see deleted replies
  - [x] Can submit, upvote, downvote reply request
  - [x] Can submit, remove own reply
  - [x] Can add, remove, upvote, downvote category
- [x] Search
  - [x] Can use global search to perform search
  - [x] Can list searched articles
    - [x] Filter works
    - [ ] ~~Sorting works~~ No such function
    - [x] Can go to article page
  - [x] Can list searched replies
    - [x] Can go to reply page

:::info
偶爾會 Service Unavailable 但好像之前就這樣
:::

Admin API
http://dev-admin-api.cofacts.tw/

## Cofacts.ai 開發

https://github.com/orgs/cofacts/projects/12

### GCE migration

> Tech design doc: https://docs.google.com/document/d/1sZ4jOsrZPvbJv4QjlMxgbqFsh_pTZNBRs-NbG-HU0rM/edit?tab=t.t599bt7kwc4o#heading=h.y3xsu1kqk04p

Cost review
![](https://g0v.hackmd.io/_uploads/BywNjXFjbx.png)

- 目前為原價，每天 USD$ 6 --> 一個月 USD$180
- 原本估算：
    - e2-highmem-4 搭配 1 年期 CUD 折扣 ~$120.00 / 月
    - 關掉 Linode （省 USD96/mo）
    - rumors-site 被 cofacts-ai 取代，直接開在 e2-highmem-4 裡面，關掉 cloudrun instances 月省 160USD/mo ![](https://g0v.hackmd.io/_uploads/H1BMpXtiZl.png)

:::info
- 用 rsync 把 production Cofacts 做個備份到本機端，然後再 delete instance [name=alfred++]
:::

### Elasticsearch 升級

> Tech design doc： https://docs.google.com/document/d/1sZ4jOsrZPvbJv4QjlMxgbqFsh_pTZNBRs-NbG-HU0rM/edit?tab=t.auumvk9ockbl

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

- 2026/04/12(日) 14:00-17:00 青職基地二樓借好了 

04/12 (日) 2pm - 5 pm 
- 誰會來呢: bil, mrorz, nonumpa, Lahna
- 辦在青職基地，已經確認借好
- [x] 食物：沒有
- [x] 場地：新北市青年局青職基地
- [ ] 時間：13:00 擺桌子場佈
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Slido 暖身
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：
  - 推播日：03/26（04/01 或是 03/24 設定）- 已經推播，目前有滿
  - 目標：雙北
- [x] KKTIX: https://cofacts.kktix.cc/events/cofactseditor52
- [ ] 記得帶：貼紙、不太環保杯 (bil)
- [x] LINE 文案：假訊息的起手式：「只要年滿 65 歲，把資費改成每月 149 元的樂齡方案，兩年合約省出 8000 多元，這些錢本來都在幫電信公司賺業績，今天就教你怎麼把它們全部省回來。」這是生成式ＡＩ做出來的假內容。動手闢謠，讓我們一起保護家人，Cofacts 真的假的 第 52 次志工查核工作坊需要你的加入，活動完全免費，（請自備電腦）04/12(日)下午，地點青職基地，最近的捷運站是捷運板橋站1號出口。連結內報名：https://cofacts.kktix.cc/events/cofactseditor52
- [ ] VOOM 發文
- [ ] FB 發文


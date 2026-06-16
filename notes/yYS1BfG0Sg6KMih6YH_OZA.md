---
tags: cofacts, 
---

# 20260616 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 上週待辦

### GCE Migration
- [ ] 跑幾週看穩定度，決定是否要再把 tw site 也搬進 GCE
    - AI 建議不要
- [x] 跑幾個月看實際用到的運算量，決定 GCP committed use discount 怎麼買比較划算
    - See "GCP Committed Use Discount（CUD）購買方案討論" below

### Kaggle
- [ ] 手動在 johnson 個人帳號上傳，並處理授權條款
- [ ] 研究自動化上傳
- [ ] 申請 Org 帳號

### url-resolver
- [ ] nonumpa 會對優化項目進行 benchmark
- [x] Johnson 會 review 已 ready 的 PR

### COSCUP
- [ ] nonumpa 準備 URL resolver 的分享內容
- [ ] yutin 準備多媒體檢索的分享內容

### AI 修正
- [ ] 支援檔案上傳
- [ ] 追蹤並修正影音訊息處理時，模型產生幻覺（腦補）或 `0:00:00` 時間戳的問題
- [ ] 為 AI writer prompt 新增長度與精簡準則
- [ ] 驗證 AI pipeline 有時會聲稱有呼叫 proofreader 但沒呼叫的問題
- [x] 為「自動 rename session 名稱」開票 --> https://github.com/cofacts/ai/issues/87

### 維運
- [x] 持續觀察 GCE server 的 Swap 用量
- [ ] 處理 `site-tw` Cloud Run 服務的記憶體高壓問題

## General

- **防火牆與 openapi.json 問題**
  - @mrorz 提到 `takedown` CI 的 `validate-api` 功能可能因為防火牆變更而失效，並已手動開放 AS 8075 (Github actions) 對 `/openapi.json` 的存取權限。
  > @nonumpa: 我發現 takedown ci 的 validate-api 好像也因為 5/4 防火牆誤擋事件的改動壞了
不確定是不是 dev-admin-api.cofacts.tw 沒處理到
  > @mrorz: 我先在 Managed rules 這裡開放 AS 8075 (Github actions 所在處) 存取 /openapi.json 囉

## Cofacts.ai & nDX progresses

### cofacts/ai

- **E2E 測試框架**
  - 新增了結合 Webwright 與 Playwright 的 E2E 測試框架，並有密集的 review 與討論。
  - [feat: initialize E2E testing framework (Webwright + Playwright)](https://github.com/cofacts/ai/pull/91)

- **對話功能改進**
  - 新增了檔案與 PDF 上傳功能。
  - [Add file/PDF attachment upload to chat](https://github.com/cofacts/ai/pull/89)
  - 修復了重新整理後工具使用標籤 (tool call badges) 會消失的問題。
  - [fix: preserve tool call badges after page refresh](https://github.com/cofacts/ai/pull/90)

- **自動為 session 命名**
  - MrOrz 開了新 issue，希望在 session 結束後，能用 LLM 自動生成有意義的標題。
  - [自動為 session 命名](https://github.com/cofacts/ai/issues/87)

- **釋出新版本**
  - [release/20260613](https://github.com/cofacts/ai/releases/tag/release/20260613)
  - [release/20260612](https://github.com/cofacts/ai/releases/tag/release/20260612)

### cofacts/url-resolver

- **效能優化**
  - 新增了在靜態抓取可以取得文章時，跳過 puppeteer 的邏輯。
  - [Skip puppeteer when a static fetch can extract the article](https://github.com/cofacts/url-resolver/pull/74)

- **依賴套件升級**
  - 升級 Node.js, puppeteer, 與 @grpc/grpc-js。
  - [chore(deps): upgrade to Node 24, puppeteer 24, and @grpc/grpc-js](https://github.com/cofacts/url-resolver/pull/73)

### cofacts/takedowns

- **處理垃圾訊息使用者**
  - [Takedown spam user Khac Dum iy1fsZ4BEY7yIwhp6ask](https://github.com/cofacts/takedowns/pull/304)


## Cofacts AI 週報 2026-06-08 ～ 06-15

---

### 一、使用量概覽

| 指標 | 數值 |
|------|------|
| Sessions | 30 |
| Traces | 35 |
| 有 LLM 費用的 traces | 33 |
| 總費用 | ~USD $3.67 |
| 平均費用（有費用的 trace） | ~USD $0.11 |
| 最高單次費用 | USD $1.58（Session `8e621519`，Jun 13，多輪長對話） |
| 活躍天數 | 5 天（6/8, 6/9, 6/11, 6/13, 6/15） |
| 活躍使用者 | 2 位 |

**流量分布**：6/13 明顯最密集（20 traces），集中在早上 5–9 點（含同一 session 多輪的測試場景）。

---

### 二、User Feedback 分析（本週 6 筆）

**評分分布：3 ↑ / 3 ↓ （50% 好評率）**

#### 正向 👍 (+1)
| 時間 | 評語 | 摘要 |
|------|------|------|
| 6/8 | ☑ 出處精準 | 引用連結正確有效 |
| 6/9 | ☑ 語氣適合 | 語氣符合事實查核文章風格 |
| 6/15 | ☑ 篇幅適中 | 輸出長度合宜 |

#### 負向 👎 (-1)
| 時間 | 評語 | 問題描述 |
|------|------|----------|
| 6/9 | 你沒繼續呼叫 | Agent 中途停止，沒有繼續執行後續 tool 呼叫 |
| 6/13 | ☑ 提供不存在的出處 | Investigator 找到的兩個 URL（科技大觀園、泛科學）實際不可開啟 |
| 6/13 | ☑ 提供不存在的出處 + Verifier 幻覺 | Verifier 被餵入 4 個無效 URL（investigator 幻覺產生），卻回報「全部支持」。且 mygopen 原本正確的 `honey.html` 變成不存在的 `honey-metal.html` |

> **⚠️ 重複出現的高優先問題：幻覺出處**
> - 同一個 session（蜂蜜主題，`fcbe502f`）連續出現兩次 -1，都是「提供不存在的出處」
> - Investigator → Verifier 的 URL 傳遞鏈：investigator 搜尋出幻覺 URL，verifier 拿到壞 URL 後依然宣稱「支持」
> - 這個問題在更早期（5/24, 5/6, 5/15）也多次出現，本週未見改善

---

### 三、本週 Prompt 迭代（本週新增：**無**，沿用 6/6-6/7 的版本）

本週 agent.py 沒有新的 prompt 修改。本週使用的 prompt 是上週 6/1–6/7 合併的改動，以下是這批改動的內容：

#### 📝 Prompt 改動回顧（6/1–6/7 合入 main，本週正式驗收中）

**1. Writer/Verifier 角色分工重構 (`02b63f3`, 6/6)**

> **背景**：之前 Writer 直接看媒體，導致職責不清。

- **改前**：Writer 可以自己處理影片相關任務
- **改後**：Writer **只**從逐字稿（transcript）工作，無法直接看媒體；Verifier 是 pipeline 中**唯一**能看影片/聽音訊的 agent。Verifier 的 claim inventory 格式也強化為「exhaustive、atomic、numbered」逐條列舉，覆蓋聲音+視覺兩個層次

**2. 強制要求影音文章走 Verifier 關卡 (`fc8ab69`, 6/6)**

> **背景**：之前如果文章已有逐字稿，可能跳過 Verifier 看媒體這個步驟。

- **改前**：「還是要叫 verifier 去看...」（偏建議）
- **改後**：「即使逐字稿看起來完整，VIDEO/AUDIO 文章**至少需要一次** verifier 實際觀看/聆聽的 pass」（強制要求）

**3. attachmentUrl 傳遞方式 (`71311b5` → `617a090`, 6/6)**

> **背景**：Writer 有時傳錯 URL 給 Verifier（傳 Cofacts 頁面 URL 而非 gs:// 媒體 URI）。

- **初版**（`71311b5`）：用大寫 VERBATIM、禁止語氣強調必須原封不動傳 `attachmentUrl`
- **修正版**（`617a090`）：改為正向說明「`get_single_cofacts_article` 回傳的是 `gs://...` URI，直接轉交就好」，移除過於強硬的措辭

**4. 編輯約束追蹤說明更新 (`b9d73d7`, 6/1)**

> **背景**：「Track editorial constraints」的說明過於抽象，模型不清楚什麼算約束。

- **改前**：`（例如「影片沒用 X 字，不要自創」、「從士兵角度論證」、「訊息沒提到 Y」）`（用原文的具體例子）
- **改後**：換成通用例子，分三類描述：(1) 避免的措辭，(2) 寫作角度/框架，(3) 語氣/長度偏好

---

### 四、本週 Bug Fix（Frontend，非 Prompt）

這週的工程重點是 **frontend 顯示 bug**，與 ADK streaming 的 functionCall ID 處理有關：

| 日期 | 修復 | 影響 |
|------|------|------|
| 6/11 | RightDrawer 串流後顯示空白 | ADK 在 partial event 用 ephemeral ID，在 complete event 用 canonical ID，前端存了 ephemeral 但 tool response 配 canonical → 永遠顯示空白 |
| 6/13 | 頁面重整後 tool call badge 消失 | history replay 時所有 event 的 partial: false，導致 functionCall parts 被過濾掉 |

---

### 五、待追蹤的問題

| 優先 | 問題 | 現象 | 觀察到的次數 |
|------|------|------|-------------|
| 🔴 高 | **Investigator 幻覺 URL → Verifier 跟著幻覺** | investigator 搜到不存在的網址，verifier 不做真實 HTTP 驗證，直接宣告支持 | 本週 2 次（同主題），歷史也有多次 |
| 🟡 中 | **Agent 中途停止不繼續** | 使用者說「你沒繼續呼叫」，可能是 writer 沒有在需要時繼續 tool 呼叫 | 本週 1 次 |
| 🟢 觀察中 | attachmentUrl gs:// 傳遞 | 上週已改 prompt，本週尚未看到影音案例的反饋 | — |

---

### 六、數量對比（近三週 user-thumbs）

| 週期 | 正評 | 負評 | 中性 | 好評率 |
|------|------|------|------|--------|
| 6/8–6/15（本週） | 3 | 3 | 0 | **50%** |
| 6/1–6/7（上週） | 2 | 5 | 1 | 29% |
| 5/25–5/31 | 4 | 5 | 0 | 44% |

好評率從上週的 29% 回升到 50%，但「提供不存在的出處」問題仍是主要拉分因素。

---

**數據都是從 Langfuse 直接撈取的，prompts 的 diff 是對應 git commit 的實際內容。** 如果要在週會上 deep dive 特定 trace，可以直接開 `https://langfuse.cofacts.tw` 用 trace ID 查看完整的 observation tree。




## GCP Committed Use Discount（CUD）購買方案討論

### 背景

Google Cloud 提供 **Compute Flexible CUD**，一張 commitment 可同時涵蓋 Compute Engine、Cloud Run、GKE，以 Billing Account 為單位，不鎖 project 或 region。

### 目前費用基準（2026-05 實際）

| 項目 | 月費 | CUD 可涵蓋 |
|---|---|---|
| GCE VM（e2-highmem-4 RAM + CPU）| $155 | ✅ |
| Cloud Run CPU（生產 + staging）| $60 | ✅ |
| GCE Carrier Peering egress | $51 | ❌ |
| 其他（disk、Cloud SQL…）| ~$50 | ❌ |
| **可被 CUD 涵蓋的合計** | **~$188/mo（$0.26/hr）** | |

折扣率：GCE E2 為 3 年 46% / 1 年 28%；Cloud Run request-based 為 17%（1 年與 3 年相同）。

Carrier Peering egress 的 cost saving 見下一段。

### 費用走勢假設

cofacts.ai 預計一年內取代 rumors-site（Cloud Run 生產站），屆時 eligible spend 降至約 **$0.22/hr**（GCE $155 + Cloud Run zh + staging $22）。

### 方案比較（3 年總費用，假設轉移發生於第 12 個月）

| 方案 | 年 1/月 | 年 2-3/月 | **3 年總計** | 比 Google 推薦省 |
|---|---|---|---|---|
| 不買 CUD | $190 | $161 | $6,132 | — |
| Google 推薦：$0.16/hr 全 3 年 | $117 | $117（浪費 $18）| $4,205 | — |
| $0.14/hr 3 年 only | $126 | $102 | $3,964 | +$241 |
| **$0.14/hr 3 年 + $0.02/hr 1 年** ✦ | **$121** | **$102** | **$3,908** | **+$297** |
| $0.13/hr 3 年 + $0.03/hr 1 年 | $123 | $101 | $3,910 | +$295 |

![](https://g0v.hackmd.io/_uploads/SyIwUzvZze.png)

![](https://g0v.hackmd.io/_uploads/rJg-dIGD-Ml.png)


✦ **建議方案**

### 建議方案說明：$0.14/hr 3 年 + $0.02/hr 1 年

- **$0.14/hr 3 年**：涵蓋轉移後的穩定基準用量（GCE 長期存在）
- **$0.02/hr 1 年**：涵蓋目前 Cloud Run 生產站的暫時性用量，到期後不續約
- Cloud Run request-based 的 CUD 折扣 1 年與 3 年相同（均為 17%），無需為即將縮減的用量 commit 3 年
- 即使 cofacts.ai 上線延遲，GCE VM 單獨即可吸收 $0.14/hr commitment，無浪費風險

### 待決事項

- [ ] 確認 cofacts.ai 取代 rumors-site 的預計時程
- [ ] 決定是否採用建議方案，由有 Billing Account 權限者於 GCP Console 購買

## Idea: Cofacts knowledge base

> Reference: Open knowledge format: https://gemini.google.com/share/841c65c8736a (based on LLM wiki)

"Knowledge" we have:
- cofacts.tw/hack: 各種 notes、規則 etc
- https://g0v.hackmd.io/@cofacts/meetings
- https://g0v.hackmd.io/@cofacts/rd/
- Design doc https://docs.google.com/document/d/1sZ4jOsrZPvbJv4QjlMxgbqFsh_pTZNBRs-NbG-HU0rM/edit?pli=1&tab=t.t599bt7kwc4o

解決痛點：
- 很難找過去東西：會議記錄、design doc 等等
    - 這樣記者採訪前，也能用自己的 claude code 直接彙整最近在幹嘛，超酷
- 很難寫新東西：
    - 寫在哪
    - hackmd mcp 只能一次編輯整個檔案，大檔無法直接編輯

問題：
- visibility：沒辦法分權限
    - 但本來上面這些東西就全公開了
    - 還是可以把 private 東西分到別的 private repo，如 devops 
- 沒辦法像 hackmd 那樣開會時同時編輯
    - hackmd 開會時還是可以用，只是開完會之後移動到 github，hackmd 只放當下的 meeting
- Github 介面比 hackmd / hackfoldr 可怕 (?)
    - 找個不錯的 Github pages / llm wiki 模板？

## Block SEO crawler for egress cost saving

![](https://g0v.hackmd.io/_uploads/H1zvJ2pZfl.png)

**Cloudflare 設定更新：擋商業 SEO 爬蟲 + en/ja/zh 網站快取（6/10 晚間生效）**

*改了什麼*
1. *WAF 新規則「Block 商業爬蟲」*：封鎖 DotBot (Moz)、SemrushBot、AhrefsBot、DataForSeoBot、Barkrowler、MJ12bot。這些是純商業 SEO 工具的爬蟲，每月吃掉 ~330 GB origin 流量（快取命中率 ~0%），但對 Google/Bing 搜尋排名沒有任何貢獻。
2. *新 Cache Rule「en/ja/zh SSR HTML」*：en/ja/zh.cofacts.tw 的頁面改由 Cloudflare 快取 60 秒。之前這些 SSR 頁面 100% 直接打到主機（zh 還因為舊規則的條件寫法完全沒被快取到）。

*為什麼*
GCE 的 egress 費用 $51/月，單位流量成本是 Cloud Run 的 6 倍；分析後發現大宗是 SEO 爬蟲狂抓 + HTML 完全沒快取。

*生效 36 小時的成效*（前後各 34 小時對照，打到 origin 的流量）
• en.cofacts.tw：9.5 GB → 4.4 GB（*-54%*）
• ja.cofacts.tw：9.2 GB → 2.8 GB（*-70%*）
• zh.cofacts.tw：7.5 GB → 2.2 GB（*-71%*，快取命中率 12% → 43%）
• cofacts.tw：18.5 GB → 10.8 GB（*-42%*，純粹來自擋爬蟲）
• 六隻爬蟲流量 26 GB → 36 MB（全是 403），36 小時共攔 13,823 個請求
• 估計省 *GCE egress $13–15/月 + Cloud Run $4–5/月*，正式驗收看 7 月帳單

*對使用者的影響*
• 一般使用者與 Google/Bing/搜尋排名：無影響
• en/ja/zh 頁面內容最多延遲 60 秒更新（送出回應後重整頁面可能要等一分鐘才看到）
• 被站方封鎖的使用者看到的頁面不受快取影響（有特別排除）

*後續*
• ClaudeBot（Anthropic AI 爬蟲，95 GB/月）要不要擋還在評估
• 評估把同樣的快取模式套到 cofacts.tw 的 /article/* （Googlebot 每月 91 GB 還在直打 Cloud Run）

詳細分析與規則設定記錄在 devops repo 的 Cloudflare.md（commit 7ba2439）

---

# Cofacts Production report 2026-06-08 ～ 2026-06-15）


### 一、GCE 主機（cofacts-prod）每日指標

| 日期  | CPU (min\|avg\|p95\|max)             | Mem (min\|avg\|p95\|max)             | Swap (min\|avg\|p95\|max)            |
| ----- | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| 06/08 | 17.5% \| **50.4%** \| 67.1% \| 77.6% | 62.0% \| 67.4% \| 71.1% \| **88.6%** | 47.5% \| **48.5%** \| 49.9% \| 50.1% |
| 06/09 | 13.2% \| 26.9% \| 41.8% \| 50.7%     | 61.8% \| 66.5% \| 68.5% \| 83.6%     | 44.0% \| 46.5% \| 49.9% \| 50.0%     |
| 06/10 | 8.7% \| 23.0% \| 41.4% \| 45.1%      | 61.5% \| 65.3% \| 67.8% \| 68.9%     | 44.9% \| 48.1% \| 49.4% \| 52.6%     |
| 06/11 | 10.0% \| 18.5% \| 25.3% \| 31.3%     | 61.3% \| 64.8% \| 66.9% \| 68.2%     | 42.3% \| 44.5% \| 46.8% \| 47.8%     |
| 06/12 | 9.7% \| 21.5% \| 33.8% \| 44.8%      | 61.6% \| 65.1% \| 67.6% \| 68.7%     | 43.7% \| 45.5% \| 47.1% \| 47.5%     |
| 06/13 | 8.5% \| 22.4% \| 33.0% \| 43.7%      | 61.6% \| 64.7% \| 67.0% \| 67.9%     | 28.8% \| 35.7% \| 46.3% \| 46.8%     |
| 06/14 | 12.7% \| 24.1% \| 33.3% \| 35.9%     | 61.7% \| 64.7% \| 66.9% \| 69.2%     | 35.0% \| **35.8%** \| 36.8% \| 38.5% |
| 06/15 | 10.3% \| 23.6% \| 34.5% \| 41.8%     | 61.6% \| 64.2% \| 66.5% \| 68.5%     | 34.8% \| **35.6%** \| 37.1% \| 37.1% |

**目前即時狀態（截至報告時）：**
- 負載：1.39 / 1.66 / 1.75（穩定）
- RAM：20 GiB / 31 GiB（65%）
- Swap：1.4 GiB / 4.0 GiB（35%）
- 磁碟：46 G / 67 G（68%）

---

### 二、GCE 行程資源排行

#### 記憶體（RSS）

| 行程                            | 日常平均         | 週最高峰             | 穩定度（Stddev）    | 備註                           |
| ------------------------------- | ---------------- | -------------------- | ------------------- | ------------------------------ |
| **Elasticsearch**               | 19,068–19,193 MB | 19,530 MB            | 75–193 MB（穩定）   | 最大記憶體消耗者，整週平穩     |
| **node server.js** (API server) | 286–545 MB       | **1,994 MB** (06/08) | std 115–161         | 06/08 有明顯高峰，之後逐漸下降 |
| **node build/index.js**         | 145–154 MB       | 669 MB               | std 4–7（非常穩定） | 正常                           |
| **node index.js**               | 62–76 MB         | **528 MB** (06/11)   | std 5–18            | 06/11 有短暫爆衝               |
| **Puppeteer chrome renderers**  | 140–169 MB/實例  | 517 MB               | std ≈ 0（短暫）     | 截圖任務產生的暫時性 process   |

#### CPU（累計 ms/分鐘，越高代表越吃 CPU）

| 行程                            | 日常平均  | 週最高峰日        | 觀察                           |
| ------------------------------- | --------- | ----------------- | ------------------------------ |
| **Elasticsearch**               | 290k–900k | 899k（06/08）     | 06/08 後大幅下降，趨勢明顯改善 |
| **node server.js**              | 161k–514k | 514k（06/08）     | 與 Elasticsearch 走勢同步      |
| **node build/index.js**         | 132k–317k | 317k（06/08）     | 同上                           |
| **node server.js（另一個）**    | 1.5k–123k | 143k（06/14）     | 06/14 升高，需持續觀察         |
| **cloudflared**                 | 24k–74k   | 74k（06/08）      | 與整體流量正相關               |
| **python main.py** (cofacts-ai) | 2.4k–3.2k | **9.5k（06/13）** | 06/13 有異常爆衝，但孤立事件   |

---

### 三、Cloud Run 服務

所有 11 個服務狀態正常（✔）。

#### CPU 使用量（vCPU，p50 為正常值、p95/p99 為突發尖峰）

| 服務                | p50（正常） | p95（尖峰） | p99（最差）   | 觀察                         |
| ------------------- | ----------- | ----------- | ------------- | ---------------------------- |
| **site-tw**         | 0.05–0.31   | 0.59–0.92   | 0.78–**1.01** | 06/08 壓力最大，之後明顯下降 |
| **cofacts-ai**      | ~0.015      | 0.14–0.27   | 最高 0.44     | 低消耗，穩定                 |
| **site-staging-\*** | < 0.04      | < 0.17      | < 0.48        | 正常                         |
| **line-bot-\***     | < 0.009     | < 0.24      | < 0.35        | 正常                         |

#### 記憶體使用量（GiB，p50 為正常值）

| 服務                | p50            | p99           | 觀察                     |
| ------------------- | -------------- | ------------- | ------------------------ |
| **site-tw**         | 0.76–0.81 GiB  | ~1.01 GiB     | 長期貼近限額上緣，需注意 |
| **site-staging-ja** | 0.83–0.89 GiB  | ~1.01 GiB     | 偏高（staging 服務）     |
| **site-staging-tw** | 0.76–0.81 GiB  | 0.93–1.01 GiB | 同上                     |
| **line-bot-\***     | ~0.39–0.41 GiB | < 0.50 GiB    | 正常                     |
| **cofacts-ai**      | ~0.045 GiB     | < 0.10 GiB    | 非常低                   |

#### Cloud Run 對外流量（site-tw）

| 日期  | 對外流量    |
| ----- | ----------- |
| 06/08 | **12.1 GB** |
| 06/09 | 8.2 GB      |
| 06/10 | 7.3 GB      |
| 06/11 | 5.6 GB      |
| 06/12 | 6.3 GB      |
| 06/13 | 6.1 GB      |
| 06/14 | 4.0 GB      |
| 06/15 | **3.1 GB**  |

---

### 四、重點分析與建議

1. **WAF 封鎖 SEO 爬蟲效果顯著**：`site-tw` 對外流量從週初 12.1 GB 降至 06/15 的 3.1 GB，**一週減少約 74%**。GCE CPU 平均從 06/08 的 50.4% 大幅下降至 06/09 後的 18–24%，顯示爬蟲封鎖及 cache rule 對主機的壓力釋放效果明顯。

2. **Swap 使用下降**：由週初的 ~48% 降至 06/13 後穩定在 ~35%，與流量下降及 cofacts-ai 記憶體優化（改為 python main.py）同步改善。

3. **site-tw 記憶體貼近上限**：Cloud Run `site-tw` 的 p99 記憶體長期接近 1.01 GiB，幾乎貼滿配置。目前未造成問題，但若流量回升需留意是否觸碰 OOM。

4. **python main.py CPU 06/13 異常**：cofacts-ai 於 06/13 出現 CPU 爆衝（峰值 9.5k ms/min），但為孤立事件，06/14 重新部署後恢復正常（06/14 有新版部署）。

5. **磁碟使用率 68%**：目前尚有餘裕，但需定期清理 log 或快照避免接近上限。




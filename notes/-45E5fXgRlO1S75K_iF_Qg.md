---
tags: cofacts,
---

# 20260421 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, lahna, mrorz, nonumpa
- 線上出席：Alfred, ggm
- https://meet.google.com/mrz-dgrd-pri
:::

## 追蹤事項

### GCE Migration
- [x] 04/16 凌晨重開機清了 swap、也刪了 v6 的 disk，空出 10GB 空間
- [ ] 跑幾週看穩定度，決定是否要再把 tw site 也搬進 GCE
- [ ] 跑幾個月看實際用到的運算量，決定 GCP committed use discount 怎麼買比較划算
- [x] Cloudflare HTML cache and AI crawler defense --> 下面「bots and network cost」討論

### Elasticsearch 升級
- [x] 修正 weekly opendata publish https://github.com/cofacts/opendata/pull/32
	- Review 時要注意 CI 時的備份資料夾位置

:::success
nonumpa 會協助
:::

### Discord spammer
- [ ] 需要把 Discord 進入門檻拉高一點（提問 etc）
    :::info
    nonumpa 會看
    :::

### Cofacts.ai

過進度：https://github.com/orgs/cofacts/projects/12/views/1

- bot user 變多，有更多熱門訊息，但都是 FB link [name=bil]
  - cofacts.ai 可以存取 cofacts.tw 上面顯示的所有資料
  - FB 現在抓不到，url context tool 也很有限，有待 url-resolver 開發完畢
  	- beta-adk 做實驗
  	- 比較 4 種方法
  	- dataset: cofacts 過去資料庫的網域數量，sample 一些具有代表性的網域
  - 可以考慮再找一個外包來開發 url-resolver

## Community updates

### General Channel

- **rumors-deploy 更新**
  - mrorz 分享了 rumors-deploy 的更新，並在 README 中加入了一張架構圖。
  - > mrorz: rumors-deploy 更新囉，也放了張圖
    > https://github.com/cofacts/rumors-deploy?tab=readme-ov-file#architecture-overview
  - 有個方式可以設定 github org 首頁 [name=alfred]

- **Cloudflare Browser Run**
  - mrorz 提出了使用 Cloudflare 的 browser run 功能，可能可以簡化目前在 cofacts worker repo 中爬取資料的流程。
  - > mrorz: Cloudrun 的 browser run (原 browser rendering) 現在可以直接讓 local puppeteer 連結，也有 MCP 可以讓 coding agent 直連
    > https://blog.cloudflare.com/browser-run-for-ai-agents/
    > 這樣一來就不需要像 cofacts worker repo 那樣把爬資料整個拉到 worker 去，直接接好像也可以

### Server Alerts

- **服務短暫中斷**
  - 4 月 15 日晚上 6 點左右，`api.cofacts.tw` 和 `line-bot.cofacts.tw` 出現了約 1 分鐘的 "Unhealthy" 狀態，原因是 "Response code mismatch error"。

### Github Activities

- **`cofacts/ai`**
  - **Langfuse 使用者回饋功能** ([#24](https://github.com/cofacts/ai/pull/24))：MrOrz 開了一個新的 PR 來實作 Langfuse 的使用者回饋系統，讓 UI 上可以針對每個 agent message 傳送 feedback。
  - **CI/CD 流程設定** ([#23](https://github.com/cofacts/ai/pull/23))：為 `cofacts/ai` 專案設定了 pre-commit hooks 和 CI pipelines，以確保程式碼品質。
  - **Markdown 支援與訊息元件重構** ([#21](https://github.com/cofacts/ai/pull/21))：MrOrz review 並修正了 `cofacts/ai` 中關於 Markdown 渲染和訊息元件的程式碼。

- **`cofacts/rumors-api`**
  - **身分驗證流程改造** ([#386](https://github.com/cofacts/rumors-api/pull/386), [#385](https://github.com/cofacts/rumors-api/issues/385), [#384](https://github.com/cofacts/rumors-api/issues/384))：nonumpa 提出了一個新的身分驗證流程，主要是為 `cofacts.ai` 的 SSR (Server-Side Rendering) 設計一個客製化的 Authorization Code Flow。

- **`cofacts/beta-ai`**
  - **URL 內容提取基準測試** ([#17](https://github.com/cofacts/beta-ai/pull/17))：MrOrz 建立了一個 benchmark 腳本，用來測試四種不同的 URL 內容提取策略，並將結果存入 Langfuse 以便比較。
  - **修正 HackMD agent 的操作指示** ([#16](https://github.com/cofacts/beta-ai/pull/16))：為了避免 agent 直接修改大型的會議記錄首頁，更新了對 agent 的指示，讓它只提供生成好的標題和連結，由使用者手動更新。

- **`cofacts/takedowns`**
  - **移除 spam 使用者** ([#294](https://github.com/cofacts/takedowns/pull/294))：nonumpa 移除了一個 spam 使用者。


- **`cofacts/devops`**
  - 新 skills https://github.com/cofacts/devops/pull/5 : 每週 production status report、備份 config、整理 contributor 等


## 開會時間
- 5 月初會暫停一次開會 for RightsCon
- 5/23, 24 g0v summit 擺攤

## RightsCon 擺攤

### 攤位資訊

Your Booth Details

The Community Village is the heart of RightsCon — a mixed-use space located on the ground floor within the Kenneth Kaunda wing of our venue, the MICC.

Booth #: Booth 17

Thematic Zone: Digital Security & Privacy

Date(s): Fri 8 May

Time slot: Half Day (9:00 AM – 1:00 PM)

![](https://g0v.hackmd.io/_uploads/ByRDD1rabg.png)

Q: What is the exact footprint of my booth?
A: A standard Community Village allocation includes:
● Footprint: 2m (width) x 2m (depth) designated floor area.
● Table: One 6ft x 2.5ft (1.8m x 0.75m) trestle table with a linen cloth.
● Seating: Two conference chairs.
● Max Display Height: 2.5 meters for any pull-up banners.
● Electrical: One plug point (Type G)

Q: Can I use floor-standing banners?
A: Yes, provided they fit within your footprint and preferably behind your stand.
Sustainability Tip: We recommend lightweight fabric X-frame banners over heavy vinyl
roll-ups.

Q: What materials are recommended for my booth?
A: We encourage you to use environmentally responsible materials in line with RightsCon’s
commitment to sustainability. Examples could be fabric banners, QR codes linking to digital
content, recycled cardboard displays, and potted plants. Please avoid, if possible, PVC/vinyl
banners, foam boards, polystyrene, inflatables, single-use plastics and excessive printed
materials. Please note that helium balloons are strictly prohibited.

Q: Does my booth need to be staffed for the entire duration of the exhibit?
A: You are responsible for providing staff at your booth for the duration of the exhibit, and all
exhibitors must be registered for RightsCon. Booths must be fully staffed throughout the
duration of the period you have been assigned.

### 展出內容

- [ ] 名片 [name=mrorz] [name=bil]
- [ ] 貼紙 [name=bil]
- [ ] 布條：Cofacts & 彩虹鯨魚旗
- [ ] 傳單
    - [ ] acho 黃色傳單 (英文)，確認 QR code [name=mrorz]
    - [ ] 志超的單面介紹，一般性介紹
- [ ] 多媒體
		- 英文 youtube 輪播
		- 英文網頁 https://en.cofacts.tw/about
- bil laptop, mrorz laptop, portable screen

目標群眾
- 想知道 insight
- 不太會想知道 bot 怎麼用

:::success
回去點一下，不夠的話盡快印
:::

## Bots and server network cost

- Cloudflare 好像不能對 verified bot 設定 cache
    - configuration rule 不能用 verified bot 設
    - 但好像能手動設 user agent rule
- [Cloudflare AI crawl control](https://www.cloudflare.com/zh-tw/ai-crawl-control/) 相關設定
    - 原先：並未開放 AI Crawler 僅開放 Search engine clawer
    - 在 2026/4/18 11am 左右調整了 Cloudflare 設定，讓 bots 來爬 

![](https://g0v.hackmd.io/_uploads/BJgMFY46be.png)

![](https://g0v.hackmd.io/_uploads/BkB1zcVpbx.png)

![](https://g0v.hackmd.io/_uploads/S1lHBPFEpZx.png)

Cost: $1.5/day --> $3/day ($45USD/mo --> $90USD/mo)

Monthly budget 從 250 USD 提升到 300 USD

## 📊 Cofacts Production Status Report (2026-04-21 更新版)

:::spoiler
#### 20260419 調整 swapiness 並洗掉 swap
1. Swap 爆滿原因
 * vm.swappiness: 設定值為 60 (Linux 預設值)。這代表當實體記憶體尚有餘裕時，系統仍會主動將較不常使用的分頁移往 Swap。
 * 最大佔用者: Java (Elasticsearch)。
		 * 其中一個 Java 進程佔用了約 3.6GB 的 Swap，這幾乎吃光了 4GB 的 Swap 空間。
		 * 這通常發生在實體記憶體曾經非常吃緊 (Pressure) 的時候，或是 Elasticsearch 分配的 Heap 雖然大，但部分記憶體區塊長時間未被讀寫，被系統強制 Swap out。

2. 今日 (4/18) 負載異常分析
 * 目前 Load Average 約為 3-4，對於一台 4-vCPU (n2-custom-4-32768) 的機器來說，這仍在安全範圍但偏高。
 * 主要 CPU 消費者仍然是 elasticsearch 與 node /srv/www/server.js。

搬遷 site-tw 的風險評估與建議
既然您只想搬遷 site-tw 並關心 Swap 問題，以下是我的建議：

 1. 解決 Swap 效能隱憂:
		 * 方法 A: 在搬遷前手動執行 swapoff -a && swapon -a (前提是 12GiB Free RAM 足以容納 4GB Swap 的內容)。這能清空 Swap 並讓所有內容回到實體記憶體，大幅提升系統反應。
		 * 方法 B: 調降 vm.swappiness 至 10，減少未來發生同樣情況的機率。
 2. 今日異常的關聯性:
		 * 如果今日負載是常態（例如週末流量增加），搬遷 site-tw (約增加 0.8~1.0 vCPU 負載) 會使 Load Average 常態性維持在 4-5。
 3. 結論:
		 * 搬遷可行: 系統目前還有 12GiB 實體記憶體，且 CPU 雖高但未破表。
		 * 操作順序建議:
				 1. 先優化 GCE 的 Swap 設定 (swappiness = 10)。
				 2. 監測 Elasticsearch 負載是否與今日 site-tw 的特定流量有關（如果共用後端 API）。
				 3. 將 site-tw 移至 GCE，並將其 CPU Limit 限制在合理範圍內（如果是透過 Docker 部署）。

---

✦ 根據 docker stats 與進程列表的即時分析，CPU 高負載的「真兇」呼之欲出了：

  1. CPU 主要消耗者 (即時數據)
   1. rumors-deploy-db-1 (Elasticsearch): 83.85% CPU。
       * 這是最大的來源。Elasticsearch 目前分配了 16GB Heap，且正在處理大量的查詢或索引作業。
   2. rumors-deploy-site-en-1: 78.48% CPU。
       * 這非常異常。一個英文版的 rumors-site 竟然佔用了近 80% 的 CPU。
   3. rumors-deploy-api-1: 32.32% CPU。
       * API 容器也承受了不小的壓力。

  2. url-resolver 的狀況
   * rumors-deploy-url-resolver-1: 0.01% CPU。
       * 它幾乎沒在動。所以 CPU 負載與它無關。

  3. 為什麼 site-en 這麼高？
  通常 site-tw 的流量遠大於 site-en。site-en 衝到 78% CPU 可能的原因有：
   * 爬蟲攻擊: 可能有大量的機器人在爬英文版網站。
   * SSR (Server Side Rendering) 壓力: 如果有大量頁面正在進行伺服器端渲染，Node.js 的 CPU 會飆高。
   * 死循環或記憶體洩漏: 導致 Node.js 持續高負載。

  總結
   * 不是 url-resolver。
   * 主要是 Elasticsearch 和英文版網站 (site-en) 撐起了目前的負載。
   * 今日 (4/18) 負載較高 的原因，看起來是因為 site-en 出現了異常的高負載，加上 elasticsearch 本身就挺忙的。

  如果您想搬遷 site-tw 過來，我們可能得先弄清楚為什麼 site-en 會吃掉這麼多資源。您需要我查看 site-en 的日誌 (logs) 來確認是否有異常流量嗎？
:::

### ⚡ 總結：4/18 開放 AI 爬蟲後負載翻倍
本週系統在 4/18 開放 AI Crawl Control 後出現顯著負載跳升。**Cloud Run 上的 `site-tw` 已達配額上限**，而 **GCE 上的渲染服務則出現記憶體過度擴張**，導致系統 Swap 緩衝歸零。

---

### ☁️ Cloud Run 狀況 (`site-tw`) 🚨 **已達瓶頸**

*   **流量尖峰**：4/19 單日 Network Out 達 **16.6 GB** (翻倍)。
*   **資源飽和**：
    *   **Memory**: P99 觸及 **1.01 GB** (已撞到 1GB 限制)。
    *   **CPU**: P99 觸及 **1.01 vCPU** (已撞到上限)。
*   **影響**：在爬蟲高峰期，`site-tw` 可能出現頻繁重啟或回應延遲。

---

### 🖥️ GCE `cofacts-prod` 狀況 (`site-en`, `site-ja`, `api`)

#### 1. CPU 負載 ⚠️ **4/18 起翻倍**
| 日期 | 平均負載 | P95 負載 | 狀態 |
|------|---------|---------|------|
| 4/14 - 4/17 | ~23% | ~32% | 正常 |
| **4/18 - 4/20** | **~48%** | **~64%** | ⚠️ **高負載** |

*   **分析**：主要消耗來自 **Elasticsearch (CPU 翻倍至 890k)**，顯示 AI 爬蟲正在大量檢索長尾資料。

#### 2. 記憶體管理異常 ⚠️ **Swap 99.8% 已滿**
*   **`server.js` (GCE site-en/ja)**: 峰值 RSS 達 **2.24 GB** (遠高於 Cloud Run 版的 1GB)。
*   **分析**：在缺乏 cgroup 限制下，GCE 上的渲染進程持續吞噬記憶體。由於多個進程累積，導致 **4GB Swap 剩餘不到 10MB**。

---

### 🔍 深度分析：Swap 滿載與 Elasticsearch (ES) 的關聯
經查證，目前 4GB Swap 空間中，有 **3.7 GB (約 92%) 是被 `java` (Elasticsearch) 所佔用**。

*   **為什麼 Swap 會長回來？**：4/18 瞬時壓力期間，Linux 將 ES 中「看起來不常用」的匿名分頁換出。由於 Linux 的 Sticky Swap 特性，這些分頁即便壓力過後也不會主動搬回 RAM，造成目前的滿載假象。
*   **加大 Heap 的利弊**：加大 Heap (目前 16GB) 可能減少部分查詢壓力，但會進一步壓縮作業系統的 Page Cache (快取索引檔案用)，並增加垃圾回收 (GC) 的停頓時間。

---

### 🤖 Cloudflare AI Crawl 關聯分析
*   **主要來源**：`Meta-ExternalAgent` (56GB) 與 `Googlebot` (90GB) 的並發存取。
*   **渲染稅**：AI 爬蟲強迫觸發 JS 渲染，對 Puppeteer 造成巨大壓力，這也是 `server.js` 記憶體在 GCE 上失控的主因。

---

### 🔥 建議行動 (Action Items)

1.  **Cloud Run 擴容 (`site-tw`)**：
    *   建議將 `site-tw` 的記憶體配額提升至 **2GB**，以應付 4/18 後的新常態。

2.  **建立觀察基準 (Swap 重整)**：
    *   手動執行 `swapoff -a && swapon -a` 清空當前 Swap，觀察它是否會在未來幾天因新爬蟲壓力再次快速增長。

3.  **GCE 記憶體回收 (`site-en`, `site-ja`)**：
    *   **已手動重啟一次**。需觀察 30 分鐘後的記憶體回升速度，若回升過快，建議考慮將定時 `pm2 reload` 改為定時 `docker restart`。

4.  **長期控管**：
    *   針對 `Meta-ExternalAgent` 在 Cloudflare 進行頻率限制。
    *   確保 ES `bootstrap.memory_lock: true` 有效。

---
**Reporter:** Gemini CLI
**Date:** 2026-04-21



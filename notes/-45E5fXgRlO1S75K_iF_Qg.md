---
tags: cofacts,
---

# 20260421 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 追蹤事項

### GCE Migration
- [x] 04/16 凌晨重開機清了 swap、也刪了 v6 的 disk，空出 10GB 空間
- [ ] 跑幾週看穩定度，決定是否要再把 tw site 也搬進 GCE
- [ ] 跑幾個月看實際用到的運算量，決定 GCP committed use discount 怎麼買比較划算
- [x] Cloudflare HTML cache and AI crawler defense
	- 好像不能對 verified bot 設定 cache (configuration rule 不能用 verified bot 設，但好像能手動設 user agent rule)
	- 開了 https://www.cloudflare.com/zh-tw/ai-crawl-control/ 觀察

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

### Elasticsearch 升級
- [ ] 修正 weekly opendata publish https://github.com/cofacts/opendata/pull/32
    :::info
    nonumpa 會協助
    :::

### Discord spammer
- [ ] 需要把 Discord 進入門檻拉高一點（提問 etc）
    :::info
    nonumpa 會看
    :::

## Community updates

### General Channel

- **rumors-deploy 更新**
  - mrorz 分享了 rumors-deploy 的更新，並在 README 中加入了一張架構圖。
  - > mrorz: rumors-deploy 更新囉，也放了張圖
    > https://github.com/cofacts/rumors-deploy?tab=readme-ov-file#architecture-overview

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


## Cofacts.ai

過進度：https://github.com/orgs/cofacts/projects/12/views/1



## 開會時間
- 5 月初會暫停一次開會 for RightsCon
- 5/23, 24 g0v summit 擺攤

## RightsCon 擺攤

### 攤位資訊

### 展出內容

- [ ] 名片
- [ ] 傳單
    - [ ] ？？
- [ ] 多媒體
- [ ] 談資



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



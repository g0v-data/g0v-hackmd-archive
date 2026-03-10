# 20260310 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 上次會議待辦

### 臉書推廣
> MrOrz 使用 Gemini 撰寫一篇 Facebook 貼文來推廣 huggingface dataset，並附上圖片。

![](https://g0v.hackmd.io/_uploads/SyxIhOpFbx.png)

![](https://g0v.hackmd.io/_uploads/BJ0NsdaFZx.png)

### 伺服器維護
> - 持續觀察伺服器的記憶體與 I/O 狀況。
> - 檢查 url-resolver 的資源使用情況，評估是否需要更頻繁的重啟策略。

#### Production 機器健康檢查報告 (2026-03-10)

距離 2026-02-13 事故後兩週，以下為 Production VPS 目前的狀態。

##### 整體評估：✅ 健康，但記憶體偏緊

機器自 2/13 重啟後已穩定運行 24 天，無 Zombie Process，Docker 全部正常。

##### 系統指標

| 指標 | 數值 | 狀態 |
|:---|:---|:---|
| **Uptime** | 24 天 (自 2/13 重啟後) | ✅ 穩定運行 |
| **Load Average** | 1.07, 0.79, 0.64 | ✅ 正常 (6 CPUs) |
| **I/O Wait** | 0.04% ~ 0.16% | ✅ 非常低 |
| **CPU Idle** | ~90% | ✅ 充裕 |
| **Zombie Processes** | 0 | ✅ 無 |
| **Docker Containers** | 8/8 Up | ✅ 全部正常 |
| **Swap** | 349MB / 4GB (8.3%) | ✅ 合理範圍 |
| **sysstat** | 正常記錄中 | ✅ 監控有效 |

##### 記憶體使用

```
             total       used       free     shared    buffers     cached
Mem:           15G        15G       253M       719M       147M       6.1G
-/+ buffers/cache:       9.1G       6.5G
Swap:         4.0G       349M       3.7G
```

- **實際使用 (扣除 buffers/cache)**: 9.1GB
- **可用 (含可回收 cache)**: 6.5GB
- **Free (不含 cache)**: 253MB ⚠️

##### 各 Process 記憶體佔用

| Process | RSS | 佔比 | 備註 |
|:---|:---|:---|:---|
| **Elasticsearch (Java)** | **10.3GB** | **63.1%** | JVM Heap 8GB + Lucene off-heap (mmap) |
| **Node.js (APIx5 + Admin API)** | ~1.5GB | ~9% | 多個 PM2 worker |
| **Docker daemon** | 277MB | 1.7% | |
| **Redis** | 97MB | 0.6% | |
| **Chrome (Puppeteer)** | 96MB | 0.6% | url-resolver |
| **其他 Node.js** | ~500MB | ~3% | collab-server, line-bot, site-old 等 |
| **合計** | **~12.8GB** | **~80%** | |

> ⚠️ Elasticsearch 雖然 JVM Heap 設定 `-Xms8g -Xmx8g`，但加上 JVM overhead 與 Lucene mmap，實際 RSS 達到 10.3GB。

##### I/O Wait 歷史 (sysstat/sar)

```
12:00:01 AM     CPU     %user     %nice   %system   %iowait    %steal     %idle
12:05:01 AM     all      6.63      0.00      1.08      0.04      1.05     91.20
12:15:01 AM     all      7.48      0.00      1.18      0.06      1.21     90.08
12:25:01 AM     all      6.15      0.00      1.13      0.16      0.79     91.77
12:35:01 AM     all      7.94      0.00      1.13      0.05      0.88     90.00
12:45:01 AM     all      8.41      0.00      1.18      0.12      1.05     89.25
Average:        all      7.40      0.00      1.15      0.09      0.99     90.38
```

✅ I/O Wait 均低於 0.2%，無磁碟瓶頸。

##### 風險評估

目前系統穩定，但記憶體使用在邊界值上：

- **正常情況**: buffers/cache 有 6.1GB 可被回收，短期內不會有問題。
- **風險場景**: 如果某個瞬間大量 API 請求同時進來，或 Chrome 開多個分頁，可能會再次觸發 Swap Thrashing（與 2/13 事故相同模式）。

##### 建議

1. **升級機器記憶體到 32GB**（最根本的解法，徹底消除記憶體壓力）
2. **或降低 ES Heap 到 6-7GB**（權衡：Query 可能稍慢，但避免整台機器卡死）
3. **持續監控**：定期檢查 `sar -u` 與 `free -h`，留意 Swap 使用量是否持續上升

## AI 逐字稿換 model

20260307 深夜更換

Latency: 應該變低了數秒

![](https://g0v.hackmd.io/_uploads/rJgyQ-W6Y-x.png)

Cost:
https://console.cloud.google.com/billing/017CA0-902C8B-5A26FB/reports;grouping=GROUP_BY_SKU;products=services%2FC7E2-9256-1C43?organizationId=273083271964&project=industrious-eye-145611

![](https://g0v.hackmd.io/_uploads/B1V3MZatWe.png)

- 每個月 cost 不高（~ USD $20/mo, compared to $200/mo total GCP cost）
- 大多是 Video input & Audio input
- 從 Mar 8 數據看來，Cost 顯著下降 --> Vertex AI 有望下降到 $6 USD/mo


## Cofacts.ai 開發

https://github.com/orgs/cofacts/projects/12

- Project description
- Views
- Field definition
- Review issues

---

### AI Chat

- [ ] React-markdown --> 回應編輯器
- [ ] 資料關聯整理：準備 source list 然後掃 messages
- [ ] Session list
- [ ] Deploy to production w/ Claudelare
- [ ] 整理 header (logo、menu、搜尋⋯⋯ etc)
- [ ] landing page focus issue
- [ ] input 在組字時 enter 會直接送出
- [ ] tool call 細節調整
- [ ] Langfuse feedback buttons
- [ ] ADK 升級到可以看到 openapi.json
- [ ] 直接用 ADK type 來 render events 而非轉成 messages
- [ ] 在 tool call 中間關掉瀏覽器視窗再打開同一個 session page，要可以繼續串流結果


### Revamp
> 與 YuTin 討論網站重構事宜。

### Admin
提醒季報的繳交期限。


## Design review

- Authentication
- Cost reduction: GCE w/ Container-optimized OS + Commited usage discount


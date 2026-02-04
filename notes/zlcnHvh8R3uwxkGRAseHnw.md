# 20260204 會議記錄

:::info
- [所有會議記錄](https://gov.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## :eyes: 上次會議跟進事項

- [ ] 將 url-resolver 搬離主機
- [ ] 小聚籌備
    - [ ] 食物
    - [ ] 投放目標
    - [ ] 記得帶：貼紙、不太環保杯 (bil)
    - [ ] VOOM 發文
    - [ ] FB 發文

## 📝 一般討論 (General)

### 伺服器記憶體問題

:::spoiler Detial

#### System Overview
- Uptime: 406 days
- Load Average: 1.05, 1.02, 1.07 (on 6 Cores) -> Healthy CPU Load
- Memory: 16GB Total
- Used: ~12GB (Applications) + ~3GB (Cache)
- Free: ~340MB
- Swap: 100% Used (4GB / 4GB) -> CRITICAL

#### Resource Consumers
##### Memory
The system is under heavy memory pressure with Swap completely full.
1. Elasticsearch (rumors-deploy_db_1): ~7.83GB (50% of Host RAM)
2. Uptime: 2 hours (Recently restarted, yet memory filled again).
3. Heap Setting: ES_JAVA_OPTS=-Xms7g -Xmx7g.
4. Docker Daemon (dockerd): 2.3GB (RES). This is unusually high for a daemon and is a significant contributor to memory pressure.
5. Page Cache: ~3.1GB. usage is normal for Elasticsearch (Lucene indices interally use OS cache), but in a constrained system, this competes with applications.

##### Swap Analysis
- Swap Usage: 100% (4GB).
- Swappiness: 10 (Low).
- Interpretation: Even with a low preference for swapping (vm.swappiness=10), the system was forced to swap out 4GB because physical RAM was completely exhausted.

##### CPU
1. API (rumors-deploy_api_1):
    - Process node /srv/www/build/index.js (PID 14667) was using 74.6% CPU in top snapshot.
    - Averaged ~3.5% in docker stats.
    - This indicates traffic spikes or a heavy query processing, but keeping overall load low (~1.0).
2. Elasticsearch: ~58% of 1 core (in docker stats).

#### Resolution (Implemented 2026-01-28)
User applied the following limits to prevent OOM Killer from targeting random system processes:
1. Elasticsearch (db):
    1. Java Heap: 7g.
    2. Status: Healthy (7.6GB used).
2. URL Resolver:Status: Healthy (82MB used).

Result:
- System Swap is still full (expected without host reboot)

Post-Reboot Verification (2026-01-28 03:00台北時間)
The system rebooted successfully at 19:00 UTC.

Current Status
- Uptime: 5 minutes
- Memory:
    - Used: 7.3GB (Much lower than the previous 12GB + 4GB Swap)
    - Free: 8.3GB
    - Swap: 0B / 4GB (Completely cleared!)
- Docker Daemon: Memory usage is reset and healthy.
- Service Verification:
    - All core services are Up.
    - Note: `db` and `url-resolver` required a manual `up -d` right after reboot as they did not auto-start initially, but they are now running stable with the new limits.

Final Configuration
- Elasticsearch: Heap 7G
- Result: The system now has ~5-8GB of breathing room for OS cache and other services, significantly reducing the risk of a system-wide freeze.

:::

- **mrorz** 回報 API 服務不穩，主因是伺服器記憶體耗盡。
> "API not accessible now"
- 2026/1/28 **mrorz** 進行了緊急處理，包括調降 Elasticsearch 的 Java heap space，並重新啟動伺服器。
> "System Swap is still full (expected without host reboot), but apps are now contained."
> "The system rebooted successfully at 19:00 UTC."
- **mrorz** 提供了詳細的系統狀態分析，指出 Elasticsearch 是主要的記憶體消耗者。

要注意的事情：現在 Linode 上的 Linux 核心沒有開啟 cgroup memory，導致
- docker stats 現在不會顯示各個 container 的 RAM usage
- docker-compose 無法使用 mem_limit (本來我們也沒在用)

總之現在跟昨晚最大的差別就是
- elasticsearch container 的 Java heap space 從 8GB 調降到 7GB
- 重開過機器所以 swap 清空了、docker daemon 用的 RAM usage 也變低了
- docker stats somehow 看不到 RAM 了

### 會議與協作
- **mglee** 表示想參加 2/4 的會議，了解 AI agent 的開發狀況。
> "請問可以參與 2/4 小聚嗎？想多了解目前 Cofacts 開發 AI agent 的狀況~"
- **edchen93** 與 **chewei 哲瑋** 討論了 HackMD 的筆記權限問題。

## 🚨 伺服器警報 (Server Alerts)

- 從 2026-01-27 到 2026-02-03，Cloudflare 多次發出 `cofacts.tw`、`api.cofacts.tw` 和 `line-bot.cofacts.tw` 的服務不健康警報，原因多為 HTTP timeout 或 回應代碼不符 (response code mismatch)。這似乎是一個持續存在的問題。

## 🤖 Github 活動 (Github Activities)

### cofacts/beta-ai
- **Pull Request #12: [Setup Langfuse for all ADK agents](https://github.com/cofacts/beta-ai/pull/12)**
  - 由 `MrOrz` 於 2026-02-02 發起，目的是為所有 ADK agents 設定 Langfuse 以進行觀察。
  - `gemini-code-assist[bot]` 和 `google-labs-jules[bot]` 已提供 review 意見。

### cofacts/takedowns
- **Pull Request #282: [Takedown spam user bk8linkvip iK_cEpwBRkUkW3J-LOKq](https://github.com/cofacts/takedowns/pull/282)**
  - 於 2026-01-31 建立並完成，處理了垃圾訊息使用者的下架。

## nDX

https://ndx.dta.tw/google-%e5%8f%b0%e7%81%a3%e6%96%b0%e8%81%9e%e6%95%b8%e4%bd%8d%e5%85%b1%e6%a6%ae%e5%9f%ba%e9%87%91%e6%94%af%e6%8c%81%e4%b9%8b-ndx-%e6%95%b8%e4%bd%8d%e5%89%b5%e6%96%b0%e7%8d%8e%e5%8a%a9%e8%a8%88-2/

Cofacts.ai：打造多代理人 AI 陪伴公民查核者對抗網路不實訊息
台灣實科協會

焦點小組運作
- 換 term？

社群工作坊與國際交流
- 國內分享
- 國際交流

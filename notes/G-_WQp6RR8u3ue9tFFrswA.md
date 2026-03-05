# 20260305 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, lahna, mrorz, nonumpa
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 上次會議待辦
- **資料庫遷移**：nonumpa 分享 feature/upgrade-to-elasticsearch-v9 branch 進度與效能問題。

## Past events

- DB backup
    - Production elasticsearch 的 backup 停了，因為 gcs 找不到
    - 主因是 production elasticsearch 沒有 bind mount elasticsearch 放 plugin 的地方
    - 改了 docker-compose.yml 使 plugin 也在 host machine 的檔案系統了
- Opendata 
    - 自動打包 https://github.com/cofacts/opendata/pull/29
    - 自動上傳 https://github.com/cofacts/opendata/pull/30
    - https://huggingface.co/datasets/Cofacts/line-msg-fact-check-tw 每週一凌晨會更新了
- 要 po 粉專宣傳嗎？可以。

:::success
要用 Gemini 寫個 FB 貼文推廣 huggingface dataset + 圖
by MrOrz
:::

### 重大事件：伺服器無回應
- **mrorz** 在 2026/02/13 20:06 (UTC+8) 回報 API 無回應，最終在約一小時後，透過重啟伺服器解決。
> mrorz@g0v-tw: API 似乎掛了，但我看不出為啥
- **mrorz** 提供了詳細的事後分析，指出原因是 Elasticsearch container 變成殭屍程序，導致 Docker daemon 操作卡死。
> mrorz@g0v-tw: Post-mortem: Production API Unresponsive Incident (2026-02-13)
事件摘要
Production API 在晚間無回應。經檢查發現系統負載極高 (Load Average > 6)，Elasticsearch container 變成 Zombie process 且無法停止，Docker daemon 操作卡死。最終透過重啟整台 VPS 恢復服務。

#### Post-mortem: Production API Unresponsive Incident (2026-02-13)
事件摘要
- Production API 在晚間無回應。經檢查發現系統負載極高 (Load Average > 6)，Elasticsearch container 變成 Zombie process 且無法停止，Docker daemon 操作卡死。最終透過重啟整台 VPS 恢復服務。
影響範圍
- 時間: 約 20:00 - 21:03 (UTC+8)，持續約 1 小時。
- 服務: API (api.cofacts.tw) 回應 Timeout，導致網站與 LINE Bot 無法正常運作。
- 狀態: 目前已完全恢復。

##### 事件時間軸 (Timeline)
• 20:06: User 發現 API 無反應。嘗試重啟 url-resolver 與 api 成功，但服務未恢復。嘗試停止 db (Elasticsearch) 失敗，docker stop 與 docker kill command hang 住。
• 20:39: Coding Agent (我) 介入調查。
• 20:40: 診斷發現機器 Load Average 6.11，Elasticsearch process (PID 2443) 呈現 Zombie 狀態且佔用 26.5% CPU。kswapd0 活躍 (Swap Thrashing)。
• 20:41: 嘗試 docker-compose restart db，Timeout 失敗。
• 20:43: 嘗試直接 kill -9 Elasticsearch 的父行程 (containerd-shim)。
結果：Container 重啟了，記憶體釋放 (12GB -> 8.7GB)，API Port 恢復連線。
問題：Elasticsearch 因非正常關閉，留下了 write.lock 檔案，導致新啟動的 process 無法寫入資料目錄而啟動失敗。
• 20:50: 嘗試再次停止 db container 以清理 lock files。所有 Docker 指令 (stop, kill, update) 全部卡死無反應。
• 20:54: 判斷 Docker Daemon 本身已故障，嘗試 systemctl restart docker。
結果：指令卡在 deactivating 狀態超過 6 分鐘，無法完成 graceful shutdown。
• 21:00: 執行 sudo reboot 強制重啟整台機器。
• 21:03: 機器重啟完成。SSH 恢復，所有 Docker containers 自動啟動 (Up)，Load Average 降至正常值 (1.80)。API 確認恢復正常回應。
• 21:18: 啟用 sysstat (sar) 服務以記錄未來系統資源歷史數據。更新 VPS.md Troubleshooting 指南。

##### 根因分析 (Root Cause Analysis)

- 直接原因: Elasticsearch Java Process 進入 Zombie/Uninterruptible Sleep (D state) 狀態，導致 Docker Daemon 無法透過標準信號 (SIGTERM/SIGKILL) 控制它。
- 潛在原因 (推測): Memory Exhaustion & I/O Wait。
- 證據：事故當下 kswapd0 佔用 CPU，Swap 使用量增加，Load Average 飆高。
- 推論：系統記憶體不足 (16GB RAM, ES Heap 8GB + Chrome/Node.js overhead)，導致 Kernel 頻繁將 Page Cache 交換到 Disk (Thrashing)。這造成 Disk I/O 隊列塞爆，所有嘗試寫入 Log 或狀態檔的操作 (包含 Docker 指令) 全部被 Block 住。
- API Timeout: 分析 Logs 發現大量請求在 120s (Timeout 設定) 結束，證實因為 DB 卡死導致 API thread pool 耗盡或無法回應。

##### 後續改善措施 (Action Items)
1. [已完成] 啟用系統監控: 已在 Production 機器啟用 sysstat，每 10 分鐘記錄一次 CPU、I/O Wait 與記憶體狀態。
未來除錯指令：sar -u -f /var/log/sysstat/sa<DATE>
2. [已完成] 更新文件: 更新
VPS.md，加入 sysstat 使用方式與嚴重 Docker 故障的處理流程。
3. [建議] 持續觀察記憶體與 I/O:
若再次發生類似狀況，檢查 sar 紀錄確認是否為 I/O Wait 飆高。
若記憶體壓力持續，建議將 Elasticsearch Heap Size 從 8GB 調降至 6GB-7GB，預留更多空間給 OS Page Cache。
4. [建議] 檢查服務資源佔用: 留意 url-resolver (Puppeteer) 是否有記憶體洩漏傾向，可能需要更激進的重啟策略或資源限制。

## Github 活動
### cofacts/ai
- **MrOrz** 關閉了 Cloudflare Tunnel sidecar 相關的 Pull Request。
  - [Add Cloudflare Tunnel sidecar to Cloud Run deployment](https://github.com/cofacts/ai/pull/11)
- **MrOrz** 關閉了 Cloud Run workflow 相關的 Pull Request。
  - [Add Cloud Run deployment workflow with sidecar support](https://github.com/cofacts/ai/pull/10)
- **MrOrz** 建立了 issue，希望更新專案的 README.md。
  - [Update readme](https://github.com/cofacts/ai/issues/9)
- **MrOrz** 關閉了 Langfuse instrumentation 相關的 Pull Request。
  - [Setup Langfuse instrumentation for Google ADK agent](https://github.com/cofacts/ai/pull/8)
- **MrOrz** 關閉了 session 頁面讀取問題的 Pull Request。
  - [Load session chat history on direct navigation](https://github.com/cofacts/ai/pull/3)

#### cofacts/takedowns
- **MrOrz** 提出了一個關於隱私移除的 Pull Request，Cofacts 工作小組決定對回報的圖片進行處理，在保護個資的同時，保留詐騙內容以供公眾警惕。
  - [20260228 privacy removal](https://github.com/cofacts/takedowns/pull/285)

#### cofacts/opendata
- **MrOrz** 關閉了一個關於開放資料產生的 Pull Request。
  - [feat: Add Open Data generation workflow](https://github.com/cofacts/opendata/pull/29)

## 系統警報
- 在 2026/02/13，`cofacts.tw`, `api.cofacts.tw`, `line-bot.cofacts.tw` 皆因 HTTP timeout 或 回應 530 錯誤而觸發警報。
- 在 2026/02/23，`api.cofacts.tw`, `line-bot.cofacts.tw`, `cofacts.tw` 皆因 HTTP timeout 而觸發警報。

### 自動刪除帳號
	
- 2/23 ~ 2/25 spammer 持續貼文，沒發現他已經被我們標記。
- 最近 spammer 都貼泰文 [name=nonumpa]
- 網站流量最高前五名有孟加拉 [name=bil]
	
## Transcript model

- 2026 年 3 月初出了 Gemini 3.1 Flash Lite https://ai.google.dev/gemini-api/docs/models/gemini-3.1-flash-lite-preview?hl=zh-tw
- Transcript benchmark 跑起來很漂亮
	- [和之前用的 1.5 pro 002 比較](https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/datasets/cm7ri4we80004ql0bfu6lvtoi/compare?runs=cm9pyw5mr00mfjy061mdp8mbd&runs=297ab508-4758-4bd1-a30d-7a9d441c739b&runs=6525f9e8-9c3f-4a51-9490-6c4f75eff39a)
	- [和現在用的 gemini 2.5 flash 比較](https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/datasets/cm7ri4we80004ql0bfu6lvtoi/compare?runs=297ab508-4758-4bd1-a30d-7a9d441c739b&runs=6525f9e8-9c3f-4a51-9490-6c4f75eff39a&runs=cmc7y45eo003ulr08zef9jtd1)
	- 準確度相當，速度稍快
- [Pricing](https://cloud.google.com/vertex-ai/generative-ai/pricing#standard)
    - Gemini 2.5 Flash：
        - Video: $0.30/1M token
        - Audio: $1/1M token
    - Gemini 3.1 Flash-Lite
        - Video: $0.25/1M token
        - Audio: $0.5/1M token
- 又好又快又便宜 --> 換！ https://github.com/cofacts/rumors-api/pull/380

## nDX 專案

分三塊
1. cofacts.ai：chat interface & agent
2. Website revamp：現在的 cofacts.tw 的改進，以與 AI 整合
3. 行政項目：找人、準備文件等等


### Cofacts.ai

- 嘗試過的組合
    - mastra + copilotkit https://github.com/MrOrz/beta-ai-mastra
        - mastra 是 typescript 很不錯
        - 和 adk 相比 mastra 包的東西有點太多（workflow, trace 什麼的）我覺得可能會有點複雜
    - adk + copilotkit (AGUI)
        - copilotkit 有現成的 UI 算是舒服
        - 但即使是「在 landing page 傳訊息之後跳轉到 session 頁面」這樣的 UX，也會需要用到付費的 headless hook
        - 只用 AGUI protocol: 不會保留 ADK 的 author 等欄位
        - 最後決定直接用純的 ADK
- 現況
    - 製作方法
        - 在 antigravity 分析完現有 figma 圖片之後送進 stitch 做 UI，經過多次來回後完成初稿 https://stitch.withgoogle.com/projects/3329376242415119860?pli=1
        - 將初稿（圖片 + HTML）下載下來後 vibe coding
    - https://github.com/cofacts/ai
        - 對話已經會 work (同 beta-ai)
        - 右側欄還沒接
    - Tanstack start 接 Python ADK
        - Python ADK 所有 API 不直接對外，由 tanstack start 的 API 做 proxy
    - Staging: cofacts-ai-236494820908.asia-east1.run.app
        - 直接用 [sidecar](https://docs.cloud.google.com/run/docs/deploying?hl=zh-tw#sidecars) 把 ADK 和 tanstack start build 出來的兩個 image 塞在同一個 Google run service
        - min instance = 0，啟動稍慢 (acceptable for staging)
- TODO
	- React-markdown --> 回應編輯器 
	- 資料關聯整理：準備 source list 然後掃 messages 
	- Session list
	- Deploy to production w/ Claudelare
	- 整理 header (logo、menu、搜尋⋯⋯ etc)
	- landing page focus issue
	- input 在組字時 enter 會直接送出
	- tool call 細節調整
	- Langfuse feedback buttons
	- ADK 升級到可以看到 openapi.json
	- 直接用 ADK type 來 render events 而非轉成 messages
	- 在 tool call 中間關掉瀏覽器視窗再打開同一個 session page，要可以繼續串流結果

### Website revamp

- In contact with YuTin, will discuss tomorrow night 8pm
- 幾個大項目 
  - cofacts.tw 重寫進 cofacts.ai 的 repository，終極目標是 cofacts.ai 取代現在 cofacts.tw 的樣子
  - cofacts 帳號系統 https://docs.google.com/document/d/1sZ4jOsrZPvbJv4QjlMxgbqFsh_pTZNBRs-NbG-HU0rM/edit?tab=t.3fmvmgsjjweh (不確定)
	- 圖片影片向量化搜尋、thumbnail

### Administrative

- Quarterly reports deadline
	- 2026-07-05 Q1 report
	- 2026-09-04 Mid-term report
	- 2026-12-04 Q3 report
  - 2027-02-01 Final report
- 報告開放兩週前繳交
- 2027-04 實體發表會
- Legal documents and contracts	
	
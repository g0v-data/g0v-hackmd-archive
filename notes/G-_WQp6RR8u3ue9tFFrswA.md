# 20260305 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 上次會議待辦

- [ ] **小聚檢討**：盤點延長線，為 4/12 小聚做準備。
- [ ] **伺服器**：將 Elasticsearch 的 heap space 從 7GB 調整到 8GB。
- [ ] **資料庫遷移**：nonumpa 分享 feature/upgrade-to-elasticsearch-v9 branch 進度與效能問題。
- DB backup
    - Production elasticsearch 的 backup 停了，因為 gcs 找不到
    - 主因是 production elasticsearch 沒有 bind mount elasticsearch 放 plugin 的地方
    - 改了 docker-compose.yml 使 plugin 也在 host machine 的檔案系統了
- Opendata 
    - 自動打包 https://github.com/cofacts/opendata/pull/29
    - 自動上傳 https://github.com/cofacts/opendata/pull/30
    - https://huggingface.co/datasets/Cofacts/line-msg-fact-check-tw 每週一凌晨會更新了

## Past events
### 系統架構討論
- **mrorz** 在 2026/02/13 分享了系統架構圖，並引發了相關討論。
> Alfred chen@g0v-tw: 我理解的我們系統的結構長這樣對不對？

### 重大事件：伺服器無回應
- **mrorz** 在 2026/02/13 20:06 (UTC+8) 回報 API 無回應，最終在約一小時後，透過重啟伺服器解決。
> mrorz@g0v-tw: API 似乎掛了，但我看不出為啥
- **mrorz** 提供了詳細的事後分析，指出原因是 Elasticsearch container 變成殭屍程序，導致 Docker daemon 操作卡死。
> mrorz@g0v-tw: Post-mortem: Production API Unresponsive Incident (2026-02-13)
事件摘要
Production API 在晚間無回應。經檢查發現系統負載極高 (Load Average > 6)，Elasticsearch container 變成 Zombie process 且無法停止，Docker daemon 操作卡死。最終透過重啟整台 VPS 恢復服務。


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
    - adk + copilotkit
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
- 時程
    - [ ] Johnson 分享新年期間 Cofacts.ai 開發進度。
    - [ ] 討論 evaluation 機制。
- Projects (organization project on Github)
    - Cofacts.ai
    - Website revamp
    - Administrative

### Website revamp

- In contact with YuTin, will discuss tomorrow night 8pm
- 幾個大項目
    - 


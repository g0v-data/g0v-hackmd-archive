# 20251229 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## :eyes: 上次會議跟進事項

- [nonumpa] 試用 Google Cloud 上的 Hosted Elasticsearch
- GCP cost 監控

## 伺服器穩定度

- 從 12/23 到 12/28，`api.cofacts.tw` 和 `line-bot.cofacts.tw` 持續出現服務不穩定的警報，原因包括 "Response code mismatch error" (回傳 502, 530) 和 "HTTP timeout occurred"。
- mrorz: "Line bot tunnel error", "API 也 tunnel rrror" (2025-12-27)
    - ![](https://g0v.hackmd.io/_uploads/BJ8NyCyVWe.png) ![](https://g0v.hackmd.io/_uploads/r13NkRJVbe.png)
    - 重開 url-resolver 後恢復

## 2025 回顧

### 第一季 (1-3月)
- 基礎設施與維運
    - 自動化垃圾訊息移除：設計並實作了自動偵測並移除垃圾訊息的機制 (Automated Spam Removal)。
    - Langfuse/Clickhouse 維運：處理了監測服務 Langfuse 因 Clickhouse 記憶體與磁碟空間問題導致的服務不穩，並完成修復與設定優化。
    - 網站安全強化：透過 Cloudflare 設定了內容安全政策 (CSP)，防止點擊劫持 (Clickjacking) 攻擊。
    - 服務穩定性：修復了因 LLM 影片轉錄功能超時導致的服務中斷問題。
- 功能開發與更新
    - LLM 影片轉錄：完成 Gemini 模型比較實驗，並正式上線 LLM 影片轉錄功能，取代舊有服務。
    - API 修復：修正了後台 API openapi.json 的 bug。
    - 徽章系統 (Badge)：開始進行徽章功能後端 API 的開發。
- 社群與活動
    - RightsCon 2025：完成籌備並參與數場於台北的座談、演講與擺攤活動。
    - SITCON 2025：參與 SITCON 學生計算機年會，設置攤位與社群交流。
    - g0v 大松：參與 g0v 黑客松並進行專案協作。

### 第二季 (4-6月)
- 基礎設施與維運
    - 自動化下架系統優化：為自動化下架 (Takedown) 系統撰寫了審核者 (Moderator) 操作文件，並持續根據實務案例調整偵測邏輯，因誤判率高而暫時關閉了針對文章 (Article) 的自動偵測。
    - 攻擊事件應對：成功分析並阻擋了一次來自特定 IP 的攻擊事件。
    - Langfuse 升級：將 Langfuse 監測服務從 3.56.0 升級至 3.66.1 版，並解決了背景遷移任務卡住的問題。
    - Open165 專案重構：啟動 Open165 專案的重構計畫，將資料同步功能從 Github Workflow 遷移至 Cloudflare Workflows。
- 功能開發與更新
    - 徽章系統 (Badge)：正式上線徽章功能，包含前後端實作，並後續增加了撤銷徽章的 API。
    - 網站 UI/UX 優化：
        - 改善了網站的文章篩選器 (Filter) 介面。
        - 修復了「使用現有回應」時會搜尋到已刪除回應的問題。
- 社群與活動
    - 謠言惑眾獎：與 MyGoPen 合作推廣「謠言惑眾獎」活動。
    - 線下小聚：舉辦了數場編輯小聚並根據回饋進行了檢討與改善。
    - g0v 大松：參與 g0v 黑客松活動。
### 第三季 (7-9月)
- 基礎設施與維運
    - 服務穩定性改善：
        - 處理了多次因 url-resolver 服務記憶體問題造成的服務中斷，並將其重啟頻率增加至每小時一次以緩解問題。
        - 為 rumors-deploy 中的多項服務增加了 restart:always 策略，確保服務異常中斷後能自動重啟。
        - 處理了一次 DDoS 攻擊。
    - Cloudflare Tunnel 設定：完成 Cloudflare Tunnel 的設定，並逐步移除 Nginx，簡化架構。
    - 域名重導向：將 cofacts-api.g0v.tw 的流量永久重導向至 cofacts.tw，統一管理。
    - DevOps 手冊：開始撰寫 devops-manual 文件，記錄系統架構與維運細節。
- 功能開發與更新
    - 編輯器體驗優化：上線了新的編輯器，改善了項目符號 (List) 的 Markdown 使用體驗。
- 社群與活動
    - g0v 大松與面海松：參與 g0v 黑客松與面海松活動。
    - 線下小聚：持續舉辦編輯小聚。
    - Gather Town 停用：因 Gather Town 改變收費方案，會議地點轉移至 Google Meet。

### 第四季 (10-12月)
- 基礎設施與維運
    - 遷移至 Google Cloud Run：成功將 cofacts.tw 網站服務從 Linode 主機遷移至 Google Cloud Run，提升擴展性與穩定性。
    - Cloudflare 健康檢查優化：調整了 Cloudflare Health Check 的警報設定，有效減少了誤報。
    - Langfuse 服務修復：解決了 Langfuse 因 Redis 連線中斷而停止接收資料的問題，並完成版本升級。
    - Elasticsearch 遷移研究：開始進行將 Elasticsearch 從 v6 遷移至 v9 的研究與測試。
    - 垃圾訊息處理：持續透過 takedowns 機制處理並下架多位垃圾訊息使用者。
- 功能開發與更新
    - 移除讚/倒讚功能：上線了收回對回應的讚或倒讚的功能。
    - Node.js 版本升級：將網站前端的 Node.js 環境升級至 24 版。
    - UI/UX 修復：
        - 修復了行動版網頁上使用者頭像右側空間過大的問題。
        - 完成了 ArticleReplyFeedback 收回功能的實作。
- 社群與活動
    - 人權市集：參與了在國家人權博物館舉辦的人權市集擺攤活動。
    - 線下小聚與感恩茶會：舉辦了數場編輯小聚，並在年底舉辦了期末感恩茶會。

## 2026 TODO

- Cofacts classifier + URL resolver https://github.com/cofacts/worker/pull/3/files
    - URL resolver that handles videos https://github.com/cofacts/worker/issues/2
- [cofacts.ai] Groundness Check agent 實作 https://github.com/cofacts/beta-ai/issues/5
    - ADK <> Langfuse integration https://github.com/cofacts/beta-ai/issues/6
    - 接上個好 UI？至少要可以切 session 沒 bug + show tool calls + 停止等等
- Elasticsearch v9 migration
- Preview of videos in article list
    - Thumbnails 怎麼做 https://g0v.hackmd.io/@cofacts/rd/%2FaJqHn8f5QGuBDLSMH_EinA#Video-summarization-for-thumbnails
    - Cloudflare R2 https://g0v.hackmd.io/@cofacts/meetings/%2FJqg-lecyRhKtFDnbxnx_ZA#Possible-Solution-GCS-bucket---gt-Cloudflare-R2 搭配 Cloudflare video / images？
- 網站用 TailwindCSS 改寫？
    - 移除 CSS-in-JS 可以簡化啟動流程 https://g0v.hackmd.io/@cofacts/rd/%2F%40cofacts%2FHJ_O1Xhhs#Ideas
    - 子龍 figma: 
- Cofacts analytics: Opendata trend & LINE Bot usage 報表問題
- Devops manual
- cAdvisor 研究與安裝



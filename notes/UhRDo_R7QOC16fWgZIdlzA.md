<i>0908</i> 服務不穩定問題、混合式URL resolver、devops-manual、面海松與小聚籌備
# 20250908 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- 線上出席：bil, nonumpa
- https://meet.google.com/mrz-dgrd-pri
:::

## 本次會議待追蹤項目 (由 2025/09/01 會議記錄結案)

No Updates:
*   **[Johnson]** 資訊安全權限設定
*   **CCPRIP - Analytics**: Opendata trend & LINE Bot usage 報表問題
*   **cofacts.ai**: Groundness Check agent 實作 (追蹤提案與文件)
*   **[nonumpa, mrorz]** LLM based Topic Classifier: 追蹤 bug 修復與 benchmark 結果

Updates:
*   **[mrorz]** 確認 Johnson 家是否還有中文講義
    * 大概有 2cm 厚。另，英文也還有 3cm 厚
    * 9/13 面海松需攜帶 
*   **url-resolver update**: Implement Hybrid URL Content Resolver with Gemini and Video Understanding (https://github.com/cofacts/worker/issues/2)
    - Should have a design doc first
    - break down to rumors-api after design review
*   **Cofacts API access management**: 執行並持續追蹤 [5/12 會議](https://g0v.hackmd.io/4gx_3uFUTHSYB853Fcgmlg?view#Op-API-access-management)中提議的 Cofacts API access management 第一步
    

## 系統狀況

### Error reports from server-alerts

- **2025-09-07**
  - `cofacts.tw`, `api.cofacts.tw`, `line-bot.cofacts.tw` 在台灣時間 23:00 - 24:00 之間發生數次 HTTP timeout error。
- **2025-09-05**
  - `cofacts.tw`, `api.cofacts.tw`, `line-bot.cofacts.tw` 在台灣時間 03:53 - 05:57 之間發生數次 HTTP timeout error。

### General discussion

- **服務不穩定**
  - `mrorz` 提到 `url-resolver` 服務在 2025-09-07 發生問題，重啟 API 後恢復正常。
  > 11:30 發現 url-resolver 用到 2GB --> 重開 url-resolver
  > 12:20 好像還是壞的 (網站首頁可 load 但 article page 不行)，server loading 都在 1 以下。
  > 試圖重開 DB --> 還是壞的
  > 12:31 試圖重開 API --> 好了
  - `nonumpa` 在 2025-09-05 提到，當天早上 7~12 點 API/DB 連線狀況導致 linebot 異常。
  > nonumpa@g0v-tw猜測是早上 7~12 點 api/db 連線有些狀況，
  > 所以 linebot 才有一直有問題、只有網站有 load。
  > 我當時只有打開首頁，沒有點訊息列表，才沒有發現...
  >
  > 稍微紀錄一些 log 在這裡 https://hackmd.io/yD0sOcj5SWehyUvr-V8gkw

## Github Activities

### New Issues

- **[cofacts/worker] [Feature] Implement Hybrid URL Content Resolver with Gemini and Video Understanding**
  - Issue: https://github.com/cofacts/worker/issues/2
  - `MrOrz` 根據 2025/08/26 會議結論，開票實作混合 `url-resolver` 與 Gemini 的 URL 解析器。
- **[cofacts/rumors-deploy] Use env_file instead of environment in docker-compose files**
  - Issue: https://github.com/cofacts/rumors-deploy/issues/37
  - `MrOrz` 建議將 secrets 從 docker-compose 移至 env files 管理，避免外洩。

### Merged Pull Requests

- **[cofacts/takedowns] Takedown spam user Pepi Lopian p1DeDpkBkYc0K64ECXPG**
  - Pull Request: https://github.com/cofacts/takedowns/pull/256
  - 處理了由 Takedown Bot 自動建立的 spam user 移除請求。

## CCPRIP

### [Op] cofacts/devops-manual
- 把 docker-compose.yaml 改寫成沒有 secret 的版本，讓 AI 方便讀
  - https://github.com/cofacts/rumors-deploy/issues/37
- Private Github Repository
  - Format: markdown files
  - 人 or coding agent 能來管理 Cofacts infra
- 把 Cofacts 的 infra 記下來
  - README.md
    - onboard 新的 devops 要設定什麼、給哪些權限
    - 先 checkout cofacts 的 repo
    - 各 Cofacts repository 簡介
    - 文件的 table of contents
  - Linode.md
    - ssh config
    - 放 authorized keys
    - server 上的資料夾結構
    - Cronjob
    - rumors-deploy & docker-compose 介紹、與實際機器上的差異
  - Cloudflare.md: MCP
    - 一些已知設定（MCP 拉下來存著）
  - GCP.md:
    - Google cloud logging
    - cloud run（gcloud 指令）
  - Backup / recovery
    - GCS multimedia
    - GCS Elasticsearch snapshot (weekly)
      - Credentials
    - Linode Elasticsearch
    - Opendata repo https://github.com/cofacts/opendata/blob/master/CONTRIBUTING.md
  - Analytics
    - BigQuery (LINE)
    - Google Anlaytics (Website, LIFF)
    - Looker studio (/analytics)

## 9/13 面海松

攜帶
- [x] Cofacts 黃色傳單（華語 + 英語）[name=mrorz]
- [x] Cofacts Logo 貼紙 [name=mrorz]

做
* [ ] 設定 cofacts-api 的 303 redirect 並找 Ronny approve [name=mrorz]
  * [ ] 跟 AI 一起寫 cofacts/devops-manual [name=mrorz]
* [ ]  [Implement Hybrid URL Content Resolver with Gemini and Video Understanding](https://github.com/cofacts/worker/issues/2)
* [ ] 準備十月小聚，小樹屋 [name=bil]

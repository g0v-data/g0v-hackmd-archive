# 20260106 會議記錄

:::info
- [所有會議記錄](httpss://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, mrorz, alfred
- 線上出席：nonumpa, Chris
- https://meet.google.com/mrz-dgrd-pri
:::

## :eyes: 上次會議跟進事項

- [x] 研究 cloud logging 為啥會暴增
	- 2025/11/26 release node-fetch upgrade, which updates the user-agent string
	- 2025/12/29 updated Cloudflare rate limiting rule conditions
	- ![](https://g0v.hackmd.io/_uploads/ryexNJD9VZl.png)


## 專案進度與討論摘要

### 綜合討論 (General)

- **Cofacts 工作會議參與**: 有成員詢問工作會議是否需要報名，Bil 回應可直接參加。

### 系統狀態 (Server Status)

- **服務中斷事件**:
  - **日期**: 2026-01-01
  - **服務**: `api.cofacts.tw`, `line-bot.cofacts.tw`
  - **狀況**: Cloudflare 偵測到服務無回應 (錯誤代碼 502, 530)。
- **服務中斷事件**:
  - **日期**: 2026-01-03
  - **服務**: `api.cofacts.tw`, `line-bot.cofacts.tw`
  - **狀況**: Cloudflare 偵測到服務無回應 (錯誤代碼 530)。

### 開發活動 (GitHub Activities)

- **隱私權下架處理**:
  - **Pull Request**: `cofacts/takedowns#279` - [Add 2024/07/22 privacy takedown notice](https://github.com/cofacts/takedowns/pull/279)
  - **進度**: 由 jules-bot 提出，經 nonumpa review 後，已由 MrOrz 合併並關閉。

- **部署流程改善**:
  - **Pull Request**: `cofacts/rumors-deploy#38` - [Move all environment variables to dedicated env files](https://github.com/cofacts/rumors-deploy/pull/38)
  - **進度**: 為簡化環境變數管理，MrOrz 提出將其移至獨立的 .env 檔案，此 PR 已完成並關閉。

## Devops manual

> 首次提議：https://g0v.hackmd.io/UhRDo_R7QOC16fWgZIdlzA?view#Op-cofactsdevops-manual

- Production & staging 的 rumors-deploy/docker-compose.yaml 裡的 secret 已經全部都搬到 env-files
- Staging 上的服務也從 answerfamily-deploy 改成用 rumors-deploy 啟動
- 建立 https://github.com/cofacts/devops

Example usage
- 問 server 現在如何
- 問 log 狀況 ![](https://g0v.hackmd.io/_uploads/S1g2qYUc4Zx.png)
- 寫好 cloudflare 文件之後：
    - 分析流量與被攻擊狀況
    - 畫系統相依圖（cloudflare 上有服務 mapping；rumors-deploy 上）
- 加上 analytics 說明（bigquery, Google analytics 等等）: 可以詢問流量 

TODO
- 改 README.md 只留下每個檔案在幹嘛
    - 介紹說這份文件是讓人和 coding agent 能協同管理 Cofacts deployment 用的
    - 詢問範例
    - 介紹文件結構：Getting access, setup & 其他
- 寫 AGENTS.md 放幾點：
	- 原則：簡潔、不寫常識、專注在 Cofacts 專有的設定與架構
	- 當使用者發問時，可以預設使用者已經完成所有文件的 Getting access & setup 過程；如果遇到問題，才回頭檢視 setup 有沒有做完全。
	- 介紹怎麼撰寫與維護這些 markdown file（移除 update.md）：
		- 先看文件針對服務現狀寫了哪些敘述
		- 連進服務裡看看那些敘述是否還符合文件敘述
		- 如果發現文件與現狀不同，詢問使用者應該怎麼處理
		- 如果有新發現，也詢問使用者
- 加入 Github claude workflow
	- open issue & `@claude` to collect information
	- Authenticate to Google using [workload identity provider](https://github.com/cofacts/rumors-site/blob/master/.github/workflows/build-and-push.yml#L100-L103)
	- Cloudflare & VPS: 不確定怎麼做
- 其他想法？
	> https://github.com/pranshuparmar/witr Why is this running? [name=Chris]
	> 因應害怕 rm 的風險，我現在用保哥的 https://github.com/doggy8088/better-rm ，它取代系統的 rm，它會擋一些已知重要的目錄不可刪，而允許刪除的檔案，它會改移到垃圾筒，因此可以事後復原 [name=Chris]


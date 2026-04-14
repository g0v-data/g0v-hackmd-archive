---
tags: cofacts,
---

# 20260414 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, lahna, nonumpa, mrorz
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 追蹤事項

### GCE Migration

- [x] 可以開始把 en, ja 搬到 GCE 上 --> estimated cost save = 70USD/mo
	- Done on 2026/4/8
- [ ] 跑幾週看穩定度，決定是否要再把 tw site 也搬進 GCE
- [ ] 跑幾個月看實際用到的運算量，決定 GCP committed use discount 怎麼買比較划算
- [ ] Cloudflare HTML cache and AI crawler defense
	- 這個觀察 traffic 再來進行也不遲
- [x] Linode rsync 備份 + 刪 instance
	- rsync: 4/12 已備份在 macbook pro (僅設定檔如 env files & cronjobs)
	- 4/14 已刪除 Linode instance

:::spoiler
## 📊 調查結果摘要

### 🖥️ GCE `cofacts-prod` 伺服器負載

#### CPU（`sar -u` 日平均）

| 日期 | %user | %sys | %iowait | %idle |
|------|-------|------|---------|-------|
| 4/8 | ~12% | ~1.6% | **0.42%** | 86% |
| 4/9 | ~14% | ~2.0% | **0.58%** | 83% |
| 4/10 | ~19% | ~2.6% | **0.59%** | 77% |
| 4/11 | ~20% | ~2.6% | **0.45%** | 77% |
| 4/12 | ~18% | ~2.5% | **0.60%** | 79% |
| 4/13 | ~18% | ~2.4% | **0.70%** | 79% |

**結論**：CPU 無問題。4/10-11 因新服務上線後穩定跑，%user 升了約 8pp，但 %idle 仍有 77%。`%iowait` 全程 < 1%，無 I/O 瓶頸。

#### 記憶體（目前狀態）⚠️ **需要關注**

| 日期 | **平均 used** | **%memused** | kbmemfree |
|------|-------------|-------------|-----------|
| **4/8 前段**（上線前） | ~15.1 GiB | **50.3%** | ~8.0 GiB |
| **4/8 後段**（新服務啟動） | ~12.2 GiB | **60.0%** | ~7.3 GiB |
| **4/9** | ~12.5 GiB | **58.5%** | ~6.8 GiB |
| **4/10** | ~14.0 GiB | **53.8%** | ~9.7 GiB |
| **4/11** | ~13.8 GiB | **54.3%** | ~9.6 GiB |
| **4/12** | ~13.7 GiB | **54.8%** | ~9.4 GiB |
| **4/13** | ~13.7 GiB | **54.9%** | ~9.6 GiB |

**觀察**：
- 新服務上線後（4/8→4/9）used 從 ~50% 跳到 ~58-60%，增加約 2.5 GiB
- 4/10 之後趨於穩定，大約都在 **54-55%（~13.7 GiB）**，有約 **9-10 GiB free**

整體來說 **RAM 沒有超過負荷**，平均使用率健康。


```
Mem:  31Gi total  |  17Gi used  |  9.6Gi free  |  4.4Gi buff/cache
Swap: 4.0Gi total |  3.9Gi used |  142Mi free   ← Swap 幾乎用滿！
```

**各容器記憶體**：

| Container | CPU | MEM |
|-----------|-----|-----|
| `db` (Elasticsearch) | 29.7% | 15.6 GiB |
| `site-en` | **13.4%** | **1020 MiB** ← 接近警戒線 |
| `api` | 4.1% | 790 MiB |
| `site-ja` | 0.7% | 555 MiB |
| `line-bot-zh` | 1.3% | 293 MiB |


**⚠️ Swap 幾乎打滿（3.9G / 4G）**。追溯 `sar -r` 可以看到 4/9 開始 used 增加了約 2GB（新服務加入），目前系統仍穩定運行，但 swap 壓力大。`site-en` 也已接近 1GB 警戒線。

---

### ☁️ Cloud Run 降載分析

#### site-en / site-ja 請求量（轉移至 GCE 後急降）

| 日期 | site-en | site-ja |
|------|---------|---------|
| 4/6 | ~78k | ~41k |
| 4/7 | ~67k | ~36k |
| **4/8** | **~28k** ↓ | **~22k** ↓ |
| 4/9+ | **0** ✅ | **0** ✅ |

4/8 開始在 GCE 上線，流量已大幅移走。4/9 之後 Cloud Run 的 site-en / site-ja **完全沒有新請求**，降載成功。

#### Cloud Run instance count（確認縮容）

| 日期 | site-en max instances | site-ja max instances |
|------|----|----|
| 4/7 | 5 | 5 |
| 4/8 | 7（轉移當天短暫高峰） | 5 |
| 4/9 | 5（殘留一些） | 5 |
| 4/10+ | **資料無（已縮到 0）** ✅ | **資料無** ✅ |

---

### 🔥 需要立即處理的問題

**Swap 幾乎用滿 (3.9G / 4G)**。建議：

```bash
# 重啟 site-en（目前最吃記憶體的非 ES 服務）
gcloud compute ssh cofacts-prod --tunnel-through-iap \
  --command="cd /srv/rumors-deploy && docker compose restart site-en"
```

或者如果重啟後仍然偏高，考慮重啟整台機器讓 swap 清空：

```bash
gcloud compute instances reset cofacts-prod --zone=asia-east1-b --project=industrious-eye-145611
```

:::

### Elasticsearch 升級
- [x] 找一個離峰時間重開 GCE --> reset Swap ＆ apply Ubuntu kernel
- [x] 確認 weekly backup 有正常運作

		✅ Production ES v9 的每週備份有在正常運作。

		排程方式：cron job，每週日 00:20 執行
		機制：透過 docker compose exec 進入 ES v9 container 直接呼叫 _snapshot API，以當天日期（ISO 8601 格式）作為 snapshot 名稱
		儲存位置：GCS bucket cofacts-db-snapshots，base_path v9
		執行紀錄：
		2026-04-05（週日）— ✅ SUCCESS
		2026-04-12（週日）— ✅ SUCCESS
		連續兩週都有成功執行，備份機制運作正常。

- [ ] 修正 weekly opendata publish https://github.com/cofacts/opendata/pull/32
	:::info
	nonumpa 會協助
	:::

## 查核小聚

> 小松果：https://g0v.hackmd.io/@mrorz/BkvGFidhZg?type=view

- 延長線很重 [name=bil]
- 延長線拉在兩列桌子中間很不錯
	- 新排法 https://docs.google.com/drawings/d/1alkhSEp45u_izIo901cYB1_7a7Hw5PK45s_jfVk4l-M/edit <img src="https://docs.google.com/drawings/d/e/2PACX-1vTy2yIiGPlGEHt7Lx53u0_Ai8We0xNQpNMeMrOKJgIC1BB5Ef5J8isCDLxM4oOMUGSnoLKexNOGsSvI/pub?w=943&amp;h=652">
- New Taipei 不怎麼樣，樓下也沒活動，人數也沒有很多
	- 還是需要自架網路
	- 手機分享網路到沒電（3:45 左右沒電）
		- MrOrz 5G 36GB 流量用光
- 傳單錯字：LLM 那張左下角有個錯字


## 上週訊息彙總

以下是從 2026/4/7 上次會議後，到目前為止的 Discord 各頻道摘要：

### General Channel

- **mrorz**:
  > 今日議程
  > https://g0v.hackmd.io/@cofacts/meetings/%2FhE2gBMkYSyOEbrzoGsEqvg
- **Alfred chen**:
  > 不是 這應該沒重要到上紀錄吧😅

### Server Alerts

- `api.cofacts.tw` 與 `line-bot.cofacts.tw` 在 4/8 發生服務中斷，`mrorz` 表示此為重啟 server 清空 swap 所致。

### GitHub Activities

- **cofacts/takedowns**
  - Takedown spam user 51fans (PR #293) - Merged
    - Link: https://github.com/cofacts/takedowns/pull/293
  - Takedown spam user Bini Angelo (PR #292) - Merged
    - Link: https://github.com/cofacts/takedowns/pull/292

- **cofacts/devops**
  - docs(gce): document site-en, site-ja, cofacts.ai and manual deployment (PR #4) - Merged
    - Link: https://github.com/cofacts/devops/pull/4

- **cofacts/rumors-deploy**
  - feat: add cofacts-ai services and adk env template to sample compose (PR #41) - Open
    - Link: https://github.com/cofacts/rumors-deploy/pull/41
  - chore: modernize docker-compose with  healthchecks (PR #42) - Open
    - Link: https://github.com/cofacts/rumors-deploy/pull/42
    - 由於實際狀況會紀錄在非公開 devops repo，rumors-deploy 就能大幅簡化
  - [Infra] 提升 url-resolver 服務穩定性 (Issue #34) - Commented
    - Link: https://github.com/cofacts/rumors-deploy/issues/34

- **cofacts/rumors-site**
  - ci: skip Cloud Run deployment for production en/ja locales (PR #623) - Open
    - Link: https://github.com/cofacts/rumors-site/pull/623
  - Upgrade Hocuspocus provider v3 and yjs ecosystem (PR #622) - Merged
    - Link: https://github.com/cofacts/rumors-site/pull/622
  - New release: release/20260409
    - Link: https://github.com/cofacts/rumors-site/releases/tag/release/20260409

- **cofacts/collab-server**
  - Upgrade hocuspocus v3, Elasticsearch client v9, and related dependencies (PR #9) - Merged
    - Link: https://github.com/cofacts/collab-server/pull/9
  - New release: release/20260409
    - Link: https://github.com/cofacts/collab-server/releases/tag/release/20260409

## Cofacts.ai 

過進度：https://github.com/orgs/cofacts/projects/12/views/1

## Discord spammer
> discord general --> slack

需要把 Discord 進入門檻拉高一點（提問 etc）

- 說不定可以用 MCP 和 AI 一起想辦法

:::info
nonumpa 會看
:::

## 開會時間

- 5 月初會暫停一次開會 for RightsCon
- 5/23, 24 g0v summit 擺攤

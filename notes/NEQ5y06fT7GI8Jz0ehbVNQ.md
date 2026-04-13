---
tags: cofacts,
---

# 20260414 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 追蹤事項

### GCE Migration

- [ ] 可以開始把 en, ja 搬到 GCE 上 --> estimated cost save = 70USD/mo
	- Done on 2026/4/8
- [ ] 跑幾週看穩定度，決定是否要再把 tw site 也搬進 GCE
- [ ] 跑幾個月看實際用到的運算量，決定 GCP committed use discount 怎麼買比較划算
- [ ] Cloudflare HTML cache and AI crawler defense
	- 這個觀察 traffic 再來進行也不遲
- [x] Linode rsync 備份 + 刪 instance
	- rsync: 4/12 已備份在 macbook pro (僅設定檔如 env files & cronjobs)
	- 4/14 已刪除 Linode instance

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


## 查核小聚

> 小松果：https://g0v.hackmd.io/@mrorz/BkvGFidhZg?type=view

好的，這就為您準備 4/14 的會議。

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
  - chore: modernize docker-compose with profiles and healthchecks (PR #40) - Open
    - Link: https://github.com/cofacts/rumors-deploy/pull/40
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


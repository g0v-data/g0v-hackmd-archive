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
	- Done on 2026/4/OO
- [ ] 跑幾週看穩定度，決定是否要再把 tw site 也搬進 GCE
- [ ] 跑幾個月看實際用到的運算量，決定 GCP committed use discount 怎麼買比較划算
- [ ] Cloudflare HTML cache and AI crawler defense
- [ ] Linode rsync 備份 + 刪 instance

### Elasticsearch 升級
- [ ] 找一個離峰時間重開 GCE --> reset Swap ＆ apply Ubuntu kernel
- [ ] 確認 weekly backup 有正常運作、修正 weekly opendata publish https://github.com/cofacts/opendata/pull/32

## 查核小聚

> 小松果：https://g0v.hackmd.io/@mrorz/BkvGFidhZg?type=view

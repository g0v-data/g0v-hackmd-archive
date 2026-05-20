---
tags: cofacts,
---

# 20260522 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 上週待辦

### GCE Migration
- [ ] 跑幾週看穩定度，決定是否要再把 tw site 也搬進 GCE
- [ ] 跑幾個月看實際用到的運算量，決定 GCP committed use discount 怎麼買比較划算

### rumors-api tickets
- [ ] 移除 Twitter 登入功能

### g0v summit
- [ ] X 型布幕
- [ ] mrorz, bil: 名片
- [ ] mrorz: 貼紙
- [ ] mrorz: acho 黃色傳單 (中文)，確認 QR code
- [ ] mrorz: 摺頁 demo (BOT QR Code)
- [ ] QR code 板板、Cofacts 板板
- [ ] 外接螢幕：cofacts Youtube + about page

### 主機維運
- [ ] （高優先）清除 Swap：在離峰時段執行 `swapoff -a && swapon -a`，確認 Swap 能正常回收。若無法清除，需排查是否有 memory leak。
- [ ] （中優先）site-tw 記憶體：容器持續在 1 GB 邊緣，建議評估是否需調高 Cloud Run memory limit 或優化 SSR 記憶體用量。
- [ ] （持續追蹤）Cloudflare One token 導入：作為防火牆誤擋的根本解法，取代 Bot Fight Mode 作為 API 存取控制。

## 

## 下次開會

---
tags: cofacts
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

## g0v summit

60cmx180cm 長桌（同 sitcon）、兩張椅子、一組排插

![](https://g0v.hackmd.io/_uploads/rye-r5ds1zl.png)

（那個藍色的牌子會一直掉，可能還是要用個無痕膠帶）

> SITCON 擺攤檢討 https://g0v.hackmd.io/@cofacts/meetings/%2FAvpmwuvvSGaWgHLf3sITdg#SITCON-%E5%AD%B8%E7%94%9F%E8%A8%88%E7%AE%97%E6%A9%9F%E5%B9%B4%E6%9C%83%E6%93%BA%E6%94%A4%E6%AA%A2%E8%A8%8E

- 5/23 8:30 開始場佈，9:30 ~ 17:00 擺攤
- 5/24 9:30 ~ 16:30 擺攤，隨後撤場

---

- [ ] X 型布幕
- [ ] mrorz, bil: 名片
- [ ] mrorz: acho 黃色傳單 (中文)、群組漫畫傳單
- [ ] mrorz: 摺頁 demo (BOT QR Code)
- [ ] mrorz: 立板、手板
  - 還有青年促參計劃嗎？
- [x] mrorz: 喉糖、桌布、黏土、貼紙
- [ ] QR code 板板、Cofacts 板板
- [ ] 外接螢幕：cofacts Youtube + about page

## 主機維運
- [ ] （高優先）清除 Swap：在離峰時段執行 `swapoff -a && swapon -a`，確認 Swap 能正常回收。若無法清除，需排查是否有 memory leak。
- [ ] （中優先）site-tw 記憶體：容器持續在 1 GB 邊緣，建議評估是否需調高 Cloud Run memory limit 或優化 SSR 記憶體用量。
- [ ] （持續追蹤）Cloudflare One token 導入：作為防火牆誤擋的根本解法，取代 Bot Fight Mode 作為 API 存取控制。

## Kaggle

## 小聚籌備

TBA

## 下次開會

- 回到週二？


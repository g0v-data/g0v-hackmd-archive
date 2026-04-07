# 20260407 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 💬 Discord 上聊了什麼？

### general

- **mrorz@g0v-tw**
  > 上面這個 15 天前的訊息，紀錄了我們從 COS 轉 ubuntu 的心境轉折
- **Alfred chen@g0v-tw**
  > 我們不是ubuntu嗎？

### server-alerts
- `line-bot.cofacts.tw` 在 `2026-03-31 20:05:25 +0000 UTC` 回報為 Unhealthy，原因是 `Response code mismatch error`。

## 💻 Github 上發生了什麼？

- **cofacts/takedowns**
  - [Add privacy removal report for message in database #291](https://github.com/cofacts/takedowns/pull/291)
    - MrOrz 開了 PR，希望能移除包含家庭隱私資訊的訊息。
  - [Takedown spam user 日本外送茶TG：yy9882 YMwgWJ0BZgZZYBoadwoP #290](https://github.com/cofacts/takedowns/pull/290)
    - nonumpa 關閉了這個 PR。
- **cofacts/ai**
  - [design: Cofacts design system component library #22](https://github.com/cofacts/ai/pull/22)
    - MrOrz 開了 PR，新增了 Cofacts design system component library。


## :mag: 本週確認事項

### GCE Migration
- Cost review
- Cloudflare HTML cache and AI crawler defense

### Elasticsearch 升級
- Production cutover status

### Cofacts.ai 開發
- Progress update: https://github.com/orgs/cofacts/projects/12
- Hybrid search: https://docs.google.com/document/d/1sZ4jOsrZPvbJv4QjlMxgbqFsh_pTZNBRs-NbG-HU0rM/edit?tab=t.lhafy6bbdc9p
    - 例子：AI 假海嘯影片 https://cofacts.tw/article/6w6rYJgBngzKCCgMrohC
    - 例子：鳥喝水暴斃 https://cofacts.tw/article/Ar4e2pgB6nor6FKt1vXc

### 小聚籌備
- Event review and follow-up

## API access

verify1st.tw / https://github.com/topben/cryptotruth/pull/50

Product
- 主要是用 LLM 生成防詐文案
- Cofacts 用來作為 Crowd-source evidence，會交給 LLM 生成最後訊息

Concerns
- 源頭活水：希望流量數字可以收得到、feedback 收得到
- 不要有 extra effort for us

https://github.com/cofacts/opendata/blob/master/LEGAL.md

- 不在 LINE 所以給 LIFF URL 沒有太大幫助
- 
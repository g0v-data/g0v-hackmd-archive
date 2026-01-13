# 20260113 會議記錄

:::info
- [所有會議記錄](httpss://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## :eyes: 上次會議跟進事項

- [ ] Devops manual: Update README.md
- [ ] Devops manual: Create AGENTS.md
- [ ] Devops manual: Add Github Claude workflow

## 專案進度與討論摘要

## 小聚籌備

- 2026/02/08 14:00-17:00 青職基地二樓借好了 [name=bil++]
## Server Alerts
- `api.cofacts.tw` and `line-bot.cofacts.tw` 在 1/7 和 1/9 皆有數次不穩的狀況。
- 1/9：
    ![](https://g0v.hackmd.io/_uploads/H1eMSZDXBbe.png) ![](https://g0v.hackmd.io/_uploads/BJlYSZvXSbl.png)
    > 看起來仍然是 url-resolver 使用太多 RAM 使系統 RAM 超過臨界
    > SSH 進去重開 url resolver 之後狀況解除
    > 工程方向仍是把 url-resolver 搬出去

### GitHub
- [cofacts/takedowns] Privacy takedown notice 新增與關閉
  - [Add 2024/07/22 privacy takedown notice](https://github.com/cofacts/takedowns/pull/279)
- [cofacts/rumors-deploy]
  - [Use env_file instead of environment in docker-compose files](https://github.com/cofacts/rumors-deploy/issues/37)
  - [Move all environment variables to dedicated env files](https://github.com/cofacts/rumors-deploy/pull/38)


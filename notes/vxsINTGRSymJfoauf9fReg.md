# 20251021 會議記錄

:::info
- [所有會議記錄](https://gov.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, mrorz, geopeper, Justin, Joe, Yuyu
- 線上出席：nonumpa, helen
- https://meet.google.com/mrz-dgrd-pri
:::

## 上次會議待追蹤項目

- **Cloud Run Migation**: error rate & cost estimation update.
- **Takedown request**: 確認文章 (https://cofacts.tw/article/2fS7y4oBAjOeMOkl_Ljg) 是否已下架。
- **小聚籌備**:
    - [ ] 食物
    - [ ] (bil) 攜帶貼紙、杯子
    - [ ] 發送行前通知 (含德國之聲記者採訪一事)
- **[Johnson]** 資訊安全權限設定
- **CCPRIP - Analytics**: Opendata trend & LINE Bot usage 報表問題
- **[nonumpa, mrorz]** LLM based Topic Classifier: 追蹤 bug 修復與 benchmark 結果
- **[mrorz]** `cofacts/devops-manual` 撰寫進度。
- **[mrorz]** 新 URL resolver 設計文件進度 (https://github.com/cofacts/worker/issues/2)。
- **cofacts.ai**: Groundness Check agent 實作 (追蹤提案與文件)
- **[mrorz]** cAdvisor 研究與安裝

### Langfuse 停止運作 & 升級
- **mrorz@g0v-tw** 發現 Langfuse 自 10/2 起就沒有收到 rumors-api 和 takedown 的資料，原因是 langfuse-worker 和 redis 的連線斷開了。

> **mrorz@g0v-tw**:
> Cofacts 的 Langfuse 在 10/2 之後就收不到東西了 QQ
> rumors-api 和 takedown 都是，我還沒想到為啥

> **mrorz@g0v-tw**:
> 查了一下，10/2 開始 langfuse-worker 和 redis 的連線斷開了
> 應該是這個緣故

Mitigation: redis 增加 restart: always

----

Langfuse 從 3.66 升級到 3.119
- UI 在 evaluation 有不少新功能

## 服務穩定性 (Server Alerts)

- **Cloudflare** 持續回報 `cofacts.tw` 和 `api.cofacts.tw` 服務不穩定，出現多起 HTTP timeout 和 5xx 錯誤。
- 頻率：10/19 一日 12 次，其他日子一天 1~3 次

## 開發與程式碼庫活動 (GitHub Activities)

### 處理詐騙與垃圾訊息
- 持續進行垃圾訊息與詐騙使用者的下架作業，相關 pull requests 皆已完成。
  - [Add 2025/10/16 financial scam report detailing removal of fraudulent image](https://github.com/cofacts/takedowns/pull/270)
  - [Takedown spam user 優質外約+gleezy：k66099 C14Yp5cBfs35m9MiCypf](https://github.com/cofacts/takedowns/pull/272)
  - [Takedown spam user 五益 5cBJ8pkBWwAUNc5b-3gz](https://github.com/cofacts/takedowns/pull/271)
  - [Create 1014-privacy.md](https://github.com/cofacts/takedowns/pull/269)
  - [Takedown spam user Lei Meng lbEh4ZkBFga8s_Raiu76](https://github.com/cofacts/takedowns/pull/268)

### URL Resolver 效能問題
- `rumors-api` 的 [追蹤 URL Resolver 效能問題與重構](https://github.com/cofacts/rumors-api/issues/373) 已關閉，後續將由 [worker repo](https://github.com/cofacts/worker/issues/2) 的新計畫取代。


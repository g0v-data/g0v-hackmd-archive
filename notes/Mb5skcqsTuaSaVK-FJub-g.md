# <i>1014</i> Downtime 原因分析、網站上 Cloud Run、下架文章、小聚籌備

:::info
- [所有會議記錄](https://gov.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, mrorz, nonumpa, geopeper, Justin, Joe, Yuyu
- https://meet.google.com/mrz-dgrd-pri
:::

## 上次會議待追蹤項目

No Updates
*   **[Johnson]** 資訊安全權限設定
*   **CCPRIP - Analytics**: Opendata trend & LINE Bot usage 報表問題
*   **[nonumpa, mrorz]** LLM based Topic Classifier: 追蹤 bug 修復與 benchmark 結果
*   **[mrorz]** `cofacts/devops-manual` 撰寫進度。
*   **[mrorz]** 新 URL resolver 設計文件進度 (https://github.com/cofacts/worker/issues/2)。
*   **cofacts.ai**: Groundness Check agent 實作 (追蹤提案與文件)
    *   ADK <> Langfuse 應該先做 https://github.com/cofacts/beta-ai/issues/6
*   **[mrorz]** cAdvisor 研究與安裝

## Downtime
- **Downtime incidents**: 多使用者回報 `api.cofacts.tw` 出現 bad gateway，以及 server load 過高的問題。
- 10/13 18:41 downtime **根本原因**:
  - mrorz: "卡在老問題：kswapd"
  - mrorz: "rumors-site 用太多 RAM" ![](https://g0v.hackmd.io/_uploads/Hk_xp3jaex.png)
  - ronnywang 推測："有很多 AI 爬蟲都可以用數百數千個 IP 一起抓"
  - Cloudflare 可以擋 AI [name=nonumpa]
    - 找不到確切的狀況，nginx 拿掉之後 request log 要在 cloudflare 上看
    - API (GraphQL) log 留在 GCP
- **臨時解決方案**:
  - mrorz: "網站重啟後恢復"
- **目前架構**:
  - 原本路由是 cofacts.tw & api.cofacts.tw & line-bot.cofacts.tw --> cloudflare proxy --> cloudflare tunnel --> docker container (host machine: linode)
  - 現在只剩下 api.cofacts.tw & line-bot.cofacts.tw 走上面
  - cofacts.tw --> cloudflare proxyh --> Google Frontend (CloudRun) （見下）

## CCPRIP

### [Infra] Migrate to Cloudrun

> Ref: https://g0v.hackmd.io/BRsJOevWSbyUMBSZEVVWrA?view#Phase-1-rumors-site-amp-rumors-line-bot-%E4%B8%8A-Google-cloud-run
> 20240603 預測 tw site cost ~= 78USD/mo - https://g0v.hackmd.io/fj-DahVuTDKZSsqF6dy8Rg#Infra-Migrate-to-Cloudrun
>

- 2025/10/14 3am~4am 搬移 cofacts.tw 到 cloudrun
- 在 cloudflare 上打了[洞](https://old.reddit.com/r/googlecloud/comments/kvj2ss/cloud_run_custom_domain_with_cloudflare/lhg8gl0/)
- Cloud Run cost increase ![](https://g0v.hackmd.io/_uploads/r15_ziopxg.png)

:::info
下週更新數字
- error rate
- cost estimation
:::

## 來信

- https://cofacts.tw/article/2fS7y4oBAjOeMOkl_Ljg
- 參考 https://github.com/cofacts/takedowns/blob/master/2024/0318-investment.md
- 只有一篇而已 [name=mrorz]

:::info
協助拿掉
:::

## 小聚籌備

10/26 (日) 2pm - 5 pm 

---

- [ ] 食物：
- [x] 場地：小樹屋 紅豆杉 201
- [x] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Slido 暖身
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 4:50 介紹分類、RSS、合照
        - 4:50 - 5:00 場復、離開
- [x] 投放目標：
  - 推播日：10/8
  - 目標：北北基桃
- [x] KKTIX: https://cofacts.kktix.cc/events/cofactseditor49
- [x] 誰會來呢： bil, mrorz, nonumpa, geopeper, Justin, Joe, Helen
- [ ] 記得帶：貼紙、不太環保杯 (bil)
- [x] LINE richmenu
- [x] LINE 文案：(copy-pasted)
- [ ] ~~VOOM 發文~~
- [ ] ~~FB 發文~~
- [ ] 行前通知要提德國之聲記者可能會採訪，會要求其尊重意願

:::info
- 小樹屋重訂 13:00 ~ 17:00
:::



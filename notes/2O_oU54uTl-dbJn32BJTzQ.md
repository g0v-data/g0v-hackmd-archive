# 20251125 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 上次會議
*   **[Johnson]** 資訊安全權限設定
*   **[CCPRIP - Analytics]** Opendata trend & LINE Bot usage 報表問題
*   **[nonumpa, mrorz]** LLM based Topic Classifier: 追蹤 bug 修復與 benchmark 結果
*   **[mrorz]** `cofacts/devops-manual` 撰寫進度。
*   **[mrorz]** 新 URL resolver 設計文件進度 (https://github.com/cofacts/worker/issues/2)。
*   **[mrorz]** cAdvisor 研究與安裝
*   **[cofacts.ai]** Groundness Check agent 實作
*   **[Infra]** ElasticSearch v9 reindex 研究 [name=nonumpa]
*   **[cofacts/worker]** url-resolver & 分類器實作路徑
*   **11/23 大松籌備**
*   **12/06 人權市集**
*   **12/07 小聚籌備**

### 🗓️  自 2025-11-18 以來的重點事件

#### 🌐 綜合討論 (General Channel) & 🚨 伺服器狀態 (Server Alerts)

*   **網站服務中斷**
    *   自 11 月 19 日以來，`cofacts.tw` 服務頻繁出現不穩，Cloudflare 多次發出超時或 5xx 錯誤的警報。
    *   11 月 23 日，mrorz@g0v-tw 回報：「現在倒站，loading 飆到 15 但我看不出為啥」。

#### 🛠️ GitHub 活動 (Github Activities)

*   **rumors-site (前端網站)**
    *   **[新功能]** `lancatlin` 提出了 PR **#614**，旨在增加「移除讚/倒讚」的功能。([link](https://github.com/cofacts/rumors-site/pull/614))
    *   **[環境升級]** `lancatlin` 提交的 PR **#613** 已合併，將 Node.js 版本升級至 24。([link](https://github.com/cofacts/rumors-site/pull/613))
    *   **[錯誤修復]** `lancatlin` 提交的 PR **#612** 已合併，此 PR 修復了議題 **#603**「行動版 Replies list 頭像右側空間過大」的問題。([link](https://github.com/cofacts/rumors-site/pull/612))

*   **worker (背景任務)**
    *   `MrOrz` 在議題 **#2** 留言，補充了關於混合式 URL resolver 的執行細節，將包含 url-resolver 和 classifier 的實作。([link](https://github.com/cofacts/worker/issues/2#issuecomment-3546449944))

*   **takedowns (下架處理)**
    *   啟動了對多位騷擾訊息用户的下架程序，如 PR **#276**。([link](https://github.com/cofacts/takedowns/pull/276))

## :potable_water: Release pipeline

### :rocket: Staging

#### :globe_with_meridians: Site

lancatlin++
- Avatar right margin on mobile https://github.com/cofacts/rumors-site/pull/612
- Upgrade nodejs to 24 https://github.com/cofacts/rumors-site/pull/613
- Able to remove reply feedback vote https://github.com/cofacts/rumors-site/pull/614

##### Testing checklist

https://dev.cofacts.tw (手機版＆桌面版)

登入前檢測
- [ ] 手機檢視有回應過的訊息 --> 回應頭像與旁邊的使用者名稱等資訊有合適的間距
- [ ] 桌機檢視有回應過的訊息 --> 回應頭像與旁邊的使用者名稱等資訊有合適的間距

登入後檢測
- [ ] 按讚或倒讚後，再按一下可以收回
    - comment 會被消掉

## 大松檢討
> https://g0v.hackmd.io/YfGHcY92TtWEC_dXCN6QhQ?view

## 小聚籌備

12/07 (日) 2pm - 5 pm 
- OK: bil, mrorz, nonumpa
- 辦在青職基地，已經確認借好
- [ ] 食物：沒有
- [x] 場地：新北市青年局青職基地
- [ ] 時間：13:00 擺桌子場佈
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
        - 4:40 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：
  - 推播日：12/07（11/21 或是 11/25 設定）
  - 目標：雙北
- [ ] KKTIX: https://cofacts.kktix.cc/events/cofactseditor50
- [ ] 誰會來呢： 
- [ ] 記得帶：貼紙、不太環保杯 (bil)
- [ ] LINE 文案： Youtube 上有很多白袍醫師面對鏡頭講話的影片，但其實都是假的，他們都是生成式ＡＩ做出來的假人跟假內容。讓我們一起保護家人，Cofacts 真的假的 第 50 次志工查核工作坊需要你的加入，活動完全免費，（請自備電腦）12/07(日)下午，地點青職基地，最近的捷運站是捷運板橋站1號出口，結束後還可以去歡樂耶誕城！！連結內報名：https://cofacts.kktix.cc/events/cofactseditor50
- [ ] VOOM 發文
- [ ] FB 發文

## CCPRIP


### [Infra] ElasticSearch v9 reindex 研究 

試著 v6 直接 reindex 到 v9，除了 OOM 外目前還沒看到其他問題
- v9 container 至少要配置 2g
- v6 container 可能要配置 2g 以上，分次轉換可能可以解決 OOM 問題

TODOs
- 檢查轉換完之後有沒有什麼格式不相容的問題
- 檢查 api, db 要不要改 code

migration 計畫
- Option 1: (downtime 較長) production 直接 v9 載入預先轉換完的 snapshot，剩下的資料再用 reindex 補回來
- Option 2: (downtime 較短) 直接在另一台機器起一個 v9，用換 ip/domain 的方式切換

### url-resolver & classifier


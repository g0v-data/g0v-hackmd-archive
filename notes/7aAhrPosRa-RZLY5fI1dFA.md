# 20250930 會議記錄

:::info
- [所有會議記錄](https://gov.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, Helen, MrOrz
- 線上出席：nonumpa
- https://meet.google.com/mrz-dgrd-pri
:::

## 上次會議待追蹤項目

### No Updates
*   **[Johnson]** 資訊安全權限設定
*   **CCPRIP - Analytics**: Opendata trend & LINE Bot usage 報表問題
*   **cofacts.ai**: Groundness Check agent 實作 (追蹤提案與文件)
*   **[nonumpa, mrorz]** LLM based Topic Classifier: 追蹤 bug 修復與 benchmark 結果
*   **[mrorz]** 撰寫混合式 URL resolver 的設計文件 (Ref: [worker#2](https://github.com/cofacts/worker/issues/2))。


### Updates
*   **[mrorz]** 著手進行 `cofacts/devops-manual` 的撰寫。
    *   現在 cofacts production & staging 的所有服務 HTTP request 都是透過 cloudflare tunnel 來 dispatch
    *   Cloudflare tunnel 設定完畢，之後要弄新服務的 routing 也都應該在 cloudflare 做
    *   已經 spin down production & staging 的 nginx
        *   production: 台灣時間 2025-09-28 11:32
        *   staging: 台灣時間 2025-09-30 18:45 左右
    *   TODO: 改 env-file https://github.com/cofacts/rumors-deploy/issues/37
*   **[bil]** 準備十月小聚，預定小樹屋。
    *   巒大杉 101 不能預定
    *   小樹屋後續追蹤：
        > 有幾間確實因為內部調整無法租用，但也可能之後忽然開通，小樹屋不願回應具體時程。如果有急用建議先找其他空間，但確實是沒有人租的。
*   **[mrorz]** url-resolver 從每日 4am 重啟 --> 每小時 5 分時重啟
*   **[bil]** 團購網法律信件，由 bil 寫初版

## 小聚籌備

10/26 (日) 2pm - 5 pm 
- 辦在小樹屋或是 艋舺龍山寺 (板橋文化廣場大樓) 603/604 同格局，坐滿 30 人 https://spshfu.tw/rent/ 4500元三小時 (超時每半小時 500 元) 有 wifi 無線麥克風、投影機、HDMI， mac 請自備轉接頭 地址：新北市板橋區文化路二段242號6樓（ 龍山寺文化廣場）
捷運： #江子翠捷運站 3 號出口，往新埔方向步行約 2分鐘

小樹屋｜合歡 B303
捷運台北車站 5 分鐘
臺北市中正區忠孝西路一段50號 B3樓-B303房
合歡分館位於台北車站Z區地下街 Z2 出口日藥本舖旁邊
- [ ] 食物：
- [ ] 場地：
- [ ] 時間：
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
  - 推播日：
  - 目標：雙北
- [ ] KKTIX: 
- [ ] 誰會來呢： 
- [ ] 記得帶：貼紙、不太環保杯 (bil)
- [ ] LINE 文案：
- [ ] VOOM 發文
- [ ] FB 發文

## Downtime

## Takedowns

## Communications

- RightsCon: The Investigator, the Verifier, and the Proofreader: Fighting Disinfo with a Multi-Agent AI Crew
- 採訪？

## 10 月開會時間




# 20260120 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, nonumpa, mroprz
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## :eyes: 上次會議跟進事項

- [ ] Devops manual: Add Github Claude workflow
- [ ] 將 url-resolver 搬離主機

## 🗓️ 2026/01/13 - 2026/01/20
### #general
- **Production 環境伺服器記憶體耗盡事件 (2026-01-16)**
  - `mrorz` 回報在 1/16 早上 9:35 - 9:45 發生 production server記憶體(16GB)與Swap(4GB)被 Elasticsearch process 佔滿，導致 OOM killer 把 Elasticsearch process 砍掉。`url-resolver` 在手動重啟後恢復正常。
![](https://g0v.hackmd.io/_uploads/H11SGlTB-g.png)

- **OCR 功能異常與修復 (2026-01-18)**
  - `mrorz` 提到 OCR 功能從 2026/1/1 開始壞掉，導致圖片和影片沒有逐字稿，影響比對功能。
    > mrorz@g0v-tw: 1 月初開始，圖片和影片全都沒有逐字稿，這樣比對功能應該是壞的 ![](https://g0v.hackmd.io/_uploads/rJk6Geprbx.png)
  - 問題已在 1/18 17:42 修復，原因是 `GCS credential` 的變數名稱不小心改錯。

### #server-alerts
- **服務不穩定警報 (2026-01-16)**
  - 在 1/16 伺服器記憶體耗盡事件期間，`api.cofacts.tw` 和 `line-bot.cofacts.tw` 多次出現 `Unhealthy` 的狀態。

## 💻 GitHub 活動摘要

### cofacts/takedowns
- **Spam 使用者下架**
  - PR #280: [Takedown spam user TG搜@lg5221學生妹 d5XHx5sB9EfTQQdNGq14](https://github.com/cofacts/takedowns/pull/280)
- **隱私下架**
  - PR #281: [Privacy takedown](https://github.com/cofacts/takedowns/pull/281)

### cofacts/rumors-api
- **新增 AI 逐字稿功能**
  - PR #378: [feat: Add admin handler for generating AI transcripts for media articles](https://github.com/cofacts/rumors-api/pull/378)
    - 這個 PR 應該是為了解決 OCR 功能異常期間，沒有產生逐字稿的文章。

### cofacts/devops

- Cloudflare: 紀錄現況
- Analytics: 教 agent 怎麼從 API 與 elasticsearch 撈資料

## :potable_water: Release pipeline

### :rocket: Staging

#### :globe_with_meridians: API

- PR #378: [feat: Add admin handler for generating AI transcripts for media articles](https://github.com/cofacts/rumors-api/pull/378)
- 這個 PR 應該是為了解決 OCR 功能異常期間，沒有產生逐字稿的文章。


## 小聚籌備

- 2026/02/08 14:00-17:00 青職基地二樓借好了 [name=bil++]

02/08 (日) 2pm - 5 pm 
- 誰會來呢: bil, mrorz, nonumpa, alfred
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
  - 推播日：01/21（01/21 或是 01/25 設定）
  - 目標：雙北
- [x] KKTIX: https://cofacts.kktix.cc/events/cofactseditor51
- [ ] 記得帶：貼紙、不太環保杯 (bil)
- [x] LINE 文案：「俄羅斯總統女兒腦腫瘤血破裂，求助台灣女婿向台積電求援，經台積電台大醫院聯手開刀診治救回成功🏆」這是生成式ＡＩ做出來的假內容。動手闢謠，讓我們一起保護家人，Cofacts 真的假的 第 51 次志工查核工作坊需要你的加入，活動完全免費，（請自備電腦）02/08(日)下午，地點青職基地，最近的捷運站是捷運板橋站1號出口。連結內報名：https://cofacts.kktix.cc/events/cofactseditor51
- [ ] VOOM 發文
- [ ] FB 發文

## 韌性

- 電池
    - 可以接哪些電器
    - 市電充電速度
- 太陽能板
    - 是否可以幫電池充電
- Meshtastic
    - 設定 app 與裝置連線
    - 約定通訊頻道與方式
    - 實地測試
## 大松
要去ㄇ？
[高雄](https://g0v.hackmd.io/@jothon/g0v-hackath71n/https%3A%2F%2Fg0v.hackmd.io%2FKvzHayP4SPqXRhtrn2QH0w%3Fview?fbclid=IwY2xjawPcURpleHRuA2FlbQIxMABicmlkETFOcVNhb2I2S1RKS1NudXlUc3J0YwZhcHBfaWQQMjIyMDM5MTc4ODIwMDg5MgABHr-4gghuGYqA7zg5DYG-Xj3AYnA1kT4Cy_Pw6aYfSVjo9B591qnyJ9M4mDgi_aem__j1aTm4stI-a9LgEaya8fg)
01/25 (日) 10:30-17:30

> 結論：留在台北 XD

# 20260127 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, alfred, ed chen, mrorz
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## :eyes: 上次會議跟進事項

- [ ] 將 url-resolver 搬離主機
- [x] 小聚籌備：投放目標、VOOM/FB 發文

## :potable_water: Release pipeline

### :rocket: Production

#### :globe_with_meridians: API

https://github.com/cofacts/rumors-api/releases/tag/release/20260124

## 🗓️ 2026/01/20 - 2026/01/27
- **OCR and Staging Environment (Jan 24)**:
  - `mrorz@g0v-tw` mentioned that the image OCR was not working due to a code error and that the staging environment has been fixed. He also mentioned that he will merge the changes and backfill the transcripts for January.
  > "mrorz@g0v-twTest 又不過了，因為我把 test 改成 integration test 來抓問題 ._.
  > 前幾天我注意到 code 寫錯導致圖片 OCR 根本不會動
  > 然後也修正 staging 上 service account 的權限問題，所以現在 staging 上可以正常作業了
  > 不過變成 unit test 不會動了
  > 我想先 merge 然後在 production 補之前的逐字稿，1 月到上禮拜有些關稅相關的圖應該要做成逐字稿的 orz"
- 831 篇空的逐字稿已經在週六處理完畢

- **Gemini Model Update (Jan 21)**:
  - `mrorz@g0v-tw` noted that a test failed due to an update in the Gemini model and that a fix has been merged.
  > "<https://github.com/cofacts/rumors-api/pull/378> test 過囉，可以 review 了

### Server Alerts

- **Unhealthy Services (Jan 25)**:
  - Several "Unhealthy" alerts for `line-bot.cofacts.tw` and `api.cofacts.tw` with "Response code mismatch error" and "HTTP timeout occurred".

- **Unhealthy Services (Jan 23)**:
  - "Unhealthy" alerts for `line-bot.cofacts.tw` and `api.cofacts.tw` with "Response code mismatch error".

- **Unhealthy Services (Jan 21)**:
  - "Unhealthy" alert for `cofacts.tw` with "Response code mismatch error".

## 韌性

https://g0v.hackmd.io/6fWdUufOTJ6njaEe_vrZJg

- Meshtastic
    - 設定 app 與裝置連線
    - 約定通訊頻道與方式
    - 實地測試

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

## 下週開會

2/4 (三) 嗎
- Change to 2/4 (wed) if bil is not available in Tuesday
- Update: yes, change to 2/4


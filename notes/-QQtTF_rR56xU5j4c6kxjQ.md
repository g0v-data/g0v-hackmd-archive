# 20260127 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## :eyes: 上次會議跟進事項

- [ ] Devops manual: Add Github Claude workflow
- [ ] 將 url-resolver 搬離主機
- [ ] 小聚籌備：投放目標、VOOM/FB 發文

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

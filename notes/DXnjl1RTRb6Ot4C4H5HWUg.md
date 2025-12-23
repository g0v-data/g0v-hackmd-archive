# 20251223 會議記錄

## :eyes: 上次會議跟進事項

*   **[Epic] Elasticsearch Migration**
    *   改 API
    *   驗證資料是否正常
        *   記錄一下 reindex 所需時間
        *   reindex 時 elasticsearch 會用多少記憶體
    *   上 staging
    *   Note: 似乎可以考慮 Elasticsearch: hosted elasticsearch on Google cloud https://www.elastic.co/partners/google-cloud
	- pricing table: https://cloud.elastic.co/cloud-pricing-table?
	- calculator: https://console.qa.cld.elstc.co/pricing/
* GCP cost
    - 持續監控
    - 目前花了 184USD, forecast 280USD (怎麼算的？) ![](https://g0v.hackmd.io/_uploads/BkSHEbdXWl.png)


## 綜合討論 (General)

- **服務穩定性**
  - `mrorz` 觀察到 `GET /graphql` 的異常流量，來源為 AWS 上的 Python 程式。
    > mrorz@g0v-tw: 我不是很明白為啥會有人一直 `GET /graphql`，要做事都是 POST 才對
    > mrorz@g0v-tw: 這個 GET graphql 都是 python 打的，看起來是 AWS

  - 在 2025/12/18，Cofacts 服務短暫中斷後自動重啟。
    > mrorz@g0v-tw: 剛才似乎倒站，但又重開了？
    > mrorz@g0v-tw: 很ㄍㄧㄥ

## 系統警報 (Server Alerts)

**服務不穩定**:
- `api.cofacts.tw` 與 `line-bot.cofacts.tw` 在這週頻繁出現服務不健康的警報，主要問題為 `Response code mismatch error`，收到的 HTTP 狀態碼為 530 或 502，表示服務無法正常回應。

LINE:
![](https://g0v.hackmd.io/_uploads/Hy8CiJ_7We.png)

## 活動

- 12/28 14:00 Cofacts 期末感恩茶會 @ 青職基地

## 開發活動 (Github Activities)

- **[cofacts/rumors-site]**
  - **新版本發布**: MrOrz 發布了 `release/20251216` 版本。
    - [New release published: release/20251216](https://github.com/cofacts/rumors-site/releases/tag/release/20251216)
  - **議題關閉**:
    - [實作 ArticleReplyFeedback 的收回功能 (#611)](https://github.com/cofacts/rumors-site/issues/611)

- **[cofacts/takedowns]**
  - **PR**:
    - MrOrz 提出並關閉了 [新增 2024/05/21 隱私權公告 (#278)](https://github.com/cofacts/takedowns/pull/278)。

- **[cofacts/beta-ai]**
  - **議題與 PR**:
    - MrOrz 開立並透過 PR [Update ADK to 1.21 (#11)](https://github.com/cofacts/beta-ai/pull/11) 解決了 [Update ADK to 1.21 (#10)](https://github.com/cofacts/beta-ai/issues/10)。

## Gemini updates

- 目前是 gemini 2.5 flash w/ thinking budget=0
- [Gemini 3 Flash](https://docs.cloud.google.com/vertex-ai/generative-ai/docs/models/gemini/3-flash) 實驗效果：
	- [Run 1](https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/datasets/cm7ri4we80004ql0bfu6lvtoi/runs/2183dc74-1f73-4215-acdf-8945afcb7742): 
		- 速度和 gemini 2.5 flash 差不多（做完 5 個實驗的平均時間只比多 4 秒）
		- 但那是因為有些測資翻到一半就不翻了
	- [Run 2](https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/datasets/cm7ri4we80004ql0bfu6lvtoi/runs/542acf48-e7e9-47b9-86e8-63568f909640) [修改 prompt](https://github.com/cofacts/rumors-api/compare/gemini-3-flash-exp?expand=1) 後：
	  	- 速度變慢更多。
	  	- 準確度算不錯。
- Gemini 3 flash [比 2.5 flash 貴](https://cloud.google.com/vertex-ai/generative-ai/pricing)。
- 建議不要升級

![](https://g0v.hackmd.io/_uploads/B1IKXl_QZl.png)

:::success
建議繼續使用 Gemini 2.5 Flash
:::

## 下週開會

下週開會是週一 12/29 喲

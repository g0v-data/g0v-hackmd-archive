---
tags: cofacts,
---

# 20250916 會議記錄

:::info
- [所有會議記錄](https://gov.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, Helen, mrorz
- 線上出席：
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
*   **[mrorz]** 準備面海松要用的中文講義、Cofacts 傳單與貼紙。
    *   攜帶的十數張英文講義發光了（家裡還有）
*   **[mrorz]** 著手進行 `cofacts/devops-manual` 的撰寫。
    *   要先把 env-files 移出去才能寫
    *   正在從 staging & production 移除 nginx，用 cloudflare tunnel + DNS 取代
        *   未來會不再有 nginx log，要看網路 log 就上 cloudflare
*   **[mrorz]** 設定 cofacts-api 的 303 redirect。
    >  2025/9/13 1:52pm cofacts.g0v.tw / cofacts-api.g0v.tw 的 request 現在都會轉到 cofacts.tw domain 由 Cloudflare 管理囉
    > https://github.com/g0v/domain/pull/90
*   **[bil]** 準備十月小聚，預定小樹屋。

## 10 月小聚

- 定在 10/26 
- 10/25 同志遊行，避開

地點
- 青職基地滿了
- NPO Hub?
- https://thehapp.com/space/162 本大樓無電梯，須走樓梯上樓且樓梯稍窄。
- https://thehapp.com/space/336
  免費插座 18 個無麥克風 20 個椅子
- https://thehapp.com/space/267 老地方不知道為什麼不可以訂
- 好像還有一間也是 1 樓（北車）但好像消失了

:::success
bil 先問為啥巒大杉 101 不能訂
:::


## 0914 downtime

- **服務不穩定**: 9/14 發生了服務不穩定的狀況，`url-resolver` 負載過高。重啟 `url-resolver` 及 API 後服務恢復正常。
    > nonumpa@g0v-tw: 我 9.18 的時候看 url resolver load 200%，先重啟 url resolver ，發現 api 還是連不上的，再重啟 api，就好了

db 17:26 左右出現 gc 的 log
db 19:49 左右也出現 gc 的 log
db 剛好在 21:17 重啟
https://cloudlogging.app.goo.gl/1WSpg5rRY6ETY9HH9

- 可以監控 container 狀態，但要裝 cadviser 之類
  - gcp 有內建 cadviser 選項
  - 但好像沒有(?) linode 送到 gcp visualize 的選項

### Linode
![](https://g0v.hackmd.io/_uploads/SJICDKEsle.png)

19:10 load 下降
19:32 進伺服器看~~啥都沒有~~ url-resolver 2GB ram
19:40 load 又開始變高

19:32 時的圖表：
![](https://g0v.hackmd.io/_uploads/BkxHq_ALsgl.png)
![](https://g0v.hackmd.io/_uploads/H1c5dCIsle.png)

:::success
url-resolver 從每日 4am 重啟 --> 每小時 5 分時重啟
:::

## GitHub Activities

### [cofacts/beta-ai](https://github.com/cofacts/beta-ai)
- **New Issue**: [[AI] connect to VertexAiSessionService](https://github.com/cofacts/beta-ai/issues/9)
- **Discussion**: [[AI] Notes on Langfuse integration](https://github.com/cofacts/beta-ai/issues/6) - MrOrz initiated a discussion with Claude AI about integrating Langfuse into the ADK project.

### [cofacts/rumors-deploy](https://github.com/cofacts/rumors-deploy)
- **New Pull Request**: [Move all environment variables to dedicated env files](https://github.com/cofacts/rumors-deploy/pull/38) - To improve configuration management.

### [cofacts/takedowns](https://github.com/cofacts/takedowns)
- Several spam users were taken down.

## Communication

### Generative AI 小聚
https://docs.google.com/presentation/d/18NGr_DCACysX_yi3IhqRAIlWZ9uPFpsX4Ju2HGZKNF0/edit

### Legal Email
- https://cofacts.tw/article/2jffeimafoo37
- 已經有回應 [name=mrorz]
  - 從 https://www.gogoma.com.tw/wc-56 看起來好像也跟 Cofacts 訊息不同
- 從反詐騙角度來做提醒
- 搭配訊息看起來，像是有詐騙集團冒用名義
  - 若確實是被冒用，那下架無法改變被冒用的事實
  - 還是會被另一個詐騙受害者傳進來
- 建議保留
- 官方網站 https://www.gogoma.com.tw/ 若有反詐騙公告，可以自行撰寫回應附上該公告，把使用者從詐騙處導向到正確的地方

:::success
bil 寫初版
:::

### RightsCon
本週六下午 4 點最後 deadline

## 下週開會

下週暫停一次


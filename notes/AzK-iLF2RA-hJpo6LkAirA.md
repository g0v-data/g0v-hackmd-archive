---
tags: vtaiwan
---

# 「Sensemaker意見綜整器」使用說明(V3)

##  特色

1. 現在可用LM Studio近端模型，免費執行Sensemaker意見綜整器了!
2. 使用懶人腳本，只要設好參數，一行指令即可完全部流程!

## 簡介

此分支擴充了 Sensemaker，讓使用者能 **LM Studio** 以低成本、高效能、自選模型的方式執行意見綜整器，並可自訂報告輸出的語言。只需執行 `run_local_html_report.sh` 一個腳本，即可從 Polis 匯出資料一鍵產生完整的互動式 HTML 網頁報告。
使用方式及參數設計範例，請見 [run_local_html_report.sh](https://github.com/bestian/sensemaking-tools/blob/new-feature-open-router-ggml/run_local_html_report.sh) 中的註解。



### 當前限制

1. `run_local_html_report.sh`腳本僅支援LM Studio，報告生成速度會隨您的算力機的強度而異。
2. `run_local_html_report.sh`腳本僅支援Pol.is的report base URL。

### 替代方案

1. 可使用`open router`工作流程(腳本研究中...)
2. (Pol.is外其他平台的原始資料，暫不相容)


### 專案源碼

* 開源程式庫：https://github.com/bestian/sensemaking-tools/

* 分叉於此上游專案：https://github.com/Jigsaw-Code/sensemaking-tools/


## 起步


### 1. 安裝 LM Studio

LM Studio 是一套可在本機執行大型語言模型（LLM）的桌面工具，目前提供 **macOS、Windows、Linux** 版本。官方建議先從下載頁面取得對應作業系統的安裝檔，再進行安裝。 ([LM Studio][1])

#### 安裝步驟

1. 前往 LM Studio 官方下載頁。 ([LM Studio][1])
2. 依您的作業系統下載對應版本：

   * **macOS**：下載 `.dmg`
   * **Windows**：下載 `.exe`
   * **Linux**：下載對應安裝包或 AppImage 版本
     這些安裝形式可見於官方下載頁與官方更新說明。 ([LM Studio][1])
3. 執行安裝檔並完成安裝。
4. 第一次開啟 LM Studio 後，即可進入主畫面，後續可在內建的 **Discover** 分頁搜尋並下載模型。 ([LM Studio][2])

#### 基本確認

安裝完成後，建議先確認以下幾點：

* LM Studio 可以正常開啟。
* 您的電腦符合基本硬體需求。
* 之後可在 **Discover** 分頁下載模型，並在 **Chat** 分頁載入模型到記憶體中使用。 ([LM Studio][3])

#### 補充說明

* 若您是一般使用者，安裝 **桌面版 LM Studio** 即可。 ([LM Studio][1])
* 若您是要在**算力機、伺服器、雲端機器或無圖形介面環境**上執行，官方另外提供無 GUI 的 `llmster` 安裝方式：

  * Mac / Linux：

    ```bash
    curl -fsSL https://lmstudio.ai/install.sh | bash
    ```
  * Windows：

    ```powershell
    irm https://lmstudio.ai/install.ps1 | iex
    ```

  這是 LM Studio 官方提供的 headless 安裝方式。 ([LM Studio][1])

#### 下一步

LM Studio 安裝完成後，下一步是：

1. 下載一個可用模型
2. 載入模型
3. 確認本機 API 或聊天功能可正常運作
   如此即可進入後續的 Sensemaker 腳本設定流程。 ([LM Studio][2])


[1]: https://lmstudio.ai/download?utm_source=chatgpt.com "Download LM Studio - Mac, Linux, Windows"
[2]: https://lmstudio.ai/docs/app/basics?utm_source=chatgpt.com "Get started with LM Studio"
[3]: https://lmstudio.ai/docs/app?utm_source=chatgpt.com "Welcome to LM Studio Docs!"


### 2. 找到Pol.is報告的原始資料匯出用的baseURL


(...)

### 3. 設定參數

(...)

### 4. 執行腳本並等待

範例：

```bash

bash ./run_local_html_report.sh \
     --export-base-url "https://pol.is/api/v3/reportExport/r3nhe9auvzhr36dwaytsk" \
     --report-title "分享您對生成式AI的觀點" \
     --report-subtitle "在第二屆「民主高峰會」（Summit4Democracy）之際，集體智慧計畫（Collective Intelligence Project）和唐鳳（Audrey Tang）誠摯邀請您分享並探討您對生成式人工智慧影響的看法。 （資料原始出處：cip.org/s4d (2023)）" \
     --report-question "您的意見和見解非常重要；我們將利用本次對話的成果，為即將開展的一系列關於人工智慧治理的廣泛討論提供參考，這些討論將為人工智慧實驗室和政策制定者的具體決策提供依據。" \
     --additional-context "在第二屆「民主高峰會」（Summit4Democracy）之際，集體智慧計畫（Collective Intelligence Project）和唐鳳（Audrey Tang）誠摯邀請您分享並探討您對生成式人工智慧影響的看法。" \
     --model "qwen/qwen3.6-35b-a3b" \
     --outputLang "zh-TW"

```

### 5. 得到完整的互動網頁(HTML格式)報告

(...)

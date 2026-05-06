---
tags: vtaiwan
---

# 「Sensemaker意見綜整器」使用說明(V3)

## 概說

「[城邦 Polis](https://pol.is/)」是國際審議民主社群常用的意見調查工具，在臺灣也曾用於具爭議性的公共議題中，協助找出各方可接受的罕見共識。例如 Uber-X 進入臺灣時引發的爭議，便透過 vTaiwan 的審議民主程序，促成了各方均可接受的解決方案。

這段歷史可參考：[歷史案例：Uber 爭議透過 vTaiwan 審議民主程序的解決](https://hackmd.io/Os5_JBm_RPiWBnZ8v9EpFQ?view)

然而，當 Polis 蒐集到大量意見與投票資料，且意見內容出現重複、相近或分歧時，若只依靠人工分析，往往不容易有效分類、綜整並找出罕見共識與主要分歧。因此，Google Jigsaw 團隊研發了「意見綜整器 Sensemaker」，用來分析大量意見與投票資料，並產生有意義的綜整報告。

在語言支援方面，原專案一開始僅能產出英文報告。Bestian 的 fork 版本對此做了改良，使程式可以產生正體中文、簡體中文、西班牙文、日文、法文、德文等多語言報告。

在模型運用方面，原專案一開始僅支援 Google Vertex AI 上的 Gemini 模型。Bestian 的 fork 版本進一步改良，使程式可以改用 OpenRouter 上的 gpt-oss-120b 等模型，在維持相近報告品質的同時，將成本降低至原本約 5%。Audrey 則進一步擴充，使 Sensemaker 可以選用 LM Studio 的地端模型來生成報告，不僅可免費執行，對重視資安與資料自主的使用者而言，也是一項重要突破。

目前相關改良正向上游提交中，包括 [PR #38](https://github.com/Jigsaw-Code/sensemaking-tools/pull/38) 與 [PR #54](https://github.com/Jigsaw-Code/sensemaking-tools/pull/54)，Jigsaw 團隊也正在參考與評估這些改動。



## 報告實例

1. https://www.vtaiwan.tw/uber-x-report
2. https://www.alearn.org.tw/report


## 技術說明

此分支擴充了 Sensemaker，讓使用者能透過 **OpenRouter** 或地端 **LM Studio** 以低成本、高效能、自選模型的方式執行意見綜整器，並可自訂報告輸出的語言。提供兩個一鍵腳本，可從 Polis 匯出資料直接產生完整的互動式 HTML 網頁報告：

* **地端 LM Studio：** [`run_local_html_report.sh`](https://github.com/bestian/sensemaking-tools/blob/new-feature-open-router-ggml/run_local_html_report.sh)
* **OpenRouter（雲端）：** [`run_open_router_html_report.sh`](https://github.com/bestian/sensemaking-tools/blob/new-feature-open-router-ggml/run_open_router_html_report.sh)

使用方式及參數設計範例，請見各腳本開頭的註解。


## 專案源碼

* 開源程式庫：https://github.com/bestian/sensemaking-tools/

* 分叉於此上游專案：https://github.com/Jigsaw-Code/sensemaking-tools/

### 相容性

* 此腳本目前唯一支援[pol.is](https://pol.is/)的report base URL。

* 相容於Agora Citizen等其他平台的版本，請見： https://make.vtaiwan.tw

* 舊版使用說明，請見：
    * [V1](https://g0v.hackmd.io/6mzxQkY3Sr6ILYSfSMsqVg)
    * [V2](https://g0v.hackmd.io/vjYMEjYqRmGfYc0hScQkWg)


# 起步

## 一、建立Polis意見徵集


**關於如何建立Polis意見徵集，請見：**
https://make.vtaiwan.tw/guide/polis



## 二、找到Pol.is報告的原始資料匯出用的baseURL


**在Polis的管理後台，找到Reports分頁，可以找到baseURL**

![baseURL截圖](https://g0v.hackmd.io/_uploads/S19mNPORWe.png)




## 三、運用模型來分析

您可選擇：

1. [運用雲端模型](#運用雲端模型)
2. [運用地端模型](#運用地端模型)


## 運用雲端模型

### 1. 申請open router帳號和API KEY

詳細圖文說明，請見：
https://make.vtaiwan.tw/guide/openrouter


取得API KEY後，請見[一鍵產生雲端分析報告](#一鍵產生雲端分析報告)



## 運用地端模型

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
4. 第一次開啟 LM Studio 後，即可進入主畫面，後續可在內建的 **Discover** 分頁搜尋並下載模型。 


#### 補充說明

* 若您是一般使用者，安裝 **桌面版 LM Studio** 即可。 ([LM Studio][1])
* 若您是要在**算力機、伺服器、雲端機器或無圖形介面環境**上執行，官方另外提供命令列(CLI)的安裝方式，請見[LM Studio官網](https://lmstudio.ai/download?utm_source=chatgpt.com "Download LM Studio - Mac, Linux, Windows")

#### 下一步

LM Studio 安裝完成後，下一步是：

1. 下載一個可用模型
2. 載入模型
5. 確認本機 API 或聊天功能可正常運作
4. **將max-content-length盡量調高，以免承受不住**
5. 如此即可進入後續的 Sensemaker 腳本設定流程。 
   


[1]: https://lmstudio.ai/download?utm_source=chatgpt.com "Download LM Studio - Mac, Linux, Windows"

## 一鍵產生地端分析報告


您只需執行腳本並等待一段時間，報告即會自動產生，存入您電腦的目錄中


腳本：

```run_local_html_report.sh```

範例：

```bash

bash ./run_local_html_report.sh \
     --export-base-url "https://pol.is/api/v3/reportExport/r3nhe9auvzhr36dwaytsk" \
     --report-title "分享您對生成式AI的觀點" \
     --report-subtitle "在第二屆「民主高峰會」（Summit4Democracy）之際，集體智慧計畫（Collective Intelligence Project）和唐鳳（Audrey Tang）誠摯邀請您分享並探討您對生成式人工智慧影響的看法。 （資料原始出處：cip.org/s4d (2023)）" \
     --report-question "您的意見和見解非常重要；我們將利用本次對話的成果，為即將開展的一系列關於人工智慧治理的廣泛討論提供參考，這些討論將為人工智慧實驗室和政策制定者的具體決策提供依據。" \
     --additional-context "在第二屆「民主高峰會」（Summit4Democracy）之際，集體智慧計畫（Collective Intelligence Project）和唐鳳（Audrey Tang）誠摯邀請您分享並探討您對生成式人工智慧影響的看法。" \
     --model "nvidia/nemotron-3-super" \
     --outputLang "zh-TW"

```


參數說明：


1. `--outputLang`：報告的輸出語言
2. `--model`：選用的語言模型(對應到您在LM Studio上啟動的模型名稱)


如可得到完整的互動網頁(HTML格式)報告

您可以把報告更名、部署在自己的網站上




## 一鍵產生雲端分析報告

您只需執行腳本並等待一段時間，報告即會自動產生，存入您電腦的目錄中


(接續前面的[三、運用模型來分析](#三、運用模型來分析) 第一選項：運用雲端模型 )


腳本：

`run_open_router_html_report.sh`


範例：

```bash
   bash ./run_open_router_html_report.sh \
     --export-base-url "https://pol.is/api/v3/reportExport/r3nhe9auvzhr36dwaytsk" \
     --report-title "分享您對生成式AI的觀點" \
     --report-subtitle "在第二屆「民主高峰會」（Summit4Democracy）之際，集體智慧計畫（Collective Intelligence Project）和唐鳳（Audrey Tang）誠摯邀請您分享並探討您對生成式人工智慧影響的看法。 （資料原始出處：cip.org/s4d (2023)）" \
     --report-question "您的意見和見解非常重要；我們將利用本次對話的成果，為即將開展的一系列關於人工智慧治理的廣泛討論提供參考，這些討論將為人工智慧實驗室和政策制定者的具體決策提供依據。" \
     --additional-context "在第二屆「民主高峰會」（Summit4Democracy）之際，集體智慧計畫（Collective Intelligence Project）和唐鳳（Audrey Tang）誠摯邀請您分享並探討您對生成式人工智慧影響的看法。" \
     --model "openai/gpt-oss-120b" \
     --open-router-api-key "sk-or-..." \
     --outputLang "zh-TW" \
```
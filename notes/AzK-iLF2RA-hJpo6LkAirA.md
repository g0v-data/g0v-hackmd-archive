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

1. `run_local_html_report.sh`腳本僅支援LM Studio，若您沒有算力機，就無法跑此腳本
2. `run_local_html_report.sh`腳本僅支援Pol.is

### 替代方案

1. 可使用`open router`工作流程(腳本建置中...)
2. (Pol.is外其他平台的原始資料，暫不相容)


### 專案源碼

* 開源程式庫：https://github.com/bestian/sensemaking-tools/

* 分叉於此上游專案：https://github.com/Jigsaw-Code/sensemaking-tools/


## 起步

### 1. 安裝 LM Studio

(...)


### 2. 找到Pol.is報告的原始資料匯出用的baseURL


(...)

### 3. 設定參數

(...)

### 4. 執行腳本並等待

(...)

### 5. 得到完整的互動網頁(HTML格式)報告

(...)

# 🚀 Open Babel GPU 加速引擎：異地開發協作流程

以下是本專案從本地端架構設計到實驗室 GPU 叢集上線的完整開發藍圖。

```mermaid
flowchart TD
    subgraph Dorm ["💻 宿舍環境 - 你的筆電 (大腦與架構區)"]
        direction TB
        P1A["[階段 1：建立基準真相]<br>讀取 dockgen.csv 提取 SMILES"] --> P1B["呼叫原版 Open Babel (CPU)<br>計算 VDW 能量"]
        P1B --> P1C[/"📁 產出 cuda_benchmark_targets.json"/]
        
        P1C --> P2A["[階段 2：資料與介面準備]<br>開發 C++ SoA (Structure of Arrays) 轉換層"]
        P2A --> P2B["建立 FastAPI Mock 節點<br>測試 n8n 自動化流程"]
        
        P2B --> P3["[階段 3：核心邏輯盲寫]<br>使用 AI 輔助，將 VDW for 迴圈轉為<br>CUDA __global__ Kernel 草稿"]
    end

    subgraph Lab ["🖥️ 實驗室環境 - GPU 伺服器 (肌肉與驗證區)"]
        direction TB
        P4A["[階段 4：編譯與驗證閉環]<br>透過 SSH 連線，使用 nvcc 進行編譯"]
        P4B{"執行測試程式<br>比對 JSON 基準答案<br>❌ 誤差 ➔ 讀取 Log 讓 AI 修正<br>✅ 正確 ➔ 進入下一階段"}
        
        P4A --> P4B
        
        P4B --> P5["[階段 5：極限榨取效能]<br>使用 Nsight Compute 進行 Profiling<br>優化 Shared Memory 與 Thread 佔用率"]
        
        P5 --> P6A["[階段 6：系統上線]<br>透過 pybind11 打包成 Python 模組"]
        P6A --> P6B((🚀 替換 n8n Mock 節點<br>正式啟動 Indole 計畫高通量篩選))
    end

    %% 跨環境連線
    P3 -- "傳遞 .cu 程式碼" --> P4A
    P1C -. "帶入實驗室作為解答本" .-> P4B

    %% 樣式設定
    classDef dormBox fill:#f4f6f9,stroke:#5c7cfa,stroke-width:2px,stroke-dasharray: 5 5;
    classDef labBox fill:#f8f9fa,stroke:#20c997,stroke-width:2px;
    classDef dataBox fill:#fff3bf,stroke:#f59f00,stroke-width:2px;
    classDef goalBox fill:#eebefa,stroke:#ae3ec9,stroke-width:3px;
    
    class Dorm dormBox;
    class Lab labBox;
    class P1C dataBox;
    class P6B goalBox;```
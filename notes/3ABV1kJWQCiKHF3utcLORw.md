Chapter 5: CPU Scheduling

CPU Scheduling（CPU 排程）是一種作業系統內部機制，用於管理與安排不同進程或執行緒在CPU上的執行順序。因為CPU資源有限，而現代系統會同時執行許多應用程式或任務，所以必須使用CPU排程來合理分配CPU的時間，使得系統能夠更高效地運作並滿足用戶的需求。

### CPU Scheduling 的目標
1. **最大化CPU使用率**：確保CPU大部分時間都在工作，而不是閒置。
2. **公平性**：讓所有進程都有機會執行，不偏袒某些進程。
3. **最大化吞吐量**：讓盡可能多的進程在單位時間內完成。
4. **最小化等待時間**：減少進程在等待CPU資源的時間。
5. **最小化周轉時間**：減少進程從提交到完成所需的時間。
6. **最小化響應時間**：減少互動式進程的響應時間，以提高用戶體驗。

### 常見的CPU Scheduling 演算法
1. **先來先服務（FCFS, First-Come, First-Served）**：按進程到達的順序執行，簡單但可能導致「等待時間」較長的問題。

2. **短作業優先（SJF, Shortest Job First）**：優先執行執行時間最短的進程，能最小化平均等待時間，但不適合預測執行時間不確定的進程。

3. **最短剩餘時間優先（SRTF, Shortest Remaining Time First）**：是SJF的變體，允許在進程執行期間中斷並切換到執行時間更短的進程。

4. **時間片輪轉（RR, Round Robin）**：為每個進程分配固定的CPU時間片，時間到則切換到下一個進程，適合多工系統，但可能增加上下文切換成本。

5. **優先級排程（Priority Scheduling）**：根據優先級高低分配CPU，優先級高的進程先執行。通常需要設計「老化機制」避免「飢餓現象」，即優先級低的進程長期得不到執行機會。

6. **多級隊列排程（Multilevel Queue Scheduling）**：將進程分類到不同的隊列中，不同隊列有不同的優先級和調度方式，適合有多類型任務的系統。

7. **多級反饋隊列排程（Multilevel Feedback Queue Scheduling）**：進程可以在不同的隊列間移動，根據進程的執行情況動態調整其優先級，靈活性高，適合變動的系統需求。

### CPU Scheduling 在系統中的應用
CPU排程廣泛應用於作業系統，如Windows、Linux 和 macOS。它保證系統能夠在多任務環境中穩定、高效地運作。對於實時系統，排程尤為重要，因為實時系統需要滿足嚴格的時間約束來保證系統的可靠性。

### 總結
CPU Scheduling 是一個在作業系統中至關重要的功能，通過不同的排程算法，根據系統需求和進程特性選擇合適的排程方式，來提高系統效率，平衡不同進程間的執行需求。

**CPU Burst（CPU 執行期）：**

指的是進程持續使用 CPU 進行計算的時間段。在此期間，進程執行計算、數據處理、邏輯判斷等需要 CPU 資源的任務。
典型的 CPU 密集型任務，例如科學計算、加密運算等，都會有較長的 CPU burst。
**I/O Burst（I/O 執行期）：**

指的是進程在執行 I/O 操作（如讀寫硬碟、傳輸數據、等待用戶輸入等）所經歷的時間段。在此期間，進程會停止使用 CPU，等待 I/O 操作完成。
I/O 密集型任務（如文件讀寫、大量數據傳輸等）往往會有較長的 I/O burst。
進程的執行通常是一系列的 CPU Burst 和 I/O Burst 交替進行的循環。例如，進程可能先進行一段 CPU 計算（CPU burst），接著等待數據輸入或輸出（I/O burst），完成後再進行下一段 CPU 計算，如此反覆進行。

Basic Concepts
- **透過多工處理獲得最大的CPU使用率**
- **CPU–I/O突發週期**：程序的執行由CPU執行和I/O等待交替組成的週期
   - CPU突發後接著I/O突發
   - CPU突發的分佈是主要關注的重點
  ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_184b5dd48d3dd07102c634d6593df386.PNG)

Histogram of CPU-burst Times
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7cffa13751f5aeef2f9581f271b7f8d9.PNG)
**CPU 排程器**

- 短期排程器（Short-term Scheduler）會從就緒隊列中的進程中進行選擇，並將 CPU 分配給其中一個進程。
- 就緒隊列可以以不同的方式進行排序。
- 當進程處於以下情況時，可能會進行 CPU 排程決策：
  1. 從執行狀態轉換為等待狀態
  2. 從執行狀態轉換為就緒狀態
  3. 從等待狀態轉換為就緒狀態
  4. 終止
- 在情況 1 和 4 下的排程是「非搶占式」的。
- 其他所有排程情況均為「搶占式」。
- 需要考慮對共享數據的訪問。
- 考慮在核心模式（Kernel Mode）中進行搶占的情況。
- 考慮在操作系統執行關鍵活動期間中斷發生的情況。
**分派器（Dispatcher）**

- 分派器模組將 CPU 控制權交給短期排程器選定的進程，這涉及：
  - 切換上下文
  - 切換到用戶模式
  - 跳轉到用戶程序中的適當位置以重新啟動該程序
- 分派延遲（Dispatch Latency）– 分派器停止一個進程並啟動另一個進程所需的時間
**排程準則（Scheduling Criteria）**

- **CPU 利用率** – 讓 CPU 保持盡可能忙碌的狀態
- **吞吐量** – 每單位時間內完成執行的進程數量
- **周轉時間** – 執行一個特定進程所需的總時間
- **等待時間** – 進程在就緒隊列中等待的時間
- **響應時間** – 從請求提交到系統產生第一個響應（非輸出）的時間（適用於分時環境）
**先來先服務（First-Come, First-Served, FCFS）排程**

進程及執行時間（Burst Time）：
- P1：24
- P2：3
- P3：3

假設進程按照以下順序到達：P1、P2、P3  
此排程的甘特圖（Gantt Chart）如下：

- P1 的等待時間 = 0
- P2 的等待時間 = 24
- P3 的等待時間 = 27

平均等待時間 = (0 + 24 + 27) / 3 = 17

甘特圖表示：
- P1 -> P2 -> P3
- 時間點：0, 24, 27, 30
假設進程按照以下順序到達：  
P2、P3、P1

該排程的甘特圖（Gantt Chart）如下：

- P1 的等待時間 = 6
- P2 的等待時間 = 0
- P3 的等待時間 = 3

平均等待時間 = (6 + 0 + 3) / 3 = 3

這比前一種情況要好得多。

**隊列效應（Convoy Effect）**：短進程被長進程排在後面。

考慮一個 CPU 密集型進程和多個 I/O 密集型進程的情況。
**最短作業優先（Shortest-Job-First, SJF）排程**

- 將每個進程的下一次 CPU 執行時間（CPU burst 時間）與該進程關聯。
- 使用這些執行時間來排程執行時間最短的進程。
- SJF 是最佳的排程方法 —— 對於給定的一組進程，能產生最小的平均等待時間。
- 難點在於如何預測下一次 CPU 請求的執行時間長度。
- 可以詢問用戶以獲得執行時間。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7717e9e4f86fc5e46e223e9b1a6494ad.PNG)
**確定下一次 CPU 執行時間的長度**

- 只能對下一次 CPU 執行時間進行估算——這個估算應與之前的執行時間相似。
- 然後選擇預測下一次 CPU 執行時間最短的進程。
- 這可以通過使用之前的 CPU 執行時間長度，使用指數平滑法來實現。
- 通常，α 設置為 ½。

**定義：**
1. **實際的 CPU 執行時間長度**  
2. **下一次 CPU 執行時間的預測值**  
3. 介於 0 到 1 之間的 α 值
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_263947260255383ef8beb1717c94cf6b.PNG)

- **搶占式版本**：稱為最短剩餘時間優先（Shortest-Remaining-Time-First）。
Examples of Exponential Averaging
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3b613b717b7ca1cab3b1f923461c0698.PNG)
Prediction of the Length of the Next CPU Burst
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9db9a3534072dc61d234e9fbd3ee74d6.jpg)
Example of Shortest-remaining-time-first
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_78cb8203a774dbb0e3b8414c62a01d12.PNG)
**優先級排程（Priority Scheduling）**

- 每個進程都會分配一個優先級數字（整數）。
- CPU 會分配給優先級最高的進程（數字最小的整數表示最高優先級）。
- 可以是 **搶占式** 或 **非搶占式**。
- SJF 排程是一種特殊的優先級排程，其中優先級是預測的下一次 CPU 執行時間的倒數。
- **問題**：饑餓（Starvation） – 低優先級的進程可能永遠無法執行。
- **解決方案**：老化（Aging） – 隨著時間推移，提高進程的優先級。
Example of RR with Time Quantum = 4
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_40b0338b2bf60ccbefac2869b398c920.PNG)

**CPU 利用率（CPU Utilization）** 是衡量 CPU 在一段時間內被有效使用的程度，通常以百分比表示。這是一個重要的性能指標，用於評估系統資源的使用效率。

### 計算方式
CPU 利用率可以通過以下公式計算：

\[
\text{CPU Utilization} = \left( \frac{\text{時間內 CPU 被使用的時間}}{\text{總時間}} \right) \times 100\%
\]

### 高 CPU 利用率的意義
- **高效率**：表明系統資源被充分利用，能夠處理更多的任務或進程。
- **降低閒置時間**：減少 CPU 閒置等待的時間，提高整體系統性能。

### 影響因素
1. **進程數量**：多進程或多任務系統通常會有更高的 CPU 利用率，因為可以隨時切換不同的進程以保持 CPU 繁忙。
2. **排程策略**：不同的 CPU 排程算法會影響 CPU 利用率，某些算法可能會導致更長的等待時間或進程閒置。
3. **工作負載**： CPU 的工作負載越高，利用率通常也會越高。相反，當系統處於低負載時，CPU 利用率會下降。

### 最佳實踐
在設計和配置系統時，應努力實現適當的 CPU 利用率，以平衡性能和資源使用。過高的利用率（接近 100%）可能意味著系統過載，導致延遲或服務質量下降；而過低的利用率則表示資源未被有效利用，可能需要進行優化。
**周轉時間（Turnaround Time）** 是衡量進程從提交到完成所需的總時間，是一個重要的性能指標，通常用來評估系統的效率。

### 定義
周轉時間可以被定義為：

\[
\text{周轉時間} = \text{完成時間} - \text{到達時間}
\]

### 組成部分
周轉時間包括以下幾個部分：

1. **等待時間（Waiting Time）**：進程在就緒隊列中等待被調度的時間。
2. **執行時間（Burst Time）**：進程實際使用 CPU 的時間。
3. **I/O 時間**：進程在進行 I/O 操作時等待的時間。

### 計算方式
對於一個進程的周轉時間計算如下：

- **到達時間（Arrival Time）**：進程開始進入系統的時間。
- **完成時間（Completion Time）**：進程完成執行並退出系統的時間。

### 示例
假設有一個進程 P1，其到達時間為 0，執行時間為 5，並在 10 時完成，那麼它的周轉時間為：

\[
\text{周轉時間} = 10 - 0 = 10
\]

### 平均周轉時間
如果有多個進程，平均周轉時間可以這樣計算：

\[
\text{平均周轉時間} = \frac{\sum \text{所有進程的周轉時間}}{\text{進程數量}}
\]

### 重要性
周轉時間是評估系統性能的一個重要指標，因為它直接影響用戶的體驗和應用的效率。在多進程系統中，減少周轉時間可以提升整體吞吐量，並提高用戶的滿意度。
**等待時間（Waiting Time）** 是指進程在就緒隊列中等待 CPU 資源的時間，這段時間不包括進程正在執行或進行 I/O 操作的時間。它是評估系統性能的重要指標之一。

### 定義
等待時間可以被定義為：

\[
\text{等待時間} = \text{周轉時間} - \text{執行時間}
\]

或更具體地，對於每個進程來說：

\[
\text{等待時間} = \text{完成時間} - \text{到達時間} - \text{執行時間}
\]

### 組成部分
- **周轉時間（Turnaround Time）**：進程從提交到完成所需的總時間。
- **執行時間（Burst Time）**：進程實際使用 CPU 的時間。

### 示例
假設有一個進程 P1，其到達時間為 0，執行時間為 5，完成時間為 10，那麼它的等待時間計算如下：

\[
\text{等待時間} = 10 - 0 - 5 = 5
\]

### 平均等待時間
對於多個進程，可以計算平均等待時間：

\[
\text{平均等待時間} = \frac{\sum \text{所有進程的等待時間}}{\text{進程數量}}
\]

### 重要性
- **系統性能指標**：等待時間反映了進程在就緒隊列中被調度的效率，等待時間越短，系統的響應速度通常越快。
- **用戶體驗**：對於用戶交互式應用程序，較低的等待時間能提高用戶滿意度，因為用戶能更快地看到結果或反應。

### 影響因素
1. **排程策略**：不同的排程算法（如 FCFS、SJF、RR 等）會影響進程的等待時間。
2. **進程到達順序**：進程的到達順序和資源需求會影響其在就緒隊列中的等待時間。
3. **CPU 和 I/O 的需求**：需要大量 I/O 操作的進程可能會導致其他進程的等待時間增加。

在設計和優化作業系統時，降低等待時間是一個重要的目標，以提高整體系統性能和用戶滿意度。
**響應時間（Response Time）** 是指從進程提交請求到系統產生第一個響應所需的時間。在交互式系統中，響應時間是一個關鍵性能指標，影響用戶體驗。

### 定義
響應時間可以定義為：

\[
\text{響應時間} = \text{第一次響應的時間} - \text{請求提交的時間}
\]

### 組成部分
響應時間通常不包括進程的執行時間，而僅僅是用戶請求和系統第一次回應之間的時間。這意味著響應時間考慮的是系統的反應速度，而不是進程完成所有操作的時間。

### 示例
假設用戶在 0 秒時提交一個請求，而系統在 5 秒時產生了第一個響應，那麼響應時間為：

\[
\text{響應時間} = 5 - 0 = 5 \text{秒}
\]

### 平均響應時間
對於多個進程，可以計算平均響應時間：

\[
\text{平均響應時間} = \frac{\sum \text{所有進程的響應時間}}{\text{進程數量}}
\]

### 重要性
- **用戶體驗**：響應時間直接影響用戶的感知和體驗。在交互式應用中，較短的響應時間能顯著提高用戶滿意度。
- **性能指標**：響應時間是評估系統性能的重要指標，特別是在實時系統和在線服務中。

### 影響因素
1. **排程算法**：不同的 CPU 排程算法（如 FCFS、SJF、RR 等）會影響進程的響應時間。
2. **系統負載**：系統中的其他進程和任務會影響資源的可用性，從而影響響應時間。
3. **I/O 操作**：需要進行大量 I/O 操作的進程可能會增加響應時間，因為系統需要等待這些操作完成。

在設計和優化系統時，降低響應時間是提升用戶體驗和系統效率的一個重要目標。
Time Quantum and Context Switch Time
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_95df64b6f7dec4c11bb6cea9b50a0e6f.PNG)
Turnaround Time Varies With The Time Quantum
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0e343749e492247e7002da5dbde44638.PNG)

**上課稍微有提到**
評估 CPU 排程算法的常見方法有四種，每種方法針對不同情境，幫助分析算法的效率、性能和適用性。

### 1. **模擬（Simulation）**
   - 透過程式模擬算法的運行，分析其在不同情境下的行為。
   - 通常使用隨機數生成模擬進程的到達時間、執行時間和 I/O 操作。
   - 優點：靈活，可測試不同負載和條件，生成細緻的性能數據。
   - 缺點：模擬設置可能偏離實際系統，且需要較高的運算資源。

### 2. **排程模型分析（Queueing Models）**
   - 利用排隊論模型來模擬進程在系統中的排隊和等待過程。
   - 常用指標：平均等待時間、平均周轉時間、CPU 利用率等。
   - 優點：能用數學模型直接分析系統性能，適合初步設計和算法比較。
   - 缺點：假設條件簡化了現實場景的複雜性，可能不完全準確。

### 3. **時間分析（Deterministic Modeling）**
   - 使用一組固定的進程和已知的到達時間、執行時間進行分析。
   - 通常計算不同算法下的平均等待時間、周轉時間等性能指標。
   - 優點：結果精確，便於在標準情境下進行比較。
   - 缺點：無法模擬系統中的隨機因素和動態行為。

### 4. **實驗測試（Implementation Testing）**
   - 將算法直接應用於操作系統或實際測試環境中，觀察其性能表現。
   - 優點：結果最貼近真實系統，能直接驗證算法的實際效果。
   - 缺點：耗費時間和資源，且在實際系統中切換算法可能有風險。

### 總結
- **模擬** 和 **排程模型分析** 更適合於設計階段的測試。
- **時間分析** 和 **實驗測試** 適合進行精確驗證或真實環境中的實際測試。
**實作（Implementation）**

- 即使是模擬，也具有有限的準確性。
- 可以直接實作新的排程器並在實際系統中測試。
- 代價高、風險大。
- 不同的環境條件各不相同。
- 大多數靈活的排程器可以依照站點或系統需求進行調整。
- 或者透過 API 來調整優先級。
- 但環境差異仍然存在。
Evaluation of CPU Schedulers by Simulation
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fd1f596c09212822f76febc12725e1d4.jpg)
多級佇列

 將就緒佇列劃分為不同的佇列，例如：
   - 前景（互動式）
   - 背景（批次處理）

 每個程序永久屬於一個特定的佇列

 每個佇列都有自己的排程算法：
   - 前景佇列使用RR（輪轉法）
   - 背景佇列使用FCFS（先到先服務）

 需要在各佇列之間進行排程：
   - 固定優先級排程（例如：先處理所有前景佇列，再處理背景佇列），但可能會導致飢餓問題。
   - 時間片分配——每個佇列獲得一定的CPU時間，並在其內部進行排程；例如，分配80%給前景佇列，使用RR排程
   - 分配20%給背景佇列，使用FCFS排程
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_42ca9f290a7fec688b5fcaae21f02711.PNG)
多級回饋佇列

 一個程序可以在不同的佇列間移動；可以通過這種方式實現老化機制
 多級回饋佇列排程器的定義參數如下：

   - 佇列的數量
   - 每個佇列的排程算法
   - 升級程序的判斷方法
   - 降級程序的判斷方法
   - 判斷程序在需要服務時將進入哪個佇列的方法
多級回饋佇列的範例

 三個佇列：
   - Q0 – 使用輪轉法（RR），時間量為8毫秒
   - Q1 – 使用輪轉法（RR），時間量為16毫秒
   - Q2 – 使用先到先服務（FCFS）

 排程流程：
   - 新的作業進入佇列Q0，並以先到先服務（FCFS）方式處理
      - 當作業獲得CPU時，將獲得8毫秒的執行時間
      - 如果在8毫秒內未完成，則將作業移至佇列Q1

   - 在Q1中，作業再次以先到先服務（FCFS）方式處理，並獲得額外的16毫秒執行時間
      - 如果仍然未完成，則被搶佔並移至佇列Q2
執行緒排程

 使用者層級執行緒和核心層級執行緒之間的區別
 要在CPU上運行，使用者層級的執行緒最終必須映射到相關的核心層級執行緒，雖然這種映射可能是間接的，並且可能使用輕量級程序（LWP, Light Weight Process）
 在多對一和多對多模型中，執行緒庫將使用者層級執行緒排程到LWP上運行
 這種排程被稱為進程爭用範疇（PCS, Process-Contention Scope），因為排程競爭發生在同一個進程內
   - 通常由程式設置的優先級來完成
 核心層級執行緒被排程到可用的CPU上則屬於系統爭用範疇（SCS, System-Contention Scope）—此時所有執行緒在整個系統中競爭
Pthread 排程

 API允許在創建執行緒時指定使用PCS或SCS
 `PTHREAD_SCOPE_PROCESS` 使用PCS排程執行緒
 `PTHREAD_SCOPE_SYSTEM` 使用SCS排程執行緒
 可能會受操作系統限制——Linux和Mac OS X只允許`PTHREAD_SCOPE_SYSTEM`
Pthread Scheduling API
#include <pthread.h> 
#include <stdio.h> 

#define NUM_THREADS 5 

int main(int argc, char *argv[]) { 
    int i, scope;
    pthread_t tid[NUM_THREADS]; 
    pthread_attr_t attr; 

    /* get the default attributes */ 
    pthread_attr_init(&attr); 

    /* first inquire on the current scope */
    if (pthread_attr_getscope(&attr, &scope) != 0) 
        fprintf(stderr, "Unable to get scheduling scope\n"); 
    else { 
        if (scope == PTHREAD_SCOPE_PROCESS) 
            printf("PTHREAD_SCOPE_PROCESS\n"); 
        else if (scope == PTHREAD_SCOPE_SYSTEM) 
            printf("PTHREAD_SCOPE_SYSTEM\n"); 
        else
            fprintf(stderr, "Illegal scope value.\n"); 
    }

    /* Optional: Create threads */
    for (i = 0; i < NUM_THREADS; i++) {
        pthread_create(&tid[i], &attr, /* thread function */, NULL);
    }

    /* Destroy the attribute object */
    pthread_attr_destroy(&attr);

    /* Optional: Join threads */
    for (i = 0; i < NUM_THREADS; i++) {
        pthread_join(tid[i], NULL);
    }

    return 0; 
}
Multiple-Processor Scheduling
當多個CPU可用時，CPU排程變得更加複雜

 在多處理器中，處理器為同質（相同的）處理器
 非對稱多處理（AMP, Asymmetric Multiprocessing）– 只有一個處理器訪問系統數據結構，減少了數據共享的需求
 對稱多處理（SMP, Symmetric Multiprocessing）– 每個處理器自我排程，所有進程在一個公共就緒佇列中，或者每個處理器有自己私有的就緒進程佇列
   - 目前最為常見
 處理器親和性 – 進程對其當前運行的處理器具有親和性
   - 軟性親和性（soft affinity）
   - 硬性親和性（hard affinity）
 包括處理器集合在內的變體
NUMA and CPU Scheduling
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a65566f61ceb6051045493d5f8149b8a.PNG)
Multicore Processors
近期趨勢是將多個處理器核心置於同一個實體晶片上

 更快且消耗更少的電力
 每個核心上的多執行緒技術也在增長
 利用記憶體停滯的時間，在等待記憶體檢索時繼續處理其他執行緒
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_041d7d7a53005075912121e8fb8c6c4f.PNG)

第五章有些內容必須要去看影片補充
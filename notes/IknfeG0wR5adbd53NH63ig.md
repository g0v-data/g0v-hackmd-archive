Chapter 3: Processes
作業系統執行各種程序：
- **批次系統** - 作業（Jobs）
- **分時系統** - 使用者程式或任務（Tasks）

教科書幾乎將「作業」（job）和「程序」（process）這兩個術語互換使用。
- **程序** - 是正在執行的程式；程序執行必須以**順序**方式進行。

程序包含多個部分：
- **程式碼**，也稱為文字段（text section）
- 當前活動，包括**程式計數器**（program counter）、**處理器暫存器**（processor registers）
- 包含暫時資料的**堆疊**（stack）
  - 函式參數、返回地址、局部變數
- 包含全局變數的**資料段**（data section）
- 包含在執行時期動態分配的記憶體的**堆**（heap）

- **程式**是被動實體，存儲在磁碟上（可執行檔案），而**程序**是**主動**的。
- 當可執行檔案被加載到記憶體中時，程式變成程序。
- 程式的執行可通過 GUI 的滑鼠點擊、命令行輸入程式名稱等方式啟動。
- 一個程式可以是多個程序。
  - 考慮多個使用者執行相同程式的情況。
 Process in Memory
 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_94c2d1022b492ee1356147226a544db2.PNG)
程序狀態

當一個程序執行時，它會改變狀態：

- **new（新建）**: 程序正在被創建
- **running（執行）**: 指令正在被執行
- **waiting（等待）**: 程序在等待某些事件發生
- **ready（就緒）**: 程序正在等待被分配到處理器
- **terminated（終止）**: 程序已完成執行
Diagram of Process State
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5c799f6cde5e00dd919f71984b69608b.PNG)
**程序控制塊 (PCB)**

與每個程序相關的資訊  
（也稱為任務控制塊）

- **程序狀態** – 執行中、等待中等
- **程式計數器** – 下一條要執行的指令的位置
- **CPU 暫存器** – 所有與程序相關的暫存器內容
- **CPU 排程資訊** – 優先級、排程隊列指標
- **記憶體管理資訊** – 分配給程序的記憶體
- **記帳資訊** – 已使用的 CPU 時間、從開始執行以來經過的時間、時間限制
- **I/O 狀態資訊** – 分配給程序的 I/O 設備、打開的文件列表
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5449d343f5086af6f485442b3f258ef6.PNG)

CPU Switch From Process to Process
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1d99625e03b0f051a5fcbb2ef3e0b51f.PNG)
**程序排程**

最大化 CPU 使用率，快速切換程序到 CPU 上以進行**時間共享**。

- **程序排程器**從可用的程序中選擇下一個要在 CPU 上執行的程序。
- 排程器維護程序的排程隊列：
  - **作業隊列**（Job queue）– 系統中所有程序的集合
  - **就緒隊列**（Ready queue）– 位於主記憶體中，準備執行並等待執行的程序集合
  - **設備隊列**（Device queues）– 等待 I/O 設備的程序集合
- 程序在不同的隊列之間進行遷移。
就緒隊列（Ready Queue）和各種 I/O 設備隊列
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_74009599afcb52d5ab4f095e928dd925.PNG)
**程序排程的表示**
排隊圖表示隊列、資源、流程
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_905afd1972c046e20cd09705a2b9557f.PNG)
**短期排程器**（或 CPU 排程器）– 選擇應該下一個執行的程序並分配 CPU。  
有時它是系統中唯一的排程器。

- **短期排程器**會頻繁地被調用（以毫秒為單位）（必須快速）。
  
**長期排程器**（或作業排程器）– 選擇哪些程序應該被放入就緒隊列。  
**長期排程器**調用的頻率較低（以秒或分鐘為單位）（可以較慢）。

**長期排程器**控制多程式設計的程度。
**增加中期排程**

如果需要降低多程式設計的程度，可以添加**中期排程器**。  
中期排程器會將程序從記憶體中移除，儲存到磁碟，然後再從磁碟中讀取以繼續執行，這個過程稱為**交換（swapping）**。

程序可描述為：
- **I/O 密集型程序** – 花費更多時間在 I/O 操作上，而非計算，具有許多短暫的 CPU 執行週期。
- **CPU 密集型程序** – 花費更多時間在計算上，具有少數但較長的 CPU 執行週期。

**長期排程器**的目標是保持良好的程序混合。

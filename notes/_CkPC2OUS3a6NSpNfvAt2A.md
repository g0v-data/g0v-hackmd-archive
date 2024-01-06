# 作業系統
## Ch1. Introduction
### Interrupt (中斷)
- OS是中斷驅動(interrupt driven)
- trap/exception是由錯誤或使用者請求引起的軟體生成的interrupt
- 類型
    1. polling (輪詢)
    2. vectored interrupt system
### Direct Memory Access (DMA)
- I/O設備控制器不需要CPU干涉即可將數據塊從buffer直接傳輸到主記憶體
- 每個block產生一次interrupt，而不是每個byte產生一個interrupt
## Ch2. Operating-System Structures
### OS服務
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_90627c5f5b665efe300564cefadf75a2.png)
### System Call
- OS提供的服務的程式interface
- 透過API訪問，而不是直接使用system call
- 參數傳遞方式
    1. register
    2. memory
    3. stack
- 類型
    1. process control (ex. fork()、exec())
    2. file management (ex. fopen())
    3. device management
    4. information maintenance
    5. communications (ex. message passing)
    6. protection
## Ch3. Process
- process is an active program
- OS會分配唯一ID(PID)給它
    | 部分 | 內容 |
    | - | - |
    | text section | program code |
    | current activity | program counter、process register |
    | stack | function parameters、return addresses、local variables |
    | data section | global variables |
    | heap | dynamic allocated memory |
- program
    - passive entity stored on disk (executable file)
    - 載入到記憶體會變成process
    - 可以是多個process，因為可能有多個使用者執行同一個程式
- process state
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dfe0c7a0e37a077db1fc951e64664fa0.png)
- process control block (PCB)
    - process state
    - process number
    - program counter
    - registers
    - memory limits
    - list of open files
    - CPU scheduling information
    - memory-management information
    - accounting information
    - I/O status information
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_222723704bc5895cc7d146e8f137a6ba.png)
- content switch
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fa077e46c5bb768f1c65f663e1c1e255.png)
- thread
    - multiple program counter per process
    - multiple locations can execute at once
- process scheduling
    - process scheduler在可用process中選擇下一次要在CPU上執行的process
        - job queue：系統中所有的process
        - ready queue：在主記憶體中所有process，就緒並等待執行
        - device queue：等待I/O設備的process
- process creation
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1affef8d644a895f463c28a8ac80fc1c.png)
- process termination
    - cascading termination
    - zombie：no parent waiting (did not invoke wait)
    - orphan：parent terminated without invoking wait
- interprocess comminication
    1. shared memory
        ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1fe7724610b89a2f6634102da43e8bc7.png)
    2. message passing
        ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_748f003a8696f1c7fce1bffbe9d01c57.png)
## Ch4. Threads & Concurrency
- Multithreaded Server Architecture
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c68a8bf29cd7ea25fe5877add5324832.png)
- concurrency
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6dcd069ed88107e3c19b8a6ca0129a60.png)
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cf27ead74819a4f60f24940691e79a6c.png)
- parallelism
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e63f8952d22ae0e926d8a03167b83147.png)
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_58678f42c9a2ab32b648485998b2d140.png)
- Amdahl’s Law
    - S is serial portion
    - N processing cores
        ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1f31043d6689bb9dad7a1017f46c75ca.png)
- multithreading model
    1. many-to-one
        ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_90bc7760245ed913288929ee2c4cabce.png)
        - 一個thread阻塞會導致所有thread阻塞
    2. one-to-one
        ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5d4869a308a58ed437649fa5689af67b.png)
    3. many-to-many
        ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ffa0a2e06f9ea1ccb050d1b1eae06345.png)
## Ch5. CPU Scheduling
### scheduling criteria
1. CPU utilization：讓CPU盡可能忙碌
2. throughput：單位時間內完成的process數量
3. turnaround time：執行process的時間
4. waiting time：process在ready queue等待的時間
    - 不是在waiting queue中的時間
5. response time：從提交請求到產生第一個回應的時間
### First-Come, First-Served (FCFS)
| process | burst time |
| - | - |
| p1 | 24 |
| p2 | 3 |
| p3 | 3 |

|| p1(24) || p2(3) || p3(3) ||
| - | - | - | - | - | - | - |
| 0 || 24 || 27 || 30 |

| process | waiting time |
| - | - |
| p1 | 0 |
| p2 | 24 |
| p3 | 27 |

average waiting time = (0 + 24 + 27) / 3 = 17
- convey effect：短process在長process後，會增加average waiting time
### Shortest-Job-First (SJF)
- process的最小平均等待時間
- non-preemptive

| process | burst time |
| - | - |
| p1 | 6 |
| p2 | 8 |
| p3 | 7 |
| p4 | 3 |

|| p4(3) || p1(6) || p3(7) || p2(8) ||
| - | - | - | - | - | - | - | - | - |
| 0 || 3 || 9 || 16 || 24 |

| process | waiting time |
| - | - |
| p1 | 3 |
| p2 | 16 |
| p3 | 9 |
| p4 | 0 |

average waiting time = (3 + 16 + 9 + 0) / 4 = 7
### priority
- smallest integer -> highest priority
- 問題：
    - starvation：低優先度的process可能永遠不會執行
    - 解決方法：
        - aging：隨著時間增加process的優先度
### Round Robin (RR)
- 每個process獲得一個小單位的CPU時間(time quantum q)
- q結束後，process被強佔並移到ready queue的尾端
- q大 -> 接近FCFS
- q小 -> content switch overhead會很大
## Ch6. Synchronization Tools
### critical section
- 同時訪問共享資料可能導致資料不一致
- 維護資料一致性需要機制來確保process的有序執行
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f72c16289304304fccfc6c4e3a7fcf2e.png)
- 解法必備三要素
    1. mutual exclusion
        如果process在critical section執行，則其他process不能進入critical section
    2. progress
        如果沒有process在critical section執行，則下一個想進入critical section的process可以進入
    3. bounded waiting
        process等待進入critical section的時間是有限的
### Peterson’s Solution
- 共享變數
    ```c
    int turn; // 輪到誰進入critical section
    bool flag[2]; // flag[i] = true表示process i已經準備就緒
    ```
- process i
    ```c
    do
    {
        flag[i] = true;
        turn = j;
        while (flag[j] && turn = = j);
        // critical section
        flag[i] = false;
        // remainder section
     } while (true);
    ```
### test_and_set
```c
bool test_and_set(bool *target)
{
    bool return_value = *target;
    *target = true;
    return return_value;
}
```
- 共享變數
    ```c
    bool lock = false;
    ```
- solution
    ```c
    do
    {
        while (test_and_set(&lock));
        // critical section
        lock = false;
        // remainder section
    } while (true);
    ```
### compare_and_swap
```c
int compare_and_swap(int *value, int expected, int new_value)
{
    int temp = *value;
    if (*value == expected)
        *value = new_value;
    return temp;
}
```
- 共享變數
    ```c
    int lock = 0;
    ```
- solution
    ```c
    do
    {
        while (compare_and_swap(&lock, 0, 1) != 0);
        // critical section
        lock = 0;
        // remainder section
    } while (true);
    ```
### mutex lock
- 透過硬體原子指令
- 需要buzy waiting
```c
void acquire()
{
    while (!available); // buzy waiting
    available = false;
}
void release()
{
    available = true;
}
```
- solution
    ```c
    do
    {
        acquire();
        // critical section
        release();
        // remainder section
    } while (true);
    ```
### semaphore
- 整數變數，只能透過兩個原子指令訪問：wait()和signal()
```c
void wait(S)
{
    while (S <= 0);
    S--;
}
void signal(S)
{
    S++;
}
```
- 分類
    1. counting semaphore
        - 整數值的範圍不受限制
    2. binary semaphore
        - 整數值只能為0或1
        - 與mutex lock相同
- 使用
    - 共享變數
        ```c
        int synch = 0;
        ```
    - S1在S2前執行
        ```c
        P1:
            S1;
            signal(synch);
        P2:
            wait(synch);
            S2;
        ```
### semaphore without buzy waiting
- 每個semaphore都對應一個waiting queue
- 兩個操作
    1. block：將process放在適當的waiting queue中
    2. wakeup：移除waiting queue中的一個process並放入ready queue
### deadlock & starvation
- deadlock
    - 兩個或多個process等待一個事件，而該事件只能由一個正在等待的process引起
- starvation
    - 無限期阻塞
    - process永遠不會從它掛起的semaphore queue中刪除
### monitor
- 抽象資料類型
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_37dd0f50df9fd0be04b75bca7b30f7a8.png)
## Ch7. Synchronization Examples
### bounded-buffer problem
- n個buffer，每個buffer可以容納一個item
- semaphore mutex = 1
- semaphore full = 0
- semaphore empty = n
- producer
    ```c
    do
    {
        // produce an item
        wait(empty);
        wait(mutex);
        // add item to buffer
        signal(mutex);
        signal(full);
    } while (true);
    ```
- consumer
    ```c
    do
    {
        wait(full);
        wait(mutex);
        // remove an item from buffer
        signal(mutex);
        signal(empty);
        // consume the item
    } while (true);
    ```
### readers-writers problem
- reader：只讀取dataset
- writer：讀或寫dataset
- 只有一個writer可以同時訪問共享數據
- 共享變數
    1. dataset
    2. semaphore rw_mutex = 1
    3. semaphore mutex = 1
    4. read_count = 0
- writer
    ```c
    do
    {
        wait(rw_mutex);
        // writing
        signal(rw_mutex);
    } while (true);
    ```
- reader
    ```c
    do
    {
        wait(mutex);
        read_count++;
        if (read_count == 1)
            wait(rw_mutex);
        signal(mutex);
        // reading
        wait(mutex);
        read_count--;
        if (read_count == 0)
            signal(rw_mutex);
        signal(mutex);
    } while (true);
    ```
### dining-philosophers problem
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_925c4625f9f044c3cebbe3c2390f133e.png)
- 哲學家一生都在思考和進食之間交替度過
- 不與鄰居互動，偶爾嘗試拿起兩根筷子（一次一根）從碗裡吃東西，吃完東西後釋放它們
- 共享變數
    1. 一碗飯 (dataset)
    2. semaphore chopstick[n] 初始化為1
- **待補**
## Ch8. Deadlocks
### 需要同時滿足四個條件
1. mutual exclusion
    - 一次只有一個process能使用一種資源
2. hold and wait
    - 持有至少一種資源的process正在等待獲取其他process持有的資源
3. no preemption
    - 資源只能由持有它的process在完成後釋放
4. circular wait
    - 存在一組process {p0, p1, ..., pn}，p0等待p1的資源，p1等待p2的資源，pn等待p0的資源
### 處理方式
1. deadlock prevention
2. deadlock avoidance
3. 進入deadlock後恢復
4. 忽略
### deadlock prevention
- 讓四個條件任意一個不滿足
1. mutual exclusion
    - 不請求共享資源
2. hold and wait
    - process請求資源時不能持有其他資源
3. no preemption
    - 持有某些資源的process請求另一個無法立即分配給它的資源，則釋放所有持有的資源
4. circular wait
    - 將所有資源編號，process請求的資源編號必須要遞增
### deadlock avoidance
- 要求每個process聲明可能需要的每種類型資源的最大數量
- deadlock avoidance演算法動態檢查資源分配狀態
- 當process請求資源時，系統必須決定立即分配是否使系統處於safe state
- 系統處於safe state -> 不會發生deadlock
- 確保系統不會進入unsafe state
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4811897780915bc3f1e46701c8919d8e.png)
- Banker's Algorithm
    - 5個process：p0 ~ p4
    - 3個類別的資料
        - A (10個)
        - B (5個)
        - C (7個)
    - snapshot at time T0
        | process | allocation ||| max |||
        | - | - | - | - | - | - | - |
        || A | B | C | A | B | C |
        | p0 | 0 | 1 | 0 | 7 | 5 | 3 |
        | p1 | 2 | 0 | 0 | 3 | 2 | 2 |
        | p2 | 3 | 0 | 2 | 9 | 0 | 2 |
        | p3 | 2 | 1 | 1 | 2 | 2 | 2 |
        | p4 | 0 | 0 | 2 | 4 | 3 | 3 |
        
        | available |||
        | - | - | - |
        | A | B | C |
        | 3 | 3 | 2 |
    - need = max - allocation
        | process | need |||
        | - | - | - | - |
        | p0 | 7 | 4 | 3 |
        | p1 | 1 | 2 | 2 |
        | p2 | 6 | 0 | 0 |
        | p3 | 0 | 1 | 1 |
        | p4 | 4 | 3 | 1 |
    - **待補**
## Ch9. Main Memory
### base and limit register
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_035b9fdfd14d02b511509f181b6d931a.png)
### hardware address protection
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_94f47b36f82a41e356bc7a0c5157a1e8.png)
### multistep processing of user program
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f30020cc5638f143a3930452c0365d39.png)
### logical vs physical address
- logical address
    - 由CPU生成
    - aka virtual address
- physical address
    - 主記憶體位址
### memory-management unit (MMU)
- base register這裡稱為relocation register
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ccc438efe154af471e856356b16ac6c9.png)
### swapping
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_739b29d82c9d7c3bec13b8db361646f6.png)
### hardware support for relocation and limit registers
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_81bf98fb8833eac9ba05e08d9e984114.png)
### fragmentation
- external fragmentation
    - 總空間存在以滿足請求，但它不是連續的
- internal fragmentation
    - 分配的空間比請求的大
### segmentation
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1d99e4ba2a130cb556dc035bf8f9a098.png)
- logical address：<segmentaion-number, offset>
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b8b6f765cd9342e723d5b2d53748d6c1.png)
### paging
- 避免external fragmentation
- 將physical memory劃分為固定大小的frame
- page number ( p )
- page offset ( b )
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_65ddbd64c20a462957bd453cc2b340b1.png)
### translation look-aside buffers (TLB)
- 快取記憶體，加速查表
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2fc16d7f498969d9e1059fce34857fbf.png)
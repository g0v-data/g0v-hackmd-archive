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
**老師有問長期 短期 與中程 的不同之處**
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cb8e81c3689e645d6b9c49c4ce91d769.PNG)
**上下文切換**

當 CPU 切換到另一個程序時，系統必須保存舊程序的狀態，並通過上下文切換加載新程序的已保存狀態。

- 程序的上下文表示在**程序控制塊 (PCB)** 中。
- 上下文切換時間是一種**開銷**；在切換期間，系統無法執行有用的工作。
- 作業系統和 PCB 越複雜，**上下文切換**所需的時間越長。
- 上下文切換時間依賴於**硬體支援**。
- 有些硬體提供每個 CPU 的多組暫存器 ➔ 可以一次加載多個上下文。
**對程序的操作**

系統必須提供以下機制：
- **程序創建**，
- **程序終止**，
- 等等，具體內容如下。

### 程序創建

父程序創建子程序，子程序又可以創建其他程序，形成一棵程序樹。  
通常，程序通過**程序識別碼（pid）**來識別和管理。

**資源共享選項**：
- 父程序和子程序共享所有資源。
- 子程序共享父程序資源的子集。
- 父程序和子程序不共享任何資源。

**執行選項**：
- 父程序和子程序同時執行。
- 父程序在子程序終止之前等待。
**地址空間**

- **子程序**是父程序的**副本**。
- 子程序有一個程式載入到它的地址空間中。

### UNIX 範例

- **fork()** 系統調用用於創建新程序。
- **exec()** 系統調用在 `fork()` 之後使用，用於將程序的記憶體空間替換為新程序。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_28a26586f473b3a5c10f095cf0b17acc.PNG)
**程序終止**

- 程序執行最後一條語句，然後通過 `exit()` 系統調用請求作業系統刪除自己。
- 通過 `wait()` 將狀態數據從子程序返回給父程序。
- 作業系統會釋放程序的資源。
- 父程序可以使用 `abort()` 系統調用終止子程序的執行。這樣做的原因包括：
  - 子程序超出了分配的資源。
  - 分配給子程序的任務不再需要。
一些作業系統不允許子程序存在於其父程序已終止的情況下。如果一個程序終止，那麼它的所有子程序也必須被終止，這稱為**級聯終止**（cascading termination）。所有的子程序、孫程序等都會被終止。

- 終止是由作業系統啟動的。
- 父程序可以使用 `wait()` 系統調用等待子程序的終止。
- 如果沒有父程序在等待（未調用 `wait()`），則該程序成為**僵屍程序**（zombie）。
- 如果父程序在未調用 `wait()` 的情況下終止，則該程序成為**孤兒程序**（orphan）。
### 程序終止

1. **執行最後語句**：程序執行完最後一條語句後，通過 `exit()` 系統調用請求作業系統刪除自己。
  
2. **返回狀態數據**：狀態數據通過 `wait()` 從子程序返回給父程序。

3. **資源釋放**：作業系統會釋放程序所占用的資源。

4. **父程序終止子程序**：父程序可以使用 `abort()` 系統調用終止子程序的執行，這樣做的原因包括：
   - 子程序超出了分配的資源。
   - 分配給子程序的任務不再需要。

5. **級聯終止**：某些作業系統不允許子程序在其父程序已終止的情況下存在。如果一個程序終止，那麼它的所有子程序也必須被終止，這稱為**級聯終止**（cascading termination），即所有的子程序、孫程序等都會被終止。

6. **由作業系統啟動**：程序的終止由作業系統發起。

7. **等待終止**：父程序可以使用 `wait()` 系統調用等待子程序的終止。

8. **僵屍程序**：如果沒有父程序在等待（未調用 `wait()`），則該程序成為**僵屍程序**（zombie）。就是小孩發出終止信號 但父母沒有收到 或者沒有反應 家長就被稱為殭屍程式 但通常os會認為是合法情況 因此常被設計為惡意程式

9. **孤兒程序**：如果父程序在未調用 `wait()` 的情況下終止，則該程序成為**孤兒程序**（orphan）。父母產生小孩之後就死翹翹了 所以小孩就變成孤兒
### 進程間通信（Interprocess Communication, IPC）

系統中的進程可以是獨立的或是合作的。合作進程可以影響其他進程，或被其他進程影響，包括共享數據。

#### 合作進程的原因：
- **信息共享**：允許進程之間共享數據。
- **計算加速**：通過並行處理提高計算速度。
- **模塊化**：將複雜的問題分解為更小的、易於管理的部分。
- **便利性**：提高系統的使用效率和便利性。

合作進程需要進程間通信（IPC），主要有以下兩種模型：

### IPC 的兩種模型 https://hackmd.io/@YiZjennnnn/OS_Note/https%3A%2F%2Fhackmd.io%2F%40YiZjennnnn%2Fipc_interprocess_communication?type=book

1. **共享記憶體**（Shared Memory）：多個進程可以訪問同一段記憶體空間以進行數據共享。
2. **消息傳遞**（Message Passing）：進程之間通過傳送和接收消息來進行通信。

### 通信模型
- **(a) 消息傳遞**：進程通過發送和接收消息來交流。
- **(b) 共享記憶體**：進程通過訪問共享的記憶體區域來交流。

這兩種模型各有優缺點，適用於不同的應用場景和需求。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7707350344a229ebf463d797aaa5c545.PNG)
### 生產者-消費者問題(疑似會考的部分)

這是一種合作進程的範例，其中生產者進程生成信息，並由消費者進程消耗這些信息。

#### 兩種緩衝區的概念：

1. **無界緩衝區**（Unbounded Buffer）：
   - 沒有實際的緩衝區大小限制，生產者可以隨意生產數據，消費者可以隨意消耗數據。這種情況下，資料的生產和消費不會受到緩衝區大小的約束。

2. **有界緩衝區**（Bounded Buffer）：
   - 假設緩衝區的大小是固定的，這意味著生產者必須在緩衝區已滿的情況下等待，直到消費者消耗一些資料以釋放空間。這增加了進程間協調的複雜性，因為需要管理緩衝區的滿和空狀態。

這一問題的解決通常需要使用進程間通信機制（如信號量或互斥鎖）來確保資料的一致性和正確性。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d75b76bc71c6dcac5221df163bbb5bee.PNG)
### 進程間通信 – 共享記憶體

- **共享記憶體**是指在希望進行通信的進程之間共享的記憶體區域。
- 通信由用戶進程控制，而不是由作業系統控制。
- 主要問題是提供機制，使得用戶進程在訪問共享記憶體時能夠同步其操作。  
  - 同步問題在第5章中有詳細討論。

### 進程間通信 – 消息傳遞

- **消息傳遞**是一種讓進程之間進行通信和同步其行動的機制。
- 消息系統使得進程之間可以相互通信，而不需要依賴共享變量。
- 進程間通信（IPC）功能提供兩種操作：
  - **send(message)**：發送消息。
  - **receive(message)**：接收消息。
  
- 消息的大小可以是固定的或可變的。 

這兩種進程間通信的機制各有其適用場景，根據具體需求選擇合適的方式可以提高系統的效率和靈活性。
### 進程間通信的步驟

如果進程 P 和 Q 希望進行通信，它們需要：

1. **建立通信連結**：在它們之間創建一個通信通道。
  
2. **通過發送/接收消息進行交換**：使用消息傳遞來互相交流。

### 通信連結的實現

#### 物理層面：
- **共享記憶體**：進程之間通過訪問同一段記憶體區域進行通信。
- **硬體總線**：通過硬體接口進行數據傳輸。
- **網絡**：在不同的機器或系統之間進行通信。

#### 邏輯層面：
- **直接或間接**：
  - **直接通信**：進程直接指定彼此作為通信的對象。
  - **間接通信**：進程通過中介（如消息隊列）進行通信。

- **同步或異步**：
  - **同步通信**：發送進程在接收到接收進程的確認之前會被阻塞。
  - **異步通信**：發送進程不需要等待接收進程的確認即可繼續執行。

- **自動或顯式緩衝**：
  - **自動緩衝**：系統自動管理消息的緩存。
  - **顯式緩衝**：開發者需要明確指定消息的緩存行為。

這些實現方式和選項的選擇取決於具體的應用需求和系統設計。
### 直接通信（Direct Communication）

- **進程明確命名**：進程必須顯式指定彼此的名稱。
  - `send(P, message)`：將消息發送到進程 P。
  - `receive(Q, message)`：從進程 Q 接收消息。

#### 通信連結的屬性：
- **自動建立**：連結在進程之間自動建立。
- **唯一性**：每一對通信進程僅與一個連結相關聯。
- **單一連結**：每對進程之間僅存在一個連結。
- **方向性**：該連結可以是單向的，但通常是雙向的。

### 間接通信（Indirect Communication）

- **郵箱（或端口）**：消息是指向郵箱中發送和接收的。
  - 每個郵箱都有一個唯一的識別碼。
  - 只有當進程共享一個郵箱時，才能進行通信。

#### 通信連結的屬性：
- **共享郵箱**：只有在進程共享公共郵箱的情況下才會建立連結。
- **多進程關聯**：一個連結可以與多個進程相關聯。
- **多連結共享**：每對進程可以共享多個通信連結。
- **方向性**：連結可以是單向或雙向的。

### 操作
- **創建新郵箱（端口）**。
- **通過郵箱發送和接收消息**。
- **銷毀郵箱**。

#### 原語定義：
- `send(A, message)`：將消息發送到郵箱 A。
- `receive(A, message)`：從郵箱 A 接收消息。

### 郵箱共享

- 進程 P1、P2 和 P3 共享郵箱 A。
- P1 發送消息，P2 和 P3 接收。

#### 誰接收消息？
- **解決方案**：
  1. 允許一個連結僅與最多兩個進程相關聯。
  2. 僅允許一個進程同時執行接收操作。
  3. 允許系統任意選擇接收者，並通知發送者接收者是誰。 

這些策略可以幫助確保消息的正確傳遞和接收者的選擇，解決進程之間的通信問題。
### 同步（Synchronization）

進程間通信中的消息傳遞可以是阻塞的或非阻塞的，這影響著進程之間的同步方式。

#### 阻塞通信（Blocking Communication）(重點)
- **阻塞被視為同步**。在這種模式下，發送和接收操作會使進程等待。
  - **阻塞發送**（Blocking Send）：發送者在消息被接收之前會被阻塞，無法繼續執行。
  - **阻塞接收**（Blocking Receive）：接收者在有消息可用之前會被阻塞，無法繼續執行。

#### 非阻塞通信（Non-blocking Communication）(重點)
- **非阻塞被視為異步**。在這種模式下，進程不會因為發送或接收操作而等待。
  - **非阻塞發送**（Non-blocking Send）：發送者發送消息後可以立即繼續執行，而不需要等待接收者。
  - **非阻塞接收**（Non-blocking Receive）：接收者接收一條有效的消息，或者如果沒有可用消息，則接收一個空消息（Null message）。

### 不同的組合
- 根據進程的需求，可能會出現不同的阻塞和非阻塞組合。例如：
  - 如果**發送**和**接收**都是阻塞的，則會發生**會合（Rendezvous）**，即發送者和接收者都必須在此時互相等待，直到彼此都準備好進行通信。

這些同步機制對於確保進程間的有效通信和協調是至關重要的。
### 生產者-消費者問題的簡化版本

在這個簡化的生產者-消費者模型中，生產者和消費者之間的通信通過消息傳遞來實現，以下是具體的實現：

#### 生產者進程

```c
message next_produced; 
while (true) {
    /* 生產一個項目到 next_produced 中 */
    // 這裡添加生成項目的代碼，例如：
    // next_produced = produce_item();
    
    send(next_produced);  // 發送生成的項目
}
```

#### 消費者進程

```c
message next_consumed;
while (true) {
    receive(next_consumed);  // 接收消息，從而獲得項目
    /* 消費 next_consumed 中的項目 */
    // 這裡添加消費項目的代碼，例如：
    // consume_item(next_consumed);
}
```

### 簡化分析

- **生產者**：在無限循環中，生產者生成一個項目並將其發送出去。
- **消費者**：消費者也在無限循環中，接收來自生產者的項目並進行消費。

### 特點

- **阻塞行為**：在這個模型中，`send` 和 `receive` 操作可以是阻塞的，這意味著生產者會等待直到消費者接收了消息，反之亦然。
- **簡單性**：這種方法消除了共享緩衝區的需要，簡化了同步問題，因為消息傳遞本身提供了必要的同步機制。

### 可能的改進

- 可以增加生產者和消費者的並發性，例如允許多個生產者和消費者進行通信。
- 可以考慮緩衝機制（如隊列），以支持生產者在消息尚未被消費者接收時，仍然可以繼續生成更多消息。 

這樣的模型使得生產者-消費者問題變得更加容易理解和實現，尤其是在進程間通信機制健全的情況下。
### 同步（Synchronization）

消息傳遞可以是阻塞的或非阻塞的。

#### 阻塞（Blocking）被視為同步
- **阻塞發送**（Blocking Send）：發送者會被阻塞，直到消息被接收。
- **阻塞接收**（Blocking Receive）：接收者會被阻塞，直到有消息可用。

#### 非阻塞（Non-blocking）被視為異步
- **非阻塞發送**（Non-blocking Send）：發送者發送消息後可以繼續執行，而不需等待接收者。
- **非阻塞接收**（Non-blocking Receive）：接收者可以接收：
  - 一條有效消息，或
  - 空消息（Null message）。

### 不同的組合
可能會出現不同的阻塞和非阻塞組合。例如：
- 如果**發送**和**接收**都是阻塞的，那麼會發生**會合（Rendezvous）**，即發送者和接收者都必須在此時互相等待，直到彼此都準備好進行通信。
### 生產者-消費者問題的簡化版本

```c
message next_produced; 
while (true) {
    /* 在 next_produced 中生成一個項目 */
    send(next_produced);  // 發送生成的項目
}
```

```c
message next_consumed;
while (true) {
    receive(next_consumed);  // 接收消息，獲取項目
    /* 消費 next_consumed 中的項目 */
}
```

### 翻譯

#### 生產者進程

```plaintext
消息 next_produced; 
當 (true) {
    /* 在 next_produced 中生成一個項目 */ 
    發送(next_produced); 
} 
```

#### 消費者進程

```plaintext
消息 next_consumed;
當 (true) {
    接收(next_consumed);
    /* 消費 next_consumed 中的項目 */
}
```

### 簡要說明

- **生產者**：在無限循環中，生產者生成項目並將其發送出去。
- **消費者**：消費者也在無限循環中，接收來自生產者的項目並進行消費。 

這樣的設計使得生產者和消費者之間的通信變得簡單明了。
### IPC 系統示例 - POSIX

#### POSIX 共享內存

1. **創建共享內存段**：
   ```c
   shm_fd = shm_open(name, O_CREAT | O_RDWR, 0666);
   ```
   - 首先，進程創建共享內存段。`name` 是共享內存的名稱，`O_CREAT | O_RDWR` 表示創建一個可讀可寫的內存段，`0666` 是權限設置。

2. **設置對象大小**：
   ```c
   ftruncate(shm_fd, 4096);
   ```
   - 使用 `ftruncate` 設置共享內存段的大小為 4096 字節。

3. **寫入共享內存**：
   ```c
   sprintf(shared_memory, "Writing to shared memory");
   ```
   - 現在，進程可以將數據寫入共享內存，這裡的例子是寫入字符串 "Writing to shared memory"。

### 翻譯

#### POSIX 共享內存

1. **創建共享內存段**：
   ```plaintext
   shm_fd = shm_open(name, O_CREAT | O_RDWR, 0666);
   ```
   - 進程首先創建共享內存段。`name` 是共享內存的名稱，`O_CREAT | O_RDWR` 表示創建一個可讀可寫的內存段，`0666` 是權限設置。

2. **設置對象大小**：
   ```plaintext
   ftruncate(shm_fd, 4096);
   ```
   - 使用 `ftruncate` 設置共享內存段的大小為 4096 字節。

3. **寫入共享內存**：
   ```plaintext
   sprintf(shared_memory, "Writing to shared memory");
   ```
   - 現在，進程可以將數據寫入共享內存，這裡的例子是寫入字符串 "Writing to shared memory"。
 ### IPC 系統示例 - Mach

1. **Mach 通信是基於消息的**：
   - 即使是系統調用也是以消息的形式進行的。
   
2. **每個任務在創建時獲得兩個信箱**：
   - 內核信箱（Kernel）和通知信箱（Notify）。
   
3. **只需三個系統調用來進行消息傳遞**：
   - `msg_send()`, `msg_receive()`, `msg_rpc()`。

4. **信箱是通信所需的，通過 `port_allocate()` 創建**。

5. **發送和接收消息具有靈活性**，例如當信箱已滿時，有四種選擇：
   - 無限期等待
   - 等待最多 n 毫秒
   - 立即返回
   - 暫時緩存一條消息

---

### IPC 系統示例 - Windows

1. **基於消息傳遞的通信**，通過先進的本地過程調用（LPC）機制實現。
   - 僅適用於同一系統上的進程之間。

2. **使用端口（類似於信箱）來建立和維護通信通道**。

3. **通信過程如下**：
   - 客戶端打開子系統連接端口對象的句柄。
   - 客戶端發送連接請求。
   - 服務器創建兩個私有通信端口，並將其中一個端口的句柄返回給客戶端。
   - 客戶端和服務器使用對應的端口句柄來發送消息或回調，並等待回覆。
Local Procedure Calls in Windows
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bf53d8b4e03b8efa6b8521c26f4bde60.PNG)
### 客戶端-服務器系統中的通信

#### 套接字（Sockets）(上課有講)
- **套接字**被定義為通信的端點。
- 套接字是 **IP 地址** 和 **端口號** 的組合——消息包的開頭包含端口號，用來區分主機上的不同網絡服務。
- 例如，套接字 **140.114.75.168:80** 指的是主機 **140.114.75.168** 上的端口 **80**。
- 通信是在一對套接字之間進行的。
- 所有 **1024 以下的端口** 是眾所周知的端口，用於標準服務。

#### 套接字通信
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2f5da5d0b2309532793b52fee4aed8ba.PNG)
### 遠程程序調用（Remote Procedure Calls）v.s.LPC

- **遠程程序調用 (RPC)** 抽象了網絡系統中進程之間的過程調用。
- 同樣使用端口來區分不同的服務。
- **存根（Stubs）**：客戶端代理，用於在服務器上調用實際的過程。
  - 客戶端存根負責定位服務器並打包（編組）參數。
  - 服務器端存根接收消息，解包編組參數，並在服務器上執行該過程。

---

### 管道（Pipes）(重點)

- 管道充當允許兩個進程進行通信的通道。

#### 問題：
1. 通信是單向的還是雙向的？
2. 如果是雙向通信，它是**半雙工**還是**全雙工**？
3. 進行通信的進程之間是否必須存在關係（如父子進程關係）？
4. 管道是否可以跨網絡使用？

#### 普通管道：
- 不能從創建它的進程外部訪問。通常由父進程創建，並用來與它創建的子進程通信。

#### 命名管道：(有提到)
- 無需父子進程關係即可訪問。
### 普通管道（Ordinary Pipes）

- **普通管道**允許以標準生產者-消費者模式進行通信。
  - **生產者**向管道的一端（管道的寫入端）寫入數據。
  - **消費者**從管道的另一端（管道的讀取端）讀取數據。
  
- 因此，普通管道是單向的。

- 需要通信進程之間存在**父子進程關係**。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b9c29e1f1fb54f6045ddad482a7d95a1.PNG)


- 在 **Windows** 中，這些被稱為 **匿名管道**。

- 可參考課本中的 Unix 和 Windows 代碼示例。
### 命名管道（Named Pipes）

- **命名管道**比普通管道更強大。
- 通信是**雙向的**。
- 通信進程之間**不需要父子進程關係**。
- 多個進程可以使用命名管道進行通信。
- 在 **UNIX** 和 **Windows** 系統中都提供了命名管道。
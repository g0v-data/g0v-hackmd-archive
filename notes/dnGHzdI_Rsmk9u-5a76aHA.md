# 該死的os
## 重點
* Clustered systems vs. multiprocessor system (chap 1 page 38-47)
    *  Clustered systems是將多台計算機連接在一起形成一個系統，每台計算機都具有自己的處理器、記憶體和儲存設備。 Clustered systems可以通過網路進行通訊，並共享資源。
    * multiprocessor system是一台計算機中包含多個處理器的系統。multiprocessor system中的處理器可以共享記憶體和儲存設備，但它們通常在同一塊主機板上。
    
        * 兩者之間的差異主要體現在以下幾個方面：

        結構：Clustered systems由多台計算機組成，每台計算機都是獨立的實體。multiprocessor system統則是一台計算機，其中包含多個處理器。
        
        擴展性：Clustered systems可以通過增加新的計算機來擴展。multiprocessor system統則需要更換主機板才能擴展。
        
        成本：Clustered systems的成本通常高於multiprocessor system。
        
        可靠性：Clustered systems中如果有一台計算機出現故障，其他計算機可以繼續運行。multiprocessor system中如果一個處理器出現故障，整個系統可能會停止運行。
        
        應用場景：Clustered systems通常用於高性能計算（HPC）和高可用性（HA）應用。multiprocessor system則通常用於桌上型電腦、筆記型電腦和伺服器等應用。
* Clustered Systems (chap 1 page 43)
* multiprocessor(chap 1 page 38):
    * 優勢：
        - 增加吞吐量
        - 大多數系統使用對稱多處理（SMP）
        - 每個對等CPU處理器執行所有任務，包括作業系統功能和使用者程序。
        - 許多進程可以同時運行而不會導致效能顯著下降。
    - 現代作業系統（如Windows、macOS、Linux、Android和OS等）都支援SMP
    - 非對稱多處理
    - 每個處理器被分配一個特定的任務。
    - 例如，主處理器安排和分配工作給工作處理器。
* ~~Monolithic system ~~(chap 2 page 66-71)
* ~~Monolithic system vs Microkernel ~~(ch2 79)
    * Monolithic:作業系統被寫成一組過程，每個過程在需要時可以呼叫任何其他過程。
    * Microkernel:僅在作業系統核心中提供了一小組必要的基本功能。
* Systems(chap 2 page 79)
* Real-Time(chap 1 page 133)：
    即時系統能夠在指定或確定的時間內完成系統功能和外部或內部、同步或非同步時間做出回應的系統。特點: 任務具有一定的時間約束

* Embedded(chap 1 page 129)
    * 嵌入式系統是一種結合了計算機硬體和軟體，可能還包含額外的機械部件或其他組件，旨在執行特定任務的系統。
* bootstrap:
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_809e48086a032f22641c6b5804395289.png)
    **初始化硬體：**bootstrap首先會初始化硬體，包括處理器、記憶體、儲存設備等。
    **載入作業系統：**bootstrap會載入作業系統的核心（kernel），並將控制權交給核心。
    
* System Call：
    當User Process於執行過程中，若需要O.S.提供服務時，則User Process會發出此中斷通知O.S.，提供所指定的Service。
    
*  interrupt: v.s trap
    trap:
    Software-Generated Interrupt. 
    User Process需要O.S.提供時會發出
    當有錯誤的數學運算 (Arithmetic Errors) 發生時 (e.g., 除0)
    
    interrupt:
    Hardware-Generated Interrupt. 
    I/O device 發出 “I/O Complete”中斷
    
* interrupt
  中斷 (Interrupt) 是電腦架構中一個重要的部份，每個電腦的設計均擁有自已的中斷技術。
        1) O.S.要求系統 (CPU)暫停目前Process的執行，同
        時保存其當時執行的狀態。
        2) 根據Interrupt ID去查詢Interrupt Vector，以便可以
        找到相對應ISR之起始位址。
        3) Jump to 相對應的ISR之起始位址，系統執行ISR。
        4) ISR執行完畢，將控制權交回給O.S.。
        5) Resume原先中斷前的Process之執行

* microkernel:
    * 自核心移走一些非必要性的模組，這些模組交由System Program或User Program來製作，如此可得到 Kernel稱之。
    
* Fault-tolerant system
* Virtualbox：
    *    虛擬機
* multiprogramming：
    透過CPU Scheduling的技巧，讓CPU在許多不同的Process之間切換(即：Context Switch)，使得CPU總是有事可做 (always busy)。
    
    當某個Process取得CPU正在執行時，若因為某個事件發生 (e.g., wait for I/O complete…etc.)而需被迫暫停時，此時O.S. 透過CPU排班(CPU Scheduling) 將CPU切換給其它需要的Process使用。因此，若系統內存在許多欲獲得CPU執行的Processes，則可以讓CPU always busy，故CPU不致於Idle。

* ~~monolithic:~~

* PCB：
    * 每個進程在作業系統中由一個進程控制塊（PCB）表示。
    * PCB也稱為任務控制區塊。
    * PCB是一個資料結構，包含與特定流程相關的資訊。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_65170ec1b8fc88de2323aeb3ee089634.png)

* many to many:
    * 多個User Threads對應到多個（個數少於或等於使用者執行緒個數）kernel threads
        * 多對一模式可以產生它所需要的執行緒 數量，但因為核心一次只能使用一個執行緒，所以數個執行緒不能真正的在多處理器的環境下並行執行
        * 一對一模式雖然可以提供較強的並行能力，但不能產生太多的的執行緒
    * Programmer或O.S.可以產生所需要的 Thread數目，使其在多處理器上並行執 行;另外，當一個Thread暫停執行時，O.S. 可以安排另一個Thread接著執行。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7abd71d204a09ce89c1a7fe842e08499.png)

* many to one:指多個user threads 對應到一個kernel threads
    * 優：執行緒主要的管理動作是在使用者 空間執行，所以很有效率。
    * 缺：
    1. 如果有任何一個User Level的Thread執行暫停的系統呼叫，將造成整個行程暫停執行。 
    2. 雖然這個模式可以產生它所需要的Thread數量，但因為只有一個Kernel Thread 可以存取Kernel，O.S.一次只能使用一個執行緒，且O.S.不知道有這些User Threads存在，無法將 Block以外的Thread配給其它的處理器，所以數個執行緒不能在多個處理器上並行執行
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9798d1b256fcab67cd3a9e911b721180.png)

上並行執行。
* dual-mode operation：
    * 當發生中斷（硬體中斷或軟體中斷）或陷阱時，硬體會切換到kernel mode以執行操作系統代碼。
    * 完成後，系統會切換到用戶模式，並將控制權返回以執行用戶代碼。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_df01ddfc62a03a63db678d3ee4ed8a67.png)

* The dual-mode為我們提供了保護作業系統免受錯誤使用者和保護錯誤使用者免受彼此傷害的手段。
* ~~operating-system design~~
* producer-consumer problem:
    * 合作進程的範式，生產者進程產生由消費者進程消耗的資訊。
    * 例如，Web 伺服器（生產者）和 Web 瀏覽器（消費者）。
    * 無界緩衝區：緩衝區大小無限。
    * 有界緩衝區：固定緩衝區大小。
    * 緩衝區可以由作業系統透過使用訊息傳遞設施提供，也可以由應用程式設計師使用共享記憶體明確編碼。
    
    Producer 會把 data 放在有限或是無限的buffer 中等 Consumer來拿，要確保 Producer 不會在 buffer 滿的時候加入 data ，而 consumer 不會在 buffer 空的時候拿 data
    
* memory layout of a Multiprogramming System
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7ecf6f25e2e619f574852f23ba3d2905.png)

* memory layout of a process
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_60535c35b4033e44adc7dde6add02830.png)

* context:
    * context在其進程控制區塊 (PCB) 中表示，包括 CPU 暫存器的值、進程狀態和記憶體管理資訊。
* context-switch act：
    * 當 CPU 切換到另一個行程時，系統必須透過上下文切換儲存舊行程的狀態，並載入新行程的儲存狀態。
    
    * 上下文切換時間純粹是開銷；在切換期間，系統不會執行有用的工作。
    * 典型的速度為數微秒。
    * 上下文切換時間高度依賴硬體支援。
```
儲存目前處理上下文
載入下一個進程上下文
更新核心資料結構
切換記憶體映射
復原執行
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c7adf2075a7e0fee6962eaf5044807cb.png)

* one-to-one multithreading model
    * 每一個User Thread都對應到一個kernel thread  當一個使用者執行緒處於暫停或是等待的狀態時，其它的執行緒都還可以執行。
    * 它比多對一模式提供了更多的並行功能，也允許多個thread 在multiprocessor上並行執行
    * 產生一個User Thread時，需連帶產生一個Kernel Thread，而Kernel Thread會對程式的執行產生一些額外的負擔。所以此模式限制執行緒的個數
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ec1bba9e8849467084fe77c058988dd0.png)

* ~~loadable kernel modules approach~~

* microkernel and the loadable kernel modules extensibility, performance, and security/pros cons
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a7dd36465e6724ee1ae7d81c27fa51ca.png)
* ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c29a1316eb045a5452d6e5b313d21bab.png)
* microkernel
    * 優：
        * 更容易擴展微內核
        * 更容易將作業系統移植到新的架構
        * 提供更多安全性和可靠性
    * 缺：
        * 微核心可能會因係統功能開銷的增加而導致效能下降。
* loadable kernel modules
    * 優：
    * 缺：

* shared memory vs. message passing：
    * message passing:
        * 用於交換較小量的數據，因為不需要避免衝突
        * 對於跨電腦通信，比共享記憶體更容易實現
    * shared memory
        * 允許以最大速度和便利性進行通信，因為在電腦內部進行通信時可以以記憶體傳輸速度進行
        * 需要保護和同步。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b04f6332fdffe6603c81e508d390997e.png)

* shared memory:
    * 資料的形式和位置由這些進程決定。
    * 這些進程負責確保它們在不同時寫入相同的位置。
    * 需要保護和同步。
* message passing：
    * 透過作業系統提供的進程間通訊設施交換資訊。
    * 資訊可以透過共同的郵箱直接或間接地在進程之間交換。
    * 要進行通訊的程序可以位於同一台電腦或不同的電腦上。
* Time-Sharing System：
    * 將時間分割為間隔或時間片段，然後限制一項作業一次只能執行一個時間片段的技術。
    * 在每個時間片段結束時，目前作業被擱置，允許另一個作業在下一個時間片段內執行。
    * 透過以這種方式迅速切換作業，創造了多個作業同時執行的假象。
* uniform Memory Access system：從任何 CPU 存取任何 RAM 的時間都是相同的。
* Non-uniform Memory Access (NUMA) System：CPU 對記憶體的某些部分比對其他部分有更快的存取速度。
* Free Software Foundation(FSF) 應該是Open source：Richard Stallman 和自由軟體基金會 (FSF) 鼓勵自由交流軟體原始碼以及自由使用該軟體鼓勵分享和改進
* Fault-tolerant system：可以承受任何單一組件故障但仍能繼續運作的系統，例如 HP NonStop 系統（前身為 Tandem）系統利用硬體和軟體的重複來確保在故障時繼續運作。
* layer OS
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6aeae7ef1b9c67edda4e3cd4e485afe6.png)
* monolithic kernel：提供檔案系統、CPU調度、記憶體管理和其他作業系統功能；將大量功能結合到一個層級。
    * 優：系統呼叫介面的開銷小，核心內部的通訊快速
    * 缺：它們很難實現和擴展
* memory layout of a process
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_34f2be017bb4c98c6869cdd7ce5db777.png)
```
stack:存放temporary data(ex:local variables、function call)
heap: 動態配置的記憶體空間
data: 存放global variables
text: 存放程式碼
context 儲存 process 的狀態，PCB、PC、SP、base、limit…
```
* multithreaded application perform on multiprocessor system  vs. a single-processor system
    * 能充份利用Multiprocessing架構的效益，因為同一 個Process的不同Threads可以同時在不同的CPU執 行
*  single-processor system(chap 1 page 37)
    * Single-Processor Systems:一台電腦只有單一顆CPU

    * Multiprocessor Systems:一台電腦有多顆CPU可以處理執行的程式(Process)

        * 特點:
            共享相同的記憶體空間、I/O Device、Bus
            多個CPU之間的溝通(指Data交換)，大部份是採Share Memory技術
        * 優點:
            穩定度高
            處理效率較佳
        * Multiprocessor Systems分兩種種類:
            Symmetric Multiprocessing: 對稱式多元處理
            每一個Processor具有相同的功能。
            可靠度 (Reliability) 較高，當某一個Processor壞了，則在其
            上未完成的工作可以轉移到其它的Processor繼續執行。∴
            系統不會整個Crash。
            強調Load Balance (負載平衡)，希望在每一個Processor上的
            負擔均等。

            Asymmetric Multiprocessing: 非對稱式多元處理
            每個 (或某群) Processor 各自負責不同的工作 (功能)，通常具有一個
            Master Processor負責控制、協調及分配Process到其它的Processors去運
            作。其餘的Processors稱為Slave Processor。
            又稱為Master/Slave 架構。
            通常效能比SMP佳，但可靠度較差


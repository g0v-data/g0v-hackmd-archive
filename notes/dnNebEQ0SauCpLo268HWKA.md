# OS
http://debussy.im.nuu.edu.tw/sjchen/OS_Final.html
https://hackmd.io/@thisishunglee/SklStC0X9

## 第一章
**os是什麽**
作業系統是一種管理電腦硬體的軟體，它充當電腦使用者和電腦硬體之間的中介程式。 其主要目的是為使用者提供一個方便且有效率的環境，以執行程式。 作業系統充當資源分配器，管理所有資源，並在衝突請求之間做出決策，以實現高效和公平的資源利用。 此外，它還充當控製程序，管理使用者程式的執行，以防止錯誤和不當使用電腦。
`test`

**kernel**
核心是作業系統的核心部分，負責管理電腦硬體資源、進程、檔案系統、記憶體以及裝置驅動程序，以提供應用程式運行所需的基本功能和資源。 它是作業系統的關鍵組件，始終在電腦上運行，協調和控制各項任務。

**Boostrap**
cpu到rom喚醒boostrap,接著boostrap再從disk載入os的kernel到ram,然後cpu再執行kernel

**GUI shell**
用戶登入成功後，GUI shell會從disk載入到ram裏面，例如：桌面背景、工作列、啟動選單和圖形界面

**application program**
使用者可以使用 GUI Shell 啟動和管理各種應用程式。 他們可以點擊應用程式圖標、使用啟動選單、鍵盤快捷鍵等方式來運行應用程式。

**interrupt**
發生一個事件時,通常是由硬體或軟體產生interrupt來通知，硬體可以在任何時間傳出hardware signal送給cpu來觸發中斷，軟體可以藉由執行一項特殊的system call也叫monitor call來觸發中斷

**interrupt driven**
中斷驅動，如果沒有程式要執行，沒有I/O裝置要服務，也沒有使用者需要回應，作業系統就會靜靜地待在那邊，等待某些事情發生

**interrupt service routine (ISR)** 
是中斷服務程式的縮寫，它是用來處理中斷事件的一段程式碼。 中斷可以是由硬體引發（如設備故障或定時器中斷）或由軟體觸發（透過系統呼叫）。 當中斷發生時，作業系統需要知道要執行哪個中斷服務例程來處理特定的中斷事件。 這個資訊通常包含在中斷向量表中（interrupt vector)，該表中包含了各個中斷的服務例程位址。

**interrupt vector** 中斷向量表是一個資料結構，它包含了每個中斷事件的唯一識別碼和對應的中斷服務例程的位址，用於幫助作業系統確定如何處理特定中斷事件。 中斷向量的使用使系統能夠有效率地管理和回應多個中斷。

**Interrupt architecture** 
是電腦系統的一部分，負責管理中斷處理的硬體和軟體機制。 它必須確保中斷事件被適當地識別、分派到正確的ISR，並在處理中斷後能夠恢復中斷前的執行狀態。

I/O 设备准备好：当一个 I/O 设备（如硬盘、键盘、鼠标、网络接口等）完成一个任务或者需要处理一个请求时，它会产生一个中断信号。

中断请求：I/O 设备向计算机的中断控制器发送中断请求信号，通常是一个特定的电信号或信号线的变化。

**I/O 设备产生中断的流程：**
I/O 裝置準備好：當一個 I/O 裝置（如硬碟、鍵盤、滑鼠、網路介面等）完成一個任務或需要處理一個請求時，它會產生一個中斷訊號。

中斷請求：I/O 設備向電腦的中斷控制器發送中斷請求訊號。

中斷控制器處理：中斷控制器接收到來自不同設備的中斷請求，然後將它們優先排隊，以確定哪個中斷應該被處理。 

CPU 回應中斷：當中斷控制器決定要處理哪個中斷時，它會傳送一個中斷請求給 CPU。 CPU 接收中斷要求後，會停止目前正在執行的程序，並跳到一個特定的處理程序，稱為中斷服務例程（ISR）。

中斷服務例程執行：中斷服務例程是一個特定的程序，它由作業系統或應用程式編寫，用於處理特定中斷事件。 中斷服務例程執行必要的操作，例如從裝置讀取資料、傳送資料至裝置、處理輸入、更新資料結構等。

中斷處理完成：一旦中斷服務程式完成了相關操作，CPU會繼續先前中斷的程式的執行。 這通常需要保存和還原中斷前的執行狀態，以確保程式在中斷處理後繼續正常運作。

**I/O Structure (Cont.)**
在啟動I/O操作時，設備驅動程序會配置設備控制器的暫存器。設備控制器檢查這些暫存器，然後執行相應的I/O請求。如果請求是讀取數據，控制器會開始將數據從設備傳輸到本地緩衝區。當數據傳輸完成時，設備控制器通過觸發中斷通知CPU，告知它已完成操作。

**DMA（Direct Memory Access）I/O**
是一種資料傳輸技術，它允許外部設備（如硬碟、網路適配器、音訊設備等）直接存取電腦內存，而無需透過中央處理器（CPU）的直接幹預。 這種技術的主要目的是提高資料傳輸的效率和減輕 CPU 的負擔。

在傳統的 I/O 操作中，CPU 負責控制資料的傳輸，它需要不斷地將資料從外部裝置讀入記憶體或將資料從記憶體傳送到外部裝置。 這樣的過程需要 CPU 的持續介入，導致 CPU 的效能使用率較低。

DMA I/O 解決了這個問題，它引入了一個稱為 DMA 控制器的硬體元件。 DMA 控制器允許外部裝置與記憶體之間的資料傳輸，而 CPU 只需設定傳輸參數和啟動傳輸，然後可以繼續執行其他任務。 DMA 控制器負責實際的資料傳輸，包括讀取資料、寫入資料以及在需要時觸發中斷以通知 CPU 傳輸完成。

裝置控制器將整個資料區塊直接傳輸到主記憶體，或從主記憶體傳輸到自己的緩衝記憶體，無需 CPU 幹預。
每個資料塊只產生一個中斷，而不是對於低速設備每個位元組產生一個中斷。
在裝置控制器執行資料傳輸時，CPU 可以自由執行其他任務。

**現代電腦系統如何運作**
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b20fc376c31e91c2123e49c54a3d5d82.png)
execution cycle:執行週期

儲存結構：
- 速度
- 成本
- 大小
- 揮發性（指資料斷電後是否會遺失）
- 快取
- 將資訊複製到更快的儲存系統；主記憶體可以看作是輔助儲存的快取。

**多處理器系統的主要優勢：**
- 增加了吞吐量
- 大多數系統使用對稱多處理（SMP）架構
- 每個對等的CPU處理器執行所有任務，包括作業系統功能和使用者程序。
- 可以同時運行許多進程，而不會導致效能明顯下降。
- 現代作業系統（如Windows、macOS、Linux、Android等）都支援SMP。
- 不對稱多處理
- 每個處理器被分配一個特定的任務。
- 例如，主處理器負責調度和分配工作給工作處理器。 

**Memory Access Model：**
"記憶體存取模型" 指的是多處理器系統中，不同的處理器（CPU）如何存取共享記憶體以及存取的延遲方式。 "均勻記憶體存取（UMA）" 是一種儲存模型，表示任何處理器都可以以相同速度和延遲存取共享內存，通常與對稱多處理（SMP）架構相關。 在SMP架構中，多個處理器共享相同的內存，而不會導致不同處理器的存取延遲不同。 這有助於簡化並行程式設計，因為不需要擔心特定處理器的記憶體存取速度比其他處理器慢。

**多道程式設計系統所需的作業系統功能：**
記憶體管理
CPU 調度
系統必須選擇下一個準備在記憶體中運行的作業，以便由CPU下一步運行
並發控制
同時執行多個作業需要限制它們在作業系統的各個階段（包括進程調度、磁碟儲存和記憶體管理）對彼此的影響。

**並發執行（Concurrent Execution）**
是指在電腦系統中同時執行多個任務或進程的能力。 這些任務可以在同一時間段內交替執行，而不是在一個任務完全執行完後再執行下一個任務。 並發執行可以提高系統資源的使用率和效能，特別是在多核心處理器和多任務作業系統中。

在同時執行中，各個任務之間可能會以不同的方式相互影響，因此需要採取適當的並發控制措施，以確保資料的一致性和避免衝突。 作業系統和程式語言提供了各種工具和機制來實現並發執行，如進程、執行緒、鎖定、信號量等。 這些機制允許多個任務在共享資源的同時安全地進行操作，以實現更高的系統效率。

**如果發生無限loop會怎麽樣：**
系統資源耗盡：無限loop會佔用系統資源，例如記憶體和CPU時間。如果系統資源耗盡，可能會導致其他應用程式無法正常運行。

**Operating-System Operations**
作業系統 (OS) 必須能夠處理中斷，中斷是表示需要採取某些措施的事件。對於每種中斷類型，OS 都有一個稱為中斷服務例程 (ISR) 的獨立程式碼段，用於確定要採取的動作。
其他進程問題包括無限循環，在這種情況下，進程會陷入循環而無法完成，以及進程修改彼此或 OS，如果修改不正確，可能會導致問題。
一個設計良好的 OS 必須能夠保護自己免受惡意程式攻擊，這些程式可能會試圖導致其他程式或 OS 本身執行不正確。
雙模式和多模式操作是 OS 可以用來保護自己免受惡意程式的兩種方式。雙模式操作允許 OS 在兩種模式之間切換：用戶模式，用戶程式在其中運行，特權模式，OS 本身在其中運行。在特權模式下，OS 可以訪問計算機的所有資源，而在用戶模式下，用戶程式只能訪問他們已被明確授予的資源。這使得惡意程式更難損壞 OS 或其他程式。
多模式操作是一種更高級的保護形式，允許 OS 在單獨的內存空間中運行多個進程。這意味著進程不能修改彼此的內存，這有助於防止問題。
計時器是 OS 用來跟踪時間並確保進程不會運行太長時間的一種方式。如果進程沒有響應計時器中斷，OS 可以終止它。

**Dual-Mode & Multimode Operation**
作業系統 (OS) 程式碼和使用者定義程式碼的執行必須有所區別。
大多數計算機系統都提供硬體支援，至少可以區分兩種操作模式：
在計算機硬體中添加一個模式位來指示當前模式。
用戶模式 (1)
代表使用者執行
核心模式 (0) (也稱為監控模式、系統模式或特權模式)
代表作業系統執行
額外說明：
在雙模式操作中，作業系統在核心模式下執行，而使用者程式在用戶模式下執行。
在核心模式下，作業系統可以訪問計算機的所有資源。
在用戶模式下，使用者程式只能訪問他們已被明確授予的資源。
多模式操作是雙模式操作的一種擴展，允許作業系統在單獨的內存空間中運行多個進程。這意味著進程不能修改彼此的內存，這有助於防止問題。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_60f4a6d6bf7b988fbcc24630db1a66a9.png)
這張圖在說disks把application載入ram等待cpu執行，當cpu從ram從ram讀取Appl指令並執行時因A=5/0發生exception所以cpu將控制權轉移到exception handler，exception handler程序完成後，它將控制權返回到 CPU。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_634897c1a4cd1a5cfd8ed2dced1761aa.png)

這張圖表示作業系統的雙模式操作。雙模式操作是一種保護機制，可防止使用者程式直接訪問計算機的硬體和其他資源。

在圖中，CPU 有兩種模式：
用戶模式：用戶程式在用戶模式下運行。在用戶模式下，使用者程式只能訪問他們已被明確授予的資源。
核心模式：作業系統在核心模式下運行。在核心模式下，作業系統可以訪問計算機的所有資源。
當使用者程式需要訪問硬體或其他資源時，它必須發出系統呼叫。系統呼叫是一種指令，它會將控制權轉移到作業系統。作業系統在核心模式下處理系統呼叫，並採取適當的措施。

圖中的詳細說明如下：
CPU 在用戶模式下執行使用者程式。
使用者程式發出系統呼叫。
CPU 將控制權轉移到作業系統。
作業系統在核心模式下處理系統呼叫。
作業系統完成系統呼叫後，將控制權返回到 CPU。
CPU 恢復到用戶模式，並繼續執行使用者程式。
雙模式操作提供了以下優點：

它可以防止使用者程式直接訪問計算機的硬體和其他資源。
它可以防止惡意程式損壞計算機或其他程式。
它可以提高系統的安全性和穩定性。

**Privileged Instructions（特權指令）：**
可能導致系統損壞的指令，只能在核心模式下執行。
例如：切換到核心模式的指令、I/O 控制、計時器管理、中斷管理等。
如果在使用者模式下嘗試執行特權指令，硬體會將其視為非法操作並將其交給作業系統。

**Multimode Operation（多模式操作）：**
大多數現代作業系統，如 Windows、UNIX 和 Linux，都利用了這種雙模式特性，並為作業系統提供了更強大的保護。
越來越多的 CPU 支援多模式操作。
例如，一些 CPU 支援虛擬化。
虛擬機器管理程式 (VMM) 模式用於來賓虛擬機器。
由各種核心組件使用的不同模式。
例如，Intel 64 系列 CPU 支援 4 個特權等級（保護環）並支援虛擬化。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_67a06924befc06872c728085700358e0.png)
(1) 應用程式需要訪問作業系統服務。
(2) 應用程式向作業系統發出系統呼叫。
(3) 系統呼叫將應用程式切換到核心模式。
(4) 作業系統處理系統呼叫。
(5) 作業系統返回到用戶模式。
(6) 應用程式繼續執行。

**System call:**
系統呼叫是使用者程式請求作業系統代表使用者程式執行任務的方式。
它通常透過將控制權轉移到中斷向量表中的特定位置來實現。
此中斷可以使用通用中斷指令執行，但有些系統具有專用的系統呼叫指令來呼叫系統呼叫。
當執行系統呼叫時，硬體將其視為軟體中斷。


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ac7aeef06cf3d2687a795b602d5edc81.png)
在本例中，應用程式需要訪問磁碟驅動器。因此，應用程式向作業系統發出系統呼叫。系統呼叫將應用程式切換到核心模式，然後作業系統會處理系統呼叫。作業系統會向磁碟驅動器發出命令，然後返回到用戶模式。
Mode bit 是指處理器的一個位元，它用來指示處理器目前處於哪種模式。
Return mode bit 是指處理器的一個位元，它用來指示處理器返回到用戶模式時是否需要執行返回棧。
Trap 是指處理器在執行非法指令或訪問非法記憶體地址時發生的異常。
在本例中，如果應用程式在用戶模式下嘗試訪問磁碟驅動器，則處理器會將其視為非法操作並將其轉交給作業系統。作業系統會向應用程式返回一個錯誤消息。

**system call的過程如下：**
應用程式將系統呼叫編號存儲在一個暫存器中。
應用程式將系統呼叫的參數存儲在其他暫存器中。
應用程式向作業系統發出一個中斷。
中斷處理程序將處理器切換到核心模式。
作業系統將應用程式的系統呼叫編號和參數從暫存器中讀取出來。
作業系統處理系統呼叫。
作業系統將結果返回給應用程式。
作業系統將處理器切換回用戶模式。

**timer:**
防止 CPU 資源被使用者程式卡住（即，陷入無限循環）
為了確保作業系統保持對 CPU 的控制，可以設定計時器在指定的時間段後中斷電腦。
在安排進程之前設定以重新獲得控製或終止超出分配時間段的程序
時間段可以是固定的，也可以是可變的。
使用計時器來防止用戶程式運行太長時間。
用允許的執行時間初始化計數器


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_da05d0bda2805600a51c5f27f56cda4e.png)
在圖片中，CPU 是中央處理器，它是計算機的運算核心。計時器是一種硬體設備，它可以用來定時事件。
在圖片中，計時器將在程序執行了一段指定的時間後中斷程序。這段時間稱為計時器的周期。
如果程序在計時器周期內沒有完成，則它將被中斷。中斷是指將處理器的控制權從程序轉移到作業系統。
作業系統可以使用中斷來做幾件事，例如：
檢查程序是否有錯誤。
終止程序。
將程序調度到另一個 CPU 核心。
在圖片中，作業系統使用計時器來防止程序執行太長時間。這可以防止程序在無限循環中卡住或佔用過多的 CPU 資源。
具體來說，作業系統會在程序開始執行時設置計時器。計時器將在程序執行了一段指定的時間後中斷程序。
如果程序在計時器周期內沒有完成，則作業系統將中斷程序。作業系統可以檢查程序是否有錯誤，或終止程序。
在某些情況下，作業系統可能會將程序調度到另一個 CPU 核心。這可以防止程序佔用過多的 CPU 資源。

Process Management
進程是正在執行的程式。
程序本身不是進程。
程式是一個被動的實體，就像磁碟上儲存的檔案內容一樣，而進程是一個活躍的實體。
進程需要資源才能完成其任務
CPU 時間、記憶體、I/O、文件
初始化數據
進程終止需要回收任何可重複使用的資源。 回收利用

Program vs Process
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0178c4e9d842a25503c40596b8c0688f.png)
例子:一個program可以是一個文本文件，它包含了用於顯示“Hello, world!”的程式碼。當這個program被操作系統執行時，它就成為了一個process。這個process會在 CPU 上執行程式碼，並顯示“Hello, world!”。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c156a45098bbec721d9b11531c621e67.png)
創建：當用戶啟動一個程式時，操作系統會創建一個進程來執行該程式。
就緒：當進程被創建後，它會處於就緒狀態，等待 CPU 的調度。
執行：當進程被調度到 CPU 上時，它會處於執行狀態，並在 CPU 上執行指令。
阻塞：當進程需要等待某些事件發生時，它會處於阻塞狀態。例如，如果進程正在等待 I/O 操作完成，它就會處於阻塞狀態。
終止：當進程完成其任務或發生錯誤時，它會被終止。
在圖中，每個進程都由一個進程控制塊（PCB）表示。PCB 包含了進程的所有信息，包括進程的狀態、進程的上下文、進程的資源等。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8e5e89a5ec57dd669d58e6fb649d4f6e.png)
在圖中，進程 A 正在 CPU 上執行。當進程 A 需要等待 I/O 操作完成時，它會被阻塞。在這個時候，作業系統會將 CPU 切換到進程 B。當 I/O 操作完成後，進程 A 會被解除阻塞，並重新回到就緒狀態。
總而言之，這張圖顯示了作業系統如何管理進程的控制。進程控制是作業系統的重要功能，它允許作業系統有效地管理多個進程。

**Memory Management:**
內存管理是指操作系统如何分配和使用內存資源。
內存管理的主要目的是提高 CPU 利用率和響應時間。
內存管理方案是指操作系统如何組織和管理內存空間。
硬件支持是指操作系统如何使用硬件來實現內存管理功能。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_47831224638aa98f7c4a53087e147376.png)
圖中虛擬內存的示例
在圖中，用戶程序需要分配一個 100 字節的內存塊。作業系統分配了一個虛擬地址空間給該程序，這個虛擬地址空間的大小是 200 字節。
當用戶程序訪問虛擬地址 0x1000 時，作業系統會使用虛擬內存頁表來查找相應的物理地址。頁表中沒有找到物理地址，因此作業系統將數據從磁盤讀取到物理內存中，並將物理地址映射到虛擬地址 0x1000。

**File-System Management：**
將文件組織成目錄，以便於尋找和管理。
控制對文件的訪問，以保護文件免受未經授權的訪問。
提供對檔案的操作，例如創建、刪除、讀取和寫入。
將文件映射到實體介質上，並透過儲存設備存取這些文件。
管理文件的儲存空間，以確保文件的有效儲存和使用。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1f6120cb0a68e2c22d69c5e3ab6d2b7e.png)
這張圖顯示了文件系統管理的不同活動。在圖中，文件系統管理活動被分為兩個主要類別：文件管理和目錄管理。文件管理活動涉及對文件本身的操作，而目錄管理活動涉及對目錄的操作。文件管理活動包括創建、刪除、讀取、寫入、重命名、移動和搜索文件。目錄管理活動包括創建、刪除、移動和重命名目錄。

**Mass-Storage Management**
大容量儲存是指電腦系統中用於儲存大量資料的儲存設備。
二級儲存是指電腦系統中除主記憶體之外的所有儲存設備。
主存是電腦系統中速度最快、容量最小的儲存設備。
三級儲存是指電腦系統中速度最慢、容量最大的儲存設備。
作業系統 (OS) 是電腦系統中最基本的軟體，負責管理電腦系統的各種硬體和軟體資源。
應用程式是電腦系統中用於執行特定任務的軟體。


**Secondary Storage Management：**
當使用者插入磁碟裝置時，作業系統會自動掛載該裝置。
當使用者拔下磁碟設備時，作業系統會自動卸載該設備。
作業系統會追蹤磁碟上的可用空間，並在使用者需要分配空間時提供可用空間。
作業系統會使用點陣圖來追蹤磁碟上的可用空間。
作業系統會使用鍊錶來連結檔案或目錄。
作業系統會將檔案或目錄分配到磁碟上的可用空間。
作業系統會使用磁碟調度演算法來決定磁碟存取順序。
作業系統會將磁碟劃分為多個邏輯磁碟，以提高磁碟的使用率和安全性。
作業系統會使用存取控制機制來防止未經授權的磁碟存取。

**Caching Management：**
cache是一種用於儲存臨時資料的高速記憶體。
cache通常位於CPU和主存之間。
當CPU需要存取資料時，它首先檢查cache。
如果資料存在於cache中，則CPU可以直接從cache中存取資料。
如果資料不存在於cache中，則CPU需要從主記憶體存取資料。
主記憶體比cache慢，但容量更大。
將資料從主記憶體複製到快取稱為cache命中。
將資料從主記憶體複製到cache稱為cache未命中。


**S/W Cache：**
決定快取的大小。
制定替換策略。
將檔案系統資料快取到主記憶體。
從磁碟到記憶體的資料傳輸。
將修改後的檔案系統資料寫回磁碟。

**Cache Coherency in Multiprocessor Environment：**
在多處理環境中，多個處理器共享同一個主記憶體。 每個處理器都有自己的本地緩存，用於儲存最近訪問過的資料。 如果多個處理器存取同一個記憶體位址，則每個處理器都會將其快取中的資料更新為最新的值。
但是，如果多個處理器同時修改同一個記憶體位址，則會導致資料不一致。 例如，如果處理器 A 將記憶體位址 0x1000 的值修改為 1，而處理器 B 也會將記憶體位址 0x1000 的值修改為 2，則這兩個處理器快取中的值會不一致。

**Cache Coherency一致性:**
必須確保對快取中 A 的值進行的更新立即反映在所有其他快取中，其中 A 駐留。
通常是硬體問題。
共享記憶體快取處理器 X Y 快取 Y 處理器公共匯流排連接
簡單解決方案：
當共享記憶體更改時，通知其他處理器它們的快取副本無效。 他們需要重新路由到共享記憶體。

**Cache Coherency in Distributed Environment：**
在分散式環境中，多個電腦共用同一個檔案系統。 同一個檔案可以有多個副本，分佈在不同的電腦上。 如果一個電腦修改了檔案的副本，則必須確保其他電腦上的副本也盡快更新，以保持資料的一致性。


**I/O System Management：**
輸入/輸出（I/O）子系統是電腦系統中負責處理輸入和輸出資料的子系統。 I/O 子系統包括記憶體管理元件、通用裝置驅動程式介面和針對特定硬體裝置的驅動程式。
記憶體管理元件負責管理輸入和輸出資料在記憶體中的儲存和存取。 緩衝是指將輸入或輸出資料暫時儲存在記憶體中，以提高資料傳輸的效率。 快取是指將輸入或輸出資料儲存在更快的儲存中，以提高資料的存取速度。 spooling 是作業系統協調並發輸出的一種方式。 spool 是一個緩衝區，用於容納印表機等無法接受交織資料流的裝置的輸出。
通用設備驅動程式介面是作業系統與設備驅動程式之間的一層介面。 它為作業系統提供了存取設備硬體的通用方法。
針對特定硬體設備的驅動程式是負責管理特定硬體設備的軟體。 它將硬體設備的特性映射為作業系統可以理解的介面。

**Security and Protection：**
保護機制可以執行以下功能：
阻止未經授權的使用者存取資源。
控制授權使用者的存取權限。
記錄使用者的存取行為。
偵測和回應攻擊。

**Virtualization：**
虛擬化是一種允許我們將單一電腦的硬體（CPU、記憶體、磁碟機、網路介面卡等）抽象化為多個不同的執行環境的技術，從而創建一種每個單獨的環境都在其自己 的私有計算機上運行的假象。
一台實體機可以同時運行多個作業系統，每個作業系統都在自己的虛擬機器中。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ffb89c745648b01f9e8c0d7cac7312f7.png)

**VMware Workstation(跟virtual box一樣):**
VMware Workstation 是一種虛擬化軟體，可將一台實體機器劃分為多個虛擬機器。 每個虛擬機器都可以運行自己的作業系統，就像是一台獨立的電腦一樣。 VMware Workstation 的核心是虛擬機器監視器（VMM），它負責管理虛擬機器的資源，例如 CPU、記憶體、磁碟空間和網路介面卡。 VMM 還負責保護每個虛擬機器免受其他虛擬機器的影響。

**Distributed Systems：**
在分散式系統中，多個電腦共享資源和功能。 這可以提高系統的運算速度、功能、數據可用性和可靠性。 分散式系統通常使用網路協定、網路適配器和設備驅動程式來實現通訊。 網路作業系統提供網路之間系統之間的功能，例如檔案共用、列印服務和電子郵件。 通訊方案允許不同電腦上的進程交換訊息，例如遠端過程呼叫（RPC）和訊息傳遞介面（MPI）。 分散式作業系統提供一個不太自治的環境，因為不同的電腦必須密切通訊才能提供單一作業系統控製網路的幻覺
















## 第三章
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c1d2b5713f4b1f68df28eaff75020589.jpg)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1c34117080ca7884b147850f8b0876f4.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5f6e03a7fec13092b0f7ed10a25343c3.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8606b78748e6f112b152bfa7c7ec78f2.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e53cae28f5f8429944673ff7fbb72e19.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_eb131507df4368f5c0f57327cc0a6fa9.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_779dfed54775139f92ecfa8173906d30.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_de6cd0b64902b742a787c33d45a12ea1.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d75b1c0cf0f2e13ef76dd78507ef4885.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_33574c170bd67bda48b59dfd1a8b1312.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3aaac1fbbf5fdc02500ead33995bc124.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0bf20a26e3a6f56a755c3e2503b5fc9d.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4e8cb1dd62b92a99215d2b85220e6064.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ab3203e1fa48a16be59258b96556c568.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_18db6b557841982a6933e63815f09bb2.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c5ecc7407482f1a4a3113804a1eba767.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e8ab6ff4dc5fe6364a5b210c9f886479.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_66d9cb1108e3174167d384237ad7e025.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_789e771dd8ae9a5b88ad2a49a1d24c3b.jpg)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_67a97c1feea6c98a74b7c051bd853e81.jpg)
* producer-consumer problem
    * 例如，Web伺服器（生產者）和Web瀏覽器（消費者）
    * unbounded-buffer無界緩衝：緩衝區大小無限制
    * bounded-buffer有界緩衝：緩衝區大小固定
    * buffer區可以由os提供，通過使用傳遞訊息的功能，或者可以由應用程     式開發人員明確編寫，使用shared memory。
* 3.6 訊息系統中的進程間通訊（IPC）
    * cooperating process可以在shared memory環境中進行通訊。
        * 這個方案需要process共享一個memeory區域，並且access和操作shared memory的code必須由programmer明確編寫。
    * 另一種方式是讓os提供手段，使cooperating process可以通過傳遞訊息的方式相互通訊。
    * 訊息傳遞提供了一種機制，允許進程進行通訊並同步其操作，而無需共享相同的地址空間
        * 特別適用於位於不同計算機上的通訊process
        * 例如，網際網路即時通訊程式
    * 一個message-passing設施至少提供兩個操作：
        * send(message) - 訊息大小可以是固定的或可變的
        * receive(message)
    * 如果進程 P 和 Q 希望進行通訊，它們需要：
        * 建立它們之間的communication link
        * 通過 send/receive 進行訊息交換
    * 有幾種實現連接以及 send()/receive() 操作的邏輯方法：
        * 直接或間接通訊
        * 同步或非同步通訊
        * 自動或顯式buffering
* Naming命名
    * 希望進行通訊的進程必須有一種方式來引用彼此。
        * 直接通訊Direct communication
        * 間接通訊inDirect communication
* Direct communication
    * prcess必須明確地name彼此的名稱：
        * send(P, message) - 將消息發送給process P
        * receive(Q, message) - 從process Q 接收消息
    * 此類link的特點：
        * 在希望通信的每一對process之間自動建立了一個連接。
        * 一個link與確切的兩個process相關聯。
        * 每一對process之間只存在一個link。
    * 對稱式命名 symmetric in addressing
        * send(P, message) - 將消息發送給process P
        * receive(Q, message) - 從process Q 接收消息
    * 非對稱式命名 asymmetric in addressing
        * send(P, message) - 將消息發送給process P
        * receive(id, message) - 從任何process接收消息
    * 缺點：更改process的識別符號？
        * 更改process的識別符號可能導致混淆或不明確的通信 
* inDirect communication
    * 指的是透過mailboxes(郵箱)或ports(連接埠)發送和接收訊息。 每個mailbox都有一個唯一的識別碼。 只有擁有共用mailbox的process才能進行通訊。
    - Send(A, message) - 傳送訊息至mailbox A。
    - Receive(A, message) - 從mailboxA接收訊息。
    * communication link的特性包括：
        * 只有當一對procee shared mailbox時，才會在它們之間建立連結。
        * 連結可以與多個process相關聯。
        * 一對通訊的process可以共享多個通訊鏈接，每個連結對應一個郵箱。
    * Mailbox sharing信箱分享
        * P1、P2 和 P3 共用信箱 A。
        * P1 發送；P2 和 P3 接收。
        * 由 P1 發送的訊息將由誰接收？
    * 解決方案
        * 允許一個連結最多與兩個進程相關聯。
        * 一次只允許最多一個行程執行接收操作。
        * 允許系統隨意選擇接收方。 寄件者將被通知接收者是誰。
    * mailbox可以由進程或os擁有
    * 如果一個mailbox由進程擁有，那麼： 
        * own - 可以接收從mailbox發來的消息
        * user - 可以向mailbox發送消息
    * 如果一個mailbox由os擁有，那麼os必須提供一個機制，允許進程：
        * 創建一個新的mailbox
        * 通過mailbox發送和接收消息。
        * 刪除一個mailbox
* Synchronization同步
    * 消息傳遞可以是blocking的或nonblocking的
    * blocking被視為Synchronization
        * blocking發送：發送方一直blocking，直到消息被接收方或郵筒接收
        * blocking接收：接收方一直blocking，直到消息可用
    * nonblocking被視為asynchronous
        * nonblocking發送：發送方發送消息並繼續執行
        * nonblocking接收：接收方接收有效消息或空消息
    * 當send()和receive()都是blocking的時候，發送方和接收方之間發生rendezvous(集會)。
* Buffering
    * 消息隊列附加到連接，可使用以下三種方式之一實現。
        * 零容量(Zero Capacity)(No buffering)：Queue length = 0。發送者必須等待，直到接收者接收消息。
    * 有界容量(Bounded Capacity)(automatic buffering)：Finite queue length = n。當隊列已滿時，發送者必須等待。
    * 無界容量(Unbounded Capacity)(automatic buffering)：無限長度infinite length。發送者永遠不會被阻塞。
* POSIX Shared Memory
    * 進程首先創建共享內存段
        * shm_fd = shm_open(name, O_CREAT | O_RDRW, 0666);
        * 也用於打開現有的共享內存段以分享它
    * 設置對象的大小
        * ftruncate(shm_fd, 4096);
    * 創建包含共享內存對象的內存映射文件：
        * ptr = mmap(0,SIZE, PROT_READ | PROT_WRITE, MAP_SHARED, shm_fd, 0);
    * 使用從mmap()返回的指針將共享內存作為常規內存訪問：
        * sprintf(ptr,"%s", message0);
    * 從系统中删除共享内存段
        * shm_unlink(name);

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_eab093af13cf549a4bcaa6237f6573ed.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2c56b0183714f0ff31dfebf296ae6af4.png)
*  C program illustrating POSIX shared-memory API
    1. 引入必要的函式庫和定義常數和變數。
        - `SIZE` 定義了共享記憶體物件的大小。
        - `name` 是共享記憶體物件的名稱。
        - `message_0` 和 `message_1` 是要寫入到共享記憶體物件的訊息。

    2. 開啟或建立共享記憶體物件。
        - `shm_open` 函數用於建立或開啟一個共享記憶體對象，將其關聯到檔案描述符 `fd`。

    3. 配置共享記憶體物件的大小。
        - `ftruncate` 函數用於設定共享記憶體物件的大小，確保它足以容納要寫入的資料。

    4. 映射共享記憶體物件到進程的位址空間。
        - `mmap` 函數將共享記憶體物件對應到進程的位址空間，傳回一個指向共享記憶體物件的指標 `ptr`。 映射設定了對記憶體區域的讀取和寫入權限，並標記它為共享內存，允許其他進程訪問相同的內存物件。

    5. 檢查映射是否成功。
        - 程式檢查 `ptr` 是否等於 `MAP_FAILED`，如果是，則表示映射失敗。

    6. 向共享記憶體物件寫入資料。
        - 使用 `sprintf` 函數將 `message_0` 和 `message_1` 寫入到共享記憶體物件。 透過遞增 `ptr` 來確保資料被寫入到正確的位置。
    7. 最後，程式返回0，表示成功執行。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_32a6af8aa1fffb419c6b1e732966b248.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2d6ee79d8fd75c1347e97302d26c7cf3.png)
* C program illustrating POSIX shared-memory API
    1. 引入必要的函式庫和定義常數和變數。
        - `SIZE` 定義了共享記憶體物件的大小。

     2. 開啟共享記憶體物件。
        - 使用 `shm_open` 函數以唯讀權限開啟現有的共享記憶體物件。 如果開啟失敗，將顯示錯誤訊息並退出程式。

     3. 映射共享記憶體物件到進程的位址空間。
        - 使用 `mmap` 函數將共享記憶體物件對應到進程的位址空間，傳回一個指向共享記憶體物件的指標 `ptr`。 映射設定了對記憶體區域的唯讀權限，並標記它為共享內存，允許其他進程存取相同的內存物件。

     4. 檢查映射是否成功。
        - 程式檢查 `ptr` 是否等於 `MAP_FAILED`，如果是，則表示映射失敗。

     5. 從共享記憶體物件讀取資料。
        - 使用 `printf` 函數列印從共享記憶體物件讀取的字串。

     6. 刪除共享記憶體物件。
        - 使用 `shm_unlink` 函數刪除共享記憶體物件的名稱，以便清理資源。

     7. 最後，程式返回0，表示成功執行。
* Mach Message Passing
    * Mach核心支援建立和銷毀多個任務，每個任務都有多個控制threads。
    * Mach中的大多數通訊都是透過訊息完成的。 訊息被傳送到稱為ports的郵箱中，然後從中接收。
    * 當每個任務被建立時，Kernel mailbox和通知郵箱也會被建立。 Notify mailbox用於核心與任務之間的通訊。
    * 只需要三個系統呼叫來進行訊息傳輸。
        - msg_send()
        - msg_receive()
        - msg_rpc()（發送一條訊息並等待接收方發送回傳訊息）。
    - port_allocate() system call用於建立新的郵箱，並為其訊息queue分配空間。
    - 發送和接收操作非常靈活。
    - 如果郵箱沒有滿，訊息會被複製並且發送線程會繼續。 否則，發送線程有四種選擇：
        - 無限等待，直到信箱有空間。
        - 最多等待n毫秒。
        - 不等待，立即返回。
        - 暫時快取一則訊息。 作業系統只保留一則這樣的訊息。
    - 如果沒有訊息等待接收，接收執行緒必須等待、最多等待n毫秒，或不等待。
    - Mach最初是為分散式系統設計的，但後來證明它也適用於處理器核心較少的系統。
    - 訊息系統的主要問題通常是由於從發送方連接埠複製訊息到接收方連接埠而導致的效能不佳。
    - Mach試圖透過使用虛擬記憶體管理技術來避免複製操作。
        - 它將包含發送方訊息的位址空間對應到接收方的位址空間，使得訊息本身實際上不會被複製。 （僅適用於系統內部訊息）寫時複製，共享記憶體。
* Windows
    * Windows提供多個操作環境或子系統的支援。
    - 應用程式透過訊息傳遞機制與子系統通訊。
    - 應用程式可以被視為Windows子系統伺服器的用戶端。
    - Windows中的訊息傳遞設施稱為高階本機程序呼叫（ALPC）設施。
    - 這僅在同一系統上的進程之間有效。
    - 使用連接埠（類似郵箱）來建立和維護通訊通道。
    - 通訊過程如下：
       - 用戶端開啟一個handle以存取子系統的連接埠物件。
       - 用戶端發送連線請求。
       - 伺服器建立兩個私人通訊端口，並將其中一個handle傳回給用戶端。
       - 用戶端和伺服器使用對應的連接埠句柄來傳送訊息或回呼以及等待回覆。
## 考古
### 2019
* I. Fill in the Blanks. (Answer terminologies in English only) (10%)

    1. In a ＿ system, OS contains a large amount of functionality to be combined into one level. OS is written as a collection of procedures, each of which can call any of the other ones whenever it needs to.

    2. A ＿ system composes of two or more individual systems or nodes joined together. It is usually used to provide high availability or high-performance computing environments.
    
    3. A ＿ system functions correctly only if it returns the correct result within its time constraints.

    4. An ＿ system is a combination of computer hardware and software, and perhaps additional mechanical or other parts, designed to perform specific tasks.
    5. An initial program that initializes all aspects of the system, loads OS kernel, starts executing the OS is ＿.


---
* 解答
```
1. Monolithic system
2. Clustered Systems
3. Real-Time(參考網路)
4. Embedded(參考網路)
5. bootstrap
```


---

* II. Questions. (Answer in Chinese or English) (90%)

    1. (15%) Give examples and describe the differences between trap, system call, and interrupt. Using trap, system call, and timer interrupt as examples to discuss why modern operating systems take advantage of hardware-supported dual-mode operation. (9%)(6%)
    2. (24%) Answer the following questions regarding the operating-system design. 
    (a) Draw the diagram of a typical microkernel and describe the microkernel approach. (4%)(4%) 
    (b) Describe the loadable kernel modules approach. (4%) 
    (c) For the microkernel and the loadable kernel modules approach, compare their strengths and weaknesses in terms of extensibility, performance, and security. Explain your answer. (12%)
    3. (16%) What is the producer-consumer problem? To solve the producer-consumer problem, discuss the strengths and weaknesses of using two different models of interprocess communication. Draw the diagram for each communication models. (2%) (10%) (4%)
    4. (12%) Draw the diagram and describe the memory layout of a process. What is the context of a process? Describe the actions taken by a kernel to context-switch between processes. (4%) (4%) (4%)
    5. (11%) Answer the following questions regarding the one-to-one multithreading model.
    (a) Draw the diagram and describe the one-to-one multithreading model.
    (b) Discuss whether a multithreaded application can perform better on a multiprocessor system than on a single-processor system. Explain your answer.
    (e) On a single-processor system, can an application using a multithreaded solution perform better than using a single-threaded solution? Explain your answer.
    6. (12%) What would be the output for the following C program using UNIX fork() and Pthreads API?
    ```
    #include <pthread.h>
    #include <stdio.h>
    #include <unistd.h>
    #include <sys/wait.h>

    int value = 1;

    void *start(void *param) 
    {
    printf(" (a) %d\n", value);
    value = 4;
    pthread_exit(0);
    }

    void main() 
    {
    int pid;
    pthread_t tid;
    pthread_attr_t attr;

    printf(" (b) %d\n", value);
    pid = fork();
    value++;
    if (pid == 0) { /* child process /
    value++;
    pthread_attr_init(&attr);
    pthread_create(&tid, &attr, start, NULL);
    pthread_join(tid, NULL);
    printf(" (c) %d\n", value);
    value++;
    } 
    else if (pid > 0) { / parent process */
    value++;
    wait(NULL);
    printf(" (d) %d\n", value);
    value++;
    } 
    printf(" (e) %d\n", value);
    value++;
    }


---
* 解答
1. Give examples and describe the differences between trap, system call, and interrupt. Using trap, system call, and timer interrupt as examples to discuss why modern operating systems take advantage of hardware-supported dual-mode operation. 
 * interrupt 軟體或硬體發出中斷，告訴系統工作已經完成了
    ex: I/O 想要將訊息和資料放進 RAM，interrupt

    * trap 軟體發生的中斷
    執行時發生錯誤: error, user 執行 print(8/0)
    os service request: system call
    * system call 可以呼叫 OS 進入 kernel mode 執行需要權限的服務
    * 用 system call、trap… 舉例解釋 dual-mode operation
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dbfe20efd022034ff0b34e41c7cf9625.png)
目的：為了要保護系統資源
避免使用者直接存取系統資源，如果使用者不小心用錯誤的指令修改 kernel 內的相關設定，可能會導致系統 crash 
2. Answer the following questions regarding the operating-system design. 
    * (a) Draw the diagram of a typical microkernel and describe the microkernel approach.
    * microkernel
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3838c99c6812124014d673aa78641fed.png)
Microkernel是一種作業系統設計方法，其核心思想是將作業系統核心的功能限製到最小的核心部分，而將其他功能以User-mode process的形式運行
* (b) Describe the loadable kernel modules approach.
將所有功能模組化，當使用者需要用到時才會動態載入到 kernel，而且不需要透過 message passing 傳遞訊息
* (c) For the microkernel and the loadable kernel modules approach, compare their strengths and weaknesses in terms of extensibility, performance, and security. Explain your answer.
    * extensibility:
        microkernel 和 LKM 的 extensibility 都不錯，
        LKM 可以將擴充的功能寫成 module，所有功能如果有需要再動態載入到 kernel
        microkernel 則是可以將功能擴充到 user mode。
    * performance:
        mocrokernel < LKM
        LKM 所有的 module 都可以動態載入到 kernel 執行。
        micorkernel 只有將比較常用的功能保留在 kernel mode，其餘功能在 user mode，而且要用 user mode 的 services 時要用 message passing 傳送訊息，所以效能比 LKM 低
    * security:
        microkernel > LKM
        如果 LKM 的 module 沒有寫好，載入到 kernel 時，容易造成整個系統當機、不穩定。
        microkernel : 萬一 service fail,因為 service 大都 run 在 user mode，頂多相當於 user process 死掉而已，對系統及其他 users、process 無害
3. What is the producer-consumer problem? To solve the producer-consumer problem, discuss the strengths and weaknesses of using two different models of interprocess communication. Draw the diagram for each communication models.
    * Producer-consumer problem：Producer 會把 data 放在有限或是無限的buffer 中等 Consumer來拿，要確保 Producer 不會在 buffer 滿的時候加入 data ，而 consumer 不會在 buffer 空的時候拿 data 


* interprocess communication models
    * shared memory
        * 優:
            不需要 kernel 介入
            如果 process 都在同一台機器，資料都可以從共享記憶體抓，速度比較快
        * 缺:
            protection & synchronize: 設計麻煩，要避免 data 被覆寫，所以要有 lock 的機制
        * 預留的 memory 空間要夠
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d229288276e836d3c272a42f5c778940.png)
* message passing
    * 優:
        適合跨機器
        可以同步
    * 缺:
        執行較慢，訊息收或送都需要由OS介入,收送都要 memory copy
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_482fa9da4418b458210bc8a7d3c83985.png)


4. Draw the diagram and describe the memory layout of a process. What is the context of a process? Describe the actions taken by a kernel to context-switch between processes.
    * Process Memory的分布:
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_27d38951ebfc161ac5fd690f486d06c4.png)
    * tack:存放temporary data(ex:local variables、function call)
        heap: 動態配置的記憶體空間
        data: 存放global variables
        text: 存放程式碼
        context 儲存 process 的狀態，PCB、PC、SP、base、limit…
        核心在進程間進行上下文切換時會執行以下操作：

    1. 儲存目前處理上下文
    2. 載入下一個進程上下文
    3. 更新核心資料結構
    4. 切換記憶體映射
    5. 復原執行



5. (a)：有一個 user thread 就會建立一個 kernel thread
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f78f9ec00050164646e38c504ae8dc04.png)
(b)
yes.
因為 multiprocessor system 有多個 processors，所以 process 可以平行執行；但是 single-process 只有一個 processor 獨立幹活(好可憐 :cry:)，如果 single-process 被其中一個 thread block 住，整個系統就會被 block 住無法繼續執行
(c )
no. 在 single-processor system 中，因為只有一個 CPU，只有一個 kernel thread，所以就算有多個 user thread，同一時間還是只能執行一個 user thread

也就是 many to one
(甚至拆成多個 thread，會有 context switch 的成本，會變慢)


6. output :

```
(b) 1 
(a) 3 
(c) 4 
(e) 5 
(d) 3 
(e) 4
```


---

### 2017
* I. Fill in the Blank. (Answer terminologies in English only) (20%)

1. A _ system can suffer a failure of any single component and still continue operation

2. A _ system composes of two or more individual systems or nodes joined together. It is usually used to provide high availability or high-performance computing environments.

3. What virtualization software do you use to build your virtual machines?_

4. In a _ system, all processors are peers and no boss-worker relationship exists between processors. Therefore, each processor performs all tasks within OS.

5. An _ system is a combination of computer hardware and software, and perhaps additional mechanical or other parts, designed to perform specific tasks.

6. In a _ system, OS keeps several jobs in memory simultaneously. When one job being executed needs to wait, the OS switches to and executes another job.

7. In a _ system, OS contains a large amount of functionality to be combined into one level. OS is written as a collection of procedures, each of which can call any of the other ones whenever it needs to.

8. An initial program that initializes all aspects of the system, loads OS kernel, start executing the OS is _

9. When arranging the CPU to run another process, the system must save the state of the old process and load the saved state for the new process via a _

10. Consider a multithreaded program running on a multicore system. If a thread makes a blocking system call, the entire process will block for the _ model. 


---
* 解答
```
1. Fault-tolerant system
2. clustered
3. Virtualbox
4. symmetric multiprocessing(SMP)
5. embedded
6. multiprogramming
7. monlithic
8. bootstrap
9. PCB
10. many to one
```



---

* II. Questions. (Answer in Chinese or English) (80%)
    1. ~~(13%) What is dual-mode operation? Using trap, system call, and timer interrupt as examples to discuss why modern operating systems take advantage of hardware-supported dual-mode operation. (4%) (9%)~~
    
    2. ~~(16%) Describe the microkernel and the modular kernel approach in operating-system design. Compare their strengths and weaknesses in terms of extensibility. (8%) (8%)~~
    
    3. ~~(12%) Please take the producer-consumer problem as an example to discuss the strengths and weaknesses of using two different models of interprocess communication to solve the producer-consumer problem. Draw the diagram for each model. (8%)(4%)~~
    
    4. (8%) What is the one-to-one multithreading model? Discuss its strengths and weaknesses. (2%)(6%)(6%)
    
    5. (10%) What would be the output for the following C program using UNIX fork() and Pthreads API? 
```
        #include <pthread.h> 
        #include <stdio.h> 

        int value = 1;
        void runner() 
        { 
            value++; 
            printf("(a) %d\n", value); 
        } 

        void *start(void *param) 
        { 
            runner(); 
            value++; printf("(b) %d\n", value); 
            pthread_exit(0); 
        } 
        int main(int argc, char *argv[]) 
        {
            int pid; 
            pthread_t tid; 
            pthread_attr_t attr;
            /* parent process /
            value++;
            pid = fork();
            if (pid == 0) { / child process /
                 value++;
                 printf("(b) %d", value);
                 pthread_attr_init(&attr);
                 pthread_create(&tid, &attr, start, NULL);
                 pthread_join(tid, NULL);
                 value++
            }
            else if (pid > 0) { / parent process */
                    value++;
                    wait(NULL);
                    runner();
            }
            value++;
            printf("(c) %d", value);
        }
```
6. (4%) Including the initial process, how many processes are created by the following program? Explain your answer.
```
#include <stdio.h>
#include <unistd.h>
void main() {
    int i;
    for (i=0; i<2;i++)
        fork();
  return;
}
```
7. (9%) A system distinguishes two classes of processes: real-time process and normal process. Basically, the system uses preemptive priority-based scheduling algorithm. Real-time processes are assigned with the highest priority and scheduled in FCFS order. Normal processes are assigned with the lowest priority and scheduled in Round-Robin order with time quantum 2. The table below shows four processes that need to be scheduled. The length of the CPU-burst time is given in milliseconds.
(a) Please draw the Gantt chart. (4%)
(b) Please show the waiting time for each process and the average waiting time. (5%)


| process | Arrival time | CPU Burst | class |
| ------- | ------------ | --------- | ----- |
| p1        |       1       |    7       |     Normal  |
|   p2      |       7       |    3       |  Real-time     |
|     p3    |       0       |    3       |   Normal    |
|   p4  |       4   | 1      |    Real-time   |

8. (8%) Consider two processes, P1 and P2, where p1=70, t1=30, d1=12, p2=56, t2=20, and d2=15. Using Gantt charts (till time 140) to illustrate the scheduling of these two processes using earliest-deadline-first (EDF) scheduling and rate-monotonic scheduling. (Note: p: period, t: processing time, d: deadline) (4%) (4%)



---

* 解答:
4. What is the one-to-one multithreading model? Discuss its strengths and weaknesses.
    * 優點：
        * 透過允許另一個thread在一個thread執行阻塞系統呼叫時運行，提供了比more-to-one一模型更多的並發性。
        * 允許多個thread在多處理器上並行運行。

    * 缺點：
        * 建立一個user thread需要建立對應的kernel threads，大量的核kernel threads可能會影響系統的效能。


5. What would be the output for the following C program using UNIX fork() and Pthreads API?
    * (b)4 (b)5 (c ) 8 (a)6 (a)5 (b)6


6. (4%) 包括初始程序在內，以下程序會創建多少個程序？解釋您的答案。
    * 4
    Explain: 
        初始進程是啟動程序的進程。
        fork() 函數建立一個新進程，該進程是父進程的副本。
        for 迴圈呼叫 fork() 兩次，因此建立了兩個新程序。
        然後，兩個新進程分別再次呼叫 fork()，因此總共創建了四個進程。

---

### 2020
* I. Fill in the Blanks. (Answer terminologies in English only) (20%)
1. A ＿ system composes of two or more individual systems or nodes joined together. It is usually used to provide high availability or high-performance computing environments.

2. In a _ system, the CPU executes multiple jobs by rapidly switching among them, the illusion of several jobs executing simultaneously is created. 

3. A _ system functions correctly only if it returns the correct result within its time constraints.

4. An initial program that initializes all aspects of the system, loads OS kernel, starts executing the OS is _.

5. _systems have two or more processors, sharing the computer bus and sometimes the clock, memory, and peripheral devices.

6. In _ systems, a CPU has faster access to some parts of memory than to other parts.

7. _ refers to a kind of software that not only makes source code available but also is licensed to allow no-cost use, redistribution, and modification.

8. A _ system can suffer a failure of any single component and still continue operation.

9. An _ system is a combination of computer hardware and software, and perhaps additional mechanical or other parts, designed to perform specific tasks.

10. _ is a technology that allows us to abstract the hardware of a single computer (CPU, memory, disk drives, network interface cards) into several different execution environments, thereby creating the illusion that each separate environment is running on its own private computer.


---
* 解答
```
1. Clustered System
2. Time-Sharing System
3. real-time system
4. bootstrap program
5. Multiprocessor system
6. Non-uniform Memory Access (NUMA) System
7. Free Software Foundation(FSF) 應該是Open source
8. Fault-tolerant system
9. embedded system
10. Virtualization
```
---

* II. Questions. (Answer in Chinese or English) (90%)

    1. (4%) Draw the diagram and discuss how the OS increases CPU utilization in a multiprogramming system.

    2. ~~(24%) Give examples and describe what traps, system calls, and interrupts are. Draw the diagrams and use trap, system call, and timer interrupt as examples to discuss why modern operating systems take advantage of hardware-supported dual-mode operation. (9%) (9%) (6%)~~

    3. ~~(41%) Answer the following questions regarding the operating-system design.
        (a) Describe the microkernel approach, the monolithic kernel approach, the loadable kernel modules approach. (9%)
        (b) Regarding the extensibility issue, for microkernel, monolithic kernel, and loadable kernel modules approach, please compare their strengths and weaknesses. Explain your answer. (12%)
        (c) Regarding the performance issue, for microkernel, monolithic kernel, and loadable kernel modules approach, please compare their strengths and weaknesses. Explain your answer. (12%)
        (d) Regarding the security issue, for microkernel and loadable kernel modules approach, please compare their strengths and weaknesses. Explain your answer. (8%)~~

    4. ~~(12%) Draw the diagram and describe the memory layout of a process. What is the context of a process? Describe the actions taken by a kernel to context-switch between processes. (4%) (4%) (4%)~~
    
    5. ~~(11%) Draw the diagram and describe the memory layout of a process. What is the context of a process? Draw the diagram and describe the actions taken by a kernel to context-switch between processes.
~~

---
* 解答
1. Draw the diagram and discuss how the OS increases CPU utilization in a multiprogramming system.
    * 讓某個進程始終在運行，以最大化 CPU 使用率
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_268aeeacd1b83b7660599cf1f2fab702.png)


---
## 關鍵字
* Clustered systems vs. multiprocessor system (chap 1 page 38-47)
* Clustered Systems (chap 1 page 43)
* multiprocessor(chap 1 page 38)
* Monolithic system (chap 2 page 66-71)
* Monolithic system vs Microkernel Systems(chap 2 page 79)
* Real-Time(chap 1 page 133)
* Embedded(chap 1 page 129)
* bootstrap
* Trap
* System Call
* v.s trap, system call, and interrupt
* microkernel
* Fault-tolerant system
* Virtualbox
* symmetric multiprocessing(SMP)
* multiprogramming
* monlithic
* PCB
* many to one
* dual-mode operation
* operating-system design
* producer-consumer problem
* memory layout of a process
* context
* context-switch act
* one-to-one multithreading model
* loadable kernel modules approach
* microkernel and the loadable kernel modules extensibility, performance, and security/pros cons
* shared memory
* message passing
* Time-Sharing System
* Non-uniform Memory Access (NUMA) System
* Free Software Foundation(FSF) 應該是Open source
* Fault-tolerant system
* layer OS
* monolithic kernel
* memory layout of a process
* multithreaded application perform on multiprocessor system  vs. a single-processor system
*  single-processor system(chap 1 page 37)
## 重點
[重點](https://g0v.hackmd.io/dnGHzdI_Rsmk9u-5a76aHA?both)

###### tags: 1091 os 筆記
# CH1
-  why os is needed?
    - os管理電腦記憶體、程序跟硬體資源
- 電腦系統由多個CPU跟驅動裝置(device controller)組成
- 電腦可區分成
    1. 使用者
    2. 應用程式
        - 編譯器、網頁、開發套件Development Kit(eg.SDK軟體開發套件)
    3. 作業系統
    4. 硬體
        - CPU、Memory、I/O device、etc

![](https://i.imgur.com/x3FX7bW.png =300x)

![](https://i.imgur.com/chbWnX5.png =300x)

![](https://i.imgur.com/QCrFPqm.png =300x)
應用程式透過shell跟os互動(use shell:common interpreter)


## ==OS 可以做啥 ?==
- 分配資源管理
- 控制程序
    - 管理使用者的正在執行程式，避免錯誤跟失當的使用電腦
    - <span style="font-weight:bold">更為常見的定義是，操作系統是始終在計算機上運行的一個程序（通常稱為內核</span> <span style="color:red;font-weight:bold">kernel</span><span style="font-weight:bold">），而其他所有程序都是應用程序。</span>
- 管理硬體的軟體
- 提供服務(以下詳細解說)
#### OS的主要目的在於:提供使用者可以以方便、高效方式的執行指令環境
## Services of the OS 
![](https://i.imgur.com/62m589K.png)
- ==提供的服務 :== 
    - <span style="color:black;font-weight:bold"> 程式執行(execute program)、i/o 運作(operating)、檔案系統操控(file system)、accounting</span>
    - <span style="color:black;font-weight:bold"> 通訊(communication)、錯誤檢測(error detection)、資源分配(resource allocation)、保護跟安全機制(protect & security)</span>
        - accounting:用來記錄用了哪些資源
- <p style="font-size:16px">使用者介面user interface(UI)，GUI圖形化介面、CLI命令列介面、batch批次系統介面皆為UI<br>使用者透過system call要求os提供服務<br> </p>

![](https://i.imgur.com/chbWnX5.png=50x50)
--<h3>OS開始工作，四個時機: 
1. 開機system booting
2. 中斷發生interrupt occur
3. 錯誤發生 exception
4. System call</h3>

### <span style="font-size:22px;font-weight:bold">system booting</span>

![](https://i.imgur.com/L1evyx3.png =400x)![](https://i.imgur.com/5Ozl0mU.png =300x)

- 需要有一個初始化的程式(Needs to have an initial program to run): <span style="color:blue;font-weight:bold">bootstrap</span>
- os存在disk裡面，記憶體分成ROM(左邊)、RAM(右邊)
- bootstrap為開機第一個程式，存在ROM裡
    1. CPU執行bootstrap後，把OS載入RAM，開始執行OS
    2. os開始執行第一個程序(process)，例如:初始化程式(init)or等待事件發生(wait event to occur)



### <span style="font-size:22px;font-weight:bold">interrupt occur</span>
> ![](https://i.imgur.com/kPq58nL.png =400x)
![](https://i.imgur.com/lIR11UQ.png =400x)
- cpu載入GUI shell放到RAM，執行GUI時，把API載入RAM

#### <span style="font-size:19px;font-weight:bold">Interrupt 的處理流程</span>
1. 暫停目前 process 執行並保存此 process 當時執行狀況
2. OS 根據 中斷的Interrupt ID 在 Interrupt vector查尋並取得 ISR (Interrupt Service Routine) 中斷起始的位址
3. ISR 執行
4. 執行完成，恢復先前 process 執行狀況
5. 回到原先中斷前的執行

![](https://i.imgur.com/QNZDI9j.png =400x)
##### <span style="font-size:18px;font-weight:bold">中斷的種類</span>
- <span style="font-weight:bold">外部中斷（External Interrupt）</span>
    -  eg. I/O Complete Interrupt、 I/O Device error
- <span style="font-weight:bold">內部中斷（Internal Interrupt）</span> 
    - 不合法的用法所引起的，CPU 本身所引發
        - Debug、Divide-by-zero、overflow
- <span style="font-weight:bold">軟體中斷（Software Interrupt）</span>
    - 使用者程式在執行時，若需要 OS 提供服務時，會藉由 System Call 來呼叫 OS 執行對應的 ISR，完成服務請求後，再將結果傳回給使用者程式

### 錯誤發生 exception occur
![](https://i.imgur.com/17vz4hY.png =450x)

當error發生，處理器會透過interrupt vector得到exception handler的位址，去處理os的exception
- divide by 0、infinit roop、program misbehavior


### System call



### 1.4.2雙模式、多模式運作
##### mode分為
- User mode
    - mode bit=1
    - run user 程式的模式
- Kernel mode 
    - mode bit=0
    - 有很大的權限，做所有的硬體操作和其他系統停止指令
    - 亦稱: supervisor mode, or system mode, or privileged mode
當有錯誤發生或是故障(trap)時，需轉換成kernel mode模式執行os code
![](https://i.imgur.com/OTUolYr.png)




### I/O
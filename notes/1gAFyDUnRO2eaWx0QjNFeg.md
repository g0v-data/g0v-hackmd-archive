# 恐龍書Ch2

###### tags: OS

## 2.2 User and Operating-System Interface
### 2.2.1 Command Interpreter
扮演user&os的溝通介面，主要是去抓取以及執行user command
如果有許多command interpreters 供選擇，我們統稱為   **shell**
抓取方式分為兩種
1. 直接執行自己內部的code
2. 透過system program

Quiz:

    1. what is the purpose of command intepreter?
        Ans : 扮演user & os 的溝通介面
    2. why is it usually seperate from kernel?
        Ans : 不同於Windows & UNIX整合在一起，分開的好處可以讓使用者選擇(shell)


### 2.2.2 Graphical User Interface
現今許多電腦都是長這樣，透過鼠標點擊圖案來執行程式，隨者時代進而衍生到手機那種touch screen 模式
### 2.2.3 Choice of Interface
對系統比較熟的(System administrators & power user)會用command interpreter，但GUI強在較為直觀，也就是全看個人喜惡


---

## 2.3 System Calls 
> 作為user process & os 溝通介面

[https://ithelp.ithome.com.tw/m/articles/10275598](https://)

system call 有各式各種呼叫方式，而傳入參數的方式只有三種
1. Register : 簡單快速但能存的數量較少
2. Memory : 用block保存參數並以register存該block的位址(速度較慢)
3. Stack : pop&push來執行，但stack要大不然會stack overflow

---

## 2.4 Types of System Calls
分為六種
1. Process Control
2. File Management
3. Device Management
4. Information Maintenance
5. Communication
6. protection

### 2.4.1 Process Control
控制程式的結束(自願用end()、不自願用abort())
產生新的process時會用fork()再搭配exec()去決定要用哪種功能
### 2.4.2 File Management
控制file的屬性以及移動複製等動作(會在ch11,12做介紹)
### 2.4.3 Device Management
實體(disk drive)跟虛擬(file)都有，可以read()、write()，通常會有deadlock的風險(之後會講)
### 2.4.4 Information Maintenance
information 指的是time()、date()這類的資訊，但有的可以追朔使用過什麼system call像是dump()
像是microprocesser會在每個指令執行完後都發出trap(provide a CPU mode after every instruction)
### 2.4.5 Communication(interprocess)
分為兩種
1. message-passing model : 有client&server的角色，每台computer has its own name(host name==IP address)，each process also has its name，server and client 分別為收發daewon(a computer program running as background process)
2. shared-memory model : 共享記憶體，但通常os會禁止複數個process in same memory，所以得有多個process同意削掉這個限制

### 2.4.6 Protection
控管使用者的資源權限

---

## 2.5 System Programs
從另一個角度看modern system就是system program的集合，提供方便的環境給program
分為以下面向:
1. File Management : 對檔案以及資料夾做新增刪除等動作
2. Status Information:存寫的權限、使用者人數等資訊
3. File Modification : Several text editors may be available to create and modify the content of files stored on disk or other storage devices
4. Programming-language support : compiler、assemblers、debbuger、interpreter都會包在裡面
5. Program loading and execution : 提供工具做loading&execution e.g.absolute loader
6. Communication : provide virtual connection among process、user and computer system
7. Background service : 指的是會執行到系統停止的程式，像是資料庫、網頁瀏覽器

---

## 2.6 Operating-System Design and Implementation

### 2.6.1 Design Goals
雖然會因為系統的性質不同(Time-sharing、Batch)而目標不同，但可分為user goal以及system goal

    user goal 主要是為了fast safe但這些可能不適用於system goal

### 2.6.2 Mechanisms and Policies
1. Mechanisms : how to do
2. Policies : what will be done
e.g time construct 就是一種mechanisms，但time要設置多長就是policy

policy與mechanism的差別就是在彈性，policy會隨者情況變化

         Policy decisions are important for all resource allocation. Whenever it is necessary to decide whether or not to allocate a resource ,a policy decision must be made. Whenever the question is how rather than what,it is a  mechanism that must be determined


### 2.6.3 Implementation
可以用assembly language或是high-level language(e.g MCP)
 
 ---
 
## 2.7 Operating System Structure
比起單一的大小，更傾向切成小塊來看
 
### 2.7.1 Simple Structure
同字面意思就是簡單的構造，因為簡單所以對functionality切割以及硬體的保護也不到位 
e.g.MSDOS
 
### 2.7.2 Layered Approach
將system分成好幾個layer，由內到外layer增加，每層都只能用自己以下層數的功能
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a08ef8ce398ade2a7415b27b6557181f.png)

* advantage : 建立以及除錯簡單
* disadvantage : 定義(分工)困難、效率差(因為要不斷跨層)

### 2.7.3 Microkernel
> [color=#8e61e8]
>與其相反的為monolithic 

將不必要的服務元件移除，提供以下三個服務
1. Process Management/control
2. Memory Management
3. InterProcess Communication

* advantage : 
    * easy extension(新增/刪除元件) : 大部分在user site
    * easy port : 輕鬆到不同的硬體CPU
    * 高可靠度/安全性 : service foul 相當於一個user process死掉對kernel&other process沒有影響
* disadvantage : Performance(因為要大量的message passing between user mode and kernel mode)



### 2.7.4 Modules
運用 loadable kernel module
kernel 提供 core service ， 其他service會動態執行
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b8ed155ba700938723e4a5b768539b21.png)


### 2.7.5 Hybrid Systems
為了因應各種情況鮮少系統會採用一種模式，大部分是混合
e.g Mac OS、IOS、Android

---

## 2.8 Operating-System Debugging
debugging 就是指針對hardware&software做偵錯以及除錯的動作

### 2.8.1 Failure Analysing
在錯誤發生時，多數的os會將錯誤的資訊寫入 ***log file*** 或者是執行 ***Core dump***

    core dump就是當程序運行的過程中異常終止或崩潰，作業系統會將程序當時的內存狀態記錄下來，保存在一個文件中(記憶體轉儲)
    
### 2.8.2 Performing Tuning(效能調整)
performance提升的關鍵在如何移除掉bottleneck，但要先測試system performance，而測試的方法為以下兩種
1. **trace lists**:包含時間以及重要參數
2. interactive tools(single purpose):windows的工作管理員

新的一代測試工具

### 2.8.3 Dtrace
在user process & in the kernel動態插入probes(探針)
當執行提供者(provider)的程式，探測點(probe)會將擷取到的狀態數據發送給探測點的消費者(consumer)
除錯時DTrace對Performance的影響很小，並且很安全，所以是一個選擇
* enabling control block(ECBs): when a probe fires,it emits data that are managed by kernel.

---

## 2.9 Operating-System Generation(作業系統的建立)
* OS通常以disk、ISO映像黨(CD-ROM、DVD-ROM)

* Sysgen program
    * 獲取有關硬體系統特定配置的信息以組成該機的作業系統
    * 如果多cpu，每個屬性都要讀取
    * 決定記憶體容量
    * 最佳化系統選項

---

## 2.10 System Boot

* booting : 載入kernel以開啟電腦的程序，其program叫做bootstrap program or bootstrap loader

---

boostrap program
1. 存在ROM(不須initialization、且不易被病毒攻擊)
2. ROM is firmware
3. e.g : GRUB(for Linux)
4. 全部的bootstrap loading完後的這個狀態才叫 ***running***





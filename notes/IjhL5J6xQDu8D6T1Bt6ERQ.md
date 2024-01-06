# Ch4 Threads
## 4.1 Overview
### 4.1.1 Motivation 
在某些情況，a single application may be required to perform several similar tasks，而在threads盛行前，通常是就當作single process持續運作，一個個解決(single-threaded)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_84c41a0fd9fd4f66545b7ff58be4682e.png)

### 4.1.2 Benefits
以下為multithread的好處
1. Responsiveness : 若執行中的thread被blocked，則CPU可以切給process內其他的**available thread**，故process不會被停止 
2. Resource sharing : 共享process內的資源達到多工
3. Economy : 因為Threads之**私有資訊量少**，所以Thread Creation快速，也節省memory空間，Thread間的context switch也faster than process
4. Scability : utilization(遠贏multiprocess)

## Multicore Programming
* 將多數運算單元(computing cores)放置在single chip.
* each core 會被視為separate processor

        這邊簡單敘述concurrency & parallelism
        concurrency 是單一core不斷切換工作達到multiprogramming的目的
        parallelism 則是多數個core同時做工作
* amdahl's law
s:不可平行執行的部分(serially)
n: number of core
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9b032f1276cd6620ed31ffc0106b62e4.png)

### 4.2.1 Programming Challenges
multicore 厲害歸厲害還是又實行上的困難
1. Identifying tasks : 工作那些可以concurrency，以方便切出來
2. Balance : 每個core是否有平均分配這些工作
3. Data splitting : data accessed and manipulating 也要被分配到其他cores
4. Data dependency : 資料相依性
5. Testing & Debugging : 因為分出去了所以除錯變難了

### 4.2.2 Types of Parallisms 
1. Data Parallisms : 分配相同資料到cores上做相同運算(e.g 從1加到10 會拆成1加到5跟6加到10)
2. Task Parallisms : 分配Threads到multiple cores，each threads做不同運算(我做我的你做你的)
---
## 4.3 Mutithreading model
Thread有兩種分別為kernel thread & user thread
in note book(Pt.2) 
### 4.3.1~4.3.3 
many user threads to one kernel threads


|| Many to one| one to one| many to many|
| ---------------------------- | -------------------------------------- | ------------------------------------ | ---------------------------------------- |
| Def.| many user threads to one kernel thread | one user thread to one kernel thread | many user threads to many kernel threads |
| Thread Management Efficiency | Fast| slower| slower|
| Responsiveness| no| yes| yes|
| kernel負擔| 輕| 重| 居中|
| Scability| no| yes| yes|
| OS製作複雜度|no,是靠Thread lib.|simple|Complicated|
| 例子| Thread lib.|Linux,Windows| solaris2|

## 4.4 Thread Libraries
Thread Libraries 提供programmer API 創造&管理threads，而根據有沒有kernel的介入會分為兩種
https://ithelp.ithome.com.tw/articles/10203786
## 4.5 Implicit Threading
將creation&management of threads 從application developer 轉移到compilers and run-time libraries
以下介紹三種實作方式
### 4.5.1 Thread Pools
in Note Pt2
### 4.5.2 OpenMP
* OpenMP是用將可平行處理的部分(parallel region)視為code block 
* OpenMP也會讓developers去選平行的層級(e.g:手動調整部分的thread，可以知道哪些是共享的那些是私人的)

### 4.5.3 Grand Central Dispatch
GCD是ios,Mac裡面將複雜不易懂的thread操作方式簡化過的API(將單一任務拆成多個小任務並同時執行，或是同時執行多個任務)，目的是為了縮短執行時間

## 4.6 Threading Issue
### 4.6.1 The fork() and exec() System calls
如果其中一個thread()執行到了fork()，究竟是否要將process所有的thread都複製，而exec()也是同個道理，執行到的時候取代整個process
### 4.6.2 Signal Handling
signal是用來告知特定事件的發生
signal在發出後，交由兩個handler來處理分別為default signal handler & user-defined handler
每個signal都有default signal handler，而user-defined handler可以蓋過預設的處理

### 4.6.3 Thread Cancellation
Cancellation是指在Thread結束執行前就停止，要被終止的thread會被稱呼為**target thread**，而中止可以依情況分兩種
1. Asynchronous Cancellation:one thread **立即中止** target thread
2. Deferred Cancellation: 定期檢查target thread是否該被終止，讓他自我終結

        asynchronous cancellation後，os會要回系統資源但不一定是全部，對比之下，在特定情況下做完檢查才決定是否要終止的deferred cancellation比較適合
        
Deferred Cancellation決定檢查是否要終止的地方較cancellation point
### 4.6.4 Thread-Local Storage
雖然thread會共享process內的data，但總有需要屬於自己那一份的時候，我們稱呼那種data就叫Thread-Local Storage(TLS)
e.g. 交易系統裡，每筆交易可以分給每一個thread

### 4.6.5 Scheduler Activations
這是聚焦在kernel與thread library，這通常是用many-to-many或是two-level models(這樣達到好的performance)，而作為user thread與kernel thread之間的data structure叫做lightweight process(LWP)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8f635d8d5dbb8fde7f40480cb7349a2b.png)

Scheduler Activaitons就是其中一種溝通方式實際工作流程如下:
1. kernel提供virtual processors application(功用:schedule user threads onto an available virtual processors)
2. kernel在certain events發生時會發通知(此動作稱upcall，thread library 有個管理這個叫upcall handler，而upcall handler會在virtual processors上跑)

## 4.7 Operating-System Examples
### 4.7.1 Windows Threads
### 4.7.2 Linux Threads
## 4.8 Summary
thread是process內的control flow，可以單數或多數個，thread的四個好處以及user&kernel thread的差異，user thread是不會被kernel偵測到，三種有關user&kernel thread的model

創造thread的方式除了用APT of library(explicit)也可以交給compilers and run-time library(implicit) 



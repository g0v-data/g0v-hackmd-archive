# Ch6 CPU Scheduling
## 6.1 Basic Concept
讓cpu不會因為one process去I/O就idle，透過排程讓cpu保持工作
### 6.1.1 CPU-I/O Burst Cycle
Process在執行中不是在execution(CPU burst)不然就是在I/O wait(I/O burst)
CPU burst 會有長時間的持續時間，如圖
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9b23557e0fc76b6c487ac62d270cb660.png)
I/O bound 會有許多小的cpu burst但cpu bound則會相反持some long-term cpu bursts
### 6.1.2 CPU Scheduler
也叫做short-term scheduler，負責將ready quene內的process順序(不一定是FIFO)
### 6.1.3 Preemptive Sceduling 
process可以插隊的那種(標準沒有一定)，反之就是nonpreemtive
preemptive可能會造成race condition(resource shared by mutiple process)，
### 6.1.4 Dispatcher
同時參與cpu-sceduling的另一個元件，主要做三件事情
1. Context Switch
2. Switching to user mode
3. Jumping to the proper location in the user program to restart the program

因為只要切換process就一定會參與，所以這段時間(**dispatch latency**)越短越好

## 6.2 Scheduling Criteria
* CPU utilization :cpu的利用率 
* Throughput :單位時間輸出的量
* Turnaround Time :執行時間
* Waiting Time : 進入Ready state後到結束時間前沒在執行之前
* Response Time : 回應所需要的時間，interactive system會很講究這個，從提出需求到第一個回應被製造出來

CPU utilization & Throughput 越大越好，其餘三個則相反

## 6.3 Scheduling Algorithms
都可以用Gantt Chart來寫
### 6.3.1 FIFO(nonpreemptive)
先進先完成，所以有可能有convoy effect(有個時間要花很久的process在前面會卡住後面許多小的)

### 6.3.2 Shortest-Job-First Scheduling
簡稱SJF，由Turnaround time從小排到大，average waiting time是最小的，但難處是要怎麼知道每個的執行時間，如果是由batch system的long-term scheduler就可以。
可preemptive(**SRJF**)也可以nonpreemptive

### 6.3.3 Priority Scheduling
就有其他因素可以決定Process的順序，可以先外部決定或是內部決定，也可以preemptive or nonpreemptive(new process wii be placed in the head of ready quene)。
主要還是會產生無限的block或是starvation

## 6.4 Thread Scheduling
牽扯到user level 以及 kernel level，分為兩種sch
## 6.5 Mutiple-Processoer Scheduling
### 6.5.1 Apporoaches to Multiple-Processor Scheduling
ASMP & SMP
### 6.5.2 Processor Affinity
不希望process一直在core之間跳轉，這樣會造成大量的context switching(負擔)，簡單來講就是Process 有傾向(affinity)去待在同一個processor。
根據嚴格程度可以分為hard affiniy && soft affinity
### 6.5.3 Load Balancing
就是想讓每個processor之間的workload差距不會太大(idle vs busy)，移動的方法分為push(上司分配) and pull(同事幫你) migration

### 6.5.4 Multicore Processor
在同個physical chip塞入多數個processor cores形成multicore processor。
發現進入memory的時間好久(memory stall)所以實作multithreaded processor，透過switch thread來避免因為memory stall就整個processor停止。
multithread 也分為兩種，分別是coarse-grained 以及 fine-grained

## 6.6 Real-Time system
分為hard real time 以及soft real time
hard time : critical task 必定準時完成
soft time : critical task 必保持最高priority

主要讓系統等待有兩個latency，分別為interrupt latency 和 dispatch latency:
interrupt latency 指的是interrupt到達CPU直到ISR開始的這段時間
dispatch latency 用圖來解釋
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5f401e5febce35ff98379173c3b5d0e8.png)
[](https://)

## 6.7 Operating-System Example 
### 6.7.1 Linux Scheduling 
靠Complete Fair Scheduler(CFS)來跑，CFS會根據每個task的nice value來決定要分配多少CPU time，CFS在計算時間也不是用分散式的方式而是用target latency(interval of time which every runnable task should run at least once)
由scheduling class來決定，每個class都有特定的priority(可比較)，而Linux中用兩種scheduling class，分別為scheduled by CFS(default) and real-time scheduling。
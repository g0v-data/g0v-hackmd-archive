# [作業系統] CH5 CPU Scheduling 



## CPU 排程方式

依照process是否能夠在途中更換分為兩種：



**1. preemptive(搶先)**
Process在執行途中，若有優先級更高的程序加入，會將正在執行的Process中斷進行context switch換為新的Process，原本執行的Process則會回到ready state。
**2. non-preemptive(非搶先)**
正在執行的Process一定會等到執行完成才能切換到下一個Process。



而排程方式又分為：

**1. FCFS(First Come Fist Serve)**
顧名思義，先到的Process先開始處理。可能會造成Concoy effect（護衛效應）。

* Concoy effect（護衛效應）：較長處理時間的Process卡住後面的所有程序。

**2. SJF(Shortest Job First)**
最短的程序優先執行，比較不會造成塞車。

**3. Priority**
有定好的優先權級，Priority高的先執行。
如果同Priority並沒有特別註記的情況下，依照SJF值ㄒㄧㄥ

**4. Round Robin**
比較特殊，先設定一個time segment，當time segment時間到或Process執行完畢，則換下一個Process。
可以將它想成一個環狀的quene。

也就是：
time segment > process time，依照正常程序切換。
time segment < process time，ts到的時候context switch，將目前執行的process丟到ready quene最後面。


---

## Starvation
依靠優先級去排程(SJF/Priority)的系統，有可能會造成Starvation。
Starvation指有低優先級的Process，因為新的高優先級Process不停地加入插隊，導致一直無法被執行到。

解決Starvation有幾種方法，其中一種方法是可以讓等待時間久的Process慢慢增加優先級，以保證一定會被執行到。

---

## Average Waiting Time/ Average Turnaround Time
幾本上理解上面的幾種排程方法的機制，畫得出甘特圖就很好計算。令有n個process要執行，公式如下：
> Average Waiting Time = $[(P_1開始執行的時間 - p_1抵達的時間) + (p_2開始執行的時間 - p_2抵達的時間) + ... + (p_n開始執行的時間 - p_n抵達的時間)] / n$

> Average Turnaround Time = $Average Wating Time + (總執行時間)/n$
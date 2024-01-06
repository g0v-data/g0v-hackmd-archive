# Chapter 9 / Virutal Memory Mangagment

## 前言
Virutual Memory（虛擬記憶體）能夠讓應用程式認為其還有足夠的連續（非連續）的記憶體可以使用，而實際上有部分暫時放在記憶體外部的磁碟機上，需要的時候才會進行交換（Swap out、Swap in）。

優點：
- 允許程式大小大於實體記憶體時，仍然可以執行。
- OS的負擔，與程式設計師無關
- 每一個User Program使用的實體記憶體空間減少，更多的Program可以在同時間run。使得 **CPU使用率（CPU untilization）** 和 **產量（throughoupt）** 提高，但並沒有相對提高回應時間（respnse time）和單個Program執行結束的時間（turnaround time）。
- 每一次的I/O減少，單需要額外的load和swap時間，整體使得User Program可以run的更加快速



## 9.2 Demand Paging
Demand Paging是一種實現virtual memory的方式。
以page為基礎，採用lazy swapper技巧。程式執行之初不會將整個process載入，而是只載入需要的pages。如要處理page fault，則交給OS來做。

**<補充 lazy swapper：在page需要錢絕對不會把該page swap進入memory。>**

### 9.2.1 Basic Concepts

當一個process被swap in，pager會在process再次被swap out前猜測哪一個page會再次被用到。
**而為了實現virtual memory，會需要到額外的硬體來支援並區分page現在在memory還是在disk中。**

1. valid-invalid bit：判斷此次的reference是否成功
- vaild：合法的acess地址，且該資料存在於memory中
- invalid：**發出page fault**，然後透過translate再去檢查
    1. 不合法的acess
    2. 合法的acess地址，但是資料不存在於memory中

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3a7c5e85f1f2d1a4d8a88f485c06668f)


硬體透過page table要轉換address時，發現page table裡的invalid bit被設置了而發trap（當OS無法將想要將page載入memory時）給OS。處理此trap的流程為：
1. 確認想要reference的addres是否合法
2. 若是該address事實上為不合法，就中止該process;但若此address是合法，就把page載入memory中
3. 從memory中找尋一個可用的（free）frame
4. 對Disk進行排程，便於將想要的page載入進memory中
5. 當disk讀取完畢，修改page table，指出剛剛載入的page已在memory中（valid bit -> valid）
6. 重新啟動（restart）剛剛造成page fault的指令（因為只要program開始執行，PC = PC + 4會一直運行下去）

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e7ff1c2cea9e858960bd0b3b829346c1)

### 9.2.2 Performance of Demand Paging

**Effective Access Time**

一般來說，memory-acess time被註記為ma，只要page faults越少，那麼effective access time就越趨近於只有memory access的時間。

假設p是有可能有page fault的比例，我們期待p越接近0越好。

effective access time = (1 - p)* ma + p * page fault time 

為了能夠計算出effective access time，我們必須知道需要花多少時間來處理一個page fault。
而一個page fault可能會發下列一連串的事情。
1. 發送trap給OS
2. 保存使用者記憶體以及process state（便於處理完後可以restart instruction）
3. 確定此interrupt是一個page fault
4. 檢查reference是否合法，並確定page在disk中的地址
5. 將page從disk讀取進入free frame的問題
    - 在queue裡面等待自己被request被服務
    - 等待device所花的latency time
    - 開始transfer page進入free frame



## 9.4 Page Replacement
狀況：當沒有free frame讓想要載入的page進入時。


<補充 modify bit(dirty bit)>


page要從disk移入memory有兩大種演算法要掌握
1. frame-allocation algorithm
    1.要分配給每個process的frame有幾個
    2.那些frame要被replace掉
2. page-replacement algorithm
盡可能地降低page fault rate
    
- FIFS（First In First Out）舊的先走

    誰先進來，就決定它成為victim，
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ada5fbdabaf8f0b6d6933fe814d3b395)

<補充 Belady's anomaly：增加了frame數量，卻反而增加了更多的page fault>

- Optimal Page Replacement
選將來最久都不會使用的page換掉，需要往後看來選擇。

    **不會存在Belady's anomaly**

- LRU Algorithm
類似於Optimal Page Replacement，但不同是LRU Algorithm是往前看，選取最久沒有使用的來replace。

    **不會存在Belady's anomaly**

    實作：
    1. Counter：每個page-table的entry都需要一個counter去計算，在每一次memory reference時都遞增，如此一來我們就能取得最近每個page最近的refernce為何時，在依照這個counter的數值，選取最小的來替換。
    問題：counter可能overflow，或是每次要reset還要花上liner time
    2. Stack
    若現在使用的page不在stack就塞入，若已經存在於stack，就把該page拉到top，若要replace的話就選擇stack的bottom。
    
    
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fc64c4c1ff68102eb3c365cf9f714e1d)


<結論：Optimal和LRU皆屬stack algorithm，且不會產生Belady's anomaly



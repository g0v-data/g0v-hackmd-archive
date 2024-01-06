![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ad05c49e98741b40605567899d5147e5)

# **Meltdown**
**前言**
Google Project Zero近來揭發CPU的「推測執行」（speculative execution）安全漏洞,Meltdown與Spectre都是利用推測執行造成的處理器設計弱點所發動的攻擊方式，對於全球有用到問題CPU的桌機、筆電、伺服器、工業電腦甚至是智慧手機都受到衝擊。旁通道攻擊是針對硬體或物理上的特性來達成滲透，其中Meltdown與Spectre是針對CPU的Cache Attack，分別利用Out-of-order Execution與Branch Prediction來讀取其他程式儲存在記憶體中的資料。 CPU除了用Virtual Address Space區隔每個程式的程式碼與資料，也使用了Address Space Layout Randomization(ASLR)、Kernel Address Space Layout Randomization(KALSR)等技術，來防止駭客從固定記憶體位置(分配給作業系統以外程式的記憶體)找出機敏資料(帳號、密碼等)，而Meltdown與Spectre則可以透過針對Cache與記憶體的Flush+Reload攻擊來取得機敏資料。

Q1 Meltdown與Spectre兩者攻擊手法有何不同？

簡單說，Meltdown主要是打破了應用程式被禁止任意存取系統記憶體的保護機制()，使得應用程式也能跟著存取到記憶體內的內容。Spectre則是透過欺騙手法，讓其他應用程式能進到記憶體內的任意位置存取內容。兩者都是利用旁路攻擊（side channel attacks）的方式，從存取的記憶體位置竊取機敏資訊。

Q2 我的防毒軟體可以檢測或阻止這類的攻擊嗎？
理論上可行，但實際執行上極為困難。不像一般惡意軟體，防毒軟體很難在應用程式正常啟用時，就能分辨出是不是遭到Meltdown和Spectre的攻擊，除非是在發現已知的惡意軟體後，再通過比對Binary(二進位)文件來檢測這些攻擊。


Q3目前有沒有解決或修復的辦法？
現在已經有Linux、Windows 以及OS X等作業系統業者針對Meltdown釋出更新修補。另外還有些則是針對軟體的安全進行強化，個別釋出軟體更新（如LLVM的更新等），以降低遭受Spectre攻擊的危害。


Q4目前有哪類系統會受到Meltdown的影響？
Meltdown的部分，包括了桌機、筆電、雲端電腦設備均受影響。若從技術面來講，只要你的系統用的是能實作亂序執行（out-of-order execution）的英特爾處理器（自1995年出產的CPU幾乎都有提供此功能，少數例外，如 Intel Itanium與2013年以前的 Intel Atom），就有潛在風險。目前還不清楚 ARM與 AMD 處理器有沒有受影響。

 
**起因**
現代CPU為了提高處理性能，會採用亂序執行(Out-of-Order Execution)和預測執行(Speculative Prediction)。亂序執行是指CPU並不是嚴格按照指令的順序串行執行，而是根據相關性對指令進行分組並行執行，最後彙總處理各組指令執行的結果。預測執行是CPU根據當前掌握的信息預測某個條件判斷的結果，然後選擇對應的分支提前執行。

**原理**
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_69b0c3636dd227291df814537e85dacf)
每個階段執行的操作如下：

1）獲取指令，解碼後存放到執行緩衝區Reservations Stations

2）亂序執行指令，結果保存在一個結果序列中

3）退休期Retired Circle，重新排列結果序列及安全檢查（如地址訪問的權限檢查），提交結果到寄存器

**利用**
Meltdown漏洞的利用過程有4個步驟：

1) 指令獲取解碼
2) 亂序執行3條指令，指令2和指令3要等指令1中的讀取內存地址的內容完成後才開始執行，指令3會將要訪問的rbx數組元素所在的頁加載到CPU Cache中。
3) 對2)的結果進行重新排列，對1-3條指令進行安全檢測，發現訪問違例，會丟棄當前執行的所有結果，恢復CPU狀態到亂序執行之前的狀態，但是並不會恢復CPU Cache的狀態
4) 通過緩存測信道攻擊，可以知道哪一個數組元素被訪問過，也即對應的內存頁存放在CPU Cache中，從而推測出內核地址的內容

**目前防止方式**
Intel 在硬體做出來的改變只能緩解 Meltdown（Intel 稱為「variant 3」）和 Specter v2，是透過新的分區系統減輕了漏洞，同時改善了行程（process）和特權級別（privilege-level）分離，類似「防護牆」的做法。

**影響**
測試環境
處理器：Intel core i7-8700K
主板：ROG MAXIMUS ⅩAPEX
記憶體：芝奇Sniper X DDR4 2666記憶體套裝（8GB×2
顯卡：NVIDIA GeForce GTX 1070 Ti
硬碟：金士頓SUV400 240GB SSD、希捷1TB HDD
散熱器：Tt Floe Riing RGB 360水冷散熱器
作業系統:windows 10

|   測試項目        |修補前          |修補後           |
| --------         | --------      | --------       |
| 4K影片轉720P      | 30S           |31S             |
|execl中相同方程式運算|2.782/s        |2.796/s         |
|CPU-Z Bench多線程得分|3889.5        |3866.3          |
|sisoftware sandra |194.46/GOPS    |193.56/GOPS     |

**心得**


參考資料
http://www.cc.ntu.edu.tw/chinese/epaper/0045/20180620_4508.html
https://men.fanpiece.com/leiphone/%E8%A7%A3%E8%AE%80CPU%E6%BC%8F%E6%B4%9E-Meltdown%E5%92%8CSpectre-c1306485.html
https://ek21.com/news/1/113368/
中獎名單
https://kb.vmware.com/s/article/52085

# TLB (Translation lookaside buffer)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_dc140e0e97806770e63c037ef113bec2)


Page table是存放在記憶體中，作業系統運用page-table base register(PTBR)記錄起始位置跟page-table length register(PTLR)記錄page table的大小。這有個缺點：速度慢，就是因為他必須存取記憶體兩次，一次是page table，一次是要找的data。幸好這個缺點有個方法可以解決，用Translation Look-aside Buffers(TLBs)，他就類似所提的快取(cache)。

Inverted page table(反轉分頁表)：
他是以physical address為對象，建立一個page table給所有process(有m個frame，就有m個table entry)，每個entry都會紀錄被哪個process的page運用，所以裡面記錄著process id跟page number。

分頁表是一種資料結構，也是一種管理記憶體的方式。在使用虛擬記憶體的狀況下，程式會以為記憶體是一大塊連續的，不過實際上，因為分頁表做了轉譯地址的動作，所以這些記憶體有可能在實際上並不是連在一起的。

處理器的記憶體控制器會有一份快取表，紀錄最近用到的實體位置-虛擬位置組合。這個叫做 TLB，Translation lookaside buffer。
當要將虛擬記憶體位置轉成實體位置的時候，記憶體控制器會先去看這張表，如果有這組紀錄，就是中了tlb hit，並返回要查的實體位置。如果沒中，就得去分頁表(memory page)裡面做掃表的動作。

掃分頁表也可能會發生失敗的問題，例如說地址寫錯（這狀況有可能會引起存取錯誤，segfault），或是那東西被趕去硬碟上了（這時候就得去讀硬碟）。

# KASLR (Kernel	Address	Space Layout Randomization)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6f48696efad7d4c96d12951325829df6)

Kernel 每次重開機相關 fucntion 都會映射到隨機的位置上

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_66dadbeb660c758f7db8d47d28e0cb59)

Linux Kernel 有一fucntion是叫 commit creds 是駭客想攻擊的的function

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a76cc9d768748637c176be141169749d)

Normal user can't not access Kernel Space address

Only root user can access and KASLR change kernel symbol address every boot

# TLB Time Side Channel 
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4891f630e65d7b7fa2094ea3685a7289)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_990e1bcbddfdfe6c0372acf4de5c74b1)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_30963740a6f07809b0fa2c97a2fc8138)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a3553e9ab653d532a3c84c48343f8abf)



![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0a15c67d2b4c5cf926bf3519f0282521)
If an executed instruction causes an exception,
diverting the control flow to an exception handler, the subsequent instruction must not be executed. 

Due to outof-order execution, the subsequent instructions may already have been partially executed, but not retired. However, architectural effects of the execution are discarded.

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_31880c6077046228c38a3220e808d489)


Out-of-order Execution
因為不同指令所需的執行時間長度不一樣，當前幾條CPU指令尚未執行完成以前，提前完成的CPU指令就稱為Out-of-order Execution。[2]
Meltdown透過在引起Exception Handker前，CPU先完成從其他程式的記憶體空間載入資料到Cache的Out-of-order Execution，當Out-of-order Execution因Exception Handker被中斷後，雖然Reorder Buffer會清空Out-of-order Execution所使用的Registers，但是載入的資料仍存在Cache中，再透過Flush+Reload就能從最後一層Cache中取得資料。

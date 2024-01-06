# 07屆SP期末考古筆記
1. Compare user-level thread and kernel-level thread
* User-level: Kernel不知道thread的存在，user 自己維護一個thread control block
* Kernel-level: Kernel除了維護Process control block之外也要維護Thread control block，因為system call，消耗較高

2.Compare shared library & static library
* Shared: 動態連結，編譯時先不把library的內容編譯進去，因此執行檔size較小，直到執行該執行檔內屬於shared library的函式，才會動態連接至shared library，若library有更新，也不需重新編譯執行檔。
* static: 靜態連接，編譯時直接把library內會用在這個執行檔裡的內容編進去，因此執行檔尺寸較大，會有library更新時也需要重新編譯執行檔的問題

3. Compare Deadlock & Starvation:
* Deadlock: 由於一組process導致circular waiting(可能是兩個operation互相等待)，導致所有在waiting cycle中的process無法往下執行
* Starvation: 低優先權的process長期或無限期,無法獲得系統的資源

4. Compare
* system buffer cache: 減少DiskIO的次數以提高效能
* c-library buffer: 減少trapping system的次數以提高效能

keyword: Delay Write, Read Ahead

2(b)why binary I/O such as `fwrite` has portability issue
binary IO 讀取不需要格式，只要直接讀取內容。像是char是1byte，int是4bytes，如果binaryIO讀進了4byte會不知道是4個char 還是1 個int，還會有little-endian和big-endian解讀上的問題

2(d)Explain why every running process seems to have exclusive use of CPU and main memory in UNIX
* exclusive use of CPU:
logic control flow, context switch
* exclusive use of main memory:
private address space, kernel會維護每個process的virtual memory和實際上的physical memory之間的對應關係，使得不同process不會彼此access到同一個memory block
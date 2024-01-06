# OS 筆記

###### tags: os


---

### 簡介
作業系統沒有一個明確的定義，但它是用來分配電腦的資源去做到效能最大化的一個工具，在啟動OS前要使boostrap program這個程式先啟動才行，啟動後作業系統會有兩種模式，分別為duo mode 跟 中斷驅動(interrupt driven)，前者是為了保護特定的元件而分成root&user，後者則是可以去讓OS去做資源安排

---

### process
process(程序)是正在執行的program，一個process會包含以下五個
1. program code
2. process counter 、 process register
3. stack(儲存暫時性資料)
4. data section(儲存跟程式、process相關的資料)
5. heap(執行時產生的動態的記憶體空間)

在電腦的世界裡還有所謂的父母(parent)與子女(child)的關係，在程式碼裡面最常看到的是`fork()` 要注意的是有時候會結束掉parent process而忘記child process而導致出現zombie process消耗無謂的資源
# System Programming --- Slide 1

### Computer System
* Hardware:
    * Physical device
    * Microarchitecture 微架構（使指令集架構可以在處理器上被執行）
    * Machine Language（1&0）
* System Programs
    * Operating System e.g. Unix, Windows ...
    * Compilers, Editor, Command interpreter
     
* Application programs

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b6b209aee3b1e6e2f13cbccdd4d63808.png)



---

###  Function call VS System call
| Function call                                                                | System call |
| ----------- | ----------- |
| Caller and callee are in the same process.| OS is trusted; user is not.       |
|Same user||
|Same "domain of trust"||

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4cf6fea9a5e35d2c1e4bd5a10c018ffc.png)




---

### User VS Kernel 
| User mode | Kernel mode |
| -------- | -------- | 
| forbidden to access those portions of memory that have been allocated to the kernel or to other programs |  priveleged | 

When a user mode process wants to use a service that is provided by the kernel (e.g. a **system call**), the system must **switch temporarily into kernel mode**. 

###    
#### System memory is divided into two parts:

| User space | Kernel space | 
| -------- | -------- | 
| each user process is protected (**isolated**) from another(except for shared memory segments and mmapings) | kernel executes | 

When it performs a **system call**, user program executes in Kernel space

####    
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bbd666144dd57ef01d9e6fe5068927e1.png)



---

### Meaning of Real, User and Sys time statistics:
-    Real is **wall clock time** – time from start to finish of the call **including time used by other processes** and time the process spends blocked (for example if it is waiting for I/O to complete).
-    User is the actual CPU time used in executing the process. ...(**User Mode**) 
-    Sys is the amount of CPU time spent in the **kernel** within the process.

> 在多核心的電腦裡可能發生“ real < user + sys ”的情況
> 
real time 一樣的前提下，能讓 user time 和 sys time 比較小的 process ，我們認為他效能較佳
####  案例探討：



case1: 執行下列程式碼
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f3d60a301a0c1bf3542ff777dff40b77.png)
####    
Result: **real 5.60, user 5.50, sys 0.00 (bad)**
####     
case2: 執行指令 time –p sleep 5
Result: **real 5.00, user 0.00, sys 0.00 (good)**
####     
結論：case1 把休息寫在程式碼裡，所以 CPU 也有消耗
#     
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_694915d1eba388fa3dc3fbb1e997a3c9.png)
#    

### Resource Manager
* Services for Application Programs:
User Identification, Process Management,
Memory Management, File/Directory Management,
Inter-process Communication, Signal, I/O Management
(e.g., Terminal, Network, etc), …
* OS Kernel:
CPU Scheduling, Virtual Memory, File System,
Protection, Security, Synchronization, I/O Control, …
#    
### User Identification in UNIX
#### Logging In 
**/etc/passwd** 檔案儲存了所有 Linux 帳號的登入資訊，例如 User ID, Group ID, 家目錄, shell 等。每一個帳號一行 資料，每個欄位以冒號 “：” 分隔。一般帳號對 passwd 有可讀權限，而**只有 root 有可寫入的權限**。
- Username: 帳號登入的 username, 長度可以 1 至 32 個字元。
- Password: 這個欄位會**用 x 字元代替加密的密碼**(或＊字元)，而加密的密碼儲存在 **/etc/shadow** 檔案內。
- User ID (UID): 每個帳號都有一個獨一無二的 user ID (UID), **UID 0 是留給 root**，而 1 至 99 預留給系統帳號。
- Group ID (GID): 儲存在 **/etc/group** 的 primary group ID.
- User ID Info: 可以加入一些額外的資訊，例如姓名，電話等，但不是必須要有內容。
- Home Directory: 帳號的家目錄。
- Shell: 帳號使用的 shell。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_52b5126cc04e8da21478e772b3718d3b.png)


---

### Password Encryption and Salt
In cryptography, a **salt** is **random data** that is used as an additional input to a one-way function that hashes data.
* e.g. 
    * crypt(3) designed to make a key search computationally expensive
    * crypt( “apple”, “am” ) = “amADBMNoVAZpc”
    * crypt( “water”, “pm” ) = “pmRarHxhhU34U”
* Salt is converted into a **two character string** and stored in the encrypted password file
* Salt allows users to use the **same password on different computers**
* /bin/passwd **selects a salt based on the time of day**
     
---
### Process Management

| Program | Process | 
| -------- | -------- | 
| 建築藍圖     | 正在施工的工程     | 
|An execut**able** file residing in a disk file|An **executing** instance of a program|
||Unique process ID|
||Related shell commands: ps, top
ps - report a snapshot of the current processes
top – display processes

---
### CPU Scheduling
Deciding which process should occupy the resource (CPU, disk, etc)

> User can **change a process priority**
> Related shell command: **nice**
> 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e48adbfde08d09ef7bc6e96692408d60.png)
CPU處理簡單工作
Event處理expensive 工作，像是diskI/O
* Ready State: Ready Queue
* Running State: CPU
* Blocked State: Event Queue


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6807579921080c7ce29b172f1cc2d52b.png)

---
### Unix Process
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3d7b8b809372f414fce85f9ae0c84d19.png)

#### Unix Shells
* **/bin/sh**, Bourne shell (已經被 /bin/bash 所取代)
Steve Bourne at Bell Labs
* **/bin/bash**, Bourne Again shall (就是 Linux 預設的 shell)
* **/bin/csh**, C shell (已經被 /bin/tcsh 所取代)
Bill Jay at Berkeley: Command-line editing, history, job-control, etc
* **/bin/ksh**, KornShell (相容於 bash))
David Korn (successor of Bourne shell): Command-line editing, job-control, etc
* **/bin/zsh**  (基於 ksh 發展出來的，功能更強大的 shell)
* Related shell command: chsh (i.e.,change shell)

殼層（英語：shell）指「為使用者提供使用者介面」的軟體，通常指的是命令列介面的解析器。一般來說，這個詞是指作業系統中提供存取核心所提供之服務的程式。Shell也用於泛指所有為用戶提供操作介面的程式，也就是程式和用戶互動的层面。因此與之相對的是核心（英語：Kernel），核心不提供和用戶的互動功能。

#### Windows OS 是 shell 嗎?
shell 分為圖形使用者界面(GUI)和命令列界面(CLI)兩大類。

嚴格來說 Windows OS 裡面的的資源管理器(explorer.exe)就是一種 GUI 類型的 shell，而命令提示字元(cmd.exe)則是 CLI 類型的 shell。

Unix 系統則有不同的 shell，如 bash、C shell、Z shell 等等，而 macOS 內建預設都是 bash(即 Bourne Again shell)。

---
### Inter-process Communication
* Pipe
在類Unix作業系統（以及一些其他借用了這個設計的作業系統，如Windows）中，管道（英語：Pipeline）是一系列將標準輸入輸出連結起來的行程，其中**每一個行程的輸出被直接作為下一個行程的輸入**。 每一個連結都由匿名管道實現。 管道中的組成元素也被稱作過濾程式。
* Filter
A program that takes input and transforms it in some way
    * wc - gives a count of words/lines/chars
    * grep - searches for lines with a given string
    * more
    * sort - sorts lines alphabetically or numerically
* Examples of Filter & Pipe
    * ls -la | more
    * cat file | wc
    * man ksh | grep “history”
    * ls -l | grep “bowman” | wc
    * who | sort > current_users
---
### Some System Calls For Process Management


| Call | Description |
| -------- | -------- |
| pid = fork()    | Create a child process identical to the parent     |
| pid = waitpid(pid, &statloc, options)     | Wait for a child to terminate     |
| s = execve(name, argv, environp)     | Replace a process' core image     |
| exit(status)     | Terminate process execution and return status     |


---
### Typical Memory Arrangement
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_92cc00b602ee0359edfb311e96a8c583.png)

---
### UNIX File and Directory
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4ef1ebccbbfed2cbe796ef5345273b3f.png)
###    
Unix命令列的**mount指令是告訴作業系統，對應的檔案系統已經準備好，可以使用了**，而該檔案系統會對應到一個特定的點（稱為掛載點）。掛載好的檔案、目錄、裝置以及特殊檔案即可提供使用者使用。除了作業系統呼叫的mount指令外，mount_root()會優先掛載（或稱根目錄） 。在這個情況下，作業系統會在呼叫setup前，先呼叫mount。

它的對應指令，umount，則是告訴作業系統，斷開與該檔案系統的連接，使其脫離掛載點。mount與umount指令必須以**超級使用者的權限執行**。檔案系統也可在/etc/fstab檔案中指定特定使用者才能掛載。這同樣也只能由超級使用者進行修改。


---
### File Permission
`輸入指令 ls -l`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f0aad75a673c06abea5d820484a9ff48.png)
Read ( r ) 4, write ( w ) 2, and execute ( x ) 1

For **owner, group, and world (everyone)**
* chmod <mode> <file(s)>
* chmod 700 file.txt
* chmod g+rw file.txt
* Related shell commands: chmod,chown,touch

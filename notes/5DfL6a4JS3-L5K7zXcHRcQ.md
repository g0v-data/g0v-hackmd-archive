# System Programming - Slide5 
# chapter 8

### Process Control
* Objective
    * Process Control
        * process creation and termination,
program execution, etc.
    * Process Properties and Accounting
e.g., ID’s.
    * Process Identifiers
        * Process ID – a nonnegative unique integer
        tmpnam:
        C 库函数 char *tmpnam(char *str) 生成并返回一个有效的临时文件名，该文件名之前是不存在的。如果 str 为空，则只会返回临时文件名。

      


process ID會reuse(而非recursion的assign)，但當一個process被kill不會立刻reuse

### Booting
Boot process 把 Unix process叫起來
Bootstrapping
* **The process of starting up a computer from a powered down condition** (cold boot)
* Initializing all aspects of the system, e.g., CPU registers, device controllers, memory, etc.
* The memory-resident code reads the boot program from the boot device
* Boot program reads in the kernel and passes control to it.
* Kernel identifies and configures the devices.
* Initializes the system and starts the system processes.
* Brings up the system in single-user mode (if necessary).
* Runs the appropriate startup scripts.
* Brings up the system for multi-user operation. 


### Special Processes
* PID **0 – Swapper** (or scheduler)
    * PID為0者為交換行程（英語：swapper），屬於核心行程，負責分頁任務
    * **Kernel process**
    * No program on disks correspond to this process
* PID **1** – **init** responsible for **bringing up a Unix system**
    * bootstrap到尾聲時會呼叫這隻process 
    * **after** the kernel has been **bootstrapped**.
    * User process with superuser privileges
    * Initializing system processes, e.g., various daemons, login processes, etc.
    * /etc/rc* or /sbin/rc*
* PID **2** - pagedaemon responsible for **paging**
    * Kernel process

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6801b233f733d39ed755ec4fbff5f5cf.png)

### Process Control Block (PCB)
Information associated with each process
![Uploading file..._ju7w0v2ul]()

* **Process state: running, ready , block**
* Program counter
* CPU registers
* CPU scheduling information
* Memory-management information
* Accounting information
* I/O status information
* sys/proc.h
* Some of the fields of the proc structure:重要！
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b0c69b371e98cf10b4939c51e2a42154.png)

### Process States
* 要有新的process一定要用fork
* New: The process is being created
* Running: Instructions are being executed
* Waiting: The process is waiting for some event to occur
* Ready: The process is waiting to be assigned to a processor
* Terminated: The process has finished execution

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a1ed323f6b2a8a23f986bc07e52b1a55.png)

### CPU Switch between Processes
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7c85c75cbf96fd43035cc1c5602cd6d4.png)
換得了更好的response time，但消耗了ＣＰＵ(從PCB0和PCB1之間切換的cost)

### Process Scheduling Queues
* **Job queue** – set of **all processes** in the system -> 所謂的process table
* Ready queue – set of all processes residing in main memory, **ready and waiting to execute**
* Device queues – set of processes **waiting for an I/O device**
* Processes migrate among the various queues

### Ready Queue & I/O Queues
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2b6092c996591723e0aa8dfb650bd1ff.png)

### Process Scheduling
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c83b660849a75b5aba6a3769823442d5.png)
### Process Metadata & Content
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cc91df2314100dc70c44c9005aba83aa.png)

### Process Control
```
#include <sys/types.h>
#include <unistd.h>
pid_t getpid(void)
pid_t getppid(void)
uid_t getuid(void)
uid_t geteuid(void)
gid_t getgid(void)
gid_t getegid(void)
```
None of them has an error return
### Process Creation and Termination 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c528b3dbeba66522cae6d3244aa06d2c.png)
* childprocess如果結束了會把exit的方式儲存在PCB的p_xstat，等parent process接收後，childprocess的PCB就會被回收，如果childprocess的p_xstat沒有被parent process接收，那childprocess的virtual memory, register等等資料都會被釋放，但pid沒有辦法被recycle，就變成zombie process.

### What's a fork()?
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3d2e709dffa8e682ce15c920b477d1ee.png)

* Child is an exact copy of the parent process.
* They **have their own memory space**
### fork
```
#include <sys/types.h>
#include <unistd.h>
pid_t fork(void)
```
* The **only way beside the bootstrap process to create a new process**.
* Call once but return twice
    * **0** for the **child process** (getppid)
    * Child pid for the parent (1:n) 要有這一部不會變zombie
* Cannot predict which process runs first
    * Process scheduling
* **Copies of almost everything but no sharing of memory**, except text Copy-on-write
* They have their own memory space.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_39a033be857f6a26febbe57bb8c58e53.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7c1e79125f469b90303c888c0fa63258.png)
上圖是copy-on-write的技術
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cc28bfa95ff7fd8bb3a98548ec4c2bf1.png)

#### Example of fork()
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_964a30c8a972123cbfc696f9870b400a.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7c5e59cba34ac766d75d9773a13de2fb.png)
* buffer IO 的好處是減少system call
* 當standard output指向terminal: line buffer
一讀到\n就把“before fork\n”印出去了，buffer也會清空，
所以只有印一次
* 當standard output指向file: fully buffer
會將所有output放在buffer裡直到程式結束，所以parent & children 的buffer各有一個“before fork\n”，總共印兩次

### File Sharing
Sharing of file offsets (including stdin, stdout, stderr)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3963ad19812f7582c527cdf74285a0e3.png)

#### Practice
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a60af83fd48aa8ee0f7e66c217db5241.png)
Ans:4
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_97c92eaafcda9b466e18b6da67298a0a.png)

Ans:5
重要！重要！

* Normal cases in fork:
    1. The parent waits for the child to complete.
    2. The parent and child each go their own way (e.g.,network servers).
* Inherited properties:
    * Real uid, effective uid, real gid, effective gid, supplementary gid, process group id, session id, controlling terminal, set[ug]id flag, current working dir, root dir, file-mode creation mask, signal mask & dispositions, close-on-exec flag, environment, attached shared memory segments, resource limits
* Differences on properties:
    * Returned value from fork, **process id**, parent pid, **tms_[us]time, tms_c[us]time**, **file locks**, pending alarms, pending signals
    * The tms_**u**time element is the amount of time **spent executing your code**, or the code in the C library. The tms_**s**time element is the amount of time spent in the **kernel executing code** on your behalf.
* Reasons for **fork to fail**
    * **Too many processes** in the system
    * The total number of processes for the real uid exceeds the limit `CHILD_MAX`(PCB發完)
* Usages of fork
    * Duplicate a process to run different sections of code
        * Network servers
    * Want to run a different program
        * shells (**spawn = fork+exec**)





### vfork 早期發展出來的
* Design Objective
    * An optimization on performance
        * No fully copying of the parent’s address space into the child.（fork最被詬病的一點）
        * **Sharing of address space**，但childprocess還是會有自己的PCB，只是virtual memory那一塊沒有複製，直接指到parent'VM，使得parent在child結束前都不能run
    * Execute **exec() right after returns from fork()**.
* Mechanism – SVR4 & 4.3+BSD
    * Since 4BSD
        * <vfork.h> in some systems
* vfork() is as the same as fork() **except**
    * The **child runs in the address space of its parent**.
    * The parent waits until the child calls exit() or exec().
        * **Child** process **always** executes **first**.
        * A possibility of deadlock if the child waits for the parent to do something before calling exec().

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1d56180b15b1a1b7b4c06c04b3a8da27.png)
exit(0)造成錯誤要用有底線的＿exit(0)
exit(0)會把buffer flash掉

### Dead Lock
* Deadlock is a situation wherein two or more competing actions are waiting for the other to finish, and thus neither ever does
* Example:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e432a2d67d17d7ba3fd8fd9c686df5af.png)

### Process Termination (Ch7.3)
Eight ways to terminate:
* Normal termination
    * Return from main()
        * exit(main(argc, argv));
    * Call `exit()`
    * Call `_exit()` or `_Exit()`直接回到kernel
    * Return of the last thread from its start routine
    * Calling `pthread_exit` from the last thread.
* Abnormal termination (Chapter 10)
    * Call `abort()` (generating the SIGABRT signal)
    * Be **terminated by a signal**
    * Response of the last thread to a cancellation request

### How a C program is started and terminated
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b6e4eda7385865509c6282428771301b.png)

### Process Termination

```
#include <stdlib.h>
void exit(int status)
```
* Perform cleanup processing
    * Call exit handlers
    * Close and flush I/O streams (fclose)
    * Called once, never returns
    * **Puts the process into “zombie” status**
    
```
void _Exit(int status)    //ANSI C
```

```
#include <unistd.h>
void _exit(int status)    //POSIX.1
```
* Exit status:
    * Undefined exit status:
        * Exit/return without status.
        * main() is not declared to be an integer.
* 0 as the status:
    * main() is declared to be an integer and main() falls off the end.
    * return(0) and exit(0).

```
#include <stdlib.h>
int atexit(void (*func)(void))
```
* C庫函數 int atexit(void (*func)(void)) 會導致程序終止時被調用指定的函數功能。可以注冊在你喜歡的任何地方，但它會被稱為當時的程序終止的終止函數。
* At least 32 functions called by exit – ANSI C, supported by SVR4&4.3+BSD
* The same exit functions can be registered for several times.
* Exit functions/handlers will be **called in reverse order of their registration**.
* Exit handlers registered will be cleared if exec() is called.

#### Example of atexit()
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5ec068f8bfd885b50821cdbb983ea529.png)

### wait & waitpid
```
#include <sys/types.h>
#include <sys/wait.h>
pid_t wait(int *statloc)
pid_t waitpid(pid_t pid, int *statloc, int op)
```
* **Called by the parent process** to retrieve the termination status of its child process
    * **wait** will **block** until one child(任何一個child) terminates or an error could be returned
    死掉的那個child的status存在 *statloc裡
    * waitpid could wait for a **specific one**(可以指定等它死掉的child) and **has an option not to be blocked**(寫在op參數)
* **SIGCHILD** from the kernel if a **child terminates**
    * Default action is ignoring
* Three situations in calling wait/waitpid
    * Block
    * Return with the termination status of a child
    * Return with an error.
* Termination Status <sys/wait.h>
    * Exit status (WIFEXITED, WEXITSTATUS)
    * Signal # (WIFSIGNALED, WTERMSIG)
    * Core dump (WCOREDUMP)
    * Others (WIFSTOPPED, WSTOPSIG)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4f3e719b84d7ec4eccd3c1cc32f50c1c.png)

```
pid_t waitpid(pid_t pid, int *statloc, int op);
```
### waitpid的pid
* pid == **-1** -> wait for **any child**
* pid > 0 -> wait for the child with pid
* pid == 0 -> wait for **any child** with the **same group id**
* pid < -1 -> wait for any child with the group ID = |pid|
* pid of the child or an error is returned.
> wait(&status) == waitpid(-1, &status, 0)
> 
#### Errors
* No such child or wrong parent
#### Option for waitpid（non-blocking）
* **WNOHANG**(op=0)(沒有任何小孩死掉->立刻return 0，讓它不會block), WUNTRACED
* WNOWAIT, WCONTINUED (SVR4)
* ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c7f7b66324266bbd56c25fa5268ccd33.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c45d0f5d211211f890832df9b40f02e1.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0ec879caa6caefd6377bb06e0e873777.png)

### stop & continue 不講

### Zombie & Orphan
* Zombie
    * The process has terminated, but its **parent has not yet(parent也可能已死) waited for it**.
    * It keeps the **minimal information** (e.g., **process ID, termination status, and CPU time** taken) for the parent process.
* What if the parent process terminates before the child process? (orphan)
    * **Inherited by init**
        PCB會紀錄這個process的parent id，在process Terminate的時候告知parent，然後檢查一整個process table看有沒有process的parent是這個死掉的process，有的話就把死掉的process的child process的parent id設為1.
    * When a parent terminates, it is done by the kernel.
    * Clean up of the zombies by the init – wait whenever needed!


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fa428c55c3c69e2b2bd1c0734b5547d7.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7557fa5583967c20826729bff71e7f6b.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_163688e914ab9cf6e1bd33cf3eb55759.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_510e50f7dfc93c6fcd06b0885fb7223a.png)

### 強到爆的方法：double fork
核心概念：
1.把原本要給child做的事給grandchild做
2.讓child fork 出grandchild後就立刻死掉 （parent process還是要wait child process不過child process很快就死了沒差）
3. grandchild變orphan重新接到init，init會自己定期清理zombie
效果：grandchild變成一隻background process，我原本的parent process不用block在那邊等它

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f251ea43fb01f956b5ca9bc60725c828.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e98f26c8f53b2901611c782bfca87ccd.png)



### Race Condition
競爭危害（race hazard）又名競態條件、競爭條件（race condition），它旨在描述一個系統或者進程的輸出依賴於不受控制的事件出現順序或者出現時機。此詞源自於兩個訊號試著彼此競爭，來影響誰先輸出。

舉例來說，如果電腦中的兩個行程同時試圖修改一個共享記憶體的內容，在沒有並行控制的情況下，最後的結果依賴於兩個行程的執行順序與時機。而且如果發生了並行存取衝突，則最後的結果是不正確的。

競爭危害常見於不良設計的電子系統，尤其是邏輯電路。但它們在軟體中也比較常見，尤其是有採用多執行緒技術的軟體

#### Example:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_65eabf391c1b8f7bd7995a9590e1ee95.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0c7ce5605d1422f3a5997f96a0326d21.png)
有可能grandchild process睡完2秒回來child process還沒死-> 出錯
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_24159d00810dd7e2ebb2164ca151b8fa.png)


### exec系列函數：把程式內容換掉，但沒有換process的環境
exec替換進程映像 在進程的創建上Unix採用了一個獨特的方法，它將進程創建與加載一個新進程映象分離。這樣的好處是有更多的餘地對兩種操作進行管理。

當我們創建了一個進程之後，通常將子進程替換成新的進程映象，這可以用exec系列的函數來進行。當然，exec系列的函數也可以將當前進程替換掉。

例如：在shell命令行執行ps命令，實際上是shell進程調用fork複製一個新的子進程，在利用exec系統調用將新產生的子進程完全替換成ps進程。

用exec函數可以把當前進程替換為一個新進程，且**新進程與原進程有相同的PID**。exec名下是由多個關聯函數組成的一個完整系列，

```
#include <unistd.h>
int execl(const char *pathname, const char *arg0, … /* (char *) 0 */);
int execv(const char *pathname, char *const argv[]);
int execle(const char *pathname, const char *arg0, … /* (char *) 0, char* const envp[] */);
int execve(const char *pathname, char *const argv[], char *const envp[]);
int execlp(const char *filename, const char*arg0, … /* (char *) 0 */);
int execvp(const char *filename, , char *const argv[]);
```
* l, v, and e stands for list, vector, and environment, respectively.
* 大部分情況很少需要用environment variable
* With p, a filename is specified unless it contains ‘/’.
帶 p 的exec函數：execlp,execvp，表示第一個參數path不用輸入完整路徑，只有給出命令名即可，它會在環境變量PATH當中查找命令
    * PATH=/bin:/usr/bin:.
    * /bin/sh is invoked with “filename” if the file is not a machine executable.
    * 有p的**遇到not binary會認為是script**
* 最後一個參數要是`(char*) NULL`或`(char*)0`
* 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_787996d50b4173c6c74c1c978b44afac.png)
* in-initialized data 和 initialized data 不可動

#### Environment Variables
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1ee20fca372afb7505ef4660df8fe778.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8c0dbf931bf2159b10e0daa511d315f6.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_57d34caa7970383bd1254c64ab653796.png)

特性：
* **Inherited** from the calling process:
    * pid, ppid, real [ug]id, supplementary gid,
proc gid, session id, controlling terminal,
time left until alarm clock, current working dir,
root dir, file mode creation mask, file locks,
proc signal mask, pending signals, resource
limits, tms_[us]time, tms_cutime, tms_ustime
    * FD_CLOEXEC flag
* Requirements & Changes
    * Closing of open dir streams, effective
user/group ID, etc.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_102effe880d4b46474f55f3c7688301b.png)

* 呼叫exec時換了新進程但PID一樣，process table entry也沒換
* FD_CLOEXEC幫我換程式內容時把該關的fd pointer關掉

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b88bc7dbacf70e4b3c2747b97670cfbd.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_90d243953a3f6801c900a943ba23c8cc.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_75cb09cf224ec1835abb0db300a2e8c7.png)

### Interpreter Files
```
Def: a file begins with a line of the form:
#! pathname [optional-argument]
E.g., “#! /bin/sh”
```
* Implementation:
    * Recognition is done within the kernel
    * Interpreter (normally an absolute pathname) vs the interpreter files
    * Line-limit of the first line, e.g., 32 chars
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_36326ed3dc6a3b1de422687f3b8ffdef.png)

Interpreter: 執行檔名 -f program名
/bin/awk –f /usr/local/bin/awkexample file1 FILE2 f3

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1ae52e57c8766e293cc8217533499654.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8b473f87438c37b0eaa6564eec4f4016.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_25da166b41153b1e6bb68473115eeb11.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3f17ce13e1c6f1f11f1525b35cf89c9e.png)


### Why Interpreter Files?
* Pro
    * Hide the fact that certain programs are scripts in other languages.
    * Provide an efficiency gain with interpreter scripts(wrapping the program in a shell script)
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c973103867e48f0285f538003bb8b4cb.png)
        *  execlp -> /bin/sh -> fork, exec, wait
    * Choose shells other than /bin/sh
* Against:
    * Efficiency for users but at the cost of the kernel
    (還得特別去辨認是不是interpreter file)
    * Executable files? /bin/sh? /bin/awk?

### Why keep fork() and exec() separate
* In many client-server applications, the server may fork processes that continue to execute the same program
    * multi-threading
* Child ensures that the new program to be executed is in the desired state
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_273475672df547192945ff455674f7c3.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6866ab75e683c1c6f8b70b4351ff18cd.png)

### Pipes (Ch15.2)
* Pipes have two limitations:
    * They are half-duplex.
    * 半雙工（half-duplex）的系統允許二台設備之間的雙向資料傳輸，但不能同時進行。 因此同一時間只允許一設備傳送資料，若另一設備要傳送資料，需等原來傳送資料的設備傳送完成後再處理
    * They can be used between processes that have a **common ancestor**.
    * Stream pipes are duplex (Chap 17.2)
    * **Named pipes/FIFOs** and **named stream pipes** (Chap 17.2) can be used between process **not having the same ancestor.**
```
#include <unistd.h>
int pipe( int filedes[2] );


```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_848ab87dc0987092586d029bb30c3cc5.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_877bbea79afa5705d808ecf8bbec72e9.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_136631e9c5f1edae91712ea7ac6a0672.png)
考試時不用的要關

### Read from/Write to Pipes
* When the write end is closed, after all the data has been read, reading from a pipe returns 0 (end of file)
* When the read end of a pipe is closed, **writing** to a pipe **triggers SIGPIPE signal**.
* Kernel’s pipe buffer size:
    * Constant PIPE_BUF specifies the pipe buffer size.
    * Writing PIPE_BUF or less **will not be interleaved**.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_55818c4ed69d05848e6b611f2968d993.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b10e2cd748234e99eb84a1c83d4c4bf1.png)
要用dup2，轉完不要忘記把不用的fd關掉
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_47009aecbeeeac70fcf84692c64e6a93.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5cba677671555405e5824ccb176092ef.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9ab8a5c8d15dc9bc3e9b5fef0a924c88.png)

#### Avoid Race Condition
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_25bb4f4f878b0a6aa333142edf16f8dc.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_447da0c0dafa2e748fcd247396f9bc5a.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_374b405be9efcc88c73f53d28e5bcf94.png)



### FIFOs (Ch15.5)
* FIFOs – named pipes for (un-)related processes to exchange data.
    * A file type – st_mode (S_ISFIFO macro)
    * Data in a FIFO removed when the last referencing process terminates.
    * 匿名管道由pipe函数创建并打开。
命名管道由mkfifo函数创建，打开用open。
FIFO（命名管道）与pipe（匿名管道）之间唯一的区别在它们创建与打开的方式不同，这些工作完成之后，它们具有相同的语义
```
#include <sys/types.h>
#include <sys/stat.h>
int mkfifo(const char *pathname, mode_t mode);
```
* mode and usr/grp ownership = those of a file
* Op’s: open, close, read, write, unlink, etc
* O_NONBLOCK
    * NO -> an open for read-only blocks until some other process opens the FIFO for writing (write-only as well).
    * Yes -> an open for read-only always returns, while that for write-only returns with an error(errno=ENXIO) if there is no reader.
* Write for a no-reader FIFO -> SIGPIPE
    * Closing of the last writer -> EOF
* Atomic writes
    * PIPE_BUF

#### How to pipe the standard output of aprocess to more than one file/process?
* Example – Stream Duplication
```
mkfifo fifo1
prog3 < fifo1 &
prog1 < infile | tee fifo1 | prog2
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ce920a21efd510f9f2044ab999903f5c.png)





# System Programming - Slide8
# chapter9

### Signals
#### Objectives:
* An overview of signals
* Related functions and problems (reliability & incompatibility)
#### What is a signal?
* Used to notify a process of important events
* Synchronous vs. asynchronous (events)
    * Synchronous: occur as a result of instruction execution
        * e.g. **divided by zero, segmentation fault**
    * Asynchronous: external to current execution context
        * e.g. killed by other processes, **child termination**
        * 不可預期說content跑到哪裡時會死掉
* 15 signals for Version 7, 31 signals for SVR4 & 4.3+BSD –<signal.h> (# > 0)
    * signal有編號，０是null signal

### Conditions to Generate Signals
* Terminal-generated signals
    * **DELETE key**, Ctrl-C -> SIGINT (2)
* Signals from exceptions
    * **divided-by-0** -> **SIGFPE** (8)
    * **illegal memory access** -> **SIGSEGV** (11)
* Function kill
    * Owner or superuser
* Shell command kill, e.g., `kill –9 pid` (SIGKILL)
* Signals because of software conditions
    * reader of the pipe terminated -> SIGPIPE
    * expiration of an alarm clock -> SIGALRM


### Disposition of a Signal (Action)
* Ignore signals
    * **SIGKILL** and **SIGSTOP** can not be ignored.
    * There could be undefined behaviors for ignoring signals, such as SIGFPE.
* Catch signals
    * **SIGKILL** and **SIGSTOP** can not be caught
    * Provide a **signal handler**
    * e.g., **calling waitpid() when a process receives SIGCHLD**
* Apply the default action
Terminate, ignore, stop
大部分的default action都是terminate
#### Examples of Signals
* SIGABRT – terminate w/core
    * Call `abort()`
* SIGALRM – terminate
    * Call `setitimer()`, `alarm()`
    * `setitimer()`可以設定不止walk clock time也可以設定user time
    * `alarm()`只能設walk clock time
    * `alarm()`用過一次就失效，`setitimer()`可以一直重複
* SIGBUS – terminate w/core
    Implementation-defined HW fault
* SIG**CHLD** – ignore
    * sent to the parent whenever a **child** process **terminates or stops**
* SIGCONT – continue/ignore
    * Continue a stopped process
* **SIGFPE** – terminate w/core
    * Divid-by-0, floating point overflow, etc.
    * FPE -> Floating Point Error 
* **SIGHUP** – terminate
    * **Disconnection** is detected by the terminal interface (no daemons) -> controlling process of a terminal
    * Triggering of the **rereading of the configuration files**(daemons)（比較常見）
    * 可以寄給server，然後server就會去找configuration檔（組態檔），例如換port
* SIGILL – terminate w/core
    * Illegal hardware instruction
* **SIGINT** – terminate
    * DELETE key or `CTRL-C`
* **SIGIO** – terminate/ignore
    * Indicate an **asynchronous I/O** event
    * (SIGIO=SIGPOLL, Terminate on SVR4)
* **SIGKILL** – terminate
    * Could not be ignored or caught!
* **SIGPIPE** – terminate
    * reader of the **pipe/socket terminated**
* SIGPROF – terminate
    * A profiling timer expires (setitimer)
* SIGPWR – ignore (SVR4)
    * System dependent on SVR4
    * UPS -> init shutdowns the system
    UPS是確保在最後關機前剩餘的電力能夠將未儲存的東西dump到disk去
* SIGQUIT – terminate w/core
    * CTRL-\ triggers the terminal driver to send the signal to all foreground processes.
* SIGSEGV – terminate w/core
    * Invalid memory access
* SIGSTOP – stop process (like SIGTSTP)
    * Can not be caught or ignored
* SIGSYS – terminate w/core
    * Invalid system call
* SIGTERM – terminate
    * Termination signal sent by kill command
* SIGTSTP – stop process
    * Terminal stop signal (CTRL-Z) to all foreground processes
* SIGURG – ignore
    * Urgent condition (e.g., receiving of out-of-band data on a network connection)
* SIGUSR1 – terminate
    * User-defined
* SIGUSR2 – terminate
    * User-defined
* SIGVTALRM – terminate
    * A virtual timer expires (setitimer)
* SIGWINCH – ignore
    * Changing of a terminal window size
* SIGXCPU – terminate w/core
    * Exceed the soft CPU time limit
* SIGXFSZ – terminate w/core
    * Exceed the soft file size!

### Remark
Terminate w/core – not POSIX.1
* No core file:
    * non-owner setuid process
    借用別人的權限在core dump會沒辦法做
    * non-grp-owner setgid process
    * no access rights at the working dir
    * file is too big (RLIMIT_CORE)
* core.prog (4.3+BSD)

### Set Disposition of Signal to Handler
#### signal prototype
```
#include <signal.h>
void (*signal(int signo, void (*func)(int)))(int);
//signal function的參數：int signo, void (*func)(int)
//void (*func)(int)指導一個回傳值是void的函數input是int

```
* typedef void Sigfunc(int)
**Sigfunc \*signal(int, Sigfunc \*);**
* signo: signal number
```
#define SIG_ERR (void (*)())-1
#define SIG_DFL (void (*)())0    //DFL -> default
#define SIG_IGN (void (*)())1
```
* func: SIG_IGN, SIG_DFL, 
the **address** of the **signal handler / signal-catching** function
SIGKILL & SIGSTOP cannot be ignored and caught
Return: the **address of the previous handler.**

#### Example Program: catch SIGUSR
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9a0859c614b618e1ea27aaf96ba1b43a.png)

* pause() forces a **process to pause/sleep until a signal is caught**.
 The signal cannot be set to be ignored.
* for(;;)是無限迴圈

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5a1c3b77e3382dc3ef357e5ab35ec6d4.png)
* `./a.out  &`的`&`讓process在background執行

### Handling Signals
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_26081470f023bb3c36d64c301317e4a8.png)

### signal Remarks
 Not able to determine the current disposition of a signal without changing it.
* Possible solution:
e.g.: if (^C is not ignored now) then set it to a handler
如果SIGINT沒有被ignore就把它設成ignore
```
int sig_int();  //sig_int()什麼事也沒做所以就是ignore
if (signal(SIGINT, SIG_IGN) != SIG_IGN)
signal(SIGINT, sig_int);
```
* The process **catches only the signal** if the signal is **not currently being ignored.**
    * **pause() will not return for SIGCHLD**


### Program Start-Up
當child process call `exec`:
All signals are set to their default actions **unless the process that calls exec is ignoring the signal**.除非它是ignore，不然就會設成default
* The exec functions change the disposition of any signals that are being caught to their default action. (Why?)

How about fork()?
* **fork() lets the child inherit the dispositions of the parent!**
child會繼承parent的signal mask，用thread的角度更準確的說，是child process只會有一個thread，它會繼承process裡當初呼叫fork的那個thread的signal mask

The shells automatically set the disposition of the **interrupt** and **quit** signals of **background processes** to **“ignored”**. (Why?)
* 在背景執行的process 會ignore `SIGINT`

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_872e21f5677be9552218dd1fe35a3c94.png)

### Interrupted System Calls
* Conventional Approach
    * Slow system calls can block forever
    * **“Slow” system calls could be interrupted
        -> errno = EINTR**
* “Slow” System Calls (not disk I/O):
    * Reads from or writes to files that can block the caller forever (e.g., pipes, terminal devices, and network devices)
* Opens of files (e.g., terminal device) that block
    * until some conditions occurs.
* pause, wait, certain ioctl operations
* Some IPC functions
#### A typical code sequence
```
again:
    if ((n = read(fd, buff, BUFFSIZE)) < 0) {
        if (errno == EINTR)
            goto again; //其實還沒結束
    }    
```
* Restarting of interrupted system calls – since 4.2BSD
    * ioctl, read, readv, write, writev, wait, and waitpid.
    * 4.3BSD allows a process to disable the restarting on a per-signal basis.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d14f366c8fde6729a6a55b456cf31970.png)

### Reentrant Functions
若一個程序或子程序可以「在任意時刻被中斷然後作業系統調度執行另外一段代碼，這段代碼又調用了該子程序不會出錯」，則稱其為可重入（reentrant或re-entrant）的。即當該子程序正在運行時，執行執行緒可以再次進入並執行它，仍然獲得符合設計時預期的結果
* When interrupts occur, a function could be called twice and causes problems. while reentrant funcs don't cause error.
* Potential Problem
    * In the signal handler, we **can’t tell where the process was** executing when the signal was caught!
* A function is described as reentrant if it can be **safely called recursively**

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ffd00312c4908bb32bca14dbc03de56d.png)

#### Example of Non-Reentrant Function
```
/* non-reentrant function */
char *strtoupper(char *string) {
    static char buffer[MAX_STRING_SIZE];
    int index;
    for (index = 0; string[index]; index++)
        buffer[index] = toupper(string[index]);
    buffer[index] = 0 ;
    return buffer;
}
```

因為static，buffer會被放在global

```
/* non-reentrant function */
char *strtoupper(char *string) {
    char *buffer;
    int index;
    /* error-checking should be performed! */
    buffer = malloc(MAX_STRING_SIZE);
    for (index = 0; string[index]; index++)
        buffer[index] = toupper(string[index]);
    buffer[index] = 0 ;
    return buffer;
}
```
因為malloc

#### Better Solution: work only on the data provided to it by the caller
```
/* reentrant function (a better solution) */
char *strtoupper_r(char *in_str, char *out_str) {
    int index;
    for (index = 0; in_str[index]; index++)
        out_str[index] = toupper(in_str[index]);
    out_str[index] = 0 ;
    return out_str;
} 
```

### Reentrant Functions
Non-Reentrant Functions
* Those which use **static** data structures
* Those which return a **pointer to static data**
* Those which call **malloc() or free()**
* Those which are part of the standard I/O library – usage of **global** data structures – such as **printf().**
    * Calling printf() in your signal handlers may lead to unexpected results.
    * 但通常為了debug我們還是會用printf
* Those which are POSIX.1 system database functions ：
例如`getgrgid(), getgrnam(),getpwuid(),getpwnam`
* Those which call non-reentrant functions

Restoring of errno inside a handler
* 通常剛進handler的時候會把errno另外存起來，退出前再改回來

Updating of a data structure – longjmp()

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c2eb9fad71f75a9a8fc669576fc725ac.png)

#### Call a non-reentrant function from a signal handler
`getpwnam`是non-reentrant function,用來得到帳密資訊
以下是作者想展示會出問題的狀況

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e838f107ce6efbc64ed8f7a34cc39954.png)

### Unreliable Signals
Unreliable Signals: “Signals could get lost!”
Why?
(1) The action for a signal was reset to its default
each time the signal occurred.
```
int sig_int();
…
signal(SIGINT, sig_int);
…
sig_int() {
    /* might terminate here 會有race condition*/
    signal(SIGINT, sig_int);
    …
}
```
(2) The process could only ignore signals, instead of turning off the signals when the process is busy


```
int sig_int_flag;
main() {
    …
    /* if signal is delivered here, then signal will be ignored */
    signal(SIGINT, sig_int);
    …
    while (sig_int_flag == 0)
        pause(); //A process could sleep forever!
}
sig_int() {
    signal(SIGINT, sig_int);
    sig_int_flag = 1;
}
```
### Reliable Signals
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8cff7b664bdb1fc3893caa5da3ea34cf.png)


* A signal is generated (or sent to a process) when
    * the event that causes the signal occurs!
    * A flag is set in the process table.
    * 把ＰＣＢ上紀錄signal的bit on起來
* A signal is delivered when
    * the action for the signal is taken.
(**once blocked, it will be not delivered**)
* A signal is pending during
    * the time between its delivery and generation
* A signal is blocked until
    * the process unblocks the signal, or
    * the **corresponding action becomes “ignore”**
(if the action is either default or a handler).
* The system determines which signals are blocked and pending!
    * `sigpending()`
    returns the set of signals that are pending for delivery to the calling thread (i.e., the signals which have been raised while blocked).  **The mask of pending signals is returned in set**.
* A signal mask for each process defines the set of signals currently blocked from delivery
    * `sigprocmask()`決定哪些signal被block
    *  on => block 被on就是被block
* **Signals are queued** when
    * **A blocked signal** is generated **more than once**.
    * POSIX.1 (but not over many Unix) allows a system to deliver the signal either once or more than once.
* Delivery order of signals
    * No order under POSIX.1, but its Rationale states that signals related to the current process state,
e.g., **SIGSEGV** should be **delivered first**.(Invalid memory access)
    * 通常會先deliver最嚴重的
    
### Func: kill and raise
```
#include <sys/types.h>
#include <signal.h>
int kill(pid_t pid, int signo);
int raise(int signo);
```
kill功能：send signal to a process
raise功能：send signal to itself
kill的參數：
* pid > 0 -> to the process
* pid == 0 -> to “all” processes with the **same gid of the sender** (excluding proc 0, 1, 2)
* pid < 0 -> to “all” processes with gid == |pid|
* pid == -1 -> broadcast signals under SVR4 and 4.3+BSD

我們也可以打在terminal:
`kill -USR1 531`指的是對pid=531的process寄signal

#### Right permissions must be applied!
要有權限才能用 kill & raise
* Superuser is mighty!
* **Real or effective uid** of the **sender** == that of the **receiver**
* _POSIX_SAVED_IDS -> receiver’s saved set-uid is checked up, instead of effective uid
#### signo ==0 ~ a null signal
* **Normal error checking** is performed by kill() to see **if a specific process exists**.
* kill() returns –1, and errno == ESRCH
#### Signal (not blocked) generated for the calling process
* signo or some other **pending, unblocked** signal is delivered to the process **before kill() returns**
> 如果kill是呼叫給自己，kill system call return前會至少deliver一個，再殺掉process
* The implementation of `abort()` will explain it

### Func: alarm & pause
```
#include <unistd.h>
unsigned int alarm(unsigned int secs);
```
* SIGALRM is generated when the timer expires
* There **could be a delay** because of processor scheduling delays.
* **A previously registered alarm is replaced by the new value** – the left seconds is returned!
* **alarm(0) resets the alarm.**
* Default: termination
```
#include <unistd.h>
int pause(void);
```
* pause() suspends the calling process until a signal is caught
* Return if a signal handler is executed and returns.
    * Returns –1 with errno = **EINTR**
     會return 表示有error，成功的話應該block在那

### Sleep1(): Simple, incomplete implementation of sleep
sleep() makes the calling process sleep until seconds have elapsed or **a signal arrives which is not ignored**.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_00e57abd089fa981acafd2e111e95e93.png)

* Potential problems:
1. Any previous alarm?
呼叫的process可能在呼叫sleep()之前就已經設了別的鬧鐘。
3. The lost of the previous SIGALRM handler
pause也可能接到不是SIGALRM的鬧鐘
5. A race condition (between alarm() & pause())
有可能在pause前就context switch

#### Any previous alarm?
設一個新鬧鐘，如果舊的會比較早響就只響舊的，新的會比較早響，就讓新的早響但要把舊的設回來因為我們不能隨意取消別人的alarm
```
if ( (oldalarm = alarm(nsecs)) > 0)
    if (oldalarm < nsecs) {
        alarm( oldalarm );
        pause();
        return(alarm(0));}
    else {
        pause();
        return( alarm( oldalarm – nsecs) );
}
```
#### Previous SIGALRM handler?
```
if ( (oldhandler = signal(SIGALRM, sig_alrm)) == SIG_ERR )
    return (nsecs);
alarm( nsecs);
pause();
signal(SIGALRM, oldhandler);
return( alarm(0) );
```

### Nonlocal Jumps (Ch7.10)
* Powerful (but dangerous) user-level mechanism for transferring control to an arbitrary location
* Objective:
Goto to escape from a deeply nested function call!
break the procedure call/return discipline
Useful for error recovery and signal handling (Ch. 10)

### Func: setjmp, longjmp
```
#include <setjmp.h>
int setjmp(jmp_buf env);
```
* Return 0 if called directly; otherwise, it could **return a value val from longjmp()**.
* env tends to be a **global variable**.
* `setjmp`可以用很多次，下面的會覆蓋上面的

### Potential Problems of Nonlocal Jumps
* Works within stack discipline
    * Can only long jump to environment of function that has been called but not yet completed
    
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fe9bf8e81b4b88cbab0cbd1f7b4173ba.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9976b7b813fe67eed24f7d096fc5c3b1.png)



`int longjmp(jmp_buf env, int val);`
* longjmp() unwinds the stack and affect some variables.
* Parameter: jmp_buf
Definition is machine-dependent.
Includes **CPU registers, stack pointers and return address (Program Counter).**

#### Example of setjmp() and longjmp()
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_944d78ebb9c7ff1f2bc08723d9102f3a.png)


### Sleep2(): Another (imperfect) implementation of sleep
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_53347528cd86d6e5db1d541db1b7633c.png)
* When a future SIGALRM occurs, the control goes to the right point in sleep2() à No race condition!
* 雖然setjmp, lomgjmp不是reentrant function但在這邊不會出問題

但Sleep2還是會導致其他地方出錯
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_35f9e403f9d3da40c2fc1f6947788a1a.png)

----
### alarm & puase
#### Timeout a read() (on a “slow” device)!
* A race condition (between alarm() & read())
* Automatic restarting of read()?
    * No portable way to specifically interrupt a slow system call under POSIX.1.
#### Timeout & restart a read by longjmp()!
* Problems with other signal handlers!
有race condition，有可能在alarm(10)和read之前context switch，然後就沒有alarm了


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d78bdacacaa9544767f102728e6af4d0.png)

* 這個版本把`signal`改成`sigaction`就對了

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_99879ee38e04039b18b660dc9c3d8a8d.png)

### Signal Mask
* Signal mask is a per process property
    * 每個process都有一個signal mask
    * Empty in the beginning
* Under certain circumstance, we may **desire the process not to be interrupted.**
    * E.g., in the process of changing handlers or in the process of handling a delivered signal
* It defines the set of signals for being blocked from delivery to the process
    * Blocked signal vs. Ignored signal
        * An ignored signal will not be delivered to the receiving process.
        * A **blocked signal** will be queued until the receiving process is ready to process it or **the signal is ignored**

### Signal Sets
Why sigset_t ?
* To present a number of signals
* The number of different signals could exceed the number of bits in an integer!
```
#include <signal.h>
int sigemptyset(sigset_t *set);
int sigfillset(sigset_t *set); //會是每一個signal bit 都有on的
int sigaddset(sigset_t *set, int sig_no);
int sigdelset(sigset_t *set, int sig_no);
int sigismember(const sigset_t *set, int sig_no);
```
### sigprocmask
```
#include <signal.h>
int sigprocmask(int how, const sigset_t *set, sigset_t *oldset);
```
* If oldset is not null, return current signal mask by it
為了output用、或未來要把現在被取代掉的signal設回來
* If set is not null, check how (SIG_BLOCK, SIG_UNBLOCK, SIG_SETMASK);
otherwise, ignore how
e.g. 如果要把一些signal block，就是設how為SIG_BLOCK，然後把set裡要被block的set bit on 起來
* If any **unblocked** signals are **pending**, **at least one of unblocking signals will be delivered** before the sigprocmask() returns.重要！跟kill signal給自己一樣

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_27860d07ab21327c4124f17bec6117c2.png)


#### Example of showing names of signals currently blocked
* 用`sigismember`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2386b72a0976f8026f5b079f52797ae6.png)

### sigpending
```
#include <signal.h>
int sigpending(sigset_t *set);
```
* Returns the set of **pending, blocked** signals
* 被blocked才會長時間pending
#### Example (next slide)

```
signalprocmask(SIG_BLOCK, &newmask, &oldmask);
```
=> SIGQUIT is blocked, current signal mask is saved in `oldmask`


the process sleeps for 5 seconds, and then during these 5 secs we press "slash back" key, so SIGQUIT is unblocked.

```
sigprocmask(SIG_SETMASK, &oldmask, NULL)
```
=> SIGQUIT is delivered until the signal is unblocked and before `sigprocmask(SIG_SETMASK, &oldmask, NULL)` returns.
=> 把mask的狀態回復到還沒做這些操作之前

#### Question看不懂我自己在寫什麼
Can we use “SET_UNBLOCK” when trying to unblock SIGQUIT?
No queuing of signals.
Ans: 不行

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f937b8d509f32e6ffdad021f4195f8ed.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d10db77bea20915d2f7246234a16a74b.png)

它不會幫你數按幾次，只會確認這個signal的bit有沒有on

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7fa2542ca92c2a5298a05d446cbf2340.png)

### Signal Masks (fork() & exec())
#### Properties (of parent) inherited by child
* fork(): signal mask, dispositions
* exec(): signal mask
    pending signals, time left until alarm clock
#### Properties (of parent) changed from child
* fork()
    pending signals are set to empty for child
    pending alarms are cleared for child
    因為小孩的pid換了
* exec()
    **disposition** of caught signals is **set to default action for child**
    原本ignore的還是ignore
    
### sigaction
註冊一次，終生有效。
* A better implementation of signal()
* Allows us to examine or modify the signal handler
* Signal mask:
    * Additional signals can be masked before the handler function is called.
    * **The caught signal is blocked** before the handler returns to avoid signal lost.
* Installed action remains installed until another sigaction() is called. 

```
#include <signal.h>
int sigaction(int signo, const struct sigaction *act, struct sigaction *oact);

struct sigaction {
    void (*sa_handler)(int);
    sigset_t sa_mask;
    int sa_flags;
    /* alternate handler 和上面的handler擇一*/
    void (*sa_sigaction)(int, siginfo_t *, void *);
};
```
* signo: signal number
* act: if not-null, modify the handler
* oact: if not-null, return previous handler
* **sa_mask**: additional signals needed to be **blocked** when the action is taken.
* sa_flags: next slide
會自動include自己現在這個signal
**sa_flags = 0** 代表沒有flag
* Unlike signal(), **signal handlers remain!**
* 使用範例：
```
act.sa_handler = sighandler;
sigaction(SIGTSTP, &act, NULL);
```

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c4a05ebd3b0661c6e04a1234e5c74a94.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c64072edc7d76a36c06d2562fe347ee4.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b3f792c2330d1fa8e2eea8d2e79b2062.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7f2e706c358b163cb1e821f7ed28cad5.png)

### Changes of signal mask for sigaction
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_93d62f045f15e28d373e454c76684155.png)
* signal deliever時，handler會自己把他暫時變成block，然後因為`act.sa_mask=set2`，在SIGINT deliver的時候，進handler時set2會被block

### A reliable implementation of signal using sigaction
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4ccf5f10f68b8a12a8b5baf969aa32d0.png)
重要：**return oact.sa_handler**

#### Prevent any interrupted system calls from being restarted
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_50c13a94312de6b1db7bb96dde252b36.png)

### sigsetjmp & siglongjmp
```
#include <setjmp.h>
int sigsetjmp(sigjmp_buf env, int savemask);
void siglongjmp(sigjmp_buf env, int val);
```
* sigsetjmp() saves the current signal mask of the process in env if savemask !=0.
如果希望longjmp回來的時候signal mask跟當初一樣，要把savemask設成不是0
* setjmp & longjmp save/restore the signal mask:
    * 4.3+BSD and Mac OS X, but not SVR4, Linux 2.4, Solaris 9
    一般的setjmp & longjmp跳回去時會不會變回原本的signal mask則因系統不同而異
    
#### Example of signal masks, sigsetjmp, & siglongjmp
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ab5e83a167e42830fe24fbf41b1a42d7.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3568dc9d228264c296605682c7815b34.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_081132c61f12d875da45901dc4b9a795.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_62a95a6e1990f7b2557bcdf254dac840.png)
* 從handler return 後signal在signal mask上就不會是on的狀態
* sig_usr1的最後是sigsetjmp因此沒有return
* 因為sigsetjmp會使mask回復，所以最後ending main:是empty set

### sigsuspend
sigprocmask(SIG_BLOCK)和pause的結合
* Recall that, race condition between alarm() and pause() may block a process forever if there is no other signal.
* Similar race condition may occur between sigprocmask() and pause(), leading to missed signals. 
* 下面例子發生的事是：
把SIG_INT block住，我們期待的是pause被SIGALRM叫醒，如果ALRM在pause之前已經delivered，表示pause會被forever block

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a0318bcce13758378be4ed85a06443e8.png)
```
#include <signal.h>
int sigsuspend(const sigset_t *mask);
```
功能：
* sigsuspend() **temporarily replaces the signal mask of the calling thread with the mask given by `mask`** and then **suspends the thread until** delivery of a signal whose action is to **invoke a signal handler** or to **terminate a process.**
* `mask`裡面有on的signal會被block
* Reset the signal mask and put the process to sleep **in a single atomic operation**
* If a signal is caught **and if the signal handler returns**, then `sigsuspend()` returns
* Return –1. errno = EINTR if the signal handler returns
* The mask is restored when the function returns會回復成原本的mask
#### Example
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fca8fa02d225c1e2faea843d5149395a.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d9a4b1f70e8f13f6e0c1c62e22b28967.png)


### A correct way to protect a critical region from a signal 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ec3028df5fcb33a66c9f75bed1f2c7bc.png)
* `
in sig_int: SIGINT SIGUSR1
`有SIGINT是因為handler會自己把呼叫它的signal block住、有SIG_USR1是因為`sigsuspend`
* `after return from sigsuspend`只有SIGINT是因為他會回復到呼叫`sigsuspend`之前的mask
### Avoid Race Condition (Chap 8)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_176cfcb3e30ba2567d644087957e4bab.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4d3180da89db59330f72756c2937b161.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3e27e054ad02732e888a901f64a99625.png)

### Routines to allow a parent and child to synchronize using signals重要！
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d0c5bc54e24a9154b61c05518d4a7ecb.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9dee7bd7a362305b7f3d441e86933497.png)

### Func: sleep
```
#include <unistd.h>
unsigned int sleep(unsigned int secs);
```
Suspend until 
1. the specified time elapsed, or 
2. **a signal is caught and the handler returns** and sleep function **returns the unslept seconds**

* Problems:
alarm(10), 3 secs, sleep(5)?
    * Another SIGALRM in 2 seconds? Both SVR4 & 4.3BSD – not POSIX.1 requirements
    * Under SVR4, **alarm(6), 3 secs, sleep(5) -> sleep()** returns in 3 secs
* **alarm() & sleep() both use SIGALRM**
* sleep會被任何不是ignore的signal叫醒

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_56211e71761abaebd97b68bd7f676e8d.png)
* `unslept = alarm(0)` => 如果設置新的alarm時上一個SIGALRM還沒被deliver，則新的alarm會回傳上一個SIGALRM剩餘的秒數

### 考古題（要記得回來看）
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bd8633e9fd9ddcdc30bd29e6a4d845ed.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_98c8cd6bcff1a346e7f3f8874320c2fc.png)

### Func: abort
```
#include <stdlib.h>
void abort(void)
```
* Sends SIGABRT to the process => `raise(SIGABRT)`
* ANSI C requires that if the signal is caught, and the signal handler returns, then abort still doesn’t return to its caller.
* The SIGABRT **won’t return if its handler calls `exit, _exit, longjmp, siglongjmp.`**
* 一般來說當SIGABRT delivered，會進入handler然後死掉，但一種情況例外：longjmp
#### ANSI C
* The Implementation determines whether output streams are flushed and whether temporary files are deleted.
#### POSIX.1
* POSIX.1 specifies that abort **overrides** the blocking or ignoring of the signal by the process.
就算有把SIGABRT block，還是得delivered
* If abort() terminates a process, all open standard I/O streams are closed (by fclose()); otherwise, nothing happens

#### POSIX.1 implementation of abort()
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a751d28127b2df2fabb39fe0ed16383f.png)
* `sigaction(SIGABRT,NULL,&action)`把新action設NULL是設成default的意思
* `kill`必須等至少一個unblocked signal delivered才會死掉，而因為除了SIGABRT的其他signal都被block了，所以我們可以確定SIGABRT一定會被delivered然後進handler之後死掉
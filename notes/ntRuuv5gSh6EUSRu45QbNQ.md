# System Programming - Slide9
# chapter11.12
### The Process Model
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_36164893cd27550ddca3277398cdcf4f.png)

#### Process Concept
* Resource grouping
    * Address space, open files, child processes, pending alarms, signal handlers, accounting information, etc.
* (A single thread of) execution
    * The entity scheduled for execution on CPU

### Typical Memory Arrangement(Ch7.6)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_884ea58eff5a17482c0aca4ed2aff742.png)

**Stack & Heap 差別**
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_66142c1e1c561ccb167d4046a144ef34.png)
* value type 的變數, 包括指標變數會放在 stack
* reference type 的變數 (如 string, object) 本身也會放 stack, 然而他的值 (value) 則是放 heap
* box 就是 value types to reference types 的過程, 所以 value 會被放到 heap 中, 而產生一個 object 變數來指向這個 value, 變數指標則是在 stack
* unbox 是  reference types to value types 的過程,  所以原本 object 所指向的值 (heap 中) 會被複製到 stack 中並賦予明確 value type 型別

### The Thread Model
* Thread Concept
    * A lightweight process
    * Resource sharing

### Process vs. Thread
#### Process
* Multi-processes
* (Probably) owned by different users (fight)
* Processes do not share resource very well (security)
* Creation of a new process using fork() is **expensive in terms of time and memory** and forms a process hierarchy.
* Process **context switch cost is very high**
#### Thread (lightweight process)
* Multi-threads
* Owned by a single user (cooperate)
* All threads **share most of the resources** (no protection)
* Often all threads being **equal** (沒有所謂parent)
* The cost of thread creation and switch is low

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b939a51fe6f6ad5dc8ee57c74032066b.png)

### Thread Benefits
* Deal with asynchronous events by assigning a separate thread to handle each event type
* Automatically share the same memory address space and file descriptors
* Problems can be partitioned and overall program throughput can be improved
* Interactive programs can realize improved **response time** by using multiple threads

### Thread Drawbacks
* Writing multithreaded programs require **more careful** thought (no protection)
* More **difficult to debug** than single threaded programs
* For **single processor** machines, creating several threads in a program may not necessarily produce an increase in performance

### Implementing Threads in User Space
*  **Kernel knows nothing about multi-threads**
(portability)
* **Run-time system**: a collection of procedures that **manage threads**
* Thread table: manage each thread's program
**counter, stack pointer, registers, state**, etc.
所以每個thread有自己的counter, stack pointer, registers, state
* Problems
    * How blocking system calls are implemented
        * Nonblocking, I/O multiplexing
        * 網路資料：**Blocking calls in one thread should not affect other threads.** If the blocked thread locks a mutex prior to entering the blocked call and the second thread attempts to lock the same mutex, then they the second thread would need to wait for the blocking call to finish and for the first thread to release the lock.
    *  No other thread can run **unless running thread voluntarily gives up CPU** (non-preemptive)
        *  Run-time system request a clock signal to get control

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c66a314ddb0b3bf6befbcca58db22964.png)

### Implementing Threads in Kernel
* Kernel knows about and manages threads
* Calls that **block a thread can be system calls**
    * Kernel threads **do not require any new, nonblocking system calls.**
* Kernel can run a thread from the same or different process
* Problems
    * The **cost of a system call is substantial**
    * Relatively greater cost of creating and destroying threads
        * Recycle(如果一個thread死掉，它的resource會留給下一個thread)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e8c5f4f47c519086f167c73fcdaa9f7d.png)

### Hybrid Implementation
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dddb177d40576f790f3d26c5356850c6.png)

### Thread Supports
* The traditional UNIX process model supports only one thread of control per process
* Thread library on different platforms:
    * POSIX Threads, or Pthreads, is a POSIX standard for threads (IEEE 1003.1c-1995)
    * Win32 Threads on Windows
    * SProc (Shared Group Process) on SGI, not compatible with POSIX
* With **Pthreads**, when a program runs, it starts out as a single process with a single thread of control, i.e., **main thread**.

### POSIX threads share …
Text, global data & heap segments, open file
descriptors, environment variables, process ID,
parent process ID, process group ID and
session ID, controlling terminal, user and group
IDs, record locks, signal dispositions, file mode
creation mask, working directory, root directory,
resource limits, measurements of the
consumption of CPU time and resources
### POSIX threads have their own …
Thread ID, **stack**, registers, **signal mask**,
**errno value**, scheduling properties, **thread specific data**

### Thread Creation
protoptype:
```
int pthread_create( pthread_t *tidp, pthread_attr_t *attr, 
void *(*start_rtn)(void *),void *arg )
```
* tidp: **pointer for thread** id/handle
* attr: customized thread attribute (NULL: default)
(要先呼叫`pthread_attr_init`)
* start_rtn(start routine): **starting function** for the created thread
* arg: **argument for the starting function pointer** to a structure
* Create a new thread, specify a procedure for it to run
* When a thread is created, **there is no guarantee which** (newly created vs. calling threads) **runs first** (like fork())
* No parent-child relationship. Main vs. spawned threads.
* 成功執行時回傳0

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_540bd754772235c67df8314032625141.png)

### Thread ID
```
pthread_t pthread_self ( void )
```
* Get thread ID
* A thread ID is represented by the pthread_t data type
* On most systems thread ID is just an integer (but it does not have to be) (有可能是拿位址當ID)
```
int pthread_equal ( pthread_t tid1, pthread_t tid2 )
```
* Compare two thread IDs
* **Nonzero if equal**

### Thread Attributes
```
int pthread_attr_init(pthread_attr_t *attr)
int pthread_attr_destroy(pthread_attr_t *attr)
```
* Calling `pthread_attr_init` to **set up the default** values
* `pthread_attr_destroy` **frees memory** allocated by
`pthread_attr_init` & sets `pthread_attr_t` to be **invalid values**

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4573cddfd68a020c900a2106f9a485f0.png)

### Changing Attributes
```
int pthread_attr_getdetachstate (pthread_attr_t *attr, int *detachstate)
int pthread_attr_setdetachstate (pthread_attr_t *attr, int detachstate)
```
* get and set the current detachstate attribute
* detachstate: detached vs. joinable thread
    * PTHREAD_CREATE_**DETACHED**
        * **don't need the thread's termination status** (a thread's storage can be reclaimed immediately on termination)
    * PTHREAD_CREATE_**JOINABLE (default)** 

### Detaching a thread
```
int pthread_detach(pthread_t tid)
```
某個threaad已經生成了，但我想改成detached
Indicate that system resources for thread tid **should
be reclaimed when it ends**
– If the thread is ended, resources are reclaimed immediately
– This routine does not cause the calling thread to end
detach itself: `pthread_detach( pthread_self() )`
* Threads are detached
– **after a `pthread_detach()` call**
– PTHREAD_CREATE_DETACHED is set on creation
– after a pthread_join() call

#### Print Thread IDs
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1bd883425c11426205db28a768d4a828.png)
* 有可能`pthread_create`先執行`thr_fn`但`ntid`還沒有建立好，然後直接`printids`就會出錯

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_409fd9a7e71471ec13c5b36dc2a3ef30.png)

#### Example of changing thread attributes
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1292e03a975ca49ab4913a9bb8b7c018.png)

### Passing Arguments to Threads
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e508b149cb98e053b9ce8bd7374384e2.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_de69741de315a4985fe41991fa59ef94.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bd382344578bc8e4c534f1c8c94bd6a0.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3919f0eea651bc87fda9083a39a20334.png)
有可能等他printf的時候no已經＋＋了

### Thread Termination
* Thread is a part of a process
* Terminating a process will terminate all threads
    * Any thread within a process **calls exit, _Exit, or _exit**
    * A **signal** whose **default action** is **termination** is received
    * **Return** from main() in the **main thread**
* A single thread **exits without terminating** the entire process
    * Return from the **start routine** (except the main thread)
(the **return value** is the **thread's exit code**)
    * Call `pthread_exit()`
    * Canceled by another thread in the same process
    

```
void pthread_exit (void *rval_ptr)
```
terminate calling thread
* Doesn’t close any files
* Guarantee that all threads get a chance to execute
(1) **main()** explicitly calls pthread_exit() to **block** until the threads it created are done
(2) Alternative is to call pthread_join() in main() to join (or wait for) all of the threads it created (也會等待小孩死掉)
類似process的`wait(&stat)`;
(3) 如果main創造A，A創造B，main不會等B
```
int pthread_join(pthread_t tid, void **rval_ptr)
```
block on non-detached thread tid
只有 joinable的thread能call pthread_join
通常一個joinable的thread只能被join一次
成功時回傳0
* retval:會接到start routine裡`pthread_exit`回傳的exit code
If retval is not NULL, then pthread_join() copies the exit status
       of the target thread (i.e., the value that the target thread
       supplied to pthread_exit(3)) into the location pointed to by
       retval.  If the target thread was canceled, then **PTHREAD_CANCELED**
       **is placed in the location pointed to by retval**.
    * The **calling thread blocks**(呼叫`pthread_join`的thread) until the specified thread calls `pthread_exit`, returns from its start routine, or is canceled(PTHREAD_CANCELED)
* **The calling thread automatically places the specified thread in the detached state**. If the specified thread is in the detached state, it returns EINVAL.
* NULL: not retrieve the thread's termination status
* What if pthread_join() isn’t called for non-detached thread?
這是指 **joinable 的 thread 死了沒人去 join ,就會變成 zombie thread**:
deallocates the resources used by the thread but keeps an entry in the thread/process table.
> reminder:
> zombie process:小孩死了它的資源留在那等parent接，但parent沒接就死了，所以小孩的process其實還沒死光，就變zombie process
* What if two threads simultaneously try to join with one thread?
undefined，每個thread只能被join一次
* What if the thread calling pthread_join() is canceled?
**If the thread calling pthread_join() is canceled, the target thread is not detached.**
* `pthread_timedjoin_np()`: timeout **(return ETIMEDOUT)**
* `pthread_tryjoin_np()`: **nonblocking** ( *_np: nonportable)
#### Example1
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_333c19c1d97e825a3d6d357fb387ca0d.png)
#### Example2
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4aa46cf533f2f278ab9c0a1ab2541a77.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a69f5778577093ab265ae7f870c245e5.png)

### Cancelling Threads
```
int pthread_cancel(pthread_t tid)
```
* Cause thread tid to behave as if it had called `pthread_exit` with an argument of PTHREAD_CANCELED
* Thread tid **can elect to ignore or control how it is canceled**
* 成功時回傳0
```
int pthread_setcancelstate(int state, int *oldstate)
```
Cancelability state:
* PTHREAD_CANCEL_ENABLE (default)
* PTHREAD_CANCEL_DISABLE
* For PTHREAD_CANCEL_ENABLE
    * Doesn't wait for thread tid to terminate
    * Only makes the request. Thread tid will continue to **execute until it reaches a cancellation point**.
* For PTHREAD_CANCEL_DISABLE,
    * Will not kill thread tid
    * Remains **pending**
    * Acts at the next cancellation point when enabled
```
int pthread_setcanceltype(int type, int *oldtype)
```
Cancelability type: (state==PHTREAD_CANCEL_ENABLE)
PTHREAD CANCEL DEFERRED (default:一定要跑到cancaellation point) or
PTHREAD CANCEL ASYNCHRONOUS（立刻cancel）
```
void pthread_testcancel(void)
//是一種cancellation point
```
Request delivery of any pending cancellation request
**Cancelability** should be **enabled**

#### If a thread is asked to be cancelled and has:
– PTHREAD_CANCEL_DISABLE
* The thread is **not cancelled**
* The request remains **pending**

– PTHREAD_CANCEL_ENABLE
1) PTHREAD_ASYNCHRONOUS
        The thread is cancelled immediately
2) PTHREAD_DEFFERRED
    *  The cancellation is deferred until:
          *  thread reaches a cancellation point or
          *  thread executes `pthread_testcancel()`
    * To know when the thread has actually terminated, call pthread_join() after cancelling it

#### Cancellation point
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_200a56e97d466a2d26303f1b979060f5.png)

### Why Cancellation Points
* Asynchronously cancelling threads might be unsafe
    * allocation or deallocation of shared resources
    * lock or unlock for shared resources
* Blocked system calls

### Thread Cleanup Handlers
```
void pthread_cleanup_push(void (*rtn)(void *), void *arg)
void pthread_cleanup_pop(int execute)
```
* `pthread_cleanup_push` pushes handlers to be called **in the reverse order** when the thread exits like `atexit()`
* the cleanup function rtn to be called with the argument arg when the thread performs one of the actions:
    * Make a call to `pthread_exit()`
    * Respond to a cancellation request
    * Make a call to `pthread_cleanup_pop()` with a nonzero argument
* pthread_cleanup_pop always pops a handler if any
    * **Optionally invoke the handler (if `execute` is non-zero)**.
    如果`pthread_cleanup_pop(1)`就會進入當初push的handler
    如果`pthread_cleanup_pop(0)`則不會
* Restriction: the two functions/macros must be used in matched pair

> 就算你用不到pop也要寫pop，寫了幾個push就要幾個pop
> 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2797c2b7d148ccfec97203153901001a.png)

### Comparison between Process andThread APIs
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2470f0b079136a115508cae957e2e5f0.png)

#### Thread Control
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e8453c490184785b51c795ed27819b4a.png)
不是cancel完就沒事，如果該thread是joinable要在創造這個thread的thread 做`pthread_join`

### Thread Synchronization
* Problem: When multiple threads share single address space, each thread can potentially see inconsistencies of shared memories
* `i++`在低階語言會變成三個指令`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_598c4e968a75284668195dfbd334ee40.png)
* 所以不該同時對同個shared的data做事->用mutex
### Mutexes
* Mutual-exclusion interfaces
* Semantically equivalent to a (**advisory**) lock
* State: lock, unlock
– Set (lock) mutex lock before accessing a shared resource
– Release (unlock) when we’re done
* A thread will **be blocked if it tries to lock a mutex
which has been locked**
如果A上了mutex之後A被block住，B此時也想上mutex，則B會被block住，直到A變nonblock之後unlock mutex
* If more than one thread is blocked when we unlock the mutex, then **all** threads blocked on the lock will be made **runnable**, and the first one to run will be able to set the lock
– Only one thread will proceed at a time
– The thread with the **highest priority gets the lock.** 

```
int pthread_mutex_init ( pthread_mutex_t *mutex, pthread_mutexattr_t *attr )
int pthread_mutex_destroy ( pthread_mutex_t* mutex )
```
* Statically allocated: PTHREAD_MUTEX_INITIALIZER
* Dynamically allocated: freed by pthread_mutex_destory()
* Mutex attributes:
    * *Process-shared* attribute and *type* attribute
    * NULL: set the default attributes
* Process-shared attribute
    * **PTHREAD_PROCESS_SHARED: allows independent processes to access the mutex**
        * check _POSIX_THREAD_PROCESS_SHARED or _SC_THREAD_PROCESS_SHARED (sysconf)
        * **PTHREAD_PROCESS_PRIVATE (default): Within a process, multiple threads can access the same mutex**
    * Related functions: `pthread_mutexattr_getpshared()`, `pthread_mutexattr_setpshared()`
* Type attribute
    * PTHREAD_MUTEX_NORMAL: no error checking or deadlock detection
        * (relock without unlock) :
A thread will deadlock itself if it tries to lock the same mutex twice
    * PTHREAD_MUTEX_ERRORCHECK
    * **PTHREAD_MUTEX_RECURSIVE:** **lock count allows one thread to lock the mutex multiple times not released until unlocked the same number of times**
    * PTHREAD_MUTEX_DEFAULT: one of the three
        * e.g. Linux: PTHREAD_MUTEX_NORMAL
    * Related functions: `pthread_mutexattr_gettype()`,
`pthread_mutexattr_settype()`

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a1366de81d1ba5882d02951ccc9f785f.png)

### Lock, Unlock and Try Lock
```
int pthread_mutex_lock(pthread_mutex_t *mutex)
int pthread_mutex_trylock(pthread_mutex_t*mutex)
int pthread_mutex_unlock(pthread_mutex_t*mutex)
```
* pthread_mutex_lock: If the mutex is already locked, the calling thread will block until the mutex is unlocked
* pthread_mutex_trylock: **non-blocking lock** (EBUSY)
* pthread_mutex_unlock: unlock the mutex. If a lock is not released, deadlock may occur.
* Remember: all threads to follow the same data-access rules when using mutexes (no protection)

### Thread Safety 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7c16119fc87ddf9e2285bc5d4ba38939.png)


### Example of Shared Memory (mmap)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_65405735d1943a7d7d3d24f5eb382fb9.png)
* bufptr是shared（mmap裡設定的），所以mlock也會被share(不然一般lock不會被child process繼承)
* 如果實際上沒有想mmap到某個檔案，可以設MAP_ANONYMOUS，把file descriptor設成-1，範例如下：
```
bufptr = (buftype*) mmap(NULL, sizeof(buftype), PROT_READ | PROT_WRITE, MAP_SHARED| MAPANONYMOUS, -1, 0);
```
* 用`MAP_SHARED`搭配`fd`就可以寫到檔案，但不是同步，要用`msync`才會真的同步到檔案
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2b03976bd3dafe75c7cf6c8ca8d6d963.png)


### Deadlock
解決辦法：把所有shared resource排order，例如想上三號的lock，要先上一號的lock、二號的lock、才能上三號的lock
缺點是thread平行度會降低
* Deadlocks can be avoided by carefully controlling the order in which mutexes are locked.
* You can also use `pthread_mutex_trylock()` to avoid deadlocking in this case.
* Locking granularity
    * Too coarse: little improvement possible from concurrency
    * Too fine: bad performance from excess locking overhead

以下兩個例子會造成deadlock、race condition
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d9d9cd52acaefdadc12a1786ea71b91f.png)
deadlock:有可能上完lock後被cancel（殺死）
race condition: 不知道死掉的時候a和b換完了沒
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d5bd35f0b4dbff1827f465404f6def98.png)
deadlock: cancel發生在`pthread_cleanup_push`之前的話還是會有deadlock

### ReaderWriter Locks
*  Higher degrees of parallelism (vs mutex )
    *  Allowing concurrent reads and exclusive write
* Semantically **equivalent to a RW lock**
* State: read-lock, write-lock, unlock
     * Set read/write lock before accessing a shared resource Release (unlock) when we’re done
* Lock compatibility
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b36a1d042f62475f9de5b14275449d05.png)
* Good if shared data are read more often than modified
* Write-starvation problem
Starvation: 低優先權的process長期或無限期,無法獲得系統的資源

### Rdlock, Wrlock and Unlock
```
int pthread_rwlock_init(pthread_rwlock_t *restrict rwlock,
const pthread_rwlockattr_t *restrict attr)
```
```
int pthread_rwlock_destroy(pthread_rwlock_t *rwlock)
```
Process-shared attribute (identical to mutex)
```
int pthread_rwlock_rdlock(pthread_rwlock_t *rwlock)
```
```
int pthread_rwlock_wrlock(pthread_rwlock_t *rwlock)
```
```
int pthread_rwlock_unlock(pthread_rwlock_t *rwlock)
```
```
int pthread_rwlock_tryrdlock(pthread_rwlock_t *rwlock)
int pthread_rwlock_trywrlock(pthread_rwlock_t *rwlock)
```
Implementations might place a limit on the number of times a
readerwriter lock can be locked in shared mode

### Thread Pool
* A master thread
    * assign thread IDs to new jobs on queue
    * 要用write-lock
* A pool of worker threads
    * remove jobs tagged with its thread ID from queue
    * 用read-lock就好
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ee732fa85cdbec7e210e6ee6020c48e2.png)

#### Using readerwriter locks to implement thread pool
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a10b158b34e6063b4505a0fbe925565d.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8c189b9fb6894acc269e7ab7490dfd11.png)

### Condition Variables
* Allow explicit event notification
    * Threads wait in a **race-free** way for arbitrary conditions
    * The condition is protected by a mutex
    * Threads must acquire the mutex lock to change or evaluate the condition state
* Two main operations: **wait & signal**
```
int pthread_cond_init(pthread_cond_t *restrict cond, pthread_condattr_t *restrict attr)
int pthread_cond_destroy( pthread_cond_t*cond)
```
* Statically allocated: PTHREAD_COND_INITIALIZER
* Dynamically allocated: freed by pthread_cond_destory()
* NULL attr: set the default attribute

### Condition Variable Attributes
```
int pthread_condattr_init (pthread_condattr_t *attr)
int pthread_condattr_destroy (pthread_condattr_t *attr )
```
* Process-shared attribute
    * PTHREAD_PROCESS_SHARED: allows independent processes to access the condition
        * check _POSIX_THREAD_PROCESS_SHARED or _SC_THREAD_PROCESS_SHARED (sysconf)
        * **PTHREAD_PROCESS_PRIVATE (default): Within a process, multiple threads can access the same condition**
    * Related functions:create cond之後再改attr
 `pthread_condattr_getpshared()`,`pthread_condattr_setpshared()`
 
### Waiting on Condition Variables
```
int pthread_cond_wait(pthread_cond_t *restrict cond, 
                    pthread_mutex_t *restrict mutex);
```
Wait for a condition to be true 
Called with a mutex lock held
#### Usage:每步都必做！
Acquire a mutex lock 得到mutex後才能檢查condition
Check the condition (iteratively) 如果condition現在是false就還要等
Call pthread_cond_wait() 這個函式做的事如下：
* **Sleep until signaled**
* **Release the mutex** just before sleep
* **Reacquire the lock when waken up** (return)
```
pthread_cond_timedwait()
```
return error if the condition isn’t satisfied within given
**absolute** time ( now + relative time; 通常要先用`gettimeofday()`得到現在時間)幾點幾分之類的

### Signaling on Conditional Variables
```
int pthread_cond_signal(pthread_cond_t *cond)
```
wake up **one** waiting thread on a condition
```
int pthread_cond_broadcast(pthread_cond_t * cond)
```
there might be a pool of threads waiting for a condition
wake up all waiting threads on the condition
* Signal waiting threads only after changing the state of the condition

### Example1
Waiting for x==y condition
```
pthread_mutex_lock(&m);
while (x != y)
    pthread_cond_wait(&v, &m);
// do something here if necessary
// 如果這裡都不會動到x就可以執行下一行把m先unlock
pthread_mutex_unlock(&m);
```
Notifying waiting thread that x is incremented
```
pthread_mutex_lock(&m);
x++;
pthread_mutex_unlock(&m);
//What happens if x is changed here?
pthread_cond_signal(&v)    //會回到pthread_cond_wait
```

### Example 2
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ca389fa4f0381c8c4f21b36e6eafcf26.png)

### Example 3: Sync. between 2 Threads
如果要讓priority高的thread搶到工作，要把pthread_cond_signal放在unlock之前。如果沒有priority的問題，兩種寫法都可以。
```
int done = 0;
pthread_mutex_t m = PTHREAD_MUTEX_INITIALIZER;
pthread_cond_t c = PTHREAD_COND_INITIALIZER;
void *spawned(void *arg) {
    // spawned thread goes first
    pthread_mutex_lock(&m);
    done = 1;
    pthread_cond_signal(&c);
    pthread_mutex_unlock(&m);
    //會呼叫所有在等著上lock的thread
    return NULL;
}
int main(int argc, char *argv[]) {
    pthread_t p;
    pthread_create(&p, NULL, spawned, NULL);
    pthread_mutex_lock(&m);
    while (done == 0)
        pthread_cond_wait(&c, &m);
        //如果是main thread搶到lock，cond_wait會把它release
    pthread_mutex_unlock(&m);
    // main thread continues
}
```
#### What happens if doneis removed?
有可能forever wait
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1765071819f46e0b2c4252797e0fb9d5.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_60a920948e9bd96c9cccd6437a0b0836.png)



### Threads vs. fork()
* **Only one thread (that called fork() in the parent) exists in the child process**
* Problem: **Child holds any locks held by parent**
* Solutions: (e.g., mutex)
    * Call `exec()` in the child
    * Establish fork handlers to clean up (unlock) the locks
```
int pthread_atfork(void (*prepare)(void),
void (*parent)(void), void (*child)(void))
```
* prepare: called in the parent **before fork creates the child**
* parent is called in the parent **after fork has created the child process, but before fork has returned**.
* child is **called in the child before returning from fork**.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_85488aba6ca98e68b87e7b2dc7ff1609.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_080c49722005028ac509b284de8abf52.png)

### Thread Signals
* Each thread has its own signal mask.
    * Different threads can block different signals.
* The signal disposition is shared by all threads in the process.
    * When a thread modifies the action associated with a given signal, **all the other threads share the action.**
    * One thread may change the disposition to ignore and all the other threads lost the signals
* Signals are delivered to a single thread in the process.
    * If the signal is related to a hardware fault or expiring timer, the signal is sent to the thread whose action caused the event.
    * Other signals are delivered to an arbitrary thread.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_346d25b378252188adb67e6f1db05400.png)
* 造成exception的thread會接收到對應的signal
* asynchronous的signal是在沒有把該signal block住的thread中選一個

### Thread Signal
```
int pthread_sigmask(int how, const sigset_t *restrict set, sigset_t *restrict oset)
```
* The first **thread in a child process** inherits its signal mask **from the thread in its parent that called fork()**. **Additional threads** inherits the signal mask of the **thread that created them**.
* Similar to sigprocmask() for process
```
int sigwait(const sigset_t *restrict set, int *restrict signop)
```
* Similar to `sigsuspend()` for process但是相反
`sigwait`會unblock `set`裡的signal
`sigsuspend`會block `set`裡的signal
* `set`: it specifies the set of signals for which the thread is waiting & selects a signal in set that is pending on the calling thread
* The waited signals are blocked before suspending the thread
* sigwait **atomically unblocks** the signals and wait until one is delivered
* The mask is restored before sigwait returns.
* `signop`: the integer will contain signal # that was delivered.
* Only one signal is delivered even multiple threads are waiting for the same signal.

### Synchronous Signal Handling
* Unlike asynchronous process signal handling, thread signal handling is synchronous.
* **Signal handlers are called in** the normal (sequential) **thread context**.
* Dedicated signal handling threads
    * One or more threads dedicated to handling the signals
        * A **loop for handling all the signals one by one**
        * Don’t worry about which functions are safe to call from a signal handler
* If a signal is being caught and a thread is waiting for the same signal in a call to sigwait, implementation can decide which way to deliver the signal (but not both).
有用sigaction，也有用thread做signal handling(`sigwait`)的話，系統會決定一個

#### Example: report by SIGUSR1
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_abdc0e543f93065ed11d86c59c17651b.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a97835972c39289a4e3ba7811413e564.png)
* 在`pthread_create`以前就要用`pthread_sigmask`把signal block住了，不然會有race condition
* While **processing SIGUSR1, this thread has SIGUSR1 blocked**.
Other SIGUSR1 signals will be held pending until sigwait()

### Thread-Safe/Atomic IO
* All the threads in the same process share the file descriptor and its file offset
* Concurrent access to the **same file** leads to **race condition**
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e29ec729de4797a4c609e73aa94165f2.png)
* Using `pread()/pwrite()` to set the offset and IO so as to assure **atomic operations**
* ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1b524ed5170d36c30863475a96d8e9ab.png)

### Atomic seek and read/write
```
#include <unistd.h>
ssize_t pread(int filedes, void *buf, size_t nbytes, off_t offset);
```
* Same to call lseek (from the start of the file) followed by read.
* Cannot interrupt pread
```
#include <unistd.h>
ssize_t pwrite(int filedes, const void *buf, size_t nbytes, off_t offset);
```
* Same to call lseek followed by write.
* Note that **file offset is not affected by the two functions** and the file referred by filedes should be seekable.

### Thread-Safe Functions
* A function is thread-safe if it can be safely called by multiple threads at the same time.
* If a function uses any **static variables (or global memory)**, it is not safe!
* Check _POSIX_THREAD_SAFE_FUNCTIONS or _SC_THREAD_SAFE_FUNCTIONS (sysconf)
#### 不保證是thread-safe的function
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a5f46cc030327455f85dcac6652aa35d.png)

### Thread-Safe v.s. Async-Signal Safe
* Thread-safe: reentrant w.r.t. multiple threads
可以被多個thread重複呼叫
    * **_r** appended at the end (e.g., acstime_r, rand_r)
    * rand() vs. rand_r(unsigned int *seedp)
    * rand() uses hidden state that is modified on each call
    * rand_r() uses *seedp to store the state between calls
* Async-signal safe: reentrant w.r.t. signal handler (safe to be reentered from handler)
可以在signal handler裡重複呼叫
* If a function is reentrant with respect to multiple threads, we say that it is thread-safe. This doesn't tell us, however, whether the function is reentrant with respect to signal handlers.
* 如果一個function是Async-signal safe，它一定是thread-safe
如果一個function是thread-safe，它則不一定是Async-signal safe
Thread-safe比較好做

#### Think about their difference
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_855b51bd2372a6f6a28433e8efdb2dc7.png)

### Thread-Safe FILE Objects
void flockfile(FILE *fp)
int ftrylockfile(FILE *fp)
void funlockfile(FILE *fp)
Obtain a lock associated with a FILE object
Recursive lock (lock again without deadlocking)
All standard I/O routines w.r.t. FILE objects behave
as if flockfile() and funlockfile() are called internally
Unlocked versions of character-based buffer I/O
Avoid serious performance degradation
getchar_unlocked(), getc_unlocked(), …
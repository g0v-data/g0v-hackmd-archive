# System Programming --- Slide 2
# chapter 3 UnbufferI/O
### Example of Unbuffered I/O
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ab8020a912578fcd9fe711f09cb65e91.png)
#    

#### UNIX Standardization 
* **ANSI C**:(stdio.h, stdlib.h, string.h, math.h, time.h, …)
Provide portability of **conforming C programs** to a wide variety of OS’s
> ANSI C、ISO C、Standard C是指美國國家標準協會（ANSI）和國際標準化組織（ISO）對C語言發布的標準
> 
* **POSIX** (unistd.h, pwd.h, dirent.h, grp.h, fcntl.h, …) 
Define the **application programming interface** for software compatible with variants of OS’s 
#    
### Unbuffered I/O 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9a64dac5af8281c786909644bf06e9ed.png)
####    
Each read() and write() invokes a **system call** in the kernel (part of POSIX.1)! 

#    
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fbb3be142da8886ec3cb6f442d7dc215.png)
####    
讀取 disk 越靠近圓心的地方， cost 越高
#    
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8ef58e9aa85860ada8aeae9274d5f1d6.png)
####    
Buffer cache: cache of **recently used disk blocks**
有了 kernel 裡的 buffer cache，我們不用每次都向 storage(disk) 要求讀取。
例如(5)(6)(7)步驟
#    
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d76a281c383da09a8a7e285de49fadd9.png)
####    
* **Buffer in user’s process** is provided by the **C standard library.**
* **Buffer cache** is provided by the **operating system**

過了紅色的線就代表一個 system call，表示佔用 CPU 資源
紅線後的 table 是在 Kernel Space
#   
### 重點整理：
* Popular functions: open, close, read, write, **lseek, dup, fcntl, ioctl**
* Each read() and write() invokes a system call!
* All data are processed as a series of bytes (no format)
* All **disk I/O** goes through the kernel's block buffers (also called the **kernel's buffer cache**)
* The term “unbuffered I/O” refers to the lack of automatic buffering in the user process

### File Descriptor
* **Non-negative integer** returned by open() or creat(): 0 .. OPEN_MAX (compiler-time limits)
* Virtually un-bounded for SVR4 & 4.3+BSD
* Referenced by the kernel
* Per-process base
* POSIX.1 – 
    <unistd.h>
    Convention employed by the Unix shells and applications 
    * 0: STDIN_FILENO
    * 1: STDOUT_FILENO 
    * 2: STDERR_FILENO
> 所以所有下載的套件 descripter 都從 3 開始

### Func: open, openat
```
#include <sys/types>
#include <sys/stat.h>
#include <fcntl.h>
``````
```
int open(const char*pathname, int oflag, …/* mode_t mode */);
```


* File/Path Name
    * PATH_MAX, NAME_MAX
    * _POSIX_NO_TRUNC -> ENAMETOOLONG if error occurs

* 必要旗標
    * O_RDONLY: 以唯讀模式開啟
    * O_WRONLY: 以唯寫模式開啟
    * O_RDWR: 以讀寫模式開啟
* 行為操作旗標
    * O_APPEND: 以附加模式開啟
以附加模式開啟的檔案，寫入操作都會從檔案末端開始，就算第二個行程也對該檔案進行寫入因而改變了檔案末端位置
例如多個行程要對相同 log 檔進行寫入的應用時，這個模式就會相當好用，因為它可以避免多個寫入者互相競爭的情況
    * O_CLOEXEC: 在執行 execl 後自動關閉該 fd
fork() 後執行 execl() 是常見的操作，不過 fork() 的子行程會複製父行程的 fd
execl() 時通常都不想保留 fd，設立此 flags 的 fd 可以在執行 execl 時自動關閉
    * O_NOATIME: 進行讀取操作時不更新檔案的存取時間
對於檢索、備份類會經常大量讀取系統上所有檔案的程式有很大的幫助，可以減少讀取後要更新 i-node 造成的寫入量
    * O_TRUNC: 若開啟的檔案存在且是一般檔案，開啟後就將其截短成長度為 0（簡單來說清空舊資料）
以 O_RDONLY | O_TRUNC 開啟檔案是未定義行為
* 同步、非同步旗標
    * O_SYNC: 以 SYNC 模式開啟檔案 (之後會再補充同步 IO)
    * O_ASYNC: 如果指定的檔案變成可讀或可寫的狀態，就產生一個 Signal (預設為 SIGIO)
用於 Socket、FIFO、Terminal 等需要非同步操作的情境
不能用於一般檔案
比較常見的應該是使用 aio 相關函式庫而不是使用 O_ASYNC 模式
    * O_NONBLOCK: 以 non-blocking IO 模式開啟
對 FIFO 做 read() 時，如果沒有資料可以讀取時立即返回(不阻擋)
因為沒資料而返回時會將 errno 設為 EAGAIN
    * O_DIRECT: 以 Direct IO 模式開啟檔案 (之後會再補充 Direct IO)
* 建檔相關旗標
    * O_CREAT: 如果指定的檔案不存在，就建立一個
    * O_EXCL: 有指定 O_CREAT 時才有效。**如果開檔時檔案已經存在，就回傳失敗**，可以避免兩個行程想同時建檔的競爭情況

ex: open(pathname, O_WRONLY | O_CREAT | O_TRUNC, mode) 
```
int openat(int dirfd, const char*pathname, int oflag, …);
```

同open相比，多了一个dirfd参数。关于它的用法，参考以下解释：`

如果pathname是绝对路径，则dirfd参数没用。如果pathname是相对路径，并且dirfd的值不是AT_FDCWD，则pathname的参照物是相对于dirfd指向的目录，而不是进程的当前工作目录；反之，**如果dirfd的值是AT_FDCWD**，pathname则是相对于进程当前工作目录的相对路径，**此时等同于open。**

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ff52ba6b5bb9ef865fae32785a2488be.png)

####  Reasons to distinguish the access modes
* Performance
    * Read ahead:是Linux核心的一個系統調用功能，透過把所需要的系統檔案預先讀入檔案快取（page cache）裡，解決磁碟存取速度的瓶頸問題，從而加快啟動時的速度。
    * buffer swapping
* Integrity/Security/Privacy
    * Process may only have read permission for a file,
 i.e., / etc/passwd
    * Opening files without proper permission leads to
 integrity/security/privacy issue. 


---
### Blocking vs. Synchronization 
**Block/non-block**: the behavior of a **function call** (Ch14.2)
* A blocking call returns after the requested operations complete
* A non-blocking call returns
    * Ask if the system receives and starts to process the request
    * Error if the system CANNOT process the request 

**Synchronized/Asynchronized IO**: the behavior of **data movement**: 
* Synchronized IO moves the data to the targeted devices and returns.
* An asynchronized IO buffers the data and moves the data to the targeted device later. 
 
---
### Func: creat and close
```
#include <sys/types>
#include <sys/stat.h>
#include <fcntl.h>
```
```
int creat(const char*pathname, mode_t mode);
```
* == open(pathname, **O_WRONLY | O_CREAT | O_TRUNC**, mode)
* This interface is made obsolete by open
* Only for write-access.
* Q: What if you want to create a file for READ and WRITE? 

```
#include <unistd.h>
int close(int filedes); 
```
* All open files are automatically closed by the kernel when a process terminates
* Closing a file descriptor **releases any record locks** on that file 

#### mode
新檔案的**使用權限**是由 open 的**第三個引數 umode_t mode 做指定**。如果**沒帶 O_CREAT 旗標，該引數會被忽略**，但如果有 O_CREAT 旗標但卻沒有指定 mode 的話，行為會是不明確的。mode 引數就是一般的 Unix 權限位元設定，可以使用 POSIX 預定義的幾個常數用 OR 運算結合指定：

* S_IRUSR: User 擁有 r 權限
* S_IWUSR: User 擁有 w 權限
* S_IXUSR: User 擁有 x 權限
* S_IRWXU: S_IRUSR | S_IWUSR | S_IXUSR
* S_IRGRP: Group 擁有 r 權限
* S_IWGRP: Group 擁有 w 權限
* S_IXGRP: Group 擁有 x 權限
* S_IRWXG: S_IRGRP | S_IWGRP | S_IXGRP
* S_IROTH: Other 擁有 r 權限
* S_IWOTH: Other 擁有 w 權限
* S_IXOTH: Other 擁有 x 權限
* S_IRWXO: S_IROTH | S_IWOTH | S_IXOTH

> 實際上儲存的權限還會受到 umask 影響，是一個行程屬性，他會遮蔽 mode 中對應的權限位元，例如 022 的 mask 會把 0666 的權限變成 0644

#### Where to store file descriptor & file status flags? 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e6829963c4726077e5fd7c5d504f6eb4.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_662662bd75c5034fec002c054b4b9725.png)

* Open File Descriptor Table
    * Each **process** has its own
    * A file descriptor contains
        * the **file descriptor flags**
        * a pointer to a system open file table entry
    * Child inherits from parents 

* System Open File Table
    * A set of all open files
    * Shared by all processes
    * Reference count of number of file descriptors pointing to each entry
    * Each file table entry contains
        * the **files status flags** for the file, the **current file offset**, & a pointer to the v-node table entry for the file
    * Each **open file** corresponds to an entry
        * a disk file may be opened multiple times 


> 兩個 process（Open File Descriptor Table）可能指向同一個 open file (System Open File Table)
> 

* V-node table
    * Each file consists of file **metadata** (or attributes) and file **content**
    * V-node table stores the **metadata**
     while buffer cache stores the **content**
    * Each open file has a v-node structure
    * Shared by all processes
    * V-node
        * Invented by Peter Weinberger (Bell Lab)/Bill Joy (Sun) to
support multiple file system types on a single computer system
    * No v-node in **linux**. A generic **i-node** is used. In SVR4, i-node
contains/is replaced with v-node.
    * i-node contains
        * **file owner, file size, residing device, block**
    * Each disk file corresponds to an entry when we open it 
    
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5cfefe34b0ddea458e8f2c9908d37a48.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a70d590267c3135666e14ba2985645d9.png)

---
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_934a6ef25228dc962271978b3197e9bb.png)

ANS: 3? 

---
### Func: lseek()

**C語言lseek()函式**：移動檔案的讀寫位置

標頭檔案：
```
#include <sys/types.h>  
#include <unistd.h>`
```
定義函式：
```
off_t lseek(int fildes, off_t offset, int whence);`
```
函式說明：
每一個已開啟的檔案都有一個讀寫位置, 當開啟檔案時通常其讀寫位置是指向檔案開頭, 若是以附加的方式開啟檔案(如**O_APPEND**), 則讀寫位置會指向**檔案尾**. 當read()或write()時, 讀寫位置會隨之增加,lseek()便是用來控制該檔案的讀寫位置. 引數fildes 為已開啟的檔案描述詞, 引數offset 為根據引數whence來移動讀寫位置的位移數.

引數 whence 為下列其中一種:

    SEEK_SET 引數offset 即為新的讀寫位置.
    SEEK_CUR 以目前的讀寫位置往後增加offset 個位移量.
    SEEK_END 將讀寫位置指向檔案尾後再增加offset 個位移量. 當whence 值為SEEK_CUR 或
    SEEK_END 時, 引數offet 允許負值的出現.
下列是教特別的使用方式:
1) 欲將讀寫位置移到檔案開頭時:lseek(int fildes, 0, SEEK_SET);
2) 欲將讀寫位置移到檔案尾時:lseek(int fildes, 0, SEEK_END);
3) 想要取得目前檔案位置時:lseek(int fildes, 0, SEEK_CUR);

> fseek()不像lseek()會返回讀寫位置, 因此必須使用ftell()來取得目前讀寫的位置.
> 
No I/O takes place until next read or write.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cfb756e4675021700694f9c5e3c802d2.png)

---
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2bd8109054297ee37ea8c1178f8c2f20.png)

```
$ od –c file.hole
//dump files in the format of ASCII characters or backslash escapes
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d21e9cdded9a0cb6f92c6c9091f49ce6.png)
```
$ cat < file.hole > file.nohole
// 把 file.hole 寫到 file.nohole 裡，cat 會自己把 null(\0) 換成 0
```
Linux Cat命令主要有三大功能:    

1.Linux Cat命令一次顯示整個檔案。$ cat  filename
2.Linux Cat命令**從鍵盤**建立一個檔案。$ cat > filename(只能建立新檔案,不能編輯已有檔案.)
3.Linux Cat命令將幾個檔案合併為一個檔案。$cat  file1   file2 > file

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a2ec3f27f334f5b7fd57eb56ec6fcacf.png)

---

### Func: read and write 
```
#include <unistd.h>
ssize_t read(int filedes, void *buf, size_t nbytes);
```

* Less than nbytes of data are read:
    * EOF(0), terminal device (line-input), network buffering, record-oriented devices (e.g., tape), signal
    * -1: error
    * Offset is increased for every read() – SSIZE_MAX 

```
#include <unistd.h>
ssize_t write(int filedes, const void *buf, size_t nbytes);
```
* Write errors for disk-full or file-size-limit causes.
* When O_APPEND is set, the file offset is set to the end of the file before each write operation.

---

### Delayed Write 

* Keep the data buffered so that multiple writes **do not require multiple disk accesses.**
* The buffer is queued for writing to disk at some later time. 

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b3e2fd809b9eb4b32abc90f24b830675.png)

---
### 名詞介紹
Disk：不會因為斷電而抹除資料的儲存媒體--磁碟。磁碟(disk)的最小儲存單位稱為sector或block，以目前的硬碟來說，通常是512bytes。

Block：寫入磁碟或是檔案系統的最小單位。檔案系統所作的每一個動作都是在操作這些block。特別注意的是，檔案系統的block大小，永遠等於或大於磁碟上的block大小(考考你，知道為什麼嗎)。

Partition: Disk上部分block的集合。一個disk可以包含多個partition。

Volume: 儲存媒體如disk上一些block集合所被賦予的名稱。這些block的集合可能來自一個完整的或是部分的disk，也可能由跨越多個disk所組成，這點是和partition有所不同之處。

Superblock: 在volume中，檔案系統用以儲存自身資訊的區塊。Superblock中的資訊通常包括像是volume的大小、名稱等等。

Metadata: 用以描述資料性質的資訊，但是不包含在資料上。像是記錄檔案大小的資訊，他不是檔案資料的本體，而只是用以說明資料的一個性質--大小。

Journaling: 用以確保檔案系統metadata的內容完整性的技術，以避免系統在不正常斷電下造成檔案毀損。

I-node: 檔案系統用來記錄所有metadata的地方，同時也記錄所有跟檔案控制相關的內容，所以I-node又稱為file control block(FCB)。

這些是主要常用到的關鍵詞，其中I-node借用於Unix作業系統。而方才提到的，檔案系統的block**必須大於或等於**disk上的block大小，其原因就是disk上的block是磁碟系統運作的基本單位。檔案系統建立在磁碟系統之上，所以檔案系統的最小單位不能小於磁碟系統。

---
### File I/O - Efficiency 

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4d57c682b4273abc5df91db9770f4c1e.png)



![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7f896e556467674e055bbe6505823b30.png)

* clock = real time
* Buffer_size越大，搬移資料次數越少，
    * User CPU效率越高（可以到0）
    * system CPU效率越高，但sys CPU time降到一定的程度就很難再低，因為一口氣搬掉，導致必須等待disk(readahead的效用降低)
### 什麽是 Read Ahead?
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b3321f6d848a4f55ed40e66af815a67d.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2c10b48d47df481044257e79d7864c2b.png)

**User CPU Time + Sys CPU Time <= Clock Time**
* Difference is quite small when the buffer size is small
* The difference increases when the buffer size comes to 128 
* Buffer size 大到一定程度 =>可以read ahead => 雖然clock time 差不多但大幅減少CPU time

---
### What Happens with Each Call?
* After each write completes, the current file offset in the file table entry is incremented. 
> If current file offset > current file size, change current file **size** in **i-node table entry**.) 
> 
* If file was opened O_APPEND, set corresponding flag in **file status flags** in **open file table**. For each write, **current file offset**(sys open file table) is first set to current file size from the i-node entry.
* **lseek** simply adjusts current file offset in file table entry (**sys open file table**)
* To lseek to the end of a file, just copy current file size into current file offset. 
* File descriptor flags versus file status flags 
    * File descriptor flags
        * `fcntl()`
        * F_GETFD
        * F_SETFD
        * FD_CLOEXEC
    * File status flags
        * `open(), openat()`
        * O_CREAT
        * O_APPEND
* **dup()** and **fork()** **causes the sharing of entries** in the (system) open file table. (Will discuss later) 
* Reading a file simultaneously is no problem 
---
### File I/O – Atomic Operations ：不可中斷的一個或一系列操作。
所謂的原子操作，取的就是“原子是最小的、不可分割的最小個體”的意義，它表示在多個執行緒訪問同一個全域性資源的時候，能夠確保所有其他的執行緒都不在同一時間內訪問相同的資源。也就是他確保了在同一時刻只有唯一的執行緒對這個資源進行訪問。這有點類似互斥物件對共享資源的訪問的保護，但是原子操作更加接近底層，因而效率更高

* Appending to a file (**O_APPEND** in open() )
* Seeking and reading/writing ( **pread(), pwrite()** )
* Creating a file (**O_CREAT|O_EXCL** in open() )

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0c1401736da9a57cb2aa9adfac7a8ed7.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a882dda8876ca553027ac6de0ca2876b.png)


---
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
> Note that **file offset is not affected** by the two functions and the file referred by filedes should be seekable. 

---
以下example有錯

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3d4a5bf04717832b8c3d8ed79bf6668d.png)

---
### Func: fork
C 語言中的 fork 函數可以將目前的程式行程（process）複製一份，建立出新的子行程（child process），而原本的行程就稱為父行程（parent process）

fork 在執行之後，會傳回一個整數的傳回值，以下是各種數值所代表的意義：

* 負值（小於零）：建立子行程失敗。
* 零：代表這個程式處於新建立的子行程中。
* 正值（大於零）：代表這個程式處於原本的父行程中，這個整數值則是子行程的 ID。
* 
在程式設計上我們可以靠著 fork 的傳回值來判別父行程與子行程，進而讓不同的行程處理不同的工作。**新建立的子行程會有獨立的行程 ID（process ID），與父行程的行程 ID 不同。**

---
### Error Handling
`errno in <errno.h> (sys/errno.h)`
E.g., 15 error numbers for open()
    * ENOENT: no such file or directory

`#define ENOTTY 25 /* Inappropriate ioctl for device */`
* Never cleared if no error occurs
* No value 0 for any error number
* Functions
```
char *strerror (int errnum) (<string.h>)
void perror(const char *msg) (<stdio.h>)
```
* Fatal error: no recovery action
* Nonfatal error: delay and try again
    * Improves robustness by avoiding an abnormal exit
* Examples
EAGAIN, ENFILE, ENOBUFS, ENOLCK,
ENOSPC, ENOSR, EWOULDBLOCK,
ENOMEM___
### Func: dup and dup2
```
#include <unistd.h>
int dup(int filedes);
int dup2(int filedes, int newfiledes);
```
* Create a copy of the file descriptor 
* dup() returns the lowest available file descriptor. 
    * == **fcntl(filedes, F_DUPFD, 0);** 
* dup2() is atomic and from Version 7, …SVR3.2
    * == close(newfiledes); fcntl(filedes, F_DUPFD, newfiledes); 
把fd3指向fd1所指的sys open file table的entry：dup2(1,3)
如果3號跟其他entry已有connection，則會先關閉它們的連接
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f70a97d073217a2dd2d4b025c156aadb.png)





---

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ffadb78ee843145d990045b13cdcbf27.png)

ANS: f
因為fd1, fd2指向不同entry

---

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3568470b313ed421d09fe6480744a9a2.png)

ANS: o
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_674e8dff88a963a33939c107e756d812.png)

---
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9226015fa2c4423ad9d9d2fd71a4c6d4.png)

ANS: o

---
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bec5e9ef3293e2226a10273ec72a1d16.png)

0代表standard input
1代表standard output，把1指到fd，所以output到fd裡

---

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_216c9aa52682ad9aee97a74b10cbe353.png)

---
### File I/O: sync(), fsync(), fdatasync()
Kernel maintains a buffer cache between apps & disks. 
```
#include <unistd.h>
int fsync(int filedes); // data + attr sync
int fdatasync(int filedes); // data sync
void sync();
 // 1. queues all kernel modified block buffers
 // for writing and returns immediately
 // 2. called by daemon update & command sync 
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1927ac03e267e20a111bc2e3371b4684.png)
在open()的時候設定，每進行read/write它就會根據option自動sync
> The Linux file system isn’t honoring the O_SYNC flag 
(**O_SYNC** should **increase** system and clock **time**)
>
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fc9618ca1d16d4e24bc5f47bcb15129d.png)
O_DSYNC: write operation Don't wait for attr(filew info)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9e2d9b7d288a3ae59cce26f15ce80564.png)
O_SYNC: write operation Don't wait for attr(filew info)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c0ad7861f1e5904efa20420bf66e9abe.png)
O_RSYNC: 每个以文件描述符作为参数的read操作等待，直到所有对文件同一部分的未决写操作完成

---
### 實驗
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e933e36aefa973b8d1100d46355e26f8.png)

Linux不支援O_SYNC，clock time很小，表示不能用，進去一下就退出來了
但同時用fync和O_SYNC就可以，f開頭的比較有強制力

---
### Func: fcntl
Changes the properties of opened files 
```
int fcntl(int fd, int cmd);

int fcntl(int fd, int cmd, long arg);

int fcntl(int fd, int cmd, struct flock *lock);
```
cmd:
* **F_DUPFD**: duplicate an existing file descriptor (**>= arg**`fd`).
    * `dup(oldfd);`等效於`fcntl(oldfd, F_DUPFD, 0);`
    * `dup2(oldfd,newfd);`等效於`close(oldfd);  fcntl(oldfd, F_DUPFFD,newfd);`
    * 在上述例子arg為`0, newfd` 函式返回大於等於arg的最小檔案描述符
    * should be **atomic operation**
* FD_CLOEXEC (close-on-exec ) is cleared (for exec()).
* F_GETFD, F_SETFD: file descriptor flag, 
    e.g., FD_CLOEXEC
* F_GETFL, F_SETFL: file status flags
    * e.g., O_APPEND, O_NONBLOCK, O_SYNC, O_ASYNC, O_RDONLY,O_WRONLY, RDWR
    * 一般來說，open完不能更改flag所以要用fcntl
* F_GETOWN, F_SETOWN: ownership, + procID, -groupID
SIGIO, SIGURG – I/O possible on a filedes/urgent condition on I/O
channel
* F_GETLK, F_SETLK, F_SETLKW
File lock 

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1a29e31b29d778deb36287ee0da3f28f.png)
* Use `accmode = val & O_ACCMODE` to check read or write

---
#### Turn on one or more flags
* val |= flags

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a01d98db7f0965b96397ebd707068316.png)

#### clear the flag
* val &= ~flags

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_65765ab89fa6a7229ea22a8749cd15b1.png)

### Func: ioctl
```
#include <unistd.h>
#include <sys/ioctl.h>
int ioctl(int filedes, int request, …);
```
* Catchall for I/O operations
    * E.g., setting of the size of a terminal’s window.
* More headers could be required:
    * Disk labels (<disklabel.h>), file I/O (<ioctl.h>),
mag tape (<mtio.h>), socket I/O (<ioctl.h>),
terminal I/O (<ioctl.h>)

### File I/O - /dev/fd
```
open(“/dev/df/n”,mode) 
```
-> **duplicate descriptor n** (assuming that n is open)

* `fd=open(“/dev/fd/0”,mode) == fd=dup(0)`

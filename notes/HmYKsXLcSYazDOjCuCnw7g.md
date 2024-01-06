# System Programming --- Slide 2

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
* All disk I/O goes through the kernel's block buffers (also called the kernel's buffer cache)
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

### open, openat
```
#include <sys/types>
#include <sys/stat.h>
#include <fcntl.h>
int open(const char*pathname, int oflag, …/* mode_t mode */);
```


* File/Path Name
    * PATH_MAX, NAME_MAX
    * _POSIX_NO_TRUNC -> ENAMETOOLONG if error occurs
* O_RDONLY, O_WRONLY, O_RDWR, O_EXEC (file access modes)
* O_CREAT, O_TRUNC, O_EXCL (file creation)
* O_APPEND, (append to the end of the file for each write)
* O_NONBLOCK (non-blocking)
* O_DSYNC, O_RSYNC, O_SYNC (data synchronization)

ex: open(pathname, O_WRONLY | O_CREAT | O_TRUNC, mode) 
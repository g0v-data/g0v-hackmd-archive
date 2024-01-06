# System Programming - Slide5.5
# chapter5

### Standard I/O Library
* Major revision by Dennis Ritchie in 1975
* An ANSI C standard
    * Easy to use and portable
    * Details handled:
        * Buffer allocation, optimal-sized I/O chunks, better interface, etc.
* Difference from File I/O =unbuffered I/O)
    * **File Pointers vs File Descriptors**
    * fopen vs open
    * When a file is opened/created, a stream is associated with the file.
    * FILE object
        * File descriptor, pointer to buffer, buffer size,# of remaining chars, an error flag,an end-of-file flag, and the like.
    * stdin, sdtout, stderr defined in <stdio.h>
STDIN_FILENO, STDOUT_FILENO,
STDERR_FILENO

* Buffered IO 是指在User Space 被 C library圈出來的buffer
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_187db2a3d1c5d7f1513a98487248c7a1.png)
> Linux shell command: strace可以讓我們追蹤這隻process使用了哪些Unbuffer IO
> 

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a373a25f3a31f81fc8714aa46a2132d8.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_46881d58dbca6e6e12fa27a4caa3a844.png)

### Func: fopen()
```
#include <stdio.h>
FILE *fopen(const char *pathname, const char *type);
```
* text file vs. binary file: b (in rb, wb, ab, r+b, …) stands for binary file – no effect for Unix kernel
* **Append mode** supports multiple access (**atomic operation**)
 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_422538ea2fb3cff591e19d6642d3769b.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_272a81b0262c17bdb7e625217dee68fd.png)

對r來說＋是加上寫入資料
對w,a來說＋是加上讀取資料

### Func: freopen()
```
FILE *freopen(const char *pathname, const char *type, FILE *fp);
```
* **close fp stream first** and clear a stream's orientation 然後把參數的pathname指向fp
* typically used to open a specified file as one of the predefined streams: standard input/output/

### fdopen, fileno, fclose
```
FILE *fdopen(int fildes, const char *type);
```

* Associate (standard) I/O stream with an existing file descriptor – POSIX.1 對unbufferIO 做bufferIO
* Pipes, network channels
* **No truncating for the file for “w”**
```
int fileno(FILE *fp);
```
Get filedes for fcntl, dup, etc.
```
int fclose(FILE *fp);
```
* **Flush buffered output**
* Discard buffered input
* All I/O streams are closed after the process exits.
* **The relocated buffers must be valid before the stream is closed**.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0d81b54ec1770774b266a38c924b153c.png)
databuf在函式結束後遺失被其他資料覆蓋

### Buffering
* Goal
    * Use the minimum number of read and write calls.
* Allocation
    * Automatically allocated when the **first-time** I/O(malloc) is performed on a stream.
    * Call setbuf() or setvbuf()
* Types
    * Fully Buffered(滿的時候才呼叫一次write)
        * Actual I/O occurs when the buffer is filled up.
        * **Disk files, pipes, and sockets** are normally fully buffered.
    * Line Buffered
        * Perform I/O when a **newline char** is encountered! – usually for terminals (e.g., stdin, stdout).
        * Caveats
            * The filling of a fixed buffer could trigger I/O.
            * The flushing of all line-buffered outputs if input is requested (from the kernel).
            就算沒有換行字元，在有input要進來的情況下還是要先write
            Example:
            char buf[100];
            printf(“$ “); // “prompt” in shell
            scanf(“%s”, buf); // trigger the output of $

    * **Unbuffered**
        Expect to output ASAP, e.g. using write()
        E.g., **stderr**
        
### Way to Synchronize Data
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f7af199a78bf78fa93b08ff7dfed0209.png)
一定要記得fflush不然fsync系列函數沒有作用

### Build up your own buffer
Must be called before any op is performed on streams!
```
void setbuf(FILE *fp, char *buf);
```
Full/line buffering if buf is not NULL (BUFSIZ)
Ex: line buffer for terminals
**Turn buffering off if buf is NULL**
```
#define BUFSIZ 1024 (<stdio.h>)
int setvbuf(FILE *fp, char *buf, int mode, size_t size);
可以自己設size和type
```
Specify the type of buffering
mode: _IOFBF, _IOLBF, _IONBF (<stdio.h>)
Optional size -> st_blksize (stat()) **最理想的buffer size是disk block size**

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a34196dfa9c3d456494d268f88169c74.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_701b0b5f0cbffc5b7363b57065008cc8.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e44cdd12e3f408b0add8b00fa030c4da.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_48537ec2d094ef7cde5f2ff6b6394821.png)

重要！
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e44b904ea90e3c648073c54283795fcf.png)
所以要用`int c`

```
#include <stdio.h>
int ferror(FILE *fp);
```
```
int feof(FILE *fp);
```
```
void clearerr(FILE *fp);
```
* Clear both of error and EOF flags
```
int ungetc(int c, FILE *fp);
```
* **No pushing back of EOF** (i.e., -1)
* No need to be the same char read!
* Clear EOF flag
* The character is **stored in IO buffer, instead of file.**

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7c9be0cdd4e1fd0227db741004d30c3c.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f88d9e1bab12153d8654caa130760776.png)

### Line-at-a-Time I/O
```
#include <stdio.h>
char *fgets(char *buf, int n, FILE *fp);
```
* **Include ‘\n’** and be terminated by null
* Could **return a partial line** with (n-1) bytes **if the line is too long.**
```
char *gets(char *buf);
```

* Read from stdin.
* **No buffer size is specified -> overflow (unsafe)**
* *buf **does not include ‘\n’** and is terminated by null.


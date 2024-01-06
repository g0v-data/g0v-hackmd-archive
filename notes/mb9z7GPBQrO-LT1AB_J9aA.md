# System Programming — Slide 3 — Advanced I/O

### Blocking vs Nonblocking

* Blocking:
    * Process is **suspended until all bytes** in the count field are read or written 
* Nonblocking:
    * The OS only reads or writes as many bytes as possible **without suspending** the process 
    * Read暫停的時機：buffer滿 or 找不到data
    * Write暫停的時機：buffer cache滿了，但資料需要回寫到硬碟裡不能丟掉
    * “Slow system calls” are those that can block forever
        * Reads or writes on **pipes, terminal devices, and network devices**
        * 要小心！
    * Nonblocking I/O lets us issue an I/O operation, such as an open, read, or write, and not have it block forever.
    * Two ways to specify nonblocking I/O
        * open() or fcntl() with the O_NONBLOCK flag

#### Turn on one or more flags with fcntl()
val **|=** flags: turn on flags
val **&= ~** flags: clear the flags
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bcaec8b230831232e54671a9635ba6d6.png)
### Example of non-blocking
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_edd9519c60845ab89a1b6ed3a80a1496.png)

Result:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0e0765871a82c097327f292cae1328b4.png)

Reason: Output queue滿了
### Terminal Device
* Each terminal device has an input queue and an output queue
* The shell redirects standard input to the terminal (in canonical
mode), and each read returns at most one line.
* When the output queue starts to fill up
    * Blocking: put process to sleep until room is available.
    * Non-blocking: polling (busy waiting; a waste of CPU time on a multiuser system)
    
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_deee0473181ced78f5d00e5668530586.png)


### I/O Multiplexing
* When an application needs to handle
multiple I/O descriptors at the same time
E.g. file and socket descriptors, multiple socket descriptors
> socket 是一種 API
* When I/O on any one descriptor can result
in blocking

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_57d12a50aff27fdf14fa665599791cf3.png)

### Func: select

`totalFds = select(nfds, readfds, writefds, errorfds, timeout)`
* nfds: the range (0.. nfds-1) of file descriptors to check 
* getdtablesize(): get file descriptor table size
* readfds: bit map of filedes. Set the bit X to ask the kernel to check
if filedes X is ready for reading. Kernel returns 1 if data can be
read on the filedes.
* writefds: bit map if filedes Y is ready for writing (same as read bitmap).
* errorfds: bit map to check for errors.
* timeout: how long to wait before un-suspending the process (microseconds)
`select ( 0, NULL, NULL, NULL, &timeval)`
Usual sleep(…) call has resolution of seconds.
* **totalFds = number of ready descriptors,** 
**0 on timeout, negative for error**

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_08cf7c588cdc5112c7d6f2436249075e.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_83da4e7c96640c2a4549a66981d73084.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3275198e15729d161c40f7219937cad8.png)

注意：常見做法是不直接去select master_set，而是先複製一份working_set，再對 working_set select，如此一來就可以確定每次讀set都從頭開始

### Func:poll
功能基本上同等於select
```
int totalFds = poll( fdarray[], nfds, timeout )
```
```
struct pollfd {
    int fd; // file descriptor to check, or <0 to ignore
    short events; // bit mask: each bit indicates an event of interest on fd
    short revents; // bit mask: each bit indicates an event that occurred on fd
}
```
* events: 
    * POLLIN: There is data to read.
    * POLLOUT: Writing now will not block.
    * POLLHUP: Hang up (output only).
    * POLLNVAL: Invalid request: fd not open (output only).
* nfds: the number of items in the fds array
* timeout: how long to wait before un-suspending the process
    * -1: wait forever
    * 0: don’t wait
    * \> 0: wait (milliseconds)
* **totalFds = number of ready descriptors**
**0 on timeout, negative for error**

### Comparison: select vs poll
> bitmask:位元遮罩
* select: rewrites a bitmask that is no longer the one you set up
poll: keeps reusing the same bitmask for input
* select: inefficient if only one fd is assigned a high number
poll: combines multiple bitmasks into one
* select: **only 3 event types**(i.e., read, write, error)
poll: more event types (e.g., POLLPRI: urgent data like out-of-band on TCP socket to read)
* Both need to check each fildesc. each time

Alternatives
* pselect() (nanoseconds, signal mask),
epoll() (good for speed & scalability)

### Comparison : I/O Mode
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ac3871ca443a749b3a17b626fde523a3.png)

缺點：
blocking: 有可能鎖在那裡，失去控制權
non-blocking: 有完整控制權，但三不五時就要check
三者的差別只在waiting for data的部分
越左邊越synchronous

### Why File Lock?
Exclusively access for avoiding data inconsistency
* More than one process may access a file at the same time
* Without exclusively access, system may overwrite some of the old data while that old data is still being read.
* Atomic Operation

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_eae17d48b8d30fb746670012e044f290.png)

### File Lock in UNIX
Exclusively locking a file prevents other processes to read/write the same file
* When a lock is granted, the process has the right to read/write the file
* When a lock is denied, the process has to wait until the lock is released by the lock holder.

Three ways to lock
* flock(): lock an entire file
* fcntl(): lock arbitrary byte ranges in a file (introduced here)
* lockf(): built on top of fcntl()

### Types of Lock
* Shared read lock
    * Any number of processes can have a shared read lock on a given byte
    * If there are one or more read locks on a byte, there can't be any write locks on that byte
* Exclusive write lock
    * Only one process can have an exclusive write lock on a given byte
    * If there is an exclusive write lock on a byte, there can't be any read locks on that byte

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_398339a10788e9116436989de801c995.png)

當某file已經有read lock，照policy來說後來加上的lock：read優先於write，但事實上不盡如此，不然就會發生wirte一直無法執行的情況

### fcntl Record Locking
`int fcntl (int filedes, int cmd, ... /* struct flock *flockptr */ );`
* Record locking command
    * F_GETLK: Get the first lock which blocks the lock description pointed to by the third argument
    * F_SETLK: Set or clear a file segment lock (like nonblocking)
    * F_SETLKW: This command shall be equivalent to F_SETLK except that **if a shared or exclusive lock is blocked by other locks, the caller shall wait until the request can be satisfied (like blocking)**
* Lockptr
```
struct flock {
    short l_type; /* F_RDLCK, F_WRLCK, or F_UNLCK */
    off_t l_start; /* offset in bytes, relative to l_whence */
    short l_whence; /* SEEK_SET, SEEK_CUR, or SEEK_END */
    off_t l_len; /* length, in bytes; 0 means lock to EOF */
    pid_t l_pid; /* returned with F_GETLK */
}
```

### Parameters to lock files
Type of lock
* F_RDLCK: a shared read lock
* F_WRLCK: an exclusive write lock
* F_UNLCK: unlocking a region

The size of the region in bytes, l_len
* \> 0: the lock extends to l_len bytes from l_whence and
can go beyond the current size of the file.
* **= 0: the lock extends to the largest possible offset of the file**

### Remarks
File access
* To obtain a read lock, the descriptor must be open for reading
* To obtain a write lock, the descriptor must be open for writing
同一個process可以上read lock再上write lock 但我們實際上不該這樣做，系統會認為我們對自己做的事有認知

Non-atomic operations
* Testing for a lock with F_GETLK and then trying to obtain that lock with
F_SETLK or F_SETLKW is not an atomic operation.

Implied inheritance and release of locks
* When a process terminates, all its locks are released
* Whenever a descriptor is closed, any **locks on the file** referenced by that descriptor for that process are released.
* Locks are **never inherited across a fork**
* Locks are **inherited across an exec except close_on_exec is set**

The compatibility rule only applies to different processes

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a38b5eeeeb3f758a40fc5458158bbb15.png)
Ans: 兩個lock都不在了，lock是對file不是對file descriptor 或 sys table entry

### FreeBSD implementation
lock只跟著process和file，與descripter無關

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bd9378accc7a90f62f0213f57cd6c099.png)

### Advisory lock
* All the processes that access the shared files shall call **the file lock function** to access file
* Any process bypasses the file lock functions may lead to inconsistent data
* fcntl() provides advisory lock 
* 這裏的先決條件是『所有的存取作業都必須經由一組特定的函式來完成

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_195788123fbe965a611c302437dc5279.png)

### Mandatory lock
* The kernel checks every open, read, and write to verify that the calling process is not violating a lock.
* Mandatory lock is not part of SUS (Single UNIX Specification)
    * Linux 2.4.22 and Solaris 9 provide mandatory record locking
    * FreeBSD 5.2.1 and Mac OS X 10.3 do not. 

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_41cd518c26fed280b70c343bc2bb3c93.png)
* Mandatory locking specified in **file permissions** (類似chmod要有權限)
* Mandatory locking involves **system overhead**

### Net working
Sockets as means for inter-processcommunication (IPC)

### IP
* Point to point
    * between machines
    * addressed using IP address
* Message (packet) based
* Unreliable
    * network failures
    * **router buffers fill up**
* Dynamic routing
    * order may be lost
* Heterogeneous intermediate networks
    * fragmentation

### TCP & UDP
* Both
    * built on top of IP
    * addressed using port numbers
* process to process (on UNIX platforms)
* TCP
    * connection based, reliable, byte stream
    * used in: FTP, telnet, http, SMTP(email)
* UDP
    * connectionless, **unreliable**, datagram (**packet based)**
    * used in: NFS, TFTP

### Port number
* 16 bit integers (0~65536)
* Unique **within a machine** (just within)
* To connect need IP address + port no
* TCP
    * connection defined by
IP address & port of server + IP address & port of client
* UNIX
port < 1023 – root only
used for authentication

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4213926afaf5f6f35289bad329bb9e94.png)

### TCP Client/Server Model
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7675cbe1bbe741d47d34097881b1ed3d.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_955a7d7fce304f1570edbd0e438e1dba.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d7e8f798a99afff9486962e94b7954fb.png)
複製port21去收訊息，這樣其他機器同時可以找21

### What is socket?
有別於 IPC ，Socket 是用於網路上不同程序的互相溝通，比如說流覽器要怎麼跟 Web Server 拿取資料、Messenger 訊息的收發、 ftp 檔案的上傳與下載等等，在現今的網路編程中，Socket 可以說是無所不在。

至今 Socket 也應不同的需求或 OS 衍生出了不少版本，這篇筆計主要是討論 Linux 的 socket ，並專注在實現 TCP 編程：

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7be180a82912f550598fe009762bd6b3.png)

#### 先從建立一個 Socket 出發
使用socket(int,int,int)，它能幫助我們在kernel中建立一個socket，並傳回對該socket的檔案描述符。
* Prototype
`int socket(int domain, int type, int protocol);`
* Arguments
    * domain
    定義了socket要在哪個領域溝通，常用的有2種：
        * AF_UNIX/AF_LOCAL：用在本機程序與程序間的傳輸，讓兩個程序共享一個檔案系統(file system)
        * AF_INET , AF_INET6 ：讓兩台主機透過網路進行資料傳輸，AF_INET使用的是IPv4協定，而AF_INET6則是IPv6協定。
    * type
說明這個socket是傳輸的手段為何：

        * SOCK_STREAM：提供一個序列化的連接導向位元流，可以做位元流傳輸。對應的protocol為TCP。
        * SOCK_DGRAM：提供的是一個一個的資料包(datagram)，對應的protocol為UDP
    * protocol
設定socket的協定標準，**一般來說都會設為0**，讓kernel選擇type對應的默認協議。

* Return Value
成功產生socket時，會返回該socket的檔案描述符(socket file descriptor)，我們可以透過它來操作socket。若socket創建失敗則會回傳-1(INVALID_SOCKET)。

* Network Byte Ordering
    * Network is big-endian, host may be big- or little-endian
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_773745c74e1569937ed3112f28cc6755.png)
    * `htons() / htonl()` : convert host byte order to network byte order
`ntohs() / ntohl()`: convert network byte order to host byte order


#### 從Client連向Server
客戶端要連向伺服端，需要先知道並儲存伺服端的IP及port，`netinet/in.h`已經為我們定義好了一個`struct sockaddr_in`來儲存這些資訊：

```
// IPv4 AF_INET sockets:
// IPv6參見 sockaddr_in6
struct sockaddr_in {
    short            sin_family;   // AF_INET,因為這是IPv4;
    unsigned short   sin_port;     // 儲存port No
    struct in_addr   sin_addr;     // 參見struct in_addr
    char             sin_zero[8];  // Not used, must be zero */
};

struct in_addr {
    unsigned long s_addr;          // load with inet_pton()
};
```
有了IP跟port，我們就能使用`connect(int struct sockaddr, int)`進行客戶端與伺服端之間的連線。
* Prototype

```
int connect(int sd, struct sockaddr *server, int addr_len)
```
* Arguments
    * sd: socket descriptor 
    * server: 負責提供關於這個socket的所有信息，以下是一個簡單的設定例子：
```
struct sockaddr_in info;

bzero(&info,sizeof(info));//初始化，將struct涵蓋的bits設為0
info.sin_family = PF_INET;//sockaddr_in為Ipv4結構
info.sin_addr.s_addr = inet_addr("123.123.13.12");//IP address
info.sin_port = htons(8080);
```


//剩下的去看http://zake7749.github.io/2015/03/17/SocketProgramming/

* BIND: bind a name/address to a socket
`int bind(int sockfd, struct sockaddr *addr, int addrlen);`
    * sockfd - socket descriptor (returned from socket())
    * addr: socket address, struct sockaddr_in is used
    * addrlen := sizeof(struct sockaddr)
    
* LISTEN: listen for connections on a socket
`int listen(int sockfd, int backlog);`
    * backlog: how many connections we want to queue
    
* ACCEPT: accept a connection on a socket. It extracts first request on the queue of pending connections for the listening socket, **creates a new connected socket**, and returns a new file descriptor referring to that socket. The original socket is unaffected. It **blocks the caller** until a connection is present.
`int accept(int sockfd, void *addr, int *addrlen);`
    * addr: here the socket-address of the caller will be written
    * returned: a new socket descriptor (for the temporal socket)
    
### Read & Write on Sockets
* Bi-directional byte stream
    * read and write to same file descriptor
    * possible to close one direction
    * special socket call, e.g., shutdown()
* Reading may block
    * reading from a file either:
(i) succeeds
(ii) gets end of file (ret = 0)
    * Reading from a socket waits until
(i) network data received (ret > 0)
(ii) connection closed (ret = 0)
(iii) network error (ret < 0)


* Writing may block
    * writing to a socket may
(i) send to the network (ret > 0)
(ii) find connection is closed (ret = 0)
(iii) network error (ret < 0)
it **may return instantly but may block if buffers are full**
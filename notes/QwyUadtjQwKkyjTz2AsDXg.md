# System Programming - Slide7
# chapter7 

### Process
* A process is an instance of a running program.
    * Not the same as “program” or “processor”
* Process provides each program with two key abstractions:
    * Logical control flow
        * Each program seems to have exclusive use of the CPU.
    * Private address space
        * Each program seems to have exclusive use of main memory.
* How are these illusions maintained?
    * Process executions interleaved (multitasking)
    * Address spaces managed by virtual memory system
> Virtual Memory的size跟bus有關
> 


### main Function

int main(int argc, char *argv[ ])

* The starting point of a C program. Programs written in different environments have a different name.
e.g., mainCRTStartup, WinMainCRTStartup
* A special **start-up routine** is called to set things up first before call main()
    * Set up by the **link editor** (invoked by the compiler)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_12308754a076bece8c1c4a646bad9233.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4f3391adc2af5e53ba8348299341e551.png)

### Command
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_75529aaa0d31cd4771e3041ef4e495ba.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8539102f319c12f4653c6455a02e894d.png)
看圖可以知道進入點是`T_start`

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a89d21eaaf91a25dedfcff0f6200c883.png)
flag: -d // disassemble
可以看到entry point 為`_start`，不是

### Process Termination
* Eight ways to terminate:
    * Normal termination
        * Return from main()
        * exit(main(argc, argv));
        * Call exit()
        * Call _exit() or _Exit()
        * Return of the last thread from its start routine
        * Calling pthread_exit from the last thread.
    * Abnormal termination (Chapter 10)
        * 異常死亡都是被SIGNAL死的
        * Call abort()
        * Be terminated by a signal
        * Response of the last thread to a **cancellation request.**


### File Format/Layout of a Program
* ELF (**Executable and Linkable Format**)
    * Standard library format for object files
    * Derived from AT&T System V Unix
        * Later adopted by BSD Unix variants and Linux
    * One unified format for
        * Relocatable object files (.o)
        * Executable object files
        * Shared object files (.so)
        * .o檔和.so檔裡面都是裝function，差別在.o把自己的code搬到呼叫它的code裡，而.so檔沒有
    * Generic name: ELF binaries
    * Better support for shared libraries than old a.out formats.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2f5634846c251b7b69e5aca18d6ed934.png)
* gcc -E :把include檔、macro放進去

### ELF Object File Format
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_21b3a1d8a637683b30bec738765fbf6d.png)
* ELF header
    * Magic number(\177ELF), type (.o, exec, .so), machine, byte ordering, entry point, size, etc.
    * 在這裡判斷這個檔案的type，如果是執行檔接下來要去讀Program header table，如果是object file接下來要去讀Section header table
* Program header table
    * Page size, virtual addresses memory segments (sections), segment sizes
* .text section
    * Code（read-Only）
    * 把程式語言的指令變成0和1的binary
* .data section
    * **Initialized** (static) data
* .bss section
    * **Uninitialized** (static) data
    * “Block Started by Symbol”
    * “Better Save Space”
    * Has section header but occupies no space
* .symtab section
    * Symbol table
    * Procedures and static variable names
    * Section names and locations
* .rel.text section
    * Relocation info for .text section
    * Addresses of instructions that will need to be modified in the executable.
    * Instructions for modifying.
    * 有些function寫在別的.c檔裡，就會存在這
* .rel.data section
    * Relocation info for .data section
    * **Addresses of pointer data** that will need to be **modified in the merged executable**.
    * 像下面Link Examle裡的&e對a.c來說就是未知，它存在m.c裡
* .debug section
    * Info for symbolic debugging (gcc –g)

要改某個symbol值的話：
.symtab -> .rel.text -> .text

每個section通常會記成跟它的start point差多少address（相對位址），如此一來可以整塊一起移



### Linking Example
* Code consists of symbol **definitions** and **references**.
重要！！要分清楚
* Each symbol definition has memory address.
* References can be either **local** or **external**.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4dba947ae591e38aeea7921bb21186a7.png)

合併後的樣子
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0a3bad6c643f7105ff7b84bf141cfd3a.png)

### Typical Memory Arrangement
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_06fe8084782d3e863ffe11a8f8caed58.png)
* 通常如果virtual memory是4Ｇ，會有3G給你用，1G不會給你用
* program在compile之後un-initialized data,initialized data,text的size就固定了
### Memory Layout of a Process
* Pieces of a process
    * Text Segment
        * Read-only usually, sharable
    * Initialized Data Segment
        * e.g.`int maxcount = 10;`
    * Uninitialized Data Segment – bss (Block Started by Symbol)
        * **Initialized to 0 by exec**
        * e.g.`long sum[1000];`
    * **Stack** – return **addr, automatic var**, etc.
    * **Heap** – dynamic memory allocation (**malloc**)
```
放全域才會被算進data section，宣告在main或其他function會被放在stack
```

### **Stack & Heap 差別**
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_66142c1e1c561ccb167d4046a144ef34.png)
* value type 的變數, 包括指標變數會放在 stack
* reference type 的變數 (如 string, object) 本身也會放 stack, 然而他的值 (value) 則是放 heap
* box 就是 value types to reference types 的過程, 所以 value 會被放到 heap 中, 而產生一個 object 變數來指向這個 value, 變數指標則是在 stack
* unbox 是  reference types to value types 的過程,  所以原本 object 所指向的值 (heap 中) 會被複製到 stack 中並賦予明確 value type 型別
### Loading Executable Binaries
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_255524a226754bc171e4ec6ddd068283.png)

* symbol table 會存`.text` , `.data` , `.bss`  的virtual memory address.
* 如果symbol table解不開，會放在 `.rel.text`,  `.rel.data` 裡，但是如果都沒有解開，程式就不能運作，一定要全部都解開

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c4e95abc5ffa73f7e2d304a456c27005.png)

* 如果我使用外部的函式，例如`printf`,`malloc`:
    * 用靜態連結的話：會直接像macro一樣把library裡面的binary code寫進`text`區
    * 用動態連結的話：在run的時候才會去找它實際上的binary code，存進`lib*.so`
* 後續的新增記憶體都存在 `lib*.so`，其他區塊都是compile完之後確定大小



### Virtual Memory
* Address translation: Hardware converts virtual addresses to physical addresses via **OS-managed lookup table (page table)**
* 有一些放不進去physical memory的就會被放進disk

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4833c244eaabbc94345220dcb6c1358e.png)


### Virtual Address Spaces
* Processes **share physical pages by mapping in page table**
* Separate Virtual Address Spaces (**separate page table**)
    * Virtual and physical address spaces divided into equal-sized blocks
        * Blocks are called “pages” (both virtual and physical)
    * Each process has its own virtual address space
        * OS controls how virtual pages as assigned to physical memory 
系統控制address transformation

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ee0082a918c13e9e0399d7c65c043a38.png)
Process1的Virtual Page2和Process2的Virtual Page1 share同一塊Physical Page，當其中一個Process要改值，就會複製另一塊Physical Page再改

### Address Translation via Page Table
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_17e8a28728c7df48263eeb37cad46bd2.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_270922667179e2188537fe50fd475db6.png)
* page offset是固定的，而且在virtual和physical上都一樣
* 假設page offset=4K=12bits, virtual address上一個block=4G, physical address上一個block=1G，則VPN有20bits,PPN有30bits
* 那address transformation table 會有2^20個index

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f77cfb058c0a566286e964386a347972.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_17ae23ed7f740218e0fa08711d24a80f.png)

* The translation from virtual memory address to physical address has to be LIGHT fast超級快.
    * **Not** possible to be done by **operating systems**.
    * **Done with hardware support**: **Memory Management Unit (MMU)**
* ‘Most’ modern processors support MMU: Pentium, PowerPC, etc.
* Processors for embedded systems may not support MMU.

#### Example
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_217767e456ec2a1efa6919ba97acd26f.png)

* 可以用 objdump 指令得到更detail的內容，
* 有時候沒有宣告global variable，data還是有可能>0

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c58c32c17d31d42a3023e350864f65c7.png)

### Stack Frame
* When one function is called, one area of memory, called frame or stack frame, is set aside for the function. Each frame contains:
    * Return address
    * Passed parameter(s)
    * Saved registers
    * Local variable(s)
* The stack frame is reclaimed by the system when a function returns.

#### Q: A func calls B func 那是誰會負責push stack frame?
Ans: 都會。
因為Return address, Passed parameter(s), Saved registers是Ａ要push，Local variable(s)是B要push
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_34c02ca544ed8e2f56681c9d3819b59b.png)

* static存在initialized data

### Potential Problem of Local Variables
* Never be referenced after their stack frames are released.
* 這段程式不會有錯，因為**fp的資訊會被fopen存在Heap裡**
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9dafbd3e0f1cd8ba316219d1ca67a376.png)
* 這段有錯，因為vfork後chlid process是share parent process的virtual memory，如果跑的順序是：
    1. (child) f1
    2. (child) f2
    3. (parent) f1
    4. (parent) f2
    
那child 跑完f1,f2後會把他們的stack frame release掉，導致parent process有錯，回到step3，parent process會以為自己還在f1的stack frame裡面

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cfb8ecf3c4b45dc9740c1501aefb305a.png)

### Nonlocal Jumps: setjmp & longjmp
* Powerful (but dangerous) user-level mechanism for transferring control to an arbitrary location
* Objective:
    * Goto to escape from a deeply nested function call!
        * break the procedure call/return discipline
    * Useful for error recovery and signal handling (Ch.10)

### Func: setjmp and longjmp
```
#include <setjmp.h>
int setjmp(jmp_buf env);
```
* Return 0 if called directly; otherwise, it could **return a value val from longjmp().**
* **env** tends to be a **global variable**.
```
int longjmp(jmp_buf env, int val);
```
* longjmp() unwinds the stack and affects some variables.

Parameter: `jmp_buf`
* Definition is machine-dependent.
* Includes **CPU registers, stack pointers**, etc.
#### Example 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5e27eb31e36a5b53377f9ef10326bb5f.png)

### Type Qualifiers in C
* Control over optimization
* const: 
no writes through this variable
* volatile: 
**variable may be modified externally**; no cache through this variable (cache is not guaranteed to contain any previous value)
當我們某些程式片段不希望做最佳化的時候呢？　就要使用 volatile 關鍵字，通常是用在有 multiple threads without using the lock Statement 的時候
* restrict: 
the pointer must be the variable used to access the object it points to(restrict means the source and target arrays **do not overlap**)
restrict 是 C 的關鍵字，只能用來修飾 pointer，目的是協助 compiler 做最佳化
是告知 compiler ，這一個 restrict pointer 是唯一指向 data 的 pointer，
意即程式當中不會透過其他變數 ( pointer,或者直接存取 ) 來 access 此 data，

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_820d442190942f27499bf1639242ae0a.png)
#### Effects on Variables
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9a37caf20b162b39dc49ea1b192d27c7.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_68ac298f8479ce4adfa4ab1ebe4ddc6a.png)
```
gcc test.c -o testjmp
gcc test.c -O2 -o testjmp.opt    //有優化
```
* 如果有優化，automatic var & register var 可以roll back 成原來的狀態
* 優化分為五種： -O0, -O1, -O2, -O3, -Os

### Compiler optimization
* **Automatic and register** variables could be in **CPU** (for reducing access time) or memory
* Volatile variables can be changed by something beyond the control of the program in which it appears, e.g., **threads, signal handlers**
* Values are often indeterminate
    * Normally no roll back on automatic and register variables
    * Variables in momory (e.g., global, static & volatile variables) are left alone when longjmp is executed.
* Portability Issues!

### Potential Problems of Nonlocal Jumps

1. 這是對的
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ef7388d49d18c72a9ebf6c28c2b9f5a5.png)

2. 這是錯的 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8a3e31fb87eb0108679afba602506f22.png)

### Shared Library vs. Static Library
* A program usually calls standard C/C++ library, POSIX functions, etc.
* The binary codes of the pre-compiled function call have to be linked with the program.
* Static library:
    * the library and program are complied into one file.
    * **In Linux, static library ends with .a**
        ex: `libc.a`
* Problems:
    * When the **library is updated, the program has to be re-linked**.
    * The file size will be large. Potential for duplicating lots of common code in the executable files on a filesystem.

### Shared Library
* **Shared libraries (dynamic link libraries**, DLLs) whose members are dynamically loaded into memory and linked into an application at run-time.
放在`lib*.so`
* Why a shared library?
    * Remove common library routines from executable files.
    * Have an easy way for upgrading
* Problems
    * More **overheads**: dynamic linking
    * 會跑去stack和heap中間執行，所以不能用relocation
* gcc:
    * Searches for shared libraries first.
    * **Static linking** can be forced with the **`-static`** option to gcc to avoid the use of shared libraries.
    * default都是動態連結。
* Supported by many Unix systems
> 有用shared library的話，compile完的東西不能有relocated的東西

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b4d07a8a6496f435ea4968ffbb80d7f2.png)


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4bc33cea95664452c30f450f7148a619.png)
沒用shared library檔案很大

### Memory-mapped I/O (Ch. 14.9)
* mmap() maps a file on disk into a buffer
in memory
* When we f**etch bytes from the buffer**, the corresponding bytes of the file are **read**.
* When we **store data in the buffer**, the corresponding bytes are **written**
* This lets us **perform I/O without using read/write or fscanf/fprintf.**
    * Kernel − our buffer
用UnbufferedIO，在output的時候就會需要在kernel的buffer cache和該process的virtual memory(userspace)的buffer轉移data
    * Kernel − standard I/O buffer − our buffer
    用bufferIO

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_30027a014f8a2070b1f867ae2a88c96b.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a3b0c408425c356263d44e3d5d505e10.png)
#### Example
實作用mmap複製檔案
* 用`fstat(fdin, &statbuf)`得到fdin長度
* 用`lseek`將fdout(目前為空)的讀寫位置移到fdin長度-1，在`write`一個字（1byte）上去，這樣fdin和fdout的size就一樣了
* Prototype:
`void *mmap(void *start,size_t length, int prot, int flags, int fd, off_t offsize);`

    * 參數start：指向欲映射的核心起始位址，通常設為NULL，代表讓系統自動選定位址，核心會自己在進程位址空間中選擇合適的位址建立映射。
映射成功後返回該位址。如果不是NULL，則給核心一個提示，應該從什麼位址開始映射，核心會選擇start之上的某個合適的位址開始映射。
建立映射後，真正的映射位址通過返回值可以得到。
    * 參數fd：由open返回的文件描述符，代表要映射到核心中的文件。如果使用匿名核心映射時，即**flags中設置了MAP_ANONYMOUS，fd設為-1**。
    * `mmap`做的事就是把`fd`文件映射到`start + offsize`的位址，映射長度為`length`
    
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8ac1800b73356d754a923db993f08771.png)



### Memory Allocation(在Heap)
其實malloc函式會去呼叫一個叫做`sbrk`system call，如果我malloc 100 bytes，為了以後不用一直sbrk，他會一次用sbrk跟系統要4G的記憶體（數字不重要只是一種表達）
* Three ANSI C Functions:
    * **malloc** – allocate a specified number of bytes of memory. Initial values are indeterminate.
    * **calloc** – allocate a specified number of objects of a specified size. The space is initialized to all 0 bits.
    * **realloc** – change the size of a previously allocated area. The initial value of increased space is indeterminate.

```
#include <stdlib.h>
void *malloc(size_t size);
void *calloc(size_t nobj, size_t size);
void *realloc(void *ptr, size_t newsize);
```
* **Suitable alignments for any data object**
* Generic void * pointer 所以我們才用`(int*) ptr = (int*)malloc`
* free(void *ptr) to release space to a pool.
* Leaking problem 用了malloc沒有free
    * allocated memory that program no longer references.
* Free already-freed blocks or blocks not from alloc().
    * `mallopt`, `mallinfo`

### Remark
* realloc() could trigger moving of data -> avoid pointers to that area!
    * ptr == NULL -> malloc()
    * 注意ptr可能換了
* `sbrk()` is used to expand or contract the heap of a process – a malloc pool
(可以拿來用或放回去，很強大) 
* Record-keeping info is also reserved for memory allocation – do not move data inside.
* `alloca()` allocates space from **the stack frame of the current function!**
    * **No needs for free** with potential portability problems
    * 它在stack上所以不需要free

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_00845fa4d73eb308b50568df6c1db14b.png)
* 前面會有一個block紀錄malloc的長度，所以我們free的時候不需要輸入長度

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7246da950e3f99e15214f2116bde56af.png)

### Environment Variables
* Name=value
    * Interpretation is up to applications.
        * Setup automatically or manually
        * E.g., HOME, USER, MAILPATH, etc.
        setenv FONTPATH $X11R6HOME/lib/X11/fonts
```
#include <stdlib.h>
char *getenv(const char *name);
```
* ANSI C function, but no ANSI C environment variable.
`int main(int agrc, char **argv, char **envp);`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_238ac563f45713534bad516c87eed5ff.png)
* 當我用putenv寫東西進去environment list 因為它list原本位置的size有限，所以list**會整個搬進Heap**，此時`extern char ** eviron`指向位置依舊正確，但`char** envp`指向的位置會錯

```
#include <stdlib.h>
int putenv(const char *name-value);
```
* Remove old definitions if they exist.
```
int setenv(const char *name, const char *value, int rewrite);
```
* rewrite = 0 -> no change on existing values.
* rewrite > 0 -> overwriting existing values.
```
int unsetenv(const char *name);
```
* Remove any def of the name
* No error msg if no such def exists.

### Adding/Deleting/Modifying of Existing Strings
* Modifying
    * The size of a new value <= the size of the existing value -> overwriting
    * Otherwise; malloc() & redirect the ptr
* Adding
    * The first time we add a new name -> malloc of pointer-list’s room & update envron
    * Otherwise; copying. realloc() if needed.
* The heap segment could be involved

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f916a0875b33b097dfb878d819f62650.png)

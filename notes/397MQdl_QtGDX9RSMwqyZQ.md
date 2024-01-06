# User Mode vs. Kernel Mode
User mode: a non-privileged mode in which processes are forbidden to access those portions of memory that have been allocated to the kernel or to other programs.

When a user mode process wants to use a service that is provided by the kernel (e.g. a system call), the system must switch temporarily into kernel mode.

System memory is divided into two parts 
- User space 
    - a process executing in user mode is executing in user space
    -  each user process is protected (isolated) from another (except for shared memory segments and mmapings, which will be discussed later) - 
- Kernel space 
    - a process executing in kernel mode is executing in kernel space 

Kernel space is the area wherein the kernel executes user space is the area where a user program normally executes, except when it performs a system call.



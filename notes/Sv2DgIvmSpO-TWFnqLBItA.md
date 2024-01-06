# [SP] Basic  OS Concepts
Physical device -> Microarchitecture -> Machine language |hardware| ->Operating System Compiler,Editor,command interpreter |System program|->browser,financial system |application program|

# What is OS
Vertically view (extended machine)
 
- Present user with a VM. (Establish UI)
- Hides the messy detail (Provide **safety**) 

horizontally view (resource manager)
- There are some resource: CPU, memory, I/O
- Each program gets time and space by resource.
- OS makes sure programs have a **fair** use 

# UNIX architecture


| Level | feature| example |
| -------- | -------- | -------- |
| Kernal | boot, system initialization | Column 3 |
| System calls   | Text     | Text     |
| Shell     | Text     | Text     |
| library routines     | Provide pre-compiled object code     | <stdio.h>     |
| Apllication     | Text     | Text     |
 
 # User mode VS Kernal mode
 Most CPU support at least two modes of execution.
 - **User mode**: Non-privileged, in which process are forbidden to access those portions of memory that have been allocated to the kernal or to other programs. (In some system call for example, open(), the system must switch temporarily into kernal mode.)

- User Space: a process executing in user mode is executing user space. Each user process is protected (isolated) from another (Except for shated memory segments mapping) 
- Kernal space: a process executing in kernal mode is executing kernal space. It's the area where in the kernal executing in kernal space. So does User space. They only switch when system call.

# Time
real: enter to end
user: run in user mode
sys: run in kernal mode

# User identity

# processing

- Ready Queue: CPU never access disk(it's too slow), so the program in ready queue **must** in memory!!
# Systems Programming (Fall, 2020) Assignment 1 (Due on 10/7, in class)

### 1. File Redirection.
#### (a) Please give the meaning of the command:
```
./a.out < infile 2>&1 > outfile`
```
Ans:
1. sets “standard input” to “infile”  (equivalent to` 0 > infile`)
2. redirects “standard error” to “standard output”
3. sets “standard output” to “outfile”
(equivalent to `1 > outfile`)

"a.out" reads the input messages from "infile".
Since “standard error” is set to “standard output” before “standard output” is set to “outfile”, error messages are shown on terminal while output messages are written to "outfile".

#### (b) Please use dup() or dup2() to do the redirections of the command 
```
./a.out < infile 2>&1 > outfile`
```
#### in the following program fragment. Error checking could be ignored.
Ans:
```
int main(int argc, char *argv[]) {
    int fd1, fd2;
    fd1 = open (infile,O_RDONLY );
    fd2 = open (outfile, O_WRONLY | O_CREAT, 0666);
    // do the redirections here
    
    dup2(fd1, STDIN_FILENO);
    close(fd1);
    dup2(STDOUT_FILENO, STDERR_FILENO);
    dup2(fd2, STDOUT_FILENO);
    close(fd2);
    
    
    execlp(“./a.out”, “./a.out”, (char *)0); 
    return 0;
}
```

### 2.	Atomic operation.
#### (a) Should		the		write_to_fd()		function		be		an		atomic		operation?		Please		give		an		example		to		clearly explain		your		answer. 
Ans: Yes, it should be an atomic operation.
Example:
```
    pid_t pid;
    // 建立子行程
    pid = fork();
    if (pid == 0) {
        // 子行程
        write_to_fd(fd, buf1, 5, 100);
    } else if (pid > 0) {
        // 父行程
        write_to_fd(fd, buf2, 10, 200);
    } else{
        //error...
    }
```
If `write_to_fd()` is not atomic, the situation may become:
```
1.(parent)     lseek(fd,100,SEEK_SET)
2.(child)      lseek(fd, 200, SEEK_SET);
3.(parent) 	write(fd,buf1,5);
4.(child) 	write(fd,buf2,10);
```
Since `write_to_fd` accepts the file descriptor straightly, the two processes point to the same system-wide file table entries. 
In the case above, `lseek(...)` in the child process simultaneously change the offset in the parent process. And then for step3, data from buf1 will be written to a wrong position, causing some error.
Hence, `write_to_fd()` should be atomic to avoid the problem.

#### (b) Should		the		write_to_fn()		function		be		an		atomic		operation?		Please		give		an		example		to		clearly explain		your		answer.
Ans:
No, there is no need for the function `write_to_fn `to be an atomic operation.
Example:
```
    pid_t pid;
    // 建立子行程
    pid = fork();

    if (pid == 0) {
        // 子行程
        write_to_fn(fn, buf1, 5, 100);
    } else if (pid > 0) {
        // 父行程
        write_to_fn(fn, buf2, 10, 200);
    } else{
        //error...
    }
```
Because the parameter of `write_to_fn` is file name, the two processes open the file with different system-wide file table entries. The writing operation in one process doesn’t affect the offset in another process. Hence, it's okay if `write_to_fn` is not an atomic function.
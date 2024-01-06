sp
國立中正大學資訊工程學系
一百學年度系統程式期末試卷
**1. Distinguish between the following.                            (12%)**
a. pipe vs. FIFO
b. fork()    vs.   vfork()
c. exit()     vs.   _exit()
d. fclose()   vs.   close()
e. execvp()  vs.   execle()
f. longjum()  vs.  siglongjump()
2. Is the following piece of code correct? If not, what is wrong? Draw a memory layout diagram to illustrate the result of executing this program.    (12%)
   int genchild(){
			pid_t pid;
			if((pid=vfork())<0)
					err_sys(“vfork error”);
			else if(pid==0){
					printf(“I am the child: %d.\n”,getpid());
					return(0);
}
else{
		wait(NULL);
		printf(“I am the parents: %d\n.”,geypid());
}
}
int main(){
		genchild();
		return(0);
}

3.Explain what the following code does. Is there anything wrong in it? If yes, how to correct the problem…                                     (10%)
				1. sigset_t sigmost;
				2. int signum= SIGUSR1;
				3. sigfillset(&sigmost);
  			4. sigdelset(&sigmost, signum);
				5. sigsuspend(&sigmost);
4.Answer ANYEIGHT(8) of the following questions briefly. Extra correct answers will be given BONUS points.                                   (56%)

	a. What is a reentrant function? Why should a signal handler be reentrant?
b. Are the value of automatic, register, and volatile variable all rolled back after 
longjump()? If not, which are and which are not? Under what condition are they 
rolled back?
  c. Explain how you can write a program to create a zombie process.
  d. For a process, suppose the real user ID is 805 and the saved set-user-ID is
 currently 902, what values can the effective user ID be set to? Can we change
 the saved set-user-ID manually? If yes, how? If no, why not?
  e. Explain how you can synchronize the order of executions of parent and child
    processes?
  f. What is the difference between standard I/O cleanups performed in the following two ways : fclose(student) and exit().
  g. What is the use of the saved set-user-ID? Give an example to illustrate your answer.
  h. What is the difference between alloca() and malloc()? When is alloca() not recommended? When is it recommended?
  i. Can signal handling be nested? If yes, give an example program in which signal handling is nested. If no, explain why not.
  j. Can we use standard I/O library function such as fgets() in a co-process? If yes, how? If not, why not?
  k. What is a co-process? How does it differ from a filter? If we want to use a co-process in our program to show us the current news, which API function should we invoke?
  l. How can we solve the race condition problem between alarm() and pause()?

5.Draw a memory layout diagram for a typical C program. Label each part clearly. (10%)

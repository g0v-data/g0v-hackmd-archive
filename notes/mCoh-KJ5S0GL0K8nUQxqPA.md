# 作業一程式碼
```c=
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <fcntl.h>
#include <sys/stat.h>
#include <sys/mman.h>

/*
    ！！！！！！！！！！！！！！！！！！！IMPORTNAT!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
    我一開始跑得時候有error顯示shm_open undefined, 後來查發現指令要加上-lrt才行（以下為官方文件內容)
    Programs using these functions must specify the "-lrt"  flag to cc in order to link against the required ("realtime") library.
    ex:  gcc -o hw1_3 hw1_3.c -lrt

    不知道對作業繳交有沒有影響但還是告知一下
*/

int main(){
    const int SIZE = 4096;
    const char *name = "os";

    int shm_fd;
    int *ptr;

    //creat shear memory
    shm_fd = shm_open(name, O_CREAT | O_RDWR, 0666);   
    ftruncate(shm_fd, SIZE);
    ptr = mmap(0, SIZE, PROT_WRITE, MAP_SHARED, shm_fd, 0);

    pid_t pid;
    pid = fork();
    if(pid < 0){            //error occured
        fprintf(stderr, "Fork Failed\n");
        return 1;
    }
    else if(pid == 0){      //child process
        ptr = mmap(0, SIZE, PROT_WRITE | PROT_READ, MAP_SHARED, shm_fd, 0);
        char *input;
        printf("child process\n");
        printf("Please input a positive integer(this is 1.3)\n");
        scanf("%[0-9]", input);
        int a  = atoi(input);

        while(a <= 0 || (int)a != a){
            printf("You have a wrong enter, please input a positive integer again!\n");
            scanf("%d", &a);
        }

        int *output_c = ptr;
        while(a != 1){
            *output_c = a;       //storage the number into share memory
            if(a % 2 == 0)
                a /= 2;
            else
                a = 3 * a + 1;            
            output_c++;
        }
        *output_c = a;
        printf("child process calculating...\n");
    }
    else{                  //parrent process
        ptr = mmap(0, SIZE, PROT_READ , MAP_SHARED, shm_fd, 0);
        wait(NULL);
        printf("child complete\n");

        int *output_p = ptr;     //read the number from shear memory
        int number;
        number = *output_p;

        while(number >= 1){      //print the number calculated in child process
            printf("%d ", number);
            output_p++;
            number = *output_p;
        }
        printf("\n");
    }

    shm_unlink(name);

    return 0;

}
```



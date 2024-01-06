# 作業系統hw2_1
```c=
#include <pthread.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int *sequence;
void *fibonacci(void *param);

int main(int argc, char *argv[]){
    pthread_t tid;
    pthread_attr_t attr;

    if (argc != 2){
        printf("You have the wrong input\n");
        return -1;
    }
    if (atoi(argv[1]) <= 0){
        printf("Please enter a positive integer\n");
        return -1;
    }    

    pthread_attr_init(&attr);
    pthread_create(&tid, &attr, fibonacci, argv[1]);
    pthread_join(tid, NULL);
    
    int n = atoi(argv[1]);
    printf("%d\n", n);
    for (int i = 0; i < n; i++){
        printf("%d ", sequence[i]);
    }

    return 0;

}

void *fibonacci(void *param){
    int amount = atoi(param);
    sequence = malloc(sizeof *sequence * amount);
    sequence[0] = 0;
    sequence[1] = 1;
    for (int i = 2; i < amount; i++){
        sequence[i] = sequence[i-2] + sequence[i-1];
    }

    pthread_exit(0);
}
```

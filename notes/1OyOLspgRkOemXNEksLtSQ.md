# 作業系統hw2_2
```c=
#include <pthread.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

double pi;
void *monteCarlo(void *param);

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
    pthread_create(&tid, &attr, monteCarlo, argv[1]);
    pthread_join(tid, NULL);
    
    printf("Final Estimation of PI = %f\n", pi);

    return 0;

}

void *monteCarlo(void *param){
    int interval = atoi(param); 
    double rand_x, rand_y, origin_dist; 
    int circle_points = 0, square_points = 0; 
  
    srand(time(NULL)); 

    for (int i = 0; i < (interval * interval); i++) { 
  
        rand_x = (double)(rand() % (interval + 1)) / interval; 
        rand_y = (double)(rand() % (interval + 1)) / interval;

        origin_dist = rand_x * rand_x + rand_y * rand_y; 
  
        if (origin_dist <= 1) 
            circle_points++; 
  
        square_points++; 
   
        pi = (double)(4 * circle_points) / square_points; 
    }    

    pthread_exit(0);
}
```
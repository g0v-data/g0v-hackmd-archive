# 作業系統hw3_2
```c=
#include <pthread.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int point_in = 0;    //total amount points in the circle
int point_out = 0;   //total amount points in the square
void *monteCarlo(void *param);
pthread_mutex_t mutex;

int main(int argc, char *argv[]){
    pthread_t t1, t2, t3, t4, t5;
    pthread_attr_t attr;
    pthread_mutex_init(&mutex, NULL);

    if (argc != 1){
        printf("You shouldn't have any input\n");
        return -1;
    }  

    pthread_attr_init(&attr);
    pthread_create(&t1, &attr, monteCarlo, "1000");
    pthread_create(&t2, &attr, monteCarlo, "1000");
    pthread_create(&t3, &attr, monteCarlo, "1000");
    pthread_create(&t4, &attr, monteCarlo, "1000");
    pthread_create(&t5, &attr, monteCarlo, "1000");
    pthread_join(t1, NULL);
    pthread_join(t2, NULL);
    pthread_join(t3, NULL);
    pthread_join(t4, NULL);
    pthread_join(t5, NULL);
    
    double pi = 4*point_in*1.0 / point_out;
    printf("interval = %s\n", "1000");
    printf("total circle_point = %d\n", point_in);
    printf("total square_point = %d\n", point_out);
    printf("Final Estimation of PI = %f\n", pi);

    return 0;

}

void *monteCarlo(void *param){
    int interval = atoi(param); 
    double rand_x, rand_y, origin_dist; 

    pthread_mutex_lock(&mutex);
    //enter critical section
    int circle_points = point_in, square_points = point_out;  
    srand(time(NULL)); 
    for (int i = 0; i < (interval); i++) { 
  
        rand_x = (double)(rand() % (interval + 1)) / interval; 
        rand_y = (double)(rand() % (interval + 1)) / interval;

        origin_dist = rand_x * rand_x + rand_y * rand_y; 
  
        if (origin_dist <= 1) 
            circle_points++; 
  
        square_points++; 
    }    
    point_in = circle_points;
    point_out = square_points;
    pthread_mutex_unlock(&mutex);
    //leave critical section
    printf("circle_point in one thread = %d\n", circle_points);
    printf("square_point in one thread = %d\n", square_points);

    pthread_exit(0);
}
# Chapter 6 / Synchronization

## 6.1 Background

什麼是Synchronization？
簡易例子：**producer-consumer problem**
在share date且是bounded buffer情況下即有可能產生Synchronization的問題

**Producer Code：**

```cpp=
while(true)
{
    while(counter == BUFFER_SIZE);
    
    buffer[in] = next.produced;
    in = (in + 1) % BUFFER_SIZE;
    counter++;
}
```

**Consumer Code：**

```cpp=
while(true)
{
    while(counter == 0); //沒有內容可以消耗
    
    next.consumed = buffer[out];
    out = (out + 1) % BUFFER_SIZE;
    counter--;
}
```

如果在Producer的counter++或是Consumer的counter--的執行過程中被打斷（還沒將正確的數值寫回記憶體）此時就會產生synchronization的問題。且**執行到最後的counter數值會依著誰先開始執行、和最後而決定，稱為race condition。**

**<補充 race condition：多個thread嘗試同時訪問和修改相同數據時的結果>**

如何解決Synchronization問題？
Ans：**定義Critical Section。**

## 6.2 TheCritical Section Problem

The Critical Section Problem：提供對共享變數之存取的互斥控制，確保資料的正確性。定義以下四項
- entry section（存取共享變數的依據條件）
- critical section（共享的變數）
- exit section（離開保護的變數範圍）
- remainder section（非共享的變數）
```cpp=
do{
    //Entry Section
        critical section
    //Exit Section
        remainder section    
}while(true);
```

Critical-Section Problem的解決有三大重點
- **Mutual exclusion**
同時間只能有一個process在critical section裡面執行。
- **Progress**
不允許在沒人使用（沒人在critical section裡面時，有人想用（假設是P1），卻不讓他使用（不讓P1進入critical section）。
- **Bounded waiting**
一個process想要進入critical section，此時有人在裡面，外面想進入的不能無限期等待。

而若critical section是作用於kernal時，兩種風法式依據kernel是否可搶奪或不可搶董
- preemptive
- non-preemptive

## 6.3 Peterson's Solution（Software solution）
在假定load和store兩個instruction是atomic（即不會被打斷），以兩個process為例子，此Algorithm使用的變數
- int turn ：當turn數值為0，代表P0可以進入critical section，為1，代表P1可進入
- boolean falge[2] ：用來記錄是否進入critical section

```cpp=
do{
    while(turn != i);
      //critical section
    turn = j;
        //remainder section
}while(1)
```

```cpp=
do{
    flag[i] = true;
    flag[j] = true;
    while( flag[j] );
    while( flag[i] ); 
}while(1)


```

```cpp=
do{
    falge[i] = true;
    turn = j; //此Algorithm較特別，想進入CS的process會先遷讓
    
    while(falge[j] && turn == j); //對方不用的話我自己就進入CS
        //critical section
    falage[i] = false;
        //remainder section
}while(1)
```

接著我們驗證此演算法是否符合critical section三大準則，以下證明：
1. Mutual exclusion 合格!
若 Pi 與 Pj 皆想進入自已的 C.S.，代表 flag[i] = flag[j] = true，而且會分別執行到 turn = i 及 turn = j 之設定，只是先後次序不同，turn 的值僅會是 i 或 j，絶不會兩者皆是。
2. Progress 合格!
若 Pi 不想進入 C.S.，則表示 flag[i] = false。此時若 Pj 想進入自已的C.S.，必可通過 **while(flag[i] and turn = i) do no-op** 這個空迴圈而進入其 C.S.，不會被 Pi 阻礙。
若 Pi 與 Pj 皆想進入自已的 C.S.，則在有限的時間內，Pi 與 Pj 會分別執行到 turn = i 及 turn = j 之設定 (只是先後次序不同)，turn 値必為 i 或是 j。因此 Pi (或 Pj) 會在有限的時間內進入自已的 C.S. (No Deadlock)。
3. Bounded-waiting 合格!
Pi 離開 C.S. 後又企圖立刻進入自已的 C.S.，此時 Pi 一定會執行 turn = j，使得 Pi 無法再搶先於 Pj 進入自已的 C.S.。所以 Pj 至多等待一次即可進入 C.S.。


```cpp=
#include<stdio.h>
#include<stdlib.h>
#include<pthread.h>
#define true 1
#define false 0
typedef int bool;
bool flag[2];
int turn;
void visit(int num)
{
        sleep(1);
        printf("P%d is visting\n",num);
}
void P0()
{
        while(true)
        {
                flag[0] = true;//P0想進入Critical Section。
                while(flag[1])//檢查P1是否也想進入
                {
                        if(turn == 1)//如果P1想進入，查看是否有訪問權力
                        {
                                flag[0] = false;//如果P1有權力，P0放棄
                                while(turn == 1);//檢查目前權力是否在P1
                                flag[0] = true;//P0想使用
            
                        }

                }
                  visit(0); //訪問Critical Section
                turn = 1; //P1訪問完成，讓給P0。
                flag[0] = false; //P1结束使用。
        }
}

void main()
{
        pthread_t t1,t2;
        flag[0] = flag[1] = false;
        turn = 0;
        int err;
        err =  pthread_create(&t1,NULL,(void*)P0,NULL);
        if(err != 0) exit(-1);
        err = pthread_create(&t2,NULL,(void*)P1,NULL);
        if(err != 0 ) exit(-1);
        pthread_join(t1,NULL);
        pthread_join(t2,NULL);
        exit(0);
}
```



## 6.3~Bakery Algorithm（PPT補充演算法）
在有n個process的狀況下可以使用。每個process給予號碼牌。

使用變數
- num[i] 第i個prcoess抽的號碼牌號碼
- choosing[i] 第i個process是否想進入CS 

```cpp=
do{
    choosing[i] = true;
    num[i] = max(num[0], num[1],...,num[n-1]) + 1; 
    //想要進入CS的process先抽號碼牌排隊
    choosing[i] = false;
    for(int j = 0 ; j < n ; j++)
    {
        while(choosing[j]);
        while((num[j] != 0) && ((num[j],j) < (num[i],i));
        //即檢查n個執行緒中，自己是否具有最小的非0排隊簽到號碼
        //或者自己是具有最小的非0排隊簽到號碼的執行緒中，pid號最小的
    }

        //critical section

        
    num[i] = 0; //release


        //remain section
        

}while(1);

```


## 6.4 Synchronization Hardware
通過要求臨界區用鎖來防護，就可以避免競爭條件，即一個程序在進入臨界區之前必須得到鎖，而其退出臨界區時釋放鎖。而硬體提供支援來解決Synchronization問題的指令，這些基於硬體支援的指令其根本原理為locking，且都具有不能被打斷（atomically）的特性，有兩種基本指令如下:

1. test_and_set()
```cpp=
boolean test_and_set(boolean *target)
{
    boolean rv = *target;
    *target = true;
    
    return rv;
}
```

**實作code：**
```cpp=
do{
    while(target_and_set(&lock)); //回傳true表示現在有人在CS裡面，要等待
    
        //Critical Section
    
    lock = false; //使用完，release lock
    
        //Remainder Section 
         
}while(true);
```

2. compare_and_swap()

```cpp=
int compare_and_swap(int *value, int expected, int new_value)
{
    int temp = *value;
    
    if(*value == expected)
    {
        *value = new_value;
    }
    
    return temp;
}
```

實作code：
```cpp=
do{
    while(compare_and_swap(&lock, 0, 1) != 0); //我想進入CS，所以期待lock為0，這樣我就能進去
    
        //ciritical section
    
    lock = 0;
    
        //remainder section
        
}while(true);
```

## 6.5 Mutex Locks

這是一種programmer可以使用軟體的方式，利用acquire()和release()取用lock（皆為atomic
），但是**如果取不到lock的話，就會進入busy waiting。所以Mutex Locks也被稱為Spinlock，因為當process在等待lock變成available時是spins的**。但此方法也是有優點，不用context switch。

**核心概念：在每一次想要進入critical section前先acquire() lock。結束則release() lock。**

```cpp=
acquire(){
    while(!available); //busy wait
    available = false; //拿到lock，換我使用了，所以把lock鎖起來，不讓別人使用
}

relase(){
    available = true; //釋放lock，讓別人使用
}

//概念

do{
    acquire();
    
        //critical section
    
    release();
    
        //remainder section

}while(true);
```

## 6.6 Semaphores
是一個同步物件，用於保持在 0 至指定最大值之間的一個計數值。其類似於 mutex lock 但更加複雜，且**不會有busy waiting（因為使用waiting queue）**。Semaphore S是一個**integer variable**。除了要初始化外，它只能利用wait()（P = proberen）和signal()（V = verhogne）來access。

**S的值只能在wait()或signal()裡面做更改，即不能有同時兩個process可以對其做更動。**

使用規則：
- 當執行緒完成一次對該 semaphore 物件等待 (wait(S) / P(S)) 時，該計數值 S-1；
```cpp=
wait(S){
    while(S == 0); //busy wait
    S--;
}
```
- 當執行緒完成一次對semaphore 物件釋放 (signal(S) / V(S)) 時，計數值 S+1。
```cpp=
signal(S){
    S++;
}
```
- 當計數值為 0，即能使用的額度已用完，則執行緒等待該 semaphore 物件直至該 semaphore 物件變成 signaled (>0)狀態。

**<注意>**
把wait()和signal()放入critical section，但這樣就有可能產生busy waiting。為了不要有busy waiting，會將所有的semaphore(有value跟pointer)連成一個waiting queue。
而waiting queue有兩種執行方式：block(process放入waiting queue)跟wakeup(process移出waiting queue，放入ready queue)。


### 6.6.1 Semaphore Usage（用法）
semaphore分為兩種：
1. counting semaphore：可用做在給定的資源下控制有多少的process能夠存取它。
2. binary semaphore。Binary semaphore和mutex locks。

例子：


### 6.6.2 Semaphore Implementation
使用system call等級的**block()** 和 **wakeup()** 來實作Semaphore，不讓process進入busy waiting。實作方法為：準備一個waiting queue，此queue可以利用linking list來實作。
等待程序的連結串列可以利用程序控制塊PCB中的一個連結域來加以輕鬆實現。即每個訊號量包括一個整型值和一個PCB連結串列的指標

```cpp=
typedef struct{
    int value;
    struct process *list;
} semaphore;

wait(semaphore *S){
    S -> value--;
    if(S -> value < 0)
    { //額度都用完了
        add this process to S -> list; //process進入waiting queue裡等待
        block();
    }
}

signal(semaphore *S){
    S -> value++;
    if(S -> value <= 0)
    {
        //執行完上述之後，S仍然小於等0，代表waiting queue裡等待的人還是很多，幫助喚醒
        remove this process P from S -> list;
        wakeup(P);
    }
}
```

### 6.6.3 Deadlocks and Starvation



### 6.6.4 Priority Inversion
當有一個high priority的process想要使用某資源，但是此資源正被low priority的process佔用著。而因為部分kernel data都會被lock保護著，導致high priority的process只能等待lower priority的完成並釋放此資源。此情況即稱為priority inversion。

而當遇到具有preempted特質的情況時會更為複雜。

**<例子>**

假設有process L、process M、process H。priority高低為L<M<H。如果在H想要用特定資源R時，L正在使用R。M此時開始runnable，將資源R從L那邊搶走。影響了H等待的總時間。

**解決辦法：priority-inheritance protocol。**

L繼承H的priority，不被M搶奪，等到L處理完後資源就順勢給了H，L的priority也恢復原本。

## 6.7 Classic Problems of Synchronization

### 6.7.1 The Bounded-Buffer Problem

### 6.7.2 The Reader-Writers Problem

### 6.7.3 The Dining-Philosophers Problem

## 6.8 Monitors








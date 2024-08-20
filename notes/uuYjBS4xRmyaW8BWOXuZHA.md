# memory

* %p: format code (shows a address in oppose to integer)
input ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5d2dac6f905e6f69bb410800767e77df.png)
output![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7d5063791ddcfd93cf64f5ce21731356.png)



* hexadecimals:
 Base 16 byte , Uses 16 digits (0-9 and A-F) to represent numbers.   
Common in computing: Used for representing colors, memory addresses, and other data.   
Examples: FF, 2A, 100

>* pointers: the address of some variable(whom can even be store in another variable)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_db4237ecda1bdb4bea558e569546c522.png)
>### Understanding the Roles of & and *
>**& :(address-of operator):** This operator is used to get the memory address of a variable.
> **(*) :(dereference operator):** This operator is used to access the value stored at the memory address pointed to by a pointer.
>####  "int* "meaning: go to that actual position
>
>
>### string = char *
>![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b12b8dde16fe238b96995e03c45bcbe5.png)
從第一個指向第二....連續操作直到碰到NULL(/0)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6b19e449f25a5dc114397b3852fb9ae6.png)

---
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9b0af659b4da239e6fda0150a369a1e8.png)
read it like this: 
-->"u make a datatype called node" with the syntex of struct(ex: int X)
int X = children[26]
string = number
------> this define how "node" works
*  *(s+1) = s[1]
*  ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_70ad5a7937cb5e89b38c9280805b8186.png)
* strcpy: define to <string.h>, copy one string to another
ex: strcpy(t, s); ________>copy s into t
____
valgrind ./code     == degugging
____
### swap the value of 2 variables
tmp(temporary) is like a third empty bowl that make the swap works
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ff7d6b9fc49f7be736fedd9f603ed265.png)
互換a,b:
把a裝進tmp(temporary) -> (現在a空了)把 b 裝進a  -> 把tmp裡的a裝回b

### 使用箭頭>
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_36aa7b72abba2b860f2b3b361c614062.png)

----
## overflow
### heap overflow:
### steak overflow:
* buffer overflow: 
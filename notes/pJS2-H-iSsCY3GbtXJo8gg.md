# lab1 
#### que1
g++ -O0 -o astO0.out ast.cpp
The difference between compiling with -O0 and -O3 is that -O0 applies no optimization, resulting in a larger binary and potentially slower runtime, while -O3 applies aggressive optimizations to reduce the binary size and improve runtime performance.

| Compiler Optimization | Binary Size | Average Runtime |
|-----------------------|-------------|-----------------|
| `-O0`                 | 18k   | 0 seconds   |
| `-O3`                 | 17k      | 0 seconds    |


### ques2
The difference in runtime for the second question might be less noticeable compared to the first, as the print operation might dominate the time consumed. However, -O3 will still likely be faster than -O0, even with the print statement.


| Compiler Optimization | Binary Size | Average Runtime |

|      `-O0`               |  174868         |100000000|
   
| `-O3`                 |    332650   |  100000000|
 
### ques3
![](https://g0v.hackmd.io/_uploads/Hk8KOVH_Jx.png)

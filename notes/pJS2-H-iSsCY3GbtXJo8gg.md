# lab1 
#### que1
g++ -O0 -o astO0.out ast.cpp
The difference between compiling with -O0 and -O3 is that -O0 applies no optimization, resulting in a larger binary and potentially slower runtime, while -O3 applies aggressive optimizations to reduce the binary size and improve runtime performance.

| Compiler Optimization | Binary Size | Average Runtime |
|-----------------------|-------------|-----------------|
| `-O0`                 | 3.2 MB      | 1.25 seconds    |
| `-O3`                 | 2.4 MB      | 0.85 seconds    |



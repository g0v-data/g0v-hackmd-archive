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

### ques4
Array: Elements are stored one after the other, so accessing and going through them is fast.
Linked List: Each element points to the next, so you have to follow pointers, which makes it slower to go through.
Main Difference: Arrays are faster to traverse because they’re stored in a single block of memory, while linked lists are slower due to scattered memory and the need to follow pointers.
Measuring traversal times...
Static array traversal time: 0 microseconds
Sum (array): 165075799
Linked list traversal time: 0 microseconds
Sum (linked list): 165168569

### ques5
uint32_t function_x(uint64_t i)// Function takes a 64-bit unsigned integer as input and returns a 32-bit unsigned integer.
{
    i = i - ((i >> 1) & 0x5555555555555555);  // Step 1: Subtract pairs of bits. `i >> 1` shifts `i` right by 1, and `& 0x5555555555555555` isolates alternate bits. This operation calculates the popcount for every pair of bits.
    
    i = (i & 0x3333333333333333) + ((i >> 2) & 0x3333333333333333);  // Step 2: Sum up counts for adjacent pairs of bits. `i & 0x3333333333333333` isolates 2 bits at a time, and `i >> 2` shifts it by 2 to sum adjacent pairs.
    
    i = (i + (i >> 4)) & 0x0f0f0f0f0f0f0f0f;  // Step 3: Sum the counts of pairs within 4-bit groups. `(i >> 4)` shifts `i` by 4 bits, adding the 4-bit chunk counts together. The mask ensures the result remains within each 4-bit section.
    
    i = i + (i >> 8);  // Step 4: Further aggregate counts by shifting `i` by 8 bits, adding the 8-bit groups together.
    
    i = i + (i >> 16);  // Step 5: Shift `i` by 16 bits and add to `i`, summing the counts for 16-bit sections.
    
    i = i + (i >> 32);  // Step 6: Finally, shift `i` by 32 bits, summing the 32-bit sections.
    
    return (uint32_t)i;  // Final step: Cast the 64-bit result to a 32-bit integer and return it. The result contains the number of 1-bits in `i`.
}
#### ques6
Runtime Comparison Explanation:
Software Popcount (function_x):

Time Complexity: O(log N), where N is the number of bits (32 for a uint32_t). This means it will loop through each bit and perform operations like shifting and masking.
Expected Runtime: For 100,000 numbers, this method will likely take several microseconds per number, especially if the algorithm involves more bit manipulation.
Hardware Popcount (hw_popcount):

Time Complexity: O(1), as it uses the SSE4.2 hardware instruction which counts the bits in a fixed number of CPU cycles.
Expected Runtime: For 100,000 numbers, this method will be much faster (in the range of tens to hundreds of nanoseconds per number), making it ideal for performance-sensitive applications.

#### ques7
The "0 microseconds" output is due to the high speed of the operations (integer multiplications) and the clock's resolution. These operations are so fast that their execution time is too short to be measured accurately in microseconds. To fix this:

Increase Iterations: Run the operations multiple times (e.g., 1 million times) to get a measurable duration.
Measure in Nanoseconds: Use std::chrono::duration<double, std::nano> for finer granularity.
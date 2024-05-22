我第一次寫leetcode，寫的是第2469題Convert the Temperature。
```
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */

double* convertTemperature(double celsius, int* returnSize) { 
    double K = celsius + 273.15; 
    double F = celsius * 1.8 + 32;
    double* ans = malloc( 2 * sizeof(double) ); 
    //function malloc will return void* -> double*, and it will be assign to ans (double*)
    
    *returnSize = 2;
    *(ans + 0) = K;
    *(ans + 1) = F;

    return ans;
}
```
寫的是第2469題Convert the Temperature。
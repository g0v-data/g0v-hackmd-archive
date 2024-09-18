#第一章C++程式設計
## 輸入輸出#include <stdio.h>
```c++
#include <stdio.h>
int main(){
	int integer, sum;//這個寫法減少一些記憶體的佔用，因為只有兩個變數，但是有兩個+號和3個=所以計算的時間可能比較長一些(程式效率較差，中央處理工作比較多) ，在記憶體夠的情形下，選擇程式效率優的寫法可能更好 
	printf("Please enter the first integer :");
	scanf("%d", &integer);
	sum = integer;
	printf("Please enter the second integer :");
	scanf("%d", &integer);
	sum = sum + integer;
	printf("Please enter the third integer :");
	scanf("%d", &integer);
	sum = sum + integer;
	printf("Sum is %d.\n",sum);
	return 0;	
} 


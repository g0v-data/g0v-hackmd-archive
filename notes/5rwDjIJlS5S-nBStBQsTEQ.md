# **CPE 一星題 10454:Beat the Spread
**Description:**
Superbowl Sunday is nearly here. In order to pass the time waiting for the half-time commercials and wardrobe malfunctions, the local hackers have organized a betting pool on the game. Members place their bets on the sum of the two final scores, or on the absolute difference between the two scores.  
Given the winning numbers for each type of bet, can you deduce the final scores?

**Input:**
The first line **of input contains n, the number of test cases. n lines follow, each representing a test case. Each test case gives s and d, non-negative integers representing the sum and (absolute) difference between the two final scores.

**Output:**
For each test case, output a line giving the two final scores, largest first. If there are no such scores, output a line containing "impossible". Recall that football scores are always non-negative integers.

**程式碼:**
```=1
#include <bits/stdc++.h>
using namespace std;
int main(){
	int test;
	cin>>test;
	int sum,dif; // a+b = sum, a-b = dif 
	int a,b;
	while(test--){
		cin>>sum>>dif;
		a=(sum+dif)/2;
		b=(sum-dif)/2;
		//總和 和 相差的分數不可能為基數總和 和 相差的分數不可能為基數
		// sum:69 dif:9  a=39 b=30
		if((sum+dif)%2==1||(sum-dif)%2==1||a<0||b<0){ 
			cout<<"impossible"<<endl;
		}else{
			cout<<a<<" "<<b<<endl;
		
		}
		
	
	}
	

}
```    



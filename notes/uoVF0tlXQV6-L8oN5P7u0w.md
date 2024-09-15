##程式設計作業

請輸出「hello, world」文字 (不含「」)。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2a0d68b57868e6c678c98a77094d495d.png)
小明家裡的電視頻道有100台，編號從0到99。頻道是可循環的，也就是如果你在第99台，按下△就能跳到第0台。同樣地，如果你在第0台，按下▽就能轉到第99台。

已知小明正在觀看的頻道和小明想要跳轉到的頻道，你能幫小明計算最少要按幾下按鍵嗎？

 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_320997153d5887d7594a23d66f502206.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b5d7b888bce70c3e5295745e1b7130e3.png)
<pre>
#include <iostream>
using namespace std;

int main()
{
	int n;
	int w;
	cout << "小明正在觀看的頻道 " << endl;
	cin >> n; // now
	cout << "小明想看的頻道 " << endl;
	cin >> w; // watching 
	int a;//次數 
	
	if(n<0 || n>99 || w<0 || w>99)
	{
		cout << "try again" << endl;
		return 0;
	}
	
	int movefoward;
	int movebackward;
	
	if(w>n)//向上轉
	{
	movefoward = w-n;
	movebackward = n-w+100; 
	}
	else if(n>w)//向下轉 
	{
	movefoward = 100+w-n;
	movebackward = n-w;
	}
	else if (n==w) //不動 
	{
		movefoward = 0;
		movebackward = 0;
	}
	
	
	if(movefoward >= movebackward)
	{
		cout << "the answer is:" << movebackward << endl;
	}
	else
	{
		cout << "the answer is:" << movefoward << endl;	
	}
	
	return 0;
}
</pre>
# 程式設計作業3
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_48ca668b87ba62881b95405d4fe90ff4.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ef3503afc1d8e056d675243c27053b1b.png)
<pre>
#include <iostream>
using namespace std;

int main()
{
	int a;
	while(cin>>a)
	{
		if(1<=a && a<=100)
		{
			cout <<a*(a+1)*(2*a+1)/6<<endl;
		}
		else
			break;
		
	}
	return 0;
}
</pre>


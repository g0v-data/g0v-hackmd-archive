# 程式設計6

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2c2baec49dad78fb7f2fc56ed06796f2.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_67b6022ba3bcccaf0e9bc6499ec2b1ab.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_33d266e8e04b5ae43de3cd31edb60d2c.png)
<pre>

#include<iostream>
#include<cmath>
using namespace std;

int main()
{
	int n;
	while(cin>>n)
	{
		int sequence[3000];
		bool difference[3000]= {false};//initialize
		//array must be initialized with a brace-enclosed initializer
		
		
		//輸入序列
		for(int i=0;i<n;i++)
		{
			cin>>sequence[i];	
		} 
		
		//找差值,判斷valid or not
		for(int i=0;i<n-1;i++)
		{
			int d = abs(sequence[i]-sequence[i+1]);
			if(d>0 && d<=n-1)
				difference[d]= true;
		}
		
		
		bool jolly = true;
		for(int a=1;a<=n-1;a++)
		{
			if(!difference[a])
			{
				jolly= false;
				break; //這整個序列是錯的就不用繼續檢查了 
			}
		}
		
		
		if(jolly)
			cout<<"Jolly"<<endl;
		else
			cout<<"Not jolly"<<endl;
	}
	return 0;
}
</pre>
# 程式設計作業3
1.![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6f1c9ef4e80dac36a71e0a79282670ea.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2f1cef641be464f6fc06ccdd9b538cae.png)
<pre>
#include<iostream>
using namespace std;

int main()
{
	int num1, num2;
	int carry, carryCount, digit1, digit2, sum;
	while(cin>>num1>>num2)
	{
		if(num1==0&&num2==0)
			break;
	
	
		carry=0;
		carryCount=0;
		
		while(num1>0||num2>0)
		{
			digit1=num1%10;
			digit2=num2%10;
			
			sum=digit1+digit2+carry;
			carry=sum/10;//現在的進位數 
			carryCount+=carry;
			
			num1 /=10;
			num2 /=10;
		}
			if(carryCount==0)
				cout<<"No carry operation."<<endl;
			else if(carryCount==1)
				cout<<"1 carry operation."<<endl;
			else
				cout<<carryCount<<" carry operations."<<endl;
			
		
	}
	return 0;
}
</pre>


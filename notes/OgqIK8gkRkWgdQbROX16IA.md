# 程式設計7
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_94b67375e53b3f561009c9ef60832a90.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_29583304559375795ae1ea12b4bc1224.png)
or
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7cc9491bb8878bb24e29569e08cb5182.png)

<pre>
#include<iostream>
#include<string.h>
using namespace std;

int main()
{
	int k='*'-'1';//第一個測資對應的ascii碼
	string s;//設定為一個array 
	while(getline(cin,s) )//用string 的時候都用getline, 
	{
		for(int i=0;i<s.length();i++)//string 用 s.length// char[]用strlen 
			cout<<char(s[i]+k);
		cout<<"\n";//換行 
	}
	return 0;
}


</pre>
======
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8674e6fa79a178cdab78d5be6bae8181.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9aeda0afa02401693cfe0a14b2f5c20f.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_582adb5459a6946ee4737981cc64011c.png)
<pre>


//題目:得到序列相加後判斷是否為基數

#include<iostream>
#include<string>
#include<cmath>
using namespace std;

bool isprime(int x)
{
	//bool prime=true;//預設是prime 
	if(x==2)
		return true;
		
	for(int i=2;i<=sqrt(x);i++)//最小的質數一定小於根號n 
	{ 
		if(x%i==0)
			return false;//不為質數	
	} 
	return true;//都沒有的話 
}



int main()
{
	string s;
	int sum;
	while(cin>>s)
	{
		//相加 
		sum=0;
		for(int i=0;i< s.length();i++)
		{
		
			if(s[i]>='a'&&s[i]<='z')
				sum+=s[i]+(1-'a');//使數字為1	
			else if(s[i]>='A'&&s[i]<='Z')
				sum+=s[i]+(27-'A');
		}
		if(isprime(sum)==true)//prime==true
			cout<<"It is a prime word."<<endl;
		else
			cout<<"It is not a prime word."<<endl;
		
	}
	return 0;
	
}

</pre>
======![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1e89dae4c6223eb4dd1a38f786058159.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_678e49cc9bd7dc85914b5a278869e1cd.png)
<pre>

//先找每組的第一個,從每組的最後一個開始輸出-->連續
#include<iostream>
#include<string>
using namespace std;

int main()
{
	int t;
	string s;
	while(cin>>t)
	{
		if(t==0)
			break;
		
		cin>>s;
		
		int groupnum=s.length()/t;
		for(int i=0;i<s.length();i=i+groupnum)//第一組是0,間距是3的話,下一次從第三組開始 
		{
			for(int j=i+groupnum-1;j>=i;j--)//ex:3~6, 第六個開始輸出,最後輸出是第一個,所以j>=i 
				cout<<s[j];
		}
		cout<<endl;
	}	
	return 0;
} 
</pre>



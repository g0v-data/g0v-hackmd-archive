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

____
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b467861050e624d9f23c6576e883e5b7.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_18e63c7fa078c4c40b8f3de38a768dab.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ee0c7ed9252941d750a599e65f4a4830.png)
<pre>


#include<iostream>
#include<cmath>
using namespace std;

int main()
{
	int c;
	cin>>c;
	while(c--)
	{
		int testcase,N;
		cin>>testcase>>N;
		while(testcase--)
		{
		
			int x0,y0,x1,y1;
			cin>>x0>>y0>>x1>>y1;
			
			if(x1==x0&&y1==y0)
				cout<<"0"<<endl;
			else if(abs(x1-x0)%2!=abs(y1-y0)%2)
				cout<<"no move"<<endl;
			else if(abs(x1-x0)%2==abs(y1-y0)%2)
				{
					if(abs(x1-x0)==abs(y1-y0))
						cout<<"1"<<endl;
					else
						cout<<"2"<<endl;
				}
		}
	}
	return 0;
}
</pre>

-----
------

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e985368e6801163a6dc1660761556cd5.png)




![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_764622e6ff7bdea761c63b74d55f5289.png)

<pre>


#include<iostream>
using namespace std;

int main()
{
	int testcase;
	int casenum =1;//他沒要求input要casenumber 
	while(cin>>testcase)
	{
		int sequence[18];
		for(int i=0;i<testcase;i++)
			cin>>sequence[i];
			
			
		long long int maxproduct=0;
		for(int i=0;i<testcase;i++)
		{
			long long int product=1;
			for(int j=i;j<testcase;j++)
			{
				product*=sequence[j];
				maxproduct= max(maxproduct,product);
			}
		}
		cout<<"Case #"<<casenum++<<": The maximum product is "<<maxproduct<<"."<<endl;
		cout<<endl;
	}
	return 0;
}

</pre>
## 用long long
從第一項開始往後每個都乘一次
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8f9fed159c5be0ebf4ed7352745b0218.png)

------
------
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a4d4b9765981932e29e21925c3d3849c.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d1d1488884f66b6fb516cb47fedcbdfa.png)
<pre>


#include<iostream>
using namespace std;

int main()
{
		
	int went, return1,back;

	while(cin>>went>>return1)
	{
		bool survive[1000]={false};
		for(int i=1;i<=return1;i++)
		{
			cin>>back;
			survive[back]=true;
		}
		if(went==return1)
			cout<<"*"<<endl;
		else
		{
			for(int a=1;a<=went;a++)
			{
				if(survive[a]==false)//!survive[a]
					cout<<a<<" ";
			}
			cout<<endl;
		}
		
	
	}
	return 0;
}

</pre>
## 輸出完一次之後記得換行,下個output才會不同行
-------
---------

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_31c5290492a7cd7bb176855179a68ef2.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_37532ec834dd3c2db98ff87a3969cb4b.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_36cf34f16e56e453ae0b5a57193fd640.png)
<pre>

#include<iostream>
using namespace std;

int main()
{
	int casenum;
	cin>>casenum;
	while(casenum--)
	{
		int testnum;
		cin>>testnum;

		int position[100];
		for(int i=0;i<testnum;i++)
		{
			cin>>position[i];
		}
			
		//array中 找最大最小 
		int maxposition=position[0];
		for(int a=0;a<testnum;a++)
		{
			if(position[a]>=maxposition)
				maxposition = position[a];
		}
			
		int minposition=position[0];
		for(int a=0;a<testnum;a++)
		{	
			if(position[a]<=minposition)
				minposition = position[a];
		}
			
		cout<<(maxposition-minposition)*2<<endl;
	
	}
	return 0;
}

</pre>
## or use <algorithm>
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4f3ee1003dc405d5c27baca5ce004c7e.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7d604efb8637f2b0633bbf81e0ddf2fc.png)
<pre>
#include<iostream>
#include<algorithm>
using namespace std;

int main()
{
	int casenum;
	cin>>casenum;
	while(casenum--)
	{
		int testnum;
		cin>>testnum;

		int position[100];
		for(int i=0;i<testnum;i++)
		{
			cin>>position[i];
		}
	
		sort(position,position+testnum);//小到大排序 ***
		cout<<(position[testnum-1]-position[0])*2<<endl;
	}
	return 0;
}

</pre>

-------
------



![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a962c2915303d1b0747ae4f558da69c3.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b92535fd60b5133f7fa6efbd6f1ed411.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5cb098bc14471fe0d7bf16c0dc9bbc1f.png)

<pre>

#include<iostream>
using namespace std;

int main()
{
	int casenum;
	cin>>casenum;
	while(casenum--)
	{
		int priority[32]={0};//initialize
		int ans=1;
		int x,y;
		cin>>x>>y;//instument,students
		
			for(int i=0;i<y;i++)
			{
				for(int j=0;j<x;j++)
				{
					int rank;
					cin>>rank;
					if(rank==1)//標記一 
						priority[j]++;
				}
			}
			
			//檢查重複 
			for(int j=0;j<x;j++)
			{
				if(priority[j]>0)
					ans*=priority[j];
				
			}
		
		
			cout<<ans<<endl;	
		
	
	}
	return 0;
}

</pre>

## 記得initialize,注意x,y位置(看題目!)
# 程式設計5

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fafc6e6485299dc846eb8107b5e58da4.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f63a24efdccc773407b6fd899b926994.png)


<pre>
#include<iostream>
using namespace std;

int k,a,b,ans;


void search(int x,int y,int k)
{
	if(k==0)
		return;//回主程式，他會自己break;
		
	if(x-k<=a&&x+k>=a&&y-k<=b&&y+k>=b)
		ans++;
	search(x+k,y+k,k/2);
	search(x+k,y-k,k/2);
	search(x-k,y+k,k/2);
	search(x-k,y-k,k/2); 
}




int main()
{
	while(cin>>k>>a>>b)
	{
		if(k==0&&a==0&&b==0)
			break;
		ans=0;
		search(1024,1024,k);//一開始的中心座標與半徑
		cout<<"  "<<ans<<endl; 
		
	}
	return 0;
}
</pre>


______
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8d4f378f74c41efa144a6f7cc21b4d48.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8e94e00e2894ac34c8d4a9d113a935af.png)
<pre>
#include<iostream>
using namespace std;

long long int calculate(int generation)
{
	if(generation==1)
		return 1;
	if(generation==2)
		return 2;
	long long int m=2;
	long long int d=1;
	long long int newm;
	for(int i=3;i<=generation;i++)
	{
		newm=m+d;
		d=m;
		m=newm;
	}
	return newm;
}

int main()
{
	int generation;
	while(cin>>generation)
	{
		if(generation==0)
			break;
		cout<<calculate(generation)<<endl;
		
	}
	return 0;
}
</pre>

____![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b015358f543e8587259c825e5414e700.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_12fd8141225823304ae0f383a4119e8d.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_377aad09fbc2ff137577079b6df068b9.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e7bc861c026fdbdd8d050344108aef33.png)
<pre>
#include<iostream>
using namespace std;


bool symm(int num)
{
	int original=num;
	int reverse=0;
	while(num>0)
	{
		reverse=reverse*10+num%10;
		num/=10;
	}
	return original==reverse;//成立即bool=true 
}


int reverse_and_add(int num)
{
	int reverse=0;
	int original=num;
	while(num>0)
	{
		reverse=reverse*10+num%10;
		num/=10;		
	}
	return original+reverse;
}


void find(int num)
{
	int add=0;
	
	num = reverse_and_add(num);
    add++;
    
	while(!symm(num))
	{
		num=reverse_and_add(num);
		add++;
	}
	cout<<add<<" "<<num<<endl;
}


int main()
{
	int c;
	cin>>c;
	while(c--)
	{
		int A;
		cin>>A;
		find(A);
	}
	return 0;
}
</pre>
## 要先reverse and add 一次 再reverse檢查 這樣t(預設是0)=1 

____
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ed583d894865072d58ca909b8a84d2a3.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_73637721f848784c7560ac1dc88ea401.png)
<pre>

#include<iostream>
using namespace std;

int main()
{
	int t;
	cin>>t;
	while(t--)
	{
		int a,b;
		cin>>a>>b;
		if(b%a==0)
			cout<<a<<" "<<b<<endl;
		else
			cout<<"-1"<<endl;
	}
	return 0;
}

</pre>
=============
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e65e9ec368d9a431b20036b9d18617cf.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_eb98c90fb79bacba6afed787c5e554f0.png)
<pre>

#include<iostream>
using namespace std;

int main()
{
	int a;
	while(cin>>a)
	{
		if(a==0)
			break;
		else if(a<=100)
			cout<<"f91("<<a<<") "<<"= "<<"91"<<endl;
		else
			cout<<"f91("<<a<<") "<<"= "<< a-10 <<endl;
	}
	return 0;
}
</pre>
--------
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0cc2fefbb03e670445685ff3604111e4.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5c6fa4388cf3e7b7d23270e7f05fc414.png)
<pre>

#include<iostream>
using namespace std;


int find(int n)
{
	int total=0;
	while(n!=0)
	{
		total+=n%10;
		n/=10;
	}
	
	if(total>=10)
		return find(total);//注意是輸出結果 
	else
		return total;
}


int main()
{
	int n;
	while(cin>>n)
	{
		if(n==0)
			break;
		cout<<find(n)<<endl;
	}
	return 0;
}
</pre>
## 用while!=0挑數字



























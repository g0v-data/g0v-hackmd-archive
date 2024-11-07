# 程式設計上課筆記

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_be0f143ae0fd774251cad5f2da1d9e46.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fda0df327353fe2b86fe06d996b8b3b4.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1803d1b83521d6d5247b3229c476ad9b.png)

and: &&     or:||




if else,  if- else if -else

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_931f3b0739401a71562b229f7a42aea2.png)
-------
#include <iostream>
using namespace std;

int main()
{
    int y,m,d,x;
    y = 2024;
    //m = 9;
    ///d = 12;
    x = y/1000 +y%1000/100+ y%100/10 +y%10;
    x = x + m/10 + m%10;
    x = x + d/10 + d%10;
    x = x/10+x%10;
    x = x/10+x%10;
    cout <<"x=" << x << end1;

    return 0;
}

-------


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_148d34a0437e12ed55be42952d17be07.png)

sum = 0;
i = 1;
sum += 2;
i++;
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c4159dafda6792a3b41faf613d2b90e7.png)
______

<pre>
#include <iostream>
using namespace std;

int main()
{
	int i=1,n,c,sum =0;
	cin >> n;
	
	while(i<=n)
	{
		c=1;
		while(c<= i)
		{
			cout << "*";
			c++;
		}
		cout << endl;
		i++;
	}
	
	i = n -1; // i從n的小一位開始 
	while(i>0)
	{
		c=1;
		while(c<=i)
		{
			cout<<"*";
			c++;
		}
		cout << endl;
		i--;
			
	}
		return 0;		
}
</pre>

*
**
***
**
*
------



<pre>
int main()
{
	int i=1,n,c,sum =0;
	cin >> n;
	
	while(i<=n)
	{
		c=1;//空格 
		while(c<=(n-i)/2)
		{
			cout << " ";
			c++;
		}
		c=1;
		while(c<=i)
		{
			cout<<"*";
			c++;
		}
		cout << endl;
		i+=2;
	}
	
	i = n -2; // i從n的小二位開始 
	while(i>0)
	{
		c=1;
		while(c<=i)
		{
			cout<<"*";
			c++;
		}
		cout << endl;
		i--;
			
	}
		return 0;		
}</pre>

找質數
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6bd3a8a3306fda167eba6ee607bd2322.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4faedf8cb805703ea2d30e65eeafda84.png)

<pre>
#include <iostream>
using namespace std;

int main()
{
	int n=2,light,c;
	while(n<=1000)
	{
		light = 1;//燈打開 
		c = 2;// 可以整除的數字 
		while(c*c<=n)//比如81=9*9 ,9是質數 
		{
			if(n%c==0)//n被成功整除 
				light = 0;//把燈關掉 
			c++;//一直嘗試直到關掉 
		}
		if(light==1)
			cout << n << endl;//燈關不掉就是質數 
		n++;//while block的變數 
	}
	return 0;
}
</pre>


----------
## 九九乘法表
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_233fec56892a7a785623f89c949ba376.png)

<pre>
#include <iostream>
using namespace std;

int main()
{
	for(int i =1; i <=9; i++)
	{
		for(int j =1;j<=9;j++)
		{
			cout << i <<"x"<< j<<"="<<i*j<<"\t";
		}
		cout << endl ;// 換行 
	}
	return 0;
} 
</pre>

費式數列
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_23891356cc5006f7a49e5474a5eb3d14.png)

## do while :先跑一次在判斷對不對
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b964a78816c05c79140da3c5afa96428.png)
## for(c=1;c<=10;c++)
## for(c=1;c<=10;c+=2)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a4371df4fe920efd64d01c7b329f3cca.png)

## 質因數分解
<pre>
	
	int s,c,m //c的幾次方 
	cin>>s; //待測數 
	c=2 //2可以整除 
	while(c*c<=s)//大於二次方 
	{
		m=0
		while(s%c==0)
		{
			s/=c;
			m++;
		}
		if(m!=0)
		{ 
			if(first==1)
			{
				cout<<c<<"^"<<m<<"*";
				first =0;
			
			}
			else
			{
				cout<<"*"<<c<<"^"<<m;
			}
		} 
		c++;
	}
	if(s!=1)
	{
		if(first==1)
			cout <<s<<"^1"<<endl;
		else
			cout<< << "*"<<s<<"1"<<endl;
	}
	return 0;
}
</pre>

## break
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_543df7689c6e8479d0294095a2fd5a4f.png)

## continue
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1a8ceaa155378e9c6e4169fc82ebb775.png)



	int m,n,t;
	cin>>m;
	cin>>n;
	while(n!=0)
	{
		m%=n;
		t=m;
		m=n;
		n=t;
	}
	cout<<m<<endl;
	
	
------
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cbead23b5ebae8fa39d5d7c734a90163.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d527e7a849e9f5355967b04f8d7d8a82.png)
question:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_02bf17faff2dca142f1886e34732dc0e.png)




-------
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_77c2ae991adea933224513b40af615dd.png)

* continue=沒有符合就跳過繼續
*break=直接跳出
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5e363e69a3d44428d22a0a5bac0cc30d.png)
* else if= elif
* print():換行
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_11d24c3a4dd7dbfdffd28d217ecd5b12.png)
<pre>
#include<iostream>
using namespace std;

int f(int x)//f(x)
{
	int r;
	r=x*x+2*x+1;
	return r;
	
}

int g(int x,int y)
{
	int i,r=1;
	for(i=1;i<y:i++)
		r*=x;
	return r;
}

int main()
{
	cout<<f(2)<<endl<<f(5)<<endl;
	cout<<g(5,3)<<endl<<g(2,10)<<endl;
	return 0;//回傳 
}</pre>
____
int main=void main
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8e253bccc70ec7a3d0b8271ced7028ce.png)

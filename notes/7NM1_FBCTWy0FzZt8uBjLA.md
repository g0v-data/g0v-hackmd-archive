#程式設計上課筆記

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
-



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
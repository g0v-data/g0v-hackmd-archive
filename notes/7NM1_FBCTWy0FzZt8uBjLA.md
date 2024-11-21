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
_____
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0da1936d9d88032e0d8f86ab5928eac6.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3a795231102f67f49ec497555290b9cc.png)
//void裡面的變數名隨便寫
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7b7f7ea7b488817e66390da856f44c8d.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_731e07b76f372940fbf2ef05c1530fca.png)
<pre>
#include<iostream>
using namespace std;

void Case(int);
void wave(int);
void wave1(int);

int main()
{
	int N;
	cin>>N;//幾筆測資
	for(int n=0;n<N;n++) 
		Case(n);
	
	return 0;	
} 

void Case(int n)//每個三角形重複幾次 
{
	int A,F;
	cin>>A>>F;
	for(int f=0;f<F;f++)
	{
		wave(A);
		cout<<endl;
	}
	
}

void wave(int A)//每個波印幾個符號 
{
	int a;
	for(a=1;a<=A;a++)
	{
		wave1(a);
	}
	for(a=A-1;a>=1;a--)
	{
		wave1(a);
	}
}

void wave1(int X)
{
	int x;
	for(x=0;x<X;x++)
		cout<<X;
	cout<<endl;
}

</pre>
__________
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5a4909368f369d1de747ba591e21bf70.png)
1.5!,4!..
2.0,1,2,3,5,8,13,21
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d5db2a62be3370b927b203e0b664efa3.png)
<pre>

#include<iostream>
using namespace std;

int S(int n)
{
	/*
	int r=1;
	for(int a=1;a<=n;a++)
		r+=a
	return r;
	*/
	if(n==1)
		return 1;
	else
		return n*S(n-1);
		//5!=5*4!=5*4*3!....一直向大int呼叫缺少的變數ex:4! 
}

int F(int n)
{
	if(n<=1)
		return n;
	return F(n-1)+F(n-2);//0,1,1,2,3,5,6,13,21
}

int main()
{
	cout<<S(5)<<endl;
	cout<<S(10)<<endl;
	
	cout<<F(5)<<endl;
	cout<<F(10)<<endl;
	return 0;
}
</pre>
_____
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_18c83b0380539b964368ccd51ca24743.png)
<pre>

int C(int m,int n)//c m取n =c(m-1)取n + c(m-1)取n-1 
{
	if(m==n)
		return 1;
	if(n==1)
		return m;
	return C(m-1,n)+C(m-1,n-1);
}
</pre>

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5a59bb22e34e59cb25d75ea6c04e8275.png)

_____
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_94e06cc16b88666d9b5f11e106d5873b.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_72929871eb6916f51565645900e186db.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8afebfcdc3c7f63b00fb8c7a631c12c8.png)

<pre>

#include<iostream>
#include<stdlib.h>//用在srand 
#include<time.h>//用在srand:time 
using namespace std;


void initialize(int c[]);
void wash(int c[]);
void print(int c[]);


int main()
{
	int cards[52],i;
	srand(time(NULL));//使每次結果不一樣 
	for(i=0;i<=52;i++)
		cards[i]=i;//array 第一個是0 
		initialize(cards);
		wash(cards);
		print(cards);
	return 0;
}

void initialize(int c[]);
{
	int i;
	for(i=0;i<52;i++)
		c[i]=i;
}

void wash(int c[])
{
	int i,m,n,tmp;
	for(i=0;i<1000;i++)//換1000次 
	{
		m = rand()%52;
		n = rand()%52;
		//c[m] <-> c[n] 
		//隨機挑兩個互換 
		tmp=c[m];
		c[m]= c[n];
		c[n]=tmp;
	}
}


void print(int c[])
{
	int n,f,d;
	for(int i=0;i<13;i++)
	{
		n=c[i];
		f=n/13;//0~3
		d=n%13+1;//1~13
		if(f==0)
			cout<<"square";
		else if(f==1)
			cout<<"heart";
		else if(f==2)
			cout<<"diamond";
		else
			cout<<"C";
			
		if(d==0)
			cout<<"A";
		else if(d==11)
			cout<<"J";
		else if(d==12)
			cout<<"Q";
		else if(d==13)
			cout<<"K";
		else
			cout<<d;
		cout<<" ";
		
	}
}


</pre>
=======
======
========
=======
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_814916fa4a6b1e21e4f97db05c639dee.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5acdc59a6d7c537e48b6ee11767fa48e.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_404aa0b127764d620786977e6bc74568.png)
<pre>

#include<iostream>
using namespace std;


void seperate(int n, int c[]);
int isValid(int c[]);//1-> 0->wrong 
int guess(int p[]);
void match(int g,int a,int AB[]);

int main()
{
	int your_ans,com_guess,com_AB[2],tmp_AB[2],i;
	do{
		cout<<"input your answer";
		cin>>your_ans;
	}while(isValid(your_answer)==0);//錯的話就再問一次 
	
	
	int pool[10000],i;
	for(i=0;i<10000;i++)
		pool[i]=isValid(i);//對應 0,1位置 
		
	do{//可能的標一，不可能標0 
		com_guess = guess(pool);
		match(com_guess,your_ans,com_AB);//回傳幾a幾b 
		cout<<com_guess<<":"<<com_AB[0]<<"A"<<com_AB[1]<<"B"<<endl;
		//update pool
		for(i=0;i<10000;i++)//殺不掉的 
		{
			if(pool[i]==1)
			{
				match(com_guess,u,tmp_AB);
				if(tmp_AB[0]!=com_AB[0])||tmp_AB[1]!=com_AB[1])
					pool[i]=0;	
			}	
		}
		
	}while(com_AB[0]!=4);//	猜到四a 之前 一直重複 
		
	return 0;
}


void seperate(int n, int c[])//分成四位數 
{
	c[0] = n/1000;
	c[1] = n%1000/100;
	c[2] = n%100/10;
	c[3] = n%10;
}

int isValid(int n)
{
	if(n>10000||n<0)
		return 0;
	int d[4];
	seperate(n,d);
	if(d[0]==d[1]||d[0]==d[2]||d[0]==d[3]||d[1]==d[2]||d[1]==d[3]||d[3]==d[2])
		return 0;
	else
		return 1;
	
}

int guess(int p[])//optional
{
	int i = 0;
	while(p[i]==0)
		i++;
	return i;
}

void match(int g, int a, int AB[])
{
	int gd[4],ad[4];
	sep(g,gd);
	sep(a,ad);
	AB[0]=0;
	AB[1]=0;
	for(m=0;m<4;m++)
	{
		for(n=0;n<4;n++)
		{
			if(gd[m]==ad[n])
			{
				if(m=n)
					AB[0]++;
				else
					AB[1]++;
			}
		}
	}
}
</pre>


| Function | Prototype | Purpose | Return Value | Example | Header | Key Considerations |
|----------|-----------|---------|--------------|---------|--------|---------------------|
| `strlen()` | `size_t strlen(const char *str)` | Calculate string length | Number of characters in string | `strlen("Hello")` returns `5` | `<string.h>` | Excludes null terminator |
| `strcpy()` | `char *strcpy(char *dest, const char *src)` | Copy one string to another | Pointer to destination string | `strcpy(dest, "Hello")` copies "Hello" to dest | `<string.h>` | No buffer size checking - risk of overflow |
| `strcmp()` | `int strcmp(const char *str1, const char *str2)` | Compare two strings | 0 if equal, <0 if str1 < str2, >0 if str1 > str2 | `strcmp("hello", "world")` returns negative | `<string.h>` | Lexicographic comparison |
| `strcat()` | `char *strcat(char *dest, const char *src)` | Concatenate (join) strings | Pointer to destination string | `strcat(dest, " World")` appends " World" | `<string.h>` | Assumes enough space in destination |

**Safety Tips:**
- Always check buffer sizes
- Use `strncpy()`, `strncat()`, `strncmp()` for length-limited operations
- Ensure destination buffers are large enough to prevent buffer overflows
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a2012750b3c4bc505d9570f873897e6b.png)
=======
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f3349be8673b21ededd0b3a4c852d152.png)

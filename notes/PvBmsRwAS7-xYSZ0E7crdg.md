# 程式設計作業2
These days, it has become commonplace to make purchases over the internet using a credit card. However, because credit card numbers are relatively long, it is easy to make a mistake while typing them in. In order to quickly identify errors like typos, most e-commerce websites use a checksum algorithm to verify credit card numbers.

   One popular checksum algorithm is the Luhn algorithm, which can detect any single-digit error as well as many common multiple-digit errors:

1. Starting with the second-last digit and moving backwards, double every other digit to obtain a list of numbers.

2. Add up the digits of these numbers, then add the undoubled digits from the original number. Sum the two results.

3. If the total ends in a 0, the credit card number is valid, and it is invalid otherwise.

1. Double the appropriate digits (5181 2710 9900 0012) to obtain the values: 10, 16, 4, 2, 18, 0, 0, 2.

2. Add up the digits of these values to get (1+0) + (1+6) + 4 + 2 + (1+8) + 0 + 0 + 2 = 25. The sum of the undoubled digits is 1+1+7+0+9+0+0+2 = 20, so the total is 20+25=45.

3. 45 does not end in a 0, so this credit card number is invalid.

    For this problem, you must write a program that checks the validity of credit card numbers according to the Luhn algorithm.
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_eb5bd9cb7ed319c67f40c113ee6102f2.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_41f92c1c23037244279bf00468339690.png)
<pre>
#include <iostream>
using namespace std;
int main()
{
	int n;//測試次數 
	cin >> n;
	while(n--)//對於每個測試用量數目  
				/*這表示當 n 不等於 0 時，進行迴圈。
				在每次進入迴圈前，n 會先被用來判斷是否繼續執行迴圈。使用後，n 才會遞減 1。*/ 
	{
		int sum=0;//初始化總和為0 //重要!!! 
		bool isEvenPosition = false; //library裡的變數 自動判斷偶數:初始化為基數位置(從第一個數字開始為基數) 
		
		
		for (int i =0; i <4; i++)//檢測卡號: 四組數字 
		{
			int group;
			cin>>group;//儲存每組數字(四個四個輸入) 
			
			for(int j=0; j<4; j++)//一組有四個數字 
			{
				int digit = group%10;//取出各位數字 =digit (當個數字d)
				group /= 10;//去掉個位數字 (前三個數字) ---> 每論檢測的數字不一樣，這輪測完 d下輪測c 
				
				if(isEvenPosition)//如果是偶數位，乘2以後加到總和 
				{
					sum+= (digit*2)/10+(digit*2)%10;
				}
				else//如果是奇數位直接加到總和 
				{
					sum+= digit;	
				}
				isEvenPosition = !isEvenPosition;//比如說abcd，我們要的數字是ac(ac預設是偶數), c這輪是偶數，下輪(abc)時就變奇數了 
			}
		}
		
		//判斷總和是否為零
		if(sum%10 ==0)//最後一位，看除與十是否有餘數
		{
			cout << "Valid" << endl;	
		} 
		else
		{
			cout << "Invalid" << endl;
		}
		 
	}
	return 0;
}
</pre>
-----
-----
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4dbe58b55a625bc3d59f38ab22913637.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f7eb0f4270ba566c1d7bd3bf72684444.png)

<pre>
#include <iostream>
using namespace std;

int main()
{
	int n;
	while(cin>>n)
	{
		int total=n;
		int newcola;
		
		while(n>=3)
		{
			newcola = n/3;
			total += newcola;
			n = newcola + n%3;
		}
		if(n==2)
		{
			total++;
		}
		
		cout << total <<endl;
	}
	return 0;
}
</pre>
-----------
--------
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b49f18aa611f8e30957b7d3a377b39e9.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dc0c972126f0bbbacd4de3c400c07ea4.png)
## or

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4c0380ea722e7f73c7c72e6520feb0da.png)


<pre>
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n; 
    while (n--) {
        long long sum, dif;
        cin >> sum >> dif; 

        if (sum < dif || (sum - dif) % 2 != 0) {
            cout << "impossible" << endl;
        } else {
            long long x = (sum + dif) / 2; 
            long long y = (sum - dif) / 2; 
            cout << x << " " << y << endl; 
        }
    }

    return 0;
}
</pre>
* The issue with your code lies in the inner while(cin >> sum >> dif) loop. This will cause the program to continuously read pairs of sum and dif until it reaches the end of input, which isn't the intended behavior. Instead, you should read sum and dif only once per test case. Here’s how to fix it:

--------
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8a1efb33289dc066f762685ced9c24a7.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_63b6057b54869f4b480af2c806c4e827.png)
<pre>
#include <iostream>
using namespace std;

int main()
{

	int n;
	cin>>n;
	while(n--)
	{
		int a,b,c,d;
		cin>>a>>b>>c>>d;
		if(0<a<230 && 0<b<230 && 0<c<230 && 0<d<230)
		{
			if(a==b&&b==c&&c==d)
				cout <<"square"<< endl;
			else if(a==b&&c==d ||a==c&&b==d||a==d&&b==c)
				cout << "rectangle" <<endl;
			else if (a+b+c>d&&a+b+d>c&&a+c+d>b&&b+c+d>a)
				cout << "quadrangle"<<endl;
			else
				cout<<"banana"<<endl;
		}
		else
			return 1;
	}
	return 0;
}
</pre>

---------
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6785b53bae6f3dcbdca6294214864cea.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1c9fd130193fc885cc2c20cfbf7d6b70.png)

<pre>
#include <iostream>
using namespace std;
#include <cmath>

int main()
{
	int n;
	cin >> n;
	while(n-- && n<15) 
	{
		int a,b;
		cin>>a>>b;
		if(abs(a) < 1000000001 && abs(b) < 1000000001)
		{
			if(a>b)
				cout <<">"<< endl;	
			else if(a<b)
				cout << "<"<<endl;
			else if(a=b)
				cout << "=" <<endl;
				
		}
		else
			return 1; 
	}
	return 0;
}
</pre>
-
 
-
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_49b6591a085269f851371e9555aaffb4.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d37ab131beae4d6cc5156cf794edd675.png)

<pre>
#include <iostream>
using namespace std;
#include<cmath>

int main()
{
	long long int n;
	cin>>n;
	while(n--&&1<=n<=5*105)
	{
		long long int s;
		cin>>s;
		if(1<=s<=pow(10,9))
		{
			long long int a;
			a=(s+1)*(s+1)-1;
			cout <<a<<endl;
		}
		else
			return 1;
	}
	return 0;
	
}
</pre>


# 程式設計作業4
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
-----
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3426f989164696ad19314f6f183a3796.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fbca6869295f72c0bff55b5dd633e671.png)
<pre>

#include<iostream>
using namespace std;
#include<cmath>

int main()
{
	int a,b;
	while(cin>>a>>b)
	{
		
		if(a==0||b==0)
			break;
			
		if(0<a&&a<=b&&b<=100000)
		{
		int aroot, broot;
		aroot=ceil(sqrt(a));
		broot=floor(sqrt(b));
		int sum;
		sum= broot-aroot;
		cout<<sum+1<<endl;
		}
		else 
			return 1;
	}
	return 0;
}
</pre>
_____
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0f99187c78802535b700dfe52886ae6b.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6bde9c23c6e1b9c1aeeba337d63a6a35.png)
<pre>

#include <iostream>

using namespace  std;

int main()
{
    int T;
    cin >> T;
    int n, c;
    int casenum=1;
    while(T--)
    {
	
        cin >> n;
        for (int i = 1; i <= n; ++i)
        {
            cin >> c;
            if (i == (n / 2)+ 1)
            cout << "Case " << casenum++ << ": " << c << '\n';
        }
    }
    
}
</pre>
-----
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_20d2841d48275ae8c0cda09a4156ca7e.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_54cd41097854097fd9996e1c23d6be02.png)
<pre>
#include <iostream>
using namespace std; 

int main()
{
 int N,onhand,found,need;
 cin>>N;
 while(N--)
 {
  cin>>onhand>>found>>need;
  int ans=(onhand+found)/need;
  onhand=(onhand+found)/need+(onhand+found)%need;
  while(onhand>=need)
  {
   ans+=onhand/need;
   onhand=onhand/need+onhand%need;
  }
  cout<<ans<<"\n"; 
 }
 return 0;
}
</pre>

------
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_187824035c95297d38266f5b3d0d37af.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2773cf7e6038f3601316d6764005ca73.png)
<pre>

#include<iostream>
#include<cmath>
using namespace std;

int main() {
    int n;
    while (cin >> n) {
        if (n == 0)
            break;

        double radius = n - 0.5; 
        int containedcells = 0;  
        int segmentcells = 0;   

      
        for (int x = 0; x < 2 * n; x++) {
            for (int y = 0; y < 2 * n; y++) {
                double d1 = sqrt((x - n) * (x - n) + (y - n) * (y - n));       // (x, y)
                double d2 = sqrt((x + 1 - n) * (x + 1 - n) + (y - n) * (y - n)); // (x + 1, y)
                double d3 = sqrt((x - n) * (x - n) + (y + 1 - n) * (y + 1 - n)); // (x, y + 1)
                double d4 = sqrt((x + 1 - n) * (x + 1 - n) + (y + 1 - n) * (y + 1 - n)); // (x + 1, y + 1)

                if (d1 <= radius && d2 <= radius && d3 <= radius && d4 <= radius)
                    containedcells++;
                else if (d1 <= radius || d2 <= radius || d3 <= radius || d4 <= radius)
                    segmentcells++;
            }
        }

       
        cout << "In the case n = " << n << ", " << segmentcells << " cells contain segments of the circle." << endl;
        cout << "There are " << containedcells << " cells completely contained in the circle." << endl;
        cout << endl; 
    }

    return 0;
}

</pre>




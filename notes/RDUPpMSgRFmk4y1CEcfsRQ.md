# 程式設計作業3
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_48ca668b87ba62881b95405d4fe90ff4.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ef3503afc1d8e056d675243c27053b1b.png)
<pre>
#include <iostream>
using namespace std;

int main()
{
	int a;
	while(cin>>a)
	{
		if(1<=a && a<=100)
		{
			cout <<a*(a+1)*(2*a+1)/6<<endl;
		}
		else
			break;
		
	}
	return 0;
}
</pre>
---------
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6e4d8246be56d927745d9bf5600ef3e1.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b4705543adb642e1253003e67536d673.png)
<pre>
#include<iostream>
using namespace std;

int main()
{
	int n,k;
	while(cin>>n>>k)
	{
		int sum=n;
		int left=n;
		while(left>=k)//重複 
		{
			int newleft=left%k;
			left=left/k;
			sum=sum+left;
			left=left+newleft;	
		}
		cout<<sum<<endl;
		
	}
	
	return 0;
	
}
</pre>
------
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e5c279806b5790ef9766005b7c6be521.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_040eeab1f55b47e9deb0fadbb7d4762d.png)
## 不能用while(t--) ?
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7e2f9c828f3af726ba38d18980e7de64.png)


<pre>
#include <iostream>
using namespace std;

int main() {
    int t;  // Number of test cases
    cin >> t;
	
    for (int i = 1; i <= t; i++) {
        int walls;  // Number of walls
        cin >> walls;
        int groups[50]; 
        
        for (int j = 0; j < walls; j++) {
            cin >> groups[j];
        }//單純輸入 
        
        int highjump = 0, lowjump = 0;
        
        //開始比較 
        for (int j = 0; j < walls - 1; j++) {
            if (groups[j] < groups[j + 1]) {
                highjump++;
            } else if (groups[j] > groups[j + 1]) {
                lowjump++;
            }
        }
        cout << "Case " << i << ": " << highjump << " " << lowjump << endl;
    }

    return 0;
}

</pre>
-------



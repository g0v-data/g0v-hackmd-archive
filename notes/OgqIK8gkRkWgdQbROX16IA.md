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
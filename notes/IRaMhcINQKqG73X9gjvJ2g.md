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
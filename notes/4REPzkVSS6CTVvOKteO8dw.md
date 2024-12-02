# 程式設計作業8
![](https://g0v.hackmd.io/_uploads/Sy8Xh997kg.png)

![](https://g0v.hackmd.io/_uploads/BJeEGh99Q1x.png)
![](https://g0v.hackmd.io/_uploads/Sk0PTEsXyg.png)

<pre>
#include<iostream>
using namespace std;

int main()
{
	int casenum,a,b;
	cin>>casenum;
	while(casenum--)
	{
		
		cin>>a>>b;
		for(int i=0;i<b;i++)//印b個波
		{
			for(int j=1;j<=a;j++)
			{
				for(int h=1;h<=j;h++)
					cout<<j;
				cout<<endl;	//每個數字後換行 
			}	
			//*
			//**
			//***
			
			for(int j=a-1;j>0;j--)
			{
				for(int h=j;h>0;h--)
					cout<<j;
				cout<<endl;	//每個數字後換行 
			}
			//**
			//*
			//cout<<endl;//最後一個不換 
			if(i!=b-1)//不適最後一個 波都要換行 :最後一個波不換行 
			{
				cout<<endl;
			}
		}
		//case間要換行 
		if(casenum>0)//casenum 0 時不換行 :最後一個案例不換行 
			cout<<endl;
		 
	}
	
	return 0;
}
</pre>
------
![](https://g0v.hackmd.io/_uploads/BkLlp9c7kl.png)
![](https://g0v.hackmd.io/_uploads/HJl2Io39Xyl.png)
![](https://g0v.hackmd.io/_uploads/SkSdihcQJe.png)
<pre>


//先設flag再決定有幾個
#include<iostream>
#include<string>
using namespace std;

int main()
{
	string baseone;//要讀input:一串測資  
	string basetwo;//
	int num;
	char flag;
	
	while(cin>>baseone&&baseone!="~")//一個一個int讀 
	{
		if(baseone=="#")
		{
			num=0;
			//轉十進位
			for(int i=0;i<basetwo.length();i++)
			{
				if(i!=0)
					num*=2;//除了第一位都成立 
					
				if(basetwo[i]=='1')
					num+=1;	//if flag=0, 跳過累加 
			} 
			basetwo="";//重置 prepare for the next casenum 
			cout<<num<<endl;
		}
		else if(baseone.length()==1)
			flag='1'; //char用''
		else if(baseone.length()==2)
			flag='0';
		else
		{
			for(int i=0;i<baseone.length()-2;i++)
				basetwo +=flag;//不是直接加二 是加兩次11	
		} 
			
		
	}
	return 0;
}
</pre>
-------
![](https://g0v.hackmd.io/_uploads/rkeF8ESjmkg.png)
![](https://g0v.hackmd.io/_uploads/BkgowEHiX1x.png)
<pre>

#include<iostream>
#include<string>
using namespace std;

int main()
{
	int casenum;
	cin>>casenum;
	while(casenum--)
	{
		string word;
		cin>>word;
		
		if(word.length()==3)
		{
			if((word[0]=='t'&&word[1]=='w')||(word[1]=='w'&&word[2]=='o')||(word[0]=='t'&&word[2]=='o'))
				cout<<"2"<<endl;
			else 
				cout<<"1"<<endl;
		}
		
		if(word.length()==5)
			cout<<"3"<<endl;
			
	}
	return 0;
}


</pre>
--------

![](https://g0v.hackmd.io/_uploads/Hk4_lUj71l.png)
![](https://g0v.hackmd.io/_uploads/SJgqgLimkl.png)
![](https://g0v.hackmd.io/_uploads/HyAcgUsQ1x.png)
<pre>


#include<iostream>
using namespace std;

int main()
{
	int casenum;
	cin>>casenum;
	while(casenum--)
	{
		int m,d;
		cin>>m>>d;
		//月份轉天數
		m--;
		while(m!=0)
		{
			if(m==1||m==3||m==5||m==7||m==8||m==10||m==12)
			{
				d+=31;
				m--;	
			}	
			else if(m==4||m==6||m==9||m==11)
			{
				d+=30;
				m--;
			}
			else if(m==2)
			{
				d+=28;
				m--;
			}
		}
		int sum;
		sum=d%7;
		
		if(sum==0)
			cout<<"Friday"<<endl;
		if(sum==1)
			cout<<"Saturday"<<endl;
		if(sum==2)
			cout<<"Sunday"<<endl;
		if(sum==3)
			cout<<"Monday"<<endl;
		if(sum==4)
			cout<<"Tuesday"<<endl;
		if(sum==5)
			cout<<"Wednesday"<<endl;
		if(sum==6)
			cout<<"Thursday"<<endl;		
	}
	return 0;
}



</pre>

--------

![](https://g0v.hackmd.io/_uploads/rkhUJwimkg.png)
![](https://g0v.hackmd.io/_uploads/BkSd1vjQkl.png)
![](https://g0v.hackmd.io/_uploads/SJfKJwjQyx.png)
<pre>

#include<iostream>
using namespace std;

int main()
{
	float h,u,d,f;//一定要用float!!!!不然過不了!! 
	while(cin>>h>>u>>d>>f)
	{
		if(h==0)
			break;
		
		int i=0;
		float sum=0;
		float tired=f*u/100;
		
		while(true)//讓系統跑 
		{
			i++;// 第一天 
			if(u>0)
				sum+=u;
			if(sum>h)
			{ 
				cout<<"success on day "<<i<<endl;
				break;//用完就跳出去  
			}//記得括號 
			sum-=d;
			if(sum<0)
			{ 
				cout<<"failure on day "<<i<<endl;
				break;
			}	
			u-=tired;
			if(u<=0)
				u=0; 
		}
			
	}
	
	return 0;
}



</pre>
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


# 程式設計作業8
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
		for(int i=0;i<b;b++)//印b個波
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
				for(int h=1;h<=j;h++)
					cout<<j;
				cout<<endl;	//每個數字後換行 
			}
			//**
			//*
			
			if(i!=b-1)//不適最後一個 波都要換行 :最後一個波不換行 
			{
				cout<<endl;
			}
		}
		if(casenum>0)//casenum 0 時不換行 :最後一個案例不換行 
			cout<endl;
		 
	}
	
	return 0;
}
</pre>
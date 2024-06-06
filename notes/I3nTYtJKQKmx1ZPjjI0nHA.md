# f640. 函數運算式求值
```
#include <iostream>
#include <bits/stdc++.h>
using namespace std;

int fun(){//把常數視為f(x)=x的函數 pps:fun一定可以算出取到的函數的數值
    string a;
    cin>>a;
    if(a=="f")
        return 2*fun()-3;
    else if(a=="g")
        return 2*fun()+fun()-7;
    else if(a=="h")
        return 3*fun()-2*fun()+fun();
    else
        return stoi(a);//把string轉成int
}

int main()
{
    cout<<fun();

    return 0;
}


```
# f637. DF-expression
```
#include <iostream> //ps:如果引入萬用標題檔會變異錯誤，原因不明
using namespace std;

int index=-1;
string s;

int fun(int n){
    index++;
    if(s[index]=='1'){
        return n*n;
    }
    else if(s[index]=='0'){
         return 0;
    }
    else{
        return fun(n/2)+fun(n/2)+fun(n/2)+fun(n/2);
    }

}

int main()
{
    int n;
    cin>>s;
    cin>>n;
    cout<<fun(n);

    return 0;
}


```
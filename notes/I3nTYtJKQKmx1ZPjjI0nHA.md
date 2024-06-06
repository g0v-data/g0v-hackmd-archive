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
        return a[0]-48;//把string轉成int
}

int main()
{
    cout<<fun();

    return 0;
}

```
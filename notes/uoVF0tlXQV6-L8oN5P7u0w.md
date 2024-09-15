##程式設計作業

請輸出「hello, world」文字 (不含「」)。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2a0d68b57868e6c678c98a77094d495d.png)
小明家裡的電視頻道有100台，編號從0到99。頻道是可循環的，也就是如果你在第99台，按下△就能跳到第0台。同樣地，如果你在第0台，按下▽就能轉到第99台。

已知小明正在觀看的頻道和小明想要跳轉到的頻道，你能幫小明計算最少要按幾下按鍵嗎？

 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_320997153d5887d7594a23d66f502206.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b5d7b888bce70c3e5295745e1b7130e3.png)
<pre>
#include <iostream>
using namespace std;

int main()
{
	int n;
	int w;
	cout << "小明正在觀看的頻道 " << endl;
	cin >> n; // now
	cout << "小明想看的頻道 " << endl;
	cin >> w; // watching 
	int a;//次數 
	
	if(n<0 || n>99 || w<0 || w>99)
	{
		cout << "try again" << endl;
		return 0;
	}
	
	int movefoward;
	int movebackward;
	
	if(w>n)//向上轉
	{
	movefoward = w-n;
	movebackward = n-w+100; 
	}
	else if(n>w)//向下轉 
	{
	movefoward = 100+w-n;
	movebackward = n-w;
	}
	else if (n==w) //不動 
	{
		movefoward = 0;
		movebackward = 0;
	}
	
	
	if(movefoward >= movebackward)
	{
		cout << "the answer is:" << movebackward << endl;
	}
	else
	{
		cout << "the answer is:" << movefoward << endl;	
	}
	
	return 0;
}
</pre>
 or
 <pre>
#include <iostream>
using namespace std;

int main()
{
    int n, w;
    
    while (cin >> n >> w)
    {
        if(n < 0 || n > 99 || w < 0 || w > 99)
        {
            cout << "try again" << endl;
            continue; 
        }

        int movefoward, movebackward;

        if(w > n) // Moving up
        {
            movefoward = w - n;
            movebackward = n - w + 100;
        }
        else if(n > w) // Moving down 
        {
            movefoward = 100 + w - n;
            movebackward = n - w;
        }
        else if (n == w) 
        {
            movefoward = 0;
            movebackward = 0;
        }
        if(movefoward <= movebackward)
        {
            cout << movefoward << endl;
        }
        else
        {
            cout <<  movebackward << endl;
        }
    }

    return 0;
}
</pre>





有一天 Joanna 發現了一個有趣的奇數排列圖形如下

1 

3 5 7 

9 11 13 15 17 

19 21 23 25 27 29 31

 ...

如果給你一個數字N代表某一特定行中有N個數字，你能幫 Joanna 算出那一行的最後三個數字總和嗎？

 提示：這題請用 long long 宣告喔

EX： long long int N;

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a0b62a68d5813da2dcd4832b492ebf9b.png)
<pre>
#include <iostream>
using namespace std;

int main()
{
    int N;
    while(cin>>N)
    {
    long long int row = (N +1)/2;
    long long int all_num = row* row;
    long long int a,b,c;

    a = all_num *2 -1;
    b = all_num *2 -3;
    c = all_num *2 -5;
    cout << a + b +c<< endl;
    }
    return 0;
}</pre>

Hashmat is a brave warrior who with his group of young soldiers moves from one place to another to fight against his opponents. Before Fighting he just calculates one thing, the difference between his soldier number and the opponent’s soldier number. From this difference he decides whether to fight or not. Hashmat’s soldier number is never greater than his opponent.

提示：本題輸入數字是小於2^32，但int的範圍是-2^31~2^31-1，因此有可能overflow，請使用long long int 宣告才會AC

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c6514493381655157a9167a303639fea.png)
<pre>
#include <iostream>
using namespace std;

int main()
{
    long long int hashmat, opponent;

    // Continuously read input until end of input (EOF)
    while(cin >> hashmat >> opponent)
    {
        // Calculate the difference between opponent's soldiers and Hashmat's soldiers
        cout << opponent - hashmat << endl;
    }

    return 0;
}

</pre>


現在您又要回學校上一個學期了，您需要記住如何操作儲物櫃上的密碼鎖。 常見的設計是 Master Brand 的設計，如下圖所示。 鎖有一個刻度盤，上面有 40 個校準標記，編號為 0 到 39。一個組合由這些數字中的 3 個組成； 例如：15-25-8。 要打開鎖，需採取以下步驟：

順時針轉動刻度盤 2 整圈
在組合的第一個數字處停止
逆時針旋轉錶盤 1 整圈
繼續逆時針旋轉，直到達到第二個數字
再次順時針轉動錶盤，直到達到第 3 個數字
拉動柄，鎖就會打開。
給定錶盤的初始位置和鎖的密碼，打開鎖時錶盤總共旋轉了多少度（順時針加逆時針）？

 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_da0261b413780f9c47ba11f0115eb341.png)

<pre>
#include <iostream>
using namespace std;

int main()
{
	int s, a, b, c;
	while(cin >> s >> a >> b >> c)
	{
		int ans = 0;
		int angle = 360/40;
		ans += 720;
		ans += ((s-a+40)%40 * angle);
		ans += 360;
		ans += ((b-a+40)%40 * angle);
		ans += ((b-c+40)%40 * angle);	
		
		cout << ans << endl;		
	}
}
}</pre>
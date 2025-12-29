leetcode-medium
===
[toc]
## Reverse Integer
::: warning
Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-2^31, 2^31 - 1], then return 0.

Assume the environment does not allow you to store 64-bit integers (signed or unsigned).

 

Example 1:

Input: x = 123
Output: 321
Example 2:

Input: x = -123
Output: -321
Example 3:

Input: x = 120
Output: 21

:::

==python==
```
class Solution(object):
    def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        if x>0:
            x=str(x)
            rev=x[::-1]
            rev=int(rev)
        else:
            x=x-(2*x)
            x=str(x)
            rev=x[::-1]
            rev=int(rev)
            rev=rev-(2*rev)
            
        if -2**31<=rev<=2**31-1:
            return rev
        else:
            return 0
      
```
==JAVA==
```
class Solution {
    public int reverse(int x) {
        int num=0;
        int rev=0;
        while(x!=0){
            num=x%10;
            if(rev>Integer.MAX_VALUE/10 || rev < Integer.MIN_VALUE/10) 
                return 0;
            rev=rev*10+num;
            x=x/10;
        }
        return rev;
    }
}
```
## Minimum Penalty for a Shop
:::info
You are given the customer visit log of a shop represented by a 0-indexed string customers consisting only of characters 'N' and 'Y':

if the ith character is 'Y', it means that customers come at the ith hour
whereas 'N' indicates that no customers come at the ith hour.
If the shop closes at the jth hour (0 <= j <= n), the penalty is calculated as follows:

For every hour when the shop is open and no customers come, the penalty increases by 1.
For every hour when the shop is closed and customers come, the penalty increases by 1.
Return the earliest hour at which the shop must be closed to incur a minimum penalty.

Note that if a shop closes at the jth hour, it means the shop is closed at the hour j.
:::
:::success
for example:
Input: customers = "YYNY"
Output: 2
Explanation: 
- Closing the shop at the 0th hour incurs in 1+1+0+1 = 3 penalty.
- Closing the shop at the 1st hour incurs in 0+1+0+1 = 2 penalty.
- Closing the shop at the 2nd hour incurs in 0+0+0+1 = 1 penalty.
- Closing the shop at the 3rd hour incurs in 0+0+1+1 = 2 penalty.
- Closing the shop at the 4th hour incurs in 0+0+1+0 = 1 penalty.
Closing the shop at 2nd or 4th hour gives a minimum penalty. Since 2 is earlier, the optimal closing time is 2.
:::
```
class Solution(object):
    def bestClosingTime(self, customers):
        """
        :type customers: str
        :rtype: int
        """
        best_hour=0 #初始時間
        #0小時時，直接算有幾個Y，就是最多懲罰次數
        penalty=customers.count('Y')
        #設最少懲罰變數
        less_penalty=penalty
        #start=1-->索引從1開始
        for index,ch in enumerate(customers,start=1):
            #該位置為Y時，penalty-1
            if ch =='Y':
                penalty-=1
            #該位置為N時，penalty+1
            if ch =='N':
                penalty+=1
            #找出最少懲罰時間
            if penalty<less_penalty:
                less_penalty=penalty
                best_hour=index
        return best_hour#回傳最佳關閉時間
        
        YYNY-> index 0 -->penalty=3
        YYNY-> index 1 -->penalty=2
        YYNY-> index 2 -->penalty=1
        YYNY-> index 3 -->penalty=2
        YYNY-> index 4 -->penalty=1
        == best_hour is (index)2 ==
        
```
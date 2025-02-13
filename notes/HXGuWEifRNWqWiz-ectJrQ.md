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
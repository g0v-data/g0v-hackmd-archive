# LeetCode
[toc]
## roman to integer
Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
For example, 2 is written as II in Roman numeral, just two ones added together. 12 is written as XII, which is simply X + II. The number 27 is written as XXVII, which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:

I can be placed before V (5) and X (10) to make 4 and 9. 
X can be placed before L (50) and C (100) to make 40 and 90. 
C can be placed before D (500) and M (1000) to make 400 and 900.
Given a roman numeral, convert it to an integer.
==python==

```

class Solution(object):
    def romanToInt(self, s):
        """
        :type s: str
        :rtype: int
        """
        num={
            'I':1,'V':5,'X':10,'L':50,
            'C':100,'D':500,'M':1000
        }
        result=0
        #current=0
        prev=0

        for i in reversed(s):
            current=num[i]
            if  current<prev:
                result-=current
            else:
                result+=current
            prev=current
        return result
        
```
==JAVA==
```

class Solution {
    public int romanToInt(String s) {
      Map<Character, Integer> num = new HashMap<>();
        num.put('I', 1);
        num.put('V', 5);
        num.put('X', 10);
        num.put('L', 50);
        num.put('C', 100);
        num.put('D', 500);
        num.put('M', 1000);

        int result = 0;
        int length = s.length(); 

        for (int i = 0; i < length; i++) {
            if (i + 1 < length && num.get(s.charAt(i)) < num.get(s.charAt(i + 1))) {
                result -= num.get(s.charAt(i));
            } else {
                result += num.get(s.charAt(i));
            }
        }
        return result;
    }
}
```
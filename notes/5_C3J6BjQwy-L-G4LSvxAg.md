LeetCode-easy
===
[toc]
## roman to integer
:::info
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
:::
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
## two sum
:::info
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

 

Example 1:

Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
:::

==python==
```
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        for i in range(len(nums)):
            if i+1<len(nums)://確保不會超出len
                a=nums[i]//設初始值
                for j in range(i+1,len(nums)):
                    if(a+nums[j]==target)://檢查相加是否等於target
                        return i,j//回傳位置
        
```
```
>>> seasons = ['Spring', 'Summer', 'Fall', 'Winter']
>>> list(enumerate(seasons))
[(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
>>> list(enumerate(seasons, start=1))       # 下标从 1 开始
[(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]
```
```
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        num_dict = {}
        //enumberate=>nums=[1,2,3]=>enumerate(nums)=[(0, 1), (1, 2), (2, 3)]
        //前面是位置，後面是值
        for i, num in enumerate(nums):
            if target - num in num_dict://發現有該值
                return [num_dict[target - num], i]//回傳補數的值以及當前位置
            num_dict[num] = i//存該值的位置
```

## Merge Two Sorted Lists
:::info
You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.

 

Example 1:


Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
Example 2:

Input: list1 = [], list2 = []
Output: []
Example 3:

Input: list1 = [], list2 = [0]
Output: [0]
:::

==C#==
```
public class Solution {
    public ListNode MergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummy=new ListNode(0);// 虛擬頭節點
        ListNode prev=dummy;
        ListNode p1=list1;
        ListNode p2=list2;
        while( p1!=null && p2!=null){ // 迴圈遍歷，合併兩個鏈結串列
            if (p1.val<p2.val){
                prev.next=p1;
                p1=p1.next;
            }
            else{
                prev.next=p2;
                p2=p2.next;
            }
            prev=prev.next;
        } 
        prev.next = p1 != null ? p1 : p2;//進入最後階段時，p1 或 p2 可能為空，如果P1不是NULL，將P1加到最後，否則將P2加到最後
        return dummy.next;
    }
}
```
==python==
```
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def mergeTwoLists(self, list1, list2):
        """
        :type list1: Optional[ListNode]
        :type list2: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        dummy=prev=ListNode(0)
        p1,p2=list1,list2
        while p1 and p2:
            if p1.val<p2.val:
                prev.next=p1
                p1=p1.next
            else:
                prev.next=p2
                p2=p2.next
            prev=prev.next
        if p1:
            prev.next=p1
        else:
            prev.next=p2
        return dummy.next
```
## Palindrome Number
:::info
Given an integer x, return true if x is a 
palindrome
, and false otherwise.

 

Example 1:

Input: x = 121
Output: true
Explanation: 121 reads as 121 from left to right and from right to left.
Example 2:

Input: x = -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
Example 3:

Input: x = 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
:::

==python==
```
class Solution(object):
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        num=0
        ori=x
        if x<0:
            return False
        else:
            while x!=0:
                num=num*10+x%10
                x=x//10
            if ori==num:
                return True
            else:
                return False
```
轉成string用法
```
class Solution(object):
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        #num=0
        #ori=x
        if x<0://負數相反一定錯
            return False
        else://正數轉成string
            x=str(x)
            if x==x[::-1]://與反轉後的字做比對
                return True
            else:
                return False
```
## Search Insert Position
:::info
Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with O(log n) runtime complexity.

 

Example 1:

Input: nums = [1,3,5,6], target = 5
Output: 2
Example 2:

Input: nums = [1,3,5,6], target = 2
Output: 1
Example 3:

Input: nums = [1,3,5,6], target = 7
Output: 4
:::

==python==
```
class Solution(object):
    def searchInsert(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        //只要找到符合的就會return 跳出function
        for i in range(len(nums)):
            if nums[i]==target://找到對應位置
                return i
            elif target<nums[0]://目標比陣列裡的數都小
                return 0
            elif i<len(nums)-1 and nums[i]<target<nums[i+1]://目標可插入在陣列中
                return i+1
        return len(nums)//目標比陣列中數都大
```
==JAVA==
```
class Solution {
    public int searchInsert(int[] nums, int target) {
        int p1=0;//頭
        int p2=nums.length;//尾
        while(p1<p2){
            int mid=(p1+p2)/2;//從中間開始找
            if(nums[mid]>=target){//如果大於target
                p2=mid;//將尾改成mid
            }
            else if(nums[mid]<target){//如果小於target
                p1=mid+1;//將頭加1
            }
        }
        return p1;//回傳結果
    }
}
```
## Missing number
:::info
Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.

 

Example 1:

Input: nums = [3,0,1]

Output: 2

Explanation:

n = 3 since there are 3 numbers, so all numbers are in the range [0,3]. 2 is the missing number in the range since it does not appear in nums.
:::

```
class Solution(object):
    def missingNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        第一版:用for迴圈慢慢找
        # s=set(nums)
        # for i in range(len(nums)+1):
        #     if i not in s:
        #         return i
        第二版:用總和公式加總，就能找到缺少的數字
        n=len(nums)
        return n*(n+1)//2-sum(nums)
```
## find the duplicate number
:::info
給定一個整數數組，其中nums包含的 n + 1整數都在給定的範圍內[1, n]（包含該範圍）。

陣列中只有一個重複的數字nums，回傳這個重複的數字。

你必須在不修改數組的情況下nums ，僅使用常數額外空間來解決該問題。
:::
```
class Solution(object):
    def findDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        check=set() //建立一個空集合，用來存「出現過的數字」
        for i in nums:
            if i in check://找到重複的數就回傳
                return i  
            else://沒找到就存進check
                check.add(i)
```

## Valid Parentheses
:::info
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.
:::
```
//用stack的方法去解，把數值一一放進
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        stack=[]
        mapping={')':'(','}':'{',']':'['}
        for char in s:
            if char in mapping.values()://先把( { [ 放進stack
                stack.append(char)
            elif char in mapping: 然後開始找)}]
                if not stack:如果stack是空的，回傳false
                    return False
                elif mapping[char] != stack.pop()://如果下一個值跟目前stack的top不是同一對，回傳false
                    return False
        return not stack
```
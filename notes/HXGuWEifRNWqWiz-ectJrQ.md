leetcode-medium
===
[toc]
## two pointer
### Container With Most Water(11)
:::warning
You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return the maximum amount of water a container can store.

Notice that you may not slant the container.

 

Example 1:
![](https://g0v.hackmd.io/_uploads/SyOVzAs4zx.png)


Input: height = [1,8,6,2,5,4,8,3,7]
Output: 49
Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.
Example 2:

Input: height = [1,1]
Output: 1
:::
```
class Solution(object):
    def maxArea(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        max_area=0 #最大面積
        left=0 
        right=len(height)-1
        while left<right:
            if height[left]<height[right]: #判斷左右兩邊哪邊比較長
                total=height[left]*(right-left) #計算面積
                left+=1 #左邊比較小則left往右移一個位置
            else:
                total=height[right]*(right-left)
                right-=1 #右邊比較小則right往左移一個位置
            if total > max_area: #判斷是否有超過原有的max_area
                max_area=total
        return max_area
              
        
```
### 3Sum(15)
:::warning
Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]]uch that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.

Notice that the solution set must not contain duplicate triplets.

 

Example 1:

Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]
Explanation: 
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.
Example 2:

Input: nums = [0,1,1]
Output: []
Explanation: The only possible triplet does not sum up to 0.
Example 3:

Input: nums = [0,0,0]
Output: [[0,0,0]]
Explanation: The only possible triplet sums up to 0.
:::
==python==
```
#==用two pointer來解==
class Solution(object):
    def threeSum(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        nums.sort() #把list排序好，由小排到大
        new=[] #創建一個新的list
        for i in range(len(nums)):
            if i > 0 and nums[i] == nums[i-1]:
                continue #確認是否與上個值重複，如果重複就跳過
            left=i+1 
            right=len(nums)-1
            while left < right:
                total =nums[i]+nums[left]+nums[right]
                if total < 0: #總和小於0，則left+1
                    left+=1
                elif total >0: #總和大於0，則right-1
                    right-=1
                else:#找到適配組合則加入new list
                    new.append([nums[i],nums[left],nums[right]])
                    left+=1 #繼續two pointer尋找下一個合適的組合
                    right-=1
                    while left<right and nums[left]==nums[left-1]: #檢查left與上一個值有沒有重複
                        left+=1
                    while left<right and nums[right]==nums[right+1]:#檢查right與下一個值有沒有重複
                        right-=1
        return new #回傳new list   
```
### 3Sum Closest(16)
:::warning
Given an integer array nums of length n and an integer target, find three integers at distinct indices in nums such that the sum is closest to target.

Return the sum of the three integers.

You may assume that each input would have exactly one solution.

 

Example 1:

Input: nums = [-1,2,1,-4], target = 1
Output: 2
Explanation: The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
Example 2:

Input: nums = [0,0,0], target = 1
Output: 0
Explanation: The sum that is closest to the target is 0. (0 + 0 + 0 = 0).
:::
```
class Solution(object):
    def threeSumClosest(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        
        nums.sort() #先對list進行排序
        cloest=nums[0] + nums[1] + nums[2]#設前三個數字加總為cloest
        for i in range(len(nums)):
            left=i+1
            right=len(nums)-1
            while left <right:
                total =nums[i]+nums[left]+nums[right]
                if abs(target-total)< abs(cloest-target):
                    cloest=total #如果相減後比上一個cloest-target還小，則替代
                if total < target: 
                    left+=1
                elif total > target:
                    right-=1
                else:
                    return target # abs(target - target) = 0
        return cloest
```

### 4Sum(18)
:::warning
Given an array nums of n integers, return an array of all the unique quadruplets [nums[a], nums[b], nums[c], nums[d]] such that:

0 <= a, b, c, d < n
a, b, c, and d are distinct.
nums[a] + nums[b] + nums[c] + nums[d] == target
You may return the answer in any order.

 

Example 1:

Input: nums = [1,0,-1,0,-2,2], target = 0
Output: [[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]
Example 2:

Input: nums = [2,2,2,2,2], target = 8
Output: [[2,2,2,2]]
:::
```
#固定兩個數字，用two pointer找另外兩個數字
class Solution(object):
    def fourSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[List[int]]
        """
        nums.sort()#先排序
        new=[]#設立新的list，找到組合後append進去
        n=len(nums)
        for i in range(n-3):
            if i>0 and nums[i]==nums[i-1]:#判斷
                continue
            for j in range(i+1,n-2):
                if j>i+1 and nums[j]==nums[j-1]:
                    continue
                left=j+1
                right=n-1
                while left < right :
                    total =nums[i]+nums[j]+nums[left]+nums[right]
                    if total<target:
                        left+=1
                    elif total>target:
                        right-=1
                    else :
                        new.append([nums[i],nums[j],nums[left],nums[right]])
                        left+=1
                        right-=1
                        while left<right and nums[left]==nums[left-1]:
                            left+=1
                        while left<right and nums[right]==nums[right+1]:
                            right-=1
        return new
                    

```
### Two Sum II - Input Array Is Sorted(167)
:::warning
Given a 1-indexed array of integers numbers that is already sorted in non-decreasing order, find two numbers such that they add up to a specific target number. Let these two numbers be numbers[index1] and numbers[index2] where 1 <= index1 < index2 <= numbers.length.

Return the indices of the two numbers index1 and index2, each incremented by one, as an integer array [index1, index2] of length 2.

The tests are generated such that there is exactly one solution. You may not use the same element twice.

Your solution must use only constant extra space.

 

Example 1:

Input: numbers = [2,7,11,15], target = 9
Output: [1,2]
Explanation: The sum of 2 and 7 is 9. Therefore, index1 = 1, index2 = 2. We return [1, 2].
Example 2:

Input: numbers = [2,3,4], target = 6
Output: [1,3]
Explanation: The sum of 2 and 4 is 6. Therefore index1 = 1, index2 = 3. We return [1, 3].
Example 3:

Input: numbers = [-1,0], target = -1
Output: [1,2]
Explanation: The sum of -1 and 0 is -1. Therefore index1 = 1, index2 = 2. We return [1, 2].
:::
```
class Solution(object):
    def twoSum(self, numbers, target):
        """
        :type numbers: List[int]
        :type target: int
        :rtype: List[int]
        """
        left=0
        right=len(numbers)-1
        while left < right:
            total=numbers[left]+numbers[right]
            if total<target:
                left+=1
            elif total>target:
                right-=1
            else:
                return [left+1,right+1]
```
## Binary Search
### Search a 2D Matrix(74)
:::warning
You are given an m x n integer matrix matrix with the following two properties:

Each row is sorted in non-decreasing order.
The first integer of each row is greater than the last integer of the previous row.
Given an integer target, return true if target is in matrix or false otherwise.

You must write a solution in O(log(m * n)) time complexity.

 

Example 1:

![](https://g0v.hackmd.io/_uploads/SklUqGk34zg.png)

Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
Output: true
:::
```
class Solution(object):
    def searchMatrix(self, matrix, target):
        """
        :type matrix: List[List[int]]
        :type target: int
        :rtype: bool
        """

        # 矩陣的列數 (row)
        row = len(matrix)

        # 矩陣的欄數 (column)
        col = len(matrix[0])

        # Binary Search 的起點 (第一個元素)
        start = 0

        # Binary Search 的終點 (最後一個元素)
        end = row * col - 1

        # 只要搜尋範圍還存在，就繼續搜尋
        while start <= end:

            # 找中間位置
            mid = (start + end) // 2

            # 將一維索引轉回二維座標
            r = mid // col      # 第幾列
            c = mid % col       # 第幾欄

            # 找到目標
            if matrix[r][c] == target:
                return True

            # target 在右半邊
            elif matrix[r][c] < target:
                start = mid + 1

            # target 在左半邊
            else:
                end = mid - 1

        # 找不到 target
        return False
```
### Find Minimum in Rotated Sorted Array(153)
:::warning
Suppose an array of length n sorted in ascending order is rotated between 1 and n times. For example, the array nums = [0,1,2,4,5,6,7] might become:

[4,5,6,7,0,1,2] if it was rotated 4 times.
[0,1,2,4,5,6,7] if it was rotated 7 times.
Notice that rotating an array [a[0], a[1], a[2], ..., a[n-1]] 1 time results in the array [a[n-1], a[0], a[1], a[2], ..., a[n-2]].

Given the sorted rotated array nums of unique elements, return the minimum element of this array.

You must write an algorithm that runs in O(log n) time.

 

Example 1:

Input: nums = [3,4,5,1,2]
Output: 1
Explanation: The original array was [1,2,3,4,5] rotated 3 times.
Example 2:

Input: nums = [4,5,6,7,0,1,2]
Output: 0
Explanation: The original array was [0,1,2,4,5,6,7] and it was rotated 4 times.
Example 3:

Input: nums = [11,13,15,17]
Output: 11
Explanation: The original array was [11,13,15,17] and it was rotated 4 times. 
:::
```
class Solution(object):
    def findMin(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        left=0
        right=len(nums)-1
        while left < right :
            mid=left+(right-left)//2
            # 最小值在右邊
            if nums[mid] > nums[right]:
                left = mid + 1
            # 最小值在左邊(包含mid)
            else:
                right=mid
        return nums[left]

```
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
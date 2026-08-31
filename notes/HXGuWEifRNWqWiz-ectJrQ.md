leetcode-medium
===
[toc]
## Arrays & Hashing
### Product of Array Except Self(238)
:::warning
Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in O(n) time and without using the division operation.

 

Example 1:

Input: nums = [1,2,3,4]
Output: [24,12,8,6]
Example 2:

Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]
:::
```
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        n=len(nums)
         # answer 先拿來存「左邊所有元素的乘積」
        answer=[1]*n
        prefix=1
        # 第一輪：算每個位置左邊的乘積
        for i in range(len(nums)):
            answer[i]=prefix
            prefix*=nums[i]
        suff=1
        for i in range(n-1,-1,-1):
            # suffix 是「我右邊所有數字的乘積」
            answer[i]*=suff
            # 把我自己加入 suffix
            # 給左邊的下一個人使用
            suff*=nums[i]
        return answer
```
### Sort an Array(912)
:::warning
Given an array of integers nums, sort the array in ascending order and return it.

You must solve the problem without using any built-in functions in O(nlog(n)) time complexity and with the smallest space complexity possible.

 

Example 1:

Input: nums = [5,2,3,1]
Output: [1,2,3,5]
Explanation: After sorting the array, the positions of some numbers are not changed (for example, 2 and 3), while the positions of other numbers are changed (for example, 1 and 5).
Example 2:

Input: nums = [5,1,1,2,0,0]
Output: [0,0,1,1,2,5]
Explanation: Note that the values of nums are not necessarily unique.
:::
```
# 使用merge sort
class Solution(object):
    def sortArray(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """

        # Base Case：
        # 如果陣列長度為 0 或 1，代表已經排序完成，直接回傳
        if len(nums) <= 1:
            return nums

        # 找到陣列中間的位置
        mid = len(nums) // 2

        # 將陣列切成左右兩半
        left = nums[:mid]
        right = nums[mid:]

        # 遞迴排序左半部
        left = self.sortArray(left)

        # 遞迴排序右半部
        right = self.sortArray(right)

        # 將兩個已排序的陣列合併
        return self.merge(left, right)

    def merge(self, left, right):

        # i：左半部索引
        # j：右半部索引
        i = j = 0

        # 存放合併後的排序結果
        result = []

        # 只要左右兩邊都還有元素，就持續比較
        while i < len(left) and j < len(right):

            # 左邊元素較小(或相等)，先放入 result
            if left[i] <= right[j]:
                result.append(left[i])
                i += 1

            # 否則放入右邊元素
            else:
                result.append(right[j])
                j += 1

        # 如果左半部還有剩餘元素，直接全部加入
        result.extend(left[i:])

        # 如果右半部還有剩餘元素，直接全部加入
        result.extend(right[j:])

        # 回傳合併完成且排序好的陣列
        return result
```
```
# quick sort解法
import random

class Solution:
    def sortArray(self, nums):
        self.quickSort(nums, 0, len(nums) - 1)
        return nums

    def quickSort(self, nums, low, high):
        # 區間只有一個元素或沒有元素
        if low >= high:
            return

        # 隨機選一個 Pivot
        pivot = nums[random.randint(low, high)]

        # lt 左邊都是小於 Pivot 的元素
        lt = low

        # i 是目前正在檢查的位置
        i = low

        # gt 右邊都是大於 Pivot 的元素
        gt = high

        while i <= gt:
            if nums[i] < pivot:
                # 小於 Pivot，交換到左邊
                nums[lt], nums[i] = nums[i], nums[lt]

                lt += 1
                i += 1

            elif nums[i] > pivot:
                # 大於 Pivot，交換到右邊
                nums[i], nums[gt] = nums[gt], nums[i]

                gt -= 1

                # 交換過來的 nums[i] 還沒檢查
                # 所以這裡不能讓 i += 1

            else:
                # 等於 Pivot，留在中間
                i += 1

        # 排序小於 Pivot 的區域
        self.quickSort(nums, low, lt - 1)

        # lt 到 gt 都等於 Pivot，不需要排序

        # 排序大於 Pivot 的區域
        self.quickSort(nums, gt + 1, high)
```
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
### Search in Rotated Sorted Array(33)
:::warning
There is an integer array nums sorted in ascending order (with distinct values).

Prior to being passed to your function, nums is possibly left rotated at an unknown index k (1 <= k < nums.length) such that the resulting array is [nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]] (0-indexed). For example, [0,1,2,4,5,6,7] might be left rotated by 3 indices and become [4,5,6,7,0,1,2].

Given the array nums after the possible rotation and an integer target, return the index of target if it is in nums, or -1 if it is not in nums.

You must write an algorithm with O(log n) runtime complexity.

 

Example 1:

Input: nums = [4,5,6,7,0,1,2], target = 0
Output: 4
Example 2:

Input: nums = [4,5,6,7,0,1,2], target = 3
Output: -1
Example 3:

Input: nums = [1], target = 0
Output: -1
:::
```
class Solution(object):
    def search(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        left = 0
        right = len(nums) - 1

        # 搜尋區間仍存在
        while left <= right:

            # 計算中間位置
            mid = left + (right - left) // 2

            # 找到 target
            if nums[mid] == target:
                return mid
            # 特殊情況：
            # nums[left]、nums[mid]、nums[right] 都相同
            # 無法判斷哪一半是有序的
            #
            # 例如：
            # [1,1,1,1,3,1]
            #  L    M     R
            #
            # 此時只能把左右各縮一格
            if nums[left] == nums[mid] == nums[right]:
                left += 1
                right -= 1
            # 左半邊有序
            #
            # 例如：
            # [4,5,6,7,0,1,2]
            #  L   M
            #
            # nums[left] <= nums[mid]
            # -------------------------------------------------
            elif nums[left] <= nums[mid]:

                # target 落在左半邊有序區間
                if nums[left] <= target < nums[mid]:
                    right = mid - 1

                # target 不在左半邊
                else:
                    left = mid + 1

            # -------------------------------------------------
            # 右半邊有序
            #
            # 例如：
            # [6,7,0,1,2,4,5]
            #        M      R
            # -------------------------------------------------
            else:

                # target 落在右半邊有序區間
                if nums[mid] < target <= nums[right]:
                    left = mid + 1

                # target 不在右半邊
                else:
                    right = mid - 1

        # 找不到
        return -1
```
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
### Search in Rotated Sorted Array II(81)
:::warning
There is an integer array nums sorted in non-decreasing order (not necessarily with distinct values).

Before being passed to your function, nums is rotated at an unknown pivot index k (0 <= k < nums.length) such that the resulting array is [nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]] (0-indexed). For example, [0,1,2,4,4,4,5,6,6,7] might be rotated at pivot index 5 and become [4,5,6,6,7,0,1,2,4,4].

Given the array nums after the rotation and an integer target, return true if target is in nums, or false if it is not in nums.

You must decrease the overall operation steps as much as possible.

 

Example 1:

Input: nums = [2,5,6,0,0,1,2], target = 0
Output: true
Example 2:

Input: nums = [2,5,6,0,0,1,2], target = 3
Output: false
:::
```
class Solution(object):
    def search(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: bool
        """

        # Binary Search 左右邊界
        left = 0
        right = len(nums) - 1

        # 搜尋區間仍存在
        while left <= right:

            # 計算中間位置
            mid = left + (right - left) // 2

            # 找到 target
            if nums[mid] == target:
                return True

            # -------------------------------------------------
            # 特殊情況：
            # nums[left]、nums[mid]、nums[right] 都相同
            # 無法判斷哪一半是有序的
            #
            # 例如：
            # [1,1,1,1,3,1]
            #  L    M     R
            #
            # 此時只能把左右各縮一格
            # -------------------------------------------------
            if nums[left] == nums[mid] == nums[right]:
                left += 1
                right -= 1

            # -------------------------------------------------
            # 左半邊有序
            #
            # 例如：
            # [4,5,6,7,0,1,2]
            #  L   M
            #
            # nums[left] <= nums[mid]
            # -------------------------------------------------
            elif nums[left] <= nums[mid]:

                # target 落在左半邊有序區間
                if nums[left] <= target < nums[mid]:
                    right = mid - 1

                # target 不在左半邊
                else:
                    left = mid + 1

            # -------------------------------------------------
            # 右半邊有序
            #
            # 例如：
            # [6,7,0,1,2,4,5]
            #        M      R
            # -------------------------------------------------
            else:

                # target 落在右半邊有序區間
                if nums[mid] < target <= nums[right]:
                    left = mid + 1

                # target 不在右半邊
                else:
                    right = mid - 1

        # 找不到
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
### Koko Eating Bananas(875)
:::warning
Koko loves to eat bananas. There are n piles of bananas, the ith pile has piles[i] bananas. The guards have gone and will come back in h hours.

Koko can decide her bananas-per-hour eating speed of k. Each hour, she chooses some pile of bananas and eats k bananas from that pile. If the pile has less than k bananas, she eats all of them instead and will not eat any more bananas during this hour.

Koko likes to eat slowly but still wants to finish eating all the bananas before the guards return.

Return the minimum integer k such that she can eat all the bananas within h hours.

 

Example 1:

Input: piles = [3,6,7,11], h = 8
Output: 4
Example 2:

Input: piles = [30,11,23,4,20], h = 5
Output: 30
Example 3:

Input: piles = [30,11,23,4,20], h = 6
Output: 23
:::
```
class Solution(object):
    def minEatingSpeed(self, piles, h):
        """
        :type piles: List[int]
        :type h: int
        :rtype: int
        """

        # 最小速度至少是 1 根/小時
        left = 1

        # 最大速度不可能超過最大那堆香蕉
        right = max(piles)

        # Binary Search 搜尋「最小可行速度」
        while left < right:

            # 猜目前的吃香蕉速度
            mid = left + (right - left) // 2

            # 計算以速度 mid 吃完所有香蕉需要多少小時
            hours = 0

            for i in piles:
                # (i + mid - 1) // mid 等同於 math.ceil(i / mid)
                # 因為一小時只能吃一堆，所以不足一小時也要算一小時
                hours += (i + mid - 1) // mid

            # 如果花費時間超過 h
            # 代表速度太慢，需要提高速度
            if hours > h:
                left = mid + 1

            # 如果可以在 h 小時內完成
            # 代表目前速度可行，試試看能不能更慢
            else:
                right = mid

        # left == right 時，就是最小可行速度
        return left
```
## Linked List
### Find the Minimum and Maximum Number of Nodes Between Critical Points(2058)
:::warning
A critical point in a linked list is defined as either a local maxima or a local minima.

A node is a local maxima if the current node has a value strictly greater than the previous node and the next node.

A node is a local minima if the current node has a value strictly smaller than the previous node and the next node.

Note that a node can only be a local maxima/minima if there exists both a previous node and a next node.

Given a linked list head, return an array of length 2 containing [minDistance, maxDistance] where minDistance is the minimum distance between any two distinct critical points and maxDistance is the maximum distance between any two distinct critical points. If there are fewer than two critical points, return [-1, -1].
![](https://g0v.hackmd.io/_uploads/BkgCpNaGdMg.png)

:::
```
class Solution:
    def nodesBetweenCriticalPoints(self, head: Optional[ListNode]) -> List[int]:
        # 少於 3 個節點，不可能有 critical point
        if head.next.next==None:
            return [-1, -1]
        
        # 第一個 critical point 的位置
        first = -1

        # 上一個 critical point 的位置
        prev_critical = -1

        # index = 1，因為目前檢查的是 head.next
        i=1

        # 最小距離
        min_dist = float('inf')# 假設是正無限大
        while head.next and head.next.next :
            current=head.next
            if (current.val<head.val and current.val<current.next.val) or (current.val>head.val and current.val>current.next.val):
                # 第一個 critical point
                if first == -1:
                    first = i

                else:
                    # 計算與上一個 critical point 的距離
                    min_dist = min(min_dist, i - prev_critical)

                # 更新上一個 critical point
                prev_critical = i
            i+=1
            head=current
        
        # 不到兩個 critical points
        if min_dist == float('inf'):
            return [-1, -1]

        # 最大距離 = 最後一個 - 第一個
        max_dist = prev_critical - first
        return [min_dist, max_dist]
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
## sliding window
### Longest Substring Without Repeating Characters(3)
:::warning
Given a string s, find the length of the longest substring without duplicate characters.

 

Example 1:

Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3. Note that "bca" and "cab" are also correct answers.
Example 2:

Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
Example 3:

Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
:::
```
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        new=set()
        left=0
        
        max_count=0
        
        # 右指針只會一往無前地向右走，絕不回頭
        for right in range(len(s)):
            
            # 如果新進來的字元 s[right] 重複了
            # 直到集合裡沒有 s[right] 為止
            while s[right] in new:
                new.remove(s[left])
                left += 1
                
            # 確保沒重複後，把新字元加進去
            new.add(s[right])
            
            # 更新最大長度
            max_count = max(max_count, right - left + 1)
        return max_count

```
### Longest Repeating Character Replacement(424)
:::warning
You are given a string s and an integer k. You can choose any character of the string and change it to any other uppercase English character. You can perform this operation at most k times.

Return the length of the longest substring containing the same letter you can get after performing the above operations.

 

Example 1:

Input: s = "ABAB", k = 2
Output: 4
Explanation: Replace the two 'A's with two 'B's or vice versa.
Example 2:

Input: s = "AABABBA", k = 1
Output: 4
Explanation: Replace the one 'A' in the middle with 'B' and form "AABBBBA".
The substring "BBBB" has the longest repeating letters, which is 4.
There may exists other ways to achieve this answer too.
:::
```
from collections import defaultdict

class Solution:

    def characterReplacement(self, s: str, k: int) -> int:

        # 紀錄目前 sliding window 中，每個字元出現的次數
        freq = defaultdict(int)

        # i 是 sliding window 的左指標
        i = 0

        # 紀錄目前找到的最長合法字串長度
        num = 0

        # j 是 sliding window 的右指標，不斷向右擴展
        for j in range(len(s)):

            # 將目前右指標指向的字元加入 window
            # 並將該字元出現次數 +1
            freq[s[j]] += 1

            # 找出目前 window 中出現次數最多的字元
            # 例如 AABA -> A 出現 3 次，所以 maxfreq = 3
            maxfreq = max(freq.values())

            # 計算目前 sliding window 的長度
            currentLen = j - i + 1

            # 需要替換的字元數
            # = window 長度 - 出現最多次的字元數
            #
            # 如果需要替換的字元數 > k
            # 代表目前 window 不合法，需要縮小 window
            if currentLen - maxfreq > k:

                # 將左指標目前指向的字元移出 window
                # 所以該字元的出現次數 -1
                freq[s[i]] -= 1

                # 左指標向右移動，縮小 window
                i += 1

            # 更新目前找到的最長合法 window 長度
            num = max(num, j - i + 1)

        # 回傳最長可以透過最多 k 次替換
        # 變成相同字元的子字串長度
        return num
```
### Permutation in String(567)
:::warning
Given two strings s1 and s2, return true if s2 contains a permutation of s1, or false otherwise.

In other words, return true if one of s1's permutations is the substring of s2.

 

Example 1:

Input: s1 = "ab", s2 = "eidbaooo"
Output: true
Explanation: s2 contains one permutation of s1 ("ba").
Example 2:

Input: s1 = "ab", s2 = "eidboaoo"
Output: false
:::
```
from collections import Counter


class Solution:

    def checkInclusion(self, s1: str, s2: str) -> bool:
        len1, len2 = len(s1), len(s2)
        if len1 > len2:
            return False

        check = Counter(s1)

        # 1. 先建立 s2 前面 len1 長度的初始視窗 Counter
        window = Counter(s2[:len1])

        # 如果一開始就 match，直接回傳 True
        if window == check:
            return True

        # 2. 開始高效滑動：一進一出
        for i in range(len1, len2):
            right_char = s2[i]  # 新進入右邊的字元
            left_char = s2[i - len1]  # 從左邊離開的字元

            # 右邊進來，數量 +1
            window[right_char] += 1

            # 左邊離開，數量 -1
            window[left_char] -= 1
            if window[left_char] == 0:
                del window[left_char]  # 數量變成 0 的字元要刪掉，免得影響 == 的比對

            # 每次只改兩個字元，馬上進行比對
            if window == check:
                return True

        return False

```

## Greedy
### Minimum Number of Pushes to Type Word II(3016)
:::warning
You are given a string word containing lowercase English letters.

Telephone keypads have keys mapped with distinct collections of lowercase English letters, which can be used to form words by pushing them. For example, the key 2 is mapped with ["a","b","c"], we need to push the key one time to type "a", two times to type "b", and three times to type "c" .

It is allowed to remap the keys numbered 2 to 9 to distinct collections of letters. The keys can be remapped to any amount of letters, but each letter must be mapped to exactly one key. You need to find the minimum number of times the keys will be pushed to type the string word.

Return the minimum number of pushes needed to type word after remapping the keys.

An example mapping of letters to keys on a telephone keypad is given below. Note that 1, *, #, and 0 do not map to any letters.

Example 2:


Input: word = "xyzxyzxyzxyz"
Output: 12
Explanation: The remapped keypad given in the image provides the minimum cost.
"x" -> one push on key 2
"y" -> one push on key 3
"z" -> one push on key 4
Total cost is 1 * 4 + 1 * 4 + 1 * 4 = 12
It can be shown that no other mapping can provide a lower cost.
Note that the key 9 is not mapped to any letter: it is not necessary to map letters to every key, but to map all the letters.
:::
```
class Solution(object):
    def minimumPushes(self, word):
        """
        :type word: str
        :rtype: int
        """
        counts = []
        # 統計 a～z 每個字母在 word 中出現幾次
        for i in range(26):
            letter = chr(97 + i)
            frequency = word.count(letter)
            counts.append(frequency)
        # 出現次數由大到小排序
        # 讓高頻字母優先放在按鍵次數較少的位置
        counts.sort(reverse=True)

        # 總按鍵次數
        total_pushes = 0

        # i：排序後的位置
        # frequency：該字母出現的次數
        for i, frequency in enumerate(counts):

            # 排序後一旦遇到 0，後面也全部都是 0
            if frequency == 0:
                break

            # 每 8 個字母為一層
            # i=0～7   → 按 1 次
            # i=8～15  → 按 2 次
            # i=16～23 → 按 3 次
            pushes_per_character = i // 8 + 1

            # 出現次數 × 每次所需按鍵數
            total_pushes += frequency * pushes_per_character

        return total_pushes
        
        # cost=0
        # count=Counter(word).most_common()
        # for i in range(len(count)):
        #     cost+=(i//8+1)*count[i][1]
        # return cost
```
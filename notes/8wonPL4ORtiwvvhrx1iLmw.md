LeetCode-hard
===
[toc]

## two pointer
### Trapping Rain Water(42)
:::danger
Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.

 

![](https://g0v.hackmd.io/_uploads/HJmcJPxuGg.png)



Input: height = [0,1,0,2,1,0,1,3,2,1,2,1]
Output: 6
Explanation: The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped.
Example 2:

Input: height = [4,2,0,3,2,5]
Output: 9
:::
```
class Solution:
    def trap(self, height: List[int]) -> int:

        # 左指標，從陣列最左邊開始
        left = 0

        # 右指標，從陣列最右邊開始
        right = len(height) - 1

        # 紀錄從左邊走到目前位置為止，遇過的最高柱子
        left_max = 0

        # 紀錄從右邊走到目前位置為止，遇過的最高柱子
        right_max = 0

        # 紀錄總共可以接多少雨水
        count = 0

        # 左右指標還沒相遇，就繼續計算
        while left < right:

            # 左邊柱子比較矮
            # 水能裝多高會受到比較矮的左邊限制
            # 所以這次處理 left
            if height[left] < height[right]:

                # 如果目前柱子比之前的 left_max 還高
                # 代表找到新的左邊最高柱子
                if height[left] >= left_max:
                    left_max = height[left]

                # 如果目前柱子比 left_max 矮
                # 中間的高度差就是這一格可以裝的水
                else:
                    count += left_max - height[left]

                # 左指標往右移動一格
                left += 1

            # 右邊柱子比較矮，或左右一樣高
            # 所以這次處理 right
            else:

                # 如果目前柱子比之前的 right_max 還高
                # 代表找到新的右邊最高柱子
                if height[right] >= right_max:
                    right_max = height[right]

                # 如果目前柱子比 right_max 矮
                # 中間的高度差就是這一格可以裝的水
                else:
                    count += right_max - height[right]

                # 右指標往左移動一格
                right -= 1

        # 回傳所有位置累積的雨水量
        return count
```
## binary serach
### Median of Two Sorted Arrays(4)
:::danger
Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.

The overall run time complexity should be O(log (m+n)).

 

Example 1:

Input: nums1 = [1,3], nums2 = [2]
Output: 2.00000
Explanation: merged array = [1,2,3] and median is 2.
Example 2:

Input: nums1 = [1,2], nums2 = [3,4]
Output: 2.50000
Explanation: merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.
:::
```

```
# Maximum Subarray

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.



Example 1:
```
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```
Example 2:
```
Input: nums = [1]
Output: 1
```
Example 3:
```
Input: nums = [0]
Output: 0
```
Example 4:
```
Input: nums = [-1]
Output: -1
```
Example 5:
```
Input: nums = [-100000]
Output: -100000
 ```

Constraints:

1 <= nums.length <= 3 * 104
-105 <= nums[i] <= 105

---

```
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        
    }
};
```

    
[-2,1,-3,4,-1,2,1,-5,4]

Step 1.

1. Final sum
2. Local sum to replace


Step 1.
-2

Step 2
-2 + 1 = -1

Step 3

-2 + 1 -3 = -4


fun maxSubArray(inout nums:[Int]) -> Int{
    var result = 0
    var numbers = nums.sorted()
    var max_value = 0
    for n in numbers
    {
        
       result += n
    }
    
    
    return result
}